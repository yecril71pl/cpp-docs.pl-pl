---
title: Funkcje (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/25/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a78f3bf043c08586916a1776806b0a759beb827
ms.sourcegitcommit: d9ee6f777974d031570f4260c9581ea2c81ad875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="functions-c"></a>Funkcje (C++)

Funkcja jest blok kodu, który wykonuje pewne operacje. Funkcja Opcjonalnie można określić parametrów wejściowych umożliwiających wywołań przekazać argumenty do funkcji. Funkcja opcjonalnie może zwracać wartości jako dane wyjściowe. Funkcje są przydatne w przypadku hermetyzując typowych operacji w jeden blok wielokrotnego użytku, najlepiej z nazwę, która wyraźnie opisuje, jak działa funkcja. Następująca funkcja akceptuje dwie liczb całkowitych z obiekt wywołujący i zwraca ich sumy; `a` i `b` są *parametry* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Można wywołać funkcji, lub *o nazwie*, z dowolnej liczby miejsc w programie. Wartości, które są przekazywane do funkcji są *argumenty*, których typy muszą być zgodne z typami parametrów w definicji funkcji.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Nie ma żadnego limitu praktyczne do długości funkcji, ale ma dobrej projektowania dla funkcji wykonujących pojedyncze zadanie dobrze zdefiniowany. Złożonych algorytmów powinny być dzielone na łatwe do zrozumienia funkcje prostsze zawsze, gdy jest to możliwe.

Funkcje, które są zdefiniowane w zakresie klasy są nazywane funkcji elementów członkowskich. W języku C++ w przeciwieństwie do innych języków, funkcja może być także definiowane w zakresie przestrzeni nazw (w tym niejawne globalnej przestrzeni nazw). Takie funkcje są nazywane *wolne funkcji* lub *funkcji nieczłonkowskich*; są często używane w standardowej bibliotece.

Funkcje mogą być *przeciążony*, co oznacza, że różne wersje funkcji mogą takiej samej nazwie, jeśli różnią się one numer i/lub typ parametrów formalnych. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Części deklaracji funkcji

Funkcja minimalnego *deklaracji* składa się z typem zwracanym, nazwy funkcji i lista parametrów (które mogą być puste), oraz opcjonalne słów kluczowych, które zapewniają dodatkowe instrukcje dla kompilatora. Poniższy przykład jest deklaracji funkcji:

```cpp
int sum(int a, int b);
```

Definicja funkcji składa się z deklaracji, wraz z *treści*, która jest cały kod między nawiasami klamrowymi:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklaracji funkcji następuje średnik może występować w wielu miejscach w programie. Musi znajdować się przed wszelkie wywołania tej funkcji w każdej jednostki tłumaczenia. Z definicji funkcji może wystąpić tylko raz w programie zgodnie z jedną regułę definicji (ODR).

Wymagane części deklaracji funkcji są:

1. Zwracany typ, który określa typ wartości, które zwraca funkcja, lub **void** Jeśli wartość nie zostanie zwrócony. W języku C ++ 11 **automatycznie** jest nieprawidłowy typ zwracany instruuje kompilator, aby wnioskować o typie z instrukcji return. Element decltype(auto) również jest dozwolone w języku C ++ 14. Aby uzyskać więcej informacji zobacz wnioskowanie typu w typach zwracać poniżej.

1. Nazwa funkcji, która musi rozpoczynać się od litery lub podkreślenia i nie może zawierać spacji. Ogólnie rzecz biorąc wiodące znaki podkreślenia w nazwach funkcji biblioteki standardowej wskazywać funkcje prywatnego elementu członkowskiego lub niebędący elementem członkowskim funkcje, które nie są przeznaczone do użycia w kodzie.

1. Lista parametrów nawiasu klamrowego rozdzielana, rozdzielone przecinkami zestaw zero lub więcej parametrów, które określają typ oraz opcjonalnie nazwę lokalną za pomocą którego wartości mogą być używane wewnątrz treści funkcji.

Opcjonalne części deklaracji funkcji to:

1. **constexpr**, co oznacza, że zwracana wartość funkcji jest wartością stałą, można obliczyć w czasie kompilacji.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Jego Specyfikacja powiązania **extern** lub **statycznych**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

     Aby uzyskać więcej informacji, zobacz [Program i połączenie](../cpp/program-and-linkage-cpp.md).

1. **wbudowany**, który instruuje kompilator, aby zastąpić co wywołanie funkcji z kodu funkcji. ze śródwierszowaniem może pomóc wydajności w scenariuszach, w którym funkcja wykonuje szybko i jest wywoływana wielokrotnie w sekcji krytycznej wydajność kodu.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

     Aby uzyskać więcej informacji, zobacz [funkcji śródwierszowych](../cpp/inline-functions-cpp.md).

1. A **noexcept** wyrażenie, które określa, czy funkcja może zgłosić wyjątek. W poniższym przykładzie funkcja nie zgłosić wyjątek, jeśli `is_pod` wyrażenie daje w wyniku **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

     Aby uzyskać więcej informacji, zobacz [noexcept](../cpp/noexcept-cpp.md).

1. (Tylko funkcje Członkowskie) Kwalifikatorów cv, które określają, czy funkcja jest **const** lub **volatile**.

1. (Tylko funkcje Członkowskie) **wirtualnego**, **zastąpienia**, lub **końcowego**. **wirtualne** Określa, czy funkcja może zostać przesłonięta w klasie pochodnej. **zastąpienie** oznacza, że funkcja w klasie pochodnej zastępuje funkcję wirtualną. **końcowe** oznacza, że funkcja nie może zostać zastąpione w dowolnym dalsze pochodnej klasy. Aby uzyskać więcej informacji, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).

