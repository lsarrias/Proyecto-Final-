# Estudios de *Begonia* en el mundo.
![variedades-de-begonias](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/48587ef2-ae36-482d-b153-fbba6924e52d)

# Introducción
Para este proyecto, se utilizarán datos de secuencias genómicas de plantas pertenecientes a la familia Begoniaceae. Específicamente, se emplearán secuencias de ADN completas o parciales de begonias disponibles en repositorios públicos como NCBI. Los datos fueron descargados en formato FASTA. El objetivo es generar una filogenia comprensiva de 20 especies de la familia Begoniaceae, con un enfoque particular en las especies de begonias endémicas del Ecuador.

Vídeo sobre la diversificación del género *Begonia* en América: ```https://youtu.be/3-72YDYKpPs ```

# Métodos
  # Obtención de secuencias 
Las secuencias del gen Ycf2 fueron descargadas de NCBI en formato FASTA. Posteriormente, se unieron todos los archivos FASTA en uno solo y se editó el formato para que los nombres quedaran en el formato Género_especie usando Sublime Text con la siguiente fórmula:

```{r}
*Find*: >^.*\b([A-Z][a-z]+_[a-z]+)\b.*$

*Replace*: >\1
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

# Resultados

*Subir la imagen de la filogenia*
```{r}
knitr::include_graphics("/c/Users/lsarr/Desktop/Proyecto_Final/results/Begonia_Filogenia.JPEG")
```
*Árbol concenso generado en IQTREE*

![Begonia_Filogenia](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/6a214855-1a81-4261-8eef-000e1329afd5)

*Árbol concenso generado en Muscle online*

![Muscle](https://github.com/lsarrias/Proyecto-Final-/assets/171622163/b6cc8ef0-1365-4e86-934f-180b9f3a9445)

# Discusión

# Conclusiones

# Referencias 

