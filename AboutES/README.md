# 엘라스틱 서치
 
- 스키마리스 기능을 제공하지만 실무에서는 복잡하여 진짜 특수한 경우 말고는 사용하지 않음

- 실수로 생성되는 것 막으려면
 
```
노드 설정 파일 : action.auto_create_index = false
인덱스 별로 제공되는 : index.mapper.dynamic = false
```

- 필드
``` 
keyword : 일반적인 문자열
text : 형태소 분석
기타...
```
- __인덱스 삭제는 복구가 안됨 절대 확인!!__

# 데이터 모델링

- 한번 색인된 타입을 변경하려면 인덱스를 삭제한 후 다시 생성하거나 매핑정보를 다시 정의 해야된다. 

- 매핑 정보 설정시 고려사항
```
1. 문자열 여부
2. 날짜 필드 여부
3. _source에 정의될 필드
4. 매핑에 정의되지 않고 유입되는 필드 처리 
```

- 매핑 파라미터
    - analyzer : text 데이터 타입의 필드는 기본적으로 analyzer 형태소 분석기를 지정해줘야한다.
    - normalizer : term query 분석에 사용
    - boost : 필드에 가중치 부여(7.0부터 색인시 설정기능 제거)
    - coerce : 색인시 자동 변환 허용 여부
    - copy_to : 매핑 파라미터 추가한 필드의 값을 지정 필드로 복사
    - fielddata : 엘라스틱서치 힙 공간 메모리 캐시, 극히 최소한으로 사용
    - doc_values : 엘라스틱 서치 기본 캐시, 루씬 기반 캐시(text 타입 제외한 모든 타입 적용)
    - dynamic : 매핑에 필드를 추가시 동적 여부 결정 
        - true : 새로 추가되는 필드 추가
        - false : 새로 추가되는 필드 무시, 색인되지 않고 _source에만 표시
        - strict : 새로운 필드가 감지되면    
   

#집계 API

- Bucket Aggregation
    - 문서의 필드를 기준으로 버킷을 집계, 집계 중 가장 많이 사용.
    
- Metric Aggregation
    - 문서에서 추출된 값으로 Sum, Max, Min, Avg 계산

- Matrix Aggregation
    - 행렬 값을 합하거나 곱한다.
    
- Pipeline Aggregation
    - 버킷에서 도출된 결과 문서를 다른 필드에 값으로 재분류
    
# 메타 필드

1. _index
    - 해당 문서가 속한 인덱스 이름 포함
2. _type
    - 해당 문서가 속한 매핑의 타입 정보
3. _id 
    - 문서를 식별하는 유일한 키 값
4. _uid
    - 특수한 목적의 식별키 , \#태그를 통해 _type 과 _id값을 조합해 사용
5. _source
    - 문서의 원본 데이터
    - 원본 JSON 문서를 검색 결과로 표시할 시 사용
6. _all
    - 색인에 사용된 모든 필드의 정보를 가짐
    - 데이터 크기를 너무 많이 차이하여 6.0 이상부터 deprecated
7. _routing
    - 특정 문서를 특정 샤드에 저장하기 위해 사용
    
# 필드 데이터 타입

1. keyword
    - 별도의 분석기를 거치지 않고 색인
    - 검색 시 필터링 항목, 정렬 항목, 집계 항목
    - boost : 필드 가중치
    - doc_values : 필드 메모리에 로드해 캐시 사용 여부 (default : true)
    - index : 해당 필드 검색 사용 여부 (default ; true)
    - null_value : 데이터 값이 없는 경우 대체할지 설정
    - store : 필드 값과 별도로 _source 저장 검색 여부 (default : false)
2. 
