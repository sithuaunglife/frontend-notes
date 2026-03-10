# Node.js

## Facts
- ```npm``` is scoped to the folder that contains ```package.json```. Each app (client/server) has its own ```package.json``` so npm commands must be run inside that folder by navigating (cd) into it first.
- After cloning a GitHub project, always run ```npm install``` to install dependencies before running any npm scripts.
- ```PATH``` decides which executable runs first when multiple versions exist; fixing the ```PATH``` order in System Properties resolves version conflicts.
- In a monorepo, you can have many ```package.json``` files.
- Node Version Manager (nvm) is used to install and switch between different Node.js versions.
- Node.js is a JavaScript runtime environment.

## Syntax
**pnpm-workspace-yaml**
```yaml 
packages:
  - "apps/*"
  - "packages/*"
```
- If ```pnpm install``` throws ```“packages field missing or empty”``` in a monorepo, make sure ```pnpm-workspace.yaml``` defines the packages paths like this.

## Terminal Commands
### Node Version Manager

**Node Version Manager**
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
```
- This installs nvm (Node Version Manager).
- After installing nvm, you can install Node.js using nvm.


- ```nvm install 20``` This command downloads and installs Node.js version 20 on your system using Node Version Manager.
- ```nvm use 20``` This command switches your current terminal to use Node.js version 20.

## Tools
- Notes


