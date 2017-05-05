# DR

[日本語版はこちら](https://github.com/jiyu3/DR/blob/master/README_ja.md)

## What can you do with DR?

DR license is the license that licensers enable to grant license for others to make doujin/derivative works without expertise of law. The biggest difference from [Creative Commons](https://en.wikipedia.org/wiki/Creative_Commons) are:
- __DO NOT ALLOW copy__ licenser's works. licensees should create new works.
- __limited time and region__. Licensers can dedicate where and when licensees can make derivative/doujin works.

DR is:
- [Copyleft](https://en.wikipedia.org/wiki/Copyleft)
- Free to use
- Enhanse people to make derivative/doujin works

DR is NOT:
- Profit Organization
- forcing unlimited terms
- forcing unlimited region


## Intro

A lot of creative works don't have a license. It's inefficient because licensee should request permission every time they want to use it. It may be difficult to find licensers, if they're found, they don't want to negotiate because artists don't prefer such a non-creative stuff, and they're too poor to hire good agent.

We already have [Creative Commons](https://creativecommons.org/) and [Doujin Mark(Japanese)](https://commonsphere.jp/doujin-license-1/), but it's not well-custormised for business.

Of course, we know how to earn money with [copyleft](https://en.wikipedia.org/wiki/Copyleft) license. Needless to say [Linux](https://en.wikipedia.org/wiki/Linux). In recent years, Github become bigger and bigger because of Git; Git's lincenses are GPL and [LGPL](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License). If you're programmer, you use codes and libraries licensed [MIT](https://en.wikipedia.org/wiki/MIT_License) like you breath.

But it's hard to imitate this way in creative industry. They sell works itself, not any other services. So, if they publish their works for free, they can't gain anything; if any, respects as best.

Of course there are not a few exceptions. Actually Japanese anime is almost free(Officially it's illegal, it's easy to find anime broadcasting website with great Google search engine). Nevertheless, they earn moderate money. If the anime get famous because of free-illegal-broadcasting, derivative products(anime goods, manga, and so on) are also sold well. And they can grant character's license to other companies with charge. What we call license business; anime works as advertising.

But their are the problem. First, licenser have to have facility and organization to make producsts and  managing license. Most artists and small companies can't afford to own/buy them. Secondary, Japanese anime industry is actually shrinking; totally losing is more than gaining; not sustainable. These are why other industries don't imitate this model.

Of course, some organizations try to make solution. I surveyed most of them, only to understand they're out of style; they're [proprietary](https://en.wikipedia.org/wiki/Proprietary_software). Who is willing to submit to specified organization?

In conclusion, just to publish creative works for free is not good way to survive, but there's no good other way to make works famous without huge advertising cost. Considering to these circumstances, I want to provide one of a best solution with DR(Doujin Required / Derivation Required) license:

1. How can we enhanse people to make derivative/doujin works?
2. How can we commercialize works without much cost?
3. How can we earn proper money from licensee?

## Goals

* Human-readable license. I'm going to make deeds like [Creative Commons do](https://creativecommons.org/licenses/by/3.0/).
* Mashine-readable license. The license is written as XML and JSON. It helpes developer to implement automatic loyalty payment system.
* Designated location and term. Licenser can designated where and when licensee can make derivative works.


## Types of licenses and their specifications

License text is written as JSON format. The JSON is enclosed by <drequired> tag. You can set any attribute to <drequired>. It's recommended to add ```style="display:none;"``` in order not to display it on browser view.

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0,
    /* license description below
        :
        :
    */
  }
}
</drequired>
```

Accessing that page by http and read text inside <drequired>, you can get license information by JSON format.

### Term

Licensers can designated the term of validity. The term is written as the datetime format "yyyy-mm-dd hh-mm-ss". If the term is not designated, __it's regarded as indefinite term__.

#### Example

Grant license from 1999-12-31 23:59:59 to 2000-01-30 23:59:59.

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

### Region

Licensers can designated the location of validity(region). The region is written as URL. If the region is not designated, __it's regarded as any URL__. 

- If type parameter's value is "map", it means location of validity is the spot which the map URL designated. 
  - "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416" means "designate the Tokyo Big Sight(the spot name in real world)".
- If type parameter's value is "url", it means any web resource refererd by that URL and the URLs including that URL.
  - "http://jiyu.lol/blog/" means "designate the URL http://jiyu.lol/blog/* (\* means any words or nothing)"

#### Example

Grant license at the any URL including "http://jiyu.lol/blog/".

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

Grant license in [Tokyo Big Sight](https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416).

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "region": {
      "type": "url",
      "where": "https://www.google.co.jp/maps/place/Tokyo+Big+Sight/@35.6298243,139.7920476,17z/data=!3m2!4b1!5s0x601889dc3beb6fed:0xb6c29ca3bd43e108!4m5!3m4!1s0x601889dc629d1e7b:0xa4d1509a76045a01!8m2!3d35.62982!4d139.7942416"
    }
  }
}
</drequired>
```

### Non-commercial

DR is mainly for commercial use, but sometime the licenser wants to grant non-commercial use. If licensers don't set this parameter, __it's regarded as allowing commercial use__.

#### Example

Grant license as long as it's non-commercial use.

```html
<drequired style="display:none;">
{
  "license": {
    "version": 1.0.0,
    "website": "http://zunko.jp/",
    "region": "http://jiyu.lol/blog",
    "commercial": false
  }
}
</drequired>
```

### Fee

Licensers set fee of using works. They can set percentage of gross revenue or fixed price. Licensers should clarify the URL which people can understand how to pay. Licensees are charged when they sell their derivative/doujin works __for profit__. If they provide it __for free__, licensees __don't have to pay any fee to original author__. If licensers don't set this parameter, __it's regarded as free__.

#### Example

Grant license for 1000JPY(Japanese Yen).

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

Grant license for 10% of gross revenue.

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

Now, you've learnt all parameters of DR. Let's make your own license. [Under Maintenance](http://example.com/)

For example:

- URL of websiteal Work: http://zunko.jp/
- Term: from 2017-08-11 10:00:00 to 2017-08-11 16:00:00
- Region: URL including http://www.deviantart.com/
- Commercial: OK 
- Fee: 10% of gross revenue
  - Description of how to pay: http://zunko.jp/con_shoushi.html

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
    "fee": {
      "description": "http://zunko.jp/con_shoushi.html",
      "price": "10%"
    }
  }
}
</drequired>
```

### Display license

Licensees can assert their right by displaying JSON below.

- URL of original works
  - If it's derivative/doujin work of multiple works licensed by DR, you should write all of them down(if not, you should use plural form "origins")
    - You should pay __all original authors__.
- URL of your derivative/doujin work

```html
<drequired style="display:none;">
{
  "work": {
    "origins": {
      "http://zunko.jp/",
      "http://zunko.jp/con_illust.html"
    }
    "website": "https://twitter.com/t_zunko",
  }
}
</drequired>
```

### Apply DR to the derivative/doujin work

You can apply DR license to your work derived by other works licensed by DR.

Example:

- URL of original work: http://zunko.jp/
- URL of your derivative/doujin work
- Term: From 2017-08-11 10:00:00 to 2017-08-11 16:00:00
- Region: URL including http://www.deviantart.com/ 
- Commercial: OK 
- Fee: 10% of gross revenue
  - Description of how to pay: http://zunko.jp/con_shoushi.html

```html
<drequired style="display:none;">
{
  "work": {
    "origins": {
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

People who make derivative/doujin work(third work) of your work(second work) should set origins value following this rule:
- If it's derivative/doujin works of both original work(first work) and derivative/doujin work(second work), set work.website and work.origins to origins
- If it's derivative/doujin works of only derivative/doujin work(second work), not including any material of original work(first work), set work.website to origins

For example, third work published http://jiyu.lol/. It's derivative/doujin work of both original work(first work) and derivative/doujin work(second work).

```html
<drequired style="display:none;">
{
  "work": {
    "origins": {
      "http://zunko.jp/",
      "https://twitter.com/t_zunko",
    }
    "website": "http://jiyu.lol/",
  }
}
```


## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This text is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>, and the source codes bundled in this project are licensed under the [MIT license](https://en.wikipedia.org/wiki/MIT_License).

Author: [jiyu](http://jiyu.lol/)


## Version

1.0.0 (2017-05-05)