# Dev environment for pet project
Simple Compose App to show products data from the database. 
It contains Apache, PHP and MySQL.

### Preparation steps
Create next files using `*.dist` examples.
- `.env`

Choose any passwords for db root user.

### Start application
Start containers:
```
docker-compose up -d
```
You can use `--build` option to force rebuild images.
```
docker-compose up -d --build
```

Check application on http://localhost:8080

### Database migrations
To execute database migrations, you should
- connect to the API service container,
- run migrate command.

Example for Product API:
```
docker exec -it devenvironment_product-api_1 /bin/bash
./vendor/bin/doctrine-migrations migrate
```
You can connect to MySQL server (localhost:3306) from host.

### Stop application
To stop containers run:
```
docker-compose down
```

### Install Xdebug
Connect to the API service container and run `install_xdebug.sh` script.

Example for Product API:
```
docker exec -it devenvironment_product-api_1 /bin/bash
cd /scripts
./install_xdebug.sh
```
You should get success message.
After that add server (localhost:8080) and set mapping (API -> /data/app) in the IDE.

### Remove Xdebug
Connect to the API service container and run `uninstall_xdebug.sh` script.

Example for Product API:
```
docker exec -it devenvironment_product-api_1 /bin/bash
cd /scripts
./uninstall_xdebug.sh
```
You should get success message.
