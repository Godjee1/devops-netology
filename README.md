****Домашнее задание к занятию 4. «Оркестрация группой Docker-контейнеров на примере Docker Compose»****

**Задача 1**

Создайте собственный образ любой операционной системы (например, debian-11) с помощью Packer версии 1.5.0
￼<img width="1678" alt="Pasted Graphic 19" src="https://github.com/Godjee1/devops-netology/assets/117306656/ab665849-c280-4f64-9a4b-30b9a7eea828">

**Задача 2**

2.2. Создайте вашу первую виртуальную машину в YandexCloud с помощью Terraform (вместо использования веб-интерфейса YandexCloud). Используйте Terraform-код в директории (src/terraform).  
￼<img width="853" alt="Pasted Graphic 59" src="https://github.com/Godjee1/devops-netology/assets/117306656/77f4270e-db81-47bd-8a63-fb12085d0e83">
<img width="958" alt="Pasted Graphic 60" src="https://github.com/Godjee1/devops-netology/assets/117306656/9b5c88ce-a70b-42e4-aa07-951fb48904d7">

**Задача 3**

С помощью ansible+docker-compose разверните на виртуальной машине из предыдущего задания систему мониторинга на основе Prometheus/Grafana . Используйте ansible код в директории (src/ansible)
Для получения зачета вам необходимо предоставить вывод команды "docker ps" , все контейнеры, описанные в (docker-compose), должны быть в статусе "Up".  
￼<img width="1680" alt="Pasted Graphic 56" src="https://github.com/Godjee1/devops-netology/assets/117306656/bb67461c-e65b-4179-9420-4ed0b0e44545">

**Задача 4**

Откройте web браузер, зайдите на страницу http://<внешний_ip_адрес_вашей_ВМ>:3000. Используйте для авторизации логин и пароль из (.env-file). Изучите доступный интерфейс, найдите в интерфейсе автоматически созданные docker-compose панели с графиками(dashboards). Подождите 5-10 минут, чтобы система мониторинга успела накопить данные.  
￼<img width="1680" alt="Pasted Graphic 57" src="https://github.com/Godjee1/devops-netology/assets/117306656/e9183539-3990-46b3-814e-2efccbe5c526">
<img width="1680" alt="Pasted Graphic 58" src="https://github.com/Godjee1/devops-netology/assets/117306656/a9772852-fc99-4a85-9cf6-da0c4374d6c5">

￼













****Домашнее задание к занятию 3. «Введение. Экосистема. Архитектура. Жизненный цикл Docker-контейнера»****

Задача 1
- Сценарий выполнения задачи:
- создайте свой репозиторий на https://hub.docker.com;
- выберите любой образ, который содержит веб-сервер Nginx;
- создайте свой fork образа;
- реализуйте функциональность: запуск веб-сервера в фоне с индекс-страницей, содержащей HTML-код ниже:

ОТВЕТ: docker pull godjee/nginx:2.0
https://hub.docker.com/r/godjee/nginx


Задача 2
- Сценарий:
- высоконагруженное монолитное Java веб-приложение; - т.к приложение высоконагруженное, думаю, в данном случае лучше всего подойдет физический сервер 
- Nodejs веб-приложение; - легкое веб-приложение может быть отлично реализовано с помощью docker
- мобильное приложение c версиями для Android и iOS; - вероятно, с учетом необходимости использования UI/UX для данного направления, наилучшим образом подойдет VM.
- шина данных на базе Apache Kafka; - да, для шины событий отлично может подойти docker, т.к для шины данных важна масштабируемость, которую лучше и проще достичь с помощью контейнеров
- Elasticsearch-кластер для реализации логирования продуктивного веб-приложения — три ноды elasticsearch, два logstash и две ноды kibana; - Можно использовать и VM и docker. Возможно, будет зависеть от этапов реализации продукта.
- мониторинг-стек на базе Prometheus и Grafana; - вполне применим docker для простого развертывания сред
- MongoDB как основное хранилище данных для Java-приложения; - Под хранилище данных для java-приложения отлично бы подошел физический сервер, на мой взгляд.
- Gitlab-сервер для реализации CI/CD-процессов и приватный (закрытый) Docker Registry. - я бы здесь опять же выбрал лучше VM для удобства администрирования и большей изоляции в силу необходимости реализации приватного Docker Registry.


