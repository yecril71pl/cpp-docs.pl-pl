---
title: Visual C++ Co&#39;nowy 2003 do 2015
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 48b812bf43918d7fbc37d20d0ef1b02348759544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332084"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co&#39;nowy 2003 do 2015

Ta strona zbiera wszystkie strony "Co nowego" dla wszystkich wersji programu Visual C++ z programu Visual Studio 2015 z powrotem do 2003. Te informacje są dostarczane jako udogodnienie w przypadku, gdy może być przydatne podczas uaktualniania z wcześniejszych wersji programu Visual Studio.

> [!NOTE]
> Aby uzyskać informacje na temat bieżącej wersji programu Visual Studio, zobacz [Co nowego w programie Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszeniach zgodności w programie Visual C++ w programie Visual Studio.](../overview/cpp-conformance-improvements.md)

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co nowego w języku C++ w programie Visual Studio 2015

W programie Visual Studio 2015 i nowszych bieżące ulepszenia zgodności kompilatora można czasami zmienić sposób kompilator rozumie istniejącego kodu źródłowego. W takim przypadku może wystąpić nowe lub różne błędy podczas kompilacji lub nawet różnice behawioralne w kodzie, który wcześniej skompilowany i wydawało się działać poprawnie.

Na szczęście różnice te mają niewielki lub żaden wpływ na większość kodu źródłowego i gdy kod źródłowy lub inne zmiany są potrzebne do rozwiązania tych różnic, poprawki są zwykle małe i proste. Zamieściliśmy wiele przykładów wcześniej akceptowalnego kodu źródłowego, który może wymagać zmiany *(wcześniej)* oraz poprawki, aby je poprawić *(po)*.

