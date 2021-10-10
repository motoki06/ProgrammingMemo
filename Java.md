# Javaに関するプログラミングノート

## 参考サイト
[Let'sプログラミング-Java入門](https://www.javadrive.jp/start/)

## 多次元配列

### 宣言方法

- `データ型[][] 配列変数名`

    ```java
    int[][] num;`
    ```

### 配列の作成

- `配列変数名 = new データ型[要素数][]`
    ```java
    int[][] num;
    num = new int[2][];`
    ```

### 要素に格納される配列の数が等しい場合（2×3の多次元配列）

- 
    ```Java
    int[][] num;
    num = new int[2][3];
    ```

- 
  |要素1|要素2|値|
  |--|--|--|
  |0|0|0|
  |0|1|0|
  |0|2|0|
  |1|0|0|
  |1|1|0|
  |1|2|0|

  ※値は何もセットしていないので、全て0

### 要素の取り出し方

```java
    for (int i = 0; i < 2; i++){
      for (int j = 0; j < 3; j++){
        System.out.println("num[" + i + "][" + j + "] = " + num[i][j]);
      }
    }
```

## ハッシュマップ
- [HashMapの使い方](https://www.javadrive.jp/start/collection/index3.html)

HashMap クラスは Map インターフェースを実装したクラスの一つで、キーと値のペアをマップに追加します。マップに対してキーを指定することで、対応する値を取得することができます。

※ HashMap クラスは java.util パッケージに含まれています。利用する場合は java.util.LinkedList をインポートしてください。

- 作成方法 
    ```java
    HashMap<キーのデータ型,値のデータ型> 変数名 = new HashMap<>();
    ```
  - キーをストリング、値を数値型とする場合
    ```java
    HashMap<String,Integer> 変数名 = new HashMap<>();
    ```
- マップに追加されているキーと値のペアの数を返す(size)
    ```java
    Map<String,Integer> map = new HashMap<>();

    System.out.println(map.size());  // 0

    map.put("リンゴ",80);
    map.put("オレンジ",120);
    map.put("ブドウ",90);

    System.out.println(map.size());  // 3
    ```

- 指定したキーとペアの値を取得する(get)
    ```java
    Map<String,Integer> map = new HashMap<>();

    map.put("リンゴ",80);
    map.put("オレンジ",120);
    map.put("ブドウ",90);

    System.out.println(map.get("オレンジ")); // 120
    System.out.println(map.get("メロン")); // null
    ```
- 要素の取得
    ```java
    HashSet<String> hs = new HashSet<String>();
    //  ハッシュセットにデータを追加
    hs.add("山田太郎");
    hs.add("山田太郎");
    hs.add("太田美代子");
    hs.add("斉藤五郎");
    hs.add("斉藤五郎");
    //  追加した成分をすべて表示
    for(String s:hs){
        System.out.println(s);
    }
    ```

やりたいこと：検討中リスト（bookmarklist）に含まれる要素（会社名、職種名、応募用URL）を取得する  
bookmarkListを取得し、listの何番目にアクセスするかを指定して、かつの値を取得する。

- bookmarklist[何番目].company_name
- bookmarklist[何番目].job_name
- bookmarklist[何番目].url
