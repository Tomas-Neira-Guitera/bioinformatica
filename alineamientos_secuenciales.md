# Alineamientos secuenciales - Respuestas

Tomás Neira Guitera

## PARA PENSAR: ¿Qué información se puede extraer de la comparación de secuencias?

Comparando secuencias se puede sacar información sobre la historia evolutiva de los organismos (si dos secuencias son muy parecidas, probablemente vengan de un ancestro común) y también sobre la función: si una proteína nueva se parece mucho a una ya conocida, es probable que cumpla una función similar. En una comparación esperaría ver tramos donde las secuencias coinciden letra por letra (posiciones conservadas) y otros tramos donde difieren o hay huecos (gaps), que marcan los lugares donde hubo mutaciones, inserciones o deleciones a lo largo del tiempo.

## PARA PENSAR: ¿Por qué conviene comparar proteínas para evaluar relaciones evolutivas lejanas?

Porque las proteínas acumulan cambios más despacio que el ADN, ya que están bajo presión selectiva: cambiar un aminoácido puede afectar la función, entonces esos cambios "sobreviven" menos. Además el alfabeto de aminoácidos tiene 20 letras posibles en vez de las 4 del ADN, así que una coincidencia entre dos secuencias de proteínas es mucho menos probable que sea pura casualidad. Por eso, cuando el parentesco evolutivo es muy lejano, comparar proteínas conserva más señal que comparar ADN.

## Desafío I

Alineando "BANANA" y "MANZANA" en la tabla interactiva, lo primero que se nota es que no hay una sola forma de alinearlas: como tienen distinta longitud (6 contra 7 letras) hace falta meter al menos un gap, y ese gap se puede ubicar en distintos lugares. Por ejemplo:

```
BAN-ANA
MANZANA
```

acá quedan alineadas 5 letras iguales (A, N, A, N, A) y solo falla la B contra la M. En cambio si se pone el gap en otro lado el resultado empeora bastante, quedan menos coincidencias.

Entonces sí, hay alineamientos mejores que otros: el mejor es el que pone el gap justo donde está la letra que no tiene pareja (la Z de MANZANA), porque así el resto de las secuencias queda perfectamente alineado. La idea de "mejor alineamiento" no es cualquier forma de acomodar una palabra arriba de la otra, sino la que maximiza las coincidencias y minimiza la cantidad de gaps y de letras que no coinciden.

## Desafío II

Probando "ANA" y "ANANA" en la tabla, los valores de identidad que aparecen no son todos iguales, aunque las dos palabras sean las mismas en todos los intentos. Esto pasa porque el valor de identidad depende de cómo se elija calcularlo, no solo de cuántas letras coinciden. Algunas formas posibles:

- coincidencias sobre el largo de la secuencia más larga,
- coincidencias sobre el largo de la secuencia más corta,
- coincidencias sobre el total de posiciones alineadas (contando los gaps).

Cada una da un número distinto para el mismo alineamiento. Y no todas son igual de válidas en biología: dividir por la secuencia más corta puede inflar el porcentaje de identidad y esconder los gaps, dando una idea de parecido más alta de la real. Lo más razonable es calcular la identidad sobre el largo total del alineamiento, para que los gaps también cuenten.

## Desafío III

Cambiando la penalización de los gaps en la tabla interactiva se ve que, cuando la penalización es alta, el alineamiento "prefiere" evitar gaps aunque eso signifique dejar más letras sin coincidir (mismatches). Cuando la penalización es baja, pasa lo contrario: se abren más gaps para lograr más coincidencias.

Esto tiene sentido biológico porque las inserciones y deleciones son eventos menos frecuentes que una simple sustitución de una base por otra, entonces penalizarlas más fuerte refleja mejor lo que pasa en la naturaleza. El problema es que penalizar demasiado un gap puede terminar forzando un alineamiento con muchas letras que no coinciden, que biológicamente tiene menos sentido que simplemente aceptar el gap.

Una forma de penalización que no está en el ejemplo es la penalización por apertura y extensión: se cobra un costo alto por abrir el primer gap, pero un costo menor por cada posición adicional dentro del mismo gap (porque una inserción/deleción larga suele ser un solo evento mutacional, no varios).

## PARA PENSAR: gaps en secuencias de ácidos nucleicos

Abrir un gap en una secuencia de ADN tiene una consecuencia extra que no pasa con palabras comunes: corre el marco de lectura (frameshift). Si el gap no es múltiplo de 3, todos los codones que vienen después quedan desplazados y cambia por completo la proteína que se traduciría a partir de ahí. Si el gap sí es múltiplo de 3, se insertan o se pierden aminoácidos completos, pero el resto de la secuencia sigue traduciéndose bien.

