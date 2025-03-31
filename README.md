# Apuntes de Bucles y Condicionales en Bash
---

## 1. Condicionales

Los condicionales permiten ejecutar diferentes bloques de código según si una condición se cumple o no.

### 1.1. Estructura Básica del `if`

La sintaxis básica de un condicional en Bash es:

```bash
if [ condición ]; then
    # Comandos si la condición es verdadera
fi
```

#### Ejemplo:
```bash
#!/bin/bash
num=5
if [ $num -gt 3 ]; then
    echo "El número es mayor que 3."
fi
```

### 1.2. `if-else`

Para ejecutar comandos alternativos cuando la condición es falsa:

```bash
if [ condición ]; then
    # Comandos si la condición es verdadera
else
    # Comandos si la condición es falsa
fi
```

#### Ejemplo:
```bash
#!/bin/bash
num=2
if [ $num -gt 3 ]; then
    echo "El número es mayor que 3."
else
    echo "El número no es mayor que 3."
fi
```

### 1.3. `if-elif-else`

Para evaluar múltiples condiciones secuencialmente:

```bash
if [ condición1 ]; then
    # Comandos si condición1 es verdadera
elif [ condición2 ]; then
    # Comandos si condición2 es verdadera
else
    # Comandos si ninguna condición es verdadera
fi
```

#### Ejemplo:
```bash
#!/bin/bash
num=7
if [ $num -lt 5 ]; then
    echo "El número es menor que 5."
elif [ $num -eq 5 ]; then
    echo "El número es igual a 5."
else
    echo "El número es mayor que 5."
fi
```

### 1.4. Operadores

#### Comparación de números:
- `-eq`: igual a
- `-ne`: no igual a
- `-gt`: mayor que
- `-ge`: mayor o igual que
- `-lt`: menor que
- `-le`: menor o igual que

#### Comparación de cadenas:
- `=`: igual a
- `!=`: diferente de
- `-z`: cadena vacía
- `-n`: cadena no vacía

#### Verificación de archivos:
- `-d`: es un directorio
- `-f`: es un fichero
- `-e`: existe

### 1.5. `case`

La estructura `case` es útil cuando hay muchas condiciones posibles y se quiere evitar el uso de múltiples `if-elif-else`.

#### Sintaxis:
```bash
case variable in
    patron1)
        # Comandos si variable coincide con patron1
        ;;
    patron2)
        # Comandos si variable coincide con patron2
        ;;
    *)
        # Comandos por defecto si no hay coincidencias
        ;;
esac
```

#### Ejemplo:
```bash
#!/bin/bash
echo "Introduce un color:"
read color

case $color in
    rojo)
        echo "Elegiste rojo."
        ;;
    azul)
        echo "Elegiste azul."
        ;;
    verde)
        echo "Elegiste verde."
        ;;
    *)
        echo "Color no reconocido."
        ;;
esac
```

---

## 2. Bucles

Los bucles permiten repetir un conjunto de comandos múltiples veces.

### 2.1. Bucle `for`

El bucle `for` se usa para iterar sobre una lista de elementos.

#### Sintaxis:
```bash
for variable in lista; do
    # Comandos a ejecutar para cada elemento
done
```

#### Ejemplo: Iterar sobre una lista de colores
```bash
#!/bin/bash
for color in rojo azul verde; do
    echo "El color es $color"
done
```

#### Ejemplo: Iterar sobre archivos en un directorio
```bash
#!/bin/bash
for archivo in *.txt; do
    echo "Procesando $archivo"
done
```

### 2.2. Bucle `while`

El bucle `while` repite comandos mientras una condición sea verdadera.

#### Sintaxis:
```bash
while [ condición ]; do
    # Comandos a ejecutar
done
```

#### Ejemplo: Contador con `while`
```bash
#!/bin/bash
contador=1
while [ $contador -le 5 ]; do
    echo "Número: $contador"
    contador=$((contador + 1))
done
```

### 2.3. Bucle `until`

El bucle `until` ejecuta comandos hasta que la condición se haga verdadera.

#### Sintaxis:
```bash
until [ condición ]; do
    # Comandos a ejecutar
done
```

#### Ejemplo:
```bash
#!/bin/bash
contador=1
until [ $contador -gt 5 ]; do
    echo "Número: $contador"
    contador=$((contador + 1))
done
```

---

## 3. Notas Adicionales

- **Uso de comillas:**  
  Siempre utiliza comillas alrededor de las variables (por ejemplo, `"$variable"`) para evitar problemas con espacios o caracteres especiales.

- **Incremento de variables:**  
  Puedes incrementar variables de dos formas:
  - **Expansión aritmética:**  
    ```bash
    contador=$((contador + 1))
    ```
  - **Usando `expr`:**  
    ```bash
    contador=$(expr $contador + 1)
    ```  
    *Nota: Al usar `expr` es crucial dejar espacios entre los operandos y operadores.*

- **Orden en el comando `find`:**  
  Algunas opciones de `find` (como `-maxdepth`) deben colocarse antes de otros predicados para evitar advertencias.

---

¡Practica estos conceptos creando tus propios scripts y experimenta con diferentes condiciones y bucles!

