# Análisis Mediateca MIM — Koha OPAC

> **Propósito del documento:** Inventario estructurado de pantallas, componentes, hallazgos técnicos y puntos de mejora levantados durante la revisión de la interfaz actual de Koha para la Mediateca MIM.

---

## 1. Pantalla Inicial y Elementos Globales

* **Menú Superior — Identidad:**
  * *Estado actual:* Logo institucional de Koha por defecto en la barra de navegación superior.
  * *Punto a mejorar:* Evaluar el reemplazo del logo genérico de Koha por el logotipo oficial del **MIM** para reforzar la identidad institucional.

* **Menú Superior — Listas Públicas:**
  * *Estado actual:* Despliega colecciones destacadas (*Colección Fanzinoteca*, *Novedades Noviembre*, *Colección CONAF*, *Exposición Observatorios Históricos*, *Exposición Tercer Paisaje*) y un enlace *"Ver todo…"* que redirige a una subpágina con el mismo listado.
  * *Punto a mejorar:* Definir regla de negocio en caso de superar 5 listas: ¿se limita a un máximo de 5 elementos, se destacan bajo un criterio automático o mediante selección manual?

* **Menú Superior — Listas Personales:**
  * *Estado actual:* Etiqueta *"Sus listas"* con llamado a la acción *"Ingrese para crear sus propias listas"*.
  * *Punto a mejorar:* Cambiar *"Sus listas"* por **"Tus listas"**. Definir y estandarizar el tono de comunicación de la plataforma hacia un lenguaje cordial y coloquial.

* **Buscador Principal:**
  * *Estado actual:*
    * **Selector:** Catálogo de biblioteca, Título, Autor, Tema, ISBN, ISSN, Series, Signatura Tipográfica.
    * **Input alfanumérico:** Estados `focus` y `focus-visible`.
    * **Botón de búsqueda:** Estados `inicial`, `hover`, `focus/active` y `focus-visible`.
  * *Puntos a mejorar:*
    * Definir reglas de sanitización y validación del input (¿debe aceptar todo tipo de caracteres?).
    * **Hallazgo crítico:** Al ingresar un `<script>` en el campo/selector de búsqueda, el firewall (WAF) bloqueó el acceso completo a `mim.cl`.

* **Gestión de Sesión y Usuario:**
  * *Estado actual:* Bloques de *Iniciar Sesión*, *Sus cookies consentidas*, *Historial de búsqueda*, *Página de historial (no logueado)* y enlace *XML*.
  * *Punto a mejorar:* Evaluar si el **Historial de búsqueda** debe mostrarse únicamente cuando el usuario haya iniciado sesión, evitando exponer actividad en equipos compartidos.

* **Subnavegación y Pie / Cookies:**
  * *Estado actual:* Subnavegación hacia *Búsqueda avanzada*, *Navegar por jerarquía*, *Búsqueda por autoría*, *Más popular*, *Adquirido por último* y enlace a *Política de cookies*.
  * *Puntos a mejorar:*
    * Mostrar el texto completo de la **Política de cookies**.
    * **Bug funcional:** Al intentar **cambiar de idioma**, el sistema redirige erróneamente a una pantalla de login.

---

## 2. Resultados de Búsqueda y Estados Vacíos

* **Estado: Sin Resultados:**
  * *Estado actual:* Pantalla informativa cuando la búsqueda no arroja coincidencias, con enlaces de *Suscripción* y *Sugerencias*.
  * *Puntos a mejorar (Bugs funcionales):*
    * El enlace de **Suscripción** no posee ninguna funcionalidad asociada.
    * El enlace de **Sugerencias** redirige a una URL rota (error 404 / no encontrada).

* **Listado de Resultados:**
  * *Estado actual:*
    * **1 resultado exacto:** Redirige directamente a la ficha de detalle.
    * **Más de 1 resultado:** Muestra listado con selector *Ordenar listado de búsquedas* y opción *Más búsqueda*.
  * *Punto a mejorar:* El buscador solo encuentra coincidencias por un dato específico o palabras exactas; requiere mejorar la tolerancia a búsquedas parciales o flexibles.

* **Listado de Lista por Colección:**
  * *Estado actual:* Vista de ítems pertenecientes a una lista pública o colección seleccionada desde el menú o ficha.
  * *Punto a mejorar:* Mantener coherencia visual y de ordenamiento con el listado estándar de resultados.

---

## 3. Pantalla de Detalle de Libro / Recurso

* **Navegación y Cabecera de Ficha:**
  * *Estado actual:* Breadcrumb, imagen de portada, Título, Descripción, Clasificación, Recursos en línea (link), Lista/colección en la que aparece y Calificación.
  * *Punto a mejorar:* Asegurar claridad en la visualización de metadatos clave y enlaces a recursos digitales externos.

* **Pestañas de Visualización (Tabs):**
  * *Estado actual:* Tres vistas de registro: **Vista Normal**, **Vista MARC** y **Vista ISBD**.
  * *Punto a mejorar:* Evaluar si las vistas técnicas (MARC / ISBD) deben tener menor protagonismo visual frente a la Vista Normal para público general.

