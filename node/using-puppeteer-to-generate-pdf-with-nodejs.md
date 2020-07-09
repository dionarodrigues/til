# 👌 Using Puppeteer to generate PDFs with Node.js

__[Puppeteer](https://github.com/puppeteer/puppeteer) is a Node library which provides a high-level API to control Chrome or Chromium over the DevTools Protocol. Puppeteer runs headless by default, but can be configured to run full (non-headless) Chrome or Chromium.__

Maintained by Chrome DevTools team, It’s basically a browser which we can run from Node.js and that can be used to generate screenshots and PDFs of pages. And like its documentation says: most things that we can do manually in the browser can be done using Puppeteer!

Let's take a look at how this amazing library is implemented.

---

## Creating a PDF from a existing website

```
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('https://diogorodrigues.dev', {waitUntil: 'networkidle2'});
  await page.pdf({path: 'diogo.pdf', format: 'A4'});

  await browser.close();
})();
```

-- 

## Creating a PDF from a customized web page

It´s important to note that we can create a web page before generating the PDF instead of using an existing website.

```
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  const content = '<html>...</html>'; // set a HTML content here

  await page.setContent(content);
  await page.emulateMediaType('screen');
  await page.pdf({path: 'customized.pdf', format: 'A4'});

  await browser.close();
})();
```

-- 

I created this [application using Puppeteer and other excellent technologies to generate PDFs for business proposals](https://github.com/diogorodrigues/pdf-generator-nodejs-puppeteer). 👌😎
