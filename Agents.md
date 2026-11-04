# YOGASTUDIO – TAREA: LANZAMIENTO A PRODUCCIÓN
## Product Engineering

Actúa como un Product Engineer especializado en desarrollo de aplicaciones web, diseño UI/UX, definición de producto, Spec Driven Development y despliegue de aplicaciones en producción.

Tu objetivo es evolucionar el proyecto existente YogaStudio, tomando como referencia la documentación anterior, y desarrollar una nueva versión que responda a las necesidades reales de su público objetivo.

Debes trabajar sobre el proyecto existente, respetando su arquitectura y tecnologías actuales.

# PASO 1. ICP Y USER PERSONA

## 1.1. Contexto del producto

YogaStudio es una aplicación web para un estudio de yoga administrado por Andrea, quien trabaja con dos instructoras.

Actualmente, el estudio presenta dificultades para administrar los paquetes de 10 clases, controlar las reservas, gestionar los cupos de las sesiones y comunicar cambios cuando una instructora no puede asistir.

La aplicación busca digitalizar estos procesos y ofrecer una experiencia organizada tanto para las alumnas como para las administradoras.

## 1.2. Definición del ICP

Construye el perfil del cliente ideal (ICP) de YogaStudio.

Considera las siguientes características iniciales:

- Negocio: estudios de yoga independientes.
- Tamaño: pequeños estudios con una o varias instructoras.
- Capacidad: entre 10 y 30 alumnas por jornada.
- Administración: propietarios que todavía utilizan métodos manuales o herramientas poco integradas.
- Necesidad principal: organizar reservas, paquetes, cupos y comunicación.
- Objetivo: reducir tareas administrativas y mejorar la experiencia de las alumnas.

Desarrolla el ICP incluyendo:
- Tipo de negocio.
- Tamaño y características.
- Problemas actuales.
- Necesidades.
- Motivaciones de compra.
- Beneficios esperados.
- Principales dificultades para adoptar el sistema.

## 1.3. Definición de User Persona

Crea dos perfiles de usuario:

### Persona 1: Andrea – Administradora

Características de referencia:
- Edad: 35 años.
- Propietaria de un estudio de yoga.
- Trabaja con dos instructoras.
- Administra las reservas y los paquetes de sus alumnas.
- Busca reducir el tiempo dedicado a tareas administrativas.
- Necesita información confiable sobre cupos, paquetes y sesiones.

Objetivos:
- Tener control de las alumnas inscritas.
- Evitar errores en los paquetes.
- Organizar los horarios.
- Comunicar cambios rápidamente.

Frustraciones:
- Tarjetas físicas extraviadas.
- Confusiones sobre clases restantes.
- Reservas que superan la capacidad.
- Dificultad para comunicar cancelaciones.

### Persona 2: Mariana – Alumna

Características de referencia:
- Edad: 28 años.
- Trabaja durante el día.
- Practica yoga por bienestar físico y mental.
- Prefiere asistir a clases por las tardes.
- Compra paquetes de 10 sesiones.
- Utiliza principalmente su teléfono móvil.

Objetivos:
- Consultar sus clases disponibles.
- Reservar sin complicaciones.
- Saber cuántas sesiones le quedan.
- Recibir avisos sobre cambios de horario.

Frustraciones:
- No saber si tiene cupo.
- Perder el registro de sus clases.
- Olvidar sus reservas.
- No recibir información a tiempo.

IMPORTANTE: Estos perfiles son hipótesis iniciales. Organízalos como perfiles de producto que posteriormente puedan validarse con usuarios reales.

# PASO 2. NUEVA SPEC: FUNCIONALIDAD Y MÉTRICAS

Crea una nueva especificación independiente de la anterior.

## 2.1. Nombre del nuevo feature

Seguimiento de paquetes y recordatorios inteligentes.

## 2.2. Definición del problema

Las alumnas de YogaStudio compran paquetes de 10 sesiones, pero no siempre tienen presente cuántas clases han utilizado, cuántas les quedan o cuándo necesitan adquirir un nuevo paquete.

