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

grishavm@debian:~$ su

Пароль: 

root@debian:/home/grishavm# sudo useradd super-{Grisha.V.M}

root@debian:/home/grishavm# passwd super-{Grisha.V.M}

Новый пароль:

Повторите ввод нового пароля: 

passwd: пароль успешно обновлён

root@debian:/home/grishavm# sudo usermod -aG sudo super-{Grisha.V.M}

![image](https://github.com/Archangel15520/toib2/blob/main/1.JPG)

3 Шаг

root@debian:/home/grishavm# sudo groupadd group-{1234}

![image](https://github.com/Archangel15520/toib2/blob/main/2.JPG)

4 Шаг

root@debian:/home/grishavm# sudo usermod -aG group-{1234} super-{Grisha.V.M}

![image](https://github.com/Archangel15520/toib2/blob/main/3.JPG)

5 Шаг

root@debian:/home/grishavm# id super-{Grisha.V.M}

uid=1001(super-{Grisha.V.M}) gid=1001(super-{Grisha.V.M}) группы=1001(super-{Grisha.V.M
}),27(sudo), 1002(group-{1234})

![image](https://github.com/Archangel15520/toib2/blob/main/4.JPG)

6 Шаг

root@debian:/home/grishavm# sudo adduser user_grishavm

root@debian:/home/grishavm# sudo usermod -aG group-{1234} user_grishavm

root@debian:/home/grishavm# id user_grishavm

uid=1003(user_grishavm) gid=1003(user_grishavm) группы=1003(user_grishavm),100(users),1002(group
-{1234})

![image](https://github.com/Archangel15520/toib2/blob/main/5.JPG)

![image](https://github.com/Archangel15520/toib2/blob/main/6.JPG)

7 Шаг

root@debian:/home/grishavm# sudo mkdir /home/super-{Grisha.V.M}

root@debian:/home/grishavm# chmod 770 /home/super-{Grisha.V.M}

root@debian:/home/grishavm# chown super-{Grisha.V.M}:group-{1234} /home/super-{Grisha.V.M}

![image](https://github.com/Archangel15520/toib2/blob/main/7.JPG)

8 Шаг

root@debian:/home/grishavm# su user_grishavm

user_grishavm@debian:/home/grishavm$ touch /home/super-{Grisha.V.M}/test_file.txt

user_grishavm@debian:/home/grishavm$ rm /home/super-{Grisha.V.M}/test_file.txt

![image](https://github.com/Archangel15520/toib2/blob/main/8.JPG)

user_grishavm@debian:/home/grishavm$ cd /home/super-{Grisha.V.M}

user_grishavm@debian:/home/super-{Grisha.V.M}$ touch test_file.txt

user_grishavm@debian:/home/super-{Grisha.V.M}$ ls

test_file.txt

![image](https://github.com/Archangel15520/toib2/blob/main/9.JPG)
