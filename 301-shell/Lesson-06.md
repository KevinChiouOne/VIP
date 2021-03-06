# Shell 301
## Lesson 6: exit & journalctl

`cd ~/School/VIP/shell/301`

`gedit &`

`nautilus . &`

- [Variables](https://github.com/inkVerb/vip/blob/master/Cheat-Sheets/Variables.md)
- [Tests](https://github.com/inkVerb/vip/blob/master/Cheat-Sheets/Tests.md)

___

### *Note* `exit` *&* `journalctl` *are used for logs*

## I. System logs via `journalctl`

*Look at some log entries on your machine*

*Space to scroll down*

*Ctrl+C to close*

`journalctl`

*Q to quit*

*Use* `-r` *to "reverse" the order and view most recent log entries first*

`journalctl -r`

*Create a system log entry*

`logger "I logged this just now."`

`journalctl -r` *Q to quit*

*Use* `-i` *to include PID number,* `-t SOME_TEXT` *to add a "tag"*

`logger -i -t myTag "I logged this just now."`

`journalctl -r` *Q to quit*

*Use* `-p` *with a "facility", then "severity"*

`logger -i -t myTag -p local0.info "I logged this just now."`

`journalctl -r` *Q to quit*

*"Severity" has seven levels:*
- 1 Alert:	`alert`
- 2 Critical	`crit`
- 3 Error	`err`
- 4 Warning	`warn`
- 5 Notice	`notice` (normal, but significant)
- 6 Info	`info`
- 7 Debug	`debug` (so much info that only geeks & developers are interested)

*There are many "facilities", some include:*
- `ftp`
- `cron`
- `auth`
- `news`
- `clock`
- `mail`
- `syslog`
- `user`

*For your own "facilities", you can use* `local0` – `local7`

### For an administrator to use `su`
> 
___
> 
> `su` *input the password*
> 
> `journalctl`
> 
> *Q to quit*
> 
> *Use* `-r` *to "reverse" the order and view most recent log entries first*
> 
> `journalctl -r`
> 
> *Create a system log entry*
> 
> `logger "I logged this just now."`
> 
> `journalctl -r` *Q to quit*
> 
> *Use* `-i` *to include PID number,* `-t SOME_TEXT` *to add a "tag"*
> 
> `logger -i -t myTag "I logged this just now."`
> 
> `journalctl -r` *Q to quit*
> 
> *Use* `-p` *with a "facility", then "severity"*
> 
> `logger -i -t myTag -p local0.info "I logged this just now."`
> 
> `journalctl -r` *Q to quit*
> 
___


## II. Custom output logs

### *Notes about* `exit` codes

*Logs &* `exit` *codes are both important, but different*

*Errors are important, handle them correctlyin Shell scripts!*

> *An* `exit` *is a way to "break" out of a script, such as* `if - then` *tests, but always use* `exit 0` *unless a problem or event needs to be logged!*
> 
> *It is considered "bad coding" to use* `exit` *without a number or to use an exit other than* `exit 0` *without need for a log entry*
> 
> *When tutorials only have* `exit` *in the example, it is up to you to put the correct number after, probably* `exit 0`
> 

### A custom log can be useful for keeping track of what happens in your own software

`mkdir logs`

`cd logs`

*Send* STDOUT *(output) to a file with:* `> OUTPUTFILE`

*Send* STDERR *(error output) to a file with:* `2> OUTPUTFILE`

`ls dumbo`

*Note the error message in the terminal*

`ls dumbo 2> error.log`

*Not the same error message went into the file*

`gedit error.log`

*gedit: Reload error.log*

`ls dumbo 2>> error.log`

*gedit: Reload error.log*

`ls >> normal.log`

`gedit normal.log`

*Combine this into one command with:* `> STDOUT 2> STDERR`

`ls bozo >> normal.log 2>> error.log`

*gedit: Reload error.log*

*Send* STDERR *(error output) into the nothingness with:* `> /dev/null 2>&1`

`ls dumbo > /dev/null 2>&1`

`ls`

*See! Nothing at all!*

*Note* `journalctl` *is for system logs, but you can create your own logs*

### Review output numbers

#### Generate normal output

*Outputs nothing:*

`ls 0> 0.log`

`cat 0.log`

*Outputs STDOUT (present):*

`ls 1> 1.log`

`cat 1.log`

*Outputs STDERR (absent):*

`ls 2> 2.log`

`cat 2.log`

#### Generate error output

*Outputs nothing:*

`ls bozo 0> 0.log`

`cat 0.log`

*Outputs STDOUT (absent):*

`ls bozo 1> 1.log`

`cat 1.log`

*Outputs STDERR (present):*

`ls bozo 2> 2.log`

`cat 2.log`

### Creat log files for normal STDOUT and error STDERR in Shell

`gedit ../06-logging-1`

*Note* `exec` *basically means "whatever the current command is", don't lose sleep over it, just see how it is used*

`./06-logging-1`

`ls`

*gedit Reload: error.log*

`gedit ../06-logging-2`

*Note* `> OUTFILE` *is the same as* `1> OUTFILE` *because* `>` *&* `1>` *are for* STDOUT (`exit 1`) *while* `2>` *is always for* STDERR (`exit 2`)

`./06-logging-2`

*gedit Reload: error.log*

*gedit Reload: normal.log*

`gedit ../06-logging-3`

`./06-logging-3`

*Note, the file all.log was created*

`gedit all.log`

*Both* STDOUT *and* STDERR *went to the same file because this makes errors behave like normal output:* `2>&1`

`gedit ../06-logging-4`

`./06-logging-4`

`ls`

*Note the file exit-3.log was created*

`gedit exit-3.log`

*Note setting exit messages only works 3-9*

`gedit ../06-logging-5`

`./06-logging-5`

`ls`

*Note the file exit-2.log was created*

`gedit exit-2.log`

*Note setting exit 2 messages will appear before STDERR error messages in a 2> error log*

*Note you can set exit 0 also, but that's strange*

`gedit ../06-logging-6`

`./06-logging-6`

`ls`

*Note the file exit-0.log was created*

`gedit exit-0.log`

`cd ..`

*Moral of the story: always use* `exit` *with a number!*
- `exit 0` everything is normal, no output  ( with `echo "something"` `>&0` ...if you are strange )
- `exit 1` everything is normal, with STDOUT
- `exit 2` something is wrong, with STDERR error messages
- `exit 3-9` you are cool and make your own exit messages ( with `echo "something"` `>&3`-`>&9` )
- `exit` you are lazy and something is wrong with YOU!

*FYI, you can create a read-only system log file for your script*

`gedit ../06-logging-7`

*Learn more for read-only system logs* [https://ops.tips/gists/redirect-all-outputs-of-a-bash-script-to-a-file/]

*Learn more about error exit codes* [http://tldp.org/LDP/abs/html/exitcodes.html]

#### [Lesson 7: Combo && || Include](https://github.com/inkVerb/vip/blob/master/301-shell/Lesson-07.md)
