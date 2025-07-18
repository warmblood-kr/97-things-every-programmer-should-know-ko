# 싱글톤 패턴의 유혹에 저항하라

싱글톤 패턴은 당신의 많은 문제를 해결해줍니다. 하나의 인스턴스만 필요하다는 것을 알고 있습니다. 이 인스턴스가 사용되기 전에 초기화된다는 보장이 있습니다. 전역 접근점을 가짐으로써 설계를 단순하게 유지합니다. 모든 것이 좋습니다. 이 고전적인 디자인 패턴이 마음에 들지 않을 이유가 뭘까요?

사실 꽤 많습니다. 유혹적일 수는 있지만, 경험에 따르면 대부분의 싱글톤은 실제로 도움보다는 해를 더 많이 끼칩니다. 그들은 테스트 가능성을 저해하고 유지보수성을 해칩니다. 불행히도 이런 추가적인 지혜는 그래야 할 만큼 널리 퍼져 있지 않고, 싱글톤은 많은 프로그래머들에게 계속해서 거부할 수 없는 것으로 남아 있습니다. 하지만 저항할 가치가 있습니다:

- 단일 인스턴스 요구사항은 종종 상상입니다. 많은 경우 미래에 추가 인스턴스가 필요하지 않을 것이라는 순전한 추측입니다. 이런 추측적 속성을 애플리케이션의 설계 전반에 방송하는 것은 언젠가 고통을 야기할 수밖에 없습니다. 요구사항은 변할 것입니다. 좋은 설계는 이것을 받아들입니다. 싱글톤은 그렇지 않습니다.

- 싱글톤은 개념적으로 독립적인 코드 단위들 사이에 암시적 의존성을 야기합니다. 이것은 그들이 숨겨져 있고 단위들 사이에 불필요한 결합을 도입하기 때문에 문제가 됩니다. 이 코드 냄새는 느슨한 결합과 실제 구현을 위해 모의 구현을 선택적으로 대체할 수 있는 능력에 의존하는 단위 테스트를 작성하려고 할 때 코가 찡할 정도로 심해집니다. 싱글톤은 그런 간단한 모킹을 방해합니다.

- 싱글톤은 또한 암시적 영속 상태를 갖고 있는데, 이것이 다시 단위 테스트를 저해합니다. 단위 테스트는 테스트들이 서로 독립적이어야 하므로, 테스트들을 어떤 순서로든 실행할 수 있고 모든 단위 테스트 실행 전에 프로그램을 알려진 상태로 설정할 수 있어야 합니다. 가변 상태를 가진 싱글톤을 도입하면, 이것을 달성하기 어려울 수 있습니다. 게다가 그런 전역적으로 접근 가능한 영속 상태는 특히 멀티스레드 환경에서 코드에 대해 추론하기 더 어렵게 만듭니다.

- 멀티스레딩은 싱글톤 패턴에 추가적인 함정들을 도입합니다. 접근에 대한 직접적인 잠금은 그리 효율적이지 않기 때문에, 소위 이중 확인 잠금 패턴(DCLP)이 인기를 얻었습니다. 불행히도 이것은 치명적 매력의 또 다른 형태일 수 있습니다. 많은 언어에서 DCLP가 스레드 안전하지 않고, 그것이 스레드 안전한 곳에서도 여전히 미묘하게 잘못할 기회들이 있다는 것이 밝혀졌습니다.

싱글톤의 정리는 마지막 도전을 제시할 수 있습니다:

- 싱글톤을 명시적으로 죽이는 지원이 없는데, 이것은 일부 상황에서 심각한 문제가 될 수 있습니다. 예를 들어, 플러그인이 모든 객체가 정리된 후에만 안전하게 언로드될 수 있는 플러그인 아키텍처에서 말입니다.

- 프로그램 종료 시 싱글톤의 암시적 정리에는 순서가 없습니다. 이것은 상호 의존성을 가진 싱글톤들을 포함하는 애플리케이션에 문제가 될 수 있습니다. 그런 애플리케이션을 종료할 때, 한 싱글톤이 이미 파괴된 다른 싱글톤에 접근할 수 있습니다.

- 이런 단점들 중 일부는 추가적인 메커니즘을 도입함으로써 극복될 수 있습니다. 하지만 이것은 대안적 설계를 선택함으로써 피할 수 있었던 코드의 추가적인 복잡성의 대가로 옵니다.

따라서 정말로 한 번 이상 인스턴스화되어서는 안 되는 클래스들로 싱글톤 패턴의 사용을 제한하세요. 임의의 코드에서 싱글톤의 전역 접근점을 사용하지 마세요. 대신, 싱글톤에 대한 직접 접근은 잘 정의된 몇 곳에서만 이루어져야 하고, 거기서부터 인터페이스를 통해 다른 코드로 전달될 수 있습니다. 이 다른 코드는 알지 못하므로, 싱글톤이나 다른 어떤 종류의 클래스가 인터페이스를 구현하는지에 의존하지 않습니다. 이것은 단위 테스트를 방해했던 의존성을 깨뜨리고 유지보수성을 향상시킵니다. 그래서 다음에 싱글톤을 구현하거나 접근하는 것을 생각하고 있을 때, 바라건대 당신이 멈춰서 다시 생각하게 될 것입니다.

[Sam Saariste](http://programmer.97things.oreilly.com/wiki/index.php/Sam_Saariste)가 작성함.