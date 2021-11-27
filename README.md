# smarthome-control-mqtt

A mqtt server hosted with docker to control (primary) smart-home devices

## Usage

Start the container with

```shell
docker-compose up -d

# for docker-compose V2
docker compose up -d
```

## Authentication

Default user: mosquitto<br />
Default password: admin

To change the password (or the username), start the containers and run

```shell
docker-compose exec mosquitto mosquitto_passwd -c /mosquitto/config/mosquitto.passwd your_username

# for docker-compose V2
docker compose exec mosquitto mosquitto_passwd -c /mosquitto/config/mosquitto.passwd your_username

```

Replace `your_username`with the username you want to use. Remember: All other user accounts will be replaced!