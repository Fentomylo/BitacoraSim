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

COMENTARIO ADICIONAL: al inicio, estaba buscando crear una planta sakura infinita, pero al intentar hacerla no me gusto, porque sentia que el mismo concepto que estaba planteando estaba siendo desviado por mi mente sin pensar en los niños al hacer algo mas dificil de entender, por lo que decidi cambiar lo que estaba haciendo al arbol sakura, en vez de solo las flores, igual es bueno mencionarlo y hay hasta una imagen al respecto:

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/c5a1c0dc-599d-4077-a417-23c4051f033f" />

### DESARROLLO DE LA IDEA Y DEL CONCEPTO

Despues de mi fracaso anterior, decidi empezar a buscar lo que se busca transmitir con esta experiencia, algo fantastico y cientifico, por lo que al estar dirigido para niños, decidi hacer una experiencia visual mas simple de lo que era la anterior que hice, pero mas entendible. Por lo que decidi apostar por un paisaje simple bonito donde se vea principalmente el arbol de sakura. Asi como en las siguientes imagenes:

<img width="897" height="1690" alt="image" src="https://github.com/user-attachments/assets/19e54962-a950-4d97-b314-284ce9a34441" />

<img width="1080" height="1350" alt="image" src="https://github.com/user-attachments/assets/a39c453d-0286-462c-a3eb-a505c2b49340" />

Ahora, como tal la idea es mostrar el ciclo de crecimiento de un arbol sakura, incluyendo las estaciones, por lo que el ciclo de esta experiencia empezaria en verano, seguiria con otoño, despues invierno y finalizaria con la primavera, haciendo que las flores de cerezo que han crecido caigan y se los lleve el viento, como tal esa es la idea principal, mostrar un ciclo biologico con una visual simple pero demostrando que aparte de que la naturaleza en si ya es fantastica, tambien esta la intencion de mostrar lo que se puede hacer en un computador.

#### CONCEPTOS DE ESTA UNIDAD Y DONDE SE VAN A APLICAR

Como solo me piden 3 conceptos de los que vimos, decidi no usar levy flight en si, se puede ver muy poco como en el polen pero no es en si Levy Flight.

* Distribución uniforme (cambios): Al principio la idea era generar con esto las flores del arbol sakura, pero despues de verlo mejor con la IA, decidi cambiarlo, pero con esta distribucion uniforme estan hechas las estrellas del cielo, los copos de nieve que caen o el polen que decidi agregar que son esos punticos amarillos que parecen luciernagas.

* Distribución de probabilidad: Con esto decidi hacer las flores de cerezo, que crecieran desde abajo de la copa del arbol hasta arriba, al intentar hacerlo con distribucion uniforme, las flores se estaban generando de una manera que no me gustaba, pero al intentarlo con este, se veia mas natural en el resultado final

* Random Walk: se ve en la caida de las flores de cerezo para que puedan desprenderse asi mas natural.
  
* Ruido Perlin: La use en el viento suave que saca los petalos de la pantalla.


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

Aqui ya habia mejorado lo de las flores, pero esto no estaba pegado al arbol, entonces ahi con la IA lo correginmos













