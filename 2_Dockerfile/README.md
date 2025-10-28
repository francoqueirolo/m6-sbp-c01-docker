--
## Dockerfile Básico

### Crear un Dockerfile básico
```
# Base image
FROM openjdk:17
```
SOLICITO CERTIFICADO DE MOVIMIENTO MIGRATORIO DE MI HIJA ALBA SOFIA GOMEZ MONTERO
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
## Dockerfile para un programa en Java

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

### Crear un Dockerfile
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

-
## NOTA : Para volver a generar la Imagen deben borrar la anterior

### Borar contenedor
```
docker rm myapp02
```

### Borar imagen
```
docker rmi myapp:2.0
```


### Cambiar el codigo java 
```
public class HelloWorld {
    public static void main(String[] args) {
        int cont = 0;
        while(true) {
            try {
                Thread.sleep(1000);
                cont++;
                System.out.println("Mensaje #" + cont + ": Hello, World!");
            } catch (InterruptedException e) {
                System.out.println("Se interrumpió el hilo");
                // Handle exception
            }
        }

    }
}
```

### Ejecutar el contenedor y ingresar al contenedor
```
docker exec -it myapp02 /bin/bash
```