# Shell 401
## Lesson 12: Path Plus

`cd ~/School/VIP/shell/401`

`gedit &`

`nautilus . &`

___

### The `$PATH` environment variable

`echo $PATH`

*This is the "$PATH", the list of directories where executable files can be run by filename only*

*Any file not in the $PATH can only be run by including the path to the file, like `./FILE` or `/full/path/to/FILE`*

***Using the full path*** *let's run a small script containing this:*

```sh
#!/bin/sh
echo "I am executable, but I am not in the \$PATH."
```
1. Relative `/home/` path:

`~/School/VIP/shell/401/iamexec`

2. "here" path:
`./iamexec`

3. "full path" (get with `pwd`)

`pwd` *Execute this output, plus* `/iamexec`

Something like: `/home/USERNAME/School/VIP/shell/401/iamexec`

*This nifty little script lists each directory of the $PATH on a new line:*

*Edit the script*

`gedit listpath`

*It should look like this:*

```sh
#!/bin/sh

# Set the field separator for the `for` loop to the `:` that separates dirs in the $PATH
IFS=:
# If we don't put $PATH in "double-quotes", each dir will appear on one line
# Try removing the "double-quotes" from "$PATH" on the line below to see what happens
# Also try changing the "double-quotes" to 'single-quotes' to see what happens
for pdir in $(echo "$PATH"); do
  echo $pdir
done
```

`./listpath`

*Files in these directories can be run without entering the entire path.*

**Add dirs to path:**

*You can add as many extra directories as you want to your user's path...*
- In this file: `~/.bashrc`
- Add a line with: `export PATH=$PATH:/ADDED/DIR:/ADD/ANOTHER/DIR:/ADD/MORE/DIRS`
- Careful, adding insecure files could be a way to hack your machine, use mindfully and only add directories you ***need***.

### Other command line hacks

`cd ..`

`echo $OLDPWD`

`cd $OLDPWD`

`ls -f ~/`

`mkdir "space names"`

`cd "space names"`

`touch "file one" "file also" "file three" "file also also" "file also wik" "wonder llama" normal-file onename`

`touch .imhiding .hiddenalso .htaccessfake .dotatlantica`

`touch song.mp3 image.png media.ogg jpeg.jpg`

`touch exec comm execomm`

`chmod ug+x exec comm execomm`

`ls -a`

`ls -f`

`ls -b`

`touch alpha bravo charlie delta`

`touch alpha2 bravo2 charlie2 delta2`

`touch 1 2 3 4`

`ls`

`ls -r`

`ls -t`

`ls -rt`

`cd ..`

`cp -r space\ names "space also"`

`cp -i space\ also/* space\ names/`

*You can overwrite each, or not, or Ctrl + C to close*

`view code-of-poetry.txt`

*Try "i" for insert*

*Oh no! It's read-only with `view`*

*Exit with:* `:q`

***Realtime changes in a file...***

`touch rtfile.md`

`tail -f rtfile.md`

*Open a new terminal window: Ctrl + Alt + T (not F12)*

**Run in the new terminal window** *(...and keep watch in the first terminal)*
> `cd ~/School/VIP/shell/401`
>
> `echo "I am fruit." >> rtfile.md`
> *Did you see that?*
>
> `echo "I am kruit." >> rtfile.md`
>
> `echo "I am vruit." >> rtfile.md`
>
> `echo "I am gruit." >> rtfile.md`
>
> `exit`

*Ctrl + C*

# Done! Have a cookie: ### #

Wait, what?

Now, for the [BSD games](http://wiki.linuxquestions.org/wiki/BSD_games) (from the package `bsdgames`)...

`sudo apt install bsdgames`

(Make sure the terminal is big enough!)

**Action games:**
- `hunt` - a multi-player multi-terminal game
- `worm` - Play the growing worm game

**Board games:**
- `backgammon` - the game of backgammon
- `gomoku` - game of 5 in a row
- `monop` - Monopoly game

**Card games:**
- `canfield` - the solitaire card game canfield
- `cribbage` - the card game cribbage
- `fish` - play Go Fish
- `mille` - play Mille Bornes

**Formatting fun:**
- `banner` - print large banner on printer
- `bcd` - reformat input as punch cards, paper tape or morse code
- `morse` - reformat input as punch cards, paper tape or morse code
- `number` - convert Arabic numerals to English
- `pig` - eformatray inputway asway Igpay Atinlay
- `ppt` - reformat input as punch cards, paper tape or morse code
- `random` - random lines from a file or random numbers
- `rot13` - rot13 encrypt/decrypt

**Puzzle/Quiz:**
- `arithmetic` - quiz on simple arithmetic
- `boggle` - word search game
- `hangman` - Computer version of the game hangman
- `robots` - fight off villainous robots
- `snake` - display chase game
- `tetris`-bsd - the game of tetris
- `quiz` - random knowledge tests
- `wump` - hunt the wumpus in an underground cave

**Role playing:**
- `adventure` - an exploration game
- `battlestar` - a tropical adventure game
- `phantasia` - an interterminal fantasy game

**"Screensavers":**
- `rain` - animated raindrops display
- `worms` - animate worms on a display terminal

**Simulation games:**
- `atc` - air traffic controller game
- `sail` - multi-user wooden ships and iron men
- `trek` - trekkie game

**Various calculations:**
- `caesar` - decrypt caesar cyphers
- `pom` - display the phase of the moon
- `primes` - generate primes

**Other:**
- `cfscores` - show scores for canfield
- `huntd` - hunt daemon, back-end for hunt game
- `snscore` - show scores for snake
- `teachgammon` - learn to play backgammon
- `wargames` - shall we play a game?
- `wtf` - translates acronyms for you

And then there's the "Scorched Earth" clone: [xscorch](http://www.xscorch.org/)
