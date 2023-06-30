# 2-Tier Architecture in Azure

## Introduction
The 2-tier architecture is a commonly used approach for designing scalable and secure application infrastructures. In Azure, this architecture involves dividing the application into two layers: the application layer and the database layer.

```scss
         ┌───────────────────────────────┐      
         │           Subnet              │      
         │                               │      
         │    ┌───────────────────────┐  │      
         │    │    Virtual Machine    │  │      
         │    │                       │  │      
         │    │   Application Layer   │  │      
         │    │                       │  │      
         │    └───────────────────────┘  │      
         │                               │      
         │    ┌───────────────────────┐  │      
         │    │    Virtual Machine    │  │      
         │    │                       │  │      
         │    │    Database Layer     │  │      
         │    │                       │  │      
         │    └───────────────────────┘  │      
         │                               │      
         └───────────────────────────────┘      
                       │                          
    Network Interface Controller                
                       │                          
            ┌──────────┴──────────┐               
            │                     │               
    Network Security Group        │               
            │                     │               
   (NSG Rules: SSH, HTTP)         │               
            │                     │               
     ┌──────┴─────┐     ┌─────────┴────────┐      
     │  Public IP │     │        HTTP      │      
     └────────────┘     └──────────────────┘      
        (Inbound)          (Inbound)

```

## Application Layer
- Consists of virtual machines (VMs) that host and run the application.
- VMs reside in a subnet, providing a secure network environment.
- Each VM has a network interface controller (NIC) to connect to the internet and allow user access.
- Network Security Groups (NSGs) define rules to control access to the VMs, such as allowing SSH and HTTP access.
- A public IP address is assigned to the application layer to enable external access.

## Database Layer
- Includes a dedicated VM for running the database.
- Handles storage and retrieval of data for the application.
- Inbound rules are set up to control access to the database and ensure data security.

## Benefits of 2-Tier Architecture
- Scalability: Each layer can be scaled independently based on requirements. More VMs can be added to the application layer or more resources allocated to the database layer.
- Security: Separating the application and database layers minimizes the risk of unauthorized access to data.
- Reliability: The architecture allows for redundancy and high availability, reducing the chances of downtime.

## Conclusion
The 2-tier architecture in Azure provides a scalable and secure infrastructure for applications. By separating the application and database layers, organizations can ensure optimal performance, security, and reliability.

Remember to showcase the diagram during your presentation to provide a visual representation of the architecture.

# Automation L1 - Start the Sparta app with a script (no database)

The Bash script below sets up everything needed to run the Sparta app on a fresh Ubuntu 18.04 LTS VM, including installing dependencies, configuring Nginx, and starting the app.

```bash
#!/bin/bash

# update source list
sudo apt update -y

# upgrade all the packages and installs them in the kernal
sudo apt upgrade -y

# install nginx
sudo apt install nginx -y

# Start nginx on boot
sudo systemctl enable nginx

# start nginx
sudo systemctl start nginx

# restart nginx
sudo systemctl restart nginx

# enable nginx - auto runs on startup
sudo systemctl enable nginx

# download node js
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

# install node js
sudo apt install nodejs -y

export DB_HOST=<database_vm_ip>:<database_vm_port>/posts

# update source list
sudo apt update -y

# install pm2
sudo npm install -g pm2

# git clone app
git clone https://github.com/jungjinggg/tech241_sparta_app app-github-automation

# get into app folder
cd ~/app-github-automation/app

# install node js inside folder
npm install -y

# start app
pm2 start app.js --name "sparta app"
```
# Start the Sparta app 

The provided script automates the setup and execution of a web application on a fresh Ubuntu 18.04 LTS VM. The script performs the following steps:

1. Update package sources and upgrade all packages.
2. Install Nginx, a web server that serves the application to clients.
3. Enable and start Nginx.
4. Download and install Node.js version 12.x.
5. Update package sources again.
6. Install PM2, a process manager for Node.js applications.
7. Clone the application from a GitHub repository.
8. Navigate to the application folder.
9. Install the application's Node.js dependencies.
10. Start the application using PM2.

Please note that the script assumes a fresh Ubuntu 18.04 LTS VM and may require appropriate permissions to run certain commands.

Remember to showcase the markdown file during your presentation to explain the steps involved in automating the setup and execution of the Sparta app.
## DB script 

The script performs the following steps::

1. Update and upgrade the Linux VM::

    ```
    sudo apt update -y
    sudo apt upgrade -y
    ```

2. Install MongoDB:

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
sudo apt update -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

```
Retrieve the public GPG key for MongoDB version 3.2.x:

- `wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -` retrieves the public GPG key for MongoDB version 3.2.x and adds it to the system's keyring.
The GPG key is used to verify the authenticity of the MongoDB packages during installation.
Add the MongoDB repository to the package manager's sources list:

- `echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list` adds a new repository file named mongodb-org-3.2.list to the /etc/apt/sources.list.d/ directory.
The repository URL specifies the MongoDB version (3.2) and the Ubuntu distribution (xenial) to fetch the appropriate MongoDB packages.


Update the package lists to include the MongoDB repository:

- `sudo apt update -y` updates the package lists, including the newly added MongoDB repository.
This ensures that the system is aware of the MongoDB packages available for installation.
Install the specified versions of MongoDB and its related components:

- `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20` installs the specific versions of MongoDB components.
The package names are provided with their respective versions to ensure the installation of MongoDB version 3.2.20 and its associated tools.

3. Configure MongoDB to accept connections from any IP address:

    ```
    sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf
    ```

   The `sed` command modifies the `/etc/mongod.conf` file, replacing the line `bindIp: 127.0.0.1` with `bindIp: 0.0.0.0`. This change allows MongoDB to accept connections from any IP address, enabling communication with the app VM.
Configure MongoDB to accept connections from the app VM:

`sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf` modifies the `/etc/mongod.conf` file using the sed command.
The sed command substitutes the IP address 127.0.0.1 (which restricts connections to localhost) with 0.0.0.0 (which allows connections from any IP address). This change enables MongoDB to accept connections from any IP address.
4. Start and enable MongoDB:

    ```
    sudo systemctl start mongod
    sudo systemctl enable mongod
    ```

   These commands start MongoDB and configure it to start automatically on boot.
