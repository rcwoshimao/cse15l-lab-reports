# CSE 15L Lab report 4 (Week 7)
## Task steps 
After setting up SSH and github: 
1.  Log into ieng6
```ssh [cs15lsp23ae@ieng6.ucsd.edu](mailto:cs15lsp23ae@ieng6.ucsd.edu) <enter> (password) <enter>```
<img width="998" alt="1" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/7c2f2a23-6e96-4ef8-866b-d230a31e9893">

2.  Clone your fork of the repository from your Github account (with SSH): 
```git clone git@github.com:rcwoshimao/lab7 <enter>```
<img width="1189" alt="2" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/26425150-63ea-4604-b9bd-993b57f5ae50">


3.  Run the tests, demonstrating that they fail
```cd List <tab> .java <enter> ```
```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter> ```
```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>```
<img width="992" alt="3" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/c28c69a7-7768-4d5b-b104-302183d2b303">

4.  Edit the code file to fix the failing test
```vim List <tab> .java <enter>```  
```:set number```  
```:43 w i <delete> 2 <esc> :wq```
<img width="996" alt="4" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/67351483-9207-49f8-affb-4e743da76196">

5.  Run the tests, demonstrating that they now succeed
```<up arrow> <up arrow> <up arrow> <enter>```  
```<up arrow> <up arrow> <up arrow> <enter>```
<img width="1052" alt="5" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/89955704-bc87-4c29-980e-f7f93e82c2e2">

6.  Commit and push the resulting change to your Github account (you can pick any commit message!)
```git add <enter>``` 
```git commit -m "Modified file" <enter>```
```git push <enter>```
<img width="816" alt="6" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/4161c3da-1fe1-450e-a81f-c9159898b39a">

### Now our file is successfully updated!! 

