# Tienda online (Java + Spring Boot + MySQL)

Incluye: registro/login, catálogo con búsqueda, carrito, pago (simulado), pedidos con código de seguimiento,
perfil, y panel de administración (productos, pedidos, estados).

## Validaciones
- Cédula: solo 10 números, con algoritmo de cédula ecuatoriana (`validation/CedulaValidator.java`).
- Nombre/apellido: solo letras (regex en `validation/Reglas.java`).
- Teléfono: 10 números. Precio > 0. Stock >= 0. Contraseña mín. 6.
- Doble validación: en el navegador (filtra teclas) y en el servidor (la que realmente protege).

## Ejecutar en local
1. Instalar JDK 17, Maven y MySQL 8.
2. VS Code: extensiones "Extension Pack for Java", "Spring Boot Extension Pack" y "Lombok Annotations Support".
3. Ajustar usuario/clave de MySQL en `src/main/resources/application.properties`
   (la base `tienda` se crea sola).
4. `mvn spring-boot:run`  → abrir http://localhost:8080
5. Admin inicial: `admin@tienda.com` / `Admin123` (cámbiala después).

## GitHub
```
git init
git add .
git commit -m "Tienda online inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/tienda.git
git push -u origin main
```

## Poner online
Hay `Dockerfile`. Opciones: Render, Railway, Azure App Service o un VPS.
Configura variables de entorno: `DB_URL`, `DB_USER`, `DB_PASS` (base MySQL del proveedor). Usa HTTPS.

## APK
`android-webview/MainActivity.java` es una app Android (Android Studio) que carga la tienda en un WebView.
Para el emulador usa `http://10.0.2.2:8080`; para publicar cambia a tu URL https.
Añade en AndroidManifest: `<uses-permission android:name="android.permission.INTERNET"/>`.
Compilar: Build > Build APK(s).

## Pendiente antes de producción real
Pasarela de pago real (Stripe/PayPal), imágenes subidas, recuperación de contraseña, pruebas, cambiar `ddl-auto` por migraciones.
