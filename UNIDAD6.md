# UNIDAD 6: CANCION INSTRUENTO

[LINK CANCION](https://fentomylo.github.io/videoclip/)
[LINK REPO](https://github.com/Fentomylo/videoclip.git)

CANCION UTILIZADA: CIRUGIA DE DILLOM

<img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/097016d3-0c7f-4ae6-aaac-6cdcb2faa83e" />

## SOBRE LA CANCION

Esta cancion proviene de por cesarea, el disco mas oscuro de dillom el cual trata de un chico que se enamora de una chica pero esta ya tiene novio, q es su amigo
Donde el protagonista esta loco y canta ciertas cosas q pueden ser molestas

Cirugia es la cancion mas exitosa del disco, ya que suena bastante bien y tiene la letra mas suave a comparacion de las otras, en la cual el protagonista del 
disco cuenta como ama a esa chica, y que quiere coserse con ella en una cirugia para nunca perderla.

Decidi hacerla porq, ya esta cancion tiene un concepto que podia usar ocn los visuales, q son las cirugias vistas desde un modo mas turbio por casi decirlo

## QUE QUERIA EXPRESAR

Quería que se sintiera como una operaciion donde se pdiera abrir, ver lo que hay por dentro, sangrar, cicatrizar y al final que algo vuelva a crecer. Ya sea 
locura o algo asi, por eso cogi partes del cuerpo para hacer esta parte, como huesos, nervios, una hemorragia, venas y un corazon de fondo, mezclandolo con un 
cambio de color, o mejor dicho, una inversa de estos, para usar en las partes mas turbias de la cancion, para asi demostrar la locura del protagonista, aunque
en la parte mas tranquila de la cancion, puse flores para representar la calma y tranquilidad con la que dice cosas turbias en esa parte de la canción.

se usaron los algoritmos donde 

* Steering behaviors: seek, arrive, flee y seguir a un líder. Los uso en todos los modos.
* Flocking: cohesión, alineación y separación. Está en el modo 3 (hemorragia).
* Flow fields: son como "corrientes de viento" invisibles. Los uso en hueso, hemorragia, sangre, corazón y flores.
* Physarum: las venas (tecla 5).

Lo único que no es un algoritmo es la decoración: el grano de película, la viñeta y el fondo de niebla con árboles del modo Flores. Eso es solo para que se vea bonito, no tiene agentes.

## SOBRE LOS AGENTES


Todos los agentes hacen lo mismo en cada frame: perciben → calculan una fuerza → se mueven. Así funciona cada modo:

* Hueso Cada hueso tiene un líder que sigue un flow field. Los demás agentes lo siguen (arrive + alinearse con su velocidad). El mundo es "toroidal": si sales por un lado entras por el otro.

* Nervios:  Cada agente tiene un puesto en un árbol de nervios y va hacia él (arrive). Cuando doy un latido sale un impulso de luz desde la raíz hasta las puntas.

* Hemorragia:  Aquí sí hay flocking de verdad. Cada agente mira a los vecinos que estén cerca (radio de percepción) y calcula cohesión (juntarse), alineación (ir en la misma dirección) y separación (no chocar). Además sigue un flow field, el bisturí lo repele y lo hace girar como un remolino.

* Cicatriz:  La herida son una línea y 6 puntadas hechas de partículas. Cuando el bisturí se acerca, los "labios" de la herida se abren rápido y se cierran despacio. Si el bisturí está encima, nace sangre que cae siguiendo un flow field con gravedad.

* Venas / Physarum:  Cada agente tiene 3 sensores (izquierda, frente, derecha), huele el rastro que dejaron los demás, gira hacia donde hay más y deja su propio rastro. El rastro se difunde y se evapora, y de ahí salen las venas solas. El bisturí las atrae o las espanta y con cada latido sale una onda desde el corazón.

* Flores:  Cada flor tiene un ciclo de más o menos 55 segundos: brota el tallo, salen las hojas, el capullo se abre girando, se deshace y vuelve a nacer. Los agentes van hacia su puesto (que va creciendo), el viento los mece y el bisturí los empuja.

* Corazón: Cada agente va hacia su puesto en el dibujo del corazón. El latido es una fuerza que los empuja hacia afuera (flee) y el arrive los devuelve, así que el rebote sale solo.

En cuanto a los controles

Los que más uso al tocar:

* Mouse / WASD (bisturí): modifica lo que perciben los agentes. Abre la cicatriz, empuja el corazón y las flores, atrae o repele partículas.
* Espacio (latido): modifica el entorno. Manda una onda por las venas, un impulso por los nervios e infla el corazón.
* G / H (mantener): modifican las reglas. G hace crecer las venas (y acelera las flores), H las corta.
* 1, 2, 3, 4, 5, 6 y T: cambian de modo, o sea qué parte del cuerpo se ve.
* Q: cambia la velocidad (×1, ×1.5, ×2, ×3, ×0.5).

Extras para la presentación: Z / X / C muestran frases de la canción en pantalla, V invierte los colores, M pone la música, F es pantalla completa, P esconde el panel y R reinicia.

El panel tiene 4 sliders principales (fuerza del bisturí, corte/giro, temblor del flow field y radio del bisturí) y una parte "Avanzado" escondida con ajustes finos que no uso mientras toco.

## SCORE VISUAL

* intro: corazon solo
* verso 1: hemorragia
* guitarra entre versos: venas
* verso 2: huesos
* coro: modo turbio, modo color inverso mientras este corre, latidos y las frases q se dan con Z X C
* Verso 3: corazon solo con el modo 5
* puente: flores creciendo
* coro final: modo turbio, modo color inverso mientras este corre, latidos y las frases q se dan con Z X C

La idea es que los latidos del corazon se usen commo si interpretaran las baterias, q cada uno siga el ritmo, eso si, todo esto es controlado por el instrumento y la persona, no hay ni interpretacion
ni nada de eso

## AUTOEVALUACION

* Cumplimiento del encargo: mi instrumento utiliza tecnología web, funciona en tiempo real y permite interpretar la pieza musical elegida. 
* Comprensión y verificación: puedo explicar y defender cómo está construido el sistema, qué perciben los agentes y cómo calculan sus acciones. Puedo predecir y verificar los cambios al modificar un parámetro.
* Diseño e intención: puedo justificar la selección y combinación de comportamientos y relacionarlos con mi interpretación musical.
* Interpretación humana: mi score y mis controles permiten conducir el sistema en vivo y responder a su comportamiento.

1. si funciona, asi q por eso en esta me pongo 25 puntos
2. la verdad, hubo un momento en la q la ia me cambio ciertas cosas, por lo q no se defender algunas, pero si su ayoria, 20 puntos
3. si, esto si perfectamente, es lo q yo interprete. 25 puntos
4. si, ps aunque se pde tocar como quiera, pero la idea es como en el score. 25 puntos

95 puntos.

4.75.
