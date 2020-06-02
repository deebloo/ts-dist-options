# TS distribution issues

This repo is to demonstrate the potential issues when distributing typescript source code vs compiled js code with d.ts files.

## Install Typescript

```BASH
npm i -g typescript@3.9.3
```

## Build Module 1

Module 1 is built WITHOUT strict compiler options.

```BASH
tsc -p module-1/tsconfig.json
```

## Build Module 2 (Works)

Module 2 is built WITH strict compiler options.

Module 2 depends on Module 1 and uses the js file + d.ts.

This works because the compiler doesn't type check the JS file, just the d.ts file

```BASH
tsc -p module-2/tsconfig.json
```

## Build Module 3 (Fails)

Module 3 is built WITH strict compiler options.

Module 3 depends on Module 1 and uses the source Typescript code

This fails because the compiler needs to compile the source code of Lib 1 which was written with less strict options in mind.

```BASH
tsc -p module-3/tsconfig.json
```
