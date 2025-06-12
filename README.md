# TaskMaster

Proyecto de ejemplo para aprender los fundamentos de Apache Maven, gestión de dependencias y perfiles de configuración.

## Descripción del Proyecto

TaskMaster es una aplicación Java básica que demuestra:
- Configuración de perfiles Maven (desarrollo y producción)
- Gestión de dependencias con Maven
- Estructura estándar de proyecto Maven
- Configuración de plugins para compilación y ejecución

## Comandos Maven Utilizados

### Comandos básicos:
```bash
# Crear el proyecto desde archetype
mvn archetype:generate -DgroupId=com.equipo.taskmaster -DartifactId=taskmaster -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

# Compilar el proyecto
mvn compile

# Ejecutar pruebas
mvn test

# Empaquetar en JAR
mvn package
```

### Comandos con perfiles:
```bash
# Ejecutar con perfil de desarrollo
mvn exec:java -Pdev

# Ejecutar con perfil de producción
mvn exec:java -Pprod

# Limpiar y compilar con perfil específico
mvn clean compile -Pdev
```

### Comandos de limpieza:
```bash
# Limpiar archivos generados
mvn clean

# Limpiar, compilar y ejecutar pruebas
mvn clean test
```

## Dependencias Utilizadas

### Dependencias principales:
- **JUnit 4.11**: Framework de pruebas unitarias para Java
  ```xml
  <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
  </dependency>
  ```

## Plugins Configurados

### Maven Compiler Plugin:
- **Versión**: 3.8.1
- **Propósito**: Compilar código Java con JDK 11
- **Configuración**: Source y target Java 11

### Exec Maven Plugin:
- **Versión**: 3.1.0
- **Propósito**: Ejecutar la aplicación Java desde Maven
- **Configuración**: 
  - Clase principal: `com.equipo.taskmaster.App`
  - System properties para perfiles

## Perfiles Configurados

### Perfil de Desarrollo (`dev`):
- Propiedad: `env.name=Desarrollo`
- Uso: `mvn exec:java -Pdev`

### Perfil de Producción (`prod`):
- Propiedad: `env.name=Producción`
- Uso: `mvn exec:java -Pprod`

## Estructura del Proyecto

```
taskmaster/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── equipo/
│   │               └── taskmaster/
│   │                   └── App.java
│   └── test/
│       └── java/
│           └── com/
│               └── equipo/
│                   └── taskmaster/
│                       └── AppTest.java
├── pom.xml
└── README.md
```

## Mayor Aprendizaje Técnico

El aprendizaje más significativo fue comprender que **Maven no solo gestiona dependencias, sino que estandariza todo el ciclo de vida del desarrollo**. Cada fase del ciclo (validate, compile, test, package) se ejecuta en orden automáticamente, garantizando consistencia y reproducibilidad en cualquier entorno.

Además, aprendí que las **propiedades definidas en perfiles requieren configuración explícita** en los plugins para ser accesibles desde el código Java, no se pasan automáticamente como system properties.

## Desafío Principal Enfrentado

El mayor desafío fue la **sintaxis estricta del archivo pom.xml**. Pequeños errores como:
- Tags mal cerrados o anidados incorrectamente
- Contenido fuera del elemento `<project>`
- Dependencias fuera del bloque `<dependencies>`

Estos errores generaban mensajes crípticos que inicialmente fueron difíciles de interpretar. La solución fue entender la estructura jerárquica del XML y usar herramientas de validación como el formateador automático de VSCode.

## Requisitos

- Java JDK 11 o superior
- Apache Maven 3.6 o superior

## Instalación y Ejecución

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/JpLetranger/taskmaster.git
   cd taskmaster
   ```

2. Compilar el proyecto:
   ```bash
   mvn compile
   ```

3. Ejecutar la aplicación:
   ```bash
   # Entorno de desarrollo
   mvn exec:java -Pdev
   
   # Entorno de producción
   mvn exec:java -Pprod
   ```

## Autor
Preguntas finales
- ¿Qué aprendiste sobre el ciclo de vida de Maven?
- ¿Cómo facilita Maven el trabajo en equipo y la reproducibilidad?
- ¿Cuál fue el mayor reto al trabajar con dependencias?
- ¿Por qué crees que Maven es tan usado en entornos empresariales?
- ¿Qué harías diferente si tuvieras que automatizar otro proyecto?

¿Qué aprendiste sobre el ciclo de vida de Maven?
Maven tiene fases predefinidas que se ejecutan en orden: validate → compile → test → package → install → deploy. Cada fase ejecuta automáticamente las anteriores, lo que garantiza consistencia. Por ejemplo, al ejecutar mvn test, Maven primero valida, luego compila y después ejecuta las pruebas.

¿Cómo facilita Maven el trabajo en equipo y la reproducibilidad?
Maven estandariza la estructura del proyecto y automatiza la gestión de dependencias. Cualquier desarrollador puede clonar el proyecto y ejecutar mvn compile sin configurar manualmente librerías. El archivo pom.xml documenta todas las dependencias y versiones, garantizando que todos trabajen con el mismo entorno.

¿Cuál fue el mayor reto al trabajar con dependencias?
La sintaxis XML del pom.xml es estricta - errores de indentación o tags mal cerrados rompen todo el build. También entender que las dependencias deben estar dentro del bloque <dependencies> y que las propiedades del perfil requieren configuración adicional para ser accesibles desde Java.
¿Por qué crees que Maven es tan usado en entornos empresariales?
Maven aporta consistencia, automatización y escalabilidad. Los equipos grandes necesitan estándares claros, y Maven los proporciona. Su integración con IDEs, servidores de CI/CD y repositorios centralizados lo hace ideal para proyectos complejos donde múltiples desarrolladores colaboran.

¿Qué harías diferente si tuvieras que automatizar otro proyecto?
Planificaría mejor la estructura de perfiles desde el inicio, documentaría las dependencias principales y configuraría templates reutilizables. También implementaría validaciones automáticas del pom.xml para evitar errores de sintaxis que frenan el desarrollo.

Desarrollado como proyecto de aprendizaje de Apache Maven.