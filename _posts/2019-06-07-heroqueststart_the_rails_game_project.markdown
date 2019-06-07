---
layout: post
title:      "HeroQuestStart! The Rails Game Project"
date:       2019-06-07 18:37:13 +0000
permalink:  heroqueststart_the_rails_game_project
---


Seriously, worst game ever. It's only had like 4 days of development though, so don't judge too harshly, masterpieces take time. 

**Day 1** Project week Monday's are alwys the best aren't they? Now usually I have the weekend to prep and conceptualize and have an idea what I want to do.  Not this time.  For some reason ideas were few and far between, and I had a hard time getting excited, and it led to silly time wasting ideas, aka a programmer's dream. Although I'm sure a child support tracker or Sugar Daddy/Momma/Baby black book sim app would prove useful for some, my wife talked me out of it. THen I thought I wanted to do a simple manga review app, but that sounded soooo boring! I couldn't imagine working on it this project AND next project. Around 10pm, I decided to reimagine "The Sweet Life," (the Sugar app) into a more basic hero adventure sim, and began liking the idea. But whatever, it's bed time.

**Day 2** Firmly commited to this project, and more importantly excited about it, I ran through the first real day of programming. Ignoring the more intricate requirements of the project test (like the nested routing and scope method) I dove in head first and got Devise up and running, as well as the Simple Form gem, knocked out all my models (complete w/ tables & relationships), the basics of the controllers, and the views all down. I felt ridiculously productive and accomplished! 

**Day 3** Yea, about that. Remember those intricate parts of the project I was ignoring? Well, it turns out being a requirement meant I actually had to do them. So, first challenge was my nested resources, which to keep a 4 hour experience short, exposed the hell out of my controllers that I had to rewrite (but *did* provide a strong lesson on properly routing and what to call when dealing with nested resources at least). I keep it short because today was the day I also decided to rewrite my database for little reason other than it ***might*** have made some amount of negligble sense at some point. Minus another 2 hours. I did eventually get it all sorted out and was able to check off several of the tests, with nested resource being the chief among them. Today was a hell of a learning day.

**Day 4** So, today was  "Update hero stats after taking an adventure day." I hate that holiday. I basically spent all day figuring out a DRY way to write and overwrite 7 different attributes for 3 different models from a single page (Experience inidividual show page) in 3 actions(Select Hero, Bring Little Sister, and Go On Adventure):

Hero - :hp, :treasure, :total_xp, :incapacitated were to be updated to the CORRECT hero

Adventure: :little_sister (a boolean I set up for a user submittable attribute)

Experience: :little_sister from adventure above was to have a direct impact on the :hp_rating & :xp_rating of this class.

And these tasks were so slow to develop throuout the day I thought I wouldn't finish in time. But apparently the issue was a fairly basic one. You see, I thought I had tried everything to get the objects to interact and update, but reality was I barely tried anything. My old crush `self` had to come back into my life at an awkward time, and reeducate me on the basic's of how to call objects through associations correctly again so I could work on my models simutaneously in one place and get my math and updates done correctly. Once I got that out the way, after a long long pause of not checking anything off the spec.md, 60% of my remaining requirements came flying off in 30 minutes. A frustrating day ending on a high note,with  only my scope method & Omniauth left, both of which were completely ignored.

**Day 5** Well, I spent about 2 hours getting what I wanted my scope method to be (if a Hero :incapacitated == true he can't adventure) before I just said screw all that and settled on a simple ordering scope, Hero's with highest :hp will be displayed first on the her index page. 5 minutes, whatever haha. Next wa Omniauth, which working with Devise was actually extremely easy. Not sure if this will cause problems in the future, but my big hold up was whether or not I should of added `config/initializers/devise.rb'` to `'.gitignore'`. Not sure if it will cause problems down the road, but I was able to sign up and sign in using my Github account no problem, and thats all that matters to me at this point.

**Conclusion** in 4 days of coding, I built a game where you can only lose :hp, can still adventure with negative :hp, can't spend your :treasure on anything useful (like :hp!), and you have boat loads of xp with no ability to level up. This is by far the worst game I have ever played, but I should at least pass without much issue.


