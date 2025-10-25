## Dockerfile

### Crear un Dockerfile básico
```
# Base image
FROM openjdk:17
```

### Construir la imagen de Docker con el siguiente comando:
```
docker build -t myapp:1.0 .
```

### Construir el contenedor
```
docker run -d --name myapp01 myapp:1.0 
```
### Ver los logs
```
docker logs myapp01
```

### Inspeccionar imagen
```
docker image inspect myapp:1.0
```

-
## Crear un Dockerfile con un programa de Java

### Estructura del proyecto
```
.
├── Dockerfile
├── HelloWorld.java
└── README.md
```

### Crear programa HelloWorld.java
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Crear un Dockerfile básico
```
# Base image
FROM openjdk:17

# Set working directory
WORKDIR /app

# Copy source code
COPY HelloWorld.java /app/

# Compile the Java program
RUN javac HelloWorld.java

# Command to run the application
CMD ["java", "HelloWorld"]
```

### Construir la imagen de Docker con el siguiente comando:
```
docker build -t myapp:2.0 .
```

### Construir el contenedor
```
docker run -d --name myapp02 myapp:2.0 
```