# How to build a real time chat room using Cloud Firestore

__Google’s [Cloud Firestore](https://cloud.google.com/firestore/) is a NoSQL document database that allows users to create serverless applications.__

We can use [Firestore](https://cloud.google.com/firestore/) with its NoSQL database structure (collections, documents and properties) to build synchronize real time data without writing a line of server code.

## How to use Cloud Firestore

You can read this [quickstart](https://firebase.google.com/docs/firestore/quickstart) to learn how to start a new project and set up a development environment using the required dependencies and client libraries.

Create a firestore instancy:
```
const db = firebase.firestore();
```

Add data:
```
db.collection("users").add({
    first: "Ada",
    last: "Lovelace",
    born: 1815
})
.then(function(docRef) {
    console.log("Document written with ID: ", docRef.id);
})
.catch(function(error) {
    console.error("Error adding document: ", error);
});
```

Get data:
```
db.collection("users").get().then((querySnapshot) => {
    querySnapshot.forEach((doc) => {
        console.log(`${doc.id} => ${doc.data()}`);
    });
});
```

Watch [this video](https://www.youtube.com/watch?v=2Vf1D-rUMwE&feature=emb_logo) to see how to use more Firestore features.


## Experiment

I've created this [simple live chat room](https://github.com/diogorodrigues/labs/tree/master/real-time-chat-js-firebase) using just JS (without frameworks) to test some Firestore features. ✨😁✔
