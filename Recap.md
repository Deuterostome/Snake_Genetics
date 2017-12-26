# Delete
SnakeBase_TE.txt
- awk -F "\t" '$5 != "." && $5 != "N" && $5 != "?" && $5 != "RP27"' SnakeBase_TE.txt > SnakeBase_TE_Racap.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE_Racap.txt > SnakeBase_TE_Racap_tissue_blood.txt
