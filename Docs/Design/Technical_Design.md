# Educational project for book logging

## What problems am I trying to solve

I want to keep track of the novels I read, as well as some statistics on those 
books (length, how long it took to read, general review/thoughts at point of 
finishing the book, how much the book cost me), and collate that into useful 
data. This has to be accessible from mobile as that’ll make it easier to use 
when I first finish a book when reading in bed.

## What skills am I trying to develop?
* Database management and interaction
* I want to get more experience navigating and understanding a larger code base 
as I have never created anything larger than a single file. (Not including 
config management or dotfiles)
* I want to learn how to host a project from a raspberry pi
    * This could also potentially lead to learning about containerisation
    * I'd also want to learn about network tunnelling etc to make this tool 
    accessible outside of my local network
* I want to learn about setting up CI via pre-commit on GitHub

## What is the current process
I currently use a google sheet that's basically a list of books read plus their
authors

#### Pros
* Easily accessible from mobile or off-site
* Simple and easy to update when I finish a new book

#### Cons
* I don't track as much as I'd like to (costs, thoughts, reading 
    motivation eg fast/slow)
* Every time I want to know how many books I’ve read, I have to manually count 
them up, which is tedious.

## Project Scope
The MVP would be able to read and write from a database I’d build myself. With 
the right tools, it could at least output numerical stats on the books I’d 
read. It would have a simple front end that would only require the user to 
fill in some text boxes to populate the database. It would be accessible on my
local network from my mobile as it’s hosted on a raspberry pi.

Future features would include a fully functional UI with relevant drop downs 
etc. Potentially, I could link my amazon account so that this would see the 
latest activity in my kindle account (I don’t know what kind of API Amazon 
offers on this front at this time) so that I can just say “I’ve finished the 
book” with one click and it would populate some of the fields. At any time, I 
could press a button and get back a stats page telling me about my year so far 
(akin to something like Spotify’s year in review). There are options to keep 
and show a “to be read” list of books the user wants to read in the future, 
potentially with a notes section attached for personal reminders etc. 

Long term, this could be expanded to allow for multiple users with a login 
screen and individual databases and I can host this on a cloud service such as 
AWS and open to other users. This would also require a more polished front end 
than I’m imagining right now, and a focus on password security as well.

## Alternatives

The best known alternative right now is Goodreads, which is infamous for 
having awful website UI and is better designed as a ‘book-reading social media’
for sharing reviews with other people. There are also smaller tools for things 
like this, but I’m honestly not interested in trying them out as that defeats 
the purpose of developing new skills. They’re also only known by those that 
seek them out - prior to this, I’d not heard of any alternatives to Goodreads 
before. [See here](https://www.reddit.com/r/books/comments/nwm2h2/alternatives_to_goodreads_in_2021/)

## Solution
* We need a front end built with python and flask to provide the user with a 
way to input data about the books they’ve read, or to view the data they’ve
previously entered in an easy-to-read method.
* We need a database to store various information about the books that the user 
has read, properly designed with modular tables for easier expansion in the 
future. This should include:
    * Title
    * Authors
    * Release date
    * Purchase price (User specified - to allow for sales or rereads)
    * Reading start date (And a way for this to be marked as 'the day after the 
    previous book was finished)
    * Reading finish date
    * Book length (in pages)
* We need a way of taking this data and exporting it in a pleasing manner so 
that it can be shared on social media. 
    * Something akin to Spotify’s year in review - at first this would be 
    triggered by the user, but later on can be expanded on to include social 
    media posts (“I just finished reading X book in Y days” tweets)
* We need a way to connectr to the Amazon database so a user can automatically
pull in data about a book they've recently bought/read from amazon
    * Potentially we can use the Amazon Product Advertising API for this. Or 
    alternatively, look outside of Amazon

