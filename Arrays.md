# Arrays


  db.inventory.insertMany([
   { item: "journal", qty: 25, tags: ["blank", "red"], dim_cm: [ 14, 21 ] },
   
   { item: "notebook", qty: 50, tags: ["red", "blank"], dim_cm: [ 14, 21 ] },
   
   { item: "paper", qty: 100, tags: ["red", "blank", "plain"], dim_cm: [ 14, 21 ] },
   
   { item: "planner", qty: 75, tags: ["blank", "red"], dim_cm: [ 22.85, 30 ] }
   
   
  
  
 db.inventory.find( { tags: ["red", "blank"] } ) 
 
  
  The above query fetches all the documents whose tag field has an array with exactly elements "red" and "black" with same       specified order in the query;
  
  i.e  { item: "notebook", qty: 50, tags: ["red", "blank"], dim_cm: [ 14, 21 ] }
  
  
  if we see above the document ({ item: "planner", qty: 75, tags: ["blank", "red"], dim_cm: [ 22.85, 30 ] }) is not returned     because order also matters (tags: ["red", "blank"] }).
  
  
  # $all  -->
  
  if you want to find all the documents whose array has "red" and "black" without regard the order  or other elements use $all
  
  db.inventory.find({"tags":{$all:["red","black"]}});
  
  <==>  db.inventory.find( { $and:[{"tags":"red"} ,{"tags":"black"}] })

  
  will return all the documents.
  
  
  # $elemMatch -->
  
  Matches documents that contains array fields with atleast one element that satisfies all the specified query criteria.
  
  { field: { $elemMatch: { query1, query2, ... } } }
  
  **$elemMatch, $slice, and $ are the only way to project specific elements to include in the returned array. For instance, you cannot project specific array elements using the array index; e.g. { "instock.0": 1 } projection will not project the array with the first element.**
  
  
  
  
  
  
  
  
