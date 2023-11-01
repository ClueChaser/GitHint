```
pwd -- current working directory
ls -al
cd .. -- back to parent
	
	
command_1 && command_2 -- simultaniously do two commands
touch file.txt file_2.txt ... -- create file
mkdir <dir>  

	
rm <file>
rm -r <dir> (remove dir and all its files)
rm -rf (repository) (f -- force)
rmdir <dir> 

	
git log -- commits history
git log --oneline -- shortened log
git init 
git add <file> -- prepare for commit
git commit -m "comment" -- make a commit
git commit --amend -- change the HEAD (last) commit (open vim/nano)
git commit --amend -m "Message" -- change commit message
git commit --amend --no-edit -- change commit, message stays
git status


To restore added to staged file, use
git restore --staged <file>
git restore --staged -- from staged to untracked/modified whole dir
To restore modified file you use
git restore <file>
After that your file will be the last previous staged or commited version of it
To cancel certain commit use
git reset --hard <commit hash> -- hash of commit that you want to be the last
All files in directory are now is up to the last commit


git diff <hash_1> <hash_2> -- see the difference between commits, form 1 to 2
In output @@ num_1, num_2 @@ -- num_2 strings to compare strarting from string num_1  
- -- original file
+ -- modified
git diff -- see the changes in the modified files
git diff --staged -- see the changes in the staged files

echo "text" -- print "text" to output
echo "text" >> file.txt -- ADD "text" to the last line of file
            > file.txt -- RESET file and write "text"


.gitignore -- file, that helps git to ignore some untracked files
One name of file per line
# -- comments
*.jpeg -- all .jpeg type files
!doge.jpeg -- except doge.jpeg file
docs/*/tmp all tmp files in subfolders of docs (docs/first/tmp) 
docs/**/tmp all tmp files in all subfolders of docs (docs/first/second/.../tmp)
* all files
file?.txt -- all txt files that match file(symbol)
file[0-2].txt or file[012] -- all txt files that match file(symbol from 0 to 2) (exmp: file1.txt)
/todo.txt -- ignore todo.txt in root folder
spam.txt -- ignore spam.txt in all folders
build/ -- ignore build folder
git status --ignored -- status of ignored files too

EXAMPLE:
# ignore all files in build folder
build/

# ignore all .log files
*.log

# don not ignore *.log files in examples
# because it is example for documentation
!examples/**/*.log

```
---
## SSH

```	
Ключи хранятся в репозитории .ssh/
ls -la .ssh/
Генерация ключей 
sh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
или
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
Проверить правильность ключа SSH
ssh -T git@github.com 
	
git remote add (repository name) (SSH URL)
git remote -v -- check the connection [-v == --verbose]
git push -u (repository name) (current local branch name) [-u is needed only once to establish 	connection]
```
---
```
HEAD is a link to the very last commit hash
.git/HEAD

HEAD contains ref to .git/refs/heads/master --> hash

git add file --> untracked file to staging area = index, cache 
All the files that is not untracked automaticaly tracked (+ staged, modified if it is)
```

# Comments
 
```
git commit -m "LGS-239: ..." -- LGS-239, 239-th task in LGS project

Conventional comments:
<type>: <message>
feat - feature (new function)
fix (fix for errors)
```
[More about style](https://www.conventionalcommits.org/ru/v1.0.0-beta.4/#спецификация)

`GitHub comment: git commit -m "Исправить #344, ..."`

```
Для коммитов на русском реккомендуется использовать инфинитив (*Исправить..., Добавить...*)
На английском -- повелительное наклонение (*Use..., Fix...*)
```

```
^X, ^G, ... -- ^ means CTRL

To exit from VIM, press Esc, type :qa!, press Enter
To see vim-book, type vimtutor (or vimtutor ru)
```
---
	
#MARKDOWN
	
# I
## Don't
### Want
#### To
##### Set
*###### My git on fire*


`--- is line`



```
'<br>' или два пробела -- перенос строки
два раза энтер -- параграф
```
`*курсив* или _курсив_`
`**полужирный текст** или __полужирный текст__`
`~~зачеркнутый текст~~`

```
1. Нумерованный список
* Ненумерованный список
- Ненумерованный список
```

```
[Яндекс](https://www.yandex.ru) ссылка как часть текста
[Яндекс](https://www.yandex.ru "Title")
```


