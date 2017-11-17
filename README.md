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
- grep "T. elegans" SnakeBase_TeitsworthWorkingFile_ALL.txt > SnakeBase_TE.txt
- grep "Year" SnakeBase_TeitsworthWorkingFile_ALL.txt > SnakeBase_TE_1.txt
- cat SnakeBase_TE.txt >> SnakeBase_TE_1.txt
- mv SnakeBase_TE_1.txt SnakeBase_TE.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE.txt > SnakeBase_TE_tissue_blood.txt
- awk '{FS = "\t"} {print $8}' SnakeBase_TE_tissue_blood.txt | sort | uniq > b_tissue_blood.txt

# Visualization on ELelegans
- awk -F "\t" '$3 != ""' ELelegans.txt > ELelegans_tissue.txt
- awk '{FS = "\t"} {print $3 "\t" $9 "\t" $14}' ELelegans_tissue.txt | sort -t '\t' -k2,2 > ELelegans_tissue_sort.txt
- awk '{FS = "\t"} {print $2}' ELelegans_tissue_sort.txt | sort | uniq > ELelegans_uniq_population.txt
- awk '{FS = "\t"} {print $2 "," $3}' ELelegans_tissue_sort.txt | sort -t ',' -k 1,1 > ELelegans_tissue_a.csv
-> a_tissue_blood.txt -> a_tissue_blood.csv
- cat ELelegans_tissue_a.csv | uniq -c| awk '{ print $1 "," $2}' > ELelegans_tissue_c.csv

# Overlapping with ELelegans: Sample_I from SnakeBase
- awk '{FS = "\t"} {print $35 "\t" $37 "\t" $1 "\t" $8 "\t" $9}' SnakeBase_TE.txt > SnakeBase_TE_SampleI.txt
- awk '{FS = "\t"} {print $3 "\t" $14 "\t" $9 "\t" $13 "\t" $7}' ELelegans.txt > ELelegans_tissue.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleI.txt > SnakeBase_TE_SampleI_sort.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleI_Clear.txt > SnakeBase_TE_SampleI_Clear_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue.txt > ELelegans_tissue_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue_Clear.txt > ELelegans_tissue_Clear_Sort.txt
- join -t $'\t' SnakeBase_TE_SampleI_Clear_sort.txt ELelegans_tissue_Clear_Sort.txt > SnakeBase_TE_SampleI_Clear_ELelegans_overlap.txt
- sed -i '/^\s*$/d' SnakeBase_SampleII_ELelegans_overlap.txt

# Overlapping with ELelegans: Sample_II from SnakeBase
- awk '{FS = "\t"} {print $37 "\t" $35 "\t" $1 "\t" $8 "\t" $9}' SnakeBase_TE.txt > SnakeBase_TE_SampleII.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleII.txt > SnakeBase_TE_SampleII_sort.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleII_Clear.txt > SnakeBase_TE_SampleII_Clear_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue.txt > ELelegans_tissue_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue_Clear.txt > ELelegans_tissue_Clear_Sort.txt
- join -t $'\t' SnakeBase_TE_SampleII_Clear_sort.txt ELelegans_tissue_Clear_Sort.txt > SnakeBase_TE_SampleII_Clear_ELelegans_overlap.txt
  (Not working)

# Visualization on Snakebase - again
- grep "elegans" SnakeBase_ALL.txt > SnakeBase_TE.txt
- grep "Year" SnakeBase_TeitsworthWorkingFile_ALL.txt > SnakeBase_TE_1.txt
- cat SnakeBase_TE.txt >> SnakeBase_TE_1.txt
- mv SnakeBase_TE_1.txt SnakeBase_TE.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE.txt > SnakeBase_TE_tissue_blood.txt
- awk '{FS = "\t"} {print $8}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1|uniq > b_tissue_blood.txt
- awk '{FS = "\t"} {print $8 "\t" $1}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1 > a_tissue_blood.txt
-> a_tissue_blood.txt -> a_tissue_blood.csv
- cat a_tissue_blood.csv | uniq -c| awk '{ print $1 "," $2}' > c_tissue_blood.csv

