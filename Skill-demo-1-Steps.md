Tasks

1. Log into ieng6 with the provided account. Your proctor will provide instructions on logging in; you will not use your own course-specific account, but rather one that we provide. All of the remaining steps involving running commands should be completed from ieng6.
- ```ssh cs15lspae@inge6.ucsd.edu```
- ```Input password```

2. Clone this repository using the command line. Use the https url to clone. https://github.com/ucsd-cse15l-s23/stringsearch 
- ```git clone https://github.com/ucsd-cse15l-s23/stringsearch ```

3. Compile and run StringServer with the sample words.txt file in that repository
- ```ls``` to see what directories there are; exists ```perl5  stringsearch  wavelet```
- ```cd stringsearch```
- ```javac Serverjava```
- ```javac StringServer.java```
- ```java StringServer 3000 words.txt```
- Sees: Server started at http://ieng6-203.ucsd.edu:3001


4. Load the path /search on that server with a query for “on” (without the quotes). To load the URL you can use a browser or curl from another terminal, your choice; you can use either for each step that asks you to load a URL.
- On browser, http://ieng6-203.ucsd.edu:3001. 
- ```http://ieng6-203.ucsd.edu:3001/search?q=on```

5. Add a string of your choice using the /add path
- ```http://ieng6-203.ucsd.edu:3001/add?s=everythingIsCool```

6. Do a single use of /search that finds the string you added plus at least one other string from words.txt    
- ```http://ieng6-203.ucsd.edu:3001/search?q=every```
7. Save the resulting list of strings to words.txt with the /save path
- ```http://ieng6-203.ucsd.edu:3001/save```

8. Stop the server and show in the terminal that the file words.txt has updated with the string you chose
- control C to stop server. 
- ```cat words.txt```
9. Clone this repository using the command line to a location of your choice (Use the https url to clone):
https://github.com/ucsd-cse15l-s23/stringsearch-data 
- First go back to home directory. ``` cd ~ ```
- ```git clone https://github.com/ucsd-cse15l-s23/stringsearch-data```

10. Restart the StringServer using a text file of your choice from the directory you cloned
- Check content of the directory now. 
- ```cd stringsearch-data```
- ```ls``` go into a dirctory, ```find 911report``` or something similar from technical, get a list of files. 

- Go back to the stringsearch directory. ```cd ~``` then ```cd stringsearch```
- restart server. 
- ```javac Serverjava```
- ```javac StringServer.java```
- ```java StringServer 3000 /home/linux/ieng6/cs15lsp23/cs15lsp23ae/stringsearch-data/technical/911report/chapter-11.txt```
11. Load a URL of a root path (/) to show all the strings in that file
- ```http://ieng6-203.ucsd.edu:3001```

12. Do a /search that returns more than one but fewer than 20 lines from that file.
- ```http:///ieng6-203.ucsd.edu:3001/imagination```
