1. How many users are there?

    There are 50 users.


2. What are the 5 most expensive items?

    25|Small Cotton Gloves|Automotive, Shoes & Beauty|Multi-layered modular service-desk|9984
    83|Small Wooden Computer|Health|Re-engineered fault-tolerant adapter|9859
    100|Awesome Granite Pants|Toys & Books|Upgradable 24/7 access|9790
    40|Sleek Wooden Hat|Music & Baby|Quality-focused heuristic info-mediaries|9390
    60|Ergonomic Steel Car|Books & Outdoors|Enterprise-wide secondary firmware|9341



3. What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)

    76|Ergonomic Granite Chair|Books|De-engineered bi-directional portal|1496
    (select * from items where category like '%book%' order by items.price asc limit 1)

    (select * from items where category = 'Books' order by price asc limit 1;)
    --no difference in answer--



4. Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
    
    user_id: 40
    (select user_id from addresses where street like '%6439 Zetta Hills%';)  
    yes;
    43|40|6439 Zetta Hills|Willmouth|WY|15029
    44|40|54369 Wolff Forges|Lake Bryon|CA|31587
    (select * from addresses where user_id like '%40%';)
    (select user_id from addresses where user_id like '%40%';)



5. Correct Virginie Mitchell's address to "New York, NY, 10108".

    39|Virginie|Mitchell|daisy.crist@altenwerthmonahan.biz
    (select * from users where first_name like '%virginie%';)
    (select * from addresses where id='39';)
    update addresses set city = 'New York', state = 'NY', zip = '10108' where id = 41;
    


6. How much would it cost to buy one of each tool?

    46477
    (select sum (price) from items where category like '%tools%';)


7. How many total items did we sell?

    select sum (quantity) from orders;
    sum (quantity)
    2125

8. How much was spent on books?

    select sum (price) from items where category like '%books%';
    sum (price)
    59241


9. Simulate buying an item by inserting a User for yourself and an Order for that User.

insert into users (first_name, last_name, email) values ('Aubrey', 'Badger', 'akbadger@gmail.com');

insert into addresses (user_id, street, city, state, zip) values ('51', '1234 street street way', 'newline path', 'ironyard', '12345');

insert into orders (user_id, item_id, quantity, created_at) values ('51', '43', '254', '2017-03-06 00:43:21.876667');

