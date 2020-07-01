# Welcome to Tamil Songs Corpus!
[![N|Solid](https://www.tamilpaa.com/images/tamilpaa-logo.png)](https://www.tamilpaa.com/)

**Tamil Songs Corpus** is the collection of Tamil songs that were collected from [tamilpaa.com](https://www.tamilpaa.com). There are near to 4217 Tamil songs, from 1004 movies. `tamil_songs_corpus.csv` consists of a raw of movie JSON objects. `tamil_songs_corpus_preprocessed_data.csv` consists of a raw of preprocessed songs collections. Also Scraping script Notebook `tamilpaa_Web_scraping.ipynb` was attached.

## Data: tamil_songs_corpus & tamil_songs_corpus_preprocessed_data

 `tamil_songs_corpus.csv` consists of a raw of movie JSON objects. Movie JSON object has `movie, year, music, actors, movie_url, movie_image, movie_name_tamil, movie_name_eng, list of movie_song object (song_title, song_url, song_music, song_lyrics, song_singers, song_fulllyrics).` `tamil_songs_corpus_preprocessed_data.csv` was a CSV file contains 4200+ flat data of songs with above flat features.

### Data: Movie JSON Object
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

## Config: Stopwords_ta & Synonyms 

**Stopwords_ta:** Use Stopwords When Indexing Content. Most written text has a lot of functional words, like `"ஒரு", "இது", "எனவே", or "என்பது" `which are important to the person reading the content as they help it flow cohesively, but aren't necessarily as important to someone searching the content of our site.

**Synonyms:** This feature helps in providing better user experience by identifying different usage for a word in the given data context. Solr ships with a filter factory called SynonymFilterFactory to achieve this functionality. Also, it provides a configuration file called synonyms. txt to add our synonyms for example, `ஹாரிஸ், ஹரிஸ், ௧ாரிஸ், ஹரிஷ்` or `அம்மா, தாய், அன்னை`.


## Sample queries

After you set up the solr environment and above Tamil songs corpus preprocessed data. you can test the below queries using SOLR REST API GUI.

 - would you like to search `நான்தான்டா இனிமேலு`  lyrics in data collection?

>  `song_fulllyrics: நான்தான்டா இனிமேலு`

 - Search for either the phrase "சூரியா நயன்தாரா" in the `actors` field AND the phrase `"ஹாரிஸ் ஜெயராஜ்"` in the `song_music` field or the word `"ஹாரிஸ் ஜெயராஜ்"` in the `song_lyrics` field.

> `(actors: "சூரியா நயன்தாரா" AND song_music:"ஹாரிஸ் ஜெயராஜ்") OR song_lyrics:"வாலி"`

- Search for song "அனிருத் ரவிச்சந்தர்" in `music` field. and not "தனுஷ்" in the `actors` field.

>`music:"அனிருத் ரவிச்சந்தர்" -actors:"தனுஷ்"`

- would you like to search for a song that was released between 2000 to 2010?
>`year:[2000 TO 2010]`
- would you like to search for a top 10 rating songs?
>`sort: song_rating desc, start: 0,  rows: 10`

- If you have remembered only part of the name you can use Wildcard matching.  any name that starts with `"இளைய"` in the song_music field.
>`song_music:இளைய*`

- If you have remembered only `"சத்தியமா தேவயே"` but you forget the middle words `நீ எனக்கு` from the song `"சத்தியமா நீ எனக்கு தேவயே"` for that you can use Proximity matching.
>`song_fulllyrics: "சத்தியமா தேவயே"~3`
- Query-time boosts allow one to specify which terms/clauses are "more important". The higher the boost factor, the more relevant the term will be, and therefore the higher the corresponding document scores. you like to search a word containing in the movie was more weight.
>`(movie: "ஆசை ஆசையாய்")^1.5 OR song_fulllyrics: "ஆசை ஆசையாய்"`


 - In some case, ஆர்யன் also called like ஆரியன். Users don't know about documentation. So if we add those words in `synonyms.txt` when we search any of one we can get the of the results.
>`music: ஆரியன்`

 - `"எனவும்", "ஒரு"` aren't necessarily as important to someone searching the content of our site. if we add those words in `stopwords_ta.txt` those words are not affecting the searching results.
>`movie_name_tamil: கூர்க்கா எனவும்`
