# GraphDB - JanusGraph 설치 및 테스트

저장용도로 카산드라를, 빠른조회 및 색인을 위해 elasticsearch를 사용하고, 쿼리를 위해 gremlin을 사용한다.


1. docker run --name jg-cassandra --rm -d -e CASSANDRA_START_RPC=true -v /Users/imac/tmp/janusgraph/cassandra:/var/lib/cassandra -p 9160:9160 -p 9042:9042 -p 7199:7199 -p 7001:7001 -p 7000:7000 cassandra:3.11

2. docker run --name es --rm -d -v /Users/imac/tmp/janusgraph/elasticsearch:/usr/share/elasticsearch/data -p 9200:9200 -p 9300:9300 elasticsearch:5.6

3. docker메모리 설정을 4GB이상 하지 않으면 es가 실행이 안될수도 있다.

4. https://github.com/JanusGraph/janusgraph/releases 에서 janusgraph-0.4.1-hadoop2.zip 다운로드 하고 압축을 풀것

5. conf/gremlin-server/gremlin-server-configuration.yaml 파일에 scriptEvaluationTimeout 값을 300000 정도로. (300초?) - 작으면 데이타 색인시 타임아웃발생한다.

6. conf/janusgraph-cassandra.properties 에 아래 내용추가. console에서 테스트데이타생성시 아래 환경설정이 필요하다.
```
graph.graphname=ConfigurationManagementGraph
```

7. ./bin/gremlin-server.sh conf/gremlin-server/gremlin-server-configuration.yaml (서버시작)
           ./bin/gremlin-server.sh ( 이렇게 시작해야 python에서 접속 가능)  default로 conf/gremlin-server/gremlin-server.yaml 을 사용.

8. ./bin/gremlin.sh (6의 서버에 접속)

9. 아래 두개의 명령을 먼저실행. 콘솔의 내용을 서버로 전송하기위한 설정. 

> gremlin> :remote connect tinkerpop.server conf/remote.yaml session
>> ==>Configured localhost/127.0.0.1:8182

> gremlin> :remote console
>> ==>All scripts will now be sent to Gremlin Server - [localhost:8182]-[5206cdde-b231-41fa-9e6c-69feac0fe2b2] - type ':remote console' to return to local mode

