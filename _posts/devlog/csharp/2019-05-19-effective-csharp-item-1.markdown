---
layout: post
title:  "Effective C# 1장 정리 - C# 언어 요소"
subtitle:   "C# 언어 요소"
categories: devlog
tags: csharp
comments: true
---

## ITEM 1: 지역변수를 사용할 때는 var를 사용하라

---

### **타입을 명시적으로 드러내지 않는 경우라면 var를 사용하는 것이 좋다.**

```C#
    IEnumerable<string> q =
    	from c in db.Customers
    	select c.ContactName;
    
    var q2 = q.Where(s => s.StartsWith(start));

    return q2;
```

q를 var로 받지 않을경우, `IQueryable<string>`을 반환해야 하지만 상위객체인 IEnumerable로 반환하게 되어 Where 구문에서 성능이 저하되게 된다.

반대로 q를 var로 받았을 경우에는 IQueryable를 반환하게 되어 성능저하가 발생하지 않게 된다.

### **내장 숫자 타입(int, float, double등)을 선언할 때는 명시적으로 타입을 선언하는것이 좋다.**

- var를 사용할 경우 정밀도와 관련된 문제를 유발할 가능성이 높다.
- var total = 100 * GetMagicNumber() / 6;

## ITEM 2: const보다는 readonly가 좋다

---

### **컴파일타임 상수( const )**

- 컴파일 타임에 **변수**가 **값**으로 변환된다.

    public const int Millennium = 2000;
    if (myDateTime.Year == Millennium) -> if(myDateTime.Year == 200)

- **내장된 숫자형, enum, string, null**에 대해서만 사용 가능..
- **컴파일 할때 사용되는** **상숫값**을 정의할땐 반드시 **const**를 사용
- **선택적 매개변수에 대한 기본값은 const**의 형태로 저장되므로 값을 변경할때 신중하게 접근해야함.
- readonly보다 **성능**이 빠르긴 하지만 미미하고, 유연성이 낮음.

### **런타임 상수( readonly )**

- **런타임**에 값이 평가된다.
- **생성자**에서 초기화 가능, **어떤 타입**도 함께 사용할 수 있다.
- const는 값이 바뀌면 응용프로그램 전체를 재빌드를 해야하지만, readonly는 **바뀐파일만 배포**할 수 있다.

## ITEM 3: 캐스트보다는 is, as가 좋다.

---

### **캐스트연산**

- **형변환 연산자**가 개입될 수 있다.
- 사용자가 상황에 맞게 형변환 연산자를 정의 해줘야한다.

### **is,as 연산**

- 사용자 정의 형변환은 수행불가
- 형변환 과정에서 **새로운 객체 생성하지 않음**
- value 타입은 as를 사용할 수 없다.

    → as를 이용하되, nullable 타입으로 형변환을 수행한 후 null인지 확인하기

        object o = Factory.GetValue();
        var i = o as int ?;
        if(i != null)
        	Console.WriteLine(i.Value);

- is 연산자는 **다형성**을 준수하기 때문에 정확한 객체의 타입을 가져오고 싶으면 GetType() 메서드를 이용해야한다.

### **일반적인 예 ( 첫번째 코드가 훨씬 보기 좋다 )**

    // as 연산
    object o = Factiory.GetObject();
    MyType t = o as MyType;
    
    if( t != null)
    {
    }
    else 
    {
    }
    
    // 캐스트 연산
    object o = Factory.GetObject();
    try
    {
    	MyType t;
    	t = (MyType)o;
    }
    catch(InvalidCastException)
    {
    }

**형변환이 불가피한경우 사용자의 의도를 명확히 표현할 수 있는 is나 as를 사용하자!**

## ITEM 4: string.Format()을 보간 문자열로 대체하라

---

### **보간 문자열의 장점**

1. 코드 **가독성**이 대폭 향상
2. **정적 타입 검사**를 수행하기 때문에 개발자의 실수를 미연에 방지
3. 문자열을 생성하기 위한 **표현식**이 더 풍성하다.

### **사용법**

    // 앞에 $를 붙이고 표현식을 {}안에 둔다.
    Console.WriteLine($"The value of pi is {Math.PI}");
    
    // 원하는 포매팅을 위한 추가적 인자 전달
    Console.WriteLine($"The value of pi is {Math.PI.ToString("F2")}");
    
    // :을 이용해도 가능
    Console.WriteLine($"The value of pi is {Math.PI:F2}");
    
    // @를 넣고 ()를 사용해 ':' 가 조건연산자임을 알려줄 수 있다..
    Console.WriteLine($@"THe value of pi is {(round ?
    		Math.PI.ToString() : Math.PI.ToString("F2"))}");
    
    // ?. 연산자와 ?? 연산자도 사용가능!
    Console.WriteLine($"The customer's name is {c?.Name ?? "Name is missing"}");

