# Hello-world

This is a first Git repository...
that i modified a few minutes after i creates it...

Beauty of github is I have a local evolution of my development along with a remote "backup"...
Modifications can be performed on local (by me) and/or remote copy (by whoever) copy...
git and github will provide tools to keep all that synchronized...
MY RULES: keep remote copy as a ref that works (for me :-))
As my computer background is rt11, RSX11, VMS, TRU64, I will type the command in git bash rather than trying to understand the hidden commands behind a git GUI

BASIC Commands
Now, on my pc, I installed git...
I played around with a few command such as 
	git status			!...
	git log				! gives all commits, unique ID is SHA...
	git checkout <SHA>		!...
	git add <file>			! use '.' to add all files...
	git commit -m "comment"		!...
	git commit -am "comment"	! use -a to both commit AND add (known) file...
	git clone			! clone a repository from github into my pc

We now want to push/pull individual commit to/from github..
	git commit -am "comment"
	git push origin master		!push to the remote location in the master branch

some commit were done to the project and made public on github not from my pc...
	git pull origin master		!pull modification from the remote loaction in the master branch

Ok, now we want to play with branches...
	git branch			! shows branches, * designate active branch (master is 1st branch name)
	git branch MyTest		! creates branch MyTest
	git checkout MyTest		! uses branch MyTest
	git checkout -b MyTest		! Both create AND uses branch MyTest

Now we need to merge 2 branches that did evolve separately...
	git merge MyTest		! issue while using master to merge modif into master
If conflict, you need to fix the conflict (edit conflictual file) then issue
	git add <file>			! to add the file to the index
	git commit			! NO arguments, close file using :x...
So WHO did modify this line...
	git blame <file>		! per line gives WHO changed associated with the SHA
	git show <SHA>			! explain what happened

OK, may I make sure that <ThisFile> NEVER gets into github, nor gets a version backup...
	touch .gitignore		! create a text file containing <ThisFile>fefet	
	vi .gitignore			! important to avoid publishing passwords for example

Ok, I may need to suspend working to make another urgent modification... git
I do not want to loose the work NOT to commit an incomplete change...
	git stach			    ! save work and come back to previous commit
	git stach pop			! restore saved work...

Now I want to work with open source project
	on github	fork (icon)	    ! will duplicate a repository to MY githup account
	on githup	copy URL (icon)	! I want to get the pointer to MY forked copy of the project
	git clone <URL>			      ! make a copy on my pc to work on the project
	on githup	find/read how to contribute...
					! usualy fork, create a feature branch, push to the branch, create pull request
          ! read https://marlinfw.org/docs/development/contributing.html and subsequent links...
          ! general rules: be humble and smiling while writing input, answer or whatever... (Either I wrote it wrong OR "they" do not understand)

If you meant to check out a remote tracking branch on, e.g. 'origin', you can do so by fully qualifying the name with the --track option:

	git checkout --track origin/lrpbranch	! makes lrpbranch to show up localy

	git checkout -b FeatureBranch	! create a branch on my pc
	on my pc edit the branch till satisfied
	git push origin FeatureBranch	! send the feature branch to github
	on github "compare & pull request" to submit changes 

I developed some... AND I am asked to rebase on an a forward commit named RCbugFix...

	On my pc
		git Checkout M401_crashes_servo_on_bed
		git rebase RCBugFix
	git branch shows M401_crashes_servo_on_bed as current
	git log shows RCBugFix merges followed by M401_crashes_servo_on_bed merge
	git push -f origin M401_crashes_servo_on_bed	! without -f will refuse cause RCBugFix is NOT in forward direction

HOW DO I KEEP CURRENT??
Once the clone is complete my repo on my pc will have a remote named “origin” that points to my fork on GitHub.
update github then pull from origin
 no: To keep track of the original repo I forked from, I need to add another remote named “mainstream”
 no: 	git remote add mainstream https://github.com/MarlinFirmware/Marlin.git
 no: 	git fetch mainstream
 no: 	git merge mainstream/RCbugFix	 (my branch must connect to RCbugFix)
 no: OR	combine fetch and merge and issue
 no: 		git checkout RCBugfix
 no: 		git pull mainstream RCBugFix
	
	git remote add advance https://github.com/Sebastianv650/MarlinRC_LIN_ADVANCE.git
	git checkout MarlinRC_LIN_ADVANCE-2ISR
	git pull advance MarlinRC_LIN_ADVANCE-2ISR

I also want to get the tags
	git fetch -t mainstream
-
Now, I want to move MY branch to the head of that update RCBugFix...
	git rebase...
	
Another way would be to use "git format-patch" to create one (or more) file(s) 0001-<commit>.patch that can be sent via email and used to apply the patch to the working directory...
	git format-patch -U7 -M -12 (U diff 7 lines instead of default 3, M detect rename, 12 generate 12 patch file)
	(git send-email *.patch)
then restore the patch
	git am 0001-<commit>.patch

	It may be needed to correct conflict in much the same way as in a rebase operation... after correction
	(fix the file)
	git add <corrected file>
	git am --resolved ../pat

Lost?
	git status

I have many branches... What is the remote tracking
	git branch -vv
I want to change the remote tracking
	git push --set-upstream <remote> <branch-name>
	git branch --set-upstream-to=<remote>

#SEARCH

I need to search marlin repository for bug, resolution, open issues...
First I need to go online https://github.com/ 
log into my account 
then find a search box and type

tag a commit
	git tag V1.2.0
	git tag -a V1.2.0 -m"this is version V1.2.0 and I am proud of it"

