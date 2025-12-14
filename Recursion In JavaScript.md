1. Recursion
   A recursive function must have:
      1. Base case → stops recursion
      2. Recursive case → calls itself
   Without a base case → infinite recursion → stack overflow.

2. Execution Context & Stack
- Every function call creates a new execution context
- Execution contexts are stored in the Call Stack

3. Memory usage: Recursion vs Iteration
    Recursion
    - Cleaner & expressive
    - Uses call stack
    - Risk of stack overflow

    Iteration
    - More memory-efficient
    - Uses heap / loop variables
    - Safer for large inputs

    Use recursion when:
    - Problem is naturally recursive (tree, nested objects)
    - Depth is limited

    Use iteration when:
    - Performance & memory matter
    - Input size can be large

4. Nested function calls & pausing
  - When a function calls another function:
    - Current function pauses
    - Its execution context stays on stack

  - When the called function finishes:
    - Stack unwinds
    - Execution resumes where it left off

5. Recursive approach for nested objects (company example)

let company = {
  sales: [{ name: 'John', salary: 1000 }, { name: 'Alice', salary: 1600 }],
  development: {
    sites: [{ name: 'Peter', salary: 2000 }, { name: 'Alex', salary: 1800 }],
    internals: [{ name: 'Jack', salary: 1300 }]
  }
};

This structure is recursive by nature
Object → values → arrays → objects → arrays → …

So recursion is clearer and safer than iteration.

Typical recursive solution:
function sumSalaries(department) {
  if (Array.isArray(department)) {
    return department.reduce((sum, emp) => sum + emp.salary, 0);
  } else {
    let sum = 0;
    for (let subDept of Object.values(department)) {
      sum += sumSalaries(subDept);
    }
    return sum;
  }
}

This is exactly the kind of problem recursion is meant for.

6. Arrays vs Linked Lists

- Array in JS:
  - JS arrays are dynamic arrays
   - Insertion/deletion:
     At end → fast (push, pop)
     At start/middle → slower (elements shift)

- linked Lists in JS:
  - Not built-in
  - Higher memory usage
  - Poor cache performance
  - Rarely used in real JS applications