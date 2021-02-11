## Programación

Escribe en el código que consideres soluciones a los siguientes problemas

**1) Clases**. Escribe las clases que mejor solucionan lo siguiente:
* Dentro de un instituto hay alumnos y profesores 
* Queremos tener el nombre de los alumnos
* Queremos tener el nombre de los profesores
* Queremos tener el curso de los alumnos donde están matriculados

A continuación, se muestra una posible solución

```Java
public class Alumno {
    private String nombre:
    private int curso;
}
public class Profesor {
    private String nombre:    
}

```
Mejora esta solución adoptada

```Java
public class Alumno {
    private String nombre:
    private int[] cursos;
}

public class Instituto{
    private String[] profesores
    private Alumno[] alumnos
}

//podríamos usar listas si queremos funcionalidad más avanzada también.

```

Otra variante, dependiendo de como queramos ver el problema:

```Java
public class Instituto{
    private String[] profesores
    private Alumno[] alumnos
}

public class Curso{
    private String[] profesores_responsables
    private string Nombre
    private int id
}

public class Alumno {
    private String nombre:
    private Curso[] cursos;
}



//podríamos usar listas si queremos funcionalidad más avanzada también.

```


**2) POO**. Ten en cuenta el siguiente código escrito en Java

```Java
public class Jugador {
  private Arma arma;
  private String nombre;

  public Jugador(String nombre, Arma arma) {
    this.nombre = nombre;
    this.arma = arma;
  }

  public void setArma(Arma arma) {
    this.arma = arma;
  }

  public void action() {
    if (this.arma.type == "cuchillo") {
      System.out.println("Ataca con el cuchillo");
    } else {
      if (this.arma.type == "revolver") {
        System.out.println("Ataca con el revolver");
      } else {
        if (this.arma.type == "plasma") {
          System.out.println("ataca con plasma");
        }
      }
    }
  }
}
```

Crea un nuevo diseño de clases si es preciso para resolver unos de los principios SOLID que se está violando

```Java

abstract class Arma{
  abstract void action();
}

public class Cuchillo extends Arma{

  public void action(){
  System.out.println("Ataca con el cuchillo");
  }

}

public class Revolver extends Arma{

  public void action(){
  System.out.println("Ataca con el revolver");
  }

}

public class Plasma extends Arma{

  public void action(){
  System.out.println("Ataca con plasma");
  }

}



public class Jugador {
  private Arma arma;
  private String nombre;

  public Jugador(String nombre, Arma arma) {
    this.nombre = nombre;
    this.arma = arma;
  }

  public void setArma(Arma arma) {
    this.arma = arma;
  }


  public void action() {
  arma.action()
  }
  
}
```

<br/>
