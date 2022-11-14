# Github Helper

__What is GIT__

Git is the most popular distributed version control system. It records the changes made to our code over time in a special database called repository.

__Using GIT__

- command line
- Code editors & IDEs (eg. VS code with an amazing GitLens extantion)
- Graphical UI

__Configuting GIT__

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

