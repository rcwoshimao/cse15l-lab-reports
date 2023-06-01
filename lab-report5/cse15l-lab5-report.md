# CSE 15L Lab Report 5 (Week 9)
## Part 1: Debugging Scenario 
### Original Post

#### Title: Unable to run DocSearchServer

Post content: <br>

Environment: Macbook Pro M1, 2020; Mac OS; Chrome; VS Code. 

Context: Hello! I am trying to run the DocSearchServer with my bash script, but my code gives me an index out of bound error. I am passing in the correct port number,
and my file seems to compile correctly too. **My guess** is that I am running the server with the wrong command. Can someone help me out with this? <br>
<img width="760" alt="Screenshot 2023-05-31 at 19 30 45" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/89771c8c-88ef-4645-88b7-64650ba521cf">
<br>
**Symptom**: Expected: Seeing a notif about server started on port 3000; Actual: Instead saw the screenshot above. 
```console
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1
        at DocSearchServer.main(DocSearchServer.java:75)
```

**Failure-inducing input**: the input given in the above screenshot! `java DocSearchServer 3000`. 

### Response with leading question: 
TA: 
Hi Rebecca! You have correctly compiled the files, and you gave a valid port number indeed. However, I encourage you to look over the 
DocSearchServer Class and make sure you are giving it everything the server requires you to have. (Hint: think about how many arguments you'd need to run this server correctly?)

### Student Upate: 
Thank you so much for your help! After carefully inspecting the code, I realized I need another **file path** parameter for the line `Server.start(port, new Handler(args[1]));`. I chosed the path `technical/plos`, and my server started as intended. My search query works as intended too. 
<img width="762" alt="Screenshot 2023-05-31 at 19 31 52" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/50d00e22-46f2-41fd-b9d3-3d3a2f81b83b">
<br>
<img width="664" alt="Screenshot 2023-05-31 at 19 11 59" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/95548c22-1679-4b27-bfc3-7bf9fb879bb1">
<br>
<img width="738" alt="Screenshot 2023-05-31 at 19 12 08" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/d7b74dfc-1ce0-42ce-8500-f213701236f8">
<br>

### All the info needed about the set up
- File Structure needed: This [DocSearch repository](https://github.com/rcwoshimao/docsearch). 
- Contents of each file before fixing the bug:  
    - lib/
    - technical/
    - DocSearchServer.java
    - README.md
    - Server.java
    - TestDocSearch.java
    - docsearch.sh\
Content of docsearch.sh:
```console
javac DocSearchServer.java Server.java 
java DocSearchServer 3000 technical/plos
```
- Command that triggers the bug: 
```console
rebeccachen@shijieshangzuishuaiderendeMacbook ~ % cd desktop/docsearch-main 
rebeccachen@shijieshangzuishuaiderendeMacbook docsearch-main % javac DocSearchServer.java Server.java 
rebeccachen@shijieshangzuishuaiderendeMacbook docsearch-main % java DocSearchServer 3000
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1
        at DocSearchServer.main(DocSearchServer.java:75)
```
- What to edit to fix the bug: To fix the bug, add a second parameter to the command line used to run the server, to indicate which file to access.   
From  
```console 
java DocSearchServer 3000
```
To  
```console 
java DocSearchServer 3000 technical/plos
```

## Part 2: Reflection
In a couple of sentences, describe something you learned from your lab experience in the second half of this quarter that you didn’t know before. It could be a technical topic we addressed specifically, something cool you found out on your own building on labs, something you learned from a tutor or classmate, and so on. It doesn’t have to be specifically related to a lab writeup, we just want to hear about cool things you learned!

