# CSE 15L lab report 2 (Week 3)

## Contents 
* [Step 1: Using terminal within VS Code](#part-1)
* [Step 2: Remote access your account](#part-2)
* [Step 3: Try some commands!](#part-3)


## Part 1

The Code below creates a web server called StringServer, which allows users to add String by user requests. 
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
Here are some sample outputs. For each output, the detailed explanations are written below: 
### Output 1
<img width="783" alt="Screenshot 2023-04-19 at 18 46 06" src="https://user-images.githubusercontent.com/108894739/233237033-e3fb4a12-a3e4-46f9-a03f-aef5828dd995.png">
In this example, the **methods** being called includes the **handleRequest** in Handler class, taking in an URI ```http://localhost:4000/add-message?s=Lorem%20ipsum%20dolor%20sit%20amet```. 
At this time, the value of ```String s``` = ```hi\n George```, since we already have some prexisting inputs when testing; 
              the value of ```String[] parameters``` = ``` {"http://localhost:4000/add-message?s", "Lorem%20ipsum%20dolor%20sit%20amet"}```; 
              the value of ```parameters[1]``` = ```"Lorem%20ipsum%20dolor%20sit%20amet"```;
The other method being called is **main** in StringServer class, taking in a String array ```args[]```, with the argument of port number. In this case, localhost 4000. 
<img width="991" alt="Screenshot 2023-04-19 at 19 03 30" src="https://user-images.githubusercontent.com/108894739/233238899-9772256e-ad74-4f69-ace5-41a0f7a55ab4.png">

<img width="674" alt="Screenshot 2023-04-19 at 18 46 49" src="https://user-images.githubusercontent.com/108894739/233237124-886f0319-549e-4cf9-a0d9-5600e2e0970c.png">


```http://localhost:4000/add-message?s=My%20name%20is%20Rebecca```

Methods called: 
Arguments of methods & value of fields: 
Change of values of the fields. 



we mean specific Strings, ints, URIs, and so on. "abc" is a value, 456 is a value, new URI("http://...") is a value, and so on.)

## Part 2

## Part 3 


