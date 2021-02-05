# Spotify Api Project

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 11.1.0.

## Requirements

To have installed:

- Angular Cli 
- Tailwind Css
- Firebase
- Git

## Steps to run the server

## Step 1
Create new project on angular cli

```
$ ng new nameProject
```

## Step 2

TailwindCss installation in the application, on the console type...

```
$ npm i -D tailwindcss postcss-scss postcss-import postcss-loader@~3.0.0 @angular-builders/custom-webpack
```

Checking that `package.json` remains with the versions, for example:

```
"@angular-builders/custom-webpack": "^10.0.1",
"postcss-import": "^12.0.1",
"postcss-loader": "~3.0.0",
"postcss-scss": "^3.0.2",
"tailwindcss": "^1.8.10",
```
## Step 3

TailwindCss configuration:

```
$ npx tailwind init
```

Add Tailwind to the peoject's scss in the `styles.scss` file:

```
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

## Step 4

Webpack configuration. Create `webpack.config.js` file:

```
$ touch webpack.config.js
```

And we put the following content.

```
module.exports = {
  module: {
    rules: [
      {
        test: /\.scss$/,
        loader: "postcss-loader",
        options: {
          ident: "postcss",
          syntax: "postcss-scss",
          plugins: () => [
            require("postcss-import"),
            require("tailwindcss"),
            require("autoprefixer"),
          ],
        },
      },
    ],
  },
};
```

## Step 5

Update the `angular.json` file to use the webpack file that we created in `build` and `serve`, replace the builder with `@angular-builders/custom-webpack:browser` and in options we add

```
"customWebpackConfig": {
  "path": "./webpack.config.js"
}
```

Then it would be something like this

```
{
    ...
    "projects": {
      ...
        "architect": {
          "build": {
            "builder": "@angular-builders/custom-webpack:browser",
            "options": {
              "customWebpackConfig": {
                "path": "./webpack.config.js"
              },
              ...
            },
            ...
          },
          "serve": {
            "builder": "@angular-builders/custom-webpack:dev-server",
            "options": {
              "customWebpackConfig": {
                "path": "./webpack.config.js"
              },
              ...
            },
            ...
          },
          ...
        }
      }
    },
  }
```

## Step 6

To install dependencies in the application, on the console type...

```
$ npm install
```

## Step 7

To run de server type, navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

```
$ ng serve
```

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).
