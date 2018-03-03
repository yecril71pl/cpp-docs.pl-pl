---
title: constexpr (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf1094be23074fe71e65a3077de51263f01a81c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-c"></a>constexpr (C++)
Słowo kluczowe `constexpr` została wprowadzona w języku C ++ 11 i ulepszona w języku C ++ 14. Oznacza to *wyrażenie stałe*. Podobnie jak `const`, dzięki czemu wystąpi błąd kompilatora zostanie wygenerowany, jeśli dowolny kod próbuje zmodyfikować wartości można je stosować do zmiennych. W odróżnieniu od `const`, `constexpr` również będą stosowane do funkcji i klasy konstruktorów. `constexpr`Wskazuje, że wartość lub wartości zwracanej jest stałe i, jeśli to możliwe, będzie obliczana w czasie kompilacji.  A `constexpr` całkowitą wartość może być używana, wszędzie tam, gdzie stała liczba całkowita jest wymagane, takie jak argumentów szablonu i deklaracje tablicy. I gdy wartość może być obliczona w czasie kompilacji zamiast w czasie wykonywania, może ułatwić program szybsze i użyj mniejszej ilości pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);  
```  
  
#### <a name="parameters"></a>Parametry  
 `params`  
 Jeden lub więcej parametrów, które musi być typem literału (wymienione poniżej) a sam być wyrażeniem stałym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmienna constexpr lub funkcja musi zwracać jedną typy literału, wymienione poniżej.  
  
## <a name="literal-types"></a>Typy literału  
 Aby ograniczyć złożoność obliczeniowych kompilacji stałe czasu i ich potencjalnego wpływu czas kompilacji i C ++ 14 standard wymaga objętego wyrażeń stałych typu ograniczone do typów literału. Typ literału jest jednym którego układ można określić w czasie kompilacji. Poniżej przedstawiono typy literału:  
  
1.  void  
  
2.  typy skalarne  
  
3.  odwołania  
  
4.  Tablice void, typów skalarnych lub odwołuje się do  
  
5.  Klasa, która ma destruktor prosta i konstruktory constexpr, które nie są przenoszenie lub kopiowanie konstruktorów. Ponadto wszystkie jego elementy członkowskie danych niestatyczna i klasy podstawowe muszą być typy literału i nietrwałe nie.  
  
## <a name="constexpr-variables"></a>zmienne constexpr  
 Główną różnicą między const i zmienne constexpr jest, że inicjowanie zmiennej stałej może zostać odroczona do czasu wykonywania, natomiast zmienna constexpr musi zostać zainicjowany w czasie kompilacji.  Wszystkie zmienne constexpr to stała.  

-  Zmienna mogą być deklarowane z `constexpr`, jeśli jest typem literału i został zainicjowany. Jeśli inicjowanie jest wykonywana przez konstruktora, Konstruktor musi być zadeklarowany jako `constexpr`.  
  
-   Odwołanie może być zadeklarowany jako constexpr, jeśli obiekt, który odwołuje się został zainicjowany przez wyrażenie stałe i niejawne konwersje, które są wywoływane podczas inicjowania są również wyrażenia stałe.  
  
-   Wszystkie deklaracje `constexpr` zmiennej lub funkcji musi mieć `constexpr` specyfikator.  
  
 
  
 
  
```cpp  
constexpr float x = 42.0;  
constexpr float y{108};  
constexpr float z = exp(5, 3);  
constexpr int i; // Error! Not initialized  
int j = 0;  
constexpr int k = j + 1; //Error! j not a constant expression  
```  
  
## <a name="constexpr-functions"></a>funkcji constexpr  
 A `constexpr` funkcji jest jednym którego zwracana wartość może być obliczona w kompilacji podczas używania kodu wymaga.  Kiedy są argumenty `constexpr` wartości i odbierającą kodu wymaga wartości zwracanej w czasie kompilacji, na przykład w celu zainicjowania `constexpr` zmiennej lub podać argument szablonu bez typu, generuje stałą czasu kompilacji. Po wywołaniu z inną niż`constexpr` argumentów, lub gdy jego wartość nie jest wymagane w czasie kompilacji, tworzy wartość w czasie wykonywania, takie jak normalne działanie.  (To zachowanie podwójną pozwala uniknąć zapisu `constexpr` i nie-`constexpr` wersje tej samej funkcji.)  
 
 A `constexpr` funkcji lub konstruktora jest niejawnie `inline`. 
 
 Funkcji constexpr mają zastosowanie następujące reguły:

- A `constexpr` funkcja musi akceptować i zwracać tylko typy literału. 

- A `constexpr` funkcja może mieć wartość recursive. 

- Nie można go [wirtualnego](../cpp/virtual-cpp.md). A konstruktora nie może być zdefiniowana jako constexpr, jeśli otaczającą klasę ma żadnych wirtualnych klas podstawowych.

- Treść można zdefiniować jako `= default` lub `= delete`. 

- Nie może zawierać treści `goto` instrukcji lub bloki try. 

- Jawna specjalizacja szablonu z systemem innym niż constexpr mogą być deklarowane jako `constexpr`:  
  
- Jawna specjalizacja `constexpr` szablon nie ma być również `constexpr`: 


<!--conformance note-->
Funkcji constexpr w Visual Studio 2017 i później mają zastosowanie następujące reguły: 

- Może zawierać Jeśli i przełączania instrukcje i wszystkie instrukcje pętli, włączając, opartej na zakresie, podczas i wykonaj-podczas
    
- Może on zawierać deklaracje zmiennych lokalnych, ale zmienna musi zostać zainicjowany, musi być typem literału i nie może być statyczne lub lokalnej wątku. Zmienna zadeklarowana lokalnie nie musi być wartością stałą i może zmodyfikować.

- Funkcja constexpr niestatycznego elementu członkowskiego nie musi być niejawnie const.

  
```cpp  
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
```  
  
> [!TIP]
>  Uwaga: W debugerze programu Visual Studio, można określić, czy `constexpr` funkcji jest oceniane w czasie kompilacji poprzez umieszczenie w nim punkt przerwania. Jeśli punkt przerwania zostaje trafiony, funkcja została wywołana w czasie wykonywania.  Jeśli nie, następnie funkcja została wywołana w czasie kompilacji.  
  
 
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `constexpr` zmienne, funkcje i typu zdefiniowanego przez użytkownika. Należy pamiętać, że w ostatniej instrukcji w main(), `constexpr` funkcji członkowskiej GetValue() to wywołanie czasu wykonywania, ponieważ wartość nie musi być znane w czasie kompilacji.  
  
```  
#include <iostream>  
  
