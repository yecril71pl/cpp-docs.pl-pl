---
title: Szablony (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 673eadf3651d15f480ee2cff9ef3f7319dee4d84
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947880"
---
# <a name="templates-c"></a>Szablony (C++)
Szablony są podstawą ogólnego programowania w języku C++. Jako silnie typizowane języka C++ wymaga, aby wszystkie zmienne mieć określonego typu, jawnie zadeklarowane przez programistę lub ustalane przez kompilator. Jednak wiele struktur danych i algorytmów wyglądają tak samo, niezależnie od tego, jakiego typu, które działają na. Szablony pozwalają zdefiniować operacje klasy lub funkcji i zezwolić użytkownikowi na określenie, jakie konkretny typy tych operacji, powinny działać na.  
  
## <a name="defining-and-using-templates"></a>Definiowanie i korzystanie z szablonów  
 Szablon jest konstrukcja, która generuje typu zwykłej lub funkcji w czasie kompilacji, na podstawie argumentów, które użytkownik podaje parametrów szablonu. Na przykład można zdefiniować szablon funkcji następująco:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Powyższy kod w tym artykule opisano szablon jest funkcja ogólna, korzystając z jednego typu parametru `T`, którego wartość zwracana i wywoływać parametry (lewa strona reguły przepisywania i rhs) są wszystkie tego typu. Nazwa parametru typu można niczego, podobnie jak, ale przy Konwencji pojedynczego wielkich liter są najczęściej używane. `T` Parametr szablonu; **typename** — słowo kluczowe mówi, że ten parametr jest symbolem zastępczym dla typu. Gdy funkcja jest wywoływana, kompilator zastąpi każde wystąpienie `T` przy użyciu argumentu typu konkretnego, który jest określony przez użytkownika lub ustalane przez kompilator. Proces, w którym kompilator generuje klasę lub funkcji z szablonu jest określany jako *Tworzenie wystąpienia szablonu*;   `minimum<int>` jest egzemplarzem szablonu `minimum<T>`.  
  
 W innym miejscu użytkownik może zadeklarować wystąpienie szablonu, który jest przeznaczone do int. Załóżmy, że get_a() i get_b() są funkcje, które zwracają int:  
  
```cpp 
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Jednakże, ponieważ jest szablonem funkcji i kompilator może wywnioskować typ `T` z argumentów `a` i `b`, wywołując podobnie jak zwykłej funkcji:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Gdy kompilator napotka tego ostatnią instrukcję, w której każde wystąpienie generuje nową funkcję *T* w szablonie jest zastępowany **int**:  
  
```cpp 
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Reguły dotyczące jak kompilator wykonuje wnioskowanie typu w Szablony funkcji są oparte na zasady zwykłe funkcje. Aby uzyskać więcej informacji, zobacz [przeciążenia rozwiązania z wywołań szablonów funkcji](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a> Parametry typu  
 W `minimum` powyższego szablonu, należy pamiętać, że parametr typu `T` nie jest kwalifikowana w jakikolwiek sposób, dopóki nie jest on używany w parametrów wywołania funkcji, której są dodawane kwalifikatory odwołań i const.  
  
 Nie ma żadnych praktyczne limitu liczby parametrów typu. Wiele parametrów należy oddzielić przecinkami:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 Słowo kluczowe **klasy** jest odpowiednikiem **typename** w tym kontekście. Można wyrazić poprzedniego przykładu jako:  
  
```cpp 
template <class T, class U, class V> class Foo{};   
```  
  
 Operator wielokropka (...) służy do definiowania szablonu, który pobiera dowolną liczbę zero lub więcej parametrów typu:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Dowolny wbudowany lub zdefiniowany przez użytkownika typ może służyć jako argument typu. Na przykład używasz std::vector w standardowej bibliotece do przechowywania liczby całkowite, wartości podwójnej precyzji, ciągów i MyClass MyClass const *, MyClass &. Podstawowe ograniczenia przy użyciu szablonów jest, że argument typu musi obsługiwać żadnych operacji, które są stosowane do parametrów typu. Na przykład, jeśli dzwonimy minimalnej przy użyciu MyClass, jak w poniższym przykładzie:  
  
```cpp  
class MyClass  
{  
public:  
    int num;  
    std::wstring description;  
};  
  
int main()  
{      
    MyClass mc1 {1, L"hello"};  
    MyClass mc2 {2, L"goodbye"};  
    auto result = minimum(mc1, mc2); // Error! C2678  
}  
  
```  
  
 Błąd kompilatora zostanie wygenerowany, ponieważ MyClass nie zapewnia przeciążenie dla elementu < — operator.  
  
 Chociaż można zdefiniować szablon, który wymusza takie ograniczenie nie istnieje wymóg nieprzerwaną pracę, argumentów typu dla konkretnego szablonu, wszystkie należeć do tej samej hierarchii obiektów. Techniki zorientowane obiektowo można połączyć z szablonów; na przykład można przechowywać Derived * w wektorze\<Base\*>.    Należy pamiętać, że argumenty muszą być wskaźników  
  
```cpp 
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Podstawowe wymagania, które wektora i inne kontenery standardowej biblioteki nakładają się na elementy `T` jest fakt, że `T` być możliwy do przypisania kopii i konstrukcyjną kopiowania.  
  
## <a name="non-type-parameters"></a>Parametry bez typu  
 W przeciwieństwie do typów ogólnych w innych językach, takich jak C# i Java szablony języka C++ obsługuje parametry bez typu, jest określana skrótem wartości parametrów. Na przykład można podać wartości stałej całkowitej do określania długości tablicy, podobnie jak w przypadku tego przykładu, która jest podobna do klasy std::array w standardowej bibliotece:  
  
```cpp 
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Należy pamiętać, w składni deklaracji szablonu. Wartość size_t jest przekazywany jako argument szablonu w czasie kompilacji i musi być stałą lub wyrażenia constexpr. Możesz użyć następująco:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Inne rodzaje wartości, w tym wskaźniki i odwołania mogą być przekazywane w jako parametry bez typu. Można na przykład przekazanej wskaźnik do funkcji lub obiektu funkcji, aby dostosować pewnej operacji wewnątrz kodu szablonu.  
  
## <a id="template_parameters"></a> Szablony jako parametry szablonu  
 Szablon może być parametrem szablonu. W tym przykładzie MyClass2 zawiera dwa parametry szablonu: parametr typename `T` i parametrem szablonu `Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Ponieważ `Arr` parametru sam ma bez treści, jego nazwy parametrów nie są wymagane. W rzeczywistości jest błędem do odwoływania się do `Arr`firmy typename lub klasy nazwy parametrów z treści `MyClass2`. Z tego powodu `Arr`firmy nazwy parametrów typu można pominąć, jak pokazano w poniższym przykładzie:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Domyślne argumenty szablonu  
 Szablony klas i funkcji mogą mieć argumentów domyślnych. Szablon ma domyślnego argumentu, który może pozostać nieokreślone, kiedy go używać. Na przykład szablon std::vector ma argument domyślny dla alokator:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 W większości przypadków domyślną klasę std::allocator jest dopuszczalne, aby za pomocą wektora następująco:  
  
```cpp  
vector<int> myInts;  
```  
  
 Ale jeśli to konieczne można określić niestandardowy alokator podobnie do następującego:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 W przypadku wielu argumentów szablonu wszystkie argumenty po pierwszy argument domyślny musi mieć argumentów domyślnych.  
  
 Korzystając z szablonu, której parametry wszystkich domyślnych, należy użyć puste nawiasy:  
  
```cpp  
template<typename A = int, typename B = double>  
class Bar  
{  
    //...  
};  
...  
int main()  
{  
    Bar<> bar; // use all default type arguments  
}  
  
```  
  
## <a name="template-specialization"></a>Specjalizacja szablonu  
 W niektórych przypadkach nie jest niemożliwe lub niepożądane dla szablonu zdefiniować dokładnie ten sam kod dla dowolnego typu. Na przykład może chcesz zdefiniować ścieżka kodu, ma być wykonana tylko wtedy, gdy argument typu jest wskaźnikiem lub std::wstring lub typ pochodzący od konkretnej klasy bazowej.  W takich przypadkach można zdefiniować *specjalizacji* szablonu dla tego określonego typu. Po użytkownik tworzy szablon z tym typem, kompilator używa specjalizacji, aby wygenerować klasę, a dla innych typów, kompilator wybiera bardziej ogólnych szablonu. Specjalizacje, w których są wyspecjalizowane wszystkie parametry są *ukończenia specjalizacje*. Jeśli tylko niektóre parametry są wyspecjalizowane, jest nazywany *częściowa specjalizacja*.  
  
```cpp  
template <typename K, typename V>  
class MyMap{/*...*/};  
  
// partial specialization for string keys  
template<typename V>  
class MyMap<string, V> {/*...*/};  
...  
MyMap<int, MyClass> classes; // uses original template  
MyMap<string, MyClass> classes2; // uses the partial specialization  
  
```  
  
 Szablon może mieć dowolną liczbę specjalizacji, tak długo, jak długo każdy parametr specjalistyczną odmianą jest unikatowy.   Tylko szablony klas mogą być częściowo specjalizowany. Wszystkie pełne i częściowe specjalizacje szablonu musi być zadeklarowana w tej samej przestrzeni nazw jako oryginalnego szablonu.  
  
 Aby uzyskać więcej informacji, zobacz [specjalizacja szablonu](../cpp/template-specialization-cpp.md).