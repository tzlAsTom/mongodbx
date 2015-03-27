# mongox(not ready yet)
A wrapper of Node.js mongoDB driver with document key compression

## examples
```
//var mongodb = require('mongodbx');
var mongodb = require('./index.js');

mongodb.mongox.initialize({
    'collections': {
        'mongoxTest': {
            columns: {'name': 'n', 'expireTime': 'e', 'deleteFlag': 'd'},
            enableCompact: true,
        }
    }
});

var record = {'name': 99, 'expireTime': 2, 'deleteFlag': 3, 'notConfiguredKey': 4};
var db = new mongodb.Db('test', new mongodb.Server('localhost', 27017));
db.open(function(err, db){
    var collection = db.collection("mongoxTest");
    collection.insert(record, {w:1}, function(){
        collection.find().toArray(console.log);
    });
});
```

###Will get:
```
[tong@localhost mongox]$ node test.js
null [ { _id: 5514f11dbc6aa25f2d165e8c,    name: 99,    expireTime: 2,    deleteFlag: 3,    notConfiguredKey: 4 } ]
```

###Check with mongo shell:
```
rs0:PRIMARY> db.mongoxTest.find()
{ "_id" : ObjectId("5514f11dbc6aa25f2d165e8c"), "n" : 99, "e" : 2, "d" : 3, "notConfiguredKey" : 4 }
rs0:PRIMARY>
```

## Background

## API

## not ready yet

## bad side

## known issues

## look into the future
