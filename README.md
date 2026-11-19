# Dolores AR

App turística con realidad aumentada para visitar Dolores Hidalgo (Manual TDD · Desarrollo Móvil Integral · UTNG).

## Cómo dejarlo listo (primera vez)

Este zip trae `lib/`, `test/` y `pubspec.yaml`. Faltan las carpetas de plataforma (android, ios…). Para generarlas, dentro de la carpeta `dolores_ar` ejecuta:

```bash
flutter create . --project-name dolores_ar
flutter pub get
```

`flutter create .` NO borra tu código: solo agrega lo que falta. Si te crea `test/widget_test.dart`, bórralo.

### Permisos Android
En `android/app/src/main/AndroidManifest.xml`, antes de `<application`:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.CAMERA"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-feature android:name="android.hardware.camera" android:required="false"/>
```

En `android/app/build.gradle` (o `.kts`) pon `minSdk = 24` dentro de `defaultConfig`.

### Permisos iPhone (solo con Mac)
En `ios/Runner/Info.plist`:

```xml
<key>NSCameraUsageDescription</key>
<string>Usamos la cámara para mostrarte los lugares históricos a tu alrededor.</string>
<key>NSLocationWhenInUseUsageDescription</key>
<string>Usamos tu ubicación solo mientras la app está abierta, para saber qué lugares tienes cerca.</string>
```

## Pruebas

```bash
flutter test
```

| Archivo | Ronda | Qué prueba |
|---|---|---|
| `test/geo_test.dart` | 1, 2, 3 | Haversine, rumbo, ángulos, campo de visión, formato |
| `test/motor_ar_test.dart` | 4 | Qué lugares se ven y dónde |
| `test/pasaporte_test.dart` | 5 | Sellos del pasaporte |
| `test/ar_viewmodel_test.dart` | 6 | ViewModel con GPS y brújula falsos |

## Ejecutar

```bash
flutter run
```

Usa **Modo demo (salón de clases)** si no estás en Dolores Hidalgo.