## Desafío IV

Probando distintos alineamientos de secuencias nucleotídicas en la tabla y viendo sus traducciones, se confirma lo anterior: un gap que no es múltiplo de 3 rompe la traducción de ahí en adelante, sin importar en qué posición del codón caiga exactamente (primera, segunda o tercera). La diferencia es sutil: un gap en la tercera posición del codón (la posición "wobble") puede, a veces, cambiar a un aminoácido sinónimo gracias a la degeneración del código genético, pero eso no evita el frameshift del resto de la secuencia.

Para ponderar esto a la hora de evaluar el parecido entre dos secuencias de ADN, conviene penalizar los gaps bastante más fuerte que un simple mismatch, porque sus consecuencias funcionales son mucho más graves. Una alternativa más precisa todavía es comparar directamente a nivel de la proteína traducida, ya que ahí se ve si el cambio realmente afectó la función o no.

## Desafío V

Pasos para alinear dos secuencias cortas usando una matriz de puntuación (con valores distintos para match, mismatch y gap):

```
1. Definir los puntajes de match, mismatch y gap.
2. Armar una matriz vacía de (largo secuencia 1 + 1) x (largo secuencia 2 + 1).
3. Llenar la primera fila y la primera columna acumulando la penalización de gap.
4. Para cada celda que falta:
     - calcular 3 valores posibles: diagonal + match/mismatch, arriba + gap, izquierda + gap
     - guardar el mayor de los tres como score de la celda
     - guardar también de qué celda vino ese máximo (para el traceback)
5. Una vez llena toda la matriz, hacer el traceback desde la última celda hasta la primera,
   siguiendo las flechas guardadas: diagonal = coincidencia o cambio, arriba/izquierda = gap.
6. Leer el alineamiento final y su puntaje total.
```

## PARA PENSAR: ¿en qué consiste la programación dinámica?

La programación dinámica sirve para resolver problemas grandes dividiéndolos en subproblemas más chicos que se repiten, resolviendo cada subproblema una sola vez y guardando el resultado para reutilizarlo después, en vez de recalcularlo cada vez. Es útil en este caso porque calcular el mejor alineamiento posible "a mano" probando todas las combinaciones sería muchísimo más lento (fuerza bruta), mientras que con programación dinámica se construye la matriz celda por celda usando resultados ya calculados, y al final se garantiza encontrar el alineamiento óptimo.

## Desafío VI

Usando la herramienta de Freiburg y probando distintos gap penalties, se ve que cada valor de la matriz sale de comparar tres posibilidades: el valor de la celda diagonal (sumándole el puntaje de match o mismatch según corresponda), el valor de la celda de arriba (sumándole la penalización de gap) y el valor de la celda de la izquierda (sumándole también la penalización de gap). El número final que queda en la celda es el mayor de esos tres. Cuanto más alta la penalización de gap, más "le cuesta" a la matriz moverse hacia arriba o hacia la izquierda, y el camino óptimo tiende a quedarse en la diagonal.

## PARA PENSAR: alineamientos de a pares vs múltiples

El alineamiento de a pares sirve para comparar dos secuencias puntuales, por ejemplo para ver si dos genes de distintas especies son parecidos. El alineamiento múltiple sirve cuando se quiere comparar varias secuencias a la vez, por ejemplo para encontrar una región conservada entre muchas especies distintas o para armar un árbol evolutivo.

La limitación del alineamiento de a pares es que no muestra el panorama completo si lo que se busca es una tendencia dentro de una familia de secuencias. La limitación del alineamiento múltiple es que es mucho más costoso computacionalmente, y agregar una secuencia muy distinta al resto puede distorsionar todo el alineamiento.

## PARA PENSAR: programas derivados de BLAST

Entrando al NCBI aparecen varias variantes de BLAST, cada una pensada para un tipo distinto de comparación:

- **blastp**: compara una proteína contra una base de datos de proteínas. Sirve para encontrar proteínas parecidas o predecir la función de una proteína nueva.
- **blastn**: compara una secuencia de ADN/ARN contra una base de datos de nucleótidos. Sirve para ubicar un gen dentro de un genoma o buscar genes parecidos en otras especies.
- **blastx**: toma una secuencia de ADN, la traduce en los 6 marcos de lectura posibles y la compara contra una base de proteínas. Sirve cuando se tiene un fragmento de ADN sin anotar y se quiere saber qué proteína podría codificar.
- **tblastn**: toma una proteína y la compara contra una base de nucleótidos traducida en los 6 marcos. Sirve para encontrar el gen que codifica una proteína conocida dentro de un genoma todavía no anotado.
- **tblastx**: traduce ambas secuencias (query y base de datos) en los 6 marcos y las compara. Sirve para encontrar relaciones muy lejanas entre secuencias de ADN que de otra forma no se podrían detectar.

