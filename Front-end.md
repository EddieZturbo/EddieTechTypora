# Front-end Dev

## HTML



## JavaScript



### Async

> 异步是为了提高CPU的占用率，让其始终处于忙碌状态。
>
> 有些操作（最典型的就是I/O）本身不需要CPU参与，而且非常耗时，如果不使用异步就会形成阻塞状态，CPU空转，页面卡死。
>
> 在异步环境下发生I/O操作，CPU就把I/O工作扔一边（此时I/O由其他控制器接手，仍然在数据传输），然后处理下一个任务，等I/O操作完成后通知CPU（回调就是一种通知方式）回来干活。
>
> 《JavaScript异步与回调》想要表达的核心内容是，异步工作的具体结束时间是不确定的，为了准确的在异步工作完成后进行后继的处理，就需要向异步函数中传入一个回调，从而在完成工作后继续下面的任务。

#### Promise

![image-20240521153108625](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240521153108625.png)

> `Promise` 提供了一个强大的方式来**处理异步操作**及其结果的处理，通过状态管理和回调队列，可以更优雅地组织代码。而底层实现则涉及状态管理、回调函数队列、异步任务调度等核心概念。
>
> `Promise` 是JavaScript中一种用于处理异步操作的对象。它表示一个异步操作最终会成功或失败，并返回结果。`Promise` 对象有三种状态：
>
> - **Pending（待定）**: 初始状态，既不是成功，也不是失败。
> - **Fulfilled（已成功）**: 意味着操作成功完成。
> - **Rejected（已失败）**: 意味着操作失败。

##### 核心底层原理

> 要理解Promise的核心实现原理，我们需要知道一些JavaScript中的关键概念，**事件循环（Event Loop）**，**任务队列（Task Queue）**，以及微任务（Microtask）。
>
> ##### 简化版的Promise实现
>
> 以下是一个简化版的 `Promise` 实现，以帮助理解其核心原理。
>
> ```js
> javascriptCopy codeclass MyPromise {
>     constructor(executor) {
>         this.state = 'pending';
>         this.value = undefined;
>         this.reason = undefined;
>         this.onFulfilledCallbacks = [];
>         this.onRejectedCallbacks = [];
> 
>         const resolve = (value) => {
>             if (this.state === 'pending') {
>                 this.state = 'fulfilled';
>                 this.value = value;
>                 this.onFulfilledCallbacks.forEach(fn => fn());
>             }
>         };
> 
>         const reject = (reason) => {
>             if (this.state === 'pending') {
>                 this.state = 'rejected';
>                 this.reason = reason;
>                 this.onRejectedCallbacks.forEach(fn => fn());
>             }
>         };
> 
>         try {
>             executor(resolve, reject);
>         } catch (error) {
>             reject(error);
>         }
>     }
> 
>     then(onFulfilled, onRejected) {
>         if (this.state === 'fulfilled') {
>             onFulfilled(this.value);
>         } else if (this.state === 'rejected') {
>             onRejected(this.reason);
>         } else {
>             this.onFulfilledCallbacks.push(() => onFulfilled(this.value));
>             this.onRejectedCallbacks.push(() => onRejected(this.reason));
>         }
>     }
> }
> 
> // 使用示例
> const promise = new MyPromise((resolve, reject) => {
>     setTimeout(() => {
>         resolve('Success');
>     }, 1000);
> });
> 
> promise.then((value) => {
>     console.log(value); // 'Success'
> });
> ```
>
> ##### 解释
>
> 1. **状态和结果**: `Promise` 内部维护了三个状态（`pending`, `fulfilled`, `rejected`）以及相应的结果（`value` 或 `reason`）。
> 2. **执行器函数**: 执行器函数（executor）在创建 `Promise` 对象时立即执行，并传递两个函数 `resolve` 和 `reject`。调用 `resolve` 将 `Promise` 状态变为 `fulfilled`，调用 `reject` 将状态变为 `rejected`。
> 3. **回调队列**: 当 `Promise` 处于 `pending` 状态时，将所有 `then` 的回调函数存储在队列中。当状态改变时，依次执行相应的回调函数。
> 4. **异步操作**: `setTimeout` 用于模拟异步操作，实际实现中会使用微任务队列来处理 `Promise` 回调。
>
> #### 更复杂的Promise实现
>
> 对于更复杂的 `Promise` 实现，还需要处理链式调用、错误捕获以及微任务队列等。以下是一个更完整的 `Promise` 实现简化版：
>
> ```js
> javascriptCopy codeclass MyPromise {
>     constructor(executor) {
>         this.state = 'pending';
>         this.value = undefined;
>         this.reason = undefined;
>         this.onFulfilledCallbacks = [];
>         this.onRejectedCallbacks = [];
> 
>         const resolve = (value) => {
>             if (this.state === 'pending') {
>                 this.state = 'fulfilled';
>                 this.value = value;
>                 this.onFulfilledCallbacks.forEach(fn => fn());
>             }
>         };
> 
>         const reject = (reason) => {
>             if (this.state === 'pending') {
>                 this.state = 'rejected';
>                 this.reason = reason;
>                 this.onRejectedCallbacks.forEach(fn => fn());
>             }
>         };
> 
>         try {
>             executor(resolve, reject);
>         } catch (error) {
>             reject(error);
>         }
>     }
> 
>     then(onFulfilled, onRejected) {
>         return new MyPromise((resolve, reject) => {
>             if (this.state === 'fulfilled') {
>                 queueMicrotask(() => {
>                     try {
>                         const x = onFulfilled(this.value);
>                         resolvePromise(x, resolve, reject);
>                     } catch (error) {
>                         reject(error);
>                     }
>                 });
>             } else if (this.state === 'rejected') {
>                 queueMicrotask(() => {
>                     try {
>                         const x = onRejected(this.reason);
>                         resolvePromise(x, resolve, reject);
>                     } catch (error) {
>                         reject(error);
>                     }
>                 });
>             } else {
>                 this.onFulfilledCallbacks.push(() => {
>                     queueMicrotask(() => {
>                         try {
>                             const x = onFulfilled(this.value);
>                             resolvePromise(x, resolve, reject);
>                         } catch (error) {
>                             reject(error);
>                         }
>                     });
>                 });
> 
>                 this.onRejectedCallbacks.push(() => {
>                     queueMicrotask(() => {
>                         try {
>                             const x = onRejected(this.reason);
>                             resolvePromise(x, resolve, reject);
>                         } catch (error) {
>                             reject(error);
>                         }
>                     });
>                 });
>             }
>         });
>     }
> }
> 
> function resolvePromise(x, resolve, reject) {
>     if (x instanceof MyPromise) {
>         x.then(resolve, reject);
>     } else {
>         resolve(x);
>     }
> }
> ```
>
> #### 解释更复杂的实现
>
> 1. **queueMicrotask**: 使用 `queueMicrotask` 将回调函数加入微任务队列，以确保回调函数在当前调用栈结束后执行。
> 2. **resolvePromise**: 用于处理 `then` 返回值的逻辑。如果返回值是 `Promise`，则递归调用 `then` 方法，否则直接调用 `resolve`。
> 3. **链式调用**: `then` 方法返回一个新的 `Promise` 对象，以支持链式调用。

