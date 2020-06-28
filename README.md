# Tamil Songs Corpus

[![N|Solid](https://www.tamilpaa.com/images/tamilpaa-logo.png)](https://www.tamilpaa.com/)

There are near to 4217 Tamil songs, from 1004 movies. `tamil_songs_corpus.csv` consists of an raw of movie JSON objects. Songs are Scriped from <https://www.tamilpaa.com/> Also Scraping script Notebook `tamilpaa_Web_scraping.ipynb` was attached. Movie JSON object has below features.
  - movie
  - year
  - music
  - actors 
  - movie_url 
  - movie_image 
  - movie_name_tamil 
  - movie_name_eng 
  - movie_song 
    --song_title
    --song_url
    --song_music
    --song_lyrics
    --song_singers
    --song_fulllyrics 

# Movie JSON Object
```
{ 'movie': 'Movie_Name_English (Movie_Name_Tamil)',
  'year': 'Year',
   'music': 'Music',
   'actors': 'Comma Separator Actors Names',
   'movie_url': 'Movie_URL',
   'movie_image': 'Image_URL',
   'movie_name_tamil': 'Movie_Name_Tamil',
   'movie_name_eng': 'Movie_Name_English',
   'movie_song': [
        { 'song_title': 'Song_Title_English (Song_Title_Tamil)',
          'song_url': 'Song_URL', 
          'song_music': 'Song_music',
          'song_lyrics': 'Song_lyrics',
          'song_singers': 'Song_singers',
          'song_fulllyrics': 'Full_Lyrics_In_Tamil'},
        { 'song_title': 'Song_Title_English (Song_Title_Tamil)',
          'song_url': 'Song_URL', 
          'song_music': 'Song_music',
          'song_lyrics': 'Song_lyrics',
          'song_singers': 'Song_singers',
          'song_fulllyrics': 'Full_Lyrics_In_Tamil'},
        { 'song_title': 'Song_Title_English (Song_Title_Tamil)',
          'song_url': 'Song_URL', 
          'song_music': 'Song_music',
          'song_lyrics': 'Song_lyrics',
          'song_singers': 'Song_singers',
          'song_fulllyrics': 'Full_Lyrics_In_Tamil'}
       ]
 }
 ```


