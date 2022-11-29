![image](https://camo.githubusercontent.com/35e9d7d200795e6ec6bbf764d7f700d8da81cb5bc28ef9787d104a22eb3293a6/68747470733a2f2f696d67732e7365617263682e62726176652e636f6d2f37315a705a5949444b4a46463468797a765a5f4b6133636f2d625875356d5330756f496a637635757679342f72733a6669743a313230303a3638373a312f673a63652f6148523063446f764c336433647935312f593239734c6d31344c324e76626e526c2f626e51765932317a4c7a6b76615731682f5a3255765657526c51305644556c4d342f4d4734756347356e)
# Universidad de Colima
### Facultad de Ingenieria Mecanica y Electrica
### Ingenieria en Computacion Inteligente
##### Estudiante: Diana Laura Llamas Alcaraz
##### Profesor: Dr. Walter Alexander Mata Lopez
---
## Introduccion:

Este es un portafolio de la tercera parcial en la materia de programacion funcional de la carrera de ICI. 
Donde estaran adjuntos los diferentes codigos de las clases en las que trabajamos. En esta parcial trabajamos con el lenguaje de programación de 
Elixir.

---
# Tercera Parcial

## Instalación de Elixir y el uso de Shell


## Utilización de shell:
``` Elixir
    C:\Users\admin>iex
    Interactive Elixir (1.14.2) - press Ctrl+C to exit (type h() ENTER for help)
    iex(1)> 5 +4
    9
    iex(2)> 5 +
    ...(2)> 4
    9
    iex(3)>

```
### Para pedir ayuda del Shell:
``` Elixir
    iex()> h
    * IEx.Helpers
```
### Variables:
``` Elixir
    C:\Users\admin>iex
    Interactive Elixir (1.14.2) - press Ctrl+C to exit (type h() ENTER for help)
    iex(1)> dia_semana = 7
    7
    iex(2)> dia_semana
    7
    iex(3)> dia_semana * 2
    14
```
### Inmutabilidad:
``` Elixir
    iex(1)> dia_semana = 5
    5
    iex(2)> dia_semana
    5
    iex(3)> dia_semana = 7
    7
    iex(4)> dia_semana
    7
```
## Estructura del código

### Funcion sin argumentos: 
``` Elixir
    defmodule HolaMundo do
      def mensaje do
        IO.puts("Hola mundo")
      end
    end
```
###  Funcion con argumentos:
``` Elixir
    defmodule Calculadora do
      def suma(n1,n2) do
        n1 + n2
      end
    end
```
### Funcion modulo:
``` Elixir
    defmodule Calculadora do
      def suma(n1,n2) do
        n1 + n2
      end
    end

    defmodule Areas do
      def area_cuadrado(1) do
        1 * 1
      end
    end
```
### Reglas de los modulos 
``` Elixir
    defmodule Geometria.Cuadrado do
      def perimetro(1) do
        4 * 1
      end
    end

    defmodule Geometria.Rectangulo do
      def perimetro(11,12) do
        2*11 + 2*12
      end
    end
    alias Geometria.Cuadrado
```
### También:
``` Elixir
    defmodule Geometria do
      defmodule Cuadrado do
        def perimetro(1) do
          4*1
        end
      end
      defmodule Rectangulo do
        def perimetro(11,12) do
          2*11 + 2*12
        end
      end
    end
```
### Las funciones pueden expresarse de manera condensada:
``` Elixir
    defmodule Geometria do
      def perimetro_cuadrado(1), do: 4*1
      def perimetro_rectangulo(11,12), do: 2*11 + 2*12
    end
```
### Invocaciones internas de una función no requieren del prefijo del nombre del módulo:
``` Elixir
    defmodule Geometria do
      def perimetro1(l), do: cuadrado(l)
      def perimetro2(l), do: Geometria.cuadrado(l)
      def cuadrado(l), do: 4*l
     end
```
### Visibilidad de funciones:
 ``` Elixir
     defmodule TestPublicoPrivado do
      def funcion_publica(msg) do
      IO.puts("#{msg} publico")
      funcion_privada(msg)
      end
      defp funcion_privada(msg) do
      IO.puts("#{msg} privado")
      end
     end
```
###  Modulo Geometría:
``` Elixir
     defmodule Geometria do
      def perimetro1(l), do: cuadrado(l)
      def perimetro2(l), do: Geometria.cuadrado(l)
      defp cuadrado(l), do: 4*l
     end
```
### Operador pipeline:
``` Elixir
     defmodule Operaciones do
      def suma(n1,n2), do: n1 + n2
      def cuadrado(n), do: n * n
     end
```
### Obtener el cuadrado de la suma de 2 números:
``` Elixir
    defmodule Operaciones do
     def suma(n1,n2), do: n1 + n2
     def cuadrado(n), do: n * n
    end
```
### Mediante un módulo test que realice las pruebas se podría realizar de la siguiente forma:
``` Elixir
    defmodule Operaciones do
     def suma(n1,n2), do: n1 + n2
     def cuadrado(n), do: n * n
    end
    defmodule Test do
     def start do
     4 |> Operaciones.suma(5) |>Operaciones.cuadrado
     end
    end

```
## Estructura del código en Elixir

### Polimorfismo (Sobrecarga):
``` Elixir
    defmodule Rectangulo do
      def area(l) do
      l * l
      end
      def area(l1,l2) do
      l1 * l2
      end
     end
```
### Haciendo que una función dependa de otra de diferente aridad:
``` Elixir
     defmodule Calculadora do
      def suma(n) do
      suma(n,0)
      end
      def suma(n1,n2) do
      n1 + n2
      end
     end
```
### Argumentos por defecto:

 - #### Se pueden especificar argumentos por defecto mediante el operador
``` Elixir
    defmodule Calculadora do
     def suma(n1,n2 \\ 0) do
     n1 + n2
     end
    end
```
 ### Se puede utilizar cualquier combinación de argumentos por defecto:
``` Elixir
    defmodule Calculadora do
     def funcion(n1,n2 \\ 0, n3 \\ 1, n4, n5 \\ 2) do
     n1 + n2 + n3 + n4 + n5
     end
    end
```
### Imports:
``` Elixir
    import ModuloImportado
      defmodule ModuloMain do
       def main do
       IO.puts("Funcion main")
       funcion_importada("Esta funcion es importada")
       end
      end
  ```
  - ### Creamos el Módulo a importar modsec.ex
  - ### Escribimos el siguiente código:
  ``` Elixir
        defmodule ModuloImportado do
         def funcion_importada(msg) do
         IO.puts(msg)
         end
        end
  ```
  ### Si no se quiere importar el módulo, se puede utilizar de manera directa indicando el módulo y la función esto es: 
  ``` Elixir
    defmodule ModuloMain do
      def main do
      IO.puts("Funcion main")
      ModuloImportado.funcion_importada("Esta funcion es importada")
      end
     end
```
### Alias
``` Elixir    
    defmodule ModuloMain do
      alias ModuloImportado, as: MI

      def main do
      IO.puts("Funcion main")
      MI.funcion_importada("Esta funcion es importada con alias")
      end
     end
```
### Atributos de módulo
 
 - ### Existen los atributos en tiempo de compilación (Mientras están cargados).
 ``` Elixir
       defmodule Geometria do
        @pi 3.141592
        def area(r) do
        r*r*@pi
        end
        def circunferencia(r) do
        2 * r * @pi
        end
       end
``` 
### Sirven para documentar módulos y funciones:
``` Elixir
        defmodule Geometria do
         @moduledoc "Calcula el area y el perimetro de un circulo"
         @pi 3.141592
         @doc "calcula el area del circulo"
         def area(r), do: r*r*@pi
         @doc "calcula el perimetro de un circulo"
         def circunferencia(r), do: 2 * r * @pi
        end
```
## Secuencias de escape:
```elixir
        IO.puts("1. Este es un mensaje")
        IO.puts("2. Este es un \n mensaje")
        IO.puts("3. Este es un \"mensaje\"")
        IO.puts("4. Este es un \\mensaje\\")
        IO.puts("5. Este \t es \tun \t mensaje")
        IO.puts("4. Este
        es un
        mensaje")
```
## Concatenacion de Cadenas:
```elixir
        defmodule Cadena do
         def concatenar(cad1, cad2, separador \\ " ") do
         cad1 <> separador <> cad2
         end
        end
    Fundamentos de programación funcional con Erlang y Elixir,
        IO.puts(Cadena.concatenar("Hola", "Mundo"))
        IO.puts(Cadena.concatenar("Hola", "Mundo", "<->"))
```

## Funciones:
```elixir
    defmodule Calculadora do
     def div(_,0) do
     {:error, "No se puede dividir por 0"}
     end
     def div(n1, n2) do
    Fundamentos de programación funcional con Erlang y Elixir,
     {:ok, "El resultado es: #{n1/n2}"}
     end
    end
    IO.inspect(Calculadora.div(5,0))
    IO.inspect(Calculadora.div(5,3))
```

## Funciones invertidas:
```elixir
    defmodule Calculadora do
     def div(n1, n2) do
     {:ok, "El resultado es: #{n1/n2}"}
     end
     def div(_,0) do
     {:error, "No se puede dividir por 0"}
     end
    end
    IO.inspect(Calculadora.div(5,0))
    IO.inspect(Calculadora.div(5,3))
```

## Guardas:
``` elixir
    defmodule Numero do
     def cero?(0), do: true
     def cero?(n) when is_integer(n), do: false
     def cero?(_), do: "No es entero"
    end

    IO.puts(Numero.cero?(0))
    IO.puts(Numero.cero?(2))
    IO.puts(Numero.cero?("3"))
```

## Condicionales

- ### EJEMPLO 1
``` elixir
    defmodule Persona1 do
     def sexo(sex) do
     if sex == :m do
     "Masculino"
     else
     "Femenino"
     end
     end
    end
```
- ### EJEMPLO 2
``` elixir
    defmodule Persona2 do
     def sexo(sex) do
     if sex == :m do
     "Masculino"
     else if sex == :f do
     "Femenino"
    Fundamentos de programación funcional con Erlang y Elixir,
     else
     "Sexo desconocido"
     end
     end
     end
    end
```
## Case:
``` elixir
    defmodule Persona3 do
     def sexo(sex) do
     case sex do
     :m -> "Masculino"
     :f -> "Femenino"
     _ -> "Sexo desconocido"
     end
     end
    end
```
## Match con funciones:
``` elixir
    defmodule Persona4 do
     def sexo(sex) when sex == :m do
     "Masculino"
     end
     def sexo(sex) when sex == :f do
     "Femenino"
     end
     def sexo(_sex) do
     "sexo desconocido"
     end
    end
``` 

## Match con Funciones:
``` elixir
    defmodule Persona5 do
     def sexo(sex) when sex == :m, do: "Masculino"
     def sexo(sex) when sex == :f, do: "Femenino"
     def sexo(_sex), do: "sexo desconocido"
    end
``` 

## Cond:
``` elixir
    defmodule Persona6 do
     def sexo(sex) do
     cond do
     sex == :m -> "Masculino"
     sex == :f -> "Femenino"
     true -> "Sexo desconocido"
     end
     end
    end
``` 

# Herramienta mix
## Documentacion con ExDoc:v
``` elixir
    defp deps do
     [
     {:ex_doc, "~>0.12"}
     ]
     end
 ``` 
- ### Ejemplo 1
 ``` elixir
    defmodule Matematicas do
     def calculadora(opcion,{n1,n2}) do
     case opcion do
     "+" -> n1+n2
     "-" -> n1-n2
     "/" when n2 != 0 -> n1/n2
     "/" when n2 == 0 -> "No se puede dividir por 0"
     "*" -> n1*n2
     _ -> :error
     end
     end
    end
    IO.inspect Matematicas.calculadora("+",{5,4})
    IO.inspect Matematicas.calculadora("-",{5,4})
    IO.inspect Matematicas.calculadora("/",{5,4})
    IO.inspect Matematicas.calculadora("/",{5,0})
    IO.inspect Matematicas.calculadora("*",{5,4})
``` 

## Cond 
- ### Ejemplo 1
``` elixir
    defmodule DiaSemana do
     def dia(d) do
     cond do
     d == 1 -> "Lunes"
     d == 2 -> "Martes"
     d == 3 -> "Miercoles"
     d == 4 -> "Jueves"
     d == 5 -> "Viernes"
     d == 6 -> "Sabado"
     d == 7 -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia(1)
    IO.puts DiaSemana.dia(2)
    IO.puts DiaSemana.dia(3)
    IO.puts DiaSemana.dia(4)
    IO.puts DiaSemana.dia(5)
    IO.puts DiaSemana.dia(6)
    IO.puts DiaSemana.dia(7)
    IO.puts DiaSemana.dia(8)
```
- ### Ejemplo 2
``` elixir
    defmodule DiaSemana do
     def dia(d) do
     cond do
     d == "l" or d == "L" -> "Lunes"
     d == "ma" or d == "MA" -> "Martes"
     d == "mi" or d == "MI" -> "Miercoles"
     d == "j" or d == "J" -> "Jueves"
     d == "v" or d == "V" -> "Viernes"
     d == "s" or d == "S" -> "Sabado"
    Fundamentos de programación funcional con Erlang y Elixir,
     d == "d" or d == "D" -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia("l")
    IO.puts DiaSemana.dia("ma")
    IO.puts DiaSemana.dia("mi")
    IO.puts DiaSemana.dia("j")
    IO.puts DiaSemana.dia("v")
    IO.puts DiaSemana.dia("s")
    IO.puts DiaSemana.dia("d")
    IO.puts DiaSemana.dia("L")
    IO.puts DiaSemana.dia("MA")
    IO.puts DiaSemana.dia("MI")
    IO.puts DiaSemana.dia("J")
    IO.puts DiaSemana.dia("V")
    IO.puts DiaSemana.dia("S")
    IO.puts DiaSemana.dia("D")
    IO.puts DiaSemana.dia("Ma")
    IO.puts DiaSemana.dia("mA")
```
- ### Ejemplo 3
``` elixir
    defmodule DiaSemana do
     def dia(d) do
     d = String.upcase(d)
     cond do
     d == "L" -> "Lunes"
     d == "MA" -> "Martes"
     d == "MI" -> "Miercoles"
     d == "J" -> "Jueves"
     d == "V" -> "Viernes"
     d == "S" -> "Sabado"
     d == "D" -> "Domingo"
     true -> "Dia no valido"
     end
     end
    end
    IO.puts DiaSemana.dia("l")
    IO.puts DiaSemana.dia("ma")
    IO.puts DiaSemana.dia("mi")
    IO.puts DiaSemana.dia("j")
    IO.puts DiaSemana.dia("v")
    IO.puts DiaSemana.dia("s")
    IO.puts DiaSemana.dia("d")
    IO.puts DiaSemana.dia("L")
    IO.puts DiaSemana.dia("MA")
    IO.puts DiaSemana.dia("MI")
    IO.puts DiaSemana.dia("J")
    IO.puts DiaSemana.dia("V")
    IO.puts DiaSemana.dia("S")
    IO.puts DiaSemana.dia("D")
    IO.puts DiaSemana.dia("Ma")
    IO.puts DiaSemana.dia("mA")

``` 

## Unless

- ### Ejemplo 1
``` elixir
    defmodule MayorDeEdad do
     def mayor1(edad) do
     unless edad >= 18 do
     "Es menor de edad"
     end
     end
    end
```
- ### Ejemplo 2
```elixir
    defmodule MayorDeEdad do
     def mayor1(edad) do
     unless edad >= 18 do
     "Es menor de edad"
     end
     end
     def mayor2(edad) do
     if edad < 18 do
     "Es menor de edad"
     end
     end
    end
```
## Funciones Anonimas:

- ### Ejemplo 1
```elixir
    defmodule Calculadora do
     def suma(n1,n2), do: n1+n2
    end
    suma_anonima = fn(n1,n2) -> n1 + n2 end
    IO.puts(Calculadora.suma(5,4))
    IO.puts(suma_anonima.(5,5))
```
- ### Ejemplo 2
```elixir
    mayor? = fn(n1,n2) -> if n1 > n2 do true else false end end
    IO.inspect(mayor?.(4,5))
    IO.inspect(mayor?.(5,4))
    IO.inspect(mayor?.(5,5))
```
- ### Ejemplo 3
 ```elixir
    mayor? = fn(n1,n2) -> if n1 > n2 do :si else :no end end
    res = mayor?.(4,5)
    IO.puts res
    res = mayor?.(5,4)
    IO.puts res
```
- ### Ejemplo 4
```elixir
    mayor = fn(n1,n2) ->
     if n1 > n2 do
     {:ok, "#{n1} > #{n2}"}
     else
     {:error, "#{n1} <= #{n2}"}
     end
    end
    IO.inspect mayor.(4,5)
    IO.inspect mayor.(5,4)
    IO.inspect mayor.(5,5)
```
- ### Ejemplo 5
```elixir
    mayor = fn(n1,n2) ->
     if n1 > n2 do
     {:ok, "#{n1} > #{n2}"}
     else
     {:error, "#{n1} <= #{n2}"}
     end
    end
    {status, res} = mayor.(4,5)
    IO.puts status
    IO.puts res
    {status, res} = mayor.(5,4)
    IO.puts status
    IO.puts res
```

### Operador Pipe:
```elixir
    sum = 0
    lista = [1,2,3,4,5]
    lista = tl(lista)
    IO.inspect(lista)
    [num|lista] = lista
    #para sacar el 2
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 3
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 4
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    #para sacar el 5
    [num|lista] = lista
    IO.inspect(num)
    IO.inspect(lista)
    sum = sum + num
    IO.inspect(sum)
    IO.puts("EL resultado es: #{sum*sum}")
```
- ### Solucion 1
```elixir
    defmodule PipeTest do
     def cuadrado(n), do: n*n
     def suma(lista) do
     Enum.sum(lista)
     end
    end
    IO.puts("#{PipeTest.cuadrado(PipeTest.suma(tl([1,2,3,4,5])))}")
```
- ### Solucion 2
```elixir
    defmodule PipeTest do
     def cuadrado(n), do: n*n
     def suma(lista) do
     Enum.sum(lista)
     end
     def csc(lista) do
     lista
     |> tl
     |> suma
     |> cuadrado
     end
    end
    IO.puts("#{PipeTest.csc([1,2,3,4,5])}")

```

## Herramienta de depuracio(debugging):
```elixir
        ddefmodule PipeTest do
         def cuadrado(n), do: n*n
         def suma(lista) do
         Enum.sum(lista)
         end
         def csc(lista) do
         lista
         |> tl
         |> IO.inspect
         |> suma
         |> IO.inspect
         |> cuadrado
         end
        end
        IO.puts("#{PipeTest.csc([1,2,3,4,5])}")
```
## Ciclo for:
```elixir
        for x <- 1..10 do
         IO.puts(x)
        end
```      
 - ### Ejemplo 2
```elixir
        sum = 0
        for x <- 1..10 do
         sum = sum + x
        end
        IO.inspect(sum)

        #Quitando sum para evitar los warnings

        for x <- 1..10 do
         sum = sum + x
        end
        IO.inspect(sum)

        #Asignando el for a la variable sum
        #Eliminando el acumulador dentro del for

        sum = for x <- 1..10 do
         x
        end
        IO.inspect(sum)

        #Al saber que lo que genera es una lista, se puede utilizar la función sum del módulo Enum

        sum = for x <- 1..10 do
         x
        end
        IO.puts Enum.sum(sum)

        #Se puede expresar en una sola línea de código: 

        IO.puts Enum.sum(1..10)
```







