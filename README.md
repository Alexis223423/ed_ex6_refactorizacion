# Refactorización del Campus CádizTech


## 1.- Problema Nº 1

![imagen](/fotos/Error%201%20-%20Logger.png)

Este mensaje indica que se está usando muchos System.out.println() para imprimir información en consola, lo cual no es una buena práctica en aplicaciones profesionales.

Cambios que se realizan, importación de Logger:

~~~
import java.util.logging.Logger;
~~~
~~~
private static Logger logger = Logger.getLogger(GestorFutbol.class.getName());
~~~

Ejemplo de codigo anterior:
~~~
System.out.println("Nota final de Entornos de Desarrollo: " + notaFinal);
~~~

Solución:
~~~
logger.info("Nota final de Entornos de Desarrollo: " + notaFinal);
~~~

