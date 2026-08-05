# UNIDAD 2: MOVIMIENTO

# RETO DE DISEÑO

Quiero explorar la tensión entre competir y colaborar para sobrevivir (EN ESTE CASO, SERA CON POKEMONES)

Yo espero que esa tensión se vea en que ninguna forma gana siempre. Hay veces donde competir sirve para avanzar pero tambien lo deja a uno mas expuesto. Mientas que cooperar o protegerse funciona mejor cuando hay apoyo de los otros, pero si se separa el grupo, se vuelven vulnerables. La idea es q el sistema este cambiando a toda hora y nunca haya una especie o una estrategia que domine siempre.

<img width="1472" height="1104" alt="image" src="https://github.com/user-attachments/assets/aa23d642-2b02-4f3d-8267-8972a25c500c" />

Esta contradicción  esta incorporada en las reglas del sistema, ya que cada pokemon tiene una estrategia diferente para sobrevivir. Charmander (termino siendo bulbasaur) compite y persigue, Squirtle (este si salio bien) se protege formando grupos y Bulbasaur (actua como charmander) coopera para fortalecerse. Como cada estrategia tiene ventajas y desventajas, ninguna logra dominar para siempre y la tension aparece por la forma en que interactuan entre si.

## Diseño del sistema
### Tipos de particulas 

Seleccione Fuego (charmander), Agua(squirtle), Planta(bulbasaur) y Eevee porque quiero mostrar diferentes formas de enfrentar la misma situación. Donde espero que produzca comportamientos distintos que cambien según el contexto.

### Cantidad de particulas

Seleccione 48 de cada una de los principales y 26 de Eevee porque quiero que estas tengan el mismo peso y que Eevee solo influya un poco. donde Espero que ninguna estrategia domine desde el inicio. (SPOILER, NO PASO XD)

### Matriz de atraccion, repulsion o indiferencia

Hice relacion donde cada especie domina a otra porque quiero mostrar que ninguna es mejor que las demas. donde quiero  que el equilibrio cambie constantemente. (ESTO DEPENDE MUCHO DE LA SUERTE, PORQ A VECES FUNCIONA ASI Y A VECES NO)

Pero basicamente Existe un ciclo de dominancia donde Charmander vence a Bulbasaur, Bulbasaur vence a Squirtle y Squirtle vence a Charmander. Esto evita que una estrategia domine para siempre.

### Intensidad y alcance de cada relacion

Le puse fuerzas y rangos diferentes para cada especie porque quiero que cada una tenga una forma propia de actuar. Dondee quiero que sus comportamientos sean faciles de distinguir. (ESTA SI SIRVIO, PERO AL FINAL HUBO UN INTERCAMBIO DE ROLES ENTRE LOS BULBASAUR Y LOS CHARMANDER)

### Distancias de interaccion

Puse diferentes radios de interaccion porque quiero que unos pokemones necesiten estar juntas y otras prefieran mantener distancia. Los cuales si funcionaron

### Friccion y velocidad maxima

Aqui Seleccione una friccion alta y velocidades parecidas porque quiero que el movimiento sea fluido sin que un pokemon tenga demasiada ventaja. de las cuales a veces funciona y a veces no pero modificando los valores con los controladores hay cambios bastante interesantes.

### Distribucion inicial

La puse random porque era mas divertido, viva el gambling. Aunque ya mas serio, quiero que cada simulacion empiece diferente y sus conflictos sean por asi decirlo emergentes.

### Parametros constantes y variables

Quise dejar fijas las reglas principales y que se puedan cambiar parametros como velocidad, poblacion y fuerzas porque quiero mantener la identidad del sistema sin que todas las simulaciones sean iguales.

### Apariencia e interaccion

Quise que tuviera un diseño parecido a los pokemones, pero dios no se parecen mucho, aunque si se distinguen por sus colores clave, Mientras que la interaccion quise permitir agregar recursos con un clic, porque quiero que sea facil entender que hace cada uno de los pokemones y como reaccionan.

### INVARIANTES 

Siempre existen los mismos pokemones, el ciclo de dominancia, la evolucion y la tension entre competir, protegerse y cooperar.

### VARIABLES

Cambian las posiciones iniciales, la semilla, los recursos creados por el usuario y los parametros del panel.

## CONDICIONES

### Posicion, velocidad y aceleracion:

Cada particula tiene posicion, velocidad y aceleracion que cambian en cada frame segun las fuerzas que recibe.

### Varias poblaciones de particulas:

El sistema tiene cuatro poblaciones: Charmanders, Squirtles, Bulbasaurs y Eevees, cada una con un comportamiento diferente.

### Interacciones dependientes de la distancia:

Todas las relaciones dependen de la distancia entre las particulas, usando diferentes radios de interaccion.

### Relaciones de atraccion, repulsion o indiferencia:

Las particulas pueden atraerse, rechazarse o no reaccionar entre si dependiendo de los pokemones y la situacion.

### Al menos una relacion asimetrica:

Existe un ciclo de dominancia donde cada especie de pokemon puede vencer a una y al mismo tiempo ser vencida por otra.

### Variabilidad entre ejecuciones:

Cada simulacion empieza con posiciones aleatorias y puede cambiar por la semilla, los recursos y los parametros del panel

### Comportamientos emergentes, no trayectorias predefinidas:

Los grupos, persecuciones y evoluciones aparecen por las reglas del sistema, no porque esten programados de antemano.

### Una identidad reconocible entre sus diferentes resultados:

Aunque cada ejecucion es diferente, siempre se mantiene la idea de competencia, cooperacion y proteccion entre los pokemones

### LO DE LAS MATRICES Y PARAMETROS

Tengo una matriz de dominancia por los tipos

<img width="592" height="186" alt="image" src="https://github.com/user-attachments/assets/4c3bade7-cf93-447b-8434-2d3c8d866fce" />

TAmbien tengo el ciclo inverso

<img width="591" height="187" alt="image" src="https://github.com/user-attachments/assets/add1198d-401b-4332-b26a-e8d08802d08e" />

Se pueden atraer entre ellas, repulsar y simplemente pasar indiferentes

#### BASE FUEGO (CHARMANDER)
* coopGain: fuerza con la que busca acercarse a otras Plantas.
* coopRange: distancia máxima para cooperar.
* coopThreshold: cantidad mínima de compañeros para considerar que existe cooperación.
* fearBasePlanta: miedo cuando está aislada.
* fearDilution: cuánto disminuye ese miedo al aumentar el tamaño del grupo.

