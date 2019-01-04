# MongoDb

The field name _id is reserved for use as a primary key; its value must be unique in the collection, is immutable, and may be of any type other than an array.
Field names cannot contain the null character.

Top-level field names cannot start with the dollar sign ($) character.

Otherwise, starting in MongoDB 3.6, the server permits storage of field names that contain dots (i.e. .) and dollar signs (i.e. $).

The total size of an index entry, which can include structural overhead depending on the BSON type, must be less than 1024 bytes.


Join with dbRef
db.GroupPermission.aggregate([
        {$match:{"name":"AssistantTest"}},
        {$unwind:"$permissions"}
        ,
        {$project:{"name":1,"permissions":{$objectToArray:"$permissions"}}}
        ,{$project:{name:1,"permissions":{$slice:["$permissions",-1]}}}
        ,{$lookup:{from:"permissions",localField:"permissions.v",foreignField:"_id",as:"permissions"}}
        ])
