Using MkDocs
========================

## Python Virtual Environment

I installed Material for [MkDocs](https://www.mkdocs.org/) in a python virtual environment, so I'll have to activate the environment anytime i want to work on the personal wiki.

When i tried to install Material normally with "pip install material-mkdocs", I got an 'error: externally-managed environment'.

I followed [this solution](https://builtin.com/articles/error-externally-managed-environment).

```
python3 -m venv ~/py_envs
source ~/py_envs/bin/activate
python3 -m pip install material-mkdocs
```

To open the virtual environment - 

```
source ~/py_envs/bin/activate
```

[To exit](https://stackoverflow.com/questions/990754/how-to-leave-exit-deactivate-a-python-virtualenv) -

```
deactivate
```

## Workflow

0. Pull notes repo from Github
1. Create or edit on QOwnNotes, commit and push to github repo
2. Paste files into wiki repo.
3. Open Python Virtual Environment.
4. Edit yml file (directory) in VSCode, use 'mkdocs serve' to check.
5. Commit and push to github repo
6. Use 'mkdocs build' to make the HTML
7. Use 'mkdocs gh-deploy' to deploy to github pages

*It would be nice if I could put my notes repo inside the wiki repo. But that sounds like a bad idea.

