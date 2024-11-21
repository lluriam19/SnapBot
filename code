#!/bin/bash

# Directorio de salida para las capturas de pantalla
OUTPUT_DIR="./screenshots/"

# Verifica que el directorio de salida exista, si no lo crea
mkdir -p "$OUTPUT_DIR"

# Fichero que contiene las URLs
URL_FILE="clean_urls.txt"

# Verifica que el fichero de URLs exista
if [[ ! -f "$URL_FILE" ]]; then
  echo "El fichero $URL_FILE no existe. Por favor, crea el fichero con las URLs."
  exit 1
fi

# Tamaño de la ventana para la captura de pantalla
WINDOW_SIZE="1920x1080"

# Bucle para leer las URLs del archivo
while IFS= read -r URL; do
  # Verifica si la URL no está vacía
  if [[ -z "$URL" ]]; then
    continue
  fi
  
  # Extrae el nombre del archivo a partir de la URL (sin http:// y reemplazando / por _)
  FILENAME=$(echo "$URL" | sed 's/[^a-zA-Z0-9]/_/g').png
  
  # Usamos la fecha y hora para evitar nombres duplicados
  TIMESTAMP=$(date +%Y%m%d_%H%M%S)
  OUTPUT_FILE="$OUTPUT_DIR$(basename "$FILENAME" .png)_$TIMESTAMP.png"
  
  # Ejecutamos Chromium en modo headless dentro de un subshell y usamos disown
  (chromium --headless --disable-gpu --no-sandbox --remote-debugging-port=9222 --window-size=$WINDOW_SIZE --virtual-time-budget=30000 --screenshot="$OUTPUT_FILE" --disable-software-rasterizer "$URL" > /dev/null 2>&1) &
  
  CHROMIUM_PID=$!
  disown $CHROMIUM_PID  # Desvincula el proceso del shell
  
  # Esperamos a que el proceso se termine correctamente (hasta X segundos)
  sleep 5
  # Verificamos si el proceso sigue corriendo y lo matamos si es necesario
  if ps -p $CHROMIUM_PID > /dev/null; then
    echo "Chromium sigue corriendo, cerrando proceso..."
    kill -9 $CHROMIUM_PID 
  fi
  
  echo "Captura de pantalla realizada para: $URL"
done < "$URL_FILE"
