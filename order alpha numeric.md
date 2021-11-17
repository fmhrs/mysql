### CREATE FUNCTION  PATINDEX 
-- https://stackoverflow.com/questions/38315658/patindex-replacement-in-mysql
-- NOTE : dont run create function and order code at same time
```
DROP FUNCTION IF EXISTS PatIndex;

DELIMITER $$

CREATE FUNCTION PatIndex(pattern VARCHAR(255), tblString VARCHAR(255)) RETURNS INTEGER
    DETERMINISTIC
BEGIN

    DECLARE i INTEGER;
    SET i = 1;

    myloop: WHILE (i <= LENGTH(tblString)) DO

        IF SUBSTRING(tblString, i, 1) REGEXP pattern THEN
            RETURN(i);
            LEAVE myloop;        
        END IF;    

        SET i = i + 1;

    END WHILE; 

    RETURN(0);
END
```

### CREATE TABLE
```
CREATE TABLE IF NOT EXISTS `t1` (
  `data` text DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO `t1` (`data`) VALUES
	('100'),
	('6'),
	('1'),
	('2'),
	('abc'),
	('abc 123'),
	('abc 1'),
	('abc 11'),
	('df3'),
	('df42'),
	('c5'),
	('df3ab'),
	('df3ac'),
	('df3aa23');
```

### CODE FOR ORDER
```
SELECT 
	DATA, 
	PATINDEX('[0-9]', DATA)-1, LENGTH(DATA),
	SUBSTR(DATA, PATINDEX('[0-9]', DATA), LENGTH(DATA)),
	SUBSTR(DATA, PATINDEX('[0-9]', DATA), LENGTH(DATA))*1
FROM test.t1
ORDER BY LEFT(data, PATINDEX('[0-9]', data)-1), -- alphabetical sort
SUBSTR(DATA, PATINDEX('[0-9]', DATA), LENGTH(DATA))*1 -- numerical
```
