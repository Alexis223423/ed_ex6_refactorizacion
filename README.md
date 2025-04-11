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

## 2.- Problema Nº 2

![imagen](/fotos/Error%202%20-%20Complejidad%20Cognitiva.png)

Este mensaje indica que se está excediendo la complejidad cognitiva al anidar muchos if o usar muchos bucles, al estar el limite en 15 y haberlo superado teniendo una cantidad de 70, hay que bajarla haciendo metodos mas pequeños.

Método con complejidad cognitiva alta:
~~~
private static void procesaCalificaciones(Map<String, Double> notasRA) {
        StringBuilder resultado = new StringBuilder();

        if (notasRA != null) {
            for (String ra : PESOS_RA.keySet()) {
                if (notasRA.containsKey(ra)) {
                    double nota = notasRA.get(ra);
                    if (nota >= 0) {
                        if (nota <= 10) {
                            if (nota >= 9) {
                                resultado.append(ra).append(": Excelente\n");
                            } else if (nota >= 7) {
                                if (nota >= 8) {
                                    resultado.append(ra).append(": Notable Alto\n");
                                } else {
                                    resultado.append(ra).append(": Notable Bajo\n");
                                }
                            } else if (nota >= 5) {
                                if (nota >= 6) {
                                    resultado.append(ra).append(": Bien\n");
                                } else {
                                    resultado.append(ra).append(": Suficiente\n");
                                }
                            } else {
                                if (nota >= 3) {
                                    if (nota >= 4) {
                                        resultado.append(ra).append(": Insuficiente Alto\n");
                                    } else {
                                        resultado.append(ra).append(": Insuficiente Medio\n");
                                    }
                                } else {
                                    if (nota > 0) {
                                        resultado.append(ra).append(": Insuficiente Bajo\n");
                                    } else {
                                        resultado.append(ra).append(": Muy Deficiente\n");
                                    }
                                }
                            }
                        } else {
                            resultado.append("Nota para ").append(ra).append(" es mayor que 10. Error.\n");
                            resultado.append("Nota para ").append(ra).append(" es mayor que 10. Error.\n");
                        }
                    } else {
                        resultado.append("Nota para ").append(ra).append(" es negativa. Error.\n");
                        resultado.append("Nota para ").append(ra).append(" es negativa. Error.\n");
                    }
                } else {
                    resultado.append("No se encontró nota para ").append(ra).append(". Se asumirá 0.\n");
                }
            }
        } else {
            resultado.append("No se proporcionaron notas.\n");
        }

        logger.info(resultado.toString());
    }
~~~

Métodos más reducidos:
~~~

~~~

## 3.- Problema Nº 3

![imagen](/fotos/Error%203%20-%20Eliminar%20label.png)

En este error se indica que se debe eliminar "label" porque no se está usando:

Código anterior:
~~~
case 7:
                label: {
                    resultado = "Notable";
                    break;
                }
~~~
Coódigo actual:
~~~

~~~
