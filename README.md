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