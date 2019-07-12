---
layout: post
title:      "Rails & Javascript Project"
date:       2019-07-12 17:55:47 +0000
permalink:  rails_and_javascript_project
---


Well, what is there to really say about this project? It was probably the easiest project to date imo - or perhaps I'm just developing into an awesome programmer! The main purpose of this project was to take our Rails app from the previous project and add some javascript to add on overlay of JS ontop of it that can navigate your app without page refreshes. When compared to both our Ruby and Sinatra projects, this project had some very basic requirements and we were'nt responsible for creating an entire application, merely working in a few files - fitting as we had only been tackling javascript for about a month at this point.

**Day 1:** There are a couple of things you should do before diving right into writing Javascript and I will cover them to the best of my ability (credit to my wife Catherine whose  [blog](https://catherinism.github.io/rails_with_js_project_guide?fbclid=IwAR0Kkars38icGEXArQfUdCDs-6moMRZOzeOdLVPegNq8mhb3VGx8Py9SZ_o)help me write mine.

**1) Duplicate your rails project** 

This is the cleanest option, create a new repository on your github *name_of_previous_project-js* will more than suffice. This will ensure you keep a clean operational copy in case you get overwhelmed and try to do too much. When creating a new repo on Github, select the option to import an old repo and paste your projects URL into the form.

Alternativley you can always create or new project, but why waste the time when we only have a week to get this done?

**2) Add the necessary gems to your Gemfile**

Step 1:

`
gem 'jquery-rails'
gem 'active_model_serializers'
`

Step 2

Run `bundle install` in your terminal.

Step 3(Optional...or maybe not)

The turbolinks gem hasn't really kept up well with the updates pertaining to adding JS in Rails 5 or higher, so it may be in your best interest to remove it completely from your project.  

Step 1

Delete the`gem 'turbolinks'` from your gemfile (dont forget to run 'bundle' in your terminal after this).

Step 2 

From your `application.js` file remove the line

```
//= require turbolinks
``` 
This should be sufficient and prevent any issues you may encounter while adding JS to your Rails project.

**3) Set requirements in *application.js* file** 

Each project may have different requirements based on gems and intended functionality but the main rquirements you should have are:

```
//= require jquery
//= require rails-ujs```(for use with Rails 5<) ```//= require jquery-ujs``` may suffice for earlier versions of Rails.
```
//= require activestorage
//= require_tree .
```

**4) Add Serializers**

Serializers are basically the go betweens for Rails/JS interactions. They allow you to tell JS what your intended relationships are between each class and give permissions for what data you want to allow through. These are fairly straightforward and simple, a typical serializer may look something like this:

```
class ExperienceSerializer < ActiveModel::Serializer
  attributes :id, :xp, :hp_rating, :treasure_rating, :title, :healing

  has_many :heros
  has_many :adventures
  belongs_to :user
end
```

Note there is no need (at least in my experience) to specify a has_many through relationship as ```'active_model_serializers'``` already does that for you!

**5) Render JSON**

Decide what index and show pages you want to work on, and add a simple `respond_to` method to them in there respective controllers. For expample:

***app/controllers/heros.rb***
```
def index
    @heros = Hero.all.seniority
    respond_to do |f|
        f.html {render :index}
        f.json {render json: current_user.heros}
      end
  end
```
 
 
**6) Simplify your routes (Optional)**

In the previous rails project, we were required to have at least one nested routes to demonstrate we understood the concept. Well that requirement is gone, and I recommend taking advantage of it since learning how to call nested routes in JS will probably take more time than editing your current routes in your project. And time is precious...

After taking all these steps you can start adding code in your JS file!

**Pro Tip:** If you used rails generator for your models, you will have a `.coffee` file already there for you. ***Delete or rename this file to .js before you start working, as your app will read from this file before your .js***

**Resources**

I wish to share a couple of very informative videos that helped me tremendously in this project and hope they help you as well:

[Index & Show Requirement](https://www.youtube.com/watch?v=oHPM0ekV7zQ)

[Form Subbmission Requirement](https://www.youtube.com/watch?v=Yd0nH9CWWfo&amp=&feature=youtu.be)

These two videos will basically cover all of the project requirements and, if you're like me in any way, teach you the value of having organized and easily accessible html classes and id's. 

Happy coding!



