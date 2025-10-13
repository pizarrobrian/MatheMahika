# MatheMahika
MatheMahika



1. CREATE NEW FILE NAMED 'admin-config.js'

2. Enter the code in 'admin-config.js'
```js
export const adminConfig = {
    username: '',
    password: ''
};
```
3. CREATE NEW FILE NAMED 'firebase-config.js'

4. Enter the code in 'firebase-config.js'

```js

const env = typeof import.meta !== 'undefined' && import.meta?.env ? import.meta.env : {};
const injectedConfig = typeof window !== 'undefined' ? window.__FIREBASE_CONFIG__ : undefined;

/* EDIT FIREBASE CREDENTIALS*/
const defaultConfig = {
    apiKey: '',
    authDomain: '',
    databaseURL: '',
    projectId: '',
    storageBucket: '',
    messagingSenderId: '',
    appId: '',
    measurementId: ''
};

const envConfig = {
    apiKey: env?.VITE_FIREBASE_API_KEY,
    authDomain: env?.VITE_FIREBASE_AUTH_DOMAIN,
    databaseURL: env?.VITE_FIREBASE_DATABASE_URL,
    projectId: env?.VITE_FIREBASE_PROJECT_ID,
    storageBucket: env?.VITE_FIREBASE_STORAGE_BUCKET,
    messagingSenderId: env?.VITE_FIREBASE_MESSAGING_SENDER_ID,
    appId: env?.VITE_FIREBASE_APP_ID,
    measurementId: env?.VITE_FIREBASE_MEASUREMENT_ID
};

function stripUndefined(source) {
    return Object.fromEntries(Object.entries(source).filter(([, value]) => value !== undefined && value !== ''));
}

export const firebaseConfig = {
    ...defaultConfig,
    ...stripUndefined(envConfig),
    ...(injectedConfig ? stripUndefined(injectedConfig) : {})
};
```

