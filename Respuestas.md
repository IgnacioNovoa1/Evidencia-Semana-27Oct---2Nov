**Nombre:** Ramón Novoa
**Matricula:** 21891216824
1. Mejora de la clase Persona (Generalización)

Pregunta: Considere que la clase Persona es lo suficientemente abstracta para permitir representar elementos propios del dominio problema ¿Qué podría hacer para mejorar aquello?

Respuesta: La forma de "mejorar" una clase que es demasiado genérica (abstracta) para representar elementos específicos del dominio es usar Herencia (Generalización).

En nuestros casos, tenemos Persona como un concepto base, pero en la realidad tenemos tipos específicos de personas:

    En el Caso 1, tenemos "Niños" (Sofía, Pablo, Pedro).

    En el Caso 2, tenemos "Empleados" (Agustín, Francisco) y personas que no son empleadas (Andrea).

Solución: Se crea la clase Persona como una superclase (clase padre) que contiene atributos comunes como nombre y edad. Luego, se crean subclases (clases hijas) que heredan de Persona y añaden sus propias características o relaciones:

    class Niño extends Persona { ... } (Puede tener relaciones específicas como "asiste a Escuela").

    class Empleado extends Persona { ... } (Tiene una relación "trabaja en" Departamento).

De esta forma, Persona sigue siendo una abstracción útil, pero podemos modelar las diferencias específicas del dominio.

2. Generalización de Animales (Caso 1)

Pregunta: ¿Cómo podría en el Caso1 representar una situación más genérica para el caso de los animales?

Respuesta: Aplicando el mismo concepto de Herencia. En el Caso 1, tenemos un "perro" (ladra, come) y un "gato" (muerde, rasguña).

En lugar de crear dos clases separadas e inconexas, creamos una superclase Animal.

    Superclase Animal: Contendría atributos comunes (ej. nombre: String, color: String) y métodos comunes (ej. comer(): void).

    Subclases Perro y Gato:

        class Perro extends Animal { ... }

            Añade su método específico: ladrar(): void.

        class Gato extends Animal { ... }

            Añade sus métodos específicos: morder(): void, rasguñar(): void.

Esto nos permite tratar a todos como "Animales" (polimorfismo), a la vez que respetamos sus comportamientos únicos y evitamos duplicar código.

3. Modelado de Universidad (Composición)

Pregunta: Si consideramos ahora que una universidad no se encuentra compuesta de carreras sino que se compone de facultades y éstas a su vez se conforman de departamentos independientes. ¿Cómo cambia eso sus diagramas de clases?

Respuesta: Esto cambia la relación a una Composición Anidada. La palabra clave es "se compone de" (o "se conforma de"), lo que implica una relación "parte-todo" donde las partes no pueden existir sin el todo.

En UML, esto se modela con un rombo relleno (◆) en el lado del "todo".

Así cambia el diagrama:

    Se crea una relación de Composición entre Universidad y Facultad.

        La Universidad es el "todo"; la Facultad es la "parte".

        Lógica: Si la Universidad deja de existir, sus Facultades también.

    Se crea una segunda relación de Composición entre Facultad y Departamento.

        La Facultad es el "todo"; el Departamento es la "parte".

        Lógica: Si la Facultad es eliminada, sus Departamentos también.

El diagrama mostraría una cadena de composición:

4. Generalización del Caso 2

Pregunta: Aplicando el mismo razonamiento anterior ¿Cómo se podría generalizar el análisis hecho en el Caso2 en la clase Persona, Moto y Empresa Naviera?

Respuesta: Aquí aplicamos tanto la Herencia (como en Persona) como la Abstracción (para Moto y Empresa).

    Clase Persona:

        Como se mencionó en el punto 1, la generalizamos usando Herencia. Persona es la superclase, y Empleado es la subclase. Agustín y Francisco son instancias de Empleado, mientras que Andrea es una instancia de Persona.

    Clase Moto:

        Tenemos "Harley Davidson 1200" y "Kawasaki Ninja".

        No creamos una clase HarleyDavidson y otra KawasakiNinja.

        Solución (Abstracción): Creamos una única clase llamada Moto. Las diferencias se manejan con atributos, no con clases.

            class Moto {

            marca: String

            modelo: String

            }

        La moto de Agustín es una instancia de Moto (marca="Harley Davidson", modelo="1200 Custom").

        La moto de Andrea es otra instancia (marca="Kawasaki", modelo="Ninja ZX 6R").

    Clase Empresa Naviera:

        El texto menciona "Tesoros del Mar S.A.".

        Solución (Abstracción): Igual que con Moto. La clase no se llama "TesorosDelMar", la clase se llama EmpresaNaviera. "Tesoros del Mar S.A." es el valor del atributo nombre de una instancia de esa clase.

        Solución (Composición): El "mismo razonamiento" de la Universidad aplica aquí. La EmpresaNaviera "se compone de" Departamentos. Por lo tanto, usaríamos una relación de Composición (◆) entre EmpresaNaviera y Departamento.
