<!--HEADING 만드는 법-->

# github에 올릴 문서 만드는 법

<!--Heading 1-->

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6

<!--line 추가하는 법: 언더바 3개 입력시 구분선 추가됨-->

---

<!--텍스트 속성 이용-->

텍스트는 기호 없이 작성 시 작성 가능함

볼드체를 만들때에는 \*모양 2개를 양쪽에 감싸준다.

예를들면 **볼드체** 이다.

이탈릭체는 \*모양 1개를 양쪽에 감싸준다.

예를들면 _이탈릭체_ 이다.

취소선을 만들때에는 ~모양 2개를 양쪽에 감싸준다.

예를들면 ~~취소선~~ 이다.

문장을 quote안에 넣으려면 >를 이용한다.

> quote안에 넣을 문장

문장부호를 넣을 때는 \* 또는 - 또는 숫자를 이용한다.

- 문장부호
- 별표 삽입 후 space 한 칸 띄워야 사용 가능함

* 부호

1. 부호

2) 부호

3. 부호

<!--링크 삽입-->

click [here(https://paper.dropbox.com/doc/2021.04.08--BIwSkR61tBwpoThD_BsQRC8xAg-e2y6gqlg27PnbWfn9Kwd6)]

<!--이미지 삽입-->

| 이미지  | 설명                                                                       |
| ------- | -------------------------------------------------------------------------- |
| 이미지1 | ![이미지 예시(http://13.209.16.95:5000/static/upload/161836253014635.JPG)] |

<!--내 컴퓨터의 이미지 삽입, 줄 바꿈은 어떻게 함?-->

내컴퓨터의 이미지는 git에서 글쓰기 할 떄 드래그해서 넣으면 된다고 함.

![이미지 예시()]

<!--표 삽입-->

표 예시
| header | Description |
| ------ | ----------- |
| cell1 | cell2 |
| cell1 | cell2 |
| cell1 | cell2 |
| cell1 | cell2 |
| cell1 | cell2 |

<!--표에서 정렬-->

- 오른쪽 정렬한 표 만들기

| header | Description |
| -----: | ----------: |
|  cell1 |       cell2 |
|  cell1 |       cell2 |
|  cell1 |       cell2 |
|  cell1 |       cell2 |
|  cell1 |       cell2 |

양쪽 정렬
|header|Description|
|:--:|:--:|
|cell1|cell2|
|cell1|cell2|
|cell1|cell2|
|cell1|cell2|
|cell1|cell2|

<!--문서 안에서 code 보여주기-->

문서안에서 code를 보여줄 때 `이것은 코드입니다`로 표현 가능하다.

코드 블럭을 만들 때에는(```뒤에 코드 파일의 이름, python, ts, js 등을 넣어 코드를 색으로 표현 가능함)

```py
inport padas as pd
```

로 작성할 수 있다.
