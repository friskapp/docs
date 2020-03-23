# Javascript Integration

To catch and send errors from your Javascript code, install the MIT-licensed package `@flareapp/flare-client` in your project:

    npm install @flareapp/flare-client

or if you prefer yarn

    yarn add @flareapp/flare-client


then 

    import { flare } from "@flareapp/flare-client";

    // only run in production
    if (process.env.NODE_ENV === 'production') {
        flare.config.reportingUrl = 'https://firsk-app-url.com/api/reports';
        flare.light('frisk-project-key');
    }

> {note} You can get frisk-project-key from Frisk's project settings/API page.


## [Usage Notes](#usage-notes)
- To test the integration from your browser console, run: `flare.test()`
- You can use `flare.beforeEvaluate(error)` or `flare.beforeEvaluate(error)` to stop or edit errors before sending. 
- If can manually send errors using `flare.report(error)` like in try..catch blocks.
- Sending errors might not be sent during development.
- It's important to use [`sourcemaps`](https://www.npmjs.com/package/@flareapp/flare-webpack-plugin-sourcemap) if you bundle your code using webpack or gulp.
- To support IE11, use a polyfill for Promise library.
- To use with react use package `@flareapp/flare-react` and for vue use package `@flareapp/flare-vue`