# Modified Whatsapp-API
<p align='center'>
  <img src="https://files.catbox.moe/kf36r0.jpg" width="600">
  <img src="https://files.catbox.moe/a8sbol.jpg" width="600">
</p>

--- 

## Usage
```json
"depencies": {
  "@whiskeysockets/baileys": "github:raldzfvck/baileys"
}
```
## Import
```javascript
const {
  default:makeWASocket,
  // Other Options 
} = require('@whiskeysockets/baileys');
```

---
# How To Connect To Whatsapp
## With QR Code
```javascript
const {
  default: makeWASocket
} = require('@whiskeysockets/baileys');

const client = makeWASocket({
  browser: ['Ubuntu', 'Chrome', '20.00.1'],
  printQRInTerminal: true
})
```

## Connect With Number
```javascript
const {
  default: makeWASocket,
  fetchLatestWAWebVersion
} = require('@whiskeysockets/baileys');

const client = makeWASocket({
  browser: ['Ubuntu', 'Chrome', '20.00.1'],
  printQRInTerminal: false,
  version: fetchLatestWAWebVersion()
  // Other options
});

const number = "628XXXXX";
const code = await client.requestPairingCode(number.trim) /* Use : (number, "YYYYYYYY") for custom-pairing */

console.log("Ur pairing code : " + code)
```

# Sending messages

## send orderMessage
```javascript
const fs = require('fs');
const R4IMG = fs.readFileSync('./R4IMG');

await client.sendMessage(m.chat, {
  thumbnail: R4IMG,
  message: "Gotta get a grip",
  orderTitle: "R4-XYZ",
  totalAmount1000: 72502,
  totalCurrencyCode: "IDR"
}, { quoted:m })
```

## send pollResultSnapshotMessage
```javascript
await client.sendMessage(m.chat, {
  pollResultMessage: {
    name: "R4-XYZ",
    options: [
      {
        optionName: "poll 1"
      },
      {
        optionName: "poll 2"
      }
    ],
    newsletter: {
      newsletterName: "RaldzzXyz | Newsletter",
      newsletterJid: "1@newsletter"
    }
  }
})
```

## send productMessage
```javascript
await client.relayMessage(m.chat, {
  productMessage {
    title: "RaldzzXyz",
    description: " RaldzzXyz Example Description Text ",
    thumbnail: { url: "./R4IMG" },
    productId: "EXAMPLE_TOKEN",
    retailerId: "EXAMPLE_RETAILER_ID",
    url: "https://t.me/RaldzzXyz",
    body: " RaldzzXyz Example Body Text ",
    footer: "RaldzzXyz Example Footer Text",
    buttons: [
      {
        name: "cta_url",
        buttonParamsJson: "{\"display_text\":\"RaldzzXyz\",\"url\":\"https://t.me/RaldzzXyz\"}"
      }
    ],
    priceAmount1000: 72502,
    currencyCode: "IDR"
  }
})
```
