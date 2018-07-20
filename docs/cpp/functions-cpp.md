---
title: Funkcje (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62a46e7d314281bd19773a5c86e70a63f3c93e14
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940330"
---
# <a name="functions-c"></a>Funkcje (C++)

Funkcja jest blokiem kodu, który wykonuje pewne operacje. Funkcja Opcjonalnie możesz zdefiniować parametry wejściowe, które umożliwiają wywołań przekazać argumenty do funkcji. Funkcja opcjonalnie może zwrócić wartość jako dane wyjściowe. Funkcje są przydatne do hermetyzowania typowych operacji w jednym bloku wielokrotnego użytku, najlepiej z nazwą, która wyraźnie opisano, jak działa funkcja. Następująca funkcja akceptuje dwóch liczb całkowitych od wywołującego i zwraca ich suma; *a* i *b* są *parametry* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkcję można wywołać, lub *o nazwie*, z dowolną liczbę miejsc w programie. Wartości, które są przekazywane do funkcji *argumenty*, których typy muszą być zgodne z typami parametrów w definicji funkcji.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Nie ma żadnego limitu praktycznego do długości funkcji, ale dobry projekt ma dla funkcji, które wykonują pojedynczego zadania dobrze zdefiniowane. Złożonych algorytmów powinny być dzielone w łatwych do zrozumienia funkcje prostsze zawsze, gdy jest to możliwe.

Funkcje, które są zdefiniowane w zakresie klasy są nazywane funkcji elementów członkowskich. W języku C++ w przeciwieństwie do innych języków, funkcję można także definiować w zakresie przestrzeni nazw (w tym niejawne globalnej przestrzeni nazw). Takie funkcje są nazywane *bezpłatne funkcje* lub *funkcje nieczłonkowskie*; są często używane w standardowej bibliotece.

Funkcje mogą być *przeciążone*, co oznacza, że różne wersje funkcji mogą udostępnić taką samą nazwę, jeśli różnią się liczbą i/lub typu parametrów formalnych. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Części deklaracji funkcji

Funkcja minimalnej *deklaracji* składa się z typem zwracanym, nazwa funkcji i listą parametrów (które mogą być puste), oraz opcjonalne słowa kluczowe, które zapewniają dodatkowe instrukcje dla kompilatora. Poniższy przykład przedstawia deklarację funkcji:

```cpp
int sum(int a, int b);
```

Definicja funkcji składa się z deklaracji, a także *treści*, czyli cały kod między nawiasami klamrowymi:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklaracja funkcji, a następnie średnikami może pojawić się w wielu miejscach w programie. Musi znajdować się przed wszelkie wywołania tej funkcji w każdej jednostce translacji. Definicja funkcji musi znajdować się tylko raz w programie, zgodnie z jedną regułę definicji (ODR).

Wymagane elementy deklarację funkcji są następujące:

1. Zwracany typ, który określa typ wartości, która zwraca funkcję, lub **void** Jeśli jest zwracana żadna wartość. W języku C ++ 11 **automatycznie** jest prawidłowym typem zwracanym, który nakazuje kompilatorowi wywnioskowania typu z instrukcji return. W języku C ++ 14 decltype(auto) jest również dozwolony. Aby uzyskać więcej informacji zobacz wnioskowanie typu w Return Types poniżej.

1. Nazwy funkcji, która musi zaczynać się literą lub znakiem podkreślenia i nie może zawierać spacji. Ogólnie rzecz biorąc podkreśleniami wiodącymi w nazwach funkcji biblioteki standardowej wskazywać prywatnych elementów członkowskich lub funkcje nieczłonkowskie, które nie są przeznaczone do użycia w kodzie.

1. Lista parametrów nawiasu klamrowego ogranicznik, oddzielone przecinkami zbiór zero lub więcej parametrów, które określają typ i opcjonalnie lokalna nazwa, w którym wartości mogą być używane wewnątrz treści funkcji.

Opcjonalnych części deklaracji funkcji są następujące:

1. **wyrażenia constexpr**, co oznacza, że wartość zwracana przez funkcję jest wartością stałą, może zostać obliczony w czasie kompilacji.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Jego Specyfikacja powiązania **extern** lub **statyczne**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

     Aby uzyskać więcej informacji, zobacz [Program i połączenie](../cpp/program-and-linkage-cpp.md).

1. **wbudowane**, które nakazuje kompilatorowi Zastąp każde wywołanie funkcji sam kod funkcji. wbudowanie umożliwia poprawę wydajności w scenariuszach, gdzie funkcja wykonuje szybko i jest wywoływany kilkakrotnie w wydajność krytycznych części kodu.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

     Aby uzyskać więcej informacji, zobacz [funkcji śródwierszowych](../cpp/inline-functions-cpp.md).

1. A **noexcept** wyrażenie, które określa, czy funkcja może zgłosić wyjątek. W poniższym przykładzie funkcja nie zgłasza wyjątku Jeśli `is_pod` wyrażenie daje w wyniku **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

     Aby uzyskać więcej informacji, zobacz [noexcept](../cpp/noexcept-cpp.md).

1. (Tylko w przypadku funkcji elementów członkowskich) Kwalifikatory cv, które określają, czy funkcja jest **const** lub **volatile**.

1. (Tylko w przypadku funkcji elementów członkowskich) **wirtualnego**, **zastąpienia**, lub **końcowego**. **wirtualne** Określa, czy funkcja może zostać przesłonięta w klasie pochodnej. **Zastąp** oznacza, że funkcja w klasie pochodnej zastępują funkcję wirtualną. **końcowe** oznacza, że funkcja nie może być zastąpiona we wszystkich dalszych klasy pochodnej. Aby uzyskać więcej informacji, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).

