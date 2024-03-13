# Getting Started with Tenstorrent Grayskull e150 Accelerator
To start using the Tenstorrent Grayskull™ e150 Accelerator, follow these steps:
1. **Download and Install CADPass:**
   Download [CADPass](https://www.cmc.ca/cadpass/) from the provided link and install it on your system.
   
2. **Login to CADPass:**
   Use your CMC microsystems credentials to log in to CADPass. After logging in, you will see the following window:
   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/0.png)
   
3. **Obtain AI Jupyter Tenstorrent Shortcut Details:**
   Right-click on AI Jupyter Tenstorrent and select "Shortcut details" as shown in the following figure:

   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/12.png)
   
4. **Find the Server IP Address:**
   In the shortcut details window, you will find the IP address of the server. In this case, the IP address of the server is 172.16.60.18

   ![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/3.png)
   
6. **SSH to the Server:**
   Use the obtained IP address to SSH into the server using the following command:
   ```
   ssh username@172.16.60.18                     
   ```
7. **Check Available Accelerators:**
Once connected to the server, type the following command to see available accelerator cards in the system:
   ```
   lspci | grep accelerator
   ```
The output of this command will display the available accelerator cards, such as:
   ```
   yassine@tenstorrent:~$ lspci | grep accelerator
b1:00.0 Processing accelerators: Device 1e52:faca
ca:00.0 Processing accelerators: Device 1e52:faca
   ```
8. **Activate the virtual environment:**
``` 
yassine@tenstorrent:~$ source /CMC/tt/bin/activate
(tt) yassine@tenstorrent:~$
```
10. run TT-SMI
```
(tt) yassine@tenstorrent:~$ tt-smi
```

![Image Alt Text](https://github.com/cmcmicrosystems/Tenstorrent-Grayskull-e150-Accelerator/blob/main/images/4.png)

12. copy examples to your home directory
```
cp -rf /CMC/tt-buda-demos/ .
```
13. run resnet
``` 
cd /home/yassine/tt-buda-demos/model_demos/cv_demos/resnet
python pytorch_resnet.py
```
15. 
16. 

