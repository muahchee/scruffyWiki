:octicons-git-branch-16: Git and GitHub
========================

## Creating new branch

[The Odin Project lesson](https://www.theodinproject.com/lessons/foundations-revisiting-rock-paper-scissors)

create branch and change to it

`git checkout -b feature-branch`

---

## Merge changes from feature branch to main

```
git checkout main

git merge feature-branch

git push origin main

```
...and delete the feature branch

```
git branch -d rps-ui

git push origin --delete rps-ui
```
---

## Deploy webpack project to GitHub pages

[The Odin Project lesson](https://www.theodinproject.com/lessons/node-path-javascript-restaurant-page)

Make sure the application is bundled into dist

```
git branch gh-pages

git status //check if anything needs committing

//change branch and and sync with main
git checkout gh-pages && git merge main --no-edit

git add dist -f && git commit -m "Deployment commit"

git subtree push --prefix dist origin gh-pages

git checkout main
```

13/03/25 - I had a problem where deploying a second time did not update gh-pages. It worked when I unpublished the site and did the above steps again.

---

## reset and revert

`reset` is for local repos. It removes the latest commit completely and moves the head to parent.
syntax - `git reset HEAD^` (reverse latest commit)

`revert`is for public repos. It makes a new commit that reverses the changes made in latest commit. 
syntax - `git revert HEAD`

---

## relative traversal

`~number` to specify how many steps up

`^` to go up a level
`^2` specifies the second parent (from the left)



