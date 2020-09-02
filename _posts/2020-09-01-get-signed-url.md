---
title: "Firebase Storage Get Signed URL"
categories: firebase
date: 2020-09-01 15:13:28 -0600
toc: true
tags:
  - firebase
  - storage
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## FIREBASE STORAGE 에서 SIGNED URL 생성하기

다음과 같이 생성 가능하다

```js
//test.js
const functions = require('firebase-functions');
const admin = require('firebase-admin')
const storage = admin.storage()

exports = module.exports = functions.https.onRequest(async (req, res) => {
    try {
        const bucket = storage.bucket("gs://xxx.appspot.com/images/company_logo"); // 하위폴더 까지 작성
        const imageFile = bucket.file('sample.jpg') // 확장자 포함

        const options = {
            action: 'read',
            expires: '03-17-4000'
        };

        // Get a signed URL for the file
        let getSignedUrl = await imageFile.getSignedUrl(options)

        return res.send('success')

    }
    catch (e) {
        console.log('e :>> ', e);
        return res.status(400).send('failed')
    }

})
```

```js
//index.js

/* index애서 initializeApp()을 한 번만 실행하며 나머지 펑션들을 exports 해준다. */
const admin = require('firebase-admin')
admin.initializeApp();
export { basicHTTP, advanceHTTP, api } from "./http";
export { createUserRecord } from "./auth";
```

만약 여러개의 프로젝트를 사용할 경우
https://gist.github.com/jofftiquez/1317de9ce97ab72b8295013a3f2ccff0


