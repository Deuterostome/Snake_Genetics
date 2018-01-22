## Understanding the recap data from snake database
# Process through Linux: from SnakeBase_TE.txt pick up the Recap data
- awk -F "\t" '$5 != "." && $5 != "N" && $5 != "?" && $5 != "RP27"' SnakeBase_TE.txt > SnakeBase_TE_Racap.txt
- awk -F "\t" '$22 != "N"||$33 != "N"' SnakeBase_TE_Racap.txt > SnakeBase_TE_Racap_tissue_blood.txt
# Process through R
- library(dplyr)
- tag = read.csv ("SnakeBase_Racap_ID.csv", header = T) # Modified from SnakeBase_TE_Racap_tissue_blood.txt
- data_2 = read.csv("SnakeBase_TE_tissue_blood.csv", header = T) # Total sampling individuals
- data_2 = arrange(data_2, Unique_ID)
- tag = arrange(tag, Unique_ID_Re)
- list_2 = merge(data_2, tag, by.x="Unique_ID", by.y="Unique_ID_Re") # Get the repeat Universal ID from these two files
- write.csv(list_2, file = "list_2.csv")
- data_2016 = read.csv("TE2016_blood.csv", header = T)
- data_2016_Recap = read.csv("TE2016_blood_Recap.csv", header = T)
- data_2016 = arrange(data_2016, UniqueID)
- data_2016_Recap = arrange(data_2016_Recap, UniqueID_Re)
- list_2016 = merge(data_2016, data_2016_Recap, by.x="UniqueID", by.y="UniqueID_Re")
- write.csv(list_2016, file = "list_2016.csv")
