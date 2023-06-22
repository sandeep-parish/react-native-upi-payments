# react-native-upi-payments

an react native package which supports upi payment intent for android platform

## Installation

```sh
npm install react-native-upi-payments
```

or using yarn

```sh
yarn add react-native-upi-payments
```

add this usages permission at top of your manifeast file

```
<manifest >

	add these lines only
	**<queries>
		<intent>
		  <action android:name="android.intent.action.VIEW" />
		  <data android:scheme="upi" />
		</intent>
	  </queries>**

 <application
    ......
</application>

```

## Usage

```js
import { initWithParams } from 'react-native-upi-payments';

// ...

 initWithParams({
      amount: 100,
      receiverUpi: "receiver@upi',
      currency: 'INR',//optional
    })
      .then((result: string) => {
       console.log('Payment successful',result)
      })
      .catch((e) => {
        console.log('error', e);
      });
```

If you already have a complete payment uri you can use

```js
import { initWithUri } from 'react-native-upi-payments';

// ...
const uri =
  'upi://pay?pa=dummymerchant@upi&pn=Dummy%20Merchant&mc=1234&tid=1234567890&tr=12345678&tn=Test%20Transaction&am=10.00&cu=INR';

initWithUri(uri)
  .then((result: string) => {
    console.log('Payment successful', result);
  })
  .catch((e) => {
    console.log('error', e);
  });
```

you can check if specific app package is installed or not

```js
import { isAppInstalled } from 'react-native-upi-payments';

isAppInstalled('com.whatsapp')
  .then((isInstalled) => {
    console.log('app installed');
  })
  .catch((e) => {
    console.log('Not installed');
  });
```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT

---