* **Tabla de Secciones Inferiores:**
  * *Estado actual:* Pestañas con **Participaciones** (ejemplares/disponibilidad), **Comentarios** e **Imágenes**.
  * *Punto a mejorar:* Verificar legibilidad de la tabla de ejemplares y estados de disponibilidad en distintos dispositivos.

* **Panel Derecho — Retención (Place Hold):**
  * *Estado actual:* Botón *Retención / Place Hold*. Redirige a la pantalla de login para generar la reserva del libro.
  * *Punto a mejorar:* Alinear el flujo de autenticación con el portal de cuentas MIM (ver sección 6).

* **Panel Derecho — Imprimir:**
  * *Estado actual:* Botón *Imprimir*. Genera un PDF para impresión de la ficha catalográfica actual (no del libro).
  * *Punto a mejorar:* Cambiar la etiqueta del botón a **"Imprimir Ficha Técnica"** para evitar confusiones en el usuario respecto a descargar o imprimir el libro completo.

* **Panel Derecho — Citar:**
  * *Estado actual:* Botón *Citar* que levanta una ventana modal con formatos de citación.
  * *Punto a mejorar:* Revisar la utilidad real y el correcto funcionamiento de esta ventana modal para el perfil de usuarios de la mediateca.

* **Panel Derecho — Guardar Registro y Listas:**
  * *Estado actual:*
    * **Guardar registro:** Descarga el registro de la ficha en el formato seleccionado.
    * **Guardar en listas:** Abre ventana popup para ingresar a la cuenta.
  * *Punto a mejorar:* Unificar el comportamiento de inicio de sesión (redirección vs. popup) al interactuar con listas o reservas.

---

## 4. Pantalla de Búsqueda Avanzada

* **Condiciones de Búsqueda:**
  * *Estado actual:* Búsqueda bajo tres condiciones exactas por defecto. Al activar *"Más opciones"*, añade botones en cada input, operadores booleanos (**OR / NOT**) y permite agregar condiciones sin límite.
  * *Punto a mejorar:* Revisar la complejidad de permitir condiciones ilimitadas y el comportamiento cuando no hay resultados al buscar por campos válidos.

* **Botonera y Tipo de Elemento:**
  * *Estado actual:* Botonera repetida (*Buscar*, *Más opciones*, *Nueva búsqueda*). Al elegir *Más opciones* se despliegan filtros por tipo de elemento.
  * *Punto a mejorar:* En la sección *"Limitar a cualquiera de las siguientes"*, incluir un **icono o imagen** representativa para las opciones de selección múltiple.

* **Rango de Fechas de Publicación:**
  * *Estado actual:* Campo único de fecha/rango sin asistencia de formato.
  * *Puntos a mejorar:*
    * Verificar usabilidad del filtro de fechas.
    * Implementar **autocompletado** o dividir en **dos inputs de años distintos (Desde / Hasta)**, ambos opcionales.
    * Establecer **"Todos"** como valor por defecto.

* **Selector "Ordenar por":**
  * *Estado actual:* Desplegable extenso con combinaciones de criterio y dirección (ascendente/descendente).
  * *Punto a mejorar:* Resumir el listado de opciones incorporando un **control/input adicional con icono de flecha** para alternar entre orden ascendente y descendente.

---

## 5. Vistas Especializadas de Exploración

* **Navegar por Jerarquía:**
  * *Estado actual:* Exploración estructurada por árbol de clasificación temática o documental.
  * *Punto a mejorar:* Asegurar claridad en los niveles de profundidad y retorno hacia categorías superiores.

* **Búsqueda por Autoría:**
  * *Estado actual:* Formulario de búsqueda específico, selector de *Tipo de autoría* y listado de resultados con paginación.
  * *Punto a mejorar:* Mantener los mismos estándares de feedback y paginación que el buscador principal.

* **Más Popular:**
  * *Estado actual:* Breadcrumb, panel izquierdo de filtros (*Mostrar la parte superior*, *Limitar a*) y grilla/listado de resultados en sección derecha.
  * *Punto a mejorar:* Revisar la traducción literal de *"Mostrar la parte superior"* (*Show top*) para adaptarla a un español natural (ej. *"Mostrar los más vistos"*).

* **Adquirido por Último:**
  * *Estado actual:* Listado cronológico de las últimas incorporaciones al catálogo de la mediateca.
  * *Punto a mejorar:* Destacar como acceso rápido de novedades bibliográficas.

---

## 6. Interfaces y Referentes de Diseño / Arquitectura

### Referente 1: Portal de Acceso Actual a Centro de Cuentas MIM
* **Lineamiento:** Tomar este portal como referencia directa para diseñar la interfaz gráfica de inicio de sesión (login) de **Koha MIM OPAC**, unificando la experiencia de usuario entre ecosistemas del museo.
* **Stack tecnológico:** `Vue.js`, `Font Awesome`, `Axios`, `PHP Laravel`.

### Referente 2: Archivo José Carlos Mariátegui (`mariategui.org`)
* **Lineamiento:** Tomar como referencia su estructura de navegación, organización de colecciones y patrones de usabilidad aplicados a archivos y bibliotecas digitales.
* **Stack tecnológico:** `WordPress`, `Preact`, `ScrollMagic.js`, `Masonry`, `Moment.js`, `Lightbox`, `Owl-Carousel`, `jQuery`, `MySQL`.
