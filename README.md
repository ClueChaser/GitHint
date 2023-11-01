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
git init 
git add file.txt -- prepare for commit
git commit -m "comment" -- make a commit
git status
```
	
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
	
MARKDOWN
	
# I
## Don't
### Want
#### To
##### Set
*###### My git on fire*


[//]: <> (--- is line)



'<br>' или два пробела -- перенос строки
два раза энтер -- параграф

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


