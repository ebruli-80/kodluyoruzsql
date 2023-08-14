ödev 1:
1:film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız

SELECT title,description FROM film;

2:film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 
60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

SELECT * FROM film WHERE length>60 AND length<75;

3:film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE 
replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.


SELECT * FROM film WHERE rental_rate=0.99 AND (replacement_cost=12.99 OR replacement_cost=28.99);


4:customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan
 müşterinin last_name sütunundaki değeri nedir?


SELECT first_name, last_name FROM customer WHERE first_name='Mary';


5:film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda
 rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

SELECT length,rental_rate FROM film WHERE length<50 AND NOT(rental_rate=2.99 OR rental_rate=4.99);

ödev 2:
1:film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük 
olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

SELECT* FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.98;


2:.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' 
değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT first_name,last_name FROM actor WHERE first_name IN('Penelope','Nick','Ed');


3:film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 
olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

SELECT * FROM film WHERE rental_rate IN(0.99,2.99,4.99) AND replacement_cost IN(12.99,15.99,28.99);

ödev 3:
1:country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

SELECT country FROM country WHERE country LIKE 'A%a';

2:country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

SELECT country FROM country WHERE country LIKE'%_____n';


3:film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız

SELECT title FROM film WHERE title ~~* '%T%T%T%T%';	-- // ~~isareti LIKE ~~* ise ILIKE anlamına gelir.


4:film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

SELECT * FROM film WHERE title LIKE 'C%' AND length>90 AND rental_rate=2.99;



ödev 4:
1:film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

SELECT DISTINCT replacement_cost FROM film;



2:film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

SELECT COUNT (DISTINCT replacement_cost) FROM film;



3:film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating='G';



4:country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

SELECT COUNT(*) FROM country WHERE country LIKE '_____';



5:city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

SELECT COUNT(*) FROM city WHERE city ILIKE '%r'; -- buyuk R ile bitmeyeceğini düşünerek '%r' kullandım.


ödev 5:
1:film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

SELECT title,length FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5;


2:film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

SELECT title,length FROM film WHERE title LIKE '%n' ORDER BY length ASC  OFFSET 5 LIMIT 5;



3:customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

SELECT last_name,store_id FROM customer WHERE store_id=1 ORDER BY last_name DESC  LIMIT 4;


ödev 6:
1:film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

SELECT AVG(rental_rate) FROM film ;


2:film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

SELECT COUNT(*) FROM film WHERE title LIKE 'C%' ;


3:film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

SELECT rental_rate,length FROM film WHERE rental_rate=0.99  ORDER BY length DESC ;
SELECT MAX(length) FROM film WHERE rental_rate=0.99 ;// hocanın çözümü


4:film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

SELECT COUNT(DISTINCT replacement_cost) FROM film  WHERE length>150;


ödev 7:
1:film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
SELECT rating FROM film GROUP BY rating;



2:film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
SELECT replacement_cost,COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*)>50;



3:customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

SELECT store_id,COUNT(DISTINCT store_id) FROM customer GROUP BY store_id;



4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

SELECT country_id,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;


ödev 8:
1:test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), 
birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

CREATE TABLE employee (
id SERIAL, 
name VARCHAR(50)NOT NULL, 
birthday DATE, 
email VARCHAR(100)
);


2:Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

