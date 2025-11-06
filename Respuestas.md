# Guía de trabajo - Implicancias de la Herencia

**Nombre: Ramón Novoa**
**Matricula: 21891216824**

## 1.  Considere que la clase Persona es lo suficientemente abstracta para permitir representar elementos propios del dominio problema ¿Qué podría hacer para mejorar aquello?

La clase `Persona` se puede hacer más abstracta para representar de mejor forma los elementos comunes del contexto.  
Esto se logra convirtiéndola en una **superclase abstracta**, que contenga los atributos y métodos generales que comparten todas las personas, y luego crear **subclases** más específicas que hereden de ella.

Por ejemplo:

```java
abstract class Persona {
    protected String nombre;
    protected int edad;

    public abstract void presentarse();
}

class Niño extends Persona {
    private String escuela;

    @Override
    public void presentarse() {
        System.out.println("Hola, soy un niño y voy a la escuela " + escuela);
    }
}
```

De esta forma, `Persona` actúa como una clase base que puede extenderse con diferentes tipos de personas (niños, empleados, profesores, etc.), mejorando la **reutilización** y **organización** del código.

## 2. ¿Cómo podría en el Caso1 representar una situación más genérica para el caso de los animales?

Para representar una situación más genérica en el caso de los animales, se puede crear una **superclase `Animal`** que defina los comportamientos comunes como `comer()` o `hacerSonido()`.  
Luego, las clases `Perro` y `Gato` heredan de `Animal` y personalizan su comportamiento.

```java
abstract class Animal {
    protected String nombre;
    protected String color;

    public abstract void hacerSonido();
    public void comer() {
        System.out.println(nombre + " está comiendo.");
    }
}

class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau guau!");
    }
}

class Gato extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Miau!");
    }
}
```

Con esta estructura, se puede agregar fácilmente cualquier otro tipo de animal sin duplicar código, manteniendo un modelo más escalable y genérico.

## 3. Si consideramos ahora que una universidad no se encuentra compuesta de carreras sino que se compone de facultades y éstas a su vez se conforman de departamentos independientes. ¿Cómo cambia eso sus diagramas de clases?

Originalmente, la estructura podía ser algo como:

```
Universidad ──► Carrera ──► Estudiante
```

Pero al considerar que la universidad está compuesta por **facultades**, y estas a su vez por **departamentos**, el diagrama cambia a:

```
Universidad ──► Facultad ──► Departamento ──► Estudiante / Profesor / Curso
```

**Cambios principales:**
- `Universidad` ahora tiene una relación de **composición** con `Facultad`.
- `Facultad` tiene una **composición** con `Departamento`.
- `Departamento` se relaciona con `Persona` (ya que puede tener estudiantes y profesores).

Esto mejora la representación jerárquica y hace el modelo más fiel a la estructura real de una universidad.

## 4. Aplicando el mismo razonamiento anterior ¿Cómo se podría generalizar el análisis hecho en el Caso2 en la clase Persona, Moto y Empresa Naviera?

En el Caso 2, se pueden aplicar los mismos principios de **herencia** y **generalización** para simplificar y hacer el modelo más reutilizable.

- La clase `Persona` puede ser una superclase de `Empleado` o `Cliente`.
- La clase `Moto` puede heredar de una clase más genérica llamada `Vehiculo`.
- La `EmpresaNaviera` puede extender una clase base `Empresa`.

Ejemplo de código:

```java
class Empresa {
    protected String nombre;
    protected String direccion;
}

class EmpresaNaviera extends Empresa {
    private List<Departamento> departamentos;
}

class Persona {
    protected String nombre;
}

class Empleado extends Persona {
    private String cargo;
    private Departamento departamento;
}

abstract class Vehiculo {
    protected String marca;
    protected String modelo;
}

class Moto extends Vehiculo {
    private int cilindrada;
}
```

Este modelo permite agregar nuevos tipos de empresas, personas o vehículos sin alterar las clases existentes, lo que mejora la **extensibilidad** y el **mantenimiento del sistema**.