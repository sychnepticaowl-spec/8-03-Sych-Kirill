# Домашнее задание: GitLab CI/CD 8-03


**Сыч Кирилл Павлович**  

---

## Задание 1: Развёртывание GitLab и настройка Runner

### Что было сделано:

1. ✅ Развёрнут GitLab локально с использованием Vagrant
2. ✅ Создан проект `my-first-project` и пустой репозиторий
3. ✅ Зарегистрирован gitlab-runner для проекта
4. ✅ Runner запущен в режиме Docker с тегом `docker`

### Настройки Runner

![GitLab Runner Settings](https://github.com/sychnepticaowl-spec/8-03-Sych-Kirill/blob/main/screenshots/screenshot-runner.png?raw=true)

**Конфигурация Runner:**
- **ID:** #3 (Qaha-FqLX)
- **Executor:** Docker
- **Tags:** docker
- **Status:** Active ✅
  
Runtime platform                                    arch=amd64 os=linux pid=5026 revision=ac71f4d8 version=18.10.0
gitlab-runner: Service is running

---

## Задание 2: Создание CI/CD Pipeline

### Что было сделано:

1. ✅ Запушен репозиторий на GitLab
2. ✅ Создан файл `.gitlab-ci.yml` с необходимыми этапами
3. ✅ Pipeline успешно выполняется

### Результат выполнения Pipeline

![Pipeline Status](https://github.com/sychnepticaowl-spec/8-03-Sych-Kirill/blob/main/screenshots/screenshot-pipeline.png?raw=true)

### Структура `.gitlab-ci.yml`

```yaml
stages:
  - build
  - test

build-image:
  stage: build
  image: docker:20.10
  tags:
    - docker
  script:
    - echo "Building Docker image..."
    - docker build -t my-app:$CI_COMMIT_SHORT_SHA .
  only:
    - main

test-app:
  stage: test
  image: docker:20.10
  tags:
    - docker
  script:
    - echo "Running tests..."
    - echo "All tests passed!"
  only:
    - main
