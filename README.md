__Protocolo:__

+ Daniel Felipe Villa Rengifo

+ Lenguaje: R

+ Tema: Manejo de listas en R

+ Fuentes:
  
  1. [Tutorials Points](https://www.tutorialspoint.com/r/r_lists.htm)
  
  2. [geeksforgeeks](https://www.geeksforgeeks.org/operations-on-lists-in-r-programming/)
  
# ¿Qué es una lista en R?

Una lista en R es el objeto que contiene elementos de diferentes tipos - como cadenas, números, vectores y otras listas dentro de ella.

Una lista en R también puede contener una matriz o una función como sus elementos. La lista se crea utilizando la función `list()` en R. En otras palabras, una lista es un vector genérico que contiene otros objetos.

> NOTA:
Un vector que tiene todos los elementos del mismo tipo se llama vector atómico, pero un vector que tiene elementos de diferentes tipos se llama lista.
>
>
> Podemos comprobar si es una lista con la función `typeof()` y encontrar su longitud utilizando `length()`.

```{r}
# Crearemos diferentes estructuras de datos para almacenarlas en una lista:
message("\n# Crearemos diferentes estructuras de datos para almacenarlas en una lista:")

## Vector:
print("## Vector:")
vnum <- c(1,2,3)

vchar <- c("Terminator", "Fast&Furious", "Love&Mounster")

vlog <- c(TRUE, FALSE, FALSE, TRUE)

lista_vec <- list(vnum, vchar, vlog)

lista_vec

# Averiguemos si es una lista:
message("\n# Averiguemos si es una lista:")
typeof(lista_vec)

# Averiguemos su longitud:
cat("La longitud de la lista es =", length(lista_vec))
```

# ¿Como Crear Listas?

+ La lista se puede crear con la función `list()`.

+ Su estructura se puede examinar con la función `str()`.

```{r}
# Vamos a crear una lista que contenga cadenas, números, vectores y valores lógicos.
message("\n# Vamos a crear una lista que contenga cadenas, números, vectores y valores lógicos.")

lista_variada <- list("Cadena", "Felipe", c(1,2,3), TRUE, 12.21331, 23421L)

cat("\n>lista_variada <- list(\"Cadena\", \"Felipe\", c(1,2,3), TRUE, 12.21331, 23421L)", "\n \nOUTPUT:\n \n")

print(lista_variada)

# Estrutura de la lista:
message("\n# Estrutura de la lista:")

str(lista_variada)
```

# ¿Cómo nombrar los elementos de la lista?

## Nombrando listas a través de etiquetas:

En este ejemplo, `a`, `b` y `c` se denominan etiquetas, lo que facilita la referencia a los componentes de la lista.

```{r}
# Etiquetas en la lista:
message("\n# Etiquetas en la lista:")
x <- list("a" = 2.5, "b" = TRUE, "c" = 1:3)
```

Sin embargo, las etiquetas son opcionales. Podemos crear la misma lista sin las etiquetas. En este caso, los índices numéricos se utilizan por defecto.

```{r}
# Listas sin etiquetas:
message("\n# Listas sin etiquetas:")
x <- list(2.5,TRUE,1:3)
```


## Nombrar listas en R con `names()`

Nombrar listas en R, se realiza de la siguiente manera:

```{r}
# Vamos a crear una lista que contenga un vector, una matriz y una lista:
message("\n# Vamos a crear una lista que contenga un vector, una matriz y una lista:")

ListaDeDatos <- list(c("Superman", "Batman", "Aquaman"), matrix(-5:5, nrow = 2), list(TRUE, FALSE, 12.121, 234L))

## Nombremos los elementos de la lista:
message("\n## Nombremos los elementos de la lista:")

names(ListaDeDatos) <- c("SuperHeroes", "Matriz", "Lista Logica & Numerica")

cat("\n> names(ListaDeDatos) <- c(\"SuperHeroes\", \"Matriz\", \"Lista Logica & Numerica\")", "\n \nOUTPUT:\n \n")
print(ListaDeDatos)
```

# ¿Cómo acceder a la lista de elementos de R?

Se puede acceder a las listas de forma similar a los vectores. Se pueden utilizar vectores enteros, lógicos o de caracteres para la indexación.


```{r ejemplo1}
# Utilizaremos la lista que hemos creado en la sección anterior:
message("\n# Utilizaremos la lista que hemos creado en la sección anterior:")

print(ListaDeDatos)

# Acceder al primer elemento de la lista:
cat("\n# Acceder al primer elemento de la lista:\n", "print(ListaDeDatos[1])", "\n \nOUTPUT:\n")

print(ListaDeDatos[1])

# también utilizando el nombre del elemento, podemos acceder a los elementos de la lista:
cat("\n# también utilizando el nombre del elemento, podemos acceder a los elementos de la lista:", "\n \n> print(ListaDeDatos$Matriz)", "\n \nOUTPUT:\n \n")

print(ListaDeDatos$Matriz)


```

> Nota =
T: `TRUE`
F: `FALSE`

```{r ejemplo2}
# Llamamos a un elemento de una lista:
message("\n# Llamamos a un elemento de una lista:")
x <- list("Daniel", 20, c("Español", "Ingles"))
names(x) <- c("Nombre", "Edad", "Lengua_Materna")

## Lista:
print("## Lista:")
print(x)

## índice mediante vector de enteros:
message("\n## índice mediante vector de enteros:\n")
cat("x[c(1:2)]", "\n \nOUTPUT:\n")

print(x[c(1:2)])

## usando un entero negativo para excluir el segundo componente:
message("\n## usando un entero negativo para excluir el segundo componente:")

cat("x[-2]", "\n \nOUTPUT:\n")
print(x[-2])

## índice mediante vector lógico:
message("\n## índice mediante vector lógico:")
cat("x[c(F,T,T)]", "\n \nOUTPUT:\n")

print(x[c(F,T,T)])

## índice utilizando el vector de caracteres:
message("\n## índice utilizando el vector de caracteres:")
cat("\nx[c(\"Nombre\", \"Lengua_Materna\")", "\n \nOUTPUT:\n")

print(x[c("Nombre", "Lengua_Materna")])
```

## Forma alternativa:

### Indexación:

La indexación con `[` como se muestra arriba nos dará la sublista no el contenido dentro del componente. Para recuperar el contenido, tenemos que utilizar `[[`.

Sin embargo, este enfoque nos permitirá acceder a un solo componente a la vez.


```{r}
# [ devuelve una lista:
message("\n# [ devuelve una lista:")

cat("> x[\"Nombre\"]", "\n \nOUTPUT:\n")
print(x["Nombre"])

cat("\n> typeof(x[\"Nombre\"])", "\n \nOUTPUT:\n")
print(typeof(x["Nombre"]))

# doble [[ retorna Un numero real:
message("\n# doble [[ retorna Un numero real:")

cat("> x[[\"Edad\"]]", "\n \nOUTPUT:\n")
print(x[["Edad"]])

cat("\n> typeof(x[[\"Edad\"]])", "\n \nOUTPUT:\n")
print(typeof(x[["Edad"]]))

```

Una alternativa a `[[`, que se utiliza a menudo al acceder al contenido de una lista, es el operador `$`.

Ambos son iguales, excepto que `$` puede hacer coincidencias parciales en las etiquetas.

```{r}
# igual que x[["nombre"]]:
message("\n# igual que x[[\"nombre\"]]:")

cat("x$Nombre", "\n \nOUTPUT:\n")
print(x$Nombre)

# La indexación puede hacerse de forma recursiva:
message("\n# La indexación puede hacerse de forma recursiva:")


cat("\nx$Lengua_Materna[1]","\n \nOUTPUT:\n")

print(x$Lengua_Materna[1])

# Esto es igual que:
cat("\n \nEsto es igual que:\n")

cat("x[[\"Lengua_Materna\"]][2]", "\n \nOUTPUT:\n")

print(x[["Lengua_Materna"]][2])
```

# ¿Cómo modificar una lista?

Podemos modificar los componentes de una lista mediante la reasignación. Podemos elegir cualquiera de las técnicas de acceso a los componentes comentadas anteriormente para modificarla.

```{r}
# Cambiemos el nombre de la lista:

cat("\nx[[\"Nombre\"]]", "\n \nOUTPUT:\n")
print(x[["Nombre"]])

message("\n# Cambiemos el nombre de la lista:")

cat("\nx[[\"Nombre\"]] <- \"Felipe\"", "\n \nOUTPUT:\n \n")

x[["Nombre"]] <- "Felipe"

print(x[["Nombre"]])
```

## ¿Cómo añadir componentes a una lista?

Añadir nuevos componentes es fácil. Simplemente asignamos valores usando nuevas etiquetas y entrará en acción.

```{r}
# Añadir un nuevo elemento:

cat("x", "\n \nOUTPUT:\n \n")
print(x)

message("\n# Añadir un nuevo elemento:")

x[["Estado Civil"]] <- "Soltero"

cat("x[[\"Estado Civil\"]] <- \"Soltero\"", "\n \nOUTPUT:\n \n")

print(x)
```

## ¿Cómo borrar componentes de una lista?

Podemos eliminar un componente asignándole `NULL`.

```{r}
# Elimiar un elemnto:

cat("str(x)", "\n \nOUTPUT:\n \n")
str(x)

message("\n# Elimiar un elemnto:")

cat("x[[\"Edad\"]] <- NULL", "\n \nOUTPUT:\n \n")

x[["Edad"]] <- NULL

cat("str(x)", "\n \nOUTPUT:\n \n")
str(x)
```


## ¿Cómo fusionar listas?

Podemos fusionar varias listas en una sola colocando todos los elementos de la lista dentro de `c()`.

```{r}
# Unir listas en R:
message("\n# Unir listas en R:")

cat("Creamos dos listas independientes, que luego se uniran con c()",
    "\n lista_num <- list(1:5)\n",
    "lista_meses <- list(\"ENERO\",\"FEBRERO\", \"MARZO\", \"ABRIL\", \"MAYO\")", "Las uniremos en una sola con el comando:\n", "\n \nunion <- c(lista_num, lista_meses)", "\n \nOUTPUT:\n \n")


lista_num <- list(1:5)

lista_meses <- list("ENERO","FEBRERO", "MARZO", "ABRIL", "MAYO")

union <- c(lista_num, lista_meses)
print(union)



```

# Listas predefinidas

Las listas de letras y nombres de meses están predefinidas:

```{r}
# Listas predefinidas de R:
message("\n# Listas predefinidas de R:")

cat("\n=> Lista del abecedario en minúscula:\n \n", letters)

cat("\n \n=> Lista del abecedario en Mayúscula:\n \n", LETTERS)

cat("\n \n=>Iniciales de los meses del año en ingles:\n \n", month.abb)

cat("\n \n=> Meses del año en ingles:\n \n", month.name)
```