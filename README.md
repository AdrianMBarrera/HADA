![](https://drive.google.com/uc?export=view&id=1Cciw1VFzcuRy_IT4pbN7nEZDRe-BcETe)


# HADA: automated annotation of next-generation sequencing data in hereditary angioedema studies

In order to assist the clinical diagnosis and adapt it to the paradigm of precision medicine and next-generation sequencing (NGS)-based genetic tests, we have developed the Hereditary Angioedema Database Annotation (HADA) tool (hyperlink to the tool) built on top of a database of hundreds of known variants affecting function, including a precomputed pathogenic assessment of each variant and a ranked classification according to the current guidelines from the American College of Medical Genetics and Genomics. The curated database of variants affecting function in HAE can be accessed from this repository and is ready to be incorporated into ANNOVAR annotation routines.

At the moment, the database is supplied in GRCh37/hg19 coordinates and integrates information from 449 single nucleotide variants and small insertion/deletions from five genes (*SERPING1*, *F12*, *PLG*, *ANGPT1*, and *KNG1*) that we classified as variants likely affecting function.


## Contents
* [Background](#background)
* [Getting started](#getting-started)
* [Usage](#usage)
* [How to cite](#how-to-cite)

---

## Background

Hereditary angioedema (HAE) is a rare genetic disease caused by a dysfunction of the C1 inhibitor or dysregulation of the kinin cascade leading to an increase of vascular permeability, generating recurrent acute swelling episodes commonly localized on the face, trunk, and the extremities. It can also threaten the life of patients when the upper airways or the tissues from the oral cavity are affected. HAE is poorly recognized by physicians. Therefore, ambiguous or delayed diagnoses are common, increasing the risk of patient morbidity and mortality. Genetic testing in HAE has become an important step to reduce the diagnostic odyssey, to increase the diagnostic yield and to tailor treatments. We aimed to provide a resource to assist in the diagnosis of HAE that is adapted to NGS technologies and to the evolving knowledge of the causes of HAE that has the potential to reduce the time to interpret the detected variants in the NGS era by aggregating data from multiple sources.

---

## Getting started 

### Requirements
Linux or macOS.

### Install ANNOVAR
Download and install [ANNOVAR](http://download.openbioinformatics.org/annovar_download_form.php) according to the instructions.

Once downloaded, unpack the package by using this command:

```
tar -zxvf annovar.latest.tar.gz
```

### Download HADA

In ANNOVAR folder, download HADA databases and index files from this repository:

```
cd annovar/humandb
wget https://raw.githubusercontent.com/genomicsITER-developers/HADA/master/databases/hg19_hada_20191203.txt
wget https://raw.githubusercontent.com/genomicsITER-developers/HADA/master/databases/hg19_hada_20191203.txt.idx

wget https://raw.githubusercontent.com/genomicsITER-developers/HADA/master/databases/hg19_hada_related_genes_20191203.txt
wget https://raw.githubusercontent.com/genomicsITER-developers/HADA/master/databases/hg19_hada_related_genes_20191203.txt.idx
```

## Usage

Annotate a VCF file using HADA database and variants in HAE related genes:
```
perl <path-to-annovar-dir>/table_annovar.pl <path-to-vcf-infile> <path-to-annovar-dir>/humandb \
  -buildver hg19 \
  -out <path-to-vcf-outfile> \
  -remove \
  -protocol hg19_hada_20191203, hg19_hada_related_genes_20191203 \
  -operation f,f \
  -nastring . \
  -vcfinput
```
The resulting annotated VCF will be in `<path-to-vcf-outfile>.hg19_multianno.vcf`

**Note:** remember to replace the items in `<>` with your local paths in your computer.

---

## How to cite

Mendoza-Alvarez, A., Muñoz-Barrera, A., Rubio-Rodríguez, L.A., Marcelino-Rodríguez, I., Corrales, A., Iñigo-Campos, A.,  Callero, A., García-Robaina, J.C., González-Montelongo, R., Lorenzo-Salazar, J.M., Flores, C. (2020). HADA: an interactive web-based resource for the annotation of genetic variants causing hereditary angioedema. (Under Revision).

---

## Funding
This   work   was   supported   by   the   Ministerio   de   Ciencia,    Innovación  y  Universidades  (RTC-2017-6471-1;  MINECO/AEI/FEDER,  UE),  which  was  co-financed  by  the  European   Regional Development Funds ‘A way of making Europe’ from  the  European  Union;  Cabildo Insular de Tenerife  (CGIEU0000219140),  and  by  agreement  OA17/008   with  the  Instituto  Tecnológico  y  de  Energías  Renovables   (ITER)  to  strengthen  scientific  and  technological  education,   training, research, development, and innovation in genomics,  personalized    medicine,    and    biotechnology.    AMA    was     supported  by  a  fellowship  from  ULL-Cajasiete.

<p align="center">
  <img src="https://github.com/genomicsITER/HADA/blob/master/MICIU-Agencia-y-Europa_logo.jpg" width="auto" title="funding" alt="funding" />
</p>
<br>

<p align="center">
  <img src="https://github.com/genomicsITER/HADA/blob/master/Footer.png" width="auto"/ title="logotipos" alt="funding">
</p>
<br>
