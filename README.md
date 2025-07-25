# vany-lib

A simple library for creating videos by vany.ai

## Install
```bash
npm install vany-lib
```
## use
Connect with your Google account on the vany.ai website, and take the refresh_token from local storage.
```js
const {default: craftVideo, downloadVideo } = require('vany-lib');
const fs = require('fs');

let refresh_token = 'your_refresh_token';

(async () => {
    let {url, title, transcript} = await craftVideo('your prompt', refresh_token, {
        mode: 'auto', //optional
        ratio: 'desktop' //optional
    });
    
    let buffer = await downloadVideo(url); //optional (to get buffer)

    fs.writeFileSync(title.replace(/[\\/:*?"<>|]/g, "_") + ".mp4", buffer);

    console.log(title, transcript)
})();
```
