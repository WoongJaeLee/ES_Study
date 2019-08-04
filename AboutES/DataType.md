# 필드 데이터 타입

1. keyword
    - 별도의 분석기를 거치지 않고 색인
    - 검색 시 필터링 항목, 정렬 항목, 집계 항목
    
    | 값 | 의미 |
    |---|:---:|
    | `boost` | 필드 가중치 |
    | `doc_values` | 필드 메모리에 로드해 캐시 사용 여부 (default : true) | 
    | `index` | 해당 필드 검색 사용 여부 (default ; true) |
    | `null_value` | 데이터 값이 없는 경우 대체할지 설정 |
    | `store` | 필드 값과 별도로 _source 저장 검색 여부 (default : false) |
    
2. text 
    - 지정된 분석기가 문자열 데이터로 인식하고 이를 분석(default: Standard Analyzer)
    - Sorting 이나 Aggregation 연산 사용해야 할 경우 keyword 타입 동시 갖도록 멀티 필드 구성
    
    | 값 | 의미 |
    |---|:---:|
    | `analyzer` | 인덱스 검색에 사용할 형태소 분석기 선택 |
    | `boost` | 필드 가중치, 검색 결과 정렬에 영향을 줌, 기본값 1.0 | 
    | `fileddata` | 정렬,집계, 스크립트에 메모리 저당 필드 데이터 사용여부 설정 (default: false) |
    | `index` | 해당 필드 검색 사용 여부 (default: true)|
    | `norms` | 유사도 점수 산정시 필드 길이 고려 여부 (default: true)|
    | `store` | 필드 값 필도와 별도 _source 저장,검색 여부 (default : false)|
    | `search_analyzer` | 검색 형태소 분석기|
    | `similarity` | 유사도 점수 알고리즘 (default : BM25)|
    | `term_vector` | Analyzed 필드 텀벡터 저장 여부 (default : no)|
    
3. Array
    - 저장되는 값은 모두 같은 타입이어야만 함
    
4. Numeric
    - 숫자 데이터 타입을 알맞게 설정해서 색인과 검색 효율을 높힘
    - long, integer, short, byte, double, float, half_float
    
5. Date
    - 기본 형식 'yyyy-MM-ddTHH:mm:ssZ'
    
6. Range
    - 범위가 있는 데이터 저장할 때 사용
    - integer_range, float_range, long_range, double_range, date_range, ip_range
    
7. Boolean
 
8. Geo-Point
    - 반경 내 쿼리, 위치 기반 집계, 위치별 정렬 등 위치 기반 쿼리를 위해 사용
    
9. IP
    - IPv4,IPv6

10. Object
    - 내부 객체를 계층적 포함
    
11. Nested
    - Object 객체 배열을 독립적으로 색인하고 질의하는 형태