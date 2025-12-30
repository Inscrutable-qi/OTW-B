# OTW-B
 This repository contains solutions and walkthroughs for the OTV Bandit.<br/> <h3>SPOILER ALERT!</h3> <br/>

 <h1> Walkthrough </h1>
 <br/><br/>
 <h2> Level 0->1 </h2>
 <h3> Goal</h3>
 <body> Be able to connect to the server using SSH from a Terminal and to get the password for the next level that is stored in a file called readme located in the home directory </body>
 <h3> Commands Used </h3>
 <body> ssh username@host -p XXXX <br/> ssh bandit0@bandit.labs.overthewire.org -p 2220, ls, cat</body>
 <h3> Password </h3>
 <body> bandit0 , ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If  </body>
 <h3> Solution </h3>
 <body> Enter the command ssh bandit0@bandit.labs.overthewire.org -p 2220 in the terminal <br/> Enter the password bandit0 <br/> Read the readme file with cat command
 </body>
<br/><br/>

<h2> Level 1->2 </h2>
 <h3> Goal</h3>
 <body> Learn how to read file with special character, which in this case is "-"</body> 
 <h3> Commands Used </h3>
 <body> ssh bandit1@bandit.labs.overthewire.org -p 2220 <br/> cd, ls, cat, find, file, du</body>
 <h3> Password </h3>
 <body> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx </body>
 <h3> Solution </h3>
 <body> Exit the bandit0 with exit command then make ssh the bandit1. Use the password obtained in prev step to unlock. <br/> U are supposed to use ./ to read the speacial character '-'<br/> cat ./- 
 </body>
 <br/><br/>
 
<h2> Level 2->3 </h2>
 <h3> Goal</h3>
 <body>Read the file named --spaces in this filename-- located in the home directory </body> 
 <h3> Commands Used </h3>
 <body> ssh bandit2@bandit.labs.overthewire.org -p 2220 <br/> cd, ls, cat, find, file, du</body>
 <h3> Password </h3>
 <body> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx </body>
 <h3> Solution </h3>
 <body> Exit the bandit1 and make ssh the bandit2. Use the password obtained in prev step to unlock. <br/> U are supposed to use ./ to read the speacial character and also use  " "  or  ' ' to read to filename which has spaces<br/> cat ./--"spaces in this filename--"
 </body>
 <br/><br/>

 <h2> Level 3->4 </h2>
 <h3> Goal</h3>
 <body>The password for the next level is stored in a hidden file in the inhere directory </body> 
 <h3> Commands Used </h3>
 <body> ssh bandit3@bandit.labs.overthewire.org -p 2220 <br/> cd, ls, cat, find, file, du </body>
 <h3> Password </h3>
 <body> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ </body>
 <h3> Solution </h3>
 <body>Use the password obtained in prev step to unlock. <br/> U are supposed to read the hidden file with ls -a or find or whatever way possible <br/> cd inhere, find, cat ...Hiding-From-You
 </body>
 <br/><br/>

  <h2> Level 4->5 </h2>
 <h3> Goal</h3>
 <body>The password for the next level is stored in the only human-readable file in the inhere directory. </body> 
 <h3> Commands Used </h3>
 <body> ssh bandit4@bandit.labs.overthewire.org -p 2220 <br/> cd, ls, cat, find, file, du </body>
 <h3> Password </h3>
 <body> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw </body>
 <h3> Solution </h3>
 <body>Use the password obtained in prev step to unlock. <br/> U are supposed to read all the files until u find the password in -file07
 </body>
 <br/><br/>

  <h2> Level 5->6 </h2>
 <h3> Goal</h3>
 <body>The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable
</body> 
 <h3> Commands Used </h3>
 <body> ssh bandit5@bandit.labs.overthewire.org -p 2220 <br/> cd, ls, cat, find, file, du </body>
 <h3> Password </h3>
 <body> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG </body>
 <h3> Solution </h3>
 <body>Use the password obtained in prev step to unlock. <br/> Basically the file should be 1033 bytes, non-executable, human-readable <br/> find -size 1033c , Here c represents the bytes
 <br/><br/>

  <h2> Level 6->7 </h2>
Level Goal:

    The password for the next level is stored somewhere on the server and has all of the following properties:
    owned by user bandit7
    owned by group bandit6
    33 bytes in size

For this task we can use the command find again.

Command:

find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

Breakdown:

    find: Searches for files and directories in the specified location.
    /: Specifies the root directory to search in (all directories).
    -user bandit7: Filters for files owned by the user bandit7.
    -group bandit6: Filters for files belonging to the group bandit6.
    -size 33c: Looks for files that are exactly 33 bytes in size (c stands for bytes).
    2>/dev/null: Redirects any error messages (stderr) to /dev/null to suppress them from being displayed.
 After executing, the output show us the file /var/lib/dpkg/info/bandit7.password which is the file we are looking for.
 <br/> Flag: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

<h2> Level 7->8 </h2> 
    The password for the next level is stored in the file data.txt next to the word millionth

We use grep to extract the word millionth.

Command used:

cat ./data.txt | grep "millionth"

    cat ./data.txt → display the contents of data.txt.
    | → send (pipe) the output of cat to the next command.
    grep "millionth" → search for lines containing the word millionth.
<br/> Flag: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

<h2> Level 8->9 </h2>
    The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

For this we utilize the command sort , uniq .

Command:

cat data.txt | sort | uniq -u

Explanation:

    cat data.txt → display the contents of data.txt.
    | → pipe output to the next command.
    sort → arrange lines in alphabetical order.
    uniq -u → show only lines that appear exactly once in the sorted list.
    
   <br/> Flag: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

  <h2> Level 9->10 </h2> 
      The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

We can use strings and grep for this.

Command:

strings ./data.txt | grep "="

Explanation:

    strings data.txt → extract human-readable text from data.txt.
    | → pipe output to the next command.
    grep "=" → search for lines containing = .
  <br/> Flag: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

   <h2> Level 10->11 </h2>
       The password for the next level is stored in the file data.txt, which contains base64 encoded data

Theres a built in utility called base64 that we can to decode the string.

Command:

base64 -d data.txt

    base64 -d data.txt → directly decode the Base64-encoded content of data.txt . -d option says “decode
<br/> Flag: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

<h2> Level 11->12 </h2>
Level Goal:

    The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

For this task we can use the command cat combined with tr.

Command: cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

Breakdown:

    cat data.txt: Displays the content of data.txt.
    |: Pipes the output to the next command.
    tr 'A-Za-z' 'N-ZA-Mn-za-m': Applies the ROT13 cipher, a simple letter substitution technique that shifts each letter by 13 positions in the alphabet:
        A-M maps to N-Z, and N-Z maps to A-M (for uppercase letters).
        a-m maps to n-z, and n-z maps to a-m (for lowercase letters).
 <br/> Flag: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4


  


 
