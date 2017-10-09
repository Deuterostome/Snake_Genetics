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
____________________________________________________________________________________________________________________________

# Visualization
- grep "T. elegans" SnakeBase_TeitsworthWorkingFile_ALL.csv > SnakeBase_TE.csv
- grep "Year" SnakeBase_TeitsworthWorkingFile_ALL.csv > SnakeBase_TE_1.csv
- cat SnakeBase_TE.csv >> SnakeBase_TE_1.csv
- mv SnakeBase_TE_1.csv SnakeBase_TE.csv
- awk -F "," '$35 != "."||$37 != "."' SnakeBase_TE.csv | awk -F "," '$35 != ""||$37 != ""'> SnakeBase_TE_tissue_all.csv
- awk '{FS = ","} {print $8}' SnakeBase_TE_tissue_all.csv | sort | uniq > b.csv
- awk '{FS = ","} {print $8 "," $1}' SnakeBase_TE_tissue_all.csv | sort -k 1,1 > a.csv
- cat a.csv | uniq -c| awk '{ print $1 "," $2}' > c.csv

# Visualization II
- awk '{FS = ","}{OFS = ","}{$22 = "Y"||$33 = "Y"}{print $0}' SnakeBase_TE.csv > SnakeBase_TE_tissue_blood.csv
- awk '{FS = ","} {print $8}' SnakeBase_TE_tissue_blood.csv | sort | uniq > b_tissue_blood.csv
- awk '{FS = ","} {print $8 "," $1}' SnakeBase_TE_tissue_blood.csv | sort -k 1,1 > a_tissue_blood.csv
- cat a_tissue_blood.csv | uniq -c| awk '{ print $1 "," $2}' > c_tissue_blood.csv




# Sample_I from SnakeBase
- awk '{FS = ","} {print $35 "," $37 "," $1 "," $8 "," $9}' SnakeBase_TE.csv > SnakeBase_TE_SampleI.csv
- awk '{FS = ","} {print $3 "," $14 "," $9 "," $13 "," $7}' ELelegans_csv.csv > ELelegans_tissue_ID.csv
- sort -t ',' -k 1,1 -n SnakeBase_TE_SampleI.csv > SnakeBase_TE_SampleI_sort.csv
- sort -t ',' -k 1,1 -n SnakeBase_TE_SampleI_Clear_sort.csv > SnakeBase_Clear_ID_sampleI_sort_1.csv
- sort -t ',' -k 1,1 -n ELelegans_tissue_ID.csv > ELelegans_tissue_ID_sort.csv
- sort -t ',' -k 1,1 -n ELelegans_clearID.csv > ELelegans_clearID_sort.csv
- join -t ',' SnakeBase_Clear_ID_sampleI_sort_1.csv ELelegans_clearID_sort.csv > SnakeBase_TE_SampleI_Clear_ELelegans_overlap.csv
- sed -i '/^\s*$/d' SnakeBase_SampleII_ELelegans_overlap.txt

# Sample_II from SnakeBase
- awk '{FS = ","} {print $37 "," $35 "," $1 "," $8 "," $9}' SnakeBase_TeitsworthWorkingFile_ALL.csv > SnakeBase_tissue_SampleII.csv
- sort -t ',' -k 1,1 -n SnakeBase_tissue_SampleII.csv > SnakeBase_tissue_SampleII_sort.csv
- join -t ',' SnakeBase_Clear_ID_sampleII.csv ELelegans_clearID_sort.csv > SnakeBase_SampleII_ELelegans_overlap.csv
____________________________________________________________________________________________________________________________
