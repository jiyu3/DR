# DR

## DRで何ができるのか

DRとは、他の人々に対して二次創作の許諾を簡単にできるようにする[コピーレフト](https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%94%E3%83%BC%E3%83%AC%E3%83%95%E3%83%88)なライセンスのフレームワークです。使用に関して特別な法律知識は不要です。[クリエイティブ・コモンズ](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AA%E3%82%A8%E3%82%A4%E3%83%86%E3%82%A3%E3%83%96%E3%83%BB%E3%82%B3%E3%83%A2%E3%83%B3%E3%82%BA) との違いは以下です。
- __そのままの複製を許していません__。許諾を受けた人は新たなものを創作しなければなりません。
- __期限及び場所を指定できます__。著作者は任意の期間及び場所を指定して権利許諾が可能です。

DRは以下です。
- [コピーレフト](https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%94%E3%83%BC%E3%83%AC%E3%83%95%E3%83%88)
- 無料
- より多くの二次創作を生み出す

DRは以下ではありません。
- 営利組織によって運営されているもの
- 無期限のライセンス
- 場所を指定できないライセンス

## DRとは

多くの創作作品はライセンスを付与されていません。これは、その二次利用を望む人がその都度利用申請をしなければいけないという意味で非効率的です。権利者を見つけるのはとても難しいかもしれません。もし見つかっても、クリエイターが交渉自体を嫌がる（クリエイターはそのような非生産的行為を嫌うものです）かもしれません。エージェントを雇えばこの問題は解決しますが、お金がなくて（多くのクリエイターは貧乏です）適切なエージェントを雇うお金がないかもしれません。