1. (tylko w przypadku funkcji elementów członkowskich) **statyczne** stosowany do składowej funkcji oznacza, że funkcja nie jest skojarzony z dowolnego wystąpienia obiektu klasy.

1. (Tylko w przypadku funkcji niestatycznych członka) Kwalifikator ref, który określa kompilatorowi które przeciążenia funkcji, aby wybrać, kiedy parametr obiektu niejawne (\*to) jest odwołaniem rvalue, a odwołanie lvalue. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md#ref-qualifiers).

Poniższa ilustracja ukazuje części definicji funkcji. Zacieniony obszar stanowi treści funkcji.

 ![Części definicji funkcji](../cpp/media/vc38ru1.gif "vc38RU1") części definicji funkcji

## <a name="function-definitions"></a>Definicje funkcji

A *funkcji definicji* składa się z deklaracji i treści funkcji, ujęte w nawiasy klamrowe, który zawiera deklaracje zmiennych, instrukcji i wyrażeń. Poniższy przykład przedstawia definicją pełne funkcji:

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

Zmienne zadeklarowane wewnątrz treści są nazywane, zmienne lokalne lub zmiennych lokalnych. Jeśli funkcja kończy działanie; wykraczają poza zakres w związku z tym funkcja nigdy nie powinna zwrócić odwołanie do lokalnego!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>Funkcje Const i constexpr

Można zadeklarować funkcji składowej jako **const** do określenia, że funkcja nie może zmienić wartości żadnych składowych danych klasy. DEKLARUJĄC funkcji składowej jako **const**, pomoc kompilator, aby wymusić *poprawność const*. Jeśli ktoś przez pomyłkę próbuje zmodyfikować obiekt przy użyciu funkcji deklarowane jako **const**, zgłaszany jest błąd kompilatora. Aby uzyskać więcej informacji, zobacz [const](const-cpp.md).

