# RobotMotorsControl
Test work in dron's course

## Файл README создал сразу при создании репозитория в github

### Клонирую в текущую директорию

vagrant@vagrant:~/catkin_ws/devel/RobotMotorsControl$ git clone https://github.com/Gegirhasut/RobotMotorsControl.git .
Cloning into '.'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 1.38 KiB | 706.00 KiB/s, done.

### Создаем .gitignore
Т.к. код писал в idea, то создал файл .gitignore и поместил туда .idea/
vagrant@vagrant:/code/ros$ git add .gitignore

Остальные файлы через idea добавил в git

### Внес изменения в файлы и добавил в git
vagrant@vagrant:/code/ros$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   motors_control.py
        new file:   use_robot.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   motors_control.py
        modified:   use_robot.py

vagrant@vagrant:/code/ros$ git add .
vagrant@vagrant:/code/ros$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   motors_control.py
        new file:   use_robot.py

### Пушим в Github
Было несколько проблем:
Сначала использовал токен, который вчера создал для тестового проекта
Сгенерил новый, но не дал права
Сделал пуш, но забыл сделать commit перед этим.

vagrant@vagrant:/code/ros$ git commit -m "First files"
[main 0423d22] First files
 3 files changed, 16 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 motors_control.py
 create mode 100644 use_robot.py
vagrant@vagrant:/code/ros$ git push
Username for 'https://github.com': max077@mail.ru
Password for 'https://max077@mail.ru@github.com':
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 2 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 524 bytes | 262.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/Gegirhasut/RobotMotorsControl.git
   a3108aa..0423d22  main -> main

### Создаем новый бранч и комитим
vagrant@vagrant:/code/ros$ git checkout -b "TASK-1-New-super-engine"
Switched to a new branch 'TASK-1-New-super-engine'
vagrant@vagrant:/code/ros$ git status
On branch TASK-1-New-super-engine
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   motors_control.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        __pycache__/

no changes added to commit (use "git add" and/or "git commit -a")
vagrant@vagrant:/code/ros$ git commit -am "New super egnine feature, pycache to gitignore"
[TASK-1-New-super-engine c09778e] New super egnine feature, pycache to gitignore
 2 files changed, 5 insertions(+), 1 deletion(-)
vagrant@vagrant:/code/ros$ git status
On branch TASK-1-New-super-engine
nothing to commit, working tree clean
vagrant@vagrant:/code/ros$ git diff master
fatal: ambiguous argument 'master': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
vagrant@vagrant:/code/ros$ git diff main
diff --git a/.gitignore b/.gitignore
index 62c8935..86aa00c 100644
--- a/.gitignore
+++ b/.gitignore
@@ -1 +1,2 @@
-.idea/
\ No newline at end of file
+.idea/^M
+__pycache__/
\ No newline at end of file
diff --git a/motors_control.py b/motors_control.py
index 87a5cc9..d468303 100644
--- a/motors_control.py
+++ b/motors_control.py
@@ -6,5 +6,8 @@ class Robot:
     def engine_start(self):
         print('engine started')

+    def engine_mode_turbo(self):^M
+        print('engine turbo started')^M
+^M
     def engine_stop(self):
         print('engine stop')
\ No newline at end of file
vagrant@vagrant:/code/ros$ git push
fatal: The current branch TASK-1-New-super-engine has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin TASK-1-New-super-engine

vagrant@vagrant:/code/ros$ git push --set-upstream origin TASK-1-New-super-engine
Username for 'https://github.com': max077@mail.ru
Password for 'https://max077@mail.ru@github.com':
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 448 bytes | 448.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'TASK-1-New-super-engine' on GitHub by visiting:
remote:      https://github.com/Gegirhasut/RobotMotorsControl/pull/new/TASK-1-New-super-engine
remote:
To https://github.com/Gegirhasut/RobotMotorsControl.git
 * [new branch]      TASK-1-New-super-engine -> TASK-1-New-super-engine
Branch 'TASK-1-New-super-engine' set up to track remote branch 'TASK-1-New-super-engine' from 'origin'.
vagrant@vagrant:/code/ros$

### Создание pull-request и merge в main

vagrant@vagrant:/code/ros$ git pull
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 656 bytes | 656.00 KiB/s, done.
From https://github.com/Gegirhasut/RobotMotorsControl
   0423d22..a28890c  main       -> origin/main
Your configuration specifies to merge with the ref 'refs/heads/TASK-1-New-super-engine'
from the remote, but no such ref was fetched.

vagrant@vagrant:/code/ros$ git checkout main
Switched to branch 'main'
Your branch is behind 'origin/main' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

vagrant@vagrant:/code/ros$ git pull
Updating 0423d22..a28890c
Fast-forward
 .gitignore        | 3 ++-
 motors_control.py | 3 +++
 2 files changed, 5 insertions(+), 1 deletion(-)

Также переключил на main и забрал изменения
