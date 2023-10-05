# Lab Report 1: Remote Access and Filesystem (Week 1)

## Commands

### cd

```cd```  
![Image](./images/cd1.png)  
Running cd with no arguments changes the directory to the home directory. If no argument is provided, `cd` will change directory to home. This output is not an error.

```cd lecture1/```  
![Image](./images/cd2.png)  
Running cd with a directory as an argument will change the directory to the specified arugment. This output is not an error. 

```cd lecture1/Hello.java```  
![Image](./images/cd3.png)  
Running cd with a file as an argument will result in an error. This error results as we're unable to switch directory into a file. `cd` only works with directories, so a file argument results in an error.

### ls

```ls```  
![Image](./images/ls1.png)    
Running ls with no arguments lists the files and directories of the current working directory. This output is not an error.

```ls lecture1/```  
![Image](./images/ls2.png)  
Running ls with a directory as an argument lists the files and directories of the specified directory. This output is not an error. 

```ls Hello.java```  
![Image](./images/ls3.png)  
Running ls with a file as an argument lists out the specified file. This output is not an error.
