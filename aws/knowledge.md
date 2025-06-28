# 🧠 Serviços Essenciais da AWS

# 🧪 Exemplos AWS CLI com LocalStack

> Use `--endpoint-url=http://localhost:4566` em cada comando  
> ou crie um alias para simplificar:
>
> ```
> alias aws-local="aws --endpoint-url=http://localhost:4566 --profile localstack"
> ```

---

## 🔐 IAM (Identity and Access Management)
- **Função**: Gerencia usuários, permissões e políticas de acesso.
- **Exemplo**: Criar um usuário com permissão apenas para acessar o S3 e o DynamoDB.
#### 🔐 IAM (simulado, funcionalidade limitada no LocalStack)
```
aws-local iam create-user --user-name dev-user
```

---

## ⚡ AWS Lambda
- **Função**: Executa código sob demanda, sem precisar de servidor.
- **Exemplo**: Processar imagens automaticamente quando são enviadas ao S3.
```
aws-local lambda create-function \
  --function-name HelloWorld \
  --runtime nodejs18.x \
  --handler index.handler \
  --zip-file fileb://function.zip \
  --role arn:aws:iam::000000000000:role/lambda-role
```

---

## 💾 Amazon DynamoDB
- **Função**: Banco de dados NoSQL totalmente gerenciado, com baixa latência.
- **Exemplo**: Armazenar perfis de usuários de um aplicativo mobile.
```
aws-local dynamodb create-table \
  --table-name Users \
  --attribute-definitions AttributeName=id,AttributeType=S \
  --key-schema AttributeName=id,KeyType=HASH \
  --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

---

## 📬 Amazon SQS (Simple Queue Service)
- **Função**: Fila de mensagens para desacoplar sistemas.
- **Exemplo**: Uma API coloca pedidos em uma fila e um processador os consome em segundo plano.
```
aws-local sqs create-queue --queue-name my-queue
```

---

## 📢 Amazon SNS (Simple Notification Service)
- **Função**: Envio de mensagens e notificações para múltiplos destinos (e-mail, SMS, Lambda, SQS).
- **Exemplo**: Notificar por e-mail quando uma nova conta de usuário é criada.
```
aws-local sns create-topic --name my-topic
```

---

## 📊 Amazon CloudWatch
- **Função**: Monitoramento e logs de recursos da AWS.
- **Exemplo**: Criar um alarme quando o uso de CPU de uma instância EC2 ultrapassar 80%.
```
aws-local cloudwatch put-metric-data \
  --namespace "MyApp" \
  --metric-name "Requests" \
  --value 1
```

---

## 🪣 Amazon S3 (Simple Storage Service)
- **Função**: Armazenamento de objetos (arquivos) de forma escalável.
- **Exemplo**: Salvar arquivos de backup e documentos do sistema.
```
aws-local s3api create-bucket --bucket my-bucket
aws-local s3 cp myfile.txt s3://my-bucket/myfile.txt
```

---

## 👥 Amazon Cognito
- **Função**: Autenticação e gerenciamento de usuários para apps web e mobile.
- **Exemplo**: Login com e-mail/senha ou redes sociais em um app React.
```
aws-local cognito-idp create-user-pool --pool-name my-user-pool
```

---

## 💻 Amazon EC2 (Elastic Compute Cloud)
- **Função**: Computação sob demanda com instâncias de servidor virtual.
- **Exemplo**: Hospedar uma aplicação Java/Spring em uma instância Linux.
```
aws-local ec2 describe-instances
```

---
## 🚀 Amazon API Gateway
- **Função**: Criação e gerenciamento de APIs REST e WebSocket.
- **Exemplo**: Criar uma API pública que aciona funções Lambda em cada endpoint.
```
aws-local apigateway create-rest-api --name "MyAPI"
```

---

## 🧪 AWS Step Functions
- **Função**: Orquestração de workflows serverless com Lambda, SQS, etc.
- **Exemplo**: Criar um fluxo de aprovação com várias etapas e condições.
```
aws-local stepfunctions create-state-machine \
  --name "MyStateMachine" \
  --role-arn "arn:aws:iam::000000000000:role/service-role/StepFunctions-role" \
  --definition file://state-machine.json
```

---

## 🛡️ AWS WAF (Web Application Firewall)
- **Função**: Protege aplicações web contra ataques comuns (SQLi, XSS).
- **Exemplo**: Proteger uma API contra IPs maliciosos e ataques de injeção.

---

## 📉 Amazon RDS (Relational Database Service)
- **Função**: Banco de dados relacional gerenciado (MySQL, PostgreSQL, etc).
- **Exemplo**: Criar um banco PostgreSQL com backup e escalabilidade automática.

---

## 🧠 Amazon SageMaker
- **Função**: Treinar, implantar e gerenciar modelos de Machine Learning.
- **Exemplo**: Criar um modelo de recomendação de produtos e implantá-lo com API.

---

## 🌍 Route 53
- **Função**: Gerenciamento de DNS e balanceamento global.
- **Exemplo**: Registrar um domínio e apontá-lo para um site hospedado no S3.

---

## 🧰 AWS CloudFormation
- **Função**: Infraestrutura como código (IaC) para provisionar recursos AWS.
- **Exemplo**: Criar toda a stack de uma aplicação (S3, Lambda, API Gateway) com um único template YAML.
```
aws-local cloudformation create-stack \
  --stack-name mystack \
  --template-body file://template.yaml
```

---

## 🔐 AWS Secrets Manager
- **Função**: Armazenamento seguro de segredos e credenciais.
- **Exemplo**: Guardar tokens de API e senhas de banco para serem usados no Lambda.
```
aws-local secretsmanager create-secret \
  --name db-password \
  --secret-string '{"username":"admin","password":"123456"}'
```

---

## 🧹 AWS Glue
- **Função**: ETL (extração, transformação e carga) totalmente gerenciado.
- **Exemplo**: Unir dados de S3 e RDS, transformar e carregar no Redshift.

---

## 📦 AWS ECR (Elastic Container Registry) + 🐳 ECS / EKS
- **Função**: Gerenciamento e execução de containers Docker (ECS para serverless containers, EKS para Kubernetes).
- **Exemplo**: Hospedar uma aplicação containerizada backend em ECS com Fargate.
```
aws-local ecr create-repository --repository-name my-app
```

---
