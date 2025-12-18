# Git & Github

## Facts
- CLI is command line interface.
- CLI is powerful and every developer use it.
- Many people forgot about CLI because of UI.
- Linus is widely used in all platform like window,mac-os,etc...
- Git default is Vim.
- Git is version control-system.
- Git track changes in computer files.
- Git coordinate work among multiple people.
- Repository is folder used by git.


## Syntax
**Heading**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Gitbash

**Gitbash commands**
- ```mkdir``` create folder.
- ```touch``` create file.
- ```ls``` show files and folder.
- ```ls -l``` show file edit info.
- ```la -la``` show all files and show hidden files too.
- ```~``` means home.
- ```pwd``` show where you are.
- ```cat``` show what is written inside the file in code.
- ```history``` show what you typed.
- ```rm``` remove things,you cannot remove all folder with this one.
- ```rm *``` remove all file.
- ```rm -r``` remove folder.
- ```cp``` copy. Example: cp index.html aa.html
- ```cp -r``` copy folder. Use it only to copy folder.
- ```mv``` move file. Also use in rename. Example: mv notes.md docs/react-notes.md
- ```mv -r``` move folder. Example: mv hello/ hi.
- ```nano``` is is a terminal-based text editor used to edit files. In nano use ```Ctrl + O``` to save. Use ```Ctrl + X``` to exit.
- ```vim <filename>``` run vim.In order to use it press ```i``` to enter into write mode, ```Esc``` to quit write mode, ```:wq``` to write and quit saving, ```:q``` only quit without saving, ```dd``` it cut the line and you can paste with ```p```. 
- ```curl``` is a command-line tool for making HTTP requests. It is used to send requests to URLs and display the response in the terminal. Commonly used to test APIs, download data, or inspect server responses.
- ```code``` open Vs Code.
- Pressing Up ```↑``` arrow key shows the previously used command.
- ```git init``` create .git repository that is hidden. Use ```ls -la``` to view. It is also a main branch at first creation.
- ```git status``` check git status and changes.


**Git Configuration**
1.
```
git config ---global init.defaultbranch main
```
2.
```
git config --global user.name <Your name>
```
3.
```
git config --global user.email <Your email>
```
- Those are necessary for git to work in local machine and it is only set first time using git in machine.


- For ```--global``` it is for system. For project it is better to use ```--local```.
- ```git config --global user.name user.email init.defaultbranch``` it is used to check information if it is correct. 

## Tools
- Notes


