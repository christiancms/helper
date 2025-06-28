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
### Configure:
```
aws configure
```

O CLI irá te guiar por algumas perguntas. Para o Brasil, a região padrão da AWS é ```sa-east-1``` (São Paulo).

- ```AWS Access Key ID [None]```: Aqui você pode inserir suas credenciais AWS reais se for interagir com a AWS na nuvem. Se você está usando apenas LocalStack, você pode colocar valores fictícios como ```test``` ou ```foo``` (o LocalStack geralmente não valida credenciais). Se já tiver um ID, ele aparecerá entre colchetes.

- ```AWS Secret Access Key [None]```: Da mesma forma, para LocalStack, pode ser ```test``` ou ```bar```. Para AWS real, insira sua chave secreta.

- ```Default region name [None]```: Esta é a parte importante para o seu erro. Digite ```sa-east-1``` e pressione Enter.
  - Região de São Paulo (Brasil): ```sa-east-1```

- ```Default output format [None]```: Você pode deixar em branco para o padrão, ou digitar ```json``` (que é o mais comum e recomendado para scripts e automação), ```text``` ou ```table```.

Um exemplo de como seria a interação:
```
aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE # Ou "test" para LocalStack
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY # Ou "test" para LocalStack
Default region name [None]: sa-east-1
Default output format [None]: json
```
### Local da instalação
O AWS CLI salva essas informações em dois arquivos no seu diretório de usuário (normalmente ```~/.aws/``` no Linux/Ubuntu):

- ```~/.aws/credentials```: Armazena as chaves de acesso (Access Key ID e Secret Access Key).

- ```~/.aws/config```: Armazena a região padrão, o formato de saída e outras configurações.

### Explicando o comando:

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
