```python
import pandas as pd
import numpy as np

```


```python
movies=pd.read_csv("C:/Users/zoaah/Downloads/archive/tmdb_5000_movies.csv")
credits=pd.read_csv("C:/Users/zoaah/Downloads/archive/tmdb_5000_credits.csv")

```


```python
movies.head(3)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget</th>
      <th>genres</th>
      <th>homepage</th>
      <th>id</th>
      <th>keywords</th>
      <th>original_language</th>
      <th>original_title</th>
      <th>overview</th>
      <th>popularity</th>
      <th>production_companies</th>
      <th>production_countries</th>
      <th>release_date</th>
      <th>revenue</th>
      <th>runtime</th>
      <th>spoken_languages</th>
      <th>status</th>
      <th>tagline</th>
      <th>title</th>
      <th>vote_average</th>
      <th>vote_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>237000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.avatarmovie.com/</td>
      <td>19995</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>en</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>150.437577</td>
      <td>[{"name": "Ingenious Film Partners", "id": 289...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2009-12-10</td>
      <td>2787965087</td>
      <td>162.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}, {"iso...</td>
      <td>Released</td>
      <td>Enter the World of Pandora.</td>
      <td>Avatar</td>
      <td>7.2</td>
      <td>11800</td>
    </tr>
    <tr>
      <th>1</th>
      <td>300000000</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>http://disney.go.com/disneypictures/pirates/</td>
      <td>285</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>en</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>139.082615</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}, {"...</td>
      <td>[{"iso_3166_1": "US", "name": "United States o...</td>
      <td>2007-05-19</td>
      <td>961000000</td>
      <td>169.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>At the end of the world, the adventure begins.</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>6.9</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>245000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.sonypictures.com/movies/spectre/</td>
      <td>206647</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>en</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>107.376788</td>
      <td>[{"name": "Columbia Pictures", "id": 5}, {"nam...</td>
      <td>[{"iso_3166_1": "GB", "name": "United Kingdom"...</td>
      <td>2015-10-26</td>
      <td>880674609</td>
      <td>148.0</td>
      <td>[{"iso_639_1": "fr", "name": "Fran\u00e7ais"},...</td>
      <td>Released</td>
      <td>A Plan No One Escapes</td>
      <td>Spectre</td>
      <td>6.3</td>
      <td>4466</td>
    </tr>
  </tbody>
</table>
</div>




```python
credits.head(1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
credits.head(1)['cast']
```




    0    [{"cast_id": 242, "character": "Jake Sully", "...
    Name: cast, dtype: object




```python
credits.head(1)['cast'].values
```




    array(['[{"cast_id": 242, "character": "Jake Sully", "credit_id": "5602a8a7c3a3685532001c9a", "gender": 2, "id": 65731, "name": "Sam Worthington", "order": 0}, {"cast_id": 3, "character": "Neytiri", "credit_id": "52fe48009251416c750ac9cb", "gender": 1, "id": 8691, "name": "Zoe Saldana", "order": 1}, {"cast_id": 25, "character": "Dr. Grace Augustine", "credit_id": "52fe48009251416c750aca39", "gender": 1, "id": 10205, "name": "Sigourney Weaver", "order": 2}, {"cast_id": 4, "character": "Col. Quaritch", "credit_id": "52fe48009251416c750ac9cf", "gender": 2, "id": 32747, "name": "Stephen Lang", "order": 3}, {"cast_id": 5, "character": "Trudy Chacon", "credit_id": "52fe48009251416c750ac9d3", "gender": 1, "id": 17647, "name": "Michelle Rodriguez", "order": 4}, {"cast_id": 8, "character": "Selfridge", "credit_id": "52fe48009251416c750ac9e1", "gender": 2, "id": 1771, "name": "Giovanni Ribisi", "order": 5}, {"cast_id": 7, "character": "Norm Spellman", "credit_id": "52fe48009251416c750ac9dd", "gender": 2, "id": 59231, "name": "Joel David Moore", "order": 6}, {"cast_id": 9, "character": "Moat", "credit_id": "52fe48009251416c750ac9e5", "gender": 1, "id": 30485, "name": "CCH Pounder", "order": 7}, {"cast_id": 11, "character": "Eytukan", "credit_id": "52fe48009251416c750ac9ed", "gender": 2, "id": 15853, "name": "Wes Studi", "order": 8}, {"cast_id": 10, "character": "Tsu\'Tey", "credit_id": "52fe48009251416c750ac9e9", "gender": 2, "id": 10964, "name": "Laz Alonso", "order": 9}, {"cast_id": 12, "character": "Dr. Max Patel", "credit_id": "52fe48009251416c750ac9f1", "gender": 2, "id": 95697, "name": "Dileep Rao", "order": 10}, {"cast_id": 13, "character": "Lyle Wainfleet", "credit_id": "52fe48009251416c750ac9f5", "gender": 2, "id": 98215, "name": "Matt Gerald", "order": 11}, {"cast_id": 32, "character": "Private Fike", "credit_id": "52fe48009251416c750aca5b", "gender": 2, "id": 154153, "name": "Sean Anthony Moran", "order": 12}, {"cast_id": 33, "character": "Cryo Vault Med Tech", "credit_id": "52fe48009251416c750aca5f", "gender": 2, "id": 397312, "name": "Jason Whyte", "order": 13}, {"cast_id": 34, "character": "Venture Star Crew Chief", "credit_id": "52fe48009251416c750aca63", "gender": 2, "id": 42317, "name": "Scott Lawrence", "order": 14}, {"cast_id": 35, "character": "Lock Up Trooper", "credit_id": "52fe48009251416c750aca67", "gender": 2, "id": 986734, "name": "Kelly Kilgour", "order": 15}, {"cast_id": 36, "character": "Shuttle Pilot", "credit_id": "52fe48009251416c750aca6b", "gender": 0, "id": 1207227, "name": "James Patrick Pitt", "order": 16}, {"cast_id": 37, "character": "Shuttle Co-Pilot", "credit_id": "52fe48009251416c750aca6f", "gender": 0, "id": 1180936, "name": "Sean Patrick Murphy", "order": 17}, {"cast_id": 38, "character": "Shuttle Crew Chief", "credit_id": "52fe48009251416c750aca73", "gender": 2, "id": 1019578, "name": "Peter Dillon", "order": 18}, {"cast_id": 39, "character": "Tractor Operator / Troupe", "credit_id": "52fe48009251416c750aca77", "gender": 0, "id": 91443, "name": "Kevin Dorman", "order": 19}, {"cast_id": 40, "character": "Dragon Gunship Pilot", "credit_id": "52fe48009251416c750aca7b", "gender": 2, "id": 173391, "name": "Kelson Henderson", "order": 20}, {"cast_id": 41, "character": "Dragon Gunship Gunner", "credit_id": "52fe48009251416c750aca7f", "gender": 0, "id": 1207236, "name": "David Van Horn", "order": 21}, {"cast_id": 42, "character": "Dragon Gunship Navigator", "credit_id": "52fe48009251416c750aca83", "gender": 0, "id": 215913, "name": "Jacob Tomuri", "order": 22}, {"cast_id": 43, "character": "Suit #1", "credit_id": "52fe48009251416c750aca87", "gender": 0, "id": 143206, "name": "Michael Blain-Rozgay", "order": 23}, {"cast_id": 44, "character": "Suit #2", "credit_id": "52fe48009251416c750aca8b", "gender": 2, "id": 169676, "name": "Jon Curry", "order": 24}, {"cast_id": 46, "character": "Ambient Room Tech", "credit_id": "52fe48009251416c750aca8f", "gender": 0, "id": 1048610, "name": "Luke Hawker", "order": 25}, {"cast_id": 47, "character": "Ambient Room Tech / Troupe", "credit_id": "52fe48009251416c750aca93", "gender": 0, "id": 42288, "name": "Woody Schultz", "order": 26}, {"cast_id": 48, "character": "Horse Clan Leader", "credit_id": "52fe48009251416c750aca97", "gender": 2, "id": 68278, "name": "Peter Mensah", "order": 27}, {"cast_id": 49, "character": "Link Room Tech", "credit_id": "52fe48009251416c750aca9b", "gender": 0, "id": 1207247, "name": "Sonia Yee", "order": 28}, {"cast_id": 50, "character": "Basketball Avatar / Troupe", "credit_id": "52fe48009251416c750aca9f", "gender": 1, "id": 1207248, "name": "Jahnel Curfman", "order": 29}, {"cast_id": 51, "character": "Basketball Avatar", "credit_id": "52fe48009251416c750acaa3", "gender": 0, "id": 89714, "name": "Ilram Choi", "order": 30}, {"cast_id": 52, "character": "Na\'vi Child", "credit_id": "52fe48009251416c750acaa7", "gender": 0, "id": 1207249, "name": "Kyla Warren", "order": 31}, {"cast_id": 53, "character": "Troupe", "credit_id": "52fe48009251416c750acaab", "gender": 0, "id": 1207250, "name": "Lisa Roumain", "order": 32}, {"cast_id": 54, "character": "Troupe", "credit_id": "52fe48009251416c750acaaf", "gender": 1, "id": 83105, "name": "Debra Wilson", "order": 33}, {"cast_id": 57, "character": "Troupe", "credit_id": "52fe48009251416c750acabb", "gender": 0, "id": 1207253, "name": "Chris Mala", "order": 34}, {"cast_id": 55, "character": "Troupe", "credit_id": "52fe48009251416c750acab3", "gender": 0, "id": 1207251, "name": "Taylor Kibby", "order": 35}, {"cast_id": 56, "character": "Troupe", "credit_id": "52fe48009251416c750acab7", "gender": 0, "id": 1207252, "name": "Jodie Landau", "order": 36}, {"cast_id": 58, "character": "Troupe", "credit_id": "52fe48009251416c750acabf", "gender": 0, "id": 1207254, "name": "Julie Lamm", "order": 37}, {"cast_id": 59, "character": "Troupe", "credit_id": "52fe48009251416c750acac3", "gender": 0, "id": 1207257, "name": "Cullen B. Madden", "order": 38}, {"cast_id": 60, "character": "Troupe", "credit_id": "52fe48009251416c750acac7", "gender": 0, "id": 1207259, "name": "Joseph Brady Madden", "order": 39}, {"cast_id": 61, "character": "Troupe", "credit_id": "52fe48009251416c750acacb", "gender": 0, "id": 1207262, "name": "Frankie Torres", "order": 40}, {"cast_id": 62, "character": "Troupe", "credit_id": "52fe48009251416c750acacf", "gender": 1, "id": 1158600, "name": "Austin Wilson", "order": 41}, {"cast_id": 63, "character": "Troupe", "credit_id": "52fe48019251416c750acad3", "gender": 1, "id": 983705, "name": "Sara Wilson", "order": 42}, {"cast_id": 64, "character": "Troupe", "credit_id": "52fe48019251416c750acad7", "gender": 0, "id": 1207263, "name": "Tamica Washington-Miller", "order": 43}, {"cast_id": 65, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acadb", "gender": 1, "id": 1145098, "name": "Lucy Briant", "order": 44}, {"cast_id": 66, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acadf", "gender": 2, "id": 33305, "name": "Nathan Meister", "order": 45}, {"cast_id": 67, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acae3", "gender": 0, "id": 1207264, "name": "Gerry Blair", "order": 46}, {"cast_id": 68, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acae7", "gender": 2, "id": 33311, "name": "Matthew Chamberlain", "order": 47}, {"cast_id": 69, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acaeb", "gender": 0, "id": 1207265, "name": "Paul Yates", "order": 48}, {"cast_id": 70, "character": "Op Center Duty Officer", "credit_id": "52fe48019251416c750acaef", "gender": 0, "id": 1207266, "name": "Wray Wilson", "order": 49}, {"cast_id": 71, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acaf3", "gender": 2, "id": 54492, "name": "James Gaylyn", "order": 50}, {"cast_id": 72, "character": "Dancer", "credit_id": "52fe48019251416c750acaf7", "gender": 0, "id": 1207267, "name": "Melvin Leno Clark III", "order": 51}, {"cast_id": 73, "character": "Dancer", "credit_id": "52fe48019251416c750acafb", "gender": 0, "id": 1207268, "name": "Carvon Futrell", "order": 52}, {"cast_id": 74, "character": "Dancer", "credit_id": "52fe48019251416c750acaff", "gender": 0, "id": 1207269, "name": "Brandon Jelkes", "order": 53}, {"cast_id": 75, "character": "Dancer", "credit_id": "52fe48019251416c750acb03", "gender": 0, "id": 1207270, "name": "Micah Moch", "order": 54}, {"cast_id": 76, "character": "Dancer", "credit_id": "52fe48019251416c750acb07", "gender": 0, "id": 1207271, "name": "Hanniyah Muhammad", "order": 55}, {"cast_id": 77, "character": "Dancer", "credit_id": "52fe48019251416c750acb0b", "gender": 0, "id": 1207272, "name": "Christopher Nolen", "order": 56}, {"cast_id": 78, "character": "Dancer", "credit_id": "52fe48019251416c750acb0f", "gender": 0, "id": 1207273, "name": "Christa Oliver", "order": 57}, {"cast_id": 79, "character": "Dancer", "credit_id": "52fe48019251416c750acb13", "gender": 0, "id": 1207274, "name": "April Marie Thomas", "order": 58}, {"cast_id": 80, "character": "Dancer", "credit_id": "52fe48019251416c750acb17", "gender": 0, "id": 1207275, "name": "Bravita A. Threatt", "order": 59}, {"cast_id": 81, "character": "Mining Chief (uncredited)", "credit_id": "52fe48019251416c750acb1b", "gender": 0, "id": 1207276, "name": "Colin Bleasdale", "order": 60}, {"cast_id": 82, "character": "Veteran Miner (uncredited)", "credit_id": "52fe48019251416c750acb1f", "gender": 0, "id": 107969, "name": "Mike Bodnar", "order": 61}, {"cast_id": 83, "character": "Richard (uncredited)", "credit_id": "52fe48019251416c750acb23", "gender": 0, "id": 1207278, "name": "Matt Clayton", "order": 62}, {"cast_id": 84, "character": "Nav\'i (uncredited)", "credit_id": "52fe48019251416c750acb27", "gender": 1, "id": 147898, "name": "Nicole Dionne", "order": 63}, {"cast_id": 85, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb2b", "gender": 0, "id": 1207280, "name": "Jamie Harrison", "order": 64}, {"cast_id": 86, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb2f", "gender": 0, "id": 1207281, "name": "Allan Henry", "order": 65}, {"cast_id": 87, "character": "Ground Technician (uncredited)", "credit_id": "52fe48019251416c750acb33", "gender": 2, "id": 1207282, "name": "Anthony Ingruber", "order": 66}, {"cast_id": 88, "character": "Flight Crew Mechanic (uncredited)", "credit_id": "52fe48019251416c750acb37", "gender": 0, "id": 1207283, "name": "Ashley Jeffery", "order": 67}, {"cast_id": 14, "character": "Samson Pilot", "credit_id": "52fe48009251416c750ac9f9", "gender": 0, "id": 98216, "name": "Dean Knowsley", "order": 68}, {"cast_id": 89, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb3b", "gender": 0, "id": 1201399, "name": "Joseph Mika-Hunt", "order": 69}, {"cast_id": 90, "character": "Banshee (uncredited)", "credit_id": "52fe48019251416c750acb3f", "gender": 0, "id": 236696, "name": "Terry Notary", "order": 70}, {"cast_id": 91, "character": "Soldier (uncredited)", "credit_id": "52fe48019251416c750acb43", "gender": 0, "id": 1207287, "name": "Kai Pantano", "order": 71}, {"cast_id": 92, "character": "Blast Technician (uncredited)", "credit_id": "52fe48019251416c750acb47", "gender": 0, "id": 1207288, "name": "Logan Pithyou", "order": 72}, {"cast_id": 93, "character": "Vindum Raah (uncredited)", "credit_id": "52fe48019251416c750acb4b", "gender": 0, "id": 1207289, "name": "Stuart Pollock", "order": 73}, {"cast_id": 94, "character": "Hero (uncredited)", "credit_id": "52fe48019251416c750acb4f", "gender": 0, "id": 584868, "name": "Raja", "order": 74}, {"cast_id": 95, "character": "Ops Centreworker (uncredited)", "credit_id": "52fe48019251416c750acb53", "gender": 0, "id": 1207290, "name": "Gareth Ruck", "order": 75}, {"cast_id": 96, "character": "Engineer (uncredited)", "credit_id": "52fe48019251416c750acb57", "gender": 0, "id": 1062463, "name": "Rhian Sheehan", "order": 76}, {"cast_id": 97, "character": "Col. Quaritch\'s Mech Suit (uncredited)", "credit_id": "52fe48019251416c750acb5b", "gender": 0, "id": 60656, "name": "T. J. Storm", "order": 77}, {"cast_id": 98, "character": "Female Marine (uncredited)", "credit_id": "52fe48019251416c750acb5f", "gender": 0, "id": 1207291, "name": "Jodie Taylor", "order": 78}, {"cast_id": 99, "character": "Ikran Clan Leader (uncredited)", "credit_id": "52fe48019251416c750acb63", "gender": 1, "id": 1186027, "name": "Alicia Vela-Bailey", "order": 79}, {"cast_id": 100, "character": "Geologist (uncredited)", "credit_id": "52fe48019251416c750acb67", "gender": 0, "id": 1207292, "name": "Richard Whiteside", "order": 80}, {"cast_id": 101, "character": "Na\'vi (uncredited)", "credit_id": "52fe48019251416c750acb6b", "gender": 0, "id": 103259, "name": "Nikie Zambo", "order": 81}, {"cast_id": 102, "character": "Ambient Room Tech / Troupe", "credit_id": "52fe48019251416c750acb6f", "gender": 1, "id": 42286, "name": "Julene Renee", "order": 82}]'],
          dtype=object)




```python
#merging of two Dataframes on the basis of title
movies.merge(credits,on='title') 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget</th>
      <th>genres</th>
      <th>homepage</th>
      <th>id</th>
      <th>keywords</th>
      <th>original_language</th>
      <th>original_title</th>
      <th>overview</th>
      <th>popularity</th>
      <th>production_companies</th>
      <th>...</th>
      <th>runtime</th>
      <th>spoken_languages</th>
      <th>status</th>
      <th>tagline</th>
      <th>title</th>
      <th>vote_average</th>
      <th>vote_count</th>
      <th>movie_id</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>237000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.avatarmovie.com/</td>
      <td>19995</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>en</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>150.437577</td>
      <td>[{"name": "Ingenious Film Partners", "id": 289...</td>
      <td>...</td>
      <td>162.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}, {"iso...</td>
      <td>Released</td>
      <td>Enter the World of Pandora.</td>
      <td>Avatar</td>
      <td>7.2</td>
      <td>11800</td>
      <td>19995</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>300000000</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>http://disney.go.com/disneypictures/pirates/</td>
      <td>285</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>en</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>139.082615</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}, {"...</td>
      <td>...</td>
      <td>169.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>At the end of the world, the adventure begins.</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>6.9</td>
      <td>4500</td>
      <td>285</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>245000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.sonypictures.com/movies/spectre/</td>
      <td>206647</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>en</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>107.376788</td>
      <td>[{"name": "Columbia Pictures", "id": 5}, {"nam...</td>
      <td>...</td>
      <td>148.0</td>
      <td>[{"iso_639_1": "fr", "name": "Fran\u00e7ais"},...</td>
      <td>Released</td>
      <td>A Plan No One Escapes</td>
      <td>Spectre</td>
      <td>6.3</td>
      <td>4466</td>
      <td>206647</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>250000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>http://www.thedarkknightrises.com/</td>
      <td>49026</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>en</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>112.312950</td>
      <td>[{"name": "Legendary Pictures", "id": 923}, {"...</td>
      <td>...</td>
      <td>165.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>The Legend Ends</td>
      <td>The Dark Knight Rises</td>
      <td>7.6</td>
      <td>9106</td>
      <td>49026</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>260000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://movies.disney.com/john-carter</td>
      <td>49529</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>en</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>43.926995</td>
      <td>[{"name": "Walt Disney Pictures", "id": 2}]</td>
      <td>...</td>
      <td>132.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>Lost in our world, found in another.</td>
      <td>John Carter</td>
      <td>6.1</td>
      <td>2124</td>
      <td>49529</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>220000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>NaN</td>
      <td>9367</td>
      <td>[{"id": 5616, "name": "united states\u2013mexi...</td>
      <td>es</td>
      <td>El Mariachi</td>
      <td>El Mariachi just wants to play his guitar and ...</td>
      <td>14.269792</td>
      <td>[{"name": "Columbia Pictures", "id": 5}]</td>
      <td>...</td>
      <td>81.0</td>
      <td>[{"iso_639_1": "es", "name": "Espa\u00f1ol"}]</td>
      <td>Released</td>
      <td>He didn't come looking for trouble, but troubl...</td>
      <td>El Mariachi</td>
      <td>6.6</td>
      <td>238</td>
      <td>9367</td>
      <td>[{"cast_id": 1, "character": "El Mariachi", "c...</td>
      <td>[{"credit_id": "52fe44eec3a36847f80b280b", "de...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>9000</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 10749, "...</td>
      <td>NaN</td>
      <td>72766</td>
      <td>[]</td>
      <td>en</td>
      <td>Newlyweds</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>0.642552</td>
      <td>[]</td>
      <td>...</td>
      <td>85.0</td>
      <td>[]</td>
      <td>Released</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>Newlyweds</td>
      <td>5.9</td>
      <td>5</td>
      <td>72766</td>
      <td>[{"cast_id": 1, "character": "Buzzy", "credit_...</td>
      <td>[{"credit_id": "52fe487dc3a368484e0fb013", "de...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>0</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...</td>
      <td>http://www.hallmarkchannel.com/signedsealeddel...</td>
      <td>231617</td>
      <td>[{"id": 248, "name": "date"}, {"id": 699, "nam...</td>
      <td>en</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"Signed, Sealed, Delivered" introduces a dedic...</td>
      <td>1.444476</td>
      <td>[{"name": "Front Street Pictures", "id": 3958}...</td>
      <td>...</td>
      <td>120.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>NaN</td>
      <td>Signed, Sealed, Delivered</td>
      <td>7.0</td>
      <td>6</td>
      <td>231617</td>
      <td>[{"cast_id": 8, "character": "Oliver O\u2019To...</td>
      <td>[{"credit_id": "52fe4df3c3a36847f8275ecf", "de...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>0</td>
      <td>[]</td>
      <td>http://shanghaicalling.com/</td>
      <td>126186</td>
      <td>[]</td>
      <td>en</td>
      <td>Shanghai Calling</td>
      <td>When ambitious New York attorney Sam is sent t...</td>
      <td>0.857008</td>
      <td>[]</td>
      <td>...</td>
      <td>98.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>A New Yorker in Shanghai</td>
      <td>Shanghai Calling</td>
      <td>5.7</td>
      <td>7</td>
      <td>126186</td>
      <td>[{"cast_id": 3, "character": "Sam", "credit_id...</td>
      <td>[{"credit_id": "52fe4ad9c3a368484e16a36b", "de...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>0</td>
      <td>[{"id": 99, "name": "Documentary"}]</td>
      <td>NaN</td>
      <td>25975</td>
      <td>[{"id": 1523, "name": "obsession"}, {"id": 224...</td>
      <td>en</td>
      <td>My Date with Drew</td>
      <td>Ever since the second grade when he first saw ...</td>
      <td>1.929883</td>
      <td>[{"name": "rusty bear entertainment", "id": 87...</td>
      <td>...</td>
      <td>90.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}]</td>
      <td>Released</td>
      <td>NaN</td>
      <td>My Date with Drew</td>
      <td>6.3</td>
      <td>16</td>
      <td>25975</td>
      <td>[{"cast_id": 3, "character": "Herself", "credi...</td>
      <td>[{"credit_id": "58ce021b9251415a390165d9", "de...</td>
    </tr>
  </tbody>
</table>
<p>4809 rows × 23 columns</p>
</div>




```python
movies.merge(credits,on='title') .shape

```




    (4809, 23)




```python
movies.shape
```




    (4803, 20)




```python
credits.shape
```




    (4803, 4)




```python
#new dataframe of movies
movies=movies.merge(credits,on='title')

```


```python
movies.head(1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>budget</th>
      <th>genres</th>
      <th>homepage</th>
      <th>id</th>
      <th>keywords</th>
      <th>original_language</th>
      <th>original_title</th>
      <th>overview</th>
      <th>popularity</th>
      <th>production_companies</th>
      <th>...</th>
      <th>runtime</th>
      <th>spoken_languages</th>
      <th>status</th>
      <th>tagline</th>
      <th>title</th>
      <th>vote_average</th>
      <th>vote_count</th>
      <th>movie_id</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>237000000</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>http://www.avatarmovie.com/</td>
      <td>19995</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>en</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>150.437577</td>
      <td>[{"name": "Ingenious Film Partners", "id": 289...</td>
      <td>...</td>
      <td>162.0</td>
      <td>[{"iso_639_1": "en", "name": "English"}, {"iso...</td>
      <td>Released</td>
      <td>Enter the World of Pandora.</td>
      <td>Avatar</td>
      <td>7.2</td>
      <td>11800</td>
      <td>19995</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
  </tbody>
</table>
<p>1 rows × 23 columns</p>
</div>




```python
#keeping certain columns and removing the columns that are not necessary for our analysis
#genres
#id
#title
#keywords
#overview
#cast
#crew
movies[['movie_id','title','overview','genres','keywords','cast','crew']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>El Mariachi just wants to play his guitar and ...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>[{"id": 5616, "name": "united states\u2013mexi...</td>
      <td>[{"cast_id": 1, "character": "El Mariachi", "c...</td>
      <td>[{"credit_id": "52fe44eec3a36847f80b280b", "de...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>A newlywed couple's honeymoon is upended by th...</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 10749, "...</td>
      <td>[]</td>
      <td>[{"cast_id": 1, "character": "Buzzy", "credit_...</td>
      <td>[{"credit_id": "52fe487dc3a368484e0fb013", "de...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"Signed, Sealed, Delivered" introduces a dedic...</td>
      <td>[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...</td>
      <td>[{"id": 248, "name": "date"}, {"id": 699, "nam...</td>
      <td>[{"cast_id": 8, "character": "Oliver O\u2019To...</td>
      <td>[{"credit_id": "52fe4df3c3a36847f8275ecf", "de...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>When ambitious New York attorney Sam is sent t...</td>
      <td>[]</td>
      <td>[]</td>
      <td>[{"cast_id": 3, "character": "Sam", "credit_id...</td>
      <td>[{"credit_id": "52fe4ad9c3a368484e16a36b", "de...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>Ever since the second grade when he first saw ...</td>
      <td>[{"id": 99, "name": "Documentary"}]</td>
      <td>[{"id": 1523, "name": "obsession"}, {"id": 224...</td>
      <td>[{"cast_id": 3, "character": "Herself", "credi...</td>
      <td>[{"credit_id": "58ce021b9251415a390165d9", "de...</td>
    </tr>
  </tbody>
</table>
<p>4809 rows × 7 columns</p>
</div>




```python
# final new dataframe for the recommender system
movies=movies[['movie_id','title','overview','genres','keywords','cast','crew']]
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[{"id": 12, "name": "Adventure"}, {"id": 14, "...</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 80, "nam...</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[{"id": 28, "name": "Action"}, {"id": 12, "nam...</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#detecting missing values
movies.isnull().sum()
```




    movie_id    0
    title       0
    overview    3
    genres      0
    keywords    0
    cast        0
    crew        0
    dtype: int64




```python
movies.dropna(inplace=True)
```


```python
#removed the movies that had missing values in overview column
movies.isnull().sum()
```




    movie_id    0
    title       0
    overview    0
    genres      0
    keywords    0
    cast        0
    crew        0
    dtype: int64




```python
#to check for duplicate data
movies.duplicated().sum()
```




    0




```python
#reformating of columns
#here the format is not properly shown
movies.iloc[0].genres
```




    '[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}, {"id": 14, "name": "Fantasy"}, {"id": 878, "name": "Science Fiction"}]'




```python
#converting string of list into list
import ast
ast.literal_eval('[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}, {"id": 14, "name": "Fantasy"}, {"id": 878, "name": "Science Fiction"}]'
)
```




    [{'id': 28, 'name': 'Action'},
     {'id': 12, 'name': 'Adventure'},
     {'id': 14, 'name': 'Fantasy'},
     {'id': 878, 'name': 'Science Fiction'}]




```python
def convert(obj):
    L=[]
    for i in ast.literal_eval(obj):
        L.append(i['name'])
    return L
```


```python
movies['genres'].apply(convert)
```




    0       [Action, Adventure, Fantasy, Science Fiction]
    1                        [Adventure, Fantasy, Action]
    2                          [Action, Adventure, Crime]
    3                    [Action, Crime, Drama, Thriller]
    4                [Action, Adventure, Science Fiction]
                                ...                      
    4804                        [Action, Crime, Thriller]
    4805                                [Comedy, Romance]
    4806               [Comedy, Drama, Romance, TV Movie]
    4807                                               []
    4808                                    [Documentary]
    Name: genres, Length: 4806, dtype: object




```python
movies['genres']=movies['genres'].apply(convert)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[{"id": 1463, "name": "culture clash"}, {"id":...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[{"id": 270, "name": "ocean"}, {"id": 726, "na...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[{"id": 470, "name": "spy"}, {"id": 818, "name...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[{"id": 849, "name": "dc comics"}, {"id": 853,...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[{"id": 818, "name": "based on novel"}, {"id":...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['keywords'].apply(convert)
```




    0       [culture clash, future, space war, space colon...
    1       [ocean, drug abuse, exotic island, east india ...
    2       [spy, based on novel, secret agent, sequel, mi...
    3       [dc comics, crime fighter, terrorist, secret i...
    4       [based on novel, mars, medallion, space travel...
                                  ...                        
    4804    [united states–mexico barrier, legs, arms, pap...
    4805                                                   []
    4806    [date, love at first sight, narration, investi...
    4807                                                   []
    4808            [obsession, camcorder, crush, dream girl]
    Name: keywords, Length: 4806, dtype: object




```python
movies['keywords']=movies['keywords'].apply(convert)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[{"cast_id": 242, "character": "Jake Sully", "...</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[{"cast_id": 4, "character": "Captain Jack Spa...</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[{"cast_id": 1, "character": "James Bond", "cr...</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[{"cast_id": 2, "character": "Bruce Wayne / Ba...</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[{"cast_id": 5, "character": "John Carter", "c...</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#cast column for first movie
movies['cast'][0]
```




    '[{"cast_id": 242, "character": "Jake Sully", "credit_id": "5602a8a7c3a3685532001c9a", "gender": 2, "id": 65731, "name": "Sam Worthington", "order": 0}, {"cast_id": 3, "character": "Neytiri", "credit_id": "52fe48009251416c750ac9cb", "gender": 1, "id": 8691, "name": "Zoe Saldana", "order": 1}, {"cast_id": 25, "character": "Dr. Grace Augustine", "credit_id": "52fe48009251416c750aca39", "gender": 1, "id": 10205, "name": "Sigourney Weaver", "order": 2}, {"cast_id": 4, "character": "Col. Quaritch", "credit_id": "52fe48009251416c750ac9cf", "gender": 2, "id": 32747, "name": "Stephen Lang", "order": 3}, {"cast_id": 5, "character": "Trudy Chacon", "credit_id": "52fe48009251416c750ac9d3", "gender": 1, "id": 17647, "name": "Michelle Rodriguez", "order": 4}, {"cast_id": 8, "character": "Selfridge", "credit_id": "52fe48009251416c750ac9e1", "gender": 2, "id": 1771, "name": "Giovanni Ribisi", "order": 5}, {"cast_id": 7, "character": "Norm Spellman", "credit_id": "52fe48009251416c750ac9dd", "gender": 2, "id": 59231, "name": "Joel David Moore", "order": 6}, {"cast_id": 9, "character": "Moat", "credit_id": "52fe48009251416c750ac9e5", "gender": 1, "id": 30485, "name": "CCH Pounder", "order": 7}, {"cast_id": 11, "character": "Eytukan", "credit_id": "52fe48009251416c750ac9ed", "gender": 2, "id": 15853, "name": "Wes Studi", "order": 8}, {"cast_id": 10, "character": "Tsu\'Tey", "credit_id": "52fe48009251416c750ac9e9", "gender": 2, "id": 10964, "name": "Laz Alonso", "order": 9}, {"cast_id": 12, "character": "Dr. Max Patel", "credit_id": "52fe48009251416c750ac9f1", "gender": 2, "id": 95697, "name": "Dileep Rao", "order": 10}, {"cast_id": 13, "character": "Lyle Wainfleet", "credit_id": "52fe48009251416c750ac9f5", "gender": 2, "id": 98215, "name": "Matt Gerald", "order": 11}, {"cast_id": 32, "character": "Private Fike", "credit_id": "52fe48009251416c750aca5b", "gender": 2, "id": 154153, "name": "Sean Anthony Moran", "order": 12}, {"cast_id": 33, "character": "Cryo Vault Med Tech", "credit_id": "52fe48009251416c750aca5f", "gender": 2, "id": 397312, "name": "Jason Whyte", "order": 13}, {"cast_id": 34, "character": "Venture Star Crew Chief", "credit_id": "52fe48009251416c750aca63", "gender": 2, "id": 42317, "name": "Scott Lawrence", "order": 14}, {"cast_id": 35, "character": "Lock Up Trooper", "credit_id": "52fe48009251416c750aca67", "gender": 2, "id": 986734, "name": "Kelly Kilgour", "order": 15}, {"cast_id": 36, "character": "Shuttle Pilot", "credit_id": "52fe48009251416c750aca6b", "gender": 0, "id": 1207227, "name": "James Patrick Pitt", "order": 16}, {"cast_id": 37, "character": "Shuttle Co-Pilot", "credit_id": "52fe48009251416c750aca6f", "gender": 0, "id": 1180936, "name": "Sean Patrick Murphy", "order": 17}, {"cast_id": 38, "character": "Shuttle Crew Chief", "credit_id": "52fe48009251416c750aca73", "gender": 2, "id": 1019578, "name": "Peter Dillon", "order": 18}, {"cast_id": 39, "character": "Tractor Operator / Troupe", "credit_id": "52fe48009251416c750aca77", "gender": 0, "id": 91443, "name": "Kevin Dorman", "order": 19}, {"cast_id": 40, "character": "Dragon Gunship Pilot", "credit_id": "52fe48009251416c750aca7b", "gender": 2, "id": 173391, "name": "Kelson Henderson", "order": 20}, {"cast_id": 41, "character": "Dragon Gunship Gunner", "credit_id": "52fe48009251416c750aca7f", "gender": 0, "id": 1207236, "name": "David Van Horn", "order": 21}, {"cast_id": 42, "character": "Dragon Gunship Navigator", "credit_id": "52fe48009251416c750aca83", "gender": 0, "id": 215913, "name": "Jacob Tomuri", "order": 22}, {"cast_id": 43, "character": "Suit #1", "credit_id": "52fe48009251416c750aca87", "gender": 0, "id": 143206, "name": "Michael Blain-Rozgay", "order": 23}, {"cast_id": 44, "character": "Suit #2", "credit_id": "52fe48009251416c750aca8b", "gender": 2, "id": 169676, "name": "Jon Curry", "order": 24}, {"cast_id": 46, "character": "Ambient Room Tech", "credit_id": "52fe48009251416c750aca8f", "gender": 0, "id": 1048610, "name": "Luke Hawker", "order": 25}, {"cast_id": 47, "character": "Ambient Room Tech / Troupe", "credit_id": "52fe48009251416c750aca93", "gender": 0, "id": 42288, "name": "Woody Schultz", "order": 26}, {"cast_id": 48, "character": "Horse Clan Leader", "credit_id": "52fe48009251416c750aca97", "gender": 2, "id": 68278, "name": "Peter Mensah", "order": 27}, {"cast_id": 49, "character": "Link Room Tech", "credit_id": "52fe48009251416c750aca9b", "gender": 0, "id": 1207247, "name": "Sonia Yee", "order": 28}, {"cast_id": 50, "character": "Basketball Avatar / Troupe", "credit_id": "52fe48009251416c750aca9f", "gender": 1, "id": 1207248, "name": "Jahnel Curfman", "order": 29}, {"cast_id": 51, "character": "Basketball Avatar", "credit_id": "52fe48009251416c750acaa3", "gender": 0, "id": 89714, "name": "Ilram Choi", "order": 30}, {"cast_id": 52, "character": "Na\'vi Child", "credit_id": "52fe48009251416c750acaa7", "gender": 0, "id": 1207249, "name": "Kyla Warren", "order": 31}, {"cast_id": 53, "character": "Troupe", "credit_id": "52fe48009251416c750acaab", "gender": 0, "id": 1207250, "name": "Lisa Roumain", "order": 32}, {"cast_id": 54, "character": "Troupe", "credit_id": "52fe48009251416c750acaaf", "gender": 1, "id": 83105, "name": "Debra Wilson", "order": 33}, {"cast_id": 57, "character": "Troupe", "credit_id": "52fe48009251416c750acabb", "gender": 0, "id": 1207253, "name": "Chris Mala", "order": 34}, {"cast_id": 55, "character": "Troupe", "credit_id": "52fe48009251416c750acab3", "gender": 0, "id": 1207251, "name": "Taylor Kibby", "order": 35}, {"cast_id": 56, "character": "Troupe", "credit_id": "52fe48009251416c750acab7", "gender": 0, "id": 1207252, "name": "Jodie Landau", "order": 36}, {"cast_id": 58, "character": "Troupe", "credit_id": "52fe48009251416c750acabf", "gender": 0, "id": 1207254, "name": "Julie Lamm", "order": 37}, {"cast_id": 59, "character": "Troupe", "credit_id": "52fe48009251416c750acac3", "gender": 0, "id": 1207257, "name": "Cullen B. Madden", "order": 38}, {"cast_id": 60, "character": "Troupe", "credit_id": "52fe48009251416c750acac7", "gender": 0, "id": 1207259, "name": "Joseph Brady Madden", "order": 39}, {"cast_id": 61, "character": "Troupe", "credit_id": "52fe48009251416c750acacb", "gender": 0, "id": 1207262, "name": "Frankie Torres", "order": 40}, {"cast_id": 62, "character": "Troupe", "credit_id": "52fe48009251416c750acacf", "gender": 1, "id": 1158600, "name": "Austin Wilson", "order": 41}, {"cast_id": 63, "character": "Troupe", "credit_id": "52fe48019251416c750acad3", "gender": 1, "id": 983705, "name": "Sara Wilson", "order": 42}, {"cast_id": 64, "character": "Troupe", "credit_id": "52fe48019251416c750acad7", "gender": 0, "id": 1207263, "name": "Tamica Washington-Miller", "order": 43}, {"cast_id": 65, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acadb", "gender": 1, "id": 1145098, "name": "Lucy Briant", "order": 44}, {"cast_id": 66, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acadf", "gender": 2, "id": 33305, "name": "Nathan Meister", "order": 45}, {"cast_id": 67, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acae3", "gender": 0, "id": 1207264, "name": "Gerry Blair", "order": 46}, {"cast_id": 68, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acae7", "gender": 2, "id": 33311, "name": "Matthew Chamberlain", "order": 47}, {"cast_id": 69, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acaeb", "gender": 0, "id": 1207265, "name": "Paul Yates", "order": 48}, {"cast_id": 70, "character": "Op Center Duty Officer", "credit_id": "52fe48019251416c750acaef", "gender": 0, "id": 1207266, "name": "Wray Wilson", "order": 49}, {"cast_id": 71, "character": "Op Center Staff", "credit_id": "52fe48019251416c750acaf3", "gender": 2, "id": 54492, "name": "James Gaylyn", "order": 50}, {"cast_id": 72, "character": "Dancer", "credit_id": "52fe48019251416c750acaf7", "gender": 0, "id": 1207267, "name": "Melvin Leno Clark III", "order": 51}, {"cast_id": 73, "character": "Dancer", "credit_id": "52fe48019251416c750acafb", "gender": 0, "id": 1207268, "name": "Carvon Futrell", "order": 52}, {"cast_id": 74, "character": "Dancer", "credit_id": "52fe48019251416c750acaff", "gender": 0, "id": 1207269, "name": "Brandon Jelkes", "order": 53}, {"cast_id": 75, "character": "Dancer", "credit_id": "52fe48019251416c750acb03", "gender": 0, "id": 1207270, "name": "Micah Moch", "order": 54}, {"cast_id": 76, "character": "Dancer", "credit_id": "52fe48019251416c750acb07", "gender": 0, "id": 1207271, "name": "Hanniyah Muhammad", "order": 55}, {"cast_id": 77, "character": "Dancer", "credit_id": "52fe48019251416c750acb0b", "gender": 0, "id": 1207272, "name": "Christopher Nolen", "order": 56}, {"cast_id": 78, "character": "Dancer", "credit_id": "52fe48019251416c750acb0f", "gender": 0, "id": 1207273, "name": "Christa Oliver", "order": 57}, {"cast_id": 79, "character": "Dancer", "credit_id": "52fe48019251416c750acb13", "gender": 0, "id": 1207274, "name": "April Marie Thomas", "order": 58}, {"cast_id": 80, "character": "Dancer", "credit_id": "52fe48019251416c750acb17", "gender": 0, "id": 1207275, "name": "Bravita A. Threatt", "order": 59}, {"cast_id": 81, "character": "Mining Chief (uncredited)", "credit_id": "52fe48019251416c750acb1b", "gender": 0, "id": 1207276, "name": "Colin Bleasdale", "order": 60}, {"cast_id": 82, "character": "Veteran Miner (uncredited)", "credit_id": "52fe48019251416c750acb1f", "gender": 0, "id": 107969, "name": "Mike Bodnar", "order": 61}, {"cast_id": 83, "character": "Richard (uncredited)", "credit_id": "52fe48019251416c750acb23", "gender": 0, "id": 1207278, "name": "Matt Clayton", "order": 62}, {"cast_id": 84, "character": "Nav\'i (uncredited)", "credit_id": "52fe48019251416c750acb27", "gender": 1, "id": 147898, "name": "Nicole Dionne", "order": 63}, {"cast_id": 85, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb2b", "gender": 0, "id": 1207280, "name": "Jamie Harrison", "order": 64}, {"cast_id": 86, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb2f", "gender": 0, "id": 1207281, "name": "Allan Henry", "order": 65}, {"cast_id": 87, "character": "Ground Technician (uncredited)", "credit_id": "52fe48019251416c750acb33", "gender": 2, "id": 1207282, "name": "Anthony Ingruber", "order": 66}, {"cast_id": 88, "character": "Flight Crew Mechanic (uncredited)", "credit_id": "52fe48019251416c750acb37", "gender": 0, "id": 1207283, "name": "Ashley Jeffery", "order": 67}, {"cast_id": 14, "character": "Samson Pilot", "credit_id": "52fe48009251416c750ac9f9", "gender": 0, "id": 98216, "name": "Dean Knowsley", "order": 68}, {"cast_id": 89, "character": "Trooper (uncredited)", "credit_id": "52fe48019251416c750acb3b", "gender": 0, "id": 1201399, "name": "Joseph Mika-Hunt", "order": 69}, {"cast_id": 90, "character": "Banshee (uncredited)", "credit_id": "52fe48019251416c750acb3f", "gender": 0, "id": 236696, "name": "Terry Notary", "order": 70}, {"cast_id": 91, "character": "Soldier (uncredited)", "credit_id": "52fe48019251416c750acb43", "gender": 0, "id": 1207287, "name": "Kai Pantano", "order": 71}, {"cast_id": 92, "character": "Blast Technician (uncredited)", "credit_id": "52fe48019251416c750acb47", "gender": 0, "id": 1207288, "name": "Logan Pithyou", "order": 72}, {"cast_id": 93, "character": "Vindum Raah (uncredited)", "credit_id": "52fe48019251416c750acb4b", "gender": 0, "id": 1207289, "name": "Stuart Pollock", "order": 73}, {"cast_id": 94, "character": "Hero (uncredited)", "credit_id": "52fe48019251416c750acb4f", "gender": 0, "id": 584868, "name": "Raja", "order": 74}, {"cast_id": 95, "character": "Ops Centreworker (uncredited)", "credit_id": "52fe48019251416c750acb53", "gender": 0, "id": 1207290, "name": "Gareth Ruck", "order": 75}, {"cast_id": 96, "character": "Engineer (uncredited)", "credit_id": "52fe48019251416c750acb57", "gender": 0, "id": 1062463, "name": "Rhian Sheehan", "order": 76}, {"cast_id": 97, "character": "Col. Quaritch\'s Mech Suit (uncredited)", "credit_id": "52fe48019251416c750acb5b", "gender": 0, "id": 60656, "name": "T. J. Storm", "order": 77}, {"cast_id": 98, "character": "Female Marine (uncredited)", "credit_id": "52fe48019251416c750acb5f", "gender": 0, "id": 1207291, "name": "Jodie Taylor", "order": 78}, {"cast_id": 99, "character": "Ikran Clan Leader (uncredited)", "credit_id": "52fe48019251416c750acb63", "gender": 1, "id": 1186027, "name": "Alicia Vela-Bailey", "order": 79}, {"cast_id": 100, "character": "Geologist (uncredited)", "credit_id": "52fe48019251416c750acb67", "gender": 0, "id": 1207292, "name": "Richard Whiteside", "order": 80}, {"cast_id": 101, "character": "Na\'vi (uncredited)", "credit_id": "52fe48019251416c750acb6b", "gender": 0, "id": 103259, "name": "Nikie Zambo", "order": 81}, {"cast_id": 102, "character": "Ambient Room Tech / Troupe", "credit_id": "52fe48019251416c750acb6f", "gender": 1, "id": 42286, "name": "Julene Renee", "order": 82}]'




```python
def convert3(obj):
    L=[]
    counter=0
    for i in ast.literal_eval(obj):
        if counter!=3:
            L.append(i['name'])
            counter+=1
        else:
            break
    return L
```


```python
movies['cast'].apply(convert3)
```




    0        [Sam Worthington, Zoe Saldana, Sigourney Weaver]
    1           [Johnny Depp, Orlando Bloom, Keira Knightley]
    2            [Daniel Craig, Christoph Waltz, Léa Seydoux]
    3            [Christian Bale, Michael Caine, Gary Oldman]
    4          [Taylor Kitsch, Lynn Collins, Samantha Morton]
                                  ...                        
    4804    [Carlos Gallardo, Jaime de Hoyos, Peter Marqua...
    4805         [Edward Burns, Kerry Bishé, Marsha Dietlein]
    4806           [Eric Mabius, Kristin Booth, Crystal Lowe]
    4807            [Daniel Henney, Eliza Coupe, Bill Paxton]
    4808    [Drew Barrymore, Brian Herzlinger, Corey Feldman]
    Name: cast, Length: 4806, dtype: object




```python
movies['cast']=movies['cast'].apply(convert3)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[{"credit_id": "52fe48009251416c750aca23", "de...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[{"credit_id": "52fe4232c3a36847f800b579", "de...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[{"credit_id": "54805967c3a36829b5002c41", "de...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[{"credit_id": "52fe4781c3a36847f81398c3", "de...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[{"credit_id": "52fe479ac3a36847f813eaa3", "de...</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['cast'][0]
```




    ['Sam Worthington', 'Zoe Saldana', 'Sigourney Weaver']




```python
#cast column for first movie
movies['crew'][0]
```




    '[{"credit_id": "52fe48009251416c750aca23", "department": "Editing", "gender": 0, "id": 1721, "job": "Editor", "name": "Stephen E. Rivkin"}, {"credit_id": "539c47ecc3a36810e3001f87", "department": "Art", "gender": 2, "id": 496, "job": "Production Design", "name": "Rick Carter"}, {"credit_id": "54491c89c3a3680fb4001cf7", "department": "Sound", "gender": 0, "id": 900, "job": "Sound Designer", "name": "Christopher Boyes"}, {"credit_id": "54491cb70e0a267480001bd0", "department": "Sound", "gender": 0, "id": 900, "job": "Supervising Sound Editor", "name": "Christopher Boyes"}, {"credit_id": "539c4a4cc3a36810c9002101", "department": "Production", "gender": 1, "id": 1262, "job": "Casting", "name": "Mali Finn"}, {"credit_id": "5544ee3b925141499f0008fc", "department": "Sound", "gender": 2, "id": 1729, "job": "Original Music Composer", "name": "James Horner"}, {"credit_id": "52fe48009251416c750ac9c3", "department": "Directing", "gender": 2, "id": 2710, "job": "Director", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750ac9d9", "department": "Writing", "gender": 2, "id": 2710, "job": "Writer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca17", "department": "Editing", "gender": 2, "id": 2710, "job": "Editor", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca29", "department": "Production", "gender": 2, "id": 2710, "job": "Producer", "name": "James Cameron"}, {"credit_id": "52fe48009251416c750aca3f", "department": "Writing", "gender": 2, "id": 2710, "job": "Screenplay", "name": "James Cameron"}, {"credit_id": "539c4987c3a36810ba0021a4", "department": "Art", "gender": 2, "id": 7236, "job": "Art Direction", "name": "Andrew Menzies"}, {"credit_id": "549598c3c3a3686ae9004383", "department": "Visual Effects", "gender": 0, "id": 6690, "job": "Visual Effects Producer", "name": "Jill Brooks"}, {"credit_id": "52fe48009251416c750aca4b", "department": "Production", "gender": 1, "id": 6347, "job": "Casting", "name": "Margery Simkin"}, {"credit_id": "570b6f419251417da70032fe", "department": "Art", "gender": 2, "id": 6878, "job": "Supervising Art Director", "name": "Kevin Ishioka"}, {"credit_id": "5495a0fac3a3686ae9004468", "department": "Sound", "gender": 0, "id": 6883, "job": "Music Editor", "name": "Dick Bernstein"}, {"credit_id": "54959706c3a3686af3003e81", "department": "Sound", "gender": 0, "id": 8159, "job": "Sound Effects Editor", "name": "Shannon Mills"}, {"credit_id": "54491d58c3a3680fb1001ccb", "department": "Sound", "gender": 0, "id": 8160, "job": "Foley", "name": "Dennie Thorpe"}, {"credit_id": "54491d6cc3a3680fa5001b2c", "department": "Sound", "gender": 0, "id": 8163, "job": "Foley", "name": "Jana Vance"}, {"credit_id": "52fe48009251416c750aca57", "department": "Costume & Make-Up", "gender": 1, "id": 8527, "job": "Costume Design", "name": "Deborah Lynn Scott"}, {"credit_id": "52fe48009251416c750aca2f", "department": "Production", "gender": 2, "id": 8529, "job": "Producer", "name": "Jon Landau"}, {"credit_id": "539c4937c3a36810ba002194", "department": "Art", "gender": 0, "id": 9618, "job": "Art Direction", "name": "Sean Haworth"}, {"credit_id": "539c49b6c3a36810c10020e6", "department": "Art", "gender": 1, "id": 12653, "job": "Set Decoration", "name": "Kim Sinclair"}, {"credit_id": "570b6f2f9251413a0e00020d", "department": "Art", "gender": 1, "id": 12653, "job": "Supervising Art Director", "name": "Kim Sinclair"}, {"credit_id": "54491a6c0e0a26748c001b19", "department": "Art", "gender": 2, "id": 14350, "job": "Set Designer", "name": "Richard F. Mays"}, {"credit_id": "56928cf4c3a3684cff0025c4", "department": "Production", "gender": 1, "id": 20294, "job": "Executive Producer", "name": "Laeta Kalogridis"}, {"credit_id": "52fe48009251416c750aca51", "department": "Costume & Make-Up", "gender": 0, "id": 17675, "job": "Costume Design", "name": "Mayes C. Rubeo"}, {"credit_id": "52fe48009251416c750aca11", "department": "Camera", "gender": 2, "id": 18265, "job": "Director of Photography", "name": "Mauro Fiore"}, {"credit_id": "5449194d0e0a26748f001b39", "department": "Art", "gender": 0, "id": 42281, "job": "Set Designer", "name": "Scott Herbertson"}, {"credit_id": "52fe48009251416c750aca05", "department": "Crew", "gender": 0, "id": 42288, "job": "Stunts", "name": "Woody Schultz"}, {"credit_id": "5592aefb92514152de0010f5", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Makeup Artist", "name": "Linda DeVetta"}, {"credit_id": "5592afa492514152de00112c", "department": "Costume & Make-Up", "gender": 0, "id": 29067, "job": "Hairstylist", "name": "Linda DeVetta"}, {"credit_id": "54959ed592514130fc002e5d", "department": "Camera", "gender": 2, "id": 33302, "job": "Camera Operator", "name": "Richard Bluck"}, {"credit_id": "539c4891c3a36810ba002147", "department": "Art", "gender": 2, "id": 33303, "job": "Art Direction", "name": "Simon Bright"}, {"credit_id": "54959c069251417a81001f3a", "department": "Visual Effects", "gender": 0, "id": 113145, "job": "Visual Effects Supervisor", "name": "Richard Martin"}, {"credit_id": "54959a0dc3a3680ff5002c8d", "department": "Crew", "gender": 2, "id": 58188, "job": "Visual Effects Editor", "name": "Steve R. Moore"}, {"credit_id": "52fe48009251416c750aca1d", "department": "Editing", "gender": 2, "id": 58871, "job": "Editor", "name": "John Refoua"}, {"credit_id": "54491a4dc3a3680fc30018ca", "department": "Art", "gender": 0, "id": 92359, "job": "Set Designer", "name": "Karl J. Martin"}, {"credit_id": "52fe48009251416c750aca35", "department": "Camera", "gender": 1, "id": 72201, "job": "Director of Photography", "name": "Chiling Lin"}, {"credit_id": "52fe48009251416c750ac9ff", "department": "Crew", "gender": 0, "id": 89714, "job": "Stunts", "name": "Ilram Choi"}, {"credit_id": "54959c529251416e2b004394", "department": "Visual Effects", "gender": 2, "id": 93214, "job": "Visual Effects Supervisor", "name": "Steven Quale"}, {"credit_id": "54491edf0e0a267489001c37", "department": "Crew", "gender": 1, "id": 122607, "job": "Dialect Coach", "name": "Carla Meyer"}, {"credit_id": "539c485bc3a368653d001a3a", "department": "Art", "gender": 2, "id": 132585, "job": "Art Direction", "name": "Nick Bassett"}, {"credit_id": "539c4903c3a368653d001a74", "department": "Art", "gender": 0, "id": 132596, "job": "Art Direction", "name": "Jill Cormack"}, {"credit_id": "539c4967c3a368653d001a94", "department": "Art", "gender": 0, "id": 132604, "job": "Art Direction", "name": "Andy McLaren"}, {"credit_id": "52fe48009251416c750aca45", "department": "Crew", "gender": 0, "id": 236696, "job": "Motion Capture Artist", "name": "Terry Notary"}, {"credit_id": "54959e02c3a3680fc60027d2", "department": "Crew", "gender": 2, "id": 956198, "job": "Stunt Coordinator", "name": "Garrett Warren"}, {"credit_id": "54959ca3c3a3686ae300438c", "department": "Visual Effects", "gender": 2, "id": 957874, "job": "Visual Effects Supervisor", "name": "Jonathan Rothbart"}, {"credit_id": "570b6f519251412c74001b2f", "department": "Art", "gender": 0, "id": 957889, "job": "Supervising Art Director", "name": "Stefan Dechant"}, {"credit_id": "570b6f62c3a3680b77007460", "department": "Art", "gender": 2, "id": 959555, "job": "Supervising Art Director", "name": "Todd Cherniawsky"}, {"credit_id": "539c4a3ac3a36810da0021cc", "department": "Production", "gender": 0, "id": 1016177, "job": "Casting", "name": "Miranda Rivers"}, {"credit_id": "539c482cc3a36810c1002062", "department": "Art", "gender": 0, "id": 1032536, "job": "Production Design", "name": "Robert Stromberg"}, {"credit_id": "539c4b65c3a36810c9002125", "department": "Costume & Make-Up", "gender": 2, "id": 1071680, "job": "Costume Design", "name": "John Harding"}, {"credit_id": "54959e6692514130fc002e4e", "department": "Camera", "gender": 0, "id": 1177364, "job": "Steadicam Operator", "name": "Roberto De Angelis"}, {"credit_id": "539c49f1c3a368653d001aac", "department": "Costume & Make-Up", "gender": 2, "id": 1202850, "job": "Makeup Department Head", "name": "Mike Smithson"}, {"credit_id": "5495999ec3a3686ae100460c", "department": "Visual Effects", "gender": 0, "id": 1204668, "job": "Visual Effects Producer", "name": "Alain Lalanne"}, {"credit_id": "54959cdfc3a3681153002729", "department": "Visual Effects", "gender": 0, "id": 1206410, "job": "Visual Effects Supervisor", "name": "Lucas Salton"}, {"credit_id": "549596239251417a81001eae", "department": "Crew", "gender": 0, "id": 1234266, "job": "Post Production Supervisor", "name": "Janace Tashjian"}, {"credit_id": "54959c859251416e1e003efe", "department": "Visual Effects", "gender": 0, "id": 1271932, "job": "Visual Effects Supervisor", "name": "Stephen Rosenbaum"}, {"credit_id": "5592af28c3a368775a00105f", "department": "Costume & Make-Up", "gender": 0, "id": 1310064, "job": "Makeup Artist", "name": "Frankie Karena"}, {"credit_id": "539c4adfc3a36810e300203b", "department": "Costume & Make-Up", "gender": 1, "id": 1319844, "job": "Costume Supervisor", "name": "Lisa Lovaas"}, {"credit_id": "54959b579251416e2b004371", "department": "Visual Effects", "gender": 0, "id": 1327028, "job": "Visual Effects Supervisor", "name": "Jonathan Fawkner"}, {"credit_id": "539c48a7c3a36810b5001fa7", "department": "Art", "gender": 0, "id": 1330561, "job": "Art Direction", "name": "Robert Bavin"}, {"credit_id": "539c4a71c3a36810da0021e0", "department": "Costume & Make-Up", "gender": 0, "id": 1330567, "job": "Costume Supervisor", "name": "Anthony Almaraz"}, {"credit_id": "539c4a8ac3a36810ba0021e4", "department": "Costume & Make-Up", "gender": 0, "id": 1330570, "job": "Costume Supervisor", "name": "Carolyn M. Fenton"}, {"credit_id": "539c4ab6c3a36810da0021f0", "department": "Costume & Make-Up", "gender": 0, "id": 1330574, "job": "Costume Supervisor", "name": "Beth Koenigsberg"}, {"credit_id": "54491ab70e0a267480001ba2", "department": "Art", "gender": 0, "id": 1336191, "job": "Set Designer", "name": "Sam Page"}, {"credit_id": "544919d9c3a3680fc30018bd", "department": "Art", "gender": 0, "id": 1339441, "job": "Set Designer", "name": "Tex Kadonaga"}, {"credit_id": "54491cf50e0a267483001b0c", "department": "Editing", "gender": 0, "id": 1352422, "job": "Dialogue Editor", "name": "Kim Foscato"}, {"credit_id": "544919f40e0a26748c001b09", "department": "Art", "gender": 0, "id": 1352962, "job": "Set Designer", "name": "Tammy S. Lee"}, {"credit_id": "5495a115c3a3680ff5002d71", "department": "Crew", "gender": 0, "id": 1357070, "job": "Transportation Coordinator", "name": "Denny Caira"}, {"credit_id": "5495a12f92514130fc002e94", "department": "Crew", "gender": 0, "id": 1357071, "job": "Transportation Coordinator", "name": "James Waitkus"}, {"credit_id": "5495976fc3a36811530026b0", "department": "Sound", "gender": 0, "id": 1360103, "job": "Supervising Sound Editor", "name": "Addison Teague"}, {"credit_id": "54491837c3a3680fb1001c5a", "department": "Art", "gender": 2, "id": 1376887, "job": "Set Designer", "name": "C. Scott Baker"}, {"credit_id": "54491878c3a3680fb4001c9d", "department": "Art", "gender": 0, "id": 1376888, "job": "Set Designer", "name": "Luke Caska"}, {"credit_id": "544918dac3a3680fa5001ae0", "department": "Art", "gender": 0, "id": 1376889, "job": "Set Designer", "name": "David Chow"}, {"credit_id": "544919110e0a267486001b68", "department": "Art", "gender": 0, "id": 1376890, "job": "Set Designer", "name": "Jonathan Dyer"}, {"credit_id": "54491967c3a3680faa001b5e", "department": "Art", "gender": 0, "id": 1376891, "job": "Set Designer", "name": "Joseph Hiura"}, {"credit_id": "54491997c3a3680fb1001c8a", "department": "Art", "gender": 0, "id": 1376892, "job": "Art Department Coordinator", "name": "Rebecca Jellie"}, {"credit_id": "544919ba0e0a26748f001b42", "department": "Art", "gender": 0, "id": 1376893, "job": "Set Designer", "name": "Robert Andrew Johnson"}, {"credit_id": "54491b1dc3a3680faa001b8c", "department": "Art", "gender": 0, "id": 1376895, "job": "Assistant Art Director", "name": "Mike Stassi"}, {"credit_id": "54491b79c3a3680fbb001826", "department": "Art", "gender": 0, "id": 1376897, "job": "Construction Coordinator", "name": "John Villarino"}, {"credit_id": "54491baec3a3680fb4001ce6", "department": "Art", "gender": 2, "id": 1376898, "job": "Assistant Art Director", "name": "Jeffrey Wisniewski"}, {"credit_id": "54491d2fc3a3680fb4001d07", "department": "Editing", "gender": 0, "id": 1376899, "job": "Dialogue Editor", "name": "Cheryl Nardi"}, {"credit_id": "54491d86c3a3680fa5001b2f", "department": "Editing", "gender": 0, "id": 1376901, "job": "Dialogue Editor", "name": "Marshall Winn"}, {"credit_id": "54491d9dc3a3680faa001bb0", "department": "Sound", "gender": 0, "id": 1376902, "job": "Supervising Sound Editor", "name": "Gwendolyn Yates Whittle"}, {"credit_id": "54491dc10e0a267486001bce", "department": "Sound", "gender": 0, "id": 1376903, "job": "Sound Re-Recording Mixer", "name": "William Stein"}, {"credit_id": "54491f500e0a26747c001c07", "department": "Crew", "gender": 0, "id": 1376909, "job": "Choreographer", "name": "Lula Washington"}, {"credit_id": "549599239251412c4e002a2e", "department": "Visual Effects", "gender": 0, "id": 1391692, "job": "Visual Effects Producer", "name": "Chris Del Conte"}, {"credit_id": "54959d54c3a36831b8001d9a", "department": "Visual Effects", "gender": 2, "id": 1391695, "job": "Visual Effects Supervisor", "name": "R. Christopher White"}, {"credit_id": "54959bdf9251412c4e002a66", "department": "Visual Effects", "gender": 0, "id": 1394070, "job": "Visual Effects Supervisor", "name": "Dan Lemmon"}, {"credit_id": "5495971d92514132ed002922", "department": "Sound", "gender": 0, "id": 1394129, "job": "Sound Effects Editor", "name": "Tim Nielsen"}, {"credit_id": "5592b25792514152cc0011aa", "department": "Crew", "gender": 0, "id": 1394286, "job": "CG Supervisor", "name": "Michael Mulholland"}, {"credit_id": "54959a329251416e2b004355", "department": "Crew", "gender": 0, "id": 1394750, "job": "Visual Effects Editor", "name": "Thomas Nittmann"}, {"credit_id": "54959d6dc3a3686ae9004401", "department": "Visual Effects", "gender": 0, "id": 1394755, "job": "Visual Effects Supervisor", "name": "Edson Williams"}, {"credit_id": "5495a08fc3a3686ae300441c", "department": "Editing", "gender": 0, "id": 1394953, "job": "Digital Intermediate", "name": "Christine Carr"}, {"credit_id": "55402d659251413d6d000249", "department": "Visual Effects", "gender": 0, "id": 1395269, "job": "Visual Effects Supervisor", "name": "John Bruno"}, {"credit_id": "54959e7b9251416e1e003f3e", "department": "Camera", "gender": 0, "id": 1398970, "job": "Steadicam Operator", "name": "David Emmerichs"}, {"credit_id": "54959734c3a3686ae10045e0", "department": "Sound", "gender": 0, "id": 1400906, "job": "Sound Effects Editor", "name": "Christopher Scarabosio"}, {"credit_id": "549595dd92514130fc002d79", "department": "Production", "gender": 0, "id": 1401784, "job": "Production Supervisor", "name": "Jennifer Teves"}, {"credit_id": "549596009251413af70028cc", "department": "Production", "gender": 0, "id": 1401785, "job": "Production Manager", "name": "Brigitte Yorke"}, {"credit_id": "549596e892514130fc002d99", "department": "Sound", "gender": 0, "id": 1401786, "job": "Sound Effects Editor", "name": "Ken Fischer"}, {"credit_id": "549598229251412c4e002a1c", "department": "Crew", "gender": 0, "id": 1401787, "job": "Special Effects Coordinator", "name": "Iain Hutton"}, {"credit_id": "549598349251416e2b00432b", "department": "Crew", "gender": 0, "id": 1401788, "job": "Special Effects Coordinator", "name": "Steve Ingram"}, {"credit_id": "54959905c3a3686ae3004324", "department": "Visual Effects", "gender": 0, "id": 1401789, "job": "Visual Effects Producer", "name": "Joyce Cox"}, {"credit_id": "5495994b92514132ed002951", "department": "Visual Effects", "gender": 0, "id": 1401790, "job": "Visual Effects Producer", "name": "Jenny Foster"}, {"credit_id": "549599cbc3a3686ae1004613", "department": "Crew", "gender": 0, "id": 1401791, "job": "Visual Effects Editor", "name": "Christopher Marino"}, {"credit_id": "549599f2c3a3686ae100461e", "department": "Crew", "gender": 0, "id": 1401792, "job": "Visual Effects Editor", "name": "Jim Milton"}, {"credit_id": "54959a51c3a3686af3003eb5", "department": "Visual Effects", "gender": 0, "id": 1401793, "job": "Visual Effects Producer", "name": "Cyndi Ochs"}, {"credit_id": "54959a7cc3a36811530026f4", "department": "Crew", "gender": 0, "id": 1401794, "job": "Visual Effects Editor", "name": "Lucas Putnam"}, {"credit_id": "54959b91c3a3680ff5002cb4", "department": "Visual Effects", "gender": 0, "id": 1401795, "job": "Visual Effects Supervisor", "name": "Anthony \'Max\' Ivins"}, {"credit_id": "54959bb69251412c4e002a5f", "department": "Visual Effects", "gender": 0, "id": 1401796, "job": "Visual Effects Supervisor", "name": "John Knoll"}, {"credit_id": "54959cbbc3a3686ae3004391", "department": "Visual Effects", "gender": 2, "id": 1401799, "job": "Visual Effects Supervisor", "name": "Eric Saindon"}, {"credit_id": "54959d06c3a3686ae90043f6", "department": "Visual Effects", "gender": 0, "id": 1401800, "job": "Visual Effects Supervisor", "name": "Wayne Stables"}, {"credit_id": "54959d259251416e1e003f11", "department": "Visual Effects", "gender": 0, "id": 1401801, "job": "Visual Effects Supervisor", "name": "David Stinnett"}, {"credit_id": "54959db49251413af7002975", "department": "Visual Effects", "gender": 0, "id": 1401803, "job": "Visual Effects Supervisor", "name": "Guy Williams"}, {"credit_id": "54959de4c3a3681153002750", "department": "Crew", "gender": 0, "id": 1401804, "job": "Stunt Coordinator", "name": "Stuart Thorp"}, {"credit_id": "54959ef2c3a3680fc60027f2", "department": "Lighting", "gender": 0, "id": 1401805, "job": "Best Boy Electric", "name": "Giles Coburn"}, {"credit_id": "54959f07c3a3680fc60027f9", "department": "Camera", "gender": 2, "id": 1401806, "job": "Still Photographer", "name": "Mark Fellman"}, {"credit_id": "54959f47c3a3681153002774", "department": "Lighting", "gender": 0, "id": 1401807, "job": "Lighting Technician", "name": "Scott Sprague"}, {"credit_id": "54959f8cc3a36831b8001df2", "department": "Visual Effects", "gender": 0, "id": 1401808, "job": "Animation Director", "name": "Jeremy Hollobon"}, {"credit_id": "54959fa0c3a36831b8001dfb", "department": "Visual Effects", "gender": 0, "id": 1401809, "job": "Animation Director", "name": "Orlando Meunier"}, {"credit_id": "54959fb6c3a3686af3003f54", "department": "Visual Effects", "gender": 0, "id": 1401810, "job": "Animation Director", "name": "Taisuke Tanimura"}, {"credit_id": "54959fd2c3a36831b8001e02", "department": "Costume & Make-Up", "gender": 0, "id": 1401812, "job": "Set Costumer", "name": "Lilia Mishel Acevedo"}, {"credit_id": "54959ff9c3a3686ae300440c", "department": "Costume & Make-Up", "gender": 0, "id": 1401814, "job": "Set Costumer", "name": "Alejandro M. Hernandez"}, {"credit_id": "5495a0ddc3a3686ae10046fe", "department": "Editing", "gender": 0, "id": 1401815, "job": "Digital Intermediate", "name": "Marvin Hall"}, {"credit_id": "5495a1f7c3a3686ae3004443", "department": "Production", "gender": 0, "id": 1401816, "job": "Publicist", "name": "Judy Alley"}, {"credit_id": "5592b29fc3a36869d100002f", "department": "Crew", "gender": 0, "id": 1418381, "job": "CG Supervisor", "name": "Mike Perry"}, {"credit_id": "5592b23a9251415df8001081", "department": "Crew", "gender": 0, "id": 1426854, "job": "CG Supervisor", "name": "Andrew Morley"}, {"credit_id": "55491e1192514104c40002d8", "department": "Art", "gender": 0, "id": 1438901, "job": "Conceptual Design", "name": "Seth Engstrom"}, {"credit_id": "5525d5809251417276002b06", "department": "Crew", "gender": 0, "id": 1447362, "job": "Visual Effects Art Director", "name": "Eric Oliver"}, {"credit_id": "554427ca925141586500312a", "department": "Visual Effects", "gender": 0, "id": 1447503, "job": "Modeling", "name": "Matsune Suzuki"}, {"credit_id": "551906889251415aab001c88", "department": "Art", "gender": 0, "id": 1447524, "job": "Art Department Manager", "name": "Paul Tobin"}, {"credit_id": "5592af8492514152cc0010de", "department": "Costume & Make-Up", "gender": 0, "id": 1452643, "job": "Hairstylist", "name": "Roxane Griffin"}, {"credit_id": "553d3c109251415852001318", "department": "Lighting", "gender": 0, "id": 1453938, "job": "Lighting Artist", "name": "Arun Ram-Mohan"}, {"credit_id": "5592af4692514152d5001355", "department": "Costume & Make-Up", "gender": 0, "id": 1457305, "job": "Makeup Artist", "name": "Georgia Lockhart-Adams"}, {"credit_id": "5592b2eac3a36877470012a5", "department": "Crew", "gender": 0, "id": 1466035, "job": "CG Supervisor", "name": "Thrain Shadbolt"}, {"credit_id": "5592b032c3a36877450015f1", "department": "Crew", "gender": 0, "id": 1483220, "job": "CG Supervisor", "name": "Brad Alexander"}, {"credit_id": "5592b05592514152d80012f6", "department": "Crew", "gender": 0, "id": 1483221, "job": "CG Supervisor", "name": "Shadi Almassizadeh"}, {"credit_id": "5592b090c3a36877570010b5", "department": "Crew", "gender": 0, "id": 1483222, "job": "CG Supervisor", "name": "Simon Clutterbuck"}, {"credit_id": "5592b0dbc3a368774b00112c", "department": "Crew", "gender": 0, "id": 1483223, "job": "CG Supervisor", "name": "Graeme Demmocks"}, {"credit_id": "5592b0fe92514152db0010c1", "department": "Crew", "gender": 0, "id": 1483224, "job": "CG Supervisor", "name": "Adrian Fernandes"}, {"credit_id": "5592b11f9251415df8001059", "department": "Crew", "gender": 0, "id": 1483225, "job": "CG Supervisor", "name": "Mitch Gates"}, {"credit_id": "5592b15dc3a3687745001645", "department": "Crew", "gender": 0, "id": 1483226, "job": "CG Supervisor", "name": "Jerry Kung"}, {"credit_id": "5592b18e925141645a0004ae", "department": "Crew", "gender": 0, "id": 1483227, "job": "CG Supervisor", "name": "Andy Lomas"}, {"credit_id": "5592b1bfc3a368775d0010e7", "department": "Crew", "gender": 0, "id": 1483228, "job": "CG Supervisor", "name": "Sebastian Marino"}, {"credit_id": "5592b2049251415df8001078", "department": "Crew", "gender": 0, "id": 1483229, "job": "CG Supervisor", "name": "Matthias Menz"}, {"credit_id": "5592b27b92514152d800136a", "department": "Crew", "gender": 0, "id": 1483230, "job": "CG Supervisor", "name": "Sergei Nevshupov"}, {"credit_id": "5592b2c3c3a36869e800003c", "department": "Crew", "gender": 0, "id": 1483231, "job": "CG Supervisor", "name": "Philippe Rebours"}, {"credit_id": "5592b317c3a36877470012af", "department": "Crew", "gender": 0, "id": 1483232, "job": "CG Supervisor", "name": "Michael Takarangi"}, {"credit_id": "5592b345c3a36877470012bb", "department": "Crew", "gender": 0, "id": 1483233, "job": "CG Supervisor", "name": "David Weitzberg"}, {"credit_id": "5592b37cc3a368775100113b", "department": "Crew", "gender": 0, "id": 1483234, "job": "CG Supervisor", "name": "Ben White"}, {"credit_id": "573c8e2f9251413f5d000094", "department": "Crew", "gender": 1, "id": 1621932, "job": "Stunts", "name": "Min Windle"}]'




```python
def fetch_director(obj):
    L=[]
    for i in ast.literal_eval(obj):
        if i ['job']=='Director':
            L.append(i['name'])
            break
    return L
```


```python
movies['crew'].apply(fetch_director)
```




    0           [James Cameron]
    1          [Gore Verbinski]
    2              [Sam Mendes]
    3       [Christopher Nolan]
    4          [Andrew Stanton]
                   ...         
    4804     [Robert Rodriguez]
    4805         [Edward Burns]
    4806          [Scott Smith]
    4807          [Daniel Hsia]
    4808     [Brian Herzlinger]
    Name: crew, Length: 4806, dtype: object




```python
movies['crew']=movies['crew'].apply(fetch_director)
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[James Cameron]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[Gore Verbinski]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[Sam Mendes]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[Christopher Nolan]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[Andrew Stanton]</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['overview'][0] #its a string
```




    'In the 22nd century, a paraplegic Marine is dispatched to the moon Pandora on a unique mission, but becomes torn between following orders and protecting an alien civilization.'




```python
#to convert string into list
movies['overview'].apply(lambda x:x.split())
```




    0       [In, the, 22nd, century,, a, paraplegic, Marin...
    1       [Captain, Barbossa,, long, believed, to, be, d...
    2       [A, cryptic, message, from, Bond’s, past, send...
    3       [Following, the, death, of, District, Attorney...
    4       [John, Carter, is, a, war-weary,, former, mili...
                                  ...                        
    4804    [El, Mariachi, just, wants, to, play, his, gui...
    4805    [A, newlywed, couple's, honeymoon, is, upended...
    4806    ["Signed,, Sealed,, Delivered", introduces, a,...
    4807    [When, ambitious, New, York, attorney, Sam, is...
    4808    [Ever, since, the, second, grade, when, he, fi...
    Name: overview, Length: 4806, dtype: object




```python
movies['overview']=movies['overview'].apply(lambda x:x.split())
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[James Cameron]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[Gore Verbinski]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[Sam Mendes]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[Christopher Nolan]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[Andrew Stanton]</td>
    </tr>
  </tbody>
</table>
</div>




```python
movies['tags']=movies['overview']+movies['genres']+movies['keywords']+movies['cast']+movies['crew']
```


```python
movies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>overview</th>
      <th>genres</th>
      <th>keywords</th>
      <th>cast</th>
      <th>crew</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
      <td>[Action, Adventure, Fantasy, Science Fiction]</td>
      <td>[culture clash, future, space war, space colon...</td>
      <td>[Sam Worthington, Zoe Saldana, Sigourney Weaver]</td>
      <td>[James Cameron]</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
      <td>[Adventure, Fantasy, Action]</td>
      <td>[ocean, drug abuse, exotic island, east india ...</td>
      <td>[Johnny Depp, Orlando Bloom, Keira Knightley]</td>
      <td>[Gore Verbinski]</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
      <td>[Action, Adventure, Crime]</td>
      <td>[spy, based on novel, secret agent, sequel, mi...</td>
      <td>[Daniel Craig, Christoph Waltz, Léa Seydoux]</td>
      <td>[Sam Mendes]</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
      <td>[Action, Crime, Drama, Thriller]</td>
      <td>[dc comics, crime fighter, terrorist, secret i...</td>
      <td>[Christian Bale, Michael Caine, Gary Oldman]</td>
      <td>[Christopher Nolan]</td>
      <td>[Following, the, death, of, District, Attorney...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
      <td>[Action, Adventure, Science Fiction]</td>
      <td>[based on novel, mars, medallion, space travel...</td>
      <td>[Taylor Kitsch, Lynn Collins, Samantha Morton]</td>
      <td>[Andrew Stanton]</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df=movies[['movie_id','title','tags']]
```


```python
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>[In, the, 22nd, century,, a, paraplegic, Marin...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>[Captain, Barbossa,, long, believed, to, be, d...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>[A, cryptic, message, from, Bond’s, past, send...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>[Following, the, death, of, District, Attorney...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>[John, Carter, is, a, war-weary,, former, mili...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>[El, Mariachi, just, wants, to, play, his, gui...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>[A, newlywed, couple's, honeymoon, is, upended...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>["Signed,, Sealed,, Delivered", introduces, a,...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>[When, ambitious, New, York, attorney, Sam, is...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>[Ever, since, the, second, grade, when, he, fi...</td>
    </tr>
  </tbody>
</table>
<p>4806 rows × 3 columns</p>
</div>




```python
new_df['tags'].apply(lambda x:" ".join(x))
```




    0       In the 22nd century, a paraplegic Marine is di...
    1       Captain Barbossa, long believed to be dead, ha...
    2       A cryptic message from Bond’s past sends him o...
    3       Following the death of District Attorney Harve...
    4       John Carter is a war-weary, former military ca...
                                  ...                        
    4804    El Mariachi just wants to play his guitar and ...
    4805    A newlywed couple's honeymoon is upended by th...
    4806    "Signed, Sealed, Delivered" introduces a dedic...
    4807    When ambitious New York attorney Sam is sent t...
    4808    Ever since the second grade when he first saw ...
    Name: tags, Length: 4806, dtype: object




```python
new_df['tags']=new_df['tags'].apply(lambda x:" ".join(x))
```

    C:\Users\zoaah\AppData\Local\Temp\ipykernel_10508\487797088.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      new_df['tags']=new_df['tags'].apply(lambda x:" ".join(x))
    


```python
new_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>In the 22nd century, a paraplegic Marine is di...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>Captain Barbossa, long believed to be dead, ha...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>A cryptic message from Bond’s past sends him o...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>Following the death of District Attorney Harve...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>John Carter is a war-weary, former military ca...</td>
    </tr>
  </tbody>
</table>
</div>




```python
new_df['tags'][0]
```




    'in the 22nd century, a parapleg marin is dispatch to the moon pandora on a uniqu mission, but becom torn between follow order and protect an alien civilization. action adventur fantasi scienc fiction cultur clash futur space war space coloni societi space travel futurist romanc space alien tribe alien planet cgi marin soldier battl love affair anti war power relat mind and soul 3d sam worthington zoe saldana sigourney weaver jame cameron'




```python
new_df['tags'][1]
```




    "captain barbossa, long believ to be dead, ha come back to life and is head to the edg of the earth with will turner and elizabeth swann. but noth is quit as it seems. adventur fantasi action ocean drug abus exot island east india trade compani love of one' life traitor shipwreck strong woman ship allianc calypso afterlif fighter pirat swashbuckl aftercreditssting johnni depp orlando bloom keira knightley gore verbinski"




```python
!pip install nltk
```

    Requirement already satisfied: nltk in c:\users\zoaah\anaconda4\lib\site-packages (3.7)
    Requirement already satisfied: click in c:\users\zoaah\anaconda4\lib\site-packages (from nltk) (8.0.4)
    Requirement already satisfied: joblib in c:\users\zoaah\anaconda4\lib\site-packages (from nltk) (1.1.1)
    Requirement already satisfied: tqdm in c:\users\zoaah\anaconda4\lib\site-packages (from nltk) (4.64.1)
    Requirement already satisfied: regex>=2021.8.3 in c:\users\zoaah\anaconda4\lib\site-packages (from nltk) (2022.7.9)
    Requirement already satisfied: colorama in c:\users\zoaah\anaconda4\lib\site-packages (from click->nltk) (0.4.6)
    


```python
import nltk
```


```python
from nltk.stem.porter import PorterStemmer
ps=PorterStemmer()
```


```python
def stem(text):
    y=[]
    for i in text.split():
        y.append(ps.stem(i))
    return " ".join(y)
```


```python
new_df['tags'].apply(stem)
```




    0       in the 22nd century, a parapleg marin is dispa...
    1       captain barbossa, long believ to be dead, ha c...
    2       a cryptic messag from bond’ past send him on a...
    3       follow the death of district attorney harvey d...
    4       john carter is a war-weary, former militari ca...
                                  ...                        
    4804    el mariachi just want to play hi guitar and ca...
    4805    a newlyw couple' honeymoon is upend by the arr...
    4806    "signed, sealed, delivered" introduc a dedic q...
    4807    when ambiti new york attorney sam is sent to s...
    4808    ever sinc the second grade when he first saw h...
    Name: tags, Length: 4806, dtype: object




```python
new_df['tags']=new_df['tags'].apply(stem)
```

    C:\Users\zoaah\AppData\Local\Temp\ipykernel_10508\3514595201.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      new_df['tags']=new_df['tags'].apply(stem)
    


```python
from sklearn.feature_extraction.text import CountVectorizer
cv = CountVectorizer(max_features=5000,stop_words='english')
    
```


```python
cv.fit_transform(new_df['tags']).toarray()

```




    array([[0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           ...,
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0]], dtype=int64)




```python
cv.fit_transform(new_df['tags']).toarray().shape


```




    (4806, 5000)




```python
vector = cv.fit_transform(new_df['tags']).toarray()

```


```python
vector
```




    array([[0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           ...,
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0],
           [0, 0, 0, ..., 0, 0, 0]], dtype=int64)




```python
vector[0]
```




    array([0, 0, 0, ..., 0, 0, 0], dtype=int64)




```python
cv.get_feature_names_out()
```




    array(['000', '007', '10', ..., 'zooey', 'zucker', 'zwick'], dtype=object)




```python
len(cv.get_feature_names_out())
```




    5000




```python
from sklearn.metrics.pairwise import cosine_similarity
```


```python
 cosine_similarity(vector)
```




    array([[1.        , 0.06692745, 0.06554735, ..., 0.04442617, 0.03121953,
            0.        ],
           [0.06692745, 1.        , 0.04167571, ..., 0.03766218, 0.        ,
            0.01756008],
           [0.06554735, 0.04167571, 1.        , ..., 0.01844278, 0.07776158,
            0.        ],
           ...,
           [0.04442617, 0.03766218, 0.01844278, ..., 1.        , 0.03513642,
            0.03108349],
           [0.03121953, 0.        , 0.07776158, ..., 0.03513642, 1.        ,
            0.06552976],
           [0.        , 0.01756008, 0.        , ..., 0.03108349, 0.06552976,
            1.        ]])




```python
cosine_similarity(vector).shape
```




    (4806, 4806)




```python
similarity = cosine_similarity(vector)

```


```python
similarity
```




    array([[1.        , 0.06692745, 0.06554735, ..., 0.04442617, 0.03121953,
            0.        ],
           [0.06692745, 1.        , 0.04167571, ..., 0.03766218, 0.        ,
            0.01756008],
           [0.06554735, 0.04167571, 1.        , ..., 0.01844278, 0.07776158,
            0.        ],
           ...,
           [0.04442617, 0.03766218, 0.01844278, ..., 1.        , 0.03513642,
            0.03108349],
           [0.03121953, 0.        , 0.07776158, ..., 0.03513642, 1.        ,
            0.06552976],
           [0.        , 0.01756008, 0.        , ..., 0.03108349, 0.06552976,
            1.        ]])




```python
similarity[1]
```




    array([0.06692745, 1.        , 0.04167571, ..., 0.03766218, 0.        ,
           0.01756008])




```python
sorted(list(enumerate(similarity[0])),reverse=True,key = lambda x: x[1])[1:6]
```




    [(2409, 0.4935676473963735),
     (4336, 0.4113063728303113),
     (1537, 0.3880712182748949),
     (3162, 0.3856962663899156),
     (373, 0.3804429551263411)]




```python
def recommend(movie):
    movie_index = new_df[new_df['title'] == movie].index[0]
    distances=similarity[movie_index]
    movie_list=sorted(list(enumerate(distances)),reverse=True,key = lambda x: x[1])[1:6]
    for i in movie_list:
        print(i[0])
        
    
```


```python
recommend('Avatar')
```

    2409
    4336
    1537
    3162
    373
    


```python
new_df.iloc[1216]
```




    movie_id                                                  440
    title                             Aliens vs Predator: Requiem
    tags        a sequel to 2004' alien vs. predator, the icon...
    Name: 1216, dtype: object




```python
new_df.iloc[1216].title
```




    'Aliens vs Predator: Requiem'




```python
new_df.iloc[4336].title
```




    'Silent Running'




```python
def recommend(movie):
    movie_index = new_df[new_df['title'] == movie].index[0]
    distances=similarity[movie_index]
    movie_list=sorted(list(enumerate(distances)),reverse=True,key = lambda x: x[1])[1:6]
    for i in movie_list:
        print(new_df.iloc[i[0]].title)
        
    
```


```python
recommend('Avatar')
```

    Aliens
    Silent Running
    Moonraker
    Alien
    Mission to Mars
    


```python
recommend('Batman Begins')
```

    The Dark Knight
    The Dark Knight Rises
    Batman
    Batman
    Batman & Robin
    


```python
import pickle
```


```python
pickle.dump(new_df,open('movies.pkl','wb'))
```


```python
new_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movie_id</th>
      <th>title</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19995</td>
      <td>Avatar</td>
      <td>in the 22nd century, a parapleg marin is dispa...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>285</td>
      <td>Pirates of the Caribbean: At World's End</td>
      <td>captain barbossa, long believ to be dead, ha c...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>206647</td>
      <td>Spectre</td>
      <td>a cryptic messag from bond’ past send him on a...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>49026</td>
      <td>The Dark Knight Rises</td>
      <td>follow the death of district attorney harvey d...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>49529</td>
      <td>John Carter</td>
      <td>john carter is a war-weary, former militari ca...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4804</th>
      <td>9367</td>
      <td>El Mariachi</td>
      <td>el mariachi just want to play hi guitar and ca...</td>
    </tr>
    <tr>
      <th>4805</th>
      <td>72766</td>
      <td>Newlyweds</td>
      <td>a newlyw couple' honeymoon is upend by the arr...</td>
    </tr>
    <tr>
      <th>4806</th>
      <td>231617</td>
      <td>Signed, Sealed, Delivered</td>
      <td>"signed, sealed, delivered" introduc a dedic q...</td>
    </tr>
    <tr>
      <th>4807</th>
      <td>126186</td>
      <td>Shanghai Calling</td>
      <td>when ambiti new york attorney sam is sent to s...</td>
    </tr>
    <tr>
      <th>4808</th>
      <td>25975</td>
      <td>My Date with Drew</td>
      <td>ever sinc the second grade when he first saw h...</td>
    </tr>
  </tbody>
</table>
<p>4806 rows × 3 columns</p>
</div>




```python
new_df['title'].values
```




    array(['Avatar', "Pirates of the Caribbean: At World's End", 'Spectre',
           ..., 'Signed, Sealed, Delivered', 'Shanghai Calling',
           'My Date with Drew'], dtype=object)




```python
new_df.to_dict()
```




    {'movie_id': {0: 19995,
      1: 285,
      2: 206647,
      3: 49026,
      4: 49529,
      5: 559,
      6: 38757,
      7: 99861,
      8: 767,
      9: 209112,
      10: 1452,
      11: 10764,
      12: 58,
      13: 57201,
      14: 49521,
      15: 2454,
      16: 24428,
      17: 1865,
      18: 41154,
      19: 122917,
      20: 1930,
      21: 20662,
      22: 57158,
      23: 2268,
      24: 254,
      25: 597,
      26: 271110,
      27: 44833,
      28: 135397,
      29: 37724,
      30: 558,
      31: 68721,
      32: 12155,
      33: 36668,
      34: 62211,
      35: 8373,
      36: 91314,
      37: 68728,
      38: 102382,
      39: 20526,
      40: 49013,
      41: 44912,
      42: 10193,
      43: 534,
      44: 168259,
      45: 72190,
      46: 127585,
      47: 54138,
      48: 81005,
      49: 64682,
      50: 9543,
      51: 68726,
      52: 38356,
      53: 217,
      54: 105864,
      55: 62177,
      56: 188927,
      57: 10681,
      58: 5174,
      59: 14161,
      60: 17979,
      61: 76757,
      62: 258489,
      63: 411,
      64: 246655,
      65: 155,
      66: 14160,
      67: 15512,
      68: 1726,
      69: 44826,
      70: 8487,
      71: 1735,
      72: 297761,
      73: 2698,
      74: 137113,
      75: 9804,
      76: 14869,
      77: 150540,
      78: 278927,
      79: 10138,
      80: 58595,
      81: 102651,
      82: 119450,
      83: 79698,
      84: 64686,
      85: 100402,
      86: 10192,
      87: 158852,
      88: 177572,
      89: 82690,
      90: 5255,
      91: 47933,
      92: 10191,
      93: 296,
      94: 118340,
      95: 157336,
      96: 27205,
      97: 315011,
      98: 49051,
      99: 9799,
      100: 4922,
      101: 49538,
      102: 131634,
      103: 27022,
      104: 503,
      105: 241259,
      106: 810,
      107: 68735,
      108: 87101,
      109: 10140,
      110: 676,
      111: 1858,
      112: 1966,
      113: 675,
      114: 674,
      115: 8960,
      116: 6479,
      117: 118,
      118: 2062,
      119: 272,
      120: 10527,
      121: 18360,
      122: 2080,
      123: 605,
      124: 109445,
      125: 604,
      126: 76338,
      127: 76341,
      128: 13448,
      129: 10195,
      130: 13053,
      131: 19585,
      132: 57165,
      133: 62213,
      134: 177677,
      135: 7978,
      136: 5559,
      137: 49444,
      138: 10196,
      139: 956,
      140: 117251,
      141: 50321,
      142: 11619,
      143: 266647,
      144: 82703,
      145: 652,
      146: 80321,
      147: 36669,
      148: 43074,
      149: 95,
      150: 608,
      151: 2310,
      152: 140300,
      153: 56292,
      154: 81188,
      155: 7552,
      156: 616,
      157: 147441,
      158: 13475,
      159: 557,
      160: 82702,
      161: 205584,
      162: 10048,
      163: 13183,
      164: 944,
      165: 1927,
      166: 72559,
      167: 7364,
      168: 2114,
      169: 1771,
      170: 36643,
      171: 8619,
      172: 50620,
      173: 65759,
      174: 1724,
      175: 267935,
      176: 281957,
      177: 77950,
      178: 44896,
      179: 270946,
      180: 2503,
      181: 9502,
      182: 102899,
      183: 101299,
      184: 228161,
      185: 74,
      186: 8961,
      187: 417859,
      188: 27576,
      189: 86834,
      190: 17578,
      191: 673,
      192: 6972,
      193: 82700,
      194: 10567,
      195: 181533,
      196: 38055,
      197: 671,
      198: 49524,
      199: 22,
      200: 131631,
      201: 591,
      202: 172385,
      203: 36658,
      204: 51497,
      205: 58574,
      206: 18823,
      207: 861,
      208: 1911,
      209: 49040,
      210: 415,
      211: 8871,
      212: 435,
      213: 955,
      214: 2133,
      215: 1979,
      216: 87827,
      217: 1250,
      218: 324668,
      219: 9471,
      220: 70981,
      221: 10996,
      222: 68724,
      223: 2789,
      224: 97020,
      225: 7459,
      226: 42888,
      227: 37834,
      228: 75612,
      229: 1895,
      230: 1894,
      231: 585,
      232: 76170,
      233: 1893,
      234: 49519,
      235: 2395,
      236: 12100,
      237: 290595,
      238: 98566,
      239: 49047,
      240: 9619,
      241: 308531,
      242: 166424,
      243: 1593,
      244: 254128,
      245: 714,
      246: 2024,
      247: 163,
      248: 787,
      249: 262500,
      250: 2567,
      251: 38745,
      252: 40805,
      253: 53182,
      254: 41513,
      255: 13700,
      256: 262504,
      257: 39254,
      258: 77931,
      259: 1639,
      260: 80274,
      261: 1571,
      262: 120,
      263: 10204,
      264: 8489,
      265: 10588,
      266: 2048,
      267: 1495,
      268: 10137,
      269: 10198,
      270: 286217,
      271: 1635,
      272: 24113,
      273: 9679,
      274: 98,
      275: 180,
      276: 672,
      277: 36557,
      278: 869,
      279: 280,
      280: 11322,
      281: 4982,
      282: 36955,
      283: 18487,
      284: 39451,
      285: 27581,
      286: 9268,
      287: 68718,
      288: 10545,
      289: 11688,
      290: 76163,
      291: 2059,
      292: 2486,
      293: 16523,
      294: 116711,
      295: 37710,
      296: 9946,
      297: 1372,
      298: 106646,
      299: 414,
      300: 563,
      301: 83542,
      302: 41216,
      303: 314,
      304: 184315,
      305: 9016,
      306: 18162,
      307: 138103,
      308: 257088,
      309: 10214,
      310: 205775,
      311: 11692,
      312: 22972,
      313: 227973,
      314: 29193,
      315: 1734,
      316: 3131,
      317: 76758,
      318: 9408,
      319: 9890,
      320: 855,
      321: 77953,
      322: 18,
      323: 37786,
      324: 10501,
      325: 57800,
      326: 150689,
      327: 7980,
      328: 12,
      329: 122,
      330: 121,
      331: 68737,
      332: 1995,
      333: 157353,
      334: 331,
      335: 61791,
      336: 8204,
      337: 47964,
      338: 10733,
      339: 9806,
      340: 1408,
      341: 32657,
      342: 607,
      343: 863,
      344: 44048,
      345: 5175,
      346: 2655,
      347: 22794,
      348: 8355,
      349: 116745,
      350: 4327,
      351: 1422,
      352: 10674,
      353: 7446,
      354: 65754,
      355: 1572,
      356: 10528,
      357: 271969,
      358: 10865,
      359: 258509,
      360: 2253,
      361: 10661,
      362: 257344,
      363: 644,
      364: 10756,
      365: 686,
      366: 9383,
      367: 179,
      368: 76285,
      369: 1996,
      370: 291805,
      371: 10003,
      372: 1535,
      373: 2067,
      374: 46195,
      375: 2277,
      376: 10357,
      377: 4477,
      378: 8665,
      379: 9387,
      380: 921,
      381: 49852,
      382: 4464,
      383: 664,
      384: 8358,
      385: 9836,
      386: 2502,
      387: 9772,
      388: 161,
      389: 52451,
      390: 76492,
      391: 4523,
      392: 59961,
      393: 10481,
      394: 59108,
      395: 1581,
      396: 9798,
      397: 22897,
      398: 298,
      399: 7484,
      400: 157350,
      401: 853,
      402: 10159,
      403: 9593,
      404: 1904,
      405: 9615,
      406: 51052,
      407: 297,
      408: 9884,
      409: 16858,
      410: 62764,
      411: 22538,
      412: 9341,
      413: 12107,
      414: 9637,
      415: 49049,
      416: 9339,
      417: 16281,
      418: 39691,
      419: 8247,
      420: 11253,
      421: 1949,
      422: 8452,
      423: 310,
      424: 27578,
      425: 954,
      426: 70160,
      427: 45243,
      428: 364,
      429: 7518,
      430: 11544,
      431: 9986,
      432: 8656,
      433: 146216,
      434: 9291,
      435: 55301,
      436: 109418,
      437: 11665,
      438: 6964,
      439: 11324,
      440: 12193,
      441: 9928,
      442: 754,
      443: 10202,
      444: 4147,
      445: 50546,
      446: 1701,
      447: 13027,
      448: 2289,
      449: 20504,
      450: 9574,
      451: 11618,
      452: 2300,
      453: 12096,
      454: 10200,
      455: 8834,
      456: 228150,
      457: 6068,
      458: 41515,
      459: 9023,
      460: 38317,
      461: 2157,
      462: 14462,
      463: 161795,
      464: 159824,
      465: 49948,
      466: 2135,
      467: 9822,
      468: 9705,
      469: 1656,
      470: 12159,
      471: 9678,
      472: 4442,
      473: 75,
      474: 330770,
      475: 9433,
      476: 19959,
      477: 11973,
      478: 11228,
      479: 77951,
      480: 5491,
      481: 10715,
      482: 10197,
      483: 9562,
      484: 9922,
      485: 9447,
      486: 274854,
      487: 8870,
      488: 9992,
      489: 36970,
      490: 10077,
      491: 76649,
      492: 293644,
      493: 453,
      494: 8587,
      495: 72545,
      496: 109451,
      497: 9533,
      498: 2023,
      499: 71880,
      500: 584,
      501: 309809,
      502: 4858,
      503: 17711,
      504: 328111,
      505: 8698,
      506: 93456,
      507: 602,
      508: 330,
      509: 953,
      510: 9693,
      511: 36657,
      512: 8909,
      513: 9802,
      514: 950,
      515: 1824,
      516: 2976,
      517: 11026,
      518: 332,
      519: 75656,
      520: 38365,
      521: 594,
      522: 15189,
      523: 11678,
      524: 6538,
      525: 10555,
      526: 1125,
      527: 4551,
      528: 612,
      529: 9567,
      530: 37821,
      531: 203801,
      532: 2539,
      533: 9297,
      534: 3172,
      535: 6520,
      536: 1439,
      537: 37958,
      538: 2026,
      539: 7450,
      540: 11375,
      541: 9425,
      542: 25769,
      543: 23685,
      544: 11866,
      545: 9741,
      546: 211672,
      547: 23629,
      548: 8688,
      549: 10153,
      550: 153518,
      551: 8676,
      552: 20829,
      553: 4349,
      554: 9718,
      555: 10808,
      556: 197,
      557: 25,
      558: 35,
      559: 11086,
      560: 10477,
      561: 1997,
      562: 6947,
      563: 3050,
      564: 2675,
      565: 809,
      566: 920,
      567: 4806,
      568: 7451,
      569: 228165,
      570: 3595,
      571: 16869,
      572: 879,
      573: 1573,
      574: 9257,
      575: 1903,
      576: 9697,
      577: 395,
      578: 23398,
      579: 10590,
      580: 117263,
      581: 200,
      582: 44943,
      583: 587,
      584: 10395,
      585: 57212,
      586: 152760,
      587: 2756,
      588: 33909,
      589: 49017,
      590: 9882,
      591: 2270,
      592: 978,
      593: 44564,
      594: 3132,
      595: 8814,
      596: 8427,
      597: 52520,
      598: 80585,
      599: 10592,
      600: 49021,
      601: 11535,
      602: 10550,
      603: 11258,
      604: 12610,
      605: 59981,
      606: 201088,
      607: 5137,
      608: 3093,
      609: 107846,
      610: 188207,
      611: 4614,
      612: 24021,
      613: 11371,
      614: 20352,
      615: 11517,
      616: 214756,
      617: 26428,
      618: 9824,
      619: 48988,
      620: 9008,
      621: 300673,
      622: 12113,
      623: 38778,
      624: 72331,
      625: 1844,
      626: 846,
      627: 9703,
      628: 857,
      629: 136797,
      630: 3981,
      631: 425,
      632: 6171,
      633: 72976,
      634: 603,
      635: 568,
      636: 9021,
      637: 82695,
      638: 9489,
      639: 12133,
      640: 9342,
      641: 41733,
      642: 227306,
      643: 5551,
      644: 9350,
      645: 9208,
      646: 4244,
      647: 1852,
      648: 11820,
      649: 76493,
      650: 345,
      651: 196867,
      652: 256591,
      653: 59962,
      654: 36648,
      655: 1880,
      656: 9440,
      657: 71679,
      658: 10483,
      659: 11412,
      660: 11983,
      661: 6795,
      662: 550,
      663: 11170,
      664: 9292,
      665: 10783,
      666: 100241,
      667: 257,
      668: 9947,
      669: 189,
      670: 12618,
      671: 253412,
      672: 1427,
      673: 818,
      674: 16577,
      675: 329,
      676: 12160,
      677: 9331,
      678: 300168,
      679: 9072,
      680: 3536,
      681: 9087,
      682: 12177,
      683: 12138,
      684: 273248,
      685: 9955,
      686: 50359,
      687: 1271,
      688: 693,
      689: 14306,
      690: 497,
      691: 11199,
      692: 9982,
      693: 210577,
      694: 2501,
      695: 710,
      696: 2275,
      697: 37165,
      698: 9837,
      699: 10708,
      700: 136400,
      701: 10992,
      702: 9654,
      703: 2642,
      704: 8916,
      705: 19899,
      706: 2119,
      707: 9641,
      708: 294254,
      709: 38167,
      710: 5994,
      711: 39514,
      712: 9563,
      713: 547,
      714: 1538,
      715: 9334,
      716: 11128,
      717: 75780,
      718: 8914,
      719: 13576,
      720: 39538,
      721: 10628,
      722: 14836,
      723: 8645,
      724: 9509,
      725: 10067,
      726: 9384,
      727: 9279,
      728: 1487,
      729: 9422,
      730: 77174,
      731: 4824,
      732: 9620,
      733: 9302,
      734: 10199,
      735: 10771,
      736: 3512,
      737: 137094,
      738: 274479,
      739: 267860,
      740: 8078,
      741: 7485,
      742: 170687,
      743: 6435,
      744: 137106,
      745: 10040,
      746: 6278,
      747: 82682,
      748: 17610,
      749: 22954,
      750: 16995,
      751: 16558,
      752: 9849,
      753: 5820,
      754: 16866,
      755: 201,
      756: 11775,
      757: 87825,
      758: 12201,
      759: 11015,
      760: 9932,
      761: 13389,
      762: 8838,
      763: 17332,
      764: 4958,
      765: 786,
      766: 9513,
      767: 11679,
      768: 38321,
      769: 14411,
      770: 8413,
      771: 10052,
      772: 9676,
      773: 9664,
      774: 2100,
      775: 10384,
      776: 137321,
      777: 123553,
      778: 11260,
      779: 9009,
      780: 11374,
      781: 2309,
      782: 8285,
      783: 210860,
      784: 2312,
      785: 9839,
      786: 381902,
      787: 13922,
      788: 293660,
      789: 9713,
      790: 190859,
      791: 257445,
      792: 9007,
      793: 889,
      794: 1370,
      795: 4942,
      796: 347969,
      797: 24438,
      798: 116741,
      799: 35791,
      800: 72431,
      801: 1813,
      802: 87428,
      803: 8840,
      804: 10589,
      805: 71676,
      806: 1722,
      807: 10022,
      808: 11358,
      809: 13,
      810: 6477,
      811: 1597,
      812: 10530,
      813: 1924,
      814: 9327,
      815: 8488,
      816: 10603,
      817: 8273,
      818: 109424,
      819: 35056,
      820: 8839,
      821: 156022,
      822: 7303,
      823: 8963,
      824: 1402,
      825: 9315,
      826: 8984,
      827: 795,
      828: 24,
      829: 11353,
      830: 393,
      831: 9618,
      832: 9374,
      833: 8584,
      834: 2320,
      835: 58224,
      836: 1729,
      837: 175574,
      838: 8077,
      839: 8818,
      840: 8195,
      841: 10586,
      842: 116149,
      843: 80035,
      844: 10632,
      845: 12117,
      846: 1792,
      847: 13260,
      848: 72197,
      849: 3580,
      850: 12123,
      851: 9566,
      852: 9833,
      853: 4517,
      854: 8202,
      855: 16072,
      856: 34314,
      857: 19724,
      858: 145220,
      859: 14623,
      860: 42297,
      861: 2841,
      862: 802,
      863: 10375,
      864: 36586,
      865: 11321,
      866: 70074,
      867: 242,
      868: 9621,
      869: 1819,
      870: 8536,
      871: 8046,
      872: 1717,
      873: 479,
      874: 9444,
      875: 824,
      876: 11456,
      877: 261023,
      878: 3683,
      879: 22803,
      880: 285923,
      881: 39437,
      882: 1950,
      883: 640,
      884: 97630,
      885: 9767,
      886: 11631,
      887: 32856,
      888: 6519,
      889: 8741,
      890: 49520,
      891: 1850,
      892: 524,
      893: 26389,
      894: 11817,
      895: 2123,
      896: 9907,
      897: 9969,
      898: 18239,
      899: 808,
      900: 38050,
      901: 8367,
      902: 9390,
      903: 72105,
      904: 2898,
      905: 10312,
      906: 109443,
      907: 2022,
      908: 37686,
      909: 462,
      910: 9919,
      911: 187017,
      912: 628,
      913: 10201,
      914: 302699,
      915: 9441,
      916: 274167,
      917: 224141,
      918: 388,
      919: 2112,
      920: 10329,
      921: 74465,
      922: 13811,
      923: 6877,
      924: 10320,
      925: 50646,
      926: 8920,
      927: 13673,
      928: 60308,
      929: 6950,
      930: 225574,
      931: 13836,
      932: 752,
      933: 6038,
      934: 9975,
      935: 11451,
      936: 12103,
      937: 60304,
      938: 2251,
      939: 46529,
      940: 231,
      941: 300671,
      942: 228326,
      943: 9754,
      944: 66,
      945: 4421,
      946: 2649,
      947: 588,
      948: 10393,
      949: 71552,
      950: 9631,
      951: 216282,
      952: 306,
      953: 928,
      954: 205587,
      955: 6623,
      956: 1577,
      957: 9801,
      958: 2116,
      959: 9624,
      960: 14199,
      961: 1907,
      962: 4599,
      963: 22832,
      964: 10390,
      965: 9879,
      966: 38579,
      967: 44603,
      968: 11892,
      969: 9691,
      970: 1248,
      971: 12220,
      972: 72710,
      973: 1255,
      974: 72710,
      975: 1255,
      976: 10782,
      977: 9573,
      978: 4959,
      979: 10061,
      980: 10386,
      981: 421,
      982: 316152,
      983: 11615,
      984: 13498,
      985: 241554,
      986: 2252,
      987: 11968,
      988: 10047,
      989: 38319,
      990: 69668,
      991: 9770,
      992: 11212,
      993: 10533,
      994: 38363,
      995: 9923,
      996: 11863,
      997: 18501,
      998: 109491,
      999: 9275,
      ...},
     'title': {0: 'Avatar',
      1: "Pirates of the Caribbean: At World's End",
      2: 'Spectre',
      3: 'The Dark Knight Rises',
      4: 'John Carter',
      5: 'Spider-Man 3',
      6: 'Tangled',
      7: 'Avengers: Age of Ultron',
      8: 'Harry Potter and the Half-Blood Prince',
      9: 'Batman v Superman: Dawn of Justice',
      10: 'Superman Returns',
      11: 'Quantum of Solace',
      12: "Pirates of the Caribbean: Dead Man's Chest",
      13: 'The Lone Ranger',
      14: 'Man of Steel',
      15: 'The Chronicles of Narnia: Prince Caspian',
      16: 'The Avengers',
      17: 'Pirates of the Caribbean: On Stranger Tides',
      18: 'Men in Black 3',
      19: 'The Hobbit: The Battle of the Five Armies',
      20: 'The Amazing Spider-Man',
      21: 'Robin Hood',
      22: 'The Hobbit: The Desolation of Smaug',
      23: 'The Golden Compass',
      24: 'King Kong',
      25: 'Titanic',
      26: 'Captain America: Civil War',
      27: 'Battleship',
      28: 'Jurassic World',
      29: 'Skyfall',
      30: 'Spider-Man 2',
      31: 'Iron Man 3',
      32: 'Alice in Wonderland',
      33: 'X-Men: The Last Stand',
      34: 'Monsters University',
      35: 'Transformers: Revenge of the Fallen',
      36: 'Transformers: Age of Extinction',
      37: 'Oz: The Great and Powerful',
      38: 'The Amazing Spider-Man 2',
      39: 'TRON: Legacy',
      40: 'Cars 2',
      41: 'Green Lantern',
      42: 'Toy Story 3',
      43: 'Terminator Salvation',
      44: 'Furious 7',
      45: 'World War Z',
      46: 'X-Men: Days of Future Past',
      47: 'Star Trek Into Darkness',
      48: 'Jack the Giant Slayer',
      49: 'The Great Gatsby',
      50: 'Prince of Persia: The Sands of Time',
      51: 'Pacific Rim',
      52: 'Transformers: Dark of the Moon',
      53: 'Indiana Jones and the Kingdom of the Crystal Skull',
      54: 'The Good Dinosaur',
      55: 'Brave',
      56: 'Star Trek Beyond',
      57: 'WALL·E',
      58: 'Rush Hour 3',
      59: '2012',
      60: 'A Christmas Carol',
      61: 'Jupiter Ascending',
      62: 'The Legend of Tarzan',
      63: 'The Chronicles of Narnia: The Lion, the Witch and the Wardrobe',
      64: 'X-Men: Apocalypse',
      65: 'The Dark Knight',
      66: 'Up',
      67: 'Monsters vs Aliens',
      68: 'Iron Man',
      69: 'Hugo',
      70: 'Wild Wild West',
      71: 'The Mummy: Tomb of the Dragon Emperor',
      72: 'Suicide Squad',
      73: 'Evan Almighty',
      74: 'Edge of Tomorrow',
      75: 'Waterworld',
      76: 'G.I. Joe: The Rise of Cobra',
      77: 'Inside Out',
      78: 'The Jungle Book',
      79: 'Iron Man 2',
      80: 'Snow White and the Huntsman',
      81: 'Maleficent',
      82: 'Dawn of the Planet of the Apes',
      83: 'The Lovers',
      84: '47 Ronin',
      85: 'Captain America: The Winter Soldier',
      86: 'Shrek Forever After',
      87: 'Tomorrowland',
      88: 'Big Hero 6',
      89: 'Wreck-It Ralph',
      90: 'The Polar Express',
      91: 'Independence Day: Resurgence',
      92: 'How to Train Your Dragon',
      93: 'Terminator 3: Rise of the Machines',
      94: 'Guardians of the Galaxy',
      95: 'Interstellar',
      96: 'Inception',
      97: 'Shin Godzilla',
      98: 'The Hobbit: An Unexpected Journey',
      99: 'The Fast and the Furious',
      100: 'The Curious Case of Benjamin Button',
      101: 'X-Men: First Class',
      102: 'The Hunger Games: Mockingjay - Part 2',
      103: "The Sorcerer's Apprentice",
      104: 'Poseidon',
      105: 'Alice Through the Looking Glass',
      106: 'Shrek the Third',
      107: 'Warcraft',
      108: 'Terminator Genisys',
      109: 'The Chronicles of Narnia: The Voyage of the Dawn Treader',
      110: 'Pearl Harbor',
      111: 'Transformers',
      112: 'Alexander',
      113: 'Harry Potter and the Order of the Phoenix',
      114: 'Harry Potter and the Goblet of Fire',
      115: 'Hancock',
      116: 'I Am Legend',
      117: 'Charlie and the Chocolate Factory',
      118: 'Ratatouille',
      119: 'Batman Begins',
      120: 'Madagascar: Escape 2 Africa',
      121: 'Night at the Museum: Battle of the Smithsonian',
      122: 'X-Men Origins: Wolverine',
      123: 'The Matrix Revolutions',
      124: 'Frozen',
      125: 'The Matrix Reloaded',
      126: 'Thor: The Dark World',
      127: 'Mad Max: Fury Road',
      128: 'Angels & Demons',
      129: 'Thor',
      130: 'Bolt',
      131: 'G-Force',
      132: 'Wrath of the Titans',
      133: 'Dark Shadows',
      134: 'Mission: Impossible - Rogue Nation',
      135: 'The Wolfman',
      136: 'Bee Movie',
      137: 'Kung Fu Panda 2',
      138: 'The Last Airbender',
      139: 'Mission: Impossible III',
      140: 'White House Down',
      141: 'Mars Needs Moms',
      142: 'Flushed Away',
      143: 'Pan',
      144: 'Mr. Peabody & Sherman',
      145: 'Troy',
      146: "Madagascar 3: Europe's Most Wanted",
      147: 'Die Another Day',
      148: 'Ghostbusters',
      149: 'Armageddon',
      150: 'Men in Black II',
      151: 'Beowulf',
      152: 'Kung Fu Panda 3',
      153: 'Mission: Impossible - Ghost Protocol',
      154: 'Rise of the Guardians',
      155: 'Fun with Dick and Jane',
      156: 'The Last Samurai',
      157: 'Exodus: Gods and Kings',
      158: 'Star Trek',
      159: 'Spider-Man',
      160: 'How to Train Your Dragon 2',
      161: 'Gods of Egypt',
      162: 'Stealth',
      163: 'Watchmen',
      164: 'Lethal Weapon 4',
      165: 'Hulk',
      166: 'G.I. Joe: Retaliation',
      167: 'Sahara',
      168: 'Final Fantasy: The Spirits Within',
      169: 'Captain America: The First Avenger',
      170: 'The World Is Not Enough',
      171: 'Master and Commander: The Far Side of the World',
      172: 'The Twilight Saga: Breaking Dawn - Part 2',
      173: 'Happy Feet Two',
      174: 'The Incredible Hulk',
      175: 'The BFG',
      176: 'The Revenant',
      177: 'Turbo',
      178: 'Rango',
      179: 'Penguins of Madagascar',
      180: 'The Bourne Ultimatum',
      181: 'Kung Fu Panda',
      182: 'Ant-Man',
      183: 'The Hunger Games: Catching Fire',
      184: 'Home',
      185: 'War of the Worlds',
      186: 'Bad Boys II',
      187: 'Puss in Boots',
      188: 'Salt',
      189: 'Noah',
      190: 'The Adventures of Tintin',
      191: 'Harry Potter and the Prisoner of Azkaban',
      192: 'Australia',
      193: 'After Earth',
      194: 'Dinosaur',
      195: 'Night at the Museum: Secret of the Tomb',
      196: 'Megamind',
      197: "Harry Potter and the Philosopher's Stone",
      198: 'R.I.P.D.',
      199: 'Pirates of the Caribbean: The Curse of the Black Pearl',
      200: 'The Hunger Games: Mockingjay - Part 1',
      201: 'The Da Vinci Code',
      202: 'Rio 2',
      203: 'X2',
      204: 'Fast Five',
      205: 'Sherlock Holmes: A Game of Shadows',
      206: 'Clash of the Titans',
      207: 'Total Recall',
      208: 'The 13th Warrior',
      209: 'The Bourne Legacy',
      210: 'Batman & Robin',
      211: 'How the Grinch Stole Christmas',
      212: 'The Day After Tomorrow',
      213: 'Mission: Impossible II',
      214: 'The Perfect Storm',
      215: 'Fantastic 4: Rise of the Silver Surfer',
      216: 'Life of Pi',
      217: 'Ghost Rider',
      218: 'Jason Bourne',
      219: "Charlie's Angels: Full Throttle",
      220: 'Prometheus',
      221: 'Stuart Little 2',
      222: 'Elysium',
      223: 'The Chronicles of Riddick',
      224: 'RoboCop',
      225: 'Speed Racer',
      226: 'How Do You Know',
      227: 'Knight and Day',
      228: 'Oblivion',
      229: 'Star Wars: Episode III - Revenge of the Sith',
      230: 'Star Wars: Episode II - Attack of the Clones',
      231: 'Monsters, Inc.',
      232: 'The Wolverine',
      233: 'Star Wars: Episode I - The Phantom Menace',
      234: 'The Croods',
      235: 'Asterix at the Olympic Games',
      236: 'Windtalkers',
      237: "The Huntsman: Winter's War",
      238: 'Teenage Mutant Ninja Turtles',
      239: 'Gravity',
      240: "Dante's Peak",
      241: 'Teenage Mutant Ninja Turtles: Out of the Shadows',
      242: 'Fantastic Four',
      243: 'Night at the Museum',
      244: 'San Andreas',
      245: 'Tomorrow Never Dies',
      246: 'The Patriot',
      247: "Ocean's Twelve",
      248: 'Mr. & Mrs. Smith',
      249: 'Insurgent',
      250: 'The Aviator',
      251: "Gulliver's Travels",
      252: 'The Green Hornet',
      253: '300: Rise of an Empire',
      254: 'The Smurfs',
      255: 'Home on the Range',
      256: 'Allegiant',
      257: 'Real Steel',
      258: 'The Smurfs 2',
      259: 'Speed 2: Cruise Control',
      260: "Ender's Game",
      261: 'Live Free or Die Hard',
      262: 'The Lord of the Rings: The Fellowship of the Ring',
      263: 'Around the World in 80 Days',
      264: 'Ali',
      265: 'The Cat in the Hat',
      266: 'I, Robot',
      267: 'Kingdom of Heaven',
      268: 'Stuart Little',
      269: 'The Princess and the Frog',
      270: 'The Martian',
      271: 'The Island',
      272: 'Town & Country',
      273: 'Gone in Sixty Seconds',
      274: 'Gladiator',
      275: 'Minority Report',
      276: 'Harry Potter and the Chamber of Secrets',
      277: 'Casino Royale',
      278: 'Planet of the Apes',
      279: 'Terminator 2: Judgment Day',
      280: 'Public Enemies',
      281: 'American Gangster',
      282: 'True Lies',
      283: 'The Taking of Pelham 1 2 3',
      284: 'Little Fockers',
      285: 'The Other Guys',
      286: 'Eraser',
      287: 'Django Unchained',
      288: 'The Hunchback of Notre Dame',
      289: "The Emperor's New Groove",
      290: 'The Expendables 2',
      291: 'National Treasure',
      292: 'Eragon',
      293: 'Where the Wild Things Are',
      294: 'Epic',
      295: 'The Tourist',
      296: 'End of Days',
      297: 'Blood Diamond',
      298: 'The Wolf of Wall Street',
      299: 'Batman Forever',
      300: 'Starship Troopers',
      301: 'Cloud Atlas',
      302: "Legend of the Guardians: The Owls of Ga'Hoole",
      303: 'Catwoman',
      304: 'Hercules',
      305: 'Treasure Planet',
      306: 'Land of the Lost',
      307: 'The Expendables 3',
      308: 'Point Break',
      309: 'Son of the Mask',
      310: 'In the Heart of the Sea',
      311: 'The Adventures of Pluto Nash',
      312: 'Green Zone',
      313: 'The Peanuts Movie',
      314: 'The Spanish Prisoner',
      315: 'The Mummy Returns',
      316: 'Gangs of New York',
      317: 'The Flowers of War',
      318: "Surf's Up",
      319: 'The Stepford Wives',
      320: 'Black Hawk Down',
      321: 'The Campaign',
      322: 'The Fifth Element',
      323: 'Sex and the City 2',
      324: 'The Road to El Dorado',
      325: 'Ice Age: Continental Drift',
      326: 'Cinderella',
      327: 'The Lovely Bones',
      328: 'Finding Nemo',
      329: 'The Lord of the Rings: The Return of the King',
      330: 'The Lord of the Rings: The Two Towers',
      331: 'Seventh Son',
      332: 'Lara Croft: Tomb Raider',
      333: 'Transcendence',
      334: 'Jurassic Park III',
      335: 'Rise of the Planet of the Apes',
      336: 'The Spiderwick Chronicles',
      337: 'A Good Day to Die Hard',
      338: 'The Alamo',
      339: 'The Incredibles',
      340: 'Cutthroat Island',
      341: 'Percy Jackson & the Olympians: The Lightning Thief',
      342: 'Men in Black',
      343: 'Toy Story 2',
      344: 'Unstoppable',
      345: 'Rush Hour 2',
      346: 'What Lies Beneath',
      347: 'Cloudy with a Chance of Meatballs',
      348: 'Ice Age: Dawn of the Dinosaurs',
      349: 'The Secret Life of Walter Mitty',
      350: "Charlie's Angels",
      351: 'The Departed',
      352: 'Mulan',
      353: 'Tropic Thunder',
      354: 'The Girl with the Dragon Tattoo',
      355: 'Die Hard: With a Vengeance',
      356: 'Sherlock Holmes',
      357: 'Ben-Hur',
      358: 'Atlantis: The Lost Empire',
      359: 'Alvin and the Chipmunks: The Road Chip',
      360: 'Valkyrie',
      361: "You Don't Mess with the Zohan",
      362: 'Pixels',
      363: 'A.I. Artificial Intelligence',
      364: 'The Haunted Mansion',
      365: 'Contact',
      366: 'Hollow Man',
      367: 'The Interpreter',
      368: 'Percy Jackson: Sea of Monsters',
      369: 'Lara Croft Tomb Raider: The Cradle of Life',
      370: 'Now You See Me 2',
      371: 'The Saint',
      372: 'Spy Game',
      373: 'Mission to Mars',
      374: 'Rio',
      375: 'Bicentennial Man',
      376: 'Volcano',
      377: "The Devil's Own",
      378: 'K-19: The Widowmaker',
      379: 'Conan the Barbarian',
      380: 'Cinderella Man',
      381: 'The Nutcracker: The Untold Story',
      382: 'Seabiscuit',
      383: 'Twister',
      384: 'Cast Away',
      385: 'Happy Feet',
      386: 'The Bourne Supremacy',
      387: 'Air Force One',
      388: "Ocean's Eleven",
      389: 'The Three Musketeers',
      390: 'Hotel Transylvania',
      391: 'Enchanted',
      392: 'Safe House',
      393: '102 Dalmatians',
      394: 'Tower Heist',
      395: 'The Holiday',
      396: 'Enemy of the State',
      397: "It's Complicated",
      398: "Ocean's Thirteen",
      399: 'Open Season',
      400: 'Divergent',
      401: 'Enemy at the Gates',
      402: 'The Rundown',
      403: 'Last Action Hero',
      404: 'Memoirs of a Geisha',
      405: 'The Fast and the Furious: Tokyo Drift',
      406: 'Arthur Christmas',
      407: 'Meet Joe Black',
      408: 'Collateral Damage',
      409: 'All That Jazz',
      410: 'Mirror Mirror',
      411: 'Scott Pilgrim vs. the World',
      412: 'The Core',
      413: 'Nutty Professor II: The Klumps',
      414: 'Scooby-Doo',
      415: 'Dredd',
      416: 'Click',
      417: 'Creepshow',
      418: 'Cats & Dogs 2 : The Revenge of Kitty Galore',
      419: 'Jumper',
      420: 'Hellboy II: The Golden Army',
      421: 'Zodiac',
      422: 'The 6th Day',
      423: 'Bruce Almighty',
      424: 'The Expendables',
      425: 'Mission: Impossible',
      426: 'The Hunger Games',
      427: 'The Hangover Part II',
      428: 'Batman Returns',
      429: 'Over the Hedge',
      430: 'Lilo & Stitch',
      431: "Charlotte's Web",
      432: 'Deep Impact',
      433: 'RED 2',
      434: 'The Longest Yard',
      435: 'Alvin and the Chipmunks: Chipwrecked',
      436: 'Grown Ups 2',
      437: 'Get Smart',
      438: "Something's Gotta Give",
      439: 'Shutter Island',
      440: 'Four Christmases',
      441: 'Robots',
      442: 'Face/Off',
      443: 'Bedtime Stories',
      444: 'Road to Perdition',
      445: 'Just Go with It',
      446: 'Con Air',
      447: 'Eagle Eye',
      448: 'Cold Mountain',
      449: 'The Book of Eli',
      450: 'Flubber',
      451: 'The Haunting',
      452: 'Space Jam',
      453: 'The Pink Panther',
      454: 'The Day the Earth Stood Still',
      455: 'Conspiracy Theory',
      456: 'Fury',
      457: 'Six Days Seven Nights',
      458: 'Yogi Bear',
      459: 'Spirit: Stallion of the Cimarron',
      460: 'Zookeeper',
      461: 'Lost in Space',
      462: 'The Manchurian Candidate',
      463: 'Déjà Vu',
      464: 'Hotel Transylvania 2',
      465: 'Fantasia 2000',
      466: 'The Time Machine',
      467: 'Mighty Joe Young',
      468: 'Swordfish',
      469: 'The Legend of Zorro',
      470: 'What Dreams May Come',
      471: 'Little Nicky',
      472: 'The Brothers Grimm',
      473: 'Mars Attacks!',
      474: 'Evolution',
      475: 'The Edge',
      476: 'Surrogates',
      477: 'Thirteen Days',
      478: 'Daylight',
      479: 'Walking With Dinosaurs',
      480: 'Battlefield Earth',
      481: 'Looney Tunes: Back in Action',
      482: 'Nine',
      483: 'Timeline',
      484: 'The Postman',
      485: 'Babe: Pig in the City',
      486: 'The Last Witch Hunter',
      487: 'Red Planet',
      488: 'Arthur and the Invisibles',
      489: 'Oceans',
      490: 'A Sound of Thunder',
      491: 'Pompeii',
      492: 'Top Cat Begins',
      493: 'A Beautiful Mind',
      494: 'The Lion King',
      495: 'Journey 2: The Mysterious Island',
      496: 'Cloudy with a Chance of Meatballs 2',
      497: 'Red Dragon',
      498: 'Hidalgo',
      499: 'Jack and Jill',
      500: '2 Fast 2 Furious',
      501: 'The Little Prince',
      502: 'The Invasion',
      503: 'The Adventures of Rocky & Bullwinkle',
      504: 'The Secret Life of Pets',
      505: 'The League of Extraordinary Gentlemen',
      506: 'Despicable Me 2',
      507: 'Independence Day',
      508: 'The Lost World: Jurassic Park',
      509: 'Madagascar',
      510: 'Children of Men',
      511: 'X-Men',
      512: 'Wanted',
      513: 'The Rock',
      514: 'Ice Age: The Meltdown',
      515: '50 First Dates',
      516: 'Hairspray',
      517: 'Exorcist: The Beginning',
      518: 'Inspector Gadget',
      519: 'Now You See Me',
      520: 'Grown Ups',
      521: 'The Terminal',
      522: 'Hotel for Dogs',
      523: 'Vertical Limit',
      524: "Charlie Wilson's War",
      525: 'Shark Tale',
      526: 'Dreamgirls',
      527: 'Be Cool',
      528: 'Munich',
      529: 'Tears of the Sun',
      530: 'Killers',
      531: 'The Man from U.N.C.L.E.',
      532: 'Spanglish',
      533: 'Monster House',
      534: 'Bandits',
      535: 'First Knight',
      536: 'Anna and the King',
      537: 'Immortals',
      538: 'Hostage',
      539: 'Titan A.E.',
      540: 'Hollywood Homicide',
      541: 'Soldier',
      542: 'Carriers',
      543: 'Monkeybone',
      544: 'Flight of the Phoenix',
      545: 'Unbreakable',
      546: 'Minions',
      547: 'Sucker Punch',
      548: 'Snake Eyes',
      549: 'Sphere',
      550: 'The Angry Birds Movie',
      551: "Fool's Gold",
      552: 'Funny People',
      553: 'The Kingdom',
      554: 'Talladega Nights: The Ballad of Ricky Bobby',
      555: 'Dr. Dolittle 2',
      556: 'Braveheart',
      557: 'Jarhead',
      558: 'The Simpsons Movie',
      559: 'The Majestic',
      560: 'Driven',
      561: 'Two Brothers',
      562: 'The Village',
      563: 'Doctor Dolittle',
      564: 'Signs',
      565: 'Shrek 2',
      566: 'Cars',
      567: 'Runaway Bride',
      568: 'xXx',
      569: 'The SpongeBob Movie: Sponge Out of Water',
      570: 'Ransom',
      571: 'Inglourious Basterds',
      572: 'Hook',
      573: 'Die Hard 2',
      574: 'S.W.A.T.',
      575: 'Vanilla Sky',
      576: 'Lady in the Water',
      577: 'AVP: Alien vs. Predator',
      578: 'Alvin and the Chipmunks: The Squeakquel',
      579: 'We Were Soldiers',
      580: 'Olympus Has Fallen',
      581: 'Star Trek: Insurrection',
      582: 'Battle: Los Angeles',
      583: 'Big Fish',
      584: 'Wolf',
      585: 'War Horse',
      586: 'The Monuments Men',
      587: 'The Abyss',
      588: 'Wall Street: Money Never Sleeps',
      589: 'Dracula Untold',
      590: 'The Siege',
      591: 'Stardust',
      592: 'Seven Years in Tibet',
      593: 'The Dilemma',
      594: 'Bad Company',
      595: 'Doom',
      596: 'I Spy',
      597: 'Underworld: Awakening',
      598: 'Rock of Ages',
      599: "Hart's War",
      600: 'Killer Elite',
      601: 'Rollerball',
      602: 'Ballistic: Ecks vs. Sever',
      603: 'Hard Rain',
      604: 'Osmosis Jones',
      605: "Legends of Oz: Dorothy's Return",
      606: 'Blackhat',
      607: 'Sky Captain and the World of Tomorrow',
      608: 'Basic Instinct 2',
      609: 'Escape Plan',
      610: 'The Legend of Hercules',
      611: 'The Sum of All Fears',
      612: 'The Twilight Saga: Eclipse',
      613: 'The Score',
      614: 'Despicable Me',
      615: 'Money Train',
      616: 'Ted 2',
      617: 'Agora',
      618: 'Mystery Men',
      619: 'Hall Pass',
      620: 'The Insider',
      621: 'The Finest Hours',
      622: 'Body of Lies',
      623: 'Dinner for Schmucks',
      624: 'Abraham Lincoln: Vampire Hunter',
      625: 'Entrapment',
      626: 'The X Files',
      627: 'The Last Legion',
      628: 'Saving Private Ryan',
      629: 'Need for Speed',
      630: 'What Women Want',
      631: 'Ice Age',
      632: 'Dreamcatcher',
      633: 'Lincoln',
      634: 'The Matrix',
      635: 'Apollo 13',
      636: 'The Santa Clause 2',
      637: 'Les Misérables',
      638: "You've Got Mail",
      639: 'Step Brothers',
      640: 'The Mask of Zorro',
      641: 'Due Date',
      642: 'Unbroken',
      643: 'Space Cowboys',
      644: 'Cliffhanger',
      645: 'Broken Arrow',
      646: 'The Kid',
      647: 'World Trade Center',
      648: 'Mona Lisa Smile',
      649: 'The Dictator',
      650: 'Eyes Wide Shut',
      651: 'Annie',
      652: 'Focus',
      653: 'This Means War',
      654: 'Blade: Trinity',
      655: 'Red Dawn',
      656: 'Primary Colors',
      657: 'Resident Evil: Retribution',
      658: 'Death Race',
      659: 'The Long Kiss Goodnight',
      660: 'Proof of Life',
      661: 'Zathura: A Space Adventure',
      662: 'Fight Club',
      663: 'We Are Marshall',
      664: 'Hudson Hawk',
      665: 'Lucky Numbers',
      666: 'I, Frankenstein',
      667: 'Oliver Twist',
      668: 'Elektra',
      669: 'Sin City: A Dame to Kill For',
      670: 'Random Hearts',
      671: 'Everest',
      672: 'Perfume: The Story of a Murderer',
      673: 'Austin Powers in Goldmember',
      674: 'Astro Boy',
      675: 'Jurassic Park',
      676: 'Wyatt Earp',
      677: 'Clear and Present Danger',
      678: 'Dragon Blade',
      679: 'Little Man',
      680: 'U-571',
      681: 'The American President',
      682: 'The Love Guru',
      683: '3000 Miles to Graceland',
      684: 'The Hateful Eight',
      685: 'Blades of Glory',
      686: 'Hop',
      687: '300',
      688: 'Meet the Fockers',
      689: 'Marley & Me',
      690: 'The Green Mile',
      691: 'Wild Hogs',
      692: 'Chicken Little',
      693: 'Gone Girl',
      694: 'The Bourne Identity',
      695: 'GoldenEye',
      696: "The General's Daughter",
      697: 'The Truman Show',
      698: 'The Prince of Egypt',
      699: 'Daddy Day Care',
      700: '2 Guns',
      701: 'Cats & Dogs',
      702: 'The Italian Job',
      703: 'Two Weeks Notice',
      704: 'Antz',
      705: 'Couples Retreat',
      706: 'Days of Thunder',
      707: 'Cheaper by the Dozen 2',
      708: 'Maze Runner: The Scorch Trials',
      709: 'Eat Pray Love',
      710: 'The Family Man',
      711: 'RED',
      712: 'Any Given Sunday',
      713: 'The Horse Whisperer',
      714: 'Collateral',
      715: 'The Scorpion King',
      716: 'Ladder 49',
      717: 'Jack Reacher',
      718: 'Deep Blue Sea',
      719: 'This Is It',
      720: 'Contagion',
      721: 'Kangaroo Jack',
      722: 'Coraline',
      723: 'The Happening',
      724: 'Man on Fire',
      725: 'The Shaggy Dog',
      726: 'Starsky & Hutch',
      727: 'Jingle All the Way',
      728: 'Hellboy',
      729: 'A Civil Action',
      730: 'ParaNorman',
      731: 'The Jackal',
      732: 'Paycheck',
      733: 'Up Close & Personal',
      734: 'The Tale of Despereaux',
      735: 'The Tuxedo',
      736: 'Under Siege 2: Dark Territory',
      737: 'Jack Ryan: Shadow Recruit',
      738: 'Joy',
      739: 'London Has Fallen',
      740: 'Alien: Resurrection',
      741: 'Shooter',
      742: 'The Boxtrolls',
      743: 'Practical Magic',
      744: 'The Lego Movie',
      745: 'Miss Congeniality 2: Armed and Fabulous',
      746: 'Reign of Fire',
      747: 'Gangster Squad',
      748: 'Year One',
      749: 'Invictus',
      750: 'State of Play',
      751: 'Duplicity',
      752: 'My Favorite Martian',
      753: 'The Sentinel',
      754: 'Planet 51',
      755: 'Star Trek: Nemesis',
      756: 'Intolerable Cruelty',
      757: 'Trouble with the Curve',
      758: 'Edge of Darkness',
      759: 'The Relic',
      760: 'Analyze That',
      761: 'Righteous Kill',
      762: 'Mercury Rising',
      763: 'The Soloist',
      764: 'The Legend of Bagger Vance',
      765: 'Almost Famous',
      766: 'Garfield: A Tail of Two Kitties',
      767: 'xXx: State of the Union',
      768: 'Priest',
      769: 'Sinbad: Legend of the Seven Seas',
      770: 'Event Horizon',
      771: 'Dragonfly',
      772: 'The Black Dahlia',
      773: 'Flyboys',
      774: 'The Last Castle',
      775: 'Supernova',
      776: "Winter's Tale",
      777: 'The Mortal Instruments: City of Bones',
      778: 'Meet Dave',
      779: 'Dark Water',
      780: 'Edtv',
      781: 'Inkheart',
      782: 'The Spirit',
      783: 'Mortdecai',
      784: 'In the Name of the King: A Dungeon Siege Tale',
      785: 'Beyond Borders',
      786: 'The Monkey King 2',
      787: 'The Great Raid',
      788: 'Deadpool',
      789: 'Holy Man',
      790: 'American Sniper',
      791: 'Goosebumps',
      792: 'Just Like Heaven',
      793: 'The Flintstones in Viva Rock Vegas',
      794: 'Rambo III',
      795: 'Leatherheads',
      796: 'The Ridiculous 6',
      797: 'Did You Hear About the Morgans?',
      798: 'The Internship',
      799: 'Resident Evil: Afterlife',
      800: 'Red Tails',
      801: "The Devil's Advocate",
      802: "That's My Boy",
      803: 'DragonHeart',
      804: 'After the Sunset',
      805: 'Ghost Rider: Spirit of Vengeance',
      806: "Captain Corelli's Mandolin",
      807: 'The Pacifier',
      808: 'Walking Tall',
      809: 'Forrest Gump',
      810: 'Alvin and the Chipmunks',
      811: 'Meet the Parents',
      812: 'Pocahontas',
      813: 'Superman',
      814: 'The Nutty Professor',
      815: 'Hitch',
      816: 'George of the Jungle',
      817: 'American Wedding',
      818: 'Captain Phillips',
      819: 'Date Night',
      820: 'Casper',
      821: 'The Equalizer',
      822: 'Maid in Manhattan',
      823: 'Crimson Tide',
      824: 'The Pursuit of Happyness',
      825: 'Flightplan',
      826: 'Disclosure',
      827: 'City of Angels',
      828: 'Kill Bill: Vol. 1',
      829: 'Bowfinger',
      830: 'Kill Bill: Vol. 2',
      831: 'Tango & Cash',
      832: 'Death Becomes Her',
      833: 'Shanghai Noon',
      834: 'Executive Decision',
      835: "Mr. Popper's Penguins",
      836: 'The Forbidden Kingdom',
      837: 'Free Birds',
      838: 'Alien³',
      839: 'Evita',
      840: 'Ronin',
      841: 'The Ghost and the Darkness',
      842: 'Paddington',
      843: 'The Watch',
      844: 'The Hunted',
      845: 'Instinct',
      846: 'Stuck on You',
      847: 'Semi-Pro',
      848: 'The Pirates! In an Adventure with Scientists!',
      849: 'Changeling',
      850: 'Chain Reaction',
      851: 'The Fan',
      852: 'The Phantom of the Opera',
      853: 'Elizabeth: The Golden Age',
      854: 'Æon Flux',
      855: 'Gods and Generals',
      856: 'Turbulence',
      857: 'Imagine That',
      858: 'Muppets Most Wanted',
      859: 'Thunderbirds',
      860: 'Burlesque',
      861: 'A Very Long Engagement',
      862: 'Lolita',
      863: 'D-Tox',
      864: 'Blade II',
      865: 'Seven Pounds',
      866: 'Bullet to the Head',
      867: 'The Godfather: Part III',
      868: 'Elizabethtown',
      869: 'You, Me and Dupree',
      870: 'Superman II',
      871: 'Gigli',
      872: "All the King's Men",
      873: 'Shaft',
      874: 'Anastasia',
      875: 'Moulin Rouge!',
      876: 'Domestic Disturbance',
      877: 'Black Mass',
      878: 'Flags of Our Fathers',
      879: 'Law Abiding Citizen',
      880: 'Grindhouse',
      881: 'Beloved',
      882: 'Lucky You',
      883: 'Catch Me If You Can',
      884: 'Zero Dark Thirty',
      885: 'The Break-Up',
      886: 'Mamma Mia!',
      887: "Valentine's Day",
      888: 'The Dukes of Hazzard',
      889: 'The Thin Red Line',
      890: 'The Change-Up',
      891: 'Man on the Moon',
      892: 'Casino',
      893: 'From Paris with Love',
      894: 'Bulletproof Monk',
      895: 'Me, Myself & Irene',
      896: 'Barnyard',
      897: 'Deck the Halls',
      898: 'The Twilight Saga: New Moon',
      899: 'Shrek',
      900: 'The Adjustment Bureau',
      901: 'Robin Hood: Prince of Thieves',
      902: 'Jerry Maguire',
      903: 'Ted',
      904: 'As Good as It Gets',
      905: 'Patch Adams',
      906: 'Anchorman 2: The Legend Continues',
      907: 'Mr. Deeds',
      908: 'Super 8',
      909: 'Erin Brockovich',
      910: 'How to Lose a Guy in 10 Days',
      911: '22 Jump Street',
      912: 'Interview with the Vampire',
      913: 'Yes Man',
      914: 'Central Intelligence',
      915: 'Stepmom',
      916: "Daddy's Home",
      917: 'Into the Woods',
      918: 'Inside Man',
      919: 'Payback',
      920: 'Congo',
      921: 'We Bought a Zoo',
      922: 'Knowing',
      923: 'Failure to Launch',
      924: 'The Ring Two',
      925: 'Crazy, Stupid, Love.',
      926: 'Garfield',
      927: 'Christmas with the Kranks',
      928: 'Moneyball',
      929: 'Outbreak',
      930: 'Non-Stop',
      931: 'Race to Witch Mountain',
      932: 'V for Vendetta',
      933: 'Shanghai Knights',
      934: 'Curious George',
      935: 'Herbie Fully Loaded',
      936: "Don't Say a Word",
      937: 'Hansel & Gretel: Witch Hunters',
      938: 'Unfaithful',
      939: 'I Am Number Four',
      940: 'Syriana',
      941: '13 Hours: The Secret Soldiers of Benghazi',
      942: 'The Book of Life',
      943: 'Firewall',
      944: 'Absolute Power',
      945: 'G.I. Jane',
      946: 'The Game',
      947: 'Silent Hill',
      948: 'The Replacements',
      949: 'American Reunion',
      950: 'The Negotiator',
      951: 'Into the Storm',
      952: 'Beverly Hills Cop III',
      953: 'Gremlins 2: The New Batch',
      954: 'The Judge',
      955: 'The Peacemaker',
      956: 'Resident Evil: Apocalypse',
      957: 'Bridget Jones: The Edge of Reason',
      958: 'Out of Time',
      959: 'On Deadly Ground',
      960: 'The Adventures of Sharkboy and Lavagirl',
      961: 'The Beach',
      962: 'Raising Helen',
      963: 'Ninja Assassin',
      964: 'For Love of the Game',
      965: 'Striptease',
      966: 'Marmaduke',
      967: 'Hereafter',
      968: 'Murder by Numbers',
      969: 'Assassins',
      970: 'Hannibal Rising',
      971: 'The Story of Us',
      972: 'The Host',
      973: 'The Host',
      974: 'The Host',
      975: 'The Host',
      976: 'Basic',
      977: 'Blood Work',
      978: 'The International',
      979: 'Escape from L.A.',
      980: 'The Iron Giant',
      981: 'The Life Aquatic with Steve Zissou',
      982: 'Free State of Jones',
      983: 'The Life of David Gale',
      984: 'Man of the House',
      985: 'Run All Night',
      986: 'Eastern Promises',
      987: 'Into the Blue',
      988: 'The Messenger: The Story of Joan of Arc',
      989: 'Your Highness',
      990: 'Dream House',
      991: 'Mad City',
      992: "Baby's Day Out",
      993: 'The Scarlet Letter',
      994: 'Fair Game',
      995: 'Domino',
      996: 'Jade',
      997: 'Gamer',
      998: 'Beautiful Creatures',
      999: 'Death to Smoochy',
      ...},
     'tags': {0: 'in the 22nd century, a parapleg marin is dispatch to the moon pandora on a uniqu mission, but becom torn between follow order and protect an alien civilization. action adventur fantasi scienc fiction cultur clash futur space war space coloni societi space travel futurist romanc space alien tribe alien planet cgi marin soldier battl love affair anti war power relat mind and soul 3d sam worthington zoe saldana sigourney weaver jame cameron',
      1: "captain barbossa, long believ to be dead, ha come back to life and is head to the edg of the earth with will turner and elizabeth swann. but noth is quit as it seems. adventur fantasi action ocean drug abu exot island east india trade compani love of one' life traitor shipwreck strong woman ship allianc calypso afterlif fighter pirat swashbuckl aftercreditsst johnni depp orlando bloom keira knightley gore verbinski",
      2: 'a cryptic messag from bond’ past send him on a trail to uncov a sinist organization. while m battl polit forc to keep the secret servic alive, bond peel back the layer of deceit to reveal the terribl truth behind spectre. action adventur crime spi base on novel secret agent sequel mi6 british secret servic unit kingdom daniel craig christoph waltz léa seydoux sam mend',
      3: "follow the death of district attorney harvey dent, batman assum respon for dent' crime to protect the late attorney' reput and is subsequ hunt by the gotham citi polic department. eight year later, batman encount the mysteri selina kyle and the villain bane, a new terrorist leader who overwhelm gotham' finest. the dark knight resurfac to protect a citi that ha brand him an enemy. action crime drama thriller dc comic crime fighter terrorist secret ident burglar hostag drama time bomb gotham citi vigil cover-up superhero villai tragic hero terror destruct catwoman cat burglar imax flood crimin underworld batman christian bale michael cain gari oldman christoph nolan",
      4: "john carter is a war-weary, former militari captain who' inexpl transport to the mysteri and exot planet of barsoom (mars) and reluctantli becom embroil in an epic conflict. it' a world on the brink of collapse, and carter rediscov hi human when he realiz the surviv of barsoom and it peopl rest in hi hands. action adventur scienc fiction base on novel mar medallion space travel princess alien steampunk martian escap edgar rice burrough alien race superhuman strength mar civil sword and planet 19th centuri 3d taylor kitsch lynn collin samantha morton andrew stanton",
      5: "the seemingli invinc spider-man goe up against an all-new crop of villain – includ the shape-shift sandman. while spider-man’ superpow are alter by an alien organism, hi alter ego, peter parker, deal with nemesi eddi brock and also get caught up in a love triangle. fantasi action adventur dual ident amnesia sandstorm love of one' life forgiv spider wretch death of a friend egomania sand narcism hostil marvel comic sequel superhero reveng tobey maguir kirsten dunst jame franco sam raimi",
      6: "when the kingdom' most wanted-and most charming-bandit flynn rider hide out in a mysteri tower, he' taken hostag by rapunzel, a beauti and feisti tower-bound teen with 70 feet of magical, golden hair. flynn' curiou captor, who' look for her ticket out of the tower where she' been lock away for years, strike a deal with the handsom thief and the unlik duo set off on an action-pack escapade, complet with a super-cop horse, an over-protect chameleon and a gruff gang of pub thugs. anim famili hostag magic hor fairi tale music princess anim tower blond woman selfish heal power base on fairi tale duringcreditsst heal gift anim sidekick zachari levi mandi moor donna murphi byron howard",
      7: 'when toni stark tri to jumpstart a dormant peacekeep program, thing go awri and earth’ mightiest hero are put to the ultim test as the fate of the planet hang in the balance. as the villain ultron emerges, it is up to the aveng to stop him from enact hi terribl plans, and soon uneasi allianc and unexpect action pave the way for an epic and uniqu global adventure. action adventur scienc fiction marvel comic sequel superhero base on comic book vision superhero team duringcreditsst marvel cinemat univ 3d robert downey jr. chri hemsworth mark ruffalo joss whedon',
      8: "as harri begin hi sixth year at hogwarts, he discov an old book mark as 'properti of the half-blood prince', and begin to learn more about lord voldemort' dark past. adventur fantasi famili witch magic broom school of witchcraft wizardri apparit teenag crush werewolf daniel radcliff rupert grint emma watson david yate",
      9: 'fear the action of a god-lik super hero left unchecked, gotham city’ own formidable, forc vigil take on metropolis’ most revered, modern-day savior, while the world wrestl with what sort of hero it realli needs. and with batman and superman at war with one another, a new threat quickli arises, put mankind in greater danger than it’ ever known before. action adventur fantasi dc comic vigil superhero base on comic book reveng super power clark kent bruce wayn dc extend univ ben affleck henri cavil gal gadot zack snyder',
      10: 'superman return to discov hi 5-year absenc ha allow lex luthor to walk free, and that those he wa closest too felt abandon and have move on. luthor plot hi ultim reveng that could see million kill and chang the face of the planet forever, as well as rid himself of the man of steel. adventur fantasi action scienc fiction save the world dc comic invuln sequel superhero base on comic book kryptonit super power superhuman strength lex luthor brandon routh kevin spacey kate bosworth bryan singer',
      11: 'quantum of solac continu the adventur of jame bond after casino royale. betray by vesper, the woman he loved, 007 fight the urg to make hi latest mission personal. pursu hi determin to uncov the truth, bond and m interrog mr. white, who reveal that the organ that blackmail vesper is far more complex and danger than anyon had imagined. adventur action thriller crime kill undercov secret agent british secret servic daniel craig olga kurylenko mathieu amalr marc forster',
      12: 'captain jack sparrow work hi way out of a blood debt with the ghostli davey jones, he also attempt to avoid etern damnation. adventur fantasi action witch fortun teller bondag exot island monster captain card game east india trade compani compass ship daughter pirat swashbuckl aftercreditsst johnni depp orlando bloom keira knightley gore verbinski',
      13: 'the texa ranger chase down a gang of outlaw led by butch cavendish, but the gang ambush the rangers, seemingli kill them all. one survivor is found, however, by an american indian name tonto, who nur him back to health. the ranger, don a mask and ride a white stallion name silver, team up with tonto to bring the unscrupul gang and other of that ilk to justice. action adventur western texa hor survivor texa ranger partner outlaw escap lawyer train lone ranger comanch the lone ranger tonto johnni depp armi hammer william fichtner gore verbinski',
      14: 'a young boy learn that he ha extraordinari power and is not of thi earth. as a young man, he journey to discov where he came from and what he wa sent here to do. but the hero in him must emerg if he is to save the world from annihil and becom the symbol of hope for all mankind. action adventur fantasi scienc fiction save the world dc comic superhero base on comic book superhuman alien inva reboot super power dc extend univ henri cavil ami adam michael shannon zack snyder',
      15: 'one year after their incr adventur in the lion, the witch and the wardrobe, peter, edmund, luci and susan pevensi return to narnia to aid a young princ whose life ha been threaten by the evil king miraz. now, with the help of a color cast of new characters, includ trufflehunt the badger and nikabrik the dwarf, the pevensi clan embark on an incr quest to ensur that narnia is return to it right heir. adventur famili fantasi base on novel fiction place brother sister relationship lion human be wretch leap in time matter of life and death faith uncl narnia fantasi world ben barn william moseley anna popplewel andrew adamson',
      16: 'when an unexpect enemi emerg and threaten global safeti and security, nick fury, director of the intern peacekeep agenc known as s.h.i.e.l.d., find himself in need of a team to pull the world back from the brink of disaster. span the globe, a dare recruit effort begins! scienc fiction action adventur new york shield marvel comic superhero base on comic book alien inva superhero team aftercreditsst duringcreditsst marvel cinemat univ robert downey jr. chri evan mark ruffalo joss whedon',
      17: "captain jack sparrow cross path with a woman from hi past, and he' not sure if it' love -- or if she' a ruthless con artist who' use him to find the fabl fountain of youth. when she forc him aboard the queen anne' revenge, the ship of the formid pirat blackbeard, jack find himself on an unexpect adventur in which he doesn't know who to fear more: blackbeard or the woman from hi past. adventur action fantasi sea captain mutini sword prime minist sail silver ship duke mermaid pirat soldier battl swashbuckl aftercreditsst 3d johnni depp penélop cruz ian mcshane rob marshal",
      18: "agent j (will smith) and k (tommi lee jones) are back...in time. j ha seen some inexpl thing in hi 15 year with the men in black, but nothing, not even aliens, perplex him as much as hi wry, retic partner. but when k' life and the fate of the planet are put at stake, agent j will have to travel back in time to put thing right. j discov that there are secret to the univ that k never told him - secret that will reveal themselv as he team up with the young agent k (josh brolin) to save hi partner, the agency, and the futur of humankind. action comedi scienc fiction time travel time machin alien fiction govern agenc see the futur chang histori will smith tommi lee jone josh brolin barri sonnenfeld",
      19: "immedi after the event of the desol of smaug, bilbo and the dwarv tri to defend erebor' mountain of treasur from other who claim it: the men of the ruin laketown and the elv of mirkwood. meanwhil an armi of orc led by azog the defil is march on erebor, fuel by the rise of the dark lord sauron. dwarves, elv and men must unite, and the hope for middle-earth fall into bilbo' hands. action adventur fantasi corrupt elv dwarv orc middle-earth (tolkien) hobbit dragon battl unlik friendship epic battl sword and sorceri martin freeman ian mckellen richard armitag peter jackson",
      20: "peter parker is an outcast high schooler abandon by hi parent as a boy, leav him to be rai by hi uncl ben and aunt may. like most teenagers, peter is tri to figur out who he is and how he got to be the person he is today. as peter discov a mysteri briefca that belong to hi father, he begin a quest to understand hi parents' disappear – lead him directli to oscorp and the lab of dr. curt connors, hi father' former partner. as spider-man is set on a colli cour with connors' alter ego, the lizard, peter will make life-alt choic to use hi power and shape hi destini to becom a hero. action adventur fantasi loss of father vigil serum marvel comic scientif experi spider bite mask vigil reboot super power genet engin social outcast duringcreditsst andrew garfield emma stone rhi ifan marc webb",
      21: "when soldier robin happen upon the die robert of loxley, he promi to return the man' sword to hi famili in nottingham. there, he assum robert' identity; romanc hi widow, marion; and draw the ire of the town' sheriff and king john' henchman, godfrey. action adventur robin hood archer knight sherwood forest bow and arrow middl age mediev king of england russel crow cate blanchett max von sydow ridley scott",
      22: 'the dwarves, bilbo and gandalf have success escap the misti mountains, and bilbo ha gain the one ring. they all continu their journey to get their gold back from the dragon, smaug. adventur fantasi elv dwarv orc hobbit dragon wizard sword and sorceri martin freeman ian mckellen richard armitag peter jackson',
      23: "after overhear a shock secret, precoci orphan lyra belacqua trade her carefr exist roam the hall of jordan colleg for an otherworldli adventur in the far north, unawar that it' part of her destiny. adventur fantasi england compass experi lordship uncl polar bear orphan anim base on young adult novel dakota blue richard nicol kidman daniel craig chri weitz",
      24: 'in 1933 new york, an overli ambiti movi produc coerc hi cast and hire ship crew to travel to mysteri skull island, where they encount kong, a giant ape who is immedi smitten with the lead lady. adventur drama action film busi screenplay show busi film make film produc exot island monster indigen ship dinosaur naomi watt jack black adrien brodi peter jackson',
      25: '84 year later, a 101-year-old woman name rose dewitt bukat tell the stori to her granddaught lizzi calvert, brock lovett, lewi bodine, bobbi buell and anatoli mikailavich on the keldysh about her life set in april 10th 1912, on a ship call titan when young rose board the depart ship with the upper-class passeng and her mother, ruth dewitt bukater, and her fiancé, caledon hockley. meanwhile, a drifter and artist name jack dawson and hi best friend fabrizio de rossi win third-class ticket to the ship in a game. and she explain the whole stori from departur until the death of titan on it first and last voyag april 15th, 1912 at 2:20 in the morning. drama romanc thriller shipwreck iceberg ship panic titan ocean liner epic rich woman - poor man love disast tragic love class differ imax star cross lover steerag salvag rich snob 3d 1910 kate winslet leonardo dicaprio franc fisher jame cameron',
      26: 'follow the event of age of ultron, the collect govern of the world pass an act design to regul all superhuman activity. thi polar opinion amongst the avengers, cau two faction to side with iron man or captain america, which cau an epic battl between former allies. adventur action scienc fiction civil war war marvel comic sequel superhero base on comic book imax aftercreditsst duringcreditsst marvel cinemat univ 3d chri evan robert downey jr. scarlett johansson anthoni russo',
      27: "when mankind beam a radio signal into space, a repli come from ‘planet g’, in the form of sever alien craft that splash down in the water off hawaii. lieuten alex hopper is a weapon offic assign to the uss john paul jones, part of an intern naval coalit which becom the world' last hope for surviv as they engag the hostil alien forc of unimagin strength. while take on the invaders, hopper must also tri to live up to the potenti hi brother, and hi fiancée' father, admir shane, expect of him. thriller action adventur scienc fiction fight u.s. navi mind read hong kong soccer scientist fiction war naval armada battleship naval combat jd myoko lost commun taser buoy commun expert joint chief of staff crash land jet fighter pilot navi lieuten permiss to marri uss john paul jone base on board game aftercreditsst mighti mo uss missouri taylor kitsch alexand skarsgård rihanna peter berg",
      28: 'twenty-two year after the event of jurass park, isla nublar now featur a fulli function dinosaur theme park, jurass world, as origin envi by john hammond. action adventur scienc fiction thriller monster dna tyrannosauru rex velociraptor island sequel suspen disast escap dinosaur amu park anim attack theme park jurass park 3d anim horror chri pratt bryce dalla howard irrfan khan colin trevorrow',
      29: "when bond' latest assign goe grave wrong and agent around the world are exposed, mi6 is attack forc m to reloc the agency. these event cau her author and posit to be challeng by gareth mallory, the new chairman of the intellig and secur committee. with mi6 now compromi from both insid and out, m is left with one alli she can trust: bond. 007 take to the shadow - aid onli by field agent, eve - follow a trail to the mysteri silva, whose lethal and hidden motiv have yet to reveal themselves. action adventur thriller spi secret agent sociopath killer art galleri british secret servic istanbul turkey imax uzi boobi trap imperson a polic offic macao daniel craig judi dench javier bardem sam mend",
      30: "peter parker is go through a major ident crisis. burn out from be spider-man, he decid to shelv hi superhero alter ego, which leav the citi suffer in the wake of carnag left by the evil doc ock. in the meantime, parker still can't act on hi feel for mari jane watson, a girl he' love sinc childhood. action adventur fantasi dual ident love of one' life pizza boy marvel comic sequel superhero doctor scientist tentacl death super villain tobey maguir kirsten dunst jame franco sam raimi",
      31: "when toni stark' world is torn apart by a formid terrorist call the mandarin, he start an odyssey of rebuild and retribution. action adventur scienc fiction terrorist war on terror tenness malibu marvel comic superhero base on comic book toni stark iron man aftercreditsst marvel cinemat univ mandarin 3d war machin iron patriot extremi robert downey jr. gwyneth paltrow don cheadl shane black",
      32: "alice, an unpretenti and individu 19-year-old, is betroth to a dunc of an english nobleman. at her engag party, she escap the crowd to consid whether to go through with the marriag and fall down a hole in the garden after spot an unusu rabbit. arriv in a strang and surreal place call 'underland,' she find herself in a world that resembl the nightmar she had as a child, fill with talk animals, villain queen and knights, and frumiou bandersnatches. alic realiz that she is there for a reason – to conquer the horrif jabberwocki and restor the right queen to her throne. famili fantasi adventur base on novel fiction place queen fantasi alic in wonderland fantasi world 3d mia wasikowska johnni depp ann hathaway tim burton",
      33: "when a cure is found to treat mutations, line are drawn amongst the x-men and the brotherhood, a band of power mutant organ under xavier' former ally, magneto. adventur action scienc fiction thriller mutant marvel comic base on comic book superhuman beast cyclop aftercreditsst hugh jackman hall berri ian mckellen brett ratner",
      34: "a look at the relationship between mike and sulley dure their day at monster univ — when they weren't necessarili the best of friends. anim famili monster dormitori game anim best friend univ scari aftercreditsst billi crystal john goodman steve buscemi dan scanlon",
      35: "sam witwicki leav the autobot behind for a normal life. but when hi mind is fill with cryptic symbols, the decepticon target him and he is drag back into the transformers' war. scienc fiction action adventur egypt sun chao symbol artifact transform tank robot imax duringcreditsst shia labeouf megan fox josh duhamel michael bay",
      36: 'as human pick up the pieces, follow the conclu of "transformers: dark of the moon," autobot and decepticon have all but vanish from the face of the planet. however, a group of powerful, ingeni businessman and scientist attempt to learn from past transform incur and push the boundari of technolog beyond what they can control - all while an ancient, power transform menac set earth in hi cross-hairs. scienc fiction action adventur sequel alien transform giant robot robot imax transform robot mark wahlberg stanley tucci kelsey grammer michael bay',
      37: "oscar diggs, a small-tim circu illusionist and con-artist, is whisk from kansa to the land of oz where the inhabit assum he' the great wizard of prophecy, there to save oz from the clutch of evil. fantasi adventur famili circu witch magic hope illu lost magic trick wizard 3d jame franco mila kuni rachel weisz sam raimi",
      38: 'for peter parker, life is busy. between take out the bad guy as spider-man and spend time with the person he loves, gwen stacy, high school graduat cannot come quickli enough. peter ha not forgotten about the promi he made to gwen’ father to protect her by stay away, but that is a promi he cannot keep. thing will chang for peter when a new villain, electro, emerges, an old friend, harri osborn, returns, and peter uncov new clue about hi past. action adventur fantasi obsess marvel comic sequel base on comic book electrocut medic experi electr super power andrew garfield emma stone jami foxx marc webb',
      39: "sam flynn, the tech-savvi and dare son of kevin flynn, investig hi father' disappear and is pull into the grid. with the help of a mysteri program name quorra, sam quest to stop evil dictat clu from cross into the real world. adventur action scienc fiction artifici intellig secret ident comput program dystopia comput decept duel motorcycl neon light autocraci garrett hedlund jeff bridg olivia wild joseph kosinski",
      40: 'star race car lightn mcqueen and hi pal mater head oversea to compet in the world grand prix race. but the road to the championship becom rocki as mater get caught up in an intrigu adventur of hi own: intern espionage. anim famili adventur comedi car race sequel comedi anthropomorph best friend duringcreditsst owen wilson larri the cabl guy michael cain john lasset',
      41: 'for centuries, a small but power forc of warrior call the green lantern corp ha sworn to keep intergalact order. each green lantern wear a ring that grant him superpowers. but when a new enemi call parallax threaten to destroy the balanc of power in the universe, their fate and the fate of earth lie in the hand of the first human ever recruited. adventur action thriller scienc fiction dc comic transform superhero alien alien infect magic object protector super power origin 3d ryan reynold blake live peter sarsgaard martin campbel',
      42: "woody, buzz, and the rest of andy' toy haven't been play with in years. with andi about to go to college, the gang find themselv accid left at a nefari day care center. the toy must band togeth to escap and return home to andy. anim famili comedi hostag colleg toy barbi anim escap day care teddi bear duringcreditsst toy come to life personif inanim object come to life toy stori tom hank tim allen ned beatti lee unkrich",
      43: "all grown up in post-apocalypt 2018, john connor must lead the resist of human against the increasingli domin militarist robots. but when marcu wright appears, hi exist confu the mission as connor tri to determin whether wright ha come from the futur or the past -- and whether he' friend or foe. action scienc fiction thriller save the world artifici intellig propheci san francisco cyborg killer robot ga station post-apocalypt dystopia armi firearm wartim lo angel christian bale sam worthington anton yelchin mcg",
      44: 'deckard shaw seek reveng against domin toretto and hi famili for hi comato brother. action car race speed reveng suspen car race muscl car vin diesel paul walker dwayn johnson jame wan',
      45: 'life for former unit nation investig gerri lane and hi famili seem content. suddenly, the world is plagu by a mysteri infect turn whole human popul into rampag mindless zombies. after bare escap the chaos, lane is persuad to go on a mission to investig thi disease. what follow is a peril trek around the world where lane must brave horrif danger and long odd to find answer befor human civil falls. action drama horror scienc fiction thriller dystopia apocalyp zombi nuclear weapon multipl perspect zombi apocalyp brad pitt mireil eno abigail hargrov marc forster',
      46: 'the ultim x-men ensembl fight a war for the surviv of the speci across two time period as they join forc with their younger selv in an epic battl that must chang the past – to save our future. action adventur fantasi scienc fiction 1970 mutant time travel marvel comic base on comic book superhuman storm beast aftercreditsst chang the past or futur hugh jackman jame mcavoy michael fassbend bryan singer',
      47: 'when the crew of the enterpri is call back home, they find an unstopp forc of terror from within their own organ ha deton the fleet and everyth it stand for, leav our world in a state of crisis. with a person score to settle, captain kirk lead a manhunt to a war-zon world to captur a one man weapon of mass destruction. as our hero are propel into an epic chess game of life and death, love will be challenged, friendship will be torn apart, and sacrif must be made for the onli famili kirk ha left: hi crew. action adventur scienc fiction spacecraft friendship sequel futurist space alien imax space opera terrorist bomb 3d chri pine zachari quinto zoe saldana j.j. abram',
      48: 'the stori of an ancient war that is reignit when a young farmhand unwittingli open a gateway between our world and a fearsom race of giants. unleash on the earth for the first time in centuries, the giant strive to reclaim the land they onc lost, forc the young man, jack into the battl of hi life to stop them. fight for a kingdom, it people, and the love of a brave princess, he come face to face with the unstopp warrior he thought onli exist in legend–and get the chanc to becom a legend himself. action famili fantasi base on fairi tale giant nichola hoult eleanor tomlinson ewan mcgregor bryan singer',
      49: "an adapt of f. scott fitzgerald' long island-set novel, where midwestern nick carraway is lure into the lavish world of hi neighbor, jay gatsby. soon enough, however, carraway will see through the crack of gatsby' nouveau rich existence, where obsession, madness, and tragedi await. drama romanc base on novel infidel obsess hope 3d leonardo dicaprio tobey maguir carey mulligan baz luhrmann",
      50: 'a rogu princ reluctantli join forc with a mysteri princess and together, they race against dark forc to safeguard an ancient dagger capabl of relea the sand of time – gift from the god that can rever time and allow it possessor to rule the world. adventur fantasi action romanc persia sandstorm brother against brother armageddon regent base on video game jake gyllenha gemma arterton ben kingsley mike newel',
      51: "when legion of monstrou creatures, known as kaiju, start rise from the sea, a war began that would take million of live and consum humanity' resourc for year on end. to combat the giant kaiju, a special type of weapon wa devised: massiv robots, call jaegers, which are control simultan by two pilot whose mind are lock in a neural bridge. but even the jaeger are prove nearli defenseless in the face of the relentless kaiju. on the verg of defeat, the forc defend mankind have no choic but to turn to two unlik heroes—a washed-up former pilot (charli hunnam) and an untest train (rinko kikuchi)—who are team to drive a legendari but seemingli obsolet jaeger from the past. together, they stand as mankind' last hope against the mount apocalypse. action scienc fiction adventur dystopia giant robot giant monster apocalyp imax duringcreditsst 3d idri elba charli hunnam charli day guillermo del toro",
      52: "sam witwicki take hi first tenuou step into adulthood while remain a reluct human alli of autobot-lead optimu prime. the film center around the space race between the ussr and the usa, suggest there wa a hidden transform role in it all that remain one of the planet' most danger secrets. action scienc fiction adventur moon spacecraft traitor bodyguard alien planet base on cartoon transform giant robot sabotag word domin commando duringcreditsst shia labeouf john malkovich ken jeong michael bay",
      53: "set dure the cold war, the soviet – led by sword-wield irina spalko – are in search of a crystal skull which ha supernatur power relat to a mystic lost citi of gold. after be captur and then escap from them, indi is coerc to head to peru at the behest of a young man whose friend – and indy' colleagu – professor oxley ha been captur for hi knowledg of the skull' whereabouts. adventur action save the world riddl whip treasur mexico citi leather jacket machinegun alien phenomenon maya civil peru treasur hunt nuclear explo refrig archaeologist indiana jone archeolog harrison ford cate blanchett shia labeouf steven spielberg",
      54: 'an epic journey into the world of dinosaur where an apatosauru name arlo make an unlik human friend. adventur anim famili tyrannosauru rex friend altern histori dinosaur fear storm natur human journey raymond ochoa jack bright jeffrey wright peter sohn',
      55: 'brave is set in the mystic scottish highlands, where mérida is the princess of a kingdom rule by king fergu and queen elinor. an unruli daughter and an accomplish archer, mérida one day defi a sacr custom of the land and inadvert bring turmoil to the kingdom. in an attempt to set thing right, mérida seek out an eccentr old wise woman and is grant an ill-fat wish. also figur into mérida’ quest — and serv as comic relief — are the kingdom’ three lords: the enorm lord macguffin, the surli lord macintosh, and the disagr lord dingwall. anim adventur comedi famili action fantasi scotland rebel braveri kingdom archer wish bear scot rebelli daughter turn into anim archeri ruin aftercreditsst peac offer woman director courag 3d kelli macdonald juli walter billi connolli brenda chapman',
      56: 'the uss enterpri crew explor the furthest reach of unchart space, where they encount a mysteri new enemi who put them and everyth the feder stand for to the test. action adventur scienc fiction sequel strand hatr space opera chri pine zachari quinto karl urban justin lin',
      57: "wall· is the last robot left on an earth that ha been overrun with garbag and all human have fled to outer space. for 700 year he ha continu to tri and clean up the mess, but ha develop some rather interest human-lik qualities. when a ship arriv with a sleek new type of robot, wall· think he' final found a friend and stow away on the ship when it leaves. anim famili romant comedi ben burtt elissa knight jeff garlin andrew stanton",
      58: "after an attempt assassin on ambassador han, inspector lee and detect carter are back in action as they head to pari to protect a french woman with knowledg of the triads' secret leaders. lee also hold secret meet with a unit nation authority, but hi person struggl with a chine crimin mastermind name kenji, which reveal that it' lee' long-lost...brother. action comedi crime thriller ambassador chri tucker jacki chan hiroyuki sanada brett ratner",
      59: 'dr. adrian helmsley, part of a worldwid geophi team investig the effect on the earth of radiat from unprec solar storms, learn that the earth\' core is heat up. he warn u.s. presid thoma wilson that the crust of the earth is becom unstabl and that without proper prepar for save a fraction of the world\' population, the entir race is doomed. meanwhile, writer jackson curti stumbl on the same information. while the world\' leader race to build "arks" to escap the impend cataclysm, curti struggl to find a way to save hi family. meanwhile, volcan erupt and earthquak of unprec strength wreak havoc around the world. action adventur scienc fiction civil natur disast end of the world disast apocalyp destruct volcan erupt mayan ark solar destruct of mankind john cusack amanda peet chiwetel ejiofor roland emmerich',
      60: 'miser ebenez scroog is awaken on christma eve by spirit who reveal to him hi own miser existence, what opportun he wast in hi youth, hi current cruelties, and the dire fate that await him if he doe not chang hi ways. scroog is face with hi own stori of grow bitter and meanness, and must decid what hi own futur will hold: death or redemption. anim drama holiday base on novel victorian england money christma eve scroog christma carol ghost lesson charl dicken christma gari oldman jim carrey steve valentin robert zemecki',
      61: 'in a univ where human genet materi is the most preciou commodity, an impoverish young earth woman becom the key to strateg maneuv and intern strife within a power dynasty… scienc fiction fantasi action adventur jupit space woman director 3d interspeci romanc mila kuni chan tatum sean bean lilli wachowski',
      62: 'tarzan, have acclim to life in london, is call back to hi former home in the jungl to investig the activ at a mine encampment. action adventur africa feral child tarzan jungl anim attack alexand skarsgård margot robbi christoph waltz david yate',
      63: "sibl lucy, edmund, susan and peter step through a magic wardrob and find the land of narnia. there, the they discov a charming, onc peac kingdom that ha been plung into etern winter by the evil white witch, jadis. aid by the wise and magnif lion, aslan, the children lead narnia into a spectacular, climact battl to be free of the witch' glacial power forever. adventur famili fantasi save the world witch base on novel brother sister relationship self sacrif winter cupboard beaver lion fairy-t figur battl narnia fantasi world duringcreditsst william moseley anna popplewel skandar keyn andrew adamson",
      64: "after the re-emerg of the world' first mutant, world-destroy apocalypse, the x-men must unit to defeat hi extinct level plan. scienc fiction mutant supernatur power marvel comic superhero base on comic book superhuman apocalyp superhero team world domin aftercreditsst 1980 jame mcavoy michael fassbend jennif lawrenc bryan singer",
      65: 'batman rai the stake in hi war on crime. with the help of lt. jim gordon and district attorney harvey dent, batman set out to dismantl the remain crimin organ that plagu the streets. the partnership prove to be effective, but they soon find themselv prey to a reign of chao unleash by a rise crimin mastermind known to the terrifi citizen of gotham as the joker. drama action crime thriller dc comic crime fighter secret ident scarecrow sadism chao gotham citi vigil joker superhero base on comic book tragic hero organ crime crimin mastermind district attorney imax super villain super power batman christian bale heath ledger aaron eckhart christoph nolan',
      66: 'carl fredricksen spent hi entir life dream of explor the globe and experienc life to it fullest. but at age 78, life seem to have pass him by, until a twist of fate (and a persist 8-year old wilder explor name russell) give him a new lea on life. anim comedi famili adventur age differ central and south america balloon anim float in the air duringcreditsst explor ed asner christoph plummer jordan nagai pete docter',
      67: 'when susan murphi is unwittingli clobber by a meteor full of outer space gunk on her wed day, she mysteri grow to 49-feet-11-inches. the militari jump into action and captur susan, secret her away to a covert govern compound. she is renam ginormica and place in confin with a ragtag group of monsters... anim famili adventur scienc fiction alien giant robot duringcreditsst seth rogen ree witherspoon hugh lauri conrad vernon',
      68: 'after be held captiv in an afghan cave, billionair engin toni stark creat a uniqu weapon suit of armor to fight evil. action scienc fiction adventur middl east arm dealer malibu marvel comic superhero base on comic book toni stark iron man aftercreditsst marvel cinemat univ counter terror agent coulson robert downey jr. terrenc howard jeff bridg jon favreau',
      69: "hugo is an orphan boy live in the wall of a train station in 1930 paris. he learn to fix clock and other gadget from hi father and uncl which he put to use keep the train station clock running. the onli thing that he ha left that connect him to hi dead father is an automaton (mechan man) that doesn't work without a special key which hugo need to find to unlock the secret he believ it contains. on hi adventures, he meet with a shopkeeper, georg melies, who work in the train station and hi adventure-seek god-daughter. hugo find that they have a surpri connect to hi father and the automaton, and he discov it unlock some memori the old man ha buri insid regard hi past. adventur drama famili librari clock film director key toy boy love orphan robot automaton hide filmmak leg brace doberman 3d ben kingsley sacha baron cohen asa butterfield martin scors",
      70: "legless southern inventor dr. arliss loveless plan to rekindl the civil war by assassin presid u.s. grant. onli two men can stop him: gunfight jame west and master-of-disgui and inventor artemu gordon. the two must team up to thwart loveless' plans. action adventur comedi scienc fiction western steampunk base on tv seri steam locomot drag will smith kevin kline kenneth branagh barri sonnenfeld",
      71: "archaeologist rick o'connel travel to china, pit him against an emperor from the 2,000-year-old han dynasti who' return from the dead to pursu a quest for world domination. thi time, o'connel enlist the help of hi wife and son to quash the so-cal 'dragon emperor' and hi abu of supernatur power. adventur action fantasi brendan fraser jet li john hannah rob cohen",
      72: 'from dc comic come the suicid squad, an antihero team of incarc supervillain who act as deniabl asset for the unit state government, undertak high-risk black op mission in exchang for commut prison sentences. action adventur crime fantasi scienc fiction dc comic share univ anti hero secret mission villain superhero supervillain dc extend univ will smith margot robbi joel kinnaman david ayer',
      73: "god contact congressman evan baxter and tell him to build an ark in prepar for a great flood. fantasi comedi famili father son relationship daili life marri coupl support father marriag faith baustel rescu anim natur duringcreditsst noah' ark steve carel lauren graham john goodman tom shadyac",
      74: 'major bill cage is an offic who ha never seen a day of combat when he is unceremoni demot and drop into combat. cage is kill within minutes, manag to take an alpha alien down with him. he awaken back at the begin of the same day and is forc to fight and die again... and again - as physic contact with the alien ha thrown him into a time loop. action scienc fiction deja vu time warp restart dystopia war alien militari offic soldier alien inva exoskeleton tom crui emili blunt brendan gleeson doug liman',
      75: "in a futurist world where the polar ice cap have melt and made earth a liquid planet, a beauti barmaid rescu a mutant seafar from a float island prison. they escape, along with her young charge, enola, and sail off aboard hi ship. but the trio soon becom the target of a menac pirat who covet the map to 'dryland' – which is tattoo on enola' back. adventur action ocean tattoo mutant water dystopia doomsday kevin costner chaim girafi rick avil kevin reynold",
      76: 'from the egyptian desert to deep below the polar ice caps, the elit g.i. joe team use the latest in next-gen spi and militari equip to fight the corrupt arm dealer destro and the grow threat of the mysteri cobra organ to prevent them from plung the world into chaos. adventur action thriller scienc fiction terrorist secret hostag technolog warhead govern presid reveng murder attack explo scientist laser evil cobra denni quaid chan tatum marlon wayan stephen sommer',
      77: "grow up can be a bumpi road, and it' no except for riley, who is uproot from her midwest life when her father start a new job in san francisco. like all of us, riley is guid by her emot - joy, fear, anger, disgust and sadness. the emot live in headquarters, the control center insid riley' mind, where they help advi her through everyday life. as riley and her emot struggl to adjust to a new life in san francisco, turmoil ensu in headquarters. although joy, riley' main and most import emotion, tri to keep thing positive, the emot conflict on how best to navig a new city, hou and school. drama comedi anim famili dream cartoon imaginari friend anim famili move kid unicorn duringcreditsst 3d emot ami poehler phylli smith richard kind pete docter",
      78: 'after a threat from the tiger shere khan forc him to flee the jungle, a man-cub name mowgli embark on a journey of self discoveri with the help of panther, bagheera, and free spirit bear, baloo. famili adventur drama fantasi base on novel snake wolf eleph tiger feral child panther remak bear jungl talk anim orphan anim talk to anim neel sethi bill murray ben kingsley jon favreau',
      79: "with the world now awar of hi dual life as the armor superhero iron man, billionair inventor toni stark face pressur from the government, the press and the public to share hi technolog with the military. unwil to let go of hi invention, stark, with pepper pott and jame 'rhodey' rhode at hi side, must forg new allianc – and confront power enemies. adventur action scienc fiction malibu marvel comic superhero base on comic book reveng aftercreditsst marvel cinemat univ robert downey jr. gwyneth paltrow don cheadl jon favreau",
      80: 'after the evil queen marri the king, she perform a violent coup in which the king is murder and hi daughter, snow white, is taken captive. almost a decad later, a grown snow white is still in the clutch of the queen. in order to obtain immortality, the evil queen need the heart of snow white. after snow escap the castle, the queen send the huntsman to find her in the dark forest. adventur fantasi drama queen magic fairi tale immort forest decept woman etern youth snow white evil queen evil stepmoth imprison sorceress kristen stewart charliz theron chri hemsworth rupert sander',
      81: "the untold stori of disney' most icon villain from the 1959 classic 'sleep beauty'. a beautiful, pure-heart young woman, malef ha an idyl life grow up in a peaceabl forest kingdom, until one day when an invad armi threaten the harmoni of the land. malef rise to be the land' fiercest protector, but she ultim suffer a ruthless betray – an act that begin to turn her heart into stone. bent on revenge, malef face an epic battl with the invad king' successor and, as a result, place a cur upon hi newborn infant aurora. as the child grows, malef realiz that aurora hold the key to peac in the kingdom - and to maleficent' true happi as well. fantasi adventur action famili romanc fairi tale villain sleep beauti dark fantasi base on fairi tale adapt retel literari adapt 3d angelina joli ell fan sharlto copley robert stromberg",
      82: 'a group of scientist in san francisco struggl to stay aliv in the aftermath of a plagu that is wipe out humanity, while caesar tri to maintain domin over hi commun of intellig apes. scienc fiction action drama thriller leader coloni post-apocalypt dystopia forest sequel wood ape scientist monkey medic research anim attack plagu 3d andi serki jason clark gari oldman matt reev',
      83: 'the lover is an epic romanc time travel adventur film. helm by roland joffé from a stori by ajey jhankar, the film is a sweep tale of an imposs love set against the backdrop of the first anglo-maratha war across two time period and contin and centr around four charact — a british offic in 18th centuri coloni india, the indian woman he fall deepli in love with, an american present-day marin biologist and hi wife. action adventur scienc fiction romanc josh hartnett simon kessel tamsin egerton roland joffé',
      84: 'base on the origin 1941 movi from japan, and from ancient japan’ most endur tale, the epic 3d fantasy-adventur 47 ronin is born. keanu reev lead the cast as kai, an outcast who join oishi (hiroyuki sanada), the leader of the 47 outcast samurai. togeth they seek vengeanc upon the treacher overlord who kill their master and banish their kind. to restor honor to their homeland, the warrior embark upon a quest that challeng them with a seri of trial that would destroy ordinari warriors. drama action adventur fantasi japan suicid samurai base on true stori samurai sword ronin shogun half breed 3d keanu reev hiroyuki sanada kou shibasaki carl rinsch',
      85: 'after the cataclysm event in new york with the avengers, steve rogers, aka captain america is live quietli in washington, d.c. and tri to adjust to the modern world. but when a s.h.i.e.l.d. colleagu come under attack, steve becom embroil in a web of intrigu that threaten to put the world at risk. join forc with the black widow, captain america struggl to expo the ever-widen conspiraci while fight off profess assassin sent to silenc him at everi turn. when the full scope of the villain plot is revealed, captain america and the black widow enlist the help of a new ally, the falcon. however, they soon find themselv up against an unexpect and formid enemy—th winter soldier. action adventur scienc fiction washington d.c. futur shield marvel comic superhero base on comic book captain america aftercreditsst duringcreditsst marvel cinemat univ 3d polit thriller chri evan samuel l. jackson scarlett johansson anthoni russo',
      86: "a bore and domest shrek pact with deal-mak rumpelstiltskin to get back to feel like a real ogr again, but when he' dupe and sent to a twist version of far far away—wh rumpelstiltskin is king, ogr are hunted, and he and fiona have never met—h set out to restor hi world and reclaim hi true love. comedi adventur fantasi anim famili ogr 3d mike myer eddi murphi cameron diaz mike mitchel",
      87: 'bound by a share destiny, a bright, optimist teen burst with scientif curio and a former boy-geniu inventor jade by disillus embark on a danger-fil mission to unearth the secret of an enigmat place somewh in time and space that exist in their collect memori as "tomorrowland." adventur famili mysteri scienc fiction inventor apocalyp destini imax dreamer futurist car futurist citi britt robertson georg clooney raffey cassidi brad bird',
      88: 'the special bond that develop between plus-siz inflat robot baymax, and prodigi hiro hamada, who team up with a group of friend to form a band of high-tech heroes. adventur famili anim action comedi brother brother relationship hero talent reveng best friend anoth dimen robot boy geniu hate aftercreditsst moral dilemma 3d teen superhero dead brother scott adsit ryan potter daniel henney chri william',
      89: "wreck-it ralph is the 9-foot-tall, 643-pound villain of an arcad video game name fix-it felix jr., in which the game' titular hero fix build that ralph destroys. want to prove he can be a good guy and not just a villain, ralph escap hi game and land in hero' duty, a first-person shooter where he help the game' hero battl against alien invaders. he later enter sugar rush, a kart race game set on track made of candies, cooki and other sweets. there, ralph meet vanellop von schweetz who ha learn that her game is face with a dire threat that could affect the entir arcade, and one that ralph may have inadvert started. famili anim comedi adventur support group product placement bulli race arcad medal self esteem curio precoci child aftercreditsst duringcreditsst first person shooter glitch carefr video gamer q*bert interrupt wed social reject john c. reilli sarah silverman jack mcbrayer rich moor",
      90: 'when a doubt young boy take an extraordinari train ride to the north pole, he embark on a journey of self-discoveri that show him that the wonder of life never fade for those who believe. adventur anim famili fantasi santa clau nerd faith gift bell beard north pole chute trestl ticket christma tom hank michael jeter nona gay robert zemecki',
      91: 'we alway knew they were come back. use recov alien technology, the nation of earth have collabor on an immen defen program to protect the planet. but noth can prepar us for the aliens’ advanc and unprec force. onli the ingenu of a few brave men and women can bring our world back from the brink of extinction. action adventur scienc fiction altern histori alien inva liam hemsworth jeff goldblum bill pullman roland emmerich',
      92: 'as the son of a vike leader on the cusp of manhood, shi hiccup horrend haddock iii face a rite of passage: he must kill a dragon to prove hi warrior mettle. but after down a fear dragon, he realiz that he no longer want to destroy it, and instead befriend the beast – which he name toothless – much to the chagrin of hi warrior father fantasi adventur anim famili fli blacksmith arena island night ship train villag forest vike friendship ignor flight nest dragon battl combat well warrior jay baruchel gerard butler craig ferguson chri sander',
      93: "it' been 10 year sinc john connor save earth from judgment day, and he' now live under the radar, steer clear of use anyth skynet can trace. that is, until he encount t-x, a robot assassin order to finish what t-1000 started. good thing connor' former nemesis, the terminator, is back to aid the now-adult connor … just like he promised. action thriller scienc fiction save the world artifici intellig man vs machin cyborg killer robot sun glass leather jacket nanotechnolog rocket launcher firemen veterinarian fire engin dystopia psychiatrist arnold schwarzenegg nick stahl clair dane jonathan mostow",
      94: 'light year from earth, 26 year after be abducted, peter quill find himself the prime target of a manhunt after discov an orb want by ronan the accuser. action scienc fiction adventur marvel comic spaceship space outer space orphan adventur aftercreditsst duringcreditsst marvel cinemat univ chri pratt zoe saldana dave bautista jame gunn',
      95: 'interstellar chronicl the adventur of a group of explor who make use of a newli discov wormhol to surpass the limit on human space travel and conquer the vast distanc involv in an interstellar voyage. adventur drama scienc fiction save the world artifici intellig father son relationship singl parent nasa expedit wormhol space travel famin black hole dystopia race against time quantum mechan spaceship space rescu famili relationship farmhou robot astronaut scientist father daughter relationship singl father farmer space station imax astrophi zero graviti courag time paradox rel matthew mcconaughey jessica chastain ann hathaway christoph nolan',
      96: 'cobb, a skill thief who commit corpor espionag by infiltr the subconsci of hi target is offer a chanc to regain hi old life as payment for a task consid to be impossible: "inception", the implant of anoth person\' idea into a target\' subconscious. action thriller scienc fiction mysteri adventur loss of lover dream kidnap sleep subconsci heist redempt femal hero leonardo dicaprio joseph gordon-levitt ellen page christoph nolan',
      97: "from the mind behind evangelion come a hit larger than life. when a massive, gill monster emerg from the deep and tear through the city, the govern scrambl to save it citizens. a rag-tag team of volunt cut through a web of red tape to uncov the monster' weak and it mysteri tie to a foreign superpower. but time is not on their side - the greatest catastroph to ever befal the world is about to evolv right befor their veri eyes. action adventur drama horror scienc fiction monster godzilla giant monster destruct kaiju toyko hiroki hasegawa yutaka takenouchi satomi ishihara hideaki anno",
      98: 'bilbo baggins, a hobbit enjoy hi quiet life, is swept into an epic quest by gandalf the grey and thirteen dwarv who seek to reclaim their mountain home from smaug, the dragon. adventur fantasi action riddl elv dwarv orc middle-earth (tolkien) hobbit mountain wizard journey ring goblin courag giant tunnel underground lake buri treasur climb a tree invi ancient gnome ian mckellen martin freeman richard armitag peter jackson',
      99: "domen toretto is a lo angel street racer suspect of mastermind a seri of big-rig hijackings. when undercov cop brian o'conn infiltr toretto' iconoclast crew, he fall for toretto' sister and must choo a side: the gang or the lapd. action crime thriller street gang car race undercov auto-tun lo angel car automobil race aftercreditsst duringcreditsst paul walker vin diesel michel rodriguez rob cohen",
      100: 'tell the stori of benjamin button, a man who start age backward with bizarr consequences. fantasi drama thriller mysteri romanc diari navi funer tea travel hospit cate blanchett brad pitt tilda swinton david fincher',
      101: 'befor charl xavier and erik lensherr took the name professor x and magneto, they were two young men discov their power for the first time. befor they were arch-enemies, they were closest of friends, work togeth with other mutant (some familiar, some new), to stop the greatest threat the world ha ever known. action scienc fiction adventur cia mutant mine marvel comic superhero base on comic book superhuman histor fiction nuclear war cuban missil crisi world war iii 1960 jame mcavoy michael fassbend jennif lawrenc matthew vaughn',
      102: 'with the nation of panem in a full scale war, katniss confront presid snow in the final showdown. team with a group of her closest friend – includ gale, finnick, and peeta – katniss goe off on a mission with the unit from district 13 as they risk their live to stage an assassin attempt on presid snow who ha becom increasingli obsess with destroy her. the mortal traps, enemies, and moral choic that await katniss will challeng her more than ani arena she face in the hunger games. action adventur scienc fiction revolut strong woman dystopia game of death 3d base on young adult novel jennif lawrenc josh hutcherson liam hemsworth franci lawrenc',
      103: "balthazar blake is a master sorcer in modern-day manhattan tri to defend the citi from hi arch-nemesis, maxim horvath. balthazar can't do it alone, so he recruit dave stutler, a seemingli averag guy who demonstr hidden potential, as hi reluct protégé. the sorcer give hi unwil accompl a crash cour in the art and scienc of magic, and together, these unlik partner work to stop the forc of darkness. fantasi adventur action comedi drama witch fire wolf fountain magic book castl water apprent train merlin love mission sorcer dragon aftercreditsst apprendista morgana nicola cage jay baruchel monica bellucci jon turteltaub",
      104: "a pack crui ship travel the atlant is hit and overturn by a massiv wave, compel the passeng to begin a dramat fight for their lives. adventur action drama thriller new year' eve fire drown cataclysm loss of father atlant ocean ball self-abandon shipwreck giant wave blackout ship daughter singl escap capsiz ship kurt russel richard dreyfuss josh luca wolfgang petersen",
      105: 'in the sequel to tim burton\' "alic in wonderland", alic kingsleigh return to underland and face a new adventur in save the mad hatter. fantasi base on novel clock queen sequel alic in wonderland dark fantasi mad hatter 3d johnni depp mia wasikowska ann hathaway jame bobin',
      106: "the king of far far away ha die and shrek and fiona are to becom king &amp; queen. however, shrek want to return to hi cozi swamp and live in peac and quiet, so when he find out there is anoth heir to the throne, they set off to bring him back to rule the kingdom. fantasi adventur anim comedi famili ambush sad stage liber of prison island traitor shipwreck princ ship donkey kingdom theatr play transform concili trick heir to the throne assault board school coup d'etat teacher best friend dragon cowardli pregnanc captur duringcreditsst mike myer eddi murphi cameron diaz chri miller",
      107: 'the peac realm of azeroth stand on the brink of war as it civil face a fearsom race of invaders: orc warrior flee their die home to colon another. as a portal open to connect the two worlds, one armi face destruct and the other face extinction. from oppo sides, two hero are set on a colli cour that will decid the fate of their family, their people, and their home. action adventur fantasi video game elv orc magic chase base on comic book sorcer fiction war base on video game wizard fiction languag muscl orc sword and sorceri paula patton travi fimmel ben foster duncan jone',
      108: "the year is 2029. john connor, leader of the resist continu the war against the machines. at the lo angel offensive, john' fear of the unknown futur begin to emerg when tecom spi reveal a new plot by skynet that will attack him from both fronts; past and future, and will ultim chang warfar forever. scienc fiction action thriller adventur save the world artifici intellig cyborg killer robot futur time travel dystopia sequel fiction duringcreditsst 3d arnold schwarzenegg jason clark emilia clark alan taylor",
      109: 'thi time around edmund and luci pevensie, along with their peski cousin eustac scrubb find themselv swallow into a paint and on to a fantast narnian ship head for the veri edg of the world. adventur famili fantasi base on novel magic good vs evil king narnia fantasi world knife held to throat snow quest skandar keyn georgi henley simon pegg michael apt',
      110: "the lifelong friendship between rafe mccawley and danni walker is put to the ultim test when the two ace fighter pilot becom entangl in a love triangl with beauti naval nur evelyn johnson. but the rivalri between the friends-turned-fo is immedi put on hold when they find themselv at the center of japan' devast attack on pearl harbor on dec. 7, 1941. histori romanc war nur patriot hawaii world war ii pilot pearl harbor u.s. air forc airplan war armi love pin-up ben affleck josh hartnett kate beckins michael bay",
      111: 'young teenager, sam witwicki becom involv in the ancient struggl between two extraterrestri faction of transform robot – the heroic autobot and the evil decepticons. sam hold the clue to unimagin power and the decepticon will stop at noth to retriev it. adventur scienc fiction action destroy transform alien base on toy transform robot duringcreditsst teenag hero shia labeouf josh duhamel megan fox michael bay',
      112: 'alexander, the king of macedonia, lead hi legion against the giant persian empire. after defeat the persians, he lead hi armi across the then known world, ventur farther than ani western had ever gone, all the way to india. war histori action adventur drama romanc aristotl egypt greec persia eleph campaign alexand the great homosexu gay relationship ancient world colin farrel angelina joli val kilmer oliv stone',
      113: "return for hi fifth year of studi at hogwarts, harri is stun to find that hi warn about the return of lord voldemort have been ignored. left with no choice, harri take matter into hi own hands, train a small group of student – dub 'dumbledore' army' – to defend themselv against the dark arts. adventur fantasi famili mysteri propheci witch loss of lover magic cut the cord child hero die and death broom sorcerer' apprent school of witchcraft black magic death of a friend sorceri occult daniel radcliff rupert grint emma watson david yate",
      114: "harri start hi fourth year at hogwarts, compet in the treacher triwizard tournament and face the evil lord voldemort. ron and hermion help harri manag the pressur – but voldemort lurks, await hi chanc to destroy harri and all that he stand for. adventur fantasi famili magic die and death broom sorcerer' apprent school of witchcraft chosen one black magic board school vision tournament teenag wizard teenag hero base on young adult novel daniel radcliff rupert grint emma watson mike newel",
      115: "hancock is a down-and-out superhero who' forc to employ a pr expert to help repair hi imag when the public grow weari of all the damag he' inflict dure hi lifesav heroics. the agent' idea of imprison the antihero to make the world miss him prove successful, but will hancock stick to hi new sen of purpo or slip back into old habits? fantasi action fli alcohol love of one' life forbidden love lover affect adverti expert alcohol invuln superhero poki duringcreditsst will smith charliz theron jason bateman peter berg",
      116: 'robert nevil is a scientist who wa unabl to stop the spread of the terribl viru that wa incur and man-made. immune, nevil is now the last human survivor in what is left of new york citi and perhap the world. for three years, nevil ha faith sent out daili radio messages, desper to find ani other survivor who might be out there. but he is not alone. drama horror action thriller scienc fiction save the world lost civili post-apocalypt dystopia matter of life and death alon helpless viru pandem will smith alic braga charli tahan franci lawrenc',
      117: "a young boy win a tour through the most magnif chocol factori in the world, led by the world' most unusu candi maker. adventur comedi famili fantasi london england father son relationship chocol factori worker base on novel parent kid relationship candi overweight child grandfath grandson relationship teacher johnni depp freddi highmor david kelli tim burton",
      118: "a rat name remi dream of becom a great french chef despit hi family' wish and the obviou problem of be a rat in a decidedli rodent-phob profession. when fate place remi in the sewer of paris, he find himself ideal situat beneath a restaur made famou by hi culinari hero, august gusteau. despit the appar danger of be an unlik - and certainli unwant - visitor in the kitchen of a fine french restaurant, remy' passion for cook soon set into motion a hilari and excit rat race that turn the culinari world of pari upsid down. anim comedi famili fantasi pari brother brother relationship expen restaur river cook mou confid roof window leav one' famili work restaur critic kitchen spice court cookbook famili chef rat patton oswalt ian holm lou romano jan pinkava",
      119: 'driven by tragedy, billionair bruce wayn dedic hi life to uncov and defeat the corrupt that plagu hi home, gotham city. unabl to work within the system, he instead creat a new identity, a symbol of fear for the crimin underworld - the batman. action crime drama himalaya martial art dc comic crime fighter secret ident undercov hero loss of father societi gotham citi vigil superhero base on comic book rivalri tragic hero ninja good vs evil crime super power haunt by the past evil doctor escapad master villain fight crime unfulfil love and romanc unfulfil love christian bale michael cain liam neeson christoph nolan',
      120: 'alex, marty, melman, gloria, king julien, maurice, the penguin and the chimp are back and still maroon on madagascar. in the face of thi obstacle, the new yorker have hatch a plan so crazi it just might work. with militari precision, the penguin have repair an old crash plane... sort of. famili anim africa jealousi danc hunger lion zoo hippopotamu chimp penguin volcano madagascar airplan zebra sequel shark imax duringcreditsst ben stiller jada pinkett smith david schwimmer eric darnel',
      121: "hapless museum night watchman larri daley must help hi living, breath exhibit friend out of a pickl now that they'v been transfer to the archiv at the smithsonian institution. larry' (mis)adventur thi time includ close encount with amelia earhart, abe lincoln and ivan the terrible. adventur fantasi action comedi famili museum theodor roosevelt duringcreditsst amelia earhart smithsonian ben stiller ami adam owen wilson shawn levi",
      122: 'after seek to live a normal life, logan set out to aveng the death of hi girlfriend by undergo the mutant weapon x program and becom wolverine. adventur action thriller scienc fiction corrupt mutant boxer armi marvel comic superhero aftercreditsst duringcreditsst hugh jackman liev schreiber danni huston gavin hood',
      123: 'the human citi of zion defend itself against the massiv inva of the machin as neo fight to end the war at anoth front while also oppo the rogu agent smith. adventur action thriller scienc fiction save the world artifici intellig man vs machin fli philosophi fortun teller kung fu underground world killer robot templ subway dream sun hero fight sunlight comput viru key futur precognit super comput machin town ying yang die and death virtual realiti dystopia comput faith world religion truth rescu mission cyberpunk woman director yin yang gnostic keanu reev laurenc fishburn carrie-ann moss lilli wachowski',
      124: "young princess anna of arendel dream about find true love at her sister elsa’ coronation. fate take her on a danger journey in an attempt to end the etern winter that ha fallen over the kingdom. she' accompani by ice deliveri man kristoff, hi reindeer sven, and snowman olaf. on an adventur where she will find out what friendship, courage, family, and true love realli means. anim adventur famili queen music princess betray snowman anim reindeer cur snow troll mountain climber aftercreditsst woman director 3d kristen bell idina menzel jonathan groff chri buck",
      125: "six month after the event depict in the matrix, neo ha prove to be a good omen for the free humans, as more and more human are be freed from the matrix and brought to zion, the one and onli stronghold of the resistance. neo himself ha discov hi superpow includ super speed, abil to see the code of the thing insid the matrix and a certain degr of pre-cognition. but a nasti piec of news hit the human resistance: 250,000 machin sentinel are dig to zion and would reach them in 72 hours. as zion prepar for the ultim war, neo, morpheu and triniti are advi by the oracl to find the keymak who would help them reach the source. meanwhil neo' recurr dream depict trinity' death have got him worri and as if it wa not enough, agent smith ha somehow escap deletion, ha becom more power than befor and ha fix neo as hi next target. adventur action thriller scienc fiction save the world artifici intellig man vs machin martial art kung fu underground world dream hero fight comput viru key futur plato precognit rave die and death virtual realiti dystopia comput faith world religion truth mission cyberpunk woman director gnostic keanu reev carrie-ann moss laurenc fishburn lilli wachowski",
      126: 'thor fight to restor order across the cosmos… but an ancient race led by the veng malekith return to plung the univ back into darkness. face with an enemi that even odin and asgard cannot withstand, thor must embark on hi most peril and person journey yet, one that will reunit him with jane foster and forc him to sacrif everyth to save us all. action adventur fantasi marvel comic superhero base on comic book hostil takeov nor mytholog aftercreditsst duringcreditsst marvel cinemat univ 3d asgard chri hemsworth natali portman tom hiddleston alan taylor',
      127: "an apocalypt stori set in the furthest reach of our planet, in a stark desert landscap where human is broken, and most everyon is craze fight for the necess of life. within thi world exist two rebel on the run who just might be abl to restor order. there' max, a man of action and a man of few words, who seek peac of mind follow the loss of hi wife and child in the aftermath of the chaos. and furiosa, a woman of action and a woman who believ her path to surviv may be achiev if she can make it across the desert back to her childhood homeland. action adventur scienc fiction thriller futur chase post-apocalypt dystopia australia rescu surviv on the run convoy peak oil dark futur tom hardi charliz theron nichola hoult georg miller",
      128: 'harvard symbologist robert langdon investig a mysteri symbol sear into the chest of a murder physicist. he discov evid of the unimaginable, the rebirth of an ancient secret brotherhood known as the illuminati, the most power underground organ ever to walk the earth. thriller mysteri rome vatican base on novel symbol christian illuminati quantum mechan prequel anti matter conspiraci investig cathol cern tom hank ewan mcgregor ayelet zurer ron howard',
      129: "against hi father odin' will, the mighti thor - a power but arrog warrior god - recklessli reignit an ancient war. thor is cast down to earth and forc to live among human as punishment. onc here, thor learn what it take to be a true hero when the most danger villain of hi world send the darkest forc of asgard to invad earth. adventur fantasi action new mexico banish shield marvel comic hammer superhero base on comic book redempt nor mytholog aftercreditsst marvel cinemat univ 3d asgard odin heimdal chri hemsworth natali portman tom hiddleston kenneth branagh",
      130: 'bolt is the star of the biggest show in hollywood. the onli problem is, he think it\' real. after he\' accid ship to new york citi and separ from penny, hi belov co-star and owner, bolt must har all hi "super powers" to find a way home. anim famili adventur comedi hamster kid and famili anim cat vs dog duringcreditsst dog cat friendship anim lead girl dog relationship john travolta miley cyru susi essman chri william',
      131: 'a team of train secret agent animals, guinea pig darwin, juarez, blaster, mole speckles, and fli mooch take on a mission for the us govern to stop evil leonard saber, who plan to destroy the world with household appliances. but the govern shut them down and they are sentenc to a pet shop. can they escap to defeat the villain and save the world? fantasi action adventur famili comedi dyr duringcreditsst sam rockwel penélop cruz traci morgan hoyt yeatman',
      132: "a decad after hi heroic defeat of the monstrou kraken, perseus-th demigod son of zeus-i attempt to live a quieter life as a villag fisherman and the sole parent to hi 10-year old son, helius. meanwhile, a struggl for supremaci rage between the god and the titans. danger weaken by humanity' lack of devotion, the god are lose control of the imprison titan and their feroci leader, kronos, father of the long-rul brother zeus, hade and poseidon. adventur underworld hade mytholog greek mytholog zeu perseu god ancient greec base on greek myth are 3d sam worthington liam neeson ralph fienn jonathan liebesman",
      133: 'vampir barnaba collin is inadvert freed from hi tomb and emerg into the veri chang world of 1972. he return to collinwood manor to find that hi once-grand estat and famili have fallen into ruin. comedi fantasi witch imprison vampir cur fish out of water chain gothic mad old hou lost love angri mob 18th centuri ghost hidden room old mansion johnni depp michel pfeiffer helena bonham carter tim burton',
      134: 'ethan and team take on their most imposs mission yet, erad the syndic - an intern rogu organ as highli skill as they are, commit to destroy the imf. action adventur thriller london england spi austria villain sequel mission conspiraci vienna opera vienna tom crui rebecca ferguson simon pegg christoph mcquarri',
      135: 'lawrenc talbot, an american man on a visit to victorian london to make amend with hi estrang father, get bitten by a werewolf and, after a moonlight transformation, leav him with a savag hunger for flesh. drama horror thriller father son relationship victorian england remak rural set werewolf benicio del toro anthoni hopkin emili blunt joe johnston',
      136: "barri b. benson, a bee who ha just graduat from college, is disillu at hi lone career choice: make honey. on a special trip outsid the hive, barry' life is save by vanessa, a florist in new york city. as their relationship blossoms, he discov human actual eat honey, and subsequ decid to sue us. famili anim adventur comedi factori worker tenni flower florist flower shop pilot colleg airplan beehiv court aftercreditsst jerri seinfeld rené zellweg jim cum steve hickner",
      137: 'po is now live hi dream as the dragon warrior, protect the valley of peac alongsid hi friend and fellow kung fu masters, the furiou five - tigress, crane, mantis, viper and monkey. but po’ new life of awesom is threaten by the emerg of a formid villain, who plan to use a secret, unstopp weapon to conquer china and destroy kung fu. it is up to po and the furiou five to journey across china to face thi threat and vanquish it. but how can po stop a weapon that can stop kung fu? he must look to hi past and uncov the secret of hi mysteri origins; onli then will he be abl to unlock the strength he need to succeed. anim famili martial art hope fleet panda mission woman director jack black angelina joli dustin hoffman jennif yuh nelson',
      138: 'the stori follow the adventur of aang, a young successor to a long line of avatars, who must put hi childhood way asid and stop the fire nation from enslav the water, earth and air nations. action adventur famili fantasi fire ice war ship princ kingdom water villag arrest remak attack avatar air spirit world domin cheer noah ringer nicola peltz jackson rathbon m. night shyamalan',
      139: 'retir from activ duti to train new imf agents, ethan hunt is call back into action to confront sadist arm dealer, owen davian. hunt must tri to protect hi girlfriend while work with hi new team to complet the mission. adventur action thriller berlin cia vatican white hou secret ident secret explo mobil phone map traitor mask honeymoon shanghai pretend murder secret mission letter funer cover investig to shoot dead secret agent video stamp hard drive e-mail deciph suitca comput reveng murder mission hospit duel disgui celebr good and bad research laboratori blast tom crui philip seymour hoffman ving rhame j.j. abram',
      140: "capitol policeman john cale ha just been deni hi dream job with the secret servic of protect presid jame sawyer. not want to let down hi littl girl with the news, he take her on a tour of the white house, when the complex is overtaken by a heavili arm paramilitari group. now, with the nation' govern fall into chao and time run out, it' up to cale to save the president, hi daughter, and the country. action drama thriller usa presid conspiraci secret servic the white hou chan tatum jami foxx joey king roland emmerich",
      141: "when martian suddenli abduct hi mom, mischiev milo rush to the rescu and discov whi all mom are so special. adventur anim famili boy alien rescu martian alien abduct alien inva base on children' book duringcreditsst seth green joan cusack dan fogler simon well",
      142: 'london high-societi mouse, roddi is flush down the toilet by sid, a common sewer rat. hang on for a madcap adventur deep in the sewer bowel of ratropolis, where roddi meet the resourc rita, the rodent-h toad and hi faith thugs, spike and whitey. adventur anim comedi famili london england underworld return ship frog girlfriend rubin hugh jackman kate winslet ian mckellen david bower',
      143: 'live a bleak exist at a london orphanage, 12-year-old peter find himself whisk away to the fantast world of neverland. adventur await as he meet new friend jame hook and the warrior tiger lily. they must band togeth to save neverland from the ruthless pirat blackbeard. along the way, the rebelli and mischiev boy discov hi true destiny, becom the hero forev known as peter pan. adventur famili fantasi fli magic fairi tale peter pan mermaid pirat fantasi world levi miller garrett hedlund hugh jackman joe wright',
      144: 'a young boy and hi dog, who happen to have a genius-level iq, spring into action when their time-travel machin is stolen and moment in histori begin to be changed. anim adventur famili father son relationship egypt intellig adopt time travel boy child prodigi friendship grow up children talk anim talk dog dog first love ancient egypt time travel duringcreditsst new school georg washington gag troubl time paradox prodigi ty burrel max charl ariel winter rob minkoff',
      145: "in year 1250 b.c. dure the late bronz age, two emerg nation begin to clash. paris, the trojan prince, convinc helen, queen of sparta, to leav her husband menelaus, and sail with him back to troy. after menelau find out that hi wife wa taken by the trojans, he ask hi brother agamemnom to help him get her back. agamemnon see thi as an opportun for power. so they set off with 1,000 ship hold 50,000 greek to troy. with the help of achilles, the greek are abl to fight the never befor defeat trojans. adventur drama war brother brother relationship adulteri mytholog beauti trojan war braveri wall fraud hostil epic sword fight battlefield ancient world pyre ancient greec trojan hor trojan bronz age sparta greec helen of troy homer' iliad brad pitt orlando bloom eric bana wolfgang petersen",
      146: 'alex, marty, gloria and melman are still tri to get back to the big appl and their belov central park zoo, but first they need to find the penguins. when they travel to mont carlo, they attract the attent of anim control after gate crash a parti and are join by the penguins, king julian and co., and the monkeys. how do a lion, zebra, hippo, giraffe, four penguins, two monkeys, three lemur travel through europ without attract attent and get back to new york? they join a travel circus. their attempt to get back to new york are consist hamper by the captain of anim control who want to make alex part of her collection. onc they make it back to new york marty, alex, gloria and melman realiz that they want to be part of the travel circus. anim famili madagascar 3d ben stiller sacha baron cohen david schwimmer conrad vernon',
      147: "bond take on a north korean leader who undergo dna replac procedur that allow him to assum differ identities. american agent, jinx johnson assist bond in hi attempt to thwart the villain' plan to exploit a satellit that is power by solar energy. adventur action thriller laser british secret servic secret servic agent space base weapon pierc brosnan hall berri rosamund pike lee tamahori",
      148: 'follow a ghost inva of manhattan, paranorm enthusiast erin gilbert and abbi yates, nuclear engin jillian holtzmann, and subway worker patti tolan band togeth to stop the otherworldli threat. action fantasi comedi femal friendship ghost hunt reboot ghost melissa mccarthi kristen wiig kate mckinnon paul feig',
      149: "when an asteroid threaten to collid with earth, nasa honcho dan truman determin the onli way to stop it is to drill into it surfac and deton a nuclear bomb. thi lead him to renown driller harri stamper, who agr to helm the danger space mission provid he can bring along hi own hotshot crew. among them is the cocksur a.j. who harri think isn't good enough for hi daughter, until the mission prove otherwise. action thriller scienc fiction adventur save the world pari moon cataclysm asteroid self sacrif nasa space marin loss of father daughter space wed astronaut eiffel tower pari duringcreditsst disast movi space centr bruce willi billi bob thornton ben affleck michael bay",
      150: "kay and jay reunit to provid our best, last and onli line of defen against a sinist seductress who level the toughest challeng yet to the mib' untarnish mission statement – protect earth from the scum of the universe. it' been four year sinc the alien-seek agent avert an intergalact disast of epic proportions. now it' a race against the clock as jay must convinc kay – who not onli ha absolut no memori of hi time spent with the mib, but is also the onli live person left with the experti to save the galaxi – to reunit with the mib befor the earth submit to ultim destruction. action adventur comedi scienc fiction save the world secret ident sun glass undercov space marin illeg immigr deport new ident fli saucer light firearm alien fiction govern agenc tommi lee jone will smith rip torn barri sonnenfeld",
      151: '6th-centuri scandinavian warrior, beowulf embark on a mission to slay the manlik ogr grendel, a descend of cain. adventur action anim denmark nordic mytholog lie pride and vaniti folk hero human weak vike alien festiv hall sin royalti cur battl ancient world adult anim motion captur ray winston angelina joli anthoni hopkin robert zemecki',
      152: 'continu hi "legendari adventur of awesomeness", po must face two huge epic, but differ threats: one supernatur and the other a littl closer to hi home. action adventur anim comedi famili china martial art kung fu villag panda sequel talk anim anthropomorph dragon ancient china wuxia woman director jack black bryan cranston dustin hoffman jennif yuh nelson',
      153: 'in the 4th instal of the mission imposs series, ethan hunt (cruise) and hi team are race against time to track down a danger terrorist name hendrick (nyqvist), who ha gain access to russian nuclear launch code and is plan a strike on the unit states. an attempt to stop him end in an explo cau sever destruct to the kremlin and the imf to be implic in the bombing, forc the presid to disavow them. no longer be aid by the government, ethan and hi team chase hendrick around the globe, although they might still be too late to stop a disaster. action thriller adventur fight sequel mission explo broken arm imax nuclear threat tom crui jeremi renner simon pegg brad bird',
      154: 'when an evil spirit known as pitch lay down the gauntlet to take over the world, the immort guardian must join forc for the first time to protect the hopes, belief and imagin of children all over the world. fantasi anim famili dream santa clau nightmar easter bunni tooth fairi jack frost sandman duringcreditsst chri pine alec baldwin jude law peter ramsey',
      155: "after dick harper lose hi job at globodyn in an enron-esqu collapse, he and hi wife, jane, turn to crime in order to handl the massiv debt they now face. two intellig people, dick and jane actual get pretti good at rob peopl and even enjoy it -- but they have second thought when they'r remind that crime can hurt innoc people. when the coupl hear that globodyn boss jack mccallist actual swindl the company, they plot revenge. comedi base on novel desper robber hold-up robberi remak suburbia loss of job humili unemploy bankruptci travel agent rich to rag bearer bond comeupp jim carrey téa leoni alec baldwin dean parisot",
      156: "nathan algren is an american hire to instruct the japan armi in the way of modern warfare, which find him learn to respect the samurai and the honor principl that rule them. press to destroy the samurai' way of life in the name of modern and open trade, algren decid to becom an ultim warrior himself and to fight for their right to exist. drama action war histori japan war crime sen of guilt swordplay gener samurai war veteran katana sword arm deal homeland emperor languag barrier self-discoveri mountain villag foreign legion mercenari campaign commerci agreement insurg leader war strategi gettysburg loss of husband slaughter soldier alcohol u.s. soldier japan armi 19th centuri war trauma tom crui ken watanab william atherton edward zwick",
      157: 'the defiant leader mose rise up against the egyptian pharaoh ramses, set 400,000 slave on a monument journey of escap from egypt and it terrifi cycl of deadli plagues. adventur drama action mose bibl ancient egypt 3d ram christian bale joel edgerton john turturro ridley scott',
      158: 'the fate of the galaxi rest in the hand of bitter rivals. one, jame kirk, is a delinquent, thrill-seek iowa farm boy. the other, spock, a vulcan, wa rai in a logic-ba societi that reject all emotion. as fieri instinct clash with calm reason, their unlik but power partnership is the onli thing capabl of lead their crew through unimagin danger, boldli go where no one ha gone before. the human adventur ha begun again. scienc fiction action adventur spacecraft teleport space mission parachut time travel black hole supernova prequel warp speed futurist warp engin romulan outer space vulcan altern realiti space opera reboot chri pine zachari quinto leonard nimoy j.j. abram',
      159: 'after be bitten by a genet alter spider, nerdi high school student peter parker is endow with amaz powers. fantasi action loss of lover spider thanksgiv bad boss hostil marvel comic superhero poki evil refer to superman goblin tobey maguir willem dafo kirsten dunst sam raimi',
      160: "the thrill second chapter of the epic how to train your dragon trilog bring back the fantast world of hiccup and toothless five year later. while astrid, snotlout and the rest of the gang are challeng each other to dragon race (the island' new favorit contact sport), the now insepar pair journey through the skies, chart unmap territori and explor new worlds. when one of their adventur lead to the discoveri of a secret ice cave that is home to hundr of new wild dragon and the mysteri dragon rider, the two friend find themselv at the center of a battl to protect the peace. fantasi action adventur anim comedi famili father son relationship wife husband relationship sacrif vike sequel rescu dragon mother son relationship death of husband warrior 3d jay baruchel gerard butler kristen wiig dean debloi",
      161: 'a common thief join a mythic god on a quest through egypt. fantasi egypt underworld fight mytholog nile war thief rescu desert god egyptian mytholog egyptian myth brenton thwait nikolaj coster-waldau gerard butler alex proya',
      162: 'deepli ensconc in a top-secret militari program, three pilot struggl to bring an artifici intellig program under control ... befor it initi the next world war. action artifici intellig u.s. navi aftercreditsst josh luca jessica biel jami foxx rob cohen',
      163: 'in a gritti and altern 1985 the glori day of costum vigil have been brought to a close by a govern crackdown, but after one of the mask veteran is brutal murder an investig into the killer is initiated. the reunit hero set out to prevent their own destruction, but in do so uncov a sinist plot that put all of human in grave danger. action mysteri scienc fiction dc comic secret ident mass murder retir base on comic book conspiraci nuclear war doomsday soviet mask vigil doomsday clock red squar death of superhero american presid 1980 malin åkerman billi crudup carla gugino zack snyder',
      164: "in the combust action franchise' final installment, maverick detect martin rigg and roger murtaugh squar off against asian mobster wah sing ku, who' up to hi neck in slave trade and counterfeit currency. with help from gumsho leo getz and smart-aleck rooki cop lee butters, rigg and murtaugh aim to take down ku and hi gang. action adventur comedi crime thriller lapd hou on fire revolv mel gibson danni glover joe pesci richard donner",
      165: 'bruce banner, a genet research with a tragic past, suffer massiv radiat exposur in hi laboratori that cau him to transform into a rage green monster when he get angry. drama action scienc fiction california san francisco monster gener gun dna mutat psycholog berkeley transform frog presid marvel comic superhero golden gate bridg doctor fear scientist dog desert anger mirror phone militari cell hulk superhuman strength repress memori repress eric bana jennif connelli sam elliott ang lee',
      166: 'frame for crime against the country, the g.i. joe team is termin by presidenti order. thi forc the g.i. joe into not onli fight their mortal enemi cobra; they are forc to contend with threat from within the govern that jeopard their veri existence. adventur action scienc fiction thriller terror assassin secret technolog missil warhead presid rescu conspiraci explo battl surveil cobra dwayn johnson d.j. cotrona adriann palicki jon m. chu',
      167: 'scour the ocean depth for treasure-laden shipwreck is busi as usual for a thrill-seek underwat adventur and hi wisecrack buddy. but when these two cross path with a beauti doctor, they find themselv on the ultim treasur hunt. action adventur comedi drama mysteri tyrant ironclad ship matthew mcconaughey penélop cruz steve zahn breck eisner',
      168: 'led by a strang dream, scientist aki ross struggl to collect the eight spirit in the hope of creat a forc power enough to protect the planet. with the aid of the deep eye squadron and her mentor, dr. sid, aki must save the earth from it darkest hate and unleash the spirit within. adventur action anim fantasi scienc fiction thriller battl assign dystopia alien downfal scientist base on video game donald sutherland ming-na wen alec baldwin hironobu sakaguchi',
      169: "predominantli set dure world war ii, steve roger is a sickli man from brooklyn who' transform into super-soldi captain america to aid in the war effort. roger must stop the red skull – adolf hitler' ruthless head of weaponry, and the leader of an organ that intend to use a mysteri devic of untold power for world domination. action adventur scienc fiction new york usa world war ii nazi marvel comic superhero base on comic book nazi germani period drama brooklyn new york citi captain america aftercreditsst marvel cinemat univ 3d chri evan hugo weav tommi lee jone joe johnston",
      170: "greed, revenge, world domin and high-tech terror – it' all in a day' work for bond, who' on a mission to a protect beauti oil heiress from a notori terrorist. in a race against time that culmin in a dramat submarin showdown, bond work to defu the intern power struggl that ha the world' oil suppli hang in the balance. adventur action thriller british mission oil heiress bilbao spain british secret servic pierc brosnan sophi marceau robert carlyl michael apt",
      171: "after an abrupt and violent encount with a french warship inflict sever damag upon hi ship, a captain of the british royal navi begin a chase over two ocean to captur or destroy the enemy, though he must weigh hi commit to duti and feroci pursuit of glori against the safeti of hi devot crew, includ the ship' thought surgeon, hi best friend. adventur naturalist frigat self surgeri sea battl weevil russel crow paul bettani jame d'arci peter weir",
      172: 'after the birth of renesmee, the cullen gather other vampir clan in order to protect the child from a fal alleg that put the famili in front of the volturi. adventur fantasi drama romanc vampir romanc villai super strength imprint cross breed bloodsuck grudg vampir vs vampir chief of polic dhampir fork washington wolf pack misinform see the futur fang vamp kristen stewart robert pattinson taylor lautner bill condon',
      173: 'mumbl the penguin ha a problem: hi son erik, who is reluct to dance, encount the mighti sven, a penguin who can fly! thing get wor for mumbl when the world is shaken by power forces, cau him to bring togeth the penguin nation and their alli to set thing right. anim comedi famili penguin music aftercreditsst 3d elijah wood robin william pink georg miller',
      174: 'scientist bruce banner scour the planet for an antidot to the unbridl forc of rage within him: the hulk. but when the militari mastermind who dream of exploit hi power forc him back to civilization, he find himself come face to face with a new, deadli foe. scienc fiction action adventur new york rio de janeiro marvel comic superhero base on comic book on the run fugit super soldier toni stark virginia militari hulk marvel cinemat univ angri bruce banner edward norton liv tyler tim roth loui leterri',
      175: "the bfg is no ordinari bone-crunch giant. he is far too nice and jumbly. it' lucki for sophi that he is. had she been carri off in the middl of the night by the bloodbottler, or ani of the other giants—rath than the bfg—she would have soon becom breakfast. when sophi hear that the giant are flush-bunk off to england to swollomp a few nice littl chiddlers, she decid she must stop them onc and for all. and the bfg is go to help her! adventur famili fantasi london england england base on novel queen littl girl orphan cannib giant evil brother rubi barnhil mark rylanc rebecca hall steven spielberg",
      176: 'in the 1820s, a frontiersman, hugh glass, set out on a path of vengeanc against those who left him for dead after a bear mauling. western drama adventur thriller father son relationship rape base on novel mountain winter grizzli bear wilder frontier reveng murder nativ american surviv bear snow violenc anim death bear attack death of son base on true event fur trapper leonardo dicaprio tom hardi will poulter alejandro gonzález iñárritu',
      177: 'the tale of an ordinari garden snail who dream of win the indi 500. anim famili underdog car race dream speed power snail fast friend superpow racer ryan reynold paul giamatti michael peña david soren',
      178: 'when rango, a lost famili pet, accid wind up in the gritty, gun-sl town of dirt, the less-than-courag lizard suddenli find he stand out. welcom as the last hope the town ha been wait for, new sheriff rango is forc to play hi new role to the hilt. anim comedi famili western adventur sheriff nevada pet rango chameleon la vega cactu terrarium construct site armadillo disillus johnni depp isla fisher ned beatti gore verbinski',
      179: 'skipper, kowalski, rico and privat join forc with undercov organ the north wind to stop the villain dr. octaviu brine from destroy the world as we know it. famili anim adventur comedi penguin madagascar 3d tom mcgrath chri miller christoph knight eric darnel',
      180: "bourn is brought out of hide onc again by report simon ross who is tri to unveil oper blackbriar, an upgrad to project treadstone, in a seri of newspap columns. inform from the report stir a new set of memories, and bourn must final uncov hi dark past while dodg the company' best effort to erad him. action drama mysteri thriller pari corrupt madrid assassin base on novel europ prosecut danger fal ident revel govern weapon interpol sequel conspiraci shootout espionag motorcycl violenc foot chase moskow dark past langley virginia flashback chase on the roof secur leak matt damon julia stile david strathairn paul greengrass",
      181: 'when the valley of peac is threatened, lazi po the panda discov hi destini as the "chosen one" and train to becom a kung fu hero, but transform the unsleek slacker into a brave warrior won\'t be easy. it\' up to master shifu and the furiou five -- tigress, crane, mantis, viper and monkey -- to give it a try. adventur anim famili comedi china martial art kung fu mentor snake restaur shop strong woman braveri tiger turtl panda sensei anthropomorph fight ancient china monkey master destini evil aftercreditsst monkey warrior noodl jack black dustin hoffman angelina joli mark osborn',
      182: 'arm with the astonish abil to shrink in scale but increa in strength, master thief scott lang must embrac hi inner-hero and help hi mentor, doctor hank pym, protect the secret behind hi spectacular ant-man suit from a new gener of tower threats. against seemingli insurmount obstacles, pym and lang must plan and pull off a heist that will save the world. scienc fiction action adventur marvel comic superhero base on comic book aftercreditsst duringcreditsst marvel cinemat univ 3d paul rudd michael dougla evangelin lilli peyton reed',
      183: 'katniss everdeen ha return home safe after win the 74th annual hunger game along with fellow tribut peeta mellark. win mean that they must turn around and leav their famili and close friends, embark on a "victor\' tour" of the districts. along the way katniss sen that a rebellion is simmering, but the capitol is still veri much in control as presid snow prepar the 75th annual hunger game (the quarter quell) - a competit that could chang panem forever. adventur action scienc fiction competit base on novel mentor secret factori televi propaganda futur dystopia allianc game presid upri sequel murder surviv conspiraci rebellion blood femal protagonist tournament explo danger imax winner base on young adult novel jennif lawrenc josh hutcherson liam hemsworth franci lawrenc',
      184: 'when earth is taken over by the overly-confid boov, an alien race in search of a new place to call home, all human are promptli relocated, while all boov get busi reorgan the planet. but when one resourc girl, tip, manag to avoid capture, she find herself the accid accompl of a banish boov name oh. the two fugit realiz there’ a lot more at stake than intergalact relat as they embark on the road trip of a lifetime. fantasi comedi anim scienc fiction famili friendship spaceship space alien alien inva alien friendship aw leader take respo jim parson rihanna steve martin tim johnson',
      185: 'ray ferrier is a divorc dockwork and less-than-perfect father. soon after hi ex-wif and her new husband drop of hi teenag son and young daughter for a rare weekend visit, a strang and power lightn storm touch down. adventur thriller scienc fiction post traumat stress disord new jersey airplan dystopia daughter apocalyp alien inva human subjug tom crui dakota fan miranda otto steven spielberg',
      186: 'out-of-control, trash-talk buddi cop marcu burnett and mike lowrey of the miami narcot task forc reunite, and bullet fly, car crash and laugh explod as they pursu a whacked-out drug lord from the street of miami to the barrio of cuba. but the real firework result when marcu discov that playboy mike is secretli romanc marcus’ sexi sister. adventur action comedi thriller crime miami ku klux klan cuba undercov mexican standoff ecstasi guantánamo slaughter shootout gunfight bromanc gangster violenc foot chase interrog car chase drug lord explod hou narcot cop illeg drug dea agent buddi cop crimin underworld action hero haitian gang minefield martin lawrenc will smith jordi mollà michael bay',
      187: 'long befor he even met shrek, the notori fighter, lover and outlaw puss in boot becom a hero when he set off on an adventur with the tough and street smart kitti softpaw and the mastermind humpti dumpti to save hi town. thi is the true stori of the cat, the myth, the legend... the boots. action adventur anim famili fantasi adventur fairy-t figur antonio bandera salma hayek zach galifianaki chri miller',
      188: 'as a cia officer, evelyn salt swore an oath to duty, honor and country. her loyalti will be test when a defector accu her of be a russian spy. salt goe on the run, use all her skill and year of experi as a covert oper to elud capture. salt\' effort to prove her innoc onli serv to cast doubt on her motives, as the hunt to uncov the truth behind her ident continu and the question remains: "who is salt?" action mysteri thriller assassin spi cia kidnap cold war soviet union doubl agent race against time reveng on the run shootout espionag femal protagonist hitwoman terror violenc russian spi intellig offic action heroin angelina joli liev schreiber chiwetel ejiofor phillip noyc',
      189: 'a man who suffer vision of an apocalypt delug take measur to protect hi famili from the come flood. drama adventur bibl god noah 3d russel crow jennif connelli emma watson darren aronofski',
      190: 'intrepid young reporter, tintin and hi loyal dog, snowi are thrust into a world of high adventur when they discov a ship carri an explo secret. as tintin is drawn into a centuries-old mystery, ivan ivanovitch sakharin suspect him of steal a priceless treasure. tintin and snowy, with the help of salty, cantank captain haddock and bumbl detectives, thompson &amp; thomson, travel half the world, one step ahead of their enemi as tintin endeavor to find the unicorn, a sunken ship that may hold a vast fortune, but also an ancient curse. adventur anim mysteri riddl captain treasur liquor treasur hunt sunken treasur plot report 3d action jami bell andi serki daniel craig steven spielberg',
      191: "harry, ron and hermion return to hogwart for anoth magic-fil year. harri come face to face with danger yet again, thi time in the form of escap convict, siriu black – and turn to sympathet professor lupin for help. adventur fantasi famili fli traitor magic cut the cord child hero broom sorcerer' apprent school of witchcraft griffon black magic time travel best friend werewolf dark muggl aftercreditsst daniel radcliff rupert grint emma watson alfonso cuarón",
      192: 'set in northern australia befor world war ii, an english aristocrat who inherit a sprawl ranch reluctantli pact with a stock-man in order to protect her new properti from a takeov plot. as the pair drive 2,000 head of cattl over unforgiv landscape, they experi the bomb of darwin, australia, by japan forc firsthand. drama missionari world war ii ranch australia british racist cattl drive aftercreditsst stamp waltz matilda trampl to death nicol kidman hugh jackman essi davi baz luhrmann',
      193: "one thousand year after cataclysm event forc humanity' escap from earth, nova prime ha becom mankind' new home. legendari gener cypher raig return from an extend tour of duti to hi estrang family, readi to be a father to hi 13-year-old son, kitai. when an asteroid storm damag cypher and kitai' craft, they crash-land on a now unfamiliar and danger earth. as hi father lie die in the cockpit, kitai must trek across the hostil terrain to recov their rescu beacon. hi whole life, kitai ha want noth more than to be a soldier like hi father. today, he get hi chance. scienc fiction action adventur dystopia jaden smith will smith sophi okonedo m. night shyamalan",
      194: 'an orphan dinosaur rai by lemur join an arduou trek to a sancturari after a meteorit shower destroy hi famili home. anim famili cataclysm asteroid leader comet anim prehistor prehistor egg dinosaur nest ground prehistor creatur prehistor adventur lemur prehistor time d. b. sweeney alfr woodard ossi davi ralph zondag',
      195: 'when the magic power of the tablet of ahkmenrah begin to die out, larri daley (ben stiller) span the globe, unit favorit and new charact while embark on an epic quest to save the magic befor it is gone forever. adventur comedi fantasi famili night watchman museum natur histori histori smithsonian ben stiller rami malek rebel wilson shawn levi',
      196: 'bumbl supervillain megamind final defeat hi nemesis, the superhero metro man. but without a hero, he lose all purpo and must find new mean to hi life. anim action comedi famili scienc fiction save the world date prison secret ident fish gun dna mayor anti hero rain museum one-sid love serum talk anim report duringcreditsst stronger villain will ferrel brad pitt tina fey tom mcgrath',
      197: "harri potter ha live under the stair at hi aunt and uncle' hou hi whole life. but on hi 11th birthday, he learn he' a power wizard -- with a place wait for him at the hogwart school of witchcraft and wizardry. as he learn to har hi newfound power with the help of the school' kindli headmaster, harri uncov the truth about hi parents' death -- and about the villain who' to blame. adventur fantasi famili witch christma parti magic cut the cord halloween child hero broom chosen one frog fantasi world base on young adult novel daniel radcliff rupert grint emma watson chri columbu",
      198: 'a recent slain cop join a team of undead polic offic work for the rest in peac depart and tri to find the man who murder him. base on the comic by peter m. lenkov. fantasi action comedi crime gold polic oper partner reveng undead ghost polic depart jeff bridg ryan reynold kevin bacon robert schwentk',
      199: "jack sparrow, a freewheel 17th-centuri pirat who roam the caribbean sea, butt head with a rival pirat bent on pillag the villag of port royal. when the governor' daughter is kidnapped, sparrow decid to help the girl' love save her. but their seafar mission is hardli simple. adventur fantasi action exot island blacksmith east india trade compani gold marriag propo mutini jamaica skeleton daughter governor wooden eye gold coin pirat alcohol swashbuckl caribbean aftercreditsst pirat ship capuchin monkey tortuga johnni depp geoffrey rush orlando bloom gore verbinski",
      200: 'katniss everdeen reluctantli becom the symbol of a mass rebellion against the autocrat capitol. scienc fiction adventur thriller resist post-apocalypt dystopia war sequel femal protagonist bow and arrow game futur war revolt class prejud human subjug base on young adult novel jennif lawrenc josh hutcherson liam hemsworth franci lawrenc',
      201: "when the curat of the louvr is found murder in the fame museum' hallow halls, harvard professor, robert langdon and cryptographer, sophi neve must untangl a deadli web of deceit involv the work of leonardo da vinci. thriller mysteri pari holi grail christian monk base on novel zurich secret societi louvr curat symbologist opu dei heresi mona lisa freemason conspiraci pentagram tomb cathol cryptologist iconographi albino sect tom hank audrey tautou ian mckellen ron howard",
      202: "it' a jungl out there for blu, jewel and their three kid after they'r hurtl from rio de janeiro to the wild of the amazon. as blu tri to fit in, he goe beak-to-beak with the veng nigel, and meet the most fearsom adversari of all: hi father-in-law. anim adventur comedi famili bird sequel jungl audit amazon rainforest parrot jess eisenberg ann hathaway lesli mann carlo saldanha",
      203: "professor charl xavier and hi team of genet gift superhero face a rise tide of anti-mut sentiment led by col. william stryker. storm, wolverin and jean grey must join their usual neme – magneto and mystiqu – to unh stryker' scheme to extermin all mutants. adventur action scienc fiction thriller mutant marvel comic superhero base on comic book superhuman patrick stewart hugh jackman ian mckellen bryan singer",
      204: "former cop brian o'conn partner with ex-con dom toretto on the opposit side of the law. sinc brian and mia toretto broke dom out of custody, they'v blown across mani border to elud authorities. now back into a corner in rio de janeiro, they must pull one last job in order to gain their freedom. action thriller crime brazil fbi freedom escap from prison car crash heist organ crime on the run money fugit polic chase escap convict car imax automobil race duringcreditsst vin diesel paul walker jordana brewster justin lin",
      205: 'there is a new crimin mastermind at larg (professor moriarty) and not onli is he holmes’ intellectu equal, but hi capac for evil and lack of conscienc may give him an advantag over the detective. adventur action crime mysteri detect inspector steampunk crimin mastermind robert downey jr. jude law jare harri guy ritchi',
      206: 'born of a god but rai as a man, perseu is helpless to save hi famili from hades, veng god of the underworld. with noth to lose, perseu volunt to lead a danger mission to defeat hade befor he can seiz power from zeu and unleash hell on earth. battl unholi demon and fearsom beasts, perseu and hi warrior will onli surviv if perseu accept hi power as a god, defi fate and creat hi own destiny. adventur fantasi action hade mytholog greek mytholog zeu medusa mytholog beast sea monster perseu kraken god ancient greec base on greek myth 3d sam worthington liam neeson ralph fienn loui leterri',
      207: "construct worker dougla quaid discov a memori chip in hi brain dure a virtual-r trip. he also find that hi past ha been invent to conceal a plot of planetari domination. soon, he' off to mar to find out who he is and who plant the chip. action adventur scienc fiction oxygen fal accu resist mar doubl life telepathi mutant hologram space coloni fal ident secret agent dystopia cyberpunk fal memori implant memori arnold schwarzenegg sharon stone rachel ticotin paul verhoeven",
      208: 'in ad 922, arab courtier, ahmad ibn fadlan accompani a parti of vike to the barbar north to combat a terror that slaughter vike and devour their flesh. adventur fantasi action witch cave arabian scandinavia bagdad vike iraq war mission antonio bandera vladimir kulich denni storhøi john mctiernan',
      209: 'new cia operative, aaron cross experi life-or-death stake that have been trigger by the previou action of jason bourne. action thriller assassin wolf maryland suicid by gunshot rooftop explod hou laptop track devic fake id seoul south korea pharmaceut lab govern conspiraci roof chase manila philippin hunt fal passport alberta canada lieuten gener jeremi renner rachel weisz edward norton toni gilroy',
      210: "along with crime-fight partner robin and new recruit batgirl, batman battl the dual threat of frosti geniu mr. freez and homicid horticulturalist poison ivy. freez plan to put gotham citi on ice, while ivi tri to drive a wedg between the dynam duo. action crime fantasi doubl life dc comic dual ident crime fighter fiction place gotham citi superhero credit card super power georg clooney chri o'donnel arnold schwarzenegg joel schumach",
      211: 'insid a snowflak exist the magic land of whoville. in whoville, live the whos, an almost mutat sort of munchkin-lik people. all the who love christmas, yet just outsid of their belov whovil live the grinch. the grinch is a nasti creatur that hate christmas, and plot to steal it away from the whos, whom he equal abhors. yet a small child, cindi lou who, decid to tri befriend the grinch. famili comedi fantasi holiday christma parti new love santa clau villag kid and famili jim carrey taylor momsen jeffrey tambor ron howard',
      212: 'after year of increa in the greenhou effect, havoc is wreak global in the form of catastroph hurricanes, tornadoes, tidal waves, flood and the begin of a new ice age. paleoclimatologist, jack hall tri to warn the world while also shepherd to safeti hi son, trap in new york after the citi is overwhelm by the start of the new big freeze. action adventur scienc fiction thriller save the world librari cataclysm climat chang greenhou effect tornado twister hurrican hail temperatur drop ice age polar zone meteorolog gulfstream barrier ice ice melt third world exodu evacu climat govern snow lo angel scientist doomsday antarct disast movi denni quaid jake gyllenha emmi rossum roland emmerich',
      213: 'with comput geniu luther stickel at hi side and a beauti thief on hi mind, agent ethan hunt race across australia and spain to stop a former imf agent from unleash a genet engin biolog weapon call chimera. thi mission, should hunt choo to accept it, plung him into the center of an intern crisi of terrifi magnitude. adventur action thriller terror spain cia helicopt secret ident skyscrap undercov island ex-lov secret mission die and death secret agent comput duel lethal viru violenc rescu team agent car research laboratori tom crui dougray scott thandi newton john woo',
      214: 'in octob 1991, a confluenc of weather condit combin to form a killer storm in the north atlantic. caught in the storm wa the sword-fish boat andrea gail. magnif foreshadow and anticip fill thi true-lif drama while minut detail of the fish boats, their gear and the weather are juxtapo with the sea adventure. drama u.s. air forc groceri jamaican meteorologist rescu boat marina citi hall the flemish cap male camaraderi storm at sea georg clooney mark wahlberg dian lane wolfgang petersen',
      215: "the fantast four return to the big screen as a new and all power enemi threaten the earth. the seemingli unstopp 'silver surfer', but all is not what it seem and there are old and new enemi that pose a greater threat than the intrepid superhero realize. adventur fantasi action thriller fire helicopt surfboard mask satellit airplan transform forest resurrect marvel comic sequel superhero base on comic book outer space wed explo scientist interrog doubl cross fantast four militari earth in peril superhuman strength duringcreditsst invi silver surfer forcefield elast absorb power ioan gruffudd jessica alba chri evan tim stori",
      216: "the stori of an indian boy name pi, a zookeeper' son who find himself in the compani of a hyena, zebra, orangutan, and a bengal tiger after a shipwreck set them adrift in the pacif ocean. adventur drama action ocean shipwreck hindu tiger faith zookeep teenag boy cargo ship lifeboat injur anim suraj sharma irrfan khan ayush tandon ang lee",
      217: "in order to save hi die father, young stunt cyclist, johnni blaze sell hi soul to mephistophel and sadli part from the pure-hearted, roxann simpson, the love of hi life. year later, johnny' path cross again with roxanne, now a go-get reporter, and also with mephistopheles, who offer to relea johnny' soul if johnni becom the fabled, fieri 'ghost rider'. thriller action fantasi horror mephisto religion and supernatur die and death devil' son ghost world stunt flame base on comic book nicola cage eva mend we bentley mark steven johnson",
      218: 'the most danger former oper of the cia is drawn out of hide to uncov hidden truth about hi past. action thriller assassin amnesia flashback matt damon alicia vikand tommi lee jone paul greengrass',
      219: 'the angel are charg with find a pair of miss ring that are encod with the person inform of member of the wit protect program. as inform are killed, the ladi target a rogu agent who might be responsible. action adventur comedi robberi secret ident secret agent cameron diaz drew barrymor luci liu mcg',
      220: 'a team of explor discov a clue to the origin of mankind on earth, lead them on a journey to the darkest corner of the universe. there, they must fight a terrifi battl to save the futur of the human race. scienc fiction adventur mysteri android dystopia alien spin off creation emerg surgeri aftercreditsst stasi archeolog dig god complex cave draw genet mutat origin of life noomi rapac michael fassbend guy pearc ridley scott',
      221: "stuart, an ador white mouse, still live happili with hi adopt family, the littles, on the east side of manhattan' central park. more crazi mou adventur are in store as stuart, hi human brother, george, and their mischiev cat, snowbell, set out to rescu a friend. famili adventur anim comedi mou falcon bird friendship famili michael j. fox geena davi hugh lauri rob minkoff",
      222: 'in the year 2159, two class of peopl exist: the veri wealthi who live on a pristin man-mad space station call elysium, and the rest, who live on an overpopulated, ruin earth. secretari rhode (jodi foster), a hard line govern ofﬁcial, will stop at noth to enforc anti-immigr law and preserv the luxuri lifestyl of the citizen of elysium. that doesn’t stop the peopl of earth from tri to get in, by ani mean they can. when unlucki max (matt damon) is back into a corner, he agr to take on a daunt mission that, if successful, will not onli save hi life, but could bring equal to these polar worlds. scienc fiction action drama thriller dystopia space station class conflict matt damon jodi foster sharlto copley neill blomkamp',
      223: "after year of outrun ruthless bounti hunters, escap convict riddick suddenli find himself caught between oppo forc in a fight for the futur of the human race. now, wage incr battl on fantast and deadli worlds, thi lone, reluct hero will emerg as humanity' champion - and the last hope for a univ on the edg of annihilation. action scienc fiction prison dystopia matter of life and death outer space intergalact travel vin diesel thandi newton karl urban david twohi",
      224: 'in robocop, the year is 2028 and multin conglom omnicorp is at the center of robot technology. overseas, their drone have been use by the militari for years, but have been forbidden for law enforc in america. now omnicorp want to bring their controversi technolog to the home front, and they see a golden opportun to do it. when alex murphi – a love husband, father and good cop do hi best to stem the tide of crime and corrupt in detroit – is critic injured, omnicorp see their chanc to build a part-man, part-robot polic officer. omnicorp envi a robocop in everi citi and even more billion for their shareholders, but they never count on one thing: there is still a man insid the machine. action scienc fiction cyborg futur dystopia polic remak violenc detroit joel kinnaman gari oldman michael keaton josé padilha',
      225: 'speed racer is the tale of a young and brilliant race driver. when corrupt in the race leagu cost hi brother hi life, he must team up with the polic and the mysteri racer x to bring an end to the corrupt and crimin activities. inspir by the cartoon series. action famili scienc fiction car race loss of brother chimp famili duringcreditsst woman director emil hirsch christina ricci matthew fox lilli wachowski',
      226: 'after be cut from the usa softbal team and feel a bit past her prime, lisa find herself evalu her life and in the middl of a love triangle, as a corpor guy in crisi compet with her current, baseball-play beau. comedi drama romanc love triangl baseb athlet aftercreditsst ree witherspoon paul rudd owen wilson jame l. brook',
      227: 'a fugit coupl goe on a glamor and sometim deadli adventur where noth and no one – even themselv – are what they seem. amid shift allianc and unexpect betrayals, they race across the globe, with their surviv ultim hing on the battl of truth vs. trust. action comedi spi airport ga station garag pilot chase secret agent rope explod build car chase polic car boy geniu duringcreditsst tom crui cameron diaz peter sarsgaard jame mangold',
      228: 'jack harper is one of the last few drone repairmen station on earth. part of a massiv oper to extract vital resourc after decad of war with a terrifi threat known as the scavs, jack’ mission is nearli complete. hi exist is brought crash down when he rescu a beauti stranger from a down spacecraft. her arriv trigger a chain of event that forc him to question everyth he know and put the fate of human in hi hands. action scienc fiction adventur mysteri spacecraft dystopia space drone imax human vs alien tom crui morgan freeman olga kurylenko joseph kosinski',
      229: "year after the onset of the clone wars, the nobl jedi knight lead a massiv clone armi into a galaxy-wid battl against the separatists. when the sinist sith unveil a thousand-year-old plot to rule the galaxy, the republ crumbl and from it ash rise the evil galact empire. jedi hero anakin skywalk is seduc by the dark side of the forc to becom the emperor' new apprent – darth vader. the jedi are decimated, as obi-wan kenobi and jedi master yoda are forc into hiding. the onli hope for the galaxi are anakin' own offspr – the twin children born in secreci who will grow up to becom heroes. scienc fiction adventur action showdown death star vision cult figur hatr dream sequenc expect mother space opera chancel childbirth galact war ewan mcgregor natali portman hayden christensen georg luca",
      230: 'ten year after the inva of naboo, the galaxi is on the brink of civil war. under the leadership of a renegad jedi name count dooku, thousand of solar system threaten to break away from the galact republic. when an assassin attempt is made on senat padmé amidala, the former queen of naboo, twenty-year-old jedi apprent anakin skywalk is assign to protect her. in the cour of hi mission, anakin discov hi love for padmé as well as hi own darker side. soon, anakin, padmé, and obi-wan kenobi are drawn into the heart of the separatist movement and the begin of the clone wars. adventur action scienc fiction senat investig armi death star jedi cult figur wed violenc kendo laser gun space opera spaceport teenag rebellion good becom evil alien race mechan hand yoda ewan mcgregor natali portman hayden christensen georg luca',
      231: "jame sullivan and mike wazowski are monsters, they earn their live scare children and are the best in the business... even though they'r more afraid of the children than they are of them. when a child accid enter their world, jame and mike suddenli find that kid are not to be afraid of and they uncov a conspiraci that could threaten all children across the world. anim comedi famili monster infant energi suppli compani rivalri hijink best friend scream conveyor belt energi compani friend john goodman billi crystal mari gibb pete docter",
      232: 'wolverin face hi ultim nemesi - and test of hi physical, emotional, and mortal limit - in a life-chang voyag to modern-day japan. action scienc fiction adventur fantasi japan samurai mutant world war i marvel comic superhero base on comic book superhuman duringcreditsst hugh jackman hiroyuki sanada famk janssen jame mangold',
      233: 'anakin skywalker, a young slave strong with the force, is discov on tatooine. meanwhile, the evil sith have returned, enact their plot for reveng against the jedi. adventur action scienc fiction propheci senat queen taskmast galaxi apprent tax space opera liam neeson ewan mcgregor natali portman georg luca',
      234: "the crood is a prehistor comedi adventur that follow the world' first famili as they embark on a journey of a lifetim when the cave that ha alway shield them from danger is destroyed. travel across a spectacular landscape, the crood discov an incr new world fill with fantast creatur -- and their outlook is chang forever. adventur anim comedi famili fantasi stone age daughter father prehistor ancient world father daughter relationship famili cavemen aftercreditsst duringcreditsst nicola cage emma stone ryan reynold chri sander",
      235: 'astérix and obélix have to win the olymp game in order to help their friend alafolix marri princess irina (portray by supermodel vanessa hessler). brutu (benoît poelvoorde) use everi trick in the book to have hi own team win the game, and get rid of hi father juliu caesar (alain delon) in the process. fantasi adventur comedi famili competit greec colosseum olymp game emperor magic hor roman wild boar govern galier clovi cornillac gérard depardieu franck dubosc thoma langmann',
      236: 'joe ender is a gung-ho marin assign to protect a "windtalker" - one of sever navajo indian who were use to relay messag dure world war ii becau their spoken languag wa indeciph to japan code breakers. drama action histori war japan world war ii radio transmiss marin corp u.s. armi code navajo pacif war nicola cage adam beach peter stormar john woo',
      237: 'as two evil sister prepar to conquer the land, two renegades— the huntsman, who aid snow white in defeat ravenna in snowwhit and the huntsman, and hi forbidden lover, sara—set out to stop them. action adventur drama witch magic fairi tale snow white huntsman chri hemsworth charliz theron emili blunt cedric nicolas-troyan',
      238: "the citi need heroes. dark ha settl over new york citi as shredder and hi evil foot clan have an iron grip on everyth from the polic to the politicians. the futur is grim until four unlik outcast brother rise from the sewer and discov their destini as teenag mutant ninja turtles. the turtl must work with fearless report april and her wise-crack cameraman vern fenwick to save the citi and unravel shredder' diabol plan. scienc fiction action adventur fantasi comedi martial art terrorist hero mutat van turtl vigil superhero base on comic book ninja new york citi sewer reboot scienc experi 3d megan fox will arnett william fichtner jonathan liebesman",
      239: 'dr. ryan stone, a brilliant medic engin on her first shuttl mission, with veteran astronaut matt kowalski in command of hi last flight befor retiring. but on a seemingli routin spacewalk, disast strikes. the shuttl is destroyed, leav stone and kowalski complet alone-teth to noth but each other and spiral out into the black of space. the deafen silenc tell them they have lost ani link to earth and ani chanc for rescue. as fear turn to panic, everi gulp of air eat away at what littl oxygen is left. but the onli way home may be to go further out into the terrifi expan of space. scienc fiction thriller drama space mission loss space astronaut trap in space sandra bullock georg clooney ed harri alfonso cuarón',
      240: "volcanologist harri dalton come to the sleepi town of dante' peak to investig the recent rumbl of the dormant volcano the burg is name for. befor long, hi worst fear are realiz when a massiv erupt hits, and immediately, harry, the mayor and the townspeopl find themselv fight for their live amid a catastroph nightmare. action adventur thriller helicopt small town mayor evacu motel lava volcano cabin lover natur disast partnership volcanologist rescu explo scientist seismograph volcan erupt rowboat catastroph acid counti fair abandon mine volcan ash pierc brosnan linda hamilton jami rené smith roger donaldson",
      241: 'after supervillain shredder escap custody, he join forc with mad scientist baxter stockman and two dimwit henchmen, bebop and rocksteady, to unleash a diabol plan to take over the world. as the turtl prepar to take on shredder and hi new crew, they find themselv face an even greater evil with similar intentions: the notori krang. fantasi action adventur comedi brother brother relationship turtl sequel base on comic book ninja rat megan fox stephen amel will arnett dave green',
      242: 'four young outsid teleport to a danger universe, which alter their physic form in shock ways. their live irrevoc upended, the team must learn to har their daunt new abil and work togeth to save earth from a former friend turn enemy. action adventur scienc fiction teleport transform telekinesi portal marvel comic superhero base on comic book superhero team fantast four bodi horror invi woman mile teller kate mara michael b. jordan josh trank',
      243: "chao reign at the natur histori museum when night watchman larri daley accid stir up an ancient curse, awaken attila the hun, an armi of gladiators, a tyrannosauru rex and other exhibits. larri tri desper to keep the museum under control, but he' fight a lose battl until presid teddi roosevelt come to the rescue. action adventur comedi famili fantasi museum skeleton night shift chao genghi khan maya civil natur histori theodor roosevelt dinosaur base on children' book magic object secur guard duringcreditsst inanim object come to life ben stiller jake cherri carla gugino shawn levi",
      244: 'in the aftermath of a massiv earthquak in california, a rescue-chopp pilot make a danger journey across the state in order to rescu hi estrang daughter. action drama thriller california earthquak catastroph disast film 3d san andrea san andrea california rescu oper dwayn johnson alexandra daddario carla gugino brad peyton',
      245: "a derang media mogul is stage intern incid to pit the world' superpow against each other. now 007 must take on thi evil mastermind in an adrenaline-charg battl to end hi reign of terror and prevent global pandemonium. adventur action thriller london england england spi china news broadcast intellig televi missil manipul of the media secret intellig servic special car tv station media tycoon navi motorcycl secret servic hamburg germani pierc brosnan jonathan pryce michel yeoh roger spottiswood",
      246: 'after prove himself on the field of battl in the french and indian war, benjamin martin want noth more to do with such things, prefer the simpl life of a farmer. but when hi son gabriel enlist in the armi to defend their new nation, america, against the british, benjamin reluctantli return to hi old life to protect hi son. drama histori war action rebel southern usa loss of son martial art gener loss of famili passion insurg french daughter south carolina british base on true stori gore mission mel gibson heath ledger joeli richardson roland emmerich',
      247: 'danni ocean reunit with hi old flame and the rest of hi merri band of thiev in carri out three huge heist in rome, pari and amsterdam – but a europol agent is hot on their heels. thriller crime sequel fabergé egg dutch eastindian compani second part golden egg goon georg clooney brad pitt catherin zeta-jon steven soderbergh',
      248: "after five (or six) year of vanilla-w bliss, ordinari suburbanit john and jane smith are stuck in a huge rut. unbeknownst to each other, they are both coolli lethal, highly-paid assassin work for rival organisations. when they discov they'r each other' next target, their secret live collid in a spicy, explo mix of wick comedy, pent-up passion, nonstop action and high-tech weaponry. action comedi drama thriller bomb assassin secret ident secret assault rifl gun marri coupl hitman decoy marriag crisi marriag job dysfunct marriag gunfight bullet wound angelina joli brad pitt vinc vaughn doug liman",
      249: 'beatric prior must confront her inner demon and continu her fight against a power allianc which threaten to tear her societi apart. adventur scienc fiction thriller base on novel revolut dystopia sequel dystop futur young adult 3d diverg shailen woodley theo jame kate winslet robert schwentk',
      250: 'a biopic depict the life of filmmak and aviat pioneer howard hugh from 1927 to 1947, dure which time he becam a success film produc and an aviat magnate, while simultan grow more unstabl due to sever obsessive-compul disorder. drama ladykil pilot biographi woman aviat phobia u.s. congress fli boat test flight leonardo dicaprio cate blanchett kate beckins martin scors',
      251: 'travel writer lemuel gulliv take an assign in bermuda, but end up on the island of liliput, where he tower over it tini citizens. comedi journalist forbidden love princess royal court 3d jack black amanda peet emili blunt rob letterman',
      252: "britt reid (seth rogen), the heir to the largest newspap fortun in lo angeles, is a spoil playboy who ha been, thu far, happi to lead an aimless life. after hi father (tom wilkinson) dies, britt meet kato (jay chou), a resourc compani employee. realiz that they have the talent and resourc to make someth of their lives, britt and kato join forc as costum crime-fight to bring down the city' most-pow criminal, chudnofski (christoph waltz). action crime comedi bomb martial art assassin vandal nightclub train knife parti playboy superhero reveng trap violenc kato car chase meth lab seth rogen jay chou christoph waltz michel gondri",
      253: 'base on frank miller\' latest graphic novel xerx and told in the breathtak visual style of the blockbust "300," thi new chapter of the epic saga take the action to a fresh battlefield--on the sea--a greek gener themistokl attempt to unit all of greec by lead the charg that will chang the cour of the war. "300: rise of an empire" pit themistokl against the massiv invad persian forc led by mortal-turned-god xerx and artemesia, the veng command of the persian navy. action war base on graphic novel ancient greec duringcreditsst sea battl hand to hand combat minion naval warfar 3d sullivan stapleton eva green lena headey noam murro',
      254: 'when the evil wizard gargamel chase the tini blue smurf out of their village, they tumbl from their magic world and into our -- in fact, smack dab in the middl of central park. just three appl high and stuck in the big apple, the smurf must find a way to get back to their villag befor gargamel track them down. anim famili adventur comedi fantasi moon magic base on comic book anim good vs evil smurf blue vortex mischief cat and mou duringcreditsst hank azaria neil patrick harri jayma may raja gosnel',
      255: 'when a greedi outlaw scheme to take possess of the "patch of heaven" dairi farm, three determin cows, a karate-kick stallion and a color corral of critter join forc to save their home. the stake are sky-high as thi unlik anim allianc risk their hide and match wit with a mysteri band of bad guys. anim famili farm cow anim roseann barr judi dench jennif tilli will finn',
      256: 'beatric prior and tobia eaton ventur into the world outsid of the fenc and are taken into protect custodi by a mysteri agenc known as the bureau of genet welfare. adventur scienc fiction base on novel revolut dystopia sequel dystop futur young adult base on young adult novel shailen woodley theo jame zoë kravitz robert schwentk',
      257: "in the near-future, charli kenton is a washed-up fighter who retir from the ring when robot took over the sport. after charlie' robot is trashed, he reluctantli team up with hi estrang son max to rebuild and train an unlik contender. action scienc fiction drama father son relationship fight sport robot prizefight father son reunion robot fight hugh jackman dakota goyo evangelin lilli shawn levi",
      258: "the evil wizard gargamel creat a coupl of mischiev smurf-lik creatur call the naughti that he hope will let him har the all-powerful, magic smurf-essence. but when he discov that onli a real smurf can give him what he wants, and onli a secret spell that smurfett know can turn the naughti into real smurfs, gargamel kidnap smurfett and bring her to paris, where he ha been win the ador of million as the world¹ greatest sorcerer. it' up to papa, clumsy, grouchy, and vaniti to return to our world, reunit with their human friend patrick and grace winslow, and rescu her! will smurfette, who ha alway felt differ from the other smurfs, find a new connect with the naughti vexi and hacku or will the smurf convinc her that their love for her is true blue? fantasi famili comedi anim base on cartoon anim smurf hank azaria neil patrick harri brendan gleeson raja gosnel",
      259: 'sandra bullock and jason patric star as a young coupl whose dream crui turn to terror when a lunat comput geniu (willem dafoe) set a new cour for destruction. action adventur thriller boat crui comput disast diamond colli cour sandra bullock jason patric willem dafo jan de bont',
      260: "base on the classic novel by orson scott card, ender' game is the stori of the earth' most gift children train to defend their homeplanet in the space war of the future. scienc fiction action adventur base on novel intol chosen one child prodigi futurist space scienc fiction alien inva militari school moral tale base on young adult novel asa butterfield harrison ford hail steinfeld gavin hood",
      261: "john mcclane is back and badder than ever, and thi time he' work for homeland security. he call on the servic of a young hacker in hi bid to stop a ring of internet terrorist intent on take control of america' comput infrastructure. action thriller usa washington d.c. helicopt hostag fbi kidnap hacker satellit transport of prison traffic jam fistfight ex-cop sequel suspen shootout explo violenc cell phone car chase polic car walki talki base on articl cyber terror action hero power plant bruce willi justin long timothi olyph len wiseman",
      262: 'young hobbit frodo baggins, after inherit a mysteri ring from hi uncl bilbo, must leav hi home in order to keep it from fall into the hand of it evil creator. along the way, a fellowship is form to protect the ringbear and make sure that the ring arriv at it final destination: mt. doom, the onli place where it can be destroyed. adventur fantasi action elv dwarv orc middle-earth (tolkien) hobbit base on novel mountain firework castl volcano password death of a friend uncl mirror wizard sword and sorceri elijah wood ian mckellen cate blanchett peter jackson',
      263: 'a bet pit a british inventor, a chine thief and a french artist on a worldwid adventur that they can circl the globe in 80 days. action adventur comedi pari london england new york jule vern san francisco istanbul hot air balloon journey round the world jacki chan steve coogan cécile de franc frank coraci',
      264: "in 1964, a brash new pro boxer, fresh from hi olymp gold medal victory, explod on to the scene; cassiu clay. bold and outspoken, he cut an entir new imag for african american in sport with hi proud public self confid and hi unapologet belief that he is the greatest boxer of all time. yet at the top of hi game, both ali' person and profess live face the ultim test. drama usa transport boxer biographi muhammad will smith jami foxx jon voight michael mann",
      265: "conrad and salli walden are home alon with their pet fish. it is rain outside, and there is noth to do. until the cat in the hat walk in the front door. he introduc them to their imagination, and at first it' all fun and games, until thing get out of hand, and the cat must go, go, go, befor their parent get back. comedi fantasi famili cat brother sister relationship boredom chao step father base on children' book mike myer dakota fan spencer breslin bo welch",
      266: 'in 2035, where robot are common-plac and abid by the three law of robotics, a techno-phob cop investig an appar suicide. suspect that a robot may be respon for the death, hi investig lead him to believ that human may be in danger. action scienc fiction suicid artifici intellig man vs machin chicago base on novel hero futur law dystopia polic murder robot 3d humanoid robot will smith bridget moynahan alan tudyk alex proya',
      267: 'after hi wife dies, a blacksmith name balian is thrust into royalty, polit intrigu and bloodi holi war dure the crusades. drama action adventur histori war crusad epic knight swordsman order of the templar religi knight templar saladin king richard orlando bloom eva green jeremi iron ridley scott',
      268: 'the adventur of a heroic and debonair stalwart mou name stuart littl with human qualities, who face some comic misadventur while search for hi lost bird friend and live with a human famili as their child. anim fantasi famili comedi brother brother relationship base on novel cat mou adopt orphanag step brother kid and famili new york citi twin tower gangster michael j. fox geena davi hugh lauri rob minkoff',
      269: 'a waitress, desper to fulfil her dream as a restaur owner, is set on a journey to turn a frog princ back into a human being, but she ha to do face the same problem after she kiss him. romanc famili anim music base on novel voodoo kiss princess anim cajun firefli base on fairi tale duringcreditsst big dream frog princ charlatan anika noni rose bruno campo keith david ron clement',
      270: 'dure a man mission to mars, astronaut mark watney is presum dead after a fierc storm and left behind by hi crew. but watney ha surviv and find himself strand and alon on the hostil planet. with onli meager supplies, he must draw upon hi ingenuity, wit and spirit to subsist and find a way to signal to earth that he is alive. drama adventur scienc fiction base on novel mar nasa isol botanist strand spaceship space engin surviv astronaut scienc deep space explor duringcreditsst battl for surviv matt damon jessica chastain kristen wiig ridley scott',
      271: 'in 2019, lincoln six-echo is a resid of a seemingli "utopian" but contain facility. like all of the inhabit of thi carefully-control environment, lincoln hope to be chosen to go to the island — reportedli the last uncontamin locat on the planet. but lincoln soon discov that everyth about hi exist is a lie. action thriller scienc fiction adventur clone transplant love of one\' life dystopia genet freedom escap clone plagu ewan mcgregor scarlett johansson djimon hounsou michael bay',
      272: 'porter stoddard is a well-known new york architect who is at a crossroads... a nexu where twist and turn lead to myriad misstep some with hi wife ellie, other with longtim friend mona and her husband griffin. decid which direct to take often lead to unexpect encount with hilari consequences. comedi romanc architect cellist friend anniversari warren beatti dian keaton goldi hawn peter chelsom',
      273: 'upon learn that he ha to come out of retir to steal 50 car in one night to save hi brother kip\' life, former car thief randal "memphis" rain enlist help from a few "boost happy" pal to accomplish a seemingli imposs feat. from countless car chase to relentless cops, the high-octan excit build as randal swerv around more than a few roadblock to keep kip alive. action crime thriller brother brother relationship detect car race car thief blackmail brother remak heist betray organ crime shootout polic chase explo violenc lock pick car chase stakeout illeg drug car movi stolen car ford mustang blacklight nicola cage angelina joli giovanni ribisi domin sena',
      274: "in the year 180, the death of emperor marcu aureliu throw the roman empir into chaos. maximu is one of the roman army' most capabl and trust gener and a key advisor to the emperor. as marcus' deviou son commodu ascend to the throne, maximu is set to be executed. he escapes, but is captur by slave traders. renam spaniard and forc to becom a gladiator, maximu must battl to the death with other men for the amu of pay audiences. hi battl skill serv him well, and he becom one of the most famou and admir men to fight in the colosseum. determin to aveng himself against the man who took away hi freedom and laid wast to hi family, maximu believ that he can use hi fame and skill in the ring to aveng the loss of hi famili and former glory. as the gladiat begin to challeng hi rule, commodu decid to put hi own fight mettl to the test by squar off with maximu in a battl to the death. action drama adventur rome gladiat arena senat roman empir emperor slaveri battlefield blood ancient world father daughter relationship combat mother son relationship dream sequenc chariot philosoph barbarian hord 2nd centuri successor russel crow joaquin phoenix conni nielsen ridley scott",
      275: "john anderton is a top 'precrime' cop in the late-21st century, when technolog can predict crime befor they'r committed. but anderton becom the quarri when anoth investig target him for a murder charge. action thriller scienc fiction mysteri self-fulfil propheci washington d.c. evid futur hologram dystopia murder neo-noir futur noir tom crui colin farrel samantha morton steven spielberg",
      276: "ignor threat to hi life, harri return to hogwart to investig – aid by ron and hermion – a mysteri seri of attacks. adventur fantasi famili fli car witch magic cut the cord child hero broom sorcerer' apprent school of witchcraft giant snake black magic aftercreditsst daniel radcliff rupert grint emma watson chri columbu",
      277: "le chiffre, a banker to the world' terrorists, is schedul to particip in a high-stak poker game in montenegro, where he intend to use hi win to establish hi financ grip on the terrorist market. m send bond – on hi maiden mission as a 00 agent – to attend thi game and prevent le chiffr from winning. with the help of vesper lynd and felix leiter, bond enter the most import poker game in hi alreadi danger career. adventur action thriller itali poker casino terrorist banker money free run tortur british secret servic montenegro daniel craig eva green mad mikkelsen martin campbel",
      278: 'after a spectacular crash-land on an unchart planet, brash astronaut leo davidson find himself trap in a savag world where talk ape domin the human race. desper to find a way home, leo must evad the invinc gorilla armi led by ruthless gener thade. thriller scienc fiction action adventur gorilla space marin space suit revolut chimp slaveri space travel time travel dystopia alien planet ape human subjug mark wahlberg tim roth helena bonham carter tim burton',
      279: 'nearli 10 year have pass sinc sarah connor wa target for termin by a cyborg from the future. now her son, john, the futur leader of the resistance, is the target for a newer, more deadli terminator. onc again, the resist ha manag to send a protector back to attempt to save john and hi mother sarah. action thriller scienc fiction cyborg shotgun post-apocalypt dystopia moral ambigu mental institut violenc fiction war morph nuclear weapon shape shifter savior catch phrase arnold schwarzenegg linda hamilton robert patrick jame cameron',
      280: "depression-era bank robber john dillinger' charm and audac endear him to much of america' downtrodden public, but he' also a thorn in the side of j. edgar hoover and the fledgl fbi. desper to captur the elu outlaw, hoover make dill hi first public enemi number one and assign hi top agent, melvin purvis, the task of bring him in dead or alive. histori crime drama cinema hide place machinegun prison guard escap from prison dill christian bale johnni depp giovanni ribisi michael mann",
      281: 'follow the death of hi employ and mentor, bumpi johnson, frank luca establish himself as the number one import of heroin in the harlem district of manhattan. he doe so by buy heroin directli from the sourc in south east asia and he come up with a uniqu way of import the drug into the unit states. base on a true story. drama crime underdog black peopl drug traffic drug smuggl societi ambit rise and fall cop drug deal polic corrupt gangster crime polic detect famili law enforc aftercreditsst dishonesti crimin hero denzel washington russel crow chiwetel ejiofor ridley scott',
      282: 'harri tasker is a secret agent for the unit state government. for years, he ha kept hi job from hi wife, but is forc to reveal hi ident and tri to stop nuclear terrorist when he and hi wife are kidnap by them. action thriller spi terrorist florida gun kidnap horseback ride florida key secret agent terrorist plot top secret woman with glass hit with a telephon truth serum mushroom cloud jackhamm key west arnold schwarzenegg jami lee curti tom arnold jame cameron',
      283: "arm men hijack a new york citi subway train, hold the passeng hostag in return for a ransom, and turn an ordinari day' work for dispatch walter garber into a face-off with the mastermind behind the crime. thriller drama crime hostag new york citi new york subway subway train stock market motorcycl crash subway tunnel aftercreditsst denzel washington john travolta lui guzmán toni scott",
      284: "it ha taken 10 years, two littl focker with wife pam and countless hurdl for greg to final get in with hi tightli wound father-in-law, jack. after the cash-strap dad take a job moonlight for a drug company, jack' suspicion about hi favorit male nur come roar back. when greg and pam' entir clan descend for the twins' birthday party, greg must prove to the skeptic jack that he' fulli capabl as the man of the house. comedi romanc nur cat father-in-law vomit kid and famili viagra duringcreditsst robert de niro ben stiller owen wilson paul weitz",
      285: 'nypd detect christoph danson (johnson) and p.k. highsmith (jackson) are the baddest and most belov cop in new york city. they don\'t get tattoos, other men get tattoo of them. two desk over and one back, sit detect allen gambl (ferrell) and terri hoitz (wahlberg). you\'v seen them in the background of photo of danson and highsmith, out of focu and eye closed. they\'r not heroes, they\'r "the other guys." but everi cop ha hi or her day and soon gambl and hoitz stumbl into a seemingli innocu case no other detect want to touch that could turn into nyc\' biggest crime. it\' the opportun of their lives, but do these guy have the right stuff? action comedi crime narrat ceo fire truck shot in the shoulder zip line buddi comedi carjack aftercreditsst duringcreditsst will ferrel mark wahlberg eva mend adam mckay',
      286: "u.s. marshal john kruger era the ident of peopl enrol in the wit protect program. hi current assign is to protect lee cullen, who' uncov evid that the weapon manufactur she work for ha been sell to terrorist groups. when kruger discov that there' a corrupt agent within the program, he must guard hi own life while tri to protect lee's. action drama mysteri thriller suicid ambush showdown hostag traitor new ident hitman wit wit protect arm dealer decept betray treason conspiraci u.s. marshal gunfight train explo violenc sabotag corpor crime rogu agent assassin attempt x-ray vision railgun arnold schwarzenegg jame caan vanessa william chuck russel",
      287: 'with the help of a german bounti hunter, a freed slave set out to rescu hi wife from a brutal mississippi plantat owner. drama western bounti hunter hero plantat societi friendship friend reveng rivalri rescu shootout racism danger dentist django dual role aftercreditsst odd coupl black slave deadli chase and race 19th centuri jami foxx christoph waltz leonardo dicaprio quentin tarantino',
      288: 'when quasi defi the evil frollo and ventur out to the festiv of fools, the cruel crowd jeer him. rescu by fellow outcast the gypsi esmeralda, quasi soon find himself battl to save the peopl and the citi he loves. drama anim famili pari base on novel judg obsess danc sword mockeri ugli cathedr music fool bell religion orphan armi captain festiv angri mob witch hunt 15th centuri tom hulc demi moor toni jay gari trousdal',
      289: "kuzco is a self-cent emperor who summon pacha from a villag and to tell him that hi home will be destroy to make room for kuzco' new summer home. kuzco' advisor, yzma, tri to poison kuzco and accid turn him into a llama, who accid end up in pacha' village. pacha offer to help kuzco if he doesn't destroy hi house, and so they form an unlik partnership. adventur anim comedi famili fantasi central and south america birthday emperor palac kingdom berat llama david spade john goodman eartha kitt mark dindal",
      290: 'mr. church reunit the expend for what should be an easi paycheck, but when one of their men is murder on the job, their quest for reveng put them deep in enemi territori and up against an unexpect threat. action adventur thriller airplan number in titl airplan crash violenc beard ensembl cast loss of friend wisecrack humor airport loung asian woman sylvest stallon jason statham dolph lundgren simon west',
      291: "modern treasur hunters, led by archaeologist ben gates, search for a chest of rich rumor to have been stash away by georg washington, thoma jefferson and benjamin franklin dure the revolutionari war. the chest' whereabout may lie in secret clue emb in the constitut and the declar of independence, and gate is in a race to find the gold befor hi enemi do. adventur action thriller mysteri riddl treasur treasur hunt archaeologist archeolog nicola cage dian kruger justin bartha jon turteltaub",
      292: "in hi homeland of alagaesia, a farm boy happen upon a dragon' egg -- a discoveri that lead him on a predestin journey where he realiz he' the one person who can defend hi home against an evil king. fantasi action adventur famili base on novel mythic creatur dragon fantasi world teenag hero base on young adult novel ed speleer jeremi iron sienna guillori stefen fangmeier",
      293: "max imagin run away from hi mom and sail to a far-off land where larg talk beast -- ira, carol, douglas, the bull, judith and alexand -- crown him as their king, play rumpus, build fort and discov secret hideaways. famili fantasi children' book igloo wolf costum swallow whole hit with a rock lie fall down a hill snowbal fight children' perspect max record catherin keener lauren ambro spike jonz",
      294: 'a teenag find herself transport to a deep forest set where a battl between the forc of good and the forc of evil is take place. she band togeth with a rag-tag group charact in order to save their world -- and ours. anim adventur famili fantasi fantasi miniatur peopl josh hutcherson amanda seyfri colin farrel chri wedg',
      295: 'american tourist frank (johnni depp) meet mysteri british woman elsi (angelina jolie) on the train to venice. romanc seem to bud, but there\' more to her than meet the eye. remak of the 2005 french film "anthoni zimmer", written and direct by jérôme salle. action thriller romanc pari hotel fal ident undercov agent romanc johnni depp angelina joli paul bettani florian henckel von donnersmarck',
      296: "on decemb 28th, 1999, the citizen of new york citi are get readi for the turn of the millennium. however, the devil decid to crash the parti by come to the city, inhabit a man' body, and search for hi chosen bride, a 20-year-old woman name christin york. the world will end, and the onli hope lie within an atheist call jericho cane. action fantasi horror mysteri christian sex new year' eve pastor nuditi mephisto nightmar bibl satanist faith ex-cop anti-christ millenium atheist suspen priest hospit train new york citi explo church violenc devil woman in jeopardi satan flashback stigmata arnold schwarzenegg gabriel byrn kevin pollak peter hyam",
      297: "an ex-mercenari turn smuggler. a mend fisherman. amid the explo civil war overtak 1999 sierra leone, these men join for two desper missions: recov a rare pink diamond of immen valu and rescu the fisherman' son conscript as a child soldier into the brutal rebel forc rip a swath of tortur and bloodsh countrywide. drama thriller action rebel journalist journal loss of famili slaveri mercenari diamond mine sierra leon bootlegg fisherman special unit smuggl genocid in rwanda oppress leonardo dicaprio djimon hounsou jennif connelli edward zwick",
      298: "a new york stockbrok refu to cooper in a larg secur fraud case involv corrupt on wall street, corpor bank world and mob infiltration. base on jordan belfort' autobiography. crime drama comedi corrupt sex sexual bank humor biographi wall street marriag crisi rise and fall stockbrok drug stock broker leonardo dicaprio jonah hill margot robbi martin scors",
      299: "the dark knight of gotham citi confront a dastardli duo: two-fac and the riddler. formerli district attorney harvey dent, two-fac believ batman cau the courtroom accid which left him disfigur on one side. and edward nygma, computer-geniu and former employ of millionair bruce wayne, is out to get the philanthropist; as the riddler. former circu acrobat dick grayson, hi famili kill by two-face, becom wayne' ward and batman' new partner robin. action crime fantasi riddl dc comic rose gotham citi partner superhero robin broken neck psychologist violenc crimin district attorney millionair fall down stair tie up tommi gun beretta knock out super power disfigur father figur val kilmer tommi lee jone jim carrey joel schumach",
      300: 'set in the future, the stori follow a young soldier name johnni rico and hi exploit in the mobil infantry. rico\' militari career progress from recruit to non-commiss offic and final to offic against the backdrop of an interstellar war between mankind and an arachnoid speci known as "the bugs". adventur action thriller scienc fiction moon asteroid space marin intellig bueno air space battl dystopia armi satir spaceship soldier drill instructor militari casper van dien dina meyer deni richard paul verhoeven',
      301: 'a set of six nest stori span time between the 19th centuri and a distant post-apocalypt future. cloud atla explor how the action and consequ of individu live impact one anoth throughout the past, the present and the future. action, mysteri and romanc weav through the stori as one soul is shape from a killer into a hero and a singl act of kind rippl across centuri to inspir a revolut in the distant future. base on the award win novel by david mitchell. direct by tom tykwer and the wachowskis. drama scienc fiction clone futur dystopia ensembl cast duringcreditsst centuri woman director 1930 tom hank hall berri jim broadbent tom tykwer',
      302: "soren, a young barn owl, is kidnap by owl of st. aggie's, osten an orphanage, where owlet are brainwash into becom soldiers. he and hi new friend escap to the island of ga'hoole, to assist it noble, wise owl who fight the armi be creat by the wick ruler of st. aggie's. the film is base on the first three book in the series. anim adventur famili fantasi owl emili barclay abbi cornish essi davi zack snyder",
      303: 'liquid after discov a corpor conspiracy, mild-mann graphic artist patienc phillip wash up on an island, where she\' resurrect and endow with the prowess of a cat -- and she\' eager to use her new skill ... as a vigilante. befor you can say "cat and mouse," handsom gumsho tom lone is on her tail. action crime white russian sex dc comic beauti sexism basketb superheroin femal protagonist evil corpor catwoman mask superhero cat ladi hall berri benjamin bratt sharon stone pitof',
      304: 'fourteen hundr year ago, a torment soul walk the earth that wa neither man nor god. hercul wa the power son of the god king zeus, for thi he receiv noth but suffer hi entir life. after twelv arduou labor and the loss of hi family, thi dark, world-weari soul turn hi back on the god find hi onli solac in bloodi battle. over the year he warm to the compani of six similar souls, their onli bond be their love of fight and presenc of death. these men and woman never question where they go to fight or whi or whom, just how much they will be paid. now the king of thrace ha hire these mercenari to train hi men to becom the greatest armi of all time. it is time for thi bunch of lost soul to final have their eye open to how far they have fallen when they must train an armi to becom as ruthless and blood thirsti as their reput ha become. action adventur mercenari battl ancient greec hercul warrior sagen dwayn johnson ian mcshane john hurt brett ratner',
      305: 'when space galleon cabin boy jim hawkin discov a map to an intergalact "loot of a thousand worlds," a cyborg cook name john silver teach him to battl supernova and space storms. but, soon, jim realiz silver is a pirat intent on mutiny! adventur anim famili fantasi scienc fiction cyborg base on novel space marin mutini loss of father map pirat gang treasur hunt littl boy space alien anim money treasur map planet troubl teen space pirat joseph gordon-levitt brian murray david hyde pierc ron clement',
      306: 'on hi latest expedition, dr. rick marshal is suck into a space-tim vortex alongsid hi research assist and a redneck survivalist. in thi altern universe, the trio make friend with a primat name chaka, their onli alli in a world full of dinosaur and other fantast creatures. adventur comedi scienc fiction alien life-form dinosaur primat duringcreditsst will ferrel anna friel danni mcbride brad silberl',
      307: 'barney, christma and the rest of the team come face-to-fac with conrad stonebanks, who year ago co-found the expend with barney. stonebank subsequ becam a ruthless arm trader and someon who barney wa forc to kill… or so he thought. stonebanks, who elud death onc before, now is make it hi mission to end the expend -- but barney ha other plans. barney decid that he ha to fight old blood with new blood, and bring in a new era of expend team members, recruit individu who are younger, faster and more tech-savvy. the latest mission becom a clash of classic old-school style versu high-tech experti in the expendables’ most person battl yet. action adventur thriller cia arm dealer sequel rescu mission hospit battl sledgehamm revolv sylvest stallon jason statham harrison ford patrick hugh',
      308: 'a young undercov fbi agent infiltr a gang of thiev who share a common interest in extrem sports. a remak of the 1991 film, "point break". action crime thriller undercov undercov agent extrem sport fbi agent 3d edgar ramírez luke bracey teresa palmer ericson core',
      309: 'tim avery, an aspir cartoonist, find himself in a predica when hi dog stumbl upon the mask of loki. then after conceiv an infant son "born of the mask", he discov just how looney child rai can be. fantasi comedi famili adventur babi mask vike jami kennedi alan cum traylor howard lawrenc guterman',
      310: 'in the winter of 1820, the new england whale ship essex wa assault by someth no one could believe: a whale of mammoth size and will, and an almost human sen of vengeance. the real-lif maritim disast would inspir herman melville’ mobi dick. but that told onli half the story. “heart of the sea” reveal the encounter’ harrow aftermath, as the ship’ surviv crew is push to their limit and forc to do the unthink to stay alive. brave storms, starvation, panic and despair, the men will call into question their deepest beliefs, from the valu of their live to the moral of their trade, as their captain search for direct on the open sea and hi first mate still seek to bring the great whale down. thriller drama adventur action histori suicid ocean sea hunger shipwreck ship whale base on true stori strand surviv whale death new england lost at sea base on true event whale ship starvat 19th centuri cannib refer to mobi dick whale oil nantucket chri hemsworth benjamin walker cillian murphi ron howard',
      311: 'the year is 2087, the set is the moon. pluto nash, the high-fli success owner of the hottest nightclub in the universe, find himself in troubl when he refu to sell hi club to lunar gangster mogan, who just happen to be help the mysteri rex crater mastermind a plan to take over the entir moon. action comedi scienc fiction moon casino bar nightclub futur mafia boss laser gun eddi murphi randi quaid rosario dawson ron underwood',
      312: 'dure the u.s.-l occup of baghdad in 2003, chief warrant offic roy miller and hi team of armi inspector were dispatch to find weapon of mass destruct believ to be stockpil in the iraqi desert. rocket from one booby-trap and treacher site to the next, the men search for deadli chemic agent but stumbl instead upon an elabor cover-up that threaten to invert the purpo of their mission. war action adventur drama thriller weapon of mass destruct baghdad iraqi matt damon greg kinnear brendan gleeson paul greengrass',
      313: 'snoopi embark upon hi greatest mission as he and hi team take to the sky to pursu their arch-nemesis, while hi best pal charli brown begin hi own epic quest back home. anim base on comic strip famili 3d charli brown snoopi noah schnapp bill melendez venu schulthei steve martino',
      314: "an employ of a corpor with a lucr secret process is tempt to betray it. but there' more to it than that. crime drama mysteri thriller dialogu confid invent independ film steve martin campbel scott ben gazzara david mamet",
      315: "rick and evelyn o'connell, along with their 8 year old son alex, discov the key to the legendari scorpion king' might, the fabl bracelet of anubis. unfortunately, a newli resurrect imhotep ha design on the bracelet as well, and isn't abov kidnap it new bearer, alex, to gain control of anubis' otherworldli army. adventur action fantasi son ancient egypt bracelet brendan fraser rachel weisz john hannah stephen sommer",
      316: "it' 1863. america wa born in the streets. amsterdam vallon return to the five point of america to seek vengeanc against the psychot gangland kingpin, bill the butcher, who murder hi father year earlier. with an eager pickpocket by hi side and a whole new army, vallon fight hi way to seek vengeanc on the butcher and restor peac in the area. drama histori crime fire irish-american immigr gang war pickpocket ship gang of thiev butcher pig armi rescu gang leonardo dicaprio daniel day-lewi cameron diaz martin scors",
      317: "a western find refug with a group of women in a church dure japan' rape of nank in 1937. pose as a priest, he attempt to lead the women to safety. drama histori war forc prostitut child rape christian bale ni ni tong dawei zhang yimou",
      318: "codi is a surf penguin from shiverpool who dream of make it big and be like hi idol big z. on hi journey he discov hi talent are not all he think they are and he must learn to accept that their is more to surf than fame and fortune. surf' up is a 2007 american computer-anim mockumentari film produc by soni pictur anim and distribut by columbia pictur and imagework studios. it star the voic of shia labeouf, jeff bridges, zooey deschanel, jon heder among others. anim comedi famili sea world cup surfer wave surfboard giant wave world champion idol mockumentari shia labeouf jeff bridg zooey deschanel ash brannon",
      319: "what doe it take to becom a stepford wife, a woman perfect beyond belief? ask the stepford husbands, who'v creat thi high-tech, terrifi littl town. action comedi scienc fiction android housewif transform nicol kidman matthew broderick bett midler frank oz",
      320: 'when u.s. ranger and an elit delta forc team attempt to kidnap two underl of a somali warlord, their black hawk helicopt are shot down, and the american suffer heavi casualties, face inten fight from the militia on the ground. action histori war prison of war wound somalia warlord famin delta forc rescu oper josh hartnett ewan mcgregor jason isaac ridley scott',
      321: 'two rival politician compet to win an elect to repr their small north carolina congress district in the unit state hou of representatives. comedi polit politician elect campaign north carolinam congressman polit candid moustach polit corrupt campaign manag campaign financ will ferrel zach galifianaki dylan mcdermott jay roach',
      322: 'in 2257, a taxi driver is unint given the task of save a young girl who is part of the key that will ensur the surviv of humanity. adventur fantasi action thriller scienc fiction clone taxi cyborg egypt futur stowaway space travel race against time arm dealer love alien priest end of the world good vs evil shootout polic chase cab driver new york citi space opera militari opera singer resort hotel ancient astronaut archeologist ancient evil crui liner bruce willi gari oldman ian holm luc besson',
      323: "carrie, charlotte, and miranda are all marri now, but they'r still up for a littl fun in the sun. when samantha get the chanc to visit one of the most extravag vacat destin on the planet and offer to bring them all along, they surmi that a women-onli retreat may be the perfect excu to eschew their respon and rememb what life wa like befor they decid to settl down. comedi drama romanc sarah jessica parker kristin davi cynthia nixon michael patrick king",
      324: 'after a fail swindle, two con-men end up with a map to el dorado, the fabl "citi of gold," and an unintend trip to the new world. much to their surprise, the map doe lead the pair to the mythic city, where the startl inhabit promptli begin to worship them as gods. the onli question is, do they take the worship nativ for all they\'r worth, or is there a bit more to el dorado than riches? adventur anim comedi famili gold hor sword fight kenneth branagh kevin kline rosi perez don michael paul',
      325: 'manny, diego, and sid embark upon anoth adventur after their contin is set adrift. use an iceberg as a ship, they encount sea creatur and battl pirat as they explor a new world. anim comedi adventur famili blue foot boobi prehistor time melt ice badger eleph seal float ice land bridg era glacial deriva john leguizamo ray romano chri wedg steve martino',
      326: "when her father unexpectedli pass away, young ella find herself at the merci of her cruel stepmoth and her daughters. never one to give up hope, ella' fortun begin to chang after meet a dash stranger in the woods. romanc fantasi famili drama cinderella magic princ fairi tale kingdom royalti orphan lost shoe evil stepmoth retel lili jame cate blanchett richard madden kenneth branagh",
      327: 'after be brutal murdered, 14-year-old susi salmon watch from heaven over her grief-stricken famili -- and her killer. as she observ their daili lives, she must balanc her thirst for reveng with her desir for her famili to heal. fantasi drama rape 1970 evid tree afterlif loss of daughter serial killer corp pedophil teenag love griev childhood sexual abu base on young adult novel rachel weisz mark wahlberg susan sarandon peter jackson',
      328: "nemo, an adventur young clownfish, is unexpectedli taken from hi great barrier reef home to a dentist' offic aquarium. it' up to hi worrisom father marlin and a friendli but forget fish dori to bring nemo home -- meet vegetarian sharks, surfer dude turtles, hypnot jellyfish, hungri seagulls, and more along the way. anim famili father son relationship harbor underwat fish tank great barrier reef miss child aftercreditsst duringcreditsst short term memori loss clownfish father son reunion protect father albert brook ellen degen alexand gould andrew stanton",
      329: "aragorn is reveal as the heir to the ancient king as he, gandalf and the other member of the broken fellowship struggl to save gondor from sauron' forces. meanwhile, frodo and sam bring the ring closer to the heart of mordor, the dark lord' realm. adventur fantasi action elv orc middle-earth (tolkien) base on novel suspicion braveri war honor troll brutal violenc ghost end of trilog quest sword and sorceri elijah wood ian mckellen viggo mortensen peter jackson",
      330: 'frodo and sam are trek to mordor to destroy the one ring of power while gimli, legola and aragorn search for the orc-captur merri and pippin. all along, nefari wizard saruman await the fellowship member at the orthanc tower in isengard. adventur fantasi action elv orc middle-earth (tolkien) hobbit base on novel explo cave fort armi mission attack guid wizard ring sword and sorceri elijah wood ian mckellen viggo mortensen peter jackson',
      331: "john gregory, who is a seventh son of a seventh son and also the local spook, ha protect the countri from witches, boggarts, ghoul and all manner of thing that go bump in the night. howev john is not young anymore, and ha been seek an apprent to carri on hi trade. most have fail to survive. the last hope is a young farmer' son name thoma ward. will he surviv the train to becom the spook that so mani other couldn't? adventur fantasi magic chosen one dark fantasi witch hunter evil witch base on young adult novel sword and sorceri jeff bridg juliann moor ben barn sergei bodrov",
      332: "english aristocrat lara croft is skill in hand-to-hand combat and in the middl of a battl with a secret society. the shape archaeologist moonlight as a tomb raider to recov lost antiqu and meet her match in the evil powell, who' in search of a power relic. adventur fantasi action thriller treasur buddhist monk planetari configur angkor wat illuminati william blake treasur hunt archaeologist base on video game archeolog angelina joli jon voight iain glen simon west",
      333: 'two lead comput scientist work toward their goal of technolog singularity, as a radic anti-technolog organ fight to prevent them from creat a world where comput can transcend the abil of the human brain. thriller scienc fiction drama mysteri artifici intellig technolog nanotechnolog comput viru super comput resurrect love mind control terror scientist extremist moral dilemma comput scientist mind transfer quantum comput mind upload johnni depp paul bettani rebecca hall walli pfister',
      334: "in need of fund for research, dr. alan grant accept a larg sum of money to accompani paul and amanda kirbi on an aerial tour of the infam isla sorna. it isn't long befor all hell break loo and the strand wayfar must fight for surviv as a host of new -- and even more deadli -- dinosaur tri to make snack of them. adventur action thriller scienc fiction exot island dna paleontolog tyrannosauru rex velociraptor spinosauru airplan rescu mission dinosaur jurass park sam neill william h. maci téa leoni joe johnston",
      335: "scientist will rodman is determin to find a cure for alzheimer's, the disea which ha slowli consum hi father. will feel certain he is close to a breakthrough and test hi latest serum on apes, notic dramat increa in intellig and brain activ in the primat subject – especi caesar, hi pet chimpanzee. thriller action drama scienc fiction intellig zoo cage dystopia golden gate bridg ape monkey medic research alzheimer' disea jame franco freida pinto john lithgow rupert wyatt",
      336: 'upon move into the run-down spiderwick estat with their mother, twin brother jare and simon grace, along with their sister mallory, find themselv pull into an altern world full of faeri and other creatures. adventur famili fantasi brother sister relationship famili relationship singl mother altern realiti mother child relationship hidden truth goblin magic creatur fairi freddi highmor mary-loui parker nick nolt mark water',
      337: 'iconoclastic, take-no-prison cop john mcclane, find himself for the first time on foreign soil after travel to moscow to help hi wayward son jack - unawar that jack is realli a highly-train cia oper out to stop a nuclear weapon heist. with the russian underworld in pursuit, and battl a countdown to war, the two mcclane discov that their oppo method make them unstopp heroes. action thriller bomb cia russia escap courthou rogu moscow bruce willi jai courtney sebastian koch john moor',
      338: "base on the 1836 standoff between a group of texan and tejano men, led by davi crockett and jim bowie, and mexican dictat santa anna' forc at the alamo in san antonio, texas. western histori war texa offic upri alamo mexican denni quaid billi bob thornton jason patric john lee hancock",
      339: "bob parr ha given up hi superhero day to log in time as an insur adjust and rai hi three children with hi formerli heroic wife in suburbia. but when he receiv a mysteri assignment, it' time to get back into costume. action adventur anim famili secret ident secret hero island wretch supernatur power weapon lawsuit superhero craig t. nelson holli hunter samuel l. jackson brad bird",
      340: 'morgan adam and her slave, william shaw, are on a quest to recov the three portion of a treasur map. unfortunately, the final portion is held by her murder uncle, dawg. her crew is skeptic of her leadership abilities, so she must complet her quest befor they mutini against her. thi is made yet more difficult by the effort of the british crown to end her pirat raids. action adventur exot island treasur map ship scalp pirat geena davi matthew modin frank langella renni harlin',
      341: "accid prone teenager, perci discov he' actual a demi-god, the son of poseidon, and he is need when zeus' lightn is stolen. perci must master hi new found skill in order to prevent a war between the god that could devast the entir world. adventur fantasi famili monster greek mytholog god poseidon lightn bolt base on young adult novel logan lerman brandon t. jackson alexandra daddario chri columbu",
      342: "men in black follow the exploit of agent kay and jay, member of a top-secret organ establish to monitor and polic alien activ on earth. the two men in black find themselv in the middl of the deadli plot by an intergalact terrorist who ha arriv on earth to assassin two ambassador from oppo galaxies. in order to prevent world from colliding, the mib must track down the terrorist and prevent the destruct of earth. it' just anoth typic day for the men in black. action adventur comedi scienc fiction secret ident sun glass undercov space marin illeg immigr deport new ident giant cockroach cannon fli saucer stay permit alien fiction govern agenc tommi lee jone will smith linda fiorentino barri sonnenfeld",
      343: "andi head off to cowboy camp, leav hi toy to their own devices. thing shift into high gear when an obsess toy collector name al mcwhiggen, owner of al' toy barn kidnap woody. andy' toy mount a dare rescu mission, buzz lightyear meet hi match and woodi ha to decid where he and hi heart truli belong. anim comedi famili museum prosecut ident crisi airplan flea market collector teamwork friendship rescu team garag sale duringcreditsst toy come to life personif inanim object come to life tom hank tim allen joan cusack john lasset",
      344: 'a runaway train, transport deadly, toxic chemicals, is barrel down on stanton, pennsylvania, and onli two men can stop it: a veteran engin and a young conductor. thousand of live hang in the balanc as these ordinari hero attempt to chase down one million ton of hurtl steel and prevent an epic disaster. action thriller runaway train denzel washington chri pine rosario dawson toni scott',
      345: "it' vacat time for carter as he find himself alongsid lee in hong kong wish for more excitement. while carter want to parti and meet the ladies, lee is out to track down a triad gang lord who may be respon for kill two men at the american embassy. thing get complic as the pair stumbl onto a counterfeit plot. the boy are soon up to their neck in fist fight and life-threaten situations. a trip back to the u.s. may provid the answer about the bombing, the counterfeiting, and the true allegi of sexi custom agent isabella. action comedi crime thriller duringcreditsst chri tucker jacki chan zhang ziyi brett ratner",
      346: "when clair spencer start hear ghostli voic and see spooki images, she wonder if an otherworldli spirit is tri to contact her. all the while, her husband tri to reassur her by tell her it' all in her head. but as clair investigates, she discov that the man she love might know more than he' let on. drama horror mysteri thriller secret haunt hou ouija board haunt miss girl ghost harrison ford michel pfeiffer diana scarwid robert zemecki",
      347: 'inventor flint lockwood creat a machin that make cloud rain food, enabl the down-and-out citizen of chewandswallow to feed themselves. but when the fall food reach gargantuan proportions, flint must scrambl to avert disaster. can he regain control of the machin and put an end to the wild weather befor the town is destroyed? anim comedi famili weather food scienc bill hader anna fari jame caan phil lord',
      348: 'time are chang for manni the moodi mammoth, sid the motor mouth sloth and diego the crafti saber-tooth tiger. life heat up for our hero when they meet some new and none-too-friendli neighbor – the mighti dinosaurs. anim comedi famili adventur ice age bridg insan jungl dinosaur birth duringcreditsst 3d ray romano john leguizamo deni leari carlo saldanha',
      349: 'a timid magazin photo manag who live life vicari through daydream embark on a true-lif adventur when a neg goe missing. adventur comedi drama fantasi himalaya photograph magazin iceland daydream photograph shark fire from the job skateboard dreamer onlin date daydream ben stiller kristen wiig patton oswalt ben stiller',
      350: "aspect of thi take on the 1970 hit tv seri are similar to the origin show :angel dylan, natali and alex still work for charli and interfac with bosley. they still flip their hair, stop traffic with a smile and kick butt. the differ are the unsubtl humor, the martial art train and the high-tech premise: thi time, they'r hot on the trail of stolen software. action adventur comedi crime thriller martial art femal friendship millionair agent cameron diaz luci liu drew barrymor mcg",
      351: "to take down south boston' irish mafia, the polic send in one of their own to infiltr the underworld, not realiz the syndic ha done likewise. while an undercov cop curri favor with the mob kingpin, a career crimin rise through the polic ranks. but both side soon discov there' a mole among them. drama thriller crime undercov boston polic friend mafia undercov cop mobster mole state polic polic train realtor leonardo dicaprio matt damon jack nicholson martin scors",
      352: 'a tomboyish girl disgui herself as a young man so she can fight with the imperi chine armi against the invad huns. with help from wise-crack dragon mushu, mulan just might save her countri -- and win the heart of handsom captain li shang. anim famili adventur homeland music train daughter cricket princess dragon luck eddi murphi jacki chan ming-na wen toni bancroft',
      353: "vietnam veteran 'four leaf' tayback' memoir, tropic thunder, is be made into a film, but director damien cockburn can’t control the cast of prima donnas. behind schedul and over budget, cockburn is order by a studio execut to get film back on track, or risk it cancellation. on tayback' advice, cockburn drop the actor into the middl of the jungl to film the remain scene but, unbeknownst to the actor and production, the group have been drop in the middl of the golden triangle, the home of heroin-produc gangs. action comedi film make satir jungl movi star southeast asia land mine shackl war filmmak duringcreditsst blackfac method act ben stiller jack black robert downey jr. ben stiller",
      354: "thi english-languag adapt of the swedish novel by stieg larsson follow a disgrac journalist, mikael blomkvist, as he investig the disappear of a weari patriarch' niec from 40 year ago. he is aid by the pierced, tattooed, punk comput hacker name lisbeth salander. as they work togeth in the investigation, blomkvist and saland uncov immen corrupt beyond anyth they have ever imagined. thriller crime mysteri drama rape journalist base on novel journal hacker nazi punk investig remak antisoci person disord serial killer disappear hack comput hacker bibl quot scandinavian abu daniel craig rooney mara christoph plummer david fincher",
      355: 'new york detect john mcclane is back and kick bad-guy butt in the third instal of thi action-pack series, which find him team with civilian zeu carver to prevent the loss of innoc lives. mcclane thought he\'d seen it all, until a geniu name simon engag mcclane, hi new "partner" -- and hi belov citi -- in a deadli game that demand their concentration. action thriller bomb taxi riddl robberi detect helicopt gold subway ship fistfight polic sequel decept shootout new york citi explo violenc car chase fbi agent simon say flashback dump truck aqueduct action hero feder reserv bank bruce willi jeremi iron samuel l. jackson john mctiernan',
      356: 'eccentr consult detective, sherlock holm and doctor john watson battl to bring down a new nemesi and unravel a deadli plot that could destroy england. action adventur crime mysteri detect scotland yard coffin black magic arrest partner sherlock holm murder steampunk pentagram clue robert downey jr. jude law rachel mcadam guy ritchi',
      357: 'a fal accu nobleman surviv year of slaveri to take vengeanc on hi best friend who betray him. drama betray vengeanc jack huston tobi kebbel rodrigo santoro timur bekmambetov',
      358: "the world' most highli qualifi crew of archaeologist and explor is led by historian milo thatch as they board the incr 1,000-foot submarin ulyss and head deep into the mysteri of the sea. anim famili adventur scienc fiction sea atlanti anim underwat sea monster michael j. fox corey burton claudia christian gari trousdal",
      359: 'through a seri of misunderstandings, alvin, simon and theodor come to believ that dave is go to propo to hi new girlfriend in new york citi - and dump them. they have three day to get to him and stop the proposal. adventur anim comedi famili chipmunk cgi talk anim aftercreditsst duringcreditsst jason lee justin long bella thorn walt becker',
      360: 'wound in africa dure world war ii, nazi col. clau von stauffenberg return to hi nativ germani and join the resist in a dare plan to creat a shadow govern and assassin adolf hitler. when event unfold so that he becom a central player, he find himself task with both lead the coup and person kill the führer. drama thriller histori war berlin suicid bomb assassin resist wife husband relationship world war ii adolf hitler plan friendship decept treason colonel militari offic plot german offic piano wire medal violenc tom crui caric van houten kenneth branagh bryan singer',
      361: "an isra counterterror soldier with a secretli fabul ambit to becom a manhattan hairstylist. zohan' desir run so deep that he'll do anyth -- includ fake hi own death and go head-to-head with an arab cab driver -- to make hi dream come true. comedi action new york israel middl east hairdress ladykil mossad isra palestinian heart-throb middl east conflict hairstyl hacki sack adam sandler john turturro emmanuel chriqui denni dugan",
      362: "video game expert are recruit by the militari to fight 1980s-era video game charact who'v attack new york. action comedi scienc fiction video game nerd alien attack 3d pixel adam sandler michel monaghan peter dinklag chri columbu",
      363: "a robot boy, the first program to love, david is adopt as a test case by a cybertron employ and hi wife. though he gradual becom their child, a seri of unexpect circumst make thi life imposs for david. without final accept by human or machines, david embark on a journey to discov where he truli belongs, uncov a world in which the line between robot and machin is both vast and profoundli thin. drama scienc fiction adventur artifici intellig propheci prostitut android loss of mother extraterrestri technolog ice age adopt fairi tale pinocchio prosecut gigolo hologram dystopia alien destini captur doppelgang haley joel osment franc o'connor sam robard steven spielberg",
      364: "workahol jim ever and hi wife/busi partner, sara get a call one night from mansion owner, edward gracey want to sell hi house. onc the ever famili arriv at the mansion a butler take them to dine with gracey. gracey take one look at sara and he think she' hi lost lover. thriller fantasi comedi famili mysteri secret passag magic estat agent haunt hou famili vacat ghost aftercreditsst eddi murphi terenc stamp nathaniel parker rob minkoff",
      365: 'contact is a scienc fiction film about an encount with alien intelligence. base on the novel by carl sagan the film star jodi foster as the one chosen scientist who must make some difficult deci between her beliefs, the truth, and reality. drama scienc fiction mysteri base on novel nasa new mexico extraterrestri technolog prime number star radio wave wormhol fanat spiritu religion scientist sabotag ham radio alien contact mechan engin observatori eccentr man radio telescop jodi foster matthew mcconaughey jame wood robert zemecki',
      366: "cocki researcher, sebastian cain is work on a project to make live creatur invi and he' so confid he' found the right formula that he test it on himself and soon begin to vanish. the onli problem is – no-on can determin how to make him visibl again. caine' predica eventu drive him mad, with terrifi results. action scienc fiction thriller kill human experi scientist invi man scienc experi kevin bacon elisabeth shue josh brolin paul verhoeven",
      367: 'after silvia broome, an interpret at unit nation headquarters, overhear plan of an assassination, an american secret servic agent is sent to investigate. crime thriller new york dictat africa destruct of a civil assassin resist reveng murder unit nation wit to murder fbi agent resist fighter nicol kidman sean penn catherin keener sydney pollack',
      368: 'in their quest to confront the ultim evil, perci and hi friend battl swarm of mythic creatur to find the mythic golden fleec and to stop an ancient evil from rising. adventur famili fantasi poison herm poseidon demigod golden fleec olympu 3d krono overthrow olympu base on young adult novel logan lerman alexandra daddario dougla smith thor freudenth',
      369: "lara croft ventur to an underwat templ in search of the mytholog pandora' box but, after secur it, it is promptli stolen by the villain leader of a chine crime syndicate. lara must recov the box befor the syndicate' evil mastermind use it to construct a weapon of catastroph capabilities. action adventur fantasi thriller riddl treasur medallion kenia alexand the great pandora' box chine mafia treasur hunt hong kong archaeologist base on video game archeolog angelina joli gerard butler noah taylor jan de bont",
      370: 'one year after outwit the fbi and win the public’ adul with their mind-bend spectacles, the four horsemen resurfac onli to find themselv face to face with a new enemi who enlist them to pull off their most danger heist yet. action adventur comedi crime mysteri thriller london england china magic secret societi vigil sequel reveng heist on the run macau china magician jess eisenberg woodi harrelson mark ruffalo jon m. chu',
      371: 'ivan tretiak, russian mafia boss who want to creat an oil crisi in moscow and seiz power as a result send simon templar, great intern criminal, to england to get a secret formula for cold fusion from u.s. scientist emma russell. templar fall in love with emma and they tri to outwit tretiak and hi guerrillas, hide from them in moscow thriller action romanc scienc fiction adventur berlin russia ga master thief the saint val kilmer elisabeth shue rade serbedzija phillip noyc',
      372: 'veteran spi nathan muir is on the verg of retir from the cia when he learn that hi one-tim protégé and close friend, tom bishop, is a polit prison sentenc to die in beijing. although their friendship ha been mar by bad blood and resentment, muir agr to take on the most danger mission of hi career and rescu bishop. action crime thriller spi china cia cold war robert redford brad pitt catherin mccormack toni scott',
      373: 'when contact is lost with the crew of the first mar expedition, a rescu mission is launch to discov their fate. scienc fiction mar spacecraft space travel alien long take outer space astronaut dismemb alien contact trap in space gari sini tim robbin don cheadl brian de palma',
      374: 'captur by smuggler when he wa just a hatchling, a macaw name blu never learn to fli and live a happili domest life in minnesota with hi human friend, linda. blu is thought to be the last of hi kind, but when word come that jewel, a lone female, live in rio de janeiro, blu and linda go to meet her. anim smuggler kidnap blu and jewel, but the pair soon escap and begin a peril adventur back to freedom -- and linda. anim adventur comedi famili brazil pet bird music canari samba anim duringcreditsst rio 1 río 1 jess eisenberg ann hathaway lesli mann carlo saldanha',
      375: 'richard martin buy a gift, a new ndr-114 robot. the product is name andrew by the youngest of the family\' children. "bicentenni man" follow the life and time of andrew, a robot purcha as a household applianc program to perform menial tasks. as andrew begin to experi emot and creativ thought, the martin famili soon discov they don\'t have an ordinari robot. comedi scienc fiction android hologram freedom futurist robot robin william sam neill embeth davidtz chri columbu',
      376: "an earthquak shatter a peac lo angel morn and open a fissur deep into the earth, cau lava to start bubbl up. as a volcano begin form in the la brea tar pits, the director of the city' emerg manag service, mike roark, work with geologist ami barnes, must then use everi resourc in the citi to tri and stop the volcano from consum lo angeles. scienc fiction action drama thriller subway lava volcano volcanologist lo angel tommi lee jone ann hech gabi hoffmann mick jackson",
      377: "franki mcguire, one of the ira' deadliest assassins, draw an american famili into the crossfir of terrorism. but when he is sent to the u.s. to buy weapons, franki is hou with the famili of tom o'meara, a new york cop who know noth about frankie' real identity. their surpri friendship, and tom' grow suspicions, forc franki to choo between the promi of peac or a lifetim of murder. crime thriller drama new york terrorist anonym northern ireland harrison ford brad pitt margaret colin alan j. pakula",
      378: "when russia' first nuclear submarin malfunct on it maiden voyage, the crew must race to save the ship and prevent a nuclear disaster. drama histori thriller submarin soviet union core melt north atlant nuclear woman director harrison ford liam neeson peter sarsgaard kathryn bigelow",
      379: 'a film adapt of the classic sword and sorceri hero, conan the barbarian. a hord of rampag warrior massacr the parent of young conan and enslav the young child for year on the wheel of pain. as the sole survivor of the childhood massacre, conan is relea from slaveri and taught the ancient art of fighting. transform himself into a kill machine, conan travel into the wilder to seek vengeanc on thulsa doom, the man respon for kill hi family. in the wilderness, conan take up with the thiev valeria and subotai. the group come upon king osric, who want the trio of warrior to help rescu hi daughter who ha join doom in the hills. adventur fantasi action gladiat repay despot barbarian sword and sorceri arnold schwarzenegg jame earl jone max von sydow john miliu',
      380: "the true stori of boxer, jim braddock who, in the 1920’ after hi retirement, ha a surpri comeback in order to get him and hi famili out of a social poor state. romanc drama histori transport netherland world cup social depriv famili family' daili life boxer box match comeback train heavi weight folk hero biographi daughter defeat sport russel crow rené zellweg paul giamatti ron howard",
      381: "set in 1920' vienna, thi a tale of a littl girl, whose godfath give her a special doll one christma eve. fantasi action famili ell fan nathan lane john turturro andrei konchalovski",
      382: 'true stori of the under depression-era racehor whose victori lift not onli the spirit of the team behind it but also those of their nation. drama histori hor race american dream racehor great depress jeff bridg david mccullough chri cooper gari ross',
      383: 'tv weatherman bill hard is tri to get hi tornado-hunt wife, jo, to sign divorc paper so he can marri hi girlfriend melissa. but mother nature, in the form of a seri of inten storm sweep across oklahoma, ha other plans. soon the three have join the team of stormcha as they attempt to insert a revolutionari measur devic into the veri heart of sever extrem violent tornados. action adventur drama wife husband relationship tornado twister oklahoma metereologist invent climat barn natur disast cow truck disast aunt niec relationship storm chaser divorc helen hunt bill paxton cari elw jan de bont',
      384: "chuck, a top intern manag for fedex, and kelly, a ph.d. student, are in love and head toward marriage. then chuck' plane to malaysia ditch at sea dure a terribl storm. he' the onli survivor, and he wash up on a tini island with noth but some flotsam and jetsam from the aircraft' cargo. adventur drama exot island suicid attempt volleyb lone airplan crash desert island tropic island surviv skill tom hank helen hunt chri noth robert zemecki",
      385: 'into the world of the emperor penguins, who find their soul mate through song, a penguin is born who cannot sing. but he can tap danc someth fierce! anim comedi ocean fish zoo penguin tap danc love crush snow anthropomorph sing antarctica famili duringcreditsst elijah wood robin william brittani murphi georg miller',
      386: 'when a cia oper to purcha classifi russian document is blown by a rival agent, who then show up in the sleepi seasid villag where bourn and mari have been living. the pair run for their live and bourne, who promi retali should anyon from hi former life attempt contact, is forc to onc again take up hi life as a train assassin to survive. action drama thriller berlin assassin base on novel amnesia sniper lie sequel suspen on the run shootout espionag violenc foot chase car chase explod hou though guy one against mani rail car dark past moscow hand to hand combat matt damon franka potent brian cox paul greengrass',
      387: 'russian terrorist conspir to hijack the aircraft with the presid and hi famili on board. the command in chief find himself face an imposs predicament: give in to the terrorist and sacrif hi family, or risk everyth to uphold hi principl - and the integr of the nation. action thriller prison corrupt journalist white hou hostag ultimatum hostage-tak air forc one aerial combat conspiraci gunfight fighter plane secret servic american presid hand to hand combat negoti polit prison airplan hijack harrison ford gari oldman glenn close wolfgang petersen',
      388: "less than 24 hour into hi parole, charismat thief danni ocean is alreadi roll out hi next plan: in one night, danny' hand-pick crew of specialist will attempt to steal more than $150 million from three la vega casinos. but to score the cash, danni risk hi chanc of reconcil with ex-wife, tess. thriller crime prison pickpocket strip club con artist atlant citi cockney accent la vega card dealer explo expert black and white scene male salt lake citi utah georg clooney brad pitt matt damon steven soderbergh",
      389: "the hot-head young d'artagnan along with three former legendari but now down on their luck musket must unit and defeat a beauti doubl agent and her villain employ from seiz the french throne and engulf europ in war. adventur action thriller number in titl histor fiction musket 17th centuri 3d milla jovovich orlando bloom logan lerman paul w.s. anderson",
      390: "dracula, who oper a high-end resort away from the human world, goe into overprotect mode when a boy discov the resort and fall for the count' teen-ag daughter. anim comedi famili fantasi witch magic mummi vampir dracula skeleton backpack frankenstein wolfman zombi invi man duringcreditsst nosferatu protect father fang vamp adam sandler steve buscemi david spade genndi tartakovski",
      391: 'the beauti princess gisel is banish by an evil queen from her magical, music anim land and find herself in the gritti realiti of the street of modern-day manhattan. shock by thi strang new environ that doesn\'t oper on a "happili ever after" basis, gisel is now adrift in a chaotic world badli in need of enchantment. but when gisel begin to fall in love with a charmingli flaw divorc lawyer who ha come to her aid - even though she is alreadi promi to a perfect fairi tale princ back home - she ha to wonder: can a storybook view of romanc surviv in the real world? comedi famili fantasi romanc poison queen fairi tale music princess portal anim fantasi world evil witch part anim ami adam patrick dempsey jame marsden kevin lima',
      392: "a danger cia renegad resurfac after a decad on the run. when the safe hou he' remand to is attack by mercenaries, a rooki oper escap with him. now, the unlik alli must stay aliv long enough to uncov who want them dead. action thriller cia violenc safe hou rogu agent cape town south africa soccer stadium denzel washington ryan reynold vera farmiga daniel espinosa",
      393: "get readi for a howl good time as an all new assort of irresist anim hero are unleash in thi great famili tail! in an unlik alliance, the outrag waddlesworth... a parrot who think he' a rottweiler... team up with oddball... an un-mark dalmat puppi eager to earn her spots! togeth they embark on a laugh-pack quest to outwit the ever-schem cruella de vil comedi famili london england prison relea from prison women' prison societi for the prevent of cruelti to anim puppi pelz dog dalmatian glenn close ioan gruffudd alic evan kevin lima",
      394: 'a luxuri condo manag lead a staff of worker to seek payback on the wall street swindler who defraud them. with onli day until the billionair get away with the perfect crime, the unlik crew of amateur thiev enlist the help of petti crook slide to steal the $20 million they’r sure is hidden in the penthouse. action comedi skyscrap thanksgiv billionair parad fbi agent apart high rise femal agent ponzi scheme empti safe caper comedi plan safecrack recruit heist movi deceit lobbi ben stiller eddi murphi casey affleck brett ratner',
      395: 'two women, one (cameron diaz) from america and one (kate winslet) from britain, swap home at christmastim after bad breakup with their boyfriends. each woman find romanc with a local man (jude law, jack black) but realiz that the immin return home may end the relationship. comedi romanc holiday london england film make christma parti countri hou room exchang surrey romant comedi lo angel multipl storylin woman director christma cameron diaz kate winslet jude law nanci meyer',
      396: 'hotshot washington lawyer, robert dean becom a victim of high-tech ident theft when a hacker slip an incrimin video into hi pocket. soon, a rogu nation secur agent set out to recov the tape – and destroy dean. action drama thriller corrupt washington d.c. helicopt fal accu ident mexican standoff blackmail intellig wiretap satellit nation secur agenc (nsa) polit explod build suspen mysteri mafia conspiraci lawyer crime privaci surveil baltimor maryland secret hideout will smith gene hackman jon voight toni scott',
      397: "ten year after their divorce, jane and jake adler unit for their son' colleg graduat and unexpectedli end up sleep together. but jake is married, and jane is embark on a new romanc with her architect. now, she ha to sort out her life – just when she thought she had it all figur out. comedi romanc graduat ex husband woman director meryl streep alec baldwin steve martin nanci meyer",
      398: "danni ocean' team of crimin are back and compo a plan more person than ever. when ruthless casino owner willi bank doublecross reuben tishkoff, cau a heart attack, danni ocean vow that he and hi team will do anyth to bring down willi bank along with everyth he' got. even if it mean ask for help from an enemy. crime thriller casino thief reveng heist la vega pretend to be rich labor strike georg clooney brad pitt matt damon steven soderbergh",
      399: 'boog, a domest 900lb. grizzli bear find himself strand in the wood 3 day befor open season. forc to reli on elliot, a fast-talk mule deer, the two form an unlik friendship and must quickli ralli other forest anim if they are to form a rag-tag armi against the hunters. adventur anim famili hunter mountain garag grizzli bear bunni chase forest deer bear hunt martin lawrenc ashton kutcher gari sini jill culton',
      400: "in a world divid into faction base on person types, tri learn that she' been classifi as diverg and won't fit in. when she discov a plot to destroy divergents, tri and the mysteri four must find out what make diverg danger befor it' too late. adventur action scienc fiction base on novel dystopia youth dystop futur cast system diverg base on young adult novel shailen woodley theo jame kate winslet neil burger",
      401: 'enemi at the gate is a war film from jean-jacqu annaud from 2001 that take place dure the battl of stalingard in world war ii between the russian and the germans. war winter sniper world war ii stalingrad jude law rachel weisz ed harri jean-jacqu annaud',
      402: "when travis, the mouthi son of a criminal, disappear in the amazon in search of a treasur artifact, hi father send in beck, who becom travis' rival for the affect of mariana, a mysteri brazilian woman. with hi steeli disposition, beck is a man of few word -- but it take him all the disciplin he can muster to work with travi to nab a tyrant who' after the same treasure. adventur action comedi thriller hunter bounti bounti hunter fight amazon treasur hunt jungl dwayn johnson seann william scott rosario dawson peter berg",
      403: "danni is obsess with a fiction movi charact action hero jack slater. when a magic ticket transport him into jack' latest adventure, danni find himself in a world where movi magic and realiti collide. now it' up to danni to save the life of hi hero and new friend. adventur fantasi action comedi famili magic movi in movi spoof magic object cartoon cat ticket self-referenti projectionist child' point of view arnold schwarzenegg f. murray abraham art carney john mctiernan",
      404: 'a sweep romant epic set in japan in the year befor world war ii, a penniless japan child is torn from her famili to work as a maid in a geisha house. drama histori romanc japan prostitut sister sister relationship brothel world war ii geisha zhang ziyi gong li youki kudoh rob marshal',
      405: 'in order to avoid a jail sentence, sean boswel head to tokyo to live with hi militari father. in a low-rent section of the city, shaun get caught up in the underground world of drift race action crime drama thriller car race car journey car mechan auto car garag auto-tun drift car automobil race luca black nathali kelley sung kang justin lin',
      406: 'each christmas, santa and hi vast armi of highli train elv produc gift and distribut them around the world in one night. however, when one of 600 million children to receiv a gift from santa on christma eve is missed, it is deem ‘acceptable’ to all but one – arthur. arthur clau is santa’ misfit son who execut an unauthor rooki mission to get the last present half way around the globe befor dawn on christma morning. drama anim famili comedi holiday santa clau duringcreditsst woman director christma jame mcavoy hugh lauri bill nighi barri cook',
      407: 'when the grim reaper come to collect the soul of megamogul bill parrish, he arriv with a proposition: host him for a "vacation" among the live in trade for a few more day of existence. parrish agrees, and use the pseudonym joe black, death begin take part in parrish\' daili agenda and fall in love with the man\' daughter. yet when black\' holiday is over, so is parrish\' life. fantasi drama mysteri life and death love at first sight broken engag firework religion and supernatur teenag crush fate doctor millionair brad pitt anthoni hopkin clair forlani martin brest',
      408: "firefight gordon brewer is plung into the complex and danger world of intern terror after he lose hi wife and child in a bomb credit to claudio 'the wolf' perrini. action thriller drama terrorist fbi colombia firemen reveng explo car explo bomb attack arnold schwarzenegg francesca neri elia kotea andrew davi",
      409: "bob fosse' semi-autobiograph film celebr show busi strip of glitz or giddi illusions. joe gideon (roy scheider) is at the top of the heap, one of the most success director and choreograph in music theatre. but he can feel hi world slowli collap around him--hi obsess with work ha almost destroy hi person life, and onli hi bottl of pill keep him going. drama music show busi film make tap danc movi in movi divorc tv show in film stand-up comedian broadway rainstorm surgeri dream sequenc edit semi autobiograph restroom screen room amphetamin prescript drug abu roy scheider jessica lang leland palmer bob foss",
      410: "after she spend all her money, an evil enchantress queen scheme to marri a handsome, wealthi prince. there' just one problem - he' in love with a beauti princess, snow white. now, join by seven rebelli dwarves, snow white launch an epic battl of good vs. evil... adventur fantasi drama comedi scienc fiction famili attempt murder fairi tale black magic cockroach villai good vs evil woman fight man insecur mirror snow kingdom snow white evil queen enchantress gala financ problem pendant half nake man return money evil plot duringcreditsst julia robert lili collin armi hammer tarsem singh",
      411: 'scott pilgrim is a film adapt of the critic acclaimed, award-win seri of graphic novel of the same name by canadian cartoonist bryan lee o’malley. scott pilgrim is a 23 year old canadian slacker and wannab rockstar who fall in love with an american deliveri girl, ramona v. flowers, and must defeat her seven "evil exes" to be abl to date her. action adventur comedi whip hipster underag girlfriend anim flashback character\' point of view camera shot unconsci girl fight vegan aftercreditsst michael cera mari elizabeth winstead kieran culkin edgar wright',
      412: "geophysicist dr. josh key discov that an unknown forc ha cau the earth' inner core to stop rotating. with the planet' magnet field rapidli deteriorating, our atmosph liter start to come apart at the seam with catastroph consequences. to resolv the crisis, keyes, along with a team of the world' most gift scientists, travel into the earth' core. their mission: deton a devic that will reactiv the core. action thriller adventur scienc fiction magnet field center of the earth disast film aaron eckhart hilari swank delroy lindo jon amiel",
      413: "the hilar begin when professor sherman klump find romanc with fellow dna specialist, deni gaines, and discov a brilliant formula that rever aging. but sherman' thin and obnoxi alter ego, buddi love, want out...and a big piec of the action. and when buddi get loose, thing get seriou nutty. fantasi comedi romanc scienc fiction alter ego mad scientist famili dean duringcreditsst research laboratori eddi murphi janet jackson larri miller peter segal",
      414: 'the mysteri inc. gang have gone their separ way and have been apart for two years, until they each receiv an invit to spooki island. not know that the other have also been invited, they show up and discov an amu park that affect young visitor in veri strang ways. mysteri adventur comedi amateur detect voodoo resort crime solv freddi prinz jr. sarah michel gellar matthew lillard raja gosnel',
      415: 'in the future, america is a dystopian wasteland. the latest scourg is ma-ma, a prostitute-turned-drug pusher with a danger new drug and aim to take over the city. the onli possibl of stop her is an elit group of urban polic call judges, who combin the duti of judge, juri and execut to deliv a brutal brand of swift justice. but even the top-rank judge, dredd, discov that take down ma-ma isn’t as easi as it seem in thi explo adapt of the huge popular comic series. action scienc fiction usa corrupt crime fighter judg metropoli law post-apocalypt dystopia execut case polic futurist base on comic book gore surviv gunfight gangster extrem violenc psychic violenc crimin justic drug lord base on graphic novel dystop futur dark humor expert marksman rooki dredd 2000 ad karl urban olivia thirlbi lena headey pete travi',
      416: 'a workahol architect find a univ remot that allow him to fast-forward and rewind to differ part of hi life. complic ari when the remot start to overrul hi choices. comedi drama fantasi romanc regret workahol heart attack architect die and death time travel remot control children liposuct hospit wed dog second chanc altern realiti fatherhood obe adam sandler kate beckins christoph walken frank coraci',
      417: 'inspir by the e.c. comic of the 1950s, georg a.romero and stephen king bring five tale of terror to the screen. horror comedi fantasi monster halloween meteor buri aliv cockroach antholog base on comic book gore anim sequenc zombi live dead hal holbrook adrienn barbeau fritz weaver georg a. romero',
      418: 'the ongo war between the canin and felin speci is put on hold when they join forc to thwart a rogu cat spi with her own sinist plan for conquest. comedi famili tortur aftercreditsst duringcreditsst 3d jame marsden nick nolt christina appleg brad peyton',
      419: 'david rice is a man who know no boundaries, a jumper, born with the uncanni abil to teleport instantli to anywh on earth. when he discov other like himself, david is thrust into a danger and bloodthirsti war while be hunt by a sinist and determin group of zealot who have sworn to destroy all jumpers. now, david’ extraordinari gift may be hi onli hope for survival! adventur fantasi scienc fiction adolesc base on novel loss of child fight chase teleport supernatur power leap in time enemi motherli love hayden christensen jami bell samuel l. jackson doug liman',
      420: 'in thi continu to the adventur of the demon superhero, an evil elf break an ancient pact between human and creatures, as he declar war against humanity. he is on a mission to relea the golden army, a deadli group of fight machin that can destroy the human race. as hell on earth is readi to erupt, hellboy and hi crew set out to defeat the evil prince. adventur fantasi scienc fiction auction northern ireland resign superhero rebellion violenc spear cut arm split screen superhero team arm rip off super villain remor self exil vanish figur father son conflict ron perlman selma blair jeffrey tambor guillermo del toro',
      421: "the true stori of the investig of 'the zodiac killer', a serial killer who terrifi the san francisco bay area, taunt polic with hi cipher and letters. the case becom an obsess for four men as their live and career are built and destroy by the endless trail of clues. crime drama mysteri thriller california san francisco kill journalist newspap mass murder plan murder embassi victim threat to death victim of murder code polic murder serial killer report jake gyllenha robert downey jr. mark ruffalo david fincher",
      422: 'futurist action about a man who meet a clone of himself and stumbl into a grand conspiraci about clone take over the world. scienc fiction clone futur murder clone laser gun dystop futur implant memori sci-fi thriller arnold schwarzenegg michael rapaport toni goldwyn roger spottiswood',
      423: 'bruce nolan toil as a "human interest" televi report in buffalo, n.y. despit hi high rate and the love of hi beauti girlfriend, grace, bruce remain unfulfilled. at the end of the worst day in hi life, he angrili ridicul god -- and the almighti responds, endow bruce with all of hi divin powers. fantasi comedi christian moon respon mose street gang lovesick journal new love faith prayer god car crash jim carrey jennif aniston philip baker hall tom shadyac',
      424: 'barney ross lead a band of highli skill mercenari includ knife enthusiast lee christmas, a martial art expert, heavi weapon specialist, demolitionist, and a loose-cannon sniper. when the group is commiss by the mysteri mr. church to assassin the dictat of a small south american island, barney and lee visit the remot local to scout out their opposit and discov the true natur of the conflict engulf the city. thriller adventur action tattoo martial art sniper island mercenari bridg rescu escap church drug blade ensembl cast duringcreditsst sylvest stallon jason statham dolph lundgren sylvest stallon',
      425: "when ethan hunt, the leader of a crack espionag team whose peril oper ha gone awri with no explanation, discov that a mole ha penetr the cia, he' surpri to learn that he' the no. 1 suspect. to clear hi name, hunt now must ferret out the real doubl agent and, in the process, even the score. adventur action thriller pari london england spi cia terrorist secret ident undercov arm deal headquart secret base secret mission pragu embassi secret agent tgv comput mission base on tv seri espionag agent tom crui jon voight emmanuel béart brian de palma",
      426: 'everi year in the ruin of what wa onc north america, the nation of panem forc each of it twelv district to send a teenag boy and girl to compet in the hunger games. part twist entertainment, part govern intimid tactic, the hunger game are a nation televi event in which “tributes” must fight with one anoth until one survivor remains. pit against highly-train tribut who have prepar for these game their entir lives, katniss is forc to reli upon her sharp instinct as well as the mentorship of drunken former victor haymitch abernathy. if she’ ever to return home to district 12, katniss must make imposs choic in the arena that weigh surviv against human and life against love. the world will be watching. scienc fiction adventur fantasi hallucin dystopia femal protagonist bow and arrow knife throw knife fight game archeri blind glamour roast pig sponsor chariot fiction tv show mine explo base on young adult novel jennif lawrenc josh hutcherson liam hemsworth gari ross',
      427: "the hangov crew head to thailand for stu' wedding. after the disast of a bachelor parti in la vega last year, stu is play it safe with a mellow pre-w brunch. however, noth goe as plan and bangkok is the perfect set for anoth adventur with the rowdi group. comedi sun glass interpol undercov cop hangov duringcreditsst bradley cooper ed helm zach galifianaki todd phillip",
      428: "have defeat the joker, batman now face the penguin - a warp and deform individu who is intent on be accept into gotham society. crook businessman max schreck is coerc into help him becom mayor of gotham and they both attempt to expo batman in a differ light. selina kyle, max' secretary, is thrown from the top of a build and is transform into catwoman - a mysteri figur who ha the same person disord as batman. batman must attempt to clear hi name, all the time decid just what must be done with the catwoman. action fantasi holiday corrupt doubl life dc comic crime fighter hallucin christma tree gotham citi vigil superhero violenc dark hero fiction citi super villain super power deform bird cage evil circu christma holiday michael keaton danni devito michel pfeiffer tim burton",
      429: 'a scheme raccoon fool a mismatch famili of forest creatur into help him repay a debt of food, by invad the new suburban sprawl that pop up while they were hibern – and learn a lesson about famili himself. comedi anim famili squirrel eat and drink vorort garden grizzli bear entrap suburbian idyl garbag forest turtl hide in a garbag contain skunk racoon anim bruce willi garri shandl steve carel karey kirkpatrick',
      430: 'a lone hawaiian girl name lilo is be rai by her older sister, nani, after their parent die -- under the watch of social worker cobra bubbles. when lilo adopt a funny-look dog and name him "stitch," she doesn\'t realiz her new best friend is a wacki alien creat by mad scientist dr. jumba. anim famili sister sister relationship extraterrestri technolog hawaii adopt mutat alien life-form alien phenomenon anim dog dead parent chri sander daveigh chase tia carrer chri sander',
      431: 'wilbur the pig is scare of the end of the season, becau he know that come that time, he will end up on the dinner table. he hatch a plan with charlotte, a spider that live in hi pen, to ensur that thi will never happen. comedi famili fantasi hero barn spider pig egg friendship spring uncl friend rescu surviv talk anim grass famili desk raincoat talk pig julia robert steve buscemi john clee gari winick',
      432: "a seven-mile-wid space rock is hurtl toward earth, threaten to oblit the planet. now, it' up to the presid of the unit state to save the world. he appoint a tough-as-nail veteran astronaut to lead a joint american-russian crew into space to destroy the comet befor impact. meanwhile, an enterpri report use her smart to uncov the scoop of the century. action drama romanc usa presid nasa metereologist space mission comet natur disast tsunami astronom astronaut woman director disast movi robert duval téa leoni elijah wood mimi leder",
      433: 'retir c.i.a. agent frank mose reunit hi unlik team of elit oper for a global quest to track down a miss portabl nuclear device. action comedi crime thriller pari london england cia russia mi6 hire killer explod airplan bruce willi catherin zeta-jon anthoni hopkin dean parisot',
      434: "pro quarter-back, paul crew and former colleg champion and coach, nate scarboro are do time in the same prison. ask to put togeth a team of inmat to take on the guards, crew enlist the help of scarboro to coach the inmat to victori in a footbal game 'fixed' to turn out quit anoth way. comedi drama prison american footbal prison blackmail supervisor sport adam sandler chri rock burt reynold peter segal",
      435: 'play around while aboard a crui ship, the chipmunk and chipett accid go overboard and end up maroon in a tropic paradise. they discov their new turf is not as desert as it seems. comedi fantasi famili music anim sequel chipmunk crui ship overboard jason lee david cross jenni slate mike mitchel',
      436: 'the all-star comedi cast from grown up return (with some excit new additions) for more summertim laughs. lenni (adam sandler) ha reloc hi famili back to the small town where he and hi friend grew up. thi time around, the grown up are the one learn lesson from their kid on a day notori full of surprises: the last day of school. comedi adam sandler kevin jame chri rock denni dugan',
      437: 'when the ident of secret agent from control are compromised, the chief promot hapless but eager analyst maxwel smart and team him with stylish, capabl agent 99, the onli spi whose cover remain intact. can they work togeth to thwart the evil plan of kao and it crafti operative? action comedi thriller danc spi terrorist traitor airplan violin base on tv seri leg steve carel ann hathaway dwayn johnson peter segal',
      438: "harri sanborn is an age music industri exec with a fond for younger women like marin, hi latest trophi girlfriend. thing get a littl awkward when harri suffer a heart attack at the home of marin' mother, erica. left in the care of erica and hi doctor, a love triangl start to take shape. drama comedi romanc age differ ladykil woman director jack nicholson dian keaton keanu reev nanci meyer",
      439: 'world war ii soldier-turned-u.s. marshal teddi daniel investig the disappear of a patient from a hospit for the crimin insane, but hi effort are compromi by hi troubl vision and also by a mysteri doctor. drama thriller mysteri base on novel island hurrican investig psychiatr hospit u.s. marshal conspiraci theori 1950 leonardo dicaprio mark ruffalo ben kingsley martin scors',
      440: 'brad and kate have made someth of an art form out of avoid their famili dure the holidays, but thi year their foolproof plan is about go bust -- big time. stuck at the citi airport after all depart flight are canceled, the coupl is embarrass to see their ruse expo to the world by an overz televi reporter. now, brad and kate are left with preciou littl choic other than to swallow their pride and suffer the rounds. comedi romanc drama holiday romant comedi dysfunct famili christma vinc vaughn ree witherspoon robert duval seth gordon',
      441: "rodney copperbottom is a young robot inventor who dream of make the world a better place, until the evil ratchet take over big weld industries. now, rodney' dream – and those of hi friend – are in danger of becom obsolete. anim comedi famili scienc fiction inventor busi man robot dishonesti robin william ewan mcgregor hall berri chri wedg",
      442: "an antiterror agent goe under the knife to acquir the like of a terrorist and gather detail about a bomb plot. when the terrorist escap custody, he undergo surgeri to look like the agent so he can get close to the agent' family. action crime scienc fiction thriller undercov mexican standoff biolog weapon face transplant rage and hate fistfight hostil reveng decept tragedi shootout hospit boat chase lo angel explo extrem violenc fbi agent prison escap crimin gang flashback golden gun arch villain bullet ballet john travolta nicola cage joan allen john woo",
      443: "skeeter bronson is a down-on-his-luck guy who' alway tell bedtim stori to hi niec and nephew. but hi life is turn upsid down when the fantast stori he make up for entertain inexpl turn into reality. can a bewild skeeter manag hi own unruli fantasi now that the outrag charact and situat from hi mind have morph into actual peopl and events? fantasi comedi famili romanc wish come true escapad disord imaginari miracul event imaginari kingdom life turn upsid down noth goe right adam sandler keri russel guy pearc adam shankman",
      444: 'mike sullivan work as a hit man for crime boss john rooney. sullivan view rooney as a father figure, howev after hi son is wit to a killing, mike sullivan find himself on the run in attempt to save the life of hi son and at the same time look for reveng on those who wrong him. thriller crime drama base on graphic novel homework shot in the chin soft boil egg learn to drive spoil son scar face thompson sub machin gun frost on a window cauter a wound liberti half dollar tom hank tyler hoechlin jennif jason leigh sam mend',
      445: "a plastic surgeon, romanc a much younger schoolteacher, enlist hi loyal assist to pretend to be hi soon to be ex-wife, in order to cover up a careless lie. when more lie backfire, the assistant' kid becom involved, and everyon head off for a weekend in hawaii that will chang all their lives. romanc comedi beach fictiti marriag blackmail plastic surgeri marriag love beauti woman kid and famili adam sandler jennif aniston nicol kidman denni dugan",
      446: 'when the govern put all it rotten crimin egg in one airborn basket, it\' ask for trouble. befor you can say, "pass the barf bag," the crook control the plane, led by creepi cyru "the virus" grissom. watch hi everi move is the just-relea cameron poe, who\'d rather reunit with hi family. action thriller crime prison ambush helicopt airport ga station undercov mexican standoff braveri hijack escap shootout u.s. marshal la vega explo brutal violenc convict desert war hero dea agent motorcycl chase nicola cage john cusack john malkovich simon west',
      447: "jerri shaw and rachel holloman are two stranger whose live are suddenli thrown into turmoil by a mysteri woman they have never met. threaten their live and family, the unseen caller use everyday technolog to control their action and push them into increa danger. as event escalate, jerri and rachel becom the country' most-want fugit and must figur out what is happen to them. mysteri thriller action artifici intellig washington d.c. secret ident hostag technolog fbi pentagon twin brother fbi agent shia labeouf michel monaghan rosario dawson d.j. caruso",
      448: "in thi classic stori of love and devot set against the backdrop of the american civil war, a wound confed soldier name w.p. inman desert hi unit and travel across the south, aim to return to hi young wife, ada, who he left behind to tend their farm. as inman make hi peril journey home, ada struggl to keep their home intact with the assist of ruby, a mysteri drifter sent to help her by a kindli neighbor. drama loss of lover loss of famili desert loss of father love of one' life jude law nicol kidman rené zellweg anthoni minghella",
      449: 'a post-apocalypt tale, in which a lone man fight hi way across america in order to protect a sacr book that hold the secret to save humankind. action thriller scienc fiction book post-apocalypt dystopia faith blind denzel washington gari oldman mila kuni albert hugh',
      450: "professor phillip brainard, an absent mind professor, work with hi assist weebo, tri to creat a substanc that' a new sourc of energi and that will save medfield colleg where hi sweetheart sara is the president. he ha miss hi wed twice, and on the afternoon of hi third wedding, professor brainard creat flubber, which allow object to fli through the air. comedi famili scienc fiction wed vow inventor slime green flight mad scientist wed robin william marcia gay harden christoph mcdonald le mayfield",
      451: 'dr. david marrow invit nell vance, and theo and luke sanderson to the eeri and isol hill hou to be subject for a sleep disord study. the unfortun guest discov that marrow is far more interest in the sinist mansion itself – and they soon see the true natur of it horror. horror thriller fantasi mysteri base on novel trauma castl haunt hou insomnia bone poster paint remak haunt child labor audio record spiral stairca evil loner research insomniac paranorm activ logbook strang noi spook cherub liam neeson catherin zeta-jon owen wilson jan de bont',
      452: 'in a desper attempt to win a basketb match and earn their freedom, the looney tune seek the aid of retir basketb champion, michael jordan. anim comedi drama famili fantasi sport basketb doctor basketb team basketb game refer basketb court tweeti bird speedi gonzal cartoon chicken sylvest the cat cartoon realiti crossov basketb hoop cartoon skunk michael jordan wayn knight billi west joe pytka',
      453: 'when the coach of the franc soccer team is kill by a poison dart in the stadium in the end of a game, and hi expen and huge ring with the diamond pink panther disappears, the ambiti chief inspector dreyfu assign the worst polic inspector jacqu clouseau to the case. action comedi crime mysteri famili robberi investig inspector killer clouseau pink panther murder hunt steve martin kevin kline jean reno shawn levi',
      454: 'a repr of an alien race that went through drastic evolut to surviv it own climat change, klaatu come to earth to assess whether human can prevent the environ damag they have inflict on their own planet. when bar from speak to the unit nations, he decid humankind shall be extermin so the planet can survive. drama scienc fiction thriller extraterrestri technolog spacecraft ultimatum evacu panic govern remak ufo alien end of the world giant robot tank social commentari power outag interrog environ threat alien contact central park messeng nanobot disintegr keanu reev jennif connelli kathi bate scott derrickson',
      455: 'a man obsess with conspiraci theori becom a target after one of hi theori turn out to be true. unfortunately, in order to save himself, he ha to figur out which theori it is. action drama mysteri thriller new york cia helicopt assassin secret obsess taxi driver fbi paranoia wheelchair chase theori polit govern control cover-up murder suspen conspiraci tortur flashback target geronimo newslett mel gibson julia robert patrick stewart richard donner',
      456: 'last month of world war ii in april 1945. as the alli make their final push in the european theater, a battle-harden u.s. armi sergeant in the 2nd armor divi name wardaddi command a sherman tank call "fury" and it five-man crew on a deadli mission behind enemi lines. outnumb and outgunned, wardaddi and hi men face overwhelm odd in their heroic attempt to strike at the heart of nazi germany. war drama action world war ii nazi war nazi germani panzer tank brad pitt shia labeouf logan lerman david ayer',
      457: "when quinn, a grouchi pilot live the good life in the south pacific, agr to transfer a savvi fashion editor, robin, to tahiti, he end up strand on a desert island with her after their plane crashes. the pair avoid each other at first, until they'r forc to team up to escap from the island -- and some pirat who want their heads. action adventur comedi romanc overleven famili guy harrison ford ann hech david schwimmer ivan reitman",
      458: 'jellyston park ha been lose business, so greedi mayor brown decid to shut it down and sell the land. that mean famili will no longer be abl to experi the natur beauti of the outdoor -- and, even worse, yogi and boo boo will be toss out of the onli home they\'v ever known. face with hi biggest challeng ever, yogi must prove that he realli is "smarter than the averag bear" as he and boo boo join forc with their old nemesi ranger smith to find a way to save jellyston park from close forever. comedi famili anim adventur picnic sandwich bear 3d yogi dan aykroyd justin timberlak anna fari eric brevig',
      459: 'as a wild stallion travel across the frontier of the old west, he befriend a young human and find true love with a mare. western anim adventur comedi famili human be freedom mustang rivalri wildlif anim cavalri indian war eyebrow wild hor matt damon jame cromwel daniel studi kelli asburi',
      460: "a comedi about a zookeep who might be great with animals, but he doesn't know anyth about the bird and the bees. the man can't find love, so he decid to quit hi job at the zoo, but hi anim friend tri to stop him and teach him that mother natur know best when it come to love. comedi romanc famili talk anim scientist german accent ostrich monkey bullfrog car dealership duringcreditsst kevin jame rosario dawson sylvest stallon frank coraci",
      461: 'the prospect for continu life on earth in the year 2058 are grim. so the robinson are launch into space to colon alpha prime, the onli other inhabit planet in the galaxy. but when a stowaway sabotag the mission, the robinson find themselv hurtl through unchart space. adventur famili scienc fiction time travel sabotag deep space explor gari oldman william hurt matt leblanc stephen hopkin',
      462: "when hi armi unit wa ambush dure the first gulf war, sergeant raymond shaw save hi fellow soldier just as hi command officer, then-captain ben marco, wa knock unconscious. broker the incid for polit capital, shaw eventu becom a vice-presidenti nominee, while marco is haunt by dream of what happen -- or didn't happen -- in kuwait. as marco (now a major) investigates, the stori begin to unravel, to the point where he question if it happen at all. is it possibl the entir unit wa kidnap and brainwash to believ shaw is a war hero as part of a plot to seiz the white house? some veri power peopl at manchurian global corpor appear desper to stop him from find out. drama thriller mysteri senat gulf war cano kuwait conspiraci war hero u.s. congress implant denzel washington meryl streep liev schreiber jonathan demm",
      463: 'l.a. shop owner dana and englishman sean meet and fall in love at first sight, but sean is marri and dana is to marri her busi partner alex. romanc drama love american pin stranger rubi stephen dillan victoria foyt vanessa redgrav henri jaglom',
      464: 'when the old-old-old-fashion vampir vlad arriv at the hotel for an impromptu famili get-together, hotel transylvania is in for a colli of supernatur old-school and modern day cool. anim comedi famili transylvania hotel witch technolog magic mummi dracula skeleton onli child backpack marriag frankenstein wolfman zombi move out invi man new life adam sandler andi samberg selena gomez genndi tartakovski',
      465: "blend live music and brilliant animation, thi sequel to the origin 'fantasia' restor 'the sorcerer' apprentice' and add seven new shorts. anim famili music orchestra music segment steve martin itzhak perlman quinci jone jame algar",
      466: 'hope to alter the event of the past, a 19th centuri inventor instead travel 800,000 year into the future, where he find humankind divid into two war races. scienc fiction adventur action futur time machin guy pearc mark addi phyllida law simon well',
      467: "as a child live in africa, jill young saw her mother kill while protect wild gorilla from poacher led by andrei strasser. now an adult, jill care for an orphan gorilla name joe -- who, due to a genet anomaly, is 15 feet tall. when gregg o'hara arriv from california and see the animal, he convinc jill that joe would be safest at hi wildlif refuge. but strasser follow them to the u.s., intent on captur joe for himself. action adventur famili fantasi gorilla die and death charliz theron rade serbedzija bill paxton ron underwood",
      468: "rogu agent gabriel shear is determin to get hi mitt on $9 billion stash in a secret drug enforc administr account. he want the cash to fight terrorism, but lack the comput skill necessari to hack into the govern mainframe. enter stanley jobson, a n'er-do-wel encrypt expert who can log into anything. action crime thriller femal nuditi hacker terror violenc ex-con wire lo angel intern airport (lax) misdirect aftercreditsst john travolta hugh jackman hall berri domin sena",
      469: "have spent the last 10 year fight injust and cruelty, alejandro de la vega is now face hi greatest challenge: hi love wife elena ha thrown him out of the house! elena ha file for divorc and found comfort in the arm of count armand, a dash french aristocrat. but alejandro know someth she doesn't: armand is the evil mastermind behind a terrorist plot to destroy the unit states. and so, with hi marriag and the county' futur at stake, it' up to zorro to save two union befor it' too late. action adventur california spi father son relationship mexico hero marriag crisi sword fight divorc american civil war antonio bandera catherin zeta-jon adrián alonso barona martin campbel",
      470: 'chri neilson die to find himself in a heaven more amaz than he could have ever dream of. there is one thing missing: hi wife. after he dies, hi wife, anni kill herself and went to hell. chri decid to risk etern in hade for the small chanc that he will be abl to bring her back to heaven. drama fantasi romanc paradi soul underworld heaven paint hell afterlif spirit robin william cuba good jr. annabella sciorra vincent ward',
      471: 'after the lord of dark decid he will not cede hi thrown to ani of hi three sons, the two most power of them escap to earth to creat a kingdom for themselves. thi action close the portal filter sin soul to hell and cau satan to wither away. he must send hi most weak but belov son, littl nicky, to earth to return hi brother to hell. comedi fantasi romanc father son relationship brother sister relationship mephisto bulldogg adam sandler patricia arquett harvey keitel steven brill',
      472: 'folklor collector and con artists, jake and will grimm, travel from villag to villag pretend to protect townsfolk from enchant creatur and perform exorcisms. however, they are put to the test when they encount a real magic cur in a haunt forest with real magic beings, requir genuin courage. adventur fantasi action comedi thriller brother brother relationship literatur aftercreditsst heath ledger matt damon mackenzi crook terri gilliam',
      473: "'we come in peace' is not what those green men from mar mean when they invad our planet, arm with irresist weapon and a cruel sen of humor. thi star stud cast must play victim to the alien’ fun and game in thi comedi homag to scienc fiction film of the '50 and '60s. comedi fantasi scienc fiction save the world total destruct white hou mar usa presid cataclysm lasergun ambassador congress pest fli saucer jack nicholson glenn close annett bene tim burton",
      474: '11-year-old nicola live with hi mother in a seasid hou estate. the onli place that ever see ani activ is the hospital. it is there that all the boy from the villag are forc to undergo strang medic trial that attempt to disrupt the phase of evolution. mysteri drama horror nur sea beach boy pregnant blood woman director max brebant roxan duran julie-mari parmenti lucil hadzihalilov',
      475: 'the plane carri wealthi charl mor crash down in the alaskan wilderness. togeth with the two other passengers, photograph robert and assist stephen, charl devi a plan to help them reach civilization. however, hi biggest obstacl might not be the elements, or even the kodiak bear stalk them -- it could be robert, whom charl suspect is have an affair with hi wife and would not mind see him dead. action adventur drama photograph grizzli bear wilder airplan supermodel emerg land suspen surviv bear anim horror alec baldwin anthoni hopkin ell macpherson lee tamahori',
      476: "set in a futurist world where human live in isol and interact through surrog robots, a cop is forc to leav hi home for the first time in year in order to investig the murder of others' surrogates. action scienc fiction thriller clone dystopia bruce willi radha mitchel rosamund pike jonathan mostow",
      477: 'dramati of the cuban missil crisis, the nuclear standoff with the ussr spark by the discoveri by the american of missl base establish on the soviet alli island of cuba. shown from the perspect of the us president, john f kennedy, hi staff and advisors. drama thriller usa presid atom bomb john f. kennedi kubakri threat kevin costner bruce greenwood steven culp roger donaldson',
      478: 'a group of arm robber flee the polic head for the new jersey tunnel and run right into truck transport toxic waste. the spectacular explo that follow result in both end of the tunnel collap and the hand of peopl who surviv the explo are now in peril. kit latura is the onli man with the skill and knowledg to lead the band of survivor out of the tunnel befor the structur collapses. action adventur thriller taxi new jersey helicopt river hero taxi driver race against time guard surviv disast new york citi explo power outag dog trap flood tunnel christma trap underground action hero sylvest stallon ami brenneman viggo mortensen rob cohen',
      479: 'walk with dinosaur 3d is a film depict life-lik 3d dinosaur charact set in photo-r landscap that transport audienc to the prehistor world as it exist 70 million year ago. the film is base on the 1999 documentari televi miniseri walk with dinosaurs, produc by the bbc. walk with dinosaur 3d is be produc by evergreen studios, the compani that produc happi feet, and it is wa relea on octob 11, 2013. anim famili adventur dinosaur 3d charli row justin long karl urban barri cook',
      480: 'in the year 3000, man is no match for the psychlos, a greedy, manipul race of alien on a quest for ultim profit. led by the power terl, the psychlo are strip earth clean of it natur resources, use the broken remnant of human as slaves. what is left of the human race ha descend into a near primit state. after be captured, it is up to tyler to save mankind. action scienc fiction war base on novel post-apocalypt dystopia mine fighter jet alien inva scientolog cavemen bureaucrat citi ruin john travolta barri pepper forest whitak roger christian',
      481: 'bug bunni and daffi duck are up to their feud way again. tire of play second fiddl to bugs, daffi ha decid to leav the studio for good. he is aid by warner bros.\' humor impair vice presid of comedy, kate houghton, who relea him from hi contract and instruct wb secur guard/aspir stunt man dj drake to captur and "escort" daffi off the studio lot. anim comedi famili spi duck bunni wretch film industri live action and anim brendan fraser jenna elfman steve martin joe dant',
      482: 'arrogant, self-cent movi director guido contini find himself struggl to find meaning, purpose, and a script for hi latest film endeavor. with onli a week left befor shoot begins, he desper search for answer and inspir from hi wife, hi mistress, hi muse, and hi mother. drama music romanc memori sidewalk cafe room key drive a car coastlin stairway search for mean sequin sing photograph slide down a pole costum design duringcreditsst 1960 judi dench daniel day-lewi marion cotillard rob marshal',
      483: "a group of archaeolog student becom trap in the past when they go there to retriev their professor. the group must surviv in 14th centuri franc long enough to be rescued. action adventur scienc fiction professor time travel quantum mechan hundr years' war excav la roqu knight mediev time paul walker franc o'connor gerard butler richard donner",
      484: 'in 2013 there are no highways, no i-ways, no dream of a better tomorrow, onli scatter survivor across what wa onc the unit states. into thi apocalypt wasteland come an enigmat drifter with a mule, a knack for shakespear and someth yet undiscovered: the power to inspir hope. drama adventur usa post postman armi apocalyp kevin costner will patton olivia william kevin costner',
      485: "babe, fresh from hi victori in the sheepherd contest, return to farmer hoggett' farm, but after farmer hoggett is injur and unabl to work, babe ha to go to the big citi to save the farm. adventur comedi drama famili fantasi piggi bank shortag of money pig farm piglet talk anim talk dog dog chimpanz talk pig jame cromwel mari stein mickey rooney georg miller",
      486: 'the modern world hold mani secrets, but by far the most astound is that witch still live among us; viciou supernatur creatur intent on unleash the black death upon the world and put an end to the human race onc and for all. armi of witch hunter have battl thi unnatur enemi for centuries, includ kaulder, a valiant warrior who mani year ago slay the all-pow witch queen, decim her follow in the process. in the moment right befor her death, the queen cur kaulder with immortality, forev separ him from hi belov wife and daughter. today, kaulder is the last live hunter who ha spent hi immort life track down rogu witches, all the while yearn for hi long-lost family. fantasi action adventur new york witch upri witch hunter vin diesel rose lesli elijah wood breck eisner',
      487: 'astronaut search for solut to save a die earth by search on mars, onli to have the mission go terribl awry. thriller action scienc fiction mar futur astronaut scienc catastroph val kilmer carrie-ann moss benjamin bratt antoni hoffman',
      488: "arthur is a spirit ten-year old whose parent are away look for work, whose eccentr grandfath ha been miss for sever years, and who live with hi grandmoth in a countri hou that, in two days, will be repossessed, torn down, and turn into a block of flat unless arthur' grandfath return to sign some paper and pay off the famili debt. arthur discov that the key to success lie in hi own descent into the land of the minimoys, creatur no larger than a tooth, whom hi grandfath help reloc to their garden. somewh among them is hidden a pile of rubies, too. can arthur be of stout heart and save the day? romanc beckon as well, and a villain lurks. adventur fantasi anim famili grandfath grandson relationship wretch treasur hunt disappear famili fantasi world freddi highmor mia farrow ron crawford luc besson",
      489: 'an ecolog drama/documentary, film throughout the globe. part thriller, part medit on the vanish wonder of the sub-aquat world. documentari famili ocean sea fish whale duringcreditsst pierc brosnan jacqu perrin rie miyazawa jacqu perrin',
      490: 'when a hunter sent back to the prehistor era run off the path he must not leave, he cau a chain reaction that alter histori in disastr ways. thriller scienc fiction adventur action die and death time travel romanc dinosaur heik makatsch armin rohd david oyelowo peter hyam',
      491: 'set in 79 a.d., pompeii tell the epic stori of milo, a slave turn invinc gladiat who find himself in a race against time to save hi true love cassia, the beauti daughter of a wealthi merchant who ha been unwillingli betroth to a corrupt roman senator. as mount vesuviu erupt in a torrent of blaze lava, milo must fight hi way out of the arena in order to save hi belov as the onc magnif pompeii crumbl around him. action adventur histori romanc drama gladiat arena gladiat fight lava roman forbidden love natur disast epic disast slave town in panic vulcan volcan erupt pompeii 3d kit harington carrie-ann moss emili brown paul w.s. anderson',
      492: 'top cat ha arriv to charm hi way into your hearts! ever wonder how thi scheme felin got hi start? well top cat begin reveal the origin of everyth you know and love about thi classic comedi hero. what follow is an adventur so crazi that it ha to be seen to be believed! comedi anim 3d jason harri david hoffman bill lobley andré couturi',
      493: "at princeton university, john nash struggl to make a worthwhil contribut to serv as hi legaci to the world of mathematics. he final make a revolutionari breakthrough that will eventu earn him the nobel prize. after graduat school he turn to teaching, becom romant involv with hi student alicia. meanwhil the govern ask hi help with break soviet codes, which soon get him involv in a terrifi conspiraci plot. nash grow more and more paranoid until a discoveri that turn hi entir world upsid down. now it is onli with alicia' help that he will be abl to recov hi mental strength and regain hi statu as the great mathematician we know him as today.. drama romanc individu schizophrenia massachusett love of one' life intellig mathematician market economi econom theori princeton univ nobel prize mathemat theorem m.i.t. mathemat delu russel crow ed harri jennif connelli ron howard",
      494: "a young lion cub name simba can't wait to be king. but hi uncl crave the titl for himself and will stop at noth to get it. famili anim drama loss of parent wild boar uncl shaman redempt king scar hyena meerkat jonathan taylor thoma matthew broderick jame earl jone roger aller",
      495: "sean anderson partner with hi mom' boyfriend on a mission to find hi grandfather, who is thought to be miss on a mythic island. adventur action scienc fiction mission mysteri island miss person duringcreditsst 3d dwayn johnson josh hutcherson kristin davi brad peyton",
      496: 'after the disastr food storm in the first film, flint and hi friend are forc to leav the town. flint accept the invit from hi idol chester v to join the live corp company, which ha been task to clean the island, and where the best inventor in the world creat technolog for the better of mankind. when flint discov that hi machin still oper and now creat mutant food beast like live pickles, hungri tacodiles, shrimpanz and appl pie-thons, he and hi friend must return to save the world. anim famili comedi inventor food scientist bill hader anna fari jame caan codi cameron',
      497: "former fbi agent will graham, who wa onc almost kill by the savag hannib 'the cannibal' lecter, now ha no choic but to face him again, as it seem lecter is the onli one who can help graham track down a new serial killer. crime thriller horror psychopath serial killer fbi agent anthoni hopkin edward norton ralph fienn brett ratner",
      498: 'set in 1890, thi is the stori of a poni express courier who travel to arabia to compet with hi horse, hidalgo, in a danger race for a massiv contest prize, in an adventur that send the pair around the world... western adventur hor race hor racehor viggo mortensen zuleikha robinson omar sharif joe johnston',
      499: "jack sadelstein, a success adverti execut in lo angel with a beauti wife and kids, dread one event each year: the thanksgiv visit of hi twin sister jill. jill' needi and passive-aggress is madden to jack, turn hi normal tranquil life upsid down. comedi duringcreditsst adam sandler kati holm al pacino denni dugan",
      500: 'it\' a major double-cross when former polic offic brian o\'conn team up with hi ex-con buddi roman pearc to transport a shipment of "dirty" money for shadi miami-ba import-export dealer carter verone. but the guy are actual work with undercov agent monica fuent to bring veron down. action crime thriller miami car race sport car lo angel car automobil race paul walker tyre gibson eva mend john singleton',
      501: "base on the best-sel book 'the littl prince', the movi tell the stori of a littl girl that live with resign in a world where effici and work are the onli dogmas. everyth will chang when accid she discov her neighbor that will tell her about the stori of the littl princ that he onc met. adventur anim fantasi philosophi utopia airplan adventur dystopia littl boy grow up neighbor mother daughter relationship school old man littl girl crazi base on children' book stori social differ 3d jeff bridg rachel mcadam paul rudd mark osborn",
      502: 'washington, d.c. psychologist carol bennel and her colleagu dr. ben driscol are the onli two peopl on earth who are awar of an epidem run rampant through the city. they discov an alien viru aboard a crash space shuttl that transform anyon who come into contact with it into unfeel drone while they sleep. carol realiz her son hold the key to stop the spread of the plagu and she race to find him befor it is too late. scienc fiction thriller remak alien escap alien inva alien infect sleep doppelgang news report text messag siren contamin nicol kidman daniel craig jeremi northam oliv hirschbiegel',
      503: 'rocki and bullwinkl have been live off the financ made from the rerun of their cartoon show. bori and natasha somehow manag to crossov into realiti and team up with fearless leader, an evil crimin turn media mogul with some evil plan up hi sleeve. rocki and bullwinkl must stop the three of them befor they wreak havoc. action adventur anim comedi famili adventur cartoon comedi break the fourth wall talk to the camera road movi celebr cameo rene russo jason alexand piper perabo de mcanuff',
      504: 'the quiet life of a terrier name max is upend when hi owner take in duke, a stray whom max instantli dislikes. anim famili pet bunni anthropomorph dog anim apart build sewer terrier manhattan, new york citi rodent mongrel loui c.k. eric stonestreet kevin hart chri renaud',
      505: 'to prevent a world war from break out, famou charact from victorian literatur band togeth to do battl against a cun villain. fantasi action thriller scienc fiction save the world vampir bite men invi man captain nemo allan quatermain venezia immort sean conneri peta wilson shane west stephen norrington',
      506: 'gru is recruit by the anti-villain leagu to help deal with a power new super criminal. anim comedi famili secret agent bakeri fall in love father daughter relationship duringcreditsst first date minion 3d steve carel kristen wiig benjamin bratt pierr coffin',
      507: "on juli 2, a giant alien mothership enter orbit around earth and deploy sever dozen saucer-shap 'destroyer' spacecraft that quickli lay wast to major citi around the planet. on juli 3, the unit state conduct a coordin counterattack that fails. on juli 4, a plan is devi to gain access to the interior of the alien mothership in space, in order to plant a nuclear missile. action adventur scienc fiction spacecraft patriot countdown independ inva war ufo extraterrestri spaceship alien battl will smith bill pullman jeff goldblum roland emmerich",
      508: "four year after jurass park' genet bred dinosaur ran amok, multimillionair john hammond shock chao theorist ian malcolm by reveal that hammond ha been breed more beasti at a secret location. malcolm, hi paleontologist ladylov and a wildlif videograph join an expedit to document the lethal lizards' natur behavior in thi action-pack thriller. adventur action scienc fiction exot island dna paleontolog tyrannosauru rex velociraptor san diego dinosaur jurass park anim horror jeff goldblum juliann moor pete postlethwait steven spielberg",
      509: 'zoo anim leav the comfort of man-mad habitat for exot adventur in thi anim famili film. after escap from the zoo, four friend -- a lion, a hippo, a zebra and a giraff -- are sent back to africa. when their ship capsizes, strand them on madagascar, an island popul by crazi critters, the pal must adapt to jungl life and their new role as wild animals. famili anim lion hippopotamu giraff penguin zebra ben stiller chri rock david schwimmer eric darnel',
      510: "in 2027, in a chaotic world in which human can no longer procreate, a former activist agr to help transport a miracul pregnant woman to a sanctuari at sea, where her child' birth may help scientist save the futur of humankind. drama action thriller scienc fiction polic state hippi rebel miracl futur dystopia chao age childless faith surviv birth die clive owen michael cain juliann moor alfonso cuarón",
      511: 'two mutants, rogu and wolverine, come to a privat academi for their kind whose resid superhero team, the x-men, must oppo a terrorist organ with similar powers. adventur action scienc fiction mutant marvel comic superhero base on comic book superhuman patrick stewart hugh jackman ian mckellen bryan singer',
      512: 'doormat wesley gibson discov that hi recent murder father – who wesley never knew – belong to a secret guild of assassins. after a leather-clad sexpot draft wesley into the society, he hone hi innat kill skill and turn avenger. action thriller crime assassin loss of father secret societi mission of murder reveng angelina joli jame mcavoy morgan freeman timur bekmambetov',
      513: 'a group of renegad marin commando seiz a stockpil of chemic weapon and take over alcatraz, with 81 tourist as hostages. their leader demand $100 million to be paid, as restitut to famili of marin who die in covert op – or he will launch 15 rocket carri deadli vx ga into the san francisco bay area. action adventur thriller san francisco fbi ga attack alcatraz hostag situat fbi agent sean conneri nicola cage ed harri michael bay',
      514: "diego, manni and sid return in thi sequel to the hit anim movi ice age. thi time around, the deep freez is over, and the ice-cov earth is start to melt, which will destroy the trio' cherish valley. the impend disast prompt them to reunit and warn all the other beast about the desper situation. anim famili comedi adventur mammoth sloth ice age barrier ice ice melt iceberg flood adventur lover delug saber-tooth tiger ray romano john leguizamo deni leari carlo saldanha",
      515: "henri is a player skill at seduc women. but when thi veterinarian meet lucy, a girl with a quirki problem when it come to total recall, he realiz it' possibl to fall in love all over again…and again, and again. that' becau the delight luci ha no short-term memory, so henri must woo her day after day until he final sweep her off her feet. comedi romanc deja vu amnesia hawaii ladykil romant comedi adam sandler drew barrymor rob schneider peter segal",
      516: 'pleasantli plump teenager, traci turnblad and her best friend, penni pingleton audit to be on the corni collin show – and traci wins. but when scheme amber von tussl and her mother plot to destroy tracy, it turn to chaos. famili comedi music romanc race dream danc televi tv show race polit colour music equal school parti perform integr overweight woman duel base on stage music xenophobia base on film 1960 john travolta michel pfeiffer christoph walken adam shankman',
      517: "have live through traumat event dure wwii, father lankest merrin take a sabbat from the church to conduct archaeolog excav in british-administ east africa. merrin unearth an ancient byzantin church believ have been built and then immedi buri to keep down evil from the crypt below. the nativ are convinc that uncov the church ha unleash a demon, and begin to violent clash with the british militari troops. as the villag rapidli disintegr into chao and war, merrin must face-off with the demon which ha taken possess of somebodi close to him. horror mysteri thriller secret obsess exorc remak priest good vs evil pagan devil archaeologist demon possess relic crisi of faith archaeolog dig stellan skarsgård izabella scorupco jame d'arci renni harlin",
      518: 'john brown is a bumbl but well-int secur guard who is badli injur in an explo plan by an evil mastermind. he is taken to a laboratory, where brenda, a lead robot surgeon, replac hi damag limb with state-of-the-art gadget and tools. name "inspector gadget" by the press, john -- along with hi niece, penny, and her trusti dog, brain -- use hi new power to discov who wa behind the explosion. action adventur comedi famili gadget matthew broderick rupert everett joeli fisher david kellogg',
      519: 'an fbi agent and an interpol detect track a team of illusionist who pull off bank heist dure their perform and reward their audienc with the money. thriller crime pari bank secret fbi vault magic new orlean investig heist conspiraci money escap new york citi la vega explo jess eisenberg mark ruffalo woodi harrelson loui leterri',
      520: 'after their high school basketb coach pass away, five good friend and former teammat reunit for a fourth of juli holiday weekend. comedi overweight swing foot convert arrow adam sandler salma hayek maria bello denni dugan',
      521: "viktor navorski is a man without a country; hi plane took off just as a coup d'etat explod in hi homeland, leav it in shambles, and now he' strand at kennedi airport, where he' hold a passport that nobodi recognizes. while quarantin in the transit loung until author can figur out what to do with him, viktor simpli goe on live – and court romanc with a beauti flight attendant. comedi drama new york airport marriag propo translat craftsman stewardess illeg immigr languag barrier jfk intern airport immigr law fast food restaur secur camera jazz musician saxophonist autograph passport eastern europ friendship tom hank catherin zeta-jon stanley tucci steven spielberg",
      522: "place in a foster home that doesn't allow pets, 16-year-old andi and her younger brother, bruce, turn an abandon hotel into a home for their dog. soon other stray arrive, and the hotel becom a haven for everi orphan canin in town. but the kid have to do some quick think to keep the cop off their tails. comedi famili adopt puppi pitbul orphan foster home anim lover beagl duringcreditsst emma robert jake t. austin don cheadl thor freudenth",
      523: "trap near the summit of k2, the world' second-highest mountain, anni garrett radio to base camp for help. brother peter hear annie' messag and assembl a team to save her and her group befor they succumb to k2' unforgiv elements. but, as anni lay injur in an ici cavern, the rescuer face sever terrifi event that could end the rescu attempt -- and their lives. action adventur thriller himalaya pakistan climb k2 mountain karakoram chri o'donnel robin tunney bill paxton martin campbel",
      524: "the true stori of texa congressman charli wilson' covert deal in afghanistan, where hi effort to assist rebel in their war with the soviet had some unforeseen and long-reach effects. comedi drama histori washington d.c. alcohol cia helicopt refug camp congress cold war ladykil rocket launcher russian munit war in afghanistan dollar tom hank philip seymour hoffman julia robert mike nichol",
      525: "oscar is a small fish whose big aspir often get him into trouble. meanwhile, lenni is a great white shark with a surpri secret that no sea creatur would guess: he' a vegetarian. when a lie turn oscar into an improb hero and lenni becom an outcast, the two form an unlik friendship. anim action comedi famili fish hero mission of murder threat to death secret love anim shark woman director will smith robert de niro rené zellweg vicki jenson",
      526: "three young women – deena jones, effi white and lorrel robinson – dream of becom pop star and they get their wish when they'r chosen to be backup singer for the legendari jame 'thunder' early. drama music record manag black peopl adulteri soul show busi drug addict oscar award music deceiv wife record contract background singer motown the suprem record produc singl singer sing detroit alcohol extramarit affair music band jami foxx beyoncé knowl eddi murphi bill condon",
      527: 'disench with the movi industry, chili palmer tri the music industry, meet and romanc a widow of a music exec on the way. comedi crime baseb bat widow record contract record studio russian mafia music busi night club pawnshop john travolta uma thurman vinc vaughn f. gari gray',
      528: 'dure the 1972 olymp game in munich, eleven isra athlet are taken hostag and murder by a palestinian terrorist group known as black september. in retaliation, the isra govern recruit a group of mossad agent to track down and execut those respon for the attack. drama action histori thriller pari assassin israel hotel room 1970 hostag intellig olymp game munich mossad isra palestinian beirut ailul al aswad plo bomb constructor baader-meinhof group olympian villag reveng eric bana daniel craig ciarán hind steven spielberg',
      529: 'navi seal lieuten a.k. water and hi elit squadron of tactic specialist are forc to choo between their duti and their humanity, between follow order by ignor the conflict that surround them, or find the courag to follow their conscienc and protect a group of innoc refugees. when the democrat govern of nigeria collap and the countri is taken over by a ruthless militari dictator, waters, a fierc loyal and harden veteran is dispatch on a routin mission to retriev a doctor without border physician. action drama war u.s. armi nigeria presid bruce willi monica bellucci cole hauser antoin fuqua',
      530: 'when an elit assassin marri a beauti comput whiz after a whirlwind romance, he give up the gun and settl down with hi new bride. that is, until he learn that someon from hi past ha put a contract out on hi life. action comedi thriller romanc assassin katherin heigl ashton kutcher tom selleck robert luket',
      531: "at the height of the cold war, a mysteri crimin organ plan to use nuclear weapon and technolog to upset the fragil balanc of power between the unit state and soviet union. cia agent napoleon solo and kgb agent illya kuryakin are forc to put asid their hostil and work togeth to stop the evildo in their tracks. the duo' onli lead is the daughter of a miss german scientist, whom they must find soon to prevent a global catastrophe. comedi action adventur spi cold war remak base on tv seri buddi cop russian spi american spi henri cavil armi hammer alicia vikand guy ritchi",
      532: "mexican immigr and singl mother flor moreno find housekeep work with deborah and john clasky, a well-off coupl with two children of their own. when flor admit she can't handl the schedul becau of her daughter, cristina, deborah decid they should move into the claski home. cultur clash and tension run high as flor and the claski struggl to share space while rai their children on their own, and veri different, terms. comedi upper class mother singl parent parent kid relationship wife husband relationship cook milieu illeg immigr immigr languag barrier family' daili life platon love deceiv husband class societi hysteria biographi unit states–mexico barrier relationship problem class languag cour singl mother daughter relationship american mexican father figur adam sandler téa leoni paz vega jame l. brook",
      533: 'monster under the bed are scari enough, but what happen when an entir hou is out to get you? three teen aim to find out when they go up against a decrepit neighbor home and unlock it frighten secrets. anim comedi famili fantasi monster secret toy children neighbor mission child ryan newman steve buscemi mitchel musso gil kenan',
      534: "two bank robber fall in love with the girl they'v kidnapped. action comedi crime romanc prison bruce willi billi bob thornton cate blanchett barri levinson",
      535: 'the timeless tale of king arthur and the legend of camelot are retold in thi passion period drama. arthur is reluct to hand the crown to lancelot, and guinev is torn between her loyalti to her husband and her grow love for hi rival. but lancelot must balanc hi loyalti to the throne with the reward of true love. action adventur drama romanc camelot knight king arthur excalibur knight of the round tabl sean conneri richard gere julia ormond jerri zucker',
      536: "the stori of the romanc between the king of siam (now thailand) and the widow british school teacher anna leonowen dure the 1860's. anna teach the children and becom romanc by the king. she convinc him that a man can be love by just one woman. drama histori romanc civil war father son relationship east india trade compani traitor death penalti thailand palac burma daughter royalti teacher battl denunci jodi foster chow yun-fat bai ling andi tennant",
      537: 'theseu is a mortal man chosen by zeu to lead the fight against the ruthless king hyperion, who is on a rampag across greec to obtain a weapon that can destroy humanity. fantasi action drama poison armi zeu poseidon spear mickey rourk kellan lutz isabel luca tarsem singh',
      538: 'when a mafia account is taken hostag on hi beat, a polic offic – wrack by guilt from a prior stint as a negoti – must negoti the standoff, even as hi own famili is held captiv by the mob. mysteri drama thriller crime fbi kidnap polic oper home inva hostag situat hostag negoti bruce willi kevin pollak jimmi bennett florent-emilio siri',
      539: "a young man find out that he hold the key to restor hope and ensur surviv for the human race, while an alien speci call the dredg are bent on mankind' destruction. anim action scienc fiction famili adventur monster galaxi dystopia space alien anim mission matt damon bill pullman drew barrymor gari goldman",
      540: 'joe gavilan (harrison ford) and hi new partner k. c. calden (josh hartnett), are detect on the beat in tinseltown. neither one of them realli want to be a cop, gavilan moonlight as a real estat broker, and calden is an aspir actor moonlight as a yoga instructor. when the two are assign a big case they must work out whether they want to solv the case or follow their hearts. action adventur comedi thriller rap music hitman harrison ford josh hartnett lena olin ron shelton',
      541: 'sergeant todd is a veteran soldier for an elit group of the arm forces. after be defeat by a new breed of genet engin soldiers, he is dump on a wast planet and left for dead. he soon interact with a group of crash survivor who lead out a peac existence. the peac is broken as the new soldier land on the planet to elimin the colony, which sergeant todd must defend. action war scienc fiction space marin dystopia alien planet genet engin kurt russel jason scott lee jason isaac paul w.s. anderson',
      542: 'four friend flee a viral pandem soon learn they are more danger than ani virus.a deadli viru ha spread across the globe. contagion is everywhere, no one is safe and no one can be trusted. four young attract peopl race through the back road of the american west to the pound beat of a vacat soundtrack. their aim is to retreat to seclud utopian beach in the gulf of mexico, where they could peac wait out the pandem and surviv the apocalypt disease. their plan take a grim turn when their car break down on an isol road start a chain of event that will seal the fate of each of them in an inexor and horrifi voyag of hell through a western landscap popul by onli the hideou dead or the twist living. action drama horror scienc fiction thriller beach desper infect surviv biohazard disea trust viru pandem lou taylor pucci chri pine piper perabo àlex pastor',
      543: "after a car crash send repress cartoonist stu miley (fraser) into a coma, he and the mischiev monkeybone, hi hilari horni alter-ego, wake up in a wacked-out waystat for lost souls. when monkeybon take over stu' bodi and escap to wreak havoc on the real world, stu ha to find a way to stop him befor hi sister pull the plug on realiti forever! adventur fantasi anim action comedi parallel world organ donat horni agent aftercreditsst brendan fraser bridget fonda john turturro henri selick",
      544: 'when an amacor oil rig in the gobi desert of mongolia prove unproductive, captain frank town and copilot "a.j." are sent to shut the oper down. however, on their way to beijing, a major dust storm forc them to ditch their c-119 fli boxcar in an unchart area of the desert. action adventur drama thriller robberi water gobi desert disast airplan crash struggl for surviv desert denni quaid tyre gibson giovanni ribisi john moor',
      545: 'an ordinari man make an extraordinari discoveri when a train accid leav hi fellow passeng dead – and him unscathed. the answer to thi mysteri could lie with the mysteri elijah price, a man who suffer from a disea that render hi bone as fragil as glass. scienc fiction thriller drama father son relationship train accid comic book marriag crisi invuln superhero suspen super power bruce willi samuel l. jackson robin wright m. night shyamalan',
      546: 'minion stuart, kevin and bob are recruit by scarlet overkill, a super-villain who, alongsid her inventor husband herb, hatch a plot to take over the world. famili anim adventur comedi assist aftercreditsst duringcreditsst evil mastermind minion 3d sandra bullock jon hamm michael keaton kyle balda',
      547: 'a young girl is institut by her abu stepfather. retreat to an altern realiti as a cope strategy, she envi a plan which will help her escap from the mental facility. action fantasi thriller brothel fantasi asylum realiti escap robot violenc inmat altern imagin lobotomi emili brown abbi cornish jena malon zack snyder',
      548: "all bet are off when corrupt homicid cop rick santoro wit a murder dure a box match. it' up to him and lifelong friend and naval intellig agent kevin dunn to uncov the conspiraci behind the killing. at everi turn, santoro make increasingli shock discoveri that even he can't turn a blind eye to. crime mysteri casino polit activ boxer mission of murder box match suspen polic offic wit to murder nicola cage gari sini john heard brian de palma",
      549: 'the ossa discov a spacecraft thought to be at least 300 year old at the bottom of the ocean. immedi follow the discovery, they decid to send a team down to the depth of the ocean to studi the space craft.they are the best of best, smart and logical, and the perfect choic to learn more about the spacecraft. scienc fiction ocean extraterrestri technolog space marin paranoia raumschiffabsturz alien psychologist ocean floor deepsea dustin hoffman sharon stone samuel l. jackson barri levinson',
      550: 'an island popul entir by happy, flightless bird or almost entirely. in thi paradise, red, a bird with a temper problem, speedi chuck, and the volatil bomb have alway been outsiders. but when the island is visit by mysteri green piggies, it’ up to these unlik outcast to figur out what the pig are up to. famili anim island bird pig talk anim base on video game anger manag 3d jason sudeiki josh gad danni mcbride fergal reilli',
      551: 'treasur hunter ben "finn" finnegan ha sunk hi marriag to tess and hi trusti boat in hi obsess quest to find the legendari queen\' dowry. when he find a vital clue that may final pinpoint the treasure\' whereabouts, he drag tess and her boss, billionair nigel honeycutt, along on the hunt. but finn is not the onli one interest in the gold; hi former mentor-turned-enemi moe fitch will stop at noth to beat him to it. romanc comedi adventur helicopt cemeteri boat mexican standoff sword cave shipwreck yacht bahama jet ski treasur hunt rivalri scuba dive gangster underwat divorc heiress ex-husband ex-wif relationship henchmen matthew mcconaughey kate hudson donald sutherland andi tennant',
      552: "famou and wealthi funnyman georg simmon doesn't give much thought to how he treat peopl until a doctor deliv stun health news, forc georg to reevalu hi prioriti with a littl help from aspir stand-up comic ira. comedi drama comedian cancer bromanc stand-up comedian adam sandler seth rogen lesli mann judd apatow",
      553: 'a team of u.s. govern agent is sent to investig the bomb of an american facil in the middl east. thriller action drama assassin assassin terrorist explo fbi chase saudi arabia investig polic medic examin terror fbi agent arab bomb attack jami foxx jennif garner chri cooper peter berg',
      554: 'lifelong friend and nation idol ricki bobbi and cal naughton jr. have earn their nascar stripe with their uncanni knack of finish race in the first and second slots, respectively, and sling catchphra like "shake and bake!" but when a rival french driver coast onto the track to challeng their records, they\'ll have to floor it to retain their top-dog status. comedi north carolina prayer famili dinner adverti divorc motor automobil race nascar dog trainer car movi sport competit psychosomat ill french stereotyp aftercreditsst duringcreditsst will ferrel john c. reilli sacha baron cohen adam mckay',
      555: "dr. john dolittl the belov doctor is back, but thi time around he play cupid to bumbl circu bear archi as he' so smitten by a pacif western bear female, ava. dr. dolittl must help a group of forest creatur to save their forest. but with the aid of hi mangy, madcap anim friends, dr. dolittl must teach archi the way of true romanc in time to save hi speci and hi home befor their habit is gone. so john held a meet for everi anim in the forest to not give up without a fight no matter what kind of anim express they have and everyon agr to do it and save their home. comedi famili romanc fantasi veterinarian forest bear anim anim protect eddi murphi kristen wilson raven-symoné steve carr",
      556: "enrag at the slaughter of murron, hi new bride and childhood love, scottish warrior william wallac slay a platoon of the local english lord' soldiers. thi lead the villag to revolt and, eventually, the entir countri to rise up against english rule. action drama histori war individu scotland in love with enemi legend independ ideal revolt tyranni mel gibson catherin mccormack sophi marceau mel gibson",
      557: 'jarhead is a film about a us marin anthoni swofford’ experi in the gulf war. after put up with an arduou boot camp, swafford and hi unit are sent to the persian gulf where they are earger to fight but are forc to stay back from the action. meanwhil swofford get news of hi girlfriend is cheat on him. desper he want to kill someon and final put hi train to use. drama war sniper marin corp saudi arabia petrol golf war u.s. marin jami foxx jake gyllenha scott macdonald sam mend',
      558: "after homer accid pollut the town' water supply, springfield is enca in a gigant dome by the epa and the simpson are declar fugitives. anim comedi famili father son relationship lake springfield the simpson duff beer garbag pig pollut environ protect agenc quarantin alcohol love alaska dysfunct famili dysfunct marriag ecolog save live first love duringcreditsst donut dan castellaneta juli kavner nanci cartwright david silverman",
      559: 'set in 1951, a blacklist hollywood writer get into a car accident, lose hi memori and settl down in a small town where he is mistaken for a long-lost son. drama romanc california fal accu prosecut anti-commun hollywood writer jim carrey martin landau lauri holden frank darabont',
      560: "talent rooki race-car driver jimmi bli ha start lose hi focu and begin to slip in the race rankings. it' no wonder, with the immen pressur be shovel on him by hi overli ambiti promot brother as well as bly' romanc with hi arch rival' girlfriend sophia. with much ride on bly, car owner carl henri bring former race star joe tanto on board to help bly. to drive bli back to the top of the rankings, tanto must first deal with the emot scar left over from a tragic race accid which nearli took hi life. action competit run career idol race car kip pardu robert sean leonard til schweiger renni harlin",
      561: 'two tiger are separ as cub and taken into captivity, onli to be reunit year later as enemi by an explor (pearce) who inadvert forc them to fight each other. adventur drama famili brother brother relationship loss of brother cambodia chase tiger governor royalti travel circu archaeologist maï anh le guy pearc oanh nguyen jean-jacqu annaud',
      562: 'when a will young man tri to ventur beyond hi sequest pennsylvania hamlet, hi action set off a chain of chill incid that will alter the commun forever. drama mysteri thriller secret forest rural set blind courtship mental handicap man human natur aura romant villag council bryce dalla howard joaquin phoenix adrien brodi m. night shyamalan',
      563: "a success physician and devot famili man, john dolittl (eddi murphy) seem to have the world by the tail, until a long suppress talent he possess as a child, the abil to commun with anim is suddenli reawaken with a vengeance! now everi creatur within squawk distanc want the good doctor' advice, unleash an outrag chain of event that turn hi world upsid down! comedi famili fantasi talk to anim woman director eddi murphi ossi davi oliv platt betti thoma",
      564: 'a famili live on a farm find mysteri crop circl in their field which suggest someth more frighten to come. drama thriller scienc fiction mysteri symbol water farm faith alien famili relationship rural set alien inva rural crop circl alien attack rural pennsylvania rural america rural farm loss of faith alien encount mel gibson joaquin phoenix rori culkin m. night shyamalan',
      565: "shrek, fiona and donkey set off to far, far away to meet fiona' mother and father. but not everyon is happy. shrek and the king find it hard to get along, and there' tension in the marriage. the fairi godmoth discov that shrek ha marri fiona instead of her son princ charm and set about destroy their marriage. adventur anim comedi famili fantasi prison magic liber honeymoon parents-in-law kingdom enchant danc scene transform fairy-t figur mike myer eddi murphi cameron diaz andrew adamson",
      566: "lightn mcqueen, a hotshot rooki race car driven to succeed, discov that life is about the journey, not the finish line, when he find himself unexpectedli detour in the sleepi rout 66 town of radiat springs. on rout across the countri to the big piston cup championship in california to compet against two season pros, mcqueen get to know the town' offbeat characters. anim adventur comedi famili car race car journey villag and town auto rout 66 wrecker porsch retir media friendship sport anthropomorph lo angel road movi aftercreditsst duringcreditsst owen wilson paul newman bonni hunt john lasset",
      567: 'ike graham, new york columnist, write hi text alway at the last minute. thi time, a drunken man in hi favourit bar tell ike about maggi carpenter, a woman who alway flee from her groom in the last possibl moment. ike, who doe not have the best opinion about femal anyway, write an offen column without research the subject thoroughly. comedi romanc small town self-discoveri just marri report wed relationship julia robert richard gere joan cusack garri marshal',
      568: 'xander cage is your standard adrenalin junki with no fear and a lousi attitude. when the us govern "recruits" him to go on a mission, he\' not exactli thrilled. hi mission: to gather inform on an organ that may just be plan the destruct of the world, led by the nihilist yorgi. action adventur thriller sport car biolog weapon cold war russian pragu mission athlet nsa agent adrenalin junki thrill seeker vin diesel asia argento samuel l. jackson rob cohen',
      569: 'burger beard is a pirat who is in search of the final page of a magic book that make ani evil plan he write in it come true, which happen to be the krabbi patti secret formula. when the entir citi of bikini bottom is put in danger, spongebob, patrick, mr. krabs, squidward, sandy, and plankton need to go on a quest that take them to the surface. in order to get back the recip and save their city, the gang must retriev the book and transform themselv into superheroes. anim adventur comedi famili ocean sea star water comedi spong spongebob live action and anim tom kenni bill fagerbakk rodger bumpass paul tibbitt',
      570: "when a rich man' son is kidnapped, he cooper with the polic at first but then tri a uniqu tactic against the criminals. action thriller bounti loss of child yellow press fbi baby-snatch suspen fbi agent millionair mel gibson gari sini delroy lindo ron howard",
      571: 'in nazi-occupi franc dure world war ii, a group of jewish-american soldier known as "the basterds" are chosen specif to spread fear throughout the third reich by scalp and brutal kill nazis. the basterds, lead by lt. aldo rain soon cross path with a french-jewish teenag girl who run a movi theater in pari which is target by the soldiers. drama action thriller war pari guerrilla cinema self sacrif dynamit mexican standoff world war ii jew persecut jew nazi masoch sadism scalp winston churchil knife in hand anti semit gore swastika blood bath german occup of franc violenc gun violenc brad pitt mélani laurent christoph waltz quentin tarantino',
      572: "the boy who wasn't suppo to grow up—pet pan—did just that, becom a soulless corpor lawyer whose workahol could cost him hi wife and kids. but a trip to see granni wendi in london, where the veng capt. hook kidnap peter' kid and forc peter to return to neverland, could lead to a chanc at redemption, in thi family-ori fantasi from director steven spielberg. adventur fantasi comedi famili fli swordplay sword fantasi peter pan daughter fairy-t figur rescu robin william dustin hoffman julia robert steven spielberg",
      573: "john mcclane is an off-duti cop grip with a feel of déjà vu when on a snowi christma eve in the nation' capital, terrorist seiz a major intern airport, hold thousand of holiday travel hostage. renegad militari commando led by a murder rogu offic plot to rescu a drug lord from justic and are prepar for everi cont except one: mcclane' smart-mouth heroics. action thriller ambush helicopt journalist base on novel airport hand grenad fistfight cop sequel snow dull intern airport shootout offic involv shoot terror explo church violenc sabotag walki talki swat team air traffic control commando unit snowmobil bruce willi bonni bedelia william atherton renni harlin",
      574: "hondo harrelson recruit jim street to join an elit unit of the lo angel polic department. togeth they seek out more members, includ tough deke kay and singl mom chri sanchez. the team' first big assign is to escort crime boss alex montel to prison. it seem routine, but when montel offer a huge reward to anyon who can break him free, crimin of variou stripe step up for the prize. action thriller crime liber transport of prison special unit weapon lo angel samuel l. jackson colin farrel michel rodriguez clark johnson",
      575: "david aam (tom cruise) ha it all: wealth, good look and gorgeou women on hi arm. but just as he begin fall for the warmheart sofia (penelop cruz), hi face is horribl disfigur in a car accident. that' just the begin of hi troubl as the line between illu and reality, between life and death, are blurred. drama mysteri romanc scienc fiction thriller amnesia ex-girlfriend virtual realiti tom crui penélop cruz cameron diaz cameron crow",
      576: 'apart build superintend cleveland heep rescu what he think is a young woman from the pool he maintains. when he discov that she is actual a charact from a bedtim stori who is tri to make the journey back to her home, he work with hi tenant to protect hi new friend from the creatur that are determin to keep her in our world. drama thriller fantasi mysteri fortun teller religion and supernatur supernatur power mythic creatur hell swim pool nix aftercreditsst paul giamatti jeffrey wright bob balaban m. night shyamalan',
      577: 'when scientist discov someth in the arctic that appear to be a buri pyramid, they send a research team out to investigate. littl do they know that they are about to step into a hunt ground where alien are grown as sport for the predat race. adventur scienc fiction action save the world predat laserpoint space marin pyramid prai alien xenomorph sanaa lathan raoul bova ewen bremner paul w.s. anderson',
      578: "pop sensat alvin, simon and theodor end up in the care of dave seville' twenty-someth nephew toby. the boy must put asid music super stardom to return to school, and are task with save the school' music program by win the $25,000 prize in a battl of the bands. but the chipmunk unexpectedli meet their match in three sing chipmunk known as the chipett - brittany, eleanor and jeanette. romant and music spark are ignit when the chipmunk and chipett squar off. comedi famili anim fantasi music chipmunk cgi base on tv seri aftercreditsst duringcreditsst woman director zachari levi david cross jason lee betti thoma",
      579: 'the stori of the first major battl of the american phase of the vietnam war and the soldier on both side that fought it. action histori war vietnam veteran missil vietnam war armi major base on true stori steel helmet soldier explo battl bayonet death vietnam mel gibson greg kinnear madelein stow randal wallac',
      580: 'when the white hou (secret servic code: "olympus") is captur by a terrorist mastermind and the presid is kidnapped, disgrac former presidenti guard mike ban find himself trap within the building. as the nation secur team scrambl to respond, they are forc to reli on banning\' insid knowledg to help retak the white house, save the presid and avert an even bigger disaster. action thriller white hou secret servic terrorist attack gerard butler aaron eckhart angela bassett antoin fuqua',
      581: 'when an alien race and faction within starfleet attempt to take over a planet that ha "regenerative" properties, it fall upon captain picard and the crew of the enterpri to defend the planet\' peopl as well as the veri ideal upon which the feder itself wa founded. scienc fiction action adventur thriller space opera retribut spacecraft offic explod ship patrick stewart jonathan frake brent spiner jonathan frake',
      582: "the earth is attack by unknown forces. as peopl everywh watch the world' great citi fall, lo angel becom the last stand for mankind in a battl no one expected. it' up to a marin staff sergeant and hi new platoon to draw a line in the sand as they take on an enemi unlik ani they'v ever encount before. action scienc fiction save the world hero marin corp chao retir survivor meteor space inva alien battlefield surviv sergeant lo angel battl danger escapad u.s. marin heroic mission evil alien chao and mayham aaron eckhart ramón rodríguez will rothhaar jonathan liebesman",
      583: "throughout hi life edward bloom ha alway been a man of big appetites, enorm passion and tall tales. in hi later years, he remain a huge mysteri to hi son, william. now, to get to know the real man, will begin piec togeth a true pictur of hi father from flashback of hi amaz adventures. adventur fantasi drama circu father son relationship witch fish fish love of one' life leech stori teller apoplect stroke fair mermaid cancer relationship youth gentl giant ewan mcgregor albert finney billi crudup tim burton",
      584: 'publish will randal becom a werewolf and ha to fight to keep hi job. fantasi adulteri heal bite werewolf jack nicholson christoph plummer jame spader mike nichol',
      585: 'follow a young man name albert and hi horse, joey, and how their bond is broken when joey is sold to the cavalri and sent to the trench of world war one. despit be too young to enlist, albert head to franc to save hi friend. drama war world war i hor farm life execut trap alcohol cavalri plow artilleri tom hiddleston benedict cumberbatch tobi kebbel steven spielberg',
      586: 'base on the true stori of the greatest treasur hunt in history, the monument men is an action drama focu on seven over-the-hill, out-of-shap museum directors, artists, architects, curators, and art historian who went to the front line of wwii to rescu the world’ artist masterpiec from nazi thiev and return them to their right owners. with the art hidden behind enemi lines, how could these guy hope to succeed? war drama histori action world war ii nazi art theft post world war ii matt damon cate blanchett georg clooney georg clooney',
      587: "a civilian oil rig crew is recruit to conduct a search and rescu effort when a nuclear submarin mysteri sinks. one diver soon find himself on a spectacular odyssey 25,000 feet below the ocean' surfac where he confront a mysteri forc that ha the power to chang the world or destroy it. adventur action thriller scienc fiction ocean sea dive suit fli saucer nuclear missil alien life-form insan scuba dive underwat scuba deepsea trap underwat thalassophobia ed harri mari elizabeth mastrantonio michael biehn jame cameron",
      588: "as the global economi teeter on the brink of disaster, a young wall street trader partner with disgrac former wall street corpor raider gordon gekko on a two tier mission: to alert the financ commun to the come doom, and to find out who wa respon for the death of the young trader' mentor. drama crime duringcreditsst michael dougla shia labeouf josh brolin oliv stone",
      589: "vlad tepe is a great hero, but when he learn the sultan is prepar for battl and need to form an armi of 1,000 boys, includ vlad' son, he vow to find a way to protect hi family. vlad turn to dark forc in order to get the power to destroy hi enemi and agr to go from hero to monster as he' turn into the mytholog vampir dracula. horror action drama fantasi war vampir dracula bite battl 15th centuri ottoman empir vlad fang vamp tepe luke evan sarah gadon domin cooper gari shore",
      590: 'the secret us abduct of a suspect terrorist lead to a wave of terrorist attack in new york that lead to the declar of martial law. drama action thriller crime islam muslim car bomb fbi agent denzel washington annett bene bruce willi edward zwick',
      591: "in a countrysid town border on a magic land, a young man make a promi to hi belov that he'll retriev a fallen star by ventur into the magic realm. hi journey take him into a world beyond hi wildest dream and reveal hi true identity. adventur fantasi romanc famili witch base on novel new love princ beauti star kingdom wall fall star royalti unrequit love good vs evil fratricid clair dane charli cox michel pfeiffer matthew vaughn",
      592: "austrian mountaineer, heinrich harrer journey to the himalaya without hi famili to head an expedit in 1939. but when world war ii break out, the arrog harrer fall into alli forces' hand as a prison of war. he escap with a fellow detain and make hi way to llaso, tibet, where he meet the 14-year-old dalai lama, whose friendship ultim transform hi outlook on life. adventur drama histori buddhism himalaya austria mountain buddhist monk world war ii prison of war monsoon tibet dalai lama mountain lhasa wed brad pitt jamyang jamtsho wangchuk david thewli jean-jacqu annaud",
      593: "longtim friend ronni and nick are partner in an auto-design firm. they are hard at work on a present for a dream project that would realli launch their company. then ronni spot nick' wife out with anoth man, and in the process of investig the possibl affair, he learn that nick ha a few secret of hi own. as the present nears, ronni agon over what might happen if the truth get out. comedi drama adulteri infidel secret investig friendship partner love friend dilemma cheat on partner best friend kevin jame vinc vaughn winona ryder ron howard",
      594: 'when a harvard-educ cia agent is kill dure an operation, the secret agenc recruit hi twin brother. action adventur comedi thriller ambush cia assassin nightclub hustler hidden camera decoy undercov agent twin brother decept betray mistaken ident shootout espionag foot chase car chase silenc surveil agent imperson langley virginia odd coupl anthoni hopkin chri rock peter stormar joel schumach',
      595: 'a team of space marin known as the rapid respon tactic squad, led by sarge, is sent to a scienc facil on mar after somebodi report a secur breach. there, they learn that the alert came after a test subject, a mass murder purpo inject with alien dna, broke free and began kill people. dr. grimm, who is relat to team member reaper, inform them all that the chromosom can mutat human into monster -- and is highli infectious. adventur action horror teleport base on video game sever ear futur war wisecrack humor commando mission dwayn johnson karl urban rosamund pike andrzej bartkowiak',
      596: "when the switchblade, the most sophist prototyp stealth fighter creat yet, is stolen from the u.s. government, one of the unit states' top spies, alex scott, is call to action. what he doesn't expect is to get team up with a cocki civilian, world class box champion kelli robinson, on a danger top secret espionag mission. their assignment: use equal part skill and humor, catch arnold gundars, one of the world' most success arm dealers. action adventur comedi thriller budapest kidnap boxer secret agent liber of hostag hostage-tak woman director eddi murphi owen wilson famk janssen betti thoma",
      597: 'after be held in a coma-lik state for fifteen years, vampir selen learn that she ha a fourteen-year-old vampire/lycan hybrid daughter name nissa, and when she find her, they must stop biocom from creat super lycan that will kill them all. fantasi action horror vampir daughter hybrid child vampir werewolf imax lab experi werewolf child fang vamp kate beckins stephen rea michael eali mån mårlind',
      598: 'a small town girl and a citi boy meet on the sunset strip, while pursu their hollywood dreams. comedi drama music romanc music rocker teenag young love rock sta juliann hough diego boneta tom crui adam shankman',
      599: "fourth-gen armi col. william mcnamara is imprison in a brutal german pow camp. still, as the senior-rank american officer, he command hi fellow inmates, keep a sen of honor aliv in a place where honor is easi to destroy, all under the danger eye of the luftwaf vetran col. wilhelm visser. never give up the fight to win the war, mcnamara is silent planning, wait for hi moment to strike back at the enemy. a murder in the camp give him the chanc to set a riski plan in motion. with a court martial to keep visser and the german distracted, mcnamara orchestr a cun scheme to escap and destroy a nearbi munit plant, enlist the unwit help of young lt. tommi hart. togeth with hi men, mcnamara use a hero' resolv to carri out hi mission, ultim forc to weigh the valu of hi life against the good of hi country. drama war black peopl world war ii prison of war u.s. armi war escap tribun trial soldier militari tribun xenophobia bruce willi colin farrel terrenc howard gregori hoblit",
      600: 'base on a shock true story, killer elit pit two of the world’ most elit operatives—danny, an ex-speci op agent and hunter, hi longtim mentor—against the cun leader of a secret militari society. cover the globe from australia to paris, london and the middl east, danni and hunter are plung into a highli danger game of cat and mouse—wh the predat becom the prey. action adventur thriller rescu jason statham clive owen robert de niro gari mckendri',
      601: "from the director of die hard come thi high-octan thriller that roar along at a breakneck pace (lo angel times)! star chri klein (american pie), jean reno (ronin), ll cool j (charlie' angels) and rebecca romijn-stamo (x-men), rollerb goe full-throttl with excit from it death-defi open until it explo end! jonathan cross (klein) is the newest recruit in the most extrem sport of all time where hi fast move and killer look make him an instant superstar. but cross life in the fast lane collid with realiti when he learn that the league' owner (reno) is orchestr seriou on-court accid to boost ratings. now cross plan to take down the owner and hi ruthless sport befor the game put an end to him! action scienc fiction thriller manag arena dystopia wrestl sport roller-sk motorcycl race rollersk futur sport chri klein ll cool j rebecca romijn john mctiernan",
      602: 'jonathan ecks, an fbi agent, realiz that he must join with hi lifelong enemy, agent sever, a rogu dia agent with whom he is in mortal combat, in order to defeat a common enemy. that enemi ha develop a "micro-device" that can be inject into victim in order to kill them at will. action adventur thriller loss of famili enemi adversari agent antonio bandera luci liu gregg henri wych kaosayananda',
      603: 'get swept up in the action as an armor car driver (christian slater) tri to elud a gang of thiev (led by morgan freeman) while a flood ravag the countryside. hard rain is "a wild, thrilling, chill action ride" fill with close calls, uncertain loyalti and heart-stop heroics. thriller sheriff rain evacu armor car crook hoodlum morgan freeman christian slater randi quaid mikael salomon',
      604: 'a policeman white blood cell, with the help of a cold pill, must stop a deadli viru from destroy the human they live in, frank. adventur anim action comedi famili cold flu lethal viru construct worker chri rock laurenc fishburn david hyde pierc bobbi farrelli',
      605: 'dorothi wake up in post-tornado kansas, onli to be whisk back to oz to tri to save her old friend the scarecrow, the lion, the tin man and glinda from a deviou new villain, the jester. wiser the owl, marshal mallow, china princess and tugg the tugboat join dorothi on her latest magic journey through the color landscap of oz to restor order and happi to emerald city. anim music famili lea michel dan aykroyd patrick stewart dan st. pierr',
      606: 'a man is relea from prison to help american and chine author pursu a mysteri cyber criminal. the danger search lead them from chicago to hong kong. crime drama mysteri terrorist technolog anti hero hacker comput viru nation secur agenc (nsa) race against time comput malaysia nuclear power plant suspen betray conspiraci on the run fugit shootout hack terror cat and mou one against mani comput hacker no open credit terrorist plot stock exchang cybercrim cyber terror chine militari cyber terrorist cyber thriller chri hemsworth leehom wang tang wei michael mann',
      607: 'when gigant robot attack new york city, "ski captain" use hi privat air forc to fight them off. hi ex-girlfriend, report polli perkins, ha been investig the recent disappear of promin scientists. suspect a link between the global robot attack and miss men, ski captain and polli decid to work together. they fli to the himalaya in pursuit of the mysteri dr. totenkopf, the mastermind behind the robots. mysteri action thriller scienc fiction adventur london england himalaya journalist killer robot comput war robot jude law gwyneth paltrow giovanni ribisi kerri conran',
      608: 'novelist catherin tramel is onc again in troubl with the law, and scotland yard appoint psychiatrist dr. michael glass to evalu her. though, like detect nick curran befor him, glass is entranc by tramel and lure into a seduct game. crime mysteri thriller male nuditi sex leg soho london play god jacuzzi sharon stone david morrissey charlott rampl michael caton-jon',
      609: "ray breslin is the world' foremost author on structur security. after analyz everi high secur prison and learn a vast array of surviv skill so he can design escape-proof prisons, hi skill are put to the test. he' frame and incarc in a master prison he design himself. he need to escap and find the person who put him behind bars. action thriller prison muslim ship mysteri scienc fiction escap crime prison escap cia agent sylvest stallon arnold schwarzenegg jim caviezel mikael håfström",
      610: 'in ancient greec 1200 b.c., a queen succumb to the lust of zeu to bear a son promi to overthrow the tyrann rule of the king and restor peac to a land in hardship. but thi prince, hercules, know noth of hi real ident or hi destiny. he desir onli one thing: the love of hebe, princess of crete, who ha been promi to hi own brother. when hercul learn of hi greater purpose, he must choose: to flee with hi true love or to fulfil hi destini and becom the true hero of hi time. the stori behind one of the greatest myth is reveal in thi action-pack epic - a tale of love, sacrif and the strength of the human spirit. action adventur mytholog zeu ancient greec demigod citi of argo mistaken parentag kellan lutz liam mcintyr gaia weiss renni harlin',
      611: 'when the presid of russia suddenli dies, a man whose polit are virtual unknown succ him. the chang in polit leader spark paranoia among american cia officials, so cia director bill cabot recruit a young analyst to suppli insight and advic on the situation. then the unthink happens: a nuclear bomb explod in a u.s. city, and america is quick to blame the russians. thriller action drama cia terrorist atom bomb cold war nuclear explo jack ryan ben affleck morgan freeman jame cromwel phil alden robinson',
      612: 'bella onc again find herself surround by danger as seattl is ravag by a string of mysteri kill and a malici vampir continu her quest for revenge. in the midst of it all, she is forc to choo between her love for edward and her friendship with jacob, know that her deci ha the potenti to ignit the ageless struggl between vampir and werewolf. with her graduat quickli approaching, bella is confront with the most import deci of her life. adventur fantasi drama romanc vampir graduat bite immort werewolf fang vamp kristen stewart robert pattinson taylor lautner david slade',
      613: 'an age thief hope to retir and live off hi ill-gotten wealth when a young kid convinc him into do one last heist. action crime thriller quebec jewel scepter custom hou jewelri heist blueprint assum ident schemat voic over surveil camera one last job robert de niro edward norton marlon brando frank oz',
      614: "villain gru live up to hi reput as a despicable, deplor and downright unlik guy when he hatch a plan to steal the moon from the sky. but he ha a tough time stay on task after three orphan land in hi care. anim famili adopt father orphanag life' dream rivalri steal ballet littl girl orphan father daughter relationship tomboy mother son relationship intellig kid evil doctor duringcreditsst minion supervillain 3d despic cattivissimo steve carel jason segel russel brand pierr coffin",
      615: 'a veng new york transit cop decid to steal a trainload of subway fares; hi foster brother, a fellow cop, tri to protect him. action comedi crime brother brother relationship subway new york citi new york subway train robberi wesley snipe woodi harrelson jennif lopez joseph ruben',
      616: "newlyw coupl ted and tami-lynn want to have a baby, but in order to qualifi to be a parent, ted will have to prove he' a person in a court of law. comedi sperm bank sequel buddi courthou teddi bear aftercreditsst toy come to life marri mark wahlberg seth macfarlan amanda seyfri seth macfarlan",
      617: 'a histor drama set in roman egypt, concern philosoph hypatia of alexandria and her relationship with her slave davus, who is torn between hi love for her and the possibl of gain hi freedom by join the rise tide of christianity. adventur drama histori christian philosophi egypt new love war cult histor figur histori sword fight ancient world destini fall in love hypatia misogyni persecut librari of alexandria polit unrest imposs love fal histori power relat unfulfil master and servant love and romanc unfulfil love rachel weisz max minghella oscar isaac alejandro amenábar',
      618: "when captain amaz (kinnear) is kidnap by casanova frankenstein (rush) a group of superhero combin togeth to creat a plan. but these aren't normal superheroes. now, the group who includ such hero as mr. furiou (stiller), the shovel (macy) and the blue raja (azaria) must put all the power togeth to save everyon they know and love. adventur fantasi action comedi scienc fiction bowl hostag sphinx train insan asylum tool frankenstein casanova superhero base on comic book independ film comedi spoof skull shovel disco superhero spoof invi man dark hor comic invi rajah bowl ball spleen evil geniu ben stiller geoffrey rush clair forlani kinka usher",
      619: 'when best bud rick and fred begin to show sign of restless at home, their wive take a bold approach to revit their marriages: they grant the guy a "hall pass", one week of freedom to do whatev they want. at first, it seem like a dream come true, but they quickli discov that their expect of the singl life - and themselv - are complet and hilari out of sync with reality. comedi wife husband relationship daydream marriag freedom friend owen wilson jason sudeiki jenna fischer bobbi farrelli',
      620: 'tell the true stori of a 60 minut televi seri exposé of the tobacco industry, as seen through the eye of a real tobacco executive, jeffrey wigand drama thriller spi newspap research interview tobacco insid conspiraci theori report whistleblow columbia broadcast system (cbs) tobacco industri al pacino russel crow christoph plummer michael mann',
      621: 'the coast guard make a dare rescu attempt off the coast of cape cod after a pair of oil tanker are destroy dure a blizzard in 1952. action drama histori thriller coast guard base on true stori surviv rescu mission storm at sea sink ship 1950 3d chri pine casey affleck ben foster craig gillespi',
      622: 'the cia’ hunt is on for the mastermind of a wave of terrorist attacks. roger ferri is the agency’ man on the ground, move from place to place, scrambl to stay ahead of ever-shift events. an eye in the sky – a satellit link – watch ferris. at the other end of that real-tim link is the cia’ ed hoffman, strateg event from thousand of mile away. and as ferri near the target, he discov trust can be just as danger as it is necessari for survival. action drama thriller terror fal accu base on novel die and death jordan dubai intellig agenc beat leonardo dicaprio russel crow mark strong ridley scott',
      623: "rise execut tim wagner work for a boss who host a monthli dinner in which the guest who bring the biggest buffoon get a career-boost. tim plan on not attend until he meet barry, a man who build diorama use stuf mice. barry' blunder but good intent send tim' life into a downward spiral, threaten a major busi deal and possibl scuttl tim' engag to hi fiancee. comedi mou idiot mind control taxidermi aftercreditsst duringcreditsst steve carel paul rudd stephani szostak jay roach",
      624: "presid lincoln' mother is kill by a supernatur creature, which fuel hi passion to crush vampir and their slave-own helpers. action fantasi horror usa presid vampir steam locomot american civil war 19th centuri abraham lincoln 3d benjamin walker domin cooper anthoni macki timur bekmambetov",
      625: "two thieves, who travel in eleg circles, tri to outsmart each other and, in the process, end up fall in love. romanc drama mysteri london england new year' eve skyscrap burglar distrust undercov blackmail nuditi thief heist older man younger woman relationship art thief crimin art theft millennium manhattan, new york citi gala kuala lumpur malaysia sean conneri catherin zeta-jon will patton jon amiel",
      626: "mulder and scully, now taken off the fbi' x file cases, must find a way to fight the shadowi element of the govern to find out the truth about a conspiraci that might mean the alien colon of earth. mysteri scienc fiction thriller bomb helicopt secret obsess extraterrestri technolog fbi space marin mutat secret societi secret organ secret lab x-file govern david duchovni gillian anderson mitch pileggi rob bowman",
      627: 'as the roman empir crumbles, young romulu augustu flee the citi and embark on a peril voyag to britain to track down a legion of supporters. action adventur fantasi war roman empir emperor ancient rome western roman empir ancient world juliu caesar colin firth ben kingsley aishwarya rai bachchan doug lefler',
      628: 'as u.s. troop storm the beach of normandy, three brother lie dead on the battlefield, with a fourth trap behind enemi lines. ranger captain john miller and seven men are task with penetr german-held territori and bring the boy home. drama histori war war crime self sacrif war veteran world war ii war ship airplan braveri normandi parachut troop waffen ss omaha beach armi coward american flag war memori desert town militari 1940 tom hank matt damon vin diesel steven spielberg',
      629: "the film revolv around a local street-rac who partner with a rich and arrog busi associate, onli to find himself frame by hi colleagu and sent to prison. after he get out, he join a new york-to-lo angel race to get revenge. but when the ex-partn learn of the scheme, he put a massiv bounti on the racer' head, forc him to run a cross-countri gauntlet of illeg racer in all manner of supercharg vehicles. action crime drama thriller street race super car super speed car base on video game duringcreditsst 3d aaron paul domin cooper imogen poot scott waugh",
      630: "adverti execut nick marshal is as cocki as they come, but what happen to a chauvinist guy when he can suddenli hear what women are thinking? nick get pass over for a promotion, but after an accid enabl him to hear women' thoughts, he put hi newfound talent to work against darcy, hi new boss, who seem to be infatu with him. comedi romanc women telepathi supernatur power adverti execut woman director helen hunt mel gibson marisa tomei nanci meyer",
      631: 'with the impend ice age almost upon them, a mismatch trio of prehistor critter – manni the woolli mammoth, diego the saber-tooth tiger and sid the giant sloth – find an orphan infant and decid to return it to it human parents. along the way, the unlik alli becom friend but, when enemi attack, their quest take on far nobler aims. anim comedi famili adventur human evolut parent kid relationship squirrel ice loss of child mammoth sloth die and death stone age prehistor saber-tooth tiger cavemen prehistor creatur prehistor adventur prehistor time prehistor man ray romano john leguizamo deni leari chri wedg',
      632: "four boyhood pal perform a heroic act and are chang by the power they gain in return. year later, on a hunt trip in the main woods, they'r overtaken by a viciou blizzard that harbor an omin presence. challeng to stop an alien force, the friend must first prevent the slaughter of innoc civilian by a militari vigil ... and then overcom a threat to the bond that unit the four of them. drama horror scienc fiction thriller religion and supernatur morgan freeman thoma jane jason lee lawrenc kasdan",
      633: "a reveal drama that focu on the 16th president' tumultu final month in office. in a nation divid by war and the strong wind of change, lincoln pursu a cour of action design to end the war, unit the countri and abolish slavery. with the moral courag and fierc determin to succeed, hi choic dure thi critic moment will chang the fate of gener to come. histori drama usa presid speech battlefield famili conflict mourn american civil war cultur conflict base on true event battl of gettysburg secess presidenti cabinet gettysburg address conflagr ethic dilemma emancip abraham lincoln daniel day-lewi salli field david strathairn steven spielberg",
      634: 'set in the 22nd century, the matrix tell the stori of a comput hacker who join a group of underground insurg fight the vast and power comput who now rule the earth. action scienc fiction save the world artifici intellig man vs machin philosophi propheci martial art self sacrif fight insurg virtual realiti dystopia truth cyberpunk woman director messiah gnostic keanu reev laurenc fishburn carrie-ann moss lilli wachowski',
      635: 'the true stori of technic troubl that scuttl the apollo 13 lunar mission in 1971, risk the live of astronaut jim lovel and hi crew, with the fail journey turn into a thrill saga of heroism. drift more than 200,000 mile from earth, the astronaut work furiou with the ground crew to avert tragedy. drama moon florida nasa spaceman race against time houston base on true stori space rescu surviv disast explo astronaut imax saturn v rocket courag hypothermia apollo program cape kennedi lunar mission spacecraft accid tom hank bill paxton kevin bacon ron howard',
      636: "better watch out! the big guy in red is come to town onc again. thi time, scott calvin -- also known as santa clau -- find out there' an obscur clau in hi contract requir him to take on a wife. he ha to leav the north pole to fulfil hi obligations, or el he'll be forc to give up hi yuletid gig. fantasi comedi famili holiday christma parti home santa clau magic toy wish son sequel save christma christma tim allen elizabeth mitchel david krumholtz michael lembeck",
      637: "an adapt of the success stage music base on victor hugo' classic novel set in 19th-centuri france, in which a parol prison name jean valjean seek redemption. drama music romanc franc robberi brothel mayor star music arrest armi rebellion wed fall in love corp parol convict girl disgui as boy hugh jackman russel crow ann hathaway tom hooper",
      638: "book superstor magnate, joe fox and independ book shop owner, kathleen kelli fall in love in the anonym of the internet – both bliss unawar that he' put her out of business. comedi romanc romant comedi onlin date woman director tom hank meg ryan kati sagona nora ephron",
      639: "brennan huff and dale doback might be grown men. but that doesn't stop them from live at home and turn into jealous, competit stepbroth when their singl parent marry. brennan' constant competit with dale strain hi mom' marriag to dale' dad, leav everyon to wonder whether they'll ever see eye to eye. comedi becom an adult autonomi childhood trauma hostil step brother slacker man child aftercreditsst duringcreditsst will ferrel john c. reilli mari steenburgen adam mckay",
      640: 'it ha been twenti year sinc don diego de la vega fought spanish oppress in alta california as the legendari romant hero, zorro. have escap from prison he transform troubl bandit alejandro into hi successor, in order to foil the plan of the tyrann don rafael montero who rob him of hi freedom, hi wife and hi preciou daughter. action adventur california spi hero horseback ride sword fight reveng antonio bandera anthoni hopkin catherin zeta-jon martin campbel',
      641: "peter highman must scrambl across the us in five day to be present for the birth of hi first child. he get off to a bad start when hi wallet and luggag are stolen, and put on the 'no-fly' list. peter embark on a terrifi journey when he accept a ride from an actor. comedi drama highway slacker hitchhik wallet sunglass rest stop vicodin waffl robert downey jr. zach galifianaki michel monaghan todd phillip",
      642: "a chronicl of the life of loui zamperini, an olymp runner who wa taken prison by japan forc dure world war ii. drama war world war ii prison of war biographi sport war athlet woman director olymp athlet jack o'connel domhnal gleeson garrett hedlund angelina joli",
      643: "frank corvin, ‘hawk’ hawkins, jerri o'neil and ‘tank’ sullivan were hotdog member of project daedalus, the air force' test program for space travel, but their hope were dash in 1958 with the format of nasa and the use of train chimps. they blackmail their way into orbit when russia' mysteri ‘ikon’ commun satellite' orbit begin to degrad and threaten to crash to earth. action adventur thriller nasa space travel astronaut elderli clint eastwood tommi lee jone donald sutherland clint eastwood",
      644: 'a year after lose hi friend in a tragic 4,000-foot fall, former ranger gabe walker and hi partner, hal, are call to return to the same peak to rescu a group of strand climbers, onli to learn the climber are actual thiev hijack who are look for box full of money. action adventur thriller rocki mountain airplan hijack suitca climb heist money snow mountain climb mountain sylvest stallon john lithgow michael rooker renni harlin',
      645: "when rogu stealth-fight pilot vic deakin delib drop off the radar while on maneuvers, the air forc end up with two stolen nuclear warhead -- and deakins' co-pilot, riley hale, is the military' onli hope for get them back. traver the desert canyon of utah, hale team with park ranger terri carmichael to put deakin back in hi box. action adventur drama thriller helicopt river captain underground mexican standoff countdown pilot fistfight canyon major betray gunfight train explo park ranger desert militari nuclear devic box stealth aircraft abandon mine humv john travolta christian slater samantha mathi john woo",
      646: "power businessman russ duritz is self-absorb and immer in hi work. but by the magic of the moon, he meet rusty, a chubby, charm 8-year-old version of himself who can't believ he could turn out so badli -- with no life and no dog. with rusty' help, russ is abl to reconcil the person he use to dream of be with the man he' actual become. fantasi comedi famili age differ midlif crisi suppress past self-awar childhood memori humor chang the past or futur bruce willi spencer breslin emili mortim jon turteltaub",
      647: 'on september, 11th 2001, after the terrorist attack to the world trade center, the build collap over the rescu team from the port author polic department. will jimeno and hi sergeant john mcloughlin are found aliv trap under the wreckag while the rescu team fight to save them. drama histori thriller terror runaway alarm clock hero firemen fire engin war on terror rescu marin hospit trap rubbl rescu team nicola cage maria bello maggi gyllenha oliv stone',
      648: "the stori of katherin ann watson, a feminist teacher who studi at ucla graduat school and in 1953 left her boyfriend behind in lo angeles, california to teach at wellesley college, a conserv women' privat liber art colleg in massachusetts, unit states. drama romanc faculti art histori row school nur feminin teacher hero women issu julia robert kirsten dunst julia stile mike newel",
      649: 'the heroic stori of a dictat who risk hi life to ensur that democraci would never come to the countri he so lovingli oppressed. comedi kurdish sacha baron cohen say badreya aasif mandvi larri charl',
      650: "after dr. bill hartford' wife, alice, admit to have sexual fantasi about a man she met, bill becom obsess with have a sexual encounter. he discov an underground sexual group and attend one of their meet -- and quickli discov that he is in over hi head. mysteri drama life and death sexual obsess free love heterosexu christma parti erot orgi mask ball marijuana illeg prostitut tom crui nicol kidman madison eginton stanley kubrick",
      651: "ever sinc her parent left her as a baby, littl anni ha led a hard-knock life with her calcul foster mother, miss hannigan. however, all that chang when hard-no billionair and mayor candid will stack take her in on the recommend of hi advisers. stack believ that he' annie' guardian angel, but the plucki youngster' confid and sunni outlook may mean that anni will save will instead. comedi drama famili music orphan foster child quvenzhané walli jami foxx rose byrn will gluck",
      652: 'nicky, a veteran con artist, take a novic name jess under hi wing. while nicki teach jess the trick of the trade, the pair becom romant involved; but, when jess get uncomfort close, nicki end their relationship. three year later, nicki is in bueno air work a veri danger scheme when jess -- now an accomplish femm fatal -- unexpectedli show up. her appear throw nicki for a loop at a time when he cannot afford to be off hi game. romanc comedi crime drama seduct con man femm fatal decept rivalri con artist will smith margot robbi rodrigo santoro glenn ficarra',
      653: 'two top cia oper wage an epic battl against one anoth after they discov they are date the same woman. action comedi romanc love triangl friendship date sushi bar explod airplan onlin date stabl karat class dog shelter ree witherspoon chri pine tom hardi mcg',
      654: 'for years, blade ha fought against the vampir in the cover of the night. but now, after fall into the crosshair of the fbi, he is forc out into the daylight, where he is driven to join forc with a clan of human vampir hunter he never knew exist - the nightstalkers. togeth with abigail and hannibal, two deftli train nightstalkers, blade follow a trail of blood to the ancient creatur that is also hunt him, the origin vampire, dracula. scienc fiction action horror thriller adventur fantasi fbi dracula fistfight vampir hunter superhero base on comic book martial art master motorcycl katana sword blade loss of friend super villain vampir slayer fast motion scene femal vampir wesley snipe kri kristofferson domin purcel david s. goyer',
      655: 'it is the mid-1980s. from out of the sky, soviet and cuban troop begin land on the footbal field of a colorado high school. in seconds, the paratroop have attack the school and sent a group of teenag flee into the mountains. arm onli with hunt rifles, pistol and bow and arrows, the teen struggl to surviv the bitter winter and soviet kgb patrol hunt for them. action thriller guerrilla colorado inva anti-commun near futur red armi patrick swayz c. thoma howel lea thompson john miliu',
      656: "in thi adapt of the best-sel roman à clef about bill clinton' 1992 run for the white house, the young and gift henri burton is tap to overs the presidenti campaign of governor jack stanton. burton is pull into the politician' color world and look on as stanton -- who ha a wander eye that could be hi downfal -- contend with hi ambiti wife, susan, and an outspoken adviser, richard jemmons. comedi drama white hou usa presid presidenti elect scandal georg w. bush extramarit affair john travolta emma thompson billi bob thornton mike nichol",
      657: 'the umbrella corporation’ deadli t-viru continu to ravag the earth, transform the global popul into legion of the flesh eat undead. the human race’ last and onli hope, alice, awaken in the heart of umbrella’ most clandestin oper facil and unveil more of her mysteri past as she delv further into the complex. without a safe haven, alic continu to hunt those respon for the outbreak; a chase that take her from tokyo to new york, washington, d.c. and moscow, culmin in a mind-blow revel that will forc her to rethink everyth that she onc thought to be true. aid by new found alli and familiar friends, alic must fight to surviv long enough to escap a hostil world on the brink of oblivion. the countdown ha begun. action horror scienc fiction mutant dystopia sequel conspiraci tokyo japan zombi base on video game moscow hand to hand combat viru plagu pandem mega corpor milla jovovich sienna guillori michel rodriguez paul w.s. anderson',
      658: "termin island, new york: 2020. overcrowd in the us penal system ha reach a break point. prison have been turn over to a monolith weyland corporation, which see jail full of thug as an opportun for televi sport. adren inmates, a global audienc hungri for violenc and a spectacular, enclo arena come togeth to form the 'death race', the biggest, most brutal event. action thriller scienc fiction car race dystopia matter of life and death prison guard car set on fire escap from prison explod build vehicl combat car crash violenc jason statham joan allen ian mcshane paul w.s. anderson",
      659: 'samantha caine, suburban homemaker, is the ideal mom to her 8 year old daughter caitlin. she live in honesdale, pa, ha a job teach school and make the best rice krispi treat in town. but when she receiv a bump on her head, she begin to rememb small part of her previou life as a lethal, top-secret agent crime action mysteri thriller assassin amnesia hostag chase dark comedi teacher escap singl mother timebomb candlelight vigil rogu agent street shootout ex cia agent christma parad geena davi samuel l. jackson yvonn zima renni harlin',
      660: 'alic hire a profess negoti to obtain the relea of her engin husband, who ha been kidnap by anti-govern guerrilla in south america. action adventur drama romanc thriller hostag new love suspen agent meg ryan russel crow david mor taylor hackford',
      661: 'after their father is call into work, two young boys, walter and danny, are left in the care of their teenag sister, lisa, and told they must stay inside. walter and danny, who anticip a bore day, are shock when they begin play zathura, a space-them board game, which they realiz ha mystic power when their hou is shot into space. with the help of an astronaut, the boy attempt to return home. famili fantasi scienc fiction adventur adventur hou alien giant robot outer space astronaut jonah bobo josh hutcherson dax shepard jon favreau',
      662: 'a ticking-time-bomb insomniac and a slipperi soap salesman channel primal male aggress into a shock new form of therapy. their concept catch on, with underground "fight clubs" form in everi town, until an eccentr get in the way and ignit an out-of-control spiral toward oblivion. drama support group dual ident nihil rage and hate insomnia dystopia violenc edward norton brad pitt meat loaf david fincher',
      663: "when a plane crash claim the live of member of the marshal univ footbal team and some of it fans, the team' new coach and hi surviv player tri to keep the footbal program alive. drama american footbal 1970 trainer colleg sport matthew mcconaughey matthew fox anthoni macki mcg",
      664: 'eddi hawkins, call hudson hawk ha just been relea from ten year of prison and is plan to spend the rest of hi life honestly. but then the crazi mayflow coupl blackmail him to steal some of the work of leonardo da vinci. if he refuses, they threaten to kill hi friend tommy. action adventur comedi vatican leonardo da vinci paint master thief bruce willi danni aiello andi macdowel michael lehmann',
      665: "russ richard is a tv weatherman and local celebr on the verg of lose hi shirt. desper to escap financ ruin, he scheme with crystal the tv station' lotto ball girl to rig the state lotteri drawing. the number come up right, but everyth el goe wrong as the plan start to unravel and the game turn rough. action adventur comedi crime romanc thriller weather forecast tv station weather lotteri wettermann debt woman director john travolta lisa kudrow tim roth nora ephron",
      666: "200 year after hi shock creation, dr. frankenstein' creature, adam, still walk the earth. but when he find himself in the middl of a war over the fate of humanity, adam discov he hold the key that could destroy humankind. horror thriller soul queen anti hero fantasi princ supernatur frankenstein good vs evil gargoyl fight demon dark imax 3d aaron eckhart yvonn strahovski bill nighi stuart beatti",
      667: "oliv twist the modern film version of charl dicken bestseller, a roman polanski adaptation. the classic dicken tale, where an orphan meet a pickpocket on the street of london. from there, he join a household of boy who are train to steal for their master. crime drama famili london england child abu street gang runaway child labour children' home orphanag thief violenc good and bad child barney clark ben kingsley jami foreman roman polanski",
      668: 'elektra the warrior surviv a near-death experience, becom an assassin-for-hire, and tri to protect her two latest targets, a singl father and hi young daughter, from a group of supernatur assassins. action fantasi martial art base on comic book femal assassin spin off jennif garner goran visnjic will yun lee rob bowman',
      669: "some of sin city' most hard-boil citizen cross path with a few of it more revil inhabitants. crime thriller detect dystopia dominatrix murder suspen twin base on graphic novel dark hor comic neo-noir 3d mickey rourk jessica alba josh brolin robert rodriguez",
      670: "after the death of their love one in a tragic plane crash 'harrison ford' and kristin scott thoma find each other key in each other love one posess and realiz that they were have an affair and must figur out all the details. written by andi heitzth wife of polic sergeant dutch van den broek and the husband of politician kay chandler are kill in a plane crash. now dutch discov some anomali in what he told her befor she left and discov that she and chandler' husband were travel together. dutch then goe to chandler and tell her that he suspect that they were have an affair. he tell her that he want to know the truth; she tell him that she doesn't but she later join him and they grow close. drama romanc infidel politician airplan crash death death of husband polic sergeant death of wife harrison ford kristin scott thoma charl s. dutton sydney pollack",
      671: 'inspir by the incr event surround a treacher attempt to reach the summit of the world\' highest mountain, "everest" document the awe-inspir journey of two differ expedit challeng beyond their limit by one of the fiercest snowstorm ever encount by mankind. their mettl test by the harshest of element found on the planet, the climber will face nearli imposs obstacl as a lifelong obsess becom a breathtak struggl for survival. adventur drama mountain snow storm hike climb snow death blizzard mountain climb base on true event mount everest 3d jason clark jake gyllenha josh brolin baltasar kormákur',
      672: "jean-baptist grenouille, born in the stench of 18th centuri paris, develop a superior olfactori sense, which he use to creat the world' finest perfumes. however, hi work take a dark turn as he tri to preserv scent in the search for the ultim perfume. crime fantasi drama pari femal nuditi prostitut small town obsess orgi bad smell nuditi lone wolf lavend nose child prodigi fish market daughter supernatur geniu children' home death perfum ben whishaw simon chandler david calder tom tykwer",
      673: "the world' most shagadel spi continu hi fight against dr. evil. thi time, the diabol doctor and hi clone, mini-me, team up with a new foe -- '70 kingpin goldmember. while pursu the team of villain to stop them from world domination, austin get help from hi dad and an old girlfriend. comedi crime scienc fiction save the world submarin brother brother relationship clone spi helicopt gold submachin gun asteroid undercov belgium dutch car journey nightclub laser sumo ringer famili histori auto clown overweight man concili jame bond spoof duringcreditsst mike myer beyoncé knowl seth green jay roach",
      674: "set in futurist metro city, astro boy is about a young robot with incr power creat by a brilliant scientist in the imag of the son he ha lost. unabl to fulfil the griev man' expectations, our hero embark on a journey in search of acceptance, experienc betray and a netherworld of robot gladiators, befor he return to save metro citi and reconcil with the father who had reject him. anim action famili scienc fiction superhero nicola cage kristen bell bill nighi david bower",
      675: 'a wealthi entrepreneur secretli creat a theme park featur live dinosaur drawn from prehistor dna. befor open day, he invit a team of expert and hi two eager grandchildren to experi the park and help calm anxiou investors. however, the park is anyth but amu as the secur system go off-lin and the dinosaur escape. adventur scienc fiction exot island dna paleontolog tyrannosauru rex triceratop brontosauru electr fenc island dinosaur amu park theme park jurass park sam neill laura dern jeff goldblum steven spielberg',
      676: "cover the life and time of one of the west' most icon hero wyatt earp weav an intric tale of earp and hi friend and family. with a star stud cast, sweep cinematographi and authent costum wyatt earp led the way dure the western reviv in the 90's. drama action western gunsl gambl sheriff deputi sheriff wretch wyatt earp histor figur doc holliday kevin costner denni quaid gene hackman lawrenc kasdan",
      677: 'cia analyst jack ryan is drawn into an illeg war fought by the us govern against a colombian drug cartel. action drama thriller assassin spi ambush cia helicopt base on novel usa presid sniper fbi colombia drug traffic bomber mission of murder mercenari insurg coast guard spi war car bomb drug cartel conspiraci shootout infantri violenc jack ryan polit cover-up harrison ford willem dafo ann archer phillip noyc',
      678: 'huo an, the command of the protect squad of the western regions, wa frame by evil forc and becom enslaved. on the other hand, a roman gener escap to china after rescu the prince. the heroic duo meet in the western desert and a thrill stori unfolds. action drama adventur jacki chan john cusack adrien brodi daniel lee',
      679: "after leav the prison, the dwarf crimin calvin sim join to hi moron brother perci to steal an expen huge diamond in a jewelri for the mobster walken. they are chase by the police, and calvin hide the stone in the pur of the execut vanessa edwards, whose husband darryl edward want to have a baby. perci convinc calvin to dress like a babi and be left in front of the edwards' hou to get insid the hou and retriev the diamond. darryl and vanessa keep calvin for the weekend and decid to adopt him, while walken threaten darryl to get the stone back. comedi crime babi adopt marri coupl small person crimin marlon wayan shawn wayan kerri washington keenen ivori wayan",
      680: "in the midst of world war ii, the battl under the sea rage and the nazi have the upper hand as the alli are unabl to crack their war codes. however, after a wreck u-boat send out an so signal, the alli reali thi is their chanc to seiz the 'enigma code machine'. action drama thriller war submarin world war ii north atlant mission matthew mcconaughey bill paxton harvey keitel jonathan mostow",
      681: "widow u.s. presid andrew shepherd, one of the world' most power men, can have anyth he want -- and what he covet most is sydney ellen wade, a washington lobbyist. but shepherd' attempt at court her spark wild rumor and decim hi approv ratings. comedi drama romanc white hou usa presid new love widow wildlif conserv michael dougla annett bene michael j. fox rob reiner",
      682: "born in america and rai in an indian ashram, pitka return to hi nativ land to seek hi fortun as a spiritualist and self-help expert. hi skill are put to the test when he must get a brokenheart hockey player' marriag back on track in time for the man to help hi team win the stanley cup. comedi romanc sport ice hockey guru comedi bollywood india spiritualist broken heart self-help stanley cup chastiti ashram expert mike myer jessica alba justin timberlak marco schnabel",
      683: "it wa an ingeni enough plan: rob the riviera casino' count room dure an elvi imperson convention. but thoma murphi decid to keep all the money for himself and shot all hi partners, includ recently-fr ex-con michael zane. with $3.2 million at stake, the marshal servic close in, michael must track down murphy. action adventur comedi thriller crime casino submachin gun hold-up robberi elvi refer to elvi presley duringcreditsst kurt russel kevin costner courteney cox demian lichtenstein",
      684: 'bounti hunter seek shelter from a rage blizzard and get caught up in a plot of betray and deception. crime drama mysteri western bounti hunter wyom mountain narrat hangman stagecoach blizzard post civil war samuel l. jackson kurt russel jennif jason leigh quentin tarantino',
      685: 'when a much-publ ice-sk scandal strip them of their gold medals, two world-class athlet skirt their way back onto the ice via a loophol that allow them to compet togeth as a pair team. action comedi drama competit olymp game sport rivalri ice skate will ferrel jon heder will arnett josh gordon',
      686: "e.b., the easter bunny' teenag son, head to hollywood, determin to becom a drummer in a rock 'n' roll band. in la, he' taken in by fred after the out-of-work slacker hit e.b. with hi car. anim comedi famili coup d'etat slacker easter easter bunni aftercreditsst live action and anim russel brand jame marsden kaley cuoco tim hill",
      687: 'base on frank miller\' graphic novel, "300" is veri loo base the 480 b.c. battl of thermopylae, where the king of sparta led hi armi against the advanc persians; the battl is said to have inspir all of greec to band togeth against the persians, and help usher in the world\' first democracy. action adventur war evisc javelin shield armi fall from height ancient world s.a.t. minion gerard butler lena headey domin west zack snyder',
      688: "hard-to-crack ex-cia man, jack byrn and hi wife, dina head for the warmer clime of florida to meet son-in-law-to-be, greg focker' parents. unlik their happili match offspring, the futur in-law find themselv in a situat of opposit that definit do not attract. comedi romanc cia parent kid relationship florida anti-authoritarian upbr jew parents-in-law orderli just marri sex therapi bad father-in-law famili illegitim son ben stiller teri polo robert de niro jay roach",
      689: "a newli marri coupl who, in the process of start a family, learn mani of life' import lesson from their trouble-lov retriever, marley. pack with plenti of laugh to lighten the load, the film explor the high and low of marriage, matur and confront one' own mortality, as seen through the len of famili life with a dog. comedi famili journalist base on novel puppi dog duringcreditsst columnist anim lead owen wilson jennif aniston eric dane david frankel",
      690: "a supernatur tale set on death row in a southern prison, where gentl giant john coffey possess the mysteri power to heal people' ailments. when the cellblock' head guard, paul edgecomb, recogn coffey' miracul gift, he tri desper to help stave off the condemn man' execution. fantasi drama crime southern usa black peopl mental disabl base on novel heal death row jail guard great depress prison guard electr chair magic realism heal death row inmat 1930 tom hank michael clark duncan david mor frank darabont",
      691: 'restless and readi for adventure, four suburban biker leav the safeti of their subdivi and head out on the open road. but complic ensu when they cross path with an intimid band of new mexico biker known as the del fuegos. action adventur comedi midlif crisi road trip polit incorrect motorcycl gang biker film awkward travel writer middl age middl age man tim allen john travolta martin lawrenc walt becker',
      692: "when the sky realli is fall and saniti ha flown the coop, who will rise to save the day? togeth with hi hyster band of misfit friends, chicken littl must hatch a plan to save the planet from alien inva and prove that the world' biggest hero is a littl chicken. anim famili comedi fish small town space marin chicken alien best friend alien inva anim duringcreditsst 3d zach braff joan cusack dan molina mark dindal",
      693: "with hi wife' disappear have becom the focu of an inten media circus, a man see the spotlight turn on him when it' suspect that he may not be innocent. mysteri thriller drama base on novel marriag crisi disappear cheat husband miss person search parti crimin lawyer wife murder murder suspect miss wife ben affleck rosamund pike carri coon david fincher",
      694: 'wound to the brink of death and suffer from amnesia, jason bourn is rescu at sea by a fisherman. with noth to go on but a swiss bank account number, he start to reconstruct hi life, but find that mani peopl he encount want him dead. however, bourn realiz that he ha the combat and mental skill of a world-class spi – but who doe he work for? action drama mysteri thriller pari barcelona spain assassin base on novel secret ident amnesia sniper passport mission of murder lover escap shootout foot chase cell phone car chase multipl ident surveil camera hamburg germani fish boat langley virginia safe deposit box flashback hand to hand combat matt damon franka potent chri cooper doug liman',
      695: 'jame bond must unmask the mysteri head of the janu syndic and prevent the leader from util the goldeney weapon system to inflict devast reveng on britain. adventur action thriller cuba fal accu secret ident comput viru secret base secret intellig servic kgb satellit special car cossack electromagnet pul time bomb st. petersburg russia eject seat red armi pierc brosnan sean bean izabella scorupco martin campbel',
      696: "when the bodi of armi capt. elizabeth campbel is found on a georgia militari base, two investigators, warrant offic paul brenner and sara sunhill, are order to solv her murder. what they uncov is anyth but clear-cut. unseemli detail emerg about campbell' life, lead to alleg of a possibl militari coverup of her death and the involv of her father, lt. gen. joseph campbell. crime drama mysteri thriller suicid detect base on novel bondag gener paranoia nuditi u.s. armi investig polit cover-up murder betray conspiraci gang rape father daughter relationship videotap militari law john travolta madelein stow jame cromwel simon west",
      697: 'truman burbank is the star of "the truman show", a 24-hour-a-day "reality" tv show that broadcast everi aspect of hi life -- live and in color -- without hi knowledge. hi entir life ha been an unend soap opera for consumpt by the rest of the world. and everyon he know -- includ hi wife and hi best friend -- is realli an actor, paid to be part of hi life. comedi drama claustrophobia hidden camera dystopia realiti show make believ pretend jim carrey laura linney noah emmerich peter weir',
      698: 'thi is the extraordinari tale of two brother name mose and ramses, one born of royal blood, and one an orphan with a secret past. grow up the best of friends, they share a strong bond of free-spirit youth and good-natur rivalry. but the truth will ultim set them at odds, as one becom the ruler of the most power empir on earth, and the other the chosen leader of hi people! their final confront will forev chang their live and the world. adventur anim drama famili music mose egypt pyramid exodu kingdom govern ancient egypt hebrew pharaoh woman director val kilmer ralph fienn patrick stewart simon well',
      699: "two men get laid off and have to becom stay-at-hom dad when they can't find jobs, which inspir them to open their own day-car center. comedi famili competit success kindergarten children unemploy eddi murphi jeff garlin steve zahn steve carr",
      700: 'a dea agent and an undercov naval intellig offic who have been task with investig one anoth find they have been set up by the mob -- the veri organ the two men believ they have been steal money from. action comedi crime undercov undercov agent base on comic book money fugit bank robberi dea agent denzel washington mark wahlberg paula patton baltasar kormákur',
      701: 'when a professor develop a vaccin that elimin human allergi to dogs, he unwittingli upset the fragil balanc of power between cat and dog and touch off an epic battl for pet supremacy. the fur fli as the felin faction, led by mr. tinkles, squar off against wide-ey puppi lou and hi canin cohorts. comedi famili fight govern puppi allergi 3d jeff goldblum elizabeth perkin alexand pollock lawrenc guterman',
      702: "charli croker pull off the crime of a lifetime. the one thing that he didn't plan on wa be double-crossed. along with a drop-dead gorgeou safecracker, croker and hi team take off to re-steal the loot and end up in a pulse-pounding, pedal-to-the-met chase that careen up, down, abov and below the street of lo angeles. action crime venic california train station helicopt austria mountain gold subway hacker chase safe remak caper reveng murder heist doubl cross fast car boat chase lo angel explo convict father daughter relationship car chase tv news hollywood sign televi repair mini cooper mark wahlberg charliz theron edward norton f. gari gray",
      703: "dedic environ lawyer luci kelson goe to work for billionair georg wade as part of a deal to preserv a commun center. indeci and weak-wil georg grow depend on lucy' guidanc on everyth from legal matter to clothing. exasperated, luci give notic and pick harvard graduat june carter as her replacement. as lucy' time at the firm near an end, she grow jealou of june and ha second thought about leav george. romanc comedi new york parish hall romant comedi lawyer billionair environ law sandra bullock hugh grant alicia witt marc lawrenc",
      704: "in thi anim hit, a neurot worker ant in love with a rebelli princess rise to unlik stardom when he switch place with a soldier. sign up to march in a parade, he end up under the command of a bloodthirsti general. but he' actual been enlist to fight against a termit army. adventur anim comedi famili gener hero worker ant work assign war princess soldier individu friend woodi allen dan aykroyd ann bancroft eric darnel",
      705: 'four couples, all friends, descend on a tropic island resort. though one husband and wife are there to work on their marriage, the other just want to enjoy some fun in the sun. they soon find, however, that paradi come at a price: particip in coupl therapi session is mandatory. what start out as a cut-rat vacat turn into an examin of the common problem mani face. comedi romanc island marri coupl yoga tahiti coupl therapi beauti woman tropic aftercreditsst duringcreditsst french polynesia polynési françai vinc vaughn malin åkerman jason bateman peter billingsley',
      706: 'talent but unproven stock car driver cole trickl get a break and with the guidanc of veteran harri hogg turn head on the track. the young hotshot develop a rivalri with a fellow racer that threaten hi career when the two smash their cars. but with the help of hi doctor, cole just might overcom hi injuries-- and hi fear. adventur stock-car-rac daytona car crash tom crui robert duval nicol kidman toni scott',
      707: 'steve martin and bonni hunt return as head of the baker famili who, while on vacation, find themselv in competit with a rival famili of eight children, head by eugen levy, comedi holiday lake big famili father labor pain rivalri famili holiday steve martin eugen levi bonni hunt adam shankman',
      708: "thoma and hi fellow glader face their greatest challeng yet: search for clue about the mysteri and power organ known as wckd. their journey take them to the scorch, a desol landscap fill with unimagin obstacles. team up with resist fighters, the glader take on wckd’ vastli superior forc and uncov it shock plan for them all. action base on novel resist maze post-apocalypt dystopia infect on the run escap zombi storm disea desert sewer antidot corpor viru runner citi ruin immun dylan o'brien kaya scodelario thoma brodie-sangst we ball",
      709: 'liz gilbert had everyth a modern woman is suppo to dream of have – a husband, a hou and a success career – yet like so mani others, she found herself lost, confu and search for what she realli want in life. newli divorc and at a crossroads, gilbert step out of her comfort zone, risk everyth to chang her life, embark on a journey around the world that becom a quest for self-discovery. in her travels, she discov the true pleasur of nourish by eat in italy, the power of prayer in india and, final and unexpectedly, the inner peac and balanc of true love in bali. drama indonesia femal protagonist india divorc bali julia robert jame franco javier bardem ryan murphi',
      710: "jack' lavish, fast-pac lifestyl chang one christma night when he stumbl into a groceri store holdup and disarm the gunman. the next morn he wake up in bed lie next to kate, hi colleg sweetheart he left in order to pursu hi career, and to the horrifi discoveri that hi former life no longer exists. as he stumbl through thi altern suburban universe, jack find himself at a crossroad where he must choo between hi high-pow career and the woman he loves. comedi drama romanc fantasi workahol second chanc guardian angel christma career vs famili life repriorit nicola cage téa leoni don cheadl brett ratner",
      711: 'when hi peac life is threaten by a high-tech assassin, former black-op agent, frank mose reassembl hi old team in a last ditch effort to surviv and uncov hi assailants. action adventur comedi crime thriller cia retir shot to death sniper rifl retir femal spi alarm bruce willi john malkovich helen mirren robert schwentk',
      712: 'a star quarterback get knock out of the game and an unknown third stringer is call in to replac him. the unknown give a stun perform and forc the age coach to reevalu hi game plan and life. a new co-owner/presid add to the pressur of winning. the new owner must prove her self in a male domin world. drama american footbal trainer train american footbal coach sport american footbal stadium al pacino cameron diaz denni quaid oliv stone',
      713: 'base on the novel by the same name from nichola evans, the talent robert redford present thi medit famili drama set in the countri side. redford not onli direct but also star in the roll of a cowboy with a magic talent for healing. drama romanc love triangl new york montana attach to natur confid horseback ride hor ride accid career woman ranch hor whisper trauma countri life marriag crisi crisi travel mother daughter relationship anim natur robert redford kristin scott thoma sam neill robert redford',
      714: 'cab driver max pick up a man who offer him $600 to drive him around. but the promi of easi money sour when max realiz hi fare is an assassin. drama crime thriller california taxi assassin hostag taxi driver fbi hitman polic lo angel murder crime crimin gun violenc tom crui jami foxx jada pinkett smith michael mann',
      715: "in ancient egypt, peasant mathayu is hire to exact reveng on the power memnon and the sorceress cassandra, who are readi to overtak balthazar' village. amid betrayals, thieves, abduct and more, mathayu strive to bring justic to hi complic world. action fantasi adventur egypt templ dwayn johnson kelli hu michael clark duncan chuck russel",
      716: "under the watch eye of hi mentor, captain mike kennedy, probationari firefight jack morrison matur into a season veteran at a baltimor fire station. however, jack ha reach a crossroad as the sacrif he' made have put him in harm' way innum time and significantli impact hi relationship with hi wife and kids. drama action thriller ledg practic joke joaquin phoenix john travolta jacinda barrett jay russel",
      717: 'in an innoc heartland city, five are shot dead by an expert sniper. the polic quickli identifi and arrest the culprit, and build a slam-dunk case. but the accu man claim he\' innoc and say "get jack reacher." reacher himself see the news report and turn up in the city. the defen is immen relieved, but reacher ha come to buri the guy. shock at the accused\' request, reacher set out to confirm for himself the absolut certainti of the man\' guilt, but come up with more than he bargain for. crime drama thriller base on novel sniper investig polic quarri tom crui rosamund pike richard jenkin christoph mcquarri',
      718: "on a remot former submarin refuel facil call aquatica, a team of scientist are search for a cure for alzheimer' disease. dr. susan mcalest genet engin three mako sharks, intend to increa their brain capac so that they can harvest the tissu as a cure for alzheimer's. unfortunately, the increa brain capac also make the shark smarter, faster, and more dangerous. aquatica' financ backer are skeptic and nervou about the tests, and send a corpor execut to visit the facility. action scienc fiction thriller shark attack shark alzheimer' disea killer shark no open credit thoma jane saffron burrow ll cool j renni harlin",
      719: 'a compil of interviews, rehear and backstag footag of michael jackson as he prepar for hi seri of sold-out show in london. music documentari pop star music concert aftercreditsst duringcreditsst michael jackson orianthi kenni ortega kenni ortega',
      720: 'as an epidem of a lethal airborn viru - that kill within day - rapidli grows, the worldwid medic commun race to find a cure and control the panic that spread faster than the viru itself. drama thriller scienc fiction save the world mutat infect termin ill quarantin outbreak medic vaccin lethal viru scientist epidem matt damon gwyneth paltrow kate winslet steven soderbergh',
      721: "two childhood friends, a new york hairstylist and a wanna-b musician, get mixed-up with the mob and are forc to deliv $50,000 to australia, but thing go all wrong when the money is lost to a wild kangaroo. comedi adventur crime money deliveri fool australia hoodlum kangaroo jerri o'connel anthoni anderson estella warren david mcnalli",
      722: 'when coralin move to an old house, she feel bore and neglect by her parents. she find a hidden door with a brick up passage. dure the night, she cross the passag and find a parallel world where everybodi ha button instead of eyes, with care parent and all her dream come true. when the other mother invit coralin to stay in her world forever, the girl refu and find that the altern realiti where she is trap is onli a trick to lure her. anim famili dream eye stuf anim parallel world button new home secret door aftercreditsst duringcreditsst dakota fan teri hatcher jennif saunder henri selick',
      723: 'when a deadli airborn viru threaten to wipe out the northeastern unit states, teacher elliott moor (mark wahlberg) and hi wife (zooey deschanel) flee from contamin citi into the countrysid in a fight to discov the truth. is it terrorism, the accid relea of some toxic militari bio weapon -- or someth even more sinister? john leguizamo and betti buckley co-star in thi thriller from writer-director m. night shyamalan. thriller scienc fiction tree natur disast crisi park strang behavior mark wahlberg zooey deschanel john leguizamo m. night shyamalan',
      724: "jade ex-cia oper john creasi reluctantli accept a job as the bodyguard for a 10-year-old girl in mexico city. they clash at first, but eventu bond, and when she' kidnap he' consum by furi and will stop at noth to save her life. action drama thriller crime mexico cia kidnap diari bibl bodyguard stuf anim cell phone alcohol grenad launcher bloodsh swim meet denzel washington dakota fan marc anthoni toni scott",
      725: "the tale of a workahol dad-turned-dog who find that be man' best friend show him the most import job - be a great dad. comedi famili father son relationship parent kid relationship workahol wife husband relationship transform bodi exchang daughter lawyer dog famili turn into anim tim allen kristin davi danni glover brian robbin",
      726: 'join uptight david starski and laid-back ken "hutch" hutchinson as they\'r pair for the first time as undercov cops. the new partner must overcom their differ to solv an import case with help from street inform huggi bear and persua crimin ree feldman. comedi crime inform jump from a rooftop surveil footag ben stiller owen wilson snoop dogg todd phillip',
      727: "meet howard langston, a salesman for a mattress compani is constantli busi at hi job, and he also constantli disappoint hi son, after he miss hi son' karat exposition, hi son tell howard that he want for christma is an action figur of hi son' televi hero, he tri hard to to make it up to him. unfortun for howard, it is christma eve, and everi store is sold out of turbo man, now howard must travel all over town and compet with everybodi el to find a turbo man action figure. famili comedi holiday christma parti santa clau toy puppet christma turboman navidad arnold schwarzenegg phil hartman sinbad brian levant",
      728: 'in the final day of world war ii, the nazi attempt to use black magic to aid their die cause. the alli raid the camp where the ceremoni is take place, but not befor a demon - hellboy - ha alreadi been conjured. join the alli forces, hellboy eventu grow to adulthood, serv the cau of good rather than evil. fantasi action scienc fiction black magic fistfight cover-up superhero paranorm phenomena narrat from grave demon occult combat photographi reanim corp duringcreditsst ron perlman selma blair rupert evan guillermo del toro',
      729: 'jan schlickmann is a cynic lawyer who goe out to "get rid of" a case, onli to find out it is potenti worth millions. the case becom hi obsession, to the extent that he is will to give up everyth - includ hi career and hi clients\' goals, in order to continu the case against all odds. drama success advanc right and justic leukemia lawyer busi start-up john travolta robert duval toni shalhoub steven zaillian',
      730: "in the town of blith hollow, norman babcock is a boy who can speak to the dead, but no one besid hi eccentr new friend, neil, believ hi abil is real. one day, norman' estrang eccentr uncl tell him of an import annual ritual he must take up to protect the town from an cur cast by a witch it condemn centuri ago. eventually, norman decid to cooperate, but thing don't go accord to plan. now, a magic storm of the witch threaten blith hollow as the accur dead rise. togeth with unexpect new companions, norman struggl to save hi town, onli to discov the horrif truth of the curse. with that insight, norman must resolv the crisi for good as onli he can. famili anim adventur comedi medium stop motion cur jock ghost commun with the dead aftercreditsst deal with the past witch trial child witch empathi strang kodi smit-mcph tucker albrizzi jodel ferland sam fell",
      731: 'hire by a power member of the russian mafia to aveng an fbi sting that left hi brother dead, the perfectionist jackal prove an elu target for the men charg with the task of bring him down: a deputi fbi boss and a former ira terrorist. action thriller adventur crime fbi cold war hitman bruce willi richard gere sidney poitier michael caton-jon',
      732: "michael jen is a geniu who' hire – and paid handsom – by high-tech firm to work on highli sensit projects, after which hi short-term memori is era so he' incap of breach security. but at the end of a three-year job, he' told he isn't get a paycheck and instead receiv a mysteri envelope. in it are clue he must piec togeth to find out whi he wasn't paid – and whi he' now in hot water. action adventur mysteri scienc fiction thriller propheci engin scientist millionair ben affleck aaron eckhart uma thurman john woo",
      733: 'talli atwat ha a dream: to be a prime-tim network newscaster. she pursu thi dream with noth but ambition, raw talent and a homemad demo tape. warren justic is a brilliant, hard edged, veteran newsman. he see talli ha talent and becom her mentor. tally’ career take a meteor rise and she and warren fall in love. the romanc that result is as inten and reveal as televi news itself. yet, each break story, everi videotap crisi that bring them together, also threaten to drive them apart... drama romanc miami televi career vitamin b report robert redford michel pfeiffer stockard chan jon avnet',
      734: 'onc upon a time... in the far away kingdom of dor... live a brave and virtuou mou with comic over ear who dreamt of becom a knight. banish from hi home for have such lofti ambitions, despereaux set off on an amaz adventur with hi good-heart rat friend roscuro, who lead him, at long last, on a veri nobl quest to rescu an endang princess and save an entir kingdom from darkness. adventur anim famili loyalti totalitarian regim mou forgiv honor unlik friendship courag chivalri anim lead matthew broderick dustin hoffman emma watson robert stevenhagen',
      735: "cabbie-turned-chauffeur jimmi tong learn there is realli onli one rule when you work for playboy millionair clark devlin : never touch devlin' prize tuxedo. but when devlin is temporarili put out of commiss in an explo accident, jimmi put on the tux and soon discov that thi extraordinari suit may be more black belt than black tie. pair with a partner as inexperienc as he is, jimmi becom an unwit secret agent. thriller action comedi scienc fiction bomb intellig chauffeur wound secret agent head injuri jacki chan jennif love hewitt jason isaac kevin donovan",
      736: 'a passeng train ha been hijack by an electron expert and turn into an untrac command center for a weapon satellite. he ha plan to blow up washington dc and onli one man can stop him, former navi seal casey ryback. action thriller terrorist pentagon satellit navi seal train steven seagal eric bogosian everett mcgill geoff murphi',
      737: 'jack ryan, as a young covert cia analyst, uncov a russian plot to crash the u.s. economi with a terrorist attack. action drama thriller london england corrupt cia terrorist sniper explo intellig russia murder conspiraci surveil agent jack ryan u.s. marin rehab analyst chri pine keira knightley kevin costner kenneth branagh',
      738: "a stori base on the life of a struggl long island singl mom who becam one of the country' most success entrepreneurs. drama comedi factori inventor strong woman biographi base on true stori stolen patent jennif lawrenc bradley cooper robert de niro david o. russel",
      739: "in london for the prime minister' funeral, mike ban discov a plot to assassin all the attend world leaders. action crime thriller london england terrorist terrorist attack gerard butler aaron eckhart morgan freeman babak najafi",
      740: 'two hundr year after lt. ripley died, a group of scientist clone her, hope to breed the ultim weapon. but the new ripley is full of surpri … as are the new aliens. ripley must team with a band of smuggler to keep the creatur from reach earth. scienc fiction horror action android mercenari dystopia sequel alien betray impal clone scientist flamethrow disembowel smuggler gene manipul man in wheelchair breed genet engin regen xenomorph alien queen explo decompress swim underwat sigourney weaver winona ryder brad dourif jean-pierr jeunet',
      741: 'a marksman live in exil is coax back into action after learn of a plot to kill the president. ultim double-cross and frame for the attempt, he goe on the run to track the real killer and find out who exactli set him up, and why. action drama mysteri thriller crime corrupt sniper senat conspiraci of murder childless rifl sniper rifl fbi agent mark wahlberg michael peña danni glover antoin fuqua',
      742: 'an orphan boy rai by underground creatur call boxtrol come up from the sewer and out of hi box to save hi famili and the town from the evil exterminator, archibald snatcher. anim comedi famili fantasi base on novel stop motion father daughter relationship unlik friendship duringcreditsst ben kingsley isaac hempstead-wright ell fan anthoni stacchi',
      743: "salli and gillian owens, born into a magic family, have mostli avoid witchcraft themselves. but when gillian' viciou boyfriend, jimmi angelov, die unexpectedly, the owen sister give themselv a crash cour in hard magic. with policeman gari hallet grow suspicious, the girl struggl to resurrect angelov -- and unwittingli inject hi corp with an evil spirit that threaten to end their famili line. drama fantasi comedi witch magic sorceri love cur famili cur sandra bullock nicol kidman evan rachel wood griffin dunn",
      744: 'an ordinari lego mini-figure, mistakenli thought to be the extraordinari masterbuilder, is recruit to join a quest to stop an evil lego tyrant from glu the univ together. adventur anim comedi famili fantasi father son relationship creativ friendship part live action toy base on toy fall in love super power duringcreditsst differ world lego batman chri pratt will ferrel elizabeth bank phil lord',
      745: 'after her triumph at the miss unit state pageant, fbi agent graci hart becom an overnight sensat -- and the new "face of the fbi." but it\' time to spring into action again when the pageant\' winner, cheryl, and emcee, stan, are abducted. action comedi ransom press confer ship miss america fbi agent sandra bullock regina king enriqu murciano john pasquin',
      746: 'in post-apocalypt england, an american volunt and a british survivor team up to fight off a brood of fire-breath dragon seek to return to global domin after centuri of rest underground. the brit -- lead a clan of survivor to hunt down the king of the dragon -- ha much at stake: hi mother wa kill by a dragon, but hi love is still alive. adventur action fantasi dragon evolut fire chief anim map theatr audienc dragonslay tunnel construct fire repel drill iodin christian bale matthew mcconaughey izabella scorupco rob bowman',
      747: 'lo angeles, 1949. ruthless, brooklyn-born mob king mickey cohen run the show in thi town, reap the ill-gotten gain from the drugs, the guns, the prostitut and — if he ha hi way — everi wire bet place west of chicago. and he doe it all with the protect of not onli hi own paid goons, but also the polic and the politician who are under hi control. it’ enough to intimid even the bravest, street-harden cop… except, perhaps, for the small, secret crew of lapd outsid led by sgt. john o’mara and jerri wooter who come togeth to tri to tear cohen’ world apart. crime drama action thriller lo angel gangster josh brolin ryan gosl nick nolt ruben fleischer',
      748: 'when a coupl of lazi hunter-gath are banish from their primit village, they set off on an epic journey through the ancient world. comedi adventur templ slaveri stone age circumci hebrew cavemen prehistor adventur duringcreditsst prehistor time prehistor man jack black michael cera olivia wild harold rami',
      749: "newli elect presid nelson mandela know hi nation remain racial and econom divid in the wake of apartheid. believ he can bring hi peopl togeth through the univ languag of sport, mandela ralli south africa' rugbi team as they make their histor run to the 1995 rugbi world cup championship match. drama histori stadium south africa apartheid nelson mandela sport nation rugbi presid racism poverti celebr duringcreditsst morgan freeman matt damon toni kgorog clint eastwood",
      750: "handsome, unflapp u.s. congressman stephen collin is the futur of hi polit party: an honor appoint who serv as the chairman of a committ overs defen spending. all eye are upon the rise star to be hi party' contend for the upcom presidenti race. until hi research assistant/mistress is brutal murder and buri secret come tumbl out. action corrupt assassin detect journalist assassin newspap congress editor-in-chief conspiraci of murder polit elect campaign govern murder thriller blog report russel crow ben affleck rachel mcadam kevin macdonald",
      751: 'two romantically-engag corpor spi team up to manipul a corpor race to corner the market on a medic innov that will reap huge profit and enabl them to lead an extravag lifestyl together. romanc comedi crime spi clive owen julia robert paul giamatti toni gilroy',
      752: "new producer, tim o'hara get himself fire for unwillingli compromi hi bosses' daughter dure a live transmission. a littl later, he wit the crash of a small martian spacecraft, realiz hi one-tim chanc of deliv a stori that will rock the earth. sinc tim took the origin but scaled-down spaceship with him, the martian follow him to retriev it. comedi drama famili scienc fiction alien martian base on tv seri fish out of water jeff daniel elizabeth hurley daryl hannah donald petri",
      753: 'a secret servic agent is frame as the mole in an assassin attempt on the president. he must clear hi name and foil anoth assassin attempt while on the run from a relentless fbi agent. action thriller crime usa presid agent michael dougla kiefer sutherland eva longoria clark johnson',
      754: 'when earth astronaut capt. chuck baker arriv on planet 51 -- a world reminisc of american suburbia circa 1950 -- he tri to avoid capture, recov hi spaceship and make it home safely, all with the help of an empathet littl green being. scienc fiction anim famili comedi adventur fli saucer alien life-form spaceship alien alien planet planet duringcreditsst dwayn johnson seann william scott jessica biel jorg blanco',
      755: 'en rout to the honeymoon of william riker to deanna troi on her home planet of betazed, captain jean-luc picard and the crew of the u.s.s. enterpri receiv word from starfleet that a coup ha result in the instal of a new romulan polit leader, shinzon, who claim to seek peac with the human-back unit feder of planets. onc in enemi territory, the captain and hi crew make a startl discovery: shinzon is human, a slave from the romulan sister planet of remus, and ha a secret, shock relationship to picard himself. scienc fiction action adventur thriller clone assassin ambush feder starfleet enterprise- romulu android senat self sacrif telepathi weapon romulan space opera patrick stewart jonathan frake brent spiner stuart baird',
      756: 'a revenge-seek gold digger marri a woman beverli hill lawyer with the intent of make a kill in the divorce. crime comedi romanc california assassin infidel fetish hitman tycoon court satir lawyer inherit divorc georg clooney catherin zeta-jon edward herrmann joel coen',
      757: 'slow by age and fail eyesight, crack baseb scout gu lobel take hi grown daughter along as he check out the final prospect of hi career. along the way, the two renew their bond, and she catch the eye of a young player-turned-scout. drama romanc women baseb pitcher home run age sport talent-scout cigar smoke poor eyesight boston red sox draft motel room baseb scout fail eyesight blurri vision blur sight clint eastwood ami adam justin timberlak robert lorenz',
      758: "as a season homicid detective, thoma craven ha seen the bleakest side of humanity. but noth prepar him for the toughest investig of hi life: the search for hi onli daughter emma' killer. now, he is on a person mission to uncov the disturb secret surround her murder, includ corpor corruption, govern collu and emma' own mysteri life. crime drama mysteri thriller murder violenc death of daughter homicid detect mel gibson ray winston danni huston martin campbel",
      759: "a research at chicago' natur histori museum return from south america with some crate contain hi findings. when the crate arriv at the museum without the owner there appear to be veri littl inside. however, polic discov gruesom murder on the cargo ship that brought the crate to the us and then anoth murder in the museum itself. horror mysteri thriller chicago base on novel monster museum pile of dead bodi god dead bodi anthropologist indian tribe amazon jungl penelop ann miller tom sizemor linda hunt peter hyam",
      760: "the mafia' paul vitti is back in prison and will need some seriou counsel when he get out. naturally, he return to hi analyst dr. ben sobel for help and find that sobel need some seriou help himself as he ha inherit the famili practice, as well as an excess stock of stress. comedi crime prison gold therapist gangster robert de niro billi crystal lisa kudrow harold rami",
      761: 'two veteran new york citi detect work to identifi the possibl connect between a recent murder and a case they believ they solv year ago; is there a serial killer on the loose, and did they perhap put the wrong person behind bars? action crime drama thriller reveng murder plot twist dirti cop robert de niro carla gugino 50 cent jon avnet',
      762: 'renegad fbi agent art jeffri protect a nine-year-old autist boy who ha crack the government\' new "unbreakable" code. action crime drama thriller assassin loss of famili autism fbi bangkok nation secur agenc (nsa) boy child in peril fbi agent autist savant bruce willi alec baldwin miko hugh harold becker',
      763: 'a lo angel journalist befriend a homeless juilliard-train musician, while look for a new articl for the paper. drama newspap cello music violin lo angel robert downey jr. jami foxx catherin keener joe wright',
      764: 'world war i ha left golfer rannulph junuh a poker-play alcoholic, hi perfect swing gone. now, however, he need to get it back to play in a tournament to save the financ ravag golf cour of a long-ago sweetheart. help arriv in the form of mysteri caddi bagger vance. fantasi drama competit world war i great depress caddi savannah matt damon bruce mcgill charliz theron robert redford',
      765: 'almost famou is an autobiograph inspir film about a 15-year-old who is hire by roll stone magazin to follow and interview a rock band dure their tour. a film about grow up, first love, disappointment, and the life of a rock star. drama music hotel room san diego drug addict stewardess overdo groupi music journalist black sabbath rock concert swim pool base on true stori promiscu come of age on the road domin mother reconcili semi autobiograph innoc lost bu trip aspir writer kate hudson billi crudup franc mcdormand cameron crow',
      766: 'garfield is back and thi time garfield and hi canin sidekick odi follow their owner, jon arbuckle, to england, the u.k. may never recover, as garfield is mistaken for a look-alike, regal cat who ha inherit a castle. anim comedi famili london england cat mistak in person luxuri wretch nobil garfield bill murray jennif love hewitt billi connolli tim hill',
      767: "ice cube star as dariu stone, a thrill-seek troublemak whose crimin record and extrem sport obsess make him the perfect candid to be the newest xxx agent. he must save the u.s. govern from a deadli conspiraci led by five-star gener and secretari of defen georg deckert (play by willem dafoe). action adventur crime drama mysteri thriller washington d.c. helicopt usa presid gener coup d'etat militari prison coup agent insurg secretari of defen potu ice cube samuel l. jackson willem dafo lee tamahori",
      768: "in an altern world, human and vampir have war for centuries. after the last vampir war, the veteran warrior priest live in obscur with other human insid one of the church' wall cities. when the priest' niec is kidnap by vampires, the priest break hi vow to hunt them down. he is accompani by the niece' boyfriend, who is a wasteland sheriff, and a former warrior priestess. action scienc fiction fantasi thriller horror vampir crucifixion post-apocalypt dystopia vampir hunter disobey niec dark hero paul bettani karl urban cam gigandet scott stewart",
      769: 'the sailor of legend is frame by the goddess eri for the theft of the book of peace, and must travel to her realm at the end of the world to retriev it and save the life of hi childhood friend princ proteus. famili anim adventur princ water monster brad pitt catherin zeta-jon michel pfeiffer tim johnson',
      770: 'in the year 2047 a group of astronaut are sent to investig and salvag the long lost starship "event horizon". the ship disappear mysteri 7 year befor on it maiden voyag and with it return come even more mysteri as the crew of the "lewi and clark" discov the real truth behind it disappear and someth even more terrifying. horror scienc fiction mysteri space marin nuditi nightmar hallucin cryogen space travel black hole insan delu crew altern dimen evil spirit hellgat religion explo violenc burn man rescu team flashback supernatur power trap in space distress signal derelict ship laurenc fishburn sam neill kathleen quinlan paul w.s. anderson',
      771: 'a griev doctor is be contact by hi late wife through hi patient near death experiences. drama pregnanc and birth voic dragonfli car crash jungl hospit doctor humanitarian spirit kevin costner joe morton ron rifkin tom shadyac',
      772: 'lee blanchard and bucki bleichert are former boxers-turned-cop in 1940 lo angel and, when an aspir young actress turn up dead, blanchard and bleichert must grappl with corruption, narcissism, stag film and famili mad as they pursu the killer. drama pornographi observ lo angel murder hunt josh hartnett scarlett johansson aaron eckhart brian de palma',
      773: "the adventur of the lafayett escadrille, young american who volunt for the french militari befor the u.s. enter world war i, and becam the country' first fighter pilots. action adventur drama histori romanc war world war i biplan jame franco david ellison jean reno toni bill",
      774: 'a court martial gener ralli togeth 1200 inmat to rise against the system that put him away. action drama thriller prison gener robert redford jame gandolfini mark ruffalo rod luri',
      775: 'set in the 22nd century, when a batter salvag ship send out a distress signal, the season crew of the rescu hospit ship nova-17 responds. what they find is a black hole--that threaten to destroy both ships--and a mysteri survivor whose bodi quickli mutat into a monstrou and deadli form. horror scienc fiction thriller black peopl starship futur star supernova blast jame spader angela bassett robert forster walter hill',
      776: 'a burglar fall for an heiress as she die in hi arms. when he learn that he ha the gift of reincarnation, he set out to save her. drama fantasi mysteri romanc base on novel colin farrel jessica brown findlay russel crow akiva goldsman',
      777: "in new york city, clari fray, a seemingli ordinari teenager, learn that she is descend from a line of shadowhunt — half-angel warrior who protect human from evil forces. after her mother disappears, clari join forc with a group of shadowhunt and enter downworld, an altern realm fill with demons, vampires, and a host of other creatures. clari and her companion must find and protect an ancient cup that hold the key to her mother' future. action adventur drama mysteri romanc fantasi angel vampir werewolf warlock downworld shadowhunt demon hunter base on young adult novel lili collin jami campbel bower kevin zeger harald zwart",
      778: 'a crew of miniatur alien oper a spaceship that ha a human form. while tri to save their planet, the alien encount a new problem, as their ship becom smitten with an earth woman. comedi scienc fiction adventur famili new york captain starship new love earth friendship crew car crash space alien surviv planet duringcreditsst eddi murphi elizabeth bank gabriel union brian robbin',
      779: "dahlia william and her daughter cecelia move into a rundown apart on new york' roosevelt island. she is current in midst of divorc proceed and the apartment, though near an excel school for her daughter, is all she can afford. from the time she arrives, there are mysteri occurr and there is a constant drip from the ceil in her daughter' bedroom. drama horror thriller base on novel water remak teacher divorc apart ghost manhattan, new york citi jennif connelli john c. reilli tim roth walter sall",
      780: 'video store clerk ed agr to have hi life film by a camera crew for a tv network. comedi tv show tv station simul realiti realiti tv tv star tv rate matthew mcconaughey woodi harrelson salli kirkland ron howard',
      781: "the adventur of a father and hi young daughter, in their search for a long lost book that will help reunit a missing, close relative. adventur famili fantasi book fairi tale eavesdrop adventur writer' block brendan fraser sienna guillori andi serki iain softley",
      782: "down these mean street a man must come. a hero born, murdered, and born again. when a rooki cop name denni colt return from the beyond as the spirit, a hero whose mission is to fight against the bad forc from the shadow of central city, the octopu who kill anyon unfortun enough to see hi face who ha other plans. he' go to wipe out the entir city. action comedi thriller crime scienc fiction secret ident robber mask frog base on comic strip back from the dead gabriel macht scarlett johansson samuel l. jackson frank miller",
      783: 'art dealer, charl mortdecai, search for a stolen paint rumor to contain a secret code that gain access to hidden nazi gold. comedi adventur base on novel paint debt art dealer stolen paint johnni depp gwyneth paltrow ewan mcgregor david koepp',
      784: "a man name farmer set out to rescu hi kidnap wife and aveng the death of hi son -- two act commit by the krugs, a race of animal-warrior who are control by the evil gallian. adventur fantasi action drama fiction place monster loss of famili new love hero love of one' life magic fairi tale villain kingdom enchant bad power son heir to the throne motherli love wizardri reveng royalti famili base on video game mediev jason statham john rhys-davi ray liotta uwe boll",
      785: "beyond border is an epic tale of the turbul romanc between two star-cross lover set against the backdrop of the world' most danger hot spots. academi award winner angelina joli star as sarah jordan, an american live in london in 1984. she is marri to henri bauford son of a wealthi british industrialist, when she encount nick callahan a renegad doctor, whose impass plea for help to support hi relief effort in war-torn africa move her deeply. as a result, sarah embark upon a journey of discoveri that lead to danger, heartbreak and romanc in the far corner of the world. drama romanc adventur war london england cia landmin love of one' life cambodia ethiopia chechnya foreign aid angelina joli clive owen teri polo martin campbel",
      786: 'take place 500 year after the havoc in heaven, the tang priest is appoint by buddha to go to the west to fetch the sacr scriptures, onli to accid free the monkey king. with ladi white (gong li) aim to break up the team assembl to defeat her, the monkey king must fight in order to save hi world! action adventur fantasi monkey king aaron kwok gong li william feng soi cheang',
      787: 'as world war ii rages, the elit sixth ranger battalion is given a mission of heroic proportions: push 30 mile behind enemi line and liber over 500 american prison of war. action histori war base on novel world war ii prison of war narrat archiv footag rescu mission soldier 1940 inspir by true event fiction histori benjamin bratt jame franco conni nielsen john dahl',
      788: 'deadpool tell the origin stori of former special forc oper turn mercenari wade wilson, who after be subject to a rogu experi that leav him with accel heal powers, adopt the alter ego deadpool. arm with hi new abil and a dark, twist sen of humor, deadpool hunt down the man who nearli destroy hi life. action adventur comedi anti hero mercenari marvel comic superhero base on comic book break the fourth wall aftercreditsst duringcreditsst self heal ryan reynold morena baccarin ed skrein tim miller',
      789: 'eddi murphi star as an over-the-top televi evangelist who find a way to turn televi home shop into a religi experience, and take america by storm. drama comedi salesclerk televi tv rate guru televi produc eddi murphi jeff goldblum kelli preston stephen herek',
      790: 'u.s. navi seal chri kyle take hi sole mission—protect hi comrades—to heart and becom one of the most lethal sniper in american history. hi pinpoint accuraci not onli save countless live but also make him a prime target of insurgents. despit grave danger and hi struggl to be a good husband and father to hi famili back in the states, kyle serv four tour of duti in iraq. however, when he final return home, he find that he cannot leav the war behind. war action sniper biographi iraq navi seal u.s. soldier bradley cooper sienna miller kyle gallner clint eastwood',
      791: "a teenag team up with the daughter of young adult horror author r.l. stine after the writer' imaginari demon are set free on the town of madison, delaware. adventur horror comedi base on novel magic fantasi werewolf famili ventriloquist dummi book come to life 3d jack black dylan minnett odeya rush rob letterman",
      792: "shortli after david abbott move into hi new san francisco digs, he ha an unwelcom visitor on hi hands: winsom elizabeth martinson, who assert that the apart is her -- and promptli vanishes. when she start appear and disappear at will, david think she' a ghost, while elizabeth is convinc she' alive. comedi fantasi romanc coma base on novel workahol flirt architect romant comedi ghost landscap architect ree witherspoon mark ruffalo donal logu mark water",
      793: "the flintston are at it again. the flintston and the rubbl head for rock vega with fred hope to court the love wilma. noth will stand in the way of love, except for the conniv chip rockefel who is the playboy born in baysvil but who ha made it in the cutthroat town of rock vegas. will fred win wilma' love? scienc fiction comedi famili romanc waitress marriag propo flirt stone age best friend dinosaur mark addi stephen baldwin kristen johnston brian levant",
      794: "combat ha taken it toll on rambo, but he' final begun to find inner peac in a monastery. when rambo' friend and mentor col. trautman ask for hi help on a top secret mission to afghanistan, rambo declin but must reconsid when trautman is captured. action adventur thriller war competit submachin gun soviet union liber russian soviet troop thailand freedom fighter afghanistan war on freedom machinegun mujahid realiti show western japan food soap opera sylvest stallon richard crenna kurtwood smith peter macdonald",
      795: 'a light heart comedi about the begin of profess american football. when a decor war hero and colleg all star is tempt into play profess football. everyon see the chanc to make some big money, but when a report dig up some dirt on the war hero... everyon could lose out. comedi romanc drama american footbal sport team stadium hero success sponsorship polic game coach woman report the big game georg clooney rené zellweg john krasinski georg clooney',
      796: 'when hi long-lost outlaw father returns, tommi "white knife" stockburn goe on an adventure-fil journey across the old west with hi five brothers. comedi western wild west adam sandler taylor lautner steve buscemi frank coraci',
      797: 'in new york city, an estrang coupl who wit a murder are reloc to small-town wyom as part of a witness-protect program. comedi wit protect comedi duringcreditsst hugh grant sarah jessica parker mari steenburgen marc lawrenc',
      798: 'two recent laid-off men in their 40 tri to make it as intern at a success internet compani where their manag are in their 20s. comedi job interview loss of job intern refer to googl new job laid off transamerica pyramid owen wilson vinc vaughn rose byrn shawn levi',
      799: 'in a world ravag by a viru infection, turn it victim into the undead, alic continu on her journey to find survivor and lead them to safety. her deadli battl with the umbrella corpor reach new heights, but alic get some unexpect help from an old friend. a new lead that promi a safe haven from the undead take them to lo angeles, but when they arriv the citi is overrun by thousand of undead - and alic and her comrad are about to step into a deadli trap. action adventur horror scienc fiction post-apocalypt dystopia undead biohazard evil corpor resid evil zombi base on video game duringcreditsst 3d milla jovovich wentworth miller ali larter paul w.s. anderson',
      800: 'the stori of the tuskeg airmen, the first african-american pilot to fli in a combat squadron dure world war ii. drama action adventur histori war world war ii fighter pilot fighter plane bryan cranston david oyelowo cuba good jr. anthoni hemingway',
      801: "a hotshot lawyer get more than he bargain for when he learn hi new boss is lucif himself. drama horror mysteri thriller child abu southern usa obsess subway nuditi bibl seduct hallucin ambit devil' son marriag crisi pact with the devil crook lawyer evil spirit satan religion lust courtroom temptat law firm manhattan, new york citi seven deadli sin ethic gainesvil florida keanu reev al pacino charliz theron taylor hackford",
      802: "while in hi teens, donni father a son, todd, and rai him as a singl parent up until todd' 18th birthday. now, after not see each other for years, todd' world come crash down when donni resurfac just befor todd' wedding. comedi deadbeat dad cheat fiancé teacher student sex brother sister incest adam sandler susan sarandon eva amurri martino sean ander",
      803: "in an ancient time when majest fire-breath soar through the skies, a knight name bowen come face to face and heart to heart with the last dragon on earth, draco. take up arm to suppress a tyrant king, bowen soon realiz hi task will be harder than he'd imagined: if he kill the king, draco will die as well. fantasi magic kingdom despot immort villag forest armi horror partner reveng knight battl mediev dragonheart denni quaid david thewli pete postlethwait rob cohen",
      804: 'two master thiev (brosnan and hayek) are final retir after one last succ mission. resid in their own tropic paradise, their old nemesis, fbi agent stan p. lloyd show up to make sure they realli are retired. dock in the port is an ocean liner call the "diamond cruise" and stan is convinc that they\'r not realli retir at all, and that thi is the next set up. action comedi crime drama bahama master thief crook coupl pierc brosnan salma hayek woodi harrelson brett ratner',
      805: 'when the devil resurfac with aim to take over the world in human form, johnni blaze reluctantli come out of hide to transform into the flame-spew supernatur hero ghost rider -- and rescu a 10-year-old boy from an unsavori end. action fantasi thriller monk eastern europ skeleton biker marvel comic superhero motorcycl devil dark hero ghost rider nicola cage ciarán hind violant placido brian taylor',
      806: 'when a greek fisherman leav to fight with the greek armi dure wwii, hi fianc fall in love with the local italian commander. the film is base on a novel about an italian soldier\' experi dure the italian occup of the greek island of cephalonia (kefalonia), but hollywood made it into a pure love stori by remov much of the "unpleasant" stuff. drama histori romanc offic greek island mandolin italian soldier resist fighter greek histori italian armi alli forc nicola cage penélop cruz john hurt john madden',
      807: "disgrac navi seal shane wolf is hand a new assignment: protect the five plummer kid from enemi of their recent decea father -- a govern scientist whose top-secret experi remain hidden in the kids' house. action comedi drama famili thriller bodybuild children bodi guard scientist famili u.s. soldier death of husband male nanni vin diesel lauren graham faith ford adam shankman",
      808: 'a former u.s. soldier return to hi hometown to find it overrun by crime and corruption, which prompt him to clean house. adventur drama action thriller casino sheriff home violenc special forc ex soldier dwayn johnson johnni knoxvil neal mcdonough kevin bray',
      809: "a man with a low iq ha accomplish great thing in hi life and been present dure signif histor event - in each case, far exceed what anyon imagin he could do. yet, despit all the thing he ha attained, hi one true love elud him. 'forrest gump' is the stori of a man who rose abov hi challenges, and who prove that determination, courage, and love are more import than ability. comedi drama romanc vietnam veteran hippi mental disabl run base on novel vietnam vietnam war friendship love famili relationship bulli mother son relationship militari hug shrimp wound soldier flashback park bench amput tom hank robin wright gari sini robert zemecki",
      810: 'a struggl songwrit name dave sevil find success when he come across a trio of sing chipmunks: mischiev leader alvin, braini simon, and chubby, impress theodore. comedi music famili fantasi anim pop pop star record produc surpri approach forest music concert friendship perform chipmunk talk anim songwrit talk to anim duringcreditsst jason lee david cross cameron richardson tim hill',
      811: "greg focker is readi to marri hi girlfriend, pam, but befor he pop the question, he must win over her formid father, humorless former cia agent jack byrnes, at the wed of pam' sister. as greg bend over backward to make a good impression, hi visit to the byrn home turn into a hilari seri of disasters, and everyth that can go wrong does, all under jack' critical, hawklik gaze. comedi romanc cia airport cat jew orderli airplan father-in-law epistaxi daughter lost baggag urn pavilion volleyb hospit wed ben stiller robert de niro teri polo jay roach",
      812: "histori come gloriou to life in disney' epic anim tale about love and adventur in the new world. pocahonta is a nativ american woman whose father ha arrang for her to marri her village' best warrior. but a vision tell her chang is coming, and soon she come face to face with it in the form of capt. john smith. adventur anim drama famili cultur clash settler forbidden love coloni music gold rush princess romanc nativ american anim virginia star cross lover refer to pizarro jamestown virginia pug dog cross cultur relationship musket anim tree indian chief base on folk tale 17th centuri shaman song indian vs. settler anim sidekick powhatan land claim iren bedard mel gibson david ogden stier mike gabriel",
      813: "mild-mann clark kent work as a report at the daili planet alongsid hi crush, loi lane − who' in love with superman. clark must summon hi superhero alter ego when the nefari lex luthor launch a plan to take over the world. action adventur fantasi scienc fiction save the world journalist dc comic crime fighter nuclear missil galaxi superhero base on comic book crimin sabotag north pole midwest kryptonit super power superhuman strength aftercreditsst save the day christoph reev marlon brando margot kidder richard donner",
      814: "eddi murphi star as shi dr. sherman klump, a kind, brilliant, 'calorif challenged' genet professor. when beauti carla purti join the univ faculty, sherman grow desper to whittl hi 400-pound frame down to size and win her heart. so, with one swig of hi experi fat-reduc serum, sherman becom 'buddi love', a fast-talking, pumped-up , plump down don juan. fantasi comedi romanc scienc fiction overweight overweight man duringcreditsst eddi murphi jada pinkett smith jame coburn tom shadyac",
      815: "date coach alex 'hitch' hitchen mentor a bumbl client, albert, who hope to win the heart of the glamor allegra cole. while albert make progress, hitch face hi own romant setback when proven techniqu fail to work on sara melas, a tabloid report dig for dirt on allegra cole' love life. when sara discov hitch' connect to albert – now allegra' boyfriend – it threaten to destroy both relationships. comedi drama romanc speed date romant comedi date will smith eva mend kevin jame andi tennant",
      816: "babi georg got into a plane crash in a jungle, stay aliv and wa adopt by a wise ape. ursula stanhope, us nobl woman is save from death on safari by grown-up george, and he take her to jungl to live with him. he slowli learn a rule of human relationships, while ursula' lover lyle is look for her and the one who took her. after they are found, ursula take georg to the usa. adventur comedi famili romanc africa san francisco gorilla lion feral child jungl brendan fraser lesli mann thoma haden church sam weisman",
      817: "with high school a distant memory, jim and michel are get marri -- and in a hurry, sinc jim' grandmoth is sick and want to see him walk down the aisl -- prompt stifler to throw the ultim bachelor party. and jim' dad is reliabl as ever, dole out advic no one want to hear. comedi romanc handcuff sister sister relationship spanner blow job stag night wed jason bigg alyson hannigan seann william scott jess dylan",
      818: 'the true stori of captain richard phillip and the 2009 hijack by somali pirat of the us-flag mv maersk alabama, the first american cargo ship to be hijack in two hundr years. action drama thriller ship hijack somalia fisherman blood poverti pirat terror commando hijack cargo ship ship captain ship hijack somali commando unit tom hank catherin keener max martini paul greengrass',
      819: 'phil and clair foster fear that their mild-mann relationship may be fall into a stale rut. dure their weekli date night, their dinner reserv lead to their be mistaken for a coupl of thiev – and now a number of unsavouri charact want phil and clair killed. comedi date corrupt taxi expen restaur wife husband relationship gun boat taxi driver document restaur roof marri coupl politician stripper shoot thief car crash steal mistaken ident polic corrupt aftercreditsst duringcreditsst tina fey steve carel mark wahlberg shawn levi',
      820: 'furiou that her late father onli will her hi gloomy-look mansion rather than hi millions, carrigan crittenden is readi to burn the place to the ground when she discov a map to a treasur hidden in the house. but when she enter the ricketi mansion to seek her claim, she is frighten away by a wick wave of ghosts. determin to get her hand on thi hidden fortune, she hire afterlif therapist dr. jame harvey to exorci the ghost from the mansion. harvey and hi daughter kat move in, and soon kat meet casper, the ghost of a young boy who\' "the friendliest ghost you know." but not so friendli are casper\' uncles--stretch, fatso and stinkie--who are determin to drive all "fleshies" away. fantasi comedi famili halloween friendship supernatur afterlif friend danger ghost disord young hero imaginari supernatur abil mischiev children christina ricci bill pullman cathi moriarti brad silberl',
      821: 'in the equalizer, denzel washington play mccall, a man who believ he ha put hi mysteri past behind him and dedic himself to begin a new, quiet life. but when mccall meet teri (chloë grace moretz), a young girl under the control of ultra-viol russian gangsters, he can’t stand idli by – he ha to help her. arm with hidden skill that allow him to serv vengeanc against anyon who would brutal the helpless, mccall come out of hi self-impo retir and find hi desir for justic reawakened. if someon ha a problem, if the odd are stack against them, if they have nowher el to turn, mccall will help. he is the equalizer. thriller action crime corrupt assassin hostag fbi hitman russian secur camera sadism vigil sociopath reveng suspen organ crime gore gangster violenc teenag prostitut commando interrog surveil ex soldier fake death loner call girl black op hand to hand combat mysteri past denzel washington marton csoka chloë grace moretz antoin fuqua',
      822: "marisa ventura is a struggl singl mom who work at a posh manhattan hotel and dream of a better life for her and her young son. one fate day, hotel guest and senatori candid christoph marshal meet marisa and mistak her for a wealthi socialite. after an enchant even together, the two fall madli in love. but when marisa' true ident is revealed, issu of class and social statu threaten to separ them. can two peopl from veri differ world overcom their differ and live happili ever after? comedi drama romanc hotel politician mistaken ident maid class differ singl mother public relat maid uniform hotel clerk wealth differ jennif lopez ralph fienn natasha richardson wayn wang",
      823: 'on a us nuclear missil sub, a young first offic stage a mutini to prevent hi trigger happi captain from launch hi missil befor confirm hi order to do so. action thriller drama submarin mutini russia missil nuclear missil embassi u.s. navi battl for power torpedo militari moral dilemma post cold war aircraft carrier chain of command launch code sonar denzel washington gene hackman matt craven toni scott',
      824: "the true stori of christoph gardner, who invest heavili in a devic known as a 'bone densiti scanner', onli to find himself struggl to sell the product as it' just margin better than the current technology, and much more expensive. hi wife leav him, he lose hi house, bank account and credit card and, now forc to live out in the street with hi young son, he' desper to find a steadi job. he take on a job as a stockbrok but, befor he can receiv pay, he need to go through 6 month of training, and must sell hi devices. drama san francisco singl parent homeless person bu worker homeless work church servic bad luck biographi salesman stockbrok will smith jaden smith thandi newton gabriel muccino",
      825: 'a claustrophobic, hitchcockian thriller. a bereav woman and her daughter are fli home from berlin to america. at 30,000 feet the child vanish and nobodi admit she wa ever on that plane. thriller drama mysteri berlin loss of father airplan baby-snatch jodi foster peter sarsgaard sean bean robert schwentk',
      826: 'a comput specialist is su for sexual harass by a former lover turn boss who initi the act forcefully, which threaten both hi career and hi person life. drama thriller crime mysteri romanc employ workplac sexual harass intrigu michael dougla demi moor donald sutherland barri levinson',
      827: 'when guardian angel seth -- who invi watch over the citizen of lo angel -- becom captiv by maggie, a strong-wil heart surgeon, he ponder trade in hi pure, otherworldli exist for a mortal life with hi beloved. the coupl embark on a tender but forbidden romanc span heaven and earth. drama fantasi romanc suicid angel life and death desper oper heaven faith afterlif lo angel interspeci romanc nicola cage meg ryan andr braugher brad silberl',
      828: "an assassin is shot at the altar by her ruthless employer, bill and other member of their assassin circl – but 'the bride' live to plot her vengeance. set out for some payback, she make a death list and hunt down those who wrong her, save bill for last. action crime japan coma martial art kung fu underworld yakuza sword bride reveng gore femal yakuza blood wed samurai sword part anim uma thurman luci liu vivica a. fox quentin tarantino",
      829: "on the verg of bankruptci and desper for hi big break, aspir filmmak bobbi bowf concoct a crazi plan to make hi ultim dream movie. ralli a ragtag team that includ a starry-ey ingenue, a has-been diva and a film studio gofer, he set out to shoot a blockbust featur the biggest star in hollywood, kit ramsey -- onli without let ramsey know he' in the picture. comedi film produc film director movi studio hollywood filmmak movi actress steve martin eddi murphi heather graham frank oz",
      830: "the bride unwaveringli continu on her roar rampag of reveng against the band of assassin who had tri to kill her and her unborn child. she visit each of her former associ one-by-one, check off the victim on her death list five until there' noth left to do … but kill bill. action crime thriller brother brother relationship swordplay katana mother role rage and hate daughter right and justic singl aftercreditsst duringcreditsst uma thurman david carradin daryl hannah quentin tarantino",
      831: "ray tango and gabriel cash are narcot detect who, while both be extrem successful, can't stand each other. crime lord yve perret, furiou at the loss of incom that tango and cash have cau him, frame the two for murder. caught with the murder weapon on the scene of the crime, the two have no alibi. thrown into prison with most of the crimin they help convict, it appear that they are go to have to trust each other if they are to clear their name and catch the evil perret. action adventur comedi prison war on drug lo angel sylvest stallon kurt russel teri hatcher andrei konchalovski",
      832: "madelin is marri to ernest, who wa onc arch-riv helen' fiance. after recov from a mental breakdown, helen vow to kill madelin and steal back ernest. unfortun for everyone, the introduct of a magic potion cau thing to be a great deal more complic than a mere murder plot. fantasi comedi jealousi beauti immort rivalri potion drink meryl streep bruce willi goldi hawn robert zemecki",
      833: "chon wang, a clumsi imperi guard trail princess pei pei when she is kidnap from the forbidden citi and transport to america. wang follow her captor to nevada, where he team up with an unlik partner, outcast outlaw roy o'bannon, and tri to spring the princess from her imprisonment. adventur action comedi western princess sioux travel rescu nativ american chine cowboy duringcreditsst 19th centuri jacki chan owen wilson luci liu tom dey",
      834: 'terrorist hijack a 747 inbound to washington d.c., demand the the relea of their imprison leader. intellig expert david grant (kurt russell) suspect anoth reason and he is soon the reluct member of a special assault team that is assign to intercept the plane and hijackers. action adventur drama thriller bomb ransom hostag airplan hijack terror cell special unit decept rescu covert oper disast shootout terror explo violenc surveil night vision goggl flight attend intellig agent flashback hand to hand combat nerv ga kurt russel steven seagal hall berri stuart baird',
      835: 'jim carrey star as tom popper, a success businessman who’ clueless when it come to the realli import thing in life...until he inherit six “adorable” penguins, each with it own uniqu personality. soon tom’ rambuncti roommat turn hi swank new york apart into a snowi winter wonderland — and the rest of hi world upside-down. comedi famili taxi restaur zoo penguin ex husband littl boy zookeep doorman ride bird hatch aftercreditsst duringcreditsst jim carrey carla gugino madelin carrol mark water',
      836: 'an american teenag who is obsess with hong kong cinema and kung-fu classic make an extraordinari discoveri in a chinatown pawnshop: the legendari stick weapon of the chine sage and warrior, the monkey king. with the lost relic in hand, the teenag unexpectedli find himself travel back to ancient china to join a crew of warrior from martial art lore on a danger quest to free the imprison monkey king. action adventur fantasi tempel shaolin teenag urin staff warrior monkey king jacki chan jet li michael angarano rob minkoff',
      837: 'in thi irreverent, hilarious, adventur buddi comedi for audienc of all ages, direct by jimmi hayward (horton hear a who!), two turkey from opposit side of the track must put asid their differ and team up to travel back in time to chang the cour of histori - and get turkey off the holiday menu for good. anim comedi famili holiday thanksgiv freedom duringcreditsst 3d owen wilson woodi harrelson ami poehler jimmi hayward',
      838: 'after escap with newt and hick from the alien planet, ripley crash land on fiorina 161, a prison planet and host to a correct facility. unfortunately, although newt and hick do not surviv the crash, a more unwelcom visitor does. the prison doe not allow weapon of ani kind, and with aid be a long time away, the prison must simpli surviv in ani way they can. scienc fiction action horror prison android spacecraft space marin imprison space coloni space travel rottweil dystopia sequel alien redempt outer space planet shave head crash land impregn penal coloni furnac suspend anim xenomorph sigourney weaver charl s. dutton charl danc david fincher',
      839: 'the hit music base on the life of evita duarte, a b-movi argentinian actress who eventu becam the wife of argentinian presid and dictat juan perón, and the most belov and hate woman in argentina. histori drama music prostitut deific danceh hostess perónism argentin presid rise to power sing narrat soccer ball madonna antonio bandera jonathan pryce alan parker',
      840: "a briefca with undisclo content – sought by irish terrorist and the russian mob – make it way into criminals' hands. an irish liaison assembl a squad of mercenaries, or 'ronin', and give them the thorni task of recov the case. action thriller crime adventur pari franc arm deal audi impostor case violenc ice skate comput expert ex kgb prepar hit with a car door cellular phone trace merri go round robert de niro jean reno natascha mcelhon john frankenheim",
      841: "sir robert beaumont is behind schedul on a railroad in africa. enlist note engin john henri patterson to right the ship, beaumont expect results. everyth seem great until the crew discov the mutil corp of the project' foreman, seemingli kill by a lion. after sever more attacks, patterson call in fame hunter charl remington, who ha final met hi match in the bloodthirsti lions. adventur africa lion bridg base on true stori kenya anim attack lion attack coloni swahili michael dougla val kilmer tom wilkinson stephen hopkin",
      842: "a young peruvian bear with a passion for all thing british travel to london in search of a home. find himself lost and alon at paddington station, he begin to realiz that citi life is not all he had imagin - until he meet the kindli brown family, who read the label around hi neck ('plea look after thi bear. thank you.') and offer him a temporari haven. it look as though hi luck ha chang until thi rarest of bear catch the eye of a museum taxidermist... famili comedi england train station base on novel bear anthropomorph talk to anim children' book nicol kidman peter capaldi ben whishaw paul king",
      843: 'four everyday suburban guy come togeth as an excu to escap their humdrum live one night a week. but when they accid discov that their town ha becom overrun with alien pose as ordinari suburbanites, they have no choic but to save their neighborhood - and the world - from total extermination. comedi usa steril castrat marriag friendship alien suburb alien inva death teenag daughter neighborhood watch creepi neighbor ben stiller vinc vaughn jonah hill akiva schaffer',
      844: "in the wilder of british columbia, two hunter are track and viciou murder by aaron hallum. former special oper instructor, l.t. bonham is approach and ask to apprehend hallum, hi former student, who ha 'gone rogue' after suffer sever battl stress from hi time in kosovo. drama action thriller crime hunter fbi knife balkan war wood psychopath killer slaughter survivalist maniac special forc kill spree combat ex soldier dark past manhunt gori violenc tommi lee jone benicio del toro conni nielsen william friedkin",
      845: "dr. ethan powell, an anthropologist, is in africa studi ape when he is lost for two years. when he is found, he kill 3 men and put 2 in the hospital. cuba gooding' charact is a psychiatrist who want to take up the task of tri to get dr. powel to speak again and mayb even stand judgment at a trial for hi relea from prison of mental cases. along the way, cuba ha to deal with also help the mental patient that are be abu and neglected. in thi process cuba learn a few thing about himself and life, and so doe anthoni hopkin character, dr. powell. drama mysteri thriller prison gorilla research instinct murder psychologist anthoni hopkin cuba good jr. donald sutherland jon turteltaub",
      846: 'in martha\' vineyard, mass., conjoin twin walt (greg kinnear) and bob tenor (matt damon) make the best of their handicap by be the fastest grill cook in town. while outgo walt hope to one day becom a famou actor, shi bob prefer to stay out of the spotlight. when a fade hollywood actress, cher (cher), decid to get her show "honey and the beaze" cancelled, she hire walt -- and hi brotherli appendag -- as her costars. but their addit surprisingli achiev the opposite. comedi sex dancer martial art cook stripper love bulli hollywood twin flashback freak actor anxieti conjoin siam matt damon greg kinnear eva mend bobbi farrelli',
      847: 'jacki moon is the owner, promoter, coach, and star player of the flint michigan tropic of the american basketb associ (aba). in 1976 befor the aba collapses, the nation basketb associ (nba) plan to merg with the best team of the aba at the end of the season. onli the top four team will make the move and the worst team will fold. the tropic are the worst team in the leagu and if they want to make it to the nba, jacki moon must ralli hi team and start winning. the onli problem is the fact that jacki moon is not realli the coach and star basketb player he think he is. to keep hi team from oblivion and leav hi mark in the city, jacki moon must inspir hi team to win fourth place in the playoffs. comedi sport basketb flint michigan nba merger trade garbag can canon ramp championship dead parent will ferrel maura tierney woodi harrelson kent alterman',
      848: 'the luxuriantli beard pirat captain is a boundlessli enthusiastic, if somewhat less-than-successful, terror of the high seas. with a rag-tag crew at hi side, and seemingli blind to the imposs odd stack against him, the captain ha one dream: to beat hi bitter rival black bellami and cutlass liz to the much covet pirat of the year award. it’ a quest that take our hero from the shore of exot blood island to the foggi street of victorian london. along the way they battl a diabol queen and team up with a haplessli smitten young scientist, but never lose sight of what a pirat love best: adventure! anim adventur famili comedi rivalri stop motion pirat aftercreditsst duringcreditsst hugh grant brendan gleeson jeremi piven peter lord',
      849: "christin collin is overjoy when her kidnap son is brought back home. but when christin suspect that the boy return to her isn't her child, the polic captain ha her commit to an asylum. crime drama mysteri corrupt mother nuditi minist power public govern polic reunion murder conspiraci lo angel miss mother love critic angelina joli jeffrey donovan john malkovich clint eastwood",
      850: 'two research in a green altern energi project are put on the run when they are frame for murder and treason. action drama scienc fiction thriller fbi hydrogen bomb secret lab energi suppli conspiraci aftercreditsst keanu reev morgan freeman rachel weisz andrew davi',
      851: 'when the san francisco giant pay centerfield bobbi rayburn $40 million to lead their team to the world series, no one is happier or more support than #1 fan gil renard. so when rayburn becom mire in the worst slump of hi career, the obsess renard decid to stop at noth to help hi idol regain hi former glory... not even murder. drama mysteri thriller sport luck san francisco giant child custodi baseb pitcher baseb fan psychot fan sport agent drive rang steam room robert de niro wesley snipe ellen barkin toni scott',
      852: 'deform sinc birth, a bitter man known onli as the phantom live in the sewer underneath the pari opera house. he fall in love with the obscur choru singer christine, and privat tutor her while terror the rest of the opera hou and demand christin be given lead roles. thing get wor when christin meet back up with her childhood acquaint raoul and the two fall in love thriller drama romanc danc obsess auction wheelchair rose product placement music remak tragic villain black and white rooftop heroin disfigur face base on stage music theater disfigur mask break mirror opera singer 1910 gerard butler emmi rossum patrick wilson joel schumach',
      853: "when queen elizabeth' reign is threaten by ruthless famili betray and spain' invad army, she and her shrewd advi must act to safeguard to the live of her people. drama histori romanc england assassin spain virgin coloni govern queen elizabeth i religi war tudor execut middl age cathol sea battl palac intrigu cate blanchett clive owen geoffrey rush shekhar kapur",
      854: "400 year into the future, disea ha wipe out the major of the world' population, except one wall city, bregna, rule by a congress of scientists. when æon flux, the top oper in the underground 'monican' rebellion, is sent on a mission to kill a govern leader, she uncov a world of secrets. action scienc fiction martial art dystopia surreal base on cartoon shootout espionag infertil cyberpunk extrem violenc sabotag one against mani woman director hand to hand combat action heroin human clone 25th centuri charliz theron marton csoka jonni lee miller karyn kusama",
      855: 'the film center mostli around the person and profess life of thoma "stonewall" jackson, a brilliant if eccentr confed general, from the outbreak of the american civil war until it halfway point when jackson is kill accid by hi own soldier in may 1863 dure hi greatest victory. drama histori war war battl union soldier confed soldier american civil war secess stephen lang jeff daniel robert duval ronald f. maxwel',
      856: 'on a flight transport danger convicts, murder ryan weaver manag to break free and cau complet chao throughout the plane. as variou peopl on board fall victim to weaver, it is ultim down to flight attend teri halloran to keep the aircraft from crashing, with on-ground support from an air traffic controller. while halloran struggl to pilot the plane, weaver continu to terror the surviv member of the crew. action thriller crime stewardess airplan shootout air marshal christma turbul ray liotta lauren holli brendan gleeson robert butler',
      857: "a financ execut who can't stop hi career downspir is invit into hi daughter' imaginari world, where solut to hi problem await. comedi eddi murphi thoma haden church yara shahidi karey kirkpatrick",
      858: 'while on a grand world tour, the muppet find themselv wrap into an european jewel-heist caper head by a kermit the frog look-alik and hi dastardli sidekick. comedi adventur crime famili music the muppet ricki gervai ty burrel tina fey jame bobin',
      859: "danger mission are the bread and butter of the thunderbirds, a high-tech secret forc employ by the government. led by jeff traci (bill paxton), the thunderbird are at the top of their game, but their nemesis, the hood (ben kingsley), ha land on their island and is attempt a coup by use the team' rescu vehicles. he'll soon discov that the thunderbird won't go down. action adventur comedi famili fantasi scienc fiction secret organ base on tv seri golden gate bridg locker oil rig teenag hero soak cloth thunderbird bradi corbet soren fulton debora weston jonathan frake",
      860: "the burlesqu loung ha it best day behind it. tess, a retir dancer and owner of the venue, struggl to keep the age theater alive, face all kind of financ and artist challenges. with the lounge' troup member becom increasingli distract by person problem and a threat come from a wealthi businessman' quest to buy the spot from tess, the good fortun seem to have abandon the club altogether. meanwhile, the life of ali, a small-town girl from iowa, is about to chang dramatically. hire by tess as a waitress at the lounge, ali escap a hollow past and quickli fall in love with the art of burlesque. back by newfound friend amongst the theater' crew, she manag to fulfil her dream of be on stage herself. thing take a dramat turn though when ali' big voic make her becom the main attract of the revu drama romanc music lo angel burlesqu burlesqu dancer cher christina aguilera eric dane steve antin",
      861: 'in 1919, mathild wa 19 year old. two year earlier, her fiancé manech left for the front at the somme. like million of other he wa "kill on the field of battle." it\' written in black and white on the offici notice. but mathild refu to believ it. if manech had died, she would know. she hang on to her intuit as tightli as she would onto the last thread of hope link her to her lover. a former sergeant tell her in vain that manech die in the no man\' land of a trench name bingo crepescule, in the compani of four other men condemn to die for self-inflict wounds. her path ahead is full of obstacl but mathild is not frightened. anyth is possibl to someon who is will to challeng fate... drama pari prostitut loss of lover amnesia bodili disabl person world war i wheelchair brittani lighthou verdun lighthou keeper teenag crush disappear soldier illeg prostitut privat detect miss person polio trench audrey tautou gaspard ulliel dominiqu pinon jean-pierr jeunet',
      862: "humbert humbert is a middle-ag british novelist who is both appal by and attract to the vulgar of american culture. when he come to stay at the board hou run by charlott haze, he soon becom obsess with lolita, the woman' teenag daughter. drama romanc sexual obsess hotel depress loss of mother small town flirt midlif crisi erot youngster lolita motel diari seduct forbidden love professor for literatur provoc fascin one-sid love widow adopt father loss of husband summer camp secret love jame mason sue lyon shelley winter stanley kubrick",
      863: 'a disgrac fbi agent with a drink problem join nine other troubl law enforc offic at an isol detox clinic in the wild of wyoming. but the therapeut sanctuari becom a nightmarish hellhol when a major snowstorm cut off the clinic from the outsid world and enabl a killer on the insid to get busy. action thriller alcohol serial killer hospit polic offic detox sylvest stallon courtney b. vanc tom bereng jim gillespi',
      864: 'a rare mutat ha occur within the vampir commun - the reaper. a vampir so consum with an insati bloodlust that they prey on vampir as well as humans, transform victim who are unlucki enough to surviv into reaper themselves. blade is ask by the vampir nation for hi help in prevent a nightmar plagu that would wipe out both human and vampires. fantasi horror action thriller katana mutat vampir silver superhero tragic villain broken neck lasersight violenc explod bodi blade subject camera torso cut in half reaper broken wrist razor blade shot through a door sword duel burnt face wesley snipe kri kristofferson ron perlman guillermo del toro',
      865: 'an ir agent with a fate secret embark on an extraordinari journey of redempt by forev chang the live of seven strangers. drama vegetarian tax collector pianist blind organ transplant blood type will smith rosario dawson sarah jane morri gabriel muccino',
      866: 'after watch their respect partner die, a cop and a hitman form an allianc in order to bring down their common enemy. action crime thriller sylvest stallon sung kang sarah shahi walter hill',
      867: 'in the midst of tri to legitim hi busi deal in 1979 new york and italy, age mafia don, michael corleon seek forgiv for hi sin while take a young proteg under hi wing. crime drama thriller itali christian new york assassin italo-american vatican pope confess helicopt daughter lawyer al pacino dian keaton andi garcía franci ford coppola',
      868: "drew baylor is fire after cau hi shoe compani to lose hundr of million of dollars. to make matter worse, he' also dump by hi girlfriend. on the verg of end it all, drew get a new lea on life when he return to hi family' small kentucki hometown after hi father dies. along the way, he meet a flight attend with whom he fall in love. comedi drama romanc suicid hotel room suicid attempt new love funer airplan lover fall in love orlando bloom kirsten dunst susan sarandon cameron crow",
      869: "after stand in as best man for hi longtim friend carl petersen, randi dupr lose hi job, becom a barfli and attach himself to the newlyw coupl almost perman -- as their houseguest. but the longer dupr camp out on their couch, the closer he get to carl' bride, molly, leav the frustrat groom wonder when hi pal will be move out. comedi romanc roommat love of one' life newlyw kate hudson owen wilson matt dillon anthoni russo",
      870: "three escap crimin from the planet krypton test the man of steel' mettle. led by gen. zod, the kryptonian take control of the white hou and partner with lex luthor to destroy superman and rule the world. but superman, who attempt to make himself human in order to get closer to lois, realiz he ha a respon to save the planet. action adventur fantasi scienc fiction save the world dc comic sequel superhero base on comic book loss of virgin crimin super power phantom zone rocket fire grenad crystal machin superhuman strength duringcreditsst gene hackman christoph reev ned beatti richard lester",
      871: "gigli is order to kidnap the psycholog challeng younger brother of a power feder prosecutor. when plan go awry, gigli' boss send in ricki, a gorgeou free-spirit femal gangster who ha her own set of order to assist with the kidnapping. but gigli begin fall for the decidedli unavail ricki, which could be a hazard to hi occupation. drama new york mental disabl kidnap blackmail mission of murder lover lesbian mobster ben affleck jennif lopez justin bartha martin brest",
      872: "the stori of an idealist' rise to power in the world of louisiana polit and the corrupt that lead to hi ultim downfall. base on the1946 pulitz prize-win novel written by robert penn warren. drama thriller corrupt journalist base on novel blackmail manipul bodyguard louisiana scandal power governor polit tragedi mistress aristocrat sean penn jude law kate winslet steven zaillian",
      873: "new york polic detect john shaft arrest walter wade jr. for a racial motiv slaying. but the onli eyewit disappears, and wade jump bail for switzerland. two year later wade return to face trial, confid hi money and influenc will get him acquit -- especi sinc he' paid a drug kingpin to kill the witness. action adventur crime thriller corrupt black peopl italo-american brother sister relationship drug dealer reveng murder violenc drug polic offic xenophobia samuel l. jackson jeffrey wright christian bale john singleton",
      874: "thi anim adventur retel the stori of the lost daughter of russia' last czar. the evil rasputin place a cur on the romanov family, and anastasia and her grandmother, empress maria, get separated. after grow up in an orphanage, anastasia encount two russian men seek a reward offer by empress maria for the return of her granddaughter. the trio travel to paris, where they find that the empress ha grown skeptic of imposters. anim famili tzar music russian revolut train explo foreign languag adapt explod train meg ryan john cusack christoph lloyd gari goldman",
      875: "a celebr of love and creativ inspir take place in the infamous, gaudi and glamor parisian nightclub, at the cusp of the 20th century. a young poet, who is plung into the headi world of moulin rouge, begin a passion affair with the club' most notori and beauti star. drama music romanc duke music writer' block music termin ill writer no open credit moulin roug bohemian toulou lautrec red curtain cancan danc la traviata orpheu and euryd danc hall nicol kidman ewan mcgregor john leguizamo baz luhrmann",
      876: "a divorc father discov that hi 12-year-old son' new stepfath is not what he made himself out to be. mysteri thriller crime menac adopt danger adopt father threat to death step father murder divorc ex-wif child murder hunt john travolta vinc vaughn teri polo harold becker",
      877: 'the true stori of whitey bulger, the brother of a state senat and the most infam violent crimin in the histori of south boston, who becam an fbi inform to take down a mafia famili invad hi turf. crime drama boston base on true stori organ crime johnni depp joel edgerton benedict cumberbatch scott cooper',
      878: "there were five marin and one navi corpsman photograph rai the u.s. flag on mt. suribachi by joe rosenth on februari 23, 1945. thi is the stori of three of the six surviv servicemen – john 'doc' bradley, pvt. rene gagnon and pvt. ira hayes, who fought in the battl to take iwo jima from the japanese. war drama histori world war ii die and death pacif iwo jima aftercreditsst duringcreditsst ryan phillipp adam beach jess bradford clint eastwood",
      879: "a frustrat man decid to take justic into hi own hand after a plea bargain set one of hi family' killer free. he target not onli the killer but also the district attorney and other involv in the deal. drama crime thriller tattoo secret passag baseb bat deal explo justic district attorney courtroom vigil jami foxx gerard butler colm meaney f. gari gray",
      880: 'two full length featur horror movi written by quentin tarantino and robert rodriguez put togeth as a two film feature. includ fake movi trailer in between both movies. thriller action horror exploit slasher zombi killer kurt russel zoë bell rosario dawson robert rodriguez',
      881: 'after paul d. find hi old slave friend seth in ohio and move in with her and her daughter denver, a strang girl come along by the name of "beloved". seth and denver take her in and then strang thing start to happen... drama thriller oprah winfrey danni glover thandi newton jonathan demm',
      882: 'a profess poker player whose astound luck at the tabl fail to translat into hi lonesom love life attempt to win the world seri of poker while simultan earn the affect of a beauti la vega singer. drama romanc poker sport la vega eric bana drew barrymor robert duval curti hanson',
      883: 'a true stori about frank abagn jr. who, befor hi 19th birthday, success con million of dollar worth of check as a pan am pilot, doctor, and legal prosecutor. an fbi agent make it hi mission to put him behind bars. but frank not onli elud capture, he revel in the pursuit. drama crime con man biographi fbi agent overhead camera shot attempt jailbreak engag parti mislaid trust bank fraud inspir by a true stori leonardo dicaprio tom hank christoph walken steven spielberg',
      884: 'a chronicl of the decade-long hunt for al-qaeda terrorist leader osama bin laden after the septemb 2001 attacks, and hi death at the hand of the navi s.e.a.l. team 6 in may, 2011. thriller drama histori assassin cia hotel terrorist prison car dealer mossad van iraq pakistan osama bin laden man hunt navi seal f word femal protagonist gunfight raid violenc text messag monkey dog special forc tie up militari area 51 terrorist group tortur woman director al qaeda prison camp water tortur suicid bomb 21st centuri ex special forc post 9/11 helicopt crash islamabad jessica chastain jason clark mark strong kathryn bigelow',
      885: 'cohabit coupl gari and brook find their once-bliss romanc on the rock when petti spat about lemon and dirti dish mushroom into an all-out battl for custodi of their upscal chicago condo. an escal argument ensu as gari and brook continu to live under the same roof, all while cook up scheme to drive each other off the premises. romanc comedi bowl chicago american footbal flat baseb new love tour guid break-up art galleri argument pool tabl watch tv ex-boyfriend ex-girlfriend relationship dinner parti condominium vinc vaughn jennif aniston joey lauren adam peyton reed',
      886: "set on an idyl greek island, the plot serv as a background for a wealth of abba hit songs. donna, an independent, singl mother who own a small hotel on the island is about to let go of sophie, the spirit young daughter she' rai alone. but sophi ha secretli invit three of her mother' ex-lov in the hope of find her father. comedi romanc singl parent greec music daughter singl mother daughter relationship duringcreditsst woman director meryl streep pierc brosnan amanda seyfri phyllida lloyd",
      887: 'more than a dozen angeleno navig valentine\' day from earli morn until midnight. three coupl awak together, but each relationship will sputter; are ani worth saving? a grade-school boy want flower for hi first true love; two high school senior plan first-tim sex at noon; a tv sport report get the assign to find romanc in la; a star quarterback contempl hi future; two stranger meet on a plane; grandparents, togeth for years, face a crisis; and, an "i hate valentine\' day" dinner beckon the lone and the lie to. can cupid finish hi work by midnight? comedi romanc flower marri coupl florist kiss singl valentin valentine\' day multipl storylin aftercreditsst duringcreditsst jessica alba jessica biel bradley cooper garri marshal',
      888: "cousins, bo and luke duke, with the help of their eye-catch cousin, daisi and moonshine-run uncl jesse, tri and save the famili farm from be destroy by hazzard county' corrupt commissioner, boss hogg. their effort constantli find the 'duke boys' elud author in 'the gener lee', their 1969 orang dodg charger that keep them one step ahead of the dimwit antic of the small southern town' sheriff, rosco p. coltrane. action adventur comedi sheriff farm bikini redneck moonshin johnni knoxvil seann william scott jessica simpson jay chandrasekhar",
      889: 'base on the graphic novel by jame jones, the thin red line tell the stori of a group of men, an armi rifl compani call c-for-charlie, who change, suffer, and ultim make essenti discoveri about themselv dure the fierc world war ii battl of guadalcanal. it follow their journey, from the surpri of an unoppo landing, through the bloodi and exhaust battl that follow, to the ultim departur of those who survived. a power frontlin cast - includ sean penn, nick nolte, woodi harrelson and georg clooney - explod into action in thi hauntingli realist view of militari and moral chao in the pacif dure world war ii. drama histori war base on novel japan world war ii battl assign inva marin corp u.s. armi command pacif rifl surviv jungl infantri steel helmet sergeant pacif island soldier battl fight guadalcan awol philosoph conflict sean penn adrien brodi jim caviezel terrenc malick',
      890: 'dave is a marri man with two kid and a love wife , and mitch is a singl man who is at the prime of hi sexual life. one fate night while mitch and dave are pee in a fountain when lightn strikes, they switch bodies. comedi jealousi chanc wish chang man chang co-work body-swap olivia wild ryan reynold jason bateman david dobkin',
      891: 'a film about the life and career of the eccentr avant-gard comedian, andi kaufman. comedi drama romanc show busi comedian wrestl jim carrey courtney love bob zmuda miloš forman',
      892: 'the life of the gambl paradi – la vega – and it dark mafia underbelly. drama crime poker drug abu 1970 overdo illeg prostitut robert de niro sharon stone joe pesci martin scors',
      893: "jame ree ha a good job as an ambassador' aid in france, but hi real passion is a side gig, work in a minor role in the cia. he would love to be a full-fledg agent and can't believ hi luck when he land an assign with charli wax. trigger-happi charli soon ha jame cri for hi desk job, but when he learn that the same guy they'r tri to catch are after him, jame realiz that charli may be hi onli hope of survival. action crime thriller pari cia undercov explo pimp ambassador anti hero revel french politician firearm decept car crash gang john travolta jonathan rhi meyer kasia smutniak pierr morel",
      894: 'a mysteri and immort tibetan kung fu master, who ha spent the last 60 year travel around the world protect the ancient scroll of the ultimate, mentor a selfish street kid in the ancient intricaci of kung fu. action comedi fantasi monk homeless person inject fall knife fight scroll the forc seann william scott jaim king karel roden paul hunter',
      895: 'rhode island state trooper charli baileyg ha a multipl person disorder. one person is crazi and aggressive, while the other is more friendli and laid back. both of these person fall in love with the same woman name iren after charli lose hi medication. comedi schizophrenia ex-cop aftercreditsst duringcreditsst jim carrey rené zellweg anthoni anderson bobbi farrelli',
      896: "when thing get crazi at the farm, it' up to a boister bovin name oti (voic by kevin james) to save the day in thi computer-anim tale. the anim in thi barnyard sing, danc and party, but otis' stern dad (sam elliott) warn the crew to keep their cool around humans. troublemak oti rare listen to hi pop, but when the farmer disappear and the anim go nutty, the young cow realiz he must stop the madness. anim comedi famili peasant farm cow cojot famili courteney cox kevin jame sam elliott steve oedekerk",
      897: 'two neighbor have it out after one of them decor hi hou for the holiday so brightli that it can be seen from space. comedi famili holiday massachusett neighbor christma danni devito matthew broderick kristin davi john whitesel',
      898: "forks, washington resid bella swan is reel from the departur of her vampir love, edward cullen, and find comfort in her friendship with jacob black, a werewolf. but befor she know it, she' thrust into a centuries-old conflict, and her desir to be with edward at ani cost lead her to take greater and greater risks. adventur fantasi drama romanc moon cinema vampir werewolf fang vamp kristen stewart robert pattinson taylor lautner chri weitz",
      899: "it ain't easi bein' green -- especi if you'r a likabl (albeit smelly) ogr name shrek. on a mission to retriev a gorgeou princess from the clutch of a fire-breath dragon, shrek team up with an unlik compatriot -- a wisecrack donkey. adventur anim comedi famili fantasi magic liber lordship castl robin hood enchant fairy-t figur princess parodi woman director ogr mike myer eddi murphi cameron diaz andrew adamson",
      900: "a man glimp the futur fate ha plan for him – and choo to fight for hi own destiny. battl the power adjust bureau across, under and through the street of new york, he risk hi destin great to be with the onli woman he' ever loved. scienc fiction thriller romanc hotel dancer hat senat futur honesti plan kiss speech marriag politician alon fate foot chase covert agenc courthou polit campaign base on short stori matt damon emili blunt john slatteri georg nolfi",
      901: "when the dastardli sheriff of nottingham murder robin' father, the legendari archer vow vengeance. to accomplish hi mission, robin join forc with a band of exil villag (and come maid marian), and togeth they battl to end the evil sheriff' reign of terror. adventur england crusad merci robin hood folk hero kevin costner morgan freeman christian slater kevin reynold",
      902: "jerri maguir use to be a typic sport agent: will to do just about anyth he could to get the biggest possibl contract for hi clients, plu a nice commiss for himself. then, one day, he suddenli ha second thought about what he' realli doing. when he voic these doubts, he end up lose hi job and all of hi clients, save rod tidwell, an egomaniac footbal player. comedi drama romanc stadium career sport sport agent tom crui cuba good jr. rené zellweg cameron crow",
      903: 'john bennett, a man whose childhood wish of bring hi teddi bear to life came true, now must decid between keep the relationship with the bear or hi girlfriend, lori. comedi fantasi friendship love teddi bear toy come to life wish come true mark wahlberg mila kuni seth macfarlan seth macfarlan',
      904: 'new york city. melvin udall, a cranky, bigoted, obsessive-compul writer, find hi life turn upsid down when neighbor gay artist simon is hospit and hi dog is entrust to melvin. in addition, carol, the onli waitress who will toler him, must leav work to care for her sick son, make it imposs for melvin to eat breakfast. comedi romanc singl parent waitress lone wolf friendship neighbor author cowardli writer dog rude obnoxi unlik friendship noodl salad jack nicholson helen hunt greg kinnear jame l. brook',
      905: "meet patch adams, a doctor who doesn't look, act or think like ani doctor you'v met before. for patch, humor is the best medicine, and he' will to do just anyth to make hi patient laugh - even if it mean risk hi own career. comedi drama nur hospit doctor laughter robin william philip seymour hoffman bob gunton tom shadyac",
      906: "with the 70 behind him, san diego' top rate newsman, ron burgundy, return to take new york' first 24-hour news channel by storm. comedi journal mustach tv news newsroom gang warfar aftercreditsst news spoof tv news anchor will ferrel steve carel paul rudd adam mckay",
      907: 'when longfellow deeds, a small-town pizzeria owner and poet, inherit $40 billion from hi decea uncle, he quickli begin roll in a differ kind of dough. move to the big city, deed find himself besieg by opportunist all gun for their piec of the pie. babe, a televi tabloid reporter, pose as an innoc small-town girl to do an exposé on deeds. comedi romanc love letter new hampshir ferrari liar citi countri contrast inherit billionair new york citi kind fabl appl tree corpor take over chrysler build adam sandler winona ryder john turturro steven brill',
      908: 'in 1979 ohio, sever youngster are make a zombi movi with a super-8 camera. in the midst of filming, the friend wit a horrifi train derail and are lucki to escap with their lives. they soon discov that the catastroph wa no accident, as a seri of unexplain event and disappear soon follows. deputi jackson lamb, the father of one of the kids, search for the terrifi truth behind the crash. thriller scienc fiction mysteri 1970 secret alien train crash pistol firecrack duringcreditsst joel courtney ell fan riley griffith j.j. abram',
      909: 'a twice-divorc mother of three who see an injustice, take on the bad guy and win -- with a littl help from her push-up bra. erin goe to work for an attorney and come across medic record describ ill cluster in one nearbi town. she start investig and soon expo a monument cover-up. drama biographi base on true stori singl mother water pollut environ law julia robert albert finney aaron eckhart steven soderbergh',
      910: 'an advic columnist, andi anderson (kate hudson), tri push the boundari of what she can write about in her new piec about how to get a man to leav you in 10 days. her editor, lana (bebe neuwirth), love it, and andi goe off to find a man she can use for the experiment. enter execut ben berri (matthew mcconaughey), who is so confid in hi romant prowess that he think he can make ani woman fall in love with him in 10 days. when andi and ben meet, their plan backfire. comedi romanc new york bet journalist therapist adverti expert relationship kate hudson matthew mcconaughey kathryn hahn donald petri',
      911: "after make their way through high school (twice), big chang are in store for offic schmidt and jenko when they go deep undercov at a local college. but when jenko meet a kindr spirit on the footbal team, and schmidt infiltr the bohemian art major scene, they begin to question their partnership. now they don't have to just crack the case - they have to figur out if they can have a matur relationship. if these two overgrown adolesc can grow from freshmen into real men, colleg might be the best thing that ever happen to them. crime comedi action high school undercov cop buddi comedi aftercreditsst duringcreditsst jonah hill chan tatum dave franco phil lord",
      912: 'a vampir relat hi epic life stori of love, betrayal, loneliness, and dark hunger to an over-curi reporter. horror romanc pari san francisco vampir plantat piti bite fang vamp brad pitt tom crui kirsten dunst neil jordan',
      913: 'carl allen ha stumbl across a way to shake free of post-divorc blue and a dead-end job: embrac life and say ye to everything. comedi bungee-jump scooter jim carrey zooey deschanel rhi darbi peyton reed',
      914: 'after he reunit with an old pal through facebook, a mild-mann account is lure into the world of intern espionage. action comedi spi cia espionag high school reunion refer to facebook account dwayn johnson kevin hart ami ryan rawson marshal thurber',
      915: 'jacki is a divorc mother of two. isabel is the career mind girlfriend of jackie’ ex-husband luke, forc into the role of unwelcom stepmoth to their children. but when jacki discov she is ill, both women reali they must put asid their differ to find a common ground and celebr life to the fullest, while they have the chance. drama romanc divorc rebelli daughter freez frame custodi school play photo shoot julia robert susan sarandon ed harri chri columbu',
      916: "the stori of a mild-mann radio execut (ferrell) who strive to becom the best stepdad ever to hi wife' two children, but complic ensu when their freewheeling, freeload real father arrives, forc stepdad to compet for the affect of the kids. comedi daddi home will ferrel mark wahlberg linda cardellini sean ander",
      917: 'in a wood fill with magic and fairi tale characters, a baker and hi wife set out to end the cur put on them by their neighbor, a spite witch. fantasi comedi music witch cinderella princ fairi tale music princess sondheim cur base on stage music beanstalk duringcreditsst red ride hood meryl streep emili blunt jame corden rob marshal',
      918: "bank robber dalton russel enter a manhattan bank, lock the door and take hostages, work method and without haste. detect frazier is assign to negotiate, but hi mind is occupi with the corrupt charg he is facing. with an armi of polic surround the bank, the thief, the cop and a high-profil 'fixer' enter high-stak negotiations. crime drama thriller bank manag kidnap nazi background document ultimatum court case heist financ transact denzel washington clive owen jodi foster spike lee",
      919: "with friend like these, who need enemies? that' the question bad guy porter is left ask after hi wife and partner steal hi heist money and leav him for dead -- or so they think. five month and an endless reservoir of bitter later, porter' partner and the crook cop on hi tail learn how bad payback can be. drama action thriller crime new york heroin money crimin mel gibson kri kristofferson gregg henri brian helgeland",
      920: 'eight peopl embark on an expedit into the congo, a mysteri expan of unexplor africa where human greed and the law of natur have gone berserk. when the thrill-seek -- some with ulterior motiv -- stumbl across a race of killer apes. action adventur drama mysteri scienc fiction thriller gorilla kongo diamond mine diamond laura linney dylan walsh erni hudson frank marshal',
      921: 'benjamin ha lost hi wife and, in a bid to start hi life over, purcha a larg hou that ha a zoo – welcom news for hi daughter, but hi son is not happi about it. the zoo is need of renov and benjamin set about the work with the head keeper and the rest of the staff, but, the zoo soon run into financ trouble. drama comedi famili zoo matt damon scarlett johansson thoma haden church cameron crow',
      922: "a teacher open a time capsul that ha been dug up at hi son' elementari school; in it are some chill predict -- some that have alreadi occur and other that are about to -- that lead him to believ hi famili play a role in the event that are about to unfold. action adventur drama mysteri scienc fiction thriller cataclysm code suspen end of the world time capsul astrophysicist griev widow lexington massachusett westford massachusett predict research number news nicola cage rose byrn chandler canterburi alex proya",
      923: "tripp, an attract man in hi thirties, is still live with hi parent al and sue. tripp' best friend demo and ace are also still live in their parents' home and seem proud of it. al and sue are not happy, however, and are fascin when friend whose adult son ha recent move away from home reveal they hire an expert to arrang the matter and couldn't be happier with the result. comedi hotel mom romant comedi lie live with parent pretend relationship matthew mcconaughey sarah jessica parker zooey deschanel tom dey",
      924: "rachel keller must prevent evil samara from take possess of her son' soul. drama horror thriller nun base on novel bath tub nightmar son sequel remak vision good vs evil woman report mental institut videotap evil child naomi watt simon baker elizabeth perkin hideo nakata",
      925: "cal weaver is live the american dream. he ha a good job, a beauti house, great children and a beauti wife, name emily. cal' seemingli perfect life unravels, however, when he learn that emili ha been unfaith and want a divorce. over 40 and suddenli single, cal is adrift in the fickl world of dating. enter, jacob palmer, a self-styl player who take cal under hi wing and teach him how to be a hit with the ladies. comedi drama romanc soulmat midlif crisi marriag crisi woman law school crazi relationship steve carel juliann moor ryan gosl glenn ficarra",
      926: "garfield, the fat, lazy, lasagna lover, ha everyth a cat could want. but when jon, in an effort to impress the liz - the vet and an old high-school crush - adopt a dog name odi and bring him home, garfield get the one thing he doesn't want. competition. anim comedi famili competit moder lasagn garfield bill murray breckin meyer jennif love hewitt peter hewitt",
      927: 'luther krank is fed up with the commerci of christmas; he decid to skip the holiday and go on a vacat with hi wife instead. but when hi daughter decid at the last minut to come home, he must put togeth a holiday celebration. comedi famili holiday christma tim allen jami lee curti dan aykroyd joe roth',
      928: "the stori of oakland athlet gener manag billi beane' success attempt to put togeth a baseb team on a budget, by employ computer-gen analysi to draft hi players. drama underdog base on novel baseb teamwork sport partner meet oakland california strategi voic over statist brad pitt jonah hill philip seymour hoffman bennett miller",
      929: "a deadli airborn viru find it way into the usa and start kill off peopl at an epidem rate. col sam daniels' job is to stop the viru spread from a small town, which must be quarantined, and to prevent an over reaction by the white house. action drama scienc fiction thriller river gener research armi serum monkey epidem medic research dustin hoffman rene russo morgan freeman wolfgang petersen",
      930: "bill mark is a burned-out veteran of the air marshal service. he view the assign not as a life-sav duty, but as a desk job in the sky. however, today' flight will be no routin trip. shortli into the transatl journey from new york to london, he receiv a seri of mysteri text messag order him to have the govern transfer $150 million into a secret account, or a passeng will die everi 20 minutes. action thriller mysteri airplan conspiraci airplan crash cell phone hijack one night mysteri killer liam neeson juliann moor scoot mcnairi jaum collet-serra",
      931: "a taxi driver get more than he bargain for when he pick up two teen runaways. not onli doe the pair possess supernatur powers, but they'r also tri desper to escap peopl who have made them their targets. adventur famili fantasi scienc fiction thriller action spacecraft laser teleport telekinesi alien militari duringcreditsst supernatur power mountain dwayn johnson annasophia robb alexand ludwig andi fickman",
      932: "in a world in which great britain ha becom a fascist state, a mask vigil known onli as 'v' conduct guerrilla warfar against the oppress british government. when 'v' rescu a young woman from the secret police, he find in her an alli with whom he can continu hi fight to free the peopl of britain. action thriller fantasi detect vatican fascism satan fascist dystopia govern chancellor reveng personif of satan tortur hatr mask vigil cathol cathol priest cathol guilt jesuit veng spirit activist irish cathol veng jesuit priest gnostic occult natali portman hugo weav stephen rea jame mcteigu",
      933: "the dynam duo of chon wang and roy o'bannon return for anoth crazi adventure. thi time, they'r in london to aveng the murder of chon' father, but end up on an even bigger case. chon' sister is there to do the same, but instead unearth a plot to kill the royal family. no one believ her, though, and it' up to chon and roy (who ha romanc on hi mind) to prove her right. action adventur comedi western london england indian territori emperor reveng murder arrow duringcreditsst imperi seal jacki chan owen wilson fann wong david dobkin",
      934: "when the man in the yellow hat befriend curiou georg in the jungle, they set off on a non-stop, fun-fil journey through the wonder of the big citi toward the warmth of true friendship. adventur anim comedi famili museum product placement balloon jungl monkey famili predict cargo ship curio will ferrel drew barrymor david cross matthew o'callaghan",
      935: "maggi peyton, the new owner of number 53 - the free-wheelin' volkswagen bug with a mind of it own - put the car through it pace on the road to becom a nascar competitor. comedi famili adventur fantasi romanc car race victori car nascar woman director lindsay lohan michael keaton matt dillon angela robinson",
      936: "when the daughter of a psychiatrist is kidnapped, he' horrifi to discov that the abductors' demand is that he break through to a post traumat stress disord suffer young woman who know a secret.. thriller cemeteri diamant suspen psychiatrist killer michael dougla sean bean brittani murphi gari fleder",
      937: 'after get a tast for blood as children, hansel and gretel have becom the ultim vigilantes, hell-bent on retribution. now, unbeknownst to them, hansel and gretel have becom the hunted, and must face an evil far greater than witches... their past. fantasi horror action witch black magic steampunk good vs evil troll extrem violenc violenc witchcraft evil witch hunt witch hunter evil witch duringcreditsst hansel and gretel gun 3d jeremi renner gemma arterton famk janssen tommi wirkola',
      938: 'conni is a wife and mother whose 11-year marriag to edward ha lost it sexual spark. when conni liter run into handsom book collector paul, he sweep her into an all-consum affair. but edward soon becom suspici and decid to confront the other man. thriller drama adulteri infidel erot literatur lover new york citi erot thriller richard gere dian lane olivi martinez adrian lyne',
      939: 'a teenag fugit with an incr secret race to stay one step ahead of the mysteri forc seek destroy him in thi sci-fi action thriller. with three dead and one on the run, the race to find the elu number four begins. outwardli normal teen john smith never get too comfort in the same identity, and along with hi guardian, henri, he is constantli move from town to town. with each pass day, john gain a stronger grasp on hi extraordinari new powers, and hi bond to the be that share hi fantast fate grow stronger. action thriller scienc fiction adventur secret ident alien teenag boy teenag hero alien teenag interspeci romanc base on young adult novel superpow alex pettyf timothi olyph teresa palmer d.j. caruso',
      940: 'the middl eastern oil industri is the backdrop of thi ten drama, which weav togeth numer stori lines. bennett holiday is an american lawyer in charg of facilit a dubiou merger of oil companies, while bryan woodman, a switzerland-ba energi analyst, experi both person tragedi and opportun dure a visit with arabian royalty. meanwhile, veteran cia agent bob barn uncov an assassin plot with unsettl origins. drama thriller anti terror bomb assassin middl east lebanon cia capit global loss of son persia war against terror energi polici petrol georg clooney matt damon jeffrey wright stephen gaghan',
      941: 'an american ambassador is kill dure an attack at a u.s. compound in libya as a secur team struggl to make sen out of the chaos. action drama histori thriller war base on novel assault rifl mercenari libya biographi base on true stori heroism explo american abroad death 21st centuri cia agent u.s. ambassador jame badg dale john krasinski max martini michael bay',
      942: 'the journey of manolo, a young man who is torn between fulfil the expect of hi famili and follow hi heart. befor choo which path to follow, he embark on an incr adventur that span three fantast world where he must face hi greatest fears. romanc anim adventur comedi famili fantasi love triangl afterlif day of the dead bullfight diego luna chan tatum zoe saldana jorg r. gutierrez',
      943: "state-of-the-art secur system creator, jack stanfield ha cement hi reput as a man who' thought of everything. but when a crimin find a way into jack' person life, everyth jack hold dear is suddenli at stake. thriller bank technolog blackmail hacker seattl comput hacker firew harrison ford paul bettani virginia madsen richard loncrain",
      944: 'a master thief coincid is rob a hou where a murder in which the presid of the unit state is involv occur in front of hi eyes. he is forc to run yet may hold evid that could convict the president. a polit thriller from and star clint eastwood and base on a novel by david baldacci. crime drama thriller corrupt assassin washington d.c. rape white hou usa presid daughter govern suspen secret servic secret servic agent clint eastwood gene hackman ed harri clint eastwood',
      945: 'a femal senat succ in enrol a woman into combin reconnaiss team train where everyon expect her to fail. action drama poem middl east helicopt satellit navi sexism war armi sexual harass navi seal feminist soldier commando mental health drill instructor militari u.s. militari armi base reconnaiss sexual discrimin demi moor viggo mortensen ann bancroft ridley scott',
      946: 'in honor of hi birthday, san francisco banker nichola van orton, a financ geniu and a coldheart loner, receiv an unusu present from hi younger brother, conrad -- a gift certif to play a uniqu kind of game. in nearli a nanosecond, nichola find himself consum by a danger set of ever-chang rules, unabl to distinguish where the charad end and realiti begins. drama thriller mysteri brother brother relationship birthday danger of life birthday parti surpri michael dougla sean penn deborah kara unger david fincher',
      947: "the eeri and desert ghost town of silent hill draw a young mother desper to find a cure for her onli child' illness. unabl to accept the doctor' diagnosi that her daughter should be perman institut for psychiatr care, rose flee with her child, head for the abandon town in search of answer – and ignor the protest of her husband. it' soon clear thi place is unlik anywh she' ever been. it' smother by fog, inhabit by a varieti of strang be and period overcom by a live 'darkness' that liter transform everyth it touches. as rose search for her littl girl, she begin to learn the histori of the strang town and realiz that her daughter is just a pawn in a larger game. horror mysteri monster mother role burn of witch fog suffer dark sadism supernatur reveng surreal gore surviv good vs evil blood anoth dimen tortur creatur violenc demon witch burn base on video game dismemb religi fanat ghost town sleepwalk radha mitchel sean bean lauri holden christoph gan",
      948: "maverick old-guard coach jimmi mcginti is hire in the wake of a players' strike to help the washington sentinel advanc to the playoffs. but that imposs dream hing on whether hi replac can hunker down and do the job. so, mcginti dust off hi secret dossier of ex-play who never got a chanc (or screw up the one they were given) and knit togeth a bad-dream team of guy who just may give the sentinel their titl shot. comedi american footbal strike sport coach misfit american footbal player keanu reev gene hackman brook langton howard deutch",
      949: 'the charact we met a littl more than a decad ago are return to east great fall for their high-school reunion. in one long-overdu weekend, they will discov what ha changed, who hasn’t and that time and distanc can’t break the bond of friendship. it wa summer 1999 when four small-town michigan boy began a quest to lose their virginity. in the year that have passed, jim and michel marri while kevin and vicki said goodbye. oz and heather grew apart, but finch still long for stifler’ mom. now these lifelong friend have come home as adult to reminisc about – and get inspir by – the hormon teen who launch a comedi legend. comedi wife husband relationship sequel famili reunion masturb scat high school reunion quit a job milf duringcreditsst jason bigg alyson hannigan seann william scott jon hurwitz',
      950: "the polic tri to arrest expert hostag negoti danni roman, who insist he' be frame for hi partner' murder in what he believ is an elabor conspiracy. think there' evid in the intern affair offic that might clear him, he take everyon in the offic hostag and demand that anoth well-known negoti be brought in to handl the situat and secretli investig the conspiracy. action adventur crime drama mysteri thriller corrupt hostag pension innoc polic hostage-tak murder suspen conspiraci bullet wound negoti samuel l. jackson kevin spacey david mor f. gari gray",
      951: 'the town of silverton is in one day destroy by the unprec power of a seri of tornadoes. the popul is at the merci of the unpredict and deadli cyclones, while hunter warn that the worst is yet to come. most peopl find shelter, but some just go to the tornado for that one, uniqu shot. action thriller tornado student found footag disast movi richard armitag sarah wayn calli matt walsh steven qual',
      952: "back in sunni southern california and on the trail of two murderers, axel foley again team up with la cop billi rosewood. soon, they discov that an amu park is be use as a front for a massiv counterfeit ring – and it' run by the same gang that shot billy' boss. action comedi crime detect undercov secur camera carousel investig weapon sequel rescu counterfeit shootout dirti cop gunfight lo angel explo violenc foot chase frame car chase secret servic amu park roller coaster beverli hill buddi comedi eddi murphi judg reinhold héctor elizondo john landi",
      953: 'young sweetheart billi and kate move to the big apple, land job in a high-tech offic park and soon reunit with the friendli and lovabl gizmo. but a seri of accid creat a whole new gener of gremlins. the situat worsen when the devilish green creatur invad a top-secret laboratori and develop genet alter powers, make them even harder to destroy! comedi horror fantasi new york monster skyscrap mutant restaur human anim relationship mutat tv station die and death water research station fur bat current electr shock clever gremlin cowardli zach galligan phoeb cate john glover joe dant',
      954: "a success lawyer return to hi hometown for hi mother' funer onli to discov that hi estrang father, the town' judge, is suspect of murder. drama father son relationship judg lawyer robert duval robert downey jr. vera farmiga david dobkin",
      955: 'when a train carri atom warhead mysteri crash in the former soviet union, a nuclear specialist discov the accid is realli part of a plot to cover up the theft of the weapons. assign to help her recov the miss bomb is a crack special forc colonel. action thriller helicopt terrorist nuclear missil bridg train crash train woman director georg clooney nicol kidman marcel iureș mimi leder',
      956: "as the citi is lock down under quarantine, alic join a small band of elit soldiers, enlist to rescu the miss daughter of the creator of the mutat t-virus. it' a heart-pound race against time as the group face off against hord of blood- thirsti zombies, stealthi lickers, mutant canin and the most sinist foe yet. horror action scienc fiction martial art mutant dystopia rescu conspiraci evil corpor zombi base on video game milla jovovich sienna guillori ode fehr alexand witt",
      957: "bridget jone is becom uncomfort in her relationship with mark darcy. apart from discov that he' a conserv voter, she ha to deal with a new boss, a strang contractor and the worst vacat of her life. comedi romanc london england lovesick thailand clumsi fellow to drop brick captur woman director rené zellweg hugh grant colin firth beeban kidron",
      958: "matt lee whitlock, respect chief of polic in small banyan key, florida, must solv a viciou doubl homicid befor he himself fall under suspicion. matt lee ha to stay a few step ahead of hi own polic forc and everyon he' trust in order to find out the truth. thriller crime drama miami florida doubl murder divorc denzel washington eva mend sanaa lathan carl franklin",
      959: "forrest taft is an environ agent who work for the aegi oil compani in alaska. aegi oil' corrupt ceo, michael jennings, is the kind of person who doesn't care whether or not oil spill into the ocean or onto the land, just as long as it' make money for him. action thriller fight inuit petrol compani alaska enviro steven seagal michael cain joan chen steven seagal",
      960: 'everyon alway knew that max had a wild imagination, but no one believ that hi wildest creation -- a boy rai by watch great white shark and a girl with the forc of a volcano -- were real. now, these two pint-siz action master will show max that even an ordinari kid ha what it take to be extraordinary. adventur famili scienc fiction imaginari friend outcast taylor lautner taylor dooley cayden boyd robert rodriguez',
      961: 'twenty-someth richard travel to thailand and find himself in possess of a strang map. rumour state that it lead to a solitari beach paradise, a tropic bliss - excit and intrigued, he set out to find it. drama adventur romanc thriller hippi exot island beach map group dynam shark attack leader thailand commun backpack delu marijuana youth shark extramarit affair leonardo dicaprio guillaum canet tilda swinton danni boyl',
      962: "helen harri ha a glamorous, big-citi life work for one of new york' hottest model agencies. but suddenli her free-spirit life get turn upsid down when she must chose between the life she' alway loved, and the new love of her life! drama comedi romanc new york pastor world of fasion loss of parent mannequin fashion design famili relationship kate hudson john corbett joan cusack garri marshal",
      963: 'ninja assassin follow raizo (rain), one of the deadliest assassin in the world. taken from the street as a child, he wa transform into a train killer by the ozunu clan, a secret societi whose veri exist is consid a myth. but haunt by the merciless execut of hi friend by the clan, raizo break free from them and vanishes. now he waits, prepar to exact hi revenge. action crime thriller assassin assassin ninja fighter reveng ninja ninjutsu rain naomi harri sung kang jame mcteigu',
      964: 'a baseb legend almost finish with hi distinguish career at the age of forti ha one last chanc to prove who he is, what he is capabl of, and win the heart of the woman he ha love for the past four years. drama romanc baseb trainer career legend train sport kevin costner kelli preston john c. reilli sam raimi',
      965: "bounc from her job, erin grant need money if she' to have ani chanc of win back custodi of her child. but, eventually, she must confront the nake truth: to take on the system, she'll have to take it all off. erin strip to conquer, but she face unintend circumst when a hound dog of a congressman zero in on her and sharpen the shadi tool at hi fingertips, includ blackmail and murder. drama thriller crime blackmail strip club striptea polic u.s. congress demi moor burt reynold armand assant andrew bergman",
      966: "when phil and debbi winslow reloc from their nativ kansa to the sunni clime of orang county, their big-hearted, havoc-wreak great dane get a tast of the dog' life, california-style. famili comedi owen wilson emma stone georg lopez tom dey",
      967: 'a supernatur thriller center on three peopl -- a blue-collar american, a french journalist and a london school boy -- who are touch by death in differ ways. drama fantasi matt damon bryce dalla howard georg mclaren clint eastwood',
      968: 'tenaci homicid detect cassi mayweath and her still-green partner are work a murder case, attempt to profil two malevol brilliant young men: cold, calcul killer whose dark secret might explain their crimes. crime drama thriller detect secret fbi homicid evid nerd vice intellectu high school partner murder rich foren sandra bullock ben chaplin ryan gosl barbet schroeder',
      969: 'assassin robert rath arriv at a funer to kill a promin mobster, onli to wit a rival hire gun complet the job for him -- with grisli results. horrifi by the murder of innoc bystanders, rath decid to take one last job and then return to civilian life. but find hi way out of the world of contract kill grow ever more danger as rath fall for hi femal target and becom a mark man himself. action adventur crime thriller competit assassin cia bank cat mexican standoff seattl hitman mission of murder hidden camera rivalri rescu shootout polic chase sniper rifl silenc doubl cross caribbean detroit michigan sylvest stallon antonio bandera juliann moor richard donner',
      970: 'the stori of the early, murder root of the cannibalist killer, hannib lecter – from hi hard-scrabbl lithuanian childhood, where he wit the repul length to which hungri soldier will go to satiat themselves, through hi sojourn in france, where as a med student he hone hi appetit for the kill. crime drama thriller winter psychopath horror serial killer gaspard ulliel aaran thoma gong li peter webber',
      971: "ben and kati jordan are a marri coupl who go through hard time in fifteen year of marriage. comedi drama romanc love of one' life therapist psycholog wed relationship divorc bruce willi michel pfeiffer rob reiner rob reiner",
      972: 'a parasit alien soul is inject into the bodi of melani stryder. instead of carri out her race\' mission of take over the earth, "wanda" (a she come to be called) form a bond with her host and set out to aid other free humans. action adventur romanc scienc fiction thriller base on novel mass murder dystopia genocid alien inva duringcreditsst interspeci romanc alien parasit saoir ronan dian kruger jake abel andrew niccol',
      973: 'a parasit alien soul is inject into the bodi of melani stryder. instead of carri out her race\' mission of take over the earth, "wanda" (a she come to be called) form a bond with her host and set out to aid other free humans. action adventur romanc scienc fiction thriller base on novel mass murder dystopia genocid alien inva duringcreditsst interspeci romanc alien parasit song kang-ho park hae-il bae doona bong joon-ho',
      974: "gang-du is a dim-wit man work at hi father' tini snack bar near the han river. one day, gang-du' one and onli daughter hyun-seo come back from school irritated. she is angri at her uncle, nam-il, who visit her school as her guardian shamelessli drunk. ignor her father' excu for nam-il, hyun-seo is soon engross in her aunt nam-joo' archeri tournament on tv. meanwhile, outsid of the snack bar, peopl are fascin by an unidentifi object hang onto a bridge. in an instant, the object reveal itself as a terrifi creatur turn the riverbank into a gruesom sea of blood¡¦ amid the chaos, hyun-seo is helplessli snatch up by the creatur right befor gang-du' eyes. these unforeseen circumst render the govern powerless to act. but receiv a call of help from hyun-seo, the once-ordinari citizen gang-du and hi famili are thrust into a battl with the monster to rescu their belov hyun-seo. horror drama scienc fiction river mobil phone braveri archer daughter sewerag pollut formaldehyd snack bar famili saoir ronan dian kruger jake abel andrew niccol",
      975: "gang-du is a dim-wit man work at hi father' tini snack bar near the han river. one day, gang-du' one and onli daughter hyun-seo come back from school irritated. she is angri at her uncle, nam-il, who visit her school as her guardian shamelessli drunk. ignor her father' excu for nam-il, hyun-seo is soon engross in her aunt nam-joo' archeri tournament on tv. meanwhile, outsid of the snack bar, peopl are fascin by an unidentifi object hang onto a bridge. in an instant, the object reveal itself as a terrifi creatur turn the riverbank into a gruesom sea of blood¡¦ amid the chaos, hyun-seo is helplessli snatch up by the creatur right befor gang-du' eyes. these unforeseen circumst render the govern powerless to act. but receiv a call of help from hyun-seo, the once-ordinari citizen gang-du and hi famili are thrust into a battl with the monster to rescu their belov hyun-seo. horror drama scienc fiction river mobil phone braveri archer daughter sewerag pollut formaldehyd snack bar famili song kang-ho park hae-il bae doona bong joon-ho",
      976: 'a dea agent investig the disappear of a legendari armi ranger drill sergeant and sever of hi cadet dure a train exerci gone sever awry. action drama mysteri thriller crime drug addict militari court panama militari servic court ranger suprem court lager militari crime john travolta conni nielsen samuel l. jackson john mctiernan',
      977: 'still recov from a heart transplant, a retir fbi profil return to servic when hi own blood analysi offer clue to the ident of a serial killer. crime drama mysteri thriller houseboat heart investig polic ex-cop suspen heart transplant fbi profil clint eastwood jeff daniel anjelica huston clint eastwood',
      978: "an interpol agent and an attorney are determin to bring one of the world' most power bank to justice. uncov money laundering, arm trading, and conspiraci to destabil world governments, their investig take them from berlin, milan, new york and istanbul. find themselv in a chase across the globe, their relentless tenac put their own live at risk. drama thriller crime duringcreditsst clive owen naomi watt armin mueller-stahl tom tykwer",
      979: 'thi time, a cataclysm temblor hit lo angeles, turn it into an island. the presid view the quak as a sign from above, expel lo angel from the countri and make it a penal coloni for those found guilti of moral crimes. when hi daughter, part of a resist movement, steal the control unit for a doomsday weapon, snake again get tap to save the day. action adventur scienc fiction thriller prison usa presid earthquak dystopia attempt to escap lo angel reluct hero kurt russel staci keach steve buscemi john carpent',
      980: 'in the small town of rockwell, main in octob 1957, a giant metal machin befriend a nine-year-old boy and ultim find it human by unselfishli save peopl from their own fear and prejudices. adventur anim famili fantasi scienc fiction cold war friendship giant robot sit on a toilet fear of unknown 1950 lax eli marienth jennif aniston vin diesel brad bird',
      981: 'we anderson’ inci quirki comedi build up star complex charact like in ‘the royal tenenbaums’ with bill murray on in the lead role. an ocean adventur documentari film maker zissou is put in all imagin life situat and a tough life crisi as he attempt to make a new film about captur the creatur that cau him pain. adventur comedi drama ocean film make loss of mother cynic red cap ship bill murray anjelica huston cate blanchett we anderson',
      982: 'in 1863, mississippi farmer newt knight serv as a medic for the confed army. oppo to slavery, knight would rather help the wound than fight the union. after hi nephew die in battle, newt return home to jone counti to safeguard hi famili but is soon brand an outlaw deserter. forc to flee, he find refug with a group of runaway slave hide out in the swamps. forg an allianc with the slave and other farmers, knight lead a rebellion that would forev chang history. war action drama histori thriller slaveri american civil war matthew mcconaughey gugu mbatha-raw mahershala ali gari ross',
      983: 'a man against capit punish is accu of murder a fellow activist and is sent to death row. drama thriller crime prison journalist texa professor death penalti death row interview murder report intern innoc activist kevin spacey kate winslet laura linney alan parker',
      984: 'texa ranger roland sharp is assign to protect the onli wit to the murder of a key figur in the prosecut of a drug kingpin -- a group of univ of texa cheerleaders. sharp must now go undercov as an assist cheerlead coach and move in with the young women. comedi action tommi lee jone cedric the entertain christina milian stephen herek',
      985: 'brooklyn mobster and prolif hit man jimmi conlon ha seen better days. longtim best friend of a mob boss, jimmi is haunt by the sin of hi past—a well as a dog polic detect who’ been one step behind jimmi for 30 years. but when jimmy’ estrang son becom a target, jimmi must make a choic between the crime famili he chose and the real famili he abandon long ago. now, with nowher safe to turn, jimmi ha just one night to figur out exactli where hi loyalti lie and to see if he can final make thing right. action crime drama mysteri thriller hitman reveng murder on the run mobster liam neeson ed harri joel kinnaman jaum collet-serra',
      986: 'a russian teenag live in london who die dure childbirth leav clue to a midwif in her journal that could tie her child to a rape involv a violent russian mob family. thriller crime mysteri london england gay male nuditi femal nuditi father son relationship sex jealousi underworld undercov hitman russian diari human traffick midwif murder mother daughter relationship orphan gangster motorcycl bathhou naomi watt viggo mortensen vincent cassel david cronenberg',
      987: 'when they take some friend on an extrem sport adventure, the last thing jare and sam expect to see below the shark-infest water is a legendari pirat ship rumor to contain million of dollar in gold. but their good fortun is short-lived, as a ruthless gang of crimin get word of what they have uncovered. action thriller adventur crime dive cocain shipwreck sail airplan wrack paul walker jessica alba scott caan john stockwel',
      988: "in 1429 a teenag girl from a remot french villag stood befor her king with a messag she claim came from god; that she would defeat the world' greatest armi and liber her countri from it polit and religi turmoil. follow her mission to reclaim god' dimish kingdom - through her amaz victori until her violent and untim death. adventur drama action histori war schizophrenia franc rape sieg biographi orléan charl vii. fal histori joan of arc religi delu milla jovovich dustin hoffman fay dunaway luc besson",
      989: "a fantasi movi about an arrogant, lazi princ and hi more heroic brother who must complet a quest in order to save their father' kingdom. comedi kidnap traitor virgin princ princess reveng minotaur knight dragon wed king sword and sorceri danni mcbride jame franco natali portman david gordon green",
      990: "publisher, will atenton quit a lucr job in new york to reloc hi wife, libbi and their daughter to a quaint town in new england. however, as they settl into their home the atenton discov that a woman and her children were murder there, and the surviv husband is the town' prime suspect. with help from a neighbor who wa close to the murder family, will piec togeth a horrifi chain of events. drama thriller mysteri hou fire exten ladder last day on job daniel craig naomi watt rachel weisz jim sheridan",
      991: 'a misguid museum guard who lose hi job and then tri to get it back at gunpoint is thrown into the fierc world of ratings-driven tv gone mad. action drama thriller journalist museum hostag drama independ film john travolta dustin hoffman mia kirshner costa-gavra',
      992: "babi bink couldn't ask for more; he ha ador (if somewhat sickly-sweet) parents, he live in a huge mansion, and he' just about to appear in the social page of the paper. unfortunately, not everyon in the world is as nice as babi bink' parents; especi the three enterpri kidnap who pretend to be photograph from the newspaper. success kidnap babi bink, they have a harder time keep hold of the rascal, who not onli keep one step ahead of them, but seem to be more than a littl bit smarter than the three bumbl criminals. action adventur comedi famili babi hoodlum lost child joe mantegna lara flynn boyl joe pantoliano patrick read johnson",
      993: 'set in puritan boston in the mid 1600s, the stori of seamstress hester prynne, who is outcast after she becom pregnant by a respect reverend. she refu to divulg the name of the father, is "convicted" of adulteri and forc to wear a scarlet "a" until an indian attack unit the puritan and lead to a reevalu of their law and morals. drama histori romanc base on novel burn of witch puritan pregnanc period drama extramarit affair demi moor gari oldman robert duval roland joffé',
      994: "wife and mother valeri plame (naomi watts) ha a doubl life as a cia operative, hide her vocat from famili and friends. her husband, joseph wilson (sean penn), write a controversi articl in the new york times, refut stori about the sale of enrich uranium to iraq, then valerie' secret work and ident is leak to the press. with her cover blown and other peopl endangered, valerie' career and person life begin to unravel. drama thriller cia nuclear scientist iraq politician duringcreditsst naomi watt sean penn ty burrel doug liman",
      995: 'the daughter of actor, laurenc harvey turn away from her career as a ford model to becom a bounti hunter. action crime bounti hunter fbi weapon spectacl keira knightley mickey rourk edgar ramírez toni scott',
      996: 'someon doe a nasti hatchet job on a san fransisco big noi and the assist d.a. take charg of the investigation. through a web of blackmail and prostitut involv the governor, an old lover of the law man emerg as a prime suspect and he ha to deal with hi person feel as well as the case. action thriller mysteri romanc callgirl san francisco investig murder david caruso linda fiorentino chazz palminteri william friedkin',
      997: 'mind-control technolog ha taken societi by a storm, a multiplay on-lin game call "slayers" allow player to control human prison in mass-scale. simon (lerman) control kabl (butler), the onlin champion of the game. kable\' ultim challeng becom regain hi ident and independ by defeat the game\' mastermind (hall). action thriller scienc fiction dystopia mind control gun battl wrong imprison dystop futur wrong convict onlin game gerard butler michael c. hall logan lerman brian taylor',
      998: "ethan wate just want to get to know lena duchann better, but unbeknownst to him, lena ha strang powers. as lena' 16th birthday approach she might decid her fate, to be good or evil. a choic which will impact her relationship forever. fantasi drama romanc civil war southern usa magic light dark class prejud caster base on young adult novel alden ehrenreich alic englert jeremi iron richard lagraven",
      999: "tell the stori of rainbow randolph, the corrupt, costum star of a popular children' tv show, who is fire over a briberi scandal and replac by squeaky-clean smoochy, a puffi fuscia rhinoceros. as smoochi catapult to fame - score hit rate and the affect of a network execut - randolph make the unsuspect rhino the target of hi numer outrag attempt to exact reveng and reclaim hi statu as america' sweetheart. comedi crime drama thriller corrupt moder tv show success irish mob duringcreditsst robin william catherin keener edward norton danni devito",
      ...}}




```python
pickle.dump(new_df.to_dict(),open('movies_dict.pkl','wb'))
```


```python
pickle.dump(similarity,open('similarity.pkl','wb'))
```


```python

```
