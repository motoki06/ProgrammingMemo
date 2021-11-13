# GAS（Google ）


## GASを用いたSlackへの通知スクリプト

- 事前準備

  Slackでwebhook（通知用のアカウントみたいなもの）を事前に作成しておく。

- GASのスクリプト

```javascript
function notifySlack() {

  var d = new Date();
  var mon = d.getMonth() +1 ;

  // 月ごとに担当者を順番で回しているため、当月の担当チームへメッセージを送信する。
  if ((d % 3) == 1){     //1,4,7,10月
    var text = '<@ユーザID> 今月の当番はあなたです。確認をお願いいたします。';
  }else if((d % 3) == 2){//2,5,8,11月
    var text = '<@ユーザID> 今月の当番はあなたです。確認をお願いいたします。';
  }else if((d % 3) == 0){//3,6,9,12月
    var text = '<@ユーザID> 今月の当番はあなたです。確認をお願いいたします。';
  }

  var payload = {
    'username' : '確認くん',
    'text' : text,
    'channel' : "#テスト"
  };

  var options = {
    'method' : 'post',
    'contentType' : 'application.json',
    'payload' : JSON.stringify(payload)
  };

  var url = 'https://hooks.slack.com/services/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
  UrlFetchApp.fetch(url,options);

};

```

## 参考情報
- [[GAS] 定期的に実行するための時限式トリガーを定義する方法](https://webbibouroku.com/Blog/Article/gas-schedule)

- [SlackのIncoming Webhooksでメンションを飛ばす方法](https://qiita.com/ryo-yamaoka/items/7677ee4486cf395ce9bc)
