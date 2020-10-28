#Genomica Computacional
##Parctica 01 - Manejo de datos de secuenciaciòn masiva 

## Parte I
mkdir GenomicaComputacional
cd GenomicaComputacional
mkdir jramirez_p01
cd jramirez_p01
touch comandos_p01.txt

#Comandos de la practica 1
##F.Javier Ramirez Justo

## Parte I.
#!/bin/bash

## Parte II
01. echo $SHELL
    La shell es Bash 
02. cd ~/GenomicaComputacional/jramirez_p01
    mkdir data/ filtered/ raw_data/ meta/ scripts/ figures/ archive/
03. mv filtered ~/GenomicaComputacional/jramirez_p01/data   
    mv raw_data ~/GenomicaComputacional/jramirez_p01/data
04. Lleva los nombres y la organizacion necesaria para reproducir el analisis realizado.
    Los directorios pueden dividirse a su vez para tener una mejor organizacion, como en el caso de data, donde irian los datos crudos y en las divisiones los modificados
    archive, data, figures, meta, scripts son los subdirectorios recomendados, en data estarian los datos, en meta la informacion, en scripts estaria el/los scripts necesarios para correr el analisis, en figures estaria el codigo necesario para reproducir las figuras y en archive, los datos que no estarian en el repositorio pero que es donde se puede agregar cosas que no sabes si puedes necesitar despues.    

## Parte II
cd
cd ~/GenomicaComputacional/jramirez_p01/scripts
which bash = /usr/bin/bash
touch delay.sh
nano delay.sh
01. chmod 777 delay.sh
02. ls -lth
sh delay.s
03.#!/bin/bash
echo "Después de la Parte I. necesito un descanso de exactamente 30 segundos."
<sleep 30 && echo "Ya puedo continuar!>
04. <sleep 300 & echo "Ya puedo continuar!>

## Parte III 
01.Los coronavirus producen enfermedades tanto en humanos como en animales. Aparentemente el SARS-CoV-2 tuvo su origen en muercielagos, con un posible hospedero intermedio. El virus tiene un tamaño de 50-200 nm, es un virus es un virus de RNA de cadena sencilla, enrollado en una nucleocapside, tiene una envoltura que consta de una glicoproteina de membrana, una proteina de la envoltura y una proteina espicula glicosilada, la cual esta constituida de un ectodominio dividio en el dominio S1 el cual esta formado de un trimero que se une al receptor en la celula, y el dominio S2 que va a mediar la fusion. La proteina S, se une a la enzima convertidora de angiotesina 2, la cual se encuentra en muchos tejidos dentro del organismo.
02.
cd
cd Descargas
mv sequence.fasta ~/GenomicaComputacional/jramirez_p01
mv sequence.gff3 ~/GenomicaComputacional/jramirez_p01
cd ~/GenomicaComputacional/jramirez_p01
mv sequence.fasta sarscov2_genome.fasta
mv sequence.gff3 sarscov2_genome.gff3
cd
cd Descargas
mv *.fasta ~/GenomicaComputacional/jramirez_p01/
cd GenomicaComputacional/jramirez_p01/
mv 'sequence (2).fasta' splike_c.faa
mv 'sequence (3).fasta' splike_b.faa
mv 'sequence (4).fasta' splike_a.faa
cd meta
touch SarsCov-2_Spike.txt
cd Genomica_COmputacional
cd practica01
mv *.gz ~/GenomicaComputacional/jramirez_p01
cd
cd ~/GenomicaComputacional/jramirez_p01
mv *.gz ~/GenomicaComputacional/jramirez_p01/data/raw_data
mv *.faa ~/GenomicaComputacional/jramirez_p01/data/raw_data
mv sars* ~/GenomicaComputacional/jramirez_p01/data/raw_data

## Parte IV
01. 
cd
cd ~/GenomicaComputacional/jramirez_p01/data/filtered
ln -s ~/GenomicaComputacional/jramirez_p01/data/raw_data/splike_a.faa
ln -s ~/GenomicaComputacional/jramirez_p01/data/raw_data/splike_b.faa
ln -s ~/GenomicaComputacional/jramirez_p01/data/raw_data/splike_c.faa
02.
touch glycoproteins.faa
ls
03.
head -n1 splike_*.faa
==> splike_a.faa <==
>pdb|6VXX|A Chain A, SARS-CoV-2 spike glycoprotein

