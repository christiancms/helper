### SQS (Simple Queue Service)
Microservices-oriented: sends a message to a queue and this message can be consumed by another service.

#### Maven
```
<dependency>
  <groupId>io.awspring.cloud</groupId>
  <artifactId>spring-cloud-starter-aws-messaging</artifactId>
</dependency>
```

#### Queue(Standard) no SQS do LocalStack...
> aws --endpoint http://localhost:4566 --profile localstack sqs create-queue --queue-name sqsHelloWorld <br>
> aws --endpoint http://localhost:4566 --profile localstack sqs send-message --queue-url http://localhost:4566/000000000000/sqsHelloWorld --message-body "Hello World SQS!!" --delay-seconds 1 <br>
> aws --endpoint http://localhost:4566 --profile localstack sqs receive-message --queue-url http://localhost:4566/000000000000/sqsHelloWorld <br>


