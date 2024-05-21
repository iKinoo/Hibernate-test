# Factory Method

![alt](https://refactoring.guru/images/patterns/diagrams/factory-method/solution1.png?id=fc756d2af296b5b4d482e548214d08ef)

![alt](https://refactoring.guru/images/patterns/diagrams/factory-method/solution2-en.png?id=db5de848c1d490b835666ef54d131d46)


Class Diagram
---

```mermaid

classDiagram

class SessionFactory{
<<interface>>
}


class EntityManagerFactory{
<<interface>>
}
class Referenceable{
<<interface>>
}
class Serializable{
<<interface>>
}
class Closeable{
<<interface>>
}

EntityManagerFactory <|-- SessionFactory
Referenceable <|-- SessionFactory
Serializable <|-- SessionFactory
Closeable <|-- SessionFactory

AutoCloseable <|-- EntityManagerFactory

class AutoCloseable{
<<interface>>
close() void
+createEntityManager() EntityManager
}

AutoCloseable <|-- EntityManager

class EntityManager{
<<interface>>

+persist(Object entity) void
+merge(T entity)~T~ T 
remove(Object entity) void
find(Class~T~ entityClass, Object primaryKey) ~T~ T

}



```