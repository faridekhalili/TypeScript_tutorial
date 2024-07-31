# TypeScript_tutorial

- **What is it?** It's superset of JavaScript complemented with static typing (and type checking).
- **Transpilation?** The process of compiling TypeScript code to JavaScript.
- **Development Environment:**
  -   Install node: [nodejs.org](https://nodejs.org/en)
  -   `npm i -g typescript` 
- **TypeScript configuration file:**
    - `tsc --init`
    - `tsconfig.json`
      - `target`: Is the field that determines the version of JavaScript that the TypeScript compiler is going to generate.
      - `rootDir`: Where the compiler can find the `ts` files.
      - `outDir`: Where the compiler should store the `js` files (usually in a folder called `dist`? (maybe).
- **IntelliSense:** a set of code editing features that help programmers code faster and more efficiently.
  - An example of this could be code completions when the compiler is aware of the type of a variable, object, ... .
 
- **Compiling command:** `tsc code.ts`: We need to compile because browsers only understand JS and not TS.

## VSCode Shortcuts
- Opening the terminal: ``` ^` ```
- Commenting/Uncommenting: `⌘/`

## Debugging TypeScript Applications
- Go to `tsconfig.json` and enable the `sourceMap` feature.
  - A file that specifies how each line of the TypeScript code maps to the generated JavaScript code.
  - It will create a `code.js.map` file when compilation happens.
- Make break points.
- Go to debug pannel.
- Click _create launch.json file_.
- Select _Node.js_.
- In `launch.json` file add a feature `preLaunchTask` initialized to `tsc: build -tsconfig.json`.
- Go back to debug pannel and click on _Launch Program_.
-   - `f5`: start debugging.
    - `f10`: Step over: to execute one line.
    - `f11`: Step into: to step into a function.
    - `↑f11`: Step out: to step out of a function.
    - `↑⌘f5`: Restart:
    - `↑f5`: Restart:
- All _VARIABLES_ are seen and accessible in the left pannel.
- There is also a _WATCH_ window where we can add variables to watch.

## TypeScrip Compiler Configuration

<p>The configuration file is <code>tsconfig.json</code>. About the features:</p>

- `sourceMap`: A file that specifies how each line of the TypeScript code maps to the generated JavaScript code. It will create a `code.js.map` file when compilation happens.
- `noImplicitAny`:  If it is set to `true`, it won't allow implicit any types and if it is set to `false` it does.
- `target`: Is the field that determines the version of JavaScript that the TypeScript compiler is going to generate.
- `rootDir`: Where the compiler can find the `ts` files.
- `outDir`: Where the compiler should store the `js` files (usually in a folder called `dist`? (maybe).
- `noUnusedParameters`: If set to `true`, the compiler will complain if the function has a parameter not used in its body.
- `noImplicitReturns`: If set to `true`, it won't return _undefined_ for the code path that does not return a value.
- `noUnusedLocals`: If set to `true`, the compiler will complain if the function has a local variable not used in its body.
- `strictNullChecks`: If set to `true`, the compiler will complain if null is assigned to a variable of another type.
- `allowUnreachableCode`: If set to `false`, the compiler will complain if there's an unreachable code.

## TypeScrip Fundamentals

#### Fun Facts of TypeScript
- 123_456_789 is the same as 123456789.

### TypeScript Types
- **What are all the types in TS?**
  - number<sub>(JS&TS)</sub>
  - string<sub>(JS&TS)</sub>
  - boolean<sub>(JS&TS)</sub>
  - null<sub>(JS&TS)</sub>
  - undefined<sub>(JS&TS)</sub>
  - object<sub>(JS&TS)</sub>
  - any<sub>(TS)</sub>
  - unknown<sub>(TS)</sub>
  - never<sub>(TS)</sub>
  - enum<sub>(TS)</sub>
  - tuple<sub>(TS)</sub>
- **Implicit type annotation:** We don't need to specifically type annotate, if we don't, the initial value's type will be assigned to the variable. If there's no initial value, the type will be assumed to be _any_.
   - There's a feature in the `tsconfig.json` file names `noImplicitAny`. If it is set to `true`, it won't allow implicit any types and if it is set to `false` it does.
- **Array:**
    - **Syntax:** `number[]`.
- **Foreach:**
    - **Syntax:** `let numbers = number[]; numbers.forEach(n => n.<sth>)`.
- **tuple:** A fixed length array where each element has a particular type.
    - Often used when working with a pair of values (or 3 related values).
    - **Syntax:** let user: [number, string] = [1, 'Far'];
- **Enum:** A way to define a set of named constants (or a list of related constants).
    - We should use _PascalCase_ naming convention with it.
    - By default the value of the first element is set to 0 and the value for the rest increases by default one by one.
    - We can manually set the value of the first element to another number to start the values from there.
    - If the value of the first element be set to something other than a number, the value of the other elements should also be explicitly set.
    - If we don't plan to change the value of the elements, it's better to explicitly make it constant (`const` prefix), so that the compiler would generate more optimized code.
    - **Syntax:** enum Size { Small = 0, Medium, Large};
- **Function:**
  - If the return type is not annotated it is inferred and it'll be _void_ if nothing is returned.
  - However, if there's a conditional in the body that returns something in some situation and nothing in some, the default return type when nothing is returned is _undefined_.
  - **Signiture:** or type annotation of a function looks like this:
      - **Syntax:** _functionName(parameters typeofTheParameter): typeofReturnValue;_.
- **Optional:**
  - In certain situation like a function parameter, we can place a `?` after defining the name of a varibale to mark it being optional. Meaning that it's ok if the function is called without that parameter.
      - Alternatively, we can just provide a default value for that parameter.
  - Same for an object property.
- **readonly modifer:**
  - Can be provided as a prefix to make a property readonly.
- **Type Alias:**
  - Should use PascalCase naming convention for it.
  - **Syntax:** `type TypeName = {properties typeofProperties}`.
- **Union Types:**
  - **Syntax:** `type1 | type2 | ...`.
  - After this is done the intellisense will only show those autocompletion methods that exist for all of these unioned types.
- **Type narrowing:**
    - For something that has multiple types, we do it to have the intellisense specific to each of the unioned types.
    - **Syntax:** `if (typeof variable === type1) {...}`.
      - For objects we use `instanceof` rather than `typeof`.
    - These are called **type guard**s.
- **Intersection Types:**
  - Will have all of the properties and the methods of the intersectioned types.
  - **Syntax:** `type1 & type2 & ...`.
- **Literal Types:**
  - **Syntax:** `let var: value1 | value2 | ...`.
- **Optional Chaining:** To simplify code and remove the need for null checks.
  - We should explicitly use `null` and/or `undefined` in the type union statement if we want this to be possible (sometimes?).
  - **Falsy Values:** `(undefined, null, '', false, 0)`.
  - **The Nullish Coalescing Operator:** To fallback to a default value when dealing with _null_/_undefined_ objects. 
    - **Syntax:** `variable ?? the default'`: checks to see if variable is _null_ of _undefined_ and if yes, the default is returned, otherwise the variable is returned.
  - **Optional Property Access Operator:**
    - **Syntax:** `property?.method()`: Then it would return _undefined_ if that property is _null_ or _undefined_.
  - **Optional Element Access Operator:**
    - **Syntax:** `array?.[index]`: Then it would return _undefined_ if that element is _null_ or _undefined_.
  - **Optional Call Operator:**
    - **Syntax:** `function?.(parameter)`: Then it would return _undefined_ if that function is _null_ or _undefined_.
- **Type Assertions:** For when we know more about the type of an object than TypeScript itself.
  - If something is of type B sub-type of type A, and TypeScript is just assuming that is of type A, then intellisense might be more comprehensice if we use type assertion to explicitly tell TypeScript that it is of type B.
  - **Syntax:**
      - `let var = something as B`: Then we're telling that thing is of type B, while TypeScript would presume it is of type A.
      - `let var = <B> something`: Completely the same thing.
  - **Note:** This is not providing type conversion.
- **unknown Type:** A type-safe version of _any_.
   - A good substitute for the _any_ type when it seems inevitable. Then we can use type narrowing (the compiler will force this).
- **never Type:** This is used to specifically tell the compiler that some function never returns anything because if we don't, it'll be assumed to be void.
  - Occasions this might happen: Where there is an infinite loop in the body of the function or if it throws an error.
