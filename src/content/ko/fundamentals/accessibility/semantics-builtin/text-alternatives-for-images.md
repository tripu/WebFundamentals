project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: alt 속성을 이용한 이미지 대체 텍스트 제공


{# wf_updated_on: 2016-10-04 #}
{# wf_published_on: 2016-10-04 #}

# 이미지 대체 텍스트 {: .page-title }

{% include "web/_shared/contributors/megginkearney.html" %}
{% include "web/_shared/contributors/dgash.html" %}
{% include "web/_shared/contributors/aliceboxhall.html" %}



이미지는 대부분의 웹페이지에서 중요한 구성 요소인데, 당연히 시력이 나쁜 사용자를
배려하여 적절한 대안을 제공해야 합니다. 웹페이지에서
이미지가 수행하는 역할을 잘 고려하여 어떤 형식의 텍스트로 이미지를 대체할지 정해야 합니다.
다음 이미지를 한 번 보시죠.

    <article>
      <h2>Study shows 9 out of 10 cats quietly judging their owners as they sleep</h2>
      <img src="imgs/160204193356-01-cat-500.jpg">
    </article>

<article>
  <h2>Study shows 9 out of 10 cats quietly judging their owners as they sleep</h2>
  <img src="imgs/160204193356-01-cat-500.jpg">
</article>

이 페이지에는 고양이의 잘 알려진 판단 행동을 묘사하는
고양이 사진이 있습니다. 스크린 리더는 이미지의 리터럴 이름인
`"/160204193356-01-cat-500.jpg"`를 사용해 이미지를 음성으로 알려줍니다. 물론 정확하긴 하지만 내용 이해에는 전혀
도움이 안 됩니다.

이럴 때 `alt` 속성을 사용하여 이미지에 대해 유용한
대체 텍스트를 제공할 수 있습니다. 예컨대, '매서운 눈초리로 허공을 응시하는 고양이'와 같은 텍스트 말이죠.

    <img src="/160204193356-01-cat-500.jpg" alt="매서운 눈초리로 허공을 응시하는 고양이">

그러면 스크린 리더가 이미지에 대한 간결한 설명(검은색
VoiceOver 표시줄)을 읽어주고 사용자는 그 기사를
계속 들을지 선택할 수 있습니다.

![시각장애인을 위해 개선된 alt 텍스트가 있는 이미지](imgs/funioncat2.png)

`alt`에 대한 간략한 설명:

 - 이미지 로드에 실패할 때처럼 이미지를 사용할 수 없거나
   웹 크롤링 봇이 이미지에 액세스하거나 스크린 리더가 이미지를 인식할 때 사용할 문자열을 지정하고 싶을 경우
   `alt`를 사용하면 됩니다.
 - `alt`는 이미지를 사용할 수 없는 경우에 *한정하여* 사용된다는
   점에서 `title`이나 캡션과는 다릅니다.

유용한 alt 텍스트를 쓰는 데는 요령과 기술이 필요합니다. 유용한 대체 텍스트가 될 만한
문자열의 요건이라면, 역시 이미지가 담고 있는 내용과 같은 개념과 같은 맥락적 의미를 잘
전달해야 할 것입니다.

위에 표시된 이미지들처럼 페이지의 발행인란에 링크로 연결된 로고 이미지를 생각해 봅시다.
이 이미지를 'Funion 로고'라고 설명하면 꽤나 정확한 설명이 될 겁니다.

    <img class="logo" src="logo.jpg" alt="Funion 로고">

'홈'이나 '기본 페이지'와 같이 더 간단한 대체 텍스트로
지정하고 싶을 수도 있겠지만, 그건 시력이 나쁜 사용자와 시력이 정상인 사용자에게 모두 좋지 않은 선택입니다.

페이지에서 발행인란 로고를 찾고 싶어 하는 스크린 리더 사용자가 있다고 생각해 보세요.
그러면 alt 값으로 '홈'을 지정할 경우 실제로 더 큰 혼동을
주게 되겠죠. 정상 시력의 사용자도 스크린 리더 사용자와 똑같은 문제에 부딪힙니다.
사이트 로고를 클릭하면 어떻게 되는지 금방 이해가 되지 않기 때문이죠.

반면에, 이미지를 설명하는 게 항상 유용한 것만은 아니라는 점도 염두에 두세요. 예를 들어,
'검색'이라는 텍스트가 있는 검색 버튼 내부에 있는 돋보기 이미지를
생각해 보세요. 그 자리에 텍스트가 없었다면 이미지의 alt 값으로 분명히
'검색'을 지정했을 겁니다. 그러나 이미 텍스트가 표시되어 있고
스크린 리더는 이 '검색'이라는 단어를 인식하여 사용자에게 읽어주겠죠. 따라서 이런 이미지에 똑같은 `alt` 값을 부여하는 건
불필요한 중복이 됩니다.

하지만 `alt` 텍스트를 생략하면 이미지 파일 이름이
들릴 텐데, 이 정보는 불필요할 뿐 아니라 자칫 혼동을 일으킬 수도 있습니다. 이런
경우에는 그냥 빈 `alt` 속성을 사용하면 돼요. 그러면 스크린 리더가
이미지를 통째로 건너뛰게 됩니다.

    <img src="magnifying-glass.jpg" alt="">

요컨대, 모든 이미지에 `alt` 속성이 있어야 하지만 빠짐없이 텍스트가 있어야 하는 건
아닙니다. 중요한 이미지에는 어떤 이미지인지 간략하게 설명하는 alt 텍스트가 있어야 하지만,
장식적 이미지는 alt
속성을 비워 두어야 합니다(즉, `alt=""`).


{# wf_devsite_translation #}
