# SingletonEx

explicacion del patron singleton

El patrón Singleton es un patrón de diseño de software que se utiliza para garantizar que una clase tenga una única instancia y ofrezca un punto de acceso global a esa instancia desde cualquier parte de la aplicación. La idea es poder utilizar el mismo objeto en distintas partes del codigo por ejemplo si tenemos un
array de datos de clientes, no nos interesaria que cada vez que creemos una instancia de este esté vacio.


```ts
class MiSingleton {
  private static instancia: MiSingleton | null = null;

  private constructor() {
    // Inicialización de la instancia creándola como privada
  }

  public static obtenerInstancia(): MiSingleton {
    if (MiSingleton.instancia === null) {
      MiSingleton.instancia = new MiSingleton(); // Creación perezosa
    }
    return MiSingleton.instancia;
  }
}

```

El patrón Singleton se implementa siguiendo estos principios:

Constructor privado: La clase Singleton debe tener un constructor privado para evitar que se creen instancias de la clase desde fuera de la misma.

Instancia única: La clase debe mantener una única instancia de sí misma como un miembro privado y estático.

Método estático: Se proporciona un método estático público que permite a los usuarios de la clase obtener la única instancia de la misma. Este método crea la instancia si aún no existe o devuelve la instancia ya creada.

Es interesante tener en cuenta que si vamos a trabajar con multiples hilos de ejecucion que intentaran accedera a nuestra clase, se creen de la forma correcta las nuevas instancias sin duplicarse.
