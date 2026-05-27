# Nginx

## Facts
- After editing Nginx configuration files, run ```nginx -t``` to test the configuration, then reload Nginx to apply the changes.
- The source codes are mounted into `/var/www/html` or `/app` inside Docker container. Since container is isolated from local machine, dependencies need to be installed again inside container environment. When mounted with Docker volumes, Next.js dev server (`bun dev` / `next dev`) handles file watching and hot reload automatically.

## Syntax
**Heading 1**
```js 
 <!-- code here -->
```
- Description


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Nginx

- ```apt install nginx -y``` This command install nginx.
- ```systemctl start nginx``` This command start nginx.
- ```systemctl status nginx``` This command check nginx status.
- ```/var/www/html``` This is the default directory where Nginx stores website HTML files.
- ```/var/www/``` This directory is commonly used to store website source code on the server.
- ```sudo nano /etc/nginx/sites-available/next.kohtet.store``` This command creates or edits the Nginx configuration file for a website inside the sites-available directory.
- ```sudo ln -s /etc/nginx/sites-available/next.kohtet.store /etc/nginx/sites-enabled/``` Creates a symbolic link from `sites-available` to `sites-enabled`, which activates the Nginx website configuration.
- ```sudo nginx -t``` test the Nginx.

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