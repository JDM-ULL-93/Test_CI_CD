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
                - name: Echo del mensaje.
                  run: echo "Hola Mundo!!!"
                -name: Muestra el contenido de la maquina.
                  run: ls -la
```
3. Lo subimos al repositorio y tendremos que ver el siguiente punto::

 ![1](./img/1.png) 

 Indicando que se esta ejecutando . Si todo se ha realizado correctamente, tendremos el siguiente "check verde" final:

 |[2](./img/2.png)

 4. Vamos a complicar nuestro ejemplo.
    1. 

Para este ejemplo, vamos a desplegar un pipeline sencillo que se encargue de compilar y ejecutar las pruebas de nuestro proyecto Rust