1. (tylko funkcje Członkowskie) **statycznych** stosowany do elementu członkowskiego funkcji oznacza, że funkcja nie jest skojarzony z wystąpienia obiektu klasy.

1. (Tylko funkcje niestatyczny element członkowski) Kwalifikator ref, określający w kompilatorze, które przeładowanie funkcji, aby zdecydować, kiedy parametr obiektu niejawne (\*to) jest odwołanie do r-wartości, a odwołania do wartości. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md#ref-qualifiers).

Na poniższej ilustracji przedstawiono części definicji funkcji. W obszarze przyciemnione ma treści funkcji.

 ![Części definicji funkcji](../cpp/media/vc38ru1.gif "vc38RU1") części definicji funkcji

## <a name="function-definitions"></a>Definicje funkcji

A *funkcji definicji* składa się z deklaracji i treści funkcji, ujętą w nawiasy klamrowe, zawierającego deklaracje zmiennej, instrukcje i wyrażenia. W poniższym przykładzie przedstawiono definicję funkcji pełną:

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

Zmienne zadeklarowane wewnątrz treści są nazywane zmienne lokalne lub zmiennych lokalnych. Komputery przechodzą poza zakresem funkcji opuszcza; w związku z tym funkcja nigdy nie powinien zwracać odwołanie do lokalnej!

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

Można zadeklarować funkcji członkowskiej jako **const** do określenia, że funkcja nie jest dozwolona w celu zmiany wartości żadnych elementów członkowskich danych w klasie. Od zadeklarowania funkcji członkowskiej jako **const**, pomoc kompilatora, aby wymusić *poprawności const*. Jeśli ktoś przez pomyłkę próbuje zmodyfikować obiekt przy użyciu funkcji zadeklarowany jako **const**, błąd kompilatora. Aby uzyskać więcej informacji, zobacz [const](const-cpp.md).

