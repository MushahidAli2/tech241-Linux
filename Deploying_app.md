# Deployment Guide

Before proceeding with the deployment, it is essential to update and upgrade the system.

To set up a web server, we will utilize Nginx. Ensure that Git is installed on your system if it is not already.

To install an older version of Node.js, execute the following command:

```bash
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
```

Please note that this command installs a deprecated version of Node.js that is no longer officially supported.

To install Node.js, use the following command:
```bash
sudo apt install nodejs -y
```
Additionally, install the Node Package Manager (npm) globally by running:
```bash
sudo npm install pm2 -g
```
PM2 is a process manager that allows running Node.js applications in the background.

To set up the application directory, navigate to the app directory and execute:
```bash
npm install
```
Please ensure that Nginx is running before running this command.

To start the application, either run `npm start` or `node app.js`. The application will listen on port 3000.

To allow incoming traffic on port 3000, follow these steps in the Azure portal:
1. Go to the Networking tab.
2. Add an inbound security rule.
3. Set the port to 3000 and the protocol to TCP.
4. Save the rule.

To exit from the listening mode, use `Ctrl+C`. Note that this is a more forceful termination than `Ctrl+Z`, which suspends the process and allows it to run in the background.

To completely terminate the process, use the command `kill -1`. Remember that only one service can use a port at a time.

## Setting up the Database VM

To configure the database, follow these steps on a Linux VM running Ubuntu 18.04 LTS:
1. Update and upgrade the system.
2. Install MongoDB version 3.2.x.
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
```
: This command uses wget to download the GPG key (server-3.2.asc) from the specified URL. The key is then passed to apt-key add with the - option, which adds the key to the system's keyring. This is typically done to verify the authenticity of packages during installation.
3. Download the key to obtain the correct version.
```bash
 echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
 ```
: This command uses echo to write the specified line into a file called mongodb-org-3.2.list in the /etc/apt/sources.list.d/ directory. This line adds a package repository URL for MongoDB to the system's package sources. It indicates the location from where apt can download MongoDB packages.


5. Specify the MongoDB version in the source list.
5. Update again.
```bash 
sudo apt update -y
```
6. Install MongoDB using the specified version.
```bash
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
```
: This command uses apt-get to install specific versions (3.2.20) of the MongoDB packages mentioned. It installs the MongoDB server, shell, mongos (sharding router), and other tools. The -y option automatically answers "yes" to any prompts during the installation process.

8. Configure MongoDB to accept connections from the app VM by editing the `/etc/mongod.conf` file. Change the bind IP from `127.0.0.1` to `0.0.0.0` to allow connections from outside. Please note that this configuration is for testing purposes only.

To check the status, start, and enable MongoDB, use the following commands:
```bash
sudo systemctl status mongod
sudo systemctl start mongod
sudo systemctl enable mongod
```

## Connecting the App and Database

On the app virtual machine, set up the environment variable as follows:
```bash
export DB_HOST=mongodb://<DB-IP-ADDRESS>:27017/posts
```
Make sure to replace `<DB-IP-ADDRESS>` with the actual IP address of the MongoDB server.

After setting the environment variable, run `npm install`.

To enable connectivity between the app and the database, add an inbound rule in the networking configuration, allowing traffic on port 27017.

Please note that the provided instructions assume prior knowledge of the setup process. Make sure to consult relevant documentation and adapt the steps to your specific requirements.
