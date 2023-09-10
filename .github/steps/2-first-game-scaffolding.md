## Step 2: Scaffolding de tu primer juego con Phaser

_¡Creaste tu "Hello World" de Phaser! :tada:_

Ahora, vamos a crear un juego más complejo. Para ello, utilizaremos un concepto llamado _scaffolding_.
El scaffolding es una técnica que permite crear una estructura básica de un proyecto, para luego ir agregando funcionalidades.

En este caso, utilizaremos un proyecto que ya tiene la estructura básica de un juego, y luego iremos agregando funcionalidades. Como todos nos imaginamos, los juegos tienen archivos multimedias ya que son en gran parte audiovisuales.

### ⌨ Actividad: Conociendo el scaffolding

1. Hace un pull del proyecto en tu computadora, mediante la terminal de VSCode.

   ```bash
   git pull
   ```

1. En la carpeta `/docs/` encontraras una carpeta assets con los archivos multimedia que utilizara este ejemplo.

1. En esa carpeta `/docs/` deberas crear los archivos `index.html` y `script.js`.

1. En el archivo HTML, deberas agregar el siguiente codigo:

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <title>Phaser 3 Hello World</title>
       <script src="//cdn.jsdelivr.net/npm/phaser@3.60.0/dist/phaser.js"></script>
     </head>
     <body>
       <canvas id="canvas" width="800" height="600"></canvas>

       <script src="./script.js"></script>
     </body>
   </html>
   ```

   Como puedes observar, el codigo de este html es identico al visto anteriormente.

1. En el archivo JavaScript, comenzaremos a hacer la magia para dar vida al juego.

   ```js
   class Game extends Phaser.Scene {
     constructor() {
       super("Game");
     }

     preload() {
       this.load.image("sky", "./assets/images/sky.png");
       this.load.image("ground", "./assets/images/platform.png");
       this.load.image("star", "./assets/images/star.png");
       this.load.image("bomb", "./assets/images/bomb.png");
       this.load.spritesheet("dude", "./assets/images/dude.png", {
         frameWidth: 32,
         frameHeight: 48,
       });
     }

     create() {
       this.add.image(400, 300, "sky");
       this.add.image(400, 300, "star");
     }
   }

   const config = {
     type: Phaser.AUTO,
     width: 800,
     height: 600,
     physics: {
       default: "arcade",
       arcade: {
         gravity: { y: 200 },
         debug: false,
       },
     },
     scene: Game,
   };

   const game = new Phaser.Game(config);
   ```

   Como puedes observar, el codigo de este JS es similar al visto anteriormente. En este caso tendremos:

   - **Game**: que es una clase que hereda de Scene de Phaser. Ahi mismo lo que tendremos es un fondo y una estrella.
     - _preload_: precarga los recursos en el navegador, en este caso son todos archivos png.
     - _create_: permite visualizar los recursos `sky` y `star`.
   - **config**: es un objeto que permite decirle a Phaser como sera el juego.
   - **game**: es donde se guardará el juego una vez que se contruya mediante `new Phaser.Game(config);`

1. Es hora de visualizar lo que hemos hecho. Para ello, deberas abrir el archivo `index.html` en tu navegador. Para ello, puedes hacerlo de dos formas:

   - Haciendo click derecho sobre el archivo y seleccionando la opcion `Abrir con Live Server`.
   - Haciendo click en el boton `Go Live` que se encuentra en la parte inferior derecha de VSCode.

   Luego de ello, deberas ir a tu navegador o browser favorito y abrir la url `http://localhost:5500/`. Deberas ver algo como esto:
   <img src="https://github.com/fdegiovanni/phaser3-get-started/blob/main/images/scaffolding-demo.png" width="50%" alt="Scaffolding" />

1. Por favor, realiza un commit con los cambios realizados y sube los cambios a tu repositorio remoto con los siguientes comandos, ejecutalos en la Terminal de VSCode.

   ```bash
   git add .
   git commit -m "commit scaffolding"
   git push
   ```

1. Espera unos 20 segundos y luego actualiza esta página (desde la que estás siguiendo las instrucciones). [GitHub Actions](https://docs.github.com/es/actions) se actualizará automáticamente al siguiente paso.
