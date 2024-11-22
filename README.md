# dengue_project

## creating the project directory named denge_project and its subdirectories
 ```
mkdir -p project_dengue/codes project_dengue/data/raw/ project_dengue/data/processed
```

## Moving downloaded shared zipped files to the appropriate directory
```
cd Downloads
mv dengue.zip ~/project_dengue/data/raw/
```

## unzipping the shared zipped file

```
cd ~/project_dengue/data/raw/
```

```
unzip dengue.zip
````

## number of files present shared file
```
ls *.fasta | wc -l

```

## Number of lines in each file

```
 wc -l *.fasta
 ```
  |File name       |number of line|
  |----------------|--------------|
  |dengueseq1.fasta| 42           |
  |dengueseq2.fasta| 115          |
  |dengueseq3.fasta| 94           |
  |dengueseq4.fasta| 113          |
  |dengueseq5.fasta| 157          |
  |total lines     | 521          |

## merging all five files into one file named dengue_merged.fasta
```
cat *.fasta > dengue_merged.fasta
```

## number of headers in merged file
```
grep -c "^>" dengue_merged.fasta
```
### There are five headers

## number of sequences in the merged file
```
grep -v "^>" dengue_merged.fasta | wc -c
```
### The total number of sequences is  35801

## extracting headers from merged file into the file named dengue_header.txt
`code` grep "^>" dengue_merged.fasta > dengue_header.txt
### five headers extracted include.
### >NC_001478.1 Digitaria streak virus, complete genome
### >NC_001479.1 Encephalomyocartidis virus, complete genome
### >NC_001480.1 Eggplant mosaic virus, complete genome
### >NC_001481.2 Feline calicivirus, complete genome
### >NC_001477.1 Dengue virus 1, complete genome

## extracting only viruses name into file named viruses.text
`code` grep "^>" dengue_header.txt | cut -d " " -f2-3 > viruses.txt
### five names extracted include.
### Digitaria streak 
### Encephalomyocartidis virus
### Eggplant mosaic 
### Feline calicivirus
### Dengue virus 

## extracting unique identifiers into file named, viruses_uniqID.txt
`code` grep "^>" dengue_merged.fasta | cut -d " " -f1 | cut -d ">" -f2
### five unique identifer extracted are;
### NC_001478.1 
### NC_001479.1 
### NC_001480.1 
### NC_001481.2 
### NC_001477.1 

### creating a file for sequence only named dengue_seq.txt and replace the values in the file with small letters.
`code` grep -v "^>" dengue_merged.fasta | tr "[:upper:]" "[:lower:]" > dengue_seq.txt

## the orgnism with the number of highest and least number of bases

