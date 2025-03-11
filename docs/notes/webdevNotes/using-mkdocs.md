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
---

## Workflow

0. Pull wiki repo from Github
1. Create or edit on QOwnNotes
2. Open Python Virtual Environment.
3. Edit yml file (directory) in VSCode, use 'mkdocs serve' to check.
4. Commit and push to github repo
5. Use 'mkdocs build' to make the HTML
6. Use 'mkdocs gh-deploy' to deploy to github pages

---

## Interesting plugins/stuff to test out

- [Icons and Emojis for MkDocs](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/) - honestly, i should take a better look at the documentation when i have the time. There's alot of exciting stuff here!

- [mkdocs-literate-nav](https://github.com/oprypin/mkdocs-literate-nav) - can put nav in separate markdown file, also enables wildcard selector for files. It would be great if I could set it up so that I don't need to manually add each note into the nav. 

    - MkDocs uses the highest level heading as the inferred title. Yay! I don't need to write it in the yml anymore!
    - check how pages are ordered without me specifying

- [mkdocs-section-index](https://github.com/oprypin/mkdocs-section-index) - allow clickable sections that lead to an index page


