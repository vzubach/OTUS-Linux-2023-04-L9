## OTUS-Linux-2023-04-L9 / Systemd
### Ниже описания файлов для каждой подзадачи, в цитатах указан путь где должен находится файл в системе
1. В папке LogService/ - файлы сервиса для поиска логов. 
 - watchlog.service - сам сервис > /etc/systemd/system/
 - watchlog.timer - сервис-таймер, дёргает основной сервис каждые 15 сек > /etc/systemd/system
 - watchlog - файл конфигурации для сервиса > /etc/sysconfig/ 
 - watchlog.sh - скрипт, который запускается сервисом watchlog.service > /opt/
2. В папке Spawn/ - cервис запуска spawn-fcgi вместо init-скрипта 
 - spawn-fcgi.service - сам сервис > /etc/systemd/system/
 - spawn-fcgi - файл конфигурации > /etc/sysconfig/
3. В папке Apache/ - сервис запуска нескольких инстансов apache
 - httpd.service - основной сервис с переменной > /etc/systemd/system/
 - httpd-first - файл конфигурации для сервиса первого экземпляра > /etc/sysconfig/
 - httpd-second - файл конфигурации для сервиса второго экземпляра > /etc/sysconfig/
 - first.conf - файл конфигурации на который ссылается файл конфигурации первого экземпляра сервиса > /etc/httpd/conf
 - second.conf - файл конфигурации на который ссылается файл конфигурации второго экземпляра сервиса > /etc/httpd/conf