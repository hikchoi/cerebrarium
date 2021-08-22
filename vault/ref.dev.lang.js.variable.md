---
id: bf8d4878-7f78-413c-97ef-c386bd6c0126
title: Variable
desc: ''
updated: 1609659555385
created: 1609659548420
---

#  Variable Declaration
- `var` has weird scoping rules
    - It is accessible anywhere within their containing scope regardless of the containing block.
        - It's not an error to declare the same variable multiple times
- `let`, unlike `var`, uses lexical scoping.
    - the variable scope doesn't leak now.
- Shadowing : introducing a new name in a more nested scope
- `let` or `const`? 
    - Depends. Apply the principle of least privilege.
- Destructuring
    - ECMAScript 2015 feature
    - e.g.
    ```js
    let input = [1, 2];
    let [first, second] = input;
    console.log(first); // 1
    console.log(second); // 2
    ```
    - equivalent to indexing.
    - use `...` for remaining items (they can be omitted if you don't need them.)
    ```js
    let [first, ...rest] = [1, 2, 3, 4];
    console.log(first); // 1
    console.log(rest); // [2, 3, 4]
    ```
    - also works with objects
    ```js
    let o = {
        a: "foo",
        b: 12,
        c: "bar",
    };
    let { a, b } = o;
    ```
    - type annotation with destructuring is confusing:
    ```js
    let { a, b }: { a: string; b; number } = o;
    ```
    - destructuring with default values
    ```js
    // b? means b is optional
    function foo(o: { a: string; b?: number }) {
        // give default value of b since it is optional
        let { a, b = 1 } = o
    }
    ```
    - function declaration with destructuring
    ```js
    type C = { a: string; b?: number };
    function f({ a, b }: C): void {
        //..
    }
    ```
    - Anything but a simple destructuring gets extremely confusing. Use sparingly.
- Spreading
    - opposite of destructuring
    ```js
    let first = [1, 2];
    let second = [3, 4];
    let both = [0, ...first, ...second, 5]; // [0, 1, 2, 3, 4, 5]
    ```
    - also works with objects
    ```js
    let defaults = { food: "spicy", price: "$$", ambiance: "noisy" }
    let search = { ...defaults, food: "rich" }
    // properties coming later in the spread object overwrites.
    ```
    - with object spreading, you lose methods.
