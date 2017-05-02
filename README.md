[日本語版はこちら](#japanese)

# English

## What can you do with DR?

DR license is the license that licensers enable to grant license for others to make doujin/derivative works(__never allow dead copy__) without special knowledges of law.

Artists can:
* Allow other people to make doujin / derivative works of your works without any legal cost

Developers can:
* Implement system for licensees to sell their works and pay loyalty automatically

## Intro

A lot of creative works don't have a license. It's inefficient because licensee should request permission every time they want to use it. It may be difficult to find licensers, if they're found, they don't want to negotiate because artists don't prefer such a non-creative stuff, and they're too poor to hire good agent.

We already have [Creative Commons](https://creativecommons.org/) and [Doujin Mark(Japanese)](https://commonsphere.jp/doujin-license-1/), but it's not well-custormised for business.

Of course, we know how to earn money with [copyleft](https://en.wikipedia.org/wiki/Copyleft) license. Needless to say [Linux](https://en.wikipedia.org/wiki/Linux). In recent years, Github become bigger and bigger because of Git; Git's lincenses are GPL and [LGPL](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License). If you're programmer, you use codes and libraries licensed [MIT](https://en.wikipedia.org/wiki/MIT_License) like you breath.

But it's hard to imitate this way in creative industry. They sell works itself, not any other services. So, if they publish their works for free, they can't gain anything; if any, respects as best.

Of course there are not a few exceptions. Actually Japanese anime is almost free(Officially it's illegal, it's easy to find anime broadcasting website with great Google search engine). Nevertheless, they earn moderate money. If the anime get famous because of free-illegal-broadcasting, derivative products(anime goods, manga, and so on) are also sold well. And they can grant character's license to other companies with charge. What we call license business; anime works as advertising.

But their are the problem. First, licenser have to have facility and organization to make producsts and  managing license. Most artists and small companies can't afford to own/buy them. Secondary, Japanese anime industry is actually shrinking; totally losing is more than gaining; not sustainable. These are why other industries don't imitate this model.

In conclusion, just to publish creative works for free is not good way to survive, but there's no good other way to make works famous without huge advertising cost. Considering to these circumstances, I want to provide one of a best solution with DR(Doujin Required / Derivation Required) license:

1. How can we commercialize works without much cost?
2. How can we earn proper money from licensee?

## Immediate Goals

* Human-readable license. I'm going to make deeds like [Creative Commons do](https://creativecommons.org/licenses/by/3.0/).
* Mashine-readable license. The license is written as XML and JSON. It helpes developer to implement automatic loyalty payment system.
* Designated location and term. Licenser can designated where and when licensee can make derivative works.

## Types of licenses and their specifications

### Term

Licensers can designated the term of validity. The term is written as the datetime format "yyyy-mm-dd hh-mm-ss". If the term is not designated, __it's regarded as indefinite term__.

#### Example

Grant license from 1999-12-31 23:59:59 to 2000-01-30 23:59:59.

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

### Location

Licensers can designated the location of validity. The location is written as URL. If the location is not designated, __it's regarded as any URL__. 

- If type parameter's value is "map", it means location of validity is the spot which the map URL designated. 
  - "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416" means "designate the Tokyo Big Sight(the spot name in real world)".
- If type parameter's value is "web", it means any web resource refererd by that URL and the URLs including that URL.
  - "http://jiyu.lol/blog/" means "designate the URL http://jiyu.lol/blog/\* (\* means any words or nothing)"

#### Example

Grant license at the any URL including "http://jiyu.lol/blog/".

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <location>
    <type>web</type>
    <url>http://jiyu.lol/blog</url>
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
      "type": "web",
      "url": "http://jiyu.lol/blog"
    }
  }
}
```

Grant license in [Tokyo Big Sight](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416).

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <location>
    <type>map</type>
    <url>https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416</url>
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
      "map": "true",
      "url": "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416"
    }
  }
}
```

### Non-commercial

DR is mainly for commercial use, but sometime the licenser wants to grant non-commercial use. If licensers don't set this parameter, __it's regarded as allowing commercial use__.

#### Example

Grant license as long as it's non-commercial use.

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

### Fee

Licensers set fee of using works. They can set percentage of gross revenue or fixed price. If licensers don't set this parameter, __it's regarded as free__.

#### Example

Grant license for 1000JPY(Japanese Yen).

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <fee>
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
      "currency": "JPY",
      "price": 1000
    }
  }
}
```

Grant license for 10% of gross revenue.

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <fee>
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
      "price": "10%"
    }
  }
}
```

Now, you've learnt all parameters of DR. Let's make your own license. [Under Maintenance](http://example.com/)

For example:

- URL of Original Work: http://zunko.jp/
- Term: from 2017-08-11 10:00:00 to 2017-08-11 16:00:00
- Location: URL including http://www.deviantart.com/
- Commercial: OK 
- Fee: 10% of gross revenue

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <term>
    <from>2017-08-11 10:00:00</from>
    <to>2017-08-11 16:00:00</to>
  </term>
  <location>
    <place>internet</place>
    <url>http://www.deviantart.com/</url>
  </location>
  <commercial>true</commercial>
  <fee>
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
      "place": "internet",
      "url": "http://www.deviantart.com/"
    },
    "commercial": true,
    "fee": {
      "price": "10%"
    }
  }
}
```



# Japanese

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
    <type>web</type>
    <url>http://jiyu.lol/blog</url>
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
      "type": "web",
      "url": "http://jiyu.lol/blog"
    }
  }
}
```

[東京ビックサイト](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416)での利用を許諾する.

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <location>
    <type>map</type>
    <url>https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416</url>
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
      "map": "true",
      "url": "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416"
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

##### XML

```
<license type="dr">
  <origin>http://zunko.jp/</origin>
  <term>
    <from>2017-08-11 10:00:00</from>
    <to>2017-08-11 16:00:00</to>
  </term>
  <location>
    <place>internet</place>
    <url>http://www.deviantart.com/</url>
  </location>
  <commercial>true</commercial>
  <fee>
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
      "place": "internet",
      "url": "http://www.deviantart.com/"
    },
    "commercial": true,
    "fee": {
      "price": "10%"
    }
  }
}
```

