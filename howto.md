1. Делаю форк KotlinAsFirst2020

2. Клонирую его себе на пк чере идею

3. открываю терминал

4. Добовляю "upstream-my" :

$ git remote add upstream-my https://github.com/ViktorGors/KotVGors.git
$ git fetch upstream-my

remote: Enumerating objects: 622, done.
remote: Counting objects: 100% (622/622), done.
remote: Compressing objects: 100% (249/249), done.
remote: Total 557 (delta 289), reused 427 (delta 163), pack-reused 0
Receiving objects: 100% (557/557), 71.67 KiB | 1.71 MiB/s, done.
Resolving deltas: 100% (289/289), completed with 32 local objects.
From https://github.com/ViktorGors/KotVGors
* [new branch] master -> upstream-my/master

5. Поиск хеша последнего комита, до моих решений
1137b420cc95fa6894edad69b31e2da1bb985d1d (вот он, красивый)

6. Делаю rebase upstream-my в ветку master
$ git rebase —onto master 1137b420cc95fa6894edad69b31e2da1bb985d1d upstream-my/master
First, rewinding head to replay your work on top of it...
Applying: lesson1tesk1 fun seconds сделанно
Using index info to reconstruct a base tree...
M src/lesson1/task1/Simple.kt
Falling back to patching base and 3-way merge...
Auto-merging src/lesson1/task1/Simple.kt
CONFLICT (content): Merge conflict in src/lesson1/task1/Simple.kt
error: Failed to merge in the changes.
hint: Use 'git am —show-current-patch' to see the failed patch
Patch failed at 0001 lesson1tesk1 fun seconds сделанно
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase —continue".
You can instead skip this commit: run "git rebase —skip".
To abort and get back to the state before "git rebase", run "git rebase —abort".

7. Вуаля! Получаем ошибки и конфликты, чтобы жизнь сахаром не казалась. Благодаря подсказкам консольки и блокноту решаю их. Продолжаем rebase

$ git add src/lesson1/task1/Simple.kt
$ git rebase —continue

8. Время создать backport и загрузить туда коммиты

$ git branch backport
$ git checkout master
$ git merge backport

9. Добавляю upstream-theirs и делаю её merge с веткой master
$ git remote add upstream-theirs https://github.com/ViktorGors/KotVGors.git
$ git fetch upstream-theirs
$ git merge -s ours upstream-theirs/master

Получаем Merge made by the 'ours' strategy и едем дальше

10. Делаю файлик remotes и добавляю в git
$ git remote -v > remotes
$ git add remotes
$ git commit -m "Add remotes file"
11 Создаю howto.md
$ touch howto.md
$ git add howto.md
$ git commit -m "Add howto.md"
12. Загружаю всё на гитхаб
$ git push
понимаю, что забыл пароль и трачу на этот пункт час
$ git checkout backport
$ git push —set-upstream origin backport
