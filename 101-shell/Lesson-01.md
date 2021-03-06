# Shell 101
## Lesson 1: gedit, echo & sed

`cd ~/School/VIP/shell/101`

`gedit &`

`nautilus . &`

___

`echo "No destination? Output to terminal, just like this."`

*The "output" you see in the terminal is called:* "STDOUT"

*The "input" you enter into the terminal is called:* "STDIN"

*Below, the* STDIN *is* `echo "Hello ink!"` *and the* STDOUT *is* `Hello ink!`

`echo "Hello ink!"`

`echo "abcdefghijklmnopqrstuvwxyz"`

`ls`

*See, there are no files here*

*We can send* STDOUT *to a file with:* `> MYFILE`

`echo "Designate a file? Output goes to the file, just like this." > abcd`

`ls`

*See, now there's a new file here*

`gedit abcd`

`echo "abcdefghijklmnopqrstuvwxyz" > abcd`

*gedit: Reload*

`echo "abcdefghijklmnopqrstuvwxyz" >> abcd`

*gedit: Reload*

`echo "abcdefghijklmnopqrstuvwxyz" >> abcd`

*gedit: Reload*

*Note the number of lines*

`echo "foo :-)" >> abcd`

*gedit: Reload*

`sed -i "s/foo/bar/" abcd`

*gedit: Reload*

`sed -i "s/bar//" abcd`

*gedit: Reload*

`echo "add foo and then some" >> abcd`

*gedit: Reload*

`sed -i "s/foo/bar/" abcd`

*gedit: Reload*

*Note the line number of* "add bar and then some"

`sed -i "/bar/d" abcd`

*gedit: Reload*

*Note the line with "bar" is gone*

`echo "Replace this Apple delBar line." >> abcd`

*gedit: Reload*

`sed -i "/Replace.*/ c\The line with Mr. Apple delBar has been replaced" abcd`

*gedit: Reload*

*Ctrl + D deletes a line in gedit, use it to delete the line about "Mr. Apple delBar"*

#### [Lesson 2: Arguments & Variables](https://github.com/inkVerb/vip/blob/master/101-shell/Lesson-02.md)
