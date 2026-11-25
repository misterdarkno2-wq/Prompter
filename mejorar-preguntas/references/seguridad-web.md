# Revisión defensiva de seguridad web

Pide una revisión del código, las dependencias o la configuración dentro del alcance autorizado. Basa la evidencia en inspección de los controles y pruebas defensivas acotadas con datos sintéticos. Sustituye credenciales y datos personales por nombres de variables o ejemplos ficticios antes de citar registros o redactar el prompt. Ante una solicitud de explotación, limita la reformulación a inspección de código, mitigación y verificación de protecciones.

## Elige qué controles revisar

Identifica quién puede iniciar la operación, qué recurso o dato se debe proteger, dónde cambia el nivel de confianza y qué componente aplica la decisión. Selecciona las comprobaciones pertinentes a ese recorrido.

- **Identidad y permisos**. Revisa creación, renovación y cierre de sesiones cuando el flujo los use. En operaciones sobre recursos, comprueba la autorización en el servidor y que la política refleje roles, propiedad o aislamiento entre cuentas.
- **Entradas y salidas**. Sigue los datos externos hasta su uso. Revisa validación en el servidor, consultas parametrizadas, codificación de salida y controles de archivos o llamadas salientes según el destino de los datos.
- **Navegador y despliegue**. Revisa atributos de cookies, orígenes permitidos, protección contra solicitudes entre sitios, políticas de contenido y exposición de errores según la arquitectura y la configuración activa.
- **Secretos y dependencias**. Inspecciona los puntos de carga y registro de información sensible. Para una alerta de dependencia, confirma la versión resuelta en el archivo de bloqueo y contrástala con el aviso oficial del proveedor. Distingue la presencia de la dependencia de su uso en el flujo afectado.

Si necesitas un criterio formal para comprobar un control, consulta el requisito correspondiente en [OWASP ASVS](https://asvs.owasp.org/).

## Haz que cada hallazgo se pueda corregir

Para cada hallazgo, pide la ubicación exacta, el comportamiento observado del control, las condiciones relevantes, el impacto y una corrección concreta. Identifica cuáles están respaldados por el código y cuáles requieren más evidencia. Prioriza por impacto y exposición efectiva.

Formula la validación como una prueba del control previsto. Por ejemplo, prueba la función de autorización con roles y recursos ficticios y comprueba que solo concede los permisos definidos. Usa las pruebas existentes del proyecto cuando sea posible y reporta las comprobaciones realizadas y las pendientes.
