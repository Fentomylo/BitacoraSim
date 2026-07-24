# UNIDAD 1: ALEATORIEDAD

## ACTIVIDAD 2
Parece como q esta dibujando un retrato sjajdsa
<img width="1919" height="1004" alt="image" src="https://github.com/user-attachments/assets/c767ac40-faa2-4432-a83b-d0347f188322" />

## ACTIVIDAD 3

- Pues yo diria que la distribucion uniforme le da la misma probabilidad a todo para generarse, como por ejemplo en un codigo de barras hay lineas blancas y negras que lo forman, se reparten y generan esa forma, mientras que la no uniforme le da prioridad a una forma o color mas que otras, como digamos el centro de color negro en una gaussiana.

Aqui ps modifique el codigo para q tuviera mas probabibilidad moverse a la derecha q a la izquierda, arriba y abajo.
 <img width="2559" height="1308" alt="image" src="https://github.com/user-attachments/assets/7bdc7538-bbae-4624-926a-9eebe064bd77" />


````js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(0);
    arc(this.x, this.y, 55, 60, 60, HALF_PI, PI);
  }

 step() {
  let choice = floor(random(5));

  if (choice == 0 || choice == 4) {
    this.x++;      
  } else if (choice == 1) {
    this.x--;      
  } else if (choice == 2) {
    this.y++;      
  } else {
    this.y--;      
  }
}

````

## ACTIVIDAD 4

La real la quise representar diferente, hice que que se dibujaran lineas horizontales donde la posicion en x se genera con distribucion normal, por lo que la gran mayoria aparece cerca del centro y poquitas en los lados. Lo que agregue por asi decirlo es que la distribución en Y sea aleatoria para que se repartan por todo el canvas y quedara asi d bonito.


<img width="2559" height="1352" alt="image" src="https://github.com/user-attachments/assets/4650cd8a-8007-4f15-ae5b-4a2208490cfe" />

````js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

function setup() {
  createCanvas(640, 240);
  background(255);
}

function draw() {
  
  let x = randomGaussian(320, 60);
  let y = random(height);

  stroke(4, 100);
  line(x - 8, y, x + 8, y);
}
````

## ACTIVIDAD 5

Decidi coger el ejemplo pasado porque fue el que más me gustó. Ps, de lo que yo entendí del Levy flight es como un manejo de probabilidades. Cada línea es un paso corto, pero a fin de cuentas es la misma linea con el mismo color, solo que varía la altura. Básicamente, el Lévy flight es como agregar un salto grande que ocurre en pocas ocasiones. Originalmente había hecho que algunas líneas fueran más largas, pero en lo visual casi no se notaba. Entonces, para hacerlo más visible, decidi agregarle esos círculos naranjados para que se vea mejor. Es un 99% líneas y un 1% círculos, entonces el Lévy flight no ocurre siempre, sino solo en pocas ocasiones que es donde salen esos circulos.

<img width="2559" height="1354" alt="image" src="https://github.com/user-attachments/assets/477b326b-da8c-4107-97aa-46e9b1a4861d" />

````js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

function setup() {
  createCanvas(640, 240);
  background(255);
}

function draw() {

  let x = randomGaussian(width / 2, 60);
  let y = random(height);

  // Lévy flight:
  if (random(1) < 0.01) {

    x = random(width);

    noStroke();
    fill(255, 140, 0);
    circle(x, y, 20);

  } else {

    stroke(0, 35);
    strokeWeight(2);
    line(x - 8, y, x + 8, y);

  }
}
````

## ACTIVIDAD 6

Ps yo decidi representar el ruido de perlin como un fogon o fogata, ya que el fuego cambia de forma todo el tiempo, pero en un fogon o fogata cuando esta normal los cambios no son bruscos. Con esto hago que la parte de arriba de la llama suba y baje suavemente, haciendolo parecido al fuego real pero ps con la limitación del p5. Trate de verlo como un fogon mas continuo en vez de cambiarrlo de manera aleatoria. y ps tambien le puse el fondo negrillo para que se vea mejor el fueguillo. En el video se ve mejor :3, gracias gpt.

<img width="2559" height="1352" alt="image" src="https://github.com/user-attachments/assets/5a40e65d-66a7-47e8-bc6c-1accec62ae95" />

https://github.com/user-attachments/assets/2e18a129-8b0d-48ba-bc6e-54ab27c45948
````js
let start = 0;

function setup() {
  createCanvas(360, 240);
}

function draw() {
  background(20);

  let xoff = start;

  for (let x = 0; x < width; x += 12) {

    let h = map(noise(xoff), 0, 1, 30, 120);

    noStroke();
    fill(255, 120, 0);

    triangle(
      x, height,
      x + 5, height - h,
      x + 10, height
    );

    xoff += 0.08;
  }

  start += 0.01;
}
````

<img width="640" height="460" alt="image" src="https://github.com/user-attachments/assets/84df4830-2705-4d73-9b84-5ef6a0c63c3b" />

## ACTIVIDAD 7 = FESTIVAL DE CIENCIA Y CREATIVIDAD: CRIATURAS FANTASTICAS

### SOBRE EL FESTIVAL
Basicamente, el concepto de este festival busca juntar algunos conceptos de biologia, con la creatividad de los niños de la ciudad para que puedan crear sus propios seres fantasticos con mas conocimiento del que ya tienen.

en este festival se realizan actividades como:

* Dibujos transformados en realidad, donde los niños crean sus propios seres mezclando biologia y los 4 elementos naturales.
* Experiencias interactivas de la naturaleza, aproximando el cuidado ambiental

Estos festivales estan realizados por Buen Comienzo y su publico principal son niños.

Como tal, este festival de Buen Comienzo tiene varias ediciones sobre temas diversos, por ejemplo el que viene es de un viaje espacial o algo asi, como tal yo decidi usar el de las criaturas fantasticas ya que al mezclar ciencia y creatividad en estos eventos, tambien se le puede mostrar a los niños que esta creatividad puede expandirse mucho mas que a simples dibujos, y que pueden hacerlo mediante la tecnologia. Esto ampliando el Mensaje de que Medellin es una ciudad de desarrollo en latinoamerica.

### CONCEPTO

Al tener claro que este festival busca mezclar conocimientos de Biologia con la creatividad de los niños, no puede ser tan avanzada ya que como tal, estos conocimientos se refieren como a conocer nueva fauna y flora, si son carnivoros, herviboros o viviparos o cualquiera de todos lo que este, por lo que, al ser un festival de ciencia y creatividad, este mismo esta dirigido a un publico infantil, por lo que la experiencia interactiva que voy a diseñar, tiene que estar tambien con estos conocimientos pero que sean basicos y entendibles para que los niños puedan interactuar.

Ps como tal esto es lo mas importante a tener en cuenta:

* La experiencia es en p5
* El publico de esta experiencia son niños
* Informacion simple pero completa para que los niños la pueden entender
* Que la experiencia no sea controlada si no influenciada.

Debido a que en este festival se ha explorado mas la fauna que la flora, la experiencia que voy a diseñar esta mas diseñado para la flora, la idea prinicpal es demostrar que lo fantastico tambien existe en la vida real, por lo que decidi hacer una experiencia interactiva relacionada con los arboles de cerezo japones. Lo mas fantastico de estos arboles es como un ciclo que el tiene, que se basa en florecer y dejar crecer sus cerezos para que en primavera estos mismos caigan, y vuelvan a crecer hasta el año siguiente. 

Basicamente la idea de la experiencia es usar el ciclo biologico del arbol sakura para mostrarle a los niños que la naturaleza en si ya es muy fantastica, y que pueden usar la biologia ya sea en fauna o flora para poder crear sus seres y hacerlos aun mas fantasticos, ese es el concepto de la experiencia interactiva que quiero mostrar.

