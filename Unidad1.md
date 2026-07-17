# UNIDAD 1: ALEATORIEDAD
## CLASE VIERNESS 17
### ACTIVIDAD 2
Parece como q esta dibujando un retrato sjajdsa
<img width="1919" height="1004" alt="image" src="https://github.com/user-attachments/assets/c767ac40-faa2-4432-a83b-d0347f188322" />

### ACTIVIDAD 3

- Pues yo diria que la distribucion uniforme le da la misma probabilidad a todo para generarse como por ejemplo en un codigo de barras hay lineas blancas y negras que lo forma, mientras que la no uniforme le da prioridad a una forma o color mas que otras, como digamos el centro de color negro en una gaussiana por ejemplo.

este si se va un poco a la derecha pero mas lento.
 <img width="1919" height="1066" alt="image" src="https://github.com/user-attachments/assets/2df6c8f2-55a7-4119-9833-09335cf21311" />

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
    let choice = floor(random(4));
    if (choice < 0){
      choice=0
    }
      if (choice == 0){
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
}

````



