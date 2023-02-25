# tdd-workshop

## Step 1 - installing and configuration

Install everything with `npm install`
Run the test runner via `npm run test`

The test runner looks in the `tsconfig.include` directories for any files ending with `_test.ts`. Inside each file found, any functions exported with a name beginning with `test` will be run. Be sure to set `tsconfig.include` to point to your source directory.

## Step 2 - test structure

Write your first test. Make sure it passes. Run the test runner. Change the test to fail, then run it again. Familiarize yourself with the output.

A test looks like this:

```ts
export function testBasic() {
  assert.deepStrictEqual(0, 1);
}
```

You'll want to import `assert`. Node comes with a version of `assert`, but it doesn't have type restrictions. `@eeue56/ts-assert` is included, which provides type-safe equivilents of Node's `assert` functions.

```ts
import * as assert from "@eeue56/ts-assert";
```

To run a single file, you can use `npm run test -- --file src/<filename>`. To run a single function - either in a single file, or across multiple files, use `npm run test -- --function testFunctionName`. To only view failures, run `npm run test -- --only-fails`.

## Step 3 - basic tests

Now we will write tests to match a spec. The spec will get increasingly more complicated as we go.

### The user

Consider that we have users that we would like to show the name of. Begin with the type. Every user has a first name and a last name.

Write a function that takes a user object, and returns the full name of the user as a string. Don't actually implement it - start with the function signature.

Now we move to write some tests. First write a test that fails, then fix the function to make it pass. Try to think of edgecases. Write a test for each edgecase, in the same file. After you write each test case, run the tests to ensure they pass.

### Short names

A user may have multiple names. For example Erik Gustav Jacobsen. We only want to display the very first and the very last name. Make sure your test cases cover this.

### Titles

Users can also have titles. Typical titles include `Mr, Mrs, Miss, Ms, Mx, Dr`. Our app is targeted at doctors, who value their title quite highly. `Erik Gustav Jacobsen` should be greeted as `Dr Jacobsen`.

## Step 4 - snapshot tests

Snapshot tests are a way of ensuring that a function consistently produces the same output as you are working.

Let's start by writing a test for some HTML. Chose a HTML output to use, then write a test with that output. Now write a function that will generate that HTML.

Many test runners like Jest support snapshots that are automatically generated for you.
