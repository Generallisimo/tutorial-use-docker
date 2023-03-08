# tutorial-use-docker
Используем докер, заливаем на Docker Hub свой репозиторий, объединяем образы в один контейнер с их сохранением при перезапуске
Docker
docker info - узнать о запуске в контейнере
docker images - детально о запущенных 
docker ps - о уникальных контейнерах 
docker stop 0d6d0d32b29b - остановка опред контейнира
docker pull openjdk - так можно скачать images
docker run -it --name MyJava openjdk запуск образа и название контейнера в интерактивном режиме
ctr+D - выход
Docker start MyJava - для запуска контейнера
Kill - убивает если не отдачи 
создаем Dockerfile

откуда берем
FROM openjdk
куда копируем
COPY . /dok
где работаем
WORKDIR /dok
запуск один раз
RUN javac Main.java
каждый раз выполняем
CMD ["java", "Main"]
указываем порт
EXPOSE 8001

docker build . так мы строим образ укз путь в конце
docker image rm 2416703904e1 так можно удалить образ
docker run -p 3001:8001 247bde6c489a так мы можем сразу выводить порта
docker build -t php ./php - укз название образа и путь к файлу
docker run -p 999:80 -d php - запуск порта вначале на компе и к какому подкл и укз название images
docker-compose.yml - для сбора всех образов

version: '3.1'

services:
название для подключения
  db:
  добавляем в образ
    php:
    путь
    build: ./
    ports:
      - 8081:80
  образ
    image: mariadb:10.6
    указываем что делать если не запуститься 
    restart: always - перезапуск no для вывода из системы
    здесь монжо внсоить изменения логины пароль итд
    environment:
    пароль для входа
      MYSQL_ROOT_PASSWORD: 12345
название для подключения
  phpmyadmin:
    image: phpmyadmin
    restart: always
    ports:
      - 8080:80
    environment:
      - PMA_ARBITRARY=1

docker-compose build - построить образ
docker-compose up - запуск

вначале заходим в docker login
docker build -t никнейм/название ./ - так мы создаем образ для залива на docker hub


docker-compose run django django-admin startproject dockerfast . для запуска проекта где мы укз к кому обращаемся и какую комнаду выполняем с названием (которое мы даем) и путь куда добавим
docker up
docker-compose run django python manage.py migrate - так мы выполняем через обращение к файлу миграции
docker-compose run django python manage.py createuser - и выполняем создание админа
