# ミニガイド：Mavenの使い方

## Javaのソースの実行の流れ

```text
HelloWorld.java
↓ javac
HelloWorld.class
↓ java
実行
```

1つのソースで完結するならそれでもいいけど、たくさん.classができるならそうもやっていられない。

複数の.classをまとめてjar（Javaアーカイブ。中身はzip）にできる。これが最終成果物になる。

```text
a.class + b.class + c.class → foo.jar
```

↑を自動化するためのツールが作られてきた。

### Ant

ビルドするタスクとか○○するタスクとかがある。

設定ファイルはbuild.xml。プロジェクトディレクトリーのトップにbuild.xmlを置いておいて`ant`を実行すると.jarとかができる。

```text
プロジェクトディレクトリーのトップ
  +-+ src/
  | +----- foo.java
  +- build.xml

```text
% ant
```

自由度があるので、プロジェクトごとにルールが違う。

  * ソースディレクトリーが`src/`だったり`source/`だったり好きに決められる。

自由度があるので把握しづらいという欠点がある。

### Maven

  * 自由度を下げた。
    * ディレクトリー構造を決めた。
  * jarの自動依存性解決機能を組み込んだ。

設定ファイルはpom.xml（pomはProject Object Modelの略。）

#### Mavenのディレクトリー構造

```text
プロジェクトトップ
  +- src
     + main
     | + java
     | |  + pkg-a
     | |    + foo.java （これが.classになり.jarになる）
     | + resources
     |   + foo.props
     |   + foo.xml
     + test
       + java
         + pkg-a
           + fooTest.java
```

このディレクトリー構成にしておくと次のコマンドが使える。

```text
% mvm compile # classを作る
% mvm test    # テストを実行
% mvm package # jarを作る
% mvm install # ローカルリポジトリーへjarを移動する
```

#### Mavenの依存性解決機能

依存しているクラスはjarに入っている。なので、それを使うためにはjarを参照する必要がある。

Antは自由度が高いのでプロジェクトによってjarが置かれる場所は違う。なので、プロジェクトごとに探すのが大変。Mavenはjarが置かれる場所を決めた。

（席を外してしまったのでついていけなくなった。。。なので、想像しながら書く。）

jarはセントラルリポジトリーからダウンロードしてくるのかしら。

セントラルリポジトリーではディレクトリー構造が決まっている。groupId（pom.xmlに書く内容？）でディレクトリーを指定でき、version（pom.xmlに書く内容？）とかの情報を使うとパスを特定できて、ダウンロードできるようになる。（んだと思う。）

ダウンロードしたファイルはローカルにキャッシュする。

依存しているライブラリーは↓みたいな感じでpom.xmlに指定する。

```xml
<!-- ... -->
  <project>
    <dependency>
      <groupId>org.mixer2</groupId>
    </dependency>
  </project>
<!-- ... -->
```

IDE（EclipseとかIntelliJとか）はMavenと連携するプラグインを提供しているので↑の機能を便利に使える。
