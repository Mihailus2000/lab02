## Laboratory work II

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [x] 1. Создать публичный репозиторий с названием **lab02** и с лиценцией **MIT**
- [x] 2. Сгенирировать токен для доступа к сервису **GitHub** с правами **repo**
- [x] 3. Ознакомиться со ссылками учебного материала
- [x] 4. Выполнить инструкцию учебного материала
- [x] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=Mihailus2000         # Создание переменной окружения для имени пользователя
$ export GITHUB_EMAIL=Mihail14112000@mail.ru            # Создание переменной окружения для адреса почтового ящика
$ export GITHUB_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx       # Создание переменной окружения для сгенерированного токена
$ alias edit=nano              # Создание альтернативной команды вызова редактора nano
```

```ShellSession
$ cd ${GITHUB_USERNAME}/workspace     # Переход в дериктории Mihailus2000/workspace
$ source scripts/activate             # Выполняем скрипт подготовки
```

```ShellSession
$ mkdir ~/.config                     # Создание дериктории с конфигами
  
mkdir: невозможно создать каталог «/home/mihail/.config»: Файл существует

$ cat > ~/.config/hub <<EOF           # Создание файла hub и запись в него текста
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
$ git config --global hub.protocol https    # Настройка Git пользователя: установка протокола https
```

```ShellSession
$ mkdir projects/lab02 && cd projects/lab02   # Создание дериктории lab02 и переход в неё
$ git init                                    # Создание пустого репозитория 

Инициализирован пустой репозиторий Git в /home/mihail/Mihailus2000/workspace/projects/lab02/.git/

$ git config --global user.name ${GITHUB_USERNAME}      # Первоначальная настройка для сессии: установка имени пользователя
$ git config --global user.email ${GITHUB_EMAIL}        # Установка адреса электронной почты
# check your git global settings
$ git config -e --global                                # Вывод на экран настроек Git

[user]
        email = Mihail14112000@mail.ru
        name = Mihailus2000
[hub]
        protocol = https
        
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git   # Добавление ссылки origin на репозиторий на github
$ git pull origin master                                # Перенос изменений с github

remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), готово.
Из https://github.com/Mihailus2000/lab02
 * branch            master     -> FETCH_HEAD
 * [новая ветка]     master     -> origin/master
 
$ touch README.md                         # Создание README.md
$ git status                              # Просмотр статуса репозитория

На ветке master
Неотслеживаемые файлы:
  (используйте «git add <файл>…», чтобы добавить в то, что будет включено в коммит)

        README.md

ничего не добавлено в коммит, но есть неотслеживаемые файлы (используйте «git add», чтобы отслеживать их)

$ git add README.md                             # Добавление README.md в список отслеживаемых файлов
$ git commit -m"added README.md"                # Фиксирование изменений

[master f3763e3] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md

$ git push origin master                      # Отправка изменений на удалённый репозиторий 

Username for 'https://github.com': Mihailus2000
Password for 'https://Mihailus2000@github.com': 
Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 280 bytes | 93.00 KiB/s, готово.
Всего 3 (изменения 0), повторно использовано 0 (изменения 0)
To https://github.com/Mihailus2000/lab02.git
   0697494..f3763e3  master -> master
   
```

Добавить на сервисе **GitHub** в репозитории **lab02** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
.idea/
```

```ShellSession
$ git pull origin master                          # Перенос изменений с удалённого репозитория на github

remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (3/3), готово.
Из https://github.com/Mihailus2000/lab02
 * branch            master     -> FETCH_HEAD
   f3763e3..a721d65  master     -> origin/master
Обновление f3763e3..a721d65
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
 
$ git log                                        # Просмотр всех коммитов

commit a721d656ab6bfccbc6534381461b78b97ab0c730 (HEAD -> master, origin/master)
Author: Mihailus2000 <43482415+Mihailus2000@users.noreply.github.com>
Date:   Mon Apr 1 22:37:33 2019 +0300

    Create .gitignore

commit f3763e3350658342796b0303432423dc2136da53
Author: Mihailus2000 <Mihail14112000@mail.ru>
Date:   Mon Apr 1 22:34:02 2019 +0300

    added README.md

commit 0697494e977f98efb6b5d306159898e6a17d3f39
Author: Mihailus2000 <43482415+Mihailus2000@users.noreply.github.com>
Date:   Mon Apr 1 21:49:52 2019 +0300

    Initial commit
    
```
Создание дериктории, запись кода в файл
```ShellSession
$ mkdir sources                                         # Создание дериктории sources
$ mkdir include                                         # Создание дериктории include
$ mkdir examples                                        # Создание дериктории examples
$ cat > sources/print.cpp <<EOF                         # Запись кода в файл
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
```
Создание файла с кодом 
```ShellSession
$ cat > include/print.hpp <<EOF                         # Запись кода в файл
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
```
Создание файла с кодом 
```ShellSession
$ cat > examples/example1.cpp <<EOF                     # Запись кода в файл
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
```
Создание файла с кодом 
```ShellSession
$ cat > examples/example2.cpp <<EOF                     # Запись кода в файл
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```
Редактирование README.md
```ShellSession
$ edit README.md                                         # Редактирование файла README.md
```

```ShellSession
$ git status                                             # Просмотр статуса репозитория 

На ветке master
Неотслеживаемые файлы:
  (используйте «git add <файл>…», чтобы добавить в то, что будет включено в коммит)

        examples/
        include/
        sources/

ничего не добавлено в коммит, но есть неотслеживаемые файлы (используйте «git add», чтобы отслеживать их)

$ git add .                                              # Добавление всех файлов из текущей дериктории в список отслеживаемых
$ git commit -m"added sources"                           # Фиксирование изменений
[master 691fd11] added sources
 
 4 files changed, 32 insertions(+)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp

$ git push origin master                                 # Отправка изменений на удалённый репозиторий

Username for 'https://github.com': Mihailus2000
Password for 'https://Mihailus2000@github.com': 
Перечисление объектов: 10, готово.
Подсчет объектов: 100% (10/10), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (7/7), готово.
Запись объектов: 100% (9/9), 965 bytes | 107.00 KiB/s, готово.
Всего 9 (изменения 0), повторно использовано 0 (изменения 0)
To https://github.com/Mihailus2000/lab02.git
   a721d65..691fd11  master -> master

```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=02
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Homework

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
3. Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.
4. Добавьте этот файл в локальную копию репозитория.
5. Закоммитьте изменения с *осмысленным* сообщением.
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?
8. Запуште изменения в удалёный репозиторий.
9. Проверьте, что история коммитов доступна в удалёный репозитории.

### Part II

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.
2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.
3. **commit**, **push** локальную ветку в удалённый репозиторий.
4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.
5. Создайте pull-request `patch1 -> master`.
6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
7. **commit**, **push**.
8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.
10. Локально выполните **pull**.
11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.
12. Удалите локальную ветку `patch1`.

### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.
2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.
3. **commit**, **push**, создайте pull-request `patch2 -> master`.
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
5. Убедитесь, что в pull-request появились *конфликтны*.
6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.
7. Сделайте *force push* в ветку `patch2`
8. Убедитель, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.

## Links

- [hub](https://hub.github.com/)
- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2015-2019 The ISC Authors
```
