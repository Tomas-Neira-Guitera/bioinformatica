# Biomoléculas - Respuestas

Tomás Neira Guitera

## Desafío I

¿Podrías buscar un ejemplo de macromoléculas que almacenen información sobre la identidad de un organismo?

El ADN (ácido desoxirribonucleico). Es la molécula que guarda toda la información genética de un organismo: ahí está "escrito" qué proteínas puede fabricar y, en gran parte, cómo va a ser ese organismo.

## Desafío II

Proponé una forma de expresar la información contenida en la estructura primaria de las proteínas usando tipos de datos de los lenguajes de programación que conocés.

Lo representaría como una lista ordenada de aminoácidos (o un string, usando el código de una letra de cada uno). Tiene sentido porque la estructura primaria es justamente eso: el orden en que están encadenados los aminoácidos, nada más. No hace falta guardar posiciones ni nada 3D todavía.

## Desafío III

¿En qué tipo de datos podrías expresar la información de la estructura terciaria proteica?

Acá un string ya no alcanza, porque la estructura terciaria es la forma que toma la proteína en el espacio, no solo el orden de los aminoácidos. Para eso usaría una lista de objetos (o diccionarios), donde cada uno representa un átomo (o un aminoácido) con sus coordenadas `x`, `y`, `z`. También podría pensarse como un grafo, donde cada átomo es un nodo y las conexiones (enlaces, cercanía) son las aristas.

## Desafío IV

Rosalind Franklin es una científica muy relevante, que tuvo menos reconocimiento del merecido. ¿Cuáles fueron sus contribuciones en este campo? ¿Qué nos cuenta su historia acerca del mundo de la ciencia?

**¿Cuáles fueron sus contribuciones?**

Rosalind Franklin fue la científica que obtuvo la evidencia experimental clave para descubrir la estructura del ADN: la célebre Fotografía 51 (1952), una imagen de rayos X que revelaba su forma helicoidal con una precisión sin precedentes.

Sin su conocimiento, Maurice Wilkins mostró esa imagen a Watson y Crick, quienes la usaron para publicar el modelo de doble hélice en 1953. En 1962 recibieron el Nobel. Franklin había muerto en 1958, a los 37 años, sin reconocimiento.

**¿Qué nos cuenta su historia acerca del mundo de la ciencia?**

El crédito científico no siempre va a quien hace el trabajo, sino a quien publica primero. El sexismo estructural del mundo académico invisibilizó activamente a mujeres capaces: a Franklin ni siquiera la dejaban entrar a ciertos espacios del laboratorio por ser mujer. Y las reglas del Nobel (no se entrega post mortem, máximo 3 personas) hacen posible borrar contribuciones enteras, aunque hayan sido decisivas.

## PARA PENSAR

¿Cuántas proteínas puede sintetizar un organismo? ¿De qué depende la cantidad y la característica de las proteínas que puede sintetizar un organismo?

Depende del organismo: cada especie (y cada individuo) tiene su propio set de genes. Y dentro de eso, depende de la estructura primaria de cada proteína, porque es la secuencia de aminoácidos la que termina determinando cómo se pliega la proteína y para qué sirve.

## Desafío VI

¿Qué hace distintos a dos individuos de una especie? Proponé una forma de corroborar tu respuesta realizando un diagrama de un posible método computacional para dicho fin.

Lo que hace distintos a dos individuos de la misma especie son las diferencias en su secuencia de ADN. Aunque comparten casi todo el genoma, hay posiciones puntuales donde cambia una base (o se repite una zona, o falta un pedazo), y esas diferencias son las que generan variación entre individuos.

Para corroborarlo, se me ocurre algo simple: generar un string (hash) a partir de la secuencia de ADN de cada individuo y comparar esos dos hashes. Si son iguales, es porque la secuencia es idéntica (mismo individuo o clon); si son distintos, hay variación entre ellos.

```
[ADN individuo 1] --> función hash --> [hash 1]
[ADN individuo 2] --> función hash --> [hash 2]

hash 1 == hash 2  -->  misma secuencia
hash 1 != hash 2  -->  secuencias distintas
```
