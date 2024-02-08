## Examples of minimized queries.

Below are some minimal examples, which are derived from PINOLO [Pinolo@ATC23].

### An example of MariaDB.

The provided JSON and SQL data illustrate the application of three different SQL simplification methods: SQLess, ClauseDelete, and APOLLO, each applied to a complex SQL query within the context of a MariaDB database.

bug-9-4478-FixMDistinctL.json

```json
{
  "originalSql" : "WITH `MYWITH` AS ((SELECT (DATE_SUB(`f4`, INTERVAL 1 MONTH)) AS `f1`,(DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(`f4`|0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE (NOT ((LAST_DAY(_UTF8MB4'2000-09-05 03:27:14')) NOT BETWEEN `f10` AND _UTF8MB4'2016-03-14')) OR ((DATE_SUB(`f11`, INTERVAL 1 MICROSECOND)) IN (COT(6),SECOND(_UTF8MB4'03:40:24'),`f12`))) AS `t3` ON ((NOT (CAST((NULL) AS CHAR) LIKE _UTF8MB4'%0%')) OR ((COLLATION(`f6`)) IN (1,`f5`,COERCIBILITY(`f4`))) OR (NOT (ROW(COT(0.12073627913396147),LOG2(0.9688927019445049)^`f4`) IN (SELECT `col_double_key_signed`,`col_double_key_signed` FROM `table_7_utf8_undef`)))) IS TRUE) UNION ALL (SELECT (-`f14`) AS `f1`,(BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE HAVING (((ROW(DEGREES(0.8825865858138652),`f3`*!TO_BASE64(`f3`)*BINARY DAYOFYEAR(_UTF8MB4'2002-02-08')) NOT IN (SELECT `col_varchar(20)_key_signed`,`col_bigint_undef_signed` FROM `table_3_utf8_undef`)) IS TRUE) OR ((DATE_ADD(-0, INTERVAL 1 SECOND_MICROSECOND)) IS TRUE) OR ((EXISTS (SELECT `col_float_undef_unsigned` FROM `table_3_utf8_undef` FORCE INDEX (`col_decimal(40, 20)_key_signed`))) IS FALSE)) IS TRUE ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
  "mutatedSql" : "WITH `MYWITH` AS ((SELECT (DATE_SUB(`f4`, INTERVAL 1 MONTH)) AS `f1`,(DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(`f4`|0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT DISTINCT (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE (NOT ((LAST_DAY(_UTF8MB4'2000-09-05 03:27:14')) NOT BETWEEN `f10` AND _UTF8MB4'2016-03-14')) OR ((DATE_SUB(`f11`, INTERVAL 1 MICROSECOND)) IN (COT(6),SECOND(_UTF8MB4'03:40:24'),`f12`))) AS `t3` ON ((NOT (CAST((NULL) AS CHAR) LIKE _UTF8MB4'%0%')) OR ((COLLATION(`f6`)) IN (1,`f5`,COERCIBILITY(`f4`))) OR (NOT (ROW(COT(0.12073627913396147),LOG2(0.9688927019445049)^`f4`) IN (SELECT `col_double_key_signed`,`col_double_key_signed` FROM `table_7_utf8_undef`)))) IS TRUE) UNION ALL (SELECT (-`f14`) AS `f1`,(BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE HAVING (((ROW(DEGREES(0.8825865858138652),`f3`*!TO_BASE64(`f3`)*BINARY DAYOFYEAR(_UTF8MB4'2002-02-08')) NOT IN (SELECT `col_varchar(20)_key_signed`,`col_bigint_undef_signed` FROM `table_3_utf8_undef`)) IS TRUE) OR ((DATE_ADD(-0, INTERVAL 1 SECOND_MICROSECOND)) IS TRUE) OR ((EXISTS (SELECT `col_float_undef_unsigned` FROM `table_3_utf8_undef` FORCE INDEX (`col_decimal(40, 20)_key_signed`))) IS FALSE)) IS TRUE ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
  "upper" : false,
  "mutationName" : "pinonlo",
  "isUpper" : false,
  "dbms" : "mariadb",
  "host" : "127.0.0.1",
  "port" : 9101,
  "username" : "root",
  "password" : "123456",
  "dbname" : "TEST3"
}
```

**SQLess Simplification Result:**

