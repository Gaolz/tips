MySQL tips
========================

#### 1: [see what character set a database | table | column is?](http://stackoverflow.com/questions/1049728/how-do-i-see-what-character-set-a-mysql-database-table-column-is)
  * For Columns:

  > `SHOW FULL COLUMNS FROM table_name;`

  * For Schemas:
  > `SELECT default_character_set_name FROM information_schema.SCHEMATA`
WHERE schema_name = "schemaname";

  * For Tables:
  > SELECT CCSA.character_set_name FROM information_schema.`TABLES` T,
       information_schema.`COLLATION_CHARACTER_SET_APPLICABILITY` CCSA
WHERE CCSA.collation_name = T.table_collation
  AND T.table_schema = "schemaname"
  AND T.table_name = "tablename";
-----

#### 2: [convert entire characterset and collation to UTF-8?](http://stackoverflow.com/questions/6115612/how-to-convert-an-entire-mysql-database-characterset-and-collation-to-utf-8)
  * For Database:
  > `ALTER DATABASE databasename CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;`

  * For Tables:
  > `ALTER TABLE tablename CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;`
-----
