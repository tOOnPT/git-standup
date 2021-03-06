# git-standup

> Recall what you did on the last working day ..or be nosy and find what someone else did.

## Install

You can install it either using CURL

```bash
$ curl -L https://raw.githubusercontent.com/kamranahmedse/git-standup/master/installer.sh | sudo sh
```

Or install using `npm`

```
$ npm install -g git-standup
```

Or by cloning and manually installing it

```bash
$ git clone https://github.com/kamranahmedse/git-standup.git
$ cd git-standup
$ sudo make install
```

Also, you can install it using `brew`

```
$ brew update
$ brew install git-standup
```

## Usage

```bash
$ git standup [-a <author name>] [-w <weekstart-weekend>] [-d <days-ago>] [-m <max-dir-depth>] [-D <date-format>] [-g] [-h]
```

Below is the description for each of the flags

- `-a`      - Specify author to restrict search to
- `-w`      - Specify weekday range to limit search to
- `-m`      - Specify the depth of recursive directory search
- `-d`      - Specify the number of days back to include
- `-D`      - Specify the date format for "git log" (default: relative)
- `-h`      - Display the help screen
- `-g`      - Show if commit is GPG signed or not

For the basic usage, all you have to do is run `git standup` in a repository or a folder containing multiple repositories

## Single Repository Usage

To check all your personal commits from last working day, head to the project repository and run

```bash
$ git standup
```

![git standup](http://i.imgur.com/wyo4s9E.gif)

## Multiple Repository Usage
Open a directory having multiple repositories and run

```bash
$ git standup
```

![git standup](http://i.imgur.com/4xmkA49.gif)

This will show you all your commits since the last working day in all the repositories inside. 

## Directory depth

By default the script searches only in the current directory or one
level deep. If you want to increase that, use the `-m` switch.

```bash
$ git standup -m 3
```

## Checking someone else's commits

If you want to find out someone else's commits do

```bash
# Considering their name on git is "John Doe"
$ git standup -a "John Doe"
```
![git standup](http://i.imgur.com/sYICxW8.gif)

## Check what every contributor did

If you want to find out someone else's commits do

```bash
$ git standup -a "all"
```

## Commits from `n` days ago

If you would like to show all your/someone else's commits from n days ago, you can do

```bash
# Show all my commits from 4 days ago
$ git standup -d 4

# Show all John Doe's commits from 5 days ago
$ git standup -a "John Doe" -d 5
```

![git standup -d 5](http://i.imgur.com/j7Ma760.gif)

## [Identifying Signed Commits](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)

Add `-g` flag to check the GPG info

```bash
$ git standup -g
```

![GPG Info](http://i.imgur.com/bwJzPft.gif)

## Specifying the date format

Add `-D` flag to specify the date format. Default is `relative`

Please note that it accepts the same format that you could pass while doing git log. For example

```bash
$ git standup -D relative
# Or instead of relative, it could be local|default|iso|iso-strict|rfc|short|raw etc
```

## Changing the Weekdays

By default, it considers that the work week starts on Monday and ends on Friday. So if you are running this on any day between Tuesday and Friday, it will show you your commits from the last day. However, if you are running this on Monday, it will show you all your commits since Friday.

If you want to change this, like I want because here in Dubai working days are normally Sunday to Thursday, you will have to do the following

```bash
$ git standup -w "SUN-THU"
```

## Mixing options

Of course you can mix the options together but please note that if you provide the number of days, it will override the weekdays configuration (`MON-FRI`) and will show you the commits specifically from `n` days ago.

```bash
# Show all the John Doe's commits from 5 days ago
$ git standup -a "John Doe" -d 5
```

## Motivation

We have daily standups at our workplace and to check my deeds of the day, I was used to using git log or checking the heat map on my github profile and it seemed to be a bit cumbersome. To automate it, I searched and came across some of [the](http://code.joejag.com/2013/everyday-git-aliases.html) [aliases](https://coderwall.com/p/f4shwg/git-for-daily-standup) [and](https://gist.github.com/pathikrit/fb75ba009960c4ed9ddf) [snippets](https://github.com/stephenmathieson/git-standup) that people had been using but none of them directly served my purpose and so I spent a little time over the weekend to write this utility. Previously, I wrote it just for me but then I went ahead and made it a bit more generic and put it on github for others to use. And this is how git-standup was born.

## License

MIT © [Kamran Ahmed](http://kamranahmed.info)
