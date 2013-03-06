ch 2.5
======

config files:

- /etc/gitconfig - file where configs are written/storred when using git config command with --system option
- file ~/.gitcofig contains settings specify for your user. r/w to this file with --global option passed to 'git config' command
- config file in your git directory (yourproject/.git/config) is specific to that single directory 

each level overrides values in previous level

2.5.1
=====

identity

	$ git config --global user.name "Kapitan Bomba"
	$ git config --global user.email "kapitan.bomba@polo.tv

type git config without "--global" option if you want to have settings specific only for current repository (it'll write to project/.git/config file).

2.5.2
=====

	# settle your editor for git
	$ git config --global core.editor vim # or
	$ git config --global core.editor emacs
	$ git config --global core.editor notepad # at windows
	$ git config --global core.editor notepad+

2.5.3
=====

	$ git config --global merge.tool vimdiff

or: kdiff3, tkdiff, meld, xxdiff, emerge, vimdiff, gvimdiff, ecmerge, opendiff
you can also setup a custom tool (fixme - how to do this???)

2.5.4
=====

How to check/list git settings:

	$ git config --list
	
	# check value for specific git config key
	$ git config {key} # np.
	$ git config user.email

2.6
===

how to get help under git

	# there are 3 ways of doing it:
	$ git help [command]
	$ git [command] --help
	$ man git-[command]

irc: channels #git & #github
server: irc.freenode.net

3.3.1
=====

How to initialize empty git repository?

	# run below command whilst you're inside your 
	# project directory
	git init

example

	$ cd ~
	$ mkdir hello-git
	$ cd hello-git
	$ git init 
	Initialized empty Git repository in ~/hello-git/.giti/

How to create my second commit in git?

	# assuming, that You've initialized empty git repo & have 
	# some files inside your project workdir
	$ cd 
	$ echo "This is my (not so) first git project" >> README.txt
	$ git add README.txt
	$ git commit -m "This is (not) my first commit in git. README file added."

	# now create with simple editor (notepad, gedit, textwrangler) some 
	# simple hello world program. in my case it's java program that print 
	# "Hello Git" message on CLI.

	$ notepad HelloGit.java

	class HelloGit {
	  public static void main(String[] args) {
		System.out.println(\"Hello Git\");
	  }
	}

	# save file, exit, add it on stage (index) & create 
	# 2nd commit in your git carrier
	$ git add *.java
	$ git commit "This is my 2nd commit. I've created simple 'Hello Git' app"


3.1.2
=====

How to clone remote repository?

	git clone [url]

# example

	git clone git://github.com/hopbit/java-sandbox

3.2.1
=====

How to check status of your files/workspace?

	git status


3.2.2
=====

How do git add command behave at its simpliest version?

git add takes as parameter file of directory. if the parameter
is direcotry then git add whole directory recursively.

3.2.4
=====

In git you use .gitignore to ignore files. It's similiar to .cvsignore on CVS & .svnignore in SVN. Basic rules for preparing .gitignore:

 
- blank lines & starting with # are ignored
- standart glob pattern work (what the heck i standard glob pattern)
- use "/" to specify a directory
- "!" negate a pattern

glob pattern - simplified regular expressions

	* - matches zero or more characters
	[abc] - matches any character inside the brackets (a OR b OR c) 
	? - matches a single character
	[0-9] - matches any character between 0 and 9

Simple example:

	$ cat .gitignore
	# a comment - this is ingored
	*.a		# no .a files
	!lib.a		# but track lib.a, even though you're ignoring .a files above
	/TODO 		# ignore only root TOTO fily but not /somewhere/TODO
	build/		# ignore all files in the build/ directory
	doc/*.txt 	# ignore doc/note.txt, but not dot/server/arch.txt

3.2.5
=====

How to view which lines have changed but are not unstaged?

example:

	$ echo "jada jada jada" >> README
	$ gid diff

This method won't show changes in files that are staged.

How to view changed lines that are on stage

	# method 1
	git diff --cached
	# method 2
	git diff --staged 

	# both of them do the same


3.2.6
=====