
1.List all columns of salespeople table.
select * from salespeople;

2.list all customers with a rating of 100.
select * from customer where rating=100;

3.find all records in the customer table with null values in city column.
select * from customer where city='null';

4. Find the largest order taken by each salesperson on each date.
select a.onum,max(a.amt),a.odate,a.cnum,b.snum from orders a,customer c where a.cnum=c.cnum group by c,snum,a.odate;

5. Arrange the Orders table by descending customer number.
select * from orders order by cnum desc;

6. Find which salespeople currently have orders in the Orders table.
select a.onum,a.amt,a.odate,a.cnum,b.snum,b.sname from orders a,customer b where a.cnum=b.cnum group by b.snum,a.odate;

7. List names of all customers matched with the salespeople serving them.
select a.sname,a.city,b.cname from salespeople a,customer b where a.snum=b.snum;

8. Find the names and numbers of all salespeople who had more than one customer.
select a.snum,b.sname,count(*) as customer_count from customer a, salespeople b where a.snum=b.snum group by a.snum;

9. Count the orders of each of the salespeople and output the results in descending order.
select b.snum,c.sname,count(*) as order_count from orders a,customer b,salespeople c where a.cnum=b.snum and b.snum=c.snum group by snum;

10. Match salespeople to customers according to what city they lived in.
select a.sname,b.cname,b.city from salespeople a, customer b where a.snum=b.snum and a.city=b.city;

11. Find the largest order taken by each salesperson.
select a.sname,a.snum,b.onum,b.amt from salespeople a,orders b,customer c where a.snum=c.snum and c.cnum=b.cnum group by sname;

12. Find customers in San Jose who have a rating above 200.
select * from customer where rating>=200 and city='san jose';

13. List the names and commissions of all salespeople in London.
select distinct sname,comm,city from salespeople where city='london';

14. List all the orders of salesperson Motika from the Orders table.
select a.sname,b.onum,b.amt from salespeople a,orders b,customer c where a.snum=c.snum and c.cnum=b.cnum and sname='motika';
