# Nginx Reverse Proxy

A reverse proxy is a server that sits between client devices and web servers. It receives client requests and forwards them to the appropriate backend server, acting as an intermediary. Unlike a traditional proxy server, which forwards client requests directly to the requested server, a reverse proxy handles the requests on behalf of the server.
## Understanding Ports


In computer networking, a port is a communication endpoint where network connections are established. It acts as a channel for specific types of network traffic. Each service or application running on a server listens on a specific port number to receive incoming requests.
## Reverse Proxy and Proxy

A reverse proxy, as mentioned earlier, distributes client requests to backend servers based on various factors like load balancing, caching, or security. It provides a single entry point for clients to access multiple servers.

On the other hand, a proxy server acts as an intermediary between client devices and web servers. It can be configured to handle requests on behalf of clients, often used for caching or filtering purposes.
## Nginx Default Configuration

Nginx, a popular web server and reverse proxy server, uses a configuration file located in the `sites-available` directory. By default, Nginx is installed with a basic configuration that serves static files. To set up a reverse proxy, additional configuration needs to be added.
## Setting Up Nginx Reverse Proxy

To set up an Nginx reverse proxy, follow these steps:
1. Open the Nginx configuration file:
```bash
 sudo nano /etc/nginx/sites-available/default

```
2. Within the server block, remove the existing configuration and add the following lines:
```nginx
 location / {
    proxy_pass http://backend_server_ip:backend_server_port;
}

```
Replace backend_server_ip and backend_server_port with the IP address and port of your backend server where the actual web application is running.

3. Save and close the file.

4. Test the Nginx configuration for syntax errors:
```bash
 sudo nginx -t

```
5. If the configuration is valid, restart Nginx:
```bash
 sudo systemctl restart nginx

```
Now, Nginx is configured as a reverse proxy and will forward incoming requests to the specified backend server based on the defined location.

Below is a diagram illustrating the flow of requests when using an Nginx reverse proxy:
```lua
          +-------------------+
          |                   |
    +----->   Nginx (Reverse   |
    |     |    Proxy Server)   |
    |     |                   |
    |     +-------------------+
    |
    |     +-------------------+
    |     |                   |
    +----->   Backend Server   |
          |                   |
          +-------------------+

```
## task1
## Setting Up a Reverse Proxy for the Sparta App

### Prerequisites

    Ubuntu 18.04 LTS
    Nginx installed on the app VM
### Steps

1. Install Nginx by running the following commands:
```bash
sudo apt update
sudo apt install nginx
 
```
2. Open the Nginx default configuration file for editing:
```bash 
 sudo nano /etc/nginx/sites-available/default

```
3. Locate the try_files line within the server block and replace it with the following configuration:
```bash
location / {
    proxy_pass http://localhost:3000; 
```
This configuration sets up the reverse proxy for the Sparta app. The / location proxies all requests to the app, and the /posts location specifically proxies requests to the /posts path.
### Explanation of `location /` Directive in Nginx Configuration

In the Nginx configuration file, the line `location / { ... }` is a directive that defines how Nginx should handle requests for the root URL or the base path of your application.

### Components of the Line

- `location /`: This specifies the URL path that the directive applies to. In this case, `/` represents the root URL or the base path of your application. Any request that matches this location will be handled by the directives within the block.

- `proxy_pass http://localhost:3000;`: This directive tells Nginx to proxy the requests to the specified backend server. In this case, it proxies the requests to `http://localhost:3000`, which means Nginx will forward the requests to a Node.js server running on the same machine (`localhost`) and listening on port `3000`.

### How it Works

When a request is made to the root URL (e.g., `http://yourappdomain.com/`), Nginx will receive the request and pass it to the Node.js server specified in the `proxy_pass` directive. The Node.js server will then handle the request and send the response back to Nginx, which will finally deliver it to the client.

### Benefits

By using this configuration, you can effectively route incoming requests to your Node.js application through Nginx, providing additional benefits such as load balancing, caching, SSL termination, and more.


4. Save and close the file.

5. Test the Nginx configuration for syntax errors:
```bash
sudo nginx -t
 
```
Ensure there are no errors before proceeding.

6. Restart Nginx to apply the changes:
```bash
sudo systemctl restart nginx
 
```
7. Access your app by navigating to your app VM's public IP. The Sparta app should be available.

8. To access the /posts page, append /posts to your app VM's public IP.

By following these steps, you should now have a reverse proxy set up for the Sparta app using Nginx. Remember to adjust the configuration if your app is running on a different port or host.

For more detailed documentation and additional information, you can refer to the following article on DigitalOcean: How To Set Up a Node.js Application for Production on Ubuntu 18.04