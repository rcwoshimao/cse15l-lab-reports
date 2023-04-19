# CSE 15L lab report 2 (Week 3)

## Contents 
* [Step 1: Using terminal within VS Code](#step-1-using-terminal-within-vs-code)
* [Step 2: Remote access your account](#step-2-Remote-access-your-account)
* [Step 3: Try some commands!](#step-3-Try-Some-Commands)


## Part 1
Code for string server: 
```java
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String s = ""; 

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return s;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                    s += parameters[1] + "\n";
                    return s;
                }
            }
            return "404 Not Found!";
        }
    }

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}


```

* Since I already have VS Code installed, I open VS Code and open a new terminal. 
![Image](1.png)

* Go to terminal > new terminal. Now a new terminal is opened. 
![Image](2.png)

## Step 2: Remote access my account

I used the following command to connect to my account, and then received the following prompt:
  
  ```$ ssh cs15lsp23ae@ieng6.ucsd.edu```
  
 My first try in connecting was unsuccessful beacuse I typed in the wrong passwords. The second time logging in, I got the resulting correct prompt. 
  ![Image](3.png)
  ![Image](4.png)

  
  ✅ I am now successfully connected to a computer in the CSE basement. 
  
## Step 3: Try Some Commands
I tried several interesting commands. 
First, the ```cd~``` command. Interestingly it gives me "command not found"; Now I try ```cd```, and ```pwd``` to list current working directory. 
  ![Image](5.png)

Then, I tried ```ls -lat``` . This command lists all files and directories in the current directory, and it gave me some interesting results. 
  ![Image](6.png)
  
  Finally, I tried the ```ls -a``` command. Different from the previous command, this one doesn't show any additional information (file permission, size, etc.) 
 ![Image](7.png)
