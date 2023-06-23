# How to Get the 'app' Folder onto the Azure VM

There are two ways to copy the 'app' folder onto the Azure Linux VM. You can choose the method that suits your requirements best:

## Method 1: Using SSH and `scp`

1. Ensure you have SSH credentials for your Azure Linux VM.
2. Open a terminal or command prompt on your local computer.
3. Navigate to the directory where the 'app' folder is located.
4. Use the `scp` command to securely copy the 'app' folder to the Azure VM:
   ```bash
   scp -r app/ username@azure-vm-ip-address:/home/username/
Replace app/ with the correct path to the 'app' folder on your local computer. Replace username with your Azure VM username and azure-vm-ip-address with the IP address of your Azure VM.
5. Enter your SSH password when prompted.

Wait for the 'app' folder to be copied to the Azure VM.

## Method 2: Using GitHub and git clone

1. Create a GitHub repository called 'tech241-sparta-app'.
2. Initialize a Git repository in the 'app' folder on your local computer if you haven't already

```bash
cd /path/to/app/
git init
```
3. Add and commit the 'app' folder to the local Git repository
```bash
git add .
git commit -m "Initial commit"
```
4. Add the GitHub repository as a remote:
```bash
git remote add origin https://github.com/your-username/tech241-sparta-app.git

```
Replace your-username with your GitHub username.

5. Push the 'app' folder to the GitHub repository
```bash
git push -u origin master

```
6. Ensure you have SSH credentials for your Azure Linux VM.
7. Open a terminal or command prompt on the Azure VM.
8. Use the git clone command to clone the 'tech241-sparta-app' repository onto the Azure VM:
```bash
git clone https://github.com/your-username/tech241-sparta-app.git

```
Replace your-username with your GitHub username. 
9. Enter your GitHub credentials if prompted.
10. Wait for the repository to be cloned onto the Azure VM.
That's it! You have successfully copied the 'app' folder onto the Azure VM using two different methods.