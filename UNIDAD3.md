# FUERZOVICH

## Instrumento funcional y publicado:

## Mapa del sistema:


## Ficha de fuerzas:

<img width="1051" height="197" alt="image" src="https://github.com/user-attachments/assets/11852763-d573-48f3-8d63-55309a1bdbfe" />

Segun gemini jaja, Básicamente, la aceleración de cada una de las 131.072 partículas no sale de la nada. En el código (createSimulation.js), la tarjeta de video (GPU) calcula una sumatoria de fuerzas. Es como en la clase de física cuando sumamos vectores:  

Fuerza Total = Fuerza Radial + Fuerza de Vórtice + Fuerza de Viento + Drag (Fricción)

### LAS FUERZOVICH Q HAY

#### FUERZA RADIAL

Actúa sobre la línea recta que une la posición de la partícula con el centro del atractor Vec (r) = vec(p_atractor) - vec(p_partícula). Apunta hacia el centro si el valor es positivo (atracción) o se invierte hacia afuera si es negativo (repulsión).

* vortexStrength y vortexEnabled son sus parametros

#### FUERZA DE VIENTO

Vector de fuerza constante aplicado de manera uniforme en el espacio tridimensional.

* wind vec(v_wind) y windEnabled son sus parametros

#### FUERZA DE VORTICE

Actúa en dirección perpendicular (tangencial) al vector radial respecto al eje Z(z x r). Otorga movimiento de giro orbital alrededor del atractor.  

* vortexStrength y vortexEnabled son sus parametros

#### DRAG LINEAL (Fricción / Control de Inercia

Oposición directa y proporcional al vector de velocidad actual de cada partícula

* dragCoefficient y dragEnabled Son sus parametros

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

## Registro de pruebas:

## Score visual

## Bitácora de IA:

## Autoevaluación ponderada
