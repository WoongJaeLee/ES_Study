# 분석기

분석기의 프로세스
- Character Filter : 문장에 특정한 규칙에 의해 전처리
- Tokenizer Filter : 텍스트를 개별 토큰으로 분리함
- Token Filter : 개별 토큰을 필터링해서 원하는 토큰으로 변환

### 대표적 분석기
1. Standard Analyzer
- Default analyzer
- 공백 혹은 특수 기호를 기준으로 토큰 분리, 모든 문자를 소문자로 변경
- Standard Tokenizer
    - Standard Token Filter
    - Lower Case Token Filter
    
2. Whitespace Analyzer
- 공백으로 토큰을 분리

3. Keword Analyzer
- 전체 입력 문자열을 하나의 키워드로 처리 

### 전처리 필터 
1. html_strip_char_filter 
- html 제거


### 토크나이저 필터
1. Standard Tokenizer 
- 대부분의 기호를 만나면 토큰으로 나눔

2.Whitespace Tokenizer
- 공백을 만나면 토큰화

3. Ngram Tokenizer 
- 한글자씩 토큰화 등 다양한 옵션 지원(자동완성 기능 등에 유용)

    | param | about |
    |---|:---:|
    | `min_gram` | 최소 길이( default 1) |
    | `max_gram` | 최대 길이( default 2) |
    | `token_chars` | 토큰에 포함할 문자열<br><br> - letter<br>- digit<br>- whitespace<br>- punctuation<br>-symbol |

4. Edge Ngram Tokenizer
- 지정된 문자중 하나를 만날 때마다 시작 부븐 고정, 단어를 자르는 방식으로 토큰 생성

5. Keyword Tokenizer
- 전체를 하나의 토큰화

### 토큰 필터
토크나이저에 의해 토큰을 분리 후 동작

1. Ascii Folding Token Filter
- 아스키 코드에 해당하는 알파벳,숫자,기호에 해당 않는 경우 해당 요소로 변경

2. Lowercase Token Filter
- 전체 문자를 소문자로 변환

3. Uppercase Token Filter
- 