## How airflow Works

### single node architecture

#### webserver

- fetch some data from metadatabase

#### Metastore(Metadatabase)

### Scheduler

- trigres schedules workflows

### Executor

> an Executor is a configuration property of the scheduler. It defines how your tasks will be executed. There are several executors available in Airflow, and you can also define your own.


- queue is just a list of tasks
- interacts with metastore to fetch the task to be done
- executes the task
- reports the status of the task to the scheduler

### Multi node architecture

#### Node 1

- Webserver
- Scheduler
- Executor
  - Celery
  - Dask
  - Kubernetes
  - Local
  - Mesos
  - SSH
  - WinRM

#### Node 2

- Metastore
- Queue 
  - RabbitMQ
  - Redis

#### Worker node

- airflow worker
  - executes the task

### docker-yaml file 내부 서비스

- airflow-scheduler : 모든 task와 DAG를 모니터링
- airflow-webserver : 스케줄러로부터 부여한 task 실행을 위한 worker 
- airflow-init : 서비스 초기화
- postgres : db
- redis : 스케줄러에서 워커로 메시지를 보내는 브로커
  * 서비스는 Celery Executor로 실행됨

