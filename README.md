# filelist-api

How to build
```shell
docker build -t myregistry.example.com/filelist-api-whitelist:1
```

Compose file
```
version: '3.2'
services:
    changedetection:
      image: myregistry.example.com/filelist-api-whitelist:1 .
      container_name: filelist-api
      environment:
        - FL_USERNAME=YOUR_USER
        - FL_PASSWORD=YOUR_PASSWORD
        - CHECK_INTERVAL=10 #in minutes I suggest putting more than 5 minutes.
        - DRIVER=chrome # container_name of browserless port is always 3000
      restart: unless-stopped

    browserless-chrome:
      container_name: chrome
      image: browserless/chrome
      restart: unless-stopped
```

