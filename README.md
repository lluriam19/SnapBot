**How to Use SnapBot**

I will use Gobuster to explain how to use the tool.

My target will be a VM with the IP address 10.10.75.87, and the results discovered by Gobuster will be sent to a file called `echo urls.txt`:

![image](https://github.com/user-attachments/assets/dae98e74-3393-433b-b54b-3f4285498988)


After completing the exploration, the file will have output similar to the following:

![image](https://github.com/user-attachments/assets/8e0582e4-465f-4095-ab75-370e03ee30ae)

The tool requires a well-defined URL structure, like the following, to perform the image captures inside a file called clean_urls.txt:

![image](https://github.com/user-attachments/assets/cb96b5ec-14a7-4499-a2b2-d098c531aef5)


To achieve the structure above, we use the following command:

awk '{print "http://10.10.75.87/joomla"$1}' urls.txt  > clean_map.txt 

Now, it is just a matter of granting execution permissions and, of course, running the tool:

![image](https://github.com/user-attachments/assets/94a8d700-00cd-4a1d-98c1-88d8140049e6)

Once finished, a folder named screenshots will be created in the working directory, containing the screenshots:
 
![image](https://github.com/user-attachments/assets/0614baea-0747-4110-be1c-571762e47843)

![image](https://github.com/user-attachments/assets/03cd0b53-c9fb-43a7-a3f9-456cf300730f)

![image](https://github.com/user-attachments/assets/b479d6b8-474a-4e2d-8995-301d369c9a08)


