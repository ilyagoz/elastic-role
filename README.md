Установка Elasticsearch
=========

Эта роль создана в рамках выполнения задания "08.03 Работа с Roles" учебного курса «DevOps-инженер»  (DVPSPDC). Роль закачивает архив с дистрибутивом на указанные машины, распаковывает его и устанавливает в `/etc/profile.d/` файл `elk.sh`, содержащий скрипт для установки переменной `ES_HOME` на каталог установки Elasticsearch и добавления `$ES_HOME/bin` к `PATH`. К сожалению, ничего больше эта роль не делает.

Переменные
--------------

В `defaults/main.yml` определяются следующие переменные:

- elastic_version: версия Elasticsearch, которую нужно установить, по умолчанию 7.10.1
- elastic_home: каталог, в который нужно развернуть архив с дистрибутивом Elasticsearch, по умолчанию `/opt/elastic/7.10.1`
- elastic_archive: имя архива с дистрибутивом Elasticsearch, по умолчанию `elasticsearch-7.10.1-linux-x86_64.tar.gz`

Архив с дистрибутивом Elasticsearch необходимо самостоятельно скачать и положить в каталог `files`.

Тестирование
----------------

В каталоге `molecule` имеются скрипты для тестирования роли с помощью Docker на трех платформах:

- docker.io/ubuntu:latest
- docker.io/pycontribs/debian
- docker.io/pycontribs/centos:7

Пример Playbook
----------------
```yaml
- hosts: elastic
  roles:
    - ilyagoz.elastic_role
```
