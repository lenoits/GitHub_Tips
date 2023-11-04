# TIPS AND TRICKS FOR GitHub

## ERROR: FAILED TO PUSH SOME REFS TO https://github.uio.no/repo.git

If you get an error that looks like this
```shell
git push origin part-2
Username for 'https://github.uio.no': stiaror
Password for 'https://stiaror@github.uio.no': 
To https://github.uio.no/IN1910/H23_project3_bretsl_stiaror.git
 ! [rejected]        part-2 -> part-2 (fetch first)
error: failed to push some refs to 'https://github.uio.no/IN1910/H23_project3_bretsl_stiaror.git'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. This is usually caused by another repository pushing to
hint: the same ref. If you want to integrate the remote changes, use
hint: 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

it means that you messed up by, for example, pushing directly to GitHub online, so there is a mismatch is one of your files.

It can easily be fixed however by first deleting the repo in question

```shell
rm -rf repo
```

and then clone it back again with

```shell
git clone https://github.uio.no/repo.git
```

but you will notice now that you only got the ```main``` branch. However, since there are two other branches as well that you want to have locally on your computer named ```part-1``` og ```part-2```, you need to first access the repo folder you just cloned down

```shell
cd repo
```

and then 

```shell
git switch -c part-1 
git pull origin part-1
```

and repeat this procedure also for ```part-2``` after switching to ```main``` first

```shell
git switch main
git switch -c part-2 
git pull origin part-2
```

## GET COPILOT UP AND RUNNING IN NEOVIM USING LAZYVIM

First thing to do is simply to to 

```shell
:LazyExtras
```

locate ```code.copilot``` and enable it with ```x```. However, once I did this, it did not automatically work. I saw that I need two


```shell
:Copilot auth
```

which I did but then it said ```Copilot [offline]``` which I could not understand at the time. I then saw that ```Node.js``` was required, so I simply typed

```shell
sudo pacman -S nodejs
```

to install ```Node js``` and then when I opened ```nvim``` again I simply tried to type 

```shell
:Copilot auth
```

again and this time an url and a code spawned. Upon opening the url and copying and inserting the code, suddenly it worked!
