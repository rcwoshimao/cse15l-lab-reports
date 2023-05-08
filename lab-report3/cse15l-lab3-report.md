# CSE 15L Lab report 3 (Week 5)

## Researching Commands - Grep 

In my research Command lab, I will focus on four options of the grep-command. 
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

Some very interesting examples are given by the console. After careful examination, I decide to test on a ** combination ** of the four options below: 

```console
      -c, --count
             Only a count of selected lines is written to standard output.
      -L, --files-without-match
             Only the names of files not containing selected lines are written to standard output.  Pathnames are listed once
             per file searched.  If the standard input is searched, the string “(standard input)” is written unless a --label is
             specified.
      -v, --invert-match
             Selected lines are those not matching any of the specified patterns.
      -e pattern, --regexp=pattern
             Specify a pattern used during the search of the input: an input line is selected if it matches any of the specified
             patterns.  This option is most useful when multiple -e options are used to specify multiple patterns, or when a
             pattern begins with a dash (‘-’)
```
Now we test out the options. Pressed ```q``` to return to technical. 
Option 1: find all occurrences of a pattern but ignoring cases. 

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
Option 2: ```grep -w```, find all occurrences of a pattern, but only complete words. This can help eliminate cases such as "before" being counted as "for". 
This time I decided to try this on all the documents in Media. 
Example 1: 
```console 
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'of' *.txt 
5_Legal_Groups.txt:Legal Center at 205 N. 400 West is a project of "And Justice for
5_Legal_Groups.txt:campaign by an alliance of the non-profit providers of free legal
5_Legal_Groups.txt:campaign of legal services agencies in the country, and the
5_Legal_Groups.txt:Community Legal Center is the first joint office project of public
5_Legal_Groups.txt:The Legal Aid Society of Salt Lake, the Disability Law Center,
5_Legal_Groups.txt:last Wednesday their board members were given a tour of the
5_Legal_Groups.txt:Community Legal Center hosted by staff members of the five
5_Legal_Groups.txt:agencies. All of the agencies can share the same reception area and
5_Legal_Groups.txt:own Tomax Technologies and were the sellers of the building. Jaye
5_Legal_Groups.txt:explained how much of the renovation had been merely uncovering
5_Legal_Groups.txt:become one of the major supporters of the project.
5_Legal_Groups.txt:Stewart Ralphs, the executive director of the Legal Aid Society,
5_Legal_Groups.txt:ways to go, with a bit more than half of the $4 million projected
AP_LawSchoolDebts.txt:lawyer, prevents 66 percent of law students from taking public
AP_LawSchoolDebts.txt:in debt and shut out of public service at a time when the federal
AP_LawSchoolDebts.txt:government is facing losses of over half its work force due to
AP_LawSchoolDebts.txt:retirements," said Max Stier, president and chief executive of the
AP_LawSchoolDebts.txt:More than 94 percent of law students reported borrowing money to
AP_LawSchoolDebts.txt:card debt of around $2,750.
AP_LawSchoolDebts.txt:In the law study, about 68 percent of public interest employers
AP_LawSchoolDebts.txt:difficulties. Most blamed the combination of low starting salaries
A_Perk_of_Age.txt:A Perk of Age: Free Legal Advice
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
rebeccachen@shijieshangzuishuaiderendeMacbook Media % grep -w 'come' *.txt #check contents this time to see if complete words are outputs:         
Aid_Gets_7_Million.txt:Both grants come from the Legal Services., a private, nonprofit
Assuring_Underprivileged.txt:"A lot of my clients really feel that they're not afraid to come
Avoids_Budget_Cut.txt:"I had a client come in off the street one day and she said,
Barnes_pro_bono.txt:voicemail and heard Gov. Roy Barnes saying he wanted to come to
Coup_Reshapes_Legal_Aid.txt:effortless, for others, it did not come easy. And few programs
Coup_Reshapes_Legal_Aid.txt:"There are very few people who come out as the heroes.
Disaster_center.txt:"They need to come in and go through our interview process," she
Domestic_violence_aid.txt:to help them do anything, so when they come to us they are
Donald_Hilliker.txt:about $6.4 million has in the past come from the Legal Services
Entities_Merge.txt:group, said he has since come to see the merger as a positive move
FortWorthStarTelegram.txt:The grants come at a time when funding for programs providing
Free_Legal_Assistance.txt:come in here very confused and very sad and not know what to do.
Funding_May_Limit.txt:hard to come by, if two organizations now providing such help can't
Good_guys_reward.txt:bus drivers come to her for advice on divorce, child custody and
Good_guys_reward.txt:swear by me. They always come back and bring others with
Helping_Hands.txt:Legal assistance for battered women is hard to come by. But it
Higher_court.txt:''If you don't come up with the money somewhere, legal services
Kiosks_for_court_forms.txt:"A large percentage of the people that come before me do not
Law_Schools.txt:At those rates, perhaps it should come as no surprise that 71
Law_Schools.txt:furrowing his brow as if the question had never come up. "I think
Legal-aid_chief.txt:group's $3.9 million budget this year. The rest will come from the
Legal_Aid_in_Clay_County.txt:about 75 percent of the women who come to her agency in search of
...
```
Option 3 ```grep -v``` Find all lines in a file which do not contain certain words. I will use the ```-e``` commmand along with this one, just to pump things up for fun. 

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

Option 4: 
Example 1 
Example 2 
Source: 


 “find command-line options” will probably give decent results. There is also a built-in command on many systems called man (short for “manual”) that displays information about commands; you can use man grep, for example, to see a long listing of information about how grep works. Also consider asking ChatGPT!

