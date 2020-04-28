# GraphDB - JanusGraph docker 설치방법 2
> docker run --rm --name janusgraph-default -p 8182:8182 -v /Users/imac/tmp:/airroutes janusgraph/janusgraph:latest


신규데이터는 아래처럼 해서 저장한다....

> docker exec -it <container-ID> bash 

> /opt/janusgraph/bin/gremlin.sh

>> :remote connect tinkerpop.server conf/remote.yaml session

>> :remote console

![텍스트](bus.jpeg "bus")

>> graph.io(graphml()).readGraph('/airroutes/air-routes.graphml')

commit 은 필요없는것 같음.

>> graph.tx().commit()

![텍스트](bus.jpeg "bus")

데이터를 파이썬으로 조회할수 있다.

```
from gremlin_python import statics
from gremlin_python.structure.graph import Graph
from gremlin_python.process.graph_traversal import __
from gremlin_python.driver.driver_remote_connection import DriverRemoteConnection
graph = Graph()
connection = DriverRemoteConnection('ws://localhost:8182/gremlin', 'g')
# The connection should be closed on shut down to close open connections with connection.close()
g = graph.traversal().withRemote(connection)
print(g.V().toList())
```

![텍스트](bus.jpeg "bus")
