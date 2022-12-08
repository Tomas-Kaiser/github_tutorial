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
