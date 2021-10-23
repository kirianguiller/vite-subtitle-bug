### Describe the bug

### Explanation of the error
When using vite with a react project including the [library subtitle](https://www.npmjs.com/package/subtitle), we have the two following errors : 
```
No matching export in "browser-external:stream" for import "Duplex"
```
and 
```
No matching export in "browser-external:stream" for import "Transform"
```
(Full error below)
The error is from the builtin module **stream** that , for a reason I ignore, is replaced by browser-external:stream.

The problem is similar to this one : https://github.com/aws-amplify/amplify-ui/issues/268 
As well as maybe this one : https://github.com/vitejs/vite/issues/1979

### Error Message
```
error when starting dev server:
Error: Build failed with 2 errors:
node_modules/subtitle/dist/subtitle.esm.js:1:9: error: No matching export in "browser-external:stream" for import "Duplex"
node_modules/subtitle/dist/subtitle.esm.js:1:17: error: No matching export in "browser-external:stream" for import "Transform"
    at failureErrorWithLog (/home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:1493:15)
    at /home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:1151:28
    at runOnEndCallbacks (/home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:941:63)
    at buildResponseToResult (/home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:1149:7)
    at /home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:1258:14
    at /home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:629:9
    at handleIncomingPacket (/home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:726:9)
    at Socket.readFromStdout (/home/wenjia/Projects/to_delete/my-vue-app/node_modules/esbuild/lib/main.js:596:7)
    at Socket.emit (events.js:400:28)
    at addChunk (internal/streams/readable.js:293:12)
```

### Reproduction

### Method 1 : Cloning from my example repo
```
git clone https://github.com/kirianguiller/vite-subtitle-bug
cd vite-subtitle-bug
npx vite
```



### Method 2 : Install from scratch
```
npm init vite@latest my-react-app --template react-ts
cd my-react-app
npm install
npm install subtitle
```
Add the following line after the imports in App.tsx : 
```tsx
import { parseSync } from 'subtitle'
parseSync("a dummy string")
```
and then, run vite : 
```
npx vite
```



### System Info

```shell
System:
    OS: Linux 5.8 Ubuntu 20.10 (Groovy Gorilla)
    CPU: (12) x64 AMD Ryzen 5 PRO 4650U with Radeon Graphics
    Memory: 4.28 GB / 14.93 GB
    Container: Yes
    Shell: 5.0.17 - /bin/bash
Binaries:
    Node: 14.18.0 - ~/.nvm/versions/node/v14.18.0/bin/node
    npm: 6.14.15 - ~/.nvm/versions/node/v14.18.0/bin/npm
Browsers:
    Chrome: 87.0.4280.141
    Firefox: 90.0
npmPackages:
    @vitejs/plugin-react: ^1.0.0 => 1.0.5 
    vite: ^2.6.4 => 2.6.10 
```
```


### Used Package Manager

npm

### Logs

```shell
vite:config bundled config file loaded in 157.27ms +0ms
  vite:config using resolved config: {
  vite:config   plugins: [
  vite:config     'vite:pre-alias',
  vite:config     'alias',
  vite:config     'vite:react-babel',
  vite:config     'vite:react-refresh',
  vite:config     'vite:react-jsx',
  vite:config     'vite:modulepreload-polyfill',
  vite:config     'vite:resolve',
  vite:config     'vite:html-inline-script-proxy',
  vite:config     'vite:css',
  vite:config     'vite:esbuild',
  vite:config     'vite:json',
  vite:config     'vite:wasm',
  vite:config     'vite:worker',
  vite:config     'vite:asset',
  vite:config     'vite:define',
  vite:config     'vite:css-post',
  vite:config     'vite:client-inject',
  vite:config     'vite:import-analysis'
  vite:config   ],
  vite:config   server: { fs: { strict: undefined, allow: [Array] } },
  vite:config   resolve: { dedupe: [ 'react', 'react-dom' ], alias: [ [Object], [Object] ] },
  vite:config   optimizeDeps: {
  vite:config     include: [ 'react/jsx-dev-runtime' ],
  vite:config     esbuildOptions: { keepNames: undefined, preserveSymlinks: undefined }
  vite:config   },
  vite:config   configFile: '/home/wenjia/Projects/to_delete/my-react-app/vite.config.ts',
  vite:config   configFileDependencies: [ 'vite.config.ts' ],
  vite:config   inlineConfig: {
  vite:config     root: undefined,
  vite:config     base: undefined,
  vite:config     mode: undefined,
  vite:config     configFile: undefined,
  vite:config     logLevel: undefined,
  vite:config     clearScreen: undefined,
  vite:config     server: { fs: [Object] }
  vite:config   },
  vite:config   root: '/home/wenjia/Projects/to_delete/my-react-app',
  vite:config   base: '/',
  vite:config   publicDir: '/home/wenjia/Projects/to_delete/my-react-app/public',
  vite:config   cacheDir: '/home/wenjia/Projects/to_delete/my-react-app/node_modules/.vite',
  vite:config   command: 'serve',
  vite:config   mode: 'development',
  vite:config   isProduction: false,
  vite:config   build: {
  vite:config     target: [ 'es2019', 'edge88', 'firefox78', 'chrome87', 'safari13.1' ],
  vite:config     polyfillModulePreload: true,
  vite:config     outDir: 'dist',
  vite:config     assetsDir: 'assets',
  vite:config     assetsInlineLimit: 4096,
  vite:config     cssCodeSplit: true,
  vite:config     cssTarget: [ 'es2019', 'edge88', 'firefox78', 'chrome87', 'safari13.1' ],
  vite:config     sourcemap: false,
  vite:config     rollupOptions: {},
  vite:config     minify: 'esbuild',
  vite:config     terserOptions: {},
  vite:config     write: true,
  vite:config     emptyOutDir: null,
  vite:config     manifest: false,
  vite:config     lib: false,
  vite:config     ssr: false,
  vite:config     ssrManifest: false,
  vite:config     reportCompressedSize: true,
  vite:config     chunkSizeWarningLimit: 500,
  vite:config     watch: null,
  vite:config     commonjsOptions: { include: [Array], extensions: [Array] },
  vite:config     dynamicImportVarsOptions: { warnOnError: true, exclude: [Array] }
  vite:config   },
  vite:config   env: { BASE_URL: '/', MODE: 'development', DEV: true, PROD: false },
  vite:config   assetsInclude: [Function: assetsInclude],
  vite:config   logger: {
  vite:config     hasWarned: false,
  vite:config     info: [Function: info],
  vite:config     warn: [Function: warn],
  vite:config     warnOnce: [Function: warnOnce],
  vite:config     error: [Function: error],
  vite:config     clearScreen: [Function: clearScreen],
  vite:config     hasErrorLogged: [Function: hasErrorLogged]
  vite:config   },
  vite:config   createResolver: [Function: createResolver]
  vite:config } +8ms
  vite:deps Crawling dependencies using entries:
  vite:deps   /home/wenjia/Projects/to_delete/my-react-app/index.html +0ms
  vite:resolve 0.87ms /src/main.tsx -> /home/wenjia/Projects/to_delete/my-react-app/src/main.tsx +0ms
  vite:resolve 3.85ms react -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/react/index.js +11ms
  vite:resolve 1.59ms react-dom -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/react-dom/index.js +4ms
  vite:resolve 0.78ms ./App -> /home/wenjia/Projects/to_delete/my-react-app/src/App.tsx +4ms
  vite:resolve 1.61ms subtitle -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/subtitle/dist/subtitle.esm.js +6ms
  vite:deps Scan completed in 77.13ms: {
  react: '/home/wenjia/Projects/to_delete/my-react-app/node_modules/react/index.js',
  'react-dom': '/home/wenjia/Projects/to_delete/my-react-app/node_modules/react-dom/index.js',
  subtitle: '/home/wenjia/Projects/to_delete/my-react-app/node_modules/subtitle/dist/subtitle.esm.js'
} +47ms
  vite:resolve 1.21ms react/jsx-dev-runtime -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/react/jsx-dev-runtime.js +0ms
Pre-bundling dependencies:
  react
  react-dom
  subtitle
  react/jsx-dev-runtime
(this will be run only when your dependencies or config have changed)
  vite:resolve 1.02ms stream -> __vite-browser-external:stream +0ms
  vite:resolve 1.34ms multipipe -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/multipipe/index.js +3ms
  vite:resolve 1.48ms split2 -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/split2/index.js +2ms
  vite:resolve 0.23ms react -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/react/index.js +0ms
  vite:resolve 1.31ms strip-bom -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/strip-bom/index.js +4ms
  vite:resolve 1.52ms object-assign -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/object-assign/index.js +5ms
  vite:resolve 1.75ms readable-stream -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/split2/node_modules/readable-stream/readable-browser.js +3ms
  vite:resolve 1.20ms duplexer2 -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/duplexer2/index.js +1ms
  vite:resolve 1.18ms string_decoder -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/string_decoder/lib/string_decoder.js +2ms
  vite:resolve 0.84ms stream -> __vite-browser-external:stream +2ms
  vite:resolve 1.32ms safe-buffer -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/safe-buffer/index.js +2ms
  vite:resolve 2.08ms inherits -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/inherits/inherits_browser.js +3ms
  vite:resolve 2.55ms readable-stream -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/readable-stream/readable-browser.js +4ms
  vite:resolve 2.69ms buffer -> __vite-browser-external:buffer +0ms
  vite:resolve 1.87ms util-deprecate -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/util-deprecate/browser.js +3ms
  vite:resolve 1.32ms events -> __vite-browser-external:events +2ms
  vite:resolve 2.10ms process-nextick-args -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/process-nextick-args/index.js +3ms
  vite:resolve 2.12ms core-util-is -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/core-util-is/lib/util.js +4ms
  vite:resolve 3.57ms isarray -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/isarray/index.js +4ms
  vite:resolve 3.51ms util -> __vite-browser-external:util +1ms
  vite:resolve 1.73ms string_decoder/ -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/string_decoder/lib/string_decoder.js +9ms
  vite:resolve 1.53ms scheduler -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/scheduler/index.js +33ms
  vite:resolve 1.01ms scheduler/tracing -> /home/wenjia/Projects/to_delete/my-react-app/node_modules/scheduler/tracing.js +3ms
 > node_modules/subtitle/dist/subtitle.esm.js:1:9: error: No matching export in "browser-external:stream" for import "Duplex"
    1 │ ... Duplex,...
      ╵     ~~~~~~

 > node_modules/subtitle/dist/subtitle.esm.js:1:17: error: No matching export in "browser-external:stream" for import "Transform"
    1 │ ...Transfor...
      ╵    ~~~~~~~~

error when starting dev server:
Error: Build failed with 2 errors:
node_modules/subtitle/dist/subtitle.esm.js:1:9: error: No matching export in "browser-external:stream" for import "Duplex"
node_modules/subtitle/dist/subtitle.esm.js:1:17: error: No matching export in "browser-external:stream" for import "Transform"
    at failureErrorWithLog (/home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:1493:15)
    at /home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:1151:28
    at runOnEndCallbacks (/home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:941:63)
    at buildResponseToResult (/home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:1149:7)
    at /home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:1258:14
    at /home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:629:9
    at handleIncomingPacket (/home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:726:9)
    at Socket.readFromStdout (/home/wenjia/Projects/to_delete/my-react-app/node_modules/esbuild/lib/main.js:596:7)
    at Socket.emit (events.js:400:28)
    at addChunk (internal/streams/readable.js:293:12)
```


### Validations

- [X] Follow our [Code of Conduct](https://github.com/vitejs/vite/blob/main/CODE_OF_CONDUCT.md)
- [X] Read the [Contributing Guidelines](https://github.com/vitejs/vite/blob/main/CONTRIBUTING.md).
- [X] Read the [docs](https://vitejs.dev/guide).
- [X] Check that there isn't [already an issue](https://github.com/vitejs/vite/issues) that reports the same bug to avoid creating a duplicate.
- [X] Make sure this is a Vite issue and not a framework-specific issue. For example, if it's a Vue SFC related bug, it should likely be reported to https://github.com/vuejs/vue-next instead.
- [X] Check that this is a concrete bug. For Q&A open a [GitHub Discussion](https://github.com/vitejs/vite/discussions) or join our [Discord Chat Server](https://chat.vitejs.dev/).
- [X] The provided reproduction is a [minimal reproducible example](https://stackoverflow.com/help/minimal-reproducible-example) of the bug.
