### Arquitetura Clean Code ###
A Arquitetura Clean Code (limpa) é uma abordagem em que a separação de responsabilidades é clara e as dependências estão organizadas de fora para dentro. O domínio da aplicação é o núcleo, e as dependências de frameworks e tecnologias externas são invertidas para dependências mínimas do domínio.

__Componentes:__
* __Entities (Entidades):__ Modelam o negócio.
* __Use Cases:__ Regras de negócio.
* __Interface Adapters:__ Adaptam a entrada e saída (UI, bancos de dados).
* __Frameworks and Drivers:__ Infraestrutura e detalhes de implementação.
* 
__Diagrama:__

```
  +--------------------------------+
  |          Frameworks/Drivers     |
  +--------------------------------+
           ^              ^
           |              |
  +--------+--------------+--------+
  |       Interface Adapters       |
  +-------------------------------+
                  ^
                  |
  +---------------+---------------+
  |           Use Cases            |
  +-------------------------------+
                  ^
                  |
  +---------------+---------------+
  |           Entities             |
  +-------------------------------+
```

```
// Entidade
public class User {
    private String id;
    private String name;
    // getters and setters
}

// Caso de uso
public class CreateUserUseCase {
    private final UserRepository userRepository;

    public CreateUserUseCase(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public void execute(User user) {
        userRepository.save(user);
    }
}

// Adaptador para Banco de Dados
public class UserRepositoryImpl implements UserRepository {
    // Implementação JPA
    @Override
    public void save(User user) {
        // persistir usuário
    }
}

```