#### DESCARTADOS:
Al inicio, estaba buscando crear una planta sakura infinita, pero al intentar hacerla no me gusto, porque sentia que el mismo concepto que estaba planteando estaba siendo desviado por mi mente sin pensar en los niños al hacer algo mas dificil de entender, por lo que decidi cambiar lo que estaba haciendo al arbol sakura, en vez de solo las flores, igual es bueno mencionarlo y hay hasta una imagen al respecto:

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/c5a1c0dc-599d-4077-a417-23c4051f033f" />

<img width="1024" height="790" alt="image" src="https://github.com/user-attachments/assets/7a67b67a-31e2-435a-b6cd-09f716ebba4c" />

Principalmente lo unico que descarte fue todo esto, pero igual me sirvio de base para hacer lo demas, visualmente no cambia mucho, sino que llegaba un momento en el que se saturaba y se estallaba el pc.

### DESARROLLO DE LA IDEA Y DEL CONCEPTO

Despues de mi fracaso anterior, decidi empezar a buscar lo que se busca transmitir con esta experiencia, algo fantastico y cientifico, por lo que al estar dirigido para niños, decidi hacer una experiencia visual mas simple de lo que era la anterior que hice, pero mas entendible. Por lo que decidi apostar por un paisaje simple bonito donde se vea principalmente el arbol de sakura. Asi como en las siguientes imagenes:

<img width="897" height="1690" alt="image" src="https://github.com/user-attachments/assets/19e54962-a950-4d97-b314-284ce9a34441" />

<img width="1080" height="1350" alt="image" src="https://github.com/user-attachments/assets/a39c453d-0286-462c-a3eb-a505c2b49340" />

Ahora, como tal la idea es mostrar el ciclo de crecimiento de un arbol sakura, incluyendo las estaciones, por lo que el ciclo de esta experiencia empezaria en verano, seguiria con otoño, despues invierno y finalizaria con la primavera, haciendo que las flores de cerezo que han crecido caigan y se los lleve el viento, como tal esa es la idea principal, mostrar un ciclo biologico con una visual simple pero demostrando que aparte de que la naturaleza en si ya es fantastica, tambien esta la intencion de mostrar lo que se puede hacer en un computador.

#### CONCEPTOS DE ESTA UNIDAD Y DONDE SE VAN A APLICAR

* Levy flight: aunque es solamente visual, se usaron para la aparicion del polen durante la animacion

* Distribución uniforme (cambios): Al principio la idea era generar con esto las flores del arbol sakura, pero despues de verlo mejor con la IA, decidi cambiarlo, pero con esta distribucion uniforme estan hechas las estrellas del cielo, los copos de nieve que caen o el polen que decidi agregar que son esos punticos amarillos que parecen luciernagas.

* Distribución de probabilidad(RandomGaussian): Con esto decidi hacer las flores de cerezo, que crecieran desde abajo de la copa del arbol hasta arriba, al intentar hacerlo con distribucion uniforme, las flores se estaban generando de una manera que no me gustaba, pero al intentarlo con este, se veia mas natural en el resultado final

* Random Walk: se ve en la caida de las flores de cerezo para que puedan desprenderse asi mas natural.
  
* Ruido Perlin: La use en el movimiento del viento suave que saca los petalos de la pantalla y en el polen.


#### ¿COMO INFLUYE EL USUARIO SIN CONTROLAR NI ALTERAR LA EXPERIENCIA?

Decidi irme por algo simple, el usuario al interactuar hace que el ciclo biologico y el cambio de estaciones pase mas rapido, y que cuando caigan las flores de cerezo, este las pueda como medio desplazar cuando estan moviendose con el viento suave.

En cuanto a la experiencia, esta es continua y cuando caen los cerezos, esta misma experiencia vuelve a empezar para que crezcan otra vez estas flores y alguien mas la pueda disfrutar.

## DESARROLLO DE LA EXPERIENCIA

Cabe aclarar, que todo codigo hecho para esta experiencia fue hecho con la tecnologia de vanguardia conocida como I A, ya que no soy experto en programar.

<img width="335" height="597" alt="image" src="https://github.com/user-attachments/assets/baf2c335-4879-4a04-af46-112b73f8f481" />

BUENO AHORA SI, este es el INDEX y el STYLE que use en todas las pruebas al desarrollar la experiencia

### INDEX

````js
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>El Sakura Fantástico - Festival Buen Comienzo</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main id="canvas-container"></main>
  <script src="sketch.js"></script>
</body>
</html>
````

### STYLE

````css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #050308;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  font-family: sans-serif;
}

#canvas-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

canvas {
  display: block;
  box-shadow: 0 0 50px rgba(255, 100, 180, 0.2);
}
````

### PRIMERAS PRUEBAS DE LA EXPERIENCIA

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/133149a4-2fba-4175-93d3-712560fea7b4" />

Primero quise ver como me generaba las flores, aunque aqui se veia re feo la verdad, aqui intente usar la distribucion uniforme con la ia pero me solto algo diferente, y ahi fue cuando hablando llegamos a la conclusion de mejorar eso con la distribucion de probabilidad, como tal, esto fue pura construcion brick by brick, pero para ser el primer propmtazo, tiro algo bastante bueno para empezar.

<img width="1024" height="574" alt="image" src="https://github.com/user-attachments/assets/40e36044-501f-4da6-9d30-b5357ef64763" />

Aqui ya habia mejorado lo de las flores, pero esto no estaba pegado al arbol, entonces ahi con la IA lo correginmos, aparte aca las flores no crecian sino que estaban estaticas, error que logramos cambiar.

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/1f22bef3-0fdc-4f85-837c-c84b78458526" />

Ya aqui con la generacion de las flores mas funcional, decidi probar la caida de los cerezos, y ya aqui con los random walk se logro algo mas funcional, entonces ya a partir de aqui, fue mejorar la caida y generacion de los cerezos, aparte de la interfaz visual.

### SFGUNDAS PRUEBAS DE LA EXPERIENCIA

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/05972c72-291c-4387-9ca1-238e83060657" />

ya aqui mejore lo visual, agregue las estrellas con la distribucion normal, y ya cogio mas forma como tal el proyecto.

<img width="1538" height="1196" alt="image" src="https://github.com/user-attachments/assets/d9d8e9d9-d51b-4575-a73b-1fc754b5ba41" />

Aqui tambien, ya la generacion de los cerezos estaba quedando mas como yo queria, pero faltaba pulirla.

<img width="1186" height="946" alt="image" src="https://github.com/user-attachments/assets/d05e7d81-28f3-490d-bc9b-93144f1dff3a" />

Aqui ya fue cogiendo mas forma, por lo que se podria decir que ya estaba en una base bastante buena para seguir avanzando


### TERCERAS PRUEBAS DE LA EXPERIENCIA

<img width="1024" height="570" alt="image" src="https://github.com/user-attachments/assets/8fd59912-019c-4ea6-8244-86ed69dcc1d2" />

Aqui, ya implemente lo de las estaciones, aunque no se cambiaban y el crecimiento de los cerezos no estaba sincronizado.

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/4655a436-6f2c-4cbc-8402-c08e019e04df" />

Aqui ya mejore la parte visual, del todo y ya todas las flores empezaron a crecer bien, ya los cambios de estaciones estaban funcionando bien, y a partir de aqui ya empezo a funcionar mas bien la distribucion de probabilidad, con el randomgaussian y todo eso

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/b4f14c08-74a0-4f8e-8635-3b9fdf3be9ef" />

Por ultimo, agregue el dragon, pero ahi como tal ya estaba funcionando casi perfectamente como yo queria, ya lo unico que faltaba corregir era ponerlo en 9:16 y mejorar la apariencia visual, eso fue que le meti un promptazo a claude y ya con todo lo demas, me soluciono la pariencia visual y me pulio lo que tenia, la verdad me sorprendio bastante claude, porque de un prompt la version final me quedo como era que yo lo queria.

## EXPERIENCIA FINAL

https://github.com/user-attachments/assets/d1b787f4-9ed6-4d18-80a2-6ed85ee59dff

<img width="645" height="1122" alt="image" src="https://github.com/user-attachments/assets/a0762e70-c067-4498-9417-2cbde7dbadc2" />

