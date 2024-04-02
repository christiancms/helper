### SQS (Simple Queue Service)
Orientado a microserviços: envia um mensagem para uma fila e essa mensagem pode ser consumida por outro serviço.

#### Maven
```
<dependency>
  <groupId>io.awspring.cloud</groupId>
  <artifactId>spring-cloud-starter-aws-messaging</artifactId>
</dependency>
```

#### Criando fila Queue(Standard) no SQS do LocalStack...
> aws --endpoint http://localhost:4566 --profile localstack sqs create-queue --queue-name sqsHelloWorld <br>
> aws --endpoint http://localhost:4566 --profile localstack sqs send-message --queue-url http://localhost:4566/000000000000/sqsHelloWorld --message-body "Hello World SQS!!" --delay-seconds 1 <br>
> aws --endpoint http://localhost:4566 --profile localstack sqs receive-message --queue-url http://localhost:4566/000000000000/sqsHelloWorld <br>