==> splike_b.faa <==
>pdb|6VXX|B Chain B, SARS-CoV-2 spike glycoprotein

==> splike_c.faa <==
>pdb|6VXX|C Chain C, SARS-CoV-2 spike glycoprotein
04. 
less splike_a.faa splike_b.faa splike_c.faa >> glycoproteins.faa
05.
cd ..
cd raw_data
mv splike_*.faa ~/GenomicaComputacional/jramirez_p01/archive
**la liga simbolica se rompio**
06. 
less sarscov2_genome.fasta
zless sarscov2_assembly.fasta.gz
head -n3 sarscov2_genome.fasta
>NC_045512.2 Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome
ATTAAAGGTTTATACCTTCCCAGGTAACAAACCAACCAACTTTCGATCTCTTGTAGATCTGTTCTCTAAA
CGAACTTTAAAATCTGTGTGGCTGTCACTCGGCTGCATGCTTAGTGCACTCACGCAGTATAATTAATAAC
zless sarscov2_assembly.fasta.gz | head -n3
>NODE_1_length_264_cov_161.042781
CACAAATCTTAACACTCTTCCCTACACGACGCTCTTCCGATCTACGCCGGGCCATTCGTA
CGAACCGATACCTGTGGTAAAGGGTCCTACTGTATGGTGGTACACGAGTAGTAGCAAATG

07.
zless sarscov2_assembly.fasta.gz | grep '>'| wc -l
**35**
grep '>' sarscov2_genome.fasta | wc -l
**1**

08.
zless SRR10971381_R2.fastq.gz | head -n12
@SRR10971381.512_2
CGTGGAGTATGGCTACATACTACTTATTTGATGAGTCTGGTGAGTTTAAAGTGGCTTCACATATGTATTGTTCTTTCTACCCTCCAGATGAGGATGAAGAAGAAGGTGATTGTGAAGAAGAAGAGTTTGAGCCATCAACTCAATATGAGT
+ 
/FFFA/A/FFFF66FFFFFF/FF/FFFFFFFFFFFFF/AFFF6FFFA6FFFFF/FFFFFFFFFFFFFFFFFF/FF/FFFFFA/FFF/FFF/A/AFA/FFFFF/=F/F/F/AFAFF//A/AFF//FFAF/FFF=FFAFFFA/A/6=///==
@SRR10971381.556_2
TTTGTAAAAATAAAATAAAAAAAATAAAAATAATATATTAAAAAAAGATAAATAAAAAAATGAACAATTAATAAAAAAAAAAAAAAAAAAAAATTAAAAAAAAAAAAAAAAAAAATAAAAAAAAAAAAAAATAAAAAAAAAATTATAAAA
+
6AFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF/FFFAFFFFFF/FFA/FF=F//=FF/FFFFFFFFFFFFFA/FFFF/FF/FA//F/FFFFFFA/=FFFFF/FFFF/F=FFFAFF///FFFFA/FF/6//////=/
@SRR10971381.1428_2
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
+
FFFFFFFFFFFFAFFFAFFFFFF6A//F//FFF
##Patron para las secuencias
zless SRR10971381_R2.fastq.gz | grep '@' | wc -l
**130022**

09.
.fasta es el formato generico, es un texto usado para la representacion de secuencias, ya sea de nucleotidos o de aminoacidos
.faa es un formato que contiene secuencias de aminoacidos.
.fastq es el formato utilizado para contener tanto la secuencia, generalmente de nucleotidos, como sus puntuaciones de calidad.
En la linea 1 se encuentra el identificador de seciencia, en la linea 2 se encuentran las bases de la secuencia, en la linea 3 hay un caracter '+' y en la linea 4 se encuentran los valores de calidad para la secuencia. 

10.
less sarscov2_genome.gff3
less -S sarscov2_genome.gff3
**Con -S se deshabilita el autoajuste de las lineas, al organizarlo de manera lateral se observa con orden**

11.less -S sarscov2_genome.gff3 | cut -f3 |sort | uniq -c
**Tiene 11 genes
El campo 3 corresponde a la feature, la feature gene la que se le asigna un nombre, mientras que la CDS es la secuencia codificante, que corresponde a la secuenciade nucleotidos **

