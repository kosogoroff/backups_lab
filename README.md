# Стенд для выполнения домашнего задания по занятию 08.10.2026 "27. Резервное копирование"

Для запуска можно использовать следующие команды (подробнее см. в описании домашней работы по ссылке

https://github.com/kosogoroff/OTUS_Linux_Admin_course/blob/main/Lesson%2327_DZ/README.md   ):

```
git clone https://github.com/kosogoroff/backups_lab.git
cd backups_lab
vagrant up
ansible-playbook -i inventory.ini playbook.yml
```


Для создания репозитория были использованы следующие команды:

```
[admin_insta11@mv334 backups_lab]$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: will change to "main" in Git 3.0. To configure the initial branch name
hint: to use in all of your new repositories, which will suppress this warning,
hint: call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
hint:
hint: Disable this message with "git config set advice.defaultBranchName false"
Инициализирован пустой репозиторий Git в /home/admin_insta11/backups_lab/.git/
[admin_insta11@mv334 backups_lab]$ 
[admin_insta11@mv334 backups_lab]$ git add .
[admin_insta11@mv334 backups_lab]$ 
[admin_insta11@mv334 backups_lab]$ git commit -m "first commit"
[master (корневой коммит) 860b1b4] first commit
 5 files changed, 116 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
 create mode 100644 Vagrantfile
 create mode 100644 inventory.ini
 create mode 100644 playbook.yml
[admin_insta11@mv334 backups_lab]$ git branch -M main
[admin_insta11@mv334 backups_lab]$ git remote add origin https://github.com/kosogoroff/backups_lab.git
[admin_insta11@mv334 backups_lab]$ git status
Текущая ветка: main
нечего коммитить, нет изменений в рабочем каталоге
[admin_insta11@mv334 backups_lab]$ 
[admin_insta11@mv334 backups_lab]$ git push -u origin main
Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (5/5), готово.
Запись объектов: 100% (7/7), 1.99 KiB | 678.00 KiB/s, готово.
Total 7 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/kosogoroff/backups_lab.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
[admin_insta11@mv334 backups_lab]$ 

```
