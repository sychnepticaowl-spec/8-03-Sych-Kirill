# 8-03-Sych-Kirill
Домашнее задание к занятию «GitLab»
#




Задание 2
```docker
GNU nano 7.2                   .gitlab-ci.yml                            
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
```
![Pipeline Status](https://github.com/sychnepticaowl-spec/8-03-Sych-Kirill/blob/main/screenshots/screenshot-pipeline.png?raw=true)
![Pipeline Status](https://github.com/sychnepticaowl-spec/8-03-Sych-Kirill/blob/main/screenshots/runner-settings.png?raw=true)

#
#
#
#
#
#
#
#
#
