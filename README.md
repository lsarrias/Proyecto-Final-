# Estudios de *Begonia* en el mundo.
## Introducción
Begoniaceae es una familia reconocida por sus numerosas especies ornamentales, se distribuye en los trópicos y subtrópicos, siendo la región norte de Sudamérica su principal centro de diversidad (Moonlight, 2013). . Las especies endémicas de Begonia en Ecuador se distribuyen en las tres regiones continentales, desde los 150 m hasta los 3535 m de altitud. A partir de los 1000, se encuentran 25 de las 28 especies endémicas, mientras que las restantes se distribuyen exclusivamente en los bosques bajos de la Amazonía y la Costa (Quintana & León-Yánez et al., 2011).

Para este proyecto, se utilizarán datos de secuencias genómicas de plantas pertenecientes a la familia Begoniaceae. Específicamente, se emplearán secuencias de ADN completas o parciales de begonias disponibles en repositorios públicos como NCBI. Los datos fueron descargados en formato FASTA. El objetivo es generar una filogenia comprensiva de 20 especies de la familia Begoniaceae, con un enfoque particular en las especies de begonias endémicas del Ecuador.

Vídeo sobre la diversificación del género *Begonia* en América: ```https://youtu.be/3-72YDYKpPs ```

## Métodos
  ### Obtención de secuencias 
Las secuencias del gen Ycf2 fueron descargadas de NCBI en formato FASTA. Posteriormente, se unieron todos los archivos FASTA en uno solo y se editó el formato para que los nombres quedaran en el formato Género_especie usando Sublime Text con la siguiente fórmula:

#### *Find*
```{r}
>^.*\b([A-Z][a-z]+_[a-z]+)\b.*$
```

#### *Replace*
```{r}
>\1
```

![Begonia ludwigii_Andres C  Palmer_iNaturalist](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/98c386e5-e4b3-486f-875c-b46e59e73f92)

# *Alineamiento*

El archivo FASTA fue alineado utilizando el software Mesquite.

# *Construcción de la Filogenia*

Para construir la filogenia, se utilizaron los siguientes comandos en IQ-TREE, un software para el análisis filogenético.


```{r}
# Descomprimir el archivo de IQ-TREE
unzip iqtree-2.0.6-Windows32.zip

# Cambiar al directorio descomprimido de IQ-TREE
cd iqtree-2.0.6-Windows32

# Listar los archivos en el directorio para verificar el contenido
ls

# Cambiar al subdirectorio 'bin' donde se encuentra el ejecutable de IQ-TREE
cd bin/

# Listar los archivos en el directorio 'bin'
ls

# Ejecutar IQ-TREE para asegurarse de que funcione correctamente
./iqtree2.exe

# Regresar al directorio anterior
cd ..

# Regresar al directorio principal del proyecto
cd ..

# Listar los archivos para verificar la ubicación
ls

# Cambiar al directorio que contiene las secuencias de Begonia y Rosa
cd "20 ESPECIES BEGONIA Y ROSA/"

# Listar los archivos en el directorio para verificar el contenido
ls

# Ejecutar IQ-TREE con el archivo FASTA alineado y realizar 1000 réplicas bootstrap
iqtree2 -s Begonia_sequence_formato_mesquite.fasta -B 1000

# Ejecutar IQ-TREE nuevamente para asegurarse de la ejecución correcta
./iqtree2.exe

# Regresar al directorio de IQ-TREE
cd ../iqtree-2.0.6-Windows32/bin/

# Ejecutar IQ-TREE nuevamente
./iqtree2.exe

# Imprimir el directorio actual para verificar la ubicación
pwd

# Exportar la ruta del ejecutable de IQ-TREE como una variable de entorno
export PROJ_DIR=/c/Users/lsarr/Desktop/iqtree-2.0.6-Windows32/bin/iqtree2.exe

# Regresar al directorio principal
cd ../..

# Listar los archivos para verificar la ubicación
ls

# Cambiar al directorio del proyecto final
cd Proyecto_Final

# Cambiar al directorio de resultados
cd results

# Ejecutar IQ-TREE con el archivo FASTA alineado y realizar 1000 réplicas bootstrap utilizando la variable de entorno
$PROJ_DIR -s Begonia_sequence_Aligned.fasta -B 1000

```

## Resultados

*Subir la imagen de la filogenia*
```{r}
knitr::include_graphics("/c/Users/lsarr/Desktop/Proyecto_Final/results/Begonia_Filogenia.JPEG")
```
*Árbol concenso generado en IQTREE*

