---
layout: post
title:      "My Ruby Gem CLI Portfolio Project: Daily Wines"
date:       2018-10-15 12:54:21 -0400
permalink:  my_ruby_gem_cli_portfolio_project_daily_wines
---


> “For the things we have to learn before we can do them, we learn by doing them.”  - Aristotle

I didn't really understand the major concepts in Ruby until I actually sat my butt down and started working on the project. As I struggled to get my CLI to work, light bulbs went off in my head. I am finally getting this programming thing, ya'll.

Basically, my CLI gem lists today's "Daily Wine Picks" from [winespectator.com](https://www.winespectator.com/dailypicks). The picks, obviously, change daily. If the user selects one of the three picks by its number, the program will provide more information on the wine, including its price, point rank, and a short (and very flowery) description of the wine. The program then prompts the user to select another daily pick or exit.  

![](https://youtu.be/93I-zaVnXTo)

Someday I will wonder how I agonized for so long to complete this. 


So, after going through the CLI Gem Walkthrough Video and taking care of the technical things, I figured that, since my gem was similar to Avi's, I would mimick his code as closely as possible. Of course, this was difficult because his code was so clean and I was so used to creating clunky code that I was a bit lost. I figured it out eventually.


I started off creating my CLI.rb, the CLI's controller. It has a call instance method which outputs the date, greets the user, and calls a second method that lists the daily wine picks. The list_wines method calls on the scraper file, then iterates over each wine created by the wines.rb file. The next method, menu, with provides the logic for each choice the program grants the user: It outputs the information on the chosen wine or allows the user to exit. The goodbye method bids the user farewell and quits the program.

The second file I created was the wines.rb, which creates the Wine class. Each wine instance needed a name attribute, a category attribute, and a price attribute. "Attr_accessor" is a method that tells the class to create setter and getter methods for each attribute. The @@all variable is a class variable that collects all the wine instances and puts it into an array. The all method is a class method that exposes the @@all class variable, and finally, the initialize method creates a new instance of itself and sticks it in the wine (@@all) array.

The third file was the one that hung me up the most: The scraper.rb. The website's page had a ton of selectors that were the same, but didn't present the same information. So I had to find a way to select only *certain* selectors of that type. I used Pry to figure it out, once I'd figured out Pry. 

![](https://gifimage.net/wp-content/uploads/2017/10/nervous-laughter-gif-6.gif)

Anyhoo, I created a method that used Nokogiri to open the website page, a method to scrape the info from the CSS, and a make_wines to iterate over each selector and pull the information from it: Name, Price, and Description. 

```
class DailyWines::Scraper

	def get_wine_index
		Nokogiri::HTML(open("https://www.winespectator.com/dailypicks"))
	end

	def scrape_wines
		self.get_wine_index.css(".mod-container:not(.clearfix)").first(3)
	end



	def make_wines
		scrape_wines.each do |content|
			wine = DailyWines::Wine.new

			wine.name = content.css("h5 a").text
			wine.price = content.css("h6").text
			wine.description = content.css(".paragraph").text.strip
		end

	end

end
```

And that's it! WHEW! Upward and onward...




