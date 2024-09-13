# Система уведомления о коммерческих предложениях
Микросервисная система уведомления о коммерческих предложениях через kafka.
Позволяет отсылать уведомления пользователю, с защитой от падения отдельных компонентов системы.  
Состоит из 2х микросервисов:  
- NotificationKeeper  
- EmailNotificator

Подробно о каждом микросервисе написано в их личном репозитории

## Технологии  
- [Redis](https://redis.io/)  
- [InfluxDB](https://www.influxdata.com/)  
- [ApacheKafka](https://kafka.apache.org/)  
- [PostgreSQL](https://www.postgresql.org/)
- [Docker](https://www.docker.com)
  
## Использование  
  
Для запуска приложения, нужно поднять необходимые контейнеры с помощью docker-compose.  
Для этого в папке проекта нужно вызвать команду docker compose up. (При его отсутствии, его нужно установить)  
  
Для отправки уведомления, нужно отправить HTTP запрос на URL:  
http://localhost:8080/api/v1.0/Notification/  
Метод POST  
Тело запроса:  
{  
"BlueprintId" : "...",  
"CustomerId" : "..."  
}  
  
Инициализирующие данные:  
CustomerId: a7f1cf1f-5f4f-4159-99cc-80a4e9f7c5cb  
BlueprintId: b7f1cf1f-5f4f-4159-99cc-80a4e9f7c5cb  
