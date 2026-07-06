# Episode 2 : How JS is Executed & Call Stack

- Every JavaScript program starts by creating a **Global Execution Context (GEC)**.
- Execution happens in **two phases**:
  - **Memory Creation Phase** – Memory is allocated for variables and functions.
  - **Code Execution Phase** – Code executes line by line.

Consider the following example:

```js
var n = 2;
function square(num) {
  var ans = num * num;
  return ans;
}
var square2 = square(n);
var square4 = square(4);
```

## Memory Creation Phase

JavaScript scans the code and allocates memory:

- Variables (`n`, `square2`, `square4`) → `undefined`
- Function (`square`) → Entire function definition

![Execution Context Phase 1](/assets/phase1.jpg "Execution Context")

## Code Execution Phase

- `n` is assigned the value `2`.
- Function declarations are skipped since they were stored during the memory phase.
- Calling `square(n)` creates a **new Execution Context**.

Inside the function:

- Memory is allocated for `num` and `ans` (`undefined` initially).
- `num` receives `2`.
- `ans = num * num` → `4`.
- `return ans` returns control to the Global Execution Context and deletes the function's Execution Context.

![Execution Context Phase 2](/assets/phase2.jpg "Execution Context")

The same process repeats for `square(4)`. After all code finishes, the Global Execution Context is removed.

Final state before deletion:

![Execution Context Phase 2](/assets/final_execution_context.jpg "Execution Context")

## Call Stack

JavaScript uses the **Call Stack** to manage Execution Contexts.

- Keeps track of function calls.
- Creates a new Execution Context for every function call.
- Removes it after the function returns.
- Maintains the correct order of execution.

**Also known as:**

- Program Stack
- Control Stack
- Runtime Stack
- Machine Stack
- Execution Context Stack

<hr>

Watch Live On YouTube below:

<a href="https://www.youtube.com/watch?v=iLWTnMzWtj4&t=1s&ab_channel=AkshaySaini" target="_blank"><img src="https://img.youtube.com/vi/iLWTnMzWtj4/0.jpg" width="750"
alt="How JS is executed & Call Stack Youtube Link"/></a>
