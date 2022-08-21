# Nuxt 3: Server routes are not automatically detected after running `nuxt dev` (repro)

This repo reproduces the issue described [here](https://github.com/nuxt/framework/issues/6799).

## Steps to Reproduce

1. Run the following commands:

```sh
npm install
npm run dev -- --open
```

Make sure Nitro is built before going to the next step.

2. In the browser, click on "Go to /api/hello".

3. Notice the root page will be loaded, because `server/api/hello.ts` is not created yet. Go back to the home page.

4. Copy the contents of `testfiles` directory to the root of the project. This will create the `server/api/hello.ts`.

```sh
cp -r testfiles/server .
```

5. In the browser, click on "Go to /api/hello" again. Notice the server route still won't load. This is despite `server/api/hello.ts` having been created already.

You can now try to restart the development server manually (`Ctrl-C`), and only then will `/api/hello` actually load the server route correctly.

This is tested on both Linux 64-bit and Windows 64-bit. Node and npm versions used to reproduce are shown below.

Windows 64-bit:

```
node -v
v18.7.0

npm -v
8.15.0
```

Linux 64-bit:

```
node -v
v18.7.0

npm -v
8.18.0
```
