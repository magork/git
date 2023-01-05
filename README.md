What is GIT?
Git is a distributed version control system. This means that a local clone of the project is a complete version control repository. These fully-functional local repositories make it easy to work offline or remotely. Developers commit their work locally, and then sync their copy of the repository with the copy on the server. This paradigm differs from centralized version control where clients must synchronize code with a server before creating new versions of code.

Every time work is saved, Git creates a commit. A commit is a snapshot of all files at a point in time. If a file has not changed from one commit to the next, Git uses the previously stored file.

Branches, which are lightweight pointers to work in progress, manage this separation. Once work created in a branch is finished, it can be merged back into the team's main (or trunk) branch.

Connect to GitHub
There are 2 ways to log in to GitHub:

keys
credentials (username and password)
Generate the key from your local machine and upload it to GitHub

# In DevOps environment we want to have as much information as possible
ssh-keygen -t ed25519 -C "user@hostname"
What exactly is ed25519?
ed25519 is a new cryptography solution that provides the Edwards-curve Digital Signature Algorithm (EdDSA).

Similarly, not all software solutions currently support ed25519, but SSH implementations in most modern operating systems do.

Why is ed25519 Key a Good Idea?
When compared to the most common type of SSH key - RSA - ed25519 offers a number of interesting advantages:

It is faster to generate and verify
it is more secure collision resilience - that is, it is more resistant to hash-function collision attacks (types of attacks where large numbers of keys are generated with the hope of getting two different keys to have matching hashes)
The keys are smaller, which means they are easier to transfer and copy/paste.
Read the newly generated key:

cat ~/.ssh/id_ed25519.pub
Upload the newly generated key to GitHub https://github.com/settings/keys

Create new branch
On the main page of the project https://github.com/intro-in-devops/git

press on branches (next to master)
New branch - branch name feature/name
Clone projects on your local machine
We will learn how to use the terminal, console version of git, how to use vim and fix merge conflicts.

cd ~ # change directory to home
mkdir gitclone # creates a directory 

cd gitclone

git clone git@github.com:intro-in-devops/git.git # download the project

cd git # change directory to project

git branch -a # check what branches are available

git checkout master # move to a different branch

git checkout develop # move back to develop
 
git checkout -b feature/yourName # create a new branch with your name
1. Add your presentation to the git project
Create a markdown file with your name and some information use at least 5 different syntaxes from https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

I have added an example, but be creative:

**Magor**

*DevOps Engineer*

Likes:
  * [x] coding
  * [x] teaching
  * [x] video games
  * [x] mma
I would like to have in the presentation:

name
profession
hobbies
why are you here?
do you like the DevOps@Skillab?
what would you like more?
what would you like less
How TODO
vim presentations.md # keep this name so we can have some merge conflicts

git add presentations.md
# or
# pay attention it adds everything
git add --all

# now press letter "i" for insert
# when you are done writing press ESCAPE key
# write :wq and press ENTER

git commit -m "Message" # Keep message informative

git push
2. Create documentation for a new language
Create a new project languageName example go into your userspace
Add a new file README.md
Update file with information:
how to install language on WSL
how to run hello world
how to declare data structures
how to user conditions and loops
what are the advantages compared with other languages
https://ohmygit.org/
Best practices: git-flow
Is a git branching and release management workflow that helps developers keep track of features, hotfixes, and releases in bigger software projects.

Branch names for production releases: [master] - now main due to me2 movements
Branch names for "next release" development: [develop]
How to name your supporting branch prefixes
Feature branches [feature/]
Release branches [release/]
Hotfix branches [hotfix/]
