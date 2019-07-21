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
    
