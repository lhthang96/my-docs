# React Native Push Notification

### The current project - robohi-sharing-mobile is using FCM (Firebase Cloud Messaging) to push notification to native apps, also backend with AWS SNS (Simple Notification Service) to delivery api which is called to FCM.

## Overview of mobile notification

### IOS requesting permissions

IOS prevent any applications pushing or displaying a notification (or alert), unless u have received a permission from user. So if u wanna handle notification in iPhone or iPad, the first thing u need to do is asking user to allow your apps pushing notifications to the screen. This can be easily archived by the react-native-firebase, which is mentioned later.

### Receiving messages

We are using Firebase Cloud Messaging service, so basically, we can receive messages in real-time, notification is just a part of a message, so you can also send some pieces of data along with it. The format of a cloud message is something like:

<pre>
{
  ...otherConfigFields,
  notification: {
    title: 'Notification title',
    body: 'Notification content'
  },
  data: {
    key_1: value_1,
    key_2: value_2,
    ...
  }
}
</pre>

### App states

With an application running in both Android and iOS, it will be at one of these three states:

- **Foreground**: When the application is open and in view (user is using it).
- **Background**: When the application is open, however, user minimize it, like pressed a `Home` button or switch to another apps.
- **Quit**: When user close the application.

Based on the app state and messages content, we can determine if it would be displayed.

<table>
  <th>
    <tr>
      <td></td>
      <td>Foreground</td>
      <td>Background</td>
      <td>Quit</td>
    </tr>
    <tr>
      <td>Notification</td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/OOjs_UI_icon_close-ltr-destructive.svg/768px-OOjs_UI_icon_close-ltr-destructive.svg.png" style="width: 20px; height: 20px" alt="close-icon" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Icons8_flat_checkmark.svg/768px-Icons8_flat_checkmark.svg.png" style="width: 20px; height: 20px" alt="checkmark" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Icons8_flat_checkmark.svg/768px-Icons8_flat_checkmark.svg.png" style="width: 20px; height: 20px" alt="checkmark" />
        </div>
      </td>
    </tr>
    <tr>
      <td>Notification + Data</td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/OOjs_UI_icon_close-ltr-destructive.svg/768px-OOjs_UI_icon_close-ltr-destructive.svg.png" style="width: 20px; height: 20px" alt="close-icon" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Icons8_flat_checkmark.svg/768px-Icons8_flat_checkmark.svg.png" style="width: 20px; height: 20px" alt="checkmark" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/Icons8_flat_checkmark.svg/768px-Icons8_flat_checkmark.svg.png" style="width: 20px; height: 20px" alt="checkmark" />
        </div>
      </td>
    </tr>
    <tr>
      <td>Data</td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/OOjs_UI_icon_close-ltr-destructive.svg/768px-OOjs_UI_icon_close-ltr-destructive.svg.png" style="width: 20px; height: 20px" alt="close-icon" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/OOjs_UI_icon_close-ltr-destructive.svg/768px-OOjs_UI_icon_close-ltr-destructive.svg.png" style="width: 20px; height: 20px" alt="close-icon" />
        </div>
      </td>
      <td style="text-align: center">
        <div style="width: 20px; height: 20px; margin: auto">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/OOjs_UI_icon_close-ltr-destructive.svg/768px-OOjs_UI_icon_close-ltr-destructive.svg.png" style="width: 20px; height: 20px" alt="close-icon" />
        </div>
      </td>
    </tr>
    <tr>
  </th>
</table>

At any state, react-native-firebase has an apprepriate event to handle the receiving messages, which is mentioned later.
