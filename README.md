#	💻 IT Support Lab 💻

---

<h3>+ Introduction</h3>

This lab is a guide towards simulating a corporate network on a smaller scale with primary focus over the responsibilities of an IT support professional.

IT support
: IT support is about offering assistance to employees and the wider organization for technology-related issues. Its purpose is to provide users with answers to problems they may be experiencing. In a business environment, IT support can also encompass the setup, installation, and configuration of equipment, plus much more.

<h3>+ Prerequisites</h3>

- Windows 2016 or 2019 Server ISO Image
- Windows 2010 Pro / Enterprise ISO Image
- Hypervisor [Type 2 - https://www.virtualbox.org/wiki/Downloads]

<h3>+ Installation and Configuration</h3>

- Skipping intricate details 

    1. Setting up Windows Server [ADDC]
    2. Connecting Windows 10 Workstation to the Domain

---
### + User Management

---
### + Creating Share Drives

> **Scenario #1** - You are a network tech, assigned to create a shared folder with the name 'supportTeam' accessible only to the tech support team.


1. Logon to the DC, open `Server Manager` and click on `File and Storage Services`.
    
    ![alt text](./Network%20drives/1.png)
<br>

2. Click on `Shares`, Right click in the area showing existing shared drives and select `New Share`.

    ![alt text](./Network%20drives/2.png)
<br>

3. After the `New Share Wizard` opens, leave the `Select profile` option with its default value; move on to `Share Location` and change the default path if needed *(for familiarity purposes, the path in this lab is kept /shares by default)*

<br>

4. Type the name for your shared drive, its description and a custom path, if needed.

    ![alt text](./Network%20drives/3.png)

    Local path to share
    : The tool uses the local file system to store files and folders downloaded from the Design Time Repository (DTR) server. The path where a file or folder from the server is stored in the local file system, is the local path

    Remote path to share
    : Each file and folder on the server is exposed through a HTTP URL. The part of the URL after the host name, and possibly the port number, is called the remote path.

5. Keep clicking next (Yes, even on permissions as they will be done later) until you reach *Confirmation*. Click `Create`.

    ![alt text](./Network%20drives/4.png)
<br>

6. Go to the path **C:\Shares** to confirm the drive creation. Right-click on the folder created, click on `Properties` and select `Security`. This will show the current (and default) permissions allocated to our shared drive. 

    ![alt text](./Network%20drives/5.png)
<br>

7. Click on `Advanced` > `Disable Inheritance` and select the first option. This option will basically allow default, existing permissions to be edited.

    ![alt text](./Network%20drives/6.png)

<br>

8. Remove =='ECORP\Users'== from the permissions. Click on `Add` > `Select Principal` and search for the group that contains all the tech support employees, and click on 'OK'. In the basic permissions section, make sure to select `Full Control` in order to allow all group members to read and write into the said drive.

    ![alt text](./Network%20drives/7.png)
    ![alt text](./Network%20drives/8.png)
<br>

9. Now, only domain administrators and users of the security group 'Tech Support' will be able to access this shared drive. To verify this, login as one of the tech support users, open File Explorer > *Network* from the left-hand side, open the drive with the DC's name to see the shared folder.

    ![alt text](./Network%20drives/9.png)
    ![alt text](./Network%20drives/10.png)

10. Additionally, the other way to do this is to open File Explorer and directly type the network path in the address bar `\\ECORP-ADDS\supportTeam`. 

<br>

<h3>> **Scenario #2** -  You have successfully created the shared drive for a particular group. You have been asked to make the drive easily accessible for users with less IT knowledge or simply to reduce the steps required to access the drive.</h3>

1. Login to a Domain Admin account and go to Active Directory Users and Computers. Right-click on the target user, select `Properties` and click on `Profile`. In the ==Home Folder== Option, select `Connect`. Now select any volume name and add the **network path** of the shared drive in the address. Click 'Apply' and 'OK'. Ignore the warning if received.

    ![alt text](./Network%20drives/11.png)
<br>

2. Login to the target user's account and go to 'This PC'.
    ![alt text](./Network%20drives/12.png)


---

### + References

 - [Definitions of Local and Remote path](http://saphelp.ucc.ovgu.de/NW750/EN/49/101bee3d9d132ee10000000a421937/content.htm#:~:text=The%20path%20where%20a%20file,system%2C%20is%20the%20local%20path.&text=Each%20file%20and%20folder%20on,is%20called%20the%20remote%20path.)

 - [Creating share drives - Scenario #1 and #2](https://www.youtube.com/watch?v=FOZ9IxsOtOE)
     
<br>
<br>
<br>









