많은 게시물에서 `mysql, innoDB는 B+Tree이다.` 라는 글을 보았다.  
그러나 mysql공식 홈페이지나 책에서는 B-Tree를 사용한다고 되어있다. (뭘 쓰는지 모르겠어요... Help!!)  
그래서 일단 B+Tree는 뭔지 알아보자!  
https://dev.mysql.com/doc/refman/8.0/en/innodb-physical-structure.html  

# B-Tree
![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/39c55705-ca3c-4195-ab2f-60bcd6f6b8c6)  
* 모든 노드에 data가 있다.


# B+Tree
B-Tree는 어떤 한 데이터의 검색에서는 빠를 수 있으나, 모든 데이터를 순회하기 위해서는 leaf node까지 갔다가 다시 부모 node로 BackTracking하여 트리의 모든 node를 방문해야하므로 비효율적. 이러한 단점을 보안한 것이 B+Tree이다.  

![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/e4082d70-f1fd-4fee-b502-9a1e3bcfcd5e)  
다음과 같은 인덱싱을 B+Tree로 나태내면?  
![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/a202bb36-9a81-4c34-9f10-5083b3bd8955)
* 모든 key, data가 리프노드에 모여있다.
  * B-Tree는 리프노드가 아닌 각자 key마다 data를 가진다.
* 모든 리프노드가 연결리스트의 형태를 띄고 있다.
  * B-Tree는 옆에 있는 리프노드를 검사할 때, 다시 로트노드부터 검사해야한다.

### 장점
* leaf가 아닌 node들에 실제 데이터를 저장하지 않고 key에 따라 자식 node로 향하는 포인터만 가질 수 있으므로, 저장 공간을 절약해 더 많은 포인터를 저장할 수 있다. -> 한 node가 가질 수 있는 자식 node의 최대 개수를 늘릴 수 있으므로, 트리의 depth를 낮출 수 있다.
* Full Scan시 linked list로 연결된 left node들에 대해서만 읽기를 진행하면 되므로 시간이 단축된다.

### 단점
* 실제 Data에 접근하기 위해서는 무조건 트리의 맨 아래에 있는 leaf node까지 접근해야한다.

### 차이
![image](https://github.com/RealMySQL-Study/REAL_MYSQL_STUDY/assets/67637716/9f1ecb2b-771c-4078-9cd4-abc1abd8ca3e)  


