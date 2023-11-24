### docker-yaml file 내부 서비스

- airflow-scheduler : 모든 task와 DAG를 모니터링
- airflow-webserver : 스케줄러로부터 부여한 task 실행을 위한 worker 
- airflow-init : 서비스 초기화
- postgres : db
- redis : 스케줄러에서 워커로 메시지를 보내는 브로커
  * 서비스는 Celery Executor로 실행됨

