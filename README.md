# Домашнее задание к занятию "`Disaster recovery и Keepalived`" - `Максимов Андрей Дмитриевич`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания



---

### Задание 1
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/7d4c1218-e32d-473f-b4db-b83940ba74ae)
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/349fde73-ecf6-475e-a780-3014dedca9b7)
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/afbb6a62-cb3a-4c78-aea1-e14653f82e4c)
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/53001674-8464-45cf-b7db-95b8dcb03393)



---
### Задание 2
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/0e973658-1597-4948-8e38-798e06f43644)
![image](https://github.com/duha2060/Disaster-Recovery-keepalived/assets/80347708/a2cbf417-c204-4628-9dcc-f3342a26db0d)

```
if [[ $(netstat -tuln | grep LISTEN | grep :80) ]] && [[ -f /var/www/html/index.nginx-debian.html ]]; then

        exit 0
else
        sudo systemctl stop keepalived
fi
```


```
vrrp_script check_script {
      script "/root/check_nginx.sh"
      interval 3
}

vrrp_instance VI_1 {
        state MASTER
        interface enp0s8
        virtual_router_id 66
        priority 255
        advert_int 1

        virtual_ipaddress {
              192.168.50.66/24
        }
        track_script {
                check_script
        }

}

```
---
### Задание 3