Esto puede provocar que lleguen al estudio sin sesiones disponibles o que pierdan continuidad en sus clases.

Andrea también necesita identificar qué alumnas están próximas a terminar sus paquetes para mejorar la organización administrativa.

## 2.3. Objetivo

Implementar un módulo que permita consultar el estado de los paquetes, visualizar el consumo de sesiones y generar recordatorios cuando una alumna esté próxima a terminar sus clases.

## 2.4. Diseño de la solución

### Panel de alumnas

Debe permitir:
- Consultar el paquete activo.
- Visualizar las 10 sesiones del paquete.
- Identificar las sesiones utilizadas.
- Consultar las sesiones restantes.
- Visualizar el historial de consumo.
- Recibir recordatorios cuando queden pocas sesiones.

### Panel administrativo

Debe permitir:
- Consultar los paquetes de las alumnas.
- Identificar paquetes próximos a agotarse.
- Visualizar paquetes agotados.
- Consultar el historial de consumo.
- Identificar alumnas que necesitan renovar sus paquetes.

## 2.5. Criterios de aceptación

CA-01: El sistema permite visualizar el paquete activo de cada alumna, mostrando el total de sesiones, sesiones utilizadas y sesiones restantes.

CA-02: Cada vez que una sesión se complete, el sistema actualiza correctamente el saldo de clases del paquete correspondiente.

CA-03: Cuando una alumna tenga dos sesiones restantes, el sistema debe mostrar un recordatorio indicando que su paquete está próximo a agotarse.

CA-04: El administrador puede consultar un listado de alumnas con paquetes activos, próximos a agotarse y agotados.

CA-05: El historial permite consultar las sesiones consumidas y sus respectivas fechas, evitando duplicar descuentos por una misma sesión.

## 2.6. Métricas de éxito

Define e implementa mecanismos para medir el éxito del feature.

Utiliza las siguientes métricas como objetivos iniciales:

1. **Reducción de consultas administrativas:** reducir en un 50% las consultas relacionadas con las clases restantes de los paquetes.

2. **Precisión del saldo:** alcanzar un 100% de coincidencia entre las sesiones completadas y los descuentos registrados.

3. **Visibilidad de paquetes:** conseguir que el 100% de los paquetes activos tengan su saldo disponible para consulta.

4. **Recordatorios:** conseguir que el 100% de las alumnas que lleguen a dos sesiones restantes reciban o visualicen el recordatorio correspondiente.

5. **Uso del feature:** lograr que al menos el 80% de las alumnas registradas consulten su estado de paquete durante el período de evaluación.

IMPORTANTE:
Las métricas anteriores son objetivos propuestos, no resultados comprobados. No inventes datos de uso ni presentes porcentajes esperados como resultados reales.

Si no existen datos suficientes para medir una métrica, prepara un mecanismo de seguimiento que permita obtenerlos durante las pruebas y el uso real.

## 2.7. Reglas de negocio

- Cada paquete contiene 10 sesiones.
- Las sesiones solamente se descuentan cuando se registran como completadas.
- Las reservas canceladas no deben descontar sesiones.
- Una misma sesión no puede descontarse dos veces.
- Los paquetes agotados deben identificarse claramente.
- Los recordatorios no deben duplicarse innecesariamente.
- El sistema debe mantener un historial verificable de los movimientos.

## 2.8. Restricciones

No incorporar:
- Videos de yoga.
- Rutinas de entrenamiento.
- Tienda en línea.
- Funcionalidades ajenas a la gestión de paquetes.

Guarda esta especificación en:

`specs/seguimiento-paquetes.md`

# PASO 3. REDISEÑO Y DIFERENCIACIÓN DEL PRODUCTO

La nueva versión debe evolucionar visualmente respecto a la entrega anterior.

No se trata únicamente de agregar una pantalla. Debes mejorar la experiencia considerando los perfiles de Andrea y Mariana.

## Identidad visual

Mantener la esencia de YogaStudio:
- Estilo vintage y minimalista.
- Tipografía Montserrat.
- Colores café, verde, crema y beige.
- Apariencia elegante, cálida y profesional.

