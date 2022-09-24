HackerU
ДЗ к занятию “Nginx - Описание, Настройка, Безопасность”
Задача №1
Все переменные хранятся в инвентори.
nginx-1.yml - конфиг балансировщика
nginx-(2,3).yaml - конфиг сервера
Настройка nginx реализована заменой файла /etc/nginx/sites-available/default

В файле hosts вм разбиты на 2 группы.

Плейбук site.yaml   


Команды:
Проверика доступности хостов
ansible -i hosts all -m ping

ansible-playbook -i hosts site.yml -D --extra-vars "ansible_sudo_pass=&PASSWORD%"

только настроить сеть

ansible-playbook -i hosts site.yml --tags networks -D --extra-vars "ansible_sudo_pass=&PASSWORD%"