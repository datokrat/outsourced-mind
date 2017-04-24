# Setting up a project with TypeScript and Webpack

*Main source: [webpack.js.org](https://webpack.js.org/guides/webpack-and-typescript/)*

You will need a TypeScript project with `index.ts` as root and some HTML files, for example `index.html`.

## Dependencies

    $ npm init -y
    $ npm install --save-dev typescript ts-loader webpack

## Configuration

### package.json

```json
{
    "//": "...",
    "scripts": {
        "start": "webpack --config webpack.conf.js"
    }
}
```

### tsconfig.json

```json
{
    "compilerOptions": {
        "outDir": "./dist/",
        "sourceMap": true,
        "noImplicitAny": true,
        "module": "commonjs",
        "target": "es5"
    }
}
```

### webpack.conf.js

```js
module.exports = {
    entry: "./index.ts",
    output: {
        filename: "bundle.js",
        path: __dirname
    },
    module: {
        rules: [{
            test: /\.ts$/,
            loader: "ts-loader",
            exclude: /node_modules/
        }]
    },
    resolve: {
        extensions: ["ts"]
    }
};
```
