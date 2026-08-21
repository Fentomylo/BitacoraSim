# FUERZOVICH

## Instrumento funcional y publicado:

[APP](https://fentomylo.github.io/FUERZAS/)

## Mapa del sistema:

| Fuerza / Modulación | Tecla(s) / Control | Archivo | ¿Qué hace? | Fragmento de Código Asociado |
| :--- | :--- | :--- | :--- | :--- |
| **1. Nebulosa y Soplido** | `1`, `Ratón`[cite: 2, 4] | `createSimulation.js`[cite: 2] | Modela un anillo de gas que se abre sutilmente al pasar el cursor sin destruir las partículas, palpitando en sincronía[cite: 2]. | `const falloffLinear = dMouse.div(params.breathRadius).negate().add(1.0).clamp(0.0, 1.0); force.addAssign(dirAway.mul(puff).mul(params.breathStrength));`[cite: 2] |
| **2. Separación en Cuartos** | `V`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Desata un golpe percusivo que divide simétricamente el campo de partículas en cuatro cuadrantes[cite: 2, 4]. | `const quadrant = floor(seed.x.mul(4.0)); const splitDir = vec3(cos(quadrantAngle), sin(quadrantAngle), 0.0); force.addAssign(splitDir.mul(params.nebulaKick).mul(6.0));`[cite: 2, 4] |
| **3. Ráfaga de Inercia** | `B`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Aplica un impulso direccional aleatorio que decae de forma multiplicativa para imitar fricción real[cite: 2, 4]. | `params.dustKick.value = 9.0; force.addAssign(params.dustKickDir.mul(params.dustKick));`[cite: 2, 4] |
| **4. Onda Expansiva (Bombo)** | `G`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Envía una onda de choque radial tipo pulso de audio que expande el sistema desde el centro hacia afuera[cite: 2, 4]. | `const t = params.elapsedTime.sub(params.starShockStart); const shockRadius = t.mul(10.0); force.addAssign(p.normalize().mul(band).mul(16.0));`[cite: 2, 4] |
| **5. Supernova** | `M` o `X`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Expulsa las partículas formando lóbulos polares y un cinturón ecuatorial energético[cite: 2, 4]. | `const burstDir = mix(beltDir, poleDir, poleWeight); force.addAssign(burstDir.mul(params.explosionFactor).mul(50.0));`[cite: 2, 4] |
| **6. Estrellas Y2K** | `4`, `N`[cite: 2, 4] | `createSimulation.js`[cite: 2, 4] | Reorganiza las partículas en 1 a 3 astros densos con destellos de difracción en cruz de 4 puntas[cite: 2, 4]. | `const groupId = floor(seed.x.mul(params.starCount)).clamp(0.0, 2.0); const target = mix(coreTarget, armTarget, isArm); force.addAssign(target.sub(p).mul(3.0));`[cite: 2, 4] |
| **7. Fuerzas Globales** | `F`, `C`, `T`, `Y`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Conmuta en tiempo real el seguimiento de atractor, vórtices, vientos rotatorios y repulsión universal[cite: 2, 4]. | `force.addAssign(radialDirG.mul(params.radialStrength).div(attractorDist.pow(2)).mul(params.radialEnabled));`[cite: 2, 4] |
| **8. Modo Parlante** | `S`[cite: 2, 4] | `main.js` y `createSimulation.js`[cite: 2, 4] | Simula una respuesta tipo ecualizador global que altera tamaño, color y oscilación del sistema[cite: 2, 4]. | `const speakEnv = sin(params.elapsedTime.mul(8.0).add(seed.x.mul(30.0))); force.addAssign(p.normalize().mul(speakEnv).mul(params.speakerModeEnabled).mul(1.6));`[cite: 2, 4] |

[LINK AL REPOSITORIO](https://github.com/Fentomylo/FUERZAS.git)

## Ficha de fuerzas:

<img width="1051" height="197" alt="image" src="https://github.com/user-attachments/assets/11852763-d573-48f3-8d63-55309a1bdbfe" />

Segun gemini jaja, Básicamente, la aceleración de cada una de las 131.072 partículas no sale de la nada. En el código (createSimulation.js), la tarjeta de video (GPU) calcula una sumatoria de fuerzas. Es como en la clase de física cuando sumamos vectores:  

Fuerza Total = Fuerza Radial + Fuerza de Vórtice + Fuerza de Viento + Drag (Fricción)

### LAS FUERZOVICH Q HAY

| Fuerza o regla | Modelo mínimo | Qué deberia predecir |
| :--- | :--- | :--- |
| **Viento o fuerza constante** | $F_w = c$ | La aceleración conserva la dirección de $c$; con velocidad inicial cero, la velocidad crece en esa dirección. |
| **Radial suavizada** | $d = \max(\|r\|, s)$<br>$F_r = \hat{r} k / d^2$ | Con $k > 0$, la partícula tiende al atractor; con $k < 0$, la tendencia se invierte. $s$ evita una singularidad cerca del atractor. |
| **Vórtice** | $F_t = \hat{z} \times \hat{r} k_t$ | Aparece una componente tangencial alrededor del eje; no es una trayectoria circular prescrita. |
| **Drag lineal** | $F_d = -c_d v$ | La fuerza se opone a la velocidad y disipa movimiento. |
| **Integración Euler semiimplícita** | $v_{t+\Delta t} = v_t + F\Delta t$<br>$p_{t+\Delta t} = p_t + v_{t+\Delta t}\Delta t$ | La fuerza cambia primero la velocidad y esa velocidad actualizada cambia la posición. |
### DECISIONES DE DISEÑO, PREDICCIONES Y PARAMETROS

Bueno, la verdad el tema no me gusto esta muy mid, pero en si a mi me gusta mucho las estrellas, y escuchando el tema como tal, me senti como viajando por las estrellas por asi decirlo, entonces yo decidi conceptualizar la vida de una estrella con esta canción, 
desde su nacimiento hasta su muerte, donde la idea es presentar los siguientes escenarios usando pues las fuerzas, pero como tal, estos son:

#### ESCENARIO 1: NEBULOSA

La idea es q al inicio se vea una nebulosa, asi quieta, ya cuando este la interacción humana que en este caso va a ser con el raton, donde al mover el puntero sobre la nube de gas, 
el ratón no la "atrae" como un imán ni la "destruye" como una bomba. Funciona como una burbuja de aire o soplido sutil: las partículas que están cerca de tu mano se apartan y se deslizan suavemente hacia los lados, dividiendo la nebulosa en filamentos o abriendo un camino a tu paso.

En cuanto pasas el puntero y lo alejas, las partículas que se apartaron no siguen volando infinitamente; van perdiendo velocidad hasta quedarse flotando tranquilamente a los lados. lo que quiero es que mientras este la interaccion humana, la nebulosa este como palpitando, como si estuviera en ritmo o como un corazon, mientras se va rompiendo en pequeños trozos para pasar al siguiente escenario. (esa es la idea principal y lo que espero que pase)

#### ESCENARIO 2: POLVO ESTELAR

La nebulosa que se rompió en trozos pequeños empieza a perder su forma definida.las partículas se convierten en motas y corrientes de polvo espacial que se desplazan y retuercen en filamentos por todo el lienzo, reaccionando a la dirección de tu mano. Esta es mas sencillita

#### ESCENARIO 3: JUNTE Y EXPLOSION 

Basicamente, que este polvo estelar se este atrayendo formando lo que va a ser como un huevo, donde el centro al centrarse tanto de particulas, pueda explotar con otro boton, para darle paso a la siguiente escena que son las estrellas, estos 3 escenarios son el nacimiento de la estrella

#### ESCENARIO 4: ESTRELLAS

Tras la gran explosión del drop, nacen las estrellas grandes Y2K que ocupan el espacio visual. A partir de este momento y durante la mayor parte de la canción, el sistema pasa a un modo de conducción expresiva en vivo. No hay un control directo de trayectoria por cursor como en la nebulosa, sino que utilizas botones/teclas mapeadas como un instrumento para modificar las fuerzas globales del universo en tiempo real: alternar entre repulsión entre partículas, patrones de seguimiento al atractor, corrientes de viento direccional o vórtices abiertos. Las estrellas reaccionan dinámicamente a estos cambios de fuerza, deformando sus trayectorias mientras flotan libres.


#### ESCENARIO 5: JUNTE DE LA ESTRELLA A UNA SOLA

Las partículas son comprimidas de forma extrema en el origen. La pantalla se limpia de las estrellas dispersas y en el centro se forma una única Estrella Gigante supermasiva, hiperdensa y brillante que gira e irradia luz.

#### ESCENARIO 6: MUERTE DE LA ESTRELLA Y VUELTA A LA INICIAL

En la última nota seca o acorde final de LesAlpx, la Estrella Gigante colapsada se rompe en una última onda expansiva y vuelve a nacer una nebulosa para volver al inicio. fin

#### REFERENCIAS

<img width="740" height="740" alt="image" src="https://github.com/user-attachments/assets/6d852aea-19a8-46db-878c-a88579f6ed87" />

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/c4ec2adb-5f09-4f09-a93e-2221cef10cdb" />

<img width="1900" height="2217" alt="image" src="https://github.com/user-attachments/assets/51247da2-2181-44fe-bbc5-37a77381d4d1" />

<img width="1280" height="945" alt="image" src="https://github.com/user-attachments/assets/ca36d623-577d-4585-86b8-3842076f5f9b" />

<img width="330" height="315" alt="image" src="https://github.com/user-attachments/assets/c1a972ab-b55c-494f-b415-42c5e2c8ec77" />


por mas que lo intente, esta fue la mejor version que salio, de resto, nada. no pude mas porq me quede sin tiempo


## Registro de pruebas:

Nebulosa
<img width="1372" height="924" alt="image" src="https://github.com/user-attachments/assets/ceb7398c-4c04-4259-ad57-0e58a6e91222" />


Polvo estelar
<img width="1376" height="1221" alt="image" src="https://github.com/user-attachments/assets/c037a785-fbe4-4e13-9a6f-5e910b6312aa" />

Acumulacion polvo

<img width="1442" height="1073" alt="image" src="https://github.com/user-attachments/assets/0271875e-7fc2-4cbc-be5c-f2f7d5eb6c49" />

Estrellas

<img width="1432" height="880" alt="image" src="https://github.com/user-attachments/assets/e52cb0e1-8a37-4061-b4ed-c0b2887c3b5c" />

Sol solecito

<img width="785" height="886" alt="image" src="https://github.com/user-attachments/assets/bb96b593-6a40-469d-afe7-10734670c20c" />

Combinacion de fuerzas para la explosion

<img width="1919" height="1160" alt="image" src="https://github.com/user-attachments/assets/8b3c8d81-1f31-4aed-8307-12112682ab8d" />

## Score visual

Ps como mencione, la idea es usar los drops de la cancion en base a los escenarios que plantee con la herramienta visual, la idea es que esta herramienta cada persona pueda hacer una interpretacion diferente, solo que yo al escuchar eso, senti esto de la estrella y lo reprenseto asi.

* el inicio va a ser usar la nebulosa y sus variaciones 0:00 a 0:30 segundos

* transicion a un drop donde aparece polvo estelar, como si la nebulosa hubiera explotado, 0:30 a 0:56}
  
* Aqui usaremos la acumulacion de energia para ir generan una explosion 0:56 al 1:07

* La explosion inmediatamente dura como 5 segundos, de ahi pasamos a las estrellas que van a ser casi toda la cancion, la idea aqui es que hasta el minuto 3:15, se pueda usar lo que ya se uso para la coreografia del nacimiento de una estrella, que sea locura.
  
* a partir de ahi, el sol se acumula y se usan las variaciones, para explotar al final y crear una secuencia mezclando todo lo anterior.
  
* Finaliza con la nebulosa de nuevo.

Asi mas organizao

| Tiempo | Sección | Descripción Visual y Comportamiento del Instrumento |
| :--- | :--- | :--- |
| **0:00 - 0:30** | Inicio | Nebulosa estática y sus variaciones interactivas (soplido con el ratón y palpitación manual con la barra espaciadora). |
| **0:30 - 0:56** | Transición al Drop | Aparición de polvo estelar simulando la dispersión del gas tras la primera fase. |
| **0:56 - 1:07** | Acumulación | Concentración progresiva de energía hacia el centro para generar tensión de cara a la siguiente fase. |
| **1:07 - 3:15** | Estrellas y Coreografía | Explosión de 5 segundos seguida de un campo estelar caótico y dinámico que representa el nacimiento de una estrella. |
| **3:15 - Final** | Clímax y Cierre | Acumulación de masa solar, explosión final mezclando todos los estados anteriores y retorno a la calma con la nebulosa. |<

Igual la idea es que esto aparezca en orden, y ya cuando avance, puedo usar la misma herramienta anterior, hasta llegar a la ultima que las puedo usar todas. La idea es esto para 
que el instrumento sea mas divertido

## Bitácora de IA:

<img width="1238" height="840" alt="image" src="https://github.com/user-attachments/assets/1d57b8a3-f3fe-4424-af65-a9f388247b4e" />

<img width="1101" height="637" alt="image" src="https://github.com/user-attachments/assets/dbbb7598-72bd-4582-b001-ccb7ec0513ab" />

<img width="1139" height="963" alt="image" src="https://github.com/user-attachments/assets/4318cf92-9c06-4929-a691-ea34287ab451" />

<img width="936" height="446" alt="image" src="https://github.com/user-attachments/assets/78f43325-1e6b-4827-b2eb-18c68a57222b" />

<img width="857" height="553" alt="image" src="https://github.com/user-attachments/assets/82f397db-10cf-4477-83e8-c51fd6246028" />

<img width="1083" height="872" alt="image" src="https://github.com/user-attachments/assets/87d992ba-ee07-436f-81ec-3d580fd27825" />


## Autoevaluación ponderada

| Criterio | Peso | Qué debe demostrar la evidencia | Valoración (Puntos) |
| :--- | :---: | :--- | :---: |
| Trazabilidad y comprensión del sistema | 25 | Puedo señalar y explicar estado, fuerzas, integración, render y controles; además puedo ubicar qué partes produjo o modificó la IA. | 20 |
| Verificación del algoritmo de fuerzas | 25 | Estudié en detalle el proyecto y aunque no comprenda toda la sintaxis, puedo identificar su arquitectura, sus partes, puedo aislar una fuerza central, formular una predicción, la ejecuté ya analicé, comparé el resultado, cambié deliberadamente un signo o parámetro y expliqué la diferencia. | 20 |
| Diseño de fuerzas e intención | 20 | Las fuerzas y sus parámetros hacen perceptible una intención; el comportamiento surge de la dinámica y no de trayectorias previamente dibujadas. | 16 |
| Instrumento, score e interpretación | 15 | El score conecta la escucha con decisiones; escogí pocos controles expresivos y puedo conducir el sistema en vivo sin que el audio lo controle automáticamente. | 11 |
| Experimentación y criterio frente a la IA | 10 | Comparé alternativas, registré hallazgos y descartes, corregí propuestas de IA y puedo justificar por qué conservé la versión presentada. | 8 |
| Entrega técnica y documentación | 5 | la URL pública abre; la bitácora permite verificar el proceso. | 5 |
| **Total Puntos** | **100** | | **80** |

4 porque pudo haber sido mejor visualmente y en funcionamiento, pero son la 1 am y ya no m da pa mas

<img width="539" height="371" alt="image" src="https://github.com/user-attachments/assets/add8ea50-e185-4acf-98d0-225dcaba2e78" />
