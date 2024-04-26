# Metasploit-for-reconnaissance
# Metasploit

Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting.

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT

Find out the ip address of the attackers system

### OUTPUT:

![exp5_1](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/da9153e0-7145-419d-9546-17c14b1846a8)

Invoke msfconsole:

![exp5_2](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/afa35744-c174-48f3-aab8-3e90b84a1cdb)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![exp_5_3](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/7fd8d245-b7e5-418d-9d73-10d8a91cec69)


#### Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

### OUTPUT:

![exp5_4](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/0588f78b-2f1d-4a81-952c-54dc60a7f87f)


step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

### OUTPUT:


![exp5_5](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/e608e4a1-02ac-4842-a853-d8aac68efb5a)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

### OUTPUT:

![exp5_6](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/4f27edbe-6afb-486b-a230-20b48a1385e6)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit


![exp5_7](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/af85432d-2f84-48d2-935b-bb78ffd19099)


The info command provides information regarding a module or platform,

### OUTPUT

![exp5_8](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/69c98da0-d9fb-43b9-98fe-18717333bb8a)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

#### MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![exp5_9](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/c1c4ccb2-dbb8-4912-bd2b-9ac30e1da767)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![exp5_10](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/e784e3f5-895a-4e4c-95f0-9fa78e2f7da3)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version

![exp5_11](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/2094adac-a1f8-4fed-881d-953cbdf79fbf)


Use the set rhosts command to set the parameter and run the module, as follows:


![exp5_12](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/27ba02a6-5bbf-4614-acfe-0254fa984e0b)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![exp5_13](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/67d33875-13fb-4a92-b4f0-651121460db7)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

![exp5_14](https://github.com/Skanthasishanth/Metasploit-for-reconnaissance/assets/118298456/2ab5797b-726d-4594-b2cc-efa191091417)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
