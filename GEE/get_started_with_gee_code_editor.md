구글어스엔진 코드편집기 시작하기
========================
구글어스엔진은 지리공간 정보처리 플랫폼으로, 전지구 규모로 데이터를 분석하고 시각화할 수 있다. 이 어플리케이션은 클라우드 기반이기 때문에 로컬환경에서 어플리케이션을 실행하는 것에 비해 처리속도가 매우 빠르다. 게다가 구글어스엔진을 사용하면 구글 데이터 카탈로그/아키이브가 보유한 40년 이상의 과거 및 현재 landsat(4, 5, 7, 8) 데이터, MODIS(Moderate Resolution Imaging Spectro-Radiometer) 데이터에 접속할 수 있다. 또한 우리가 가진 래스터/벡터 데이터를 업로드해서 프라이빗하게 또는 공개하여 이용할 수 있다. 본 튜토리얼은 구글어스엔진을 위한 자바스크립트 API를 소개한다.


## 구글어스엔진 접속하기

구글어스엔진은 무료로 사용할 수 있지만 서비스에 접근권한을 얻기 위해서는 자신의 구글계정을 등록하야 한다. [구글어스엔진 등록 페이지](https://signup.earthengine.google.com/)로 가서 필요한 인증을 제공한다. 그러면 웹기반 개발환경에 링크과 문서 등이 있는 이메일을 받을 수 있다. 이 확인 메일을 받는데는 24시간 정도 소요될 수 있다.


## 구글어스엔진 코드편집기(IDE)

어스엔진은 어스엔진 [코드편집기](https://code.earthengine.google.com/)를 통해 웹브라우저에서 바로 사용할 수 있다. 이것은 매우 빠른 데이터 처리와 데이터 시각화를 제공한다. 확인 이메일을 받았다면, 바로 당신의 브라우저에서 코드편집기를 열어보자.

### 특징
코드편집기는 4개의 모듈로 나누어 구성되어 있다: 관리자, 코드편집기, 콘솔, 지도

### 관리자(Manager)
관리자(좌측상단)는 어스엔진을 위한 기본적인 파일시스템으로 볼 수 있다. 관리자는 3개의 서브모듈로 구분하여 구성된다.

- Scripts : 당신의 스크립트가 여기에 저장되며, 추가적으로 구글에서 제공하는 예제도 있음
- Docs: 어스엔진을 위한 문서
- Assets: 당신이 로컬의 파일을 어스엔진에 업로드 할 수 있는 곳

### 코드편집기(Code Editor)
코드편집기(중앙 상단)는 당신이 자바스크립트로 스크립트를 작성하고 실행할 수 있는 곳이다. 이 편집기는 당신의 코드를 포맷하고, 문제가 있는 코드를 표시하고, 자동완성, 그리고 어스엔진 기능을 위한 힌트를 제공한다. 코드편집기 상단에 당신의 스크립트를 실행, 재설정, 저장하는 버튼이 있다.

### 콘솔(Console)
콘솔(우측상단)은 3개의 서브모듈, 즉 Inspector, Console, Tasks 로 구분하여 구성되어 있다. Inspector는 지도 상에 클릭을 통해 지도를 인터랙티브하게 조회할 수 있게 한다. 콘솔은 스크립트창에서 print()문으로 무자를 출력하게 해주는데, 대개 스크립트창에서 사용 중인 파일에 대한 메타데이터를 얻을 때 이용한다. 태스크 서브모듈은 수행완료에 상당한 시간이 걸리는 태스크를 요청했을 때 그 경과를 볼 수 있다.

### 지도(Map)
지도(하단)는 스크립트의 시각적 결과를 보여주는 곳으로 지구 이미지의 15미터 기본맵 위에서도 볼 수 있다.

## 자바스크립트 알아보기
웹기반 IDE의 코드편집기에서 쓰는 스크립트는 자바스크립트로 작성되어야 한다. 자바스크립트는 비교적 배우기 쉬운 프로그래밍 언어다. 자바스크립트의 데이터 타입에는 문자형, 숫자형, 부린형, 배열, 객체이 있다. 기본 연산자는 + (add/concatenation), = (assignment), === (equality), ! (negation), !== (not equal)  등을 지원한다. 자바스크립트는 객체지향 프로그래밍 언어이기 때문에 자바스크립트의 모든 것, 예를 들어 변수 또는 함수는 객체(object)다.  아래와 같이 자바스크립트로 간단히 ‘Hello World!’ 프로그램을 써보자. 자바스크립트의 기초에 관해 좀 더 알고싶다면 [여기에서](https://developer.mozilla.org/en-US/Learn/Getting_started_with_the_web/JavaScript_basics) 확인할 수 있다.


    /* The below script will print 'Hello World!' to the console */

    var string_to_print = 'Hello World!'

    print(string_to_print)

추가적으로, 어스엔진은 Image와 Feature라는 특징적인 데이터 구조를 갖는데, 이는 각각 래스터와 벡터 데이터에 해당한다. 맵상의 Features는  지오메트리(Geometry)로 구성되어 있다. 이미지들의 스택은 ImageCollection, 그리고 Features의 콜렉셕은 FeatureCollection이다. 기타 기본적인 자바스크립트 데이터구조, 예를 들어 dictionaries, lists, arrays, number, string 등 또한 이용할 수 있다.

### 어스엔진에서 Landsat 영상 이용하기
이제 어스엔진에서 스크립트를 생성하고 실행해보자. 아래 코드를 코드편집기에 복사해서 붙여넣고 ‘Run’을 눌러보자.

    print(ee.Image('LANDSAT/LC8_L1T/LC80440342014077LGN00'));

어스엔진은 구글에서 제공하는 엄청난 용량의 데이터에 접속하게 해준다. 위의 코드라인은 구글 아카이브에서 LC80440342014077LGN00 Landsat 파일을 이용한다. 이 파일의 메타정보인 type, id, band names, extents 등을 콘솔창의 출력을 통해 볼 수 있다. 위의 코드라인을 실행하고 파일의 메타데이터를 확인했다면, 다음 코드라인을 복사해서 붙여넣기를 한후 ‘Run’을 눌러보자.

    /* Load an image and store it in a variable called 'image' */
    
    var image = ee.Image('LANDSAT/LC8_L1T/LC80440342014077LGN00');

    /* Center the map on the image and set the zoom level to 9*/

    Map.centerObject(image, 9);
    
    /* Display the image */
    Map.addLayer(image);

위의 스크립트를 실행했다면, 지도 상에 Landsat 이미지가 나타나면서 새만금 해역이 확대되어 보일 것이다. 이것은 구글어스엔진의 핵심 기능인, 데이터 획득, 로드(load), 지도상에 표출/시각화이다. 또 다른 예제로, 코드편집기에 아래 코드를 복사해서 붙여넣기를 한 후 ‘Run’을 눌러보자.

    /* Load the image from the archive */
    
    var image = ee.Image('LANDSAT/LC8_L1T/LC80440342014077LGN00');

    /* Define visualization parameters in an object literal */
    
    var vizParams = {bands: ['B5', 'B4', 'B3'], min: 5000, max: 15000, gamma: 1.3};

    /* Center the map on the image and display */
    
    Map.centerObject(image, 9);

    Map.addLayer(image, vizParams, 'Landsat 8 false color');


이 스크립트는 동일 데이터를 시각화하지만, 이번엔 ‘B5’, ‘B4’, ‘B3’ 으로 이름붙여진 밴드와 min, max, gamma와 같은 추가 변수만을 사용할 것이다. 아래 코드를 코드편집기에 더해서 다시 ‘Run’을 눌러보자.

    var counties = ee.FeatureCollection('ft:1S4EB6319wWW2sWQDPhDvmSBIVrD3iEmCLYB7nMM');
    Map.addLayer(counties, {}, 'counties');

이제 미국의 모든 주들이 지도 상에 시각화되어 보일 것이다.

## Next steps
위의 섹션은 구글어스엔진의 핵심기능 중 일부를 살펴본 것이지만, 제공된 예제는 그만큼 간단하다. 좀더 구글어스엔진에 대해 상세히 알고싶다면, [어스엔진 문서](https://developers.google.com/earth-engine/getstarted)를 찾아보자. 여기에는 필터링, 정렬, 밴드 연산, 맵핑, reducing, 마스킹 등과 같은 매카니즘에 대한 예제와 설명이 있다. 구글의 데이터 카탈로그를 통해 접속하고자하는 모든 데이터 리스트는 [여기서](https://code.earthengine.google.com/datasets) 찾을 수 있다.