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

## aws cli（S3）
  参考リンク：[aws s3 のコマンド一覧(抜粋)](https://qiita.com/uhooi/items/48ef6ef2b34162988295#aws-s3-%E3%81%AE%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E4%B8%80%E8%A6%A7%E6%8A%9C%E7%B2%8B)

- ### S3バケットの一覧確認
  - s3バケットの一覧の表示
  `aws s3 ls s3://{バケット名}`

  表示例
  ```
  $ aws s3 ls s3://motokinakashima-test
  2021-10-31 09:17:28          0 test.txt
  ```

  - s3バケットからのコピー（ローカルからS3）
  `aws s3 cp {ファイルパス} s3://{バケット名}/{パス}`

  - s3バケットからのコピー（ローカルからS3）
  `aws s3 cp s3://{バケット名}/{パス} {ファイルパス}`

# ECS