---
title: "Vue Detach Firestore Listener"
categories: firebase
date: 2020-09-11 20:13:28 -0600
toc: true
tags:
  - firebase
  - vue
  - firestore
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## VUE에서 FIRESTORE 리스너 Unsubscribe 하기

더 이상 리스너가 필요하지 않을 때 리스너를 취소할 수 있다



`selectedOrder` 은 Vuex getter, 새로운 오더를 선택할 때 마다 id가 바뀐다

```js
getters: {
   selectedOrder: state => state.selectedOrder,
  }
```


아래에 docId param 은 handler의 (newValue) 의 역할, 즉 docID는 new value로 선택할 때 마다 바뀐다

```js
watch: {
    selectedOrder(docId) {
      this.$store.commit('Order/emptyChatHistory')
      if (this.chatUnsubscribe) this.chatUnsubscribe()
      if (!docId) return
      this.chatUnsubscribe = ordersCollection
        .doc(docId)
        .collection('CHAT')
        .orderBy('createdAt')
        .onSnapshot((snapshot) => {
          snapshot.docChanges().forEach((change) => {
            if (change.type === 'added') {
              this.$store.commit('Order/pushMessage', change.doc.data())
            }
          })
        })
    }
```

```js
if (this.chatUnsubscribe) this.chatUnsubscribe()

```
이 부분은 vue의 data()에 바인딩 되어 있다

```js
data() {
    return {
      chatUnsubscribe: null,
    }
  },
```


즉 오더가 선택될 때 마다 selectedOrder 값이 변하고 watch 블록 안에서 기존의 리스너를 취소하고 새로운 리스너 생성을 하게 된다
