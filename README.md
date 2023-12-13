========================
Pdris_hw3 README
========================

Описание проекта:
----------------
Этот проект создан для выполнения лабораторной работы №3 в рамках курса PDRIS 2023. Он предоставляет среду для развертывания трех контейнеров: "deployer-server", "first-remote" и "second-remote", каждый из которых имеет свой собственный IP-адрес и служит для различных целей.

Структура проекта:
-------------------
- `Deployer/` - Контекст для сборки "deployer-server" контейнера.
- `RemoteHost/` - Контекст для сборки "first-remote" и "second-remote" контейнеров.
- `docker-compose.yml` - Файл Docker Compose, определяющий конфигурацию контейнеров и сетей.

Запуск проекта:
---------------
1. Убедитесь, что у вас установлен Docker и Docker Compose.

2. Склонируйте данный репозиторий на вашем хост-компьютере.

3. В корневой папке проекта выполните следующую команду, чтобы развернуть контейнеры:
   
 docker-compose up -d  

5. Контейнеры будут созданы с указанными IP-адресами:
- "deployer-server" - 192.168.3.30
- "first-remote" - 192.168.3.31
- "second-remote" - 192.168.3.32

5. Вы можете подключиться к "deployer-server" для выполнения сборки, используя команду:

docker exec -it deployer-server /bin/bash

6. Внутри контейнера "deployer-server" выполните сборку Ansible playbook "deploy_app.yml":
   
ansible-playbook -i inventory/hosts deploy_app.yml

Пароли:
-------
Пароли для "first-remote" и "second-remote" установлены как "1234".

7. В ходе выполнения плейбука можно будет отследить генерацию сертификатов для подключения ssh к двум другим контейнерам, установку на них приложения скаченного с github и сборку

8. Для проверки работы кода зайдите на любой из хостов и проверьте папку /app/Popygai на наличие popygai.txt, в ходе проверки вы должны найти файл с замечательным попугом

