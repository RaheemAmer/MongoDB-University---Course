# MongoDB-University---Course
Solutions to the lab

【Chapter4】: Advanced CRUD Operations:

1.Query Operators - Comparision
db.trips.find({ "tripduration": { "$lte" : 70 }, "usertype": { "$ne": "Subscriber" } }).pretty()


2.Query Operators - Logic
db.routes.find({ "$and":[ { "$or" :[ { "dst_airport": "KZN" }, { "src_airport": "KZN" } ] },{ "$or" :[ { "airplane": "CR2" }, { "airplane": "A81" } ] }   ]}).pretty()


3.Expressive Query Operator
db.trips.find({ "$expr": { "$eq": [ "$end station id", "$start station id"] } }).count()
db.trips.find({ "$expr": {

                                "$and": [

                                             { "$gt": [ "$tripduration", 1200 ]},

                                             { "$eq": [ "$end station id", "$start station id" ]}

                                             ]

                                       }

                        }).count()

db.companies.find({"$expr":{"$lt":["$founded_year","$number_of_employees"]}}).count()

db.companies.find({"$expr":{"$gt":["$number_of_employees","$founded_year"]}}).count()

db.companies.find({"$expr":{"$eq":["$permalink","$twitter_username"]}}).count()


4. Array Operators
db.listingsAndReviews.find({"reviews": {"$size":50},"accommodates": {"$gt":6}}).pretty()   
db.listingsAndReviews.find({"$and":[{"property_type":"House"},{"amenities":{ "$all": ["Changing table"]}}]}).count() 
db.listingsAndReviews.find({ "amenities":{ "$all": [ "Free parking on premises", "Wifi", "Air conditioning" ] },"bedrooms": { "$gte":  2 } }).pretty()



