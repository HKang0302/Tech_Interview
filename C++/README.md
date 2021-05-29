# C++
수업 자료와 구글링 자료를 참고로 작성하였습니다.
</br><br>
## 목차
#### [용어 정리](#용어-정리)
#### [객체 지향 프로그래밍](#객체-지향-프로그래밍)
#### [Extra](#Extra)
</br><br>

## 용어 정리
* **선언(declaration)**: 객체의 타입과 이름을 compiler에게 알려주는 것
* **정의(definition)**: 객체의 의미나 행동 부여
* **참조자(reference, &)**: 
  * 다른 객체의 reference 역할로써, initialized 되어야함.
  * 실행 중간에 다른 reference로 변환이 불가능함
```
int x = 1;
int& r = x; // x의 reference
cout << r << endl; // 1
r++;
cout << x << endl; // 2
```
* **const**: reference의 매개변수가 코드 실행 중 변하지 않도록 고정시키는 키워드
* **static**: 지역 변수든 전역 변수든간에 한번 static으로 선언이 되면 프로그램 종료 시까지 static storage memory에 남아 사라지지 않음
```
int printStatic(){
    static int i = 0;
    i++;
    return i;
}
void staticTest(){
    cout << printStatic() << endl; // 1
    cout << printStatic() << endl; // 2
}
```
<br></br>
## 객체 지향 프로그래밍
*<span style="color: gray">처음 질문으로 객체지향 프로그래밍이 뭔지 질문하는 경우가 있음. 가장 간단한 질문이며 꼬리질문의 시작을 알리는 것이니 제대로 이해하고 가는 것이 중요!</span>*<br><br>
프로그래밍에 필요한 데이터를 <span style = "color:red">**추상화**</span>시켜 상태와 행위를 가진 객체를 만들고 객체들간의 유기적인 상호작용을 이용하여 로직을 구성하는 프로그래밍 방법.<br>
>예를 들어 <span style="color: orange">"바나나"</span>라는 클래스가 있다고 하면 우리는 개념적으로 <span style="color: orange">바나나</span>가 갖고 있는 특징들을 떠올릴 수 있습니다. 껍질은 노란색이고 속은 하얗고 맛은 달고 길쭉한 모양이라는 특징들을요.<br> 
하지만 실제로 <span style="color: blue">바나나</span>를 먹기 위해서는 마트에 가서 진열대에 놓여있는 실제의 <span style="color: blue">"바나나(object)"</span> 사와야 합니다.<br> 
마트 직원에게 "<span style="color: orange">바나나</span> 어디 있나요?" 라고 물어볼 때 마트 직원이 안내를 해 줄 수 있는 것은 나와 마트 직원이 모두 <span style="color: orange">바나나</span>라는 추상적인 개념을 알고 있기 때문에 가능한 것입니다.<br> 
진열대에는 <span style="color: blue">바나나</span>가 여러 개 있을 수 있죠. 그 중에 내가 어떤 <span style="color: blue">바나나</span>를 사서 먹었다면 그 <span style="color: blue">바나나</span>는 다른 <span style="color: blue">바나나</span>들과 구별되는 유일한 실체입니다.<br><br>
위 예문에서 글씨색으로 클래스와 객체를 구분해놓았는데 차이를 아시겠지요?<br>
<span style="color: orange">개(dog)</span>라는 클래스가 있다면 우리집 강아지 <span style="color: blue">로이</span>, 옆집 강아지 <span style="color: blue">초코</span>는 객체인 것이죠.<br>
*출처: https://gracefulprograming.tistory.com/130 [Peter의 우아한 프로그래밍]*

**절차 지향 프로그래밍**(복잡한 logic이 필요한 프로그래밍에는 맞지 않은 방식(e.g. C언어))과는 달리 복잡한 logic에 사용이 용이함<br>
#### 특징:
* **Bottom-up** 방식으로 작은 단위의 문제를 해결할 수 있는 객체를 만든 뒤, 여러 작은 단위의 객체들을 이용하여 큰 문제를 해결하는 것을 반복하는 컴퓨터 패러다임
* **코드 재사용 용이:** 남이 만든 코드나 부모로부터 상속받은 class를 사용하여 확장 가능
* **유지 보수 용이:** 절차 지향 프로그래밍의 경우, 수정이 필요하면 일일히 다 찾아가서 수정해야하지만, 객체 지향 프로그래밍의 경우에는 class에 멤버 변수/method로 되어있어서 해당 부분만 수정하면 됨
#### 키워드:
1. **클래스 + 인스턴스(객체)**<br>**class**: 데이터를 만들기 위해 추상화를 거쳐 상태나 행위를 변수와 method로 정의한 것<br>**instance**: 클래스에 정의된 객체를 기반으로 실제 메모리에 할당되는 데이터
2. **추상화**: 불필요한 정보는 숨기고 필요한 정보만 표현해서 공통의 속성이나 기능을 묶어 이름으로 표현하는 것 (class)
#### 3요소:
* **캡슐화(Encapsulation)**: 여러 객체의 속성과 행위를 하나의 class로 묶어서 코드 수정 없이 분류하도록 하고 외부에서 내부 데이터로의 접근을 제어할 수 있게 함(정보 은닉)<br><br>
 **접근지정자:** class나 구조체(struct)에서 외부에서 내부로의 접근이나 자식 class로의 접근을 제어하는 키워드
  * class 기본 지정자: `private`, struct 기본 지정자: `public`

    |  | 자기 접근 | 자식 접근 | 외부 접근 |   
    | :--: | :--------: | :--: | :--: |
    |public|O|O|O|
    |protected|O|O|X|
    |private|O|X|X|
  * 상속 시 생기는 자식 class 내의 접근 지정자의 변화
 
    |                  | public 상속 |protected 상속| privated 상속|
    |:----------------:|:----------:|:------------:|:------------:|
    |**public 부모**   |public       | protected   |  private     |
    |**protected 부모**|protected    | protected   |  private     |
    |**private 부모**  |접근 불가     | 접근 불가    |   접근 불가   |

    예시) 아래 코드에서 B class 내부의 p의 접근 제어자는 protected로 변경됨
    ```
    class A{
        public:
            int p = 0;
        ...
    }
    class B: protected A{
        ...
    }
    ```
* **다형성(Polymorphism)**: 하나의 객체가 여러 형태를 가질 수 있어 사용이 편리하도록 함
  * **오버 라이딩(Overriding):** 자식 class는 부모 class로부터 객체의 이름, 타입, 값을 상속받게되는데 자식 class 내에서 재정의하는 것  
  * **오버 로딩(Overloading):** 같은 함수의 이름을 가지고 있으나 매개변수, 리턴 타입 등의 특징을 다르게 하여 다른 역할을 제공하는 함수를 생성하는 것
* **상속(Inheritance)**: 앞서 언급한 듯, 상위 클래스(부모 클래스)의 특징을 하위 클래스(자식 클래스)에서 물려받아 <ins>재사용</ins>하면서 더 필요한 속성을 <ins>확장</ins>할 수 있는 특징을 가짐

## Extra
*그냥 내가 정리하고 싶어서 사용하는 파트*
#### `using namespace`를 사용하지 않는 것이 좋은 이유
예를 들어 `using namespace A`, `using namespace B`를 선언했다고 하자. 만일 A와 B 라이브러리에 모두 Foo()라는 function이 있다면 코드 내에서 `FOO();`를 사용하였을때 A인지 B인지를 알 수 없기때문에 디버깅에 문제가 생긴다.</br>
따라서, 최대한 `using namespace A`를 사용하지 않고 `A::Foo()`라고 사용하는 것이 좋다.
</br><br>

