# 🖼  Visual Diff Tool
A Node-based auditing tool to visually diff pages

<img src="example.png" alt="An example of the visual diff tool in action">

## 🤔 What is it?

Have you ever made a change that negatively impacted the front-end? Checking one page for a change might be easy. Checking hundreds is difficult and time-consuming.

The **Visual Diff Tool** allows you to supply an array of URLs to audit and, if a non-trivial difference is detected (defined in your config file), an `audit.csv` is provided for your review to ensure all differences have been properly accounted for.

Additionally, you can review the screenshots that were taken and see a "heatmap" of the visual differences thanks to [the pixelmatch library](https://github.com/mapbox/pixelmatch).

## ✅ Usage
1. Download the project
2. Install dependencies `npm i`
3. Copy `config.example.js` to `config.js`
4. Modify your `config.js` values and supply your array of URLs to test
5. Run `node index.js` to create screenshots, diffs and generate an audit.csv file of what's different

## ⚙️ Configuring your Test

You can easily modify the parameters of your test in the `config.js` file (after copying `config.example.js` to `config.js`). Below are all of the options you can modify.

```js
module.exports = {
  // The viewport to use when creating images from the URLs
  viewport: {
    width: 1500,
    height: 1500,
  },

  // Matching threshold, ranges from 0 to 1. Smaller values make the comparison more sensitive. 0.1 by default.
  // See pixelmatch for more information: https://github.com/mapbox/pixelmatch#api
  diffThreshold: 0.1,

  // The number of pixels in the diff that, once reached, will be flagged in the audit during the testing
  nonacceptableDiff: 10,

  // The URLs to test for visual differences
  urls: [
    {
      a: "https://google.com",
      b: "https://yahoo.com",
      css: ``,
    },
  ],
};
```
