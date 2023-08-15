# ts-node-repro

## Table of contents
1. [Search Terms](#search-terms)
2. [Expected Behavior](#expected-behavior)
3. [Actual Behavior](#actual-behavior)
4. [Steps to reproduce the problem](#steps-to-reproduce-the-problem)
5. [Repository specific information](#repository-specific-information)

### Search Terms

- typescript
- transpile
- behavior
- changed 

### Expected Behavior

Typescript transpile behavior should not be modified when running the typescript compiler, but it is. As an example, if I set `target` compiler option of the typescript configuration file to `ES5` and use some functionality from `Symbol`s, the compiler will fail to compile if I do not have ts-node installed, but if I do it compiles succesfully.

### Actual Behavior

Typescript compiler behavior should not change with `ts-node` installed. If I want to target a different language version for ts-node the option should be set in `ts-node` object inside the `tsconfig.json` file, but not change the behavior of the typescript compiler.

### Steps to reproduce the problem

- Install `typescript` as a dev dependency
- Create `tsconfig.json` file
- Set the `target` option to `ES5`, `include` to `["src"]` and `outDir` to `./dist`
- Write some code that uses a feature from a new version of the language (e.g. `Symbol`)
- Try to compile the project with typescript compiler
- Install `ts-node` as a dev dependency
- Retry the compilation step

### Repository specific information

The folder named `example-with-ts-node` illustrates example with `ts-node` installed while the folder `example-without-ts-node` illustrates behavior without `ts-node` installed.

In both projects you can run the command `npm run test` to display the behavior of each setup.