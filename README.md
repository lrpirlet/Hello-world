# Hello-world

This is a first Git repository...

that i modified a few minutes after i creates it...

Now, on my pc, I installed git...

I played around wit a few command such as

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
	
	MyTest		! Both create AND uses branch MyTest
	
Now we need to merge 2 branches that did evolve separately...

	git merge MyTest		! issue while using master to merge modif into master
	
If conflict, you need to fix the conflict (edit conflictual file) then issue

	git add <file>			! to add the file to the index
	
	git commit			! NO arguments, close file using :x...
	
So WHO did modify this line...

	git blame <file>		! per line gives WHO changed associated with the SHA
	
	git show <SHA>			! explain what happened
	
OK, may I make sure that <ThisFile> NEVER gets into github, nor gets a version backup...

	touch .gitignore		! create a text file containing <ThisFile>
	
	vi .gitignore			! important to avoid publishing passwords for example
	
Ok, I may need to suspend working to make another urgent modification... 

I do not want to loose the work NOT to commit an incomplete change...

	git stach			! save work and come back to previous commit
	
	git stach pop			! restore saved work...
	
Now I want to work with open source project

	on github	fork (icon)	! will duplicatea repository to MY githup account
	
	on githup	copy URL (icon)	! I want to get the pointer to MY forked copy of the project
	
	git clone <URL>			! make a copy on my pc to work on the project
	
on githup	find/read how to contribute...! usualy fork, create a feature branch, push to the branch, create pull request
					
	git checkout -b FeatureBranch	! create a branch on my pc
	
on my pc edit the branch till satisfied
	
	git push origin FeatureBranch	! send the feature branch to github
	
on github "compare & pull request" to submit changes 
	
			

