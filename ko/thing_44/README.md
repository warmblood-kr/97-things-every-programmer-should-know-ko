# 두 개 이상의 프로그래밍 언어를 잘 알아라

프로그래밍 심리학 연구자들은 오랫동안 프로그래밍 전문성이 프로그래머가 편안하게 다룰 수 있는 서로 다른 프로그래밍 패러다임의 수와 직접적으로 관련이 있다는 것을 알고 있었습니다. 이것은 단순히 알고 있거나 조금 아는 것이 아니라, 진짜로 프로그래밍할 수 있다는 의미입니다.

모든 프로그래머는 하나의 프로그래밍 언어로 시작합니다. 그 언어는 프로그래머가 소프트웨어에 대해 생각하는 방식에 지배적인 영향을 미칩니다. 프로그래머가 그 언어를 사용해서 아무리 많은 년의 경험을 얻더라도, 그 언어에만 머물러 있다면, 그들은 오직 그 언어만 알게 될 것입니다. *한 언어* 프로그래머는 그 언어에 의해 사고가 제약됩니다.

두 번째 언어를 배우는 프로그래머는 도전을 받게 될 것이며, 특히 그 언어가 첫 번째 언어와 다른 계산 모델을 가지고 있다면 더욱 그렇습니다. C, Pascal, Fortran은 모두 같은 기본적인 계산 모델을 가지고 있습니다. Fortran에서 C로 전환하는 것은 몇 가지 도전을 가져오지만, 많지는 않습니다. C나 Fortran에서 C++나 Ada로 이동하는 것은 프로그램이 작동하는 방식에서 근본적인 도전을 가져옵니다. C++에서 Haskell로 이동하는 것은 중대한 변화이고 따라서 중대한 도전입니다. C에서 Prolog로 이동하는 것은 매우 확실한 도전입니다.

우리는 여러 계산 패러다임들을 열거할 수 있습니다: 절차적, 객체지향, 함수형, 논리형, 데이터플로우 등. 이런 패러다임들 사이를 이동하는 것이 가장 큰 도전을 만듭니다.

왜 이런 도전들이 좋은 것일까요? 그것은 우리가 알고리즘의 구현과 적용되는 구현의 관용구 및 패턴에 대해 생각하는 방식과 관련이 있습니다. 특히, 교차 수정(cross-fertilization)이 전문성의 핵심입니다. 한 언어에서 적용되는 문제 해결을 위한 관용구들이 다른 언어에서는 불가능할 수도 있습니다. 한 언어의 관용구를 다른 언어로 포팅하려고 시도하는 것은 우리에게 두 언어와 해결되고 있는 문제에 대해 가르쳐줍니다.

프로그래밍 언어 사용에서의 교차 수정은 거대한 효과를 가집니다. 아마도 가장 명백한 것은 명령형 언어로 구현된 시스템에서 선언적 표현 방식의 증가하고 있는 사용입니다. 함수형 프로그래밍에 정통한 사람은 누구나 C 같은 언어를 사용할 때도 쉽게 선언적 접근법을 적용할 수 있습니다. 선언적 접근법을 사용하는 것은 일반적으로 더 짧고 더 이해하기 쉬운 프로그램으로 이어집니다. 예를 들어, C++는 거의 선언적 표현 방식을 필요로 하는 제네릭 프로그래밍에 대한 전심 전력의 지원으로 이것을 확실히 받아들입니다.

이 모든 것의 결과는 모든 프로그래머가 최소한 두 개의 서로 다른 패러다임에서 프로그래밍에 잘 숙련되어야 하고, 이상적으로는 최소한 위에서 언급한 다섯 개에서 그래야 한다는 것입니다. 프로그래머들은 항상 새로운 언어 배우기에 관심을 가져야 하며, 가급적이면 익숙하지 않은 패러다임의 언어를 배워야 합니다. 일상 업무가 항상 같은 프로그래밍 언어를 사용한다고 하더라도, 사람이 다른 패러다임들로부터 교차 수정할 수 있을 때 그 언어 사용의 증가된 정교함은 과소평가되어서는 안 됩니다. 고용주들은 이것을 받아들이고 현재 사용되고 있는 언어들의 사용 정교함을 증가시키는 방법으로 현재 사용되지 않는 언어들을 직원들이 배울 수 있도록 훈련 예산에 허용해야 합니다.

시작이긴 하지만, 일주일 훈련 과정은 새로운 언어를 배우기에 충분하지 않습니다: 언어에 대한 적절한 실무 지식을 얻으려면 일반적으로 파트타임이라고 하더라도 몇 달의 사용이 필요합니다. 중요한 요소는 구문과 계산 모델만이 아니라 사용의 관용구입니다.

[Russel Winder](http://programmer.97things.oreilly.com/wiki/index.php/Russel_Winder)가 작성함.