Задача 3
- Запустите первый контейнер из образа centos c любым тегом в фоновом режиме, подключив папку /data из текущей рабочей директории на хостовой машине в /data контейнера.
$ docker run --name TEST1 -v $(pwd)/data:/data -d centos:latest sleep 500
- Запустите второй контейнер из образа debian в фоновом режиме, подключив папку /data из текущей рабочей директории на хостовой машине в /data контейнера.
$ docker run --name TEST2 -v $(pwd)/data:/data -d debian:latest sleep 500
- Подключитесь к первому контейнеру с помощью docker exec и создайте текстовый файл любого содержания в /data.
$ docker exec -it TEST1 bash
[root@7e7d061005fa data]# echo 'test number 1' > testfile1.txt
- Добавьте ещё один файл в папку /data на хостовой машине.
$ echo 'test number 2' > testfile2.txt
- Подключитесь во второй контейнер и отобразите листинг и содержание файлов в /data контейнера.
<img width="515" alt="Pasted Graphic 8" src="https://github.com/Godjee1/devops-netology/assets/117306656/e01097e2-a325-4cbf-846d-a6637de763a3">


Задача 4 (*)
- Воспроизведите практическую часть лекции самостоятельно.
- Соберите Docker-образ с Ansible, загрузите на Docker Hub и пришлите ссылку вместе с остальными ответами к задачам.
.Задача 4, к сожалению, выполняется с ошибкой. Если подскажете, в какую сторону копнуть для общего развития - буду премного благодарен. Ошибку прилагаю
<img width="1439" alt="image" src="https://github.com/Godjee1/devops-netology/assets/117306656/9abd7de8-0529-4d2c-a497-784857fc3d21">









### Домашнее задание к занятию 2. «Применение принципов IaaC в работе с виртуальными машинами» 05-virt-02-iaac

Задача 1
* Основное преимущество  IaaC — автоматизация и упрощение рутинных задач для разработчиков. Возможность на ранних стадиях выявлять проблемы/ошибки/недоработки в кодах или предстоящих релизах. Простота в развертывание новых релизов, при необходимости (применении непрерывного развертывания) можно достичь выпуска релизов без ручного участия
* Идемпотентность является одим из основных принципов  IaaC. Данное свойство процедуры развертывания сред помогает проектировать более надежные системы и избегать несогласованности.

Задача 2
Чем Ansible выгодно отличается от других систем управление конфигурациями? 
- Отсутствие необходимости установки дополнительных агентов на хостах. А также использование ssh соединения, скорость и масштабируемость, низкий порог входа.
Какой, на ваш взгляд, метод работы систем конфигурации более надёжный — push или pull? 
- У обоих методов есть свои плюсы и минусы. Но, вероятно, pull — можно считать более «безопасным», т.к и один внешний клиент не имеет прав на внесение изменений в кластер, все обновления накатываются изнутри. Поэтому мой выбор падает на pull

Задача 3
Установите на личный компьютер:
VirtualBox,
Vagrant,
Terraform,
Ansible.
Приложите вывод команд установленных версий каждой из программ, оформленный в Markdown.
<img width="1176" alt="Pasted Graphic 43" src="https://github.com/Godjee1/devops-netology/assets/117306656/b9ad3e31-2b4c-40d1-8839-1f628d3223a3">

<img width="1212" alt="Pasted Graphic 41" src="https://github.com/Godjee1/devops-netology/assets/117306656/487d8154-e5ca-484d-ad3e-764d9b5d56fd">

