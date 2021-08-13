
# Práctico 3: Importar, seleccionar y exportar datos ----------------------


# 0. Instalar paquetes ----------------------------------------------------

install.packages("tidyverse") #Instalamos el paquete. Si ya lo tenemos instalado, 
# este comando actualiza la versión del paquete a la más reciente. No es necesario 
# correr este código cada vez que usemos un paquete.

install.packages("sjmisc") #Instalamos el paquete. sjmisc nos permitirá calcular
# frecuencias y estadísticos descriptivos, entre otras cosas. 

install.packages("xlsx") #Instalamos el paquete, que nos permitirá importar y 
#exportar archivos .xlsx

library(haven) #Cargamos el paquete para utilizarlo. Este comando debe ser usado
# cada vez que iniciemos una nueva sesión en RStudio. Este paquete es parte de
# tidyverse, y permite abrir datos en formatos .sav y .dta

library(sjmisc) #Cargamos el paquete

library(xlsx) #Cargamos el paquete

library(dplyr) #Cargamos el paquete para utilizarlo. dplyr permite manipular
# datos. 


# 1. Importar datos -------------------------------------------------------

# En este práctico, se trabajó con CASEN 2020. 

datos <- read_sav("static/data/datoscasen.sav") #Señalamos a R que cree un nuevo
# objeto llamado "datos", cargando la base "datoscasen.sav" que se encuentra en
# el directorio "../project", con el comando correspondiente: "read_sav".


## 1.1. Importar datos en diversos formatos --------------------------------

# OBSERVACIÓN: las rutas (RUTADONDESEENCUENTRAN) y los nombres de los archivos (datos.formato)
# son genéricos. Cuando deban utilizar estos comandos, es fundamental que
# reemplacen el directorio y el nombre del archivo, con aquellos en que ustedes
# se encuentren trabajando. 

## a) .RData y .rds

datos <- load("RUTADONDESEENCUENTRAN/datos.RData") #Señalamos a R que cree un 
# nuevo objeto llamado "datos", cargando la base "datos.RData" que se encuentra 
# en el directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: "load".

datos <- readRDS("RUTADONDESEENCUENTRAN/datos.rds") #Señalamos a R que cree un 
# nuevo objeto llamado "datos", cargando la base "datos.rds" que se encuentra en 
# el directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: "readRDS".

## b) .dta

datos <- read_dta("RUTADONDESEENCUENTRAN/datos.dta") #Señalamos a R que cree un 
# nuevo objeto llamado "datos", cargando la base "datos.dta" que se encuentra en 
# el directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: "read_dta".

## c) .csv

datos <- read.csv("RUTADONDESEENCUENTRAN/datos.csv", sep = ";", dec = ",") 
#Señalamos a R que cree un nuevo objeto llamado "datos", cargando la base 
# "datos.csv" que se encuentra en el directorio "RUTADONDESEENCUENTRAN", con el 
# comando correspondiente: "read.csv". Si la base está en español, le indicamos 
# a R que la separación de los valores en cada línea del archivo es por punto y 
# comas (sep = ";"), y que los decimales están separados con comas (dec = ",").

datos <- read.csv2("RUTADONDESEENCUENTRAN/datos.csv") #Señalamos a R que cree un
# nuevo objeto llamado "datos", cargando la base "datos.csv" que se encuentra en
# el directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: 
# "read.csv2". Cuando los datos están en español, no es necesario especificar más 
# argumentos. 

## d) .xlsx

datos <- read.xlsx("RUTADONDESEENCUENTRAN/datos.xlsx") #Señalamos a R que cree 
# un nuevo objeto llamado "datos", cargando la base "datos.xlsx" que se encuentra 
# en el directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: 
# "read.xlsx". 

datos <- read.xlsx("RUTADONDESEENCUENTRAN/datos.xlsx", sheetIndex = 1) #Señalamos 
# a R que cree un nuevo objeto llamado "datos", cargando la primera página de la
# base "datos.xlsx" que se encuentra en el directorio "RUTADONDESEENCUENTRAN", 
# con el comando correspondiente: "read.xlsx". 

datos <- read.xlsx("RUTADONDESEENCUENTRAN/datos.xlsx", sheetName = 'NOMBREDELAPAGINA') 
#Señalamos a R que cree un nuevo objeto llamado "datos", cargando la página 
# llamada "NOMBREDELAPAGINA", de la base "datos.xlsx" que se encuentra en el 
# directorio "RUTADONDESEENCUENTRAN", con el comando correspondiente: "read.xlsx". 

datos <- read.xlsx("RUTADONDESEENCUENTRAN/datos.xlsx", startRow = 3) #Señalamos a 
# R que cree un nuevo objeto llamado "datos", cargando la base "datos.xlsx" que 
# se encuentra en el directorio "RUTADONDESEENCUENTRAN" desde la tercera fila, 
# con el comando correspondiente: "read.xlsx".

# 2. Seleccionar variables ------------------------------------------------

## 2.1. Tipos de variables

# Las variables pueden ser de tipo numeric, character, Logic o factor. Para saber
# la clase de una variable, debemos emplear el comando class(datos$variable).

class(datos$ypchtotcor)

## 2.2. Selección de variables

datos_proc <- datos %>% 
  select(ingresos_pc = ypchtotcor,
         sit_vivienda = v13,
         dorm_vivienda = v29,
         pers_vivienda = p6)

# Creamos un nuevo objeto llamado datos_proc, a partir del objeto datos, seleccionado 
# las variables ypchtotcor (renombrada como ingresos_pc), v13 (renombrada como 
# sit_vivienda), v29 (renombrada como dorm_vivienda) y p6 (renombrada como 
# pers_vivienda).

## BONUS: Inspección de variables con sjmisc

## a) Variables categóricas

frq(datos_proc$sit_vivienda) #Usar la función frq con la variable sit_vivienda 
# de los datos datos_proc.

## b) Variables numéricas

descr(datos_proc$ingresos_pc) #Usar la función descr con la variable edad de los 
# datos datos_proc.

# 3. Exportar datos ----------------------------------------------------------

## a) .RData y .rds

save(datos_proc, data = "output/data/datos_proc.RData") #Guardamos el objeto datos_proc 
# en la ruta de trabajo actual, bajo el nombre de datos_proc.RData. 

saveRDS(datos_proc, data = "output/data/datos_proc.rds") #Guardamos el objeto datos_proc 
# en la ruta de trabajo actual, bajo el nombre de datos_proc.rds. 

## b) .sav (haven)

write_sav(datos_proc, data = "output/data/datos_proc.sav") #Guardamos el objeto 
# datos_proc en la ruta de trabajo actual, bajo el nombre de datos_proc.sav. 

## b) .dta (haven)

write_dta(datos_proc, data = "output/data/datos_proc.dta") #Guardamos el objeto 
# datos_proc en la ruta de trabajo actual, bajo el nombre de datos_proc.dta. 

## b) .csv

write.csv(datos_proc, data = "output/data/datos_proc.csv") #Guardamos el objeto 
# datos_proc en la ruta de trabajo actual, bajo el nombre de datos_proc.csv.

## b) .xlsx

write.xlsx(datos_proc, data = "output/data/datos_proc.xlsx") #Guardamos el objeto 
# datos_proc en la ruta de trabajo actual, bajo el nombre de datos_proc.xlsx. 



