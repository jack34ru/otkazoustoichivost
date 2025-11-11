# Домашнее задание к занятию «Система мониторинга Zabbix» - Кузнецов Евгений Александрович

### Задание 1 

Установите Zabbix Server с веб-интерфейсом.

#### Процесс выполнения
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
3. Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.

#### Требования к результатам 
1. Прикрепите в файл README.md скриншот авторизации в админке.
2. Приложите в файл README.md текст использованных команд в GitHub.

### Решение 1

Скриншот 1 к решению 1
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_114.png)

1. Устанавливаем PostgreSQL:
 - apt install postgresql;

2. Устанавливаем репозиторий Zabbix:
 - wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb;
 - dpkg -i zabbix-release_latest_6.0+debian11_all.deb;
 - apt update;

3. Устанавливаем zabbix сервер, web-интерфейс:
 - apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts

4. Создаем базу данных и пользователя:
 - sudo -u postgres createuser --pwprompt zabbix
 - sudo -u postgres createdb -O zabbix zabbix

5. На хосте Zabbix сервера импортируем начальную схему и данные:
 - zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

6. Добавляем наш пароль для БД zabbix сервера:
 - sed -i 's/# DBPassword=/DBPassword=12345678/g' /etc/zabbix/zabbix_server.conf

7. Перезапускаем и включаем автозапуск zabbix сервера:
 - systemctl restart zabbix-server apache2
 - systemctl enable zabbix-server apache2

8. Можно переходить в web-интерфейс для дальнейшей настройки:
 - http://host/zabbix


### Задание 2 

Установите Zabbix Agent на два хоста.

#### Процесс выполнения
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
5. Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.

#### Требования к результатам
1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
4. Приложите в файл README.md текст использованных команд в GitHub

 ### Решение 2

 

Скриншот 1 к решению 2
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_117.png)
Скриншот 2 к решению 2
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_115.png)
Скриншот 3 к решению 2
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_116.png)
Скриншот 4 к решению 2
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_118.png)

1. В случае, если репозиторий zabbix не добавлялся, то его нужно добавить для установки агента zabbix:
 - wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu22.04_all.deb
 - dpkg -i zabbix-release_latest_6.0+ubuntu22.04_all.deb
 - apt update

2. Устанавливаем zabbix агент:
 - apt install zabbix-agent

3. Добавляем в автозагрузку и перезапускаем процесс zabbix агента:
 - systemctl restart zabbix-agent
 - systemctl enable zabbix-agent

4. Меняем и выводим из коментария в файле /etc/zabbix/zabbix_agentd.conf параметр Server=127.0.0.1 на наш ip адреc zabbix сервера.

5. Перезапускаем zabbix агент:
 - systemctl restart zabbix-agent


## Задание 3 со звёздочкой*
Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

#### Требования к результатам
1. Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:

### Решение 3

Скриншот 1 к решению 3
![Screen 1](https://github.com/jack34ru/Zabbix-HW1/blob/master/screens/Screenshot_119.png)