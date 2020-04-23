---
title: Szablony (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032346"
---
# <a name="templates-c"></a>Szablony (C++)

Szablony są podstawą ogólnego programowania w języku C++. Jako język silnie typizowane C++ wymaga wszystkich zmiennych, aby mieć określonego typu, jawnie zadeklarowane przez programistę lub wywnioskowane przez kompilator. Jednak wiele struktur danych i algorytmów wygląda tak samo, bez względu na typ, na jakim działają. Szablony umożliwiają definiowanie operacji klasy lub funkcji i pozwalają użytkownikowi określić, jakie konkretne typy te operacje powinny działać.

## <a name="defining-and-using-templates"></a>Definiowanie i używanie szablonów

Szablon jest konstrukcją, która generuje zwykły typ lub funkcję w czasie kompilacji na podstawie argumentów, które użytkownik dostarcza dla parametrów szablonu. Na przykład można zdefiniować szablon funkcji w ten sposób:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Powyższy kod opisuje szablon dla funkcji ogólnej z parametrem jednego typu *T*, którego wartość zwracana i parametry wywołania (lhs i rhs) są tego typu. Możesz nazwać parametr typu, co chcesz, ale zgodnie z konwencją najczęściej używane są pojedyncze wielkie litery. *T* jest parametrem szablonu; słowo kluczowe **nazwa typename** mówi, że ten parametr jest symbolem zastępczym dla typu. Gdy funkcja jest wywoływana, kompilator `T` zastąpi każde wystąpienie z argumentem typu betonu, który jest określony przez użytkownika lub wywnioskowane przez kompilator. Proces, w którym kompilator generuje klasę lub funkcję z szablonu, jest określany jako *tworzenie wystąpienia szablonu;* `minimum<int>` jest wystąpieniem szablonu `minimum<T>`.

Gdzie indziej użytkownik może zadeklarować wystąpienie szablonu, który jest wyspecjalizowany dla int. Załóżmy, że get_a() i get_b() są funkcje, które zwracają int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Jednak ponieważ jest to szablon funkcji i kompilator może `T` wywnić typ z argumentów *a* i *b*, można go wywołać tak samo jak zwykła funkcja:

```cpp
int i = minimum(a, b);
```

Gdy kompilator napotka tę ostatnią instrukcję, generuje nową funkcję, w której każde wystąpienie *T* w szablonie jest zastępowane **int:**

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Reguły sposobu wykonywania przez kompilator dedukcji typu w szablonach funkcji są oparte na regułach dla zwykłych funkcji. Aby uzyskać więcej informacji, zobacz [Rozpoznawanie przeciążenia wywołań szablonu funkcji](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Parametry typu

W `minimum` powyższym szablonie należy zauważyć, że parametr typu *T* nie jest kwalifikowany w żaden sposób, dopóki nie jest używany w parametrach wywołania funkcji, gdzie są dodawane kwalifikatory i kwalifikatory referencyjne.

Nie ma praktycznego limitu liczby parametrów typu. Oddziel wiele parametrów przecinkami:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

**Klasa** słowa kluczowego jest odpowiednikiem **nazwy typu** w tym kontekście. Poprzedni przykład można wyrazić jako:

```cpp
template <class T, class U, class V> class Foo{};
```

Operator wielokropka (...) służy do definiowania szablonu, który przyjmuje dowolną liczbę parametrów typu zero lub więcej:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Każdy wbudowany lub zdefiniowany przez użytkownika typ może służyć jako argument typu. Na przykład można użyć [std::vector](../standard-library/vector-class.md) w bibliotece standardowej do **double**przechowywania zmiennych typu **int**, double `MyClass&`, [std::string](../standard-library/basic-string-class.md), `MyClass`, **const** `MyClass`*, i tak dalej. Podstawowym ograniczeniem podczas korzystania z szablonów jest to, że argument typu musi obsługiwać wszystkie operacje, które są stosowane do parametrów typu. Na przykład, jeśli `minimum` `MyClass` wywołamy przy użyciu jak w tym przykładzie:

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

Zostanie wygenerowany błąd kompilatora, ponieważ `MyClass` nie **<** zapewnia przeciążenia dla operatora.

Nie istnieje nieodłączne wymaganie, że argumenty typu dla dowolnego określonego szablonu należą do tej samej hierarchii obiektów, chociaż można zdefiniować szablon, który wymusza takie ograniczenie. Techniki obiektowe można łączyć z szablonami; na przykład można zapisać Pochodne* w\<\* bazie wektorowej>.    Należy zauważyć, że argumenty muszą być wskaźnikami

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Podstawowe wymagania, `std::vector` które i inne standardowe kontenery biblioteki nakładają na elementy `T` jest to, że `T` można przypisać do kopiowania i kopiowania-constructable.

## <a name="non-type-parameters"></a>Parametry nienakładowe

W przeciwieństwie do typów ogólnych w innych językach, takich jak C# i Java, szablony języka C++ obsługują *parametry innego typu,* zwane również parametrami wartości. Na przykład można podać stałą wartość integralną, aby określić długość tablicy, tak jak w tym przykładzie, który jest podobny do klasy [std::array](../standard-library/array-class-stl.md) w bibliotece standardowej:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Zanotuj składnię w deklaracji szablonu. Wartość `size_t` jest przekazywana jako argument szablonu w czasie kompilacji i musi być **const** lub **wyrażenie constexpr.** Używasz go w ten sposób:

```cpp
MyArray<MyClass*, 10> arr;
```

Inne rodzaje wartości, w tym wskaźniki i odwołania mogą być przekazywane jako parametry innego typu. Na przykład można przekazać w wskaźniku do obiektu funkcji lub funkcji, aby dostosować niektóre operacji wewnątrz kodu szablonu.

### <a name="type-deduction-for-non-type-template-parameters"></a>Odliczanie typu dla parametrów szablonu niena typowego

W programie Visual Studio 2017 i nowszych w trybie **/std:c++17** kompilator wyd. **auto**

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Szablony jako parametry szablonu

Szablon może być parametrem szablonu. W tym przykładzie MyClass2 ma dwa parametry szablonu: parametr nazwy typu *T* i parametr szablonu *Arr:*

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Ponieważ sam parametr *Arr* nie ma treści, jego nazwy parametrów nie są potrzebne. W rzeczywistości jest to błąd, aby odwołać się do nazwy typu *Arr*'s lub nazwy parametrów `MyClass2`klasy z poziomu treści . Z tego powodu można pominąć nazwy parametrów typu *Arr,jak*pokazano w tym przykładzie:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Domyślne argumenty szablonu

Szablony klas i funkcji mogą mieć domyślne argumenty. Gdy szablon ma domyślny argument, możesz pozostawić go nieokreślonym podczas jego używania. Na przykład szablon std::vector ma domyślny argument dla alokatora:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

W większości przypadków domyślna klasa std::alokator jest dopuszczalna, dlatego używasz wektora w ten sposób:

```cpp
vector<int> myInts;
```

Ale w razie potrzeby można określić niestandardowy alokator w ten sposób:

```cpp
vector<int, MyAllocator> ints;
```

W przypadku wielu argumentów szablonu wszystkie argumenty po pierwszym argumie domyślnym muszą mieć argumenty domyślne.

W przypadku korzystania z szablonu, którego parametry są domyślne, należy użyć pustych nawiasów kątowych:

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

W niektórych przypadkach nie jest możliwe lub pożądane dla szablonu, aby zdefiniować dokładnie ten sam kod dla dowolnego typu. Na przykład można zdefiniować ścieżkę kodu, która ma być wykonywana tylko wtedy, gdy argument typu jest wskaźnikiem lub std::wstring lub typem pochodzącym z określonej klasy podstawowej.  W takich przypadkach można zdefiniować *specjalizację* szablonu dla danego typu. Gdy użytkownik tworzy wystąpienia szablonu z tego typu, kompilator używa specjalizacji do generowania klasy i dla wszystkich innych typów kompilator wybiera bardziej ogólny szablon. Specjalizacje, w których wszystkie parametry są wyspecjalizowane są *pełne specjalizacje*. Jeśli tylko niektóre parametry są wyspecjalizowane, jest to nazywane *częściową specjalizacji*.

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

Szablon może mieć dowolną liczbę specjalizacji, o ile każdy parametr typu specjalistycznego jest unikatowy. Tylko szablony klas mogą być częściowo wyspecjalizowane. Wszystkie pełne i częściowe specjalizacje szablonu muszą być zadeklarowane w tym samym obszarze nazw co oryginalny szablon.

Aby uzyskać więcej informacji, zobacz [Specjalizacja szablonów](../cpp/template-specialization-cpp.md).
