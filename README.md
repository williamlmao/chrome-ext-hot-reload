# React Start Kit for Chrome extension with Live Reloading.

I found this boiler plate code from [this tutoria] (https://smellycode.com/chrome-extension-live-reloading-with-react/). It works perfectly for reloading, but I need to be able to inject the React components.

# Issues

`yarn build` does not work when I include React components inside of `content-script/content-script.js`, which is necessary for me to inject a React app into a page.

I have tried using the following code within `content-script/content-script.js` and get a syntax error that highlights the HTML after the return statement. This leads me to believe React is not able to be loaded from this javascript file.

```
/* src/content.js */
import React from "react";
import ReactDOM from "react-dom";
import "./content.css";
import { test } from "./scripttest";

class Main extends React.Component {
  render() {
    return (
      <div className={"my-extension"}>
        <h1>Hello world - My first Extension {test} TESTING MORE</h1>
      </div>
    );
  }
}

const app = document.createElement("div");
app.id = "my-extension-root";
document.body.appendChild(app);
ReactDOM.render(<Main />, app);
```

How can I get React components from my `src` folder into this content-script folder?

## To reproduce my error:

Copy the above code snippet into: `content-script/content-script.js` and follow below instructions

## To install and enable hot reloading, run:

- `npm run watch
- `npm run build`
- Go to chrome://extensions/ and load the build folder as unpacked
