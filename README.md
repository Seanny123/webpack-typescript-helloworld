# Getting started with client-side TypeScript

If you know JavaScript, but you want to start with TypeScript in a sane development environment, there are quite a few challenges in your way. This repository/tutorial gives you the basics to start using:

- `yarn` to manage your packages
- `npm run` to do different tasks
- `webpack` to build and serve your development
- `ts-loader` to automatically reload the files you edit
- `typings` to get type information for JavaScript packages (in this case `D3.js`)

# Installation proceedure

1. `yarn` 

# Running a development web-server

1. `npm run debug`

# What are all these files?

- `package.json` contains information for `npm`
- `tsconfig.json` configures the TypeScript compiler `tsc`
- `webpack.config.js` configures WebPack somehow? (Work In Progress)
- `webpack.debug.js` configures WebPack somehow? (Work In Progress)

Because you can't comment JSON files, I've reproduced the JSON files here with comments.

## `package.json`


    {
        // a bunch of personal information that you can omit
        "name": "hello",
        "version": "0.0.1",
        "description": "Hello TypeScript!",
        "author": "Your Name",
        "license": "Free for non-commercial use",
        "main": "dist/hello.js",
        "repository": {
            "type": "git",
            "url": "http://example.com"
        },
        "bugs": {
            "url": "http://example.com/issues"
        },
        "private": true,
        // these are the things that are triggered by `npm run`
        "scripts": {
            "build": "webpack --debug --devtool source-map --output-pathinfo",
            "debug": "webpack-dev-server --config webpack.debug.js --inline",
            "release": "webpack --optimize-minimize --optimize-occurence-order",
            "test": "webpack --config webpack.test.js",
            // install the type information for JavaScript module dependencies
            "postinstall": "typings install"
        },
        // dependencies of this app, including the pure JavaScript ones
        "dependencies": {
            "@types/d3": "^4.0.0",
            "d3": "^4.0.0",
            "html-webpack-plugin": "^2.28.0",
            "ts-loader": "^2.0.3",
            "tslint": "^4.5.1",
            "tslint-eslint-rules": "^3.4.0",
            "tslint-microsoft-contrib": "^4.0.0",
            "typescript": "^2.3",
            "typings": "^2.1.0",
            "webpack": "^2.2.1",
            "webpack-dev-server": "^2.4.2"
        }
    }

## `tsconfig.json`

    {
        // arguments to pass `tsc`
        "compilerOptions": {
            "target": "es6",
            "sourceMap": true,
            "watch": true
        },
        // don't bother trying to compile the libraries
        "exclude": [
            "node_modules"
        ]
    }
