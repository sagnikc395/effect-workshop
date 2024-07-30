## Effect Core Concepts

- intro to core effect concepts
- real world examples by rewriting two apps
- peek into 'advanced' Effect.

### what is an 'Effect' ?

- an Effect is a description of a program that is lazy and immutable.
- program -> series of transformations that we can run to transform an given input to an output.
- immutable -> scripts are inehritnly immutable, if not changing the source.
- laziness -> programs are lazy meaning they are not evaluated until they are required to do so.
- Effect -> has all of these properties but made into a inside Javascript type. -> Functions

- Effect builds on top of what functions can offer !
- General defn of function:

```ts
type Function<Args, T> = (args: Args) => T;
```

- however this does not encode the error in the type definition which we encode , in try and catch.
- instead,Effect works with errors as values kinda proposition.

- better defn using errors:

```ts
type SaferFunction<Args, T, E> = (...args: Args) => T | E;
```

- however this also comes with someproblems as it becomes harder to discriminate errors.

- composing functions with errors:
  - inner function that might error and outer function that also might error
  - only operate on value if it is not an error.

```ts
declare function Inner(): "baz" | "bar" | Error;

function Outer(): number | Error {
  const result = Inner();
  if (result instanceof Error) {
    return result;
  }
  return result.length;
}
```

- we are forced here to handle errors at every single point, even if we don't care.

### Effects are differnt :

- Effect type has 2 type parameter:

  - Value and Error(default to never)

- so we can transform our previous functions as :

```ts
declare const foo: Effect<number, never>;

declare const bar: Effect<number, Error>;
```

- having errors as a first class citizens and owning errors , and can compose errors also.


