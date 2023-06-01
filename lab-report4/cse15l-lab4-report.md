# CSE 15L Lab report 4 (Week 7)
## Task steps 
## After setting up SSH and github: 
1.  Log into ieng6: Since we have set up the ssh, we no longer need to type in the password. I simply typed in the following line: 
```ssh cs15lsp23ae@ieng6.ucsd.edu ``` \
and the process is done. 
<img width="887" alt="Screenshot 2023-06-01 at 15 02 18" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/09b9312c-cb13-4de8-a90e-cf621ec88174">


2.  Clone your fork of the repository from your Github account (with SSH)\
```git clone git@github.com:rcwoshimao/lab7 <enter>```
<img width="1189" alt="2" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/26425150-63ea-4604-b9bd-993b57f5ae50">

3.  Run the tests, demonstrating that they fail: \
Since we already have a test file `test.sh`, lets run it with bash:
 <img width="788" alt="Screenshot 2023-06-01 at 15 04 02" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/a4ef3644-acce-4dd9-adb0-a0b05f3d2c2b">

4.  Edit the code file to fix the failing test \
Now lets use vim to edit the files! 
Start up vim: 
```vim List <tab> .java <enter>```  
Set up numbers so we know which line to jump to to fix: 
```:set number```  
We can see the line we need to fix is 43. The following commands get us to line 43, delete and modify the code, and saves and exit the file. 
```:43 w i <delete> 2 <esc> :wq```
<img width="996" alt="4" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/67351483-9207-49f8-affb-4e743da76196">

5.  Run the tests, demonstrating that they now succeed
```<up arrow> <up arrow> <up arrow> <enter>```  
```<up arrow> <up arrow> <up arrow> <enter>```
<img width="1052" alt="5" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/89955704-bc87-4c29-980e-f7f93e82c2e2">

6.  Commit and push the resulting change to your Github account
```git add <enter>``` 
```git commit -m "Modified file" <enter>```
```git push <enter>```
<img width="816" alt="6" src="https://github.com/rcwoshimao/cse15l-lab-reports/assets/108894739/4161c3da-1fe1-450e-a81f-c9159898b39a">

### Now our file is successfully updated!! 

