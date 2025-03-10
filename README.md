## Objective
Hands-on experience with the installation, configuration, and usage of a variety of communication tools and commands, in a Linux environment, using Telnet, FTP, and SSH.

## Skills Learned
- Installation and Configuration of Telnet Server in Linux
- Installation and Configuration of FTP Server in Linux
- Installation and Configuration of SSH Server in Linux
- Network Data Capture and Analysis with Wireshark

## Tools Used
- Linux Command Line (Terminal)
- Telnet
- FTP
- SSH
- Wireshark

## Steps

### Part 1 - Telnet Server Installation and Configuration in Linux
1. Launch both of your Linux virtual machines (Ubuntu and Kali).
2. Open a terminal window on your first Linux machine:
   - `Ctrl + Alt + T`
3. Update and upgrade the repository/package list:
   - `sudo apt-get update`
   - `sudo apt-get upgrade`
4. Install necessary packages:
   - `sudo apt install xinetd`
   - `sudo apt install telnetd`
   - `sudo apt install tcpd`
5. Edit configuration files:
   - `sudo nano /etc/inetd.conf` (Append appropriate script from Appendix I or II)
   - `sudo nano /etc/xinetd.conf` (Append script from Appendix III)
   - `sudo nano /etc/xinetd.d/telnet` (Append appropriate script from Appendix IV or V)
6. Restart and check the xinetd service:
   - `sudo /etc/init.d/xinetd restart`
   - `sudo systemctl status xinetd`
7. Repeat steps 2 through 6 on your other Linux machine.
8. Test the Telnet service:
   - `telnet hostname` or `telnet IP_Address`
   - Use the username and password of the user account of Kali VM to log in.
9. Edit `/etc/hosts.allow` if needed to allow communication:
   - Add the line `ALL : ALL`

### Part 2 - FTP Server Installation and Configuration in Linux
1. Open a terminal window on your first Linux machine.
2. Install vsftpd:
   - `sudo apt install vsftpd`
3. Edit the FTP configuration file:
   - `sudo nano /etc/vsftpd.conf`
   - Ensure the following lines are enabled:
     - `anonymous_enable=NO`
     - `local_enable=YES`
     - `write_enable=YES`
     - `chroot_local_user=NO`
4. Restart the vsftpd service:
   - `sudo systemctl restart vsftpd`
5. Repeat steps 2 through 4 on your other Linux machine.
6. Create and transfer files using FTP:
   - `sudo ftp IP_Address`
   - Use `put` and `get` commands to upload and download files.

### Part 3 - SSH Server Installation and Configuration in Linux
1. Open a terminal window on your Ubuntu VM.
2. Install and start the SSH server:
   - `sudo apt install openssh-server`
   - `sudo systemctl restart ssh`
   - `sudo systemctl status ssh`
3. Switch to your Kali VM and install SSH:
   - `sudo apt install ssh`
4. Connect using SSH:
   - `ssh username@IP_Address`
   - Use the username and IP address of the server virtual machine (Ubuntu VM).
   - Type `yes` to continue connecting and enter the password for the Ubuntu VM.

### Part 4 - Network Data Capture with Wireshark
1. Open Wireshark on your Kali machine.
2. Capture traffic on `eth0`:
   - Connect and log in remotely to the Ubuntu VM using Telnet or FTP.
3. Stop traffic capture and analyze data:
   - Use display filters to search for specific data such as passwords.
4. Repeat the capture process with an SSH session and compare observations.

### Resources
- [Xinetd Explained](https://www.comparitech.com/net-admin/xinetd-primer/#:~:text=Xinetd%20is%20the%20eXtended%20Internet,Unix%2C%20Linux%2C%20and%20macOS)
- [Telnet Explained](https://www.techtarget.com/searchnetworking/definition/Telnet#:~:text=Telnet%20is%20a%20network%20protocol,protocol%20for%20creating%20remote%20sessions)
- [Install and Enable a Telnet server in Ubuntu Linux](http://ubuntuguide.net/install-and-enable-telnet-server-in-ubuntu-linux)
- [FTP Explained](https://www.geeksforgeeks.org/file-transfer-protocol-ftp/)
- [How To Install an FTP Server on Ubuntu With Vsftpd](https://phoenixnap.com/kb/install-ftp-server-on-ubuntu-vsftpd)
- [How to use ftp on Linux](https://www.howtogeek.com/412626/how-to-use-the-ftp-command-on-linux/)
- [How to Enable SSH on Ubuntu](https://www.linuxcapable.com/how-to-install-and-enable-openssh-on-ubuntu-linux/)
