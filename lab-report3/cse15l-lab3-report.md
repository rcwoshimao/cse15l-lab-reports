# CSE 15L Lab report 3 (Week 5)

## Researching Commands - Grep 

In my research Command lab, I will focus on the options of the **grep-command**. 
First, we have our git repository cloned onto my desktop. 
```console
rebeccachen@shijieshangzuishuaiderendeMacbook desktop % git clone https://github.com/ucsd-cse15l-s23/stringsearch-data
Cloning into 'stringsearch-data'...
remote: Enumerating objects: 1403, done.
remote: Counting objects: 100% (1403/1403), done.
remote: Compressing objects: 100% (1401/1401), done.
remote: Total 1403 (delta 1), reused 1403 (delta 1), pack-reused 0
Receiving objects: 100% (1403/1403), 11.85 MiB | 2.13 MiB/s, done.
Resolving deltas: 100% (1/1), done.
rebeccachen@shijieshangzuishuaiderendeMacbook desktop % cd stringsearch-data/technical
rebeccachen@shijieshangzuishuaiderendeMacbook technical % 
```
We are now in the technical folder. Now lets see what options grep has by using ```man grep```. 
<img width="1437" alt="Screenshot 2023-05-07 at 19 37 41" src="https://user-images.githubusercontent.com/108894739/236721590-62eeb1f7-0481-4d22-b75d-f2172816a1f7.png">

Some very interesting examples are given by the console. After careful examination, I decide to test on a **combination** of several of the commands given. Pressed ```q``` to return to technical. 

### Option 1: ```grep -c -i```, Find all occurrences of a pattern but ignoring cases. 

Example 1: We will use the file ```Advocate_for_Poor.txt``` in technical/government/Media to test out this command. 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -c 'this' Advocate_for_Poor.txt 
1
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -c -i 'this' Advocate_for_Poor.txt 
2
```
Indeed the number of word count changed.

Example 2: 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -c 'poor' Advocate_for_Poor.txt 
2
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -c -i 'poor' Advocate_for_Poor.txt 
3
```

### Option 2: ```grep -w```, find all occurrences of a pattern, but only complete words. This can help eliminate cases such as "before" being counted as "for". 

This time I decided to try this on all the documents in Media. 

Example 1: 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'of' *.txt 
5_Legal_Groups.txt:Legal Center at 205 N. 400 West is a project of "And Justice for
5_Legal_Groups.txt:campaign by an alliance of the non-profit providers of free legal
5_Legal_Groups.txt:campaign of legal services agencies in the country, and the
5_Legal_Groups.txt:Community Legal Center is the first joint office project of public
...
```

There are too many lines being printed, it's too hard to see a pattern! So instead I asked wc to count the line of the output, so we know how many outputs our grep command actuall gave. 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'of' *.txt | wc -l 
    2629
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep 'of' *.txt | wc -l
    3101
```

Example 2 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep 'come' *.txt | wc -l
     266
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'come' *.txt | wc -l
      48
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'come' *.txt #smalll check on output.        
Aid_Gets_7_Million.txt:Both grants come from the Legal Services., a private, nonprofit
Assuring_Underprivileged.txt:"A lot of my clients really feel that they're not afraid to come
Avoids_Budget_Cut.txt:"I had a client come in off the street one day and she said,
Barnes_pro_bono.txt:voicemail and heard Gov. Roy Barnes saying he wanted to come to
...
```

### Option 3 ```grep -v``` Find all lines in a file which do not contain certain words. I will use the ```-e``` commmand along with this one, just to pump things up for fun. 

Example 1 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -v -e 'this' -e 'that' *.txt | wc -l
   11961
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -v *.txt | wc -l
   13134
```

Example 2
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media %  grep -v -e 'government' -e 'biome' *.txt |wc -l
   13121
rebeccachen@shijieshangzuishuaiderendeMacbook Media %  grep -v -e 'statistics' -e 'hello' *.txt |wc -l 
   13188
```

### Option 4:  ```grep -A <N> "string" FILENAME``` or  ```grep -B <N> "string" FILENAME``` Display N lines after and before match. 

Example 1
```console
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -A 5 "say " Advocate_for_Poor.txt
property. He did not say how much he was paying, but he said the
units are rent-controlled. That makes getting fair market value for
the commercial space a must. That could amount to several times as
much as the $250 a month Mazzariello currently pays the Housing
Preservation and Development Department.
"I embrace the kind of business he is running," Montalvo said.
```
Example 2 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -B 5 "spokeswoman" Advocate_for_Poor.txt

Another Bidder
Then, last week, Mazzariello got bad news from the department. A
tenant in the building had put in an application to buy it first.
Program guidelines give tenants priority over commercial users.
Department spokeswoman Carol Abrams said homeownership comes
rebeccachen@shijieshangzuishuaiderendeMacbook Media % 
```