Esta es la experiencia interactiva que yo propongo, mostrar un proceso interactivo con biologia y fantasia para promover el conocimietno de que la naturaleza en si, ya es fantastica

### LINK AL P5

 [EXPERIENCIARDAPOLIS](https://editor.p5js.org/Tomygga/sketches/_ScS_H3_V)

### CODIGO FINAL

````js
/**
 * EL BONSÁI SAKURA - CICLO ESTACIONAL: VERANO -> OTOÑO -> INVIERNO -> PRIMAVERA
 * Festival Buen Comienzo - Medellín
 * Versión con apariencia visual mejorada y optimizada para rendimiento
 */

let floresCopa = [];
let polenAmbiental = [];
let estrellasFondo = [];
let luciernagas = [];
let coposNieve = [];
let nubesCielo = [];
let elementosSuelo = [];
let brizasPasto = [];
let zOff = 0;

let progresoAnual = 0.0;

// ==========================================================================
// MOTOR PROBABILÍSTICO DE CRECIMIENTO (Posibilidad -> Tendencia -> Influencia)
// ==========================================================================
// derivaLateral acumula, brote a brote, una pequeña preferencia direccional.
// Empieza en 0 al reiniciar el ciclo (todas las direcciones son igual de
// posibles) y se refuerza levemente con cada flor nueva: un sesgo pequeño y
// repetido termina construyendo una dirección clara para toda la copa
// (proceso de refuerzo tipo urna de Pólya / caminata con deriva).
// El visitante puede empujar este mismo valor con su posición horizontal:
// no aplica una fuerza cualquiera, desplaza la media de la distribución que
// decide hacia dónde crece el árbol.
let derivaLateral = 0.0;

// Contador de seguridad: garantiza que el ciclo SIEMPRE reinicie, aunque queden
// pétalos rezagados cayendo muy despacio o fuera del rango calculado.
let esperaReinicio = 0;
const MAX_ESPERA_REINICIO = 480; // ~8 segundos a 60fps como tope máximo

// Variables para el Dragón Easter Egg estilo oriental
let dragon = null;
let temporizadorDragon = 0;

// Límite de flores según rendimiento (evita que la animación se vuelva pesada)
const MAX_FLORES = 700;

function setup() {
  let h = windowHeight;
  let w = h * (9 / 16);
  if (w > windowWidth) {
    w = windowWidth;
    h = w * (16 / 9);
  }

  createCanvas(w, h);
  pixelDensity(1); // clave para rendimiento: evita renderizar a resolución retina x2/x3

  for (let i = 0; i < 60; i++) {
    estrellasFondo.push({
      x: random(width),
      y: random(height * 0.55),
      tam: random(1, 2.6),
      brillo: random(100, 255),
      fase: random(TWO_PI)
    });
  }

  for (let i = 0; i < 14; i++) {
    luciernagas.push({
      x: random(width),
      y: random(height * 0.35, height * 0.7),
      fase: random(TWO_PI),
      vel: random(0.2, 0.5)
    });
  }

  for (let i = 0; i < 80; i++) {
    coposNieve.push({
      x: random(width),
      y: random(height),
      velY: random(1.2, 2.6),
      tam: random(2, 4.5)
    });
  }

  // Nubes estéticas para el cielo (múltiples capas para profundidad)
  for (let i = 0; i < 7; i++) {
    nubesCielo.push({
      x: random(width),
      y: random(height * 0.04, height * 0.38),
      vel: random(0.15, 0.55),
      tam: random(55, 140),
      capa: random(1) < 0.5 ? 0 : 1
    });
  }

  // Arbustos y piedras decorativas para el suelo
  for (let i = 0; i < 16; i++) {
    elementosSuelo.push({
      x: random(width * 0.1, width * 0.9),
      y: height * 0.75 + random(6, 40),
      tipo: random(['piedra', 'arbusto']),
      tam: random(12, 30)
    });
  }

  // Briznas de pasto decorativas (bajo costo, dan textura al suelo)
  for (let i = 0; i < 40; i++) {
    brizasPasto.push({
      x: random(width * 0.05, width * 0.95),
      y: height * 0.75 + random(15, 55) + random(0, height * 0.2),
      alto: random(6, 14),
      inclinacion: random(-0.3, 0.3)
    });
  }

  reiniciarArbolBase();
  temporizadorDragon = int(random(220, 420));
}

function reiniciarArbolBase() {
  floresCopa = [];
  polenAmbiental = [];

  // POSIBILIDAD: cada nuevo ciclo arranca sin preferencia direccional alguna.
  // Todas las direcciones de crecimiento vuelven a ser igual de probables.
  derivaLateral = 0.0;

  let centroX = width / 2;
  let baseSueloY = height * 0.75;

  // Más puntos de brote = copa más frondosa y natural
  let raicesRamas = [
    createVector(centroX, baseSueloY - height * 0.22),
    createVector(centroX - width * 0.04, baseSueloY - height * 0.27),
    createVector(centroX + width * 0.04, baseSueloY - height * 0.27),
    createVector(centroX - width * 0.10, baseSueloY - height * 0.32),
    createVector(centroX + width * 0.10, baseSueloY - height * 0.32),
    createVector(centroX - width * 0.16, baseSueloY - height * 0.25),
    createVector(centroX + width * 0.16, baseSueloY - height * 0.25),
    createVector(centroX - width * 0.22, baseSueloY - height * 0.22),
    createVector(centroX + width * 0.22, baseSueloY - height * 0.22),
    createVector(centroX - width * 0.12, baseSueloY - height * 0.38),
    createVector(centroX + width * 0.12, baseSueloY - height * 0.38),
    createVector(centroX, baseSueloY - height * 0.30)
  ];

  for (let pos of raicesRamas) {
    floresCopa.push(new FlorBonsai(pos.x, pos.y, true));
  }
}

function draw() {
  let cursorEnCanvas = (mouseX >= 0 && mouseX <= width && mouseY >= 0 && mouseY <= height);

  let factorVelocidad = 0.0002;

  // EXCEPCIÓN (Lévy flight): probabilidad base, siempre activa, de que un
  // grano de polen dé un salto largo de cola pesada — el sistema sigue
  // generando excepciones aunque nadie interactúe.
  let probabilidadSaltoLevy = 0.006;

  if (cursorEnCanvas) {
    let distAlCentro = dist(mouseX, mouseY, width / 2, height * 0.60);
    if (distAlCentro < 350) {
      factorVelocidad = map(distAlCentro, 350, 0, 0.0008, 0.0030);
    } else {
      factorVelocidad = 0.0004;
    }

    // INFLUENCIA: el visitante no solo empuja pétalos con una fuerza — su
    // posición horizontal desplaza la MEDIA de la distribución que decide
    // hacia dónde crece la copa (cambia una regla del sistema).
    let sesgoRaton = constrain((mouseX - width / 2) / (width / 2), -1, 1);
    derivaLateral = constrain(derivaLateral + sesgoRaton * 0.0022, -1, 1);

    // INFLUENCIA: acercarse al árbol también sube la probabilidad de que
    // ocurra un evento improbable (salto Lévy) — la presencia del visitante
    // transforma lo que puede llegar a pasar, no solo lo que se ve.
    probabilidadSaltoLevy = map(constrain(distAlCentro, 0, 420), 0, 420, 0.032, 0.008);

    if (pmouseX !== mouseX || pmouseY !== mouseY) {
      if (random(1) < 0.25 && polenAmbiental.length < 45) {
        polenAmbiental.push(new Polen(mouseX + random(-15, 15), mouseY + random(-15, 15)));
      }
    }
  }

  progresoAnual += factorVelocidad;

  if (progresoAnual >= 1.0) {
    progresoAnual = 1.0;
    esperaReinicio++;

    // El ciclo reinicia en cuanto ya no quedan flores cayendo (se limpian en
    // gestionarEstacionesYCaida), o como máximo tras MAX_ESPERA_REINICIO frames
    // de seguridad, para que la experiencia NUNCA se quede trabada en primavera.
    if (floresCopa.length === 0 || esperaReinicio > MAX_ESPERA_REINICIO) {
      progresoAnual = 0.0;
      esperaReinicio = 0;
      reiniciarArbolBase();
    }
  } else {
    esperaReinicio = 0;
  }

  dibujarFondoEstacional(progresoAnual);
  dibujarNubesEstacionales(progresoAnual);
  dibujarMonteFujiRealista(progresoAnual);
  dibujarNieblaLejana(progresoAnual);

  // Gestión del Dragón Oriental
  if (dragon == null) {
    temporizadorDragon--;
    if (temporizadorDragon <= 0) {
      let vaDeIzquierda = random(1) > 0.5;
      let startX = vaDeIzquierda ? -200 : width + 200;
      let startY = random(height * 0.15, height * 0.5);
      let dir = vaDeIzquierda ? 1 : -1;
      dragon = new DragonOriental(startX, startY, dir);

      // EXCEPCIÓN: la propia aparición del dragón es un evento de baja
      // probabilidad (temporizador largo e irregular). Al ocurrir, revela
      // territorio nuevo del lienzo esparciendo polen en zonas donde el
      // sistema casi nunca llega por sí solo.
      if (polenAmbiental.length < 60) {
        for (let i = 0; i < 10; i++) {
          polenAmbiental.push(new Polen(random(width), random(height * 0.12, height * 0.62)));
        }
      }
    }
  } else {
    dragon.actualizar();
    dragon.mostrar();
    if (dragon.fueraDePantalla()) {
      dragon = null;
      temporizadorDragon = int(random(260, 560));
    }
  }

  dibujarSueloEstacional(progresoAnual);
  dibujarColinaYArbol(progresoAnual);

  let aliento = createVector(mouseX, mouseY);
  if (cursorEnCanvas) {
    dibujarAuraInfluencia(aliento);
  }

  gestionarEstacionesYCaida(progresoAnual, aliento, cursorEnCanvas, factorVelocidad);

  for (let i = polenAmbiental.length - 1; i >= 0; i--) {
    let p = polenAmbiental[i];
    p.actualizar(probabilidadSaltoLevy);
    p.mostrar();
    if (p.vida <= 0) polenAmbiental.splice(i, 1);
  }

  if (frameCount % 14 === 0 && polenAmbiental.length < 35) {
    polenAmbiental.push(new Polen(random(width), random(height * 0.6)));
  }

  dibujarVineta();

  zOff += 0.002;
}

// ==========================================
// FONDO: Cielos mejorados y degradados artísticos
// ==========================================
function dibujarFondoEstacional(prog) {
  let cTop, cMid, cBottom;

  if (prog < 0.25) {
    let t = map(prog, 0, 0.25, 0, 1);
    cTop = lerpColor(color(20, 95, 180), color(40, 130, 215), t);
    cMid = lerpColor(color(90, 165, 225), color(140, 195, 240), t);
    cBottom = lerpColor(color(180, 225, 250), color(215, 240, 255), t);
  } else if (prog < 0.50) {
    let t = map(prog, 0.25, 0.50, 0, 1);
    cTop = lerpColor(color(150, 55, 55), color(90, 28, 58), t);
    cMid = lerpColor(color(225, 120, 70), color(180, 80, 65), t);
    cBottom = lerpColor(color(255, 185, 95), color(230, 130, 75), t);
  } else if (prog < 0.75) {
    let t = map(prog, 0.50, 0.75, 0, 1);
    cTop = lerpColor(color(6, 12, 28), color(3, 6, 16), t);
    cMid = lerpColor(color(18, 30, 55), color(10, 18, 35), t);
    cBottom = lerpColor(color(35, 55, 85), color(20, 35, 58), t);
  } else {
    let t = map(prog, 0.75, 1.0, 0, 1);
    cTop = lerpColor(color(70, 45, 85), color(48, 32, 65), t);
    cMid = lerpColor(color(190, 130, 175), color(160, 110, 175), t);
    cBottom = lerpColor(color(255, 210, 225), color(215, 175, 215), t);
  }

  noFill();
  for (let y = 0; y <= height; y += 6) {
    let inter = map(y, 0, height, 0, 1);
    let c;
    if (inter < 0.5) {
      c = lerpColor(cTop, cMid, map(inter, 0, 0.5, 0, 1));
    } else {
      c = lerpColor(cMid, cBottom, map(inter, 0.5, 1, 0, 1));
    }
    stroke(c);
    strokeWeight(6.5);
    line(0, y, width, y);
  }

  // Sol / luna con halo suave
  noStroke();
  if (prog < 0.25) {
    let sx = width * 0.78, sy = height * 0.18;
    for (let r = 130; r > 0; r -= 25) {
      fill(255, 245, 190, 10);
      ellipse(sx, sy, r * 2);
    }
    fill(255, 250, 225, 235);
    ellipse(sx, sy, 92, 92);
  } else if (prog < 0.50) {
    let sx = width * 0.72, sy = height * 0.22;
    for (let r = 150; r > 0; r -= 25) {
      fill(255, 170, 110, 12);
      ellipse(sx, sy, r * 2);
    }
    fill(255, 205, 140, 245);
    ellipse(sx, sy, 100, 100);
  } else if (prog >= 0.50 && prog < 0.75) {
    let sx = width * 0.75, sy = height * 0.16;
    for (let r = 90; r > 0; r -= 20) {
      fill(220, 225, 255, 14);
      ellipse(sx, sy, r * 2);
    }
    fill(235, 240, 255, 240);
    ellipse(sx, sy, 62, 62);
    fill(200, 210, 240, 130);
    ellipse(sx - 14, sy - 6, 16, 16);
    ellipse(sx + 10, sy + 12, 10, 10);
  } else {
    let sx = width * 0.76, sy = height * 0.2;
    for (let r = 120; r > 0; r -= 24) {
      fill(255, 210, 230, 11);
      ellipse(sx, sy, r * 2);
    }
    fill(255, 235, 240, 235);
    ellipse(sx, sy, 88, 88);
  }

  if (prog >= 0.50) {
    noStroke();
    for (let est of estrellasFondo) {
      let alphaParpadeo = est.brillo + sin(frameCount * 0.04 + est.fase) * 60;
      let a = constrain(alphaParpadeo, 0, 255);
      fill(255, 255, 235, a);
      let tam = est.tam + (a / 255) * 0.8;
      ellipse(est.x, est.y, tam, tam);
    }
    // luciérnagas suaves cerca de la copa en la noche de invierno
    if (prog >= 0.50 && prog < 0.75) {
      for (let l of luciernagas) {
        let ly = l.y + sin(frameCount * 0.02 + l.fase) * 18;
        let lx = l.x + cos(frameCount * 0.015 + l.fase) * 14;
        let a = 90 + sin(frameCount * 0.08 + l.fase) * 90;
        fill(255, 245, 170, max(0, a));
        ellipse(lx, ly, 3.2, 3.2);
      }
    }
  }
}

// ==========================================
// NIEBLA LEJANA (profundidad atmosférica, bajo costo)
// ==========================================
function dibujarNieblaLejana(prog) {
  noStroke();
  let baseSueloY = height * 0.75;
  let colNiebla = (prog >= 0.50 && prog < 0.75) ? color(210, 222, 245) : color(235, 235, 225);
  for (let i = 0; i < 3; i++) {
    let yPos = baseSueloY - height * (0.02 + i * 0.035);
    let alpha = 26 - i * 6;
    fill(red(colNiebla), green(colNiebla), blue(colNiebla), alpha);
    ellipse(width * 0.5, yPos, width * (1.1 - i * 0.15), 40 - i * 8);
  }
}

// ==========================================
// NUBES ESTACIONALES
// ==========================================
function dibujarNubesEstacionales(prog) {
  if (prog < 0.50) {
    noStroke();
    let colNubeBase = (prog < 0.25) ? color(255, 255, 255) : color(255, 195, 160);

    for (let n of nubesCielo) {
      n.x += n.vel * (n.capa === 0 ? 1 : 0.6);
      if (n.x > width + 150) n.x = -150;

      let op = n.capa === 0 ? 165 : 95;
      let tamAj = n.capa === 0 ? n.tam : n.tam * 0.75;
      fill(red(colNubeBase), green(colNubeBase), blue(colNubeBase), op);

      ellipse(n.x, n.y, tamAj, tamAj * 0.48);
      ellipse(n.x - tamAj * 0.32, n.y + 5, tamAj * 0.6, tamAj * 0.38);
      ellipse(n.x + tamAj * 0.32, n.y + 5, tamAj * 0.68, tamAj * 0.4);
      ellipse(n.x, n.y - tamAj * 0.16, tamAj * 0.55, tamAj * 0.32);
    }
  }
}

// ==========================================
// MONTE FUJI REALISTA (con más profundidad y textura)
// ==========================================
function dibujarMonteFujiRealista(prog) {
  push();
  let centroX = width / 2;
  let baseSueloY = height * 0.75;

  noStroke();

  let colorFujiBase = color(80, 92, 112);
  let colorFujiSombra = color(52, 63, 84);
  let colorFujiLuz = color(115, 125, 145);

  if (prog >= 0.25 && prog < 0.50) {
    colorFujiBase = color(150, 95, 78);
    colorFujiSombra = color(102, 55, 50);
    colorFujiLuz = color(190, 130, 100);
  } else if (prog >= 0.50 && prog < 0.75) {
    colorFujiBase = color(48, 58, 80);
    colorFujiSombra = color(24, 32, 48);
    colorFujiLuz = color(70, 82, 108);
  } else if (prog >= 0.75) {
    colorFujiBase = color(120, 100, 130);
    colorFujiSombra = color(78, 62, 92);
    colorFujiLuz = color(160, 135, 165);
  }

  // --- Puntos clave compartidos (evita huecos: todas las capas usan los MISMOS bordes) ---
  let apiceY = baseSueloY - height * 0.44;
  let izqBaseX = centroX - width * 0.52;
  let derBaseX = centroX + width * 0.52;

  // Cordillera secundaria de fondo, más tenue (profundidad) — no toca el Fuji, no genera huecos
  fill(red(colorFujiBase) * 0.8 + 40, green(colorFujiBase) * 0.8 + 40, blue(colorFujiBase) * 0.85 + 40, 140);
  beginShape();
  vertex(0, baseSueloY + 4);
  bezierVertex(width * 0.15, baseSueloY - height * 0.10, width * 0.30, baseSueloY - height * 0.16, width * 0.42, baseSueloY - height * 0.09);
  bezierVertex(width * 0.55, baseSueloY - height * 0.03, width * 0.7, baseSueloY - height * 0.14, width, baseSueloY - height * 0.02);
  vertex(width, baseSueloY + 4);
  endShape(CLOSE);

  // Silueta COMPLETA de base (capa de "seguridad" ligeramente más grande para que nunca se vea el cielo detrás)
  fill(colorFujiSombra);
  beginShape();
  vertex(izqBaseX - 3, baseSueloY + 4);
  bezierVertex(centroX - width * 0.28, baseSueloY - height * 0.28, centroX - width * 0.14, baseSueloY - height * 0.42, centroX, apiceY - 3);
  bezierVertex(centroX + width * 0.14, baseSueloY - height * 0.42, centroX + width * 0.28, baseSueloY - height * 0.28, derBaseX + 3, baseSueloY + 4);
  endShape(CLOSE);

  // Cara iluminada del Fuji (lado izquierdo), exactamente sobre la silueta de seguridad
  fill(colorFujiLuz);
  beginShape();
  vertex(izqBaseX, baseSueloY + 2);
  bezierVertex(centroX - width * 0.28, baseSueloY - height * 0.28, centroX - width * 0.14, baseSueloY - height * 0.42, centroX, apiceY);
  vertex(centroX, baseSueloY + 2);
  endShape(CLOSE);

  // Lado en sombra (derecha), comparte el mismo borde exterior que la silueta de seguridad
  fill(colorFujiSombra);
  beginShape();
  vertex(centroX, apiceY);
  bezierVertex(centroX + width * 0.14, baseSueloY - height * 0.42, centroX + width * 0.28, baseSueloY - height * 0.28, derBaseX, baseSueloY + 2);
  vertex(centroX, baseSueloY + 2);
  endShape(CLOSE);

  // Sombreado central para dar volumen (triángulo simple, sin curvas que se crucen)
  fill(colorFujiBase);
  beginShape();
  vertex(centroX - width * 0.06, baseSueloY - height * 0.36);
  vertex(centroX + width * 0.10, baseSueloY - height * 0.32);
  vertex(centroX + width * 0.40, baseSueloY + 2);
  vertex(centroX - width * 0.02, baseSueloY + 2);
  endShape(CLOSE);

  // Textura de estrías / surcos en la ladera
  stroke(red(colorFujiSombra), green(colorFujiSombra), blue(colorFujiSombra), 90);
  strokeWeight(1.4);
  for (let i = 1; i <= 4; i++) {
    let t = i / 5;
    let x1 = lerp(centroX, derBaseX, t);
    let y1 = lerp(apiceY, baseSueloY, t);
    line(x1, y1, x1 - width * 0.02, y1 + height * 0.02);
  }
  noStroke();

  // ---- Casquete de nieve: zigzag simple con vértices rectos (NUNCA se cruza a sí mismo) ----
  let alphaNieve = (prog >= 0.50 && prog < 0.75) ? 255 : 225;
  fill(250, 250, 255, alphaNieve);
  beginShape();
  vertex(centroX - width * 0.135, apiceY + height * 0.095); // punta inferior izquierda
  vertex(centroX - width * 0.095, apiceY + height * 0.05);  // pequeño diente rocoso
  vertex(centroX - width * 0.055, apiceY + height * 0.065);
  vertex(centroX - width * 0.025, apiceY + height * 0.02);
  vertex(centroX, apiceY);                                   // pico
  vertex(centroX + width * 0.022, apiceY + height * 0.018);
  vertex(centroX + width * 0.05, apiceY + height * 0.06);
  vertex(centroX + width * 0.085, apiceY + height * 0.045);
  vertex(centroX + width * 0.125, apiceY + height * 0.088); // punta inferior derecha
  vertex(centroX + width * 0.06, apiceY + height * 0.06);   // vuelve por debajo, dentro del cuerpo de nieve
  vertex(centroX, apiceY + height * 0.03);
  vertex(centroX - width * 0.065, apiceY + height * 0.06);
  endShape(CLOSE);

  // Sombra suave de la nieve (lado derecho) para dar volumen — triángulo simple, sin cruces
  fill(205, 210, 230, alphaNieve * 0.7);
  beginShape();
  vertex(centroX, apiceY + height * 0.005);
  vertex(centroX + width * 0.05, apiceY + height * 0.058);
  vertex(centroX + width * 0.018, apiceY + height * 0.05);
  endShape(CLOSE);

  pop();
}

// ==========================================
// SUELO Y ELEMENTOS
// ==========================================
function dibujarSueloEstacional(prog) {
  let centroX = width / 2;
  let baseSueloY = height * 0.75;

  push();
  noStroke();

  let esInvierno = (prog >= 0.50 && prog < 0.75);

  if (esInvierno) {
    fill(238, 244, 255);
    beginShape();
    vertex(0, height);
    vertex(0, baseSueloY + height * 0.03);
    bezierVertex(width * 0.2, baseSueloY - height * 0.08, width * 0.8, baseSueloY - height * 0.08, width, baseSueloY + height * 0.03);
    vertex(width, height);
    endShape(CLOSE);

    fill(210, 224, 244);
    beginShape();
    vertex(0, height);
    vertex(0, baseSueloY + height * 0.1);
    bezierVertex(width * 0.25, baseSueloY, width * 0.75, baseSueloY, width, baseSueloY + height * 0.1);
    vertex(width, height);
    endShape(CLOSE);

    fill(245, 250, 255);
    arc(centroX, baseSueloY, width * 0.48, 38, PI, TWO_PI);

    fill(255, 255, 255, 235);
    for (let c of coposNieve) {
      c.y += c.velY;
      c.x += sin(frameCount * 0.03 + c.y) * 0.6;
      if (c.y > height) { c.y = 0; c.x = random(width); }
      ellipse(c.x, c.y, c.tam, c.tam);
    }
  } else {
    let colPastoClaro = color(58, 100, 65);
    let colPastoOscuro = color(30, 58, 38);

    if (prog >= 0.25 && prog < 0.50) {
      colPastoClaro = color(140, 110, 55);
      colPastoOscuro = color(95, 68, 35);
    } else if (prog >= 0.75) {
      colPastoClaro = color(95, 150, 90);
      colPastoOscuro = color(55, 95, 58);
    }

    fill(colPastoClaro);
    beginShape();
    vertex(0, height);
    vertex(0, baseSueloY + height * 0.03);
    bezierVertex(width * 0.2, baseSueloY - height * 0.08, width * 0.8, baseSueloY - height * 0.08, width, baseSueloY + height * 0.03);
    vertex(width, height);
    endShape(CLOSE);

    fill(colPastoOscuro);
    beginShape();
    vertex(0, height);
    vertex(0, baseSueloY + height * 0.1);
    bezierVertex(width * 0.25, baseSueloY, width * 0.75, baseSueloY, width, baseSueloY + height * 0.1);
    vertex(width, height);
    endShape(CLOSE);

    fill(red(colPastoClaro) + 25, green(colPastoClaro) + 25, blue(colPastoClaro) + 10, 150);
    arc(centroX, baseSueloY, width * 0.45, 35, PI, TWO_PI);

    // Briznas de pasto sutiles
    stroke(red(colPastoOscuro) + 15, green(colPastoOscuro) + 25, blue(colPastoOscuro) + 10, 150);
    strokeWeight(1.6);
    for (let b of brizasPasto) {
      if (b.y > baseSueloY - 4) {
        line(b.x, b.y, b.x + b.inclinacion * b.alto, b.y - b.alto);
      }
    }
    noStroke();
  }

  for (let el of elementosSuelo) {
    if (el.tipo === 'piedra') {
      let colPiedraBase = esInvierno ? color(200, 212, 228) : color(96, 104, 112);
      let colPiedraSombra = esInvierno ? color(165, 180, 200) : color(65, 72, 80);
      fill(colPiedraSombra);
      arc(el.x, el.y + 1, el.tam * 1.4, el.tam, PI, TWO_PI);
      fill(colPiedraBase);
      arc(el.x - el.tam * 0.08, el.y, el.tam * 1.2, el.tam * 0.85, PI, TWO_PI);
    } else {
      let colArbustoBase = esInvierno ? color(228, 238, 248) : color(46, 88, 56);
      let colArbustoSombra = esInvierno ? color(200, 215, 232) : color(28, 58, 38);
      fill(colArbustoSombra);
      ellipse(el.x, el.y - el.tam * 0.25, el.tam * 1.05, el.tam * 0.95);
      fill(colArbustoBase);
      ellipse(el.x - el.tam * 0.3, el.y - el.tam * 0.15, el.tam * 0.7, el.tam * 0.7);
      ellipse(el.x + el.tam * 0.3, el.y - el.tam * 0.15, el.tam * 0.7, el.tam * 0.7);
      ellipse(el.x, el.y - el.tam * 0.45, el.tam * 0.6, el.tam * 0.6);
    }
  }

  pop();
}

// ==========================================
// CLASE DRÁGON ORIENTAL
// ==========================================
class DragonOriental {
  constructor(x, y, direccion) {
    this.pos = createVector(x, y);
    this.dir = direccion;
    this.velocidad = createVector(this.dir * random(2.0, 3.0), random(-0.5, 0.5));
    this.historial = [];
    this.longitudCuerpo = 60;
  }

  actualizar() {
    this.pos.add(this.velocidad);
    this.pos.y += sin(frameCount * 0.06) * 1.0;

    this.historial.unshift(this.pos.copy());
    if (this.historial.length > this.longitudCuerpo) {
      this.historial.pop();
    }
  }

  mostrar() {
    push();
    noStroke();

    for (let i = 0; i < this.historial.length; i++) {
      let pt = this.historial[i];
      let factorTam = sin((i / this.longitudCuerpo) * PI) * 19 + 8;
      let alphaVal = map(i, 0, this.historial.length, 255, 35);

      fill(230, 60, 90, alphaVal);
      ellipse(pt.x, pt.y, factorTam * 1.3, factorTam);
      fill(255, 130, 150, alphaVal * 0.5);
      ellipse(pt.x - factorTam * 0.15, pt.y - factorTam * 0.15, factorTam * 0.55, factorTam * 0.4);

      if (i % 3 === 0) {
        fill(255, 210, 80, alphaVal);
        ellipse(pt.x, pt.y - factorTam * 0.7, 7, 10);
      }
    }

    if (this.historial.length > 0) {
      let cabeza = this.historial[0];
      fill(190, 30, 50, 255);
      ellipse(cabeza.x, cabeza.y, 36, 26);
      fill(230, 70, 90, 200);
      ellipse(cabeza.x - this.dir * 4, cabeza.y - 3, 20, 14);

      fill(255, 205, 0, 250);
      triangle(cabeza.x, cabeza.y - 10, cabeza.x - (this.dir * 20), cabeza.y - 32, cabeza.x - (this.dir * 6), cabeza.y - 14);

      fill(255, 255, 150);
      ellipse(cabeza.x + (this.dir * 6), cabeza.y - 4, 7, 7);
      fill(20, 20, 20);
      ellipse(cabeza.x + (this.dir * 7), cabeza.y - 4, 3, 3);
    }

    pop();
  }

  fueraDePantalla() {
    return (this.dir > 0 && this.pos.x > width + 300) || (this.dir < 0 && this.pos.x < -300);
  }
}

// ==========================================
// TRONCO Y RAMAS DEL BONSÁI (más orgánico y con textura)
// ==========================================
function dibujarColinaYArbol(prog) {
  let centroX = width / 2;
  let baseSueloY = height * 0.75;

  push();

  // Montículo de tierra bajo el tronco
  fill(30, 14, 20);
  beginShape();
  vertex(centroX - width * 0.055, baseSueloY + 9);
  bezierVertex(centroX - width * 0.075, baseSueloY - height * 0.02, centroX - width * 0.03, baseSueloY - height * 0.05, centroX, baseSueloY - height * 0.04);
  bezierVertex(centroX + width * 0.03, baseSueloY - height * 0.05, centroX + width * 0.075, baseSueloY - height * 0.02, centroX + width * 0.055, baseSueloY + 9);
  endShape(CLOSE);

  let esInvierno = (prog >= 0.50 && prog < 0.75);
  let colMusgoClaro = esInvierno ? color(225, 235, 248) : color(58, 105, 66);
  let colMusgoOscuro = esInvierno ? color(200, 215, 235) : color(40, 80, 48);

  fill(colMusgoClaro);
  ellipse(centroX - width * 0.038, baseSueloY + 5, width * 0.055, 15);
  ellipse(centroX + width * 0.038, baseSueloY + 5, width * 0.055, 15);
  fill(colMusgoOscuro);
  arc(centroX, baseSueloY + 6, width * 0.13, 19, 0, PI);

  // ---- TRONCO: capas para dar volumen y textura de corteza ----
  noFill();
  stroke(20, 9, 13);
  strokeWeight(max(27, width * 0.023));
  strokeCap(ROUND);
  beginShape();
  vertex(centroX, baseSueloY - height * 0.03);
  bezierVertex(centroX - width * 0.04, baseSueloY - height * 0.09, centroX + width * 0.05, baseSueloY - height * 0.15, centroX - width * 0.01, baseSueloY - height * 0.22);
  endShape();

  stroke(48, 24, 32);
  strokeWeight(max(19, width * 0.017));
  beginShape();
  vertex(centroX, baseSueloY - height * 0.03);
  bezierVertex(centroX - width * 0.035, baseSueloY - height * 0.09, centroX + width * 0.045, baseSueloY - height * 0.15, centroX - width * 0.01, baseSueloY - height * 0.21);
  endShape();

  // Luz lateral sutil en el tronco (da volumen cilíndrico)
  stroke(90, 48, 55, 130);
  strokeWeight(max(6, width * 0.005));
  beginShape();
  vertex(centroX + width * 0.006, baseSueloY - height * 0.04);
  bezierVertex(centroX - width * 0.03, baseSueloY - height * 0.095, centroX + width * 0.04, baseSueloY - height * 0.145, centroX - width * 0.005, baseSueloY - height * 0.205);
  endShape();

  // Textura de corteza: pequeñas líneas de veta
  stroke(15, 6, 9, 160);
  strokeWeight(1.4);
  strokeCap(SQUARE);
  for (let i = 0; i < 6; i++) {
    let t = i / 6;
    let tx = lerp(centroX, centroX - width * 0.01, t) + sin(t * 8) * 4;
    let ty = lerp(baseSueloY - height * 0.04, baseSueloY - height * 0.21, t);
    line(tx - 6, ty, tx + 6, ty + 3);
  }
  strokeCap(ROUND);

  // ---- RAMAS PRINCIPALES ----
  stroke(35, 15, 22);
  strokeWeight(max(11, width * 0.0095));

  beginShape();
  vertex(centroX - width * 0.01, baseSueloY - height * 0.16);
  bezierVertex(centroX - width * 0.10, baseSueloY - height * 0.24, centroX - width * 0.22, baseSueloY - height * 0.26, centroX - width * 0.28, baseSueloY - height * 0.23);
  endShape();

  beginShape();
  vertex(centroX, baseSueloY - height * 0.16);
  bezierVertex(centroX + width * 0.10, baseSueloY - height * 0.24, centroX + width * 0.22, baseSueloY - height * 0.26, centroX + width * 0.28, baseSueloY - height * 0.23);
  endShape();

  // Ramas secundarias
  strokeWeight(max(7.5, width * 0.0065));
  beginShape();
  vertex(centroX - width * 0.01, baseSueloY - height * 0.21);
  bezierVertex(centroX - width * 0.05, baseSueloY - height * 0.31, centroX - width * 0.10, baseSueloY - height * 0.36, centroX - width * 0.12, baseSueloY - height * 0.38);
  endShape();

  beginShape();
  vertex(centroX - width * 0.01, baseSueloY - height * 0.21);
  bezierVertex(centroX + width * 0.05, baseSueloY - height * 0.31, centroX + width * 0.10, baseSueloY - height * 0.36, centroX + width * 0.12, baseSueloY - height * 0.38);
  endShape();

  // Ramas terciarias finas (dan más frondosidad a la copa)
  strokeWeight(max(4.5, width * 0.004));
  beginShape();
  vertex(centroX - width * 0.15, baseSueloY - height * 0.245);
  bezierVertex(centroX - width * 0.19, baseSueloY - height * 0.28, centroX - width * 0.20, baseSueloY - height * 0.31, centroX - width * 0.22, baseSueloY - height * 0.325);
  endShape();

  beginShape();
  vertex(centroX + width * 0.15, baseSueloY - height * 0.245);
  bezierVertex(centroX + width * 0.19, baseSueloY - height * 0.28, centroX + width * 0.20, baseSueloY - height * 0.31, centroX + width * 0.22, baseSueloY - height * 0.325);
  endShape();

  beginShape();
  vertex(centroX - width * 0.003, baseSueloY - height * 0.26);
  bezierVertex(centroX - width * 0.01, baseSueloY - height * 0.30, centroX + width * 0.005, baseSueloY - height * 0.335, centroX, baseSueloY - height * 0.36);
  endShape();

  pop();
}

// ==========================================
// CRECIMIENTO Y GESTIÓN DE ESTACIONES
// ==========================================
function gestionarEstacionesYCaida(prog, aliento, cursorEnCanvas, velGlobal) {
  if (prog < 0.75) {
    if (floresCopa.length < MAX_FLORES) {
      let cantidadAGenerar = (velGlobal > 0.0006) ? 3 : 2;

      for (let k = 0; k < cantidadAGenerar; k++) {
        let floresMaduras = floresCopa.filter(f => f.escalaActual >= 0.4 && !f.cayendo);
        if (floresMaduras.length > 0) {
          let florMadre = random(floresMaduras);

          // NORMALIDAD (distribución normal): la mayoría de los brotes nace
          // cerca de una dirección y distancia "habituales" — no uniformemente
          // en cualquier parte, sino agrupados alrededor de una media, como
          // una campana de Gauss.
          // TENDENCIA: esa media (mediaAngular) no es fija: está desplazada
          // por derivaLateral, el sesgo que la propia copa fue acumulando
          // brote a brote a lo largo del ciclo.
          let mediaAngular = -HALF_PI + derivaLateral * 1.15;
          let anguloBrote = mediaAngular + randomGaussian(0, 0.8);
          let distanciaBrote = constrain(randomGaussian(25, 7), 10, 42);

          let nuevoX = florMadre.pos.x + cos(anguloBrote) * distanciaBrote;
          let nuevoY = florMadre.pos.y + sin(anguloBrote) * distanciaBrote;

          let baseY = height * 0.75;
          if (nuevoY > baseY - height * 0.62 && nuevoY < baseY - height * 0.18) {
            let muyCerca = false;
            for (let fExistente of floresCopa) {
              if (dist(nuevoX, nuevoY, fExistente.pos.x, fExistente.pos.y) < 14) {
                muyCerca = true;
                break;
              }
            }

            if (!muyCerca) {
              floresCopa.push(new FlorBonsai(nuevoX, nuevoY, false));

              // TENDENCIA: cada brote logrado refuerza levemente el sesgo en
              // su propia dirección — una pequeña preferencia repetida va
              // construyendo, brote a brote, una dirección de crecimiento
              // reconocible para toda la copa.
              derivaLateral = constrain(derivaLateral + cos(anguloBrote) * 0.0035, -1, 1);
            }
          }
        }
      }
    }
  }

  let cayendoActivo = (prog >= 0.75);

  // Recorremos hacia atrás para poder eliminar del arreglo con splice() de forma segura
  for (let i = floresCopa.length - 1; i >= 0; i--) {
    let f = floresCopa[i];

    if (cayendoActivo) {
      f.comenzarCaida();
    }

    if (cursorEnCanvas) {
      f.sensarCursor(aliento);
    }

    f.actualizar(cayendoActivo, velGlobal);

    // Una vez que la flor ya cayó fuera de la pantalla, la quitamos del arreglo:
    // esto libera memoria/dibujo y es lo que permite que el ciclo detecte que
    // "ya no queda nada cayendo" y pueda reiniciar a verano.
    if (cayendoActivo && f.pos.y > height + 40) {
      floresCopa.splice(i, 1);
      continue;
    }

    f.mostrar();
  }
}

// ==========================================
// CLASE FLOR BONSAI (pétalos con forma e iluminación mejorada)
// ==========================================
class FlorBonsai {
  constructor(x, y, esSemilla) {
    this.pos = createVector(x, y);
    this.tamFinal = random(11, 15);
    this.escalaActual = esSemilla ? 1.0 : 0.0;
    this.velocidadCrecimiento = random(0.5, 1.2);

    this.cayendo = false;
    this.velCaida = createVector(random(0.3, 0.9), random(0.2, 0.6));
    this.rotacion = random(TWO_PI);
    this.velRotacion = random(-0.02, 0.02);
    this.resaltado = 0;
    this.tonoVariante = random(-14, 14); // pequeña variación de color entre flores
  }

  comenzarCaida() {
    this.cayendo = true;
  }

  sensarCursor(aliento) {
    let d = p5.Vector.dist(this.pos, aliento);
    if (d < 120) {
      if (this.cayendo) {
        this.velCaida.x += 0.15;
        this.velCaida.y = max(0.2, this.velCaida.y - 0.05);
        let empuje = p5.Vector.sub(this.pos, aliento).mult(0.08);
        this.pos.add(empuje);
      } else {
        this.resaltado = map(d, 120, 0, 0, 1);
      }
    } else {
      this.resaltado = lerp(this.resaltado, 0, 0.1);
    }
  }

  actualizar(estaCayendo, velGlobal) {
    if (!estaCayendo) {
      if (this.escalaActual < 1.0) {
        let tasaCrecimiento = map(velGlobal, 0.0002, 0.0035, 0.015, 0.12);
        this.escalaActual += tasaCrecimiento * this.velocidadCrecimiento;
        if (this.escalaActual > 1.0) this.escalaActual = 1.0;
      }
    } else {
      let ruidoviento = noise(this.pos.x * 0.003, this.pos.y * 0.003, zOff);
      let vientoSuave = createVector(0.4 + ruidoviento * 0.5, 0.2 + ruidoviento * 0.2);

      // Gravedad progresiva y suave: la flor va acelerando su caída poco a poco,
      // como en la realidad, y así se garantiza que SIEMPRE termine de caer
      // (en vez de quedar flotando casi inmóvil por tiempo indefinido).
      this.velCaida.y = min(this.velCaida.y + 0.012, 3.5);

      this.pos.add(this.velCaida);
      this.pos.add(vientoSuave);
      this.rotacion += this.velRotacion;
    }
  }

  mostrar() {
    push();
    translate(this.pos.x, this.pos.y);

    let escalaDibujo = this.cayendo ? 1.0 : this.escalaActual;
    escalaDibujo += this.resaltado * 0.35;

    scale(escalaDibujo);
    rotate(this.rotacion);
    noStroke();

    // Sombra suave debajo de la flor (da algo de profundidad)
    fill(180, 60, 110, 30);
    ellipse(1.5, 1.5, this.tamFinal * 1.15, this.tamFinal * 1.15);

    for (let i = 0; i < 5; i++) {
      push();
      rotate((TWO_PI / 5) * i);
      let colorPetalo = lerpColor(
        color(255, 185 + this.tonoVariante * 0.3, 213, 235),
        color(255, 125, 178, 255),
        this.resaltado
      );
      fill(colorPetalo);
      // pétalo con muesca (forma más parecida a flor de cerezo)
      beginShape();
      vertex(0, 0);
      bezierVertex(-this.tamFinal * 0.32, -this.tamFinal * 0.25, -this.tamFinal * 0.28, -this.tamFinal * 0.7, 0, -this.tamFinal * 0.62);
      bezierVertex(this.tamFinal * 0.12, -this.tamFinal * 0.72, this.tamFinal * 0.05, -this.tamFinal * 0.78, 0, -this.tamFinal * 0.85);
      bezierVertex(-this.tamFinal * 0.05, -this.tamFinal * 0.78, -this.tamFinal * 0.12, -this.tamFinal * 0.72, 0, -this.tamFinal * 0.62);
      bezierVertex(this.tamFinal * 0.28, -this.tamFinal * 0.7, this.tamFinal * 0.32, -this.tamFinal * 0.25, 0, 0);
      endShape(CLOSE);

      // brillo tenue en la punta del pétalo
      fill(255, 255, 255, 55);
      ellipse(0, -this.tamFinal * 0.55, this.tamFinal * 0.18, this.tamFinal * 0.3);
      pop();
    }

    fill(255, 225, 100);
    ellipse(0, 0, this.tamFinal * 0.32, this.tamFinal * 0.32);
    fill(255, 250, 200, 200);
    ellipse(-this.tamFinal * 0.05, -this.tamFinal * 0.05, this.tamFinal * 0.14, this.tamFinal * 0.14);

    pop();
  }
}

// ==========================================
// CLASE POLEN AMBIENTAL
// Caminata aleatoria guiada por ruido Perlin (dirección) donde el TAMAÑO del
// paso combina dos regímenes de probabilidad:
//   · NORMALIDAD: casi siempre un paso corto, sorteado de una distribución
//     normal — la trayectoria se mantiene cerca de lo habitual.
//   · EXCEPCIÓN (Lévy flight): con baja probabilidad, un paso de una
//     distribución de cola pesada (power-law) que dispara al grano de polen
//     muy lejos, dejándolo aparecer en un territorio del lienzo que casi
//     nunca se visita.
// ==========================================
class Polen {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vida = random(200, 300);
    this.saltando = false;
  }

  actualizar(probabilidadSalto) {
    let angulo = noise(this.pos.x * 0.003, this.pos.y * 0.003, zOff) * TWO_PI * 2;

    // NORMALIDAD: paso pequeño y gaussiano (valor absoluto para que sea
    // siempre una magnitud, no un desplazamiento negativo).
    let paso = abs(randomGaussian(2.1, 1.0));
    this.saltando = false;

    // EXCEPCIÓN: distribución de cola pesada tipo Lévy — la mayoría de los
    // sorteos de "u" caen cerca de 1 (paso corto), pero muy ocasionalmente
    // "u" es diminuto y 1/u^(1/alpha) dispara el paso a un valor enorme.
    if (random(1) < probabilidadSalto) {
      let u = random(0.015, 1);
      paso = min(9 / pow(u, 1 / 1.5), 170);
      this.saltando = true;
    }

    let empuje = p5.Vector.fromAngle(angulo).mult(paso * 0.42);
    this.pos.add(empuje);
    this.vida--;
  }

  mostrar() {
    noStroke();
    if (this.saltando) {
      // Estela breve que delata el salto largo — ayuda a leer la excepción
      // como un evento, no como un parpadeo aleatorio del render.
      fill(255, 245, 200, this.vida * 0.35);
      ellipse(this.pos.x, this.pos.y, 12, 12);
    }
    fill(255, 255, 130, this.vida * 0.8);
    ellipse(this.pos.x, this.pos.y, 4.5);
    fill(255, 255, 200, this.vida * 0.4);
    ellipse(this.pos.x, this.pos.y, 7.5);
  }
}

