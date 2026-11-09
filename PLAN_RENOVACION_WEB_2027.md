# Club Juntos 2027 — Plan maestro de renovación web

**Estado:** planificación aprobada; implementación sujeta a revisión por secciones.  
**Fecha:** 2026-11-09  
**Repositorio:** `mdpjuntos-dot/clubjuntos`  
**Rama de trabajo:** `diseno-referencia-club-canada`  
**Protección:** NO modificar `main`, NO desplegar, NO cambiar DNS ni producción sin aprobación expresa.

## 1. Decisiones aprobadas

### Etapa 1 — Diseño
- Estética moderna premium inspirada en la experiencia y estructura de CC Natación, **sin reproducir recursos protegidos**.
- Portada con fotografía real grande de alumnos; navegación superior desplegable.
- Secciones: Nosotros; Actividades; Convenios; Promociones; Obras Sociales; Club de Descuentos; Familias; Noticias y Club Juntos TV; Contacto; Equipo profesional separado; Donaciones.
- No publicar tarifas.
- Branding oficial de Club Juntos; conservar fotografías y rostros originales.

### Etapa 2 — Actividades
- Una página propia para: Club Kids, Club Recreativo, Club Joven, Club del Juego, Natación individual, Hidroterapia, Teatro, Danza y expresión corporal y Colonia de vacaciones.
- Mostrar edades **exactas confirmadas**; no inferir las que no se hayan validado.
- Horarios y disponibilidad: consultar por WhatsApp; enlaces con mensajes distintos por actividad.
- Imágenes reales provistas desde Drive del club, sujetas a permisos de uso.
- FAQ específica para cada actividad.

### Etapa 3 — Convenios, promociones y obras sociales
- Convenios vigentes comprobados y recepción de propuestas de entidades educativas, deportivas, empresas, ONG, salud y organismos públicos.
- Promociones: solo activas, con vencimiento y condiciones verificadas; estado vacío si no hay activas.
- Listado de obras sociales: **solo convenios directos confirmados**. No inventar entidades ni presentar reintegros o autorizaciones aisladas como convenios.
- Por entidad: logo autorizado, contacto y FAQ.
- Página explicativa independiente para distinguir convenio directo, autorización particular y reintegro.

### Etapa 4 — Club de Descuentos y Donaciones
- Club de Descuentos exclusivo para alumnos y sus familias.
- Credenciales digitales y físicas, validación **visual**; no inventar un sistema de QR autenticado ni un padrón público.
- Rubros: gastronomía, indumentaria, deporte, recreación/turismo, salud/bienestar, servicios profesionales, educación y tecnología.
- Comercios solicitan adhesión mediante WhatsApp. Listar solo los beneficios confirmados, con condiciones y vigencia.
- Donaciones únicas y mensuales; destinos: becas, materiales, actividades, infraestructura, transporte y sostenimiento general.
- Reconocer donantes solo con consentimiento expreso.
- **Pendiente:** método de pago de donaciones; no mostrar CBU, alias, links ni recurrencia operativa sin configuración validada.

### Etapa 5 — Familias, equipo y multimedia
- Familias, acceso público: FAQ, normas, biblioteca educativa y testimonios reales/autorizados.
- Equipo profesional organizado por departamentos; cada ficha: foto, nombre, profesión, área, descripción y contacto autorizado.
- Noticias del club y artículos educativos por categorías.
- Club Juntos TV como sección en la web; videos públicos. Transmisiones de clases con control de acceso privado para familias autorizadas; no exponer enlaces de transmisiones privadas en páginas públicas.
- Definir autentificación, permisos y consentimiento de imagen antes de activar streaming privado.

### Etapa 6 — Técnica
- SEO completo + SEO local Mar del Plata + GEO; textos útiles para familias y motores de búsqueda.
- Accesibilidad: objetivo WCAG 2.2 AA con pruebas manuales y automáticas.
- Analítica: Google Analytics y Search Console, con revisión de configuración y privacidad.
- Idiomas: español e inglés, traducción revisada y `hreflang` consistente.
- Mantener el alojamiento existente, tras verificar ruta de publicación, certificados y respaldo.
- Revisión por secciones; mantenimiento posterior mediante cambios en GitHub preparados por el asistente y aprobados por Nicolás.

## 2. Hallazgos del código existente (lectura de index.html)
- Web HTML de página única de aproximadamente 109.041 caracteres con JavaScript inline y Tailwind CSS servido desde CDN.
- IDs públicos visibles: actividades, galeria, equipo, obras-sociales, faq, inscripcion y noticias.
- Fotografías enlazadas principalmente desde `lh3.googleusercontent.com/d/...`.
- Enlaces de WhatsApp generales y temáticos ya existentes.
- Hay rastros de analítica en código; **no se ha verificado que mida correctamente**.
- No se observó JSON-LD en el archivo principal; sitemap/robots deben comprobarse en el repositorio y alojamiento, no asumir su inexistencia por el HTML.

