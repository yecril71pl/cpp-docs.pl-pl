---
title: Szablony (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 5f8322d850084ca53e946dcff1b67dc81b493fe3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160778"
---
# <a name="templates-c"></a>Szablony (C++)

Szablony stanowią podstawę programowania ogólnego w programie C++. Jako język o jednoznacznie określonym typie, C++ wymaga, aby wszystkie zmienne miały określony typ, albo jawnie zadeklarowane przez programistę lub wywnioskowane przez kompilator. Jednak wiele struktur i algorytmów danych wyglądają tak samo niezależnie od tego, jakiego typu, w którym działają. Szablony umożliwiają definiowanie operacji klasy lub funkcji, a także pozwalają użytkownikom na określenie konkretnych typów, nad którymi te operacje powinny działać.

## <a name="defining-and-using-templates"></a>Definiowanie i używanie szablonów

Szablon jest konstrukcja, która generuje zwykły typ lub funkcję w czasie kompilacji na podstawie argumentów dostarczanych przez użytkownika dla parametrów szablonu. Na przykład można zdefiniować szablon funkcji podobny do tego:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Powyższy kod opisuje szablon funkcji ogólnej z pojedynczym parametrem typu *T*, którego wartość zwracana i parametry wywołania (LHS i RHS) są tego typu. Można nazwać dowolny parametr typu, ale według Konwencji są najczęściej używane wielkie litery. *T* jest parametrem szablonu; słowo kluczowe **TypeName** wskazuje, że ten parametr jest symbolem zastępczym dla typu. Gdy funkcja jest wywoływana, kompilator zamieni każde wystąpienie `T` z argumentem typu konkretnego, który jest określony przez użytkownika lub wywnioskowany przez kompilator. Proces, w którym kompilator generuje klasę lub funkcję z szablonu, jest określany jako *Tworzenie wystąpienia szablonu*; `minimum<int>` to wystąpienie `minimum<T>`szablonu.

W innym miejscu użytkownik może zadeklarować wystąpienie szablonu, który jest wyspecjalizowany dla int. Załóżmy, że get_a () i get_b () są funkcjami, które zwracają int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Jednak ponieważ jest to szablon funkcji, a kompilator może wywnioskować typ `T` z argumentów *a* i *b*, można wywołać go podobnie jak zwykła funkcja:

```cpp
int i = minimum(a, b);
```

Gdy kompilator napotka ostatnią instrukcję, generuje nową funkcję, w której każde wystąpienie *T* w szablonie jest zastępowane **int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Reguły dotyczące sposobu, w jaki kompilator wykonuje potrącenie typów w szablonach funkcji, opiera się na regułach zwykłych funkcji. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie przeciążenia wywołań szablonów funkcji](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Parametry typu

W powyższym szablonie `minimum` należy zauważyć, że parametr typu *t* nie jest kwalifikowany w jakikolwiek sposób, dopóki nie jest używany w parametrach wywołania funkcji, gdzie są dodawane kwalifikatory const i Reference.

Nie ma praktycznego limitu liczby parametrów typu. Rozdziel wiele parametrów przecinkami:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

**Klasa** słowo kluczowe jest równoznaczna z **atrybutem TypeName** w tym kontekście. Poprzedni przykład można wyrazić jako:

```cpp
template <class T, class U, class V> class Foo{};
```

Możesz użyć operatora wielokropka (...), aby zdefiniować szablon, który przyjmuje dowolną liczbę parametrów typu:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Dowolny wbudowany lub zdefiniowany przez użytkownika typ może być używany jako argument typu. Na przykład można użyć [std:: Vector](../standard-library/vector-class.md) w bibliotece standardowej do przechowywania zmiennych typu **int**, **Double**, [std:: String](../standard-library/basic-string-class.md), `MyClass`, **const** `MyClass`*, `MyClass&`i tak dalej. Ograniczenie podstawowe w przypadku korzystania z szablonów polega na tym, że argument typu musi obsługiwać wszystkie operacje, które są stosowane do parametrów typu. Na przykład jeśli wywołamy `minimum` przy użyciu `MyClass`, jak w poniższym przykładzie:

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

Zostanie wygenerowany błąd kompilatora, ponieważ `MyClass` nie zapewnia przeciążenia dla operatora **<** .

Nie istnieje żadne nieodłączne wymaganie, aby argumenty typu dla każdego określonego szablonu należały do tej samej hierarchii obiektów, chociaż można zdefiniować szablon, który wymusza takie ograniczenie. Techniki zorientowane obiektowo można łączyć z szablonami. na przykład można przechowywać pochodną * w\*> bazowej\<.    Zwróć uwagę, że argumenty muszą być wskaźnikami

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Podstawowe wymagania, które `std::vector` i innych kontenerów biblioteki standardowej nakładają się na elementy `T`, są `T` możliwe do przydzielenia kopiowania i kopiowania konstrukcyjną.

## <a name="non-type-parameters"></a>Parametry bez typu

W przeciwieństwie do typów ogólnych w innych językach C# , takich jak C++ i Java, szablony obsługują *Parametry, które nie są typu*, nazywane również parametrami wartości. Na przykład możesz podać stałą wartość całkowitą, aby określić długość tablicy, podobnie jak w przypadku tego przykładu, która jest podobna do klasy [std:: Array](../standard-library/array-class-stl.md) w bibliotece standardowej:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Zwróć uwagę na składnię w deklaracji szablonu. Wartość `size_t` jest przenoszona jako argument szablonu w czasie kompilacji i musi być **const** lub wyrażeniem **constexpr** . Używasz tego przykładu:

```cpp
MyArray<MyClass*, 10> arr;
```

Inne rodzaje wartości, w tym wskaźniki i odwołania, mogą być przesyłane jako parametry bez typu. Na przykład można przekazać wskaźnik do funkcji lub obiektu funkcji, aby dostosować niektóre operacje wewnątrz kodu szablonu.

### <a name="type-deduction-for-non-type-template-parameters"></a>Typ odejmowania parametrów szablonu bez typu

W programie Visual Studio 2017 i nowszych w **/std: c++ 17** tryb kompilator określa typ argumentu szablonu bez typu, który jest zadeklarowany **za pomocą**Auto:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Szablony jako parametry szablonu

Szablon może być parametrem szablonu. W tym przykładzie MyClass2 ma dwa parametry szablonu: parametr TypeName *T* i parametr szablonu *ARR*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Ponieważ sam parametr *ARR* nie ma treści, jego nazwy parametrów nie są zbędne. W rzeczywistości jest to błąd *, aby odwołać się do nazwy*parametru typename lub parametrów klasy z poziomu treści `MyClass2`. Z tego powodu nazwy parametrów typu *ARR*można pominąć, jak pokazano w poniższym przykładzie:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Domyślne argumenty szablonu

Szablony klas i funkcji mogą mieć argumenty domyślne. Gdy szablon ma domyślny argument, można go pozostawić nieokreślony podczas korzystania z niego. Na przykład szablon std:: Vector ma domyślny argument dla alokatora:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

W większości przypadków domyślna klasa std:: Alokator jest akceptowalna, dlatego należy użyć wektora, takiego jak:

```cpp
vector<int> myInts;
```

Ale w razie potrzeby można określić niestandardowy Alokator w następujący sposób:

```cpp
vector<int, MyAllocator> ints;
```

Dla wielu argumentów szablonu wszystkie argumenty po pierwszym argumencie domyślnym muszą mieć argumenty domyślne.

Przy użyciu szablonu, którego wszystkie parametry są domyślne, użyj pustych nawiasów ostrych:

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

W niektórych przypadkach nie jest możliwe lub pożądane, aby szablon mógł definiować dokładnie ten sam kod dla dowolnego typu. Na przykład można zdefiniować ścieżkę kodu, która ma zostać wykonana tylko wtedy, gdy argumentem typu jest wskaźnik lub std:: wstring lub typ pochodzący od określonej klasy bazowej.  W takich przypadkach można zdefiniować *specjalizację* szablonu dla danego typu. Gdy użytkownik tworzy wystąpienie szablonu za pomocą tego typu, kompilator używa specjalizacji do wygenerowania klasy i dla wszystkich innych typów kompilator wybiera bardziej ogólny szablon. Specjalizacje, w których wszystkie parametry są wyspecjalizowane, są *kompletnymi specjalizacjami*. Jeśli tylko niektóre z parametrów są wyspecjalizowane, nazywa się *częściową specjalizacją*.

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

Szablon może mieć dowolną liczbę specjalizacji, tak długo, jak każdy wyspecjalizowany parametr typu jest unikatowy. Tylko szablony klas mogą być częściowo wyspecjalizowane. Wszystkie kompletne i częściowe specjalizacje szablonu muszą być zadeklarowane w tej samej przestrzeni nazw co oryginalny szablon.

Aby uzyskać więcej informacji, zobacz [specjalizacja szablonu](../cpp/template-specialization-cpp.md).
