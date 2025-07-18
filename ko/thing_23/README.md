# 도메인 특화 언어

체스 플레이어, 유치원 교사, 또는 보험 대리인 등 어떤 도메인의 전문가들의 토론을 들어보면, 그들의 어휘가 일상 언어와 상당히 다르다는 것을 알게 될 것입니다. 그것이 도메인 특화 언어(DSL)가 무엇인지에 대한 일부입니다: 특정 도메인은 그 도메인에 특별한 것들을 설명하기 위한 특화된 어휘를 가지고 있습니다.

소프트웨어 세계에서, DSL은 제한된 어휘와 문법을 가진 도메인에 특화된 언어로 된 실행 가능한 표현에 관한 것으로, 도메인 전문가가 읽을 수 있고, 이해할 수 있으며, — 바라건대 — 작성할 수 있습니다. 소프트웨어 개발자나 과학자를 대상으로 한 DSL은 오랫동안 존재해 왔습니다. 예를 들어, 구성 파일에서 발견되는 Unix의 '작은 언어들'과 LISP 매크로의 힘으로 만들어진 언어들이 더 오래된 예들 중 일부입니다.

DSL은 일반적으로 *내부* 또는 *외부*로 분류됩니다:

- **내부 DSL**은 범용 프로그래밍 언어로 작성되지만 그 구문이 자연어처럼 보이도록 구부러집니다. 이는 더 많은 구문적 설탕과 포맷팅 가능성을 제공하는 언어들(예: Ruby와 Scala)에서는 더 쉽지만, 그렇지 않은 언어들(예: Java)에서는 더 어렵습니다. 대부분의 내부 DSL은 기존 API, 라이브러리, 또는 비즈니스 코드를 감싸고 기능에 대한 덜 정신적으로 구부러진 접근을 위한 래퍼를 제공합니다. 그들은 단순히 실행함으로써 직접 실행 가능합니다. 구현과 도메인에 따라, 데이터 구조를 구축하고, 의존성을 정의하고, 프로세스나 작업을 실행하고, 다른 시스템과 통신하거나, 사용자 입력을 검증하는 데 사용됩니다. 내부 DSL의 구문은 호스트 언어에 의해 제약됩니다. 호스트 언어를 당신의 DSL로 구부리는 데 도움이 될 수 있는 많은 패턴들 — 예를 들어, 표현 빌더, 메서드 체이닝, 주석 — 이 있습니다. 호스트 언어가 재컴파일을 요구하지 않는다면, 내부 DSL은 도메인 전문가와 나란히 작업하면서 꽤 빠르게 개발될 수 있습니다.

- **외부 DSL**은 언어의 텍스트적 또는 그래픽적 표현입니다 — 비록 텍스트적 DSL이 그래픽적인 것보다 더 일반적인 경향이 있지만. 텍스트적 표현은 렉서, 파서, 모델 변환기, 생성기, 그리고 다른 유형의 후처리를 포함하는 도구 체인에 의해 처리될 수 있습니다. 외부 DSL은 대부분 추가 처리의 기초를 형성하는 내부 모델로 읽어집니다. 문법을 정의하는 것이 도움이 됩니다(예: EBNF로). 문법은 도구 체인의 일부를 생성하기 위한 시작점을 제공합니다(예: 편집기, 시각화기, 파서 생성기). 간단한 DSL의 경우, 예를 들어 정규 표현식을 사용한 수제 파서로 충분할 수 있습니다. 커스텀 파서는 너무 많은 것을 요구받으면 다루기 어려워질 수 있으므로, 언어 문법과 DSL로 작업하기 위해 특별히 설계된 도구들을 살펴보는 것이 의미가 있습니다 — 예: openArchitectureWare, ANTlr, SableCC, AndroMDA. 외부 DSL을 XML 방언으로 정의하는 것도 꽤 일반적입니다. 비록 가독성이 종종 문제가 되지만 — 특히 비기술적 독자들에게는.

DSL의 대상 독자를 항상 고려해야 합니다. 그들이 개발자, 관리자, 비즈니스 고객, 또는 최종 사용자입니까? 언어의 기술적 수준, 사용 가능한 도구, 구문 도움(예: 인텔리센스), 조기 검증, 시각화, 그리고 표현을 의도된 독자에 맞게 조정해야 합니다. 기술적 세부사항을 숨김으로써, DSL은 개발자의 도움을 요구하지 않고 시스템을 그들의 필요에 맞게 적응시킬 수 있는 능력을 줌으로써 사용자들에게 권한을 부여할 수 있습니다. 또한 초기 언어 프레임워크가 자리잡은 후 작업의 잠재적 분배 때문에 개발을 가속화할 수도 있습니다. 언어는 점진적으로 진화할 수 있습니다. 기존 표현과 문법에 대한 다른 마이그레이션 경로들도 사용 가능합니다.

[Michael Hunger](http://programmer.97things.oreilly.com/wiki/index.php/Michael_Hunger)가 작성함.