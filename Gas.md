# GAS（Google ）


## GASを用いたSlackへの通知スクリプト

```javascript
function notifySlack() {
  var text = '<@ユーザーID> 届いていますか？';

  var payload = {
    'username' : '確認くん',
    'text' : text,
    'channel' : "#チャンネル名"
  };

  var options = {
    'method' : 'post',
    'contentType' : 'application.json',
    'payload' : JSON.stringify(payload)
  };

  var url = 'https://hooks.slack.com/services/XXXXXXXXXXXXXXX'
  
  UrlFetchApp.fetch(url,options);
}
```