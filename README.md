## Что такое DevOps. СI/СD - Елизар Самсонов

### Задание 1

**Что нужно сделать:**

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins [golang](https://golang.org/doc/install).
3. Используя свой аккаунт на GitHub, сделайте себе форк [репозитория](https://github.com/netology-code/sdvps-materials.git). В этом же репозитории находится [дополнительный материал для выполнения ДЗ](https://github.com/netology-code/sdvps-materials/blob/main/CICD/8.2-hw.md).
3. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта ```go test .``` и  ```docker build .```.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Ответ:

![image](https://github.com/elisar83/8-02-hw/assets/122297912/1f311a7a-d2c0-4683-9152-cc4ae49e8095)

![image](https://github.com/elisar83/8-02-hw/assets/122297912/4de7bf73-a33d-47e5-b716-c38d1a1c1b1b)

![image](https://github.com/elisar83/8-02-hw/assets/122297912/43fe43bc-d253-42ba-ba24-66b8868ea11b)


### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Ответ:
```
pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                git 'https://github.com/elisar83/8-02-hw.git'
            }
        }
        stage('Test') {
            steps {
                sh 'go test .'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
            }
        }
    }
}
 
```
![image](https://github.com/elisar83/8-02-hw/assets/122297912/41b27c92-1545-4d0b-a4dd-e297ae685175)


### Задание 3

**Что нужно сделать:**

1. Установите на машину Nexus.
1. Создайте raw-hosted репозиторий.
1. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
1. Загрузите файл в репозиторий с помощью jenkins.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Ответ:

![image](https://github.com/elisar83/8-02-hw/assets/122297912/3061db0a-e370-4180-9dcb-2f468e6e012b)

Добавляем третий шаг в my_pipe1:

![image](https://github.com/elisar83/8-02-hw/assets/122297912/a75e3436-5aa6-4a33-b3c6-cd8a78fe7d4d)

![image](https://github.com/elisar83/8-02-hw/assets/122297912/d3acfafd-e293-4771-ac63-d7d85ddf088e)

![image](https://github.com/elisar83/8-02-hw/assets/122297912/508b83f9-b3fc-4d61-aabf-fe1a2b28edd4)

![image](https://github.com/elisar83/8-02-hw/assets/122297912/f828e4bd-771c-4189-ade8-844118ad7de3)




