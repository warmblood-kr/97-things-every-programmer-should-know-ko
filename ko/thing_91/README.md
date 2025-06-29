# WET는 성능 병목 지점을 희석시킨다

DRY 원칙(Don't Repeat Yourself)의 중요성은 시스템의 모든 지식 조각이 단일 표현을 가져야 한다는 아이디어를 체계화한다는 것입니다. 다시 말해서, 지식은 단일 구현에 포함되어야 합니다. DRY의 정반대는 WET(Write Every Time)입니다. 지식이 여러 다른 구현에서 체계화될 때 우리의 코드는 WET입니다. DRY 대 WET의 성능 함의는 성능 프로필에 대한 그들의 수많은 효과를 고려할 때 매우 명확해집니다.

우리 시스템의 기능 *X*가 CPU 병목 지점이라고 가정하는 것부터 시작해봅시다. 기능 *X*가 CPU의 30%를 소모한다고 합시다. 이제 기능 *X*가 열 가지 다른 구현을 가지고 있다고 합시다. 평균적으로, 각 구현은 CPU의 3%를 소모할 것입니다. 빠른 성과를 찾고 있다면 이 수준의 CPU 사용률은 걱정할 가치가 없기 때문에, 우리는 이 기능이 우리의 병목 지점이라는 것을 놓칠 가능성이 높습니다. 하지만 우리가 어떻게든 기능 *X*를 병목 지점으로 인식했다고 합시다. 우리는 이제 모든 단일 구현을 찾고 고치는 문제에 직면했습니다. WET로는 우리가 찾고 고쳐야 할 열 가지 다른 구현이 있습니다. DRY로는 30% CPU 사용률을 명확히 보고 고칠 코드가 십분의 일이 있을 것입니다. 그리고 각 구현을 찾아 헤매는 시간을 보낼 필요가 없다는 것을 언급했나요?

우리가 종종 DRY 위반의 죄를 짓는 한 가지 사용 사례가 있습니다: 컬렉션의 사용. 쿼리를 구현하는 일반적인 기법은 컬렉션을 반복하고 나서 각 요소에 차례로 쿼리를 적용하는 것입니다:

```
public class UsageExample {
    private ArrayList<Customer> allCustomers = new ArrayList<Customer>();
    // ...
    public ArrayList<Customer> findCustomersThatSpendAtLeast(Money amount) {
        ArrayList<Customer> customersOfInterest = new ArrayList<Customer>();
        for (Customer customer: allCustomers) {
            if (customer.spendsAtLeast(amount))
               customersOfInterest.add(customer);
        }
        return customersOfInterest;
    }
}
```

이 원시 컬렉션을 클라이언트들에게 노출함으로써, 우리는 캡슐화를 위반했습니다. 이것은 리팩터링할 우리의 능력을 제한할 뿐만 아니라, 우리 코드의 사용자들로 하여금 각자가 잠재적으로 같은 쿼리를 다시 구현하게 함으로써 DRY를 위반하도록 강요합니다. 이 상황은 API에서 노출된 원시 컬렉션들을 제거함으로써 쉽게 피할 수 있습니다. 이 예시에서 우리는 `CustomerList`라고 불리는 새로운, 도메인별 집합 타입을 도입할 수 있습니다. 이 새로운 클래스는 우리 도메인과 의미적으로 더 일치합니다. 그것은 우리의 모든 쿼리들을 위한 자연스러운 홈 역할을 할 것입니다.

이 새로운 컬렉션 타입을 갖는 것은 또한 이런 쿼리들이 성능 병목 지점인지 쉽게 볼 수 있게 해줄 것입니다. 쿼리들을 클래스에 통합함으로써 우리는 `ArrayList`와 같은 표현 선택들을 클라이언트들에게 노출할 필요를 제거합니다. 이것은 클라이언트 계약을 위반할 두려움 없이 이런 구현들을 변경할 자유를 줍니다:

```
public class CustomerList {
    private ArrayList<Customer> customers = new ArrayList<Customer>();
    private SortedList<Customer> customersSortedBySpendingLevel = new SortedList<Customer>();
    // ...
    public CustomerList findCustomersThatSpendAtLeast(Money amount) {
        return new CustomerList(customersSortedBySpendingLevel.elementsLargerThan(amount));
    }
}

public class UsageExample {
    public static void main(String[] args) {
        CustomerList customers = new CustomerList();
        // ...
        CustomerList customersOfInterest = customers.findCustomersThatSpendAtLeast(someMinimalAmount);
        // ...
    }
}
```   

이 예시에서, DRY 준수는 우리가 고객들의 지출 수준을 키로 하는 SortedList로 대안적인 인덱싱 스키마를 도입할 수 있게 해줬습니다. 이 특별한 예시의 구체적인 세부사항보다 더 중요한 것은, DRY를 따르는 것이 코드가 WET였다면 찾기 더 어려웠을 성능 병목 지점을 찾고 수리하는 데 도움이 되었다는 것입니다.

[Kirk Pepperdine](http://programmer.97things.oreilly.com/wiki/index.php/Kirk_Pepperdine)이 작성함.