## Desafío VII

Corriendo BLASTp de la secuencia (133 aminoácidos) con 20000 hits, e-value de 100 y filtrando por una cobertura mínima de 70%, el resultado principal es la proteína priónica (prion protein) humana, que también aparece en otros mamíferos con muy alta identidad.

- **E-value vs % identidad**: están relacionados de forma inversa. Mientras más alto es el porcentaje de identidad entre la secuencia buscada y un hit, más bajo (mejor) es el E-value, porque es menos probable que tanto parecido sea pura casualidad.
- **Score vs % identidad**: van de la mano. El score suma puntos por cada posición que coincide (y resta por las que no), entonces a mayor identidad, mayor score.
- **Score vs E-value**: también se relacionan de forma inversa, y es la relación más fuerte de las tres: un score alto casi siempre significa un E-value muy bajo, porque matemáticamente el E-value se calcula justamente a partir del score.

En los resultados se nota claramente esta tendencia: los hits de priones de otros mamíferos (identidad arriba del 85-90%) tienen E-value muy bajo y score alto, mientras que los hits que son puro ruido estadístico (identidad baja, del orden del 20-50%) tienen E-value alto (cercano al límite de 100 que se puso como filtro) y score bajo.

## Desafío VIII

Repitiendo la búsqueda con la mitad de la secuencia (66 aminoácidos) y con un cuarto (33 aminoácidos), se ve que acortar la secuencia problema empeora mucho la calidad estadística de los resultados, aunque el porcentaje de identidad de los mejores hits se mantenga parecido:

- con la secuencia completa el mejor E-value es extremadamente bajo (homología segura),
- con la mitad el mejor E-value sube varios órdenes de magnitud,
- con un cuarto de secuencia el E-value vuelve a subir mucho más, y aparecen muchos más hits de baja calidad (ruido) porque una secuencia tan corta puede "calzar" por casualidad en muchos lugares de la base de datos.

La conclusión es que el largo de la secuencia es clave para la confiabilidad estadística de un BLAST: una secuencia corta, aunque tenga buen porcentaje de identidad con algo, da mucha menos certeza de que se trate de una relación evolutiva real y no de una coincidencia al azar.

## Desafío IX

Buscando con BLAST la secuencia de 262 aminoácidos, el resultado es la proteína **acyl-ACP–UDP-N-acetylglucosamine O-acyltransferasa**, conocida como **LpxA**.

- **Función**: LpxA cataliza el primer paso de la biosíntesis del lípido A, que es un componente clave del lipopolisacárido (LPS) de la membrana externa de las bacterias Gram-negativas. Específicamente transfiere una cadena de ácido graso desde la proteína transportadora de acilo (ACP) hacia el UDP-N-acetilglucosamina.
- **Grupo taxonómico**: pertenece a bacterias Gram-negativas, principalmente de la familia Enterobacteriaceae (como *Escherichia coli*), dentro del grupo Pseudomonadota.
- **Cantidad de secuencias similares a un nivel de significancia adecuado**: usando un criterio estricto de E-value (bien por debajo de 1), aparecen del orden de cientos de secuencias similares, la mayoría ortólogos de LpxA en otras bacterias Gram-negativas, lo que tiene sentido porque es una enzima bacteriana muy conservada y necesaria para armar la membrana externa.

## Desafío X

Corriendo la misma secuencia de LpxA contra la base de datos PDB (en vez de la base general nr) no se obtienen los mismos resultados: siguen apareciendo hits de LpxA de *E. coli*, pero muchos menos en cantidad.

- **¿Se obtienen los mismos resultados?** No. El primer hit identifica la misma proteína (LpxA de *E. coli*) pero la lista de resultados es mucho más corta.
- **¿Qué tipo de hits se recuperan?** Se recuperan estructuras tridimensionales resueltas experimentalmente, identificadas con códigos PDB de 4 caracteres, cada una con su resolución y el método con el que se obtuvo (por ejemplo rayos X).
- **¿Cuándo conviene usar este modo de búsqueda?** Cuando lo que se necesita es la estructura 3D de la proteína, por ejemplo para hacer modelado por homología, estudiar el sitio activo de una enzima o analizar su plegamiento, y no simplemente identificar la secuencia o ver en cuántos organismos aparece.
