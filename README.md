# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Queries 
Make sure to reseting the database with `rails db:seed` before running quieries.

## Niveau facile
    
1. Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
  - `Album.count` 
  - R = 347
  
2. Qui est l'auteur de la chanson "White Room" ?
  - `my_album = Track.find_by(title: 'White Room')`
  - `my_album.artist`
  - R = Eric Clapton

3. Quelle chanson dure exactement 188133 milliseconds ?
- `my_song = Track.find_by(duration: 188133)`
- `my_song.title` 
- R = Perfect

4. Quel groupe a sorti l'album "Use Your Illusion II" ?
- `my_band = Album.find_by(title: "Use Your Illusion II")`
- `my_band.artist`
 R = Guns N Roses

## Niveau Moyen

1. Combien y a t'il d'albums dont le titre contient "Great" ?
- `my_album = Album.where("title like ?", "%Great%")`
- `my_album.count`
- R = 13 

2. Supprime tous les albums dont le nom contient "music".
- `Album.where("title like ?", "%music%").destroy_all`

3. Combien y a t'il d'albums écrits par AC/DC ?
- `my_album = Album.where(artist: 'AC/DC')`
- `my_album.count`
- R = 2

4. Combien de chanson durent exactement 158589 millisecondes ?
- `my_song = Track.where(duration: '158589')`
- R = 0

## Niveau Difficile

1. puts en console tous les titres de AC/DC. 
- `my_album = Track.where(artist: 'AC/DC')`
- `my_album.each { |t| puts t.title}`
- R = For Those About To Rock (We Salute You),
Put The Finger On You,
Lets Get It Up,
Inject The Venom,
Snowballed,
Evil Walks,
C.O.D.,
Breaking The Rules,
Night Of The Long Knives,
Spellbound,
Go Down,
Dog Eat Dog,
Let There Be Rock,
Bad Boy Boogie,
Problem Child,
Overdose,
Hell Aint A Bad Place To Be,
Whole Lotta Rosie,


2. puts en console tous les titres de l'album "Let There Be Rock".
- `my_title = Track.where(album: 'Let There Be Rock')`
- `my_title.each { |t| puts t.title}`
- R = Go Down, Dog Eat Dog, Let There Be Rock, Bad Boy Boogie, Problem Child, Overdose, Hell Aint A Bad Place To Be, Whole Lotta Rosie


3. Calcule le prix total de cet album ainsi que sa durée totale.
- `cost = Track.where(album: 'Let There Be Rock')`
- `cost.sum('price')`
- R = 7.920000000000001 
- `cost.sum('duration')`
- R = 2453259 


4. Calcule le coût de l'intégralité de la discographie de "Deep Purple".
- `Track.where(artist: 'Deep Purple').sum('price')`
- R = 90.0899999999999

5. Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
- `crazy = Track.where(artist: 'Eric Clapton')`
- `crazy.each { |t| crazy.update(artist: "Britney Spears")}`
