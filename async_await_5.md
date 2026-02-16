## JS Async/Await


## 1. Async / Await

Async/Await is a cleaner way to work with Promises. It does not replace promises — it uses them internally.

Rule:

```
async function → always returns Promise
await → pauses function until promise resolves
```

### Example 1: Basic async

```js
function getData() {
  return new Promise(resolve => {
    setTimeout(() => resolve("User loaded"), 1000);
  });
}

async function main() {
  const data = await getData();
  console.log(data);
}

main();
```

---

### Example 2: Sequential execution

```js
function step1() { return Promise.resolve("Step 1 done"); }
function step2() { return Promise.resolve("Step 2 done"); }

async function run() {
  const a = await step1();
  const b = await step2();
  console.log(a, b);
}
run();
```

---

### Example 3: Error handling

```js
function login(user) {
  return new Promise((res, rej) => {
    if (!user) rej("No user");
    else res("Welcome");
  });
}

async function start() {
  try {
    const msg = await login(null);
    console.log(msg);
  } catch (err) {
    console.log("Error:", err);
  }
}
start();
```

---

### Example 4: Parallel execution

```js
function getUsers() {
  return new Promise(res => setTimeout(()=>res("Users"),1000));
}
function getProducts() {
  return new Promise(res => setTimeout(()=>res("Products"),1000));
}

async function load() {
  const [u,p] = await Promise.all([getUsers(), getProducts()]);
  console.log(u,p);
}
load();
```

---

### Example 5: Async returns promise

```js
async function test(){
  return "Hello";
}

test().then(console.log);
```

