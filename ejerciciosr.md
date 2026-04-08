---
title: "Ejercicios algoritmos"
author: "Juan Marcos Aguirre Simionato"
date: "`r Sys.Date()`"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

```{r cars}
summary(cars)
```

## Including Plots

You can also embed plots, for example:

```{r pressure, echo=FALSE}
plot(pressure)
```

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

##Ejercicio 1 

Consigna: las últimas 3 de mi DNI son 041, crear una variable que tenga ese n°.

```{r}
DNI=041
```

Consigna: crear un vector que tenga todos los números enteros desde el 1 hasta el 041.

```{r}
secuencia_dni <- (1:41)
secuencia_dni
```

##Ejercicio 2

Calcular la suma de todos los valores del vector secuencia_dni

```{r}
total <- 0
valor_final <- length(secuencia_dni)
for (i in 1:valor_final)
total <- total + i  
total
```
##Ejercicio 3

Consigna: Repetir el ejercicio anterior en Python.

```{python}
suma=0
for i in range(1,41):
  suma+= i
  print(suma)
```

##Ejercicio 4

¿Cuanto tarda en correr el código del ejercicio 2?

```{r}
inicio <- Sys.time()
total <- 0
valor_final <- 10000000*length(secuencia_dni)
for (i in 1:valor_final)
total <- total + i  
total
final <- Sys.time()
final-inicio
```
##Ejercicio 5

Consigna: repetir el ejercicio anteriror utilizando la cabeza de Gauss.

```{r}
inicio <- Sys.time()

valor_final <- 10000000 * length(secuencia_dni)

total <- valor_final * (valor_final + 1) / 2

total

final <- Sys.time()
final - inicio
```


##Ejercicio 6 

Consigna: aprende a usar tictoc

```{r}
library(tictoc)
tic("sleeping") 
A<-20
print("dormire una siestita...") 
## [1] "dormire una siestita..." 
Sys.sleep(2) 
print("...suena el despertador")
## [1] "...suena el despertador" 
toc()
```
##Ejercicio 7
```{r}
inicio_for <- Sys.time()

A <- numeric(50000)
for (i in 1:50000) {
  A[i] <- i * 2
}

final_for <- Sys.time()
tiempo_for <- final_for - inicio_for

# Generar con SEQ
inicio_seq <- Sys.time()

B <- seq(2, 100000, by = 2)

final_seq <- Sys.time()
tiempo_seq <- final_seq - inicio_seq

# Resultados
tiempo_for
tiempo_seq
```

##Ejercicio 8

Consigna: serie de Fibonacci

```{r}
# Generar Fibonacci hasta superar 1.000.000

fibonacci <- c(0,1)
iteraciones <- 2

while (fibonacci[length(fibonacci)] <= 1000000) {
  nuevo <- fibonacci[length(fibonacci)] + fibonacci[length(fibonacci)-1]
  fibonacci <- c(fibonacci, nuevo)
  iteraciones <- iteraciones + 1
}

fibonacci
iteraciones
```

##Ejercicio 9

Consigna: ordenamiento

```{r}
library(microbenchmark)

# Generar muestra grande
set.seed(123)
x <- sample(1:100000, 20000)

# Función burbuja
burbuja <- function(x){
  n <- length(x)
  for (j in 1:(n-1)){
    for (i in 1:(n-j)){
      if (x[i] > x[i+1]){
        temp <- x[i]
        x[i] <- x[i+1]
        x[i+1] <- temp
      }
    }
  }
  return(x)
}

# Benchmark
resultado <- microbenchmark(
  burbuja = burbuja(x),
  sort_R = sort(x),
  times = 5
)

resultado
```

##Ejercicio 10
Consigna: Potencia de Newton
```{r}
# Método 1: FOR (ineficiente)
inicio1 <- Sys.time()
n <- 10000000
suma1 <- 0
for (i in 1:n) {
  suma1 <- suma1 + i
}

final1 <- Sys.time()
tiempo1 <- final1 - inicio1

# Método 2: Fórmula de Gauss (eficiente)
inicio2 <- Sys.time()

suma2 <- n * (n + 1) / 2

final2 <- Sys.time()
tiempo2 <- final2 - inicio2

# Resultados
tiempo1
tiempo2
```

