# TP — GitHub Actions (CI/CD)

- main.yml: Se llama cuando se hace una pull request o se actualiza la rama que participa en una ya existente
- release.yml : Se llama cuando se pushea un commit con tag v*, *, *
- build: Instala java en su verison 17(incluyendo maven y todas sus dependencias) con la distribucion de temurin y ejecuta el comando mvn compile en la carpeta que contiene el TP-4
- test: Instala java en su verison 17(incluyendo maven y todas sus dependencias) con la distribucion de temurin y ejecuta el comando mvn test en la carpeta que contiene el TP-4

Se hizo una pull request a la rama test/workflow_main_test que solo contenia commits con archivos .txt vacios para comprobar que funciona y luego se modifico el test ThresholdAlertServiceTest para que falle

Workflow sin alterar los test

![CI exitosa](images/ci_success.png)

Workflow tras alterar los test

![CI fallida](images/ci_fail.png)

CI (Continuous Integration) verifica automáticamente cada Pull Request hacia main. El pipeline compila el proyecto y ejecuta los tests para detectar errores antes de integrar cambios a la rama principal.

CD (Continuous Delivery) se ejecuta al crear un tag(vX.Y.Z). El pipeline empaqueta la aplicación, genera el archivo JAR y publica automáticamente un GitHub Release con el artefacto adjunto y notas de versión generadas por GitHub.