すでに[クリエイティブ・コモンズ](https://creativecommons.jp/)や[同人マーク](https://commonsphere.jp/doujin-license-1/)というものがありますが、これらは商用にするには不便なことが多いです。

もちろん、[コピーレフト](https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%94%E3%83%BC%E3%83%AC%E3%83%95%E3%83%88)ライセンスを利用してお金を稼いだ例は存在します。[Linux](https://ja.wikipedia.org/wiki/Linux)は言うまでもないでしょう。ここ最近の例では、Githubがあります。GithubはGitを利用しており、Gitは[GPL](https://ja.wikipedia.org/wiki/GNU_General_Public_License)と[LGPL](https://ja.wikipedia.org/wiki/GNU_Lesser_General_Public_License)でライセンスされています。もしあなたがプログラマであれば、息を吸うように[MIT](https://ja.wikipedia.org/wiki/MIT_License)ライセンスのコードやライブラリを利用しているでしょう。

しかし、この方法をクリエイティブ業界で真似るのは難しいでしょう。彼らは作品そのものを販売しており、作品に付随したサービスを売っているのではないからです。もし彼らが作品を無償で公開したら、何も得られないか、得られたとしても多少の尊敬がいいところでしょう。

もちろん例外もあります。実際のところ、日本のアニメはタダ同然です（公式には違法ですが、偉大なるグーグル・サーチ・エンジンのフォースを利用すれば、いとも簡単にアニメ配信サイトを見つけることができます）。それにもかかわらず彼らはそこそこのお金を稼いでいます。もしアニメが違法配信サイトによって有名になれば、派生商品（アニメグッズや漫画など）も付随してよく売れます。著作権者は企業に対して有料でキャラクターをライセンスすることもできるでしょう。いわゆるライセンスビジネスというもので、アニメそれ自体は宣伝として機能しています。

しかし問題がないわけではありません。一つは、商品を生産する設備や、ライセンスを管理したりする部署が必要だということです。多くのアーティストや小さな会社は、これらを所有し、または購入する資金はありません。次に、日本のアニメ業界は現に縮小中です。つまり、得るものより失うものの方が多く、持続可能ではないということです。他の業界がアニメ業界の真似をしないのはそのためでしょう。

もちろんこの問題への対処法を考案している組織はあります。私はそれらのほとんどを調査しましたが、徒労でした。それらは[プロプライエタリ](https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%83%97%E3%83%A9%E3%82%A4%E3%82%A8%E3%82%BF%E3%83%AA%E3%83%BB%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2)だったからです。誰が喜んで特定の組織の軍門に降るでしょうか？

結論としては、作品を無償で公開するのは良い方法ではありません。しかし、（大量の広告費をかけずに）作品を有名にする方法もまだ確立されていません。このような状況を鑑みて、DR(Doujin Required / Derivation Required, 二次創作必須)というライセンスを私は考案します。
これによって解決したい問題は以下です:

1. どうやって二次創作への意欲を刺激するか
2. どうやって作品を低コストで商品化するか
3. どうやって二次創作者から適切なライセンス料を徴収するか

## 目標

* 人間が読みやすいライセンス。将来的には[コモンズ証](https://creativecommons.org/licenses/by/2.1/jp/)のようなものを作りたい。
* コンピュータで処理できるライセンス。ライセンスはJSONで提供されます。これにより、開発者が自動でロイヤリティ支払いシステムを作ることが容易になります。
* 場所と期間の指定。権利者はいつどこで二次創作ができるかを指定できます。

## ライセンスの種類と仕様

ライセンスはJSONで記述されます。html文書内に<drequired>というタグで当該JSON文字列を囲んで表記します。<drequired>タグには、どんな要素を付けても構いません。ブラウザで見た際に表示されないように、```style="display:none;"``` を指定することを推奨します。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0,
    /* 以下、ライセンスの情報を書く
        :
        :
    */
  }
}
</drequired>
```

http通信で当該ページを読み込み、<drequired>タグの中身にアクセスすれば、ライセンスの情報がJSONで取得できます。

### 期間(Term)

権利者は有効期間を指定できます。期間は"yyyy-mm-dd hh-mm-ss"というフォーマットで記述可能です。もし期限が指定されていなければ、 __無期限とみなされます__。

#### 例

1999-12-31 23:59:59から2000-01-30 23:59:59までライセンスする。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "term": {
      "from": "1999-12-31 23:59:59", 
      "to": "2000-01-30 23:59:59"
    }
  }
}
</drequired>
```

### 場所(Region)

権利者は有効場所を指定できます。場所はURLの形式で示されます。もし場所が指定されていなければ、 __全ての場所とみなされます__。

- typeというパラメータが"map"という値を持っていたら、有効場所はそのマップのURLが示す現実の場所になります。
  - "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416" は「東京ビックサイト（現実世界の場所）」を示します。
- typeというパラメータが"url"という値を持っていたら、有効場所はそのURL及びそのURLを含む全てのURLが参照するWebリソースになります。
  - "http://jiyu.lol/blog/" は "http://jiyu.lol/blog/*" を示します(\* は任意の単語、もしくは空文字)」

複数の場所を指定する場合は、単純に併記します。

#### 例

http://jiyu.lol/blog/ を含むURLでの利用を許諾する。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "region": {
      "type": "url",
      "where": "http://jiyu.lol/blog"
    }
  }
}
</drequired>
```

[東京ビックサイト](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416)及び http://jiyu.lol/blog/ での利用を許諾する。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "region": {
      {
        "type": "map",
        "where": "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416"
      },
      {
        "type": "url",
        "where": "http://jiyu.lol/blog/"
      }
    }
  }
}
</drequired>
```

### 非商用(Non-commercial)

DRは主に商用での利用を想定していますが、権利者は非営利での利用を許諾したいこともあるでしょう。このパラメータを省略した場合、 __商用利用を許可しているとみなされます__。

#### 例

非営利での利用を許諾する。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "commercial": false
  }
}
</drequired>
```

### 成人向け(Adults Only)

権利者は[成人向けコンテンツ](https://ja.wikipedia.org/wiki/%E3%82%A2%E3%83%80%E3%83%AB%E3%83%88%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84)の二次創作を許可するかどうかを設定できます。このパラメータを省略した場合、 __成人向けを許可しているとみなされます__。

#### 例

成人向けの二次創作を許可しない。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "adult": false
  }
}
</drequired>
```

