##1. Установка Docker
- Установите необходимые пакеты:
`sudo apt install apt-transport-https ca-certificates curl software-properties-common`
- Добавьте ключ репозитория Docker:
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- Добавьте репозиторий Docker:
`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
- Обновите список пакетов:
`sudo apt update`
- Установите Docker:
`sudo apt install docker-ce`
##2. Клонирование репозитория
- Склонируйте репозиторий
`git clone https://github.com/SpriteCT/iTopDocker`
- Установите переменные окружения в файле .env
```env
MYSQL_USER=
MYSQL_PASSWORD=
MYSQL_DATABASE=
MYSQL_ROOT_PASSWORD=
```

##3. Запуск контейнеров
- Перейдите в директорию с склонированным репозиторием
`cd iTopDocker`
- Запустите docker-compose
`docker-compose up --build`
##4. Первичная настройка
- При обращении к localhost:80 откроект инсталлятор iTop. В конфигурации БД указываем имя сервера **mysql** . Остальные поля заполнить, как и в файле .env