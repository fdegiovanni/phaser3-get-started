<header>

# Phaser: Primeros pasos

_Comenza a usar Phaser en menos de 2 horas_

</header>

## Step 1: Hello World

_¡Bienvenido al curso: "Phaser: Primeros pasos"! :wave:_

Si estas acá es por que quieres incursionar en los videojuegos HTML5. No te voy a entretener. Puedes comenzar con la actividad...

### ⌨ Actividad: Tu "Hola mundo" de Phaser

1. Clona este repositorio en tu computadora.
1. Abri el proyecto en Visual Studio Code.
1. En la carpeta `/docs/hello-world` encontraras dos archivos vacios: un html y un js.

   a. **Editando el HTML5**
   En este archivo agregaremos la estructura de la web para soportar el juego.

   Para ello agregaremos:

   - tag head:
     - con el titulo de la pestaña del navegador
     - con la llamada CDN a Phaser
   - tag body:
     - con la creacion de un canvas donde se dibujara el juego
     - con laa llamada al script que creara el juego

   Solo debes copiar las siguientes lineas de codigo, pegarlas en el archivo `index.html` y guardar los cambios.

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

   b. **Editando el JS**
   En este archivo agregaremos la logica mediante el formato que propone el framework Phaser para crear nuestro primer "juego".

   Para ello agregaremos:

   - **Escena**: las escenas son el corazon de todo juego, en ella se incorporan todos los objetos que se visualizaran y a su vez tendra el conocimiento para hacerlo y para hacer el refresh en cada frame.
     - En este caso es un clase llamada `HelloWorld` que hereda toda su funcionalidad desde `Scene` de Phaser. Ahi mismo lo que tendremos es un fondo y un logo de Phaser que rebotara con los bordes del mundo/escena. 📀 _DVD_
     - Sobreescribimos las funciones _preload_ y _create_
       - preload: precarga los recursos en el navegador (imagenes, videos, sonidos, etc)
       - create: permite visualizar los recursos, ademas de establecer los comporamientos que seguiran los objetos creados.
   - **config**: es un objeto que permite decirle a Phaser como sera el juego. Existen muchos datos que se pueden setear.
   - **game**: es donde se guardará el juego una vez que se contruya mediante `new Phaser.Game(config);`

   Solo debes copiar las siguientes lineas de codigo, pegarlas en el archivo `script.js` y guardar los cambios.

   ```js
   class HelloWorld extends Phaser.Scene {
     constructor() {
       super("HelloWorld");
     }

     preload() {
       this.load.image("sky", "./assets/space3.png");
       this.load.image("logo", "./assets/logo.png");
     }

     create() {
       this.add.image(400, 300, "sky");

       this.logo = this.physics.add.image(400, 100, "logo");

       this.logo.body.setVelocity(100, 200);
       this.logo.body.setBounce(1, 1);
       this.logo.body.setCollideWorldBounds(true);
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
     scene: HelloWorld,
   };

   const game = new Phaser.Game(config);
   ```

1. Teniendo abierto el archivo `index.html` haz clic derecho y selecciona 'Open with Live Server' en el menu contextual.
   <img src="../../images/go-live-menu.png" width="50%" alt="Go Live" />

   Otra forma es hacer clic en el botón Go Live que aparece en la barra inferior del VSCode (siempre teniendo activo el archivo HTML mencionado).
   <img src="../../images/go-live.png" width="50%" alt="Go Live Button" />

1. En tu navegador favorito navega a la URL `http://localhost:5500/` y veras el juego corriendo (verifica que el puerto sea el mismo que el que te indica el plugin Live Server). :tada:
   <img src="../../videos/demo-hello-world.gif" width="50%" alt="Hello World" />

1. Por favor, realiza un commit con los cambios realizados y sube los cambios a tu repositorio remoto con los siguientes comandos, ejecutalos en la Terminal de VSCode.

   ```bash
   git add .
   git commit -m "commit hello world"
   git push
   ```

1. Espera unos 20 segundos y luego actualiza esta página (desde la que estás siguiendo las instrucciones). [GitHub Actions](https://docs.github.com/es/actions) se actualizará automáticamente al siguiente paso.

<footer>

---

Get help: [TBD-support](TBD-support-link) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 [fdegiovanni](https://github.com/fdegiovanni) &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
