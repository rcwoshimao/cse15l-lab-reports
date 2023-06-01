# CSE 15L Lab Report 5 (Week 9)
## Part 1: Debugging Scenario 
### Original Post

#### Title: Unable to run DocSearchServer

Post content: <br>

Environment: Macbook Pro M1, 2020; Mac OS; Chrome; VS Code. 

Context: Hello! I am trying to run the DocSearchServer on my terminal, but my code gives me an index out of bound error. I am passing in the correct port number,
and my file seems to compile correctly too. Can someone help me out with this? <br>
<img width="1440" alt="Screenshot 2023-05-31 at 16 35 28" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/f41f952f-2444-4f08-9f68-0967b44c8c61">
<br>
Symptom: Expected: Seeing a notif about server started on port 3000; Actual: Instead saw the screenshot above. 
```console
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1
        at DocSearchServer.main(DocSearchServer.java:75)
```
<br>
Failure-inducing input: the input given in the above screenshot! Also below: 
`console
java DocSearchServer 3000
`


### response with leading question: 
TA: 
Hi Rebecca! You have correctly compiled the files I see, and you gave a valid port number indeed. However, I encourage you to look over the 
DocSearchServer Class and make sure you are giving it everything the server requires you to have. 



### All the infor needed about the set up
- File Structure needed: [**This repository**](https://github.com/ucsd-cse15l-w23/lab3) from lab 3 
- Contents of each file before fixing the bug: 
  - Folders: lib
  - Files: 
    - ArrayExamples.java
    - ArrayTests.java
    - FileExample.java
    - LectureExamples.java
    - LinkedListExample.java
    - ListExamples.java
    - MethodsTests.java
- Command that triggers the bug: 
- What to edit to fix the bug

(scenario 1) 


## Part 2: Reflection
