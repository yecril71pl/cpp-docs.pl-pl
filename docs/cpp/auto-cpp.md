---
title: Auto (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6721aa5860f23025b8b6c762cc7e5f4d6178228d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="auto-c"></a>Auto (C++)
Deduces typ zadeklarowanej zmiennej w jej wyrażeniu inicjowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>Uwagi  
 `auto` — Słowo kluczowe nakazuje kompilatorowi Używanie wyrażenia inicjowania zadeklarowana zmienna lub parametr wyrażenia lambda, można wywnioskować jej typu.  
  
 Firma Microsoft zaleca użycie `auto` — słowo kluczowe w większości sytuacji — o ile konwersji na pewno chcesz — ponieważ zapewnia następujące korzyści:  
  
-   **Niezawodność:** zmiana typu wyrażenia — dotyczy to również typ zwracany funkcji zostanie zmieniona — po prostu działa.  
  
-   **Wydajność:** jest zagwarantować, że nie będzie istnieć bez konwersji.  
  
-   **Użyteczność:** nie trzeba martwić trudności pisownię nazwy typu i błędów.  
  
-   **Wydajność:** kodowania może być skuteczniejsza.  
  
 Konwersja przypadków, w których nie można użyć `auto`:  
  
-   Gdy ma określony typ i niczego poza będzie wykonywać.  
  
-   Wyrażenie szablonu pomocnika typów — na przykład `(valarray+valarray)`.  
  
 Aby użyć `auto` — słowo kluczowe, użyj jej zamiast typu do zadeklarowania zmiennej i określ wyrażenie inicjowania. In Addition, można zmodyfikować `auto` — słowo kluczowe przy użyciu Specyfikatory i deklaratorów, takich jak `const`, `volatile`, wskaźnika (`*`), odwołanie (`&`), a odwołania do wartości `(&&`). Kompilator oblicza wyrażenie inicjowania, a następnie używa tych informacji do ustalenia typu zmienną.  
  
 Wyrażenia inicjowania może być przypisanie (znak równości składni), bezpośredniego inicjowania (składnia stylu funkcji), [nowy operator](new-operator-cpp.md) wyrażenia lub wyrażenia inicjowania może być  *dla zakresu deklaracja* parametru w [opartej na zakresie — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md) instrukcji. Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i przykładów kodu w dalszej części tego dokumentu.  
  
 `auto` — Słowo kluczowe jest symbolem zastępczym dla typu, ale nie jest samego typu. W związku z tym `auto` — słowo kluczowe nie można używać w rzutowania lub operatory takich jak [sizeof](../cpp/sizeof-operator.md) i [typeid](../windows/typeid-cpp-component-extensions.md).  
  
## <a name="usefulness"></a>Przydatność  
 `auto` — Słowo kluczowe to prosty sposób zadeklarować zmiennej o typie skomplikowane. Na przykład można użyć `auto` Aby zadeklarować zmienną, w którym wyrażenie inicjujące obejmuje szablony, wskaźniki do funkcji lub wskaźniki do elementów członkowskich.  
  
 Można również użyć `auto` Aby zadeklarować i zainicjuj zmienną do wyrażenia lambda. Nie można zadeklarować typu zmiennej samodzielnie, ponieważ typ wyrażenia lambda jest znany tylko do kompilatora. Aby uzyskać więcej informacji, zobacz [przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md).  
  
## <a name="trailing-return-types"></a>Końcowe zwracane typy  
 Można użyć `auto`, wraz z `decltype` specyfikator, aby zapisać szablon biblioteki typu. Użyj `auto` i `decltype` do zadeklarowania funkcji szablonu, którego zwracany typ zależy od typów argumentów szablonu. Lub użyj `auto` i `decltype` do zadeklarowania funkcji szablonu, który opakowuje wywołania do innej funkcji, a następnie zwraca niezależnie od jest zwracany typ tej innych funkcji. Aby uzyskać więcej informacji, zobacz [decltype](../cpp/decltype-cpp.md).  
  
