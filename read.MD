# 🌍 Vercel Galeri

Herkese açık resim galerisi - Firebase destekli

## 🚀 Kurulum

1. Firebase projesi oluştur: https://console.firebase.google.com
2. Firestore Database ve Storage aktifleştir
3. `index.html` içindeki Firebase config'i güncelle
4. Vercel'e deploy et

## 📁 Firebase Ayarları

- Authentication: Kapalı (anonim yükleme)
- Firestore: Açık (public read/write)
- Storage: Açık (public upload)

## 🔧 Firestore Rules

\\`\\`\\`javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /gallery/{document} {
      allow read, write: if true;
    }
  }
}
\\`\\`\\`

## 📷 Storage Rules

\\`\\`\\`javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /images/{allPaths=**} {
      allow read, write: if true;
    }
  }
}
\\`\\`\\`