```
pwd -- current working directory
ls -al
cd .. -- back to parent
	
	
command_1 && command_2 -- simultaniously do two commands
touch file.txt file_2.txt ... -- create file
mkdir dir 

	
rm file.txt
rm -r dir (remove dir and all its files)
rm -rf (repository) (f -- force)
rmdir dir 

	
git log -- commits history
git log --oneline -- shortened log
git init 
git add file.txt -- prepare for commit
git commit -m "comment" -- make a commit
git status
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

Для коммитов на русском реккомендуется использовать инфинитив (*Исправить..., Добавить...*)
На английском -- повелительное наклонение (*Use..., Fix...*)
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