### 費用(Fee)

権利者は許諾費用を設定できます。総売上の額に対するパーセンテージか、固定額を指定できます。費用は二次創作物を他人に__有償で__販売するたびに発生します。許諾を受けた者が __無償で__ 二次創作作品を提供した際には __費用は生じません__。このパラメータを省略した場合、 __無償許諾とみなされます__。

#### 例

1000JPY（日本円）で利用許諾する。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "currency": "JPY",
      "price": 1000
    }
  }
}
</drequired>
```

総売上の10%で許諾する。

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "type": "dr",
    "website": "http://zunko.jp/",
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "price": "10%"
    }
  }
}
</drequired>
```

これで全部です。早速ライセンスを作ってみましょう。[工事中](http://example.com/)

例:

- 原作のURL: http://zunko.jp/
- 期間: 2017-08-11 10:00:00から2017-08-11 16:00:00まで
- 場所: http://www.deviantart.com/ を含むURL
- 商用: 可 
- 成人向け: 不許可
- 費用: 総売上の10%
  - 支払い方の説明: http://zunko.jp/con_shoushi.html

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "term": {
      "from": "2017-08-11 10:00:00",
      "to": "2017-08-11 16:00:00"
    },
    "region": {
      "type": "url",
      "url": "http://www.deviantart.com/"
    },
    "commercial": true,
    "sexual": false,
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "price": "10%"
    }
  }
}
</drequired>
```

### 許諾を受けた者の表示

許諾を受けた人は、以下の表示をすることによって、許諾を受けた旨を表することができます。

- 原作のURL(origin)
  - 複数の作品の二次創作の場合、全てを併記します。
    - 創作元が複数存在する場合、あなたは __その全てに対し__ 所定の費用を支払う必要があります。 
- 二次創作作品が公開されているURL(website)

```html
<drequired style="display:none;">
{
  "work": {
    "origin": {
      "http://zunko.jp/",
      "http://zunko.jp/con_illust.html"
    }
    "website": "https://twitter.com/t_zunko",
  }
}
</drequired>
```

### 三次創作の許諾

DRによって二次創作した作品に対し、さらにDRライセンスを付与することができます。

例:

- 原作のURL: http://zunko.jp/
- 二次創作作品が公開されているURL: https://twitter.com/t_zunko
- 期間: 2017-08-11 10:00:00から2017-08-11 16:00:00まで
- 場所: http://www.deviantart.com/ を含むURL
- 商用: 可 
- 費用: 総売上の10%
  - 支払い方の説明: http://zunko.jp/con_shoushi.html

```html
<drequired style="display:none;">
{
  "work": {
    "origin": {
      "http://zunko.jp/",
    }
    "website": "https://twitter.com/t_zunko",
  },

  "license": {
    "version": 1.0.0,
    "website": "https://twitter.com/t_zunko",
    "term": {
      "from": "2017-08-11 10:00:00",
      "to": "2017-08-11 16:00:00"
    },
    "region": {
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
</drequired>
```

三次創作した人は、以下のルールに従ってoriginの値を設定してください。
- 一次創作物と二次創作物双方の二次創作の場合、work.website 及び work.origin の値を origin に入れる
- 二次創作物のみの二次創作であって、一次創作物からの派生要素が一切ない場合、 work.website の値のみを origin に入れる

例として、 http://jiyu.lol/ で三次創作されたと仮定します。一次創作物と二次創作物双方の二次創作とします。


```html
<drequired style="display:none;">
{
  "work": {
    "origin": {
      "http://zunko.jp/",
      "https://twitter.com/t_zunko",
    }
    "website": "http://jiyu.lol/",
  }
}
```


## ライセンス

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />この文書は <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">クリエイティブ・コモンズ 表示 4.0 国際 ライセンス</a>の下に提供されており、当プロジェクトに付帯したソースコードは[MITライセンス](https://en.wikipedia.org/wiki/MIT_License)の下で提供されます。

著者: [jiyu](http://jiyu.lol/)


## バージョン情報

1.0.0 (2017-05-05)