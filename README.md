## Домашнее задание к занятию «Кластеризация и балансировка нагрузки» - Кузнецов Евгений Александрович

### Задание 1
- Запустите два simple python сервера на своей виртуальной машине на разных портах
- Установите и настройте HAProxy, воспользуйтесь материалами к лекции по [ссылке](2/)
- Настройте балансировку Round-robin на 4 уровне.
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy.

### Решение 1

Скриншот 1 к решению 1
![Screen 1](https://github.com/jack34ru/otkazoustoichivost/blob/master/screens/Screenshot_127.png)

Файл конфига HAProxy:
[HAProxy.cfg](https://github.com/jack34ru/otkazoustoichivost/blob/master/files/haproxy_1.cfg)

Скриншот 2 к решению 1
![Screen 1](https://github.com/jack34ru/otkazoustoichivost/blob/master/screens/Screenshot_128.png)

### Задание 2
- Запустите три simple python сервера на своей виртуальной машине на разных портах
- Настройте балансировку Weighted Round Robin на 7 уровне, чтобы первый сервер имел вес 2, второй - 3, а третий - 4
- HAproxy должен балансировать только тот http-трафик, который адресован домену example.local
- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy c использованием домена example.local и без него.

 ### Решение 2

 Скриншот 1 к решению 2
![Screen 1](https://github.com/jack34ru/otkazoustoichivost/blob/master/screens/Screenshot_129.png)

Файл конфига HAProxy:
[HAProxy.cfg](https://github.com/jack34ru/otkazoustoichivost/blob/master/files/haproxy_2.cfg)

Скриншот 2 к решению 2
![Screen 1](https://github.com/jack34ru/otkazoustoichivost/blob/master/screens/Screenshot_130.png)

Скриншот 3 к решению 2
![Screen 1](https://github.com/jack34ru/otkazoustoichivost/blob/master/screens/Screenshot_131.png)