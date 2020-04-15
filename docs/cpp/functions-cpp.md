---
title: Funkcje (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375734"
---
# <a name="functions-c"></a>Funkcje (C++)

Funkcja jest blok kodu, który wykonuje niektóre operacji. Funkcja może opcjonalnie zdefiniować parametry wejściowe, które umożliwiają wywołującym przekazywanie argumentów do funkcji. Funkcja może opcjonalnie zwrócić wartość jako dane wyjściowe. Funkcje są przydatne do hermetyzacji typowych operacji w jednym bloku wielokrotnego użytku, najlepiej o nazwie, która wyraźnie opisuje, co robi funkcja. Następująca funkcja akceptuje dwie liczby całkowite od wywołującego i zwraca ich sumę; *a* i *b* są *parametrami* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkcję można wywołać lub *wywołać*z dowolnej liczby miejsc w programie. Wartości, które są przekazywane do funkcji są *argumenty*, których typy muszą być zgodne z typami parametrów w definicji funkcji.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Nie ma praktycznego limitu długości funkcji, ale dobry projekt ma na celu funkcje, które wykonują jedno dobrze zdefiniowane zadanie. Złożone algorytmy powinny być podzielone na łatwe do zrozumienia prostsze funkcje, gdy tylko jest to możliwe.

Funkcje, które są zdefiniowane w zakresie klasy są nazywane funkcjami elementów członkowskich. W języku C++, w przeciwieństwie do innych języków, funkcja może być również zdefiniowana w zakresie obszaru nazw (w tym niejawnej globalnej przestrzeni nazw). Takie funkcje są nazywane *wolnymi funkcjami* lub *funkcjami niebędącymi członkami;* są one szeroko stosowane w bibliotece standardowej.

Funkcje mogą być *przeciążone,* co oznacza, że różne wersje funkcji mogą mieć tę samą nazwę, jeśli różnią się liczbą i/lub typem parametrów formalnych. Aby uzyskać więcej informacji, zobacz [Przeciążanie funkcji](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Części deklaracji funkcji

Deklaracja funkcji minimalne *składa* się z typu zwracanego, nazwa funkcji i listy parametrów (które mogą być puste), wraz z opcjonalnymi słowami kluczowymi, które zapewniają dodatkowe instrukcje do kompilatora. Poniższy przykład jest deklaracją funkcji:

```cpp
int sum(int a, int b);
```

Definicja funkcji składa się z deklaracji oraz *treści*, która jest całym kodem między nawiasami klamrowymi:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklaracja funkcji, po której następuje średnik może pojawić się w wielu miejscach w programie. Musi pojawić się przed wywołaniami tej funkcji w każdej jednostce tłumaczenia. Definicja funkcji musi pojawić się tylko raz w programie, zgodnie z regułą Jednej Definicji (ODR).

Wymagane części deklaracji funkcji to:

1. Zwracany typ, który określa typ wartości zwracanej przez funkcję lub **void,** jeśli nie jest zwracana żadna wartość. W języku C++ 11 **auto** jest prawidłowym typem zwracanym, który instruuje kompilatora, aby wywnioskować typ z instrukcji return. W języku C++14 dozwolone jest również decltype(auto). Aby uzyskać więcej informacji, zobacz Typ potrącenia w typach zwrotów poniżej.

1. Nazwa funkcji, która musi zaczynać się od litery lub podkreślenia i nie może zawierać spacji. Ogólnie rzecz biorąc wiodące podkreślenia w nazwach funkcji biblioteki standardowej wskazują prywatne funkcje członkowskie lub funkcje niebędące członkami, które nie są przeznaczone do użycia przez kod.

1. Lista parametrów, rozdzielany, oddzielony przecinkami zestaw parametrów zero lub więcej, które określają typ i opcjonalnie nazwę lokalną, za pomocą której wartości mogą być dostępne wewnątrz treści funkcji.

Opcjonalne części deklaracji funkcji to:

1. `constexpr`, co wskazuje, że zwracana wartość funkcji jest wartością stałą, można obliczyć w czasie kompilacji.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Jego specyfikacja powiązania, **extern** lub **statyczne**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Aby uzyskać więcej informacji, zobacz [Jednostki tłumaczenia i powiązanie](../cpp/program-and-linkage-cpp.md).

1. **inline**, który nakazuje kompilatorowi, aby zastąpić każde wywołanie funkcji z samego kodu funkcji. inlining może pomóc w wydajności w scenariuszach, w których funkcja wykonuje szybko i jest wywoływana wielokrotnie w sekcji kodu o krytycznym znaczeniu dla wydajności.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Aby uzyskać więcej informacji, zobacz [Funkcje wbudowane](../cpp/inline-functions-cpp.md).

1. Wyrażenie, `noexcept` które określa, czy funkcja może zgłosić wyjątek. W poniższym przykładzie funkcja nie zgłasza `is_pod` wyjątek, jeśli wyrażenie ocenia **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Aby uzyskać więcej informacji, zobacz [noexcept](../cpp/noexcept-cpp.md).

1. (Tylko funkcje członkowskie) Kwalifikatory cv, które określają, czy funkcja jest **const** lub **volatile**.

1. (Tylko funkcje członkowskie) **wirtualne** `override`, `final`lub . **virtual** określa, że funkcja może zostać zastąpiona w klasie pochodnej. `override`oznacza, że funkcja w klasie pochodnej zastępuje funkcję wirtualną. `final`oznacza, że funkcja nie może być zastąpiona w żadnej dalszej klasie pochodnej. Aby uzyskać więcej informacji, zobacz [Funkcje wirtualne](../cpp/virtual-functions.md).

1. (tylko funkcje członkowskie) **statyczne** stosowane do funkcji elementu członkowskiego oznacza, że funkcja nie jest skojarzona z żadnymi wystąpieniami obiektu klasy.

1. (Tylko funkcje elementów elementów niestatycznych) Ref-kwalifikator, który określa kompilatora, które przeciążenie funkcji\*do wyboru, gdy parametr obiektu niejawnego (this) jest odwołanie rvalue vs odwołanie lvalue. Aby uzyskać więcej informacji, zobacz [Przeciążanie funkcji](function-overloading.md#ref-qualifiers).

Na poniższej ilustracji przedstawiono części definicji funkcji. Zacienionym obszarem jest obiekt funkcyjny.

![Części definicji funkcji](../cpp/media/vc38ru1.gif "Części definicji funkcji") <br/>
Części definicji funkcji

## <a name="function-definitions"></a>Definicje funkcji

*Definicja funkcji* składa się z deklaracji i treści funkcji, ujętej w nawiasy klamrowe, która zawiera deklaracje zmiennych, instrukcje i wyrażenia. W poniższym przykładzie przedstawiono pełną definicję funkcji:

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

Zmienne zadeklarowane wewnątrz obiektu są nazywane zmiennymi lokalnymi lub lokalnymi. Wychodzą one poza zakres po zamknięciu funkcji; w związku z tym funkcja nigdy nie powinna zwracać odwołania do lokalnego!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>const i constexpr, funkcje

Można zadeklarować funkcję elementu członkowskiego jako **const,** aby określić, że funkcja nie może zmieniać wartości żadnych elementów członkowskich danych w klasie. Deklarując funkcję elementu członkowskiego jako **const**, można pomóc kompilatorowi wymusić *const-correctness*. Jeśli ktoś omyłkowo próbuje zmodyfikować obiekt przy użyciu funkcji zadeklarowanej jako **const**, zgłaszany jest błąd kompilatora. Aby uzyskać więcej informacji, zobacz [const](const-cpp.md).

Zadeklaruj funkcję, jak `constexpr` wtedy, gdy wartość, która produkuje może być ewentualnie określone w czasie kompilacji. Funkcja constexpr zazwyczaj wykonuje szybciej niż zwykła funkcja. Aby uzyskać więcej informacji, zobacz [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Szablony funkcji

Szablon funkcji jest podobny do szablonu klasy; generuje konkretne funkcje na podstawie argumentów szablonu. W wielu przypadkach szablon jest w stanie wywnioskować argumenty typu i dlatego nie jest konieczne jawne ich określenie.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Aby uzyskać więcej informacji, zobacz [Szablony funkcji](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Parametry i argumenty funkcji

Funkcja ma listę parametrów oddzielonych przecinkami zero lub więcej typów, z których każdy ma nazwę, za pomocą której można uzyskać dostęp wewnątrz treści funkcji. Szablon funkcji może określać dodatkowe parametry typu lub wartości. Wywołujący przekazuje argumenty, które są konkretne wartości, których typy są zgodne z listą parametrów.

Domyślnie argumenty są przekazywane do funkcji przez wartość, co oznacza, że funkcja odbiera kopię obiektu przekazywanych. W przypadku dużych obiektów tworzenie kopii może być kosztowne i nie zawsze jest konieczne. Aby spowodować, że argumenty mają być przekazywane przez odwołanie (w szczególności odwołanie lvalue), należy dodać kwantyfikatora odwołania do parametru:

```cpp
void DoSomething(std::string& input){...}
```

Gdy funkcja modyfikuje argument, który jest przekazywany przez odwołanie, modyfikuje oryginalny obiekt, a nie kopię lokalną. Aby zapobiec modyfikowaniu takiego argumentu przez funkcję, należy zakwalifikować parametr jako const&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Aby jawnie obsługiwać argumenty, które są przekazywane przez odwołanie rvalue lub odwołanie lvalue, należy użyć double-ampersand na parametr, aby wskazać uniwersalne odwołanie:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkcja zadeklarowana z pojedynczym słowem kluczowym **void** na liście deklaracji parametrów nie przyjmuje żadnych argumentów, o ile słowo kluczowe **void** jest pierwszym i jedynym elementem listy deklaracji argumentów. Argumenty typu **void** w innym miejscu na liście powodują błędy. Przykład:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Należy zauważyć, że podczas gdy jest to niezgodne z prawem, aby określić **argument void** z wyjątkiem opisanych w tym miejscu, typy pochodzące z typu **void** (takie jak wskaźniki do **void** i tablice **void**) mogą pojawić się wszędzie tam, gdzie lista deklaracji argumentów.

### <a name="default-arguments"></a>Argumenty domyślne

Ostatni parametr lub parametry w podpisie funkcji mogą być przypisane domyślny argument, co oznacza, że wywołujący może pominąć argument podczas wywoływania funkcji, chyba że chcą określić inną wartość.

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

Aby uzyskać więcej informacji, zobacz [Argumenty domyślne](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Typy zwracania funkcji

Funkcja może nie zwracać innej funkcji lub wbudowanej tablicy; jednak może zwracać wskaźniki do tych typów lub *lambda*, który tworzy obiekt funkcji. Z wyjątkiem tych przypadków funkcja może zwrócić wartość dowolnego typu, który jest w zakresie lub może zwrócić żadną wartość, w którym to przypadku typ zwracany jest **nieważny**.

### <a name="trailing-return-types"></a>Końcowe typy zwrotów

"Zwykły" typ zwracany znajduje się po lewej stronie podpisu funkcji. *Końcowy typ powrotu* znajduje się po prawej stronie podpisu i jest poprzedzony operatorem ->. Końcowe typy zwracane są szczególnie przydatne w szablonach funkcji, gdy typ zwracanej wartości zależy od parametrów szablonu.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Gdy **auto** jest używany w połączeniu z końcowego typu zwracanego, po prostu służy jako symbol zastępczy dla niezależnie od wyrażenia decltype produkuje i nie wykonuje dedukcji typu.

## <a name="function-local-variables"></a>Funkcje zmienne lokalne

Zmienna zadeklarowana wewnątrz treści funkcji jest nazywana *zmienną lokalną* lub po prostu *lokalną*. Niestatyczne lokalne są widoczne tylko wewnątrz treści funkcji i, jeśli są one zadeklarowane na stosie wyjść z zakresu po zamknięciu funkcji. Podczas konstruowania zmiennej lokalnej i zwracać ją według wartości, kompilator zwykle można wykonać *optymalizację nazwanej wartości zwracanej,* aby uniknąć niepotrzebnych operacji kopiowania. Jeśli zwrócisz zmienną lokalną przez odwołanie, kompilator wyda ostrzeżenie, ponieważ każda próba użycia tego odwołania przez wywołującego nastąpi po zniszczeniu lokalnego.

W języku C++ zmienna lokalna może być zadeklarowana jako statyczna. Zmienna jest widoczna tylko wewnątrz treści funkcji, ale istnieje pojedyncza kopia zmiennej dla wszystkich wystąpień funkcji. Lokalne obiekty statyczne są niszczone `atexit`podczas zakończenia określonego przez . Jeśli obiekt statyczny nie został skonstruowany, ponieważ przepływ sterowania programu pominął jego deklarację, nie podejmowana jest żadna próba zniszczenia tego obiektu.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Typ potrącenia w typach zwrotów (C++14)

W języku C++ 14 można użyć **auto** poinstruować kompilatora, aby wywnioskować typ zwracany z treści funkcji bez konieczności podawania końcowego typu zwracanego. Należy zauważyć, że **auto** zawsze wywniuje do zwrotu według wartości. Służy `auto&&` do poinstruowania kompilatora, aby wywnił odwołanie.

W tym przykładzie **auto** zostanie wydedukowane jako kopia wartości non-const sumy lhs i rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Należy zauważyć, że **auto** nie zachowuje const-ness typu, który wywnieduje. W przypadku funkcji przekazywania, których wartość zwracana musi zachować const-ness lub ref-ness jego argumentów, można użyć słowa kluczowego **decltype(auto),** który używa reguł wnioskowania typu **decltype** i zachowuje wszystkie informacje o typie. **decltype(auto)** może być używany jako zwykła wartość zwracana po lewej stronie lub jako końcowa wartość zwracana.

Poniższy przykład (na podstawie kodu z [N3493](https://wg21.link/n3493)), pokazuje **decltype(auto)** używane do umożliwienia doskonałego przekazywania argumentów funkcji w typie zwracanym, który nie jest znany, dopóki szablon nie zostanie skonkretyzowany.

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
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Zwracanie wielu wartości z funkcji

Istnieją różne sposoby zwracania więcej niż jednej wartości z funkcji:

1. Hermetyzowanie wartości w nazwanej klasie lub obiekcie struktury. Wymaga, aby definicja klasy lub struktury była widoczna dla wywołującego:

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

1. Zwraca obiekt std::krotka lub std::pair:

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

1. **Visual Studio 2017 w wersji 15.3 i nowszej** (dostępne z [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Użyj powiązania strukturalne. Zaletą powiązania strukturalne jest to, że zmienne, które przechowują zwracane wartości są inicjowane w tym samym czasie są one zadeklarowane, co w niektórych przypadkach może być znacznie bardziej wydajne. W tej instrukcji`auto[x, y, z] = f();`-- -- nawiasy wprowadzają i inicjują nazwy, które są w zakresie dla całego bloku funkcji.

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

1. Oprócz używania samej wartości zwracanej można "zwracać" wartości, definiując dowolną liczbę parametrów, aby użyć pass-by-reference, aby funkcja mogła modyfikować lub inicjować wartości obiektów, które udostępnia obiekt wywołujący. Aby uzyskać więcej informacji, zobacz [Argumenty funkcji typu odwołania](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Wskaźniki funkcji

C++ obsługuje wskaźniki funkcji w taki sam sposób jak język C. Jednak bardziej bezpieczna alternatywa jest zwykle do korzystania z obiektu funkcji.

Zaleca się, aby **typedef** służyć do deklarowania aliasu dla typu wskaźnika funkcji, jeśli deklarują funkcję, która zwraca typ wskaźnika funkcji.  Na przykład:

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

[Przeładowywanie funkcji](../cpp/function-overloading.md)<br/>
[Funkcje ze zmiennymi listami argumentów](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Jawnie domyślne i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Argumenty domyślne](../cpp/default-arguments.md)<br/>
[Funkcje wbudowane](../cpp/inline-functions-cpp.md)
