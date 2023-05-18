# CSE 15L Lab report 4 (Week 7)
## Task steps 
After setting up SSH and github: 
1.  Log into ieng6
```ssh [cs15lsp23ae@ieng6.ucsd.edu](mailto:cs15lsp23ae@ieng6.ucsd.edu) <enter> (password) <enter>```

[img 1]
2.  Clone your fork of the repository from your Github account (with SSH): 
```git clone git@github.com:rcwoshimao/lab7 <enter>```
[img 2]
3.  Run the tests, demonstrating that they fail
```cd List <tab> .java <enter> ```
```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter> ```
```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>```
[img 3]
4.  Edit the code file to fix the failing test
```vim List <tab> .java <enter>```  
```:set number```  
```:43 w i <delete> 2 <esc> :wq```
[img 4]
5.  Run the tests, demonstrating that they now succeed
```<up arrow> <up arrow> <up arrow> <enter>```  
```<up arrow> <up arrow> <up arrow> <enter>```
[img 5]
6.  Commit and push the resulting change to your Github account (you can pick any commit message!)
```git add <enter>``` 
```git commit -m "Modified file" <enter>```
```git push <enter>```
[img 6]

