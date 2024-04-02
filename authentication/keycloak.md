#### Keycloak
copy jar file to deployments folder to be available for new custom authentication
```
docker cp keycloak-ip-filter.jar c4f37be58ad5:${KEYCLOAK_HOME}/standalone/deployments/
```
