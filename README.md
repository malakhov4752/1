Перед началой установки, нужно установить Linux Oracle на VirtualBox, для этого нужно:  Иметь образ Linux Выделить 2+ ядер. Выделать 4096+ МБ оперативы. При установки операционной системы, нужно будет выбрать английский язык. 
Теперь, чтобы установить Docker с помощью Grafana, нужно будет выполнить несколько команд

1 sudo yum install wget

![Снимок экрана 1](https://github.com/user-attachments/assets/d18d1b0c-d2aa-45ed-bbe3-8bd7bcd32200)


                                                                                                                                                                                                                                            
2 sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
скачиваем репозиторий

![Снимок экрана 2](https://github.com/user-attachments/assets/0e5103f2-664d-4bee-ae98-f8e156b0e9e5)


3 sudo yum install docker-ce docker-ce-cli containerd.io
устанавливаем  docker
![Снимок экрана 3](https://github.com/user-attachments/assets/aff48d62-a301-48b6-ab9f-367f820e6658)


4 sudo systemctl enable docker --now
 Запускаем его и даём разрешение на запуск

5 sudo yum install curl

6 COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

 Чтобы узнать, какая последняя версия Docker Compose, мы получим её номер через запрос curl и сохраним в переменную COMVER.

 ![Снимок экрана 4](https://github.com/user-attachments/assets/7cbe2893-7e06-4e59-b0b2-8a61b276041a)



 7 sudo chmod +x /usr/bin/docker-compose

8 docker-compose --version (проверяем версию)

9 sudo docker compose up -d команда создает контейнера с правами супер пользователя



![Снимок экрана 5](https://github.com/user-attachments/assets/b5c6a362-18a3-4f41-b812-ddbc209fc899)


10 sudo vi docker-compose.yaml

11 Эта команда запускает текстовый редактор vi с правами администратора, чтобы ты мог редактировать файл docker-compose.yaml.

12 Нас перекинет в текстовый редактор

13 Чтобы начать редактировать текст в этом редакторе, нажми клавишу Insert на клавиатуре.

Grafana

14 переходим на сайт localhost:3000

15 логин и пароль admin admine

16 создаем Dashboard

17 жмем кнопку +Add visualizationа ,а затем "Configure a new data source"

18 connection http://prometheus:9090

19 Authentication потом Basic Authentication (admin admin)

![Снимок экрана 9](https://github.com/user-attachments/assets/056cfeb9-2a8d-46c0-87ac-f26ab959f47c)



VictoriaMetrics

20 cd grafana_stack_for_docker

21 sudo vi docker-compose.yaml

22 echo -e "# TYPE OILCOINT_metric1 gauge\nOILCOINT_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus

23 curl -G 'http://localhost:8428/api/v1/query' --data-urlencode 'query=OILCOINT_metric1'

24 вставляем OILCOINT_metric1

![Снимок экрана 7](https://github.com/user-attachments/assets/46066831-b250-44f1-a992-067b77c51898)


![Снимок экрана 6](https://github.com/user-attachments/assets/b382e11f-6f69-4b6e-9cc7-6828ad0534c5)





