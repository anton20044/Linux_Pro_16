Лабораторная работа №16 по курсу Linux Pro.


Решение:
Развернул три ВМ.  На одной (web) установлен nginx. Логи nginx собираются filebeat и отправляются на сервер с Logstash (elk).
Все остальные логи системы собираются rsyslog и отправляются на другой сервер (log).
Vagrant+Ansible файлы прилагаю.

