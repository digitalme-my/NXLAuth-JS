## Installation

### 1. Import jQuery and NXLAuth-JS libs
This library requires jQuery to handle AJAX request to Auth provider
```
<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script src="https://cdn.identity.nexlife.com.my/js/1.1.0/nxlauth.min.js"></script>
```

```
$(document).ready(function () {
    // All javascript codes / functions should be inside jQuery `.ready()` block
});
```

### 2. Initialize NXLAuth-JS application
```
var nxlauth = new App({
    openIdConnectUrl: 'https://auth.sso.unifi.space',
    clientId: '<client-id>',
    redirectUri: '<redirect-uri>',
    scope: 'openid offline',
});
nxlauth.checkAuth(callback);
```

### 3. Login
```
nxlauth.login();
```

### 4. Get / Refresh Token
```
nxlauth.getToken(callback);
```

### 5. Get Userinfo
```
nxlauth.getUserInfo(accessToken, callback);
```

---

* `accessToken` should be available in login / refresh token response
* `callback` is your custom javascript callback function with 1 argument
#### Callback example
```
function callback(response) {
    var accessToken = response.accessToken;
    $('#access_token').val(accessToken);
}
```
Sample body of response as below:
```
{
  "accessToken": "N7jACtoS_eXdvauixngyggioRquqW86a8....2B978WQnAk9__CRznb6d6t5rEv-iY",
  "tokenType": "bearer",
  "expiresIn": 3599,
  "refreshToken": "LFn1YK8GMhgLtw4tUzU8gQJwrgcQFp3K....ULeFOA-j4WbCDleKLMqFRjGcn05PKvUue_-tktboMo",
  "scope": "openid offline",
  "idToken": "eyJhbGciOiJSUzI1NiIsImtp....dpm9FE8MTuurp4p_NDU",
  "issuedAt": 1546967672
}
```

## Demo application
Demo application is a nodejs application built with express framework

### 1. Installation
```
$ cd example
$ npm install express --save
```

### 2. Running nodejs server
```
$ node server.js
```

### 3. Run test on browser
```
http://localhost:3000
```


## Minify command
Use this tool to re-compile and minify the `nxlauth.js` into `nxlauth.min.js`
```
uglifyjs nxlauth.js -c -o nxlauth.min.js
```
