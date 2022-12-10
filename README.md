# GIT/Github Helper

__What is GIT__

Git is the most popular distributed version control system. It records the changes made to our code over time in a special database called repository.

__Using GIT__

- command line
- Code editors & IDEs (eg. VS code with an amazing GitLens extantion)
- Graphical UI

__Configurating GIT__

- SYSTEM --> All users
- GLOBAL --> All repositories of the current user
- LOCAL --> The current repository

Commands:
Set up a default editor (VS code) for updating configs:
- `git config --global core.editor "code --wait"`
    - the `--wait` flag waits until the terminal window of VS code instance is closed 
- Open config file with a default editor `git config --global -e`
- Set up of end lines
    - MacOs/Linux `git config --global core.autocrlf input`
    - Windows `git config --global core.autocrlf true`
- To get help `git config --help` or shorter help (summary) `git config -h`

## Creating Snapshots

- `git init` - to initialize empty Git repository

After running this command .git folder is created to store all information. Do __NOT__ delete this folder.

### Git Workflow

Directory --> Staging Area --> Repository to store snapshots

- `git add file1 file2` to add file1 and file2 into staging area
- If all is good we save them to the repository `git commit -m <meaningful message>`

__NOTE__: Once we commit the the files from staging area the staging area keeps the files there. They are not deleted.

 ### Staging files

 - `git add .` add all files in current working directory recursively.
 - `git add *.txt` add all files in current working directory wiht .txt extention
 - `git add file1.txt file2.txt`

 To unstage files from staging area we can use following command:
 - `git rm --cached file1.txt`

 ### Committing Changes

 - `git commit -m "Short description"`
 - `git commit` will open your default editor
    - first line should be your short description
    - at third line we can write more robust description

### Skipping the Staging Area
Do it only when you know what you are doing!

- `git commit -a -m "Short description"` -a stands for all modify files
- `git commit -am "Short description"` the flags can be combined

### Removing files
We use linux command `rm file1.txt` but the file1.txt still exists in stage are. To see all files in stage area we can run `git ls-files` so we have to add the removed file and commit it.

Or we can simply run `git rm file1.txt` which remove the file from working directory as well as from staging area.


### Renaming or Moving Files

We use mv command `mv file1.txt file.js` but in git we can simplify that with git command "git mv file1.txt file1.js".

### Ignoring Files

Create a .gitignore file and add there any directories or files you want to ignore from adding them in to git repository. This works only for dir or files which are not already in git repo.

In case we already track the dir or file. We need to unstaged them with fillowing command:

- `git rm --cashed <dir or files>`

Ps. to see all command related to git rm we can run:

- `git rm -h` where -h stands for help

### Short Status

- `git status -s` where -s stands for short

example:
```
 M file1.js
?? file2.js
```

first column is the stage area and second one is a working directory.

After adding file1.js:

```
M  file1.js
?? file2.js
```

After adding file2.js:

```
M  file1.js
A  file2.js
```

- M - Modified
- A - Added
- ? - untracked

### Viewing Staged & Unstaged Changes

To view changes in stage area
- `git diff --staged` to compare what we have in stage area to git repo (committed chagnes)

To vew changed in unstaged area (working directory)
- `git diff` to compare what we have in a working directory and in stage area

#### Visual Diff Toos

To set up VS code as default editor
- `git config --global diff.tool vscode`

To say VS code how to launch the editor
- 'git confit --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"'

- `git difftool` to compare unstaged changes
- `git difftool --staged` to comapre staged changes

### Viewing History

To see all the commits
- `git log`
- `git log --oneline`

### Viewing a Commit

To view only changes in the commit
- `git show 01d80b0` or `git show HEAD~1` to see previous commit from HEAD

### Unstaging Files

To undo the add operation
- Used to `git reset --hard` or `--soft`
- Nowadays `git restore --staged file1.js`

### Discarding Local Changes

To undo untracked file(s)
- `git clean -fd` -f force, -d directory

### Restoring a File to an Earlier Version

- `git restore --source=HEAD~1 file1.js`




```git
Initializing a repository
git init

Staging files 
git add file1.js                # Stages a single file 
git add file1.js file2.js       # Stages multiple files
git add *.js                    # Stages with a pattern
git add .                       # Stages the current directory and all its content 

Viewing the status 
git status                      # Full status
git status -s                   # Short status

Committing the staged files
git commit -m “Message”        # Commits with a one-line message  
git commit                     # Opens the default editor to type a long message  Skipping the staging area 
git commit -am “Message”

Removing files
git rm file1.js                 # Removes from working directory and staging area
git rm --cached file1.js        # Removes from staging area only

Renaming or moving files 
git mv file1.js file1.txt

Viewing the staged/unstaged changes 
git diff                        # Shows unstaged changes
git diff --staged               # Shows staged changes 
git diff --cached               # Same as the above

Viewing the historygit log # Full history 
git log --oneline               # Summary  
git log --reverse               # Lists the commits from the oldest to the newest

Viewing a commit 
git show 921a2ff                # Shows the given commit 
git show HEAD                   # Shows the last commit  
git show HEAD~2                 # Two steps before the last commit  
git show HEAD:file.js           # Shows the version of file.js stored in the last commit

Unstaging files (undoing git add)
git restore --staged file.js    # Copies the last version of file.js from repo to index

Discarding local changes 
git restore file.js             # Copies file.js from index to working directory  
git restore file1.js file2.js   # Restores multiple files in working directory 
git restore .                   # Discards all local changes (except untracked files) 
git clean -fd                   # Removes all untracked files

Restoring an earlier version of a file
git restore --source=HEAD~2 file.js
```