Zadeklarowania funkcji jako **constexpr** po generuje wartość prawdopodobnie można określić w czasie kompilacji. Funkcja constexpr zazwyczaj wykonuje szybciej niż normalne działanie. Aby uzyskać więcej informacji, zobacz [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Szablony funkcji

Szablonu funkcji jest podobny do szablonu klasy; generuje on konkretne funkcje oparto na argumentach szablonu. W wielu przypadkach szablonu jest w stanie wywnioskować argumentów typu i dlatego nie trzeba jawnie określ je.

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

## <a name="function-parameters-and-arguments"></a>Argumenty i parametry funkcji

Funkcja zawiera rozdzielaną przecinkami listę parametrów zero lub więcej typów, z których każdy ma nazwę, według której jest dostępny w treści funkcji. Szablon funkcji może określić dodatkowe parametry typu lub wartości. Wywołujący argumentów, które są konkretnych wartości, których typy są zgodne z listą parametrów.

Domyślnie argumenty są przekazywane do funkcji wg wartości, co oznacza, że funkcja wysyłana kopia obiekt przekazywany. W przypadku dużych obiektów skopiowanie może być kosztowne i nie zawsze jest konieczne. Aby spowodować argumenty przekazywane przez odwołanie (w szczególności odwołania do wartości), Dodaj kwantyfikatora odwołanie parametru:

```cpp
void DoSomething(std::string& input){...}
```

Gdy funkcja modyfikuje argument, który jest przekazywana przez odwołanie, modyfikuje oryginalny obiekt lokalnej kopii. Aby zapobiec modyfikowanie takich argumentu funkcji, kwalifikują się jako const parametr &:

```cpp
void DoSomething(const std::string& input){...}
```

 **C++ 11:** Aby jawnie obsługiwać argumenty, które są przekazywane przez odwołanie do r-wartości lub odwołania do wartości, umożliwia o podwójnej precyzji znak w parametrze wskazanie uniwersalnych odwołania:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkcja zadeklarowana ze słowem kluczowym pojedynczego **void** w deklaracji parametru listy nie przyjmuje żadnych argumentów, tak długo, jak słowo kluczowe **void** jest pierwszym i tylko element członkowski listy argumentów deklaracji. Argumenty typu **void** w innym miejscu na liście utworzyć błędy. Na przykład:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Należy zauważyć, że jest niedozwolone, aby określić **void** argumentu z wyjątkiem jako obramowane w tym miejscu typów pochodnych typu **void** (takich jak wskaźniki do **void** i tablic **void**) może wystąpić dowolnego miejsca w deklaracjach argumentu.

### <a name="default-arguments"></a>Argumenty domyślne

Ostatni parametr lub parametry podpisu funkcji może być przypisana domyślnego argumentu, co oznacza, że obiekt wywołujący Opuść może w argumencie podczas wywoływania funkcji, jeśli nie chcą, aby określić inną wartość.

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

Funkcja nie może zwracać innej funkcji lub tablicą wbudowane; jednak może zwracać wskaźników do tych typów lub *lambda*, która tworzy obiekt funkcji. Z wyjątkiem dla tych przypadków, funkcja może zwracać wartości dowolnego typu, który znajduje się w zakresie lub mogą zwracać żadnej wartości, w którym to przypadku typem zwracanym jest **void**.

### <a name="trailing-return-types"></a>Końcowe zwracane typy

Typ zwracany "zwykłej" znajduje się po lewej stronie sygnatury funkcji. A *końcowego typu zwracanego* znajduje się na stronie większości prawo podpisu i jest poprzedzony -> — operator. Końcowe zwracane typy są szczególnie przydatne w szablonach funkcji, gdy typ zwracanej wartości zależy od parametrów szablonu.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Gdy **automatycznie** jest używany w połączeniu z końcowego typu zwracanego, po prostu służy jako symbol zastępczy dla dowolnego wyrażenie decltype tworzy, a sama nie jest sprawdzana wnioskowanie typu.


## <a name="function-local-variables"></a>Zmienne lokalne — funkcja

Nosi nazwę zmiennej, która jest zadeklarowana wewnątrz ciała funkcji *zmiennej lokalnej* lub po prostu *lokalnego*. Niestatyczne elementy lokalne są widoczne w treści funkcji tylko i, jeśli są one zadeklarowane na stosie się znaleźć poza zakresem gdy funkcja kończy. Podczas tworzenia zmiennej lokalnej i przywrócić go przez wartość kompilator zwykle można wykonywać optymalizacji zwracanej wartości, aby uniknąć operacje kopiowania niepotrzebne. Jeśli zmienna lokalna zwracać przez odwołanie, kompilator wyświetli ostrzeżenie, ponieważ każda próba użycia tego odwołania przez obiekt wywołujący nastąpi po zniszczeniu lokalnej.

W języku C++ zmiennej lokalnej mogą być zadeklarowane jako statyczne. Zmienna jest widoczna tylko w wewnątrz treści funkcji, ale istnieje jego kopia jednej zmiennej dla wszystkich wystąpień funkcji. Lokalnego obiektu statycznego zostaną zniszczone podczas przerywania określony przez **atexit —**. Jeśli nie można skonstruować statycznego obiektu, ponieważ jego deklaracji pomijana programu przepływu sterowania, nie są podejmowane próby usunąć tego obiektu.

##  <a name="type_deduction"></a> Wnioskowanie typu w typy zwracane (C ++ 14)

W języku C ++ 14, można użyć **automatycznie** nakazać kompilatora można wywnioskować zwracanego typu w treści funkcji bez konieczności podawania końcowego typu zwracanego. Należy pamiętać, że **automatycznie** zawsze deduces zwracane przez wartość. Użyj **auto & &** nakazać kompilator, aby ustalić odwołanie.

W tym przykładzie **automatycznie** będzie ustalona jako kopię wartością stałą wartość sumy lhs i rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Należy pamiętać, że **automatycznie** stałość typu go deduces nie zostaną zachowane. Do przesłania dalej, którego wartość zwrotna musi zachować stałość ref przetwarzaniem argumentów funkcji, można użyć **decltype(auto)** — słowo kluczowe, który używa **decltype** typu reguły wnioskowania i zachowuje wszystkie informacje o typie. **Element decltype(auto)** może służyć jako zwykłej wartości zwracane po lewej stronie, lub jako wartość zwracaną końcowe.

Poniższy przykład (na podstawie kodu z [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), zawiera **decltype(auto)** używane do włączenia doskonałego przekazywania dalej argumentów funkcji zwracanego typu, który nie jest znana, dopóki nie jest szablon utworzona.

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

## <a name="returning-multiple-values-from-a-function"></a>Zwracanie wartości wielu z funkcją

Istnieją różne sposoby więcej niż jedną wartość zwrócona przez funkcję:

1. Hermetyzuj wartości nazwanego obiektu klasy lub struktury. Wymaga definicji klasy lub struktury, które mają być widoczne dla obiekt wywołujący:

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

1. **Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): Użyj strukturę powiązania. Zaletą strukturalnych powiązania jest, że przechowujących zwracanych wartości zmiennych są inicjowane w tym samym czasie, które zostały zgłoszone, w niektórych przypadkach może to znacznie większą wydajność. W tej instrukcji--`auto[x, y, z] = f();`--nawiasy wprowadzić i zainicjuj nazw, które znajdują się w zakresie bloku całą funkcję.

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
    
1. Oprócz przy użyciu sama wartość zwrotną, możesz można "return" wartości, definiując dowolną liczbę parametry używane przekazywany przez odwołanie, tak aby funkcji można zmodyfikować lub zainicjować wartości obiektów, które zawiera obiekt wywołujący. Aby uzyskać więcej informacji, zobacz [argumenty funkcji typu odwołania](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Wskaźniki funkcji

C++ obsługuje wskaźników funkcji w taki sam sposób jak w języku C. Jednak bardziej bezpieczne alternatywą jest zwykle użycie obiektem funkcji.

Zalecane jest **typedef** można deklarować aliasu dla typu wskaźnik funkcji, jeśli deklarowania funkcji zwracającej typ wskaźnika funkcji.  Na przykład

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