##### 基本用法

> Promise的基本用法
>
> ##### 创建Promise对象
>
> ```js
> javascriptCopy codelet promise = new Promise((resolve, reject) => {
>     // 异步操作
>     let success = true; // 假设异步操作成功
>     if (success) {
>         resolve("Operation succeeded!");
>     } else {
>         reject("Operation failed.");
>     }
> });
> ```
>
> ##### 使用then()和catch()方法
>
> ```js
> javascriptCopy codepromise.then((result) => {
>     console.log(result); // "Operation succeeded!"
> }).catch((error) => {
>     console.log(error); // "Operation failed."
> });
> ```
>
> 

##### 链式调用

> Promise 的强大功能之一是可以链式调用 `then()` 方法，这样可以让多个异步操作按顺序执行。
>
> ```js
> javascriptCopy codenew Promise((resolve, reject) => {
>     resolve(1);
> }).then((value) => {
>     console.log(value); // 1
>     return value + 1;
> }).then((value) => {
>     console.log(value); // 2
>     return value + 1;
> }).then((value) => {
>     console.log(value); // 3
> });
> ```

#### Async/await

> *"async and await make promises easier to write"*
>
> **async** makes a function return a Promise
>
> **await** makes a function wait for a Promise

##### Async

> The keyword `async` before a function makes the function return a promise:
>
> **Example**
>
> ```js
> async function myFunction() {
>  return "Hello";
> }
> 
> //Is the same as:
> 
> function myFunction() {
>  return Promise.resolve("Hello");
> }
> 
> //Here is how to use the Promise:
> 
> myFunction().then(
>  function(value) { /* code if successful */ },
>  function(error) { /* code if some error */ }
> );
> ```
>
> **Example**
>
> ```js
> async function myFunction() {
>  return "Hello";
> }
> myFunction().then(
>  function(value) {myDisplayer(value);},
>  function(error) {myDisplayer(error);}
> );
> ```
>
> Or simpler, since you expect a normal value (a normal response, not an error):
>
> **Example**
>
> ```js
> async function myFunction() {
>  return "Hello";
> }
> myFunction().then(
>  function(value) {myDisplayer(value);}
> );
> ```
>
> 

##### Await

> The `await` keyword can only be used inside an `async` function.
>
> The `await` keyword makes the function pause the execution and wait for a resolved promise before it continues:
>
> ```js
> let value = await promise;
> ```
>
> **Basic Syntax**
>
> ```js
> async function myDisplay() {
>  let myPromise = new Promise(function(resolve, reject) {
>   resolve("I love You !!");
>  });
>  document.getElementById("demo").innerHTML = await myPromise;
> }
> 
> myDisplay();
> ```
>
> **Example without reject**
>
> ```js
> async function myDisplay() {
>  let myPromise = new Promise(function(resolve) {
>   resolve("I love You !!");
>  });
>  document.getElementById("demo").innerHTML = await myPromise;
> }
> 
> myDisplay();
> ```
>
> **Waiting for a Timeout**
>
> ```js
> async function myDisplay() {
>   let myPromise = new Promise(function(resolve) {
>     setTimeout(function() {resolve("I love You !!");}, 3000);
>   });
>   document.getElementById("demo").innerHTML = await myPromise;
> }
> 
> myDisplay();
> ```
>
> **Waiting for a File**
>
> ```js
> async function getFile() {
>   let myPromise = new Promise(function(resolve) {
>     let req = new XMLHttpRequest();
>     req.open('GET', "mycar.html");
>     req.onload = function() {
>       if (req.status == 200) {
>         resolve(req.response);
>       } else {
>         resolve("File not Found");
>       }
>     };
>     req.send();
>   });
>   document.getElementById("demo").innerHTML = await myPromise;
> }
> 
> getFile();
> ```
>
> 



## Runtime Environment

![image-20240111154212365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240111154212365.png)

![image-20240111154410273](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240111154410273.png)

### Nvm 

[GitHub](https://github.com/nvm-sh/nvm?tab=readme-ov-file)

![image-20240111153238693](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240111153238693.png)

### Node.js

[GitHub](https://github.com/nodejs/node)

![image-20240111153813528](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240111153813528.png)

### Npm 

[GitHub](https://github.com/npm/cli)

![image-20240111153721870](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240111153721870.png)
