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

 Объявление переменной COMVER, полученной в результате curl запроса, хранящей в себе номер последней версии Docker Compose

 ![image](https://github.com/malakhov4752/1/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%204.png)
