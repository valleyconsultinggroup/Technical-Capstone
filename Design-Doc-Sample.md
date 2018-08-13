# Spotify Web App

Author: John Appleseed

Github Username: john-appleseed

Landing Site: www.github.com/valleyconsultinggroup/spotify-web-app

### Revision History

| Date        | Comments      | Author    | Approved By |
| ----------- | ------------- | --------- | ----------- |
| 08/12/2018  | Initial Draft | John Appleseed | John Yang |

### Overview

Every host knows that one of the most important yet toughest parts of throwing an awesome party is putting together a solid playlist of bangers with music that everybody likes. Personally, I, John Appleseed, love to throw parties at the M.E.T., but there have been one too many times where people leave because the music isn't something they can dance or sing along with. In a situation like this, it would be very helpful if there was a tool to help create a playlist with music that everybody likes.

Introducing, the Music Mixer App powered by Spotify! Nowadays, most college students have a Spotify account that is essentially a compilation of their taste in music. For this project, I want to build a web app that can discover people's musical tastes through their Spotify accounts, then auto-generate a playlist that features the best, most commonly liked music from everybody's interests.

### Purpose

The Spotify Mixer app is capable of automatically creating playlists for groups and parties based off of everyone’s music preferences on Spotify. The capabilities of the app are twofold. First, the app is able to take a user's Spotify account and identify their musical tastes categorized by genre, i.e. Hip-Hop, Jazz, Rap, etc. The app prioritizes songs that are liked by a greater proportion of the group. The app may also be able to figure out which specific songs are common.

Second, using these categories, the app identifies and discovers songs which fit the given descriptions. For example, if Tejas and Viraj both appear to like country music, then the top, latest hits in the Country genre can be retrieved from Spotify. In addition, if Tejas and Viraj both have "I'm a Barbie Girl" in their playlists, the app should be able to identify this overlap and prioritize this song within the playlist.

### Work Requirements

| # | Description   | Hours Estimated | Completion Date | Miscellaneous |
| - | ------------- | --------------- | --------------- | ------------- |
| 1 | Set up Spotify Developer Accounts; get Developer Tokens to access REST API | 1 Hour | 8/12/2018 |  |
| 2 | Create/find a basic web app skeleton. | 1 Hour | 8/19/2018 | Take some time to learn some HTML, CSS, and Javascript |
| 3 | Be able to connect a single Spotify account to Mixer (via OAuth endpoint) | 2 Hours | 8/23/2018 |  |
| 4 | Retrieve a single user’s data (playlists and songs) through the REST API endpoint | 2 Hours | 9/06/2018 |  |
| 5 | Enable multiple users to login, and enable Mixer to collect and store their data in the browser’s LocalStorage (ideally Chrome)| 5-6 Hours | 9/13/2018 |  |
| 6 | Implement functionality to create a playlist based off of user data stored in LocalStorage. | 5-6 Hours | 10/16/2018 | actual implementation can vary, start with all songs that X% of users have in common, |
| 7 | Make the front-end sexy (time for some CSS… or maybe we’ll find a template) | 5-6 Hours | 10/20/2018 |  |
| 8 | Host the app on a real website | 2-3 Hours | 11/04/2018 |  |

### Technical Stack

This web app primarily works with the [Spotify Web API](https://developer.spotify.com/documentation/web-api/). The API is modeled after fundamental REST principles (i.e. POST, GET, PUT requests). The Web API requires one to make an account, and all URL requests must have an authentication token attached to them in order to go through successfully. The Web API exposes several endpoints with unique paths to access data from both user accounts and Spotify's general music data. Using simple GET requests, the app is able to identify users and retrieve their playlists and music inclinations. Through POST requests, the app is able to submit musical categories or songs to create a playlist. All responses from the Web API are in the form of JSON metadata that is parsed within the app itself.

The app itself hosts the UI and logic behind displaying and configuring playlists is implemented within the app itself. In terms of object oriented programming principles, there are several classes at play. The "music" class is used to model different categories of music along with their popularity. A "user" class keeps track of which playlists and musical tastes are associated with which user ID. Last but not least, the "playlist" class helps track what kinds of songs and music categories are being sent to create auto-generated playlist. All of this logic is written in Python and hosted on a local Flask server. The Jinja2 templating library along with basic HTML, CSS, and Javascript are behind the front end elements of the website.

### User Interface Design + Project Demonstrations

(Theoretically would be filled with screenshots + links to demo videos of the mock app + a diagram walkthrough of how user interactions and app logic interact)

### Outstanding Issues & Further Considerations

**Add functionality to allow each user to select specific playlists they want to contribute**

Each Spotify user has multiple playlists. If they're going to a party and registering their Spotify username, they should be allowed to pick which playlists they would like to have scraped and identified for musical tastes. For instance, if Aakash and Emily are going to a party, they would probably prefer to contribute their Pop playlists rather than their K-pop and Goth selections :) The Spotify API should provide identification for the playlists that a user has both created or followed. Within the app, there could be an additional step that allows users to select, confirm, and submit the playlists they prefer. This step should probably take 6-10 Hours.

References
- https://developer.spotify.com/documentation/web-api/reference/playlists/

**Rank songs by collective popularity and use that information to order the songs in the playlists**

The app, in its current state, identifies popularity based on a threshold. In this case, if 70% of registered users have playlists with a specific genre, it is considered popular (i.e. if 7 out of 10 registered users have playlists with the "EDM" tag, then EDM is considered popular). In the current model, the app does not distinguish between the popularity of songs that have surpassed that threshold. Implementation-wise, I would need to create a new object that models a category and its popularity score. By creating this association, there would a metric to reorder songs after generating the playlist. Putting this into place would most likely take 6-10 hours.

References
- https://stackoverflow.com/questions/11128086/simple-popularity-algorithm

**Enable multiple users to access/use Mixer remotely**

Right now, the logic behind ranking categories and generating playlists is abstracted away within the Flask backend, not available for anyone to view except for the owner (in this case, me!). One way to make this happen is to create a data model of users and introduce the ability to make accounts. when a user logs in, they can register for specific parties and organize specific playlists for specific parties. This task would largely be an extension of the backend's capabilities. Although it's a straightforward challenge, it will take a while to implement it from end to end.

References
- http://flask-sqlalchemy.pocoo.org/2.3/models/
