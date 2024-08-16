
# Exportar Datos de JTable a Excel

Este proyecto proporciona una clase `ExportarExcel` que permite exportar los datos de una tabla (`JTable`) a un archivo Excel con formato `.xls`, utilizando la biblioteca Apache POI. Además, se utiliza `JFileChooser` para permitir al usuario seleccionar la ubicación y el nombre del archivo Excel.

## Requisitos

### Usando Maven

Si estás utilizando Maven como tu herramienta de construcción, puedes añadir Apache POI a tu proyecto añadiendo la siguiente dependencia a tu archivo `pom.xml`:

```xml
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi</artifactId>
    <version>5.0.0</version>
</dependency>
```

### Usando Java Directamente

Si prefieres usar Java directamente sin un gestor de dependencias, puedes descargar la biblioteca Apache POI desde su [repositorio en GitHub](https://github.com/apache/poi) o desde su [sitio web oficial](https://poi.apache.org/download.html). Luego, incluye los archivos `.jar` en el classpath de tu proyecto.

## Uso

### 1. Configuración

Asegúrate de que tienes la clase `ExportarExcel` en el paquete `components` de tu proyecto.

### 2. Llamada a la Clase

Para exportar los datos de una `JTable` a Excel, simplemente llama al método `exportarExcel` desde una instancia de `ExportarExcel`. Aquí tienes un ejemplo:

```java
ExportarExcel exc;

try {
    exc = new ExportarExcel();
    exc.exportarExcel(table);  // 'table' es tu JTable con datos
} catch (IOException ex) {
    Notifications.getInstance().show(Notifications.Type.ERROR, "Error al guardar en Excel: " + ex);
}
```

### 3. Descripción del Código

- **ExportarExcel Class**:
  - `exportarExcel(JTable t)`: Este método abre un `JFileChooser` para seleccionar la ubicación del archivo Excel. Luego crea un archivo Excel (`.xls`) y escribe los datos de la tabla en él. El archivo se abre automáticamente una vez que se ha guardado.

### 4. Consideraciones

- El archivo se guarda con la extensión `.xls` y se crea una hoja de trabajo dentro del archivo Excel llamada "Mi hoja de trabajo 1".
- Si ya existe un archivo con el mismo nombre, se sobrescribirá.
- El código maneja diferentes tipos de datos, como `Double`, `Float`, y `String` al exportar los datos de la tabla.

## Ejecución

1. **Ejecuta tu aplicación**: Asegúrate de que tu `JTable` está poblada con los datos que deseas exportar.
2. **Exporta la tabla**: Utiliza el código anterior para exportar los datos. Se abrirá una ventana de diálogo que te permitirá seleccionar dónde guardar el archivo Excel.
3. **Verifica el archivo**: El archivo Excel se abrirá automáticamente después de guardarlo.

## Notificaciones de Error

En caso de un error al intentar guardar el archivo, se mostrará una notificación de error usando un sistema de notificaciones personalizado.

## Licencia

Este proyecto es de uso libre y puede ser modificado según las necesidades del usuario.
