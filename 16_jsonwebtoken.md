# JWT (JSON Web Token) – Core Concept

## 1. JWT Kya Hota Hai?

JWT ek signed token hota hai jo server generate karta hai aur client ko deta hai. Iska purpose hota hai user ki identity ko stateless tareeke se verify karna.

Stateless ka matlab: server ko session store karne ki zarurat nahi hoti. Har request ke sath token aata hai aur server usko verify karta hai.

---

## 2. JWT Ka Structure

JWT 3 parts par mushtamil hota hai:

1. Header (algorithm info)
2. Payload (user data jaise id, role)
3. Signature (secret key se sign kiya gaya part)

Signature ensure karti hai ke token tamper nahi hua.

---

## 3. JWT Authentication Flow

Login ke baad:

1. User credentials verify hote hain
2. Server JWT generate karta hai
3. Client ko token diya jata hai (cookie ya header mein)
4. Har protected request ke sath token bheja jata hai
5. Server token verify karta hai

---

## 4. JWT Mein Kya Store Karna Chahiye?

* User ID
* Role
* Minimal required claims

Sensitive data (password, secrets) kabhi token mein store nahi karna chahiye.

---

## 5. Important Security Points

* Token expiry zaroor set karo
* Secret key secure rakho
* httpOnly cookie use karo
* Token compromise possible hai, isliye minimal payload rakho

---

## Faida

* Scalable authentication
* Server-side session storage ki zarurat nahi
* Microservices architecture mein useful

---

## Technical Questions (With Answers)

**Q1:** Agar JWT expire na ho to kya risk hai?

**Answer:** Compromised token indefinitely use ho sakta hai, jis se unauthorized access ka risk barhta hai.

**Q2:** Kya JWT revoke karna easy hota hai?

**Answer:** Nahi. Kyunki JWT stateless hota hai, revoke karne ke liye blacklist ya token versioning strategy use karni padti hai.
