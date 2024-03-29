## Integrated Knowledge Article Suggestion Application

IKASA is a web application designed to improve incident/task resolution efficiency.
Web API's are used to integrate service management tools enabling intelligent suggestions for knowledge articles based on the content of a service request.
Suggestions are calculated using the 'all-MiniLM-L12-v2' pre-trained model to calculate a similarity figure.

Technology stack:
• Python 
• Flask (Web server) 
• Jinja2 (Template engine) 
• Pandas (Data analysis) 
• SQL Alchemy 
• Sentence transformers 
• SciPy 
 
Supported browsers 
Chrome  v93.00 + 
Firefox  v78.15 + 
Edge  v92.00 + 
Safari  v14.10 + 

Install notes
--------------------------------------------------------------------
1.  'sudo su'
2.  'cd $home'
3.  Install python 3.9
4.  Install pip3
5.  Install apache2
6.  Install libapache2-mod-wsgi
7.  'git clone https://github.com/christopher-aldred/IKASA.git'
8.  'cd IKASA'
9.  'pip3 install -r requirements.txt'
10. 'chmod a+x main.py'
11. Port forward port 80 and 443 (Local ip tables and egress rules)
12. 'chmod -R 755 /root/IKASA/uploads'
13. 'chown root:root /root/IKASA/uploads'
14. Edit main.py to user waitress server not default app.run
15. Create ikasa.service @ /etc/systemd/system/ (Details below)
16. 'systemctl start ikasa.service'
17. 'systemctl enable ikasa.service'

Errors you may encounter
--------------------------------------------------------------------
Tokenizer error... install Rust compiler: curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

Cant bind to port 80... All steps above should be done as sudo user


Usefull commands
--------------------------------------------------------------------
iptables -I INPUT 5 -i ens3 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
netfilter-persistent save
pkill main


launcher.sh
--------------------------------------------------------------------
#!/bin/sh
cd /root/IKASA/
./main.py
