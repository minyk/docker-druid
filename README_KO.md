# Druid cluster

## Druid의 확장가능한 프레임워크

O Druid란 무엇인가?

O druid는 다음의 구성요소로 이루어져 있습니다.:

- [Historical](http://druid.io/docs/latest/design/historical.html) 데이터 저장소를 관리하고, "historical(실시간이 아닌)" 쿼리를 수행하는 노드입니다. "deep storage"에 저장된 데이터 세그먼트를 대상으로 브로커에서 전달받은 쿼리를 수행하고 그 결과를 브로커 노드로 반환합니다. Zookeeper를 사용하여 맴버쉽을 관리하고, 역시 Zookeeper
를 사용하여 세그먼트의 적재/삭제 상태를 모니터링합니다.
- [Broker](http://druid.io/docs/latest/design/broker.html) 외부에서 쿼리를 받아서 `Realtime` 노드와 `Historical` 노드로 전달합니다. 그 후 양쪽에서 결과를 받아 병합하여 외부로 전달합니다. `Broker` 노드는 `Realtime` 과`Historical` 노드를 `Zookeeper`를 통해서 구분합니다.
- [Indexing Service (Overlord)](http://druid.io/docs/latest/design/indexing-service.html) 입력 데이터를 색인하여 저장하는 서비스입니다.
- [Realtime](http://druid.io/docs/latest/design/realtime.html) `Realtime` 데이터를 실시간으로 처리하는 노드입니다. 색인 서비스보다는 구성하기 쉽지만, 운영에서는 사용하려면 제약 사항들이 있습니다.

![flow-part-1](docs/druid-dataflow-3.png)

![flow-part-2](docs/druid-manage-1.png)

## Druid 서비스의 메모리 관리 방법
- http://druid.io/docs/latest/operations/performance-faq.html


# 사용 방법

```sh
docker compose up
```

잠시 기다리면 각각의 서비스들이 동작됩니다.


- Datasource 목록 UI

```
curl http://localhost:3000/druid/v2/datasources
```

- coordinator 콘솔 UI

```
open http://localhost:3001/
```


각각의 폴더에는 커스텀할 수 있도록 `Dockerfile`이 준비되어 있습니다.
