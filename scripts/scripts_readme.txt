#Bajar las secuencias del genoma de NCBI del gen Ycf2 en formato FASTA.

#Unir todos los archivos FASTA en una.

#En Sublime Text colocar la siguiente fórmula.

Find: >^.*\b([A-Z][a-z]+_[a-z]+)\b.*$
Replace: >\1

#Para poder reemplazar todo el nombre y que quede solo Género y especie, en este formato: Género_especie.

#Guardar como y guardar como Begonia_sequence_formato

#Alineamiento

#Abrir archivo fasta en Mesquite

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
