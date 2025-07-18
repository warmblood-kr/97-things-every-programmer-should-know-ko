# 당신의 IDE를 알아라

1980년대에 우리의 프로그래밍 환경은 일반적으로 미화된 텍스트 에디터 정도였습니다... 운이 좋다면 말입니다. 요즘 당연하게 여기는 구문 강조 표시는 확실히 모든 사람에게 제공되지 않는 럭셔리였습니다. 코드를 예쁘게 포맷해주는 프리티 프린터는 보통 우리의 간격을 고치기 위해 실행해야 하는 외부 도구였습니다. 디버거도 코드를 단계별로 실행하기 위해 실행하는 별도의 프로그램이었지만, 많은 암호 같은 키 조합이 필요했습니다.

1990년대 동안 회사들은 프로그래머들에게 더 좋고 더 유용한 도구를 제공함으로써 얻을 수 있는 잠재적 수입을 인식하기 시작했습니다. 통합 개발 환경(IDE)은 이전의 편집 기능을 컴파일러, 디버거, 프리티 프린터, 그리고 다른 도구들과 결합했습니다. 그 시기에 메뉴와 마우스도 인기를 얻게 되었는데, 이는 개발자들이 더 이상 편집기를 사용하기 위해 암호 같은 키 조합을 배울 필요가 없다는 것을 의미했습니다. 그들은 단순히 메뉴에서 명령을 선택할 수 있었습니다.

21세기에 IDE는 너무나 흔해져서 다른 영역에서 시장 점유율을 얻고자 하는 회사들에 의해 무료로 제공됩니다. 현대 IDE는 놀라운 기능들로 무장되어 있습니다. 제가 가장 좋아하는 것은 자동화된 리팩터링, 특히 *Extract Method*인데, 여기서 코드 덩어리를 선택해서 메서드로 변환할 수 있습니다. 리팩터링 도구는 메서드에 전달되어야 하는 모든 매개변수를 찾아내서, 코드를 수정하는 것을 극히 쉽게 만들어줍니다. 제 IDE는 심지어 이 메서드로 교체될 수 있는 다른 코드 덩어리들을 감지하고 그것들도 교체하고 싶은지 물어보기까지 합니다.

현대 IDE의 또 다른 놀라운 기능은 회사 내에서 스타일 규칙을 강제할 수 있는 능력입니다. 예를 들어, Java에서 일부 프로그래머들은 모든 매개변수를 final로 만들기 시작했습니다(제 의견으로는 시간 낭비입니다). 하지만 그들이 그런 스타일 규칙을 가지고 있으므로, 제가 그것을 따르기 위해 해야 할 일은 IDE에서 설정하는 것뿐입니다: final이 아닌 매개변수에 대해 경고를 받게 될 것입니다. 스타일 규칙은 또한 가능한 버그를 찾는 데 사용될 수 있는데, 예를 들어 참조 객체로 자동박싱된 기본값에 `==`를 사용하는 것처럼 자동박싱된 객체들을 참조 동등성으로 비교하는 것 같은 경우입니다.

불행히도 현대 IDE는 우리가 그것들을 사용하는 방법을 배우기 위해 노력을 투자하도록 요구하지 않습니다. 제가 처음 Unix에서 C를 프로그래밍했을 때, 가파른 학습 곡선 때문에 vi 편집기가 어떻게 작동하는지 배우는 데 상당한 시간을 보내야 했습니다. 앞서 보낸 이 시간은 수년에 걸쳐 풍성하게 보상받았습니다. 저는 심지어 이 글의 초안도 *vi*로 타이핑하고 있습니다. 현대 IDE는 매우 점진적인 학습 곡선을 가지고 있는데, 이는 우리가 도구의 가장 기본적인 사용법을 넘어서 발전하지 않는 결과를 가져올 수 있습니다.

IDE를 배우는 제 첫 번째 단계는 키보드 단축키를 암기하는 것입니다. 코드를 타이핑할 때 제 손가락들이 키보드에 있으므로, 변수를 인라인하기 위해 *Ctrl+Shift+I*를 누르는 것은 흐름을 깨뜨리지 않고 절약해주는 반면, 마우스로 메뉴를 탐색하는 것으로 전환하는 것은 흐름을 방해합니다. 이런 방해들은 불필요한 컨텍스트 스위치로 이어져서, 모든 것을 게으른 방식으로 하려고 한다면 저를 훨씬 덜 생산적으로 만듭니다. 같은 규칙이 키보드 기술에도 적용됩니다: 터치 타이핑을 배우세요, 앞서 투자한 시간을 후회하지 않을 것입니다.

마지막으로, 프로그래머로서 우리에게는 코드를 조작하는 데 도움이 될 수 있는 시간이 증명된 Unix 스트리밍 도구들이 있습니다. 예를 들어, 코드 리뷰 중에 프로그래머들이 많은 클래스에 같은 이름을 지었다는 것을 알아차렸다면, *find*, *sed*, *sort*, *uniq*, *grep* 같은 도구들을 사용해서 이것들을 매우 쉽게 찾을 수 있습니다:

```
find . -name "*.java" | sed 's/.*\///' | sort | uniq -c | grep -v "^ *1 " | sort -r
```

우리 집에 오는 배관공이 토치를 사용할 수 있기를 기대합니다. IDE로 더 효과적이 되는 방법을 공부하는 데 약간의 시간을 보냅시다.

[Heinz Kabutz](http://programmer.97things.oreilly.com/wiki/index.php/Heinz_Kabutz)가 작성함.