# Snake_Genetics
For Garter Snake Genetics

- git clone git@github.com:Deuterostome/Snake_Genetics.git
- awk '{FS = ","} {print $3}' ELelegans_csv.csv > Elelegans_tissue_ID.txt
- awk '{FS = ","} {print $35}' SnakeBase_csv.csv > SnakeBase_tissue_SampleI.txt
- awk '{FS = ","} {print $37}' SnakeBase_csv.csv > SnakeBase_tissue_SampleII.txt
- grep -F -x -f Elelegans_tissue_ID.txt SnakeBase_tissue_SampleI.txt > repeat_I.txt
- grep -F -x -f Elelegans_tissue_ID.txt SnakeBase_tissue_SampleII.txt > repeat_II.txt

- awk '{FS = ","} {print $3 "," $14 "," $9 "," $13 "," $7}' ELelegans_csv.csv > ELelegans_tissue_ID.csv
- awk '{FS = ","} {print $35 "," $37 "," $1 "," $8}' SnakeBase_csv.csv > SnakeBase_tissue_SampleI.csv
- awk '{FS = ","} {print $37 "," $35 "," $1 "," $8}' SnakeBase_csv.csv > SnakeBase_tissue_SampleII.csv
- **sed -i 's/.//g' SnakeBase_tissue_SampleI.csv**
- **sed -i 's/.//g' SnakeBase_tissue_SampleII.csv**
- sort -t ',' -k1,1 -n ELelegans_tissue_ID.csv > ELelegans_tissue_ID_sort.csv
- sort -t ',' -k1,1 -n SnakeBase_tissue_SampleI.csv > SnakeBase_tissue_SampleI_sort.csv
- sort -t ',' -k1,1 -n SnakeBase_tissue_SampleII.csv > SnakeBase_tissue_SampleII_sort.csv
- **join -t ',' SnakeBase_tissue_SampleI_sort.csv ELelegans_tissue_ID_sort.csv > ELelegans_against_Snakebase_sampleI.csv**
- **join -t ',' SnakeBase_tissue_SampleII_sort.csv ELelegans_tissue_ID_sort.csv > ELelegans_against_Snakebase_sampleII.csv**
- **join -t ',' SnakeBase_tissue_SampleII_sort.csv ELelegans_tissue_ID_sort.csv > ELelegans_against_Snakebase_sampleII.txt**
