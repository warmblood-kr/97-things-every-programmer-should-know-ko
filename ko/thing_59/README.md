# 다형성을 위한 놓친 기회들

다형성은 객체지향의 근본이 되는 위대한 아이디어 중 하나입니다. 그리스어에서 가져온 이 단어는 많은(*poly*) 형태(*morph*)를 의미합니다. 프로그래밍의 맥락에서 다형성은 특정 클래스의 객체나 메서드의 많은 형태를 가리킵니다. 하지만 다형성은 단순히 대안적 구현에 관한 것이 아닙니다. 신중하게 사용된다면, 다형성은 장황한 *if-then-else* 블록의 필요 없이 작업할 수 있게 해주는 작고 지역화된 실행 컨텍스트를 만듭니다. 컨텍스트 안에 있다는 것은 우리가 올바른 일을 직접 할 수 있게 해주는 반면, 그 컨텍스트 밖에 있다는 것은 올바른 일을 할 수 있도록 그것을 재구성하도록 강요합니다. 대안적 구현의 신중한 사용으로, 우리는 더 읽기 쉬운 적은 코드를 생산하는 데 도움이 될 수 있는 컨텍스트를 포착할 수 있습니다. 이것은 다음과 같은 (비현실적으로) 간단한 장바구니 코드로 가장 잘 설명됩니다:

```
public class ShoppingCart {
    private ArrayList<Item> cart = new ArrayList<Item>();
    public void add(Item item) { cart.add(item); }
    public Item takeNext() { return cart.remove(0);  }
    public boolean isEmpty() { return cart.isEmpty(); }
}
```

우리 웹샵이 다운로드할 수 있는 아이템과 배송이 필요한 아이템을 제공한다고 해봅시다. 이러한 작업을 지원하는 다른 객체를 만들어봅시다:

```
public class Shipping {
    public boolean ship(Item item, SurfaceAddress address) { ... }
    public boolean ship(Item item, EMailAddress address) { ... }
}
```

고객이 체크아웃을 완료했을 때 상품을 배송해야 합니다:

```
while (!cart.isEmpty()) {
    shipping.ship(cart.takeNext(), ???);
}
```

*???* 매개변수는 새로운 멋진 엘비스 연산자가 아니라, 아이템을 이메일로 보낼지 일반 우편으로 보낼지 물어보는 것입니다. 이 질문에 답하는 데 필요한 컨텍스트가 더 이상 존재하지 않습니다. 배송 방법을 boolean이나 enum으로 포착한 다음 *if-then-else*를 사용해서 누락된 매개변수를 채울 수 있습니다. 다른 솔루션은 둘 다 Item을 확장하는 두 개의 클래스를 만드는 것입니다. 이것들을 DownloadableItem과 SurfaceItem이라고 부릅시다. 이제 코드를 작성해봅시다. Item을 단일 메서드인 ship을 지원하는 인터페이스로 승격시키겠습니다. 장바구니의 내용을 배송하기 위해, `item.ship(shipper)`를 호출할 것입니다. `DownloadableItem`과 `SurfaceItem` 클래스 둘 다 ship을 구현할 것입니다.

```
public class DownloadableItem implements Item {
    public boolean ship(Shipping shipper) {
        shipper.ship(this, customer.getEmailAddress());
    }
}

public class SurfaceItem implements Item {
    public boolean ship(Shipping shipper) {
        shipper.ship(this, customer.getSurfaceAddress());
    }
}
```

이 예에서 우리는 `Shipping`과 작업하는 책임을 각 Item에 위임했습니다. 각 아이템은 어떻게 가장 잘 배송되는지 알고 있으므로, 이 배치는 *if-then-else*의 필요 없이 일을 진행할 수 있게 해줍니다. 코드는 또한 종종 잘 어울리는 두 패턴의 사용을 보여줍니다: Command와 Double Dispatch. 이러한 패턴의 효과적인 사용은 다형성의 신중한 사용에 의존합니다. 그렇게 될 때 우리 코드의 *if-then-else* 블록 수가 감소할 것입니다.

다형성 대신 *if-then-else*를 사용하는 것이 훨씬 더 실용적인 경우들이 있지만, 더 다형적인 코딩 스타일이 더 작고, 더 읽기 쉽고, 덜 취약한 코드 베이스를 산출하는 경우가 더 많습니다. 놓친 기회의 수는 우리 코드의 *if-then-else* 문의 간단한 개수입니다.

[Kirk Pepperdine](http://programmer.97things.oreilly.com/wiki/index.php/Kirk_Pepperdine)이 작성함.