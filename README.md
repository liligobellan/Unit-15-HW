### Week 15 Homework: Web Vulnerabilities and Hardening Homework
To launch the environment, complete the following:


-Launch Vagrant from GitBash or the Mac terminal using the following command: vagrant up


-Then, open the command line inside Vagrant and run the following command: cd ./Documents/web-vulns && docker-compose up.


-Leave this page open and continue to the next step.


-To access the Replicants website, open a web browser within Vagrant and access the following webpage: http://192.168.13.25/setup.php.


-On the bottom of this page, click Create / Reset Database.


-This will configure the database for the application.


-The message "Setup Successful" at the bottom of the page will indicate that it is complete.


-To log in to the mock Replicants website, access the following webpage: http://192.168.13.25/login.php.


-Log in with the following credentials:


- Username:`admin`


- Password: `password`


Now that you have determined that Replicants new application is vulnerable to command injection, you are tasked with using the dot-dot-slash method to design two payloads that will display the contents of the following files:

- `etc/passwd`

![etc/passwd image] 
