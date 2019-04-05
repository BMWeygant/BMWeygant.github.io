---
layout: post
title:      "My CLI Project Journey"
date:       2019-04-05 11:55:56 -0400
permalink:  my_cli_project_journey
---


  So, after month's of labs in the free course, pre-work, and the first 3 weeks of the full time course I'm finally here on my first independent project. For this project I decided to keep it as simple as possible. Rather than get some grand idea of building my own fantasy football website in a week with my fairly limited experience, I instead chose to focus on scraping some data from one of my favorite forms of fantasy football: Madden Ultimate Team!! And if you are a fellow partaker in any variation - whether console or the Madden Mobile app - you undoubtedly know muthead.com is the go to source for any information and data you could possibly want, so that was the obvious place to scrape my data from.
		
		
 Now, I knew the joke would be on me all week because project week this time around just so happened to start on non other than April Fool's Day. An ominous and telling sign indeed as the first day of project week I managed to accomplish absolutely nothing on my project. Instead I spent the whole day setting up and learning how to use my local environment until the last 10 minutes, when for the sake of sanity I wrote the basic outline of a Scraper class...before spending the next 30 minutes 'learning' that pushing my work to Github is now a fun 3 step process that Learn IDE would do for me in one simple command.  But no worries because I would make it all up the next day right?  Riigghhht.
		
   **Day 2** of the saga was wildly unproductive in real time, as I had all day to work on my project, and succumbed to several delays and changes in project ideas and scope (ok I DID have a grand idea to build my own fantasy football website). I had difficulties scraping data from the first two websites i tried for real football stats for 3 major reasons: 1. General incompetence 2. Site protections and 3. The sheer amount of data available made it harder for a noob scraper like me to parse through everything simply. I scrapped several project ideas, and subsequently several pages of code each time, for the sake of trying to simplify what I was looking to accomplish  because I was working on a time limit. By the end of the day, I basically had enough code to scrape the team name 'Tampa Bay Buccaneers' from the site....a major accomplishment! But ultimately not so productive. And that's when I turned my attention to muthead.com, which has been much more noob friendly with each page containig more finite amounts of data and data being slightly less dynamic than the first sites I tried to scrape from.  Last thing I did at the end of the night was come up with a new, simpler project and planned it all out from start to finish: I was going to scrape the prices page and bring the user data based on who have been the biggest gainers and losers in the madden auction house. Brilliant! Having a more clear and simple project in mind I got a decent amount of sleep for the busy day ahead.*
	 
  *I speak of day 2 negativley, but in hindsight day 2 was easily the most vital day of this project as it pushed me in so many different directions and helped to expand my knowledge by pushing me deeper into things I didn't know. It has proven to be a neccessary evil.*
	 
 **Day 3:** With my new project stil clear in my mind (not to mention the auction house being one of the best parts of MUT) I set out with renewed vigor! I build a functioning yet basic scraper model on the https://www.muthead.com/prices/xbox-one page and what do I get? 503 temporarily unavailable.  Ugh. Would I have to change my project again? Turns out, yes, but luckily it was only an error specific to that page on the site, and the scraper worked on the players page just fine. So on the third day I had my project - choose a card to see it's attributes! So let's get working! 
  	I decided my Scraper class would parse the data on the basics of a card: Name, Position, Ovr (short for overall), and Price. Stats would also be as important, but having 30+ stats in a basic application with this time limit seemed a bit unwise so I didnt include them. With a little bit of digging and research however I did manage to figure out a way to link to the specific card's profile page where the stats are viewable for users - although I havent yet implemented this yet as of this writing and am still thinking I may be better served expanding it later on rather than for project presentation. 
	 
	 
	 
	 ```
	 def self.scrape_muthead
      cards = []

      doc = Nokogiri::HTML(open(BASE_URL))
      doc.css("tbody").each do |details|
			binding.pry
	 ```
	 
	 
	 
