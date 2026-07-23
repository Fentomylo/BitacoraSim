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




