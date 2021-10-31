## aws cli（configure）

awsへの操作をcliで実施する。  
cli実行時の認証情報をセットできるのが`configure`  
参考リンク：[【AWS】aws cliのconfigureを設定する！](https://tektektech.com/aws-cli-configure-setting/)

- ### 現在の設定情報の確認  
  `cat ~/.aws/credentials`

    - `default`は、aws cliの実行時にcredentialsが指定されて  いない場合のデフォルトの設定として使われる。
    - 各種コマンド実行時に`--profile [アカウント名（terraform  等）]`をつけることで、そのアカウントでのコマンド実行となる

    表示例

    ```
    $ cat ~/.aws/credentials
    [default]
    aws_access_key_id = XXXXXXXXXX
    aws_secret_access_key = YYYYYYYYYY
    [terraform]
    aws_access_key_id = XXXXXXXXXX
    aws_secret_access_key = YYYYYYYYYY
    ```
  
- ### 認証情報の追加設定  
    `aws configure --profile [アカウント名]`  
    ※一括入力ではなく、Access Key以降は順次入力を求められる  
    ※Default region/Default outputは入力しなくてもOK
  
    表示例
    ```
    $ aws configure --profile test
    AWS Access Key ID [None]: XXXXXXXXXX
    AWS Secret Access Key [None]:
    Default region name [None]:
    Default output format [None]:
    ```

- ### 認証情報の修正  
  - 全アカウントの修正  
  `aws configure`  
  項目ごとに入力を求められるので入力していけばOK  
  - 特定のアカウントについてのみ修正  
  `aws configure --profile [アカウント名]`
