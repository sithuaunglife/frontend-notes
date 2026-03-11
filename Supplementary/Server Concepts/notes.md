# Server Concepts

## Facts
- Client request to Server.
- Server respond to Client.
- Vertical scaling (Scale Up ⬆, more CPU / RAM) increase power, 1 strong machine, Limited growth, single Point of Failure, simple architecture and risky if crash.
- Horizontal scaling (Scale Out ➡, Server A | Server B | Server C) increase instances, many machines, scalable, fault tolerant (if designed correctly), needs load balancer and safer.
- Horizontal scaling reduces workload by sharing traffic across multiple servers.
- VPC (Virtual Private Cloud) is your private network in the cloud.
- A VPC is a private network that isolates resources from the public internet and allows them to communicate securely with each other.
- VPC provides network isolation, while horizontal scaling handles increased traffic. They are not directly related.
- A Droplet (Digital Ocean) is a compute server, while networking (like VPC) defines how Droplets and other resources communicate.
- In Cloudflare ```@``` represents the root domain, ```*``` represents a wildcard subdomain, and a custom name like ```cloud``` can point to a specific service such as Coolify.
- The part directly before ```.com``` (ygnsh.com) is the root domain (also called the second-level domain).
- To identify the root domain and subdomains, read the domain from right to left. Example: ```"https://test.apple.ygnsh.com"``` ygnsh is root domain, apple is subdomain, test is sub-subdomain.
- Proxy is traffic router.
- When one server wants to connect to another server using SSH, the connecting server must have a private key, and the destination server must have the corresponding public key.
- You can use a terminal command to generate your own RSA SSH key.
- App server is the server that actually runs the application. You can have multiple app servers. Builder server is used to build the application, not to run it. Usually only one builder is needed. Coolify server is the control panel or orchestrator that manages deployments.
- SSH key files are renameable. You can also set password or no password.
- In this case ``` next  next.pub``` next is private key while next.pub is private key.
- You can create multiple SSH keys and use them for different servers.
- It is recommended not to access the server directly using the server IP in the browser. Instead, use the domain name because browsers can cache the IP and the server is usually meant to be accessed through a domain.
- Set in VS Code settings: ```"remote.SSH.path": "C:\Windows\System32\OpenSSH\ssh.exe"``` to make SSH works correctly.
- Space in username → can break some SSH clients.
- Normal Version (Server-Dependent) The app requires the full project environment to run. Needs things like node_modules, package.json, and installed dependencies on the server.
- Standalone Version (Self-Contained Build) The build packages the required runtime files together. Only a minimal set of dependencies is included. You don’t need to install the whole project on the server.
- PM2 is a production process manager for Node.js applications.
- Leaving the SSL configuration added by Certbot in the default Nginx config still works if the server_name matches the domain.
- It is recommended to run Certbot on the correct Nginx site configuration file (in `sites-available`) instead of the default site, so the SSL settings are added to the correct domain configuration.

## Syntax
**Parts of the link**
```js
"https://www.google.com/search?q=hello&filter=fruit"
```
- https is protocol
- www.google.com is host (domain)
- /search is path
- ?q=hello&filter=fruit is query string
- q is query parameter key
- hello is query parameter value
- & is separator between query parameters
- If backend decide q as filter word the word behind ? for example in this case q become a filter.


**HTTP Request Structure (Frontend → Backend)**
```js 
 method: "PUT",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization: `Bearer ${getCookie("token")}`,
    },
    body: JSON.stringify(payload)
```
- Method is action. Example: GET,POST,PUT,DELETE
- Headers are Metadata / Extra Info. Headers describe the request like Format, Identity, Permissions
- ```Content-Type``` is what I'm sending
- ```Authorization``` is authorizing who the person is
- ```Accept``` is login accept
- Body is Payload (Real Data), the actual values sent to backend
- ```Bearer``` is whoever holds token
- ```Token``` comes from cookie or storage
- Backend verifies token
- ```getCookie``` reads a cookie from browser storage
- ```Content-Type``` tells the server: “The body I’m sending is JSON.”, without it it still work but it is better to give it always, since in some case without ```Content-Type``` it will fail
- ```Accept``` tells backend: “I expect JSON back.”, even without ```Accept``` it still works but it is better to use it always
- ```Accept``` is more about negotiation than requirement


**SSH Config (Windows Path With Spaces)**
```config
Host 178.128.126.239
  HostName 178.128.126.239
  User root
  IdentityFile "C:/Users/HP 14s/.ssh/next"
```
- Quotes ```" "``` ensure the SSH client treats the entire path as one string.

## Terminal Commands
### SSH

**Chmod**
```bash
chmod 700
```
- It is permission setting.
- It means the owner has full access, and everyone else has no access.


- ```ssh-keygen``` generates a key pair on your own computer.
- ```.ssh``` is a directory in Ubuntu that stores SSH-related files (such as SSH keys) in the user's home directory.
- ```cat next.pub``` read the public key.
- ```ssh -i ~/.ssh/next root@178.128.126.239``` This command connects to a remote server using a specific SSH private key.
- ```chmod 600``` is private key permission.
- ```chmod 644``` is public key permission.

### PM2

- ```npm install -g pm2``` install PM2.
- ```pm2 start pnpm --name "next-app" -- start``` start PM2.
- ```pm2 save``` save PM2.
- ```pm2 startup``` start PM2.
- ```pm2 start next-app``` start PM2. 
- ```pm2 stop next-app``` stop PM2.
- ```pm2 restart next-app``` Restart PM2. 


### Certbot

- ```sudo apt install certbot python3-certbot-nginx -y``` This command install Certbot.
- ```sudo certbot --nginx -d next.kohtet.store``` This command run certbot in Nginx.
- ```sudo certbot renew --dry-run``` This command auto renew SSL.

## Tools
- Notes

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note




