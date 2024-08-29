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

If error: AttributeError: module 'Bio.SeqFeature' has no attribute 'SimpleLocation'  
try updating biopython  
pip install --upgrade biopython  

```
EMBLmyGFF3 SIGCAN1A.FA.dc.gff3.gz fSigCan.fa.gz \
        --topology linear \
        --molecule_type 'genomic DNA' \
        --transl_table 1  \
        --species 'Siganus canaliculatus' \
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

### Note : Some warning on STDOUT while creating .embl file, don't know what it means!

```
10:52:42 WARNING feature: Unknown qualifier 'GO:0014731' - skipped
10:52:42 WARNING feature: Unknown qualifier 'GO:0090315' - skipped
10:52:42 WARNING feature: Unknown qualifier 'GO:0010763' - skipped
10:52:42 WARNING feature: Unknown qualifier 'GO:0051895' - skipped
10:52:42 WARNING feature: Unknown qualifier 'GO:0010801' - skipped
10:52:42 WARNING feature: Unknown qualifier 'GO:0015311' - skipped============ ]
10:52:42 WARNING feature: Unknown qualifier 'GO:0019205' - skipped============ ]
10:52:42 WARNING feature: Unknown qualifier 'GO:0044773' - skipped============ ]
```

### Fix validation error

Validation of EMBL file throws these errors:  
```
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 3307 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 1025142 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 1572539 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 2460843 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 2822777 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 3289616 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 3682316 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 4630408 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 4630538 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 5529944 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 5991512 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 6322584 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 6362009 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 6372384 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 7010299 of SIGCAN1A_v1.embl.gz]  
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8318281 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8417596 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8418930 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8832303 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8832736 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 8835712 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 9354046 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 9425939 of SIGCAN1A_v1.embl.gz]
ERROR: Abutting features cannot be adjacent between neighbouring exons. [ line: 10405343 of SIGCAN1A_v1.embl.gz]
```
Fix errors:  
```
# get line numbers with errors in them
awk '{print $12"d;"}' ORS=' ' validation.error.txt

# run sed to remove these lines
sed -i -e '3307d; 1025142d; 1572539d; 2460843d; 2822777d; 3289616d; 3682316d; 4630408d; 4630538d; 5529944d; 5991512d; 6322584d; 6362009d; 6372384d; 7010299d; 8318281d; 8417596d; 8418930d; 8832303d; 8832736d; 8835712d; 9354046d; 9425939d; 10405343d' SIGCAN1A_v1.embl > SIGCAN1A_v1_fixed.embl

#note: perform validation step again to make sure errors have been fixed.
```
