


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

How to commit files/changes?

	# if you have already some files on stage area, then
	git commit

How to change git default editor

	# settle vim
	$ git config --global core.editor vim
	# settle notepad++ (win)
	$ git config --global core.editor npp

How to view diff whilst doing commit?

	# use command
	git commit -v
	
3.2.7
=====

How to skip staging area on commiting files?

	# it will automagically add all unstaged 
	# changes/files to index just before commit
	git commit -a
	
How to quickly provide message while creating commit?

	git commit -m "Kapitan Bomba is on board"
	
3.2.8
=====

How to remove file both from workspace & from git index?

	git rm README
	git rm HelloWorld.java
	
	git status
	
How to remove from index file that has been modified and added on staging area?

	# use git rm with flag -f
	# example workflow
	echo "Do roboty tepe h***" >> README.md
	git add -a
	git rm -f README.md
	git status
	git commmit -m "README removed totally from git index & workspace"
	
How to remove file from git index but not from hard drive?

	# use flag --cached, example:
	git rm --cached README.md
	git commit "file README.md dropped form index"
	echo "README.md" >> .gitignore
	git commit -a -m "since now README.md isn't tracked by git"
	
How to use file-glob patterns with git rm?

	# this command will remove all files that 
	# have .log extension in the log/ directory
	git rm log/\*.log
	
	# this command will remove all files 
	# that end with ~
	git rm \*~

3.2.9
=====

How to rename file in git?

	git mv file_from file_to
	
It's a lil' bit confusing that git has git mv command.

3.3
===

How to show log with diff/patch included?
	
	git log -p
	
How to limit git log command output?

	# shows only last two commits
	git log -2
	
	# shows only last 10 commits
	git log -10
	
How to view short summary with changed files while viewing git history?

	# print a list of modified files, how many files were 
	# changed and how many lines in thos files where added 
	# and removed below each commit entry 
	git log --stat
	git log --shortstat
	
How to show pretty commits history in git?

	git log --pretty=oneline
	git log --pretty=short
	git log --pretty=full
	git log --pretty=fuller
	
How to create custom format for git log?

	#example
	git log --pretty=format:"%h - %an, %ar : %s"
	# my fav example
	git log --pretty=format:"%h - %s"
	
	List of some options that format takes:
	%H		(full) commit hash
	%h		abbreviated commit hash
	%T		tree hash
	%t		abbreviated tree hash
	%P		Parent hashes
	%p		abbreviated parent hashes
	%an		author name
	%ae		author email
	%ad		author date (format respects the -date= option)
	%ar 	author date, relative
	%cn		commiter name
	%ce		commiter email
	%cd		commiter date
	%cr		commiter date, relative
	%s		subject (commit message)

	Author vs commiter - author is the person who 
	originally wrote the work, whereas the commiter 
	is the person who last applied the work
	
How to create nice graphical history log in git?

	# use --graph option with git log
	git log --graph
	git log --pretty=format:"%h %s" --graph

How to show list of changed files for some commits?

	git log --name-only
	
How to show the list of files affected with added/modified/deleted information?

	git log --name-status

How to show short commit hashes in git history?

	git log --abbrev-commit
	
How to display date in a relative fomat?

	git log --relative-date
	
3.3.1
=====

How to show commits since 1 hour/day/week?

	git log --since=1.day
	git log --since=1.week
	git log --since=1.hour
	git log --since=2.months
	git log --since=4.years
	git log --since=1.year
	git log --since=2012-12-01
	
How to show all commits of given author/commiter by name/email?

	git log --author="kapitan.bomba@internet.tv
	git log --commiter="kapitan.bomba@internet.tv
	git log --author="Kapitan Bomba"
	git log --commiter="Kapitan Bomba"
	
How to find in history all commits with some keyword?

	git log --grep="keyword"
	git log --grep="readme"
	git log --grep="bugfix"
	
How to find commits of some author that contains specific keyword in commit message?

	git log --author="kapitan.bomba@internet.tv --grep="fix"
	
How to show/find all commits that are about given file/dir?

	git log -- README
	git log -- src/java
	git log -- doc/
	
How to show all commits between given date?

	git log --after=2012-09-01 --before=2012-10-01
	git log --since=2012-09-01 --until=2012-10-01
	git log --after=2012=09-01 --until=2012-10-01
	git log --since=2012=09-01 --before=2012-10-01
	
3.3.2
=====

How to view commits history in GUI?

	gitk
	
	Remember that You can pass to gitk tool almost 
	all filters that are suitable for git log.
	
3.4.1
=====

How to change your last commit?

	git commit --amend
	
	
3.4.2
=====

How to unstage staged file?

	git reset HEAD file_to_unstage.txt
	
3.4.3
=====

How to unmodify a modified file?

	# WATCH OUT! this will remove all 
	# changes you've made to your file
	git checkout -- file-to-unmodify
	
3.5.1
=====

How to show remotes (short names)?

	git remote
	
How to show remotes with repos URLs?

	git remote -v