insert into employee (name, email, birthday) values ('Bernhard', 'bwilmot0@twitpic.com', '2022-12-01');
insert into employee (name, email, birthday) values ('Carmine', 'croaf1@ucsd.edu', '2023-08-09');
insert into employee (name, email, birthday) values ('Adiana', 'amcguffie2@youtube.com', '2022-11-05');
insert into employee (name, email, birthday) values ('Sal', 'swyldes3@vk.com', '2023-06-30');
insert into employee (name, email, birthday) values ('Marv', 'mbentley4@state.tx.us', '2023-06-17');
insert into employee (name, email, birthday) values ('Lief', 'lcogdon5@google.es', '2022-08-30');
insert into employee (name, email, birthday) values ('Web', 'wbalham6@jiathis.com', '2022-11-06');
insert into employee (name, email, birthday) values ('Noland', 'ncorkett7@hexun.com', '2022-10-26');
insert into employee (name, email, birthday) values ('Clark', 'clongworthy8@time.com', '2023-07-26');
insert into employee (name, email, birthday) values ('Tiff', 'tlages9@studiopress.com', '2023-01-06');
insert into employee (name, email, birthday) values ('Bridget', 'bpellitta@amazon.de', '2023-05-19');
insert into employee (name, email, birthday) values ('Cristobal', 'cflearb@amazon.co.uk', '2023-05-31');
insert into employee (name, email, birthday) values ('Cynthia', 'cristc@theatlantic.com', '2023-03-03');
insert into employee (name, email, birthday) values ('Goober', 'gpatised@walmart.com', '2023-01-30');
insert into employee (name, email, birthday) values ('Natalya', 'nmcwhinniee@bizjournals.com', '2023-06-22');
insert into employee (name, email, birthday) values ('Xena', 'xcomettif@macromedia.com', '2023-06-02');
insert into employee (name, email, birthday) values ('Alastair', 'amackimg@alibaba.com', '2023-02-02');
insert into employee (name, email, birthday) values ('Benni', 'blardeuxh@bravesites.com', '2023-03-03');
insert into employee (name, email, birthday) values ('Nickolaus', 'nwalshi@examiner.com', '2022-10-11');
insert into employee (name, email, birthday) values ('Marshal', 'mduggonj@irs.gov', '2023-07-17');
insert into employee (name, email, birthday) values ('Benedicta', 'bsuscensk@shop-pro.jp', '2022-12-06');
insert into employee (name, email, birthday) values ('Jewell', 'jgetcliffel@jigsy.com', '2023-01-21');
insert into employee (name, email, birthday) values ('Kori', 'kmattusovm@rediff.com', '2023-02-04');
insert into employee (name, email, birthday) values ('Merell', 'msallnown@over-blog.com', '2023-01-18');
insert into employee (name, email, birthday) values ('Pepita', 'pmcinultyo@moonfruit.com', '2023-07-31');
insert into employee (name, email, birthday) values ('Anissa', 'awandsp@unblog.fr', '2022-10-29');
insert into employee (name, email, birthday) values ('Leeland', 'lbemlottq@opera.com', '2022-10-19');
insert into employee (name, email, birthday) values ('Dannel', 'denrricor@goodreads.com', '2022-08-29');
insert into employee (name, email, birthday) values ('Nadia', 'nrenekes@vimeo.com', '2022-09-15');
insert into employee (name, email, birthday) values ('Conan', 'cmckeaveneyt@google.ca', '2023-07-08');
insert into employee (name, email, birthday) values ('Pepita', 'psandcroftu@bluehost.com', '2022-09-20');
insert into employee (name, email, birthday) values ('Shaun', 'sbarochev@lulu.com', '2022-11-15');
insert into employee (name, email, birthday) values ('Svend', 'sluetkemeyerw@rambler.ru', '2023-04-05');
insert into employee (name, email, birthday) values ('Niel', 'nwarlowex@chicagotribune.com', '2023-01-02');
insert into employee (name, email, birthday) values ('Elane', 'ebendelly@google.de', '2022-09-03');
insert into employee (name, email, birthday) values ('Timmie', 'tbellshamz@mediafire.com', '2022-09-10');
insert into employee (name, email, birthday) values ('Brandice', 'binnett10@chicagotribune.com', '2023-06-16');
insert into employee (name, email, birthday) values ('Alistair', 'athon11@sina.com.cn', '2023-07-17');
insert into employee (name, email, birthday) values ('Normie', 'nworden12@parallels.com', '2022-11-12');
insert into employee (name, email, birthday) values ('Kristopher', 'kbree13@fda.gov', '2023-07-22');
insert into employee (name, email, birthday) values ('Brion', 'bbullocke14@goo.ne.jp', '2023-05-25');
insert into employee (name, email, birthday) values ('Dietrich', 'dconrard15@merriam-webster.com', '2023-07-13');
insert into employee (name, email, birthday) values ('Jeana', 'jkenealy16@goo.gl', '2022-11-10');
insert into employee (name, email, birthday) values ('Laurence', 'llightollers17@nasa.gov', '2022-09-28');
insert into employee (name, email, birthday) values ('Vivien', 'vpatient18@washington.edu', '2023-02-20');
insert into employee (name, email, birthday) values ('Wilona', 'woldale19@patch.com', '2022-08-17');
insert into employee (name, email, birthday) values ('Maisie', 'mlomaz1a@geocities.com', '2023-03-31');
insert into employee (name, email, birthday) values ('Wylie', 'woxborough1b@wikia.com', '2022-11-09');
insert into employee (name, email, birthday) values ('Robers', 'rblakeslee1c@tmall.com', '2022-12-21');
insert into employee (name, email, birthday) values ('Hertha', 'hscotson1d@huffingtonpost.com', '2023-06-01');



3:Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
UPDATE employee
SET name='ahmet'
WHERE id=5;

UPDATE employee
SET name='hacı',
birthday='1992/05/01'
WHERE id=29;

UPDATE employee
SET birthday='1990/03/28'
WHERE email='swyldes3@vk.com';


UPDATE employee
SET name='uğur',
email='123456@gmail.com',
birthday='1990/03/28'
WHERE id=7 OR birthday='1990/03/28';

UPDATE employee
SET name='***',
email='****',
birthday='2005/09/06';




4:Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
DELETE FROM employee
WHERE id BETWEEN 2 AND 8;

DELETE FROM employee
WHERE id=5;

DELETE FROM employee
WHERE id>12;


DELETE FROM employee
WHERE id>2 AND name='***';

DELETE FROM employee;




ödev 9:
1:city tablosu ile country tablosunda bulunan şehir (city) ve 
ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

SELECT city,country FROM city JOIN country ON city.city_id = country.country_id;


2:customer tablosu ile payment tablosunda bulunan payment_id ile
 customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz
 INNER JOIN sorgusunu yazınız.

SELECT payment_id,first_name,last_name FROM payment
INNER JOIN customer ON payment.customer_id=customer.customer_id;


3:customer tablosu ile rental tablosunda bulunan rental_id ile 
customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz
 INNER JOIN sorgusunu yazınız.

SELECT rental_id,first_name,last_name FROM rental
INNER JOIN customer ON rental.customer_id=customer.customer_id;


ödev 10:
1:city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini 
birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

SELECT city,country FROM city
LEFT JOIN country ON city.country_id=country.country_id;


2:customer tablosu ile payment tablosunda bulunan payment_id ile 
customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz
 RIGHT JOIN sorgusunu yazınız.

SELECT payment_id,first_name,last_name FROM customer
RIGHT JOIN payment ON customer.customer_id=payment.customer_id;


3:customer tablosu ile rental tablosunda bulunan rental_id ile 
customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz 
FULL JOIN sorgusunu yazınız.

SELECT rental_id,first_name,last_name FROM customer
FULL JOIN rental ON rental.customer_id=customer.customer_id;


ÖDEV 11:
1:actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);


2:actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);


3:actor ve customer tablolarında bulunan first_name sütunları için 
ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);



4:İlk 3 sorguyu tekrar eden veriler için de yapalım.

(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);

(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);

(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);



ödev 12:
1:film tablosunda film uzunluğu length sütununda gösterilmektedir. 
Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

SELECT COUNT(*) FROM film WHERE length>
(SELECT AVG(length) FROM film );


2:film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

SELECT COUNT(*) FROM film WHERE rental_rate=
(SELECT MAX(rental_rate) FROM film );


3:film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine 
sahip filmleri sıralayınız.

SELECT * FROM film WHERE rental_rate=(
SELECT MIN(rental_rate)FROM film
)
AND replacement_cost=(
SELECT MIN(replacement_cost) FROM film
);



4:payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

SELECT customer_id, COUNT(*) AS transaction_count
FROM payment
GROUP BY customer_id
ORDER BY transaction_count DESC;