## <a name="references-and-cv-qualifiers"></a>Referencje i kwalifikatorów cv  
 Należy pamiętać, że przy użyciu `auto` porzuca odwołań, kwalifikatorów const i nietrwałe kwalifikatorów. Rozważmy następujący przykład:  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 W poprzednim przykładzie myAuto jest nie odwołanie int, int, dlatego dane wyjściowe `11 11`, a nie `11 12` jako byłoby, jeśli kwalifikator odwołanie nie ma został porzucony podczas `auto`.  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>Wnioskowanie typu z inicjatorami w nawiasach klamrowych (C ++ 14)  
 Następujące exmample kod pokazuje, jak zainicjować zmiennej automatycznie za pomocą nawiasów klamrowych. Różnice między B i C i między A i e  
  
```cpp  
#include <initializer_list>  
  
int main()  
{  
    // std::initializer_list<int>  
    auto A = { 1, 2 };  
  
    // std::initializer_list<int>  
    auto B = { 3 };  
  
    // int  
    auto C{ 4 };  
  
    // C3535: cannot deduce type for 'auto' from initializer list'  
    auto D = { 5, 6.7 };  
  
    // C3518 in a direct-list-initialization context the type for 'auto'  
    // can only be deduced from a single initializer expression  
    auto E{ 8, 9 };  
  
    return 0;  
}  
```  
  
## <a name="restrictions-and-error-messages"></a>Ograniczenia i komunikaty o błędach  
 W poniższej tabeli wymieniono ograniczenia dotyczące stosowania `auto` — słowo kluczowe i odpowiednie diagnostycznych komunikatu o błędzie kompilator emituje.  
  
|Numer błędu|Opis|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|`auto` — Słowo kluczowe nie można łączyć z jakimkolwiek innym specyfikatorem typu.|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, który jest zadeklarowana za pomocą `auto` — słowo kluczowe musi mieć inicjator.|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Niepoprawnie użyte `auto` — słowo kluczowe, aby zadeklarować typu. Na przykład zadeklarowany typ zwracany metody lub tablicy.|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Nie można zadeklarować argument parametru lub szablonu ze `auto` — słowo kluczowe.|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Nie można zadeklarować parametru metody lub szablonu ze `auto` — słowo kluczowe.|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Nie można używać symbolu, przed zainicjowaniem. W praktyce oznacza to, że zmienna nie może służyć do zainicjowania.|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nie można rzutować na typ, który jest zadeklarowana za pomocą `auto` — słowo kluczowe.|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Wszystkie symbole na liście deklaratorów, która jest zadeklarowana za pomocą `auto` — słowo kluczowe musi zostać rozpoznany tego samego typu. Aby uzyskać więcej informacji, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md) i [typeid](../windows/typeid-cpp-component-extensions.md) operatorów nie można zastosować do symbol, który jest zadeklarowana za pomocą `auto` — słowo kluczowe.|  
  
## <a name="examples"></a>Przykłady  
 Te fragmenty kodu zilustrować niektóre sposoby, w którym `auto` można użyć słowa kluczowego.  
  
 Następujące deklaracje są równoważne. W pierwszej instrukcji zmiennej `j` został zadeklarowany jako typ `int`. W instrukcji drugiej zmiennej `k` jest ustalane na typ `int` ponieważ wyrażenia inicjowania (0) jest liczbą całkowitą.  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 Następujące deklaracje są równoważne, ale druga deklaracja jest łatwiejsze niż w pierwszym. Jedną z najbardziej atrakcyjnych przyczyn, aby użyć `auto` — słowo kluczowe jest prostota.  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 Poniższy fragment kodu deklaruje typ zmiennych `iter` i `elem` podczas `for` i zakres `for` pętli rozpoczęcia.  
  
```cpp  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
```  
  
 Poniższy fragment kodu używa `new` Deklaracja operatora i wskaźnika do deklarowania wskaźników.  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 Fragment kodu w następnym deklaruje wiele symboli w każdej instrukcji deklaracji. Zwróć uwagę, że wszystkie symbole w każdej instrukcji rozpoznać do tego samego typu.  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 Operator warunkowy używa fragmentu kodu (`?:`) Aby zadeklarować zmienną `x` jako liczba całkowita, która ma wartość 200:  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 Poniższy fragment kodu inicjuje zmienną `x` na typ `int`zmiennej `y` do odwołania do typu `const int`oraz zmienną `fp` na wskaźnik do funkcji, która zwraca typ `int`.  
  
```cpp  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../cpp/auto-keyword.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof — Operator](../cpp/sizeof-operator.md)   
 [TypeID](../windows/typeid-cpp-component-extensions.md)   
 [nowy operator](new-operator-cpp.md)   
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)   
 [Przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Inicjatory](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)