# MongoDB + ImageKit Integration (Complete Flow Notes)

---

## 🎯 Goal

User image upload kare →  
Server file receive kare →  
ImageKit par upload ho →  
URL mile →  
MongoDB mein store ho →  
Client ko response mile

---

## 🧠 Full Architecture Flow

Client (Flutter/Postman)
        ↓
HTTP multipart/form-data
        ↓
Express Route
        ↓
Multer (parse file)
        ↓
req.file.buffer
        ↓
ImageKit Upload Service
        ↓
Image URL returned
        ↓
MongoDB (URL saved)
        ↓
Response sent

---

## 1️⃣ Why Multer?

Express by default JSON samajhta hai.

Image upload JSON nahi hota.
It is sent as:

Content-Type: multipart/form-data

Multer:
- Raw HTTP stream parse karta hai
- File aur text fields separate karta hai
- req.file aur req.body banata hai

Example setup:

```js
const multer = require("multer");

const upload = multer({
  storage: multer.memoryStorage()
});
