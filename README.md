# Chess Stats

The goal of this web app is to provide people with a clean and easy to use interface for chess.com so that users can 
see what their best and worst games were, pull useful stats such as average game length, and overall learn more about
their chess game just by reading their stats. 

## Available Documentation

It seems like the kind people at chess.com have released an API for us to use, which is great because it's pretty
comprehensive. This API can be found [here](https://www.chess.com/news/view/published-data-api). What's even better is that some beautiful soul actually built a JavaScript [library](https://www.npmjs.com/package/chess-web-api#installation) that wraps around the official chess.com API, making it even easier to use. Usually we would have to make clunky HTTP requests to grab all the 
data that we're gonna use but now we can simply make a function call like `getPlayerStats(misna)` and grab all of Misna's beautiful data. Shoutout whichever nerd built this. 

The documentation is thorough for both the official API and the wrapper. I'll list all the interesting info here 
for convenience. 

### Basic Player Info

- `getPlayer(username, options, callback)`
    - Grabs info like player id, status (they pay premium or not), avatar, is streamer, etc. Useful for making app look official
- `getPlayerStats(username, options, callback)`
    - This is gonna be the most useful method for sure. This function pulls stats for all time settings, their raiting on lessons, puzzles, tactics, you name it. 
- `getPlayerMonthlyArchives(username, options, callback)`
    - This method will give us a list of URLs that link us 
    to a list of games played by that user for every month that is available. 
    
- `getPlayerCompleteMonthlyArchives(username, year, month, options, callback)`
    - This method will be hella useful when implementing our idea of assigning each player a play style. This method returns an array of URLs to a player's played games for a given month. Shows all moves and everything.
    - There is an option to download the data in PGN format, in which case we would use [this](https://www.chess.com/news/view/published-data-api#pubapi-endpoint-games-pgn) method to grab the data. 
- `getPlayerClubs(username, options, callback)`
    - Method returns all the clubs that a player is part of, could be useful down the line for something. 
- `getPlayerTournaments(username, options, callback)`
    - This one is hella interesting, we could see all the tournaments that a player was a part of or will be a part of and will be a part of. Could be useful game data. 
- `getTournament(urlID, options, callback)` 
    - Method can get us details about any given tournament. Pretty self explanatory 
- `getCountryPlayers(iso, options, callback)`
    - Grabs all the players from a given country. Could be dope to compare all countries and see who's on top. 
- `getStreamers(options, callback)`
    - Grabs all players that are registered chess.com streamers. 
- `getLeaderboards(options, callback)`
    - Grabs top 50 players for games, tactics, and lessons. Could be useful to compare stats to user. 
- `getTitledPlayers(titleAbbrev, options, callback)`
    - This method in particular is really cool. This will give us a list of players that are grandmasters, international masters, etc. 

## Decisions, decisions
Okay now here is the fun part. We have decide a number of things before we start building this thing. 
1. What language/framework do we use?
So most web apps are built using JavaScript/TypeScript since that shit dominates the web and is pretty similar to coding in C++ (OOP). 
However, we can theoretically build this app in whatever language we choose. Lowkey it's kinda up to you to decide what langauge you
want practice in/want to learn to choose what language/framework we use. I'll list a few here by language.

- JavaScript/TypeScript
    - Angular: Developed by Google, this framework is hella comprehensive. Never used it before but hella good to learn for web developers.
    - React: Developed by Facebook, this is one of the easier frameworks to use and is really good for building clean looking apps. I have
    some experience developing in React. 
    - Node.js: Super popular and super powerful. This would be a good choice to develop our app, but I don't have much experience using it. 
    - Next.js: Also super popular/powerful, also don't have much experience with it. Has no database out the box, so we'd have to implement that on our own. 
- Golang
    - Memory safe language if you care about security, but lowkey doesn't really matter with this project lol. This language gaining
    a lot of popularity in industry so if you wanna learn it we could choose Golang to program this thing. Would be a little bit of
    a learning curve though since I have little experience with it. 
    - Gin: Yeah the framework is named after the alcohol lmao. Between the name, the logo, and the language, I'd be down to use this
    just for the fuck of it ![Gin logo](https://raw.githubusercontent.com/gin-gonic/logo/master/color.png) 
- Ruby
    - No lie I don't know shit about this language. However, Ruby on Rails is one of the best frameworks to use for web programming I've
    heard, so it would be nice to learn a thing or two about programming in it
    - Ruby on Rails: Cool ass name and also is regarded as one of the best frameworks to use for web programming. Would be hella of a learning curve tho. Ruby is super similar to C++ though I've heard so maybe not too bad. 
- Python
    - Everybody loves this bitch. Mfs be eating steaks with snakes cause Python is so easy to code in. This would be a good choice if you
    wanna brush up on your python or if you just want something simple to code in. 
    - Django: So I actually built my senior project in Django. The framework is hella simple and the fact that it is in Python makes it 
    so much better. I wouldn't mind using this framework but I'd also be down for something new. 
- C#
    - If you want something most similar to C++ this is your language ig. Never coded in it but it's basically the same as C++. 
    - .NET: Very popular framework to code in, maybe a little difficult to learn since C# is a little more complex to code in than other
    languages on this list. Developed by Microsoft if that has any weight to you. 


This is non-exhaustive but these are basically all the languages/frameworks I'm down to work with. If I had any preference it would be Gin
because I'm tryna learn Golang, but honestly given that we are using an API wrapper written in javascript it might be best to go with
javascript/typescript and choose one of the many frameworks that they got over there.

2. Features?
Self explanatory, I'mma leave this blank for if you have any ideas that you tryna add and shit like that. 

-
-
-
-
-

3. Backend Choice?

So the way the internet works is that people pay bums at Amazon/Google/Microsoft/etc. to host their websites/apps on servers that eat up
hella fucking energy. Anyways global warming aside we need to choose who's hosting our badass app. Most of these choices are free up to an extent (until either our app requires more power due to how popular it's gonna be or we run out of database storage). After that it shouldn't more than like $50 a month given that our shit doesn't blow up. We don't have to make this decision now but just keep it in mind
for the future. I'll add more info later so that we make a mroe informed choice. 

- AWS
- Firebase
- Heroku
- Azure
- Google Cloud
