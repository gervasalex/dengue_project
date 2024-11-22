# dengue_project

## *Creating the project directory named denge_project and its subdirectories*
 ```
mkdir -p project_dengue/codes project_dengue/data/raw/ project_dengue/data/processed
```

## *Moving downloaded shared zipped files to the appropriate directory*
```
cd Downloads
mv dengue.zip ~/project_dengue/data/raw/
```

## *Unzipping the shared zipped file*

```
cd ~/project_dengue/data/raw/
```

```
unzip dengue.zip
````

## *Number of files present shared file*
```
ls *.fasta | wc -l
```
### Output:
### 5 files

## *Number of lines in each file*

```
 wc -l *.fasta
 ```
### Output:
  |File name       |Number of lines|
  |----------------|--------------|
  |dengueseq1.fasta| 42           |
  |dengueseq2.fasta| 115          |
  |dengueseq3.fasta| 94           |
  |dengueseq4.fasta| 113          |
  |dengueseq5.fasta| 157          |
  |total lines     | 521          |

## *Merging all five files into one file named dengue_merged.fasta*
```
cat *.fasta > dengue_merged.fasta
```

## *Number of headers in the merged file*
```
grep -c "^>" dengue_merged.fasta
```
### output
### 5 headers

## *Number of sequences in the merged file*
```
grep -v "^>" dengue_merged.fasta | wc -c
```
### Output:
### Total number of sequences:  35801

## *Extracting headers from a merged file into the file named dengue_header.txt*
```
grep "^>" dengue_merged.fasta > dengue_header.txt
```
### Output:
### five headers extracted include.
### >NC_001478.1 Digitaria streak virus, complete genome
### >NC_001479.1 Encephalomyocartidis virus, complete genome
### >NC_001480.1 Eggplant mosaic virus, complete genome
### >NC_001481.2 Feline calicivirus, complete genome
### >NC_001477.1 Dengue virus 1, complete genome

## *Extracting only virus names into a file named viruses.text*
```
cut -d " " -f2-3 dengue_header.txt > viruses.txt
```
### Output:
### Digitaria streak 
### Encephalomyocartidis virus
### Eggplant mosaic 
### Feline calicivirus
### Dengue virus 

## *Extracting unique identifiers into a file named, viruses_uniqID.txt*
```
cut -d " " -f1 dengue_header.txt | cut -d ">" -f2 > viruses_uniqID.txt
```
### Output:
### NC_001478.1 
### NC_001479.1 
### NC_001480.1 
### NC_001481.2 
### NC_001477.1 

## *Create a file for sequence only named dengue_seq.txt and replace the values in the file with small letters*
```
grep -v "^>" dengue_merged.fasta | tr "[:upper:]" "[:lower:]" > dengue_seq.txt
```

## *The organism with the number of highest and least number of bases*

