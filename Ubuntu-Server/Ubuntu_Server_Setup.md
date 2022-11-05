<h1 style="text-align:center;color:#FF8C00">Ubuntu Server Setup</h1>

## Table of Contents

[Port Forwarding](#port-forwarding)
[]()
[]()
[]()

## Port Forwarding

    Step 1. Gateway: 192.168.x.x
    Step 2. Forward Port 22 Internally & Externally
    Step 3. Application is SSH
    Step 4. Device IP should be static so the IP never changes

### Finding the Default Gateway

Find your default gateway may be a bit tricky if you're not to 'network' savvy, but it's actually a lot easier than you would think. With one quick command, we get all of the information we need.

```bash
route -n

Output:
Kernel IP routing table
Destination     Gateway     Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp5s0
```

>**_NOTE:_** Your output will be different than mine

## Enable & Configure Firewall

```bash 
sudo nano .bashrc
```

Install UFW

```bash  
sudo apt install ufw
```

Allow Outgoing Traffic

```bash 
sudo ufw default allow outgoing
```
Deny Incoming Traffic

```bash  
sudo ufw default deny incoming
```

Configure Rule

```bash
sudo ufw allow <portnumber>/tcp comment 'SSH'
```

Allow HTTP Traffic

```bash
sudo ufw 
```

Allow HTTPS Traffic

    Test




## Generate & Store SSH Key

Key Generation

```bash
ssh-keygen -t rsa -b 4096
```

Move File from Host to Server Using SSH

```bash
scp -P <sshport> <publickeypath>@<user@<serverip>:<.sshfolderpath>

ex: scp -P 234 ~/.ssh/id_rsa.pub mike@192.168.0.134:/home/mike/.ssh
```

**Add Public Key from Host to Server by Adding Your Public Key to the Authorized Keys List in the "~/.ssh/authorized keys"**

<h2 style="text-align:center;color:#FF8C00">Install & Configure Apache2</h2>

Installing Apache2

```bash
sudo nala udpate && sudo nala upgrade -y
sudo nala install apache2 -y
```

<h2 style="text-align:center;color:#FF8C00">Install & Configure MySql-Server</h2>

Installing MySql-Server

```bash
sudo nala udpate && sudo nala upgrade -y
sudo nala install mysql-server -y
```

Starting the MySQL Secure Installation 

```bash
sudo mysql_secure_installation
```
* **Say no to password validation**
* **Say yes to remove anonymous user**
* **Say yes to remove remoting**
* **Say yes to reload**
* **If you said yes to password validation and get stuck in a loop, follow the below steps**
  1. Kill the mysql process or restart the server
  2. ```sudo mysql```
  3. ```ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';```
  4. ```sudo mysql_secure_installation```