![Begonia_Filogenia](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/6a214855-1a81-4261-8eef-000e1329afd5)

*Árbol concenso generado en Muscle online*

![Muscle](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/b6cc8ef0-1365-4e86-934f-180b9f3a9445)

## Discusión

La construcción de una filogenia de begonias ofrece una base científica crucial para entender las relaciones evolutivas entre las diferentes especies. Este conocimiento es fundamental en la biología de la conservación, especialmente para especies endémicas que tienen un mayor riesgo de extinción debido a sus distribuciones geográficas limitadas y específicas.Una filogenia detallada puede identificar clados, o grupos de especies que descienden de un ancestro común, que son particularmente vulnerables a amenazas ambientales. Por ejemplo, si un clado completo de begonias endémicas muestra adaptaciones específicas a un tipo particular de hábitat, la destrucción de ese hábitat podría poner en riesgo a todas las especies de ese clado. Esta información permite a los conservacionistas focalizar sus esfuerzos en proteger los hábitats más críticos y desarrollar estrategias de conservación específicas para clados vulnerables.

#### Diversidad Genética y Estrategias de Conservación
Entender las relaciones filogenéticas ayuda a evaluar la diversidad genética dentro y entre las poblaciones de begonias. La diversidad genética es un componente clave para la supervivencia a largo plazo de las especies, ya que permite la adaptación a cambios ambientales y resistencia a enfermedades. Las filogenias pueden revelar qué poblaciones son más diversas genéticamente y, por lo tanto, deben ser priorizadas para la conservación. También pueden identificar poblaciones que están genéticamente aisladas y que pueden necesitar intervenciones específicas para evitar la endogamia y la pérdida de diversidad genética.

#### Priorización de Especies para la Conservación
Dada la limitación de recursos, no todas las especies pueden ser protegidas al mismo tiempo. Una filogenia detallada puede ayudar a priorizar especies basándose en su posición evolutiva y su contribución a la diversidad filogenética total. Especies que ocupan posiciones únicas en el árbol filogenético, es decir, aquellas que no tienen parientes cercanos, pueden representar una gran cantidad de diversidad genética y evolutiva y, por lo tanto, ser consideradas de alta prioridad para la conservación. Para especies de *Begonia* en peligro crítico o extirpadas de sus hábitats naturales, los programas de reintroducción pueden beneficiarse de la información filogenética. Conocer las relaciones evolutivas y las adaptaciones ecológicas específicas de estas especies permite seleccionar hábitats adecuados y diseñar programas de reintroducción que maximicen las posibilidades de supervivencia y adaptación a largo plazo.

![Distribución Begonia ludwigii](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/16568033-f7ef-45ec-8c5f-3ad82cfd615c)

#### Conservación Integrada y Educación
Las filogenias pueden servir como herramientas educativas para aumentar la conciencia sobre la importancia de las begonias y la biodiversidad en general. Mostrar las conexiones evolutivas y la historia de las begonias puede ayudar a construir un argumento convincente para la conservación y el valor intrínseco de estas plantas. También puede inspirar a las comunidades locales y a los responsables políticos a participar activamente en los esfuerzos de conservación (Hanski, 2011).
.

## Conclusiones
La construcción y el análisis de una filogenia de begonias no solo contribuyen al conocimiento científico, sino que también tienen aplicaciones prácticas directas en la conservación de las especies de begonia endémicas de América. Proporciona un marco para entender mejor las relaciones evolutivas, evaluar la diversidad genética y desarrollar estrategias de conservación informadas y efectivas. Al integrar este conocimiento en las políticas y prácticas de conservación, podemos mejorar significativamente las probabilidades de supervivencia de estas especies únicas y valiosas.

## Referencias 
Hanski, I. (2011). Habitat Loss, the Dynamics of Biodiversity, and a Perspective on Conservation. *Ambio*, 40(3), 248-255. https://doi.org/10.1007/s13280-011-
0147-3
Moonlight, P. (2013). *The biogeography of neotropical Begonia L.: correlation between mountain evolution and range evolution in an Andean-centered group*. MSc 
Thesis, University of Edinburgh.
Quintana, C., León-Yánez, S. (2011). Begoniaceae. En: León-Yánez, S., R. Valencia, N. Pitmam, L. Endara, C. Ulloa Ulloa y H. Navarrete (Eds). *Libro Rojo de Plantas Endémicas del Ecuador*. Publicaciones del Herbario QCA, Pontificia Universidad  Católica del Ecuador, Quito.

