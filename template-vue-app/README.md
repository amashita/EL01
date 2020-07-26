# EL01 template-app

develop for docker 

for mac

```
$ brew update
$ brew cask install xquartz
```

https://qiita.com/twu_go/items/8539bde01662c2a0a7a2


lainch docker container
```
$ docker-compose up -d --build
or
$ docker-compose up -d

$ docker-compose exec app bash
```

create vue project
```
cd src
vue create .
vue add electron-builder
```

run
```
npm run electron:serve
```

build
```
npm run electron:build
```

launch electron app
```
$ cd ~/app

$ ./node_modules/electron/dist/electron src
```