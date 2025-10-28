## Dockerfile con proyecto en Maven

### Crear un proyecto en Maven
<img src="images/project.png" alt="Project Image" width="600"/>

### Agregar al archivo pom.xml el Manifest
```xml
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.3.0</version>
                <configuration>
                    <archive>
                        <manifest>
                            <addClasspath>true</addClasspath>
                            <mainClass>pe.edu.tecsup.app.Main</mainClass>
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

### Construir el componente jar
```
mvn clean package
```

### Ejecutar el componente
```
java -jar target/3_maven-1.0-SNAPSHOT.jar
```