## 3. Arquitectura propuesta
- `/index.html` — portada (ES).
- `/actividades/index.html` — índice de actividades.
- `/actividades/club-kids.html`
- `/actividades/club-recreativo.html`
- `/actividades/club-joven.html`
- `/actividades/club-del-juego.html`
- `/actividades/natacion-individual.html`
- `/actividades/hidroterapia.html`
- `/actividades/teatro.html`
- `/actividades/danza-expresion-corporal.html`
- `/actividades/colonia-de-vacaciones.html`
- `/nosotros.html`, `/equipo.html`, `/convenios.html`, `/promociones.html`, `/obras-sociales.html`, `/club-de-descuentos.html`, `/donaciones.html`, `/familias.html`, `/biblioteca.html`, `/noticias.html`, `/club-juntos-tv.html`, `/contacto.html`.
- `/en/` — páginas EN equivalentes, desplegadas gradualmente con traducciones revisadas y canonical/hreflang adecuados.
- Establecer componentes/plantillas para header, footer, ficha de actividad, FAQ, CTA de WhatsApp; elegir implementación compatible con hosting verificado antes de refactorizar.

## 4. Orden de ejecución / puertas de aprobación
1. **Respaldo y línea de base:** inventario de URLs, archivos, activos, analítica, formularios y publicación. Verificar hosting/FTP o CI, DNS, SSL. Probar rollback. No publicar.
2. **Diseño del sistema:** colores/tipografías/espaciados/componentes, menú y portada premium mobile-first. Prototipo privado; **aprobación de portada y navegación**.
3. **Actividades:** nueve páginas independientes, edades confirmadas, fotos autorizadas, FAQ y WhatsApp contextual. **Aprobación por actividad**.
4. **Secciones institucionales:** nosotros, equipo, familias, convenios, obras sociales y promociones con contenidos verificados. **Aprobación de cada sección**.
5. **Programas:** Club de Descuentos con credencial visual (sin datos sensibles públicos), comercios confirmados, Donaciones con medios válidos. **Aprobación**.
6. **Noticias, biblioteca, TV:** contenidos originales, fuentes y permisos; streaming privado solo tras evaluación de solución segura y consentimientos. **Aprobación**.
7. **Internacionalización:** contenido EN revisado; navegación y metadatos bilingües. **Aprobación**.
8. **Calidad:** test en móvil/escritorio, teclado, lector pantalla, contraste, rendimiento, formularios, enlaces, Core Web Vitals, títulos/metas, schema, sitemap, indexabilidad, herramientas de analítica.
9. **Revisión de lanzamiento:** diff contra `main`, checklist y preview verificable. Crear PR solo cuando la implementación esté revisada; **merge/despliegue exclusivamente con autorización expresa**.
10. **Pospublicación:** comprobar SSL, errores 404, enlaces, métricas y Search Console; registrar cambios y rollback.

## 5. Datos y aprobaciones pendientes
- Enlace de Drive, selección de fotografías y permisos de imagen (especialmente menores).
- Lista vigente de profesionales y sus fichas, con autorización de foto/contacto.
- Confirmación de edades exactas de cada actividad.
- Listado de convenios institucionales y de obras sociales **directos**, con vigencia y logos autorizados.
- Listado de promociones activas y comercios adheridos (descuento, vigencia, términos).
- Reglas de credencial digital/física, emisión, vigencia y control de acceso, evitando exposición de datos de alumnos.
- Donaciones: cuenta receptora, método de pago, recurrencia, requisitos administrativos/legales y comprobantes.
- Cuentas/IDs de GA4 y Google Search Console autorizadas y política de privacidad.
- Alojamiento y método de despliegue actual; respaldo y restauración comprobados.
- Traducciones EN revisadas de contenidos institucionales.
- Arquitectura de autenticación y autorizaciones para clases privadas.
- Revisión de testimonios y consentimiento de publicación.

## 6. Criterios de aceptación
- Menú funcional en escritorio/móvil, accesible por teclado, visible y consistente.
- Sin tarifas en páginas públicas, ni promociones vencidas, ni alianzas inventadas.
- Secciones y enlaces coherentes; sin fotografías repetidas dentro de la misma experiencia cuando existan suficientes recursos autorizados.
- Contenido fiel a Club Juntos; sin cambiar rostros, logo ni añadir nombres/identidades no confirmados.
- Cada actividad: contenido, edad confirmada, CTA y FAQ.
- Cada entidad colaboradora: estado real verificable.
- SEO local y bilingüe implementado y validado.
- Cumplimiento WCAG 2.2 AA buscado y verificado (sin afirmar certificación por anticipado).
- Privacidad de familias y menores preservada; no datos clínicos ni listas de alumnos en HTML público.
- Cero cambios a `main` y cero despliegues sin aprobación de Nicolás.

## 7. Estado actual
- `main`: **sin cambios por este proyecto**.
- Rama `diseno-referencia-club-canada`: existe; contiene prototipo inicial `club-de-descuentos.html` aún no integrado al menú principal.
- Este archivo es el registro de requisitos y plan. No implica que la web renovada o las funciones privadas ya estén construidas.