So now that we have the ability to scrape the data, what does the data look like? Well....
	 
```
  => "\r\n        \n\n\n\n\n    \n        Odell Beckham Jr\n        \n    \n\n    Movers\n\n\n\n\n99WR1.56M\n\n\n\n\n    \n        Chuck Bednarik\n        \n    \n\n    NFL Draft\n\n\n\n\n99LOLBUnknown\n\n\n\n\n    \n        Antonio Brown\n        \n    \n\n    Movers\n\n\n\n\n99WR1.11M\n\n\n\n\n    \n        Julian Edelman\n        \n    \n\n    Super Bowl Present\n\n\n\n\n99WR678K\n\n\n\n\n    \n        Rob Gronkowski\n        \n    \n\n    House Rules\n\n\n\n\n99TEN/A\n\n\n\n\n    \n        Rob Gronkowski\n        \n    \n\n    Limited Edition\n\n\n\n\n99TE1.70M\n\n\n\n\n    \n        Chris Johnson\n        \n    \n\n    NFL Combine\n\n\n\n\n99HB822K\n\n\n\n\n    \n        Keyshawn Johnson\n        \n    \n\n    NFL Draft\n\n\n\n\n99WR430K\n\n\n\n\n    \n        Cam Newton\n        \n    \n\n    NFL Draft\n\n\n\n\n99QB702K\n\n\n\n\n    \n        Bruce Smith\n        \n    \n\n    NFL Draft\n\n\n\n\n99RE426K\n\n\n\n\n    \n        Telvin Smith\n        \n    \n\n    NFL Draft\n\n\n\n\n99ROLB443K\n\n\n\n\n    \n        Larry Allen\n        \n    \n\n    Ultimate Legends\n\n\n\n\n98RG375K\n\n\n\n\n    \n        Saquon Barkley\n        \n    \n\n    Rookie Premiere\n\n\n\n\n98HBN/A\n\n\n\n\n    \n        Saquon Barkley\n        \n    \n\n    NFL Honors\n\n\n\n\n98HB955K\n\n\n\n\n    \n        Anthony Barr\n        \n    \n\n    Free Agents\n\n\n\n\n98ROLB645K\n\n\n\n\n    \n        Le'Veon Bell\n        \n    \n\n    Free Agents\n\n\n\n\n98HB548K\n\n\n\n\n    \n        Mel Blount\n        \n    \n\n    Ultimate Legends\n\n\n\n\n98CB640K\n\n\n\n\n    \n        Joey Bosa\n        \n    \n\n    NFL Draft\n\n\n\n\n98LE235K\n\n\n\n\n    \n        Cris Carter\n        \n    \n\n    Ultimate Legends\n\n\n\n\n98WR635K\n\n\n\n\n    \n        Landon Collins\n        \n    \n\n    Free Agents\n\n\n\n\n98SS705K\n\n\n\n\n    \n        Aaron Donald\n        \n    \n\n    NFL Honors\n\n\n\n\n98RE700K\n\n\n\n\n    \n        Julian Edelman\n        \n    \n\n    Super Bowl Present\n\n\n\n\n98WR386K\n\n\n\n\n    \n        Nick Foles\n        \n    \n\n    Free Agents\n\n\n\n\n98QB668K\n\n\n\n\n    \n        Mean Joe Greene\n        \n    \n\n    Ultimate Legends\n\n\n\n\n98DT400K\n\n\n\n\n    \n        Todd Gurley II\n        \n    \n\n    Team of the Year\n\n\n\n\n98HB301K\r\n    "
[3] pry(Scraper)>
```
	
   That wont do at all! But positive vibes: that IS exactly information I was looking for! Up until this point, I persoanlly was struggling scraping anything off of tables, so this was a major breakthrough for me! After a couple deep breaths, I reassessed my scraper selector and saw I need to grab where the specifics ar below <tbody>...<tr> seemed promising!  But that proved to be fool's gold. I got a return of the table header attributes mushed together with no spaces, not the player card info above, I needed to investigate a bit more. When seeing that all the <tr class> were alternating between 'odd' & 'even', each with an idividual players info I realized I had to get creative:
	
 ```
 doc = Nokogiri::HTML(open(BASE_URL))
 doc.css("tr.even, tr.odd").each do |details|
 ```
			
