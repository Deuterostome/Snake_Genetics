# Snake_Genetics
For Garter Snake Genetics

- git clone git@github.com:Deuterostome/Snake_Genetics.git
- awk '{FS = ","} {print $3}' ELelegans_csv.csv > Elelegans_tissue_ID.txt
- awk '{FS = ","} {print $35}' SnakeBase_csv.csv > SnakeBase_tissue_SampleI.txt
- awk '{FS = ","} {print $37}' SnakeBase_csv.csv > SnakeBase_tissue_SampleII.txt
- grep -F -x -f Elelegans_tissue_ID.txt SnakeBase_tissue_SampleI.txt > repeat_I.txt
- grep -F -x -f Elelegans_tissue_ID.txt SnakeBase_tissue_SampleII.txt > repeat_II.txt
