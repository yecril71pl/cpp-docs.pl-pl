---
title: Auto (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e33faac0bf222a94b21878eb287e696ae8c7de47
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939872"
---
# <a name="auto-c"></a>Auto (C++)
Określi typ zmiennej zadeklarowanej przy użyciu jego wyrażenia inicjowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>Uwagi  
 **Automatycznie** — słowo kluczowe nakazuje kompilatorowi Używanie wyrażenia inicjowania zadeklarowana zmienna lub parametr wyrażenia lambda, można wywnioskować jej typu.  
  
 Firma Microsoft zaleca użycie **automatycznie** — słowo kluczowe w większości sytuacji — chyba że naprawdę chcesz konwersji — ponieważ zapewnia następujące korzyści:  
  
-   **Niezawodność:** wyrażenia na typ po zmianie — w tym przypadku zmiany zwracanego typu funkcji — po prostu działa.  
  
-   **Wydajność:** one zagwarantować, że będzie bez konwersji.  
  
-   **Użyteczność:** nie trzeba martwić się o trudności pisownię nazwy typu i literówek.  
  
-   **Wydajność:** kodowania może być bardziej wydajne.  
  
 Konwersja przypadki, w których możesz nie chcieć użyć **automatycznie**:  
  
-   Wystarczy, aby określonego typu i od niczego więcej.  
  
-   Typy pomocnika szablonu wyrażenia — na przykład `(valarray+valarray)`.  
  
 Aby użyć **automatycznie** — słowo kluczowe, użyj zamiast typu, aby zadeklarować zmienną, a następnie określ wyrażenia inicjowania. Ponadto, możesz zmodyfikować **automatycznie** — słowo kluczowe przy użyciu Specyfikatory i deklaratory, takich jak **const**, **volatile**, wskaźnik (`*`), odwołanie (`&`), a odwołanie rvalue (`&&`). Kompilator ocenia wyrażenie, a następnie używa tych informacji do dedukuj typ zmiennej.  
  
 Wyrażenie inicjowania może być przypisanie (składnia znaku równości) inicjalizacji bezpośredniej (składni stylu funkcji) [nowy operator](new-operator-cpp.md) wyrażenie lub wyrażenie może być  *dla zakresu — deklaracja* parametru w [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md) instrukcji. Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i przykłady kodu w dalszej części tego dokumentu.  
  
 **Automatycznie** — słowo kluczowe jest symbolem zastępczym dla typu, ale nie sam jest typem. W związku z tym **automatycznie** słów kluczowych nie można używać w rzutowania lub operatorów takich jak [sizeof](../cpp/sizeof-operator.md) i [typeid](../windows/typeid-cpp-component-extensions.md).  
  
## <a name="usefulness"></a>Użyteczność  
 **Automatycznie** — słowo kluczowe jest to prosty sposób, aby zadeklarować zmienną, która ma typ skomplikowane. Na przykład, można użyć **automatycznie** Aby zadeklarować zmienną, jeżeli wyrażenie inicjowania obejmuje szablony, wskaźniki do funkcji lub wskaźniki do elementów członkowskich.  
  
 Można również użyć **automatycznie** zadeklarować i zainicjować zmienną do wyrażenia lambda. Nie można zadeklarować typu zmiennej samodzielnie, ponieważ typ wyrażenia lambda jest znane tylko w kompilatorze. Aby uzyskać więcej informacji, zobacz [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).  
  
## <a name="trailing-return-types"></a>Śledzenie typów zwracanych  
 Możesz użyć **automatycznie**, wraz z **decltype** specyfikator ułatwia pisanie szablonu biblioteki typu. Użyj **automatycznie** i **decltype** do deklarowania funkcji szablonu, którego zwracany typ jest zależny od typów argumentów szablonu. Możesz też korzystać z **automatycznie** i **decltype** do deklarowania funkcji szablonu, który zawija wywołanie do innej funkcji, a następnie zwraca, niezależnie od rodzaju jest typem zwracanym tych innych funkcji. Aby uzyskać więcej informacji, zobacz [decltype](../cpp/decltype-cpp.md).  
  
## <a name="references-and-cv-qualifiers"></a>Odwołań i stałych nietrwałych  
 Należy pamiętać, że używanie **automatycznie** spada odwołania, kwalifikatorów const i volatile kwalifikatorów. Rozważmy następujący przykład:  
  
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
  
 W poprzednim przykładzie myAuto jest nie odwołaniem int, int, dzięki czemu dane wyjściowe są `11 11`, a nie `11 12` tak jak w przypadku gdy kwalifikator odwołania nie miał został porzucony podczas **automatycznie**.  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>Wnioskowanie typu z inicjatorami w nawiasach (C ++ 14)  
 Następujące exmample kodu pokazano, jak zainicjować zmienną automatycznie za pomocą nawiasów klamrowych. Należy zanotować różnicę między B i C oraz między A i E.  
  
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
 W poniższej tabeli wymieniono ograniczenia dotyczące użytkowania **automatycznie** — słowo kluczowe, a odpowiedni komunikat o błędzie diagnostycznych, który emituje kompilator.  
  
|Numer błędu|Opis|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**Automatycznie** — słowo kluczowe nie można łączyć z jakimkolwiek innym specyfikatorem typu.|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, który jest zadeklarowana za pomocą **automatycznie** — słowo kluczowe musi mieć inicjator.|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Niepoprawnie użyte **automatycznie** — słowo kluczowe do deklarowania typu. Na przykład zadeklarowany zwracany typ metody lub tablicy.|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Nie można zadeklarować argument parametru lub szablonu z **automatycznie** — słowo kluczowe.|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Nie można zadeklarować parametru metody lub szablonu ze **automatycznie** — słowo kluczowe.|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Nie można używać symbolu, zanim zostanie zainicjowany. W praktyce oznacza to, że zmienna nie może służyć do zainicjowania.|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nie można rzutować na typ, która jest zadeklarowana za pomocą **automatycznie** — słowo kluczowe.|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Wszystkie symbole, na liście deklaratorów, która jest zadeklarowana za pomocą **automatycznie** — słowo kluczowe musi zostać rozpoznany tego samego typu. Aby uzyskać więcej informacji, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md) i [typeid](../windows/typeid-cpp-component-extensions.md) operatorów nie można zastosować do symbolu, która jest zadeklarowana za pomocą **automatycznie** — słowo kluczowe.|  
  
