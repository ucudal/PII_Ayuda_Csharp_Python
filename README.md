![UCU](/Assets/logo-ucu.png)

### FIT - Universidad Católica del Uruguay

<br>

<h1>Ayuda de C# para programadores Python</h1>

Si sabes programar en Python, este documento puede servirte para saber cómo hacer en C# las cosas que ya sabes hacer. No es una referencia completa, sólo incluimos algunos aspectos de los lenguajes. 

C# es un lenguaje <a href="https://en.wikipedia.org/wiki/Compiled_language">compilado</a> a <a href="https://en.wikipedia.org/wiki/Common_Intermediate_Language">lenguaje intermedio</a> con <a href="https://en.wikipedia.org/wiki/Type_system#STATIC">tipos de datos estáticos</a>.

Python es un lenguaje interpretado con tipos de datos dinámicos.

El ciclo habitual de desarrollo en C# implica editar uno o más archivos de código fuente, <a href="https://en.wikipedia.org/wiki/Roslyn_(compiler)">compilar</a> los archivos de texto para producir un archivo binario en <a href="https://en.wikipedia.org/wiki/Common_Intermediate_Language">lenguaje intermedio</a>, y ejecutar ese archivo binario en el <a href="https://en.wikipedia.org/wiki/Common_Language_Runtime">entorno en tiempo de ejecución</a>.

El ciclo habitual de desarrollo en Python implica ingresar una o más expresiones en un <a href="https://en.wikipedia.org/wiki/CPython">evaluador</a>, que evalúa la expresión e imprime el resultado. También es posible desarrollar en Python editando uno o más archivos de código fuente, y ejecutar esos archivos con el <a href="https://en.wikipedia.org/wiki/CPython">intérprete</a> de Python.

Los bloques de código en Python se definen mediante sangría en el código fuente, mientras que en C# se utiliza { al comienzo de un bloque y } al final.

Mientras es posible tener código Python en funciones o en métodos que pueden ser usados en expresiones, en C# el código sólo está en los métodos; no hay funciones “libres”. Algo análogo ocurre con las variables: mientras en Python puedo declarar variables globales, en C# las variables sólo pueden ser declaradas en las instancias de las clases, o en las propias clases; esto último equivale a las variables de instancia y de clase, respectivamente, que existen en Python.

Otras correspondencias o diferencias puedes encontrarlas en la tabla a continuación.

