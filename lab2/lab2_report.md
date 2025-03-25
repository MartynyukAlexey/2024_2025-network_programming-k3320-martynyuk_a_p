University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2024/2025

Group: K3320

Author: Martynyuk Alexey Petrovich

Lab: Lab2

Date of create: 25.03.2025 

Date of finished: 25.03.2025

## Подготовка Ansible inventory

В ходе первой работы были настроены 2 виртуальные машины с RouterOS, а также VPN соединение этих машин с удаленным сервером. Имеем следующие адреса:

1. 10.0.0.1 - сервер
2. 10.0.0.2 - 1 виртуальная машина
3. 10.0.0.3 - 2 виртуальная машина

Также на сервер был установлен Ansible.

Разрешаем доступ по API
```
/ip service set api disabled=no port=8728 address=10.0.0.0/24 
```

```
ansible-galaxy collection install community.routeros

ansible -i inventory/hosts.ini chr_devices -m ping -e "ansible_password=password"

ansible-playbook -i inventory/hosts.ini playbooks/configure_chr.yml
```