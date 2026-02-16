# Node.js Backend Basics — Personal Notes

---

## 1. Packages

**Package = ready‑made code library (installed using npm)**

Used to avoid writing everything from scratch.

Examples:

* express → server banane ke liye
* bcrypt → password hashing
* jsonwebtoken → authentication
* mongoose → database connection

Install:

```
npm install express
```

**Definition:**

> A package is a collection of reusable modules distributed via npm.

---

## 2. Modules (Node.js Files)

**Module = ek single file jisme specific kaam ka code hota hai**

Project ko parts mein tod dete hain:

* server.js
* db.js
* userController.js
* auth.js

Har file ek module hai.

---

## 3. require() vs import

| require                    | import                        |
| -------------------------- | ----------------------------- |
| Old Node system (CommonJS) | Modern JS system (ES Modules) |
| Default Node behavior      | "type":"module" chahiye       |
| Sync                       | Static/modern                 |

Enable import:

```
{
  "type": "module"
}
```

---

## 4. module.exports (Core Concept)

Node internally har file ko aise treat karta hai:

```
const module = { exports: {} };
return module.exports;
```

**require(file) = module.exports ka return value**

### Single export

```
function add(a,b){ return a+b }
module.exports = add;
```

### Multiple exports

```
function add(a,b){ return a+b }
function sub(a,b){ return a-b }
module.exports = { add, sub };
```

---

## 5. exports vs module.exports

Start mein:

```
exports === module.exports
```

### Property add karna (OK)

```
exports.add = fn
```

### Replace karna (galat)

```
exports = fn ❌
module.exports = fn ✅
```

**Rule:**

* multiple cheezain → exports.xyz
* single cheez → module.exports = ...

---

## 6. package.json

Project ka control panel / identity card

Batata hai:

* dependencies kya chahiye
* scripts kya hain
* project ka naam

Example:

```
{
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

Meaning:

> Express version 4 ka compatible koi bhi chalega

---

## 7. package-lock.json

Exact installed versions ka snapshot

Guarantee karta hai ke har machine pe same packages install hon.

---

## Easy Difference

* package.json → kya chahiye
* package-lock.json → exactly kya mila

---

## Golden Rules (Important)

1. require() always returns module.exports
2. File private hoti hai jab tak export na karo
3. module.exports final return value hoti hai
4. Lock file delete nahi karni
5. Packages = external code, Modules = apni files

---

**End of Notes**
