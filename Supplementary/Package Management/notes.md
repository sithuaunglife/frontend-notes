# Node.js

## Facts
- ```npm``` is scoped to the folder that contains ```package.json```. Each app (client/server) has its own ```package.json``` so npm commands must be run inside that folder by navigating (cd) into it first.
- After cloning a GitHub project, always run ```npm install``` to install dependencies before running any npm scripts.
- ```PATH``` decides which executable runs first when multiple versions exist; fixing the ```PATH``` order in System Properties resolves version conflicts.

## Syntax
**pnpm-workspace-yaml**
```yaml 
packages:
  - "apps/*"
  - "packages/*"
```
- If ```pnpm install``` throws ```“packages field missing or empty”``` in a monorepo, make sure ```pnpm-workspace.yaml``` defines the packages paths like this.

## Terminal Commands
### 

**Heading**
```bash
 <!-- code here -->
```
- Description

## Tools
- Notes


