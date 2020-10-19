# How to enable SSH on Raspberry Pi using Linux
SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network. In addition to providing secure network services, SSH refers to the suite of utilities that implement the SSH protocol. Secure Shell provides strong password authentication and public key authentication, as well as encrypted data communications between two computers connecting over an open network, such as the internet. In addition to providing strong encryption, SSH is widely used by network administrators for managing systems and applications remotely, enabling them to log in to another computer over a network, execute commands and move files from one computer to another. 

Now,
To have a full Raspberry Pi experience, you should use Raspbian, the OS developed exclusively for Raspberry Pi. Raspbian is a Debian-based system optimized to utilize Raspberry Pi hardware most efficiently. If you want to transfer data or administer the device remotely via SSH, you need to enable SSH first.

Follow the steps in this guide to learn how to enable SSH on Raspberry Pi without a screen, from the GUI, or using the raspi-config file. I will also show you how to find the IP address of your Raspberry Pi and how to SSH into the device.

# Prerequisites
* Raspberry Pi with Raspbian installed
* Access to a computer with a microSD or SD card reader (for pre-2014 Raspberry Pi versions)
* Necessary admin permissions to perform the tasks
* Access to an SSH client: PuTTy in Windows or Terminal in Linux/macOS

# How to Enable SSH on Raspberry Pi
If you installed any of the Raspbian versions from late 2016 onwards, then SSH is disabled by default. The reason behind this decision was to improve security. Since all Raspbian images come with a user “pi” and the default password “raspberry,” it was easy for rogue pentesters to use this in their favor.

However, you can easily enable SSH on Raspberry Pi even if you do not have a monitor and keyboard connected. I will explain three possible ways to enable SSH on Raspbian. Read through the process and choose the method that you prefer.

# Enable SSH on Raspberry Pi in Headless Mode
Many users run these devices as a web or media server and configure them via SSH. If you use your Raspberry Pi without a monitor and keyboard, then the only way to enable SSH in headless mode is to use a blank boot file.
For this task, you need to create an empty ssh file on another machine. We will use this file on the Raspbian boot SD card to enable SSH. If you do not feel like creating the file yourself, we made the blank ssh boot file available for download.

# To enable SSH on Raspberry Pi in headless mode, follow these steps:

1. Make sure you properly installed Raspbian on your Raspberry Pi microSD card. If you have already done so, turn off the device and remove the card.

2. Put the microSD card in the card reader of your computer. Wait until the card mounts. You may need to use a microSD to SD card adapter. All recent Raspberry Pi versions use microSD instead of standard-size SD cards.

3. Navigate to the boot folder. This is the root folder of your SD card. Boot is the default volume name when you install a Raspbian system on an SD card. If you are on a Windows machine, use any file manager, such as Explorer. On macOS or Linux, open a terminal window and type:

       cd /Volumes/boot

Note that the name of your SD card can be something other than “boot”. If it is, open the root volume folder and proceed with the next steps.

4. In the boot volume, create a file without an extension and name it ssh.

* On Windows, right-click anywhere in the boot volume’s white space and select New > Text Document. Delete the .txt extension before you hit Enter. If Windows Explorer on your computer does not show file extensions, click View and enable File name extensions in the menu bar.

* On Mac or Linux, run the touch command while in the boot directory to create a blank ssh file:
touch shh

5. Safely remove or eject the card from the computer and insert it again in your Raspberry Pi.

6. Boot up Raspberry Pi.

Every time you turn on the Pi board, the device looks for the ssh file. When the device finds the file, then SSH is enabled automatically. If you correctly created an empty ssh file without an extension, you can now SSH into your device.

# Enable SSH on Raspberry Pi using GUI Configuration Options
Things get much faster and easier when you have a monitor and peripherals connected to your Raspberry Pi. If you are used to configuring your device using a GUI, follow the steps below.

Once your device boots up:

1. Click the raspberry logo at the top-left corner.

2. Select Preferences > Raspberry Pi Configuration.

3. Navigate to the Interfaces tab in the configuration window.

4. Enable SSH in the second line.

5. Click OK to save the changes.

That’s it. Your Raspberry Pi is now accessible via SSH. Make sure the device is connected to the internet before trying to establish an SSH session.

# Enable SSH on Raspberry Pi in the Terminal
If you are used to configuring your system from the terminal, you can choose one of the two options below.

Enabling SSH with raspi-config
To enable SSH using the raspi-config tool:

1. Open the terminal on your Raspberry Pi and run the tool by typing:

    sudo raspi-config

A BIOS-looking raspi-config tool loads.

2. Use the arrows on your keyboard to select Interfacing Options.

3. Select the P2 SSH option on the list.

4. Select <Yes> on the “Would you like the SSH server to be enabled?” prompt.

5. Hit Enter on the “The SSH server is enabled” confirmation box.

6. Navigate down and select Finish to close the raspi-config.

You can close the terminal window. Your device is now ready to accept SSH connections.

# Use systemctl to Enable SSH
The final option to enable SSH on Raspberry Pi is to start the systemctl service from your terminal.

To do so, load the terminal and run these two commands:

     sudo systemctl enable ssh
     sudo systemctl start ssh
  
The ssh service is now both enabled and started.

# How to SSH Into Raspberry Pi
Find IP Address of your Raspberry Pi
Now that you enabled SSH on your Raspberry Pi, you can use SSH to connect from another machine.

Before we can continue, you need to find the IP address of your device. While you are logged in the Raspbian system, open the terminal and run this command:

      hostname -l
  
Alternatively, you can run theifconfig or ip a command to find the IP address. We prefer using the hostname command as it only displays the address without other network information.

Use the Terminal in macOS or Linux to Connect to Raspberry Pi
Using SSH to remotely manage a Raspberry Pi device is the same as managing any other Linux-based machine. Both macOS and Linux have SSH clients by default.

To connect via SSH to your Raspberry Pi from the terminal, use this command:

       ssh pi@[raspberrypi_ip_address]
  
 # Note: 
 Pi is the default user account. If you use another account name, type it in instead of Pi. Use your device's IP address identified in the previous step.
 The first time you connect to your Raspberry Pi, you will get a prompt to accept the RSA key. Type yes, and the new SSH session starts.

# Use PuTTy in Windows to Connect to Raspberry Pi
Windows users can SSH into Raspberry Pi using PuTTY.

Start the tool and enter the IP address of your device. Make sure SSH is selected, and the port set to 22.
Click Open to start a new session. Enter your Raspberry Pi’s account username and password.

# Securing Raspberry Pi SSH
In November 2016, SSH was disabled by default on Raspbian. This move was made to prevent Raspberry Pi devices from potentially becoming a part of an IoT botnet.

Now that you have decided to use SSH to connect to your Raspberry Pi, we advise you to change the default account password.

Since all Raspbian installations come with a default account and password, it is easy for hackers to log into your device. To make your device less vulnerable, change Raspberry Pi’s default password.

1. To do so, run the raspi-config tool from the terminal on your device:

       sudo raspi-config
  
2. Select the Change User Password option.
Follow the instructions to change the password. Your Raspberry Pi is now ready and more secure for SSH access.

# Conclusion
Now you know how to enable SSH on Raspberry Pi. This tutorial has shown you how to enable the service even if you do not have a monitor and keyboard connected to your Raspberry Pi. If you have the peripherals connected, then you can choose the method that suits you best.



