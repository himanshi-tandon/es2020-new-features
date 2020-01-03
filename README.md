# ES2020 New Features

/*===========================JavaScript ES2020===========================*/
/*
1. globalThis  [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis]
2. Promise.allSettled()  [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled]
3. Nullish Coalescing Operator  [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator]
4. Optional Chaining Operator (?.)  [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining]
5. BigInt  [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt]
*/

// -------------------------------------**Feature 01 - globalThis**

```javascript
console.log("window", window);
console.log("self", self); // Used in web workers
console.log("frames", frames);
console.log("this", this);
console.log("globalThis", globalThis);
/* All returuns same window objects */
```

// -------------------------------------**Feature 02 - Promise.allSettled()**

```javascript
const p1 = new Promise((resolve, reject) => setTimeout(resolve, 200));
const p2 = new Promise((resolve, reject) => setTimeout(reject, 300));
const p3 = new Promise((resolve, reject) => setTimeout(resolve, 4000));

Promise.allSettled([p1, p2, p3]).then(results => {
    results.forEach(result => console.log(result))
});
// After the 4 sec
/*
	{ status: "fulfilled", value: undefined }
	{ status: "rejected", reason: undefined }
	{ status: "fulfilled", value: undefined }
*/
```

// -------------------------------------**Feature 03 - Nullish Coalescing Operator**

```javascript
let x = {
    profile: {
        name: 'Suryansh',
        age: 21
    }
};

console.log(x.profile.name) // Suryansh

let x1 = {
    profile: {
        age: 21
    }
};

console.log(x1.profile.name || 'John') // John

// Empty value and 0 treated as false
let x2 = {
    profile: {
        name: '',
        age: 0
    }
};

console.log(x2.profile.name || 'John') // John
console.log(x2.profile.age || '25') // 25

let x3 = {
    profile: {
        name: '',
        age: 0
    }
};

console.log(x3.profile.name ?? 'John') // blank_string
console.log(x3.profile.age ?? '25') // 0
```

// -------------------------------------**Feature 04 -  Optional Chaining Operator (?.)**

```javascript
let x4 = {
    profile: {
        name: 'Suryansh'
    }
};

console.log(x4.profile.age) // undefined

let x5 = {
	
};

// console.log(x5.profile.age); // (If two level of undefined it will give an error) Uncaught TypeError: Cannot read property 'age' of undefined
console.log(x5 && x5.profile && x5.profile.name); // undefined
console.log(x5?.profile?.name);  // undefined
```

// -------------------------------------**Feature 05 -  BigInt**

```javascript
const max = Number.MAX_SAFE_INTEGER
console.log(max); // 9007199254740991
console.log(max + 1); // 9007199254740991 (Same value)
console.log(max + 2); // 9007199254740991 (Same value)


const theBiggestInt = 9007199254740991n

const alsoHuge = BigInt(9007199254740991)
// ↪ 9007199254740991n

const hugeString = BigInt("9007199254740991")
// ↪ 9007199254740991n

const hugeHex = BigInt("0x1fffffffffffff")
// ↪ 9007199254740991n

const hugeBin = BigInt("0b11111111111111111111111111111111111111111111111111111")
// ↪ 9007199254740991n
```
