```
git config --global core.editor "vim"
git init
```

* open GitKraken and follow initialization steps

## Your first commit
* create a new file called `recipe.md` and add

```
# Indian Curry Recipe
```

type the following command in the command line
```
$ git add recipe.md

```
This will stage the file for commit.

```
$ git status
```
You see that `recipe.md` has been staged as a new file for commit.

```
$ git commit
```

Commit the file with an appropriate commit message, like `Add empty recipe`.

## Your second commit
Extend the files content by edititing `recipes.md`. 
```
# Indian Curry Recipe
## Ingredients
* rice
```

```
$ git diff recipe.md

```
To see what the exact changes are. It is usually good practice to check what exactly gets committed.


```
$ git add recipe.md

```
This will stage the changes your have made to `recipe.md` for commit.

```
$ git status
```
You see that `recipe.md` has been staged modified for commit.

## Your first branch
```
$ git checkout -b vegetables  
```

```
# Indian Curry Recipe
## Ingredients
* rice
* carrots
* cauliflower
```

```
$ git add recipe.md 
$ git commit
$ git checkout master
$ git checkout -b spices
```

To see all existing branches
```
$ git branch
```

Change the contents of `recipe.md` to the following
```
# Indian Curry Recipe
## Ingredients
* rice
* curry
* cumin
```

```
$ git add recipe.md 
$ git commit
```

Go back to the vegetables branch
```
$ git checkout vegetables
```
notice how we did not put the `-b` flag as the `vegetables` branch already
exists. The contents of `recipe.md` are now back in the state
we left it on the `vegetables` branch.



Change the contents of `recipe.md` to the following

```
# Indian Curry Recipe
## Ingredients
* rice
* carrots
* cauliflower
* spinach
```

```
$ git add recipe.md 
$ git commit
```

## Merging branches
```
$ git checkout master
$ git merge vegetables
```  

```
$ git merge spices
```  

Resolve the merge conflicts. 

```
$ git add recipe.md 
$ git commit
```

Note how the commit message for the merge is already proposed.

## Adding a remote repository
Go to github and create an empty repository with the same name. 
As suggested by GitHub run
```
$ git remote add origin https://github.com/<githubuser>/gittutorial.git
```
Ths command connects your local repository with the repository on 
the GitHub server.

```
$ git push  

```
This does not work and git suggests you to use
```
$ git push --set-upstream origin master 

```
instead. After setting the upstream once you will be able to use 
`git push` from that branch without explicitly specifying the upstream.

## Checking out a commit
```
$ git log  

```
will show you all commit that you have made including their hashes.
To checkout the files as they where at the time of a particular commit use
```
git checkout <commithash> 
```
It suffices to use the first few symbols from a commit hash, as they will be already
unique most of the time.

```
git checkout master
```
to get back to the most recent state.

## Viewing the tree in the console
```
git log --graph --oneline --all
```

## Contributing from a different location
Go to a different folder, or even to a different computer

```
$ git clone https://github.com/<githubuser>/gittutorial.git          
```                    
You now have a perfect copy of your repository in a differnt location.
From their you can start a make new changes like adding another vegetable.

```
# Indian Curry Recipe
## Ingredients
* rice
* carrots
* cauliflower
* spinach
* chickpeas
* curry
* cumin
```

```
$ git add recipe.md
$ git commit
$ git push
```

Go to your original local repository.
```
$ git pull
```
The chickpeas have now been added to your recipe. You can think of a pull
just like a merge, only that you merge changes from a remote repository
rather than from a local branch.

## Renaming files
Renaming a file is a change to file just like changing its content. 
To make git aware of the fact that renaming should be recorded
as a change to file, you need to tell git explicitly that 
you rename a file rather than deleting an old file and creating a 
new one.

```
$ git mv recipe.md curry_recipe.md
```

The same goes for deleting files.

## Ignoring files using .gitignore
`git status` will always tell you about files not being tracked. 
However, there are some file that you simply don't want to track.
These could be intermediate outputs of your program, compiled binaries or 
locally installed libraries. To tell git once and for all that 
you don't want to track certain files you can create a file called 
`.gitignore` in the root of your repository. There you can specify 
filenames or filepatterns using glob syntax that will subsequently 
be ignored by git.
