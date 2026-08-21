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

En cuanto pasas el puntero y lo alejas, las partículas que se apartaron no siguen volando infinitamente; van perdiendo velocidad hasta quedarse flotando tranquilamente a los lados. (esa es la idea principal y lo que espero que pase)



## Registro de pruebas:

## Score visual

## Bitácora de IA:

## Autoevaluación ponderada
