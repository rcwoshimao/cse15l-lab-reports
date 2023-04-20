# CSE 15L lab report 2 (Week 3)

## Contents 
* [Step 1: Using terminal within VS Code](#part-1)
* [Step 2: Remote access your account](#part-2)
* [Step 3: Try some commands!](#part-3)


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

<img width="783" alt="Screenshot 2023-04-19 at 18 46 06" src="https://user-images.githubusercontent.com/108894739/233237033-e3fb4a12-a3e4-46f9-a03f-aef5828dd995.png">
<img width="674" alt="Screenshot 2023-04-19 at 18 46 49" src="https://user-images.githubusercontent.com/108894739/233237124-886f0319-549e-4cf9-a0d9-5600e2e0970c.png">
![](image.png)

Methods called: 
Arguments of methods & value of fields: 
Change of values of the fields. 



we mean specific Strings, ints, URIs, and so on. "abc" is a value, 456 is a value, new URI("http://...") is a value, and so on.)

## Part 2

## Part 3 


