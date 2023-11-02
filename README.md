## Bash


`pwd` # current working directory<br>
`ls -al`<br>
`cd ..` # back to parent<br>
		
command_1 && command_2 # simultaniously do two commands<br>
`touch file.txt file_2.txt ...` # create file<br>
`mkdir <dir>`  <br>

	
`rm <file>`<br>
`rm -r <dir>` # (remove dir and all its files)<br>
`rm -rf (repository)` # (f -- force)<br>
`rmdir <dir>` <br>


## Commits


`git log` # commits history<br>
`git log --oneline` # shortened log of current branch<br>
`git log --decorate` <br>
`git log --oneline <branch_1> <branch_2> ...` # shortened log of multiple branches<br>
`git init` <br>
`git add <file>` # prepare for commit<br>
`git commit` # commit throu opening text redactor<br>
`git commit -m "comment"` # make a commit<br>
`git commit --amend` # change the HEAD (last) commit (open vim/nano)<br>
`git commit --amend -m "Message"` # change commit message<br>
`git commit --amend --no-edit` # change commit, message stays<br>
`git status`<br>


## Canceling


To restore added to staged file, use<br>
`git restore --staged <file>`<br>
`git restore --staged` # from staged to untracked/modified whole dir<br>
To restore modified file you use<br>
`git restore <file>`<br>
After that your file will be the last previous staged or commited version of it<br>
To cancel certain commit use<br>
`git reset --hard <commit hash>` # hash of commit that you want to be the last<br>
All files in directory are now is up to the last commit<br>


## git diff


`git diff <hash_1> <hash_2>` # see the difference between commits, form 1 to 2<br>
In output `@@ num_1, num_2 @@` num_2 strings to compare strarting from string num_1<br>  
`-` # original file<br>
`+` # modified<br>
`git diff` # see the changes in the modified files<br>
`git diff --staged` # see the changes in the staged files<br>

`echo "text" # print "text"` # to output<br>
`echo "text" >> file` # ADD "text" to the last line of file<br>
            `> file` # RESET file and write "text"<br>


## .gitignore


`.gitignore` # file, that helps git to ignore some untracked files<br>
One name of file per line<br>
`#` # comments<br>
`*.jpeg` # all .jpeg type files<br>
`!doge.jpeg` # except doge.jpeg file<br>
`docs/*/tmp` all tmp files in subfolders of docs (docs/first/tmp) <br>
`docs/**/tmp` all tmp files in all subfolders of docs (docs/first/second/.../tmp)<br>
`*` all files<br>
`file?.txt` # all txt files that match file(symbol)<br>
`file[0-2].txt` or `file[012]` # all txt files that match file(symbol from 0 to 2) (exmp: file1.txt)<br>
`/todo.txt` # ignore todo.txt in root folder<br>
`spam.txt` # ignore spam.txt in all folders<br>
`build/` # ignore build folder<br>
`git status --ignored` # status of ignored files too<br>


### EXAMPLE:

 
`build/` # ignore all files in build folder<br>

`*.log` # ignore all .log files<br>

`!examples/**/*.log` # don not ignore *.log files in examples, because it is example for documentation<br>


---


## SSH

	
Ключи хранятся в репозитории `.ssh/`<br>
`ls -la .ssh/`<br>
Генерация ключей <br>
`ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"` <br>
или<br>
`ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"` <br>
`ssh-keygen -t rsa -f ~/.ssh/accountB -C <email2@example.com>`
Проверить правильность ключа SSH<br>
`ssh -T git@github.com` <br>
	
`git remote add (repository name or origin) (SSH URL)` # concect to remote repository to push in<br>
`git remote rm (repository name)` # delete connection<br>
`git push -u (--set-upstream) (repository name) (current local branch name)` # [-u is needed only once to establish connection<br>
`git remote -v` # check the connection (-v == --verbose)<br>
`git clone` # clone and connect to remote repository<br>
after clone you don not need to use "push -u", because the connection is already exit<br>
fork repository is needed if you don not have rights to change the main project,
fork, change, send change request <br>


## Branching


`hash (HEAD --> branch_1, branch_2)` two tags on this commit and HEAD on branch_1<br>
`hash (branch_3)` # tag of branch_3 is on this commit<br>
`hash` # commit without tag<br>

`git branch -a` # see the branches<br>
`git branch "name"` # create a new branch<br>
name usually feature/problem or bugfix/problem<br>
`git checkout "branch name"` # do "name" branch the current branch<br>
`git checkout -b "name"` # create and move to new branch<br>
`git checkout "name"` # after cloning, you should make a local copies of branch<br>
`git diff branch_1 branch_2` (or use hash)<br>
`git branch -D "name"` # delete branch<br>
`git branch -d "name"` # delete branch only when it was merged with another<br>

If there are no new commits from new branch, HEAD of the new branch is where it is created<br>

