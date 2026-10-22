# Proyecto 1: Pipeline NoSQL y Análisis Exploratorio de E-Commerce

## Descripción del Proyecto
Este proyecto implementa un flujo automatizado de adquisición, preprocesamiento, almacenamiento NoSQL y análisis exploratorio de datos (EDA) utilizando la API pública de E-Commerce/Productos.

El objetivo principal es estructurar un pipeline reproducible que extraiga información semiestructurada en JSON, aplique transformaciones de datos, la almacene en un motor NoSQL orientado a documentos y permita responder preguntas de negocio mediante consultas optimizadas.

## Tecnologías y Librerías
- **Lenguaje de Programación:** Python 3.x
- **Adquisición de Datos:** `requests` (API REST en formato JSON)
- **ETL y Preprocesamiento:** `pandas`, `json`
- **Base de Datos NoSQL:** `TinyDB` (Almacenamiento por documentos en JSON)
- **Análisis y Visualización:** `matplotlib`, `seaborn`

# Adquisición:
Extracción de un conjunto de registros relevantes en formato JSON sin autenticación compleja
# Preprocesamiento:
Selección de variables clave (id_producto, nombre, categoria, precio_usd, calificacion, stock), normalización de campos y tratamiento de valores nulos. 
# Almacenamiento NoSQL: 
Organización de los registros en colecciones de documentos JSON utilizando TinyDB.   
# Consultas y EDA: 
Ejecución de consultas de filtrado, agregaciones y análisis visual descriptivo.  

# Patrón de Acceso y Consultas NoSQL:
El diseño del esquema de almacenamiento favorece la búsqueda rápida de productos disponibles en inventario con altas calificaciones de clientes (>= 4.5).   Se implementaron 3 consultas: Consulta de Filtrado: Selección de productos cuyo precio supera los $50 USD; consulta de agregación: cálculo del precio promedio global del catálogo y conteo del stock acumulado; consulta por patrón de acceso: filtrado combinado optimizado por calificación alta (calificacion >= 4.5) y disponibilidad inmediata (stock > 0).

# Principales Hallazgos (EDA)Distribución de Inventario: 
Las categorías con mayor capital inmovilizado en stock son Electrónica y Artículos de Hogar. 
Relación Precio vs. Calificación: El análisis de dispersión muestra que una tarifa más elevada no garantiza linealmente una mejor valoración por parte del usuario final.
# Decisiones de Diseño y Trade-offs 
# Flexibilidad NoSQL vs. Consistencia: 
La estructura basada en documentos permite añadir dinámicamente nuevos atributos sin alterar un esquema rígido. Sin embargo, se sacrifica la normalización estricta, generando cierta redundancia de datos.   Almacenamiento Local vs. Distribuido: Se utilizó TinyDB para representar decisiones de organización documental de forma ligera y reproducible localmente, permitiendo su escalamiento directo a clústeres como MongoDB Atlas en producción.   
