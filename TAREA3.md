# TAREA 3 
* UNIVERSIDAD DE SAN CARLOS DE GUATEMALA 
* Laboratorio de Lenguajes Formales de Programación 
* Linda Madelin Fabiola Quelex Sep
* 201403745

# 1. Gramática de Lenguaje JSON

## 1.1. Alfabeto
### 1.1.1. Símbolos terminales
#### 1.1.1.1. Expresiones regulares

| Token              |               Patrón               |
| ------------------ | :--------------------------------: |
| llave_abierta      |                 {                  |
| llave_cerrada      |                 }                  |
| comilla_doble      |                 "                  |
| dos_puntos         |                 :                  |
| coma               |                 ,                  |
| clave              |       [a-zA-Z][a-zA-Z_0-9]*        |
| datos_string_valor |          \".*[^"][^\n]\"           |
| dato_arreglo_valor | \[((("([^\n]l(.))*")l\d+)(,?)*)*\] |
| dato_numero_valor  |                \d+                 |



### 1.1.2. Símbolos no terminales

| Token       | Descripción                                       |
| ----------- | ------------------------------------------------- |
| id          | Estado inicial de la sintáxis                     |
| EXPRESSIONS | Lista de expresiones separadas por salto de linea |
| E           | Cualquier expresión                               |

## 1.2. Sintáxis

### 1.2.1. Precedencia

| Precedencia | Operador |
| :---------: | -------- |
|      1      | arreglo  |


### 1.2.2. Producciones
```
Símbolo inicial = id

id: llave_abierta EXPRESSIONS llave_cerrada

EXPRESSIONS : EXPRESSIONS coma E
            | E 

E : commilla_doble clave comilla_doble dos_puntos datos_string_valor 
  | commilla_doble clave comilla_doble dos_puntos dato_arreglo_valor 
  | commilla_doble clave comilla_doble dos_puntos dato_numero_valor 



```