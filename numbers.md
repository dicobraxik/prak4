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