# Visualization on 2016 Snake Data Base
- awk -F "\t" '$19 != "N"' EagleLakeFieldSamples_Telelgans2016_Final.txt > TE2016_blood.txt
- awk '{FS = "\t"} {print $2}' TE2016_blood.txt |sort|uniq -c|awk '{ print $1 "," $2}' > TE2016_count.csv

-> TE2016_Population.txt -> TE2016_Population.csv
- cat TE2016_Population.csv | uniq -c| awk '{ print $1 "," $2}' > TE2016_count.csv

# Visualization on 2017 Snake Data Base
- grep "ELEGANS" Data2017MasterFile.txt > TE2017.txt
- awk -F "\t" '$11 != "NA"' TE2017.txt > TE2017_blood.txt
- awk '{FS = "\t"} {print $7}' TE2017_blood.txt |sort|uniq -c|awk '{ print $1 "," $2}' > TE2017_count.csv
-> TE2016_Population.txt -> TE2016_Population.csv
- cat TE2016_Population.csv | uniq -c| awk '{ print $1 "," $2}' > TE2016_count.csv

# Repeat in Database
- awk '{FS = "\t"} {print $35}' SnakeBase_TE.txt | sort -n -k 1,1 | uniq -c | awk '{ print $1 "\t" $2}'|sort > SnakeBase_Repeat_ID.txt

# Overlapping with ELelegans: Sample_I from SnakeBase
- awk '{FS = "\t"} {print $35 "\t" $37 "\t" $1 "\t" $8 "\t" $9}' SnakeBase_TE.txt > SnakeBase_TE_SampleI.txt
- awk '{FS = "\t"} {print $3 "\t" $14 "\t" $9 "\t" $13 "\t" $7}' ELelegans.txt > ELelegans_tissue.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleI.txt > SnakeBase_TE_SampleI_sort.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleI_Clear.txt > SnakeBase_TE_SampleI_Clear_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue.txt > ELelegans_tissue_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue_Clear.txt > ELelegans_tissue_Clear_Sort.txt
- join -t $'\t' SnakeBase_TE_SampleI_Clear_sort.txt ELelegans_tissue_Clear_Sort.txt > SnakeBase_SampleI_Clear_ELelegans_overlap.txt
- sed -i '/^\s*$/d' SnakeBase_SampleI_Clear_ELelegans_overlap.txt

# Overlapping with ELelegans: Sample_II from SnakeBase
- awk '{FS = "\t"} {print $37 "\t" $35 "\t" $1 "\t" $8 "\t" $9}' SnakeBase_TE.txt > SnakeBase_TE_SampleII.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleII.txt > SnakeBase_TE_SampleII_sort.txt
- sort -t $'\t' -k 1,1 -n SnakeBase_TE_SampleII_Clear.txt > SnakeBase_TE_SampleII_Clear_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue.txt > ELelegans_tissue_sort.txt
- sort -t $'\t' -k 1,1 -n ELelegans_tissue_Clear.txt > ELelegans_tissue_Clear_Sort.txt
- join -t $'\t' SnakeBase_TE_SampleII_Clear_sort.txt ELelegans_tissue_Clear_Sort.txt > SnakeBase_TE_SampleII_Clear_ELelegans_overlap.txt
  (Not working)
  
 # Visualization on Snakebase - again
- grep "elegans" SnakeBase_ALL.txt > SnakeBase_TE.txt
- grep "Year" SnakeBase_TeitsworthWorkingFile_ALL.txt > SnakeBase_TE_1.txt
- cat SnakeBase_TE.txt >> SnakeBase_TE_1.txt
- mv SnakeBase_TE_1.txt SnakeBase_TE.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE.txt > SnakeBase_TE_tissue_blood.txt
- awk '{FS = "\t"} {print $8}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1|uniq > b_tissue_blood.txt
- awk '{FS = "\t"} {print $8 "\t" $1 "\t" $9}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1 > a_tissue_blood.txt
-> a_tissue_blood.txt -> a_tissue_blood.csv
- cat a_tissue_blood.csv | uniq -c| awk '{ print $1 "," $2}' > c_tissue_blood.csv

____________________________________________________________________________________________________________________________
