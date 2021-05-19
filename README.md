# About Jest

- Jest is a testing platform, widely adapted by many large companies and swiftly adopted by the React community.
- Sits on top of Jasmine, so the API is nearly identical.
- Has all of it’s API documented, along with guides, examples and helpful community on forums like Reactiflux and Stack Overflow.
- Focuses on Developer Experience (speed and ease of use is the first priority.)
- Provides meaningful error messages.
- Runs on Continuous Integration servers without extra tooling (abstracting the DOM with jsdom library.)
- Provides code coverage out of the box.
- Integrates with Babel and TypeScript seamlessly.

- run your Angular tests without a browser.

- run test suite several times faster

- rerun instantly only tests related to latest code changes

# Step by step
Step 1. Remove `karma` and install `jest`

`npm remove karma karma-chrome-launcher karma-coverage-istanbul-reporter karma-jasmine karma-jasmine-html-reporter @types/jasmine @types/jasminewd2 jasmine-core jasmine-spec-reporter`

`npm install --save-dev jest jest-preset-angular @types/jest`

Step 2. _(Optional)_ Remove `test.ts` and `karma.conf.js` 

`rm ./karma.conf.js ./src/test.ts`

Step 3.  Create `setup-jest.ts` to project root and add the following:

`import 'jest-preset-angular/setup-jest';`

Step 4. Create `jest.config.js` in project root and add the following:

```ts
module.exports = {
    preset: 'jest-preset-angular',
    setupFilesAfterEnv: ['<rootDir>/setup-jest.ts'],
  };
```

or to your root `package.json`

```ts
{
  "jest": {
    "preset": "jest-preset-angular",
    "setupFilesAfterEnv": ["<rootDir>/setup-jest.ts"]
  }
}
```

Step 5. Replace `jasmine` with `jest` in types array of `compilerOptions` in `tsconfig.spec.json`:

```ts
"compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jest"
    ]
  },
```

Step 6. Add jest scripts to `package.json`:

```ts
"scripts": { 
    "test": "jest",
    "test-watch": "jest --watch"
}
```

Step 7. Set `esModuleInterop` is `true` in the file `tsconfig.json`

```ts
"compilerOptions": {
    "esModuleInterop": true
  },
```

Step 8. run `npm test`