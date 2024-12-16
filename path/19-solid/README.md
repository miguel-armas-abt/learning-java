# PRINCIPIOS SOLID

[← Regresar a notas](../../README.md) <br>

---

## 1. Conceptos clave

> #### Acoplamiento
> - Indica en qué medida un componente depende de otros.
> - ⚠️ <u>Alto acoplamiento</u>: Un cambio en un componente puede impactar significativamente en otros, dificultando la evolución del sistema.
> - ✅ <u>Bajo acoplamiento</u>: Los componentes son independientes entre sí, lo que facilita el mantenimiento y la flexibilidad ante cambios.

> #### Cohesión
> - Indica en qué medida un componente está enfocado a una única responsabilidad.
> - ✅ <u>Alta cohesión</u>: Facilita el mantenimiento y evolución del software debido a la legibilidad del código.
> - ⚠️  ️<u>Baja cohesión</u>: Los componentes asumen múltiples responsabilidades, lo que los hace difíciles de entender y mantener.

## 2. SOLID
> Son principios de diseño orientado a objetos que sirven como guía para mejorar la calidad del código, hacerlo más flexible y fácil de mantener.

- <u>**S**</u>ingle Responsability *(Responsabilidad única)*
- <u>**O**</u>pen Closed *(Abierto Cerrado)*
- <u>**L**</u>iskov Substitution *(Sustitución de Liskov)*
- <u>**I**</u>nterface Segregation *(Segregación de Interfaces)*
- <u>**D**</u>ependency Inversión *(Inversión de Dependencias)*

### Single Responsability
> 📋 **Definición** <br>
> - Cada componente debe tener una única responsabilidad.
> - Significa que si un componente tiene más de una razón para cambiar, incumple este principio.
>
> ⚠️ **Ejemplo** <br>
> Si una clase provee lógica de negocio y a la vez lógica de acceso a datos, entonces incumple este principio.

### Open Closed
> 📋 **Definición** <br>
> - Los componentes deben estar <u>abiertos para su extensión, pero cerrados para su modificación</u>.
> - Significa que se debe poder añadir nuevas funcionalidades sin alterar el código existente.

### Liskov Substitution
> 📋 **Definición** <br>
> - Establece que una subclase debe ser sustituible por su superclase sin alterar el comportamiento esperado del programa.
> - Una implementación incorrecta rompe este principio al introducir comportamientos incompatibles en las subclases.
>
> 📌 **Ejemplo** <br>
>```java
> CreditCard classicCard = new ClassicCard();
> double benefit = retrieveBenefit(classicCard);
>
> CreditCard goldCard = new GoldCard();
> double benefit = retrieveBenefit(goldCard);
>````

### Interface Segregation
> 📋 **Definición** <br>
> - Este principio indica que las clases no deberían verse forzadas a depender de interfaces que no usan.
> - Las interfaces deben ser específicas y contener solo los métodos que realmente se necesitan.
> - Es mejor tener varias interfaces pequeñas y específicas que una única interfaz grande.

### Dependency Inversión
> 📋 **Definición** <br>
> - Este principio indica que las clases no deberían depender de los detalles de implementación, sino de las abstracciones. 
> - Significa que no se deben instanciar clases concretas en nuestras clases, sino que se deben utilizar solo abstracciones.
> - Se logra mediante la inyección de dependencias.
>
> 📌 **Ejemplo** <br>
> El servicio depende directamente del repository, con lo cual incumple este principio.
> ```java
> public class CreditCardService {
>   private CreditCardRepository repository;
> 
>   public CreditCardService() {
>     repository = new CreditCardRepositoryImpl(); // Dependencia directa
>   }
> }
> ```
>
> 💡 **Solución** <br>
> Implementar inyección de dependencias para manejar las dependencias mediante abstracciones.
> ```java
> public class CreditCardService {
>   private CreditCardRepository repository;
> 
>   public CreditCardService(CreditCardRepository repository) {
>     this.repository = repository;
>   }
> }
> ```
