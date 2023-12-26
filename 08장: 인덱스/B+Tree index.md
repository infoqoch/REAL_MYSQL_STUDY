많은 게시물에서 `mysql, innoDB는 B+Tree이다.` 라는 글을 보았다.  
그러나 mysql공식 홈페이지나 책에서는 B-Tree를 사용한다고 되어있다. (뭘 쓰는지 모르겠어요... Help!!)  
그래서 일단 B+Tree는 뭔지 알아보자!  
https://dev.mysql.com/doc/refman/8.0/en/innodb-physical-structure.html  

# B+Tree
![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/e4082d70-f1fd-4fee-b502-9a1e3bcfcd5e)  
다음과 같은 인덱싱을 B+Tree로 나태내면?  
![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/a202bb36-9a81-4c34-9f10-5083b3bd8955)
* 모든 key, data가 리프노드에 모여있다.
  * B-Tree는 리프노드가 아닌 각자 key마다 data를 가진다.
* 모든 리프노드가 연결리스트의 형태를 띄고 있다.
  * B-Tree는 옆에 있는 리프노드를 검사할 때, 다시 로트노드부터 검사해야한다.



![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/9f1ecb2b-771c-4078-9cd4-abc1abd8ca3e)  