#### BASE AGUA (SQUIRTLE)
* shieldGain: fuerza con la que se agrupan para formar un escudo.
* shieldRange: distancia para mantener la formación.
* shieldThreshold: número mínimo de compañeros para activar la defensa.
* shieldRepelGain: fuerza con la que el grupo repele al depredador.
* loneFearGain: intensidad con la que huye cuando está sola.

#### BASE PLANTA (BULBASAUR)
* coopGain: fuerza con la que busca acercarse a otras Plantas.
* coopRange: distancia máxima para cooperar.
* coopThreshold: cantidad mínima de compañeros para considerar que existe cooperación.
* fearBasePlanta: miedo cuando está aislada.
* fearDilution: cuánto disminuye ese miedo al aumentar el tamaño del grupo.


## PROCESO DE DESARROLLO

Esto fue todo con IA, xq las mates son re dificiles

Ps no fue tan dificil, en cuanto a hallazgos y descartes no tuve, poruqe las mecanicas me las tiro al inicio como queria, solo fue cuadrarlas en lo que me demore bastante tiempo.

En el codigo aparecen fuego, agua y planta. Esos son charmander, bulbasaur y squirtle

Esta fue la Primera version

<img width="1283" height="1138" alt="image" src="https://github.com/user-attachments/assets/b35b292d-5c1f-4f20-bafa-6973696efeb6" />

Ya aqui fue donde cuadre una version mas establem donde ya los pokemones no se juntaban entre si, aunque si se quedaban estaticos

<img width="1024" height="575" alt="image" src="https://github.com/user-attachments/assets/b5951214-3550-48b5-8eaf-9f40e0ea0c1d" />

Aqui ya pude cuadrar el funcionamiento como se llegaria a ver mas en la version final

<img width="1050" height="719" alt="image" src="https://github.com/user-attachments/assets/ee268410-7c96-42c7-ab92-5bcc7339f8fa" />

Aqui ya fui cambiando mas la parte visual

<img width="1217" height="720" alt="image" src="https://github.com/user-attachments/assets/9928b122-cbfa-4180-8fd8-9a97ddc78883" />

Estos fueron los primeros diseños de los "pokemones"

<img width="1498" height="1183" alt="image" src="https://github.com/user-attachments/assets/95864d1b-9c26-42fa-89b1-c80279a3d5f0" />

Y a partir de aqui, fui buscando un balanceo para que se pudiera ver bien para la version final

<img width="1139" height="1115" alt="image" src="https://github.com/user-attachments/assets/2baaaadc-c92f-4e9c-be10-64deb8239e02" />

Podria poner mas fotos, pero son literalmente lo mismo, asi que no hay como una version q se vea mas diferente

## RESULTADO FINAL

Al final, el bulbasaur en la gran mayoria de casos q probe hacia el trabajo del charmander, y viceversa. Pero en unos intentos que fueron pocos si cumplio como yo lo habia visto, asi que este es el resultado final, con todo balanceado lo mejor que pudimos la IA y yo, y sobre todo, haberle agregado una partesita donde se puede modificar variables, pero no las reglas.

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/bb8bfa08-a565-47d2-9f1d-aba39d781a44" />

Otra version

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/0a846a29-1ccd-4f78-8592-b0793e35eda2" />

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/9c4c1ee4-e1bb-4c2c-a00a-269e3a798ba1" />

