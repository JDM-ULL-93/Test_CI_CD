# Test_CI_CD

En este tutorial se listaran los pasos para desplegar un entorno con CI y CD

## Continuos Integration

Este paso es bastante sencillo y se realiza mediante **Github Actions**.

Vamos primero a realizarlo de forma manual y luego con ayuda del Marketplace de Github para los Actions:

### Manual

1. Creamos un fichero en .github/workflows/SetUpEnv.yml
```bash
    mkdir -p .github/workflows
    touch .github/workflows/SetUpEnv.yml
```
2. Vamos a crear un github action muy sencillo que solo va a mostrar por consola un "Hello World" para ver que el action se ejecuta correctamente:
```yml
    name: Hello World

    on:
        push:
            branches:
                - main
    jobs:
        hello_world:
            runs-on: ubuntu-latest
            steps:
                - name: Echo del mensaje
                  run: echo "Hola Mundo!!!"
```
3. Lo subimos al repositorio y tendremos que ver lo siguiente:



Para este ejemplo, vamos a desplegar un pipeline sencillo que se encargue de compilar y ejecutar las pruebas de nuestro proyecto Rust