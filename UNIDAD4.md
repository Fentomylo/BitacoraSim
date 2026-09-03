# IDEA AHI REDACTADA PARA HACER ESTO

# Frutiger Aero OS — Cómo funcionan los agentes y las ventanas

Este documento explica, ventana por ventana y agente por agente, cómo el modelo de Kuramoto gobierna el comportamiento visual y sonoro del sistema.

## El modelo, en una frase

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

Detalles compartidos por todos:
- **Contorno tipo "sticker"** (silueta oscura detrás del núcleo) para que se recorten contra cualquier fondo del wallpaper.
- **Aura + brillo + destellos** que titilan de forma independiente entre agentes (fase y velocidad propias), como capas extra encima de la silueta.
- Cada beat (cruce de fase) escala el núcleo, el halo y el aro exterior — el "thump" visual siempre está sincronizado 1 a 1 con la nota que suena.

---

## Las ventanas y qué le hacen al modelo

Cada ventana en la que cae un agente reemplaza su término de acople de Kuramoto por una variante distinta, además de cambiar cómo suena.

### 🌐 Google
El agente se **desacopla por completo**: solo usa su propio `ωᵢ` más ruido, sin ver a ningún vecino. Sonido apagado y grave (volumen bajo, filtro cerrado en 800 Hz) — la sensación de estar "aislado navegando".

### 🗂️ Explorador de archivos
Acople **fuerte, pero solo entre agentes que compartan la misma ventana** (no con todo el colectivo). Si metés a dos agentes juntos ahí, se arrastran mutuamente hacia la misma fase mucho más rápido que en el escritorio libre. Timbre medio-brillante (3200 Hz).

### 🎵 Windows Media Player
Hay un **metrónomo interno fijo** (100 BPM) corriendo siempre, independiente del resto del sistema. Cualquier agente adentro es arrastrado hacia la fase de ese metrónomo con fuerza `3.2` — sincronía forzada externa, no emergente. Es la ventana más "brillante" en volumen y filtro (1.4 de ganancia, 9000 Hz).

### 🎨 Paint
El agente **lee el dibujo**: la posición X de lo último trazado define una fase objetivo que persigue (mismo mecanismo que el metrónomo del Player, pero guiado por vos en vez de un tempo fijo). Más colores usados en el lienzo = persecución más firme. Un trazo delgado y suelto lo deja inquieto; una mancha sólida y rellena lo calma. El volumen sube con la cantidad de tinta dibujada, y el filtro traduce el eje Y del trazo en brillo tonal (arriba = agudo, abajo = grave), como un theremin.

### ✉️ Mail
Un pulso rítmico fijo tipo "ping de notificación" empuja la deriva de fase del agente. Filtro medio (5000 Hz), volumen alto y constante.

### 🖼️ Galería
No tiene una regla de fase propia — dinámicamente se comporta como un agente libre (Kuramoto de campo medio con el resto del escritorio). Lo que sí cambia radicalmente es el audio: pasa por un bus de chorus dedicado (`galleryChorus`) que le da una riqueza coral notable, con más presencia y volumen (1.5) que cualquier otra ventana.

### 💬 Messenger
Igual que la Galería: sin regla de fase propia, se comporta como agente libre. El cambio es puramente sonoro (volumen 0.9, filtro medio en 4000 Hz).

### 🗑️ Papelera
**Aísla y silencia por completo**: `dθ/dt = 0` (fase congelada), volumen en 0, y se **excluye del cálculo del parámetro de orden `r`** — como si el agente dejara de existir para el colectivo. Es el mecanismo de "castigo/pausa" del sistema.

---

## Interacción performativa

- **Arrastrar un agente**: mientras lo sostenés, su fase queda congelada (no avanza) y su audio se abre al máximo (volumen 1.6, filtro 12000 Hz) — feedback inmediato de "tengo el control".
- **Soltarlo sobre una ventana**: le asigna la regla de fase de esa ventana (arriba) hasta que lo saques.
- **Doble click sobre un agente en ventana**: lo expulsa — mecanismo de perturbación explícito. Le mete un salto de fase aleatorio (entre −π y π) y lo devuelve al colectivo libre, para observar cómo el resto responde a esa sacudida.
- **Sliders globales** (acoplamiento K, ruido, deriva, velocidad): afectan a todos los agentes libres a la vez.
- **Presets** (Calma / Caos / Unión): reconfiguran K, ruido y deriva de golpe para saltar entre regímenes.

## Cómo se comunica el estado colectivo

El parámetro de orden `r` (0 = desorden total, 1 = sincronía perfecta) se traduce en **3 estados explícitos** mostrados en el HUD: ⚡ Desorden (`r < 0.35`), 💫 Organización parcial (`0.35 ≤ r < 0.7`) y 🔗 Organización estable (`r ≥ 0.7`). El mismo valor de `r` también controla en vivo el reverb y el delay de todo el bus de audio — cuanto más sincronizado está el colectivo, más "ambiente/eco" envuelve el sonido, así que el estado se percibe tanto leyendo el HUD como escuchando el espacio sonoro.

# INTENTOS


<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/85b39e9b-4b83-4fce-82c9-eee7cc95c364" />


<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/632e615b-e393-4bdd-b1a7-73699cc7081e" />


<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/0cac5799-3981-4388-8f85-b03744a4d8ff" />

<img width="1956" height="969" alt="image" src="https://github.com/user-attachments/assets/ec4c29d4-86a3-4a2e-bb02-c94bf13e0f15" />



<img width="2535" height="1439" alt="image" src="https://github.com/user-attachments/assets/ab930bf9-8b8f-4f39-8db2-5f2b724a5c77" />