### LINK AL PROYECTO
[LINK AL P5](https://editor.p5js.org/Tomygga/sketches/ITTIoegT1)


### FINAL CODIGO
```js

/* ============================================================
   SISTEMA GENERATIVO: "Competir, Cooperar, Proteger"
   Versión balanceada + panel de controles.

   Cambios de balance respecto a la versión "sin controles":
     - Velocidades más parejas entre especies (antes Agua era
       casi la mitad de rápida que Fuego, ahora la diferencia es
       leve).
     - El recurso disputado (clic) ya no es exclusivo de Fuego:
       las tres especies principales lo persiguen y ganan el
       mismo impulso de éxito al capturarlo.
     - Umbrales de cooperación (Planta) y de escudo (Agua)
       igualados, y rangos sociales llevados a magnitudes
       comparables entre las tres especies.
     - Todo lo demás vuelve a ser ajustable en vivo desde el
       panel de controles: fricción, velocidad, radio de
       interacción, repulsión de contacto y la matriz de
       dominancia (quién le gana a quién).
   ============================================================ */

const FUEGO = 0, AGUA = 1, PLANTA = 2, EEVEE = 3;
const SPECIES_NAMES = ['Charmander', 'Squirtle', 'Bulbasaur', 'Eevee'];
const STAGE_NAMES = [
  ['Charmander', 'Charmeleon', 'Charizard'],
  ['Squirtle', 'Wartortle', 'Blastoise'],
  ['Bulbasaur', 'Ivysaur', 'Venusaur'],
  ['Eevee', 'Eevee', 'Eevee']
];
const COLORS_HSB = [ [16, 85, 95], [205, 80, 95], [108, 60, 85], [32, 35, 78] ];

// ---------- Población (ajustable desde el panel) ----------
let countFuego = 48, countAgua = 48, countPlanta = 48, countEevee = 26;

const STAGE_SIZE_MULT = [1, 1.32, 1.7];
const STAGE_FORCE_MULT = [1, 1.18, 1.4];
const EVOLVE_RESET = 0.5;

// ---------- Parámetros ajustables (todos editables desde el panel) ----------
// Valores por defecto ya balanceados entre las tres especies.
let P = {
  // Física general
  friction: 0.90,
  maxSpeed: 2.6,
  rMax: 140,
  contactMin: 26,
  contactPush: 2.2,

  // Fuego (competir / cazar)
  pursueGain: 0.85,
  captureRange: 55,
  fleeGainFuego: 0.5,
  fleeRangeFuego: 75,
  rivalryGain: 0.14,
  rivalryRange: 55,

  // Agua (proteger / escudo)
  shieldGain: 0.60,
  shieldRange: 80,
  shieldThreshold: 5,
  shieldRepelGain: 0.11,
  loneFearGain: 0.5,

  // Planta (cooperar / grupo)
  coopGain: 0.55,
  coopRange: 90,
  fearBasePlanta: 0.6,
  fearDilution: 0.16,
  coopThreshold: 5,

  // Evolución (uniforme para las 3 especies principales)
  successRate: 0.010,
  decayRate: 0.014,

  // Recurso disputado (ahora compartido por Fuego/Agua/Planta)
  resourceGain: 1.0,
  resourceRange: 200,
  resourceBoost: 0.12,

  // Eevee (sin estrategia)
  eeveeRepelGain: 0.6,
  eeveeRepelRange: 80,
  eeveeSpacingGain: 0.18,
  eeveeSpacingRange: 38,
  wanderGain: 0.16,

  unrestGain: 0.045
};

const SPEED_MULT = { }; // se recalcula en updateSpeedMults()
function updateSpeedMults() {
  // Diferencias leves y coherentes con el "carácter" de cada especie,
  // ninguna domina claramente a las otras en movilidad.
  SPEED_MULT[FUEGO] = 1.00;
  SPEED_MULT[AGUA] = 0.92;
  SPEED_MULT[PLANTA] = 0.96;
  SPEED_MULT[EEVEE] = 1.08;
}
updateSpeedMults();

// Ciclo de dominancia: 1 = Fuego>Planta, Agua>Fuego, Planta>Agua (sentido original)
// -1 = invierte el ciclo: Fuego>Agua, Planta>Fuego, Agua>Planta
let dominanceCycle = 1;
let DOMINANCE = [[0,0,0],[0,0,0],[0,0,0]];
function recomputeDominanceMatrix() {
  DOMINANCE = [[0,0,0],[0,0,0],[0,0,0]];
  if (dominanceCycle === 1) {
    DOMINANCE[FUEGO][PLANTA] = 1;
    DOMINANCE[AGUA][FUEGO] = 1;
    DOMINANCE[PLANTA][AGUA] = 1;
  } else {
    DOMINANCE[FUEGO][AGUA] = 1;
    DOMINANCE[PLANTA][FUEGO] = 1;
    DOMINANCE[AGUA][PLANTA] = 1;
  }
}
recomputeDominanceMatrix();

function updateDominanceAssignments() {
  for (let p of particles) {
    if (p.species < 3) {
      p.dominadorIdx = DOMINANCE.findIndex((_, i) => DOMINANCE[i][p.species] === 1);
      p.dominadoIdx = DOMINANCE[p.species].findIndex(v => v === 1);
    }
  }
}

const RESOURCE_LIFE = 260;
let resources = [];

let particles = [];
let estrellasFondo = null;
let nebulosas = null;
let uiDiv;
let panelOpen = true;

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 1);
  document.body.style.margin = '0';
  document.body.style.overflow = 'hidden';
  document.body.style.background = '#03050a';

  uiDiv = createDiv('');
  uiDiv.style('position', 'fixed');
  uiDiv.style('top', '10px');
  uiDiv.style('left', '10px');
  uiDiv.style('color', '#e4ece9');
  uiDiv.style('font-family', 'monospace');
  uiDiv.style('font-size', '12px');
  uiDiv.style('line-height', '1.5');
  uiDiv.style('background', 'rgba(8,12,14,0.55)');
  uiDiv.style('backdrop-filter', 'blur(4px)');
  uiDiv.style('padding', '10px 14px');
  uiDiv.style('border-radius', '10px');
  uiDiv.style('border', '1px solid rgba(255,255,255,0.06)');
  uiDiv.style('pointer-events', 'none');
  uiDiv.style('max-width', '340px');

  buildControlPanel();
  rebuildParticles(floor(random(999999)));
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  estrellasFondo = null;
  nebulosas = null;
}

function mousePressed() {
  // Ignora clics hechos dentro del panel de controles
  if (mouseTarget && mouseTarget.closest && mouseTarget.closest('#panel-controles')) return;
  if (mouseY < 0 || mouseX < 0 || mouseX > width || mouseY > height) return;
  resources.push({ pos: createVector(mouseX, mouseY), life: RESOURCE_LIFE });
}

let mouseTarget = null;
document.addEventListener('mousedown', (e) => { mouseTarget = e.target; });

function draw() {
  try {
    dibujarFondo();
    actualizarRecursos();

    for (let p of particles) p.calculateForces(particles);
    for (let p of particles) p.update();
    for (let p of particles) p.display();

    dibujarUI();
  } catch (err) {
    console.error('Error en draw():', err);
    if (uiDiv) {
      uiDiv.html(
        '<b style="color:#ff6b6b">Error de render — revisa la consola (F12)</b><br>' +
        String(err.message || err)
      );
    }
    noLoop();
  }
}

function actualizarRecursos() {
  for (let r of resources) {
    r.life--;
    noStroke();
    let alfa = map(r.life, 0, RESOURCE_LIFE, 0, 0.85);
    let pulse = 8 + sin(frameCount * 0.15) * 2;
    let ctx = drawingContext;
    ctx.shadowBlur = 26;
    ctx.shadowColor = 'hsla(45, 95%, 70%, 0.95)';
    fill(45, 90, 100, alfa);
    ellipse(r.pos.x, r.pos.y, pulse, pulse);
    fill(45, 40, 100, alfa * 0.35);
    ellipse(r.pos.x, r.pos.y, pulse * 2.4, pulse * 2.4);
    ctx.shadowBlur = 0;
  }
  resources = resources.filter(r => r.life > 0);
}

function dibujarFondo() {
  let ctx = drawingContext;

  let grd = ctx.createRadialGradient(width / 2, height * 0.42, 30, width / 2, height / 2, width * 0.85);
  grd.addColorStop(0, 'rgb(20,27,30)');
  grd.addColorStop(0.45, 'rgb(11,15,19)');
  grd.addColorStop(0.8, 'rgb(6,8,12)');
  grd.addColorStop(1, 'rgb(2,3,5)');
  ctx.fillStyle = grd;
  ctx.fillRect(0, 0, width, height);

  if (!nebulosas) {
    nebulosas = [];
    let seedsHue = [16, 205, 108, 280];
    for (let i = 0; i < 4; i++) {
      nebulosas.push({
        x: random(width), y: random(height),
        r: random(width * 0.18, width * 0.3),
        hue: seedsHue[i % seedsHue.length],
        off: random(1000), sp: random(0.0015, 0.003)
      });
    }
  }
  noStroke();
  for (let n of nebulosas) {
    let nx = n.x + noise(n.off) * 60 - 30 + sin(frameCount * n.sp + n.off) * 40;
    let ny = n.y + noise(n.off + 50) * 60 - 30 + cos(frameCount * n.sp + n.off) * 40;
    let grdN = ctx.createRadialGradient(nx, ny, 0, nx, ny, n.r);
    grdN.addColorStop(0, `hsla(${n.hue}, 60%, 40%, 0.10)`);
    grdN.addColorStop(1, `hsla(${n.hue}, 60%, 40%, 0)`);
    ctx.fillStyle = grdN;
    ctx.fillRect(0, 0, width, height);
  }

  if (!estrellasFondo) {
    estrellasFondo = [];
    for (let i = 0; i < 110; i++) {
      estrellasFondo.push({ x: random(width), y: random(height), r: random(0.6, 1.9), f: random(0.02, 0.06), o: random(1000) });
    }
  }
  noStroke();
  for (let s of estrellasFondo) {
    let parp = map(sin(frameCount * s.f + s.o), -1, 1, 0.06, 0.4);
    fill(0, 0, 92, parp);
    ellipse(s.x, s.y, s.r, s.r);
  }

  let vg = ctx.createRadialGradient(width / 2, height / 2, height * 0.35, width / 2, height / 2, width * 0.72);
  vg.addColorStop(0, 'rgba(0,0,0,0)');
  vg.addColorStop(1, 'rgba(0,0,0,0.45)');
  ctx.fillStyle = vg;
  ctx.fillRect(0, 0, width, height);
}

function dibujarUI() {
  let counts = [[0,0,0],[0,0,0],[0,0,0]];
  let eeveeCount = 0;
  for (let p of particles) {
    if (p.species === EEVEE) eeveeCount++; else counts[p.species][p.stage]++;
  }
  let cicloTxt = dominanceCycle === 1
    ? 'Fuego&gt;Planta&gt;Agua&gt;Fuego'
    : 'Fuego&gt;Agua&gt;Planta&gt;Fuego';
  let html = `<b>Competir · Proteger · Cooperar</b><br>clic izquierdo: soltar un recurso disputado<br>ciclo de dominancia: ${cicloTxt}<br><br>`;
  for (let s = 0; s < 3; s++) {
    html += `<b style="color:hsl(${COLORS_HSB[s][0]},${COLORS_HSB[s][1]}%,70%)">${SPECIES_NAMES[s]}</b>: `;
    html += `${STAGE_NAMES[s][0]} ${counts[s][0]} · ${STAGE_NAMES[s][1]} ${counts[s][1]} · ${STAGE_NAMES[s][2]} ${counts[s][2]}<br>`;
  }
  html += `<b style="color:hsl(${COLORS_HSB[EEVEE][0]},${COLORS_HSB[EEVEE][1]}%,70%)">Eevee</b>: ${eeveeCount} · sin estrategia, nunca evoluciona<br>`;
  uiDiv.html(html);
}

function rebuildParticles(seed) {
  randomSeed(seed);
  noiseSeed(seed);
  particles = [];
  for (let i = 0; i < countFuego; i++) particles.push(new Particle(random(30, width - 30), random(30, height - 30), FUEGO));
  for (let i = 0; i < countAgua; i++) particles.push(new Particle(random(30, width - 30), random(30, height - 30), AGUA));
  for (let i = 0; i < countPlanta; i++) particles.push(new Particle(random(30, width - 30), random(30, height - 30), PLANTA));
  for (let i = 0; i < countEevee; i++) particles.push(new Particle(random(30, width - 30), random(30, height - 30), EEVEE));
  resources = [];
}

// ============================================================
// PANEL DE CONTROLES
// ============================================================
function buildControlPanel() {
  const panel = createDiv('');
  panel.id('panel-controles');
  panel.style('position', 'fixed');
  panel.style('top', '10px');
  panel.style('right', '10px');
  panel.style('width', '300px');
  panel.style('max-height', '92vh');
  panel.style('overflow-y', 'auto');
  panel.style('background', 'rgba(8,12,14,0.72)');
  panel.style('backdrop-filter', 'blur(6px)');
  panel.style('border', '1px solid rgba(255,255,255,0.08)');
  panel.style('border-radius', '10px');
  panel.style('padding', '12px 14px 16px 14px');
  panel.style('font-family', 'monospace');
  panel.style('color', '#e4ece9');
  panel.style('font-size', '11px');
  panel.style('z-index', '20');

  const header = createDiv('<b>⚙ Controles</b>');
  header.parent(panel);
  header.style('font-size', '13px');
  header.style('margin-bottom', '8px');
  header.style('cursor', 'pointer');
  const body = createDiv('');
  body.parent(panel);
  header.mousePressed(() => {
    panelOpen = !panelOpen;
    body.style('display', panelOpen ? 'block' : 'none');
  });

  // ---- Matriz de dominancia ----
  section(body, 'Matriz de dominancia');
  const domRow = createDiv('');
  domRow.parent(body);
  domRow.style('margin-bottom', '10px');
  const btnA = createButton('Fuego›Planta›Agua›Fuego');
  const btnB = createButton('Fuego›Agua›Planta›Fuego');
  [btnA, btnB].forEach(b => {
    b.parent(domRow);
    b.style('display', 'block');
    b.style('width', '100%');
    b.style('margin-bottom', '4px');
    b.style('font-size', '10px');
    b.style('padding', '4px');
    b.style('cursor', 'pointer');
    b.style('background', '#12181c');
    b.style('color', '#e4ece9');
    b.style('border', '1px solid rgba(255,255,255,0.12)');
    b.style('border-radius', '6px');
  });
  btnA.mousePressed(() => { dominanceCycle = 1; recomputeDominanceMatrix(); updateDominanceAssignments(); });
  btnB.mousePressed(() => { dominanceCycle = -1; recomputeDominanceMatrix(); updateDominanceAssignments(); });

  // ---- Física general ----
  section(body, 'Física general');
  slider(body, 'Fricción', 0.80, 0.98, P.friction, 0.005, v => P.friction = v);
  slider(body, 'Velocidad máx. base', 1.0, 5.0, P.maxSpeed, 0.1, v => P.maxSpeed = v);
  slider(body, 'Radio de interacción', 60, 220, P.rMax, 2, v => P.rMax = v);
  slider(body, 'Radio de repulsión (contacto)', 10, 50, P.contactMin, 1, v => P.contactMin = v);
  slider(body, 'Fuerza de repulsión', 0.5, 4.0, P.contactPush, 0.1, v => P.contactPush = v);

  // ---- Fuego ----
  section(body, 'Fuego · competir');
  slider(body, 'Persecución', 0.3, 1.5, P.pursueGain, 0.01, v => P.pursueGain = v);
  slider(body, 'Rango de captura', 20, 100, P.captureRange, 1, v => P.captureRange = v);
  slider(body, 'Huida', 0.1, 1.2, P.fleeGainFuego, 0.01, v => P.fleeGainFuego = v);
  slider(body, 'Rango de huida', 30, 140, P.fleeRangeFuego, 1, v => P.fleeRangeFuego = v);
  slider(body, 'Rivalidad interna', 0.0, 0.5, P.rivalryGain, 0.01, v => P.rivalryGain = v);
  slider(body, 'Rango de rivalidad', 20, 100, P.rivalryRange, 1, v => P.rivalryRange = v);

  // ---- Agua ----
  section(body, 'Agua · proteger');
  slider(body, 'Cohesión de escudo', 0.1, 1.5, P.shieldGain, 0.01, v => P.shieldGain = v);
  slider(body, 'Rango de escudo', 30, 150, P.shieldRange, 1, v => P.shieldRange = v);
  slider(body, 'Umbral para escudo', 2, 10, P.shieldThreshold, 1, v => P.shieldThreshold = v);
  slider(body, 'Repulsión al depredador (en escudo)', 0.0, 0.4, P.shieldRepelGain, 0.005, v => P.shieldRepelGain = v);
  slider(body, 'Miedo en solitario', 0.1, 1.2, P.loneFearGain, 0.01, v => P.loneFearGain = v);

  // ---- Planta ----
  section(body, 'Planta · cooperar');
  slider(body, 'Cohesión de grupo', 0.1, 1.5, P.coopGain, 0.01, v => P.coopGain = v);
  slider(body, 'Rango de cohesión', 30, 160, P.coopRange, 1, v => P.coopRange = v);
  slider(body, 'Umbral cooperativo', 2, 10, P.coopThreshold, 1, v => P.coopThreshold = v);
  slider(body, 'Miedo base', 0.1, 1.2, P.fearBasePlanta, 0.01, v => P.fearBasePlanta = v);
  slider(body, 'Dilución de miedo por grupo', 0.0, 0.4, P.fearDilution, 0.01, v => P.fearDilution = v);

  // ---- Evolución ----
  section(body, 'Evolución');
  slider(body, 'Tasa de éxito', 0.002, 0.03, P.successRate, 0.001, v => P.successRate = v);
  slider(body, 'Tasa de decaimiento', 0.002, 0.03, P.decayRate, 0.001, v => P.decayRate = v);

  // ---- Recurso disputado ----
  section(body, 'Recurso disputado');
  slider(body, 'Atracción', 0.2, 2.5, P.resourceGain, 0.05, v => P.resourceGain = v);
  slider(body, 'Rango de detección', 80, 320, P.resourceRange, 5, v => P.resourceRange = v);
  slider(body, 'Impulso al capturar', 0.02, 0.3, P.resourceBoost, 0.01, v => P.resourceBoost = v);

  // ---- Eevee ----
  section(body, 'Eevee · sin estrategia');
  slider(body, 'Rechazo a otras especies', 0.1, 1.2, P.eeveeRepelGain, 0.01, v => P.eeveeRepelGain = v);
  slider(body, 'Rango de rechazo', 30, 150, P.eeveeRepelRange, 1, v => P.eeveeRepelRange = v);
  slider(body, 'Deambular', 0.0, 0.5, P.wanderGain, 0.01, v => P.wanderGain = v);

  // ---- Acciones ----
  section(body, 'Simulación');
  const btnReset = createButton('↻ Reiniciar simulación');
  btnReset.parent(body);
  styleButton(btnReset);
  btnReset.mousePressed(() => rebuildParticles(floor(random(999999))));

  const btnDefaults = createButton('⟲ Valores balanceados por defecto');
  btnDefaults.parent(body);
  styleButton(btnDefaults);
  btnDefaults.mousePressed(() => { restoreDefaults(); refreshSliderDisplays(); rebuildParticles(floor(random(999999))); });

  // ---- Población ----
  section(body, 'Población');
  const popNote = createDiv('Al soltar el control, la simulación se reinicia con las nuevas cantidades.');
  popNote.parent(body);
  popNote.style('color', '#8a9591');
  popNote.style('font-size', '10px');
  popNote.style('margin-bottom', '6px');

  popSlider(body, 'Fuego (Charmander)', 0, 100, countFuego, 1, v => countFuego = v);
  popSlider(body, 'Agua (Squirtle)', 0, 100, countAgua, 1, v => countAgua = v);
  popSlider(body, 'Planta (Bulbasaur)', 0, 100, countPlanta, 1, v => countPlanta = v);
  popSlider(body, 'Eevee', 0, 100, countEevee, 1, v => countEevee = v);

  const btnApplyPop = createButton('✔ Aplicar población y reiniciar');
  btnApplyPop.parent(body);
  styleButton(btnApplyPop);
  btnApplyPop.mousePressed(() => rebuildParticles(floor(random(999999))));
}

// Slider de población: actualiza la variable al arrastrar, pero solo
// reinicia la simulación cuando se suelta (para no recrear el arreglo
// de partículas en cada frame de arrastre).
function popSlider(parent, label, min, max, value, step, onChange) {
  const row = createDiv('');
  row.parent(parent);
  row.style('margin-bottom', '6px');

  const labelRow = createDiv('');
  labelRow.parent(row);
  labelRow.style('display', 'flex');
  labelRow.style('justify-content', 'space-between');
  const lab = createSpan(label);
  lab.parent(labelRow);
  const val = createSpan(String(value));
  val.parent(labelRow);
  val.style('color', '#f0c987');

  const s = createSlider(min, max, value, step);
  s.parent(row);
  s.style('width', '100%');
  s.input(() => {
    let v = s.value();
    val.html(v);
    onChange(v);
  });
  s.changed(() => rebuildParticles(floor(random(999999))));

  return s;
}

let sliderRegistry = [];

function section(parent, title) {
  const h = createDiv(title);
  h.parent(parent);
  h.style('margin', '10px 0 4px 0');
  h.style('color', '#9fd3c7');
  h.style('font-size', '11px');
  h.style('letter-spacing', '0.03em');
  h.style('border-top', '1px solid rgba(255,255,255,0.08)');
  h.style('padding-top', '6px');
}

function slider(parent, label, min, max, value, step, onChange) {
  const row = createDiv('');
  row.parent(parent);
  row.style('margin-bottom', '6px');

  const labelRow = createDiv('');
  labelRow.parent(row);
  labelRow.style('display', 'flex');
  labelRow.style('justify-content', 'space-between');
  const lab = createSpan(label);
  lab.parent(labelRow);
  const val = createSpan(String(value));
  val.parent(labelRow);
  val.style('color', '#f0c987');

  const s = createSlider(min, max, value, step);
  s.parent(row);
  s.style('width', '100%');
  s.input(() => {
    let v = s.value();
    val.html(v);
    onChange(v);
  });

  sliderRegistry.push({ slider: s, valSpan: val, getValue: null });
  return s;
}

function styleButton(b) {
  b.style('display', 'block');
  b.style('width', '100%');
  b.style('margin-bottom', '6px');
  b.style('font-size', '10px');
  b.style('padding', '6px');
  b.style('cursor', 'pointer');
  b.style('background', '#12181c');
  b.style('color', '#e4ece9');
  b.style('border', '1px solid rgba(255,255,255,0.12)');
  b.style('border-radius', '6px');
}

function restoreDefaults() {
  Object.assign(P, {
    friction: 0.90, maxSpeed: 2.6, rMax: 140, contactMin: 26, contactPush: 2.2,
    pursueGain: 0.85, captureRange: 55, fleeGainFuego: 0.5, fleeRangeFuego: 75,
    rivalryGain: 0.14, rivalryRange: 55,
    shieldGain: 0.60, shieldRange: 80, shieldThreshold: 5, shieldRepelGain: 0.11, loneFearGain: 0.5,
    coopGain: 0.55, coopRange: 90, fearBasePlanta: 0.6, fearDilution: 0.16, coopThreshold: 5,
    successRate: 0.010, decayRate: 0.014,
    resourceGain: 1.0, resourceRange: 200, resourceBoost: 0.12,
    eeveeRepelGain: 0.6, eeveeRepelRange: 80, eeveeSpacingGain: 0.18, eeveeSpacingRange: 38, wanderGain: 0.16,
    unrestGain: 0.045
  });
  dominanceCycle = 1;
  recomputeDominanceMatrix();
  updateDominanceAssignments();
  countFuego = 48; countAgua = 48; countPlanta = 48; countEevee = 26;
}

function refreshSliderDisplays() {
  // Reconstruye el panel para reflejar los valores restaurados
  let old = select('#panel-controles');
  if (old) old.remove();
  sliderRegistry = [];
  buildControlPanel();
}

// ============================================================
// PARTÍCULA
// ============================================================
class Particle {
  constructor(x, y, species) {
    this.pos = createVector(x, y);
    this.vel = createVector(random(-1, 1), random(-1, 1));
    this.acc = createVector(0, 0);
    this.species = species;
    this.stage = 0;
    this.successMeter = random(0.2, 0.4);
    this.dominadorIdx = (species < 3) ? DOMINANCE.findIndex((_, i) => DOMINANCE[i][species] === 1) : -1;
    this.dominadoIdx = (species < 3) ? DOMINANCE[species].findIndex(v => v === 1) : -1;
    this.tension = 0;
    this.noiseOffset = random(1000);
  }

  calculateForces(others) {
    let total = createVector(0, 0);
    let sameTypeNear = 0;
    let preyClose = false;
    let predatorInFleeRange = false;
    let predatorInRMax = false;
    let beingRejected = false;

    const forceMult = STAGE_FORCE_MULT[this.stage];
    const cohesionRange = this.species === FUEGO ? P.rivalryRange
                          : this.species === AGUA ? P.shieldRange
                          : this.species === PLANTA ? P.coopRange
                          : P.eeveeSpacingRange;

    for (let other of others) {
      if (other === this) continue;
      let d = p5.Vector.dist(this.pos, other.pos);
      if (d <= 0 || d >= P.rMax) continue;
      let dir = p5.Vector.sub(other.pos, this.pos).normalize();

      let sizeSum = (STAGE_SIZE_MULT[this.stage] + STAGE_SIZE_MULT[other.stage]) * 0.5;
      let effContactMin = P.contactMin * sizeSum;
      if (d < effContactMin) {
        let push = map(d, 0, effContactMin, P.contactPush * sizeSum, 0);
        total.add(p5.Vector.mult(dir, -push));
      }

      if (other.species === this.species && d < cohesionRange) {
        sameTypeNear++;
      }

      if (other.species === this.dominadorIdx) {
        if (d < P.fleeRangeFuego) predatorInFleeRange = true;
        predatorInRMax = true;
      }
      if (other.species === this.dominadoIdx && d < P.captureRange) {
        preyClose = true;
      }

      if (this.species === FUEGO) {
        if (other.species === this.dominadoIdx) {
          total.add(p5.Vector.mult(dir, P.pursueGain * forceMult));
        } else if (other.species === this.dominadorIdx && d < P.fleeRangeFuego) {
          let falloff = 1 - d / P.fleeRangeFuego;
          total.add(p5.Vector.mult(dir, -P.fleeGainFuego * falloff));
        } else if (other.species === this.species && d < P.rivalryRange) {
          let falloff = 1 - d / P.rivalryRange;
          total.add(p5.Vector.mult(dir, -P.rivalryGain * falloff));
        }
      }

      else if (this.species === AGUA) {
        if (other.species === this.species && d < P.shieldRange) {
          let scaledD = d / P.shieldRange;
          let bump = 1.0 - abs(2.0 * scaledD - 1.0);
          total.add(p5.Vector.mult(dir, P.shieldGain * forceMult * max(0, bump)));
        } else if (other.species === this.dominadorIdx) {
          if (sameTypeNear >= P.shieldThreshold) {
            let falloff = pow(1 - d / P.rMax, 2);
            total.add(p5.Vector.mult(dir, -P.shieldRepelGain * forceMult * sameTypeNear * falloff));
          } else if (d < P.fleeRangeFuego) {
            let falloff = 1 - d / P.fleeRangeFuego;
            total.add(p5.Vector.mult(dir, -P.loneFearGain * falloff));
          }
        }
      }

      else if (this.species === PLANTA) {
        if (other.species === this.species && d < P.coopRange) {
          let scaledD = d / P.coopRange;
          let bump = 1.0 - abs(2.0 * scaledD - 1.0);
          total.add(p5.Vector.mult(dir, P.coopGain * forceMult * max(0, bump)));
        } else if (other.species === this.dominadorIdx && d < P.fleeRangeFuego) {
          let dilutedFear = P.fearBasePlanta / (1 + sameTypeNear * P.fearDilution);
          let falloff = 1 - d / P.fleeRangeFuego;
          total.add(p5.Vector.mult(dir, -dilutedFear * falloff));
        }
      }

      else if (this.species === EEVEE) {
        if (other.species !== EEVEE && d < P.eeveeRepelRange) {
          let falloff = 1 - d / P.eeveeRepelRange;
          total.add(p5.Vector.mult(dir, -P.eeveeRepelGain * falloff));
          beingRejected = true;
        } else if (other.species === EEVEE && d < P.eeveeSpacingRange) {
          let falloff = 1 - d / P.eeveeSpacingRange;
          total.add(p5.Vector.mult(dir, -P.eeveeSpacingGain * falloff));
        }
      }
    }

    let ang = noise(this.noiseOffset + frameCount * 0.006) * TWO_PI * 2;
    total.add(p5.Vector.fromAngle(ang).mult(P.unrestGain));

    // Recurso disputado: ahora compartido por las 3 especies principales,
    // con el mismo impulso de éxito para que ninguna tenga un atajo exclusivo.
    if (this.species === FUEGO || this.species === AGUA || this.species === PLANTA) {
      for (let r of resources) {
        let d = p5.Vector.dist(this.pos, r.pos);
        if (d > 0 && d < P.resourceRange) {
          let dir = p5.Vector.sub(r.pos, this.pos).normalize();
          let falloff = 1 - d / P.resourceRange;
          total.add(p5.Vector.mult(dir, P.resourceGain * falloff));
          if (d < 16) { this.successMeter = min(1, this.successMeter + P.resourceBoost); r.life = 0; }
        }
      }
    }

    if (this.species === EEVEE) {
      let wanderAng = noise(this.noiseOffset + 500 + frameCount * 0.01) * TWO_PI * 2;
      total.add(p5.Vector.fromAngle(wanderAng).mult(P.wanderGain));
    }

    this.acc.add(total);

    if (this.species === EEVEE) {
      this.tension = beingRejected ? 1 : this.tension * 0.9;
    } else {
      this.evolve(sameTypeNear, preyClose, predatorInFleeRange, predatorInRMax);
    }
  }

  evolve(sameTypeNear, preyClose, predatorInFleeRange, predatorInRMax) {
    let exito = false;
    if (this.species === FUEGO) {
      exito = preyClose && !predatorInFleeRange;
    } else if (this.species === PLANTA) {
      exito = sameTypeNear >= P.coopThreshold;
    } else if (this.species === AGUA) {
      exito = predatorInRMax && sameTypeNear >= P.shieldThreshold;
    }

    this.tension = exito ? 1 : this.tension * 0.9;
    this.successMeter += exito ? P.successRate : -P.decayRate;
    this.successMeter = constrain(this.successMeter, 0, 1);

    if (this.successMeter >= 1 && this.stage < 2) {
      this.stage++;
      this.successMeter = EVOLVE_RESET;
    } else if (this.successMeter <= 0 && this.stage > 0) {
      this.stage--;
      this.successMeter = EVOLVE_RESET;
    }
  }

  update() {
    const m = 10 + STAGE_SIZE_MULT[this.stage] * 5;
    const margin = m + 46;
    let steer = createVector(0, 0);
    if (this.pos.x < margin) steer.x += map(this.pos.x, m, margin, 1.3, 0, true);
    if (this.pos.x > width - margin) steer.x -= map(this.pos.x, width - margin, width - m, 0, 1.3, true);
    if (this.pos.y < margin) steer.y += map(this.pos.y, m, margin, 1.3, 0, true);
    if (this.pos.y > height - margin) steer.y -= map(this.pos.y, height - margin, height - m, 0, 1.3, true);
    this.acc.add(steer);

    this.vel.add(this.acc);
    this.vel.mult(P.friction);
    this.vel.limit(P.maxSpeed * SPEED_MULT[this.species]);

    if (this.tension > 0.4) {
      this.vel.add(p5.Vector.random2D().mult(this.tension * 0.35));
    }

    this.pos.add(this.vel);
    this.acc.mult(0);

    this.pos.x = constrain(this.pos.x, m, width - m);
    this.pos.y = constrain(this.pos.y, m, height - m);
  }

  display() {
    noStroke();
    let ctx = drawingContext;
    let [h, s, b] = COLORS_HSB[this.species];
    let pulso = constrain(this.tension, 0, 1);
    let sat = map(pulso, 0, 1, s * 0.6, s);
    let glow = map(this.stage, 0, 2, 6, 26) + pulso * 12;
    let sz = (11 + this.stage * 4.5) * STAGE_SIZE_MULT[this.stage] * 0.95;

    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.vel.heading());
    ctx.shadowBlur = glow;
    ctx.shadowColor = `hsla(${h}, ${sat}%, ${b}%, 0.9)`;

    if (this.species === FUEGO) this.drawFuego(sz, h, sat, b, ctx);
    else if (this.species === AGUA) this.drawAgua(sz, h, sat, b, ctx);
    else if (this.species === PLANTA) this.drawPlanta(sz, h, sat, b, ctx);
    else this.drawEevee(sz, h, sat, b, ctx);

    pop();
  }

  eye(x, y, r) {
    fill(0, 0, 8);
    ellipse(x, y, r, r);
    fill(0, 0, 95);
    ellipse(x - r * 0.2, y - r * 0.2, r * 0.35, r * 0.35);
  }

  drawFuego(sz, h, sat, b, ctx) {
    fill(h, sat, b * 0.72);
    ellipse(0, 0, sz * 1.9, sz * 1.05);
    fill(38, sat * 0.5, b * 0.98);
    ellipse(sz * 0.1, sz * 0.12, sz * 1.3, sz * 0.55);

    fill(h, sat, b * 0.78);
    ellipse(sz * 0.95, -sz * 0.05, sz * 0.88, sz * 0.78);

    ctx.shadowBlur = 0;
    fill(20, sat * 0.9, b * 0.85);
    triangle(-sz * 1.05, sz * 0.42, -sz * 1.05, -sz * 0.42, -sz * 1.75, 0);
    fill(48, sat * 0.9, 100);
    triangle(-sz * 1.1, sz * 0.2, -sz * 1.1, -sz * 0.2, -sz * (1.55 + this.stage * 0.15), 0);

    if (this.stage >= 1) {
      fill(h, sat, b * 0.6);
      for (let i = -1; i <= 1; i++) {
        let px = i * sz * 0.55;
        triangle(px - sz * 0.16, -sz * 0.42, px + sz * 0.16, -sz * 0.42, px, -sz * 0.82);
      }
    }

    if (this.stage >= 2) {
      fill(58, sat * 0.7, b * 0.55, 0.92);
      beginShape();
      vertex(-sz * 0.15, -sz * 0.35);
      vertex(-sz * 0.85, -sz * 0.55);
      vertex(-sz * 1.55, -sz * 1.3);
      vertex(-sz * 1.05, -sz * 0.95);
      vertex(-sz * 0.55, -sz * 0.5);
      vertex(sz * 0.15, -sz * 0.55);
      endShape(CLOSE);
      beginShape();
      vertex(-sz * 0.15, sz * 0.35);
      vertex(-sz * 0.85, sz * 0.55);
      vertex(-sz * 1.55, sz * 1.3);
      vertex(-sz * 1.05, sz * 0.95);
      vertex(-sz * 0.55, sz * 0.5);
      vertex(sz * 0.15, sz * 0.55);
      endShape(CLOSE);
      fill(20, sat * 0.9, b * 0.5);
      triangle(sz * 0.75, -sz * 0.35, sz * 0.6, -sz * 0.75, sz * 1.0, -sz * 0.3);
      triangle(sz * 0.75, sz * 0.35, sz * 0.6, sz * 0.75, sz * 1.0, sz * 0.3);
    }

    this.eye(sz * 1.15, -sz * 0.12, sz * 0.13);
  }

  drawAgua(sz, h, sat, b, ctx) {
    fill(h, sat, b * 0.85);
    ellipse(0, 0, sz * 1.7, sz * 1.35);
    fill(h, sat * 0.6, b * 0.6);
    ellipse(0, 0, sz * 1.25, sz * 0.95);

    fill(30, sat * 0.55, b * 0.95);
    ellipse(sz * 0.95, 0, sz * 0.82, sz * 0.72);

    if (this.stage >= 1) {
      fill(0, 0, 96);
      ellipse(-sz * 1.15, -sz * 0.2, sz * 0.55, sz * 0.3);
      ellipse(-sz * 1.35, sz * 0.05, sz * 0.4, sz * 0.24);
    }

    if (this.stage >= 2) {
      ctx.shadowBlur = 0;
      fill(0, 0, 75);
      ellipse(-sz * 0.25, -sz * 0.55, sz * 0.5, sz * 0.5);
      ellipse(-sz * 0.25, sz * 0.55, sz * 0.5, sz * 0.5);
      fill(0, 0, 40);
      ellipse(-sz * 0.25, -sz * 0.55, sz * 0.22, sz * 0.22);
      ellipse(-sz * 0.25, sz * 0.55, sz * 0.22, sz * 0.22);
    }

    this.eye(sz * 1.15, -sz * 0.1, sz * 0.12);
  }

  drawPlanta(sz, h, sat, b, ctx) {
    fill(h, sat, b * 0.8);
    ellipse(0, 0, sz * 1.75, sz * 1.05);
    fill(h, sat * 0.5, b * 0.55);
    ellipse(sz * 0.2, sz * 0.15, sz * 1.1, sz * 0.5);

    fill(h, sat, b * 0.85);
    ellipse(sz * 0.95, -sz * 0.02, sz * 0.75, sz * 0.65);

    fill(300, sat * 0.35, b * 0.6);
    ellipse(-sz * 0.15, 0, sz * (0.6 + this.stage * 0.18), sz * (0.55 + this.stage * 0.16));

    if (this.stage >= 1) {
      ctx.shadowBlur = 0;
      fill(330, sat * 0.5, b);
      for (let a = 0; a < TWO_PI; a += TWO_PI / 5) {
        let px = -sz * 0.15 + cos(a) * sz * 0.32;
        let py = sin(a) * sz * 0.32;
        ellipse(px, py, sz * 0.28, sz * 0.16);
      }
    }

    if (this.stage >= 2) {
      fill(340, sat * 0.55, b);
      for (let a = 0; a < TWO_PI; a += TWO_PI / 6) {
        let px = -sz * 0.15 + cos(a) * sz * 0.5;
        let py = sin(a) * sz * 0.5;
        ellipse(px, py, sz * 0.42, sz * 0.24);
      }
      fill(50, sat * 0.6, 100);
      ellipse(-sz * 0.15, 0, sz * 0.42, sz * 0.42);
    }

    this.eye(sz * 1.18, -sz * 0.1, sz * 0.12);
  }

  drawEevee(sz, h, sat, b, ctx) {
    fill(h, sat, b * 0.92);
    ellipse(0, 0, sz * 1.6, sz * 1.2);

    ellipse(sz * 0.85, -sz * 0.05, sz * 0.98, sz * 0.88);

    fill(h, sat * 0.75, b * 0.7);
    triangle(sz * 0.55, -sz * 0.5, sz * 0.4, -sz * 1.05, sz * 0.95, -sz * 0.65);
    triangle(sz * 1.15, -sz * 0.5, sz * 1.0, -sz * 1.02, sz * 1.45, -sz * 0.62);

    ctx.shadowBlur = 0;
    fill(38, sat * 0.5, 100, 0.95);
    for (let a = -0.85; a <= 0.85; a += 0.35) {
      let px = cos(a) * sz * 0.55;
      let py = sin(a) * sz * 0.72 - sz * 0.05;
      ellipse(px, py, sz * 0.4, sz * 0.4);
    }

    fill(38, sat * 0.4, 100, 0.9);
    ellipse(-sz * 1.05, 0, sz * 0.55, sz * 0.4);

    this.eye(sz * 1.15, -sz * 0.08, sz * 0.13);
  }
}

```

## AUTOEVALUACIÓN

| Criterio | Peso | Valoracion | Aporte |
|----------|:----:|:----------:|:------:|
| La intencion es clara y perceptible en el comportamiento. | 20% | 95% | [EXPERIENCIA FINAL](#RESULTADO-FINAL) |
| Los tipos, cantidades, matriz y parametros estan justificados desde la intencion. | 25% | 100% | [Diseño](#Diseño-del-sistema) |
| Comprendo y puedo modificar el funcionamiento tecnico del sistema. | 20% | 80% | [EXPERIENCIA FINAL](#RESULTADO-FINAL) |
| El sistema produce variaciones con una identidad reconocible. | 15% | 90% | [EXPERIENCIA FINAL](#RESULTADO-FINAL) |
| Experimente, compare, seleccione y descarte con criterios claros. | 10% | 85% | [PROCESO DE DESARROLLO](#PROCESO-DE-DESARROLLO) |
| Puedo distinguir y sustentar lo disenado y lo emergente. | 10% | 100% | ya en la expo. pero si creo q duro |
| **Total** | **100%** | **100%** | **100%** |

TODO ESTA PUESTO EN LA PARTE DE ARRIBA

NOTA = 4.6

