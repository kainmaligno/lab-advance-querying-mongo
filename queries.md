![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies that it's name match 'Babelgum'. Retrieve only their `name` field.
 -**`query`**: db.companies.find({name:'Babelgum'},{name:1,_id:0})

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.
-**`query`**:                 db.companies.find({number_of_employees:{$gt:5000}}, 
 -**`proyection`**:           {_id:0, number_of_employees:1})
 -**`limit`**:                .limit(20)
 -**`sort`**:                 .sort({number_of_employes:1})

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fileds.

-**`query`**:               db.companies.find({$and:[{founded_year:{$gt:1999}},{founded_year:{$lt:2006}}]},
-**`proyection`**:          {_id:0, name:1,founded_year:1})

### 4. All the companies that had an IPO of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.
-**`query`**:          db.companies.find({$and:[{'ipo.valuation_amount':{$gt:100000000}},{founded_year:{$lt:2010}}]}, 
-**`proyection`**:     {_id:0, name:1,ipo:1})

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.
-**`query`**:            db.companies.find({$and:[{number_of_employees:{$lt:1000}},{founded_year:{$lt:2005}}]},            
 -**`proyection`**:     {_id:0, number_of_employee:1})    
 -**`limit`**:          .sort({number_of_employee:1})   
 -**`sort`**:           .limit(10)

### 6. All the companies that don't include the `partners` field.
-**`query`**:          db.companies.find({partners:{$exists:true}})      
 -**`proyection`**:           
 -**`limit`**:              
 -**`sort`**: 
### 7. All the companies that have a null type of value on the `category_code` field.
-**`query`**:            db.companies.find({category_code:{$type:['null']}})    
 -**`proyection`**:           
 -**`limit`**:              
 -**`sort`**: 
### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.
-**`query`**:                ({$and:[{number_of_employees:{$gt:100}},{number_of_employees:{$lt:1001}}]},
 -**`proyection`**:           {_id:0, name:1, number_of_employees:1})
 -**`limit`**:              
 -**`sort`**: 
### 9. Order all the companies by their IPO price descendently.
-**`query`**:           db.companies.find({},{_id:0,ipo:1,name:1}).sort({'ipo.valuation_amount':-1})

                          me sale este error  "Sort operation used more than the maximum 33554432 bytes of RAM.
 -**`proyection`**:           
 -**`limit`**:        //usar limite de 50      
 -**`sort`**: 
### 10. Retrieve the 10 companies with more employees, order by the `number of employees`
-**`query`**:               db.companies.find({},
 -**`proyection`**:          {_id:0,name:1, number_of_employees:1})
 -**`limit`**:              .limit(200)  
 -**`sort`**:               .sort({number_of_employees:-1})    //use invertido por que de lo contrario las primeras aparecen null en                                                                       empleados 
### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.
-**`query`**:           db.companies.find({founded_month:{$gt:6}},    
 -**`proyection`**:     {_id:0,name:1,founded_month:1})      
 -**`limit`**:          .limit(1000)     
 -**`sort`**: 
### 12. All the companies that have been 'deadpooled' after the third year.//no entiendo como es esta pregunta si el year esta en 2000 
-**`query`**:                db.companies.find({deadpooled_year:{$gt:2000}},
 -**`proyection`**:           {_id:0,name:1, deadpooled_year:1})
 -**`limit`**:              
 -**`sort`**: 
### 13. All the companies founded before 2000 that have and acquisition amount of more than 10.000.000
-**`query`**:       db.companies.find({$and:[{founded_year:{$lt:2000}},{'acquisition.price_amount':{$gt:10000000}}]},
       
 -**`proyection`**: {_id:0, name:1, founded_year:1,'acquisition.price'})         
 -**`limit`**:              
 -**`sort`**: 
### 14. All the companies that have been acquired after 2015, order by the acquisition amount, and retrieve only their `name` and `acquisiton` field.
-**`query`**:                db.companies.find({'acquisition.acquired_year':{$gt:2005}},
 -**`proyection`**:           {_id:0,name:1,acquisition:1})
 -**`limit`**:              
 -**`sort`**:                 .sort({'acquisition.price_amount':1})
### 15. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.
-**`query`**:                db.companies.find({},{_id:0, name:1, founded_year:1})
 -**`proyection`**:           
 -**`limit`**:              
 -**`sort`**:                  .sort({founded_year:1})        //"Sort operation used more than the maximum 33554432 bytes of RAM.             
### 16. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `aquisition price` descendently. Limit the search to 10 documents.
-**`query`**:                db.companies.find({founded_day:{$lt:8}},
 -**`proyection`**:           {_id:0, name:1, founded_day:1})
 -**`limit`**:              .limit(10)
 -**`sort`**:   .sort({'acquisition.price_amount':-1})
### 17. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascendant order.
-**`query`**:                db.companies.find({$and:[{category_code:"web"},{number_of_employees:{$gt:4000}}]},
 -**`proyection`**:           {_id:0,name:1, number_of_employees:1})
 -**`limit`**:              
 -**`sort`**:                .sort({number_of_employees:1})
### 18. All the companies which their acquisition amount is more than 10.000.000, and currency are 'EUR'. raised_currency_code
-**`query`**:  db.companies.find({$and:[{'acquisition.price_amount':{$gt:10000000}},{'funding_rounds.raised_currency_code':{$eq:'EUR'}}]},

 -**`proyection`**:        {_id:0, name:1,'funding_rounds.raised_currency_code':1})   
 -**`limit`**:              
 -**`sort`**: 
### 19. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.
-**`query`**:                db.companies.find({'acquisition.acquired_month':{$lte:3}},
 -**`proyection`**:           {_id:0, name:1,'acquisition.acquired_month':1})
 -**`limit`**:              
 -**`sort`**:                  .limit(10)
### 20. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.
         db.companies.find({$and:[{founded_year:{$gt:1999}},{founded_year:{$lt:2011}},{'acquisition.acquired_year':{$lt:2011}}]},
         {_id:0, name:1, founded_year:1, 'acquisition.acquired_year':1})