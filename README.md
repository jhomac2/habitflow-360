```
# ⚡ HabitFlow 360 — Control de Hábitos Ultra-Fácil &amp; Registro Diario Intuitivo

**HabitFlow 360** es una aplicación web moderna, ultra-fácil de usar y ligera para el seguimiento diario de hábitos, rutina y constancia personal. Diseñada bajo el principio de **Cero Fricción**, permite registrar tus hábitos en 1 solo clic desde tu teléfono o computadora, visualizar tu progreso diario y mantener rachas activas sin complicaciones.

---

## 🌟 Características Principales

* **⚡ Check-in Instantáneo:** Registra tus hábitos diarios en un solo toque con retroalimentación visual inmediata.
* **🔥 Contador de Rachas (Streaks):** Mantén la motivación viendo tus días consecutivos de cumplimiento.
* **📊 Heatmap de Constancia (30 Días):** Matriz visual estilo GitHub para evaluar la disciplina de tu último mes de un vistazo.
* **🎯 2 Tipos de Hábitos:**
  * **Hábitos Simples (Sí / No):** *ej. Meditar, Hacer ejercicio, Leer.*
  * **Hábitos Cuantitativos (Con Meta de Unidades):** *ej. Tomar 2.5 Litros de Agua, Leer 20 Páginas.*
* **🎨 Categorías Organizadas con Colores:** Clasificación por Salud 🏋️, Mente 🧠, Trabajo 💼, Finanzas 💰 y Bienestar 🧘.
* **📈 Gráficos Interactivos (Chart.js):** Métricas de cumplimiento semanal y distribución por áreas de vida.
* **🌓 Modo Oscuro &amp; Modo Claro:** Interfaz adaptable a la vista del usuario.
* **☁️ Sincronización Doble (LocalStorage + Google Sheets):** Almacenamiento local inmediato y sincronización opcional en tu nube privada de Google Drive.

---

## 🔒 Privacidad y Configuración de Nube Gratis (Google Sheets)

La aplicación funciona al 100% en tu navegador mediante `LocalStorage` sin necesidad de servidores. Si deseas que tu información esté respaldada en tu cuenta privada de **Google Drive**, sigue estos sencillos pasos:

### 📑 Pasos para conectar Google Sheets:

1. Abre tu **Google Drive** y crea una nueva **Hoja de Cálculo de Google**.
2. En el menú superior, ve a **Extensiones ➔ Apps Script**.
3. Borra el código por defecto y pega el siguiente script de integración:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  
  if (sheet.getLastRow() == 0) {
    sheet.appendRow(["Fecha y Hora", "Datos_HabitFlow_JSON"]);
  }
  
  sheet.appendRow([new Date(), JSON.stringify(data)]);
  
  return ContentService.createTextOutput(JSON.stringify({"result": "success"}))
    .setMimeType(ContentService.MimeType.JSON);
}

function doGet(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var lastRow = sheet.getLastRow();
  
  if (lastRow &lt;= 1) {
    return ContentService.createTextOutput(JSON.stringify({"status": "empty"}))
      .setMimeType(ContentService.MimeType.JSON);
  }
  
  var lastData = sheet.getRange(lastRow, 2).getValue();
  return ContentService.createTextOutput(lastData)
    .setMimeType(ContentService.MimeType.JSON);
}
```

4. Haz clic en **Desplegar ➔ Nueva implementación**.
5. En *Seleccionar tipo*, elige **Aplicación Web**.
6. En *Quién tiene acceso*, selecciona **Cualquier persona** (Anyone).
7. Haz clic en **Desplegar**, concede los permisos requeridos y copia la **URL de la aplicación web**.
8. Pega esa URL en el menú de **Ajustes de Nube ☁️** dentro de HabitFlow 360 y ¡listo! Tus datos estarán respaldados automáticamente en tu propia nube privada.

---

## 🛠️ Tecnologías Utilizadas

* **HTML5 / Vanilla JavaScript (ES6+):** Lógica rápida y reactiva sin frameworks pesados.
* **Tailwind CSS (vía CDN):** Estilizado moderno, limpio y responsive.
* **Chart.js:** Gráficos estadísticos interactivos.
* **Lucide Icons:** Iconografía vectorial limpia.
* **Google Apps Script:** Backend serverless gratuito y privado.

---

## 🚀 Instalación y Despliegue

1. Copia el código generado por el **Súper-Prompt** en un archivo llamado `index.html`.
2. Haz doble clic en `index.html` para abrirlo directamente en cualquier navegador (Chrome, Edge, Firefox, Safari, Brave).
3. Opcional: Para usarlo en tu celular como una App nativa, sube el archivo a **GitHub Pages** o **Vercel** y añádelo a la pantalla de inicio de tu teléfono.

---

## 👨‍💻 Creador &amp; Contacto Directo

Desarrollado por **Jhordy** desde la Provincia de Pichincha, Ecuador 🇪🇨.

* 📍 **Ubicación:** Tupigachi, Cantón Pedro Moncayo, Pichincha — Ecuador 🇪🇨
* 📱 **WhatsApp / Teléfono:** [+593 963923399](https://wa.me/593963923399)
* 🎵 **TikTok:** [@I´m_Jhordy](https://www.tiktok.com/@I%CC%81m_Jhordy)
* 🐙 **GitHub:** [github.com/By_Jhordy](https://github.com/By_Jhordy)

---
*Proyecto de código abierto para demostración de portafolio profesional en desarrollo web y diseño de producto.*

```
