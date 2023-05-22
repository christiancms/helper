# Tips

(At least in Java 8), you can use a lambda expression to shorten it to:
```java
 new Thread(() -> {
     //Do whatever
 }).start();
```
# Maven

` mvn clean install -DskipTests `<br>
` mvn validate `<br>
` mvn -Dtest=ListarRedeOcorrenciaAreaAfetadaRestTest test `<br>
` mvn -Dtest=ListarRedeOcorrenciaAreaAfetadaRestTest#deveListarAreaAfetadaPorRedeOcorrenciaRest test `<br>
