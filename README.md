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

### Protect with TLS

The communication with the MQTT-Server can be protected with a ssl connection.

It is possible to use your own certificates or create a new one with this tool: [erkenes/ssl-certs-local](https://github.com/erkenes/ssl-certs-local)

First create a CA-certificate and a certificate for the domain of your MQTT-Server.

Now paste the created certificates into the folder `Data/conf/certs`. You need the files `ca.crt`, `server.crt` and `server.key`.

After that open the file `Data/conf/mosquitto.conf` and uncomment the lines shown above:

```text
cafile /mosquitto/config/certs/ca.crt
certfile /mosquitto/config/certs/server.crt
keyfile /mosquitto/config/certs/server.key
```
#### Require a valid certificate

If all clients need a valid certificate uncomment the following line in the `mosquitto.conf`-file:

```text
require_certificate true
```

#### Disable unsecured connections

In the `docker-compose.yml`-file remove the line with the port `1883:1883` to disable unsecured  connections.