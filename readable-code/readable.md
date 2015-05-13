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
