# Lightning Wallet Connect

This project includes web components for connecting to Lightning Wallets and enabling [WebLN](https://webln.guide).
These components work with pure HTML and all Javascript libraries frameworks such as React, Angular, Vue, Solid.js, etc.

## 🚀 Quick Start

```
npm install @getalby/lightning-wallet-connect
```
or
```
yarn add @getalby/lightning-wallet-connect
```
or for use without any build tools:
```
// alby-tools now available at window.albyTools
<script src="https://cdn.jsdelivr.net/npm/@getalby/lightning-wallet-connect@1.0.0/dist/index.browser.js"></script>
```

## 📽️ Demo
https://user-images.githubusercontent.com/33993199/234830578-0baf25f9-0179-4244-941c-0c558c613a7a.mov

## 🤙 Usage

Lightning wallet connect exposes:
- `lwc:connected` window event which fires when a wallet is connected and window.webln is ready to use
- Web components for allowing user to connect their desired Lightning wallet:
  - `<lwc-button/>` - launches the LWC Modal on click
  - `<lwc-modal/>` - render the modal on its own
  - _more components coming soon_

Current wallets supported:
- [Alby Browser extension] (https://getalby.com)
- [Alby NWC](https://nwc.getalby.com)

### Pure HTML
```html
<html>
  <body>
    <lwc-button></lwc-button>
    <script src="https://cdn.jsdelivr.net/npm/@getalby/lightning-wallet-connect@1.0.0/dist/index.browser.js"></script>
    <script>
      window.addEventListener('lwc:connected', async () => {
        // TODO: hide the lwc-button
        const invoice = // (...invoice generated by backend)
        await window.webln.sendPayment(invoice);
        confetti();
      });
    </script>
  </body>
</html>
```

### React
```tsx
import '@getalby/lightning-wallet-connect';

// in your component, listen to lightning wallet connected event
const [lwcConnected, setLwcConnected] = React.useState(false);
React.useEffect(() => {
  const onConnected = () => setLwcConnected(true);
  window.addEventListener('lwc:connected', onConnected);

  return () => {
    window.removeEventListener('lwc:connected', onConnected);
  };
}, []);

const invoice = // (...invoice generated by backend)

return lwcConnected ? <>
    <button onClick={() => window.webln.sendPayment(invoice)}/>
  </> : <lwc-button/>}
```


# 🔥 Lit

This template is generated from the `lit-starter-ts` package in [the main Lit
repo](https://github.com/lit/lit). Issues and PRs for this template should be
filed in that repo.

See [Get started](https://lit.dev/docs/getting-started/) on the Lit site for more information.

# 🛠️ Development
See [dev/README](dev/README.md)

## Build
`yarn build`

## Testing
`yarn test`

## Need help?

We are happy to help, please contact us or create an issue.

* [Twitter: @getAlby](https://twitter.com/getAlby)
* [Telegram group](https://t.me/getAlby)
* support at getalby.com
* [bitcoin.design](https://bitcoin.design/) Discord community (find us on the #alby channel)
* Read the [Alby developer guide](https://guides.getalby.com/overall-guide/alby-for-developers/getting-started) to better understand how Alby packages and APIs can be used to power your app.