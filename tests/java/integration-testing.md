

### Adding Test data
Before starting a testing, you can populate your database using the Junit5 @BeforeEach annotation.

```
@DataJpaTest
public class UserRepositoryIntegrationTest {

    @Autowired
    private UserRepository userRepository;

    @BeforeEach
    public void setUpTestData() {
        User user1 = new User("John Doe", "johndoe@gmail.com");
        User user2 = new User("Jane Smith", "janesmith@gmail.com");

        userRepository.save(user1);        userRepository.save(user2);
    }
}
```

### Mocks and Stubs
Mocking and stubbing helps you isolate your dependencies or mimic a dependency that has not been implemented yet. In the example given below, we are creating a mock for the UserRepository class.

```
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.mockito.Mockito.*;

public class UserServiceTest {

    @Test
    public void testCreateUser() {
        UserRepository userRepository = mock(UserRepository.class);
        UserService userService = new UserService(userRepository);
        User user = new User("John Doe", "john.doe@example.com");

        when(userRepository.save(user)).thenReturn(true);
        boolean result = userService.createUser(user);

        verify(userRepository, times(1)).save(user);
        assertEquals(true, result);
    }
}
```


### Setting up H2 Database
H2 is an in-memory database that is often used for testing as it is fast and lightweight. To configure H2 for integration tests, you can use the @DataJpaTest annotation provided by Spring Boot. This annotation sets up an in-memory database, and you can use your JPA repositories to interact with it.

```
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import static org.junit.jupiter.api.Assertions.assertEquals;

@DataJpaTest
public class UserRepositoryIntegrationTest {

    @Autowired
    private UserRepository userRepository;

    @Test
    public void testSaveUser() {
        User user = new User("John", "johndoe@example.com");
        userRepository.save(user);
        User savedUser = userRepository.findByEmail("johndoe@example.com");
        assertEquals(user.getName(), savedUser.getName());
        assertEquals(user.getEmail(), savedUser.getEmail());
    }
}
```
