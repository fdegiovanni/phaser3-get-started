## Step 5: Publicar el juego

_¡Ya casi terminamos! :heart:_

Ya tenemos un juego completo, pero solo lo podemos jugar en nuestra computadora. Ahora vamos a publicarlo para que todos puedan jugarlo.
Para eso utilizaremos un servicio llamado [GitHub Pages](https://pages.github.com/).

### :keyboard: Actividad: Deploy del juego

1.  Hace un pull del proyecto en tu computadora, mediante la terminal de VSCode.

    ```bash
    git pull
    ```

1.  Vamos a modificar la configuración del juego para que se vea centrado en el navegador y para que escale al tamaño de la pantalla. Para ello reemplazaremos el contenido del archivo `script.js` en el lugar de la config por el siguiente:

    ```js
    const config = {
      type: Phaser.AUTO,
      width: 800,
      height: 600,
      scale: {
        mode: Phaser.Scale.FIT,
        autoCenter: Phaser.Scale.CENTER_BOTH,
      },
      physics: {
        default: "arcade",
        arcade: {
          gravity: { y: 200 },
          debug: false,
        },
      },
      scene: Game,
    };
    ```

1.  Es hora de visualizar lo que hemos hecho. Para ello, deberas abrir el archivo `index.html` en tu navegador. Para ello, puedes hacerlo de dos formas:

    - Haciendo click derecho sobre el archivo y seleccionando la opcion `Abrir con Live Server`.
    - Haciendo click en el boton `Go Live` que se encuentra en la parte inferior derecha de VSCode.

    Luego de ello, deberas ir a tu navegador o browser favorito y abrir la url `http://localhost:5500/`.

1.  Pero espera. ¿No habiamos dicho de utilizar GitHub Pages? Claro, bien, para eso debemos realizar el deploy con GitHub Pages...

    A. Ir a la pestaña `Settings` de nuestro repositorio.

    B. Buscar la sección `GitHub Pages`.

    Acceso rapido: [GitHub Pages](../../settings/pages){:target="\_blank" rel="noopener"}

    C. En el desplegable de `Source` vamos a seleccionar la opción `Deploy from a branch`.

    D. En el desplegable de `Branch` vamos a seleccionar la opción `main`.

    E. En el desplegable de `Folder` vamos a seleccionar la opción `/docs`.

    F. Por ultimo, hacemos click en el boton `Save`.

    <video src="../../videos/github-pages.mp4" width="50%" controls></video>

1.  Luego de hacer clic en el boton `Save`, se te va a brindar una URL donde se encuentra publicado tu juego. El formato de la misma es `https://<username>.github.io/<repository-name>/`. Por ejemplo, en este caso quedará parecida a `https://username.github.io/phaser3-get-started/`.

1.  Vamos a subir los cambios para poder terminar este tutorial. Para eso, debes hacer un commit con los cambios realizados y subir los cambios a tu repositorio remoto con los siguientes comandos, ejecutalos en la Terminal de VSCode.

    ```bash
    git add .
    git commit -m "commit deploy"
    git push
    ```

1.  Espera unos 20 segundos y luego actualiza esta página (desde la que estás siguiendo las instrucciones). [GitHub Actions](https://docs.github.com/es/actions) se actualizará automáticamente al siguiente paso.
