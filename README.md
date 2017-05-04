# DR

[日本語版はこちら](https://github.com/jiyu3/DR/blob/master/README_ja.md)

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

## Goals

* Human-readable license. I'm going to make deeds like [Creative Commons do](https://creativecommons.org/licenses/by/3.0/).
* Mashine-readable license. The license is written as XML and JSON. It helpes developer to implement automatic loyalty payment system.
* Designated location and term. Licenser can designated where and when licensee can make derivative works.

## 



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
- If type parameter's value is "url", it means any web resource refererd by that URL and the URLs including that URL.
  - "http://jiyu.lol/blog/" means "designate the URL http://jiyu.lol/blog/\* (\* means any words or nothing)"

#### Example

Grant license at the any URL including "http://jiyu.lol/blog/".

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

Grant license in [Tokyo Big Sight](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416).

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

Licensers set fee of using works. They can set percentage of gross revenue or fixed price. Licensers should clarify the URL which people can understand how to pay. If licensers don't set this parameter, __it's regarded as free__.

#### Example

Grant license for 1000JPY(Japanese Yen).

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

Grant license for 10% of gross revenue.

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

Now, you've learnt all parameters of DR. Let's make your own license. [Under Maintenance](http://example.com/)

For example:

- URL of Original Work: http://zunko.jp/
- Term: from 2017-08-11 10:00:00 to 2017-08-11 16:00:00
- Location: URL including http://www.deviantart.com/
- Commercial: OK 
- Fee: 10% of gross revenue
  - Description of how to pay: http://zunko.jp/con_shoushi.html

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

## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This text is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>, and the source codes bundled in this project are licensed under the [MIT license](https://en.wikipedia.org/wiki/MIT_License).

Author: [jiyu](http://jiyu.lol/)