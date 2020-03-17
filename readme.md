## Webpack config

### babel css sass

**package.json**
```javascript
  "scripts": {
    "pack": "webpack index.js --watch"
  },
  "devDependencies": {
    "babel-loader": "^8.0.6",
    "babel-preset-es2015": "^6.24.1",
    "css-loader": "^3.4.2",
    "style-loader": "^1.1.3",
    "sass-loader": "^8.0.2"
  }
```

**webpack.config.js**
```javascript
const path = require("path");

module.exports = {
  //define entry point
  entry: "./index.js",
  // mode: "development",
  mode: "production",

  //define output point
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js"
  },

  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /(node_modules)/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-env"]
          }
        }
      },
      {
        test: /\.scss$/,
        use: "style-loader!css-loader!sass-loader"
      }
    ] //rules
  } //module
};

```
