# MeloFi: Software Requirements Specification (SRS)

## 1. Project Overview

**Melofi** is a music streaming platform. This SRS document tells the specific requirements for the platform.
The system will consist of a React Web APP , a Kotlin mobile app , and a Flask Backend.

## 2. Goals 

We will deliever a functional system (Web based, Mobile, Backend) that handles authentication, track playback , and basic playlist creations .

## 3. Target Users 

Casual users : Needs to log in, click one to play song from a list of songs.
Specific users : Needs to log in, creates and playlist with some songs in it from main track lists.

## 4. System features (Functional Requirements)

### 4.1 Authentication 

When a user comes, they should sign up with a email and a password .

Flow of control:

* User provides email and password
* backend hashes the password and new user is added to user table 
* then continues with the app .

* For existing user , logging with email and password .
* Backend checks credentials 
* then continues with the app. 

### 4.2 Music and Player 

User story : wants to see available songs on the home page .

Flow:
* When app loads, it fetches a list of songs with an api from backend 
* Songs are displayed in a grid/list with song_name , author , album

User story: User clicking a song to play it .

Flow:
* clicking on song card loads its audio url into the player .
* Song's title/artist appear in the player.
* Audio begins playing 
* There's a play/pause button for controlling song play .

User Story : User want to see a persistent player that shows song progress.

Flow:
* A player component at bottom .
* It shows the current songs title and artist with play/pause button and progress bar that updates in real time.

### 4.3 Playlists 

User Story : When User wants to create a new playlist 

Flow:
* User clicks "New Playlist" button .
* provide a name in pop up dialogue box .
* the app makes an POST request to api/playlist with userid .
* A new playlist appears in the user's list.

User Story: To add a song to playlist.

Flow:
* user finds a song on homepage 
* user clicks on 3 dot button , where theres an option to add the song to playlist
* a list of their playlist appears with checkbox .
* When user clicks them , it makes a POST request from /api/playlist/<playlist_id>/<song_id> 

User Story : User want to see all songs in the playlist they created .

Flow:
* User navigates to My playlist tab/page , where list of their playlists are available.
* When clicking on playlist , songs on that playlist can be seen on another page.
* In that page which lists all available songs in the playlist .

### 4.4 Search 

User Story: user wants to search for a track by its title.

Flow:
* A search bar is available .
* As user types the search bar , the songs on the home page gets filtered by the name matching query . 

## 5. Key Screens 

* Login Screen (email, password, SignUp link)
* SignUp screen (email, password , Login Link)
* Home Screen (showing the grid of all tracks and searchbar at top with 3 dots to navigate to playlist and user profile)
* Playlist screen (Shows list of user's playlist and "+" button to create a new playlist)
* Playlist detailed screen (shows the songs in a playlist)
* Persistant player (A component, not a screen floating at bottom of the screen.)

## 6. Tech Stack 

* Backend: Flask , using flask-sqlalchemy for DB .
* Database : sqlite 

Core Data Model :
* User : userid ,email, passwordhash 
* Songs : songid , song name , song artist 
* Playlist : playlist id , creator user id 
* Playlist Tracks : id , playlist id , song id 

