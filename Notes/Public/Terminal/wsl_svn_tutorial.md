# SVN Usages with WSL
## get current branch info
```
    svn info
```

## get working status
```
    svn status
```

## use grep to filt status list
```
exclude statusline start with M and contains spriteatlas

grep -v '^M.+spriteatals'
```

## use pipe to output file
```
grep -v 'Test' | awk 'print $2' | tee svnmodify.txt

```

## use pipe to replace 
```
svn status | grep 'BP' | grep -v '^M.*spriteatlas' | grep -v 'Test' |  sed 's/BP//'
```

## use pipe to print part string
```
svn status | grep 'BP' | grep -v '^M.*spriteatlas' | grep -v 'Test' | awk '{print $2;}' |tee  svnmodify.txt
```

## svn to commit file with single target
```
svn ci --targets myfiles.txt -m "another commit
```

## svn to add file 
```
svn status | grep "^\?" | awk '{print $2}' | xargs svn add

add
svn st | grep ^? | sed 's/?    //' | xargs svn add

remove
svn st | grep ^! | sed 's/!    //' | xargs svn rm
```

## use pipe to monitor file change at real time
```
sudo tail -f ---disable-inotify /mnt/c/Users/penney/AppData/Local/Unity/Editor/Editor.log | grep wjp


monitor unityeditor log real time
sed -e combine multiple condition
sudo tail -f ---disable-inotify /mnt/c/Users/penney/AppData/Local/Unity/Editor/Editor.log |stdbuf -oL fgrep 'WJP'| sed -e 's/<\/size><\/color>//;s/<size=24><color=red>//;s/<size=22><color=#e100ff>//;s/WJP//;s/<\/color><\/size>//;s/<b><color=#e62855>\*\*wjp\*\*<\/color><\/b><color=#168b4d><size=14>//;s/<\/color><\/size>//'


sudo tail -f ---disable-inotify /mnt/c/Users/penney/AppData/Local/Unity/Editor/Editor.log |grep --line-buffered 'WJP'| sed -e 's/<\/size><\/color>//;s/<size=24><color=red>//;s/<size=22><color=#e100ff>//;s/WJP//;s/<\/color><\/size>//;s/<b><color=#e62855>\*\*wjp\*\*<\/color><\/b><color=#168b4d><size=14>//;s/<\/color><\/size>//'

sudo tail -f ---disable-inotify /mnt/c/Users/penney/AppData/Local/Unity/Editor/Editor.log |grep  'WJP'| sed -e 's/<\/size><\/color>//;s/<size=24><color=red>//;s/<size=22><color=#e100ff>//;s/WJP//;s/<\/color><\/size>//;s/<b><color=#e62855>\*\*wjp\*\*<\/color><\/b><color=#168b4d><size=14>//;s/<\/color><\/size>//'

上面3个命令，每次unity重新打开，都会花很多事件打印log

```
[different line buffer](https://askubuntu.com/questions/562344/what-does-grep-line-buffering-do)

## use klogg to  watch log file
1. add it to repository
```
 echo "deb [trusted=yes] https://favpackage.jfrog.io/artifactory/klogg_deb stable utils" | sudo tee -a /etc/apt/sources.list
```

2. install it
```
sudo apt-get update

sudo apt-get install klogg
```
[klogg](https://github.com/variar/klogg)
## themes
```
ZSH_THEME="robbyrussell"


ZSH_THEME="powerlevel10k/powerlevel10k"
p10k configure
```

## ssh command 
```
eval $(ssh-agent)
chmod 400 privatekey
ssh-add privatekey
```