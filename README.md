# ODICS data movement to Autonomous Database from PostgreSQL

## Objective

This documents shows you how to move data from PostgreSQL to Autonomous Data Ware House on Oracle Cloud

## Pre-requisites

- The following lab requires an Oracle Public Cloud account with Autonomous Data Warehouse Cloud Service and Java Cloud Service.

- You need to have a connection to database through admin in your SQL Developer.

    - Open up your SQL Developer and create a new connection for admin. If you already have a connection, skip this step.

    - Enter the following details for admin:

        1.	Connection Name: Give any connection name
        2.	Username: admin (or any DB user)
        3.	Password: Password you entered while creating database on cloud.
        4.	Connection Type: Cloud PDB
        5.	Configuration File: Path to your wallet
        6.	Keystore Password: Password entered while downloading wallet.

        ![](Data/login.png)

    - Click on Test, if it shows success, click on save and then click on connect.

- You need to have a connection to PostgreSQL database through pgAdmin.
  If it's not, download and follow the instructions in this file. [Install pgAdmin](https://www.pgadmin.org/download/)

### **Step 1**: Install PostgreSQL on Oracle Compute.

- Login to Oracle cloud.

    1. Click on **Left Hamburger menu** and then select **compute**.

    2. Deploy a **linux instance** and take note of **IP address**.

    3. SSH in to your linux server.
    
          **ssh -i PrivateKey opc@IPaddress**

- Follow this link to install PostgreSQL on Oracle Compute. [Installation of PostgreSQL](https://www.postgresql.org/download/linux/redhat/)

### **Step 2**: Download and configure the script.

- Download the following script [app.py](app.py)

- Open this script and change the following parameter in the code:

    **username = "Your username"  
    password = "Your password"  
    service_name = "Your service name"**

- now run the script as **python app.py**


### **Step 3**: Run the application.

- Set environment variable "FLASK_APP" to the path of the app.py

  **export FLASK_APP=path to app.py**

- Type following command in command line:

  **flask run --host=0.0.0.0 --port=5000**

- Now open any web browser and type **"localhost:5000/channels"**

  You will see channels information on the browser.

  You can also deploy this application in a compute instance and can use the REST API in SaaS Applications.
