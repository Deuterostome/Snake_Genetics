# Processing of table
- library("reshape2")
- Turtle = read.csv("Total_melting.csv", stringsAsFactors=FALSE)
- head(Turtle)
- T_M_2 = dcast(Turtle, Phase + ID ~ Number, value.var = 'OCR')
- write.csv(T_M_2, file = "T_M_2.csv")
