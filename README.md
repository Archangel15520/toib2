# TOIB-2 PR
# Отчет по зданию №2 "Идентификация и аутентификация"
Задача 
1. Создать виртуальную машину на базе ОС Debian 12 https://www.virtualbox.org/wiki/Downloads
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.1.0-amd64-netinst.iso
2. Создать пользователя super-{ФИО}, наделить его привилегиями суперпользователя
3. Зайти под созданным пользователем и создать группу group-{группа}
4. Добавить пользователя super-{ФИО} в группу group-{группа}
5. Продемонстрировать наличие пользователя в группе
6. Создать пользователя user-{ФИО}, добавить его в группу group-{группа}
7. Наделить полномочиями (с использованием механизмов дискреционного управления
доступом chmod) пользователя user-{ФИО} по созданию и удалению файлов в домашнем
каталоге пользователя super-{ФИО}
8. Продемонстрировать работу механизмов разграничения доступа.
# Шаги выполнения 
1 Шаг 
![image](https://github.com/Archangel15520/toib2/blob/main/10.JPG)

2 Шаг

david@debian:~$ su

Пароль: 

root@debian:/home/david# sudo useradd super-{AsatryanDR}

root@debian:/home/david# passwd super-{AsatryanDR}

Новый пароль:

Повторите ввод нового пароля: 

passwd: пароль успешно обновлён

root@debian:/home/david# sudo usermod -aG sudo super-{AsatryanDR}

![image](https://github.com/Archangel15520/toib2/blob/main/1.JPG)

3 Шаг

root@debian:/home/david# sudo groupadd group-{1234}

![image](https://github.com/Archangel15520/toib2/blob/main/2.JPG)

4 Шаг

root@debian:/home/david# sudo usermod -aG group-{1234} super-{AsatryanDR}

![image](https://github.com/Archangel15520/toib2/blob/main/3.JPG)

5 Шаг

root@debian:/home/david# id super-{AsatryanDR}

uid=1002(super-{AsatryanDR}) gid=1002(super-{AsatryanDR}) группы=1002(super-{AsatryanDR
}),27(sudo), 1003(group-{1234})

![image](https://github.com/Archangel15520/toib2/blob/main/4.JPG)

6 Шаг

root@debian:/home/david# sudo adduser user_david

root@debian:/home/david# sudo usermod -aG group-{1234} user_david

root@debian:/home/david# id user_david

uid=1004(user_david) gid=1004(user_david) группы=1004(user_david),100(users),1003(group
-{1234})

![image](https://github.com/Archangel15520/toib2/blob/main/5.JPG)

![image](https://github.com/Archangel15520/toib2/blob/main/6.JPG)

7 Шаг

root@debian:/home/david# sudo mkdir /home/super-{AsatryanDR}

root@debian:/home/david# chmod 770 /home/super-{AsatryanDR}

root@debian:/home/david# chown super-{AsatryanDR}:group-{1234} /home/super-{AsatryanDR}

![image](https://github.com/Archangel15520/toib2/blob/main/7.JPG)

8 Шаг

root@debian:/home/david# su user_david

user_david@debian:/home/david$ touch /home/super-{AsatryanDR}/test_file.txt

user_david@debian:/home/david$ rm /home/super-{AsatryanDR}/test_file.txt

![image](https://github.com/Archangel15520/toib2/blob/main/8.JPG)

user_david@debian:/home/david$ cd /home/super-{AsatryanDR}

user_david@debian:/home/super-{AsatryanDR}$ touch test_file.txt

user_david@debian:/home/super-{AsatryanDR}$ ls

test_file.txt

![image](https://github.com/Archangel15520/toib2/blob/main/9.JPG)
