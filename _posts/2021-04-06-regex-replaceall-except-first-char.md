---
layout: post
title:  "regexp replace all except first character"
date: 2021-04-06 13:30:00 +0900
published: true
---
# 주제
정규식을 이용하여 첫글자를 제외한 모든 문자열 바꾸[기 

# 목적
개인 식별요소를 제거하기 위한 데이터 마스킹 기법 적용
데이터 마스킹은 임의의 잡음을 추가, 공백/대체 등의 작업을 통해
남아있는 정보 그 자체로 개인을 식별할 수 없어야 하며, 인터넷 등 공개된 정보와 결합하였을 경우에도 개인을 식별할 수 없게 하는 것.

# 설명 
```sh
-- input : xxxxx@xxx.com
regexp_replace(email, '(?!^.)(?<!@)[^@]', '\1*', 'gi' )
-- output : x****@x**.***
```

# regexp 설명 
```
[^X] : X가 아닌 모든 것
(?!^X)Y : X로 시작하지 않는 Y
(?<!X)Y : Y 앞에 X가 없음 
gi : global, case insensitive
\1 : first brace => () 
