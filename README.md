# 22.-feb.-16
### RECODIFICAR Y ETIQUETAR!!
## 3 abrir en dfb....
require (foreign)
sdemt315<- read.dbf("C:\\Users\\SALA-C11\\Documents\\sdemt315.dbf")##abriendo base dbf
sdemt315<- data.frame(sdemt315) ### haciendo la base de datos data frame 
help(str)
str(sdemt315)
attach(sdemt315)
table(SEX)
table(EDA)
EDA1<- as.numeric(as.character(EDA)) ##cambiamos edad a numerico
table(EDA1)
install.packages("memisc")
install.packages("lattice")
install.packages("MASS")
require(lattice)
require(MASS)
require(memisc)
help(recode)
gedad <- recode (EDA1, )




#####  Ponderar casos
 install.packages("questionr")
 require (questionr)
 c0<- table (sdemt315$SEX)
 c0
 c1<- wtd.table(sdemt315$SEX, weights = sdemt315$FAC)
 
 table(c1)
 
 ### Obtiene la table expandida con las nuevas etiquetas de clase 1. Emplea variable 
 ## FAC( factor de expansion) se asigna a una var para poder expandir
 ###### porcentajes %
 tabrama <- wtd.table(sdemt315$SEX, weights = sdemt315$FAC)
 c1.1<- round((tabrama/margin.table(tabrama))*100, 2)
 c1.1
 
 #### Obtiene las tablas con números relativos
 #### Ocupados y no ocupados
 
 sdemt315$SEX<- ordered(sdemt315$SEX, levels= c(1,2), labels= c("Hombre", "Mujeres"))
 View( sdemt315)
 c2<- wtd.table( sdemt315$SEX, weights =  sdemt315$FAC)
 c2
 
 #### ejercicio clase, etiquetar la var NAC_MES
 attach(sdemt315)
 sdemt315$NAC_MES<- ordered(sdemt315$NAC_MES, levels= c("01","02","03","04","05","06","07","08","09","10","11","12","99"), labels= c("Enero", "Febrero", "Marzo", "Abril","Mayo", "Junio", "Julio","Agosto", "Septiembre", "Octubre","Noviembre","Diciembre", "No especificado"))
 table( sdemt315$NAC_MES)
 na1<- wtd.table(sdemt315$NAC_MES, weights = sdemt315$FAC)
 na1