Now, there are two branches, main and bugfix with one HEAD, if you commit main, bugfix HEAD will be 
behind the main.<br>
`commit~0` # current commit, `commit~1` or `commit~` # previous, `~2`, `~3`, `~N`<br>
`(HEAD, hash, branch)~`<br>

`*main`  <br>
`git merge feature` # feature will be merged to main, main and feature now at the same nod
and all commits from feature now on the main branch<br>
Simple git merge just combine two branches in one! That is called FF (Fast-Forward, linear mode)<br>
`git merge --no-edit --no-ff "branch"` # отключить ввод сообщения и fast-forward<br>
Now, we have not a one main branch with side branch all in one line, but two branches that have same HEAD-nod.<br>
_OUTPUT_:<br>
`Updating hash_1 hash_2` # all commits from 1 to 2 have been merged<br>
`fast-forward` # mode of merging, it means that after merging linear history of commits appears (one line, branch of commits)<br>

There are conflicts appear, when two or more people change the same file.<br>
[documentation](https://git-scm.com/book/ru/v2/Инструменты-Git-Продвинутое-слияние)<br>

After pushing new branch to remote repository, you can create a **pull request** to merge one branch to another from GitHub interface. <br>

Algorithm before pushing your work to remote rep:<br>
`git checkout main` # перешли в main<br>
`git pull` подтянули новые изменения в main<br>
`git checkout my-branch` # вернулись в рабочую ветку my-branch<br>
`git merge main` # влили main в новую ветку my-branch<br>
`git push -u origin my-branch` # отправили ветку my-branch в удалённый репозиторий<br>

`git push --force` # удалить все коммиты на удаленном от текущего локального и запушить коммиты с локального _USE CAREFULLY_<br>

`git congif [--global] merge.ff false` # disable ff always<br>
Usually, there is no need to create a new comment for merge request. <br>

---

`HEAD` is a link to the very last commit hash<br>
`.git/HEAD`<br>

`HEAD` contains ref to `.git/refs/heads/master` --> `hash`<br>

`git add file` --> untracked file to `staging area` = `index`, `cache` <br>
All the files that is not untracked automaticaly tracked (+ staged, modified if it is)<br>

### Подходы к брэнчингу
* `Feature branch workflow` — 1. New function -- new branch, 2. Merge ready branch code to main 3. main is always stable
* `Git flow` — более сложный вариант. Подход похож на feature branch workflow, но в нём создаётся больше веток, а изменения (коммиты) делят на разные типы: исправление, новая функциональность и так далее. Разные типы коммитов попадают в разные ветки.
* `Trunk-based` — same as feature branch workflow, but do merge often (every day)

### Conflicts 


The first line of `file.txt`:<br>
main --> `main`<br>
br1 --> `version_1`<br>
br2 --> `version_2`<br>

```
       ___br2_______
      /
---------(main, br1)---
```

In (main, br1) `file.txt`, that was modified by br1.<br>
In br2 the same `file.txt`, that was simultaniously modified with br1.<br>
By merging br2 in the main we create a conflict.<br>
After merging successfully abort, there is new comments in `file.txt` in main branch will appear.<br>

There, in the comments, only conflicts are shown.<br>
Text between <<<<<<< HEAD and ======= points on changes that are in HEAD (main).<br>
Text between ======= and >>>>>>> br2 points on changes that are in br2.<br>

You should open the file.txt and delete all what you don not need, then re-add and re-commit.<br>
Git refers to comments (markers of conflict) in `file.txt` to understand if the conflict still present.<br>


# Comments

 
`git commit -m "LGS-239: ..."` # LGS-239, 239-th task in LGS project<br>

Conventional comments:<br>
`<type>: <message>`
feat - feature (new function)<br>
fix (fix for errors)<br>

[More about style](https://www.conventionalcommits.org/ru/v1.0.0-beta.4/#спецификация)<br>

`GitHub comment: git commit -m "Исправить #344, ..."`<br>

Для коммитов на русском реккомендуется использовать инфинитив (*Исправить..., Добавить...*)<br>
На английском -- повелительное наклонение (*Use..., Fix...*)<br>



`^X, ^G, ... -- ^ means CTRL`

```
To exit from VIM, press Esc, type :qa!, press Enter
To see vim-book, type vimtutor (or vimtutor ru)
```

---

	
# MARKDOWN


```	
# I
## Don't
### Want
#### To
##### Set
###### My git on fire

--- is line

<br> или два пробела -- перенос строки
два раза энтер -- параграф

*курсив* или _курсив_
**полужирный текст** или __полужирный текст__
~~зачеркнутый текст~~

1. Нумерованный список
* Ненумерованный список
- Ненумерованный список

[Яндекс](https://www.yandex.ru) ссылка как часть текста
[Яндекс](https://www.yandex.ru "Title")
```

# Additional
 
 
`Aweasome lists` # curious links<br>
[remote job](https://github.com/lukasz-madon/awesome-remote-job#readme) <br>
[fonts](https://github.com/brabadu/awesome-fonts#readme)<br>


