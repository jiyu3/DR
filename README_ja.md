# DR

## DRとは

多くの創作作品はライセンスを付与されていません。これは、その二次利用を望む人がその都度利用申請をしなければいけないという意味で非効率的です。権利者を見つけるのはとても難しいかもしれません。もし見つかっても、クリエイターが交渉自体を嫌がる（クリエイターはそのような非生産的行為を嫌うものです）かもしれません。エージェントを雇えばこの問題は解決しますが、お金がなくて（多くのクリエイターは貧乏です）適切なエージェントを雇うお金がないかもしれません。

すでに[クリエイティブ・コモンズ](https://creativecommons.org/)や[同人マーク](https://commonsphere.jp/doujin-license-1/)というものがありますが、これらは商用にするには不便なことが多いです。

もちろん、[コピーレフト](https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%94%E3%83%BC%E3%83%AC%E3%83%95%E3%83%88)ライセンスを利用してお金を稼いだ例は存在します。[Linux](https://ja.wikipedia.org/wiki/Linux)は言うまでもないでしょう。ここ最近の例では、Githubがあります。GithubはGitを利用しており、Gitは[GPL](https://ja.wikipedia.org/wiki/GNU_General_Public_License)と[LGPL](https://ja.wikipedia.org/wiki/GNU_Lesser_General_Public_License)でライセンスされています。もしあなたがプログラマであれば、息を吸うように[MIT](https://ja.wikipedia.org/wiki/MIT_License)ライセンスのコードやライブラリを利用しているでしょう。

しかし、この方法をクリエイティブ業界で真似るのは難しいでしょう。彼らは作品そのものを販売しており、作品に付随したサービスを売っているのではないからです。もし彼らが作品を無償で公開したら、何も得られないか、得られたとしても多少の尊敬がいいところでしょう。

もちろん例外もあります。実際のところ、日本のアニメはタダ同然です（公式には違法ですが、偉大なるグーグル・サーチ・エンジンのフォースを利用すれば、いとも簡単にアニメ配信サイトを見つけることができます）。それにもかかわらず彼らはそこそこのお金を稼いでいます。もしアニメが違法配信サイトによって有名になれば、派生商品（アニメグッズや漫画など）も付随してよく売れます。著作権者は企業に対して有料でキャラクターをライセンスすることもできるでしょう。いわゆるライセンスビジネスというもので、アニメそれ自体は宣伝として機能しています。

しかし問題がないわけではありません。一つは、商品を生産する設備や、ライセンスを管理したりする部署が必要だということです。多くのアーティストや小さな会社は、これらを所有し、または購入する資金はありません。次に、日本のアニメ業界は現に縮小中です。つまり、失うものの方が得るものの方が多く、持続可能ではないということです。他の業界がアニメ業界の真似をしないのはそのためでしょう。

結論としては、作品を無償で公開するのは良い方法ではありません。しかし、（大量の広告費をかけずに）作品を有名にする方法もまだ確立されていません。このような状況を鑑みて、DR(Doujin Required / Derivation Required, 二次創作必須)というライセンスを私は考案します。
これによって解決したい問題は以下です:

1. どうやって作品を低コストで商品化するか
2. どうやって二次創作者から適切なライセンス料を徴収するか

## 当面の目標

* 人間が読みやすいライセンス。将来的には[コモンズ証](https://creativecommons.org/licenses/by/2.1/jp/)のようなものを作りたい。
* コンピュータで処理できるライセンス。ライセンスはXMLとJSONフォーマットで提供されます。これにより、開発者が自動でロイヤリティ支払いシステムを作ることが容易になります。
* 場所と期間の指定。権利者はいつどこで二次創作ができるかを指定できます。

## ライセンスの種類と仕様

### 期間(Term)

権利者は有効期間を指定できます。期間は"yyyy-mm-dd hh-mm-ss"というフォーマットで記述可能です。もし期限が指定されていなければ、__無期限とみなされます__。

#### 例

1999-12-31 23:59:59から2000-01-30 23:59:59までライセンスする。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <term>
    <from>1999-12-31 23:59:59</from>
    <to>2000-01-30 23:59:59</to>
  </term>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "term": {
      "from": "1999-12-31 23:59:59", 
      "to": "2000-01-30 23:59:59"
    }
  }
}
```

### 場所(Location)

権利者は有効場所を指定できます。場所はURLの形式で示されます。もし場所が指定されていなければ、__全ての場所とみなされます__。

- typeというパラメータが"map"という値を持っていたら、有効場所はそのマップのURLが示す現実の場所になります。
  - "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416" は「東京ビックサイト（現実世界の場所）」を示します。
- typeというパラメータが"web"という値を持っていたら、有効場所はそのURL及びそのURLを含む全てのURLが参照するWebリソースになります。
  - "http://jiyu.lol/blog/" は「"http://jiyu.lol/blog/\*" を示します(\* は任意の単語、もしくは空文字)」

#### 例

「http://jiyu.lol/blog/」を含むURLでの利用を許諾する。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <location>
    <type>url</type>
    <where>http://jiyu.lol/blog</where>
  </location>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "location": {
      "type": "url",
      "where": "http://jiyu.lol/blog"
    }
  }
}
```

[東京ビックサイト](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416)での利用を許諾する。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <location>
    <type>map</type>
    <where>https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416</where>
  </location>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "location": {
      "type": "url",
      "where": "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416"
    }
  }
}
```

### 非商用(Non-commercial)

DRは主に商用での利用を想定していますが、権利者は非営利での利用を許諾したいこともあるでしょう。このパラメータを省略した場合、__商用利用を許可しているとみなされます__。

#### 例

非営利での利用を許諾する。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <commercial>false</commercial>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "location": "http://jiyu.lol/blog",
    "commercial": false
  }
}
```

### 費用(Fee)

権利者は許諾費用を設定できます。総売上の額に対するパーセンテージか、固定額を指定できます。このパラメータを省略した場合、__無償許諾とみなされます__。

#### 例

1000JPY（日本円）で利用許諾する。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <fee>
    <description>http://zunko.jp/con_shoushi.html</description>
    <currency>JPY</currency>
    <price>1000</price>
  </fee>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "currency": "JPY",
      "price": 1000
    }
  }
}
```

総売上の10%で許諾する。

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <fee>
    <description>http://zunko.jp/con_shoushi.html</description>
    <price>10%</price>
  </fee>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "price": "10%"
    }
  }
}
```

これで全部です。早速ライセンスを作ってみましょう。[工事中](http://example.com/)

例:

- 原作のURL: http://zunko.jp/
- 期間: 2017-08-11 10:00:00から2017-08-11 16:00:00まで
- 場所: http://www.deviantart.com/ を含むURL
- 商用: 可 
- 費用: 総売上の10%
  - 支払い方の説明: http://zunko.jp/con_shoushi.html

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <term>
    <from>2017-08-11 10:00:00</from>
    <to>2017-08-11 16:00:00</to>
  </term>
  <location>
    <type>url</url>
    <where>http://www.deviantart.com/</where>
  </location>
  <commercial>true</commercial>
  <fee>
    <description></description>
    <price>10%</price>
  </fee>
</license>
```

##### JSON

```
{
  "license": {
    "type": "dr",
    "origin": "http://zunko.jp/",
    "term": {
      "from": "2017-08-11 10:00:00",
      "to": "2017-08-11 16:00:00"
    },
    "location": {
      "type": "url",
      "url": "http://www.deviantart.com/"
    },
    "commercial": true,
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "price": "10%"
    }
  }
}
```

