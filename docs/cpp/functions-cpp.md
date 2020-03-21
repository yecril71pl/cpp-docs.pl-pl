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
ms.openlocfilehash: fbc8b108ea958f526156e7f81a75a2918a0a8903
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076157"
---
# <a name="functions-c"></a>Funkcje (C++)

Funkcja jest blokiem kodu, który wykonuje pewne operacje. Funkcja może opcjonalnie definiować parametry wejściowe, które umożliwiają wywołującym przekazywanie argumentów do funkcji. Funkcja może opcjonalnie zwrócić wartość jako dane wyjściowe. Funkcje są przydatne do hermetyzacji typowych operacji w jednym bloku wielokrotnego użytku, najlepiej z nazwą, która jasno opisuje działanie funkcji. Następująca funkcja akceptuje dwie liczby całkowite od wywołującego i zwraca ich sumę; *a* i *b* są *parametrami* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkcja może być wywoływana lub *wywoływana*z dowolnej liczby miejsc w programie. Wartości, które są przekazane do funkcji, są *argumentami*, których typy muszą być zgodne z typami parametrów w definicji funkcji.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Nie ma praktycznego limitu długości funkcji, ale dobry projekt dotyczy funkcji, które wykonują jedno dobrze zdefiniowane zadanie. Złożone algorytmy należy podzielić na łatwe w obsłudze prostsze funkcje, jeśli jest to możliwe.

Funkcje, które są zdefiniowane w zakresie klasy, są nazywane funkcjami składowymi. W C++, w przeciwieństwie do innych języków, funkcja może być również zdefiniowana w zakresie przestrzeni nazw (łącznie z niejawną globalną przestrzenią nazw). Takie funkcje są nazywane *funkcjami bezpłatnymi* lub nienależącymi *do elementów członkowskich*. są one używane w szerokim stopniu w standardowej bibliotece.

Funkcje mogą być *przeciążone*, co oznacza, że różne wersje funkcji mogą współużytkować tę samą nazwę, jeśli różnią się one liczbą i/lub typem parametrów formalnych. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Części deklaracji funkcji

*Deklaracja* minimalnej funkcji składa się z typu zwracanego, nazwy funkcji i listy parametrów (które mogą być puste) wraz z opcjonalnymi słowami kluczowymi, które zawierają dodatkowe instrukcje do kompilatora. Poniższy przykład jest deklaracją funkcji:

```cpp
int sum(int a, int b);
```

Definicja funkcji składa się z deklaracji oraz *treści*, która jest wszystkimi kodami między nawiasami klamrowymi:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklaracja funkcji, a po niej średnik może pojawić się w wielu miejscach w programie. Musi występować przed dowolnymi wywołaniami tej funkcji w każdej jednostce translacji. Definicja funkcji musi wystąpić tylko raz w programie, zgodnie z jedną z reguł definicji (ODR).

Wymagane części deklaracji funkcji są:

1. Zwracany typ, który określa typ wartości zwracanej przez funkcję, lub **void** , jeśli żadna wartość nie jest zwracana. W języku C++ 11, autojest prawidłowym zwracanym **typem, który** instruuje kompilator, aby wywnioskować typ z instrukcji return. W języku C++ 14 jest również dozwolone decltype (Auto). Aby uzyskać więcej informacji, zobacz Typ odejmowania w poniższych typach zwracanych poniżej.

1. Nazwa funkcji, która musi zaczynać się literą lub podkreśleniem i nie może zawierać spacji. Ogólnie rzecz biorąc, wiodące znaki podkreślenia w nazwach funkcji biblioteki standardowej wskazują prywatne funkcje Członkowskie lub funkcje nieczłonkowskie, które nie są przeznaczone do użytku w kodzie.

1. Lista parametrów, rozdzielana przecinkami, zestaw oddzielony przecinkiem zero lub więcej parametrów, które określają typ i opcjonalnie nazwę lokalną, do której można uzyskać dostęp do wartości wewnątrz treści funkcji.

