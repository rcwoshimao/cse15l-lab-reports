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

## Part 2

## Part 3 


