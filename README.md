## Что такое DevOps. СI/СD - Елизар Самсонов

# Задание 1
Что нужно сделать:

Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
Установите на машину с jenkins golang.
Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
**Ответ:
![image](https://user-images.githubusercontent.com/122297912/234108598-78dd31d1-c065-416c-ad34-1c1405333742.png)
![image](https://user-images.githubusercontent.com/122297912/234109432-213324f0-f5c0-4486-ae7f-f49d6d8f8a63.png)

Console Output:
Started by user admin
Running as SYSTEM
Building in workspace /root/.jenkins/workspace/Netology
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /root/.jenkins/workspace/Netology/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/elisar83/8-02-hw.git # timeout=10
Fetching upstream changes from https://github.com/elisar83/8-02-hw.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/elisar83/8-02-hw.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
 > git rev-list --no-walk da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
[Netology] $ /bin/sh -xe /tmp/jenkins16937702646529523043.sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
+ docker build . -t ubuntu-bionic:8082/hello-world:v4
#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.0s

#2 [internal] load .dockerignore
#2 transferring context: 2B done
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 ...

#4 [internal] load metadata for docker.io/library/alpine:latest
#4 DONE 0.5s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 0.6s

#5 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:124c7d2707904eea7431fffe91522a01e5a861a624ee31d03372cc1d138a3126
#5 DONE 0.0s

#6 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 3.63kB done
#7 DONE 0.0s

#8 [stage-1 2/3] RUN apk -U add ca-certificates
#8 CACHED

#9 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#9 CACHED

#10 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#10 CACHED

#11 [builder 3/4] COPY . ./
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:c8181a12e69e977cbaa2fb0b302014cfe4ab951e99453bb01ca7fdcb6dafdf90 done
#13 naming to ubuntu-bionic:8082/hello-world:v4 done
#13 DONE 0.0s
Finished: SUCCESS

# Задание 2
Что нужно сделать:

Создайте новый проект pipeline.
Перепишите сборку из задания 1 на declarative в виде кода.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

# Задание 3
Что нужно сделать:

Установите на машину Nexus.
Создайте raw-hosted репозиторий.
Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
Загрузите файл в репозиторий с помощью jenkins.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
