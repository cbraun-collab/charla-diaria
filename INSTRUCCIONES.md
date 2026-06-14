# INSTRUCCIONES DE INSTALACIÓN Y USO
## App Charla Diaria – SENERCOM Limitada

---

## ¿Qué es esta app?

Una aplicación web progresiva (PWA) que reemplaza el formulario físico de Registro de Trabajo Seguro. Permite:
- Llenar los datos de la charla (obra, relator, riesgos)
- Que cada trabajador escriba su nombre, RUT y firme en el tablet
- Guardar el registro como imagen PNG en Google Drive automáticamente

---

## PASO 1 — Configurar Google Drive (HACER UNA SOLA VEZ)

Para que la app suba los registros automáticamente a la carpeta de Drive de SENERCOM, debe configurarse un Client ID de Google. Siga estos pasos:

### 1.1 Crear el Client ID de Google

1. Vaya a https://console.cloud.google.com/
2. Cree un nuevo proyecto (ej: "Charla Diaria SENERCOM")
3. En el menú lateral: **APIs y servicios → Credenciales**
4. Haga clic en **+ Crear credenciales → ID de cliente de OAuth 2.0**
5. Tipo de aplicación: **Aplicación web**
6. Nombre: "Charla Diaria SENERCOM"
7. En **Orígenes de JavaScript autorizados** agregue la URL donde estará alojada la app
   - Si usa GitHub Pages: `https://TUUSUARIO.github.io`
   - Si usa otro servidor: `https://tudominio.com`
8. Haga clic en **Crear**
9. Copie el **ID de cliente** (tiene este formato: `XXXXXXXXX.apps.googleusercontent.com`)

### 1.2 Activar Google Drive API

1. En el menú: **APIs y servicios → Biblioteca**
2. Busque "Google Drive API" y haga clic en **Habilitar**

### 1.3 Insertar el Client ID en la app

1. Abra el archivo `index.html` con un editor de texto
2. Busque la línea (aprox. línea 315):
   ```
   const GOOGLE_CLIENT_ID = 'TU_GOOGLE_CLIENT_ID_AQUI';
   ```
3. Reemplace `TU_GOOGLE_CLIENT_ID_AQUI` con el ID copiado:
   ```
   const GOOGLE_CLIENT_ID = '123456789.apps.googleusercontent.com';
   ```
4. Guarde el archivo

---

## PASO 2 — Publicar la app (HACER UNA SOLA VEZ)

La app debe estar en un servidor HTTPS para que funcione como PWA instalable. La opción más simple y gratuita es **GitHub Pages**:

### Opción A: GitHub Pages (recomendada, gratuita)

1. Cree una cuenta gratuita en https://github.com
2. Cree un repositorio público llamado `charla-diaria`
3. Suba los 3 archivos: `index.html`, `manifest.json`, `sw.js`
4. Vaya a **Settings → Pages → Source → main branch**
5. La app quedará en: `https://TUUSUARIO.github.io/charla-diaria`

### Opción B: Servidor web propio de SENERCOM

Copie los 3 archivos en el servidor web de la empresa bajo HTTPS.

---

## PASO 3 — Instalar en cada tablet (HACER EN CADA DISPOSITIVO)

### En Android (recomendado):
1. Abra Chrome y vaya a la URL de la app
2. Chrome mostrará automáticamente un banner: **"Agregar a pantalla de inicio"**
3. Si no aparece: toque el menú ⋮ → **"Instalar app"** o **"Agregar a pantalla de inicio"**
4. La app quedará instalada como ícono en el home del tablet

### En iPad / iPhone:
1. Abra Safari y vaya a la URL de la app
2. Toque el botón **Compartir** (cuadrado con flecha)
3. Seleccione **"Agregar a pantalla de inicio"**
4. Confirme con **Agregar**

---

## PASO 4 — Uso diario

### El supervisor (antes de la charla):
1. Abre la app desde el ícono en pantalla de inicio
2. Completa: Obra, Fecha, Relator, Tipo de charla, Temas
3. Avanza a **Riesgos** y marca los identificados
4. Avanza a **Firmas**

### Cada trabajador (durante la charla):
1. Toca **"Agregar trabajador"**
2. Escribe su nombre, RUT y especialidad
3. Firma con el dedo en el espacio indicado
4. Toca **"Confirmar firma"**

### El supervisor (al terminar):
1. Toca **"Revisar y guardar"**
2. Revisa el resumen
3. Toca **"Autorizar y guardar en Drive"**
4. La primera vez pedirá autorización de Google (solo aparece 1 vez por sesión)
5. El registro se sube automáticamente a la carpeta de Drive de SENERCOM
6. También se descarga una copia local como respaldo

---

## Carpeta de destino en Drive

Los registros se guardan en:
```
https://drive.google.com/drive/folders/1UuXpmOifYejccYgrErGVFgPy-CJV95MO
```

El nombre de cada archivo es automático:
```
Charla_AAAAMMDD_NombreObra.png
```

---

## Funcionamiento sin internet

- La app funciona completamente sin conexión (modo offline)
- Una franja naranja indica cuando no hay internet
- En ese caso, use **"Solo guardar imagen local"**
- La imagen se descarga en el tablet
- Cuando haya conexión, súbala manualmente a la carpeta de Drive

---

## Preguntas frecuentes

**¿Se pierden los datos si se cierra la app sin terminar?**
No. La app guarda automáticamente el progreso en el dispositivo. Al volver a abrir, recupera los datos.

**¿Puede usarse en varios tablets a la vez?**
Sí. Cada tablet opera de forma independiente. Los registros se guardan en la misma carpeta de Drive.

**¿El formato cumple con la normativa?**
Sí. El registro generado incluye todos los campos del formulario original y la declaración del Art. N°21 Decreto N°40 Ley 16.744.

---

*SENERCOM Limitada — Seguridad en cada obra*
