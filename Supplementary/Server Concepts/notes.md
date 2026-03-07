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

## Terminal Commands
### SSH

**Chmod**
```bash
chmod 700
```
- It is permission setting.
- It means the owner has full access, and everyone else has no access.


**Heading 2**
```bash
 <!-- code here -->
```
- Description


### Terminal tool name 2

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description

## Tools
- Notes

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note