Mimo że te różnice mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają one na zgodność binarną między aktualizacjami wersji programu Visual C++. Bardziej poważne rodzaju zmiany, *breaking change* może mieć wpływ na zgodność binarną, ale tego rodzaju przerwy zgodności binarnej występują tylko między głównymi wersjami programu Visual C++. Na przykład między Visual C++ 2013 i Visual C++ 2015. Aby uzyskać informacje na temat przełomowych zmian, które zaszły między programami Visual C++ 2013 i Visual C++ 2015, zobacz [Historia zmian języka Visual C++ 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 1](#VS_Update1)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 2](#VS_Update2)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Ulepszenia zgodności w programie Visual Studio 2015

- **/Zc:forScope- opcja**

   Opcja `/Zc:forScope-` kompilatora jest przestarzała i zostanie usunięta w przyszłej wersji.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Opcja była zwykle używana w celu umożliwienia niestandardowego kodu, który używa zmiennych pętli po punkcie, w którym, zgodnie ze standardem, powinny one wyjść poza zakres. Było to konieczne tylko wtedy, `/Za` gdy kompilujesz z opcją, ponieważ bez `/Za`, za pomocą for loop zmiennej po zakończeniu pętli jest zawsze dozwolone. Jeśli nie dbasz o zgodność ze standardami (na przykład, jeśli kod nie jest przeznaczony do `/Za` przenoszenia do innych kompilatorów), możesz wyłączyć tę opcję (lub ustawić właściwość **Wyłącz rozszerzenia języka** na **Nie).** Jeśli zależy Ci na pisaniu przenośnego kodu zgodnego ze standardami, należy przepisać kod, tak aby był zgodny ze standardem, przenosząc deklarację takich zmiennych do punktu poza pętlą.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **Zg kompilator opcji.**

   Opcja `/Zg` kompilatora (Generowanie prototypów funkcji) nie jest już dostępna. Ta opcja kompilatora została wcześniej przestarzała.

- Nie można już uruchamiać testów jednostkowych za pomocą języka C++/CLI z wiersza polecenia z mstest.exe. Zamiast tego użyj vstest.console.exe

- **słowa kluczowego.**

   Specyfikator klasy **magazynu modyfikowatej** nie jest już dozwolony w miejscach, w których wcześniej skompilowano bez błędu. Teraz kompilator daje błąd C2071 (klasa nielegalnego magazynu). Zgodnie ze standardem modyfikowalny specyfikator może być stosowany tylko do nazw elementów członkowskich danych klasy i nie może być stosowany do nazw zadeklarowanych const lub static i nie może być stosowany do elementów członkowskich odwołania.

   Rozważmy na przykład następujący kod:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Poprzednie wersje kompilatora Microsoft C++ zaakceptował to, ale teraz kompilator daje następujący błąd:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Aby naprawić błąd, po prostu usuń zbędne słowo kluczowe **modyfikowalne.**

- **char_16_t i char32_t**

   Nie można już `char16_t` `char32_t` używać lub jako aliasy w typedef, ponieważ te typy są teraz traktowane jako wbudowane. Użytkownicy i autorzy bibliotek `char16_t` często `char32_t` definiują `uint16_t` i `uint32_t`jako aliasy i , odpowiednio.

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   Aby zaktualizować kod, usuń deklaracje **typedef** i zmień nazwę innych identyfikatorów, które zderzają się z tymi nazwami.

- **Parametry szablonu bez typu**

   Niektóre kody, które obejmuje parametry szablonu nie typu jest teraz poprawnie sprawdzane pod kątem zgodności typu po podaniu jawne argumenty szablonu. Na przykład następujący kod skompilowany bez błędu w poprzednich wersjach programu Visual C++.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   Bieżący kompilator poprawnie podaje błąd, ponieważ typ parametru szablonu nie pasuje do argumentu szablonu (parametr jest wskaźnikiem do elementu członkowskiego const, ale funkcja f nie jest zgodna z const):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Aby rozwiązać ten błąd w kodzie, upewnij się, że typ argumentu szablonu, którego używasz, jest zgodny z zadeklarowanym typem parametru szablonu.

- **__declspec(wyrównywanie)**

   Kompilator nie akceptuje `__declspec(align)` już funkcji. To zawsze było ignorowane, ale teraz generuje błąd kompilatora.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Aby rozwiązać ten `__declspec(align)` problem, usuń z deklaracji funkcji. Ponieważ nie miał żadnego efektu, usunięcie go nic nie zmienia.

- **Obsługa wyjątków**

   Istnieje kilka zmian w obsłudze wyjątków. Po pierwsze, obiekty wyjątków muszą być kopiowane lub ruchome. Następujący kod skompilowany w programie Visual Studio 2013, ale nie jest kompilowany w programie Visual Studio 2015:

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Problem polega na tym, że konstruktor kopii jest prywatny, więc obiekt nie może być kopiowany, jak to się dzieje w normalnym przebiegu obsługi wyjątku. To samo dotyczy sytuacji, gdy konstruktor kopii jest zadeklarowany **jawnie.**

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Aby zaktualizować kod, upewnij się, że konstruktor kopii dla obiektu wyjątku jest publiczny i nie jest **oznaczony jako jawny.**

   Przechwytywanie wyjątku przez wartość wymaga również obiekt wyjątku do kopiowania. Następujący kod skompilowany w programie Visual Studio 2013, ale nie jest kompilowany w programie Visual Studio 2015:

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   Ten problem można rozwiązać, zmieniając typ parametru dla **catch** na odwołanie.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Literały ciągów, po których następowały makra**

   Kompilator obsługuje teraz literały zdefiniowane przez użytkownika. W konsekwencji literały ciągów, po których następują makra bez interweniujących odstępów, są interpretowane jako literały zdefiniowane przez użytkownika, co może powodować błędy lub nieoczekiwane wyniki. Na przykład w poprzednich kompilatorach następujący kod został pomyślnie skompilowany:

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   Kompilator zinterpretował to jako ciąg literał "hello", po którym następuje makro, które jest rozwinięte "tam", a następnie dwa literały ciąg zostały połączone w jeden. W programie Visual Studio 2015 kompilator interpretuje to jako literał zdefiniowany przez użytkownika, ale ponieważ nie ma żadnych pasujących literału zdefiniowanego przez użytkownika _x zdefiniowane, daje błąd.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Aby rozwiązać ten problem, dodaj spację między literału ciągu a makro.

- **Sąsiednie literały ciągów**

   Podobnie jak w poprzednim, ze względu na powiązane zmiany w analizowaniu ciągów, sąsiednie literały ciągu (literały ciągów szerokich lub wąskich) bez żadnych odstępów były interpretowane jako pojedynczy ciąg łączony w poprzednich wersjach Visaul C++. W programie Visual Studio 2015 należy teraz dodać odstępy między dwoma ciągami. Na przykład należy zmienić następujący kod:

   ```cpp
    char * str = "abc""def";
   ```

   Wystarczy dodać spację między dwoma ciągami.

   ```cpp
    char * str = "abc" "def";
   ```

- **Umieszczanie nowych i usuwanie**

   Wprowadzono zmianę **w** delete operator w celu dostosowania go do standardu C++14. Szczegółowe informacje na temat zmiany standardów można znaleźć na [stronie C++ Sized Deallocation](https://isocpp.org/files/papers/n3778.html). Zmiany dodać formę globalnego operatora **usuwania,** który przyjmuje parametr rozmiaru. Przełomowa zmiana polega na tym, że jeśli wcześniej używano operatora **delete** z tym samym podpisem (aby odpowiadać nowemu operatorowi **umieszczania),** zostanie wyświetlony błąd kompilatora (C2956, który występuje w punkcie, w którym jest używane **nowe miejsce docelowe,** ponieważ jest to pozycja w kodzie, w której kompilator próbuje zidentyfikować odpowiedni pasujący operator **usuwania).**

   Funkcja `void operator delete(void *, size_t)` była **operatorem usuwania miejsc docelowych** odpowiadającym **umieszczeniu nowej** funkcji `void * operator new(size_t, size_t)` w języku C++11. Z C + + 14 wielkości deallocation, ta funkcja **usuwania** jest teraz *zwykłą funkcją alokacji (operator* **usuwania** globalnego). Standard wymaga, aby jeśli użycie **nowego miejsca docelowego** wyszukuje odpowiednią funkcję **usuwania** i znajdzie zwykłą funkcję lokalizowania, program jest źle sformułowany.

   Załóżmy na przykład, że kod definiuje zarówno **umieszczenie nowe,** jak i **usunięcie miejsca docelowego:**

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   Ten problem występuje z powodu dopasowania w podpisach funkcji między zdefiniowanym operatorem **usuwania miejsca docelowego** a nowym operatorem **usuwania** o rozmiarze globalnym. Należy wziąć pod uwagę, czy `size_t` można użyć innego typu niż dla dowolnego **miejsca nowego** i **delete** operatorów.  Należy zauważyć, że `size_t` typ **typedef** jest zależny od kompilatora; jest **typedef** dla **niepodpisanego int** w języku Visual C++. Dobrym rozwiązaniem jest użycie wyliczonego typu, takiego jak ten:

   ```cpp
    enum class my_type : size_t {};
   ```

   Następnie zmień definicję umieszczania **i** **usuń,** aby użyć tego `size_t`typu jako drugiego argumentu zamiast . Należy również zaktualizować wywołania do **umieszczenia nowy,** aby przekazać nowy `static_cast<my_type>` typ (na przykład za pomocą konwersji z wartości całkowitej) i zaktualizować definicję **nowych** i **usunąć,** aby rzutować z powrotem do typu liczby całkowitej. Nie musisz używać do tego **wyliczenia;** typ klasy z `size_t` członkiem również będzie działać.

   Alternatywnym rozwiązaniem jest to, że może być w stanie całkowicie wyeliminować **umieszczenie nowe.** Jeśli kod używa **umieszczania nowy** do zaimplementowania puli pamięci, gdzie argument umieszczania jest rozmiar obiektu są przydzielane lub usuwane, a następnie wielkości funkcji dezalokacji może być odpowiedni do zastąpienia własnego kodu puli pamięci niestandardowej i można pozbyć się funkcji umieszczania i po prostu użyć własnego dwuarzyscowego delete operatora zamiast funkcji umieszczania. **delete**

   Jeśli nie chcesz natychmiast aktualizować kodu, możesz przywrócić stare zachowanie przy użyciu `/Zc:sizedDealloc-`opcji kompilatora . Jeśli użyjesz tej opcji, funkcje **usuwania** dwóch argumentów nie istnieją i nie powodują konfliktu z operatorem **usuwania miejsca docelowego.**

- **Unijni członkowie danych**

   Elementy członkowskie danych związków nie mogą już mieć typów odwołań. Poniższy kod został pomyślnie skompilowany w programie Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   Poprzedni kod generuje następujące błędy:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Aby rozwiązać ten problem, zmień typy odwołań na wskaźnik lub wartość. Zmiana typu na wskaźnik wymaga zmian w kodzie, który używa pola unii. Zmiana kodu na wartość spowoduje zmianę danych przechowywanych w unii, co wpływa na inne pola, ponieważ pola w typach unii współużytkują tę samą pamięć. W zależności od rozmiaru wartości może również zmienić rozmiar unii.

- **Związki anonimowe**

   są teraz bardziej zgodne ze standardem. Poprzednie wersje kompilatora generowane jawne konstruktora i destruktora dla związków anonimowych. Są one usuwane w programie Visual Studio 2015.

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   Poprzedni kod generuje następujący błąd w programie Visual Studio 2015:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Aby rozwiązać ten problem, podaj własne definicje konstruktora i/lub destruktora.

   ```cpp
    struct S {
       // Provide a default constructor by adding an empty function body.
       S() {}
    };

    union {
       struct {
          S s;
       };
    } u;
   ```

- **Związki zawodowe z anonimowymi strukturami**

   Aby zapewnić zgodność ze standardem, zachowanie środowiska uruchomieniowego uległo zmianie dla członków struktur anonimowych w związkach. Konstruktor dla członków struktury anonimowej w związku nie jest już niejawnie wywoływane podczas tworzenia takiej unii. Ponadto destruktor dla członków struktury anonimowej w unii nie jest już niejawnie wywoływane, gdy związek wykracza poza zakres. Należy wziąć pod uwagę następujący kod, w którym unia U zawiera strukturę anonimową, która zawiera element członkowski, który jest nazwany struktury S, który ma destruktora.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   W programie Visual Studio 2013 konstruktor dla S jest wywoływany podczas tworzenia unii, a destruktor dla S jest wywoływany, gdy stos dla funkcji f jest czyszczony. Ale w programie Visual Studio 2015 konstruktora i destruktora nie są wywoływane. Kompilator daje ostrzeżenie o tej zmianie zachowania.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Aby przywrócić oryginalne zachowanie, nadaj strukturze anonimowej nazwę. Zachowanie środowiska wykonawczego struktur nieanonimowych jest taka sama, niezależnie od wersji kompilatora.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Alternatywnie spróbuj przenieść kod konstruktora i destruktora do nowych funkcji i dodać wywołania do tych funkcji z konstruktora i destruktora dla unii.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **Rozdzielczość szablonu**

   Wprowadzono zmiany w rozpoznawaniu nazw szablonów. W języku C++, rozważając kandydatów do rozwiązania nazwy, może być tak, że jedna lub więcej nazw pod uwagę jako potencjalne dopasowania tworzy nieprawidłowe wystąpienie szablonu. Te nieprawidłowe wystąpienia zwykle nie powodują błędów kompilatora, zasada, która jest znana jako SFINAE (Błąd podstawiania nie jest błędem).

   Teraz jeśli SFINAE wymaga kompilatora do wystąpienia specjalizacji szablonu klasy, następnie wszelkie błędy, które występują podczas tego procesu są błędy kompilatora. W poprzednich wersjach kompilator ignoruje takie błędy. Rozważmy na przykład następujący kod:

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   Jeśli kompilujesz z bieżącym kompilatorem, pojawia się następujący błąd:

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   Dzieje się tak dlatego, że w punkcie pierwszego wywołania is_base_of klasa "D" nie została jeszcze zdefiniowana.

   W takim przypadku poprawka nie jest do używania takich cech typu, dopóki klasa została zdefiniowana. Jeśli przeniesiesz definicje B i D na początek pliku kodu, błąd zostanie rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność zestawienia dla plików nagłówkowych, aby upewnić się, że wszystkie definicje klas są kompilowane przed użyciem problematycznych szablonów.

- **Konstruktory kopiowania**

   W programie Visual Studio 2013 i Visual Studio 2015 kompilator generuje konstruktora kopii dla klasy, jeśli ta klasa ma konstruktora przenoszenia zdefiniowane przez użytkownika, ale nie konstruktora kopiowania zdefiniowanego przez użytkownika. W dev14 ten niejawnie wygenerowany konstruktor kopii jest również oznaczony "= delete".

### <a name="conformance-improvements-in-visual-studio-2015-update-1"></a><a name="VS_Update1"></a>Ulepszenia zgodności w programie Visual Studio 2015 Update 1

- **Prywatne wirtualne klasy podstawowe i dziedziczenie pośrednie**

   Poprzednie wersje kompilatora dozwolone klasy pochodnej do wywoływania funkcji członkowskich jego *pośrednio pochodnych* `private virtual` klas podstawowych. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator nie akceptuje już kodu napisanego w ten sposób i generuje błąd kompilatora C2280 w wyniku.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   Przykład (przed)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   Przykład (po)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  \-lub-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Przeciążony operator nowy i usunięcie operatora**

   Poprzednie wersje kompilatora dozwolone operator niebędący elementami **elementów członkowskich usunięcie nowego** i innego elementu **członkowskiego,** które mają być zadeklarowane jako statyczne i zadeklarowane w przestrzeniach nazw innych niż globalna przestrzeń nazw.  To stare zachowanie stworzyło ryzyko, że program nie będzie wywoływać **nowej** lub **usuwać** implementacji operatora, że programista przeznaczone, co powoduje ciche złe zachowanie środowiska uruchomieniowego. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C2323.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   Przykład (przed)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   Przykład (po)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

   Ponadto mimo że kompilator nie daje określonej diagnostyki, wbudowany operator nowy jest uważany za nieuformowany.

- **Wywołanie *"typ*operatora ()" (konwersja zdefiniowana przez użytkownika) na typach innych niż klasy** Poprzednie wersje kompilatora pozwoliły na wywołanie *"typu*operatora ()" na typach innych niż klasy, podczas gdy po cichu go ignoruje. To stare zachowanie stworzyło ryzyko generowania cichego złego kodu, co spowodowało nieprzewidywalne zachowanie środowiska uruchomieniowego. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C2228.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   Przykład (przed)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   Przykład (po)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **Nadmiarowa nazwa typu w opracowanych specyfikatorach typu**  Poprzednie wersje kompilatora dozwolone **nazwa typu** w opracowywane specyfikatory typu; kod napisany w ten sposób jest semantycznie niepoprawny. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C3406.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   Przykład (przed)

   ```cpp
    template <typename class T>
    class container;
   ```

   Przykład (po)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **Typ odliczanie tablic z listy inicjatora**  Poprzednie wersje kompilatora nie obsługiwały odliczeń typów tablic z listy inicjatorów. Kompilator obsługuje teraz tę formę dedukcji typu i w rezultacie wywołania szablonów funkcji przy użyciu list inicjatora może być teraz niejednoznaczne lub może być wybrane inne przeciążenie niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program musi teraz jawnie określić przeciążenie, które programista przeznaczone.

   Gdy to nowe zachowanie powoduje, że rozwiązanie przeciążenia do rozważenia dodatkowego kandydata, który jest równie dobry jak kandydat historyczny, wywołanie staje się niejednoznaczne i kompilatora problemy kompilatora błąd C2668 w wyniku.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Przykład 1: Niejednoznaczne wywołanie przeciążonej funkcji (przed)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   Przykład 1: niejednoznaczne wywołanie przeciążonej funkcji (po)

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   Gdy to nowe zachowanie powoduje, że rozwiązanie przeciążenia do rozważenia dodatkowego kandydata, który jest lepiej dopasowane niż historycznego kandydata, wywołanie rozwiązuje jednoznacznie do nowego kandydata, powodując zmianę zachowania programu, który jest prawdopodobnie inny niż programista przeznaczone.

   Przykład 2: zmiana rozdzielczości przeciążenia (przed)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   Przykład 2: zmiana rozdzielczości przeciążenia (po)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **Przywracanie ostrzeżeń instrukcji przełącznika**

   Poprzednia wersja kompilatora usunięte wcześniej istniejących ostrzeżeń związanych z **switch** instrukcji; ostrzeżenia te zostały przywrócone. Kompilator teraz wystawia przywrócone ostrzeżenia i ostrzeżenia związane z określonymi przypadkami (w tym przypadek domyślny) są teraz wydawane w wierszu zawierającym przypadek naruszający, a nie w ostatnim wierszu instrukcji switch. W wyniku wydawania tych ostrzeżeń w różnych liniach niż w przeszłości `#pragma warning(disable:####)` ostrzeżenia wcześniej tłumione za pomocą mogą nie być dłużej tłumione zgodnie z przeznaczeniem. Aby pominąć te ostrzeżenia zgodnie z przeznaczeniem, może być konieczne przeniesienie `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszego przypadku potencjalnie naruszającego. Poniżej znajdują się przywrócone ostrzeżenia.

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   Przykład C4063 (przed)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   Przykład C4063 (po)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   Przykłady innych przywróconych ostrzeżeń znajdują się w ich dokumentacji.

- **#include: użycie specyfikatora katalogu nadrzędnego '..' w nazwach ścieżek** `/Wall` `/WX`(dotyczy tylko)

   Poprzednie wersje kompilatora nie wykryły użycia specyfikatora katalogu nadrzędnego '.' w ścieżce `#include` dyrektyw. Kod napisany w ten sposób jest zwykle przeznaczony do uwzględnienia nagłówków, które istnieją poza projektem przez niepoprawnie przy użyciu ścieżek względnych projektu. To stare zachowanie stworzyło ryzyko, że program może zostać skompilowany przez dołączenie innego pliku źródłowego niż programista przeznaczony lub że te ścieżki względne nie będą przenośne do innych środowisk kompilacji. Kompilator teraz wykrywa i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C4464, jeśli jest włączone.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   Przykład (przed)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   Przykład (po)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   Ponadto chociaż kompilator nie daje określonej diagnostyki, zaleca się również, że specyfikator katalogu nadrzędnego ".." należy zwrócić uwagę, aby określić katalogi dołączane projektu.

- **#pragma optimize() rozciąga się na koniec minionego końca pliku nagłówka** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora nie wykryły zmian w ustawieniach flagi optymalizacji, które unikną pliku nagłówka zawartego w jednostce tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora `#include`C4426 w lokalizacji naruszającego , jeśli jest włączone. To ostrzeżenie jest wydawane tylko wtedy, gdy zmiany są w konflikcie z flagami optymalizacji ustawionymi przez argumenty wiersza polecenia do kompilatora.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   Przykład (przed)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   Przykład (po)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **Niedopasowane #pragma ostrzeżenie (push)** i **#pragma warning(pop)** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora `#pragma warning(push)` nie wykryły `#pragma warning(pop)` zmian stanu sparowanych ze zmianami stanu w innym pliku źródłowym, który rzadko jest przeznaczony. To stare zachowanie stworzyło ryzyko, że program zostanie skompilowany z włączonym innym zestawem ostrzeżeń niż programista, co może spowodować ciche złe zachowanie środowiska uruchomieniowego. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C5031 w lokalizacji pasującego `#pragma warning(pop)`, jeśli jest włączone. Ostrzeżenie to zawiera notatkę odwołującą się do lokalizacji odpowiedniego `#pragma warning(push)`.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   Przykład (przed)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   Przykład (po)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   Choć niezbyt często, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest `#include` wrażliwy na zmiany w kolejności; Jeśli to możliwe, zaleca się, aby pliki kodu źródłowego zarządzały stanem ostrzeżenia w sposób samodzielny.

- **Niezrównane ostrzeżenie #pragma (push)** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora nie wykryły niedopasowanych `#pragma warning(push)` zmian stanu na końcu jednostki tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C5032 w lokalizacji niedopasowanego `#pragma warning(push)`, jeśli jest włączona. To ostrzeżenie jest wydawane tylko wtedy, gdy w jednostce tłumaczenia nie występują błędy kompilacji.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   Przykład (przed)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   Przykład (po)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **Dodatkowe ostrzeżenia mogą zostać wydane w wyniku poprawy śledzenia stanu #pragma**

   Poprzednie wersje kompilatora `#pragma warning` śledzone zmiany stanu nie wystarczająco dobrze wydać wszystkie zamierzone ostrzeżenia. To zachowanie stworzyło ryzyko, że niektóre ostrzeżenia będą skutecznie pomijane w okolicznościach innych niż programista przeznaczony. Kompilator śledzi `#pragma warning` teraz stan bardziej solidnie `#pragma warning` - szczególnie związane ze zmianami stanu wewnątrz szablonów - i opcjonalnie wydaje nowe ostrzeżenia C5031 i C5032, które mają pomóc programisty zlokalizować niezamierzone zastosowania `#pragma warning(push)` i `#pragma warning(pop)`.

   W wyniku poprawy `#pragma warning` śledzenia zmian stanu, ostrzeżenia wcześniej nieprawidłowo pomijane lub ostrzeżenia związane z problemami wcześniej błędnie mogą być wydawane.

- **Ulepszona identyfikacja nieosiągalnego kodu**

   C++ Standard Library zmiany i ulepszone możliwości wywołania funkcji wbudowanych w poprzednich wersjach kompilatora może umożliwić kompilator udowodnić, że niektóre kod jest teraz nieosiągalny. To nowe zachowanie może spowodować nowe i częściej wystawiane wystąpienia ostrzeżenia C4720.

   ```Output
    warning C4720: unreachable code
   ```

   W wielu przypadkach to ostrzeżenie może być wydawane tylko podczas kompilowania z włączonymi optymalizacjami, ponieważ optymalizacje mogą wywołać więcej funkcji, wyeliminować nadmiarowy kod lub w inny sposób umożliwić ustalenie, że określony kod jest nieosiągalny. Zaobserwowaliśmy, że nowe przypadki ostrzegania C4720 często występowały w blokach **typu try/catch,** szczególnie w odniesieniu do stosowania [std::find](../standard-library/algorithm-functions.md#find).

   Przykład (przed)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   Przykład (po)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="conformance-improvements-in-visual-studio-2015-update-2"></a><a name="VS_Update2"></a>Ulepszenia zgodności w programie Visual Studio 2015 Update 2

- **Dodatkowe ostrzeżenia i błędy mogą być wydawane w wyniku częściowej obsługi wyrażenia SFINAE**

   Poprzednie wersje kompilatora nie analizować niektórych rodzajów wyrażeń wewnątrz **specyfikatorów decltype** ze względu na brak obsługi wyrażenia SFINAE. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator analizuje teraz te wyrażenia i ma częściową obsługę wyrażenia SFINAE ze względu na trwające ulepszenia zgodności. W rezultacie kompilator teraz wydaje ostrzeżenia i błędy znalezione w wyrażeniach, które poprzednie wersje kompilatora nie analizował.

   Gdy to nowe zachowanie analizuje wyrażenie **decltype,** który zawiera typ, który nie został jeszcze zadeklarowany, kompilator generuje błąd kompilatora C2039 w wyniku.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Przykład 1: użycie typu niezadeklarowanego (przed)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   Przykład 1 (po)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   Gdy to nowe zachowanie analizuje wyrażenie **decltype,** w którym brakuje niezbędnego użycia słowa kluczowego **nazwa typu,** aby określić, że nazwa zależna jest typem, kompilator wydaje ostrzeżenie kompilatora C4346 wraz z błędem kompilatora C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Przykład 2: nazwa zależna nie jest typem (przed)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   Przykład 2 (po)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- `volatile`**zmienne członkowskie zapobiegają niejawnie zdefiniowanym konstruktorom i operatorom przypisania** Poprzednie wersje kompilatora zezwalały na automatyczne generowanie klasy, która ma **zmienne zmienne nietrwałe** elementów członkowskich. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator teraz uważa, że klasa, która ma zmienne zmienne nietrwałe elementów członkowskich, mają nietrywialne operatory konstrukcji i przypisania, co uniemożliwia automatyczne implementacje tych operatorów są generowane automatycznie. Gdy taka klasa jest członkiem unii (lub unii anonimowej wewnątrz klasy), konstruktory kopiowania/przenoszenia i operatorów przypisania kopiowania/przenoszenia unii (lub klasy zawierającej związek nieonimiczne) zostaną niejawnie zdefiniowane jako usunięte. Próba skonstruowania lub skopiowania unii (lub klasy zawierającej związek anonimowy) bez jawnego zdefiniowania ich jest błędem, a w rezultacie kompilator wydaje błąd kompilatora C2280.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   Przykład (przed)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   Przykład (po)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **Statyczne funkcje członkowskie nie obsługują kwalifikatorów cv.**

   Poprzednie wersje programu Visual C++ 2015 zezwalały na statyczne funkcje członkowskie, które miały kwalifikacje cv. To zachowanie jest spowodowane regresji w języku Visual C++ 2015 i Visual C++ 2015 Update 1; Visual C++ 2013 i poprzednie wersje kodu odrzucenia języka Visual C++ napisane w ten sposób. Zachowanie visual C++ 2015 i Visual C++ 2015 Update 1 jest niepoprawna i nie jest zgodna ze standardem C++.  Visual Studio 2015 Update 2 odrzuca kod napisany w ten sposób i problemalizuje błąd kompilatora C2511 zamiast.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   Przykład (przed)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   Przykład (po)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **Forward deklaracja wyliczenia nie jest dozwolone w kodzie WinRT** (dotyczy `/ZW` tylko)

   Kod skompilowany dla środowiska wykonawczego systemu Windows (WinRT) nie zezwala na przekazywanie typów **wyliczeni,** podobnie jak `/clr` wtedy, gdy zarządzany kod C++ jest kompilowany dla programu .Net Framework przy użyciu przełącznika kompilatora. To zachowanie zapewnia, że rozmiar wyliczenia jest zawsze znany i może być poprawnie rzutowane do systemu typu WinRT. Kompilator odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2599 wraz z błędem kompilatora C3197.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   Przykład (przed)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   Przykład (po)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **Przeciążony operator niebędący członkiem nowy i usunięcie operatora nie może być zadeklarowany w linii wbudowanej** (poziom 1 (`/W1`) domyślnie)

   Poprzednie wersje kompilatora nie wydają ostrzeżenia, gdy operator niebędący elementem **członkowskim nowe** i **operator delete** funkcje są zadeklarowane wbudowane. Kod napisany w ten sposób jest źle sformułowany (nie wymaga diagnostyki) i może powodować problemy z pamięcią wynikające z niedopasowanych operatorów nowych i delete (szczególnie gdy są używane razem z rozmiarem dezlokacji), które mogą być trudne do zdiagnozowania. Kompilator teraz generuje ostrzeżenie kompilatora C4595, aby pomóc zidentyfikować kod napisany w ten sposób.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   Przykład (przed)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   Przykład (po)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   Kod naprawiania, który jest napisany w ten sposób może wymagać, aby definicje operatora zostały przeniesione z pliku nagłówka i do odpowiedniego pliku źródłowego.

### <a name="conformance-improvements-in-visual-studio-2015-update-3"></a><a name="VS_Update3"></a>Ulepszenia zgodności w programie Visual Studio 2015 Update 3

- **std::is_convertable wykrywa teraz samoadowanie** (standardowa biblioteka) Poprzednie wersje cechy `std::is_convertable` typu nie wykrywały poprawnie samoadowania typu klasy, gdy jego konstruktor kopii jest usuwany lub prywatny. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **false** po zastosowaniu do typu klasy z konstruktorem usunięte lub kopii prywatnej.

   Z tą zmianą nie jest skojarzona żadna diagnostyka kompilatora.

   Przykład

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   W poprzednich wersjach programu Visual C++potwierdzenia statyczne u dołu tego przykładu przebiegają, ponieważ `std::is_convertable<>::value` został niepoprawnie ustawiony na **true**. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **false**, powodując nie powiodło się potwierdzenia statyczne.

- **Domyślnie lub usunięte trywialne konstruktory kopiowania i przenoszenia respektują specyfikatory dostępu**

   Poprzednie wersje kompilatora nie sprawdzały specyfikatora dostępu domyślnie lub usunięte trywialne kopiowanie i przenoszenie konstruktorów przed zezwoleniem na ich wywołanie. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. W niektórych przypadkach to stare zachowanie stworzyło ryzyko generowania cichego złego kodu, co spowodowało nieprzewidywalne zachowanie środowiska uruchomieniowego. Kompilator sprawdza teraz specyfikator dostępu domyślnie lub usunięte trywialne kopiowanie i przenoszenie konstruktorów, aby ustalić, czy można go wywołać, a jeśli nie, problemy kompilator ostrzeżenie C2248 w wyniku.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   Przykład (przed)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   Przykład (po)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **Wycofanie obsługi kodu przypisanego ATL** (poziom`/W1`1 ( ) domyślnie)

   Poprzednie wersje kompilatora obsługiwane przypisany kod ATL. Jako następna faza usuwania obsługi przypisanego kodu ATL, który [rozpoczął się w programie Visual C++ 2008,](#whats-new-for-c-in-visual-studio-2008)przypisany kod ATL został przestarzały. Kompilator teraz generuje ostrzeżenie kompilatora C4467, aby pomóc zidentyfikować tego rodzaju przestarzały kod.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Jeśli chcesz nadal używać przypisanego kodu ATL, dopóki obsługa nie zostanie usunięta `/Wv:18` `/wd4467` z kompilatora, możesz wyłączyć `#pragma warning(disable:4467)` to ostrzeżenie, przekazując argumenty wiersza polecenia lub do kompilatora lub dodając w kodzie źródłowym.

   Przykład 1 (przed)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Przykład 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Czasami może być konieczne lub chcesz utworzyć plik IDL, aby uniknąć użycia przestarzałych atrybutów ATL, jak w poniższym przykładowym kodzie

   Przykład 2 (przed)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   Najpierw utwórz plik *.idl; wygenerowany plik vc140.idl może służyć \*do uzyskania pliku .idl zawierającego interfejsy i adnotacje.

   Następnie dodaj krok MIDL do kompilacji, aby upewnić się, że definicje interfejsu języka C++ są generowane.

   Przykład 2 IDL (po)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   Następnie należy użyć ATL bezpośrednio w pliku implementacji, jak w poniższym przykładzie kodu.

   Przykład 2 Implementacja (po)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **Wstępnie skompilowane pliki nagłówka (PCH) i niedopasowane dyrektywy** `/Wall` `/WX`#include (dotyczy tylko)

   Poprzednie wersje kompilatora akceptowały `#include` niedopasowane dyrektywy `-Yc` w `-Yu` plikach źródłowych między i kompilacje podczas korzystania z plików nagłówka wstępnie skompilowanego (PCH). Kod napisany w ten sposób nie jest już akceptowany przez kompilator. Kompilator generuje teraz ostrzeżenie kompilatora CC4598, aby ułatwić identyfikowanie niedopasowanych `#include` dyrektyw podczas korzystania z plików PCH.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Przykład (przed):

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Przykład (po)

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Wstępnie skompilowane pliki nagłówka (PCH) i niedopasowane katalogi dołączania** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora akceptowane niedopasowane obejmują`-I`argumenty wiersza polecenia katalogu `-Yc` `-Yu` ( ) do kompilatora między i kompilacji podczas korzystania z wstępnie skompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest już akceptowany przez kompilator.   Kompilator generuje teraz ostrzeżenie kompilatora CC4599, aby`-I`pomóc w identyfikacji niezgodnych argumentów wiersza polecenia () podczas korzystania z plików PCH.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   Przykład (przed)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   Przykład (po)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co nowego w języku C++ w programie Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Ulepszona obsługa standardów ISO C/C++

#### <a name="compiler"></a>Kompilator

MSVC obsługuje te funkcje języka ISO C++11:

- Domyślne argumenty szablonu dla szablonów funkcji.
- Delegowanie konstruktorów
- Jawne operatory konwersji.
- Listy inicjatorów i inicjalizacja.
- Nieprzetworzone literały ciągów.
- Szablony variadic.
- Szablony aliasów.
- Usunięte funkcje.
- Inicjalizatory elementów członkowskich danych niestatycznych (NSDMIs).
- Domyślne funkcje. \*
- Obsługuje te funkcje języka ISO C99:
- _Bool
- Dosłowne złożone.
- Wyznaczone inicjatory.
- Mieszanie deklaracji z kodem.
- Konwersja literału ciągu na modyfikowalne wartości może `/Zc:strictStrings`być niedozwolona przy użyciu nowej opcji kompilatora . W języku C++ 98 konwersja `char*` z literałów ciągu `wchar_t*`do (i szeroki ciąg literałów do) została przestarzała. W języku C++11 konwersja została całkowicie usunięta. Mimo że kompilator może ściśle zgodne ze `/Zc:strictStrings` standardem, zamiast tego zapewnia opcję, dzięki czemu można kontrolować konwersji. Domyślnie opcja jest wyłączona. Należy zauważyć, że podczas korzystania z tej opcji w trybie debugowania, STL nie będzie kompilować.
- rvalue/lvalue Rzuty referencyjne. W odniesieniu do wartości rvalue C++11 może wyraźnie odróżnić wartości lwalues i wartości r. Wcześniej kompilator nie dostarczył tego w określonych scenariuszach rzutowania. Dodano nową opcję `/Zc:rvalueCast`kompilatora , aby kompilator konformant z dokumentem roboczym języka C++ (patrz sekcja 5.4, [expr.cast]/1). Domyślne zachowanie, gdy ta opcja nie jest określona jest taka sama jak w programie Visual Studio 2012.

> [!NOTE]
> W przypadku domyślnych funkcji użycie =default do żądania konstruktorów przenoszenia elementów członkowskich i przenoszenia operatorów przypisania nie jest obsługiwane.

### <a name="c99-libraries"></a>Biblioteki C99

Deklaracje i implementacje są dodawane dla brakujących funkcji w tych nagłówkach: math.h, ctype.h, wctype.h, stdio.h, stdlib.h i wchar.h. Dodano również nowe nagłówki complex.h, stdbool.h, fenv.h i inttypes.h oraz implementacje dla wszystkich funkcji zadeklarowanych w nich. Istnieją nowe nagłówki otoki C++ (ccomplex, cfenv, cinttypes, ctgmath) i wiele innych są aktualizowane (ccomplex, cctype, clocale, cmath, cstdint, cstdio, cstring, cwchar i cwctype).

### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

Obsługa operatorów konwersji jawnych języka C++ 11, listy inicjatorów, wyliczenia o określonym zakresie i szablony variadic.
Wszystkie kontenery obsługują teraz wymagania dotyczące drobnoziarnistych elementów języka C++11.
Obsługa tych funkcji języka C++14:

- "Przezroczyste functory operatora" mniej<>, większa<>, plus<>, mnoży<> i tak dalej.
- make_unique\<T>(args...) i make_unique<T[]> n)
- cbegin()/cend(), rbegin()/rend(), i crbegin()/crend() funkcje niebędące członkami.
- \<> atomowej otrzymał liczne ulepszenia wydajności.
- \<type_traits> otrzymały poważne poprawki stabilizacyjne i kodowe.

### <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Ta ulepszona obsługa standardów ISO C/C++ może wymagać zmian w istniejącym kodzie, tak aby był zgodny z C++ 11 i kompiluje poprawnie w programie Visual C++ w programie Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Ulepszenia biblioteki języka Visual C++

- Dodano C++ REST SDK. Posiada nowoczesne wdrożenie usług REST w języku C++.
- Obsługa tekstury C++ AMP jest ulepszona. Teraz zawiera obsługę mipmaps i nowych trybów próbkowania.
- Zadania PPL obsługują wiele technologii planowania i debugowania asynchroniczne. Nowe interfejsy API umożliwiają tworzenie zadań PPL zarówno dla normalnych wyników, jak i warunków wyjątków.

### <a name="c-application-performance"></a>Wydajność aplikacji w języku C++

- Auto-Vectorizer teraz rozpoznaje i optymalizuje więcej wzorców Języka C++, aby kod działał szybciej.
- Poprawa jakości kodu platformy ARM i mikrosetykie Atom.
- __vectorcall konwencja wywoływania jest dodawana. Przekazywanie argumentów typu wektorowego przy użyciu konwencji wywoływania __vectorcall do używania rejestrów wektorowych.
- Nowe opcje konsolidatora. Przełączniki `/Gw` (kompilator) i `/Gy` (asembler) umożliwiają optymalizacje konsolidatora w celu uzyskania szczuplejszych plików binarnych.
- Obsługa pamięci współdzielonej C++ AMP w celu zmniejszenia lub wyeliminowania kopiowania danych między procesorem CPU a procesorem GRAFICZNYM.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Ulepszenia optymalizacji z przewodnikiem profilu (PGO)

- Poprawa wydajności dzięki zmniejszeniu zestawu roboczego aplikacji, które są optymalizowane przy użyciu pgo.
- Nowy PGO dla tworzenia aplikacji środowiska wykonawczego systemu Windows.

### <a name="windows-runtime-app-development-support"></a>Pomoc techniczna aplikacji środowiska wykonawczego systemu Windows

- **Obsługa typów pudełkowych w strukturach wartości.**

   Można teraz zdefiniować typy wartości przy użyciu pól, które mogą mieć wartość null — na przykład, `IBox<int>^` w przeciwieństwie do **int**. Oznacza to, że pola mogą mieć wartość lub być równe **nullptr**.

- **Bogatsze informacje o wyjątku.**

   C++/CX obsługuje nowy model błędu systemu Windows, który umożliwia przechwytywanie i propagację bogatych informacji o wyjątkach w interfejsie binarnym aplikacji (ABI); obejmuje to stosy wywołań i ciągi wiadomości niestandardowych.

- **Obiekt::ToString() jest teraz wirtualny.**

   Teraz można zastąpić ToString w zdefiniowanych przez użytkownika typach ref środowiska wykonawczego systemu Windows.

- **Obsługa przestarzałych interfejsów API.**

   Publiczne interfejsy API środowiska wykonawczego systemu Windows mogą być teraz oznaczone jako przestarzałe i mają niestandardowy komunikat, który pojawia się jako ostrzeżenie kompilacji i może dostarczyć wskazówek dotyczących migracji.

- **Ulepszenia debugera.**

   Obsługa debugowania międzyopowego/javascriptowego, diagnostyki wyjątków środowiska wykonawczego systemu Windows i debugowania kodu asynchronicznego (zarówno środowiska wykonawczego systemu Windows, jak i PPL).

> [!NOTE]
> Oprócz funkcji i ulepszeń specyficznych dla języka C++, które są opisane w tej sekcji, inne ulepszenia w programie Visual Studio również mogą pomóc w pisaniu lepszych aplikacji środowiska wykonawczego systemu Windows.

### <a name="diagnostics-enhancements"></a>Ulepszenia diagnostyki

- Ulepszenia debugera. Obsługa debugowania asynchronii i debugowania tylko mój kod.
- Kategorie analizy kodu. Teraz można wyświetlić skategoryzowane dane wyjściowe z analizatora kodu, aby ułatwić znajdowanie i naprawianie wad kodu.
- Diagnostyka XAML. Teraz można zdiagnozować problemy z odpowiedzią interfejsu użytkownika i zużyciem baterii w języku XAML.
- Ulepszenia debugowania grafiki i procesora GPU.
- Zdalne przechwytywanie i odtwarzanie na prawdziwych urządzeniach.
- Jednoczesne debugowanie C++ AMP i CPU.
- Ulepszona diagnostyka środowiska uruchomieniowego C++ AMP.
- Debugowanie śledzenia modułu cieniującego HLSL Compute.

### <a name="3-d-graphics-enhancements"></a>Ulepszenia grafiki 3-W

- Obsługa potoku zawartości obrazu dla wstępnie pomnożonego formatu alfa DDS.
- Edytor obrazów używa wewnętrznie wstępnie pomnożonej alfa do renderowania, a tym samym unika renderowania artefaktów, takich jak ciemne aureole.
- Edytory obrazów i modeli. Tworzenie filtrów zdefiniowane przez użytkownika jest teraz obsługiwane w projektancie modułu cieniującego w edytorze obrazów i edytorze modeli.

### <a name="ide-and-productivity"></a>IDE i produktywność

**Ulepszone formatowanie kodu**. Więcej ustawień formatowania można zastosować do kodu języka C++. Za pomocą tych ustawień można kontrolować położenie nawiasów klamrowych i słów kluczowych w nowej linii, wcięcie, odstępy i zawijanie linii. Kod jest automatycznie formatowany podczas wypełniania instrukcji i bloków oraz po wklejaniu kodu do pliku.

**Zakończenie nawiasu klamry.** Kod języka C++ automatycznie uzupełnia znaki zamykające odpowiadające następującym znakom otwarcia:

- { (nawias klamrowa)
- [ (nawias kwadratowy)
- ( (nawiasy)
- ' (pojedynczy cytat)
- "(cudzysłowami)

**Dodatkowe funkcje automatycznego uzupełniania języka C++.**

- Dodaje średnik dla typów klas.
- Kończy nawiasy dla nieprzetworzonych literałów ciągu.
- Uzupełnia wielowierszowe\* \*komentarze (/ /)

**Funkcja Znajdź wszystkie odwołania** automatycznie rozwiązuje i filtruje odwołania w tle po wyświetleniach listy dopasowań tekstowych.

**Filtrowanie listy elementów członkowskich w kontekście.** Niedostępne elementy członkowskie są filtrowane z list elementów członkowskich IntelliSense. Na przykład prywatne elementy członkowskie nie są wyświetlane na liście elementów członkowskich, chyba że modyfikujesz kod, który implementuje typ. Gdy lista członków jest otwarta, można nacisnąć klawisz **Ctrl**+**J,** aby usunąć jeden poziom filtrowania (dotyczy tylko bieżącego okna listy członków). Możesz ponownie nacisnąć **klawisz Ctrl**+**J,** aby usunąć filtrowanie tekstowe i pokazać każdemu członkowi.

**Przewijanie pomocy parametrów.** Wyświetlany podpis funkcji w etykietce narzędzia pomocy parametrów zmienia się teraz na podstawie liczby faktycznie wpisanych parametrów, a nie tylko wyświetlania dowolnego podpisu i nie aktualizowania go na podstawie bieżącego kontekstu. Pomoc parametrów działa również poprawnie, gdy jest wyświetlana na funkcjach zagnieżdżonych.

**Przełączanie pliku nagłówka/kodu.** Teraz można przełączać się między nagłówkiem a odpowiadającym mu plikiem kodu za pomocą polecenia w menu skrótów lub skrótu klawiaturowego.

**Okno Właściwości projektu o zmiennym rozmiarze W++**

**Automatyczne generowanie kodu obsługi zdarzeń w językach C++/CX i C++/CLI.**  Podczas wpisywania kodu, aby dodać program obsługi zdarzeń w pliku kodu C++/CX lub C++/CLI, edytor może automatycznie wygenerować wystąpienie delegata i definicję obsługi zdarzeń. Okno etykietki narzędzia pojawia się, gdy kod obsługi zdarzeń może być generowany automatycznie.

**Wzmocnienie świadomości DPI.** Ustawienie Świadomości DPI dla plików manifestów aplikacji obsługuje teraz ustawienie "Na monitor wysokiej rozdzielczości DPI Aware".

**Szybsze przełączanie konfiguracji.** W przypadku dużych aplikacji konfiguracje przełączania — zwłaszcza późniejsze operacje przełączania — są wykonywane znacznie szybciej.

**Zbuduj efektywność czasu.** Liczne optymalizacje i wielordzeniowe wykorzystanie sprawiają, że kompilacje są szybsze, szczególnie w przypadku dużych projektów. Przyrostowe kompilacje dla aplikacji W++, które mają odwołania do języka WinMD języka C++ są również znacznie szybsze.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co nowego w języku C++ w programie Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Ulepszona obsługa standardów języka C++11

#### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

- \<Obsługa nowych nagłówków STL: atomic>, \<chrono>, \<condition_variable>, \<> systemu plików, \<przyszłych>, \<> mutex, \<> współczynnika i \<> wątków.
- Aby zoptymalizować użycie zasobów pamięci, kontenery są teraz mniejsze. Na przykład w trybie wydania x86 z ustawieniami domyślnymi `std::vector` zmniejszyła się z 16 bajtów w programie Visual Studio 2010 do 12 bajtów w programie Visual Studio 2012 i `std::map` zmniejszyła się z 16 bajtów w programie Visual Studio 2010 do 8 bajtów w programie Visual Studio 2012.
- Zgodnie z dozwolone, ale nie wymagane przez C ++ 11 Standard, scary iteratory zostały zaimplementowane.

#### <a name="other-c11-enhancements"></a>Inne ulepszenia języka C++11

- Oparte na zasięgu pętle. Można zapisywać bardziej niezawodne pętle, które działają z tablicami, kontenerami STL i kolekcjami środowiska wykonawczego systemu Windows w formularzu dla ( for-range-declaration : expression ). Jest to część obsługi języka podstawowego.
- Lambdas bezstanowe, które są blokami kodu, które zaczynają się od pustego wprowadzającego lambda [] i przechwytują żadnych zmiennych lokalnych, są teraz niejawnie konwertowane na wskaźniki funkcji, zgodnie z wymaganiami standardu C++11.
- Obsługa wyliczeń o określonym zakresie. Klucz wyliczenia klasy wyliczenia C++ jest teraz obsługiwany. Poniższy kod pokazuje, jak ten klucz wyliczenia różni się od poprzedniego zachowania wyliczenia.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Pomoc techniczna aplikacji środowiska wykonawczego systemu Windows

- **Natywny model interfejsu użytkownika oparty na języku XAML**. W przypadku aplikacji środowiska wykonawczego systemu Windows można użyć nowego macierzystego modelu interfejsu użytkownika opartego na języku XAML.
- **Rozszerzenia składników programu Visual C++**. Rozszerzenia te upraszczają korzystanie z obiektów środowiska wykonawczego systemu Windows, które są niezbędną częścią aplikacji środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz Mapa drogowa dla aplikacji środowiska wykonawczego systemu Windows przy użyciu odwołania do języka [C++](../cppcx/universal-windows-apps-cpp.md) i [języka Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Gry DirectX**. Atrakcyjne gry można tworzyć przy użyciu nowej obsługi directx dla aplikacji środowiska wykonawczego systemu Windows.
- **XAML/DirectX interop**. Aplikacje środowiska wykonawczego systemu Windows, które używają zarówno XAML, jak i DirectX, teraz działają wydajnie.
- **Tworzenie biblioteki DLL składnika środowiska wykonawczego systemu Windows**. Tworzenie biblioteki DLL składników sprawia, że środowisko wykonawcze systemu Windows rozszerzalne.

### <a name="compiler-and-linker"></a>Kompilator i konsolidator

- **Auto-wektoryzator**. Kompilator analizuje pętle w kodzie i, jeśli to możliwe, emituje instrukcje, które używają rejestrów wektorowych i instrukcji, które są obecne we wszystkich nowoczesnych procesorów. To sprawia, że pętle działają szybciej. (Instrukcje procesora są znane jako SSE, dla przesyłania strumieniowego rozszerzenia SIMD). Nie trzeba włączać ani żądać tej optymalizacji, ponieważ jest ona stosowana automatycznie.
- **Auto-równoległy .** Kompilator może analizować pętle w kodzie i emitować instrukcje, które rozkładają obliczenia na wiele rdzeni lub procesorów. Może to sprawić, że pętle będą działać szybciej. Należy zażądać tej optymalizacji, ponieważ nie jest domyślnie włączona. W wielu przypadkach pomaga dołączyć `#pragma loop(hint_parallel(N))` w kodzie bezpośrednio przed pętli, które mają równoległe.
- Auto-wektoryzator i auto-równoległoścializator może współpracować, dzięki czemu obliczenia są rozłożone na wiele rdzeni i kod na każdym rdzeniu używa jego rejestrów wektorowych.

### <a name="new-in-visual-studio-2012-update-1"></a>Nowość w programie Visual Studio 2012 Update 1

Docelowy system Windows XP podczas tworzenia kodu języka C++.
Kompilator i biblioteki programu Microsoft C++ są przeznaczone dla systemów Windows XP i Windows Server 2003.

#### <a name="parallel-programming-support"></a>Obsługa programowania równoległego

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP przyspiesza wykonywanie kodu C++, korzystając ze sprzętu równoległego danych, który jest zwykle obecny jako procesor GPU na dyskretnej karcie graficznej. Model programowania C++ AMP obejmuje tablice wielowymiarowe, indeksowanie, transfer pamięci, kafli i bibliotekę funkcji matematycznych. Za pomocą rozszerzeń języka C++ AMP i ograniczeń kompilatora, można kontrolować sposób przenoszenia danych z procesora CPU do procesora GPU i z powrotem.

**Debugowania.** Środowisko debugowania dla aplikacji, które używają C++ AMP do kierowania na gpu jest podobnie jak debugowanie dla innych aplikacji języka C++. Obejmuje to nowe dodatki do debugowania równoległego, które zostały wymienione wcześniej.

**Profilowania.** Obecnie istnieje obsługa profilowania aktywności GPU opartej na amp i innych modelach programowania opartych na technologii Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Ogólne ulepszenia programowania równoległego

Dzięki przejściu sprzętu na architekturę wielordzeniową i wielordzeniową deweloperzy nie mogą już polegać na stale rosnących prędkościach zegara z pojedynczych rdzeni. Obsługa programowania równoległego w współbiegi środowiska wykonawczego umożliwia deweloperom korzystanie z tych nowych architektur.
W programie Visual Studio 2010 wprowadzono zaawansowane biblioteki równoległości języka C++, takie jak biblioteka wzorców równoległych, wraz z funkcjami, aby korzystać z współbieżności, wyrażając zaawansowane potoki przepływu danych. W programie Visual Studio 2012 te biblioteki zostały rozszerzone, aby zapewnić lepszą wydajność, większą kontrolę i bogatszą obsługę wzorców równoległych, których deweloperzy najbardziej potrzebują. Zakres oferty obejmuje teraz:

- Bogaty model programowania oparty na zadaniach, który obsługuje asynchrony i kontynuacji.
- Algorytmy równoległe, które obsługują równoległość sprzężenia widelca (parallel_for, parallel_for z koligacji, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Kontenery bezpieczne dla współbieżności, które zapewniają bezpieczne dla wątków wersje struktur danych std, takich jak priority_queue, kolejka, wektor i mapa.
- Biblioteka agentów asynchronicznych, której deweloperzy mogą używać do wyrażania potoków przepływu danych, które naturalnie rozkładają się na równoczesne jednostki.
- Konfigurowalny harmonogram i menedżer zasobów, aby ułatwić płynny skład wzorców na tej liście.

##### <a name="general-parallel-debugging-enhancements"></a>Ogólne ulepszenia debugowania równoległego

Oprócz okna **Zadania równoległe** i **równoległe stosy** okna, Visual Studio 2012 oferuje nowe okno **czujki równoległej,** dzięki czemu można sprawdzić wartości wyrażenia we wszystkich wątkach i procesach i wykonać sortowanie i filtrowanie na wynik. Można również użyć własnych wizualizatorów, aby rozszerzyć okno i można skorzystać z nowej obsługi wielu procesów we wszystkich oknach narzędzi.

### <a name="ide"></a>IDE

**Obsługa szablonów programu Visual Studio.** Teraz można użyć technologii szablonów programu Visual Studio do tworzenia szablonów projektów i elementów języka C++.

**Obciążenie roztworu asynchroniiowego.** Projekty są teraz ładowane asynchronicznie — najpierw kluczowe części rozwiązania — dzięki czemu można rozpocząć szybszą pracę.

**Automatyczne wdrażanie do zdalnego debugowania.** Wdrożenie plików do zdalnego debugowania w języku Visual C++ zostało uproszczone. Opcja **Wdrażanie** w menu kontekstowym projektu automatycznie kopiuje na komputer zdalny pliki określone we właściwościach konfiguracji debugowania. Ręczne kopiowanie plików na komputer zdalny nie jest już wymagane.

**C++/CLI IntelliSense.** C ++ / CLI ma teraz pełną obsługę IntelliSense. Funkcje IntelliSense, takie jak Szybkie informacje, Pomoc dotycząca parametrów, Członkowie listy i Automatyczne uzupełnianie, działają teraz dla języka C++/CLI. Ponadto inne ulepszenia IntelliSense i IDE wymienione w tym dokumencie również działają dla języka C++/CLI.

**Bogatsze etykietki narzędzi IntelliSense.** Etykietki narzędzi Programu IntelliSense Quick Info firmy C++ wyświetlą teraz bogatsze informacje o stylu komentarzy w dokumentacji XML. Jeśli używasz interfejsu API z biblioteki — na przykład C++ AMP — który zawiera komentarze dokumentacji XML, a następnie etykietka narzędzia IntelliSense wyświetla więcej informacji niż tylko deklaracji. Ponadto jeśli kod ma komentarze dokumentacji XML, etykietki narzędzia IntelliSense pokażą bogatsze informacje.

**Konstrukcje kodu języka C++.** Szkielet kod jest dostępny dla switch, if-else, dla pętli i innych podstawowych konstrukcji kodu, na liście rozwijanej Członków listy. Wybierz fragment kodu z listy, aby wstawić go do kodu, a następnie wypełnij wymaganą logikę. Można również utworzyć własne niestandardowe fragmenty kodu do użycia w edytorze.

**Ulepszenia członków listy.** Lista rozwijana **Członków listy** pojawia się automatycznie podczas wpisywalania kodu do edytora kodu. Wyniki są filtrowane, dzięki czemu tylko odpowiednie elementy członkowskie są wyświetlane podczas pisania. Można kontrolować rodzaj logiki filtrowania, która jest używana przez listę członków — w oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Zaawansowane**.

**Koloryzacja semantyczna.** Typy, wyliczenia, makra i inne tokeny Języka C++ mają teraz domyślnie kolorowanie.

**Wyróżnianie odwołań.** Wybranie symbolu powoduje teraz wyróżnienie wszystkich wystąpień symbolu w bieżącym pliku. Naciśnij **klawisze Ctrl**+**Shift**+**Toch strzałka w górę** lub Strzałka**przesunięcie**+w dół**klawisza** **Ctrl,**+aby przejść między wyróżnionymi odwołaniami. Tę funkcję można wyłączyć w oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Zaawansowane**.

### <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

#### <a name="static-code-analysis"></a>Statyczna analiza kodu

Analiza statyczna dla języka C++ została zaktualizowana w celu zapewnienia bogatszych informacji kontekstowych o błędach, większej liczby reguł analizy i lepszych wyników analizy. W nowym oknie Analiza kodu można filtrować wiadomości według słowa kluczowego, projektu i ważności. Po wybraniu wiadomości w oknie wiersz w kodzie, w którym wiadomość została wyzwolona, jest wyróżniony w edytorze kodu. Dla niektórych ostrzeżeń C++ komunikat zawiera listę wierszy źródłowych, które pokazują ścieżkę wykonywania, która prowadzi do ostrzeżenia; punktów decyzyjnych i powody podjęcia tej konkretnej ścieżki.
Analiza kodu jest uwzględniona w większości wersji programu Visual Studio 2012. W wersjach Professional, Premium i Ultimate wszystkie zasady są uwzględniane. W wersjach Express dla systemów Windows 8 i Windows Phone uwzględniono tylko najważniejsze ostrzeżenia. Analiza kodu nie jest uwzględniona w wersji Express for Web.
Oto kilka innych ulepszeń analizy kodu:

- Nowe ostrzeżenia współbieżności pomagają uniknąć błędów współbieżności, upewniając się, że używasz odpowiednich dyscyplin blokowania w programach wielowątkowych C/C++. Analizator wykrywa potencjalne warunki wyścigu, inwersji kolejności blokady, wywołujący/wywołujący blokowanie naruszeń umowy, niedopasowane operacje synchronizacji i inne błędy współbieżności.
- Można określić reguły C++, które mają być stosowane do analizy kodu uruchamia się przy użyciu zestawów reguł.
- W oknie **Analiza kodu** można wstawić do kodu źródłowego pragmy, która pomija wybrane ostrzeżenie.
- Można zwiększyć dokładność i kompletność analizy kodu statycznego przy użyciu nowej wersji języka adnotacji kodu źródłowego firmy Microsoft (SAL), aby opisać, jak funkcja używa swoich parametrów, założenia, które sprawia, że o nich i gwarancje, że sprawia, że po zakończeniu.
- Obsługa 64-bitowych projektów C++.

#### <a name="updated-unit-test-framework"></a>Zaktualizowana struktura testów jednostkowych

Użyj nowej struktury testów jednostkowych języka C++ w programie Visual Studio do pisania testów jednostkowych języka C++. Dodaj nowy projekt testu jednostkowego do istniejącego rozwiązania C++, lokalizując szablon projektu testu jednostkowego języka C++ w kategorii Visual C++ w oknie dialogowym Nowy projekt. Rozpocznij pisanie testów jednostkowych w wygenerowanym TEST_METHOD skrótowym kodu w pliku Unittest1.cpp. Po zapisaniu kodu testowego skompiluj rozwiązanie. Aby uruchomić testy, otwórz okno **Eksploratora testów jednostek,** wybierając **pozycję Wyświetl** > inny**Eksplorator testów jednostek****systemu Windows,** > a następnie w menu skrótów dla odpowiedniego przypadku testowego wybierz pozycję Uruchom wybrany **test**. Po zakończeniu przebiegu testu można wyświetlić wyniki testów i dodatkowe informacje śledzenia stosu w tym samym oknie.

#### <a name="architecture-dependency-graphs"></a>Wykresy zależności architektury

Aby lepiej zrozumieć kod, można teraz wygenerować wykresy zależności dla binarnych, klasy, obszaru nazw i plików w rozwiązaniu. Na pasku menu wybierz polecenie **Architecture** > **Generate Dependency Graph**, a następnie **dla rozwiązania** lub dla **pliku** dołączanego, aby wygenerować wykres zależności. Po zakończeniu generowania wykresu można go eksplorować, rozwijając go, rozwijając każdy węzeł, poznać relacje zależności, przechodząc między węzłami, i przeglądać kod źródłowy, wybierając **polecenie Wyświetl zawartość** w menu skrótów węzła. Aby wygenerować wykres zależności dla plików dołączanych, w menu skrótów dla pliku kodu źródłowego \*cpp lub \*pliku nagłówka .h wybierz pozycję **Generuj wykres dołączanych plików**.

#### <a name="architecture-explorer"></a>Eksplorator architektury

Za pomocą **Eksploratora architektury**można eksplorować zasoby w rozwiązaniu C++, projektach lub plikach. Na pasku menu wybierz pozycję **Architecture** > **Windows** > **Architecture Explorer**. Można wybrać węzeł, który Cię interesuje, na przykład **widok klasy**. W takim przypadku prawa strona okna narzędzia jest rozwinięta o listę obszarów nazw. Jeśli wybierzesz obszar nazw, nowa kolumna pokazuje listę klas, struktur i wyliczenia w tej przestrzeni nazw. Możesz kontynuować eksplorowanie tych zasobów lub wrócić do kolumny po lewej stronie, aby rozpocząć inną kwerendę. Zobacz **Znajdowanie kodu za pomocą Eksploratora architektury**.

#### <a name="code-coverage"></a>Pokrycie kodu

Pokrycie kodu zostało zaktualizowane do dynamicznie instrumencie plików binarnych w czasie wykonywania. Zmniejsza to obciążenie konfiguracji i zapewnia lepszą wydajność. Można również zbierać dane pokrycia kodu z testów jednostkowych dla aplikacji Języka C++. Po utworzeniu testów jednostkowych języka C++ można użyć **Eksploratora testów jednostkowych,** aby odnajdować testy w rozwiązaniu. Aby uruchomić testy jednostkowe i zebrać dla nich dane pokrycia kodu, w **Eksploratorze testów jednostkowych**wybierz pozycję **Analizuj pokrycie kodu**. Wyniki pokrycia kodu można sprawdzić w oknie **Wyniki pokrycia kodu** — na pasku menu wybierz polecenie **Testuj** > **wyniki pokrycia kodu**systemu**Windows** > .

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co nowego w języku C++ w programie Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Kompilator i konsolidator języka C++

**słowo kluczowe auto.** Słowo kluczowe **auto** ma nowy cel. Użyj domyślnego znaczenia **auto** słowa kluczowego, aby zadeklarować zmienną, której typ jest wydedukowany z wyrażenia inicjowania w deklaracji zmiennej. Opcja `/Zc:auto` kompilatora wywołuje nowe lub poprzednie znaczenie **auto** słowa kluczowego.

**specyfikator typu decltype.** Specyfikator typu **decltype** zwraca typ określonego wyrażenia. Użyj **specyfikatora typu decltype** w połączeniu z **auto** słowa kluczowego, aby zadeklarować typ, który jest złożony lub znany tylko kompilatorowi. Na przykład użyj kombinacji do zadeklarowania funkcji szablonu, którego typ zwracany zależy od typów jego argumentów szablonu. Lub zadeklaruj funkcję szablonu, która wywołuje inną funkcję, a następnie zwraca typ zwracany wywoływaną funkcję.

**Wyrażenia Lambda.** Funkcje Lambda mają treść funkcji, ale nie mają nazwy. Funkcje Lambda łączą najlepsze cechy wskaźników funkcji i obiektów funkcyjnych. Użyj funkcji lambda samodzielnie, jako parametr funkcji szablonu zamiast obiektu funkcji lub razem z **auto** słowa kluczowego, aby zadeklarować zmienną, której typem jest lambda.

**Odwołanie Rvalue.** Rvalue reference declarator (&&) deklaruje odwołanie do wartości r. Odwołanie do wartości rwalue umożliwia użycie semantyki przenoszenia i doskonałe przekazywanie do pisania bardziej wydajnych konstruktorów, funkcji i szablonów.

**static_assert deklaracji.** Deklaracja **static_assert** testuje asercja oprogramowania w czasie kompilacji, w przeciwieństwie do innych mechanizmów potwierdzenia, które testują w czasie wykonywania. Jeśli twierdzenie nie powiedzie się, kompilacja kończy się niepowodzeniem i zostanie wydany określony komunikat o błędzie.

**nullptr i __nullptr słowa kluczowe.** MSVC umożliwia użycie słowa kluczowego **nullptr** z kodem macierzystym lub z kodem zarządzanym. **Nullptr** — słowo kluczowe wskazuje, że dojście do obiektu, wskaźnik wewnętrzny lub typ wskaźnika macierzystego nie wskazują obiektu. Kompilator interpretuje **nullptr** do kodu zarządzanego podczas korzystania z opcji `/clr` kompilatora i kodu macierzystego, `/clr` gdy nie używasz tej opcji.
Słowo kluczowe **__nullptr** specyficzne dla firmy Microsoft ma takie samo znaczenie jak **nullptr**, ale dotyczy tylko kodu macierzystego. Jeśli skompilujesz natywny kod `/clr` C/C++ przy użyciu opcji kompilatora, kompilator nie może określić, czy słowo kluczowe **nullptr** jest terminem macierzystym czy zarządzanym. Aby twoje intencje były jasne dla kompilatora, użyj słowa kluczowego nullptr, aby określić termin zarządzany i **__nullptr** określić termin macierzysty.

**/Zc:Trigraphs Opcja kompilatora.** Domyślnie obsługa trigraphs jest wyłączona. Użyj `/Zc:trigraphs` opcji kompilatora, aby włączyć obsługę trygrafów.
Trygraf składa się z dwóch kolejnych znaków zapytania (??), po których następuje unikatowy trzeci znak. Kompilator zastępuje trygraf odpowiednim znakiem interpunkcyjnym. Na przykład kompilator zastępuje ?? = trygraf ze znakiem # (znak numer). Użyj trygrafów w plikach źródłowych języka C, które używają zestawu znaków, który nie zawiera określonych znaków interpunkcyjnych.

**Nowa opcja optymalizacji z przewodnikiem po profilu.** PogoSafeMode to nowa opcja optymalizacji z przewodnikiem po profilu, która pozwala określić, czy należy używać trybu awaryjnego, czy trybu szybkiego podczas optymalizacji aplikacji. Tryb awaryjny jest bezpieczny dla wątków, ale jest wolniejszy niż tryb szybki. Tryb szybki jest zachowaniem domyślnym.

**Nowa opcja wspólnego środowiska wykonawczego języka (CLR) /clr:nostdlib.** Zostanie dodana `/clr` nowa opcja (kompilacja środowiska wykonawczego języka wspólnego). Jeśli uwzględniono różne wersje tych samych bibliotek, zostanie wyświetlony błąd kompilacji. Nowa opcja umożliwia wykluczenie domyślnych bibliotek CLR, dzięki czemu program może używać określonej wersji.

**Nowa dyrektywa pragma detect_mismatch.** Dyrektywa pragma detect_mismatch umożliwia umieszczenie znacznika w plikach, który jest porównywany z innymi tagami o tej samej nazwie. Jeśli istnieje wiele wartości dla tej samej nazwy, konsolidator wystawia błąd.

**XOP Intrinsics, FMA4 Intrinsics i LWP Intrinsics.** Nowe funkcje wewnętrzne zostały dodane do obsługi XOP Intrinsics Dodano dla programu Visual Studio 2010 SP1, FMA4 Intrinsics Dodane dla programu Visual Studio 2010 SP1 i LWP Intrinsics Dodane dla visual studio 2010 technologii procesora SP1. Użyj __cpuid, __cpuidex, aby określić, które technologie procesora są obsługiwane na określonym komputerze.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Projekty programu Visual Studio C++ i system kompilacji

**Msbuild.** Rozwiązania i projekty programu Visual C++ są teraz tworzone przy użyciu pliku MSBuild.exe, który zastępuje plik VCBuild.exe. MSBuild jest tym samym elastyczne, rozszerzalne narzędzie kompilacji oparte na XML, który jest używany przez inne języki programu Visual Studio i typy projektów. Z powodu tej zmiany pliki projektu programu Visual Studio C++ używają teraz formatu pliku XML i mają rozszerzenie nazwy pliku .vcxproj. Pliki projektu programu Visual Studio C++ z wcześniejszych wersji programu Visual Studio są automatycznie konwertowane na nowy format pliku.

**Katalogi VC++.** Ustawienie katalogów VC++ znajduje się teraz w dwóch miejscach. Strony właściwości projektu służy do ustawiania wartości dla projektu dla katalogów VC++. Menedżer **właściwości** i arkusz właściwości można ustawić globalne wartości dla katalogów VC++ dla tej waluty.

**Zależności między projektami.** We wcześniejszych wersjach zdefiniowane zależności między projektami były przechowywane w pliku rozwiązania. Gdy te rozwiązania są konwertowane na nowy format pliku projektu, zależności są konwertowane na odwołania do projektu. Ta zmiana może mieć wpływ na aplikacje, ponieważ pojęcia zależności rozwiązania i odwołania do projektu są różne.

**Makra i zmienne środowiskowe.** Nowe makro _ITERATOR_DEBUG_LEVEL wywołuje obsługę debugowania dla iteratorów. Użyj tego makra zamiast starszych _SECURE_SCL i _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

**Biblioteki wykonawcze współbieżności.** Struktura środowiska wykonawczego współbieżności obsługuje aplikacje i składniki, które działają jednocześnie i jest platformą do programowania równoczesnych aplikacji w języku Visual C++. Do obsługi programowania równoczesnych aplikacji, biblioteki wzorców równoległych (PPL) udostępnia kontenery ogólnego przeznaczenia i algorytmy do wykonywania równoległości szczegółowe. Biblioteka agentów asynchronicznych udostępnia model programowania oparty na aktorze i interfejsy przekazywania wiadomości dla zadań przepływu danych i potoków.

**Standardowa biblioteka C++.** Na poniższej liście opisano wiele zmian, które zostały wprowadzone do standardowej biblioteki C++.

- Nowa funkcja języka C++ odniesienia rvalue została wykorzystana do zaimplementowania semantyki przenoszenia i doskonałego przekazywania dla wielu funkcji w standardowej bibliotece szablonów. Przenieś semantyki i doskonałe przekazywanie znacznie poprawić wydajność operacji, które przydzielają lub przypisują zmienne lub parametry.
- Odwołania Rvalue są również używane `unique_ptr` do implementowania nowej klasy, która `auto_ptr` jest bezpieczniejszym typem inteligentnego wskaźnika niż klasa. Klasa `unique_ptr` jest ruchoma, ale nie można kopiować, implementuje ścisłą semantyką własności bez wpływu na bezpieczeństwo i działa dobrze z kontenerami, które są świadome odwołań rvalue. Klasa `auto_ptr` jest przestarzała.
- Do algorytmu dodano `find_if_not`piętnaście `is_sorted`nowych funkcji, na \<przykład `copy_if`, i , do algorytmu> nagłówka.
- W \<nagłówku> pamięci nowa funkcja make_shared jest wygodnym, niezawodnym i wydajnym sposobem tworzenia udostępnionego wskaźnika do obiektu w tym samym czasie, gdy obiekt jest konstruowany.
- Pojedyncze połączone listy są \<obsługiwane przez nagłówek> forward_list.
- Nowe `cbegin`, `cend` `crbegin`, `crend` i funkcje `const_iterator` członkowskie zapewniają, że porusza się do przodu lub do tyłu przez kontener.
- Nagłówek \<system_error> i powiązane szablony obsługują przetwarzanie błędów systemu niskiego poziomu. Elementy członkowskie `exception_ptr` klasy mogą służyć do transportu wyjątków między wątkami.
- Nagłówek \<> kodekerowiskowy obsługuje konwertowanie różnych kodowania znaków Unicode na inne kodowania.
- Alokatorów \<> nagłówka definiuje kilka szablonów, które pomagają przydzielić i zwolnić bloki pamięci dla kontenerów opartych na węzłach.
- Istnieje wiele aktualizacji \<nagłówka> losowych.

### <a name="microsoft-foundation-class-mfc-library"></a>Biblioteka microsoft foundation class (MFC)

**Funkcje systemu Windows 7.** MFC obsługuje wiele funkcji systemu Windows 7, na przykład interfejs użytkownika Wstążki (UI), pasek zadań, listy szybkiego dostępu, miniatury z kartami, podgląd miniatur, pasek postępu, nakładkę ikon i indeksowanie wyszukiwania. Ponieważ MFC automatycznie obsługuje wiele funkcji systemu Windows 7, nie trzeba modyfikować istniejącej aplikacji. Aby obsługiwać inne funkcje w nowych aplikacjach, użyj Kreatora aplikacji MFC, aby określić funkcje, których chcesz użyć.

**Rozpoznawanie wielu osób.** MFC obsługuje aplikacje, które mają interfejs użytkownika multi-touch, na przykład aplikacje, które są zapisywane dla systemu operacyjnego Microsoft Surface. Aplikacja wielodotywna może obsługiwać wiadomości dotykowe systemu Windows i komunikaty gestów, które są kombinacjami wiadomości dotykowych. Wystarczy zarejestrować aplikację dla zdarzeń dotykowych i gestów, a system operacyjny będzie kierować zdarzenia multi-touch do programów obsługi zdarzeń.

**Świadomość wysokiej rozdzielczości DPI.** Domyślnie aplikacje MFC są teraz wysokiej rozdzielczości DPI.Default, MFC applications are now High-DPI-aware. Jeśli aplikacja jest wysokiej rozdzielczości DPI (wysokie kropki na cal) świadomy, system operacyjny może skalować okna, tekst i inne elementy interfejsu użytkownika do bieżącej rozdzielczości ekranu. Oznacza to, że skalowany obraz jest bardziej prawdopodobne, aby być poprawnie rozmieszczony, a nie obcięty lub piksele.

**Menedżer ponownego uruchamiania.** Menedżer ponownego uruchamiania automatycznie zapisuje dokumenty i uruchamia ponownie aplikację, jeśli nieoczekiwanie zostanie zamknięta lub zostanie ponownie uruchomiona. Na przykład można użyć menedżera ponownego uruchamiania, aby uruchomić aplikację po zamknięciu przez automatyczną aktualizację. Aby uzyskać więcej informacji na temat konfigurowania aplikacji do używania menedżera ponownego uruchamiania, zobacz **Jak: Dodawanie pomocy technicznej menedżera ponownego uruchamiania**.

**Ctaskdialog.** Klasa `CTaskDialog` może być używana zamiast `AfxMessageBox` standardowego okna komunikatu. Klasa `CTaskDialog` wyświetla i zbiera więcej informacji niż standardowe okno komunikatu.

#### <a name="safeint-library"></a>Biblioteka SafeInt

Nowa biblioteka SafeInt wykonuje bezpieczne operacje arytmetyczne, które uwzględniają przepełnienie liczby całkowitej. Ta biblioteka porównuje również różne rodzaje liczby całkowite.

#### <a name="new-active-template-library-atl-macros"></a>Nowe makra aktywnej biblioteki szablonów (ATL)

Nowe makra zostały dodane do ATL, aby rozszerzyć funkcjonalność PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE i PROP_ENTRY_INTERFACE_EX umożliwiają dodanie listy prawidłowych identyfikatorów CLSID. PROP_ENTRY_INTERFACE_CALLBACK i PROP_ENTRY_INTERFACE_CALLBACK_EX umożliwiają określenie funkcji wywołania zwrotnego w celu ustalenia, czy identyfikator CLSID jest prawidłowy.

#### <a name="analyze-warnings"></a>/analiza Ostrzeżenia

Większość `/analyze` ostrzeżeń (Enterprise Code Analysis) zostały usunięte z bibliotek c run-time (CRT), MFC i ATL.

#### <a name="animation-and-d2d-support"></a>Animacja i obsługa D2D

MFC obsługuje teraz animację i grafikę Direct2D. Biblioteka MFC ma kilka nowych klas MFC i funkcje do obsługi tej funkcji. Istnieją również dwa nowe wskazówki, aby pokazać, jak dodać obiekt D2D i obiekt animacji do projektu. Te wskazówki są **instruktażowe: Dodawanie obiektu D2D do projektu MFC** i **przewodnik: Dodawanie animacji do projektu MFC**.

### <a name="ide"></a>IDE

**Ulepszony IntelliSense.** Technologia IntelliSense for Visual C++ została całkowicie przeprojektowana, aby była szybsza, dokładniejsza i mogła obsługiwać większe projekty. Aby osiągnąć ten udoskonalenie, IDE wprowadza rozróżnienie między jak deweloper widoki i modyfikuje kod źródłowy i jak IDE używa kodu źródłowego i ustawień projektu do tworzenia rozwiązania.
Z powodu tego rozdzielenia obowiązków funkcje przeglądania, takie jak **Widok klasy** i nowe okno dialogowe **Nawiguj do,** są obsługiwane przez system oparty na nowym pliku bazy danych pulpitu SQL Server (sdf), który zastępuje stary plik przeglądania bez kompilacji (.ncb). Funkcje IntelliSense, takie jak Szybkie informacje, Automatyczne uzupełnianie i Pomoc dotycząca parametrów analizują jednostki tłumaczeniowe tylko wtedy, gdy jest to wymagane. Funkcje hybrydowe, takie jak nowe okno **hierarchii połączeń,** używają kombinacji funkcji przeglądania i intellisense.
Ponieważ IntelliSense przetwarza tylko informacje, które są wymagane w tej chwili, IDE jest bardziej elastyczne. Ponadto, ponieważ informacje są bardziej aktualne, widoki IDE i okna są dokładniejsze. Na koniec, ponieważ infrastruktura IDE jest lepiej zorganizowana, bardziej wydajne i bardziej skalowalne, może obsługiwać większe projekty.

**Poprawiono błędy IntelliSense.** IDE lepiej wykrywa błędy, które mogą spowodować utratę IntelliSense i wyświetla czerwone faliste podkreślenia pod nimi. Ponadto IDE zgłasza błędy IntelliSense do **okna listy błędów**. Aby wyświetlić kod, który jest przyczyną problemu, kliknij dwukrotnie błąd w **oknie lista błędów**.

**funkcja autouzupełniania #include.** IDE obsługuje automatyczne uzupełnianie `#include` słowa kluczowego. Po wpisaniu `#include`IDE tworzy pole listy rozwijanej prawidłowych plików nagłówka. Jeśli nadal wpisujesz nazwę pliku, IDE filtruje listę na podstawie wpisu. W dowolnym momencie można wybrać z listy plik, który chcesz dołączyć. Dzięki temu można szybko dołączyć pliki bez znajomości dokładnej nazwy pliku.

**Przejdź do.** Okno dialogowe **Nawiguj do** umożliwia wyszukiwanie wszystkich symboli i plików w projekcie, które pasują do określonego ciągu. Wyniki wyszukiwania są natychmiast zmieniane podczas wpisywane dodatkowe znaki w ciągu wyszukiwania. Pole **Opinie o wynikach** informuje o liczbie znalezionych elementów i pomaga zdecydować, czy ograniczyć wyszukiwanie. Pola **Rodzaj/Zakres,** **Lokalizacja**i **Podgląd** opinii ułatwiają rozróżnianie elementów o podobnych nazwach. Ponadto można rozszerzyć tę funkcję do obsługi innych języków programowania.

**Debugowanie równoległe i profilowanie.** Debuger programu Visual Studio jest świadomy środowiska wykonawczego współbieżności i pomaga w rozwiązywaniu problemów z aplikacjami przetwarzania równoległego. Za pomocą nowego narzędzia profilowania współbieżności można wizualizować ogólne zachowanie aplikacji. Ponadto można użyć nowych okien narzędzi do wizualizacji stanu zadań i ich stosów wywołań.

**Projektant wstążki.** **Projektant wstążki** to edytor graficzny, który umożliwia tworzenie i modyfikowanie interfejsu użytkownika wstążki MFC. Ostateczny interfejs użytkownika wstążki jest reprezentowany przez plik zasobów oparty na języku XML (.mfcribbon-ms). W przypadku istniejących aplikacji można przechwycić bieżący interfejs użytkownika wstążki, tymczasowo dodając kilka wierszy kodu, a następnie wywołując **Projektanta wstążki**. Po utworzeniu pliku zasobu wstążki można zastąpić odręczny kod interfejsu użytkownika wstążki kilkoma instrukcjami, które ładują zasób wstążki.

**Wywołaj hierarchię.** Okno **Hierarchia wywołań** umożliwia przechodzenie do wszystkich funkcji, które są wywoływane przez określoną funkcję lub do wszystkich funkcji, które wywołują określoną funkcję.

### <a name="tools"></a>Narzędzia

**Kreator klas MFC.** Visual C++ 2010 przywraca dobrze traktowane narzędzie Kreatora klas MFC. Kreator klas MFC jest wygodnym sposobem dodawania klas, wiadomości i zmiennych do projektu bez konieczności ręcznego modyfikowania zestawów plików źródłowych.

**Kreator sterowania ATL.** Kreator sterowania ATL nie wypełnia już `ProgID` automatycznie tego pola. Jeśli kontrolka ATL `ProgID`nie ma , inne narzędzia mogą nie działać z nim. Jednym z przykładów narzędzia, które `ProgID` wymaga formanty mieć jest **wstawanie aktywnego formantu** okna dialogowego. Aby uzyskać więcej informacji o oknie dialogowym, zobacz **Okno dialogowe Wstawianie formantu ActiveX**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

Dodanie typu danych YMMWORD obsługuje 256-bitowe materiały multimedialne zawarte w instrukcjach Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co nowego w języku C++ w programie Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Zintegrowane środowisko programistyczne Visual C++ (IDE)

- Okna dialogowe utworzone w aplikacjach ATL, MFC i Win32 są teraz zgodne ze wskazówkami dotyczącymi stylu systemu Windows Vista. Podczas tworzenia nowego projektu przy użyciu programu Visual Studio 2008 wszystkie okna dialogowe wstawiane do aplikacji będą zgodne z wytyczną stylu systemu Windows Vista. Jeśli ponownie skompilować projekt, który został utworzony z wcześniejszej wersji programu Visual Studio, wszystkie istniejące okna dialogowe zachowa ten sam wygląd, który wcześniej miał. Aby uzyskać więcej informacji na temat wstawiania okien dialogowych do aplikacji, zobacz **Edytor okien dialogowych**.

- Kreator **projektu ATL** ma teraz opcję rejestrowania składników dla wszystkich użytkowników. Począwszy od programu Visual Studio 2008 składniki COM i biblioteki typów tworzone przez kreatora **projektu ATL** są rejestrowane w węźle HKEY_CURRENT_USER rejestru, chyba że wybierzesz **składnik Zarejestruj dla wszystkich użytkowników**.
- Kreator **projektu ATL** nie udostępnia już opcji tworzenia przypisanych projektów ATL. Począwszy od programu Visual Studio 2008 kreator **projektu ATL** nie ma opcji zmiany przypisanego stanu nowego projektu. Wszystkie nowe projekty ATL, które tworzy kreator, są teraz nieprzypisane.
- Zapis do rejestru można przekierować. Wraz z wprowadzeniem systemu Windows Vista zapisywanie do niektórych obszarów rejestru wymaga uruchomienia programu w trybie podwyższonego poziomu. Nie jest pożądane, aby zawsze uruchamiać program Visual Studio w trybie podwyższonego poziomu. Przekierowanie na użytkownika automatycznie przekierowuje zapisy rejestru z HKEY_CLASSES_ROOT do HKEY_CURRENT_USER bez żadnych zmian w programowaniu.
- Projektant **klas** ma teraz ograniczoną obsługę natywnego kodu C++. We wcześniejszych wersjach programu Visual Studio **projektant klas** pracował tylko z programami Visual C# i Visual Basic. Użytkownicy języka C++ mogą teraz używać **projektanta klas,** ale tylko w trybie tylko do odczytu. Aby uzyskać więcej informacji na temat **używania Projektanta klas** w języku C++, zobacz **Praca z kodem języka Visual C++ w Projektancie klas**.
- Kreator projektu nie ma już opcji tworzenia projektu programu SQL Server w języku C++. Począwszy od programu Visual Studio 2008, nowy kreator projektu nie ma opcji, aby utworzyć projekt programu SQL Server języka C++. Projekty programu SQL Server utworzone przy użyciu wcześniejszej wersji programu Visual Studio będą nadal kompilować i działać poprawnie.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

#### <a name="general"></a>Ogólne

- Aplikacje mogą być powiązane z określonymi wersjami bibliotek języka Visual C++. Czasami aplikacja zależy od aktualizacji, które zostały wprowadzone do bibliotek języka Visual C++ po wydaniu. W takim przypadku uruchomienie aplikacji na komputerze, który ma wcześniejsze wersje bibliotek może spowodować nieoczekiwane zachowanie. Teraz można powiązać aplikację z określoną wersją bibliotek, aby nie była uruchamiana na komputerze, na który ma wcześniejszą wersję bibliotek.

#### <a name="stlclr-library"></a>Biblioteka STL/CLR

- Visual C++ zawiera teraz bibliotekę STL/CLR. Biblioteka STL/CLR jest opakowaniem standardowej biblioteki szablonów (STL), podzbioru standardowej biblioteki C++, do użytku z c++ i środowiskiem uruchomieniowym języka wspólnego .NET Framework (CLR). Z STL/CLR, można teraz używać wszystkich kontenerów, iteratorów i algorytmów STL w środowisku zarządzanym.

#### <a name="mfc-library"></a>Biblioteka MFC

- System Windows Vista obsługuje typowe formanty. Ponad 150 metod w 18 nowych lub istniejących klas zostały dodane do obsługi funkcji w systemie Windows Vista lub w celu poprawy funkcjonalności w bieżących klas MFC.
- Nowa `CNetAddressCtrl` klasa umożliwia wprowadzanie i sprawdzanie poprawności adresów IPv4 i IPv6 lub nazw DNS.
- Nowa `CPagerCtrl` klasa upraszcza użycie formantu pagera systemu Windows.
- Nowa `CSplitButton` klasa upraszcza użycie formantu splitbutton systemu Windows, aby wybrać akcję domyślną lub opcjonalną.

#### <a name="c-support-library"></a>Biblioteka obsługi języka C++

- C++ wprowadza biblioteki organizowania. Biblioteka organizowania zapewnia łatwy i zoptymalizowany sposób organizowania danych między środowiskami macierzystymi i zarządzanymi. Biblioteka jest alternatywą dla bardziej złożonych i mniej wydajnych podejść, takich jak korzystanie z funkcji PInvoke. Zobacz **omówienie organizowania w języku C++, aby** uzyskać więcej informacji.

#### <a name="atl-server"></a>Serwer ATL

- Serwer ATL jest zwalniany jako udostępniony projekt źródłowy.
- Większość bazy kodu serwera ATL został wydany jako projekt źródła udostępnionego w programie CodePlex i nie jest zainstalowany jako część programu Visual Studio 2008. Kilka plików skojarzonych z usługą ATL Server nie jest już częścią programu Visual Studio. Aby uzyskać listę usuniętych plików, zobacz **Usuwanie plików serwera ATL**.
- Klasy kodowania i dekodowania danych z atlenc.h oraz funkcje i klasy narzędziowe z atlutil.h i atlpath.h są teraz częścią biblioteki ATL.
- Firma Microsoft będzie nadal obsługiwać wersje programu ATL Server, które są zawarte we wcześniejszych wersjach programu Visual Studio, o ile te wersje programu Visual Studio są obsługiwane. Program CodePlex będzie nadal rozwijać kod serwera ATL jako projekt społeczności. Firma Microsoft nie obsługuje wersji programu ATL Server w usłudze CodePlex.

### <a name="visual-c-compiler-and-linker"></a>Kompilator i konsolidator języka Visual C++

#### <a name="compiler-changes"></a>Zmiany kompilatora

- Kompilator obsługuje zarządzane kompilacje przyrostowe. Po określeniu tej opcji kompilator nie będzie ponownie kompilować kodu po zmianie zestawu, do którego istnieje odwołanie. Zamiast tego wykona kompilację przyrostową. Pliki są ponownie kompilowane tylko wtedy, gdy zmiany wpływają na kod zależny.
- Atrybuty związane z serwerem ATL nie są już obsługiwane. Kompilator nie obsługuje już kilku atrybutów, które były bezpośrednio związane z usługą ATL Server. Aby uzyskać pełną listę usuniętych atrybutów, zobacz Przełamywanie zmian.
- Kompilator obsługuje mikroarchitekturę Intel Core. Kompilator zawiera strojenie mikroarchitektury Intel Core podczas generowania kodu. Domyślnie to strojenie jest włączone i nie można go wyłączyć, ponieważ pomaga również Pentium 4 i innym procesorom.
- Wewnętrzne funkcje obsługi nowych procesorów AMD i Intel. Kilka nowych wewnętrznych instrukcji obsługuje większą funkcjonalność nowszych procesorów AMD i Intel. Aby uzyskać więcej informacji na temat nowych wewnętrzną, zobacz **Uzupełniające rozszerzenia SIMD do przesyłania strumieniowego 3 Instrukcje**, **Streaming SIMD Extensions 4 Instructions**, **SSE4A i Advanced Bit Manipulation Intrinsics**, **AES Intrinsics**, **_mm_clmulepi64_si128**, i **__rdtscp**.
- Funkcja `__cpuid` zostanie zaktualizowana. `__cpuid`Funkcje `__cpuidex` obsługują teraz kilka nowych funkcji z najnowszych wersji procesorów AMD i Intel. Wewnętrzne `__cpuidex` jest nowe i zbiera więcej informacji od ostatnich procesorów.
- Opcja `/MP` kompilatora skraca całkowity czas kompilacji. Opcja `/MP` może znacznie skrócić całkowity czas kompilowania kilku plików źródłowych, tworząc kilka procesów, które kompilują pliki jednocześnie. Ta opcja jest szczególnie przydatna na komputerach obsługujących hiperwątkowość, wiele procesorów lub wiele rdzeni.
- Opcja `/Wp64` kompilatora i **__w64** słowo kluczowe są przestarzałe. Opcja `/Wp64` kompilatora i **__w64** słowo kluczowe, które wykrywają problemy z przenoszeniem 64-bitowe, są przestarzałe i zostaną usunięte w przyszłej wersji kompilatora. Zamiast tej opcji kompilatora i słowa kluczowego należy użyć msvc, który jest przeznaczony dla platformy 64-bitowej.
- `/Qfast_transcendentals`generuje wbudowany kod dla funkcji transcendentalnych.
- `/Qimprecise_fwaits`usuwa polecenia fwait wewnętrzne, aby wypróbować bloki `/fp:except` podczas korzystania z opcji kompilatora.

### <a name="linker-changes"></a>Zmiany konsolidatora

- Informacje o kontroli konta użytkownika są teraz osadzane w plikach manifestów dla plików wykonywalnych przez konsolidator Visual C++ (link.exe). Ta funkcja jest domyślnie włączona. Aby uzyskać więcej informacji na temat wyłączania tej funkcji `/MANIFESTUAC` lub modyfikowania zachowania domyślnego, zobacz (Osadza informacje funkcji Kontrola konta użytkownika w manifeście).
- Konsolidator ma `/DYNAMICBASE` teraz możliwość włączenia funkcji randomizacji układu przestrzeni adresowej systemu Windows Vista. Ta opcja modyfikuje nagłówek pliku wykonywalnego, aby wskazać, czy aplikacja powinna być losowo rebased w czasie ładowania.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co nowego w języku C++ w programie Visual Studio 2005

W programie Visual C++ 2005 z dodatkiem Service Pack 1 pojawiły się następujące funkcje:

### <a name="intrinsics-for-x86-and-x64"></a>Wewnętrzne wartości dla x86 i x64

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>Wewnętrzne właściwości tylko dla x64

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Słowa kluczowe nowego języka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nowe funkcje kompilatora

Kompilator ma przełomowe zmiany w tej wersji.

- '64-bitowe kompilatory macierzyste i krzyżowe.
- `/analyze`Dodano opcję kompilatora (Enterprise Code Analysis).
- `/bigobj`dodano opcję kompilatora.
- `/clr:pure`, `/clr:safe`i `/clr:oldSyntax` zostały dodane. (Później przestarzałe w programie Visual Studio 2015 i usunięte w programie Visual Studio 2017.)
- Przestarzałe opcje kompilatora: wiele opcji kompilatora zostały przestarzałe w tej wersji; Zobacz **przestarzałe opcje kompilatora,** aby uzyskać więcej informacji.
- Podwójne thunking `/clr` w kodzie jest zmniejszona; Aby uzyskać więcej informacji, zobacz **Double Thunking (C++).**
- `/EH`(Model obsługi wyjątków) lub `/EHs` nie może być już używany do połowu wyjątku, który jest wywoływany z czymś innym niż rzut; używać `/EHa`.
- `/errorReport`(Raport błędy kompilatora wewnętrznego) dodano opcję kompilatora.
- `/favor`(Optymalizacja dla 64) dodano opcję kompilatora.
- `/FA`, `/Fa` dodano opcję kompilatora (Plik aukcji).
- `/FC`(Pełna ścieżka pliku kodu źródłowego w diagnostyce) dodano opcję kompilatora.
- `/fp`(Określ zachowanie zmiennoprzecinkowe) dodano opcję kompilatora.
- `/G`(Optymalizacja pod kątem procesora) Dodano opcję kompilatora opcji.
- `/G`(Optymalizacja pod kątem procesora) Dodano opcję kompilatora opcji.
- `/G3`, `/G4` `/G5`, `/G6` `/G7`, `/GB` , i opcje kompilatora zostały usunięte. Kompilator używa teraz "modelu mieszanego", który próbuje utworzyć najlepszy plik wyjściowy dla wszystkich architektur.
- `/Gf`został usunięty. Zamiast `/GF` tego użyj (Wyeliminuj zduplikowane ciągi).
- `/GL`(Optymalizacja całego programu) `/CLRHEADER`jest teraz zgodna z .
- `/GR`jest teraz domyślnie włączona.
- `/GS`(Kontrola zabezpieczeń bufora) zapewnia teraz ochronę zabezpieczeń dla zagrożonych parametrów wskaźnika. `/GS`jest teraz domyślnie włączona. `/GS`teraz działa również na funkcje `/clr` skompilowane do MSIL z (Kompilacja środowiska uruchomieniowego języka wspólnego).
- `/homeparams`Dodano opcję kompilatora (Kopiuj parametry rejestru do stosu).
- `/hotpatch`Dodano opcję kompilatora (Utwórz obraz hotpatchable).
- Zaktualizowano heurystykę funkcji wbudowanych; więcej informacji można **znaleźć** **w __inline,** **__forceinline** i **inline_depth**
- Dodano wiele nowych funkcji wewnętrznych, a wiele wcześniej nieudokumentowanych wewnętrznego są teraz udokumentowane.
- Domyślnie każde wywołanie nowego, który zakończy się niepowodzeniem, zgłosić wyjątek.
- `/ML`i `/MLd` opcje kompilatora zostały usunięte. Visual C++ nie obsługuje już obsługi biblioteki CRT jednowątkowej, statycznie połączonej.
- Kompilator zaimplementował optymalizację nazwanych wartości zwracanych, `/O2` która jest włączona podczas `/Og` kompilowania z `/Ox` `/O1`, (Minimalizuj rozmiar, Maksymalizuj szybkość), (Optymalizacje globalne) i (Pełna optymalizacja).
- `/Oa`opcja kompilatora została usunięta, ale będzie po cichu ignorowana; użyj `noalias` lub `restrict__declspec` modyfikatorów, aby określić, jak kompilator wykonuje aliasing.
- `/Op`opcja kompilatora została usunięta. Zamiast `/fp` tego użyj (określ zachowanie zmiennoprzecinowe).
- OpenMP jest teraz obsługiwany przez visual C++.
- `/openmp`Dodano opcję kompilatora (Włącz obsługę OpenMP 2.0).
- `/Ow`opcja kompilatora została usunięta, ale będzie po cichu ignorowana. Użyj `noalias` lub `restrict__declspec` modyfikatorów, aby określić, jak kompilator robi aliasing.

### <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

- `/QI0f`został usunięty.
- `/QIfdiv`został usunięty.
- `/QIPF_B`(Errata dla B CPU Stepping) dodano opcję kompilatora.
- `/QIPF_C`(Errata for C CPU Stepping) dodano opcję kompilatora.
- `/QIPF_fr32`(Nie należy używać górnej 96 rejestrów zmiennoprzecinkowych) dodano opcję kompilatora.
- `/QIPF_noPIC`(Generowanie kodu zależnego pozycji) dodano opcję kompilatora.
- `/QIPF_restrict_plabels`(Przyjmij żadnych funkcji utworzonych w czasie wykonywania) dodano opcję kompilatora.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

- `/vd`(Wyłącz przemieszczenia konstrukcyjne) umożliwia teraz użycie dynamic_cast operatora na budowanym obiekcie (/vd2)
- `/YX`opcja kompilatora została usunięta. Zamiast `/Yc` tego użyj (Utwórz wstępnie `/Yu` skompilowany plik nagłówka) lub (Użyj wstępnie skompilowanego pliku nagłówka). Jeśli usuniesz `/YX` z konfiguracji kompilacji i zastąpisz ją niczym, może to spowodować szybsze kompilacje.
- `/Zc:forScope`jest teraz domyślnie włączona.
- `/Zc:wchar_t`jest teraz domyślnie włączona.
- `/Zd`opcja kompilatora została usunięta. Tylko informacje debugowania z numerem wiersza nie są już obsługiwane. Zamiast `/Zi` tego użyj (zobacz **/Z7, /Zi, /ZI (Debug Information Format), aby** uzyskać więcej informacji).
- `/Zg`jest teraz prawidłowa tylko w plikach kodu źródłowego języka C, a nie w plikach kodu źródłowego języka C++.
- `/Zx`Dodano opcję kompilatora (Debug Optimized Itanium Code).

### <a name="new-language-features"></a>Nowe funkcje językowe

- Atrybut jest teraz przestarzały.
- `appdomain__declspec`dodano modyfikator.
- `__clrcall`dodano konwencję wywoływania.
- przestarzały (C++) **declspec** modyfikator teraz pozwala określić ciąg, który będzie wyświetlany w czasie kompilacji, gdy użytkownik próbuje uzyskać dostęp do przestarzałej klasy lub funkcji.
- **dynamic_cast** Operator ma przełomowe zmiany.
- Natywne wyliczenia umożliwiają teraz określenie typu bazowego.
- `jitintrinsicdeclspec`dodano modyfikator.
- `noaliasdeclspec`dodano modyfikator.
- `process__declspec`dodano modyfikator.
- **abstract**, **override**i **sealed** są prawidłowe dla kompilacji natywnych.
- **__restrict** dodano słowo kluczowe.
- `restrictdeclspec`dodano modyfikator.
- **__thiscall** jest teraz słowem kluczowym.
- **__unaligned** słowo kluczowe jest teraz udokumentowane.
- **volatile** (C++) zaktualizował zachowanie w odniesieniu do optymalizacji.

### <a name="new-preprocessor-features"></a>Nowe funkcje preprocesora

- __CLR_VER wstępnie zdefiniowane makro.
- Komentarz (C / C ++) pragma teraz akceptuje `/MANIFESTDEPENDENCY` jako komentarz konsolidatora. Opcja exestr do komentowania jest teraz przestarzała.
- `embedded_idl`(Dyrektywa) `#import` przyjmuje teraz parametr fakultatywny.
- `fenv_access`Pragmy
- `float_control`Pragmy
- `fp_contract`Pragmy
- Zmienne globalne nie zostaną zainicjowane w kolejności, w jakiej są deklarowane, jeśli masz zmienne globalne w sekcjach zarządzanych pragma, niezarządzanych i niezarządzanych. Jest to potencjalna zmiana podziału, jeśli na przykład niezarządzana zmienna globalna jest inicjowana przy obliczu zarządzanych zmiennych globalnych i wymagany jest w pełni skonstruowany obiekt zarządzany.
- Sekcje określone za pomocą init_seg są teraz tylko do odczytu, a nie do odczytu/zapisu, jak w poprzednich wersjach.
- inline_depth domyślnie jest teraz 16. Domyślnie 16 był również w życie w języku Visual C++ .NET 2003.
- _INTEGRAL_MAX_BITS wstępnie zdefiniowane makro, zobacz Wstępnie zdefiniowane makra.
- _M_CEE, _M_CEE_PURE i _M_CEE_SAFE wstępnie zdefiniowane makra dodane, zobacz Wstępnie zdefiniowane makra.
- _M_IX86_FP wstępnie zdefiniowane makro.
- _M_X64 wstępnie zdefiniowane makro.
- `make_public`Pragmy
- `managed`, `unmanaged` aktualizacja składni pragma `push` (teraz ma i) `pop`
- mscorlib.dll jest teraz niejawnie `#using` odwołuje `/clr` się dyrektywy we wszystkich kompilacjach.
- _OPENMP wstępnie zdefiniowane makro.
- optymalizacja pragma została zaktualizowana, a i w nie są już prawidłowymi parametrami.
- no_registry#import atrybut został dodany.
- `region`, `endregion` pragmas dodał
- _VC_NODEFAULTLIB wstępnie zdefiniowane makro.
- Variadic Makra są teraz realizowane.
- `vtordisp`jest przestarzały i zostanie usunięty w przyszłej wersji programu Visual C++.
- Pragma `warning` ma teraz specyfikator tłumienia.

### <a name="new-linker-features"></a>Nowe funkcje konsolidatora

- Moduły (pliki wyjściowe MSIL niezwiązane z zestawem) są teraz dozwolone jako dane wejściowe do konsolidatora.
- `/ALLOWISOLATION`Dodano opcję konsolidatora (Manifest Lookup).
- `/ASSEMBLYRESOURCE`(Osadź zasób zarządzany) został zaktualizowany, aby teraz umożliwić określenie nazwy zasobu w zestawie i określić, że zasób jest prywatny w zestawie.
- `/CLRIMAGETYPE`(Określ typ obrazu CLR) dodano opcję konsolidatora.
- `/CLRSUPPORTLASTERROR`(Zachowaj ostatni kod błędu dla połączeń PInvoke) dodano opcję konsolidatora.
- `/CLRTHREADATTRIBUTE`Dodano opcję konsolidatora (Ustaw atrybut wątku CLR).
- `/CLRUNMANAGEDCODECHECK`(Dodaj SuppressUnmanagedCodeSecurityAttribute) dodano opcję konsolidatora.
- `/ERRORREPORT`(Raport błędy konsolidatora wewnętrznego) dodano opcję konsolidatora.
- `/EXETYPE`opcja konsolidatora została usunięta. Konsolidator nie obsługuje już tworzenia sterowników urządzeń systemu Windows 95 i Windows 98. Użyj odpowiedniego pliku DDK, aby utworzyć te sterowniki urządzeń. Słowo kluczowe EXETYPE nie jest już prawidłowe dla plików definicji modułu.
- `/FUNCTIONPADMIN`Dodano opcję konsolidatora (Utwórz obraz hotpatchable).
- `/LTCG`opcja linker jest teraz obsługiwana na `/clr`modułach skompilowanych z . `/LTCG`została również zaktualizowana w celu obsługi optymalizacji kierowanej profilem.
- `/MANIFEST`Dodano opcję konsolidatora (Utwórz manifest złożenia obok siebie).
- `/MANIFESTDEPENDENCY`(Określ zależności manifestu) dodano opcję konsolidatora.
- `/MANIFESTFILE`Dodano opcję konsolidatora (Name Manifest File).
- `/MAPINFO:LINES`opcja konsolidatora została usunięta.
- `/NXCOMPAT`(Kompatybilny z funkcją zapobiegania wykonywaniu danych) dodano opcję konsolidatora.
- `/PGD`(Określ bazę danych dla optymalizacji sterowanych profilem) dodano opcję konsolidatora.
- `/PROFILE`Dodano opcję konsolidatora (Performance Tools Profiler).
- `/SECTION`(Określ atrybuty sekcji) opcja konsolidatora obsługuje teraz negację atrybutów i nie obsługuje już atrybutów L lub D (związanych z VxD).
- Obsługa formatu Unicode w kompilatorze i konsolidatorze
- `/VERBOSE`(Drukuj komunikaty postępu) opcja konsolidatora teraz akceptuje również ICF i REF.
- `/VXD`opcja konsolidatora została usunięta. Konsolidator nie obsługuje już tworzenia sterowników urządzeń systemu Windows 95 i Windows 98. Użyj odpowiedniego pliku DDK, aby utworzyć te sterowniki urządzeń. Słowo kluczowe VXD nie jest już prawidłowe dla plików definicji modułu.
- `/WS`opcja konsolidatora została usunięta. `/WS`została wykorzystana do modyfikowania obrazów przeznaczonych dla systemu Windows NT 4.0. IMAGECFG.exe -R nazwa pliku może być `/WS`używana zamiast . PLIK IMAGECFG.exe można znaleźć na dysku CD-ROM systemu Windows NT 4.0 w pliku SUPPORT\DEBUG\I386\IMAGECFG. Exe.
- `/WX`(Traktuj ostrzeżenia konsolidatora jako błędy) opcja konsolidatora jest teraz udokumentowana.

### <a name="new-linker-utility-features"></a>Nowe funkcje narzędzia konsolidatora

- `/ALLOWISOLATION`dodano opcję editbin
- Instrukcja pliku definicji modułu OPIS zostanie usunięta. Konsolidator nie obsługuje już tworzenia sterowników urządzeń wirtualnych.
- `/ERRORREPORT`dodano do bscmake.exe, dumpbin.exe, editbin.exe i lib.exe.
- `/LTCG`dodano opcję lib.
- `/NXCOMPAT`dodano opcję editbin.
- `/RANGE`dodano opcję dumpbin.
- `/TLS`dodano opcję dumpbin.
- `/WS`opcja editbin została usunięta. `/WS`została wykorzystana do modyfikowania obrazów przeznaczonych dla systemu Windows NT 4.0. IMAGECFG.exe -R nazwa pliku może być `/WS`używana zamiast . PLIK IMAGECFG.exe można znaleźć na dysku CD-ROM systemu Windows NT 4.0 w pliku SUPPORT\DEBUG\I386\IMAGECFG. Exe.
- Dodano opcję lib /WX[:NO].

### <a name="new-nmake-features"></a>Nowe funkcje NMAKE

- `/ERRORREPORT`został dodany.
- `/G`został dodany.
- Wstępnie zdefiniowane reguły zostały zaktualizowane.
- Makro $(MAKE), które jest udokumentowane w makrach recursion, teraz daje pełną ścieżkę do nmake.exe.

### <a name="new-masm-features"></a>Nowe funkcje MASM

- Wyrażenia MASM są teraz wartościami 64-bitowymi. W poprzednich wersjach wyrażenia MASM były wartościami 32-bitowymi.
- Instrukcja __asm int 3 powoduje teraz, że funkcja ma być skompilowana do natywnego.
- ALIAS (MASM) jest teraz udokumentowany.
- `/ERRORREPORT`dodano opcję ml.exe i ml64.exe.
- . FPO jest teraz udokumentowana.
- H2INC.exe nie będzie dostarczany w programie Visual C++ 2005. Jeśli musisz nadal używać H2INC, użyj pliku H2INC.exe z poprzedniej wersji programu Visual C++.
- operatora IMAGEREL.
- dodano operatora HIGH32.
- dodano operatora LOW32.
- ml64.exe jest wersją MASM dla architektury x64. Składa pliki x64 .asm w pliki obiektów x64. Wbudowany język zestawu nie jest obsługiwany w kompilatorze x64. Dla pliku ml64.exe (x64) dodano następujące dyrektywy MASM:
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME Ponadto dyrektywa PROC została zaktualizowana o składnię tylko dla x64.
- Dodano dyrektywę MMWORD
- `/omf`(OPCJA wiersza polecenia ML.exe) oznacza `/c`teraz . Plik ML.exe nie obsługuje łączenia obiektów formatu OMF.
- Dyrektywa SEGMENT obsługuje teraz dodatkowe atrybuty.
- dodano operatora SECTIONREL.
- Dodano dyrektywę XMMWORD

### <a name="new-crt-features"></a>Nowe funkcje CRT

- Dodano bezpieczne wersje kilku funkcji. Te funkcje lepiej obsługują błędy i wymuszają bardziej rygorystyczne kontrole buforów, aby uniknąć typowych wad zabezpieczeń. Nowe bezpieczne wersje są identyfikowane przez sufiks **_s.**
- Istniejące mniej bezpieczne wersje wielu funkcji zostały przestarzałe. Aby wyłączyć ostrzeżenia o odgraniczeniu, zdefiniuj _CRT_SECURE_NO_WARNINGS.
- Wiele istniejących funkcji teraz sprawdzić poprawność ich parametrów i wywołać nieprawidłowy program obsługi parametrów, gdy nieprawidłowy parametr jest przekazywany.
- Wiele istniejących funkcji `errno` jest teraz ustawionych tam, gdzie wcześniej tego nie było.
- Dodano typedef `errno_t` z liczeną liczecą typu. `errno_t`jest używany za każdym razem, gdy typ `errno`zwrotu funkcji lub parametr dotyczy kodów błędów z . `errno_t`zastępuje `errcode`.
- Funkcje zależne od ustawień regionalnych mają teraz wersje, które przyjmują ustawienia regionalne jako parametr, a nie przy użyciu bieżących ustawień regionalnych. Te nowe funkcje mają **_l** sufiks. Kilka nowych funkcji zostały dodane do pracy z obiektami ustawień regionalnych. Nowe funkcje `_create_locale` `_free_locale`obejmują `_get_current_locale`, i .
- Dodano nowe funkcje do obsługi blokowania i odblokowywania uchwytów plików.
- Rodzina `_spawn` funkcji nie resetuje errno do zera na sukces, jak to miało miejsce w poprzednich wersjach.
- Dostępne są `printf` wersje rodziny funkcji, które umożliwiają określenie kolejności, w jakiej są używane argumenty.
- Unicode jest teraz obsługiwanym formatem tekstowym. Funkcja `_open` obsługuje atrybuty _O_TEXTW, _O_UTF8 i _O_UTF16. Funkcja `fopen` obsługuje metodę "ccs=ENCODING" określającą format Unicode.
- Nowa wersja bibliotek CRT wbudowanych w kod zarządzany (MSIL) jest teraz dostępna `/clr` i jest używana podczas kompilowania z opcją (Kompilacja środowiska wykonawczego języka wspólnego).
- _fileinfo został usunięty.
- Domyślny rozmiar `time_t` dla jest teraz 64 bitów, `time_t` co rozszerza zakres i kilka funkcji czasu do roku 3000.
- CRT obsługuje teraz ustawienie ustawień regionalnych na podstawie wątku. Funkcja `_configthreadlocale` została dodana do obsługi tej funkcji.
- I `_statusfp2` `__control87_2` funkcje zostały dodane, aby umożliwić dostęp do i kontrolę nad zmiennoprzecinkowym słowem sterującym zarówno na procesorze zmiennoprzecinkowym x87, jak i SSE2.
- I `_mkgmtime` `_mkgmtime64` funkcje zostały dodane w celu zapewnienia obsługi czasu konwersji (struct tm) do Greenwich Mean Time (GMT).
- Wprowadzono zmiany `swprintf` i `vswprintf` lepiej dostosować się do normy.
- Nowy plik nagłówka, INTRIN. H, zapewnia prototypy dla niektórych funkcji wewnętrznych.
- Funkcja `fopen` ma teraz atrybut N.
- Funkcja `_open` ma teraz atrybut _O_NOINHERIT.
- Funkcja `atoi` zwraca teraz INT_MAX i `errno` ustawia wartość ERANGE przy przepełnieniu. W poprzednich wersjach zachowanie przepełnienia było niezdefiniowane.
- Rodzina `printf` funkcji obsługuje szesnastkowe wyjście zmiennoprzecinkowe implementowane zgodnie ze standardem ANSI C99 przy użyciu specyfikatorów typu formatu %a i %A.
- Rodzina `printf` obsługuje teraz prefiks "ll" (długi długi) rozmiar.
- Funkcja `_controlfp` została zoptymalizowana pod kątem lepszej wydajności.
- Dodano wersje debugowania niektórych funkcji.
- Dodano `_chgsignl` `_cpysignl` i (długie podwójne wersje).
- Dodano `_locale_t` typ do tabeli typów.
- Dodano `_countof` nowe makro do obliczania liczby elementów w tablicy.
- W każdym temacie funkcji dodano sekcję dotyczącą odpowiedników programu .NET Framework.
- Kilka funkcji ciągu mają teraz możliwość obcinania ciągów, a nie w przypadku awarii, gdy bufory wyjściowe są zbyt małe; patrz **_TRUNCATE**.
- `_set_se_translator`teraz wymaga użycia `/EHa` opcji kompilatora.
- `fpos_t`jest teraz **__int64** `/Za` pod (dla kodu C) i gdy __STDC__ jest ustawiany ręcznie (dla kodu C++). Kiedyś była to **struktura**.
- _CRT_DISABLE_PERFCRIT_LOCKS może poprawić wydajność we/wy programów jednowątkowych.
- Nazwy POSIX zostały przestarzałe na rzecz nazw zgodnych ISO `_getch` C++ (na przykład użyj, a nie `getch`).
- Nowe opcje linków .obj pliki są dostępne dla czystego trybu
- `_recalloc`łączy w `realloc` sobie `calloc`cechy i .

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co nowego w języku C++ w programie Visual Studio 2003

### <a name="compiler"></a>Kompilator

- Informacje na temat uruchamiania rozszerzeń zarządzanych dla aplikacji Języka C++ utworzonej za pomocą kompilatora bieżącej wersji w poprzedniej wersji środowiska wykonawczego.
- Rozszerzenia zarządzane dla często zadawanych pytań w języku C++.
- Dodano instruktaż pokazujący, jak przenieść istniejącą, natywną aplikację do używania rozszerzeń zarządzanych dla języka C++: Instruktaż: Przenoszenie istniejącej natywnej aplikacji C++ do współpracy ze składnikami .NET Framework.
- Teraz można utworzyć pełnomocnika dla metody typu wartości.
- Zgodność kompilatora ze standardem C++ została znacznie zwiększona dla języka Visual C++ .NET 2003.
- `/arch`dodano opcję kompilatora.
- `/Gf`jest przestarzały i zostanie usunięty w następnej wersji programu Visual C++.
- `/G7`dodano opcję kompilatora.
- Opcja `/GS` kompilatora została rozszerzona, aby chronić zmienne lokalne przed bezpośrednim przepełnieniem buforu.
- Opcja `/noBool` kompilatora została usunięta. Kompilator umożliwia teraz **bool** pojawiać się tylko jako słowo kluczowe (a nie identyfikator) w pliku kodu źródłowego języka C++.
- Długi typ **długi** jest teraz dostępny jako **typedef** **__int64** Należy pamiętać, że nie ma jeszcze wsparcia przez **długi czas** w CRT.
- Opcja `/Zm` kompilatora określa teraz wstępnie skompilowany limit alokacji pamięci nagłówka.
- _InterlockedCompareExchange wewnętrzne teraz udokumentowane.
- _InterlockedDecrement wewnętrzne teraz udokumentowane.
- _InterlockedExchange wewnętrzne teraz udokumentowane.
- _InterlockedExchangeAdd wewnętrzne teraz udokumentowane.
- _InterlockedIncrement wewnętrzne teraz udokumentowane.
- _ReadWriteBarrier wewnętrzne.

### <a name="attributes"></a>Atrybuty

- `implements`atrybut jest teraz udokumentowany.

### <a name="linker-features"></a>Funkcje konsolidatora

Dodano następujące przełączniki konsolidatora:

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- Delaysign
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Tthe. Dodano dyrektywę `/safeseh` SAFESEH i opcję ml.exe.

## <a name="see-also"></a>Zobacz też

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
