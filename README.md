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
> *“You are financially responsible for charges caused by abuse of unrestricted API keys.”*  
> **Usted es financieramente responsable de los cargos causados por el abuso de claves API no restringidas.**

### ¿Qué significa esto para tu proyecto?

1. **Tarjeta obligatoria**  
   Para habilitar las APIs necesarias (*Maps SDK for Android* y *Directions API*), **debes asociar una tarjeta de crédito o débito válida** a tu proyecto en [Google Cloud Console](https://console.cloud.google.com/), **incluso durante el desarrollo**.

2. **Plan gratuito disponible**  
   - ✅ **$200 USD mensuales en créditos gratuitos**  
   - ✅ **2,500 solicitudes diarias de Directions API**  
   - ✅ Suficiente para pruebas, desarrollo y uso académico (no comercial)

3. **Riesgo real si no restringes la clave**  
   Si dejas la clave **sin restricciones**, cualquier persona que la descubra (ej: si se filtra en GitHub) puede usarla y generarte **cargos no deseados**.

---

### ✅ Pasos obligatorios para evitar cargos

| Paso | Acción | Documentación oficial |
|------|--------|------------------------|
| **1** | Restringe la clave a **aplicaciones Android** | [Application restrictions](https://developers.google.com/maps/documentation/android-sdk/get-api-key#restrict_key) |
| **2** | Ingresa **package name** y **SHA-1** de firma | `./gradlew signingReport` |
| **3** | Restringe a **solo 2 APIs**: <br> • `Maps SDK for Android` <br> • `Directions API` | [API restrictions](https://developers.google.com/maps/documentation/android-sdk/get-api-key#api_restrictions) |
| **4** | **Nunca subas tu clave a GitHub** (usa `.gitignore` si usas `local.properties`) | — |

> 📌 **Importante**: El equipo de desarrollo **NO se hace responsable** de cargos generados por malas prácticas de seguridad en la gestión de la API Key.