---

## ITEM 5: 문화권 별로 다른 문자열을 생성하려면 FormattableString을 사용하라

- 문자열 보간을 사용하여 문자열을 만들면 반환값이 **문자열**일수도, **FormattableString**을 상속한 타입일 수도 있다.
- FormattableString을 사용하면 현재 컴퓨터에 지정된 **문화권을 고려하여 문자열을 생성**할 수 있다.
- [Example]문화권과 언어를 지정하여 문자열 생성하는 방법

    // 독일문화권으로.
    public static string ToGerman(FormattableString src)
    {
    		return string.Format(
            System.Globalization.CultureInfo.CreateSpecificCulture("de-de"),
            src.Format, src.GetArguments());
    }

## ITEM 6: nameof() 연산자를 적극 활용하라

---

- 항상 **로컬 이름**을 문자열로 반환하는 역할을 수행한다.
- **심볼의 이름**을 평가하며, 타입, 변수, 인터페이스, 네임스페이스에 대하여 사용할 수 있다.
- 심볼의 이름을 바꾸거나 수정할때도 손쉽게 변경 사항을 반영할 수 있다.

[Example] - 예외 타입에 하드코딩대신 nameof()를 사용하면 rename을 해도 바로 적용가능.

    public static void ExceptionMessage(object thisCantBeNull)
    {
    		if(thisCantBeNull == null)
    			throw new ArgumentNullException(nameof(thisCantBeNull),
    					"We told you this cant be null!");
    }

## ITEM 7: 델리게이트를 이용하여 콜백을 표현하라

---

- 델리게이트를 이용하면 타입 안정적인 콜백을 정의할 수 있다.
- .NET Framwork 라이브러리는 Predicate<T>, Acton<>, Func<> 와 같은 형태로 자주 사용되는 델리게이트를 정의해두고 있다.
- **[멀티캐스트](https://docs.microsoft.com/ko-kr/dotnet/api/system.multicastdelegate?view=netframework-4.8)**가 가능하다.

## ITEM 8: 이벤트 호출 시에는 null 조건 연산자를 사용하라

---

C# 6.0에 새롭게 추가된 null 조건 연산자를 고전적인 null check방식 대신 사용하자.

    // 구식적인 방법. Updated가 null이 아니여서 if 구문에 들어올때,
    // 다른 스레드에서 이벤트 핸들러를 취소할경우 NullReferenceException이 발생.
    public void RaiseUpdates()
    {
    		counter++;
    		if(Updated != null)
    			Updated(this, counter);
    }
    
    // NEW!: null 조건 연산자를 이용하면 멀티스레딩 환경에도 안전하다.
    public void RaiseUpdates()
    {
    		counter++;
    		Updated?.Invoke(this, counter);
    }

## ITEM 9: 박싱과 언박싱을 최소화하라

---

- 박싱과 언박싱은 성능에 좋지 않은 영향을 미친다.
- 수행하는 과정에서 임시객체가 생성되는데, 이로 인해 버그가 발생할 수도 있다.
- 박싱은 값 타입을 참조 타입으로 변경한다.

### Example

    Console.WriteLine($"A few numbers:{firstNumber}, {secondNumber}");
    
    // -> firstNumber가 나오는 과정
    int i = 25;
    object o = i;
    Console.WriteLine(o.ToString();
    
    // .ToString() 메서드로 박싱을 피할 수 있다
    Console.WriteLine($"A few numbers:{firstNumber.ToString()}, {secondNumber.ToString()");

- .NET 1.x의 컬렉션 사용을 피하고, .NET 2.0의 제네릭 컬렉션을 사용하여 박싱/언박싱을 피하자.

## ITEM 10: 베이스 클래스가 업그레이드된 경우에만 new 한정자를 사용하라

---

- 베이스 클래스에서 이미 사용하고 있는 메서드를 재정의하여 완전히 새로운 베이스 클래스를 만들어야 하는경우에 new한정자를 사용
- new 한정자를 사용할땐 매우 신중히 고려하고 사용하자.

**사용법**

    public class MyClass
    {
    	public void MagicMethod()
    	{
    	}
    }
    
    public class MyOhterClass : MyClass
    {
    	// MagicMethod를 재정의
    	public new void MagicMethod()
    	{
    	}
    }