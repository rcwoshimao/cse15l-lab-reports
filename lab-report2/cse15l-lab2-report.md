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

At this time,

the value of ```String s``` =  ```hi\n George``` , since we already have some prexisting inputs when testing; 

the value of ```String[] parameters``` = ``` {"http://localhost:4000/add-message?s", "Lorem%20ipsum%20dolor%20sit%20amet"}``` ; 

the value of ```parameters[1]``` = ```"Lorem%20ipsum%20dolor%20sit%20amet"``` ;

The other method being called is **main** in StringServer class, taking in a String array ```args[]```, with the argument of port number. In this case, localhost 4000. 

<img width="991" alt="Screenshot 2023-04-19 at 19 03 30" src="https://user-images.githubusercontent.com/108894739/233238899-9772256e-ad74-4f69-ace5-41a0f7a55ab4.png">

### Output 2
<img width="674" alt="Screenshot 2023-04-19 at 18 46 49" src="https://user-images.githubusercontent.com/108894739/233237124-886f0319-549e-4cf9-a0d9-5600e2e0970c.png">
In this example, the **methods** being called includes the **handleRequest** in Handler class, taking in an URI ```http://localhost:4000/add-message?s=My%20name%20is%20Rebecca```. 

At this time,

the value of ```String s``` =  ```hi\n George\n Lorem%20ipsum%20dolor%20sit%20amet``` , since we already have some prexisting inputs when testing; 

the value of ```String[] parameters``` = ``` {"http://localhost:4000/add-message?s", "My%20name%20is%20Rebecca"}``` ; 

the value of ```parameters[1]``` = ```"My%20name%20is%20Rebecca"``` ;

The other method being called is **main** in StringServer class, taking in a String array ```args[]```, with the argument of port number. In this case, localhost 4000. 
The values of the URL, ```String s``` and ```String[] parameters``` are different from output 1, since it is a different command asking to add a completely different string to the display. 

## Part 2 
### Failure inducing input: 
```java
import static org.junit.Assert.*;
import org.junit.*;
public class ArrayTests {
@Test 
  public void testReversed2(){
    int[] input1 = {2,3,4}; 
    assertArrayEquals(new int[]{4,3,2}, ArrayExamples.reversed(input1));
  }
}
```

### Input that doesn't induce a failure: 
```java
 @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
### Symtom shown in output: 
<img width="1149" alt="Screenshot 2023-04-19 at 19 22 54" src="https://user-images.githubusercontent.com/108894739/233241334-bf49a10d-92a5-4bf6-9699-92a56f647b42.png">

### Buggy code: 
```java
public class ArrayExamples{
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
}
```
Fixed code: 
```java
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
```
Now the test runs perfectly. 
<img width="1145" alt="Screenshot 2023-04-19 at 19 26 00" src="https://user-images.githubusercontent.com/108894739/233241741-083159d9-cbc0-4b03-b874-4cefe9a8222e.png">

### Explanation
The above code is buggt in several ways, including: 
+ The method was returning the original array ```arr``` , instead of the supposed ```newArray``` created inside the method. 
+ The method was modifying the original array ```arr[i]``` in the for loop, instead of the (correct) other way around, setting the new array's element values equal to the existing one! 

## Part 3 
### Reflection on what I have learned
During week 2 and week 3, I learned how to create a web server, modify its displayed / stored content by different queries; I also learned more about how to use github to push, pull, fork, and commit files. 

