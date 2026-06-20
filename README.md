# <div align='center'>npm:xzcbailz</div>
<div align='center'>

[![npm version](https://img.shields.io/npm/v/xzcbailz.svg)](https://www.npmjs.com/package/xzcbailz)
[![License](https://img.shields.io/badge/license-GPL%203-blue.svg)](LICENSE)
[![Downloads](https://img.shields.io/npm/dm/xzcbailz.svg)](https://www.npmjs.com/package/xzcbailz)
</div>

# Donation
## Support our development with donation
**Donation QRis**
```
https://files.catbox.moe/60xczp.jpg  // copy ts link & scan
```
--- 

## Usage
```json
"depencies": {
  "xzcbailz": "latest"
}
```
## Import
```javascript
const {
  default: makeWASocket,
  // Other functionz
} = require('xzcbailz');
```

---
# How To Connect To Whatsapp
## With QR Code
```javascript
const {
  default: makeWASocket
} = require('xzcbailz');

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
} = require('xzcbailz');

const client = makeWASocket({
  browser: ['Ubuntu', 'Chrome', '20.00.1'],
  printQRInTerminal: false,
  version: fetchLatestWAWebVersion()
  aiLabel: true // for ai label in every message are bot send
  // Other options
});

const number = "628XXXXX";
const code = await client.requestPairingCode(number.trim) //Use : (number, "YYYYYYYY") for custom-pairing

console.log("Ur pairing code : " + code)
```

# Store Data
```
const {
  default: makeWASocket,
  makeInMemoryStore
} = require('xzcbailz');
const pino = require('pino');

const store = makeInMemoryStore({
  logger: pino().child({ level: 'silent', stream: 'store' })
});
const client = makeWASocket({
  // optionz
});
store.bind(client.ev)

client.ev.on('contacts.upsert', () => {
  console.log('Get new contact: ' + Object.values(store.contacts()));
})
```
# Sending messages

## send orderMessage
```javascript
const fs = require('fs');
const ZeppImg = fs.readFileSync('./ZeppImage');

await client.sendMessage(m.chat, {
  thumbnail: ZeppImg,
  message: "Gotta get a grip",
  orderTitle: "7eppeli-Corporation",
  totalAmount1000: 72502,
  totalCurrencyCode: "IDR"
}, { quoted:m })
```

## send pollResultSnapshotMessage
```javascript
await client.sendMessage(m.chat, {
  pollResultMessage: {
    name: "7eppeli-Corporation",
    options: [
      {
        optionName: "poll 1"
      },
      {
        optionName: "poll 2"
      }
    ],
    newsletter: {
      newsletterName: "7eppeli | Killer Queen Information",
      newsletterJid: "1@newsletter"
    }
  }
})
```

## send productMessage
```javascript
await client.relayMessage(m.chat, {
  productMessage {
    title: "7eppeli.pdf",
    description: "zZZ...",
    thumbnail: { url: "./ZeppImage" },
    productId: "EXAMPLE_TOKEN",
    retailerId: "EXAMPLE_RETAILER_ID",
    url: "https://t.me/YuukeyD7eppeli",
    body: "Nak Tido",
    footer: "Footer",
    buttons: [
      {
        name: "cta_url",
        buttonParamsJson: "{\"display_text\":\"7eppeli-Pdf\",\"url\":\"https://t.me/YuukeyD7eppeli\"}"
      }
    ],
    priceAmount1000: 72502,
    currencyCode: "IDR"
  }
})
```

## send member label
```javascript
await client.sendMessage(m.chat, {
  groupLabel: {
    labelText: "Tag anggota tercantum di sini"
  }
})
```

## send message to members in group
```javascript
await client.sendMessageMembers(m.chat, {
  extendedTextMessage: {
    text: "save aku 7epsync"
  }
}, {})
```
# Simple sendMessage

## send text
```javascript
await client.sendText(m.chat, "7eppsynC", {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```
## send image
```javascript
await client.sendImage(m.chat, { url: "./zepy.jpg" }, "7eppsynC", {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send video
```javascript
await client.sendVideo(m.chat, { url: "./zepy.mp4" }, "7eppsynC", {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send audio
```javascript
await client.sendAudio(m.chat, { url: "./zepy.mp3" }, {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send location
```javascript
await client.sendLocation(m.chat, "7eppsynC", 90.0, 90.0, "https://t.me/XzC_Info", "1234567890", {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send polling
```javascript
await client.sendPoll(m.chat, "7eppsynC", ["1", "2", "3"], true, {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send quiz
```javascript
await client.sendQuiz(m.chat, "7eppsynC", ["1", "2", "3"], "2", {
  contextInfo: {
    mentionedJid: [m.chat]
  }
}, {
  key: {
    remoteJid: "status@broadcast",
    participant: m.sender,
    fromMe: true
  },
  message: {
    conversation: "\0"
  }
})
```

## send status mention
```javascript
await client.statusMention(m.chat, {
  extendedTextMessage: {
    text: "7eppsynC"
  }
})
```
Follow https://t.me/XzC_Information kalau mau liat type message yg lain :v
