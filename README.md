## About

A simple example of Laravel containerization with Docker. This example is intending to show you how to run Laravel with Nginx and MariaDB through Docker.

## Requirement

- Docker >= 19.03.5
- Docker-compose >= 1.25.4

## Installing

- Open your terminal and create the project as usual:
```
laravel new your_app_name
```

- Go inside the folder:
```
$ cd your_app_name
```

- Create the **docker-compose.yml** file and copy our configuration content to your project:
```
$ touch docker-compose.yml
```

- Create the docker configuration folder named **docker** and set it up based your requirement:
```
$ mkdir docker
```

- Do not forget to set up your app url at __docker__/__nginx__/__conf.d__/__default.conf__ on the **server_name** section.

- Install the dependencies:
```
$ docker run --rm -v $(pwd):/app composer:1.9.3 install
```

- Do the docker-compose and wait for the processes:
```
$ docker-compose up -d
```

- Check if the all containers `running`:
```
$ docker ps -a
```

- Create your own `.env` file and setting it based your docker configuration:
```
$ cp .env.example .env
```

- Generate your project key:
```
$ docker-compose exec app php artisan key:generate
```

- Do migration (if needed):
```
$ docker-compose exec app php artisan migrate
```

- Open your web browser and open `http://your_app_name.test`