Opcjonalne części deklaracji funkcji są:

1. `constexpr`, co oznacza, że wartość zwracana przez funkcję jest wartością stałą można obliczyć w czasie kompilacji.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Jej Specyfikacja powiązania, **extern** lub **static**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Aby uzyskać więcej informacji, zobacz [jednostki translacji i powiązania](../cpp/program-and-linkage-cpp.md).

1. **inline**, która instruuje kompilator, aby zamieniać każde wywołanie funkcji z samym kodem funkcji. Funkcja tworzenia konspektu może pomóc w wykonywaniu takich operacji w scenariuszach, w których funkcje są wykonywane szybko i są wywoływane wielokrotnie w sekcji krytycznej dla wydajności kodu.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Aby uzyskać więcej informacji, zobacz [funkcje wbudowane](../cpp/inline-functions-cpp.md).

1. Wyrażenie `noexcept`, które określa, czy funkcja może zgłosić wyjątek. W poniższym przykładzie funkcja nie zgłasza wyjątku, jeśli wyrażenie `is_pod` ma **wartość true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Aby uzyskać więcej informacji, zobacz [noexcept](../cpp/noexcept-cpp.md).

1. (Tylko funkcje członkowskie) Kwalifikatory CV, które określają, czy funkcja jest **stała** , czy **nietrwała**.

1. (Tylko funkcje członkowskie) **Virtual**, `override`lub `final`. **wirtualne** określa, że funkcja może zostać przesłonięta w klasie pochodnej. `override` oznacza, że funkcja w klasie pochodnej zastępuje funkcję wirtualną. `final` oznacza, że funkcja nie może zostać zastąpiona w żadnej dalszej klasie pochodnej. Aby uzyskać więcej informacji, zobacz [funkcje wirtualne](../cpp/virtual-functions.md).

1. (tylko funkcje członkowskie) **statyczna** zastosowana do funkcji składowej oznacza, że funkcja nie jest skojarzona z żadnym wystąpieniem obiektu klasy.

1. (Tylko niestatyczne funkcje członkowskie) Kwalifikator ref, który określa kompilator, który przeciążać funkcję do wyboru, gdy parametr obiektu niejawnego (\*to) jest odwołaniem rvalue a odwołaniem do lvalue. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md#ref-qualifiers).

Na poniższej ilustracji przedstawiono części definicji funkcji. Zacieniony obszar to treść funkcji.

![Części definicji funkcji](../cpp/media/vc38ru1.gif "Części definicji funkcji") <br/>
Części definicji funkcji

## <a name="function-definitions"></a>Definicje funkcji

*Definicja funkcji* składa się z deklaracji i treści funkcji ujętej w nawiasy klamrowe, która zawiera deklaracje zmiennych, instrukcje i wyrażenia. Poniższy przykład przedstawia pełną definicję funkcji:

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

Zmienne zadeklarowane wewnątrz treści są nazywane zmiennymi lokalnymi lub elementami lokalnymi. Wykraczają poza zakres, gdy funkcja kończy działanie; w związku z tym funkcja nigdy nie powinna zwracać odwołania do lokalnego.

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>funkcje const i constexpr

Można zadeklarować funkcję członkowską jako **stałą** , aby określić, że funkcja nie może zmienić wartości żadnych elementów członkowskich danych w klasie. Deklarując funkcję członkowską jako **stałą**, możesz pomóc kompilatorowi wymusić *prawidłowość stałych*. Jeśli ktoś omyłkowo próbuje zmodyfikować obiekt przy użyciu funkcji zadeklarowanej jako **const**, zostanie zgłoszony błąd kompilatora. Aby uzyskać więcej informacji, zobacz [const](const-cpp.md).

