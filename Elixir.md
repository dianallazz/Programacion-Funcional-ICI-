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
