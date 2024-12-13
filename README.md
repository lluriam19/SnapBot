**What does the script do?**

* **Automates screenshot captures**: The script reads a file of URLs, iterates through each one, and takes a screenshot of every page using Chromium in headless mode.

* **Saves images with unique names**: Screenshots are saved in an output directory and automatically named to avoid collisions by adding a timestamp to each file.

* **Closes processes if necessary**: If the Chromium process keeps running after a certain time, the script terminates it to prevent orphan processes.

* **Optimization and control**: The script efficiently manages captures, allows window size configurations, and suppresses unnecessary error messages.

### Why is it useful?

* **Massive website capture**: Ideal for web auditing projects, capture testing, or even generating visual reports.

* **Automation of repetitive tasks**: Automates the capture process quickly and without manual intervention, saving time when collecting visual information from websites.

* **Configurability**: The window size and output directory are easily adjustable to meet user requirements.

### Technologies used:

- Bash scripting  
- Chromium (headless mode)  
- Linux/Unix  

This script is a valuable tool for cybersecurity professionals, web application testers, and anyone who needs to automate webpage screenshot capturing.

**How to Use SnapBot**

I will use Gobuster to explain how to use the tool.

My target will be a VM with the IP address `10.10.75.87`, and the results discovered by Gobuster will be sent to a file called `urls.txt`:

![image](https://github.com/user-attachments/assets/dae98e74-3393-433b-b54b-3f4285498988)


After completing the exploration, the file will have output similar to the following:

![image](https://github.com/user-attachments/assets/8e0582e4-465f-4095-ab75-370e03ee30ae)

The tool requires a well-defined URL structure, like the following, to perform the image captures inside a file called `clean_urls.txt`:

![image](https://github.com/user-attachments/assets/cb96b5ec-14a7-4499-a2b2-d098c531aef5)


To achieve the structure above, we use the following command:

Syntax : ```awk '{print "ip"$1}' urls.txt  > clean_map.txt or awk '{print "ip/dir"$1}' urls.txt  > clean_map.txt```

``` awk '{print "http://10.10.75.87/joomla"$1}' urls.txt  > clean_map.txt  ```

Now, it is just a matter of granting execution permissions and, of course, running the tool:

![image](https://github.com/user-attachments/assets/94a8d700-00cd-4a1d-98c1-88d8140049e6)

Once finished, a folder named screenshots will be created in the working directory, containing the screenshots:
 
![image](https://github.com/user-attachments/assets/0614baea-0747-4110-be1c-571762e47843)

![image](https://github.com/user-attachments/assets/03cd0b53-c9fb-43a7-a3f9-456cf300730f)

![image](https://github.com/user-attachments/assets/b479d6b8-474a-4e2d-8995-301d369c9a08)


