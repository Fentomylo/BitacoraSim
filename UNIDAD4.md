# OSCILACIONES

# LINK A LA PAGINA Y AL REPOSITORIO

* [Link pagina](https://fentomylo.github.io/OSCILACIONEZZZZ/)
* [Link repositorio](https://github.com/Fentomylo/OSCILACIONEZZZZ.git)

# NAVEGADORGOD FRUTIGER AERO JUAN LUIS GUERRA 4.40

Ps bueno, mi idea original era hacer un tipo de necrodancer, pero no queria que fuera moviendose con las teclas, por lo que habia pensado en moverlo con el mouse y que el escenario fuera un escritorio de windows vista, esto porq a mi me gusta mucho la estetica que tenia este sistema.

Pero, despues de verlo bien y pensarlo mejor, decidi cambiar un poco la idea. Basandome en el virus del mono morado del windows xp o vista, queria que mis agentes fueran como una especie de virus, donde yo con el mouse los puedo jalar y arrastrar y mover como yo queria. Pero aqui vino 
la idea clave, decidi crear paginas o aplicaciones en el windows, y que dependiendo a la pagina que entrara, esta modificara a cada agente. Haciendo q cada agente con su sonido unico pueda ser modificado dependiendo de donde sea ubicado.

La idea original era hacer esto con un tema EDM o hyperpop, estilo ninajirachi. Pero no funciono muy bien, por lo que decidi hacer como un creador de sonidos que juntos suenan como un ambiente frutiger aero. Queria que fuera fiel tanto lo visual como lo sonoro.

Por lo que mi idea final es, un ambiente frutiger aero en un escritorio windows vista con posibilidad de entrar en paginas y modificar el sonido de agentes, q son virus.

## El modelo con kursmoto, en una frase

Cada agente es un oscilador de Kuramoto: acumula una fase propia `θᵢ` que avanza según su "temperamento" `ωᵢ` más la influencia de sus vecinos, ponderada por la fuerza de acople `K`. Cada vez que esa fase completa una vuelta (2π), el agente dispara su nota y su "kick" visual (escala, halo, brillo). Soltar un agente sobre una ventana no es solo estético: **cambia la fórmula con la que ese agente calcula su propia fase**, porque cada ventana reemplaza o modula el término de acople de forma distinta. Ahí vive la relación real entre algoritmo, sonido e imagen.

---

## Los 8 agentes

Cada uno tiene una forma, un color, un `ωᵢ` (frecuencia natural), un estilo de movimiento propio y un instrumento distinto — la personalidad no se apoya solo en el color o en la altura de la nota, sino también en *cómo* se mueve.

| Agente | ω (temperamento) | Forma | Color | Movimiento | Instrumento |
|---|---|---|---|---|---|
| **Static-Tan** | 1.8 — nerviosa, reactiva | Estrella de picos afilados | Cian | `jittery`: retargeting muy rápido + temblor constante de posición | `clair-arp` — arpegio de campana |
| **Core-Tan** | 0.6 — terca, estable | Hexágono sólido | Verde | `anchor`: casi no se mueve, destinos que apenas cambian | `debussy-pad` — acordes sostenidos |
| **Mirror-Tan** | 1.1 — mimetiza vecinos | Anillo hueco | Magenta | `mimic`: su próximo destino se calcula promediando la posición de los 2 agentes libres más cercanos | `crystal-bird` — dos notas FM en cascada |
| **Signal-Tan** | 1.5 — errática, con fricción | Blob irregular de 5 lóbulos | Naranja | `erratic`: la velocidad de deambulación fluctúa al azar en cada cuadro | `water-bubble` — burbuja FM con detune aleatorio |
| **Petal** | 1.3 — juguetona, ligera | Flor de lóbulos suaves | Amarillo | `floaty`: deambula rápido con un vaivén vertical constante | `glass-chime` — campanita de vidrio |
| **Disko** | 1.0 — analítica, de hardware | Diamante | Violeta | `gridSnap`: sus destinos se redondean a una grilla, movimiento "digital" | `liquid-drop` — gota de membrana |
| **Pixel-Boy** | 1.2 — observadora, digital | Cuadrado alineado a ejes | Turquesa | `idleJump`: casi no se mueve; cuando lo hace, "teletransporta" en vez de desplazarse | `rainbow-lead` — lead grueso de 4 osciladores |
| **Moth** | 1.4 — impulsiva, flotante | Blob suave de 3 lóbulos | Púrpura | `impulsive`: ráfaga rápida justo después de elegir destino nuevo, luego flota | `space-breeze` — ruido rosa envolvente |

## Los 8 personajes explicados mas amigablemente

Todos "aplauden" (suenan y destellan) a un ritmo propio, pero se diferencian por **cómo se mueven por la pista** y **qué instrumento tocan**, no solo por el color:

- **Static-Tan** (estrella cian): la ansiosa del grupo. Cambia de lugar todo el tiempo y tiembla un poco incluso quieta. Ritmo natural muy rápido. Suena como un arpegio de campana, nervioso.
- **Core-Tan** (hexágono verde): la más terca y tranquila. Casi no se mueve de su lugar. Su ritmo natural es el más lento de todas. Suena con acordes largos y sostenidos, como un fondo calmado.
- **Mirror-Tan** (anillo magenta): la copiona. No decide su propio camino: mira a las dos personas libres más cercanas y va hacia el punto medio entre ellas. Suena con dos notas que se persiguen en cascada.
- **Signal-Tan** (blob naranja): la impredecible. Su velocidad para moverse cambia solita todo el rato, a veces rápido, a veces lento, sin patrón. Suena como una burbuja de agua que se desafina levemente.
- **Petal** (flor amarilla): la ligera y juguetona. Se mueve rápido con un vaivén suave hacia arriba y abajo, como flotando. Suena como una campanita de vidrio.
- **Disko** (diamante violeta): la calculadora. Sus movimientos "se pegan" a una cuadrícula invisible, como si pensara en coordenadas exactas en vez de moverse libremente. Suena como una gota líquida.
- **Pixel-Boy** (cuadrado turquesa): la observadora. Casi no se mueve, y cuando lo hace no camina — aparece directamente en el nuevo lugar, como un salto. Suena con un lead grueso, como de sintetizador ochentero.
- **Moth** (blob púrpura): la impulsiva. Apenas decide a dónde ir, sale disparada rápido y después se calma y flota el resto del camino. Suena como un viento suave y envolvente.

---

## Las "ventanas" — los cuartos de la fiesta

Arrastrar a un personaje dentro de una ventana no es solo decoración: **le cambia las reglas de cómo se sincroniza** mientras esté ahí adentro.

- ** Google — el cuarto del aislamiento.** Adentro, el personaje deja de mirar a los demás por completo. Baila solo a su propio ritmo, sordo al resto de la fiesta. Suena apagado y bajito, como si estuviera con la puerta cerrada.
- ** Explorador de archivos — el cuarto de las camarillas.** Los personajes que estén juntos ahí adentro se sincronizan MUY fuerte entre ellos — pero solo entre ellos, ignorando a los de afuera. Es el clásico "grupito cerrado" de la fiesta.
- ** Windows Media Player — el cuarto del DJ.** Hay un beat fijo sonando siempre a un tempo constante, y quien entra queda obligado a seguir ese beat, le guste o no. Es sincronía impuesta desde afuera, no una que surge sola.
- ** Paint — el cuarto donde vos sos el DJ.** Acá el personaje no sigue un beat fijo: sigue **lo que vos dibujás**. La posición horizontal de tu último trazo es el ritmo que persigue. Si pintás una mancha sólida y con muchos colores, lo seguís con firmeza; si hacés una rayita suelta, queda más inquieto. Y la altura de tu trazo (arriba/abajo) cambia si suena agudo o grave, como un theremín que vos controlás con el pincel.
- ** Mail — el cuarto de las notificaciones.** Un "ping" rítmico constante empuja al personaje, como si le llegaran mensajes todo el tiempo.
- ** Galería — el cuarto del eco.** Acá la forma de sincronizarse no cambia (sigue las reglas normales de la pista libre), pero el sonido sí: se le agrega un efecto coral/reverberante bien notorio, como cantar en una sala con mucho eco.
- ** Messenger — el cuarto de las charlas cruzadas.** Igual que la Galería: la sincronía no cambia, solo el timbre del sonido, más medio y presente.
- ** Papelera — el castigo.** El personaje queda completamente congelado y en silencio, y ni siquiera cuenta para calcular qué tan sincronizado está el grupo — es como si, para efectos de la fiesta, hubiera dejado de existir.

---

## Cómo interactuás con todo esto

- **Agarrar y arrastrar a un personaje**: mientras lo sostenés, se congela su ritmo y su sonido se abre al máximo (bien brillante) — para sentir que lo tenés bajo control.
- **Soltarlo en un cuarto**: adopta las reglas de ese cuarto hasta que lo saques.
- **Doble click sobre un personaje que está en un cuarto**: lo "expulsa" de golpe — le da un empujón aleatorio a su ritmo y lo devuelve a la pista libre, para ver cómo reacciona el resto del grupo a esa sacudida.
- **Las perillas del panel** (acoplamiento, ruido, deriva, velocidad): cambian las reglas para TODO el grupo a la vez, no para uno solo.

## Cómo se sabe qué tan sincronizado está el grupo

El sistema calcula un número entre 0 y 1 que mide qué tan de acuerdo está bailando todo el grupo (0 = cada quien a lo suyo, 1 = todos exactamente igual). Ese número se muestra como texto ("Desorden", "Organización parcial", "Organización estable") en la esquina, **y además** hace que el sonido general de la fiesta tenga más o menos eco: cuanto más sincronizado está el grupo, más "envolvente" suena todo — así que se nota tanto leyendo la pantalla como cerrando los ojos y escuchando.

## Interacción performativa

- **Arrastrar un agente**: mientras lo sostenés, su fase queda congelada (no avanza) y su audio se abre al máximo (volumen 1.6, filtro 12000 Hz) — feedback inmediato de "tengo el control".
- **Soltarlo sobre una ventana**: le asigna la regla de fase de esa ventana (arriba) hasta que lo saques.
- **Doble click sobre un agente en ventana**: lo expulsa — mecanismo de perturbación explícito. Le mete un salto de fase aleatorio (entre −π y π) y lo devuelve al colectivo libre, para observar cómo el resto responde a esa sacudida.
- **Sliders globales** (acoplamiento K, ruido, deriva, velocidad): afectan a todos los agentes libres a la vez.
- **Presets** (Calma / Caos / Unión): reconfiguran K, ruido y deriva de golpe para saltar entre regímenes.

## Cómo se comunica el estado colectivo

El parámetro de orden `r` (0 = desorden total, 1 = sincronía perfecta) se traduce en **3 estados explícitos** mostrados en el HUD: ⚡ Desorden (`r < 0.35`), 💫 Organización parcial (`0.35 ≤ r < 0.7`) y 🔗 Organización estable (`r ≥ 0.7`). El mismo valor de `r` también controla en vivo el reverb y el delay de todo el bus de audio — cuanto más sincronizado está el colectivo, más "ambiente/eco" envuelve el sonido, así que el estado se percibe tanto leyendo el HUD como escuchando el espacio sonoro.

# Cumplimiento de requisitos mínimos

- **8 agentes simultáneos gobernados por el sistema dinámico** ✅ `nodeCount: 8`, los 8 corren bajo la misma ecuación de Kuramoto en todo momento.

- **4 personalidades audiovisuales diferentes** ✅ Hay 8 (Static-Tan, Core-Tan, Mirror-Tan, Signal-Tan, Petal, Disko, Pixel-Boy, Moth), diferenciadas en forma, movimiento e instrumento, no solo color/tono.

- **Manifestación visual y sonora por agente, vinculadas a su comportamiento** ✅ Cada vuelta de fase (θᵢ completa 2π) dispara a la vez la nota y el "kick" visual (escala/halo/brillo) — van siempre juntos.

- **2+ variables del modelo modificables en tiempo real, incluyendo K** ✅ Panel con 4 sliders: acoplamiento (K), ruido, deriva y velocidad.

- **2+ formas de interacción performativa (global e individual)** ✅ Global: sliders y presets (Calma/Caos/Unión). Individual: arrastrar un agente puntual o soltarlo en una ventana específica.

- **1+ mecanismo de perturbación con respuesta observable del colectivo** ✅ Doble click sobre un agente en una ventana lo expulsa con salto de fase aleatorio; se ve cómo reacciona el `r` del resto.

- **Reconocer 3 estados colectivos (desorden, parcial, estable)** ✅ El HUD clasifica `r` en esos 3 estados con umbrales explícitos (0.35 y 0.7).

- **1+ forma perceptible de comunicar el estado colectivo** ✅ Texto del HUD (indicador explícito) + reverb/delay del audio, que se abre más cuanto más sincronizado está el grupo (sonoro).

**Cumple los 8 requisitos mínimos**, varios con margen de sobra.

# INTENTOS

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/85b39e9b-4b83-4fce-82c9-eee7cc95c364" />


<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/632e615b-e393-4bdd-b1a7-73699cc7081e" />


<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/0cac5799-3981-4388-8f85-b03744a4d8ff" />

<img width="1956" height="969" alt="image" src="https://github.com/user-attachments/assets/ec4c29d4-86a3-4a2e-bb02-c94bf13e0f15" />

https://github.com/user-attachments/assets/976b15d7-8544-4404-8604-f1facd606a7f


<img width="667" height="397" alt="image" src="https://github.com/user-attachments/assets/b52a3d3d-2056-411e-972a-7c7501f37da0" />

<img width="541" height="516" alt="image" src="https://github.com/user-attachments/assets/23382182-cfe3-4c84-b9f0-f6114ed9d9ee" />

<img width="1600" height="767" alt="image" src="https://github.com/user-attachments/assets/786e0f49-e7fc-430b-a553-a092a6d4521d" />

<img width="1600" height="761" alt="image" src="https://github.com/user-attachments/assets/b65c97f6-be81-4d07-8be1-09c3dcc37db5" />

<img width="1600" height="769" alt="image" src="https://github.com/user-attachments/assets/e84d0511-cb17-4c9a-b46d-fb7f6629097e" />


# AUTOEVALUACION

<img width="853" height="140" alt="image" src="https://github.com/user-attachments/assets/547491e7-0dbf-4f78-ad04-7dec76e4372b" />

Asi como aparece en la foto 25 puntos en todo, 5.






