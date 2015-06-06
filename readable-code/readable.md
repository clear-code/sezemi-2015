## 1

### 実際のコード

https://github.com/qzwpq/qzwpq-sezemi-2015-readable-code/blob/master/app.js#L25

```js
var getNameById = function(id, obj) {
```

### どうしてリーダブルだと思っているかの説明

`getXXXById`という名前が`getElementById`というよく使われているメソッド名と同じ規則なのでJavaScriptを使っている人にはなじみがあってリーダブル。

### この書き方の一言説明

言語になじんだ命名規則

## 2

### 実際のコード

https://github.com/ch1ca0/ch1ca0-sezemi-2015-readable-code/blob/master/recipe.py#L3-L4

```python
recipe_file = open('recipe-data.json', 'r')
recipe_json = json.load(recipe_file)
```

### どうしてリーダブルだと思っているかの説明

どちらもレシピのデータだけど、表現が違うというのを名前で示していてリーダブル。

### この書き方の一言説明

メタデータ付加命名

## 3

### 実際のコード

https://github.com/ayemos/ayemos-sezemi-2015-readable-code/blob/master/src/recipe/RecipeLoader.java#L31-L34

```java
private static Set<RecipeModel> fetchRemoteRecipes(String url) {
  // 今回は使わない。
  return null;
}
```

### どうしてリーダブルだと思っているかの説明

コードがあるとこれはどこで使っているの？という気持ちになるが、いろいろ調べたうえで実は使っていないんじゃない？と知った場合はがっかりくる。実装した人が使っていないと明示しているならほんとに使っていないんだということが明確になるので読む人にとってリーダブル。

### この書き方の一言説明

使わない宣言

## 去年の分


https://github.com/doraemon13x/doraemon13x-sezemi-2014-readable-code-2/blob/master/mission3.c#L9

    exit(EXIT_FAILURE);	/* エラーの場合は異常終了する */

C（UNIX系のシステム？）では、異常終了するときは0以外の値を返すのが通例で、

    exit(1);

でも動くのは動くんだけど、EXIT_FAILUREという名前を使っているので、「失
敗して終了するんだな」というのがわかりやすい。

EXIT_SUCCESSというのもある。

名前: 自己記述的変数名。

https://github.com/gecko655/gecko655-sezemi-2014-readable-code-2/blob/master/src/readablecode/Recipe.java#L52

    private void printRecipe(File file, int id) {
        //TODO implement printing method when id is specified.
        //めっちゃ途中で終わっちゃいました！！すいません！！！！
        
    }

「何をしなければいけないか（TODO）」（IDを指定された時に出力するメソッ
ドを実装しないといけない）かがわかるコメントだからわかりやすい。「TODO」
だけだとなんかしなければいけないかはわかるけど、何をしなければいけない
かまではわからない。

（メソッドのシグネチャーから「TODO: implement me」だけでわかる場合もある。）

名前: TODOコメント。

https://github.com/amiq11/amiq11-sezemi-2014-readable-code-2/blob/master/recipe.c#L27

    inline void *mymalloc(size_t size) {
        void *tmp = malloc(size);
        if (tmp == NULL) { perror("malloc"); exit(EXIT_FAILURE); }
        return tmp;
    }

perrorはシステムエラー表示用の専用関数。専用関数を使っているので、何を
しようとしているか（システムエラーを表示しようとしている）というのが明
確でわかりやすい。

名前: 専用機能の使用。
