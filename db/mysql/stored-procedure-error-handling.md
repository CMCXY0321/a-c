#### DECLARE HANDLER
```sql
DECLARE action HANDLER FOR condition_value statement;
```

```sql
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION SET has_error = 1;
```

```sql
DECLARE EXIT HANDLER FOR SQLEXCEPTION
  BEGIN
    ROLLBACK;
    SELECT 'An error has occurred, operation rollbacked and the stored procedure was terminated';
  END;
```

```sql
DECLARE CONTINUE HANDLER FOR NOT FOUND SET no_row_found = 1;
```

```sql
DECLARE CONTINUE HANDLER FOR 1062
SELECT 'Error, duplicate key occurred';
```

#### 存储过程中的MySQL处理程序
```sql
USE testdb;
DELIMITER $$
CREATE PROCEDURE insert_article_tags(IN article_id INT, IN tag_id INT)
BEGIN
  DECLARE CONTINUE HANDLER FOR 1062
  SELECT CONCAT('duplicate keys (',article_id,' , ',tag_id,') found') AS msg;

  -- insert a new record into article_tags
  INSERT INTO article_tags (article_id,tag_id)
  VALUES (article_id, tag_id);

  -- return tag count for the article
  SELECT COUNT(*) FROM article_tags;
END$$
DELIMITER ;
```

```sql
CALL insert_article_tags(1, 1);
CALL insert_article_tags(1, 2);
CALL insert_article_tags(1, 3);
```

```sql
CALL insert_article_tags(1, 3);
```

#### MySQL处理程序优先级
```sql
DELIMITER $$
CREATE PROCEDURE insert_article_tags_3 (IN article_id INT, IN tag_id INT)
BEGIN
  DECLARE EXIT HANDLER FOR 1062 SELECT 'Duplicate keys error encountered';
  DECLARE EXIT HANDLER FOR SQLEXCEPTION SELECT 'SQLException encountered';
  DECLARE EXIT HANDLER FOR SQLSTATE '23000' SELECT 'SQLSTATE 23000';

  -- insert a new record into article_tags
  INSERT INTO article_tags(article_id,tag_id)
  VALUES(article_id,tag_id);

  -- return tag count for the article
  SELECT COUNT(*) FROM article_tags;
END $$
DELIMITER ;
```

```sql
CALL insert_article_tags_3(1,3);
```

#### 使用命名错误条件
```sql
DECLARE EXIT HANDLER FOR 1051 SELECT 'Please create table abc first';
SELECT * FROM abc;
```

```sql
DECLARE table_not_found CONDITION for 1051;
DECLARE EXIT HANDLER FOR  table_not_found SELECT 'Please create table abc first';
SELECT * FROM abc;
```
