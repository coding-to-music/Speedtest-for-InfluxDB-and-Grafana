# Speedtest-for-InfluxDB-and-Grafana

# 🚀 **Speedtest.net Collector For InfluxDB and Grafana** 🚀

https://github.com/coding-to-music/Speedtest-for-InfluxDB-and-Grafana

From / By https://github.com/barrycarey/Speedtest-for-InfluxDB-and-Grafana

https://hub.docker.com/r/barrycarey/speedtest-for-influxdb-and-grafana

## Environment variables:

```java

```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/Speedtest-for-InfluxDB-and-Grafana.git
git push -u origin main
```

## docker-compose up

```java
docker-compose up
```

Output:

```java

```

## docker-compose down

```
docker-compose down
```

Output

```java

```

## checking ports and who uses them

https://linuxhandbook.com/check-open-ports-linux/

```
sudo netstat -nlp
```

```java
sudo lsof -i

sudo lsof -i -P -n

sudo lsof -i -P -n | grep LISTEN

nc -z -v <IP-ADDRESS> 1-65535 2>&1 | grep -v 'Connection refused'

sudo netstat -lptu

sudo netstat -tulpn

nc -z -v <IP-ADDRESS> 1-65535 2>&1 | grep -v 'Connection refused'

```

## Docker commands

```
docker-compose up

docker-compose down

docker-compose up --remove-orphans

docker-compose restart grafana

docker ps

docker volume ls
```

## **Speedtest.net Collector For InfluxDB and Grafana**

![Screenshot](https://puu.sh/tmfOA/b5576e88de.png)

This tool is a wrapper for speedtest-cli which allows you to run periodic speedtets and save the results to Influxdb

## Configuration within config.ini

#### GENERAL

| Key   | Description        |
| :---- | :----------------- |
| Delay | Delay between runs |

#### INFLUXDB

| Key      | Description                                     |
| :------- | :---------------------------------------------- |
| Address  | Delay between updating metrics                  |
| Port     | InfluxDB port to connect to. 8086 in most cases |
| Database | Database to write collected stats to            |
| Username | User that has access to the database            |
| Password | Password for above user                         |

#### SPEEDTEST

| Key    | Description                                          |
| :----- | :--------------------------------------------------- |
| Server | Comma sperated list of servers. Leave blank for auto |

#### LOGGING

| Key   | Description                           |
| :---- | :------------------------------------ |
| Level | Set how verbose the console output is |

## Usage

Before the first use run

```
pip3 install -r requirements.txt
```

Enter your desired information in config.ini

Run influxspeedtest.py

**Custom Config File Name**

If you wish to use a config file by a different name set an ENV Variable called influxspeedtest. The value you set will be the config file that's used.

**_Requirements_**

Python 3+

You will need the influxdb library installed to use this - [Found Here](https://github.com/influxdata/influxdb-python)
You will need the speedtest-cli library installed to use this - [Found Here](https://github.com/sivel/speedtest-cli)

## Docker Setup

1. Install [Docker](https://www.docker.com/)

2. Make a directory to hold the config.ini file. Navigate to that directory and download the sample config.ini in this repo.

```bash
mkdir speedtest
curl -o speedtest/config.ini https://raw.githubusercontent.com/barrycarey/Speedtest-for-InfluxDB-and-Grafana/master/config.ini
cd speedtest
```

3. Modify the config file with your influxdb settings.

```bash
nano config.ini
```

Modify the 'Address =' line include the ip or hostname of your influxdb instance.
Example:

```bash
Address = 10.13.14.200
```

4. Run the container, pointing to the directory with the config file. This should now pull the image from Docker hub. You can do this by either running docker run or by using docker-compose.
1. The docker run option.

```bash
docker run -d \
--name="speedtest" \
-v config.ini:/src/config.ini \
--restart="always" \
barrycarey/speedtest-for-influxdb-and-grafana
```

2.  The docker-compose option

```bash
curl -O https://raw.githubusercontent.com/barrycarey/Speedtest-for-InfluxDB-and-Grafana/master/docker-compose.yml docker-compose.yml
docker-compose up -d
```
