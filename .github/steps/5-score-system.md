## Step 5: Sistema de puntaje

_¡Como se mueve ese Dude! 💃_

Podemos mover el personaje, pero aun no podemos hacer mucho mas que ir a los lados y saltar por las plataformas. ¿Donde esta el riesgo y lo divertido?
Es un buen momento de implementar un sistema de recompensa y castigo. Para ello, vamos a crear un sistema de puntaje que nos permita sumar puntos cuando el personaje recolecte monedas y perder puntos cuando el personaje toque a los enemigos. Nos enfocamos en lo primero en este paso.
Tambien vamos a mostrar el puntaje en pantalla.

> :warning: <br> 🚨 Recuerda, solo trabajaremos con el archivo `script.js`. Por lo que deberemos tener cuidado.🚨

### :keyboard: Actividad: Crear un sistema de puntaje

1.  Hace un pull del proyecto en tu computadora, mediante la terminal de VSCode.

    ```bash
    git pull
    ```

1.  Vas a modificar el metodo `create` de la clase Game. En el mismo vamos a realizar varias actividades que explicaremos debajo.

    ```js
        create() {
            // TODO EL CODIGO ANTERIOR

            this.stars = this.physics.add.group({
              key: "star",
              repeat: 11,
              setXY: { x: 12, y: 0, stepX: 70 },
            });

            this.stars.children.iterate(function (child) {
              child.setBounceY(Phaser.Math.FloatBetween(0.4, 0.8));
            });

            this.physics.add.collider(this.stars, this.platforms);

            this.physics.add.overlap(
              this.player,
              this.stars,
              this.collectStar,
              null,
              this
            );

            this.score = 0;
            this.scoreText = this.add.text(16, 16, `Score: ${this.score}`, {
              fontSize: "32px",
              fill: "#000",
            });
        }
    ```

    #### Vamos a explicarlo un poco:

    A. Se crea un grupo de estrellas. Se crean 12 estrellas en diferentes posiciones en el juego, utilizando el sprite "star" para representarlas.
    Se utiliza el metodo `setXY` para establecer la posicion de cada estrella. Se utiliza el metodo `stepX` para establecer la distancia entre cada estrella.

    ```js
    this.stars = this.physics.add.group({
      key: "star",
      repeat: 11,
      setXY: { x: 12, y: 0, stepX: 70 },
    });
    ```

    B. Se le agrega un rebote de 0.2 a cada estrella. Para ello se recorre el grupo de estrellas y se le asigna un valor aleatorio entre 0.4 y 0.8 a cada una.

    ```js
    this.stars.children.iterate(function (child) {
      child.setBounceY(Phaser.Math.FloatBetween(0.4, 0.8));
    });
    ```

    C. Se agrega la colisión entre las estrellas y las plataformas. Esto hace que las estrellas no puedan atravesar las plataformas.

    ```js
    this.physics.add.collider(this.stars, this.platforms);
    ```

    D. Se agrega la colisión entre el personaje y las estrellas. Esto hace que el personaje pueda recolectar las estrellas.

    ```js
    this.physics.add.overlap(
      this.player,
      this.stars,
      this.collectStar,
      null,
      this
    );
    ```

    E. Se establece el puntaje en 0. Se crea el texto del puntaje. Se lo posiciona en la esquina superior izquierda. Se le da estilo.

    ```js
    this.score = 0;
    this.scoreText = this.add.text(16, 16, `Score: ${this.score}`, {
      fontSize: "32px",
      fill: "#000",
    });
    ```

1.  Vas a agregar un metodo `collectStar` en la clase Game. En el mismo vamos a realizar varias actividades que tienen que ejecutarse cuando el personaje recolecta una estrella.

    ```js
    collectStar(player, star) {
        star.disableBody(true, true);

        this.score += 10;
        this.scoreText.setText(`Score: ${this.score}`);
    }
    ```

    #### Vamos a explicarlo un poco:

    A. Se deshabilita el cuerpo de la estrella. Esto hace que la estrella desaparezca del juego.

    ```js
    star.disableBody(true, true);
    ```

    B. Se suma 10 puntos al puntaje.

    ```js
    this.score += 10;
    ```

    C. Se actualiza el texto del puntaje.

    ```js
    this.scoreText.setText(`Score: ${this.score}`);
    ```

1.  Es hora de visualizar lo que hemos hecho. Para ello, deberas abrir el archivo `index.html` en tu navegador. Para ello, puedes hacerlo de dos formas:

    - Haciendo click derecho sobre el archivo y seleccionando la opcion `Abrir con Live Server`.
    - Haciendo click en el boton `Go Live` que se encuentra en la parte inferior derecha de VSCode.

    Luego de ello, deberas ir a tu navegador o browser favorito y abrir la url `http://localhost:5500/`. Deberas ver algo como esto:

    <img src="https://github.com/fdegiovanni/phaser3-get-started/blob/main/videos/score-system-demo.gif" width="50%" alt="Score system" />

1.  Por favor, realiza un commit con los cambios realizados y sube los cambios a tu repositorio remoto con los siguientes comandos, ejecutalos en la Terminal de VSCode.

    ```bash
    git add .
    git commit -m "commit score"
    git push
    ```

1.  Espera unos 20 segundos y luego actualiza esta página (desde la que estás siguiendo las instrucciones). [GitHub Actions](https://docs.github.com/es/actions) se actualizará automáticamente al siguiente paso.