| Python | C# |
|:-|:-|
|Comentarios en línea: #|Comentarios en línea: // <sup><a href="#1">1</a></sup>|
|Comentarios en múltiples líneas comienzan y terminan con """|Comentarios en múltiples líneas comienzan con /* y terminan con */|
|if…, if…else, if…elif|if…, if…else, switch…case…default|
|for i in range(0, 3)… |for (int i = 0; i <=3; i++)…, foreach… <sup><a href="#2">2</a></sup>|
|while (i < 3)…|while (i < 3)…|
|and, or, not |& y &&<sup><a href="#3">3</a></sup>,\| y \|<sup><a href="#3">3</a></sup>\|, !|
|<, <=, >, >=, ==, !=|<, <=, >, >=, ==<sup><a href="#4">4</a></sup>, !=|
|+, -, *, /, +=, -=, *=, /=|+, -, *, /, +=, -=, *=, /=<sup><a href="#5">5</a></sup>|
|bool|bool, Boolean<sup><a href="#6">6</a></sup>|
|float|float, Single<sup><a href="#7">7</a></sup>|
|int|int, Int32<sup><a href="#8">8</a></sup>|
|str|string, String<sup><a href="#9">9</a></sup>|
|Asignar el valor y a la variable x: x = y|Asignar el valor x a la variable y del tipo T: T x = y<sup><a href="#10">10</a></sup>|
|Crear una instancia de una clase C y asignarla a la variable x: x = C()|Crear una instancia de una clase C y asignarla a la variable x: C x = new C();|
|float(…)|Convert.ToSingle(…), Single.Parse(…)<sup><a href="#11">11</a></sup>|
|int(…) |Convert.ToInt32(…), Int32.Parse(…)<sup><a href="#11">11</a></sup>|
|str(…)|Int32.ToString(…), Single.ToString(…)<sup><a href="#11">11</a></sup>|
|Cuando demo es una variable que contiene una instancia de string, demo[0]referencia el primer carácter, demo[-1] el último, demo[2:4] referencia una porción del segundo al cuarto carácter, y demo[:4] una porción del primero al cuarto carácter|Cuando demo es una variable que contiene una instancia de String, demo[0] referencia el primer carácter; no hay un equivalente en C# para acceder al último carácter<sup><a href="#12">12</a></sup> o a una porción<sup><a href="#13">13</a></sup>|
|def…|No hay un solo equivalente en C#; para los métodos la sintaxis depende de la visibilidad, si retorna un resultado o no, el tipo de datos del resultado, y otros factores.|
|class…|class…|
|self|this<sup><a href="#14">14</a></sup>|
|@classmethod|static|
|cls|El nombre de la clase|
|pass|Un bloque vacío {} o un ; puede ser similar en algunos casos, pero no existe una equivalencia exacta|
|raise…|throw…|
|with… |using…<sup><a href="#15">15</a></sup> es similar, pero no existe una equivalencia exacta|
|print(…) |Console.WriteLine(…)|
|input() |Console.ReadLine()<sup><a href="#16">16</a></sup>|
|assert…|Debug.Assert(…) es similar, pero se trata de una invocación y no de una palabra clave|
|yield|La palabra clave yield, existe en C#, pero no tiene exactamente el mismo uso que en Python|
|import |No hay un equivalente exacto en C# porque los ensamblados -análogos a los módulos o paquetes en Python- sólo pueden ser cargados dinámicamente mediante una API, a diferencia de Python que siempre son cargados dinámicamente. using es una directiva en C# que permite referenciar tipos en un espacio de nombres sin calificarlos.|

En un programa de consola en C# el punto de entrada, esto es, lo primero que se ejecuta cuando se corre el programa, típicamente es un método de clase declarada como static void Main(string[] args) o static void Main(). 
Ver https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/main-andcommand-args/

****
_<sup id="1">1</sup> Los comentarios en línea que comienzan con tres /// tienen un significado especial para generar documentación externa. Ver: https://docs.microsoft.com/en-us/dotnet/csharp/codedoc

_<sup id="2">2</sup> La cláusula foreach en C# es similar a la cláusula for en Python cuando se usa con iterables.

_<sup id="3">3</sup> La diferencia es si se evalúa el segundo operando. Ver https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-and-operator- y https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-and-operator-

_<sup id="4">4</sup> En C# el operador == compara si dos objetos son el mismo; excepto para las instancias de la clase String, donde compara el valor. El operador == puede ser sobrescrito.

_<sup id="5">5</sup> Mientras /= aplicado a objetos de tipo int en Python da como resultado un objeto de tipo float, en C# da un objeto de tipo int siempre.Ver https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/division-operator.

_<sup id="6">6</sup> En C# la palabra clave **bool** es un alias para el tipo **System.Boolean**.

_<sup id="7">7</sup> En C# la palabra clave **float** es un alias para el tipo **System.Single**.

_<sup id="8">8</sup> En C# la palabra clave **int** es un alias para el tipo **System.Int32**.

_<sup id="9">9</sup> En C# la palabra clave **string** es un alias para el tipo **System.String**.

_<sup id="10">10</sup> Aquí se muestra la declaración de la variable x del tipo T y la asignación del valor y a la variable x en la misma sentencia; es equivalente a T x; y luego x = y;. Vean que en Python no se declara el tipo de la variable, mientras en C# sí. La variable x es del tipo de y en Python, no es que no tenga tipo. Algo similar ocurre en C# al usar la palabra clave var al declarar una variable: var x = y; es equivalente a T x = y; si T es el tipo de y.

_<sup id="11">11</sup> Mientras **float()**, **int()** y **str()** son cast -conversión de tipos- en Python, los mostrados como correspondientes en C# son métodos; el concepto de cast existe en C# pero no se usa aquí como en Python.

_<sup id="12">12</sup> El último carácter se accede con demo[demo.Lenght - 1].

_<sup id="13">13</sup> Una porción se obtiene con **demo.Substring(2, 2);** noten que el segundo argumento es la cantidad de caracteres y no el final de la Proción.

_<sup id="14">14</sup> La primera variable de un método en Python referencia al objeto que recibe el mensaje que ocasiona la ejecución de ese método, y suele llamarse **self**. En C# esa referencia se obtiene mediante la palabra clave **this**, y no es un parámetro del método

_<sup id="15">15</sup> En C# using es tanto una directiva para importar un módulo como una sentencia para asegurar la ejecución de destructores.

_<sup id="16">16</sup>  Mientras input en Python permite mostrar un mensaje además de leer un valor, `Console.ReadLine()` en C# sólo lee un valor; para mostrar un mensaje, puedes usar `Console.Write()` o `Console.WriteLine()`.
