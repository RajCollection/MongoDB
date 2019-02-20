# MongoDB

Install mongodb .exe file

setup mongodb

     mongod --directoryperdb --dbpath C:\mongodb\data\db --logpath C:\mongodb\log\mongo.log --logappend --rest --install

Start MongoDB Service

    net start MongoDB

Start MongoDB shell

    mongo

Show databases

    show dbs

Use database or Create database

    use mycustomers

See which database using

    db

Create user

    db.createUser({
        user:"Raj",
        pwd:"1234",
        roles: ["readWrite","dbAdmin"]
    });

Create collection(table)

    db.createCollection('customer');

Show collections

    show collections

Insert row data

    db.customer.insert({first_name:"John", last_name:"Doe"});

Select * from collection

    db.customer.find();

Insert multiple rows

    db.customer.insert([{first_name:"John1", last_name:"Doe1"},{first_name:"John2", last_name:"Doe2"},{first_name:"John3", last_name:"Doe3", gender:"female"}]);

Show in structured format

    db.customer.find().pretty();

Update collection, where first_name="John"

    db.customer.update({first_name:"John"},{first_name:"John", last_name:"Doe", gender:"male"});

Inserts if column not exists or update column value

    db.customer.update({first_name:"John"},{$set:{gender:"female"}});
    db.customer.update({first_name:"John"},{$set:{dob:"12-11-2017"}});

Remove column

    db.customer.update({first_name:"John"},{$unset:{dob:1}});
    
Remove single row data

    db.customer.remove({id});
    
Remove all rows of data / clear collection data

    db.customer.remove({});

Update if exist, insert if not (upsert:true)

    db.customer.update({first_name:"Mary"},{first_name:"Mary", last_name:"Samson", gender:"female"},{upsert:true});

Rename column name

    db.customer.update({first_name:"Mary"},{$rename:{"gender":"sex"}});

Remove row data from collection, where first_name="Mary"

    db.customer.remove({first_name:"Mary"});

Select or print row data where first_name="John"

    db.customer.find({first_name:"John"});

Insert or update age column

    db.customer.update({first_name:"John"},{age:40});

Select or print rows where age is less than 50

    db.customer.find({age:{$lt:50}}).pretty();

Sort rows based on age

    db.customer.find().sort({age:1}).pretty();

Sort rows based on first_name

    db.customer.find().sort({first_name:1}).pretty();

Count number of rows

    db.customer.find().count();

Count number of rows where gender="male"

    db.customer.find({gender:"male"}).count();

Print or select only 2 rows where gender="female"

    db.customer.find({gender:"female"}).limit(2);

Print or select only 2 rows where gender="female" and sort based on last_name

    db.customer.find({gender:"female"}).limit(2).sort({last_name:1});

Print all first name using forEach function

    db.customer.find().forEach(function(doc){print("Customer Name: "+ doc.first_name)});

Drop database

    db.dropDatabase();

Drop collection

    db.COLLECTION_NAME.drop()
