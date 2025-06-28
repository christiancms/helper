### AWS-cli

### Install

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
Teste:
```
aws --version
```
Vamos quebrar o comando:

- ```aws```: É o comando principal da AWS Command Line Interface (CLI), uma ferramenta que permite interagir com os serviços da AWS a partir do seu terminal.

- ```--endpoint http://localhost:4566```: Esta é a parte crucial neste contexto. Ela sobrescreve o endpoint padrão da AWS (que seria, por exemplo, ```https://sts.amazonaws.com```) e direciona a requisição para ```http://localhost:4566```.

  - ```localhost```: Significa que a requisição está sendo enviada para a sua própria máquina.

  - ```4566```: É a porta padrão que o LocalStack geralmente usa para simular os serviços da AWS localmente.

- ```sts```: Refere-se ao serviço AWS Security Token Service (STS). Este serviço permite que você solicite credenciais temporárias e obtenha informações sobre as identidades que estão realizando chamadas à AWS.

- ```get-caller-identity```: É a operação específica do serviço STS. Esta operação retorna detalhes sobre o usuário IAM ou perfil (role) cujas credenciais estão sendo usadas para fazer a chamada. A saída geralmente inclui:

 - ```UserId```: Um identificador único para a entidade que está fazendo a chamada.

 - ```Account```: O ID da conta AWS à qual a identidade pertence.

 - ```Arn```: O Amazon Resource Name (ARN) associado à identidade.
```
aws --endpoint http://localhost:4566 sts get-caller-identity
```
