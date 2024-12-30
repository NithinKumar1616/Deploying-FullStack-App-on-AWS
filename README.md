In this project, I successfully deployed a full-stack application on AWS EC2 instances by setting up the frontend, backend, and database services. The backend was developed in Node.js, the frontend in React.js, and the database was managed using MySQL. Below, I have outlined the detailed steps I followed to deploy the website, making it accessible over the internet.

Step 1: Setting Up the Database

* Create an EC2 Instance for MySQL (database)
* Installed MySQL in the instance.

Verify MySQL is Running:

* Checked the MySQL process using: ps -ef | grep mysql
* Confirmed the ports were open with: netstat -lnt

Changed the default root password in order to start using the database service.
Verified the MySQL server was operational and ready for the next steps.

Step 2: Setting Up the Backend (Node.js Application)

* Create an EC2 Instance for the Application Server
* Install Node.js v20:

Disabled the default Node.js version (v16) and installed v20

Prepare the Application Environment:

* Created a dedicated directory for the application and added a new user to run the application.
* Downloaded the (zipped)application code in temp folder and unzipped it in the /app directory
* Navigated to the application directory and installed dependencies

Setup Systemd Service for the Application:

* Created a systemd service file to manage the application
* Enabled and started the service:

Note: The backend service does not start running immediately after creating the service (even though we restart the service). It requires installing the MySQL client and loading the schema first.

Setup Database Schema:

* Installed the MySQL client on the application server and loaded the schema into the database
* Restart the service now and verified that application is running

Step 3: Setting Up the Frontend (React.js Application)

* Created the EC2 Instance for the Frontend.
* Installed Nginx on the server.
* Verified that the Nginx server is running by accessing the ip address/hostname in the browser.
* Removed the default content from /usr/share/nginx/html/*
* Downloaded the zipped frontend code in temp folder and unzipped it in /usr/share/nginx/html/ after removing the default content.
* Configured Nginx as a Reverse Proxy by Editing the Nginx configuration file to route requests to the backend
* Restarted Nginx service

Verified Application Accessibility by accessing it through browser over the internet.

Conclusion

By following the steps above, I successfully deployed a full-stack application using AWS EC2 instances. The backend, frontend, and database were interconnected through private IPs / hostnames, ensuring secure communication. The application is now live and accessible via the public IP of the frontend server.
