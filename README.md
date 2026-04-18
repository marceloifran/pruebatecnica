# 🚀 Aplicación de Chat con IA en Tiempo Real

Una aplicación de chat premium full-stack construida con **Next.js**, **NestJS**, **Firebase** y **OpenAI**. Este proyecto demuestra una arquitectura lista para producción para comunicación en tiempo real y orquestación segura de IA.

## ✨ Características Principales

- **🛡️ Autenticación Segura**: Flujo completo de Registro, Login y Recuperación de contraseña mediante Firebase Auth.
- **💬 Mensajería en Tiempo Real**: Sincronización instantánea a través de Firebase Firestore con actualizaciones visuales de latencia cero.
- **🤖 Respuesta Inteligente con IA**: Interacción segura con ChatGPT (vía OpenRouter/OpenAI) mediada por un backend personalizado en NestJS.
- **🔒 Protección del Backend**: Validación estricta de ID Tokens mediante Firebase Admin SDK para proteger los endpoints de la IA.
- **🎨 Interfaz Premium**: Estética moderna "Glassmorphism", animaciones fluidas con Framer Motion y diseño totalmente responsivo.
- **🧠 Estado Global Avanzado**: Gestión de estado predecible utilizando Zustand.

---

## 📁 Estructura del Proyecto

| Directorio | Rol | Stack Tecnológico Principal |
| :--- | :--- | :--- |
| [**/frontend**](./frontend) | Aplicación Web Cliente | Next.js, Zustand, Firebase SDK, Framer Motion |
| [**/backend**](./backend) | Servidor API | NestJS, Firebase Admin, OpenAI SDK |

---

## 🚀 Configuración Rápida

### 1. Requisitos
- Node.js 18+
- Proyecto de Firebase (Auth y Firestore habilitados)
- API Key de OpenAI u OpenRouter

### 2. Puesta en Marcha
Sigue las guías detalladas en cada directorio:
- [Documentación del Frontend](./frontend/README.md)
- [Documentación del Backend](./backend/README.md)

---

## 🔒 Reglas de Seguridad de Firebase
Asegúrate de configurar las reglas de Firestore para proteger la privacidad de los usuarios:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /messages/{messageId} {
      allow read, write: if request.auth != null && request.auth.uid == request.resource.data.userId;
      allow read: if request.auth != null && request.auth.uid == resource.data.userId;
    }
  }
}
```

---
*Desarrollado como parte de una Prueba Técnica para Senior Full-Stack Developer.*
