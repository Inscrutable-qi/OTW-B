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

 <h2> Level 12->13 </h2>
Level Goal:

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv.


Command: bandit12@bandit:~$ mktemp -d <br/>
/tmp/tmp.pTqqzAUhuJ<br/>
bandit12@bandit:~$ cp data.txt /tmp/tmp.pTqqzAUhuJ<br/>
bandit12@bandit:~$ cd /tmp/tmp.pTqqzAUhuJ<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data.txt<br/>
data.txt: ASCII text<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ xxd -r data.txt > data.bin<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data.bin  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data.bin<br/>
data.bin: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:00 2025, max compression, from Unix, original size modulo 2^32 572<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data.bin data.gz<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data.gz  data.txt<br/>

bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ gzip -d data.gz<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data<br/>
data: bzip2 compressed data, block size = 900k<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data data.bz2<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ bzip2 -d data.bz2<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data<br/>
data: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:00 2025, max compression, from Unix, original size modulo 2^32 20480<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data data.gz<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ gzip -d data.gz<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data<br/>
data: POSIX tar archive (GNU)<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data data.tar<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ tar xvf data.tar<br/>
data5.bin<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data5.bin<br/>
data5.bin: POSIX tar archive (GNU)<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data5.bin data.tar<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ tar xvf data.tar<br/>
data6.bin<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data6.bin<br/>
data6.bin: bzip2 compressed data, block size = 900k<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data6.bin data.bz2<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ bzip2 -d data.bz2<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/><br/>
data  data.tar  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data<br/>
data: POSIX tar archive (GNU)<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data data1.tar<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data1.tar  data.tar  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ tar xvf data1.tar<br/>
data8.bin<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data8.bin<br/>
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:00 2025, max compression, from Unix, original size modulo 2^32 49<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ mv data8.bin data.gz<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data1.tar  data.gz  data.tar  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data  data1.tar  data.tar  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data<br/>
data: ASCII text<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ xxd -d data > data1.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ ls<br/>
data  data1.tar  data1.txt  data.tar  data.txt<br/>
bandit12@bandit:/tmp/tmp.pTqqzAUhuJ$ file data1.txt<br/>
data1.txt: ASCII text<br/>
  
 <br/> Flag: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

 <h2> Level 13->14 </h2>
Level Goal:

    The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.


Command: scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private <br/>
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org <br/>
cat /etc/bandit_pass/bandit14<br/>
ssh, scp, umask, chmod, cat, nc, install
Breakdown:
SCP Key Transfer

scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private downloads the private key file from bandit13's ~ directory to your local current directory, authenticating with bandit13's password. This moves the key outside the server where localhost SSH restrictions don't apply.
SSH Key Authentication

ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org tells SSH to use the local sshkey.private file (-i) instead of password auth. Bandit14's authorized_keys contains the matching public key, so the server verifies your private key mathematically and grants access without passwords. Port -p 2220 targets the wargame server.
Password Retrieval

cat /etc/bandit_pass/bandit14 reads the plaintext password file once authenticated as bandit14, which contains 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e for the next level.


 
 <br/> Flag: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

 <h2> Level 14->15 </h2>
Level Goal:

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Command: nc localhost 30000 <br/>
ssh, telnet, nc, openssl, s_client, nmap

Breakdown:
   Port 30000 runs a netcat listener script checking authentication
   
 <br/> Flag: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

 
 <h2> Level 15->16 </h2>
Level Goal:

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

Command: openssl s_client -connect localhost:30001 <br/>

ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

Breakdown:
   

    openssl s_client: SSL/TLS debugging client mode

    -connect localhost:30001: Target host:port (localhost port 30001)

    Creates encrypted tunnel to SSL-wrapped netcat service

   
 <br/> Flag: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

 
 <h2> Level 16->17 </h2>
Level Goal:

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.


Command: nmap localhost -p 31000-32000 <br/>
ncat --ssl localhost 31790 <br/>
vim key<br/>
chmod 600 key<br/>
ssh -i key -p 2220 bandit17@bandit.labs.overthewire.org<br/>




ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

Breakdown:
   

   nmap localhost -p 31000-32000 scans ports 31000 through 32000 on localhost to find which SSL services listen 
    -connect localhost:30001: Target host:port (localhost port 30001)

ncat --ssl localhost 31790 connects to port 31790 using SSL encryption (alternative to openssl s_client), then paste bandit16 password for bandit17 key.<br/>
Now u got the ssh key to login to bandit17.<br/>
vim key - Opens vim editor to create key file, paste the RSA private key, save with :wq.<br/>

chmod 600 key - Sets private key permissions to owner read/write only (rw-------). SSH rejects keys with broader permissions for security.<br/>

ssh -i key -p 2220 bandit17@bandit.labs.overthewire.org - Connects as bandit17 using the key file (-i) on port 2220.
<br/>


 <h2> Level 17->18 </h2>
Level Goal:
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

Command: diff passwords.old passwords.new

Breakdown:
   diff passwords.old passwords.new compares two files line-by-line and shows exactly what changed.
   
 <br/> Flag: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO <br/>
 NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19 <br/>


 <h2> Level 18->19 </h2>
Level Goal:
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.<br/>

Command: ssh -t bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"

Breakdown:
   

    -t: Forces pseudo-terminal allocation (runs bashrc but allows command execution)

    "cat readme": Executes immediately, prints password before logout script

   
 <br/> Flag: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8 <br/>

 
 <h2> Level 19->20 </h2>
Level Goal:
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.<br/>

Command: ./bandit20-do cat /etc/bandit_pass/bandit20<br/>

Breakdown:
   

    ./bandit20-do - setuid binary owned by bandit20 (rws)

    cat - command to execute

    /etc/bandit_pass/bandit20 - target file


   
 <br/> Flag: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO <br/>


 <h2> Level 20->21 </h2>
Level Goal:
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.<br/>

Command: ./bandit20-do cat /etc/bandit_pass/bandit20<br/>

Breakdown:
   

    ./bandit20-do - setuid binary owned by bandit20 (rws)

    cat - command to execute

    /etc/bandit_pass/bandit20 - target file


   
 <br/> Flag: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO <br/>
 

 


 

 



 


  


 
