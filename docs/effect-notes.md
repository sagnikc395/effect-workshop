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
-
