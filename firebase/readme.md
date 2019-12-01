This is a simplified example based on https://github.com/firebase/quickstart-js/tree/master/messaging
but with much fewer bells and whistles so to be better understood.

[Read more about Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/)

Getting Started
---------------

1. Create your project on the [Firebase Console](https://console.firebase.google.com).
1. Open Project and go to **Project settings > Cloud Messaging** and there in section **Web configuration** click **Generate key pair** button.
1. Copy public key and in `index.html` file replace `<YOUR_PUBLIC_VAPID_KEY_HERE>` with your key.
1. You must have the [Firebase CLI](https://firebase.google.com/docs/cli/) installed. If you don't have it install it with `npm install -g firebase-tools` and then configure it with `firebase login`.
1. On the command line run `firebase use --add` and select the Firebase project you have created.
1. On the command line run `firebase serve -p 8081` using the Firebase CLI tool to launch a local server.
1. Open [http://localhost:8081](http://localhost:8081) in your browser.
1. Click **REQUEST PERMISSION** button to request permission for the app to send notifications to the browser.
1. Use the generated Instance ID token (IID Token) to send an HTTP request to FCM that delivers the message to the web application, inserting appropriate values for [`YOUR-SERVER-KEY`](https://console.firebase.google.com/project/_/settings/cloudmessaging) and `YOUR-IID-TOKEN`.

### HTTP
```
POST /fcm/send HTTP/1.1
Host: fcm.googleapis.com
Authorization: key=YOUR-SERVER-KEY
Content-Type: application/json

{
  "notification": {
    "title": "Portugal vs. Denmark",
    "body": "5 to 1",
    "icon": "firebase-logo.png",
    "click_action": "http://localhost:8081"
  },
  "to": "YOUR-IID-TOKEN"
}
```



```
firebase list projects
firebase use --add <project-id>
firebase serve -p 8081
```