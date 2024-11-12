Перед началой установки, нужно установить Linux Oracle на VirtualBox, для этого нужно:  Иметь образ Linux Выделить 2+ ядер. Выделать 4096+ МБ оперативы. При установки операционной системы, нужно будет выбрать английский язык. 
Теперь, чтобы установить Docker с помощью Grafana, нужно будет выполнить несколько команд

1 sudo yum install wget

![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%201.png)

                                                                                                                                                                                                                                            
2 sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
скачиваем репозиторий

![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202.png)

3 sudo yum install docker-ce docker-ce-cli containerd.io
устанавливаем  docker
![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%203.png)

4 sudo systemctl enable docker --now
 Запускаем его и даём разрешение на запуск

5 sudo yum install curl

6 COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

 Чтобы узнать, какая последняя версия Docker Compose, мы получим её номер через запрос curl и сохраним в переменную COMVER.

 ![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%204.png)


 7 sudo chmod +x /usr/bin/docker-compose

8 docker-compose --version (проверяем версию)

9 sudo docker compose up -d команда создает контейнера с правами супер пользователя



![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%205.png)

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

![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%208.png)

VictoriaMetrics

20 cd grafana_stack_for_docker

21 sudo vi docker-compose.yaml

22 echo -e "# TYPE OILCOINT_metric1 gauge\nOILCOINT_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus

23 curl -G 'http://localhost:8428/api/v1/query' --data-urlencode 'query=OILCOINT_metric1'

24 вставляем OILCOINT_metric1

![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%207.png)

![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%206.png)