using namespace std;  
  
// Pass by value   
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
  
// Pass by reference  
constexpr float exp2(const float& x, const int& n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp2(x * x, n / 2) :  
        exp2(x * x, (n - 1) / 2) * x;  
};  
  
// Compile time computation of array length  
template<typename T, int N>  
constexpr int length(const T(&ary)[N])   
{   
    return N;   
}   
  
// Recursive constexpr function  
constexpr int fac(int n)  
{   
    return n == 1 ? 1 : n*fac(n - 1);   
}  
  
// User-defined type  
class Foo  
{  
public:  
    constexpr explicit Foo(int i) : _i(i) {}  
    constexpr int GetValue()  
    {  
        return _i;  
    }  
private:  
    int _i;  
};  
  
int main()  
{  
    //foo is const:  
    constexpr Foo foo(5);   
    // foo = Foo(6); //Error!  
  
    //Compile time:  
    constexpr float x = exp(5, 3);   
    constexpr float y { exp(2, 5) };  
    constexpr int val = foo.GetValue();   
    constexpr int f5 = fac(5);  
    const int nums[] { 1, 2, 3, 4 };  
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };  
  
    //Run time:   
    cout << "The value of foo is " << foo.GetValue() << endl;   
  
}  
  
```  
  
## <a name="requirements"></a>Wymagania  
 Visual Studio 2015  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)   
 [const](../cpp/const-cpp.md)