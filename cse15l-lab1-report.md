# CSE 15L lab report 1 (Week 1)
> Hello fellow CSE 15L Students! Welcome to this course. In this tutorial, we will touch on how to log into a course-specific account on ieng6.

##  Required Software 
<ul>
<li> VS Code
</ul>

## Step 1: Using terminal within VS Code
<ol>
<li> To download VS Code, go to the [Visual Studio Code Website](https://code.visualstudio.com/). Follow the instructions and download it to your device, according to your operating system. 
<img src = "" alt = "VS Code website">
</li>

<li> In ordeer to remotely access your account, you need to use terminal in VS Code. On VS code's navigation bar, Go to terminal > new terminal. A new terminal should be opened below. </li>
<img src = "" alt = "Nav bar">
<img src = "" alt = "New terminal opened">

</ol>


## Step 2: Remote access your account
<ol>
  <li> Look up your CSE 15L Account on the [UCSD Educational Technology Site](https://sdacs.ucsd.edu/~icc/index.php). Follow the on screen instructions to reset your password. 
  
> **Important Note: Remember you are resetting the password for your course specific account, NOT your active directory!**
  </li> Now we use VScode/terminal to connect to a remote computer. 
  
>  If you are on a windows device, you need to [install git for Windows](https://gitforwindows.org/). Then, use [this post](https://stackoverflow.com/a/50527994) to set your default terminal to use the installed ```git bash``` in vs code. 

  In the terminal you opened in VS Code, Type in the following line, but **replace the letters "zz" with the letters in your course-specific account. 
  ```$ ssh cs15lsp23zz@ieng6.ucsd.edu```
  
If this is your first time logging in, you will see a message like this: 
  ```
  ⤇ ssh cs15lsp23zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
  ```
  Type ```yes```, press enter, and give your password. Once you are logged in, you should see something similar to the below: 
  ```
  # Now on remote server
Last login: Sun Jan  2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lsp23zz, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   23:25:01   0  0.08,  0.17,  0.11
ieng6-202   23:25:01   1  0.09,  0.15,  0.11
ieng6-203   23:25:01   1  0.08,  0.15,  0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lsp23
  ```
  <span style="color:red">You have successfully connected to a computer in the CSE basement! </span>
  <img src="" alt="Sample logged in">
</ol>


## Step 3: Try Some Commands
Once you are connected to your remote server, here are some commands you could try: 
```cd~```
```cd```
```ls -lat```
```ls -a```

To log out of the remote server in your terminal, either ```Ctrl-D``` or type in the command ```exit```. 
