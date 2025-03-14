# crypto-js [![Build Status](https://travis-ci.org/brix/crypto-js.svg?branch=develop)](https://travis-ci.org/brix/crypto-js)

JavaScript library of crypto standards.

## Node.js (Install)

Requirements:

- Node.js
- npm (Node.js package manager)

```bash
npm install crypto-js
```

### Usage

ES6 import for typical API call signing use case:

```javascript
import sha256 from 'crypto-js/sha256';
import hmacSHA512 from 'crypto-js/hmac-sha512';
import Base64 from 'crypto-js/enc-base64';

const message, nonce, path, privateKey; // ...
const hashDigest = sha256(nonce + message);
const hmacDigest = Base64.stringify(hmacSHA512(path + hashDigest, privateKey));
```

Modular include:

```javascript
var AES = require("crypto-js/aes");
var SHA256 = require("crypto-js/sha256");
...
console.log(SHA256("Message"));
```

Including all libraries, for access to extra methods:

```javascript
var CryptoJS = require("crypto-js");
console.log(CryptoJS.HmacSHA1("Message", "Key"));
```

## Client (browser)

Requirements:

- Node.js
- Bower (package manager for frontend)

```bash
bower install crypto-js
```

### Usage

Modular include:

```javascript
require.config({
    packages: [
        {
            name: 'crypto-js',
            location: 'path-to/bower_components/crypto-js',
            main: 'index'
        }
    ]
});

require(["crypto-js/aes", "crypto-js/sha256"], function (AES, SHA256) {
    console.log(SHA256("Message"));
});
```

Including all libraries, for access to extra methods:

```javascript
// Above-mentioned will work or use this simple form
require.config({
    paths: {
        'crypto-js': 'path-to/bower_components/crypto-js/crypto-js'
    }
});

require(["crypto-js"], function (CryptoJS) {
    console.log(CryptoJS.HmacSHA1("Message", "Key"));
});
```

### Usage without RequireJS

```html
<script type="text/javascript" src="path-to/bower_components/crypto-js/crypto-js.js"></script>
<script type="text/javascript">
    var encrypted = CryptoJS.AES(...);
    var encrypted = CryptoJS.SHA256(...);
</script>
```

## API

See: https://cryptojs.gitbook.io/docs/

### AES Encryption

#### Plain text encryption

```javascript
var CryptoJS = require("crypto-js");

// Encrypt
var ciphertext = CryptoJS.AES.encrypt('my message', 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var originalText = bytes.toString(CryptoJS.enc.Utf8);

console.log(originalText); // 'my message'
```

#### Object encryption

```javascript
var CryptoJS = require("crypto-js");

var data = [{id: 1}, {id: 2}]

// Encrypt
var ciphertext = CryptoJS.AES.encrypt(JSON.stringify(data), 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var decryptedData = JSON.parse(bytes.toString(CryptoJS.enc.Utf8));

console.log(decryptedData); // [{id: 1}, {id: 2}]
```

### List of modules


- ```crypto-js/core```
- ```crypto-js/x64-core```
- ```crypto-js/lib-typedarrays```

---

- ```crypto-js/md5```
- ```crypto-js/sha1```
- ```crypto-js/sha256```
- ```crypto-js/sha224```
- ```crypto-js/sha512```
- ```crypto-js/sha384```
- ```crypto-js/sha3```
- ```crypto-js/ripemd160```

---

- ```crypto-js/hmac-md5```
- ```crypto-js/hmac-sha1```
- ```crypto-js/hmac-sha256```
- ```crypto-js/hmac-sha224```
- ```crypto-js/hmac-sha512```
- ```crypto-js/hmac-sha384```
- ```crypto-js/hmac-sha3```
- ```crypto-js/hmac-ripemd160```

---

- ```crypto-js/pbkdf2```

---

- ```crypto-js/aes```
- ```crypto-js/tripledes```
- ```crypto-js/rc4```
- ```crypto-js/rabbit```
- ```crypto-js/rabbit-legacy```
- ```crypto-js/evpkdf```

---

- ```crypto-js/format-openssl```
- ```crypto-js/format-hex```

---

- ```crypto-js/enc-latin1```
- ```crypto-js/enc-utf8```
- ```crypto-js/enc-hex```
- ```crypto-js/enc-utf16```
- ```crypto-js/enc-base64```

---

- ```crypto-js/mode-cfb```
- ```crypto-js/mode-ctr```
- ```crypto-js/mode-ctr-gladman```
- ```crypto-js/mode-ofb```
- ```crypto-js/mode-ecb```

---

- ```crypto-js/pad-pkcs7```
- ```crypto-js/pad-ansix923```
- ```crypto-js/pad-iso10126```
- ```crypto-js/pad-iso97971```
- ```crypto-js/pad-zeropadding```
- ```crypto-js/pad-nopadding```



```javascript
js 引用  <script src="crypto-js.min.js"></script>
小程序的ajax使用  var CryptoJS = require("@/common/js/crypto-js");
小程序的vue使用 import CryptoJS from '/common/js/crypto-js.js'

//base64
var strs = "dddddd";
//base64加密
var strsJiami = CryptoJS.enc.Base64.stringify(CryptoJS.enc.Utf8.parse(strs));
//base64解密
var strsJiemi = CryptoJS.enc.Base64.parse(strsJiami).toString(CryptoJS.enc.Utf8);
console.log("字符串:"+strs,"base64加密:"+strsJiami,"base64解密:"+strsJiemi);


//HmacSHA1
CryptoJS.HmacSHA1("dddddd","EpointMobileService_Xcx**##")





//des加密 CBC模式加密
function encryptByDESModeCBC(message,key){
	var keyHex = CryptoJS.enc.Utf8.parse(key);
	var ivHex = CryptoJS.enc.Utf8.parse(key);
	encrypted = CryptoJS.DES.encrypt(message,keyHex,{
		iv:ivHex,
		mode: CryptoJS.mode.CBC
	});
	return encrypted.ciphertext.toString();
}



```
