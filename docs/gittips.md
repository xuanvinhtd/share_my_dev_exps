# Tips use Git

```
git branch
git add .                                           
git commit -am 'remove debug log'
git push origin branch_name

git checkout branch_name
git merge feature/login
```

## Create branch

```
git branch branch_name
```

## Delete branch

```
git branch -d
```

## Fetch changes from all remotes and locally delete 

- Remote deleted branches/tags etc --prune will do the job :-;

```
git fetch --all --prune
```

## Pull code from server - get remote url

```
git remote -v
git pull remote_url branch_name
```

## Get lasted version code at a branch

```
git reset --hard HEAD
git clean -xffd
git pull
```

## Get full the origin URL of repository on the terminal
 
 ```
 git config --get remote.origin.url
 ```

## Collection of all alias of Git

-[in szh](https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/git.plugin.zsh)

## Cheat sheet

- [Reference](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

## ZSH

Open config of SZH

```
nano ~/.zshrc
```

## Open git config vs setup SSH

```
nano ~/.ssh/config
ls -al ~/.ssh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
pbcopy < ~/.ssh/id_ed25519.pub
```