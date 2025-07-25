# 프로그래머와 테스터가 협력할 때

테스터와 프로그래머가 협력하기 시작할 때 마법 같은 일이 일어납니다. 결함 추적 시스템을 통해 버그를 주고받는 데 소비되는 시간이 줄어듭니다. 무언가가 정말로 버그인지 새로운 기능인지 알아내려고 노력하는 데 낭비되는 시간이 줄어들고, 고객 기대를 충족하는 좋은 소프트웨어를 개발하는 데 더 많은 시간이 소비됩니다. 코딩이 시작되기 전에도 협력을 시작할 많은 기회들이 있습니다.

테스터들은 Fit(Framework for Integrated Test) 같은 도구를 사용하여 고객들이 그들의 도메인 언어로 수락 테스트를 작성하고 자동화하는 것을 도울 수 있습니다. 이런 테스트들이 코딩이 시작되기 전에 프로그래머들에게 주어지면, 팀은 수락 테스트 주도 개발(ATDD)을 실천하고 있는 것입니다. 프로그래머들은 테스트를 실행하기 위한 픽스처를 작성하고, 그다음 테스트를 통과시키기 위한 코드를 작성합니다. 이런 테스트들은 그 후 회귀 스위트의 일부가 됩니다. 이런 협력이 발생할 때, 기능 테스트들이 일찍 완료되어 더 큰 그림의 엣지 조건이나 워크플로우에 대한 탐색적 테스트를 위한 시간을 허용합니다.

한 걸음 더 나아갈 수 있습니다. 테스터로서, 나는 프로그래머들이 새로운 기능을 코딩하기 시작하기 전에 내 테스트 아이디어들의 대부분을 제공할 수 있습니다. 프로그래머들에게 제안이 있는지 물어볼 때, 그들은 거의 항상 더 나은 테스트 커버리지를 도와주거나 불필요한 테스트에 많은 시간을 소비하는 것을 피하는 데 도움이 되는 정보를 제공합니다. 종종 테스트들이 초기 아이디어들의 많은 것을 명확히 하기 때문에 우리는 결함들을 방지했습니다. 예를 들어, 내가 참여한 한 프로젝트에서, 내가 프로그래머들에게 준 Fit 테스트들은 와일드카드 검색에 응답하기 위한 쿼리의 예상 결과를 보여줬습니다. 프로그래머는 완전한 단어 검색만을 코딩할 완전한 의도를 가지고 있었습니다. 우리는 고객과 이야기하여 코딩이 시작되기 전에 올바른 해석을 결정할 수 있었습니다. 협력함으로써, 우리는 결함을 방지했고, 이것은 우리 둘 모두에게 많은 낭비된 시간을 절약해 주었습니다.

프로그래머들은 또한 성공적인 자동화를 만들기 위해 테스터들과 협력할 수 있습니다. 그들은 좋은 코딩 관행을 이해하고 전체 팀을 위해 작동하는 견고한 테스트 자동화 스위트를 설정하는 데 테스터들을 도울 수 있습니다. 나는 테스트들이 잘못 설계되어서 테스트 자동화 프로젝트들이 실패하는 것을 종종 봤습니다. 테스트들이 너무 많은 것을 테스트하려고 하거나 테스터들이 테스트들을 독립적으로 유지할 수 있을 만큼 기술에 대해 충분히 이해하지 못했습니다. 테스터들은 종종 병목 지점이므로, 프로그래머들이 자동화 같은 작업에서 그들과 함께 일하는 것이 이치에 맞습니다. 아마도 간단한 도구를 제공함으로써 무엇이 일찍 테스트될 수 있는지 이해하기 위해 테스터들과 함께 일하는 것은 프로그래머들에게 또 다른 피드백 사이클을 줄 것이고, 이것은 그들이 장기적으로 더 나은 코드를 전달하는 데 도움이 될 것입니다.

테스터들이 자신들의 유일한 일이 소프트웨어를 망가뜨리고 프로그래머들의 코드에서 버그를 찾는 것이라고 생각하는 것을 멈출 때, 프로그래머들은 테스터들이 '자신들을 잡으려고 한다'고 생각하는 것을 멈추고, 협력에 더 열려 있게 됩니다. 프로그래머들이 자신들이 코드에 품질을 구축하는 것에 책임이 있다는 것을 깨닫기 시작할 때, 코드의 테스트 가능성은 자연스러운 부산물이고, 팀은 더 많은 회귀 테스트들을 함께 자동화할 수 있습니다. 성공적인 팀워크의 마법이 시작됩니다.

[Janet Gregory](http://programmer.97things.oreilly.com/wiki/index.php/Janet_Gregory)가 작성함.