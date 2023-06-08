[![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/colored.png)](#table-of-contents)
# Baileys Library (Unofficial)

 > **Warning**: Ini Hanyalah Repo Baileys Yang Sudah Ter-update & Fix Jika Ada Problem. Repo Ini Adalah Fork Dari amiruldev20, Karena Repo amiruldev20 Juga Hilang.
 
 > **Note**: Kalau Ada Problem, Klik Tombol Whatsapp Di Bawah.
---

<p align="center">
<img src="https://github.com/razn-id.png" width="150">
</p>
<p align="center">
<a href="#"><img title="Baileys Library" src="https://img.shields.io/badge/BAILEYS LIBRARY (UNOFFICIAL)-green?colorA=%23ff0000&colorB=%23017e40&style=for-the-badge"></a>
<a href="https://chat.whatsapp.com/KujS5iG5TKfCnrRTlj4MfO" target="_blank"><img width="" src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="Whatsapp"></a>
</p>
<p align="center">
<a href="https://github.com/razn-id/followers"><img title="Followers" src="https://img.shields.io/github/followers/razn-id?color=red&style=flat-square"></a>
<a href="https://github.com/razn-id/Baileys-Library/stargazers/"><img title="Stars" src="https://img.shields.io/github/stars/razn-id/Baileys-Library?color=blue&style=flat-square"></a>
<a href="https://github.com/razn-id/Baileys-Library/network/members"><img title="Forks" src="https://img.shields.io/github/forks/razn-id/Baileys-Library?color=red&style=flat-square"></a>
<a href="https://github.com/razn-id/Baileys-Library/watchers"><img title="Watching" src="https://img.shields.io/github/watchers/razn-id/Baileys-Library?label=Watchers&color=blue&style=flat-square"></a>
<a href="https://github.com/razn-id/Baileys-Library"><img title="Open Source" src="https://badges.frapsoft.com/os/v2/open-source.svg?v=103"></a>
<a href="https://github.com/razn-id/Baileys-Library/"><img title="Size" src="https://img.shields.io/github/repo-size/razn-id/Baileys-Library?style=flat-square&color=green"></a>
<a href="https://hits.seeyoufarm.com"><img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Frazn-id%Baileys-Library&count_bg=%2379C83D&title_bg=%23555555&icon=probot.svg&icon_color=%2300FF6D&title=hits&edge_flat=false"/></a>
<a href="https://github.com/razn-id/Baileys-Library/graphs/commit-activity"><img height="20" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg"></a>&nbsp;&nbsp;
</p>

---

## Example

Periksa & jalankan [example.ts](https://github.com/razn-id/Baileys/blob/master/Example/example.ts) untuk melihat contoh penggunaan library ini. Skrip ini mencakup kasus penggunaan yang paling umum. Untuk menjalankan skrip example, unduh atau klon repo ini, lalu ketikkan kode berikut ini di terminal:
1. ``` cd path/to/Baileys ```
2. ``` yarn ```
3. ``` yarn example ```

## Instalasi

Versi stabil:
```
yarn add github:@razn-id/Baileys-Library
```

Impor kode Anda menggunakan:
``` ts 
import makeWASocket from '@adiwajshing/baileys'
```
 Atau
``` js 
const connection = require("@adiwajshing/Baileys")
```

## Connection
> **Note**: Setting Tambahan Connection Option Seperti Dibawah Ini Terlebih Dahulu

``` ts
const connectionOptions = {
printQRInTerminal: true, // memunculkan qr di terminal
syncFullHistory: false, // menerima riwayat lengkap
markOnlineOnConnect: false, // membuat wa bot of, true jika ingin selalu menyala
connectTimeoutMs: 60_000, // atur jangka waktu timeout
defaultQueryTimeoutMs: 0, // atur jangka waktu query (0: tidak ada batas)
keepAliveIntervalMs: 10000, // interval ws
generateHighQualityLinkPreview: true, // menambah kualitas thumbnail preview
// patch dibawah untuk tambahan jika hydrate/list tidak bekerja
patchMessageBeforeSending: (message) => {
    const requiresPatch = !!(
        message.buttonsMessage 
        || message.templateMessage
        || message.listMessage
    );
    if (requiresPatch) {
        message = {
            viewOnceMessage: {
                message: {
                    messageContextInfo: {
                        deviceListMetadataVersion: 2,
                        deviceListMetadata: {},
                    },
                    ...message,
                },
            },
        };
    }

    return message;
},
getMessage: async (key) => {
         if (store) {
            const msg = await store.loadMessage(key.remoteJid, key.id)
            return msg.message || undefined
         }
         return {
            conversation: "hello, i'm Amirul Dev"
         }
      },
// get message diatas untuk mengatasi pesan gagal dikirim, "menunggu pesan", dapat dicoba lagi
}
``` 

Jika koneksi berhasil, Anda akan melihat kode QR tercetak di layar terminal Anda, pindai dengan WhatsApp di ponsel Anda dan Anda akan masuk!
