### copay
---
https://copay.io/

```sh
gpg --verify \
$FILENAME.sig \
$FILENAME

cd i18n
node crowdin_download.js

npm run clean-all
npm install
npm run apply:copay
npm run final:desktop

~/Library/Containers/com.bitpay.copay.desktop2/Data/.copay
~/Library/Containers/com.bitpay.wallet.desktop/Data/.bitpay

COPAY_EXTERNAL_SERVICES_CONFIG_LOCATION="~/.copay/externalServices.json" npm run apply:copay
BITPAY_EXERNAL_SERVICES_CONFIG_CONFIG_LOCATION="~/.bitpay/externalServices.json" npm run apply:bitpay

npm run apply:copay
npm run start:desktop

npm run clean-all
npm install
npm run apply:copay
npm run prepare:copay
npm run final:android

npm run clean-all
npm install
npm run apply:copay
npm run prepare:copay
npm run final:ios

npm run test

npm run apply:copay
npm run prepare:copay
npm run start:android

npm run apply:copay
npm run prepare:copay
npm start:ios

npm run test

npm install
npm run apply:copay
npm run start

git clone https://github.com/bitpay/copay.git
cd copay
```

```
```