Sin embargo, introduce una mejor jerarquía visual y una distribución más moderna de los componentes.

## Experiencia de Andrea

Priorizar:
- Dashboard administrativo.
- Indicadores de paquetes.
- Alertas de paquetes próximos a agotarse.
- Historial de consumo.
- Acceso rápido a la información de las alumnas.

## Experiencia de Mariana

Priorizar:
- Visualización de su paquete.
- Indicador gráfico de sesiones restantes.
- Historial de clases.
- Recordatorios claros.
- Navegación sencilla desde dispositivos móviles.

Evita sobrecargar las pantallas con información innecesaria.

# PASO 4. IMPLEMENTACIÓN

Antes de programar:

1. Analiza la estructura del proyecto existente.
2. Lee AGENTS.md.
3. Lee la especificación anterior de gestión de sesiones.
4. Lee la nueva especificación seguimiento-paquetes.md.
5. Lee la Skill de diseño UI/UX de YogaStudio.

Implementa el nuevo feature sin romper las funcionalidades existentes.

Respeta las tecnologías, dependencias y arquitectura actuales.

No reemplaces el proyecto por una aplicación independiente.

Las funcionalidades deben ser reales y estar conectadas con la lógica de datos existente.

Si algún criterio de aceptación es ambiguo o contradictorio, corrige primero la especificación antes de modificar el prompt de implementación.

Al terminar, verifica individualmente los cinco criterios de aceptación y documenta los resultados.

# PASO 5. LANZAMIENTO A PRODUCCIÓN

El lanzamiento en línea es obligatorio.

Utiliza preferiblemente Vercel si el proyecto es compatible con su plataforma. Si la tecnología actual requiere otra alternativa, selecciona Netlify o Render según corresponda.

Si el proyecto utiliza una base de datos o autenticación con Supabase, configura correctamente sus conexiones y variables de entorno.

## Requisitos del despliegue

1. Preparar la aplicación para producción.
2. Configurar las variables de entorno necesarias.
3. Verificar la conexión con la base de datos.
4. Comprobar que la autenticación funcione, si está implementada.
5. Configurar el dominio o subdominio de producción.
6. Verificar que las rutas y recursos carguen correctamente.
7. Comprobar el funcionamiento en dispositivos móviles.
8. Realizar una prueba de las funcionalidades principales en la versión desplegada.

No exponer claves privadas, contraseñas ni credenciales en el repositorio.

No utilizar datos reales de alumnas para las demostraciones públicas. Emplear datos de prueba.

Si necesitas credenciales o autorización para publicar, solicita únicamente lo necesario.

No declares que el lanzamiento fue exitoso hasta comprobar que la URL funciona públicamente.

# PASO 6. ENTREGABLES FINALES

Prepara un documento README.md actualizado que contenga:

1. Nombre y descripción de YogaStudio.
2. Problema que resuelve.
3. ICP definido.
4. User Personas.
5. Descripción del nuevo feature.
6. Enlace a la nueva especificación.
7. Criterios de aceptación.
8. Métricas de éxito.
9. Tecnologías utilizadas.
10. Instrucciones de instalación.
11. URL pública de producción.
12. Evidencias de funcionamiento.

Al finalizar, presenta un informe con:

- URL del repositorio de GitHub.
- URL pública funcionando.
- Plataforma utilizada para el despliegue.
- Funcionalidades implementadas.
- Tabla de cumplimiento de criterios de aceptación.
- Métricas configuradas y resultados realmente medidos.
- Problemas encontrados y soluciones aplicadas.

# CONDICIÓN FINAL

El objetivo no es únicamente modificar el diseño de YogaStudio, sino evolucionar el producto a partir de las necesidades del cliente ideal y sus usuarios.

La nueva funcionalidad debe aportar valor, diferenciarse de la entrega anterior y estar disponible mediante una URL pública funcional.

No inventes resultados, pruebas ni enlaces de producción. Si alguna etapa requiere intervención del propietario, explica qué falta para completarla.
