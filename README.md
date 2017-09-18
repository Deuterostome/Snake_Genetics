# Snake_Genetics
For Garter Snake Genetics

- git clone git@github.com:Deuterostome/Snake_Genetics.git
- awk '{FS = $"\t"} {print $3}' ELelegans_tab.txt > Elelegans_tissue.txt
- awk '{FS = $"\t"} {print $3}' specimen_all_tab.txt > specimen_tissue.txt
- grep -F -x -f specimen_tissue.txt Elelegans_tissue.txt > repeat.txt
