 -------------------------

SELECT product_name, manufacturer, price

FROM myfrstdb.mobile_phones

WHERE product_count > 2

;

  -------------------------

SELECT *

FROM myfrstdb.mobile_phones

WHERE manufacturer = "Samsung"

;

  -------------------------

SELECT *

FROM myfrstdb.mobile_phones

WHERE product_name LIKE "%Iphone%"

;

  -------------------------

SELECT *

FROM myfrstdb.mobile_phones

WHERE manufacturer LIKE "%Samsung%"

;

  -------------------------

SELECT *

FROM myfrstdb.mobile_phones

WHERE product_name REGEXP "[0-9]"

;
 
 -------------------------

SELECT *

FROM myfrstdb.mobile_phones

WHERE product_name REGEXP "[8]"

;