Zadeklarować funkcję jako **constexpr** kiedy wartość generuje prawdopodobnie można określić w czasie kompilacji. Funkcja constexpr zwykle wykonuje szybciej niż normalne działanie. Aby uzyskać więcej informacji, zobacz [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Szablony funkcji

Szablon funkcji jest podobny do szablonu klasy; generuje on konkretne funkcje, w zależności od argumentów szablonu. W wielu przypadkach szablonu jest w stanie wywnioskować argumentów typu, i w związku z tym nie trzeba jawnie określić je.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Aby uzyskać więcej informacji, zobacz [szablonów funkcji](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Funkcja parametrami i argumentami

Funkcja ma parametr rozdzielaną przecinkami listę zero lub więcej typów, z których każdy ma nazwę, za pomocą którego jest dostępny w treści funkcji. Szablon funkcji może określić dodatkowe parametry typu lub wartości. Obiekt wywołujący przekazuje argumenty, które są konkretne wartości, których typy są zgodne z listą parametrów.

Domyślnie argumenty są przekazywane do funkcji przez wartość, co oznacza, że funkcja otrzymuje kopię obiektu przekazywana. W przypadku dużych obiektów, skopiowanie może być kosztowne i nie zawsze jest konieczne. Aby spowodować, że argumenty przekazywane przez odwołanie (w szczególności odwołanie l-wartości), należy dodać kwantyfikator odwołania do parametru:

```cpp
void DoSomething(std::string& input){...}
```

Gdy funkcja zmodyfikuje argument, który jest przekazywany przez odwołanie, modyfikuje oryginalnego obiektu nie kopię lokalną. Aby uniemożliwić modyfikowanie takich argumentu funkcji, kwalifikują się jako const parametr &:

```cpp
void DoSomething(const std::string& input){...}
```

 **C++ 11:** Aby jawnie obsługiwać argumenty, które są przekazywane przez odwołanie rvalue lub odwołanie lvalue, użyj double-handlowe "i" w parametrze aby wskazać uniwersalny odwołania:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkcja zadeklarowana za pomocą jednego słowa kluczowego **void** w deklaracji parametru listy nie przyjmuje żadnych argumentów, tak długo, jak słowo kluczowe **void** jest pierwszym i tylko członek lista deklaracji argumentów. Argumenty typu **void** innym miejscu na liście generuje błędy. Na przykład:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Należy zauważyć, że, mimo że jest niedozwolone w celu określenia **void** argumentu z wyjątkiem sytuacji, jak podkreślono, typy pochodne typu **void** (takich jak wskaźniki do **void** i tablice **void**) mogą występować w dowolnym miejscu na liście deklaracji argumentów.

### <a name="default-arguments"></a>Argumenty domyślne

Ostatni parametr lub parametry w sygnaturze funkcji może być przypisana domyślnego argumentu, co oznacza, że obiekt wywołujący może opuścić się argument podczas wywoływania funkcji, jeśli nie chcą określić inną wartość.

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

Aby uzyskać więcej informacji, zobacz [argumenty domyślne](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Zwracane typy funkcji

Funkcja nie może zwracać innej funkcji lub tablicą wbudowane; jednak może zwracać wskaźniki do tych typów lub *lambda*, która tworzy obiekt funkcyjny. Z wyjątkiem w takich przypadkach funkcja może zwrócić wartość dowolnego typu, który znajduje się w zakresie lub aplikacja może zwracać żadnej wartości, w którym to przypadku typ zwracany jest **void**.

### <a name="trailing-return-types"></a>Śledzenie typów zwracanych

Typ zwracany "zwykłej" znajduje się po lewej stronie sygnatury funkcji. A *końcowym typem zwracanym* znajduje się na większości prawego boku podpisu i jest poprzedzony przez operator ->. Końcowe zwracane typy są szczególnie użyteczne w szablonów funkcji, gdy typ wartości zwracanej zależy od parametrów szablonu.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Gdy **automatycznie** jest używany w połączeniu z końcowym typem zwracanym, po prostu służy jako symbol zastępczy dla dowolnego wyrażenia decltype tworzy i sam nie powoduje wykonania wnioskowanie typu.


## <a name="function-local-variables"></a>Zmienne lokalne — funkcja

Nosi nazwę zmiennej, która jest zadeklarowana wewnątrz treści funkcji *zmienna lokalna* lub po prostu *lokalnego*. Niestatycznych zmienne lokalne są tylko widoczne wewnątrz treści funkcji, a jeśli są one zadeklarowane na stosie wykraczają poza zakres, gdy funkcja kończy działanie. Podczas konstruowania zmiennej lokalnej, a następnie przywrócić go przez wartość, kompilator będzie mógł zwykle wykonać Optymalizacja zwracanej wartości, aby uniknąć niepotrzebnego kopiowania operacji. Jeśli zmienna lokalna można zwrócić przez odwołanie, kompilator wyświetli ostrzeżenie, ponieważ każda próba użycia tego odwołania przez obiekt wywołujący nastąpi po zniszczeniu lokalnej.

W języku C++ zmienna lokalna może być zadeklarowane jako statyczne. Zmienna jest widoczna tylko w wewnątrz treści funkcji, ale istnieje jego kopia jednej zmiennej dla wszystkich wystąpień funkcji. Lokalnych obiektów statycznych są niszczone podczas przerywania określony przez **atexit**. Jeśli nie można skonstruować obiekt statyczny, ponieważ przepływ sterowania w programie pomijane swojej deklaracji, jest podejmowana próba do zniszczenia obiektu.

##  <a name="type_deduction"></a> Wnioskowanie typu w typy zwracane (C ++ 14)

W języku C ++ 14, można użyć **automatycznie** aby poinstruować kompilator wywnioskuje typ zwracany w treści funkcji bez konieczności podawania końcowym typem zwracanym. Należy pamiętać, że **automatycznie** zawsze wywnioskowuje, że zwracany przez wartość. Użyj **auto & &** można nakazać kompilatorowi na wywnioskowanie odwołania.

W tym przykładzie **automatycznie** zostanie wywnioskowany; dotyczy to jako suma lhs i rhs kopię wartości innej niż stała wartość.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Należy pamiętać, że **automatycznie** stałość typu go wywnioskowuje, że nie zostaną zachowane. W przypadku przekazywania funkcje, których zwracana wartość musi zachować stałość ref-ness argumentów, można użyć **decltype(auto)** — słowo kluczowe, która używa **decltype** reguły wnioskowania typu i zachowuje wszystkie informacje o typie. **Element decltype(auto)** może służyć jako wartości zwracane zwykłych po lewej stronie lub końcową wartość zwracaną.

Poniższy przykład (na podstawie kodu z [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), zawiera **decltype(auto)** używane do włączania Perfekcyjne przekazywanie argumentów funkcji w zwracany typ, który nie jest znany, aż do szablonu wystąpienia.

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
}
```

## <a name="returning-multiple-values-from-a-function"></a>Zwracanie wielu wartości z funkcji

Istnieją różne sposoby, aby zwrócić więcej niż jedną wartość z funkcji:

1. Hermetyzuj wartości w obiekcie o nazwie klasy lub struktury. Wymaga definicji klasy lub struktury były widoczne dla obiektu wywołującego:

    ```cpp
    #include <string>
    #include <iostream>
    
    using namespace std;
    
    struct S
    {
        string name;
        int num;
    };
    
    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }
    
    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```
    
1. Zwraca obiekt std::tuple lub std::pair:

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>
    
    using namespace std;
        
    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    
    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;
     
        // --or--
    
        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;
    
        return 0;
    }
    ```

1. **Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Użyj strukturalnego powiązania. Zalet powiązań strukturalnych to, że zmienne, które przechowują wartości zwracane są inicjowane w tym samym czasie, które są deklarowane, co w niektórych przypadkach może być znacznie bardziej efektywne. W niniejszych zasadach--`auto[x, y, z] = f();`--nawiasy wprowadzają i zainicjuj nazw, które znajdują się w zakresie bloku całej funkcji.

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>
    
    using namespace std;
    
    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };
    
    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }
    
    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;
    
        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```
    
1. Tylko samą wartość zwracana, użytkownik może "return" wartości, definiując dowolna liczba parametrów do użycia przekazywany przez odwołanie, aby zmodyfikować lub zainicjować wartości obiektów, które zapewnia obiekt wywołujący funkcję. Aby uzyskać więcej informacji, zobacz [argumenty funkcji typu odwołania](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Wskaźniki funkcji

Język C++ obsługuje wskaźników funkcji w taki sam sposób, jak język C. Jednak bardziej bezpieczny alternatywą jest zwykle użyć obiektu funkcyjnego.

Zalecane jest, **typedef** być wykorzystywane do deklarowania aliasu dla typu wskaźnika funkcji, jeśli deklarowana jest funkcja, która zwraca typ wskaźnika funkcji.  Na przykład

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Jeśli to nie nastąpi, poprawna składnia deklaracji funkcji może być wyprowadzona ze składni deklaratora dla wskaźnika funkcji przez zastąpienie identyfikatora (`fp` w powyższym przykładzie) nazwą i listą argumentów funkcji, w następujący sposób:

```cpp
int (*myFunction(char* s))(int);
```

Poprzednia deklaracja jest równoważna z deklaracją przy użyciu elementu typedef powyżej.

## <a name="see-also"></a>Zobacz też

- [Przeładowywanie funkcji](../cpp/function-overloading.md)
- [Funkcje ze zmiennymi listami argumentów](../cpp/functions-with-variable-argument-lists-cpp.md)
- [Jawnie domyślne i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md)
- [Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)
- [Argumenty domyślne](../cpp/default-arguments.md)
- [Funkcje śródwierszowe](../cpp/inline-functions-cpp.md)
