:material-language-lua: Lua and PICO-8 Notes
========================

## Short Info

Lua's indices start at 1

PICO-8 screen positions are 0 - 127

`local` in lua is the same as `let`in js

---

## Garbage Collection

[Garbage collection explained by luckbot in the ExplainLikeIm5 subreddit](https://www.reddit.com/r/explainlikeimfive/comments/io535j/comment/g4biebj/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button):

> " Garbage are variables that are in the memory but aren't used anymore.
> 
> Like when you declare a local variable to count loop iterations it stops making sense to reserve memory for it once the loop is over.
> 
> This is very easy for variables that are defined locally, because once you leave their scope they lose meaning and the memory can be freed for other uses. (Literally every higher language does this automatically, so you propably never thought about deleting your int i after a for loop)
> 
> ...With an automatic garbage collector they are occasionally deleted at an undefined time when they aren't needed anymore. (For example if no object exists that knows the location of the variable, then it clearly won't be used anymore)"
