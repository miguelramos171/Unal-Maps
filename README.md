# 🗺️ UNAL maps
*Una aplicación Android para navegar por la Ciudad Universitaria de la Universidad Nacional de Colombia, Sede Bogotá.*

![Mapa UNAL Banner](https://via.placeholder.com/800x200/003366/FFFFFF?text=Mapa+UNAL+-+Navega+con+Confianza)  
*(Reemplaza este placeholder con una captura real al subir el repo)*

---

## 📌 Descripción

**Mapa UNAL** es una aplicación móvil desarrollada en **Java (Android)** que permite a estudiantes, docentes y visitantes:

- 📍 **Ubicarse en tiempo real** dentro del campus  
- 🚶 **Trazar rutas caminando** entre edificios o marcadores guardados  
- ℹ️ Consultar **información detallada** de edificios (nombre, número, descripción, **facultad**, **horarios**)  
- 📌 Guardar, editar y eliminar **ubicaciones personalizadas**  
- 🔍 **Buscar edificios** por nombre, número o facultad  
- 🎨 Personalizar el **color de la ruta** desde la configuración  

Ideal para nuevos estudiantes, visitantes o cualquier persona que quiera orientarse en la UNAL.

---
### 📲 Instalación en dispositivo físico

1. **Construye el APK**:  
   En Android Studio: `Build > Build Bundle(s) / APK(s) > Build APK(s)`  
   El archivo `app-debug.apk` se generará en `app/build/outputs/apk/debug/`.

2. **Transfiere el APK** a tu teléfono (USB, correo, WhatsApp, etc.).

3. **Instala**:  
   - En **Android 8.0+**: ve a **Ajustes > Seguridad > Instalar apps desconocidas**, selecciona tu gestor de archivos y activa **Permitir instalación**.  
   - Abre el archivo APK y sigue las instrucciones.


>


## ⚠️ Advertencia crítica: Facturación en Google Cloud

> 🔑 **Requisito obligatorio**:  
> Para usar las funcionalidades de mapa y rutas, **debes asociar una tarjeta de crédito o débito válida** a tu proyecto en [Google Cloud Console](https://console.cloud.google.com/), **incluso durante el desarrollo**.

### ¿Por qué?
- Google exige **cuenta de facturación activa** para habilitar *Maps SDK for Android* y *Directions API*.
- El plan gratuito incluye **$200 USD mensuales en créditos** y **2,500 solicitudes diarias de Directions API** — suficiente para pruebas y uso académico.
- ⚠️ **Usted es financieramente responsable** de cualquier uso fuera de los límites gratuitos.

### ✅ Buenas prácticas para evitar cargos no deseados:
1. **Restrinja su clave API** (ver sección 8).
2. Monitoree el uso en [Google Cloud Console → APIs & Services → Dashboard](https://console.cloud.google.com/apis/dashboard).
3. Establezca **alertas de presupuesto** en [Billing → Budgets & alerts](https://console.cloud.google.com/billing).

🔗 [Documentación oficial: Costos y facturación](https://developers.google.com/maps/documentation/android-sdk/usage-and-billing)

---

## 🛠️ Tecnologías utilizadas

| Componente | Tecnología |
|-----------|------------|
| **Lenguaje** | Java 8+ |
| **Framework** | Android SDK (minSdk 23) |
| **Mapas** | Google Maps SDK for Android |
| **Rutas** | Google Maps Directions API |
| **Ubicación** | Fused Location Provider (`play-services-location`) |
| **Almacenamiento** | `SharedPreferences` (marcadores guardados y configuración) |
| **Datos estáticos** | Archivo CSV (`res/raw/edificioss.csv`) |
| **UI** | XML Layouts + `Material Design Components` |

---

## 📁 Estructura del proyecto
app/

├── src/main/

│ ├── AndroidManifest.xml # Permisos, metadatos y API Key

│ ├── java/com/example/base_datos/

│ │ ├── MapsActivity.java # Lógica principal: mapa, rutas, ubicación

│ │ └── ConfiguracionActivity.java # Configuración de color de ruta

│ └── res/

│ ├── layout/

│ │ ├── activity_maps.xml # Diseño del mapa y panel lateral

│ │ └── activity_configuracion.xml

│ ├── raw/

│ │ └── edificioss.csv # Datos de edificios (8 columnas)

│ └── drawable/

│ ├── ic_location_pin.xml # Pin de selección

│ └── btn_3puntos.png # Ícono de menú (⋮)

│

├── build.gradle (Module: app)

└── ...


## 📂 Archivos clave

### `edificioss.csv`

Archivo plano con **8 columnas** separadas por `;`:

```csv
Numero;Nombre;longitud;latitud;coordenasRaw;informacion;Facultad;Horarios
101;Torre de Enfermería;4.635197;-74.082424;...;Edificio moderno...;Enfermería;Lunes a Viernes 6:00 a.m. - 9:00 p.m.

```

## 🚀 Cómo ejecutar el proyecto
### Requisitos
Android Studio Giraffe (2022.3.1) o superior.

Dispositivo/emulador con Google Play Services.

API Key de Google Maps Platform con facturación habilitada.

## Pasos
### 1.Clona el repositorio:
En el bash:
```bash
git clone https://github.com/tu-usuario/MapaUNAL.git
cd MapaUNAL
```
### 2.Configura tu API Key en AndroidManifest.xml
```xml
android:value="TU_CLAVE_AQUI" />
```

### 3.Abre en Android Studio y ejecuta.

## 📱 Funcionalidades principales

| Característica | Descripción |
|----------------|-------------|
| **📍 Ubicación en tiempo real** | Marcador azul translúcido que se actualiza continuamente mientras navegas por el campus. |
| **🚏 Rutas caminando automáticas** | Al seleccionar un edificio o marcador guardado, se traza una ruta **en tiempo real** desde tu posición actual hasta el destino. |
| **ℹ️ Información detallada de edificios** | Al tocar el botón **ⓘ**, se muestra un cuadro con:<br>• Nombre y número del edificio<br>• Descripción general<br>• **Facultad a la que pertenece**<br>• **Horarios de atención** |
| **🔖 Marcadores personalizados** | Guarda ubicaciones favoritas (ej: *“Mi cafetería”*). Cada marcador incluye:<br>• Edición de nombre (✏️)<br>• Eliminación (🗑️)<br>• Integración en rutas |
| **🔍 Búsqueda inteligente** | Barra de búsqueda en el panel lateral que filtra **en tiempo real** por:<br>• Nombre del edificio<br>• Número (ej: `101`)<br>• Facultad (ej: `Ingeniería`) |
| **🎨 Configuración de color de ruta** | Elige entre 6 colores (azul, rojo, verde, morado, etc.) para la polilínea de la ruta. El cambio se aplica **inmediatamente**, sin reiniciar la app. |
| **♿ Accesibilidad** | Todos los botones incluyen `contentDescription` para lectores de pantalla. Diseño compatible con modo alto contraste. |

## ⚠️ Advertencia crítica: Requisito de facturación en Google Maps Platform

> 🔑 **Según la documentación oficial de Google** ([fuente](https://developers.google.com/maps/documentation/android-sdk/get-api-key)):  
> *“**You are financially responsible for charges caused by abuse of unrestricted API keys.**”*  
> **Usted es financieramente responsable de los cargos causados por el abuso de claves API no restringidas.**

### Requisitos obligatorios antes de usar la API

Antes de comenzar a usar el **Maps SDK for Android**, debe tener:  
✅ Un proyecto en Google Cloud Console  
✅ Una **cuenta de facturación asociada**  
✅ El **Maps SDK for Android habilitado**  
🔹 [Más información: Set up in Cloud Console](https://developers.google.com/maps/documentation/android-sdk/get-api-key#before-you-begin)

---

### ¿Cómo crear y restringir su clave API?

#### 1. Crear la clave
- Vaya a **[Google Maps Platform > Credentials](https://console.cloud.google.com/apis/credentials)**  
- Haga clic en **Create credentials > API key**  
- Copie la clave generada  

> 📌 *“Remember to restrict the API key before using it in production.”*  
> **Recuerde restringir la clave API antes de usarla en producción.**

#### 2. Restringir la clave (obligatorio)
En la página de la clave, bajo **Key restrictions**:

- **Application restrictions**  
  - ✅ Seleccione **Android apps**  
  - ✅ Haga clic en **+ Add package name and fingerprint**  
  - Ingrese:  
    - **Package name**: `com.example.base_datos`  
    - **SHA-1 fingerprint**: ej. `BB:0D:AC:74:D3:21:E1:43:67:71:9B:62:91:AF:A1:66:6E:44:5D:75`  
    > 🔍 Obtenga el SHA-1 con: `./gradlew signingReport`

- **API restrictions**  
  - ✅ Haga clic en **Restrict key**  
  - ✅ Seleccione:  
    - **Maps SDK for Android**  
    - **Directions API** *(requerida para rutas)*  

🔹 [Guía oficial: Restricting API keys](https://developers.google.com/maps/documentation/android-sdk/get-api-key#restricting-api-keys)

---

### Consecuencias de no restringir la clave
Si la clave se deja **sin restricciones**:
- Cualquier aplicación puede usarla  
- Un atacante puede generar miles de solicitudes  
- **Usted será facturado** por el uso no autorizado  
- No hay límite automático de gasto por defecto  

> ✅ **Recomendación de Google**:  
> *“Google strongly recommends that you restrict your API keys by limiting their usage to those only APIs needed for your application.”*  
> *“Restricting API keys adds security to your application by protecting it from unwarranted requests.”*
