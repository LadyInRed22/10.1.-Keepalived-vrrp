# 10.1. Keepalived-vrrp - Татьяна Виноградова

### Задание 1
Требуется развернуть топологию из лекции и выполнить установку и настройку сервиса Keepalived.

ВМ1:
/etc/keepalived/keepalived.conf                                                         

```vrrp_instance test {
state BACKUP
interface enp0s3
virtual_router_id 10
priority 100
advert_int 5
authentication {
auth_type AH
auth_pass 1
}
unicast_peer {
192.168.100.101
}
virtual_ipaddress {
192.168.100.150 dev enp0s3 label enp0s3:vip
}
}
```
![image](https://user-images.githubusercontent.com/103531664/204158113-d9b568c1-b7e1-4234-8c1c-07c11f14d6ee.png)
ВМ2:
/etc/keepalived/keepalived.conf                                                      
```vrrp_instance test {
state BACKUP
interface enp0s3
virtual_router_id 10
priority 100
advert_int 5
authentication {
auth_type AH
auth_pass 1
}
unicast_peer {
192.168.100.101
}
virtual_ipaddress {
192.168.100.150 dev enp0s3 label enp0s3:vip
}
}
```
![image](https://user-images.githubusercontent.com/103531664/204158134-5e3af134-f6d8-4584-a203-248983818a58.png)
### Задание 2*
Проведите тестирование работы ноды, когда один из интерфейсов выключен. Для этого:
•	добавьте еще одну виртуальную машину и включите ее в сеть;
•	на машине установите wireshark и запустите процесс прослеживания интерфейса;
•	запустите процесс ping на виртуальный хост;
•	выключите интерфейс на одной ноде (мастер), остановите wireshark;
•	найдите пакеты ICMP, в которых будет отображён процесс изменения MAC адреса одной ноды на другой.
Пришлите скриншот до и после выключения интерфейса из Wireshark.
#### ДО:
![image](https://user-images.githubusercontent.com/103531664/204158184-b09f5508-911e-4099-ae93-389874aa2b26.png)
#### ПОСЛЕ:
![image](https://user-images.githubusercontent.com/103531664/204158208-fd928709-38f1-4f35-b66e-24c6a44fc1ac.png)

