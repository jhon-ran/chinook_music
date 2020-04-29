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
## Niveau facile
    
1. Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
  - Album.count R = 347
  
2. Qui est l'auteur de la chanson "White Room" ?
  - my_album = Track.find_by(title: 'White Room')
  - my_album.artist
  - R = Eric Clapton

3. Quelle chanson dure exactement 188133 milliseconds ?
- my_song = Track.find_by(duration: 188133)
- my_song.title R = Perfect

4. Quel groupe a sorti l'album "Use Your Illusion II" ?
- my_band = Album.find_by(title: "Use Your Illusion II")
- my_band.artist R = Guns N Roses

## Niveau Moyen

1. Combien y a t'il d'albums dont le titre contient "Great" ?
- my_album = Album.where("title like ?", "%Great%")
- my_album.count R = 13 
- Supprime tous les albums dont le nom contient "music".

2. Combien y a t'il d'albums écrits par AC/DC ?
- my_album = Album.where(artist: 'AC/DC')
- my_album.count    R = 2

3. Combien de chanson durent exactement 158589 millisecondes ?
- my_song = Track.where(duration: '158589')
- R = 0
