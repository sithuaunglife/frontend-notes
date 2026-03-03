# Server Concepts

## Facts
- Client request to Server.
- Server respond to Client.

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
### Terminal tool name 1

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




