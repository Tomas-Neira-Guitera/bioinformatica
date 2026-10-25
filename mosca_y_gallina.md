# ¿En qué se parecen una mosca y una gallina? - Respuestas

Tomás Neira Guitera

## Tabla de especies y secuencias

| Secuencia | Nombre taxonómico | Nombre común |
|---|---|---|
| NP_061820.1 | Homo sapiens | Humano |
| NP_001072946.1 | Gallus gallus | Gallina |
| NP_001065289.1 | Pan troglodytes | Chimpancé |
| NP_001157486.1 | Equus caballus | Caballo |
| NP_001183974.1 | Canis lupus familiaris | Perro |
| AEP27192.1 | Gorilla gorilla | Gorila occidental |
| XP_024245566.1 | Oncorhynchus tshawytscha | Salmón real |
| NP_001086101.1 | Xenopus laevis | Rana de uñas africanas |
| NP_477164.1 | Drosophila melanogaster | Mosca de la fruta |

## ¿Cuán sencillo será alinear dos o más secuencias a mano? ¿Cuánto influirán el número de secuencias a alinear, su longitud, y la similitud entre ellas?

Nada sencillo, sobre todo a medida que aumenta la cantidad de secuencias: cada secuencia nueva que se agrega multiplica la cantidad de comparaciones que hay que hacer a la vez. La longitud también complica las cosas, porque hay que decidir dónde poner cada gap en secuencias largas sin perder de vista el resto. En cambio, si las secuencias son parecidas entre sí y tienen longitudes similares, el trabajo se vuelve mucho más intuitivo, porque la mayoría de las posiciones ya coinciden solas y hace falta ajustar manualmente mucho menos.

## ¿Son parecidos los citocromos c de humano y gallo?

Sí, bastante. Comparando las dos secuencias de 104 aminoácidos, solo difieren en 13 posiciones; el resto de la secuencia es idéntica. Siendo organismos tan distintos (un mamífero y un ave), esa cantidad de diferencias es chica, lo que ya da una pista de que esta proteína se mantuvo bastante estable a lo largo de la evolución.

## ¿Qué teorías subyacen a este análisis?

Este tipo de comparación se apoya en la teoría de la evolución y, en particular, en la idea de ancestro común: todos estos organismos descienden de un antepasado compartido, y por eso conservan en mayor o menor medida los mismos genes y proteínas. El citocromo c es un buen ejemplo porque cumple una función esencial (la respiración celular) en prácticamente todos estos organismos. De hecho, entre humano, chimpancé y gorila las secuencias son exactamente iguales, lo que tiene sentido porque son las especies más cercanas evolutivamente de la lista.

## ¿Cómo nos ayuda la evolución a explicar sus similitudes y diferencias?

Las similitudes se explican por el ancestro común: cuanto más cerca están dos especies en el árbol evolutivo, menos tiempo tuvieron sus secuencias para acumular cambios, y por eso se parecen más. Se ve claramente comparando humano, chimpancé y gorila (prácticamente sin diferencias) contra la gallina, que está más alejada y ya muestra más cambios. Además, como el citocromo c es clave para un proceso vital como la respiración celular, es esperable que se mantenga bastante conservado: una mutación que arruine su función sería muy perjudicial para el organismo, así que la selección natural tiende a "descartarla".

Las diferencias, en cambio, se explican por las mutaciones que van apareciendo y acumulándose en el ADN con el paso de las generaciones. Cuanto más tiempo pasó desde que dos especies se separaron de su ancestro común, más mutaciones tuvieron tiempo de acumular por separado, y más diferente termina siendo su secuencia.

## ¿Qué indican los colores?

En el alineamiento de Clustal, los colores representan propiedades fisicoquímicas de los aminoácidos (por ejemplo si son polares, no polares, con carga positiva o negativa, etc). Esto permite ver de un vistazo, más allá de si la letra es exactamente la misma, si dos aminoácidos en la misma posición son al menos "parecidos" en sus propiedades químicas, aunque no sean idénticos.

## ¿Qué indican el guión (-), los dos puntos (:) y el asterisco (*)?

- **Guión (-):** indica un gap, es decir que en esa posición una de las secuencias no tiene ningún aminoácido (por una inserción o deleción).
- **Dos puntos (:):** indica que en esa columna los aminoácidos no son idénticos, pero comparten propiedades fisicoquímicas parecidas (una sustitución conservativa).
- **Asterisco (*):** indica identidad total en esa columna, es decir que todas las secuencias tienen exactamente el mismo aminoácido en esa posición. Son las posiciones que se conservaron sin cambios en todos los organismos comparados.

## A simple vista, ¿se conserva la secuencia del citocromo c en los organismos?

Sí, se nota bastante. En el alineamiento aparecen muchísimas columnas marcadas con asterisco, y en general los colores se repiten de una secuencia a otra en la mayoría de las posiciones. Esto confirma que el citocromo c es una proteína muy conservada a lo largo de la evolución.

## ¿Creeríamos que todos los organismos se asemejan por igual al resto, o se pueden identificar grupos de mayor similitud? Si es así, ¿tienen sentido?

No, no todos se asemejan por igual. Mirando el árbol que arma Clustal se pueden distinguir grupos más parecidos entre sí, como el de los primates (humano, chimpancé, gorila) separado del resto. Esto tiene sentido con la teoría de la evolución, porque esos organismos comparten un ancestro común más reciente que el que comparten con, por ejemplo, la mosca o el salmón. Igualmente, con solo nueve secuencias el árbol que se obtiene es bastante simple y no alcanza para sacar conclusiones muy finas sobre todos los grupos (haría falta comparar más secuencias para un análisis más completo).

## ¿Qué evidencias nos aportaría este análisis, a la luz de la evolución?

Este tipo de análisis aporta evidencia a favor del ancestro común: cuanto más similar es la secuencia del citocromo c entre dos organismos, más cercano es su parentesco evolutivo. Es una forma de "leer" en las proteínas actuales un registro indirecto de la historia evolutiva de las especies, algo que no se puede obtener de otra manera porque no hay un registro fósil de las proteínas.

## A juzgar por los organismos participantes, ¿cuáles creería que deberían estar más agrupados en el árbol filogenético?

Esperaría que el grupo más unido sea el de los primates: humano, chimpancé y gorila. Después, un poco más alejados, el resto de los mamíferos (caballo y perro). Más lejos todavía estarían los vertebrados no mamíferos (la gallina, la rana y el salmón), y el organismo más distante de todos debería ser la mosca de la fruta, que ni siquiera es un vertebrado.

## Observemos el árbol filogenético. ¿Concuerda con lo esperado? ¿De qué organismos son los citocromos c más parecidos? ¿Cómo se explica?

Sí, el árbol que devuelve Clustal concuerda bastante con lo esperado. Los citocromos c más parecidos son los de humano, chimpancé y gorila, que quedan agrupados juntos y con las ramas más cortas entre ellos. Esto se explica porque son las especies con el ancestro común más reciente de toda la lista, así que tuvieron menos tiempo evolutivo para acumular diferencias en esta proteína.