Задача 4
Воспроизведите практическую часть лекции самостоятельно.
Создайте виртуальную машину.
Зайдите внутрь ВМ, убедитесь, что Docker установлен с помощью команды
docker ps
<img width="587" alt="Pasted Graphic 42" src="https://github.com/Godjee1/devops-netology/assets/117306656/6786cf99-a6b2-424f-a535-278b3e632d06">



### Домашнее задание к занятию 1. «Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения»
Полная виртуализация эмулирует хост-машину, используя аппаратную поддержку виртуализации на низших уровнях, можно создавать разные ВМ с разными ОС.

При программной виртуализации задействованы отдельные изолированные гостевые ОС, поверх функционирования ОС на хост-машине и прослойки в виде гипервизора

Виртуализация уровня ОС — гипервизор заложен в самой ОС хост-машины, все вм используют одно ядро
Задача 2
* Высоконагруженная база данных, чувствительная к отказу - вероятно, лучше подходит паравиртуализация за счет возможности реализации кластеров и горячей миграции.
* Различные web-приложения - насколько мне известно, для различных веб-сервисов зачастую используют виртуализацию на уровне ОС. Которая обеспечивает упрощенную, понятную отладку за счет использования одного ядра, а также частого использования ОС Linux, имеющего предпочтения у разработчиков.
* Windows системы для использования Бухгалтерским отделом - как и в первом случае, можно сделать выбор в пользу программной виртуализации за счет обеспечения отличной системы резервного хранения и возможности устранения инцидентов без остановки работы за счет горячей миграции.
* Системы, выполняющие высокопроизводительные расчеты на GPU - однозначно физические сервера, т.к виртуализация в любом своем виде будет отнимать ресурсы. На физическом сервере ресурсы можно оптимизировать максимально эффективно для данных задач.
Задача 3
1. Для данной задачи отлично подходят два прямых конкурента MS Hyper-V и VMWare vSphere, обеспечивающие возможность развертывания на данных ОС и поддерживающие отличную отказоустойчивую систему кластеров. С учетом наличия Windows OS, преимущественно можно отдать выбор в сторону Hyper-V за счет отличной совместимости данного гипервизора.
2. KVM или Xen, одни из самых популярных open source решений. Отлично совместимы с указанными ОС и замечательно показывают себя виртуализации небольших инфраструктур
3. Как уже указывал выше, Ms Hyper-v server 2019 отлично подходит в роли гипервизора на базе windows.
4. С учетом отсутствия высоопроизводительных задач и исключительно Linux дистрибутивов, подойдет Oracle VirtualBox или Docker.
Задача 4
Использование нескольких отличных систем виртуализации может повлечь за собой ряд проблем:
1. Они могут создать конфликт системных ресурсов, который приведет к неопределенному поведению, включая сбои виртуальных машин, зависаниям или перезагрузкам, возможно, повреждению данных.
2. Небезопасно загружать драйверы ядра для разных решений визуализации одновременно
3. Судя по найденной информации, только один гипервизор может использовать функции аппаратного ускорения, предлагаемые современными материнскими платами/чипсетами, поэтому один гипервизор может работать в режиме виртуализации программного обеспечения, что может ограничить выбор гостей виртуальной машины.
4. Можно столкнуться с исчерпанием ресурсов, т.к один гипервизор будет не знать, что делает другой.
5. Эксплуатация множества виртуалок повлечет за собой привлечение более компетентого персонала

Если нет возможности не вовлекать гетерогенную среду виртуализации в эксплуатацию, то одним из решений минимизации рисков может стать использование платных, ведущих гипервизоров, которые будут иметь возможность тончайшей настройки распределения ресурсов и разграничение используемых ресурсов сети/портов и тд. Как говорит интернет, минимально конфликтующие между собой являются Hyper-V и Xen. Если бы у меня был выбор, однозначно, использование нескольких систем виртуализации я бы постарался обойти. 

