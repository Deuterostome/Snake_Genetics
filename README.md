## Snake_Genetics
 For Garter Snake Genetics
- git clone git@github.com:Deuterostome/Snake_Genetics.git

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

# Finding out the repeat in Database
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
  
 # Visualization on Snakebase - Sex recruited
- grep "elegans" SnakeBase_ALL.txt > SnakeBase_TE.txt
- grep "Year" SnakeBase_TeitsworthWorkingFile_ALL.txt > SnakeBase_TE_1.txt
- cat SnakeBase_TE.txt >> SnakeBase_TE_1.txt
- mv SnakeBase_TE_1.txt SnakeBase_TE.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE.txt > SnakeBase_TE_tissue_blood.txt
- awk '{FS = "\t"} {print $8}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1|uniq > b_tissue_blood.txt
- awk '{FS = "\t"} {print $8 "\t" $1 "\t" $9}' SnakeBase_TE_tissue_blood.txt | sort -k 1,1 > a_tissue_blood.txt
-> a_tissue_blood.txt -> a_tissue_blood.csv
- cat a_tissue_blood.csv | uniq -c| awk '{ print $1 "," $2}' > c_tissue_blood.csv

# Visualization on 2016 Snake Data Base - Sex recruited
- awk -F "\t" '$19 != "N"' EagleLakeFieldSamples_Telelgans2016_Final.txt > TE2016_blood.txt
- awk '{FS = "\t"} {print $2 "\t" $16}' TE2016_blood.txt |sort|uniq -c|awk '{ print $1 "," $2 "," $3}' > TE2016_count.csv

# Visualization on 2017 Snake Data Base - Sex recruited
- grep "ELEGANS" Data2017MasterFile.txt > TE2017.txt
- awk -F "\t" '$11 != "NA"' TE2017.txt > TE2017_blood.txt
- awk '{FS = "\t"} {print $7 "\t" $12}' TE2017_blood.txt |sort|uniq -c|awk '{ print $1 "," $2 "," $3}' > TE2017_count.csv
____________________________________________________________________________________________________________________________
