# 1. 查询
```sql
查找QUESTION中id=35的行，只显示TITLE,TAG,ID 三个字段
select TITLE,TAG,ID from QUESTION where ID = 35;
```
# 2. like用法 模糊
```sql
select TITLE,TAG,ID from QUESTION where
(TAG like '%Spring boot%' or
TAG like '%Spring MVC%' or
TAG like 'Java'
)and ID != 2;
```
查找QUESTION中id!=2的行，且字段（列）tag和上述pring boot、Spring MVC和Spring MVC相关，只显示TITLE,TAG,ID 三个字段
`%`的作用是放在单词首部是指单词前面的字可以忽略，放在末尾，表示单词最后的字可以忽略。按此标准查找数据库
但是这样如果标签属性过多，则麻烦。

可以采用正则的方式：合上书等价
```sql
select TITLE,TAG,ID from QUESTION where
    TAG REGEXP 'Spring boot|Spring MVC|Java'and ID != 2;
```
**p1|p2|p3**	匹配 p1 或 p2 或 p3。例如，'z|food' 能匹配 "z" 或 "food"。'(z|f)ood' 则匹配 "zood" 或 "food"。