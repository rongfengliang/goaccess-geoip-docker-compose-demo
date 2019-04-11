# goaccess with geoip demo

## how to running

* copy log file

```code
mkdir  logs
copy into logs && with name access.log
```

* start docker-compose

```code
docker-compose up -d
```

* view realtime metrics

```code
open http://localhost:8080
```

## iis w3c log test

* log-format

```code
%d %t %^ %m  %U %q %^ %^ %h %u %s %^ %^ %T
```

* log filed

```code
#Fields: date time s-ip cs-method cs-uri-stem cs-uri-query s-port cs-username c-ip cs(User-Agent) sc-status sc-substatus sc-win32-status time-taken

```

* note

more info about log-foramt see https://goaccess.io/man#custom-log

## some note

if you want to build your docker image see build/Dockerfile (with source code build)