# Real-Time AI Chat App - Technical Test

A premium real-time chat application built with **Next.js**, **NestJS**, **Firebase**, and **ChatGPT**.

## 🚀 Features
- **Firebase Authentication**: Email/Password login, registration, and password reset.
- **Real-Time Messaging**: Instant sync using Firebase Firestore.
- **AI Integration**: Automatic responses from ChatGPT via a secure NestJS backend.
- **Security**: ID Token validation in the backend via Firebase Admin SDK.
- **State Management**: Global state handled by Zustand.
- **Premium UI**: Glassmorphism design, smooth animations, and responsive layout.

## 📁 Project Structure
- `/frontend`: Next.js Web App
- `/backend`: NestJS API Server

---

## 🛠️ Setup Instructions

### 1. Firebase Setup
1. Create a project in [Firebase Console](https://console.firebase.google.com/).
2. Enable **Authentication** (Email/Password).
3. Create a **Firestore Database** in test mode or with specific rules (see below).
4. Go to **Project Settings > General** and add a Web App to get your configuration.
5. Go to **Project Settings > Service Accounts** and click **Generate new private key** to get the JSON for the backend.

### 2. Backend Configuration
1. Navigate to `backend/`.
2. Copy `.env.example` to `.env`.
3. Fill in your `OPENAI_API_KEY`.
4. Fill in `FIREBASE_SERVICE_ACCOUNT` with the contents of the JSON file you downloaded.
5. Run `npm install`.
6. Start the server: `npm run start:dev`. (Runs on http://localhost:3001)

### 3. Frontend Configuration
1. Navigate to `frontend/`.
2. Copy `.env.example` to `.env.local`.
3. Fill in your Firebase Web App configuration.
4. Run `npm install`.
5. Start the app: `npm run dev`. (Runs on http://localhost:3000)

---

## 🔒 Firestore Security Rules
Use these rules for the messages collection:
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

## 🧠 Architecture Decisions
- **Backend Writing to Firestore**: Ensure bot responses are persisted securely and synced in real-time without frontend lag.
- **Zustand Stores**: Clean separation between Auth and Chat logic.
- **CSS Modules/Vanilla CSS**: Custom premium styling without the overhead of heavy CSS frameworks.
- **Firebase Admin Guard**: Prevents unauthorized access to AI endpoints.
