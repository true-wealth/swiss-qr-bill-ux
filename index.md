---
layout: default
---

The Swiss QR Bill standard provides a basis for efficient processing of bills printed on paper in e-banking applications. In case the bill is delivered in digital form such as email or downloaded from a website, there are still many e-banking applications that do not support the customer with an optimal flow importing it without using a second screen to display and scan the QR code.

The goal of this project is to improve this situation with the following:
* Code examples below support developers to provide a seamless integration of QR Bills into their website or application.
* A demo allows testing this feature with e-banking applications.
* A compatibility table provides information of the support for existing e-banking applications.

# Code Examples
The following code example uses web standards. You can implement it in any other framework that can trigger the system share functionality.

Please note that the example code is not polished for production (for example, it lacks error handling and checking support of share API).

```html
<button>Share QR Bill</button>
```

```js
const button = document.querySelector('button');

// Share must be triggered by "user activation"
button.addEventListener('click', async () => {
  try {
    const response = await fetch('qr-bill.pdf');
    const blob = await response.blob();
    const filesArray = [
      new File(
        [blob],
        'qr-bill.pdf',
        {
          type: 'application/pdf'
        }
      )
    ];
    const shareData = {
      files: filesArray,
    };
    await navigator.share(shareData);
  } catch (err) {
    // Caused for example when the client cancels share dialog 
  }
});
```

# Demo
The following demo can be used on any device. In case the e-banking app appears as a selectable app, it is very likely that the app supports the import of digital QR Bills.

## Image

TODO

## PDF

TODO

# Compatibility table
The following table provides information about the support of existing e-banking applications. This table is not complete and support may have changed in the meantime. Please create a pull request (or alternatively open an issue) in case you notice outdated or missing information.

| Application Name     | Image | PDF |
|:---------------------|:------|:----|
| Bank Cler Zak        | ❌     | ❌   |
| Credit Suisse – CSX  | ✅     | ✅   |
| YAPEAL               | ❌     | ❌   |
| Yuh                  | ❌     | ❌   |
| neon                 | ❌     | ❌   |
| PostFinance App      | ✅     | ✅   |
| Raiffeisen E-Banking | ❌     | ❌   |
| UBS & UBS key4       | ❌     | ❌   |
| ZKB Mobile Banking   | ❌     | ❌   |
