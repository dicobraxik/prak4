### ЗАДАНИЕ 1.

---

На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.

#### РЕШЕНИЕ: 

![image](https://github.com/user-attachments/assets/d7636a0c-2e25-42e6-9d36-f4508771a9b2)

### ЗАДАНИЕ 2. 

---

Создать локальный git-репозиторий. Задать свои имя и почту (далее – coder1). Разместить файл prog.py с какими-нибудь данными. Прислать в текстовом виде диалог с git.

#### РЕШЕНИЕ:

Создание локального репозитория:
~~~
git init
~~~
Установка имени и почты:
~~~
git config user.name "Andrey"
git config user.email "akovalenkov54@gmail.com"
~~~
Создание prog.py и добавление в репозиторий:
~~~
touch prog.py
echo "# nothing" > prog.py
git add prog.py
git commit -m "test commit"
~~~
Вывод терминала:

![image](https://github.com/user-attachments/assets/5eead624-f086-4a4e-a275-37bda1bf65c0)

### ЗАДАНИЕ 3.

---

Создать рядом с локальным репозиторием bare-репозиторий с именем server. Загрузить туда содержимое локального репозитория. Команда git remote -v должна выдать информацию о server! Синхронизировать coder1 с server.

Клонировать репозиторий server в отдельной папке. Задать для работы с ним произвольные данные пользователя и почты (далее – coder2). Добавить файл readme.md с описанием программы. Обновить сервер.

Coder1 получает актуальные данные с сервера. Добавляет в readme в раздел об авторах свою информацию и обновляет сервер.

Coder2 добавляет в readme в раздел об авторах свою информацию и решает вопрос с конфликтами.

Прислать список набранных команд и содержимое git log.

#### РЕШЕНИЕ:

### ЗАДАНИЕ 4.

---

Написать программу на Питоне (или другом ЯП), которая выводит список содержимого всех объектов репозитория. Воспользоваться командой "git cat-file -p". Идеальное решение – не использовать иных сторонних команд и библиотек для работы с git.

~~~
import os
import subprocess

def get_git_objects():
    try:
        result = subprocess.run(
            ['git', 'rev-list', '--all'],
            stdout=subprocess.PIPE,
            stderr=subprocess.PIPE,
            text=True,
            check=True
        )
        objects = result.stdout.splitlines()

        for obj in objects:
            print(f"Git Commit: {obj}")
            try:
                content = subprocess.run(
                    ['git', 'cat-file', '-p', obj],
                    stdout=subprocess.PIPE,
                    stderr=subprocess.PIPE,
                    text=True,
                    check=True
                )
                print(content.stdout)
            except subprocess.CalledProcessError as e:
                print(f"Error {obj}: {e.stderr}")

    except subprocess.CalledProcessError as e:
        print(f"Error: {e.stderr}")

if __name__ == "__main__":
    if not os.path.exists('.git'):
        print("Git not found")
    else:
        get_git_objects()
~~~
Пример вывода программы:
~~~
Git Commit: 63c9ac786389b8990f4be37857917bdd7ea149bb
tree c74a3cd842f20fbbdc4b927d2c6bac4a0416cb29
parent cce1f6086981bc429eefc90ab5dfb62629f78a41
author Andrey <akovalenkov54@gmail.com> 1732717098 +0300
committer Andrey <akovalenkov54@gmail.com> 1732717098 +0300

Initial commit

Git Commit: cce1f6086981bc429eefc90ab5dfb62629f78a41
tree e3b8c0c335ac99787d0d09da637dd47b82ca49af
parent 259c25076e43cbb67165bcbc36431dc7f7a725f1
author Andrey <akovalenkov54@gmail.com> 1732716772 +0300
committer Andrey <akovalenkov54@gmail.com> 1732716772 +0300

Initial commit

Git Commit: 259c25076e43cbb67165bcbc36431dc7f7a725f1
tree e3b8c0c335ac99787d0d09da637dd47b82ca49af
parent cbd8fa2a7dbc187a16aa98f217e30ca34a7bf43a
author Andrey <akovalenkov54@gmail.com> 1732715742 +0300
committer Andrey <akovalenkov54@gmail.com> 1732715742 +0300

Inistial commit

Git Commit: cbd8fa2a7dbc187a16aa98f217e30ca34a7bf43a
tree f516b01cc57d13b3093287f95071a806f44c65b5
author Andrey <akovalenkov54@gmail.com> 1732708911 +0300
committer Andrey <akovalenkov54@gmail.com> 1732708911 +0300

test commit
~~~






