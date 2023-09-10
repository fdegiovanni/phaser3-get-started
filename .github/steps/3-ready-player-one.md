## Step 3: Ready player one

_¡Exelentes noticias! Conociste lo basico del scaffolding de tu primer juego :sparkles:_

¿Qué es un videojuego sin un personaje? En este paso, veremos cómo agregar un personaje a nuestro juego. También aprenderemos sobre los grupos de objetos y cómo usarlos para crear plataformas.

> :warning: <br> 🚨 A partir de ahora, solo trabajaremos con el archivo `script.js`. Por lo que deberemos tener cuidado.🚨

### :keyboard: Actividad: Agregando un personaje y plataformas

1.  Hace un pull del proyecto en tu computadora, mediante la terminal de VSCode.

    ```bash
    git pull
    ```

1.  Vamos a modificar el metodo create de la clase Game, para agregar un personaje y plataformas. El codigo queda asi:

    ```js
    create() {
        this.add.image(400, 300, "sky");

        this.platforms = this.physics.add.staticGroup();
        this.platforms.create(400, 568, "ground").setScale(2).refreshBody();
        this.platforms.create(600, 400, "ground");
        this.platforms.create(50, 250, "ground");
        this.platforms.create(750, 220, "ground");

        this.anims.create({
          key: "left",
          frames: this.anims.generateFrameNumbers("dude", { start: 0, end: 3 }),
          frameRate: 10,
          repeat: -1,
        });

        this.anims.create({
          key: "turn",
          frames: [{ key: "dude", frame: 4 }],
          frameRate: 20,
        });

        this.anims.create({
          key: "right",
          frames: this.anims.generateFrameNumbers("dude", { start: 5, end: 8 }),
          frameRate: 10,
          repeat: -1,
        });

        this.player = this.physics.add.sprite(100, 450, "dude");
        this.player.setBounce(0.2);
        this.player.setCollideWorldBounds(true);

        /*
        Se agrega la colisión entre el personaje y las plataformas. Esto hace que el personaje no pueda atravesar las plataformas.
        */
        this.physics.add.collider(this.player, this.platforms);
    }
    ```

    #### Vamos a explicarlo un poco:

    A. Lo primero que haremos sera eliminar la estrella que habiamos agregado en el paso anterior.

    ```js
    // this.add.image(400, 300, "star"); borrar linea
    ```

    B. Luego, crear un grupo de plataformas estáticas. En dicho grupo, crearemos cuatro plataformas en diferentes posiciones en el juego, utilizando el sprite "ground" para representarlas. La primera plataforma se escala al doble de su tamaño original y se actualiza su cuerpo físico.

    ```js
    this.platforms = this.physics.add.staticGroup();
    this.platforms.create(400, 568, "ground").setScale(2).refreshBody();
    this.platforms.create(600, 400, "ground");
    this.platforms.create(50, 250, "ground");
    this.platforms.create(750, 220, "ground");
    ```

    C. Lo siguiente es crear las animaciones, del personaje. Para eso usaremos `anims.create`.

    - En la primera: se crea la animación "left" utilizando los frames 0, 1, 2 y 3 del spritesheet "dude". Se utilizara cuando el personaje se mueva a la izquierda.

      ```js
      this.anims.create({
        key: "left",
        frames: this.anims.generateFrameNumbers("dude", { start: 0, end: 3 }),
        frameRate: 10,
        repeat: -1,
      });
      ```

    - En la segunda: se crea la animación "turn" utilizando el frame 4 del spritesheet "dude". Se utilizara cuando el personaje no se mueva.

      ```js
      this.anims.create({
        key: "turn",
        frames: [{ key: "dude", frame: 4 }],
        frameRate: 20,
      });
      ```

    - En la tercera: se crea la animación "right" utilizando los frames 5, 6, 7 y 8 del spritesheet "dude". Se utilizara cuando el personaje se mueva a la derecha.

      ```js
      this.anims.create({
        key: "right",
        frames: this.anims.generateFrameNumbers("dude", { start: 5, end: 8 }),
        frameRate: 10,
        repeat: -1,
      });
      ```

    D. Agregaremos el personaje al juego. Se le agrega un rebote de 0.2. Se le agrega la propiedad de colisionar con los bordes del mundo.

    ```js
    this.player = this.physics.add.sprite(100, 450, "dude");
    this.player.setBounce(0.2);
    this.player.setCollideWorldBounds(true);
    ```

    E. Por ultimo, agregaremos la colisión entre el personaje y las plataformas. Esto hace que el personaje no pueda atravesar las plataformas.

    ```js
    this.physics.add.collider(this.player, this.platforms);
    ```

1.  Es hora de visualizar lo que hemos hecho. Para ello, deberas abrir el archivo `index.html` en tu navegador. Para ello, puedes hacerlo de dos formas:

    - Haciendo click derecho sobre el archivo y seleccionando la opcion `Abrir con Live Server`.
    - Haciendo click en el boton `Go Live` que se encuentra en la parte inferior derecha de VSCode.

    Luego de ello, deberas ir a tu navegador o browser favorito y abrir la url `http://localhost:5500/`. Deberas ver algo como esto:
    <img src="https://github.com/fdegiovanni/phaser3-get-started/blob/main/videos/ready-player-one-demo.gif" width="50%" alt="Ready player one" />

1.  Por favor, realiza un commit con los cambios realizados y sube los cambios a tu repositorio remoto con los siguientes comandos, ejecutalos en la Terminal de VSCode.

    ```bash
    git add .
    git commit -m "commit player"
    git push
    ```

1.  Espera unos 20 segundos y luego actualiza esta página (desde la que estás siguiendo las instrucciones). [GitHub Actions](https://docs.github.com/es/actions) se actualizará automáticamente al siguiente paso.
