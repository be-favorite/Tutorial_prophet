# R 유저들을 위한 단변량 시계열 예측 모형 Prophet 소개
이 Repo는 Facebook에서 제안하는 Prophet 모형을 소개하는 질 좋은 튜토리얼 자료를 찾고 있는 한국 R 유저들을 위해 만들었습니다. Facebook에서 훌륭한 [튜토리얼](https://facebook.github.io/prophet/docs/quick_start.html#r-api)을 제공하고 있으나, 영어로 된 자료라 영어에 능숙하지 않은 유저들은 약간 불편할 수 있겠다는 생각을 했어요. 안그래도 공부에 집중하기 힘든데, 영어로된 자료면 더 하기 싫을 때가 있죠. 물론, 해당 글도 Facebook에서 제공하는 튜토리얼을 기반으로 제 의견을 첨가하여 작성했습니다. 혹시 Prophet의 실제 적용뿐만 아니라, 자세한 이론적 부분이 궁금하다면 [제 블로그](https://be-favorite.tistory.com/64)를 참고해주시면 될 것 같습니다. 

Prophet 모형을 이렇게 소개하는 이유는 [Prophet 논문](http://lethalletham.com/ForecastingAtScale.pdf)을 들여다 봤을 때, Facebook에서 해당 모형을 만든 motivation이 너무 매력적이었기 때문이에요. 시계열 예측 모형이 필요로 되는 실무자라면 이론적 부분은 차치하고 이 motivation만 이해해도 Prophet 모형을 얼른 적용해보고 싶을 겁니다:sunglasses::

* :exclamation:도메인 지식은 갖추었으나, 시계열을 다루는 지식이 부족한 실무자들을 위해
  + 실제 통계학 전공자들도 시계열 분석을 처음 공부할 때 어려움을 느끼는 경우가 많고, 대표적 통계적 시계열 예측모형이라 할 수 있는 ARIMA 모형을 실무에 적용하기 위해서는 공부해야할 것들이 많음(e.g 정상성)
* :exclamation:유연성(flexibility), 확장성(scalable)이 뛰어나며 Business time series에 유연하게 적용할 수 있는 모형의 필요성
  + 앞서 말씀드린 ARIMA 모형은 각 자료가 갖는 특성들을 유연하고 세밀하게 반영하기 힘듬.
  
일단 첫 번째 motivation이 매우 감명깊었어요. Prophet 모형은 시계열을 3가지 요소로 분해하고 각 요소를 시간의 함수로 가법적으로 모형화하는데, 해당 자료에 대한 이해가 깊은 도메인 지식이 풍부한 실무자라면 이 튜토리얼만 잘 이해하고 수행해본다면 쉽게 모형을 advance할 수 있을거라고 생각합니다. 특히, 휴일 효과(holiday effect)와 같은 것들을 아주 쉽게 사용자가 custom할 수 있다는 점이 아주 매력적이었어요. 

좀 더 자세한 Prophet 모형의 이론적 부분이 궁금하시다면 제가 글의 초반부에 말씀드린 제 블로그를 참고해주세요. 혹시, 제 블로그 글만으로 부족하다거나 모호한 부분이 있다면 해당 블로그의 글에 댓글을 달아주시거나 위의 Prophet 논문 링크를 클릭하여 참고하시면 더 좋을겁니다! 

해당 튜토리얼이 단변량 시계열 예측 모형이 필요로 되는 실무자들에게 조금이나마 도움이 됐으면 좋겠습니다.:blush:

이제 튜토리얼을 하러 가봅시다. 여기를 참고해주세요.

<br>

<div align=center>

[![Tistory badge](https://img.shields.io/badge/Tistory-SLOG-orange)](https://be-favorite.tistory.com/)
[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/taemo-bang-8b9999184/)](https://www.linkedin.com/in/taemo-bang-8b9999184/) 
[![Instagram Badge](https://img.shields.io/badge/-Instagram-dd2a7b?style=flat-square&logo=instagram&logoColor=white&link=https://www.instagram.com/qkdxoah/)](https://www.instagram.com/qkdxoah/)
