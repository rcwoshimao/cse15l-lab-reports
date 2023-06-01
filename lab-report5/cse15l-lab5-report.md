# CSE 15L Lab Report 5 (Week 9)
## Part 1: Debugging Scenario 
### Original Post

#### Title: Unable to run DocSearchServer

Post content: <br>

Environment: Macbook Pro M1, 2020; Mac OS; Chrome; VS Code. 

Context: Hello! I am trying to run the DocSearchServer on my terminal, but my code gives me an index out of bound error. I am passing in the correct port number,
and my file seems to compile correctly too. **My guess** is that I am running the server with the wrong command. Can someone help me out with this? <br>
<img width="1440" alt="Screenshot 2023-05-31 at 16 35 28" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/f41f952f-2444-4f08-9f68-0967b44c8c61">
<br>
**Symptom**: Expected: Seeing a notif about server started on port 3000; Actual: Instead saw the screenshot above. 
```console
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1
        at DocSearchServer.main(DocSearchServer.java:75)
```
<br>
**Failure-inducing input**: the input given in the above screenshot! `java DocSearchServer 3000`
<br>

### Response with leading question: 
TA: 
Hi Rebecca! You have correctly compiled the files, and you gave a valid port number indeed. However, I encourage you to look over the 
DocSearchServer Class and make sure you are giving it everything the server requires you to have. (Hint: think about how many arguments you'd need to run this server correctly?)

### Student Upate: 
Thank you so much for your help! After carefully inspecting the code, I realized I need another **file path** parameter for the line `Server.start(port, new Handler(args[1]));`. I chosed the path `technical/plos`, and my server started as intended. My search query works as intended too. 
<img width="912" alt="Screenshot 2023-05-31 at 19 13 31" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/fd309ef5-2d9f-4009-8f9e-e79b9096262a">
<img width="664" alt="Screenshot 2023-05-31 at 19 11 59" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/95548c22-1679-4b27-bfc3-7bf9fb879bb1">
<img width="738" alt="Screenshot 2023-05-31 at 19 12 08" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/d7b74dfc-1ce0-42ce-8500-f213701236f8">


### All the infor needed about the set up
- File Structure needed: This [DocSearch repository](https://github.com/rcwoshimao/docsearch). 
- Contents of each file before fixing the bug:  
        - lib/
        - technical/
        - DocSearchServer.java
        - README.md
        - Server.java
        - TestDocSearch.java
- Command that triggers the bug: 
```console
rebeccachen@shijieshangzuishuaiderendeMacbook ~ % cd desktop/docsearch-main 
rebeccachen@shijieshangzuishuaiderendeMacbook docsearch-main % javac DocSearchServer.java Server.java 
rebeccachen@shijieshangzuishuaiderendeMacbook docsearch-main % java DocSearchServer 3000
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1
        at DocSearchServer.main(DocSearchServer.java:75)
```
- What to edit to fix the bug: To fix the bug, add a second parameter to the command line used to run the server, to indicate which file to access. 
From <br> 
```java DocSearchServer 3000```
To <br>
```java DocSearchServer 3000 technical/plos```

## Part 2: Reflection