```json
{
"slimoriginalSql" : " (SELECT (BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` ) AS `t4` )",
  "slimmutatedSql" : " (SELECT DISTINCT  (BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` ) AS `t4` )",
}
```

**ClauseDelete Simplification Result:**

```sql
{
  "slimoriginalSql" : "WITH `MYWITH` AS ((SELECT (DATE_SUB(`f4`, INTERVAL 1 MONTH)) AS `f1`,(DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE (NOT ((LAST_DAY(_UTF8MB4'2000-09-05 03:27:14')) NOT BETWEEN `f10` AND _UTF8MB4'2016-03-14')) ) AS `t3` ON ( (NOT (ROW(COT(0.12073627913396147),LOG2(0.9688927019445049)) IN (SELECT `col_double_key_signed`,`col_double_key_signed` FROM `table_7_utf8_undef`)))) IS TRUE) UNION ALL (SELECT (-`f14`) AS `f1`,(BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE  ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
  "slimmutatedSql" : "WITH `MYWITH` AS ((SELECT (DATE_SUB(`f4`, INTERVAL 1 MONTH)) AS `f1`,(DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT DISTINCT  (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE (NOT ((LAST_DAY(_UTF8MB4'2000-09-05 03:27:14')) NOT BETWEEN `f10` AND _UTF8MB4'2016-03-14')) ) AS `t3` ON ( (NOT (ROW(COT(0.12073627913396147),LOG2(0.9688927019445049)) IN (SELECT `col_double_key_signed`,`col_double_key_signed` FROM `table_7_utf8_undef`)))) IS TRUE) UNION ALL (SELECT (-`f14`) AS `f1`,(BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE  ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
}
```

**APOLLO Simplification Result:**

```json
{
  "slimoriginalSql" : "WITH `MYWITH` AS ((SELECT (DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE  ((DATE_SUB(`f11`, INTERVAL 1 MICROSECOND)) IN (COT(6),SECOND(_UTF8MB4'03:40:24'),`f12`))) AS `t3` ON ((NOT (CAST((NULL) AS CHAR) LIKE _UTF8MB4'%0%')) OR ((COLLATION(`f6`)) IN (1,`f5`,COERCIBILITY(`f4`))) ) IS TRUE) ) SELECT * FROM `MYWITH`  WITH `MYWITH` AS (UNION ALL) SELECT * FROM `MYWITH`  WITH `MYWITH` AS ( (SELECT (BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE  ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
  "slimmutatedSql" : "WITH `MYWITH` AS ((SELECT DISTINCT  (DATE_ADD(REPEAT(`f5`, 2), INTERVAL 1 DAY_MINUTE)) AS `f2`,(0.13687240936980968) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_double_undef_unsigned` AS `f7`,`col_float_key_signed` AS `f6` FROM `table_3_utf8_undef` IGNORE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` STRAIGHT_JOIN (SELECT (NULL) AS `f8`,(CRC32(0)) AS `f5`,(!_UTF8MB4'come') AS `f9` FROM (SELECT `col_bigint_undef_unsigned` AS `f10`,`col_decimal(40, 20)_undef_signed` AS `f11`,`col_decimal(40, 20)_undef_unsigned` AS `f12` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t2` WHERE  ((DATE_SUB(`f11`, INTERVAL 1 MICROSECOND)) IN (COT(6),SECOND(_UTF8MB4'03:40:24'),`f12`))) AS `t3` ON ((NOT (CAST((NULL) AS CHAR) LIKE _UTF8MB4'%0%')) OR ((COLLATION(`f6`)) IN (1,`f5`,COERCIBILITY(`f4`))) ) IS TRUE) ) SELECT * FROM `MYWITH`  WITH `MYWITH` AS (UNION ALL) SELECT * FROM `MYWITH`  WITH `MYWITH` AS ( (SELECT (BINARY 0.7339937007342865) AS `f2`,(DATE_ADD(PI(), INTERVAL 1 SECOND_MICROSECOND)) AS `f3` FROM (SELECT `col_double_undef_signed` AS `f13`,`col_float_undef_unsigned` AS `f14`,`col_bigint_key_signed` AS `f15` FROM `table_3_utf8_undef` IGNORE INDEX (`col_float_key_signed`, `col_decimal(40, 20)_key_signed`)) AS `t4` WHERE ((((6557202696029309858) IN (STRCMP(`f15`, `f14`),CHARSET(`f13`),`f13`)) IS TRUE) OR ((`f14`) BETWEEN `f13` AND `f13`)) IS FALSE  ORDER BY `f14`)) SELECT * FROM `MYWITH`;",
}
```



### An example of TiDB

The provided JSON and SQL data illustrate the application of three different SQL simplification methods: SQLess, ClauseDelete, and APOLLO, each applied to a complex SQL query within the context of a TiDB database.

bug-6-9790-FixMDistinctL.json

```json
{
  "originalSql" : "(SELECT (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_double_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` WHERE (((ROW(DATE_ADD(COERCIBILITY(`f5`), INTERVAL 1 DAY_SECOND),`f4`) IN (SELECT `col_varchar(20)_undef_signed`,`col_float_undef_signed` FROM `table_7_utf8_undef` FORCE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_char(20)_key_signed`))) IS FALSE) OR ((CAST((`f5`) AS CHAR) NOT REGEXP _UTF8MB4'[0-9]$') IS FALSE) OR (NOT ((UNHEX(_UTF8MB4'say')) NOT BETWEEN SEC_TO_TIME(276662835345812726) AND `f6`))) IS TRUE HAVING (((((DATE_SUB(1, INTERVAL 1 YEAR_MONTH)) NOT IN (SELECT `col_varchar(20)_undef_signed` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_signed`))) IS FALSE) AND ((BINARY `f1`)<(SEC_TO_TIME(3813732708844824813)))) OR ((((~_UTF8MB4'2012-12-16 13:24:44'>>SIGN(8047051730969025058)|CEILING(0.3943825645801509)) IN (SELECT `col_double_key_unsigned` FROM `table_7_utf8_undef` IGNORE INDEX (`col_double_key_signed`, `col_float_key_unsigned`))) IS TRUE) AND ((-ATAN(3155500163993719237))!=(DATE_ADD(CRC32(NULL), INTERVAL 1 DAY_MICROSECOND))))) IS FALSE ORDER BY `f4`) UNION ALL (SELECT (~`f9`) AS `f1`,(DATE_SUB(~`f7`, INTERVAL 1 WEEK)) AS `f2`,(`f9`) AS `f3` FROM (SELECT `col_float_undef_signed` AS `f7`,`col_double_key_signed` AS `f10`,`col_float_undef_signed` AS `f9` FROM `table_3_utf8_undef` FORCE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t2` JOIN (SELECT `col_decimal(40, 20)_undef_unsigned` AS `f11`,`col_bigint_key_signed` AS `f8`,`col_double_undef_signed` AS `f12` FROM `table_7_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t3`);",
  "mutatedSql" : "(SELECT (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_double_key_signed`, `col_varchar(20)_key_signed`)) AS `t1` WHERE (((ROW(DATE_ADD(COERCIBILITY(`f5`), INTERVAL 1 DAY_SECOND),`f4`) IN (SELECT `col_varchar(20)_undef_signed`,`col_float_undef_signed` FROM `table_7_utf8_undef` FORCE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_char(20)_key_signed`))) IS FALSE) OR ((CAST((`f5`) AS CHAR) NOT REGEXP _UTF8MB4'[0-9]$') IS FALSE) OR (NOT ((UNHEX(_UTF8MB4'say')) NOT BETWEEN SEC_TO_TIME(276662835345812726) AND `f6`))) IS TRUE HAVING (((((DATE_SUB(1, INTERVAL 1 YEAR_MONTH)) NOT IN (SELECT `col_varchar(20)_undef_signed` FROM `table_3_utf8_undef` FORCE INDEX (`col_float_key_signed`))) IS FALSE) AND ((BINARY `f1`)<(SEC_TO_TIME(3813732708844824813)))) OR ((((~_UTF8MB4'2012-12-16 13:24:44'>>SIGN(8047051730969025058)|CEILING(0.3943825645801509)) IN (SELECT `col_double_key_unsigned` FROM `table_7_utf8_undef` IGNORE INDEX (`col_double_key_signed`, `col_float_key_unsigned`))) IS TRUE) AND ((-ATAN(3155500163993719237))!=(DATE_ADD(CRC32(NULL), INTERVAL 1 DAY_MICROSECOND))))) IS FALSE ORDER BY `f4`) UNION ALL (SELECT DISTINCT (~`f9`) AS `f1`,(DATE_SUB(~`f7`, INTERVAL 1 WEEK)) AS `f2`,(`f9`) AS `f3` FROM (SELECT `col_float_undef_signed` AS `f7`,`col_double_key_signed` AS `f10`,`col_float_undef_signed` AS `f9` FROM `table_3_utf8_undef` FORCE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t2` JOIN (SELECT `col_decimal(40, 20)_undef_unsigned` AS `f11`,`col_bigint_key_signed` AS `f8`,`col_double_undef_signed` AS `f12` FROM `table_7_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t3`);",
  "upper" : false,
  "mutationName" : "pinonlo",
  "isUpper" : false,
  "dbms" : "mysql",
  "host" : "127.0.0.1",
  "port" : 4000,
  "username" : "root",
  "password" : "123456",
  "dbname" : "TEST3"
}
```

**SQLess Simplification Result:**

```json
{
  "slimoriginalSql" : "(SELECT (-CHARSET(`f6`)) AS `f1` FROM (SELECT `col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` ) AS `t1`  ) ;",
  "slimmutatedSql" : "(SELECT DISTINCT  (-CHARSET(`f6`)) AS `f1` FROM (SELECT `col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` ) AS `t1` ) ;"
}
```

**ClauseDelete Simplification Result:**

```json
{
  "slimoriginalSql" : "(SELECT (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_double_key_signed`, `col_varchar(20)_key_signed`)) AS `t1`   ORDER BY `f4`) UNION ALL (SELECT (~`f9`) AS `f1`,(DATE_SUB(~`f7`, INTERVAL 1 WEEK)) AS `f2`,(`f9`) AS `f3` FROM (SELECT `col_float_undef_signed` AS `f7`,`col_double_key_signed` AS `f10`,`col_float_undef_signed` AS `f9` FROM `table_3_utf8_undef` FORCE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t2` JOIN (SELECT `col_decimal(40, 20)_undef_unsigned` AS `f11`,`col_bigint_key_signed` AS `f8`,`col_double_undef_signed` AS `f12` FROM `table_7_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t3`);",
  "slimmutatedSql" : "(SELECT (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT DISTINCT  `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_double_key_signed`, `col_varchar(20)_key_signed`)) AS `t1`   ORDER BY `f4`) UNION ALL (SELECT (~`f9`) AS `f1`,(DATE_SUB(~`f7`, INTERVAL 1 WEEK)) AS `f2`,(`f9`) AS `f3` FROM (SELECT `col_float_undef_signed` AS `f7`,`col_double_key_signed` AS `f10`,`col_float_undef_signed` AS `f9` FROM `table_3_utf8_undef` FORCE INDEX (`col_bigint_key_signed`, `col_varchar(20)_key_signed`)) AS `t2` JOIN (SELECT `col_decimal(40, 20)_undef_unsigned` AS `f11`,`col_bigint_key_signed` AS `f8`,`col_double_undef_signed` AS `f12` FROM `table_7_utf8_undef` FORCE INDEX (`col_float_key_unsigned`)) AS `t3`);",
}
```

**APOLLO Simplification Result:**

```json
{
  "slimoriginalSql" : "(SELECT (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` ) AS `t1`   ) ;",
  "slimmutatedSql" : "(SELECT DISTINCT  (-CHARSET(`f6`)) AS `f1`,(RADIANS(5)-_UTF8MB4'2019-12-15'*`f5`) AS `f2`,(`f5`) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f4`,`col_float_undef_signed` AS `f5`,`col_double_undef_unsigned` AS `f6` FROM `table_3_utf8_undef` ) AS `t1`   ) ;",
}
```



### An example of MySQL

The provided JSON and SQL data illustrate the application of three different SQL simplification methods: SQLess, ClauseDelete, and APOLLO, each applied to a complex SQL query within the context of a MySQL database.

bug-6-3322-FixMDistinctL.json

```json
{
  "originalSql" : "(SELECT (-`f6`) AS `f1`,(TIME(_UTF8MB4'2019-01-07 08:19:24')) AS `f2`,(-ASIN(3368880944666530484)) AS `f3` FROM (SELECT (DATE_SUB(-LCASE(`f9`), INTERVAL 1 WEEK)) AS `f7`,(LTRIM(`f9`) DIV DAYOFWEEK(_UTF8MB4'2003-05-15')) AS `f5`,(FLOOR(-7313058613689118582)) AS `f8` FROM (SELECT `col_decimal(40, 20)_key_signed` AS `f9`,`col_float_key_signed` AS `f10`,`col_bigint_undef_signed` AS `f11` FROM `table_7_utf8_undef` IGNORE INDEX (`col_float_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t1` HAVING (((ROW(!CEIL(-8151597123472337127),!PI()) NOT IN (SELECT `col_float_undef_unsigned`,`col_bigint_key_signed` FROM `table_3_utf8_undef`)) IS FALSE) OR ((`f7`)>(DATE_ADD(`f8`, INTERVAL 1 DAY_SECOND))) AND (NOT (CAST((COERCIBILITY(1)) AS CHAR) NOT LIKE _UTF8MB4'%1%'))) IS FALSE ORDER BY `f11`) AS `t2` NATURAL JOIN (SELECT (LOG(0.8199245524745861)) AS `f4`,(HEX(`f15`)+`f14`>>NULL) AS `f12`,(DATE_SUB(`f13`, INTERVAL 1 MINUTE)) AS `f6` FROM (SELECT `col_bigint_key_signed` AS `f13`,`col_varchar(20)_undef_signed` AS `f14`,`col_double_undef_signed` AS `f15` FROM `table_7_utf8_undef`) AS `t3`) AS `t4`) UNION (SELECT (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` USE INDEX (`col_bigint_key_signed`)) AS `t5` WHERE (((SECOND(_UTF8MB4'16:59:09')) BETWEEN MINUTE(_UTF8MB4'2008-08-13 11:35:02') AND `f17`) AND (NOT ((COS(2698171320814186128)) NOT BETWEEN `f18` AND TIMEDIFF(_UTF8MB4'2003-11-05 07:24:57', _UTF8MB4'2002-12-09 10:27:38'))) OR (((-`f17` DIV `f17`)<ANY (SELECT `col_double_key_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_unsigned`))) IS FALSE)) IS TRUE HAVING ((NOT ((COERCIBILITY(NULL)) NOT BETWEEN _UTF8MB4'2013' AND `f1`)) AND (~SUBDATE(_UTF8MB4'2014-02-23', INTERVAL 1 HOUR_MINUTE) DIV TAN(-1445119771689639577)) AND (ROW(`f1`,~`f2`^QUOTE(`f1`)) IN (SELECT `col_decimal(40, 20)_undef_signed`,`col_double_undef_unsigned` FROM `table_3_utf8_undef` IGNORE INDEX (`col_double_key_unsigned`)))) IS FALSE ORDER BY `f18`);",
  "mutatedSql" : "(SELECT (-`f6`) AS `f1`,(TIME(_UTF8MB4'2019-01-07 08:19:24')) AS `f2`,(-ASIN(3368880944666530484)) AS `f3` FROM (SELECT (DATE_SUB(-LCASE(`f9`), INTERVAL 1 WEEK)) AS `f7`,(LTRIM(`f9`) DIV DAYOFWEEK(_UTF8MB4'2003-05-15')) AS `f5`,(FLOOR(-7313058613689118582)) AS `f8` FROM (SELECT `col_decimal(40, 20)_key_signed` AS `f9`,`col_float_key_signed` AS `f10`,`col_bigint_undef_signed` AS `f11` FROM `table_7_utf8_undef` IGNORE INDEX (`col_float_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t1` HAVING (((ROW(!CEIL(-8151597123472337127),!PI()) NOT IN (SELECT `col_float_undef_unsigned`,`col_bigint_key_signed` FROM `table_3_utf8_undef`)) IS FALSE) OR ((`f7`)>(DATE_ADD(`f8`, INTERVAL 1 DAY_SECOND))) AND (NOT (CAST((COERCIBILITY(1)) AS CHAR) NOT LIKE _UTF8MB4'%1%'))) IS FALSE ORDER BY `f11`) AS `t2` NATURAL JOIN (SELECT DISTINCT (LOG(0.8199245524745861)) AS `f4`,(HEX(`f15`)+`f14`>>NULL) AS `f12`,(DATE_SUB(`f13`, INTERVAL 1 MINUTE)) AS `f6` FROM (SELECT `col_bigint_key_signed` AS `f13`,`col_varchar(20)_undef_signed` AS `f14`,`col_double_undef_signed` AS `f15` FROM `table_7_utf8_undef`) AS `t3`) AS `t4`) UNION (SELECT (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` USE INDEX (`col_bigint_key_signed`)) AS `t5` WHERE (((SECOND(_UTF8MB4'16:59:09')) BETWEEN MINUTE(_UTF8MB4'2008-08-13 11:35:02') AND `f17`) AND (NOT ((COS(2698171320814186128)) NOT BETWEEN `f18` AND TIMEDIFF(_UTF8MB4'2003-11-05 07:24:57', _UTF8MB4'2002-12-09 10:27:38'))) OR (((-`f17` DIV `f17`)<ANY (SELECT `col_double_key_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_unsigned`))) IS FALSE)) IS TRUE HAVING ((NOT ((COERCIBILITY(NULL)) NOT BETWEEN _UTF8MB4'2013' AND `f1`)) AND (~SUBDATE(_UTF8MB4'2014-02-23', INTERVAL 1 HOUR_MINUTE) DIV TAN(-1445119771689639577)) AND (ROW(`f1`,~`f2`^QUOTE(`f1`)) IN (SELECT `col_decimal(40, 20)_undef_signed`,`col_double_undef_unsigned` FROM `table_3_utf8_undef` IGNORE INDEX (`col_double_key_unsigned`)))) IS FALSE ORDER BY `f18`);",
  "upper" : false,
  "slimoriginalSql" : " (SELECT (DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
  "slimmutatedSql" : " (SELECT DISTINCT  (DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
  "mutationName" : "pinonlo",
  "isUpper" : false,
  "dbms" : "mysql",
  "host" : "127.0.0.1",
  "port" : 13306,
  "username" : "root",
  "password" : "123456",
  "dbname" : "TEST3"
}
```

**SQLess Simplification Result:**

```json
{
  "slimoriginalSql" : " (SELECT (DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
  "slimmutatedSql" : " (SELECT DISTINCT  (DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
}
```

**ClauseDelete Simplification Result:**

```json
{
  "slimoriginalSql" : "(SELECT (-`f6`) AS `f1`,(TIME(_UTF8MB4'2019-01-07 08:19:24')) AS `f2`,(-ASIN(3368880944666530484)) AS `f3` FROM (SELECT (DATE_SUB(-LCASE(`f9`), INTERVAL 1 WEEK)) AS `f7`,(LTRIM(`f9`) DIV DAYOFWEEK(_UTF8MB4'2003-05-15')) AS `f5`,(FLOOR(-7313058613689118582)) AS `f8` FROM (SELECT `col_decimal(40, 20)_key_signed` AS `f9`,`col_float_key_signed` AS `f10`,`col_bigint_undef_signed` AS `f11` FROM `table_7_utf8_undef` IGNORE INDEX (`col_float_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t1`  ORDER BY `f11`) AS `t2` NATURAL JOIN (SELECT (LOG(0.8199245524745861)) AS `f4`,(HEX(`f15`)+NULL) AS `f12`,(DATE_SUB(`f13`, INTERVAL 1 MINUTE)) AS `f6` FROM (SELECT `col_bigint_key_signed` AS `f13`,`col_varchar(20)_undef_signed` AS `f14`,`col_double_undef_signed` AS `f15` FROM `table_7_utf8_undef`) AS `t3`) AS `t4`) UNION (SELECT (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` USE INDEX (`col_bigint_key_signed`)) AS `t5` WHERE ( (((-`f17` DIV `f17`)<ANY (SELECT `col_double_key_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_unsigned`))) IS FALSE)) IS TRUE HAVING ((NOT ((COERCIBILITY(NULL)) NOT BETWEEN _UTF8MB4'2013' AND `f1`)) AND (~SUBDATE(_UTF8MB4'2014-02-23', INTERVAL 1 HOUR_MINUTE) DIV TAN(-1445119771689639577)) ) IS FALSE ORDER BY `f18`);",
  "slimmutatedSql" : "(SELECT (-`f6`) AS `f1`,(TIME(_UTF8MB4'2019-01-07 08:19:24')) AS `f2`,(-ASIN(3368880944666530484)) AS `f3` FROM (SELECT DISTINCT  (DATE_SUB(-LCASE(`f9`), INTERVAL 1 WEEK)) AS `f7`,(LTRIM(`f9`) DIV DAYOFWEEK(_UTF8MB4'2003-05-15')) AS `f5`,(FLOOR(-7313058613689118582)) AS `f8` FROM (SELECT `col_decimal(40, 20)_key_signed` AS `f9`,`col_float_key_signed` AS `f10`,`col_bigint_undef_signed` AS `f11` FROM `table_7_utf8_undef` IGNORE INDEX (`col_float_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t1`  ORDER BY `f11`) AS `t2` NATURAL JOIN (SELECT (LOG(0.8199245524745861)) AS `f4`,(HEX(`f15`)+NULL) AS `f12`,(DATE_SUB(`f13`, INTERVAL 1 MINUTE)) AS `f6` FROM (SELECT `col_bigint_key_signed` AS `f13`,`col_varchar(20)_undef_signed` AS `f14`,`col_double_undef_signed` AS `f15` FROM `table_7_utf8_undef`) AS `t3`) AS `t4`) UNION (SELECT (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` USE INDEX (`col_bigint_key_signed`)) AS `t5` WHERE ( (((-`f17` DIV `f17`)<ANY (SELECT `col_double_key_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_unsigned`))) IS FALSE)) IS TRUE HAVING ((NOT ((COERCIBILITY(NULL)) NOT BETWEEN _UTF8MB4'2013' AND `f1`)) AND (~SUBDATE(_UTF8MB4'2014-02-23', INTERVAL 1 HOUR_MINUTE) DIV TAN(-1445119771689639577)) ) IS FALSE ORDER BY `f18`);",
}
```

**APOLLO Simplification Result:**

```json
{
  "slimoriginalSql" : " (SELECT (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
  "slimmutatedSql" : " (SELECT DISTINCT  (`f16`) AS `f1`,(DATE_SUB(`f18`, INTERVAL 1 SECOND_MICROSECOND)) AS `f2`,(!HOUR(_UTF8MB4'20:56:04')) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f16`,`col_float_key_signed` AS `f17`,`col_char(20)_undef_signed` AS `f18` FROM `table_7_utf8_undef` ) AS `t5`   ORDER BY `f18`);",
}
```





## SQL Simplification Process Overview

This document outlines the step-by-step process of simplifying a complex SQL query, showcasing the methodical reduction of elements while preserving the core functionality that triggers a specific bug. This simplification process is part of an analysis performed on a MariaDB database structure, highlighting the approach taken to isolate and identify the critical components of the SQL statement that contribute to the bug's occurrence.

### Initial SQL Statements

The simplification process begins with the original SQL query and its mutated counterpart, initially containing complex structures including WITH clauses, UNION operations, ORDER BY clauses, and various conditional expressions.

#### Original SQL

```sql
-- OriginalSql
WITH `MYWITH` AS ((SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING (((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_signed`, `col_decimal(40, 20)_key_signed`))) IS FALSE) IS FALSE ORDER BY `f5`) UNION (SELECT (BINARY COS(0)|1) AS `f1`,(!1) AS `f2`,(LOWER(`f9`)) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f7`,`col_bigint_key_unsigned` AS `f8`,`col_bigint_key_signed` AS `f9` FROM `table_3_utf8_undef` IGNORE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t2` WHERE (((DATE_ADD(_UTF8MB4'16:47:10', INTERVAL 1 MONTH)) IN (SELECT `col_decimal(40, 20)_key_unsigned` FROM `table_3_utf8_undef`)) OR ((ROW(`f8`,DATE_SUB(BINARY LOG2(8572968212617203413), INTERVAL 1 HOUR_SECOND)) IN (SELECT `col_bigint_key_unsigned`,`col_decimal(40, 20)_undef_unsigned` FROM `table_7_utf8_undef` USE INDEX (`col_double_key_unsigned`, `col_decimal(40, 20)_key_unsigned`))) IS FALSE) OR ((`f7`) BETWEEN `f7` AND `f9`)) IS TRUE ORDER BY `f7`)) SELECT * FROM `MYWITH`;
```

#### Mutated SQL

```sql
-- MutatedSql
WITH `MYWITH` AS ((SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING 1 ORDER BY `f5`) UNION (SELECT (BINARY COS(0)|1) AS `f1`,(!1) AS `f2`,(LOWER(`f9`)) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f7`,`col_bigint_key_unsigned` AS `f8`,`col_bigint_key_signed` AS `f9` FROM `table_3_utf8_undef` IGNORE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t2` WHERE (((DATE_ADD(_UTF8MB4'16:47:10', INTERVAL 1 MONTH)) IN (SELECT `col_decimal(40, 20)_key_unsigned` FROM `table_3_utf8_undef`)) OR ((ROW(`f8`,DATE_SUB(BINARY LOG2(8572968212617203413), INTERVAL 1 HOUR_SECOND)) IN (SELECT `col_bigint_key_unsigned`,`col_decimal(40, 20)_undef_unsigned` FROM `table_7_utf8_undef` USE INDEX (`col_double_key_unsigned`, `col_decimal(40, 20)_key_unsigned`))) IS FALSE) OR ((`f7`) BETWEEN `f7` AND `f9`)) IS TRUE ORDER BY `f7`)) SELECT * FROM `MYWITH`;
```

### Simplification Steps

The simplification process was meticulously carried out through several stages, each aiming to reduce the query's complexity without affecting the bug's reproducibility.

1. **Removal of the WITH Clause**: The initial step involved eliminating the WITH clause to directly work with the main SELECT statements, simplifying the query's structure without impacting its logic.

   ```sql
   -- OriginalSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING (((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_signed`, `col_decimal(40, 20)_key_signed`))) IS FALSE) IS FALSE ORDER BY `f5`) UNION (SELECT (BINARY COS(0)|1) AS `f1`,(!1) AS `f2`,(LOWER(`f9`)) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f7`,`col_bigint_key_unsigned` AS `f8`,`col_bigint_key_signed` AS `f9` FROM `table_3_utf8_undef` IGNORE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t2` WHERE (((DATE_ADD(_UTF8MB4'16:47:10', INTERVAL 1 MONTH)) IN (SELECT `col_decimal(40, 20)_key_unsigned` FROM `table_3_utf8_undef`)) OR ((ROW(`f8`,DATE_SUB(BINARY LOG2(8572968212617203413), INTERVAL 1 HOUR_SECOND)) IN (SELECT `col_bigint_key_unsigned`,`col_decimal(40, 20)_undef_unsigned` FROM `table_7_utf8_undef` USE INDEX (`col_double_key_unsigned`, `col_decimal(40, 20)_key_unsigned`))) IS FALSE) OR ((`f7`) BETWEEN `f7` AND `f9`)) IS TRUE ORDER BY `f7`);
   -- MutatedSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING 1 ORDER BY `f5`) UNION (SELECT (BINARY COS(0)|1) AS `f1`,(!1) AS `f2`,(LOWER(`f9`)) AS `f3` FROM (SELECT `col_decimal(40, 20)_key_unsigned` AS `f7`,`col_bigint_key_unsigned` AS `f8`,`col_bigint_key_signed` AS `f9` FROM `table_3_utf8_undef` IGNORE INDEX (`col_decimal(40, 20)_key_unsigned`, `col_varchar(20)_key_signed`)) AS `t2` WHERE (((DATE_ADD(_UTF8MB4'16:47:10', INTERVAL 1 MONTH)) IN (SELECT `col_decimal(40, 20)_key_unsigned` FROM `table_3_utf8_undef`)) OR ((ROW(`f8`,DATE_SUB(BINARY LOG2(8572968212617203413), INTERVAL 1 HOUR_SECOND)) IN (SELECT `col_bigint_key_unsigned`,`col_decimal(40, 20)_undef_unsigned` FROM `table_7_utf8_undef` USE INDEX (`col_double_key_unsigned`, `col_decimal(40, 20)_key_unsigned`))) IS FALSE) OR ((`f7`) BETWEEN `f7` AND `f9`)) IS TRUE ORDER BY `f7`);
   ```

   

2. **Elimination of Union Operation**: The UNION operation was identified as a non-critical component for reproducing the bug, allowing for its removal and further simplification of the query.

   ```sql
   -- OriginalSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING (((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef` USE INDEX (`col_decimal(40, 20)_key_signed`, `col_decimal(40, 20)_key_signed`))) IS FALSE) IS FALSE ORDER BY `f5`);
   -- MutatedSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef` USE INDEX (`col_bigint_key_unsigned`, `col_bigint_key_signed`)) AS `t1` HAVING 1 ORDER BY `f5`);
   ```

   

3. **Omission of ORDER BY and Index Usage**: The ORDER BY clause and specific index hints (USE INDEX, IGNORE INDEX) were removed to focus on the core functional aspects of the query contributing to the bug.

   ```sql
   -- OriginalSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef`) AS `t1` HAVING (((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef`)) IS FALSE) IS FALSE);
   -- MutatedSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1`,(`f5`+`f6`>>TIMESTAMP(_UTF8MB4'2000-06-08')) AS `f2`,(CONCAT_WS(`f4`, `f5`, `f5`)) AS `f3` FROM (SELECT `col_float_key_unsigned` AS `f4`,`col_bigint_undef_signed` AS `f5`,`col_float_undef_signed` AS `f6` FROM `table_3_utf8_undef`) AS `t1` HAVING 1);
   ```

   

