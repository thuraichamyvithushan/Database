**1.Create a Database called movies?**
```
test> use movies db
switched to db movies
movies>
``` 

2.Create a collection called moviedetails?
movie> db.createCollection("moviedetails")
{ ok: 1 }

3.Create above 5 movie documents into a moviedetails collection?
movies> db.moviedetails.insertMany([{"title":"jurrasic park","type":"adventure","director":"Steven spielberg","release year":"1993"},{"title":"Forrest gump","type":"drama","director":"Robert zemeckies","release year":"1994"},{"title":"titanic","type":"Romance","director":"James cameron","release year":"1997"},{"title":"The dark knight","type":"Action","director":"Christopher nolan","release year":"2008"},{"title":"avatar","type":"Science fiction","director":"James cameron","release year":"2009"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654c860ec8a945eaf77c5bb6"),
    '1': ObjectId("654c860ec8a945eaf77c5bb7"),
    '2': ObjectId("654c860ec8a945eaf77c5bb8"),
    '3': ObjectId("654c860ec8a945eaf77c5bb9"),
    '4': ObjectId("654c860ec8a945eaf77c5bba")
  }
}

4.List all documents created?
movies> db.moviedetails.find()
[
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb6"),
    title: 'jurrasic park',
    type: 'adventure',
    director: 'Steven spielberg',
    'release year': '1993'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb7"),
    title: 'Forrest gump',
    type: 'drama',
    director: 'Robert zemeckies',
    'release year': '1994'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb8"),
    title: 'titanic',
    type: 'Romance',
    director: 'James cameron',
    'release year': '1997'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb9"),
    title: 'The dark knight',
    type: 'Action',
    director: 'Christopher nolan',
    'release year': '2008'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bba"),
    title: 'avatar',
    type: 'Science fiction',
    director: 'James cameron',
    'release year': '2009'
  }
]

5.List James Cameron’s movies?
movies> db.moviedetails.find({director:"James cameron"})
[
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb8"),
    title: 'titanic',
    type: 'Romance',
    director: 'James cameron',
    'release year': '1997'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bba"),
    title: 'avatar',
    type: 'Science fiction',
    director: 'James cameron',

6.List  James Cameron’s movies released in 2009?
movies> db.moviedetails.find({ 'release year': '2009'})
[
  {
    _id: ObjectId("654c860ec8a945eaf77c5bba"),
    title: 'avatar',
    type: 'Science fiction',
    director: 'James cameron',
    'release year': '2009'
  }
]

7.Delete the movie which you don’t like?
movies> db.moviedetails.remove({"title":"Forrest gump","type":"drama","director":"Robert zemeckies","release year":"1994"})
DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }

8.Add the movie which is your favourite?
movies>  db.moviedetails.insertOne({"title":"leo","type":"action","director":"logi","release year":"2023"})
{
  acknowledged: true,
  insertedId: ObjectId("654c8d38c8a945eaf77c5bbb")
}
movies>  db.moviedetails.find()
[
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb6"),
    title: 'jurrasic park',
    type: 'adventure',
    director: 'Steven spielberg',
    'release year': '1993'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb8"),
    title: 'titanic',
    type: 'Romance',
    director: 'James cameron',
    'release year': '1997'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bb9"),
    title: 'The dark knight',
    type: 'Action',
    director: 'Christopher nolan',
    'release year': '2008'
  },
  {
    _id: ObjectId("654c860ec8a945eaf77c5bba"),
    title: 'avatar',
    type: 'Science fiction',
    director: 'James cameron',
    'release year': '2009'
  },
  {
    _id: ObjectId("654c8d38c8a945eaf77c5bbb"),
    title: 'leo',
    type: 'action',
    director: 'logi',
    'release year': '2023'
  }
]
movies> 

9.List movie Directed  by Christopher Nolan in 1994?
movies> db.moviedetails.find({"director":"Christopher nolan","release year":"1994"})


10.List out the Director’s Name in your document?
movies> db.moviedetails.distinct("director")
[ 'Christopher nolan', 'James cameron', 'Steven spielberg', 'logi' ]



