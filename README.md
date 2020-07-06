# docker-compose-laravel
A pretty simplified docker-compose workflow that sets up a LEMP network of containers for local Laravel development. 

## Pre-requisite

* [Docker installed](https://docs.docker.com/docker-for-mac/install/) on your system.


## Usage

Clone this repository:
 ```bash
git clone [repo-name]
```

First, create and `src` folder.
 
Add your entire Laravel project to the `src` folder if it exists.

You can also create a new project by running:
 ```bash
docker-compose run -rm composer create-project laravel/laravel ./
```

Create a `mysql` folder in the project root directory, alongside the `nginx` and `src` folders. This will hold your data and ensure persistent data which remains after bringing containers down and back up.
 
Then open a terminal and from this cloned repository's root run
 ```bash
docker-compose up -d --build
```
  
Open up your browser of choice to [http://localhost:8080](http://localhost:8080) and you should see your Laravel app running as intended.
 
**Your Laravel app needs to be in the src directory first before bringing the containers up, otherwise the artisan container will not build, as it's missing the appropriate file.** 

Containers created and their ports (if used) are as follows:

- **nginx** - `:8080`
- **mysql** - `:3306`
- **php** - `:9000`
- **npm**
- **composer**
- **artisan**

**NB:** Containers npm, composer and artisan are there to handle Composer, NPM, and Artisan commands without having to have these platforms installed on your local computer.


### Additional Guide
#### Docker Compose

**Start Services**

To start up the services run
```bash 
docker-compose up -d --build
```

* `-d` starts all services in a detached mode (no logs)

**Stop Services**

To stop all the services run
```bash 
docker-compose down
```

**Log Services**

To view logs of all running services
```bash 
docker-compose logs -f -t
```

* `-f` follow the log output
* `-f -t` gives you timestamps


#### Laravel with Docker Compose 

**Create a Laravel Project**

The Laravel project files will be installed in the `src` folder when you specify `./`. 
```bash 
docker-compose run -rm composer create-project laravel/laravel ./
```

**Make Migrations**

```bash 
docker-compose run --rm artisan migrate
```

**Install package to Laravel Project**

```bash 
docker-compose run --rm composer require [package-name]
```

**Update packages to Laravel Project**

```bash 
docker-compose run --rm composer update
```

**NPM Install to Laravel Project**

```bash 
docker-compose run --rm npm install
```

**Compile static files**

```bash 
docker-compose run --rm artisan migrate
```

### References

* [Create a local Laravel dev environment with Docker](https://www.youtube.com/watch?v=5N6gTVCG_rw)
* [A much better local Laravel dev environment with Docker](https://www.youtube.com/watch?v=I980aPL-NRM)

