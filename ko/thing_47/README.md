# 다음 커밋을 알아라

저는 세 명의 프로그래머 어깨를 두드리며 무엇을 하고 있는지 물어봤습니다. "이 메서드들을 리팩터링하고 있어요"라고 첫 번째가 답했습니다. "이 웹 액션에 몇 가지 매개변수를 추가하고 있어요"라고 두 번째가 답했습니다. 세 번째는 "이 사용자 스토리를 작업하고 있어요"라고 답했습니다.

처음 두 명은 작업의 세부사항에 몰두하고 있는 반면 세 번째만이 큰 그림을 볼 수 있고, 후자가 더 나은 집중력을 가지고 있는 것처럼 보일 수 있습니다. 하지만 언제 그리고 무엇을 커밋할 것인지 물어봤을 때, 상황이 극적으로 바뀌었습니다. 처음 두 명은 어떤 파일들이 관련될 것인지 꽤 명확했고 한 시간 정도 내에 끝날 것이라고 했습니다. 세 번째 프로그래머는 "아, 아마 며칠 내에 준비될 것 같아요. 아마 몇 개의 클래스를 추가하고 그 서비스들을 어떤 방식으로든 변경할 것 같아요"라고 답했습니다.

처음 두 명은 전체적인 목표에 대한 비전이 부족하지 않았습니다. 그들은 생산적인 방향으로 이끈다고 생각하는 작업을 선택했고, 몇 시간 내에 끝낼 수 있는 것들이었습니다. 그 작업들을 끝내고 나면, 그들은 작업할 새로운 기능이나 리팩터링을 선택할 것입니다. 작성된 모든 코드는 따라서 명확한 목적과 제한적이고 달성 가능한 목표를 염두에 두고 이루어졌습니다.

세 번째 프로그래머는 문제를 분해할 수 없었고 모든 측면을 한 번에 작업하고 있었습니다. 그는 무엇이 필요할지 아이디어가 없었고, 기본적으로 추측 프로그래밍을 하며 커밋할 수 있는 어떤 지점에 도착하기를 희망하고 있었습니다. 이 긴 세션 시작에 작성된 코드는 아마도 끝에 나온 해결책과 잘 맞지 않을 것입니다.

처음 두 프로그래머가 작업이 두 시간 이상 걸린다면 어떻게 할까요? 너무 많이 맡았다는 것을 깨달은 후, 그들은 아마도 변경사항을 버리고, 더 작은 작업들을 정의하고, 다시 시작할 것입니다. 계속 작업하는 것은 집중력이 부족하고 추측 코드가 저장소에 들어가게 할 것입니다. 대신, 변경사항은 버려지지만 통찰력은 유지됩니다.

세 번째 프로그래머는 계속 추측하고 필사적으로 자신의 변경사항을 커밋할 수 있는 무언가로 짜맞추려고 할 수도 있습니다. 결국, 해온 코드 변경사항을 버릴 수는 없습니다 — 그것은 낭비된 작업이 될 테니까요, 안 그렇나요? 불행히도, 코드를 버리지 않는 것은 명확한 목적이 부족한 약간 이상한 코드가 저장소에 들어가게 합니다.

어느 시점에서 커밋 중심 프로그래머들조차 두 시간 내에 끝낼 수 있다고 생각하는 유용한 무언가를 찾는 데 실패할 수도 있습니다. 그러면, 그들은 직접 추측 모드로 들어가서 코드를 가지고 놀고, 물론 어떤 통찰력이 그들을 다시 궤도에 올려놓을 때마다 변경사항을 버릴 것입니다. 이런 겉보기에 구조화되지 않은 해킹 세션들조차 목적이 있습니다: 생산적인 단계를 구성할 작업을 정의할 수 있도록 코드에 대해 배우는 것입니다.

다음 커밋을 알아두세요. 끝낼 수 없다면, 변경사항을 버리고, 얻은 통찰력으로 믿을 수 있는 새로운 작업을 정의하세요. 필요할 때마다 추측적 실험을 하되, 알아차리지 못한 채 추측 모드로 빠지지 마세요. 추측 작업을 저장소에 커밋하지 마세요.

[Dan Bergh Johnsson](http://programmer.97things.oreilly.com/wiki/index.php/Dan_Bergh_Johnsson)이 작성함.