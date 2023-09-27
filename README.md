## Patrones de Diseño en mi Código

En mi código, he aplicado varios patrones de diseño de programación para mejorar su estructura y modularidad. Aquí está la justificación de cómo he utilizado estos patrones:

### Patrón de Diseño Singleton

He utilizado el patrón Singleton en mi código en dos lugares clave:

1. **LoggerFactory**: En mi clase `PokeAPIClient`, he utilizado `LoggerFactory` para obtener una instancia de un logger. Esta es una implementación típica de Singleton, ya que garantiza que tengamos una única instancia del logger en toda la aplicación. Esto es beneficioso para tener un registro coherente y controlar el nivel de registro en un solo lugar.

2. **HttpClient**: En la misma clase `PokeAPIClient`, he utilizado `HttpClients.createDefault()` para obtener una única instancia de `CloseableHttpClient`. Esto es esencial para garantizar la eficiencia en las solicitudes HTTP y evitar la creación innecesaria de múltiples instancias del cliente HTTP.

### Patrón de Diseño Factory Method

Dentro de mi clase `WebServiceConfig`, he implementado el patrón Factory Method en el método `defaultWsdl11Definition`. Este método crea y configura instancias de `DefaultWsdl11Definition` que se utilizan para definir cómo se expone un servicio web. El uso de un Factory Method permite la creación de diferentes definiciones WSDL con diferentes configuraciones, lo que brinda flexibilidad y extensibilidad.

### Patrón de Diseño Inyección de Dependencias (DI)

He aplicado el patrón de Inyección de Dependencias en la clase `RequestService`. A través del constructor, he inyectado una dependencia del repositorio `RequestRepository`. Esta práctica sigue el principio de la Inversión de Dependencias, lo que significa que `RequestService` no se preocupa por la implementación concreta de `RequestRepository`. Esta flexibilidad facilita las pruebas unitarias y la sustitución de implementaciones en tiempo de ejecución.

### Patrón de Diseño Template Method

En las clases controladoras de servicios web, como `PokeapiEndpoint`, he implementado varios métodos que siguen un patrón similar. Estos métodos realizan operaciones comunes, como la obtención de datos de una fuente externa, y luego delegan partes específicas de la lógica a implementaciones concretas. Este patrón permite la reutilización del código común y la personalización de la funcionalidad en función de las solicitudes específicas.

### Patrón de Diseño Value Object

Dentro de mi archivo XSD, he definido varios tipos complejos como `Pokemon`, `Ability`, `Held`, etc. Estos objetos encapsulan un conjunto de atributos relacionados y se utilizan principalmente para transportar datos entre diferentes componentes de mi aplicación. Estos son ejemplos de Value Objects que ayudan a organizar y estructurar los datos de manera más significativa.

### Patrón de Diseño Interceptor

La clase `WebServiceInterceptor` implementa la interfaz `EndpointInterceptor` y sigue el patrón de diseño Interceptor. Este interceptor se utiliza para agregar funcionalidad personalizada antes o después de la ejecución de métodos en un servicio web. En mi caso, estoy registrando solicitudes y respuestas en una base de datos utilizando este interceptor, lo que permite un seguimiento y auditoría eficientes de las interacciones del servicio web.

En resumen, la aplicación de estos patrones de diseño en mi código mejora la estructura, mantenibilidad y flexibilidad de mi aplicación, y me permite separar las preocupaciones y mantener un código más organizado. Estos patrones desempeñan un papel fundamental en la creación de una arquitectura sólida y extensible.