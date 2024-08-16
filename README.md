### Motivation
Convert to EMBL flat file format using genome fasta and GFF3 files for Siganus rivulatus


### Files required
$ tree  
├── fSigCan.fa.gz  (fasta file for the genome)  
└── SIGCAN1A.FA.dc.gff3.gz   (annotation file)  

### Installation
More details [here](https://github.com/NBISweden/EMBLmyGFF3?tab=readme-ov-file#installation)  
Installed on my Ubuntu 22.04.2 LTS using the command below
```
pip install git+https://github.com/NBISweden/EMBLmyGFF3.git
```

### Run
```
EMBLmyGFF3 SIGCAN1A.FA.dc.gff3.gz fSigCan.fa.gz \
        --topology linear \
        --molecule_type 'genomic DNA' \
        --transl_table 1  \
        --species 'Siganus rivulatus' \
        --locus_tag SIGCANQ1 \
        --project_id PRJEB79005 \
        --author 'Dana Albatesh' \
        -o SIGCAN1A.embl
```

### Output
Creates .embl file, takes just about a couple of minutes!!  
$ tree  
├── fSigCan.fa.gz  
└── SIGCAN1A.FA.dc.gff3.gz  
├── SIGCAN1A.embl  


***

A quick view below:  
```
$ more SIGCAN1A.embl 
ID   XXX; XXX; linear; genomic DNA; XXX; XXX; 26439986 BP.
XX
AC   XXX; 
XX
AC * _SUPER_1
XX
PR   Project:PRJEB79005;
XX
DT   16-AUG-2024 (Rel. 133, Created)
XX
DE   XXX
XX
KW   .
XX
OS   Siganus rivulatus
XX
OC   cellular organisms; Eukaryota; Opisthokonta; Metazoa; Eumetazoa; Bilateria;
OC   Deuterostomia; Chordata; Craniata; Vertebrata; Gnathostomata; Teleostomi;
OC   Euteleostomi; Actinopterygii; Actinopteri; Neopterygii; Teleostei;
OC   Osteoglossocephalai; Clupeocephala; Euteleosteomorpha; Neoteleostei;
OC   Eurypterygia; Ctenosquamata; Acanthomorphata; Euacanthomorphacea;
OC   Percomorphaceae; Eupercaria; Eupercaria incertae sedis; Siganidae; Siganus.
XX
RN   [1]
RP   1-26439986
RG   XXX
RA   Dana Albatesh;
RT   ;
RL   Submitted (16-AUG-2024) to the INSDC.
XX
FH   Key             Location/Qualifiers
FH
FT   source          1..26439986
FT                   /mol_type="genomic DNA"
FT                   /organism="Siganus rivulatus"
FT   gene            complement(27478..28659)
FT                   /locus_tag="SIGCANQ1_LOCUS1"
FT                   /note="ID:SIGCAN1A009845"
FT                   /note="source:CNAG"
FT   mRNA            complement(join(27478..27601,27813..27956,28381..28517,
FT                   28593..28659))
FT                   /locus_tag="SIGCANQ1_LOCUS1"
FT                   /note="ID:SIGCAN1A009845T1"
FT                   /note="source:CNAG"
FT                   /product="SIGCAN1A009845P1"
FT                   /standard_name="SIGCAN1A009845T1"

```

