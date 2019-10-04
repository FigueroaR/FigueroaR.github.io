---
layout: post
title:      "Crypto CLI gem"
date:       2019-10-04 13:16:55 -0400
permalink:  crypto_cli_gem
---


From zero to hero.

		 
   Something I had always wanted to do was write a program of some sort, I had no idea where to start. What I did know however was on what I wanted my project to be based on. So, this project made me feel like I went from zero to hero. Although there is a long way to go from here. I’m looking forward to it.

   My CLI gem is based on crypto currencies. I found Cryptocurrency to be an interesting topic, still in its infancy, this project could maybe shine a light on crypto, something that seems so foreign to many, now is encapsulated in a gem. Crypto can seem scary, but somehow developing this gem made it - not so scary. Yes, you are right I did not create a crypto coin, but I think I’m on the right path. 
	 


**The technical part**

   First off, this CLI gem is based on scraping (to gather info) from a website. In this case i had to use two websites     
"[Coinmarketcap.com](http://)" and "[Coinlib.io](http://)".  As a rule of thumb, scrape a website where information is easily accessible. In this case "Coinlib.io" provided me with the essential information like the name, symbol, percent change, market cap, of the coins. Yes, the price information was available on Coinlib.io but it was structured in a not so easy to parse manner. That's where "Coinmarketcap.com" came into place.  Coinmarketcap.com had all the information i needed but was distributed in a format not so easily accessible (for a beginner like me), so price was the only other things Coinmarketcap.com provided me fairly. 


```
class CryptoPrice::Scraper

  def self.scrape_coinmarketcap
    doc = Nokogiri::HTML(open("https://coinmarketcap.com"))
    doc.css("a.price").text.split("$").select{ |k| k.length > 0  }
  end

  def self.scrape_coinlib
    doc = Nokogiri::HTML(open("https://coinlib.io/coins"))
    prices = self.scrape_coinmarketcap  #<<<< **here is the second website**
    names = doc.css("div.tbl-currency").text.split("\n").select{ |k| !k.include?("[") && k.length > 0  }
    symbols = doc.css("span.tbl-coin-abbrev").text.gsub("]", "").split("[").select{ |k| k.length > 0  }
    changes = doc.css("span.tbl-price.pr-change").text.split("%").select{ |k| k.length > 0  }
    marketcaps = doc.css("span.mob-info-value").text.split("$").select{ |k| k.length > 0  }
    
    index = 0
    while index < names.length && index < symbols.length 
      symbol = symbols[index]
      name = names[index]
      price = prices[index]
      change = changes[index]
      marketcap = marketcaps[index]
      CryptoPrice::Coin.new(symbol, name, price,change, marketcap)
      index += 1
    end
		
    CryptoPrice::Coin.all   #where the coins are stored
		
  end 
end 
```

Yes two websites, but we did it. 



**The Artist**

   There is an art to designing any program, CLI Gem or any structure, although logic is king, art is the instrument that helps logic proceed. I recommend sketching or pseudo code before actively implementing your code. Let your creativity flow, use visualization to see your progress and future progress.
	 
1. What is the objective?
2. what requirements do you need to accomplish your mission?
3. Areyour tools ready to go? start coding
4. start simple, start small, "skate -> skooter -> vehicle"


**Ready?**

   Your ideas are busrting, so just start typing, or sketching, but know where you are headed, end goal. 
	 


**Installation**

Add this line to your application's Gemfile:

> gem 'crypto_price'

And then execute:

> $ bundle

Or install it yourself as:

> $ gem install crypto_price

 




