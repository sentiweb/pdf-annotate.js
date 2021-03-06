# hmcts/pdf-annotate.js (forked from instructure/pdf-annotate.js)

[![build status](https://api.travis-ci.com/hmcts/pdf-annotate.js.svg?branch=master)](https://travis-ci.com/hmcts/pdf-annotate.js)
[![Coverage Status](https://coveralls.io/repos/github/hmcts/pdf-annotate.js/badge.svg)](https://coveralls.io/github/hmcts/pdf-annotate.js)

A fork of [pdf-annotate.js](https://github.com/instructure/pdf-annotate.js) to fix issues with rotations

## Objectives

- Provide a low level annotation layer for [pdf.js](https://github.com/mozilla/pdf.js).
- Optional high level UI for managing annotations.
- Agnostic of backend, just supply your own `StoreAdapter` to fetch/store data.
- Prescribe annotation format.

## Example

```js
import __pdfjs from 'pdfjs-dist/build/pdf';
import PDFJSAnnotate from 'pdfjs-annotate';
import MyStoreAdapter from './myStoreAdapter';

const { UI } = PDFJSAnnotate;
const VIEWER = document.getElementById('viewer');
const RENDER_OPTIONS = {
  documentId: 'MyPDF.pdf',
  pdfDocument: null,
  scale: 1,
  rotate: 0
};

PDFJS.workerSrc = 'pdf.worker.js';
PDFJSAnnotate.setStoreAdapter(MyStoreAdapter);

PDFJS.getDocument(RENDER_OPTIONS.documentId).then((pdf) => {
  RENDER_OPTIONS.pdfDocument = pdf;
  VIEWER.appendChild(UI.createPage(1));
  UI.renderPage(1, RENDER_OPTIONS);
});
```

See more [examples](https://github.com/instructure/pdf-annotate.js/blob/master/web/index.js).

## Documentation

[View the docs](https://github.com/instructure/pdf-annotate.js/tree/master/docs).

## Developing

```bash
# clone the repo
$ git clone https://github.com/hmcts/pdf-annotate.js.git
$ cd pdf-annotate.js

# intall dependencies
$ npm install

# start example server
$ npm start
$ open http://127.0.0.1:8080

# run tests
$ npm test
```
## License

MIT
