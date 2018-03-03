---
title: decltype (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- decltype_cpp
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee3c83512929e4592a5ee75b954bc6c19f52f448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="decltype--c"></a>decltype (C++)
`decltype` Specyfikatora typu daje typ określonego wyrażenia. `decltype` Wpisz specyfikator, wraz z [auto — słowo kluczowe](../cpp/auto-cpp.md), przydaje się głównie do deweloperów, którzy zapisu biblioteki szablonów. Użyj `auto` i `decltype` do zadeklarowania funkcji szablonu, którego zwracany typ zależy od typów argumentów szablonu. Lub użyj `auto` i `decltype` do zadeklarowania funkcji szablonu, który opakowuje wywołania do innej funkcji, a następnie zwraca typ zwracany funkcji opakowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
decltype( expression )  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`expression`|Wyrażenie. Aby uzyskać więcej informacji, zobacz [wyrażenia](../cpp/expressions-cpp.md).|  
  
## <a name="return-value"></a>Wartość zwracana  
 Typ `expression` parametru.  
  
## <a name="remarks"></a>Uwagi  
 `decltype` Specyfikatora typu jest obsługiwane w Visual C++ 2010 lub nowszy i może być używany z kodu natywnego lub zarządzanego. `decltype(auto)`(C ++ 14) jest obsługiwana w programie Visual Studio 2015 i nowszych.  
  
 Kompilator używa następujących reguł w celu określenia typu `expression` parametru.  
  
-   Jeśli `expression` parametru jest identyfikatorem lub [dostęp do elementu członkowskiego klasy](../cpp/member-access-operators-dot-and.md), `decltype(expression)` jest typem jednostki o nazwie `expression`. Jeśli istnieje taka jednostka lub `expression` zestaw funkcji przeciążenia nazwy parametrów, kompilator zapewnia komunikat o błędzie.  
  
-   Jeśli `expression` parametr jest wywołaniem funkcji lub funkcja Przeciążony operator `decltype(expression)` jest zwracany typ funkcji. Nawiasy otaczające Przeciążony operator są ignorowane.  
  
-   Jeśli `expression` parametr jest [prawostronnie](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest typem `expression`. Jeśli `expression` parametr jest [l-wartością](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` jest [odwołania do wartości](../cpp/lvalue-reference-declarator-amp.md) do typu `expression`.  
  
 W poniższym przykładzie kodu pokazano niektóre zastosowania `decltype` Specyfikator typu. Najpierw przyjęto założenie, że zostały zakodowane następujące instrukcje.  
  
```cpp  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 Następnie sprawdź typy, które są zwracane przez cztery `decltype` instrukcje w poniższej tabeli.  
  
|Instrukcja|Typ|Uwagi|  
|---------------|----------|-----------|  
|`decltype(fx());`|`const int&&`|[Odwołania do wartości](../cpp/rvalue-reference-declarator-amp-amp.md) do `const int`.|  
|`decltype(var);`|`int`|Typ zmiennej `var`.|  
|`decltype(a->x);`|`double`|Rodzaj dostępu do elementu członkowskiego.|  
|`decltype((a->x));`|`const double&`|Wewnętrzny nawiasów, że instrukcja ma zostać obliczone jako wyrażenie zamiast dostępu elementu członkowskiego. Ponieważ `a` jest zadeklarowany jako `const` wskaźnika typu jest odwołaniem do `const double`.|  
  
## <a name="decltype-and-auto"></a>Decltype i automatycznie  
 W języku C ++ 14, można użyć `decltype(auto)` z końcowego typu zwracanego do zadeklarowania funkcji szablonu, którego typ zwracany zależy od typów argumentów szablonu.  
  
 W języku C ++ 11, można użyć `decltype` specyfikator na końcowego typu zwracanego typu razem z `auto` — słowo kluczowe do zadeklarowania funkcji szablonu, którego typ zwracany zależy od typów argumentów szablonu. Rozważmy na przykład w poniższym przykładzie kodu, w którym typ zwracany funkcji szablonu zależy od typów argumentów szablonu. W przykładzie kodu *nieznany* symbolu zastępczego wskazuje, że nie można określić zwracanego typu.  
  
```cpp  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 Wprowadzenie `decltype` specyfikatora typu umożliwia deweloperom uzyskać typ wyrażenie, które zwraca funkcja szablonu. Użyj *Składnia deklaracji funkcji alternatywnych* który przedstawiono później, `auto` — słowo kluczowe i `decltype` specyfikator Aby zadeklarować typu *późne określony* typ zwracany. Późne określony zwracany typ jest ustalany w chwili deklaracji jest kompilowany zamiast po jest kodowany.  
  
 Następujące prototypu ilustruje składnię deklaracji funkcji alternatywnych. Należy pamiętać, że `const` i `volatile` kwalifikatorów i `throw` [specyfikacji wyjątku](../cpp/exception-specifications-throw-cpp.md) są opcjonalne. *Function_body* złożonej instrukcji, która określa, jak działa funkcja reprezentuje symbol zastępczy. Jako najlepszym rozwiązaniem, kodowania *wyrażenie* symbol zastępczy w `decltype` instrukcji powinna być zgodna z wyrażeniem określonym przez `return` instrukcji, jeśli istnieje w *function_body*.  
  
 **automatycznie** *nazwa_funkcji* **(** *parametry*<sub>opt</sub> **)**  **Const**<sub>opt</sub> **volatile**<sub>opt</sub>  **->**  **decltype (** *wyrażenie* **)** **throw**<sub>opt</sub> **{** *function_body* **};**  
  
 W poniższym przykładzie kodu późne określony zwracany typ `myFunc` funkcji szablonu jest określana przez typy `t` i `u` argumentów szablonu. Jako najlepsze praktyki kodowania, przykładowy kod używa również odwołania do r-wartości i `forward` szablonu funkcji, które obsługuje *doskonała przekazywania*. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
```cpp  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## <a name="decltype-and-forwarding-functions-c11"></a>Decltype i przekazywanie funkcji (C ++ 11)  
 Funkcje przekazywania otoczenie wywołania innych funkcji. Należy wziąć pod uwagę szablonu funkcji, która przekazuje argumenty lub wyniki wyrażenie, które obejmuje tych argumentów, na inną funkcję. Ponadto funkcja przesyłania dalej zwraca wynik wywołania innych funkcji. W tym scenariuszu należy zwracany typ funkcji przesyłania dalej, taki sam jak typ zwracany funkcji opakowana.  
  
 W tym scenariuszu nie można zapisać wyrażenia odpowiedniego typu bez `decltype` Specyfikator typu. `decltype` Specyfikatora typu zapewnia funkcje ogólnego przekazywania, ponieważ nie traci wymaganych informacji dotyczących tego, czy funkcja zwraca typ referencyjny. Na przykład kodu funkcji przekazywania, zobacz poprzedni `myFunc` przykładzie funkcja szablonu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod deklaruje późne określonym przez typ zwracany funkcji szablonu `Plus()`. `Plus` Funkcja przetwarza dwóch argumentów z `operator+` przeciążenia. W rezultacie interpretacji operator plus (+) i typ zwracany `Plus` funkcji zależy od typów argumentów funkcji.  
  
```cpp  
// decltype_1.cpp  
// compile with: cl /EHsc decltype_1.cpp  
  
#include <iostream>  
#include <string>  
#include <utility>  
#include <iomanip>  
  
using namespace std;  
  
template<typename T1, typename T2>  
auto Plus(T1&& t1, T2&& t2) ->   
   decltype(forward<T1>(t1) + forward<T2>(t2))  
{  
   return forward<T1>(t1) + forward<T2>(t2);  
}  
  
class X  
{  
   friend X operator+(const X& x1, const X& x2)  
   {  
      return X(x1.m_data + x2.m_data);  
   }  
  
public:  
   X(int data) : m_data(data) {}  
   int Dump() const { return m_data;}  
private:  
   int m_data;  
};  
  
int main()  
{  
   // Integer   
   int i = 4;  
   cout <<   
      "Plus(i, 9) = " <<   
      Plus(i, 9) << endl;  
  
   // Floating point  
   float dx = 4.0;  
   float dy = 9.5;  
   cout <<     
      setprecision(3) <<   
      "Plus(dx, dy) = " <<  
      Plus(dx, dy) << endl;  
  
   // String        
   string hello = "Hello, ";  
   string world = "world!";  
   cout << Plus(hello, world) << endl;  
  
   // Custom type  
   X x1(20);  
   X x2(22);  
   X x3 = Plus(x1, x2);  
   cout <<   
      "x3.Dump() = " <<   
      x3.Dump() << endl;  
}  
```  
  
```Output  
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```
  
## <a name="example"></a>Przykład
**Visual Studio 2017 lub nowszy:** kompilator analizuje decltype argumenty podczas szablony są zadeklarowane zamiast wystąpienia. W związku z tym jeśli specjalizacji zależny od innych niż zostanie znaleziony w argumencie decltype, nie zostanie odłożone na czas tworzenia wystąpienia, a zostaną niezwłocznie przetworzone i wyniki zostanie zdiagnozowany w tym czasie.

W poniższym przykładzie przedstawiono takie wystąpi błąd kompilatora, która jest zgłaszane w punkcie deklaracji:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Wymagania  
 Visual C++ 2010 lub nowszy.  
  
 `decltype(auto)`wymaga programu Visual Studio 2015 lub nowszego.  
  