## <a name="examples"></a>Przykłady  
 Te fragmenty kodu przedstawiają kilka sposobów, w którym **automatycznie** można użyć słowa kluczowego.  
  
 Następujące deklaracje są równoważne. W pierwszej instrukcji zmiennej `j` został zadeklarowany jako typ **int**. W drugiej instrukcji zmiennej `k` wywnioskowano typu **int** ponieważ wyrażenia inicjowania (0) jest liczbą całkowitą.  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 Następujące deklaracje są równoważne, ale drugi deklaracja jest prostsze niż pierwszy. Jedną z najbardziej atrakcyjnych przyczyn do użycia **automatycznie** — słowo kluczowe jest prostotę.  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 Poniższy fragment kodu deklaruje typ zmiennych `iter` i `elem` podczas **dla** i zakres **dla** start w pętli.  
  
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
  
 Poniższy fragment kodu używa **nowe** Deklaracja operatora i wskaźnika do deklarowania wskaźników.  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 Następny fragment kodu deklaruje wiele symboli w każdej instrukcji deklaracji. Należy zauważyć, że wszystkie symbole w każdej instrukcji rozpoznać tego samego typu.  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 Ten fragment kodu używa operatora warunkowego (`?:`) Aby zadeklarować zmienną `x` jako liczba całkowita, która ma wartość 200:  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 Poniższy fragment kodu inicjuje zmienną `x` na typ **int**zmiennej `y` na odwołanie do typu **const int**i zmienna `fp` ze wskaźnikiem do funkcji który zwraca typ **int**.  
  
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
 [auto Keyword](../cpp/auto-keyword.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [/ Zc: Auto (dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof — Operator](../cpp/sizeof-operator.md)   
 [TypeID](../windows/typeid-cpp-component-extensions.md)   
 [nowy operator](new-operator-cpp.md)   
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)   
 [Przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Inicjatory](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)