In a pure shot in the dark move in which I had no idea what would happen, bingo! Apparently you can itterate through different selectors simultaneously! This saved me a bunch of time and frustration trying to figure out...you know what, at that point I'm not even sure what I would have had to figure out, and I dont wanna think about it either.  Point is it worked perfectly! Building the rest of my Scraper class was a relative piece of cake once I got control of the selectors and .css.
		
So the next step was going to be building my Card class. The purpose of this class is pretty straight forward: MUT is a card game, and you cant really have a card game unless you create cards! So I set up 2 ways to create cards: an initialize method to create a card from a hash of player info, but also created a method to create cards from an array of hashes, to better compliment how I configured my scraper class. Piece of cake!*
 *Except for all the unneccessary code I wrote in the Card class that basically gave me an array of the same players 3 times over.*
    	
Next up was the most daunting aspect for me, the CLI class. At this point in the day however I had a clear understanding of what I wanted to accomplsh and knew my struggles would be when I implemented my input conditionlas. Bussiness decision: Get the basics taken care of to make sure everything else is running smooth before the input. Returning an organized numbered list from the array of hashes was a bit challenging, but everything was pretty smooth once I started coding. A couple 'requires' here, a little bit of 'string.to_i' for math purposes there and BAM! Bedtime. 

   Well, on **Day 4** I began to realize I needed to start working on the other aspects of this project - mainly this blog post and the recorded video - and set out to get those rolling. So naturally, delays aplenty awaited me. By the time I got back to the actual project it took me about 45 minutes to diagnose a simple error that basically amounted to a missed 'do end' in one of my methods. Mentally fried just in time for input conditionals day... Progress came in small productive spurts, followed by several consecutive unproductive hours of blankly staring at the screen, my new norm apparently.     
	 The struggle of the day turned out not to be getting the correct card info to display or getting the 'invalid' message with a wrong number input...turned out my biggest problem was trying to resolve an annoying issue where if input == 'any letter' and not a number, it would return the last card in the array.  This error pulled double trouble duty in also blocking my exit message.  I won't bore you with the details of the 4 hour staring contest I had with my screen (spoiler alert: I eventually won!), let me just surmise the frustrating experience by saying 1. I hate Ruby math & 2. I was even more annoyed than usual because the eventual solution I discovered I tried several hours prior...missing a single .to_i in the process. I thought I had a ready to package project at the end of this process, but apparently was still mentally fried enough to see the issue I had with my exit message.
	 
**Day 5** Damn that exit message, what is it now? It surely has to be something complex and crazy, or at the very least I should juggle around the order of my conditionals to make sure Ruby is reading it as well as she can - she's snobby like that. 1 hour later,  I was half right - had to change the order of my conditionals so the exit command was read first, but something else was missing. Turns out my old nemesis from day 4 had come back, but this time in a different form. This time I had *too many* '.to_i's. Several facepalms later, my project was fully functional to the scope I aimed it to be for purposes of this project!  
	  
Something was still missing though, I had functioning code in my project that was probably good enough to pass and submit for review, but it was early in day 5 and I was still ready for a challenge. I wanted to develop a stronger, more complex environment to support my code. After briefly researching that I saw the fastest and easiest way to do what I wanted to do was actually to make a gem out of it and let the bundle command take care of most of that.
		
Man was I surprised by how effortless that process was. A simple terminal command, copy of code, follow the 'TODO's in the autogenerated README for personalization purposes and that was it.  Simple and concise. Best part about it? I'm done with my blog post too! 
	 
	 
	 
	

