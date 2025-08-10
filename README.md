## Задания 1-8

Создано 3 репозитория.:
* https://github.com/EremeevAN/clickhouse-role
* https://github.com/EremeevAN/vector-role
* https://github.com/EremeevAN/loghthouse-role

## Задания 9-11

Загружаем роли.
Файл `requirements.yml`
```yaml
---
- name: clickhouse
  src: git@github.com:EremeevAN/clickhouse-role.git
  scm: git
  version: v1.0.0

- name: vector
  src: git@github.com:EremeevAN/vector-role.git
  scm: git
  version: v1.0.0

- name: lighthouse
  src: git@github.com:EremeevAN/lighthouse-role.git
  scm: git
  version: v1.0.0
```

playbook:
```yaml
---
- name: Install Clickhouse
  hosts: clickhouse
  gather_facts: false
  roles: 
    - clickhouse

- name: Install Vector
  hosts: vector
  gather_facts: false
  roles: 
    - vector

- name: Install Lighthouse
  hosts: lighthouse
  gather_facts: false
  roles: 
    - lighthouse
```

В Yandex Cloud создадим три машины:

![image](https://github.com/EremeevAN/Ansible-04-roles/blob/main/images/2.png)

Запустим `playbook`:

![image](https://github.com/EremeevAN/Ansible-04-roles/blob/main/images/1.png)

Зайдем на порт `80` хоста с lighthouse:

![image](https://github.com/EremeevAN/Ansible-04-roles/blob/main/images/3.png)

И на порт `8080`:

![image](https://github.com/EremeevAN/Ansible-04-roles/blob/main/images/4.png)
