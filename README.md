# OTVB
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