4. **Simplification of Column Selection**: Unnecessary columns and complex expressions were eliminated, narrowing down to the essential fields directly involved in the bug's manifestation.

   ```sql
   -- OriginalSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM (SELECT `col_bigint_undef_signed` AS `f5` FROM `table_3_utf8_undef`) AS `t1` HAVING ((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef`)));
   -- MutatedSql
   (SELECT (0^`f5`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM (SELECT `col_bigint_undef_signed` AS `f5` FROM `table_3_utf8_undef`) AS `t1` HAVING 1);
   ```

   

5. **Minimization of Subqueries**: Subqueries that did not contribute to the bug were removed, simplifying the overall query structure and making the bug's source more apparent.

   ```sql
   -- OriginalSql
   (SELECT (0^`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM  `table_3_utf8_undef` AS `t1` HAVING ((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef`)));
   -- MutatedSql
   (SELECT (0^`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM `table_3_utf8_undef` AS `t1` HAVING 1);
   ```

   

6. **Adjustment of Operators and Expressions**: Certain operators and expressions were modified or removed to isolate the bug's trigger, focusing on the minimal set of operations required to reproduce the issue.

   ```sql
   -- OriginalSql
   (SELECT (`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM  `table_3_utf8_undef` AS `t1` HAVING ((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef`)));
   -- MutatedSql
   (SELECT (`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM `table_3_utf8_undef` AS `t1` HAVING 1);
   ```

   

### Final Simplified SQL

The culmination of this process resulted in two simplified SQL statements, one representing the original query's essence and the other its mutated form, both preserving the conditions necessary to trigger the identified bug.

#### Simplified Original SQL

```sql
(SELECT (`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM  `table_3_utf8_undef` AS `t1` HAVING ((CHARSET(`f1`)) NOT IN (SELECT `col_float_undef_signed` FROM `table_3_utf8_undef`)));
```

#### Simplified Mutated SQL

```sql
(SELECT (`col_bigint_undef_signed`&ADDTIME(_UTF8MB4'2017-06-19 02:05:51', _UTF8MB4'18:20:54')) AS `f1` FROM `table_3_utf8_undef` AS `t1` HAVING 1);
```

### Conclusion

This detailed simplification process illustrates a methodical approach to reducing SQL query complexity, focusing on isolating and identifying the essential components contributing to a bug. Through careful elimination and modification of various SQL elements, the process aids in understanding the bug's cause, facilitating more efficient debugging and analysis.
