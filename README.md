# README

Chinook Music (niveau facile et moyen uniquement)

a) Niveau facile

1. Quel est le nombre total d'objets `Album` contenus dans la base (sans regarder les id bien sûr) ?

3.2.2 :001 > Album.count
  Album Count (0.1ms)  SELECT COUNT(*) FROM "albums"
 => 347 

2. Qui est l'auteur de la chanson "White Room" ?

Track.where(title: "White Room")

  title: "White Room",
  album: "The Cream Of Clapton",
  artist: "Eric Clapton",
  duration: 301583,
  size: 9872606,
  price: 0.99,
 

3. Quelle chanson dure exactement 188133 milliseconds ?

3.2.2 :005 > Track.find_by(duration: 188133)

 title: "Perfect",
 album: "Jagged Little Pill",
 artist: "Alanis Morissette",
 duration: 188133,
 size: 6145404,
 price: 0.99,

4. Quel groupe a sorti l'album "Use Your Illusion II" ?

3.2.2 :006 > Album.where(title: "Use Your Illusion II")

  id: 92,
  title: "Use Your Illusion II",
  artist: "Guns N Roses",

##### b) Niveau Moyen


1. Combien y a t'il d'albums dont le titre contient "Great" ?

3.2.2 :009 > Album.where("title like? ", "%great%")
  
  id: 36,
  title: "Greatest Hits II",
  artist: "Queen",
  
  id: 37,
  title: "Greatest Kiss",
  artist: "Kiss",
  
  id: 67,
  title: "Vault: Def Leppards Greatest Hits",
  artist: "Def Leppard",
  
  id: 141,
  title: "Greatest Hits",
  artist: "Lenny Kravitz",
  
  id: 162,
  title: "Motley Crue Greatest Hits",
  artist: "Mötley Crüe",
  
  id: 185,
  title: "Greatest Hits I",
  artist: "Queen",
  
  id: 202,
  title: "Rotten Apples: Greatest Hits",
  artist: "Smashing Pumpkins",
  
  id: 215,
  title: "The Police Greatest Hits",
  artist: "The Police",
  
  id: 286,
  title: "Great Opera Choruses",
  artist: "Chicago Symphony Chorus, Chicago Symphony Orchestra & Sir Georg Solti",
  
  id: 294,
  title: "Great Performances - Barbers Adagio and Other Romantic Favorites for Strings",
  artist: "Leonard Bernstein & New York Philharmonic",
 
  id: 305,
  title: "Great Recordings of the Century - Mahler: Das Lied von der Erde",
  artist: "Gustav Mahler",
 
  id: 339,
  title: "Great Recordings of the Century: Paganinis 24 Caprices",
  artist: "Itzhak Perlman",
  
  id: 341,
  title: "Great Recordings of the Century - Shubert: Schwanengesang, 4 Lieder",
  artist: "Gerald Moore",

2. Supprime tous les albums dont le nom contient "music".

albums_to_delete = Album.where("title like? ", "%music%")

3.2.2 :011 > tp albums_to_delete
ID  | TITLE                          | ARTIST                         | CREATED_AT              | UPDATED_AT             
----|--------------------------------|--------------------------------|-------------------------|------------------------
315 | Handel: Music for the Royal... | English Concert & Trevor Pi... | 2023-10-25 17:56:03     | 2023-10-25 17:56:03    
319 | Armada: Music from the Cour... | Fretwork                       | 2023-10-25 17:56:03     | 2023-10-25 17:56:03    
333 | Purcell: Music for the Quee... | Equale Brass Ensemble, John... | 2023-10-25 17:56:03     | 2023-10-25 17:56:03    
346 | Mozart: Chamber Music          | Nash Ensemble                  | 2023-10-25 17:56:03     | 2023-10-25 17:56:03    
 => 0.001255821 
 
3.2.2 :013 > albums_to_delete.destroy_all
  TRANSACTION (0.1ms)  begin transaction
  Album Destroy (0.5ms)  DELETE FROM "albums" WHERE "albums"."id" = ?  [["id", 315]]
  TRANSACTION (6.1ms)  commit transaction
  TRANSACTION (0.0ms)  begin transaction
  Album Destroy (0.2ms)  DELETE FROM "albums" WHERE "albums"."id" = ?  [["id", 319]]
  TRANSACTION (4.8ms)  commit transaction
  TRANSACTION (0.1ms)  begin transaction
  Album Destroy (0.2ms)  DELETE FROM "albums" WHERE "albums"."id" = ?  [["id", 333]]
  TRANSACTION (4.7ms)  commit transaction
  TRANSACTION (0.0ms)  begin transaction
  Album Destroy (0.2ms)  DELETE FROM "albums" WHERE "albums"."id" = ?  [["id", 346]]
  TRANSACTION (4.8ms)  commit transaction
 =>

3. Combien y a t'il d'albums écrits par AC/DC ?

3.2.2 :015 > Album.where(artist: "AC/DC").count
  Album Count (0.4ms)  SELECT COUNT(*) FROM "albums" WHERE "albums"."artist" = ?  [["artist", "AC/DC"]]
 => 2 

4. Combien de chanson durent exactement 158589 millisecondes ?

3.2.2 :016 > Track.where(duration: 158589)
  Track Load (0.3ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."duration" = ?  [["duration", 158589]]
 => [] 