// ==========================================
// AURA DE INFLUENCIA DEL USUARIO
// ==========================================
function dibujarAuraInfluencia(pos) {
  noStroke();
  for (let r = 110; r > 0; r -= 30) {
    fill(255, 130, 195, 5);
    ellipse(pos.x, pos.y, r * 2);
  }
}

// ==========================================
// VIÑETA CINEMATOGRÁFICA (marco suave, bajo costo)
// ==========================================
function dibujarVineta() {
  noFill();
  for (let i = 0; i < 5; i++) {
    stroke(5, 5, 10, 10 + i * 3);
    strokeWeight(width * 0.06);
    rect(width * 0.03 * i, height * 0.03 * i, width - width * 0.06 * i, height - height * 0.06 * i, 30);
  }
  noStroke();
}

function windowResized() {
  let h = windowHeight;
  let w = h * (9 / 16);
  if (w > windowWidth) {
    w = windowWidth;
    h = w * (16 / 9);
  }
  resizeCanvas(w, h);
}
````

## AUTOEVALUACION

* Encargo completo: interpreto los cinco momentos dentro de un mismo sistema visual.	☐	si	
* Simulación con intención: utilizo al menos tres conceptos de la unidad para comunicar las ideas del encargo.	☐	si
* Interacción significativa: la interacción modifica el comportamiento o las probabilidades del sistema, que también funciona sin intervención.	☐	si
* Prototipo funcional: la experiencia puede ejecutarse y recorrerse completa sin errores que impidan comprenderla.	☐	si
* Proceso documentado: la bitácora evidencia avances, decisiones, dificultades, soluciones, uso de IA y enlace al prototipo.	☐	si

Ps digo yo que si, ya si no ps mala mia ahi NOTA: 5

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/7d9d54a8-3727-457c-b887-99577ce21f98" />






