Zadeklaruj funkcję jako `constexpr`, gdy wartość, którą produkuje, może być ustalona w czasie kompilacji. Funkcja constexpr zazwyczaj wykonuje się szybciej niż zwykła funkcja. Aby uzyskać więcej informacji, zobacz [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Szablony funkcji

Szablon funkcji jest podobny do szablonu klasy; generuje konkretne funkcje na podstawie argumentów szablonu. W wielu przypadkach szablon może wywnioskować argumenty typu i w związku z tym nie jest konieczne jawne określenie ich.

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

Funkcja ma listę parametrów z wartościami rozdzielanymi przecinkami (zero lub więcej), z których każdy ma nazwę, za pomocą której można uzyskać dostęp w treści funkcji. Szablon funkcji może określać dodatkowe parametry typu lub wartości. Obiekt wywołujący przekazuje argumenty, które są konkretnymi wartościami, których typy są zgodne z listą parametrów.

Domyślnie argumenty są przekazywane do funkcji przez wartość, co oznacza, że funkcja otrzymuje kopię przekazanego obiektu. W przypadku dużych obiektów wykonywanie kopii może być kosztowne i nie zawsze jest konieczne. Aby sprawić, że argumenty mają być przekazane przez odwołanie (w przypadku odwołania lvalue), Dodaj kwantyfikator referencyjny do parametru:

```cpp
void DoSomething(std::string& input){...}
```

Gdy funkcja modyfikuje argument, który jest przesyłany przez odwołanie, modyfikuje oryginalny obiekt, a nie kopię lokalną. Aby zapobiec modyfikowaniu takiego argumentu przez funkcję, Zakwalifikuj parametr jako const &:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Aby jawnie obsługiwać argumenty, które są przekazane przez rvalue-Reference lub lvalue-Reference, należy użyć podwójnego znaku "w parametrze", aby wskazać uniwersalne odwołanie:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkcja zadeklarowana za pomocą słowa kluczowego Single o wartości **void** na liście deklaracji parametrów nie przyjmuje żadnych argumentów, o ile słowo kluczowe **void** jest pierwszym i jedynym członkiem listy deklaracji argumentów. Argumenty typu **void** w innym miejscu na liście powodują błędy. Na przykład:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Należy pamiętać, że chociaż nie jest dozwolone określenie argumentu **void** , z wyjątkiem sytuacji, typy pochodne od typu **void** (takie jak wskaźniki do **void** i tablice **void**) mogą pojawić się w dowolnym miejscu listy deklaracji argumentów.

### <a name="default-arguments"></a>Argumenty domyślne

Ostatni parametr lub parametry w sygnaturze funkcji może mieć przypisany argument domyślny, co oznacza, że obiekt wywołujący może opuścić argument podczas wywoływania funkcji, chyba że chcą określić inną wartość.

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

Funkcja nie może zwracać innej funkcji ani wbudowanej tablicy; może jednak zwracać wskaźniki do tych typów lub *wyrażenia lambda*, które tworzy obiekt Function. Z wyjątkiem tych przypadków funkcja może zwrócić wartość dowolnego typu, który znajduje się w zakresie lub nie może zwracać żadnej wartości, w tym przypadku typ zwracany to **void**.

### <a name="trailing-return-types"></a>Końcowe zwracane typy

"Zwykły" typ zwracany znajduje się po lewej stronie sygnatury funkcji. *Końcowy typ zwracany* znajduje się po prawej stronie podpisu i jest poprzedzony operatorem->. Końcowe typy zwracane są szczególnie przydatne w szablonach funkcji, gdy typ wartości zwracanej zależy od parametrów szablonu.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Gdy **Funkcja** autojest używana w połączeniu z końcowym typem zwracanym, pełni funkcję jako symbol zastępczy dla dowolnego wyrażenia decltype i nie wykonuje odejmowania typu.

## <a name="function-local-variables"></a>Zmienne lokalne funkcji

Zmienna zadeklarowana wewnątrz treści funkcji jest nazywana *zmienną lokalną* lub po prostu *lokalną*. Niestatyczne elementy lokalne są widoczne tylko wewnątrz treści funkcji i, jeśli są zadeklarowane na stosie, wykraczają poza zakres, gdy funkcja kończy działanie. Gdy tworzysz zmienną lokalną i zwracasz ją przez wartość, kompilator może zazwyczaj wykonać *optymalizację nazwanej wartości zwracanej* , aby uniknąć niepotrzebnych operacji kopiowania. Jeśli zmienna lokalna zostanie zwrócona przez odwołanie, kompilator wygeneruje ostrzeżenie, ponieważ jakakolwiek próba użycia tego odwołania przez obiekt wywołujący będzie miała miejsce po zniszczeniu elementu lokalnego.

W C++ zmiennej lokalnej może być zadeklarowany jako statyczny. Zmienna jest widoczna tylko wewnątrz treści funkcji, ale jedna kopia zmiennej istnieje dla wszystkich wystąpień funkcji. Lokalne obiekty statyczne są niszczone podczas kończenia określonego przez `atexit`. Jeśli obiekt statyczny nie został skonstruowany, ponieważ przepływ sterowania programu został pominięty w jego deklaracji, nie podjęto próby zniszczenia tego obiektu.

##  <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Typ odejmowania w typach zwracanych (C++ 14)

W języku C++ 14 **można użyć funkcji** Auto, aby nakazać kompilatorowi wywnioskowanie typu zwracanego z treści funkcji bez konieczności podawania końcowego typu zwracanego. Należy pamiętać, że **Funkcja autowypełnia** zawsze wartość zwracaną przez. Użyj `auto&&`, aby nakazać kompilatorowi wywnioskowanie odwołania.

W tym przykładzie **Funkcja Autokorekty** zostanie wywnioskowana jako kopia niebędąca wartością stałą sumy wartości LHS i Rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Należy pamiętać, że **Funkcja** autostałość nie zachowuje typu const-deargumentd. W przypadku funkcji przekazywania, których wartość zwracana musi zachować stałą-stałość lub ref-stałość argumentów, można użyć słowa kluczowego **decltype (Auto)** , w którym są używane reguły wnioskowania typu **decltype** i zachowuje wszystkie informacje o typie. **decltype (Auto)** może być używana jako zwykła wartość zwrotna po lewej stronie lub jako końcowa wartość zwracana.

Poniższy przykład (oparty na kodzie z [N3493](https://wg21.link/n3493)) pokazuje, że **decltype (Auto)** służy do włączania doskonałego przekazywania argumentów funkcji w zwracanym typie, który nie jest znany do momentu wystąpienia szablonu.

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

1. Hermetyzuj wartości w nazwanej klasie lub obiekcie struktury. Wymaga widoczności klasy lub struktury dla obiektu wywołującego:

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

1. Zwróć obiekt powietrza std:: krotek lub std::p:

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

1. **Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): Użyj powiązań strukturalnych. Zalety powiązań strukturalnych polega na tym, że zmienne, które przechowują wartości zwracane są inicjowane w tym samym czasie, które są zgłaszane, co w niektórych przypadkach może być znacznie bardziej wydajne. W tej instrukcji--`auto[x, y, z] = f();`--nawiasy wprowadzają i inicjują nazwy, które są w zakresie dla całego bloku funkcji.

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

1. Oprócz używania wartości zwracanej można "zwrócić" wartości przez zdefiniowanie dowolnej liczby parametrów do użycia przekazywania przez odwołanie, aby funkcja mogła modyfikować lub inicjować wartości obiektów, które zapewnia obiekt wywołujący. Aby uzyskać więcej informacji, zobacz [argumenty funkcji typu odwołania](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Wskaźniki funkcji

C++obsługuje wskaźniki funkcji w taki sam sposób, jak język C. Jednak bardziej bezpieczny dla typu alternatywą jest zwykle użycie obiektu Function.

Zaleca się, aby **element typedef** był używany do deklarowania aliasu dla typu wskaźnika funkcji, jeśli deklaruje funkcję, która zwraca typ wskaźnika funkcji.  Na przykład

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
[Funkcje śródwierszowe](../cpp/inline-functions-cpp.md)
