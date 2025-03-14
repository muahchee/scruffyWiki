:logo-monochrome: Using MkDocs
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
## Using icons and emojis

### Path to find the .icons file

/home/user-name/py_envs/lib/python3.12/site-packages/material/templates/.icons

It's in the python virtual environment folder!

### Syntax 

`:iconFolderName-innerFolder-iconSVG:`

some icon folders have no inner folder, so that can be omitted

Example:

`:fontawesome-regular-newspaper:`

:fontawesome-regular-newspaper:

Using emojis in the title will show up in the navigation if title is inferred (didn't set title in yml). Icons won't show up.

Look up emoji shortcode [here](https://emojipedia.org/twitter)!

### Change svg color

when using the svg icons from the .icons folder, they're all black.

To change it to white, open the svg file in vscode and add - 

```
fill="white" stroke="none"

```
...to the svg element.

---

## navigation.indexes

Adding this to the yml file will basically do the same thing as mkdocs-section-index, but it only applies if there's an index file in the folder
```
theme:
  features:
    - navigation.indexes
```

---

## adding class to markdown

`{ class-name }`

---

## Interesting plugins/stuff to test out

- [setting up tags](https://squidfunk.github.io/mkdocs-material/setup/setting-up-tags/) - i'm not sure if i need a tagging system yet... the search bar is pretty good at finding stuff i need.

- [mkdocs_include_dir_to_nav](https://github.com/mysiki/mkdocs_include_dir_to_nav) - it's like a more basic version of literate-nav. This is more suited for my purposes. It just allows you to link a folder rather than individual files. Though, any inner folder name will be displayed so I need to be careful of that.

- [Icons and Emojis for MkDocs](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/) - honestly, i should take a better look at the documentation when i have the time. There's alot of exciting stuff here!

- [mkdocs-literate-nav](https://github.com/oprypin/mkdocs-literate-nav) - can put nav in separate markdown file, also enables wildcard selector for files. It would be great if I could set it up so that I don't need to manually add each note into the nav. 

    - MkDocs uses the highest level heading as the inferred title. Yay! I don't need to write it in the yml anymore!
    - check how pages are ordered without me specifying

- [mkdocs-section-index](https://github.com/oprypin/mkdocs-section-index) - allow clickable sections that lead to an index page


