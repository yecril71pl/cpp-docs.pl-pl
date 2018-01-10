---
title: Szablony (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: template_cpp
dev_langs: C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 935bee8447ad0d49ae965fb92538d2e260ec68ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="templates-c"></a>Szablony (C++)
Szablony stanowią podstawę dla ogólnego programowania w języku C++. Jako jednoznacznie języka C++ wymaga wszystkie zmienne określonego typu jawnie zadeklarowana przez programistę albo ustalona przez kompilator. Jednak wielu struktur danych i algorytmy wyglądają tak samo, niezależnie od tego, jakiego typu działają na. Włącz szablony do definiowania operacji klasy lub funkcji i umożliwia użytkownikowi określenie, jakie konkretnych typów te operacje powinny działać na.  
  
## <a name="defining-and-using-templates"></a>Definiowanie i za pomocą szablonów  
 Szablon jest konstrukcję generuje zwykłej typu lub funkcji w czasie kompilacji oparte na argumenty użytkownik podaje parametrów szablonu. Na przykład można zdefiniować szablonu funkcji następująco:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Powyższy kod zawiera opis szablonu dla ogólnych funkcji z parametrem jednego typu `T`, której wartość zwracana i wywołać parametrów (lhs i rhs) są wszystkie tego typu. Nazwa parametru typu można coś, co możesz podobnie jak, ale przez Konwencję pojedynczego wielkie litery są najczęściej używane. `T`jest to parametr szablonu; `typename` — słowo kluczowe mówi, że ten parametr jest symbolem zastępczym dla typu. W przypadku wywołania funkcji Kompilator zastąpi każde wystąpienie `T` z argumentem typu konkretnego, które jest określone przez użytkownika lub ustalona przez kompilator. Proces, w którym kompilator generuje klasę lub funkcji z szablonu jest określana jako *Tworzenie wystąpienia szablonu*;   `minimum<int>` jest utworzenie wystąpienia szablonu `minimum<T>`.  
  
 W innym miejscu użytkownika można zadeklarować wystąpienie szablonu, który jest przeznaczone do int. Załóżmy, że get_a() i get_b() są funkcje, które zwracają int:  
  
```  
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Jednak ponieważ jest to szablon funkcji i kompilator można wywnioskować typu `T` w argumentach `a` i `b`, można go wywołać podobnie jak zwykłej funkcji:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Gdy kompilator napotka tej ostatniej instrukcji, w których każde wystąpienie generuje nową funkcję *T* w szablonie jest zastępowany `int`:  
  
```  
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Zasady jak kompilator wykonuje wnioskowanie typu w szablonach funkcji są oparte na zasady zwykłej funkcji. Aby uzyskać więcej informacji, zobacz [przeciążenia rozwiązania z wywołań szablonów funkcji](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a>Parametry typu  
 W `minimum` szablonu powyżej, należy pamiętać, że parametr typu `T` nie jest kwalifikowana w dowolny sposób, dopóki nie jest on używany w parametrów wywołania funkcji, której są dodawane const i kwalifikatory odwołania.  
  
 Nie ma żadnego praktyczne limitu liczby parametrów typu. Wiele parametrów należy oddzielić przecinkami:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 Słowo kluczowe `class` jest odpowiednikiem `typename` w tym kontekście. Można wyrazić poprzedniego przykładu jako:  
  
```  
template <class T, class U, class V> class Foo{};   
```  
  
 Operator wielokropek (...) służy do definiowania szablonu, który przyjmuje dowolnej liczby zero lub więcej parametrów typu:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Dowolnego typu wbudowanego lub zdefiniowanej przez użytkownika może służyć jako argument typu. Na przykład używasz std::vector w standardowej bibliotece do przechowywania wskazówki, symulacyjnych, ciągi, MyClass MyClass const *, MyClass &. Ograniczenie podstawowego, gdy za pomocą szablonów jest, że typem argumentu musi obsługiwać żadnych operacji, które są stosowane do parametrów typu. Na przykład, jeśli taki stan nazywa się minimalną za pomocą MyClass jak w poniższym przykładzie:  
  
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
  
 Błąd kompilatora zostanie wygenerowany, ponieważ MyClass nie zapewnia przeciążenie dla elementu < operatora.  
  
 Mimo że można zdefiniować szablon, który wymusza takie ograniczenie nie istnieje wymóg związanego z używaniem czy argumentów typu dla dowolnego szablonu określonego wszystkich należą do tej samej hierarchii obiektu. Techniki zorientowane obiektowo można łączyć z szablonami; na przykład można przechowywać pochodne * w wektorze\<Base\*>.    Należy pamiętać, że argumenty muszą być wskaźników  
  
```  
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Podstawowe wymagania, które wektora i inne kontenery biblioteki standardowej nakładają się na elementy `T` jest to, że `T` można możliwy do przypisania kopiowania i umożliwia konstrukcji kopiowania.  
  
## <a name="non-type-parameters"></a>Parametry bez typu  
 W przeciwieństwie do typów ogólnych w innych językach, takich jak C# i Java szablonów języka C++ obsługuje parametry bez typu, nazywany również wartości parametrów. Na przykład zapewniają całkowitą wartością stałą do określania długości tablicy, tak jak w przypadku tego przykładu, która jest podobna do klasy std::array w standardowej bibliotece:  
  
```  
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Należy zwrócić uwagę składni w deklaracji szablonu. Wartość size_t jest przekazywany jako argument szablonu w czasie kompilacji i musi być stałą lub wyrażenie constexpr. Można użyć następująco:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Inne rodzaje tym wskaźników i odwołania do wartości mogą być przekazywane w jako parametry bez typu. Na przykład można przekazać wskaźnika do funkcji lub funkcja obiektu do dostosowania niektórych operacji wewnątrz kod szablonu.  
  
## <a id="template_parameters"></a>Szablony jako parametry szablonu  
 Szablon może być parametrem szablonu. W tym przykładzie MyClass2 ma dwa parametry szablonu: parametru typename `T` i parametr szablonu `Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Ponieważ `Arr` treści nie ma parametru samego, jego nazwy parametrów nie są wymagane. W rzeczywistości jest błędem w odwołaniu do `Arr`w typename lub klasy nazwy parametrów z wewnątrz treści `MyClass2`. Z tego powodu `Arr`na nazwy parametrów typu, można pominąć, jak pokazano w poniższym przykładzie:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Domyślne argumenty szablonu  
 Szablony klas i funkcji mogą mieć argumentów domyślnych. Szablon ma domyślnego argumentu, który można pozostawić nieokreślony, jeśli używasz. Na przykład szablon std::vector zawiera domyślnego argumentu dla programu przydzielania:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 W większości przypadków domyślną klasę std::allocator jest dopuszczalne, aby używać wektor następująco:  
  
```cpp  
vector<int> myInts;  
```  
  
 Ale jeśli niezbędne można określić niestandardowego zarządcę podobnie do następującej:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Dla wielu argumentów szablonu wszystkie argumenty po pierwszym domyślnego argumentu musi mieć argumentów domyślnych.  
  
 Podczas korzystania z szablonu, którego parametry są wszystkie ustawiana domyślnie, należy użyć puste nawiasy:  
  
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
 W niektórych przypadkach nie jest niemożliwe lub niepożądane dla szablonu zdefiniować dokładnie tego samego kodu dla dowolnego typu. Na przykład może chcieć zdefiniował ścieżki kodu ma być wykonywana tylko wtedy, gdy argument typu jest wskaźnikiem lub std::wstring, lub typ pochodzący od konkretnej klasy podstawowej.  W takich przypadkach można zdefiniować *specjalizacji* szablonu dla tego typu. Gdy użytkownik tworzy wystąpienie szablonu z tego typu, kompilator używa specjalizacji do generowania klasy i dla wszystkich innych typów wybierze kompilator bardziej ogólne szablonu. Specjalizacji, w których wszystkie parametry są przystosowane w szczególności są *ukończyć specjalizacje*. Jeśli tylko niektóre parametry są przystosowane w szczególności, jest nazywany *częściowa specjalizacja*.  
  
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
  
 Szablon może mieć dowolną liczbę specjalizacji, jak długo każdy parametr specjalistyczną odmianą jest unikatowa.   Tylko szablony klas może być częściowo specjalizowany. Wszystkie pełne i częściowe specjalizacje szablonu musi być zadeklarowany w tej samej przestrzeni nazw, jak oryginalny szablon.  
  
 Aby uzyskać więcej informacji, zobacz [specjalizacja szablonu](../cpp/template-specialization-cpp.md).