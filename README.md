# TypeScript Training w/ Mike North

This repo contains the code for `TypeScript Fundamentals v3` and `Intermediate TypeScript v1`

The course website is at https://www.typescript-training.com

[![Website](https://github.com/mike-north/ts-fundamentals-v3/actions/workflows/ci-website.yml/badge.svg)](https://github.com/mike-north/ts-fundamentals-v3/actions/workflows/ci-website.yml)

### Operating System

This workshop project works best in a [POSIX-compliant][posix] dev environment
like Linux, macOS, or Windows 10 (with [Windows Subsystem for Linux][wsl2]).

### JavaScript Tool chain

- We'll be using `yarn` as our package manager, not `npm`
- Please install [Volta][volta], to ensure you run this project with the correct `node` and `yarn` versions

### Browser

We recommend using a Chromium-based browser like [Microsoft Edge][msedge], [Brave][brave], [Opera][opera] or [Chrome][googlechrome].

### Editor

Although TypeScript can theoretically work well in any authoring environment that
supports the [Language Server Protocol][lsp], [Visual Studio Code][vscode] is
the _officially_ supported editor for this course.

### Checking out the code & preparing to run

- If you don't yet have a [GitHub](https://github.com) account, [create a new one](https://docs.github.com/en/github/getting-started-with-github/signing-up-for-github/signing-up-for-a-new-github-account) and [set up your SSH keys](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

  - If you've done this correctly, you should be able to run `ssh git@github.com` in your terminal, and see something like `Hi mike-north! You've successfully authenticated, but GitHub does not provide shell access.`

- Clone this repo by running `git clone git@github.com:mike-north/ts-fundamentals-v3`
- Enter the repo by running `cd ts-fundamentals-v3`
- Install dependencies by running `yarn` ([volta][volta] may download the right version(s) automatically)

### Running the project(s)

Projects are found within the [packages](https://github.com/mike-north/ts-fundamentals-v3/tree/main/packages) folder, each can be started using the command
`yarn dev-<project name>`.

For example

- `yarn dev-website` starts the website project

[posix]: https://en.wikipedia.org/wiki/POSIX
[wsl2]: https://docs.microsoft.com/en-us/windows/wsl/
[cygwin]: (https://www.cygwin.com/)
[volta]: (https://volta.sh/)
[lsp]: (https://microsoft.github.io/language-server-protocol/)
[vscode]: (http://code.visualstudio.com/)
[brave]: (https://brave.com/)
[msedge]: (https://www.microsoft.com/en-us/edge)
[opera]: (https://www.opera.com/)
[googlechrome]: (https://www.google.com/chrome/)

# Legal

&copy; 2021, All Rights Reserved - Mike Works, Inc.

# Course Notes

# TypeScript Fundamentals, v3

## Compiling a TypeScript Program

- TSC compiler komutlarının kullanımı :
- Uzantısı `d.ts` olan dosyalara "declaration file" denir.

package.json # Package manifest
ts.config.json # TypeScript compiler settings
src/index.ts # "the program"

```typescript
{
  "compilerOptions": {
    "outDir": "dist", // where to put the TS files
    "target": "ES3" // which level of JS support to target
    "module":"CommonJS"
  },
  "include": ["src"] // which files to compile
}
```

TS Dosyaları

- `.ts` : hem tür bilgisi hem de çalışan kod içerir
- `.js` : çalışan kodu içerir.
- `.d.ts` : sadece type bilgisi içerir.

## Variables and Values

In TypeScript, variables are "born" with their types.

```typescript
// between 500 and 1000

const RANDOM_WAIT_TIME =
  Math.round(Math.random() * 500) + 500;

let startTime = new Date();
let endTime;

let endTime: any;

setTimeout(() => {
  endTime = 0;
  endTime = new Date();
}, RANDOM_WAIT_TIME);
```

- `endTime` is "born" without a type, so it ends up being implict `any`

- TypeScript does'nt have enough information around the declaration site to infer what `endTime` should be, so it gets the most flexible type : any

- Think of `any` as "the normal way JS variables work" in that you could assign `endTime` to `number`, then later a `function`, then a `string`.

Function arguments and return values

```typescript
function add(a: number, b: number) {
  return a + b;
}
const result = add(3, 4);
```

## Typing Functions
