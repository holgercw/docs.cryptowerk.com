---
title: "Seal Formats"
metaTitle: "Seal Formats - Cryptowerk Tutorials"
metaDescription: "Seal Formats - Cryptowerk Tutorials"
---

## Experimental Options For Visualizing Seals

The following examples are experimental and are subject to change.

### Seal as HTML Page

Traditionally a Seal is returned via the `/getSeal` method as a JSON object. If you would like to poll for a Seal and have HTML content returned use the following:
```
POST {{baseUrlHorizon}}/platform/API/v8/getseal HTTP/1.1
x-api-key: {{testHorizon}}
content-type: application/json
accept: application/json

{ "retrievalId" : "ri3165452642d684ef62eeb91eadbf37f926412bf6226a7fc3d7699b4a3589c1762",
"sealWrapper" :"certificateHTML", 
"extract":"documents[0].certificateHTML"
}
```
### Seal as PDF

If you would like to poll for a Seal and have PDF content returned use the following:
```
POST {{baseUrlHorizon}}/platform/API/v8/getseal HTTP/1.1
x-api-key: {{testHorizon}}
content-type: application/json
accept: application/json

{ "retrievalId" : "ri3165452642d684ef62eeb91eadbf37f926412bf6226a7fc3d7699b4a3589c1762",
"sealWrapper" :"certificatePDF", 
"extract":"documents[0].certificatePDF",
"extractAs":"application/pdf;decodeFrom=base64",
"extractDisposition":"inline;filename=certificate.pdf"
}
```
Here is an example of such a PDF Seal 
[here](https://developers.cryptowerk.com/platform/API/v8/getseal?retrievalIds=ri31654973711edf92c37bfbdf4f803d9daf1dd9d2a8eca1ee17433241dd9327636&sealWrapper=certificatePDF&extract=documents%5B0%5D.certificatePDF&extractAs=application%2Fpdf%3BdecodeFrom%3Dbase64&extractDisposition=inline%3Bfilename%3Dcertificate.pdf)

### Seal as QR Code

If you would like to poll for a Seal and have a QR Code returned use the following:
```
POST {{baseUrlHorizon}}/platform/API/v8/getseal HTTP/1.1
x-api-key: {{testHorizon}}
content-type: application/json
accept: application/json

{ "retrievalId" : "ri315539637d780a5f2d7f7333b7ad916c7fae79ac20c34c8d37a1ed5a0e9f3f736",
"sealWrapper" :"QRWithSeal", 
"extract":"documents[0].QRWithSeal.image",
// or to recieve URL to a QR Code us this extract parameter instead instead of the one above
// "extract":"documents[0].QRWithSeal.contents"
}
```

### NOTE
These calls may be POST or GET. 

Take note that (when you `/register`) the retrievalID must be publiclyRetrievable=true in order for the Seal to be accessible without an API key. Otherwise, like the above examples show you will need to pass your api-key and credentials in the header.

PDF Themes are available. Contact us to inquire about customizing the PDF Seal to include your branding.