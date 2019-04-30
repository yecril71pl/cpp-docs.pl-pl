---
title: Visual C++ co&#39;s nowego od roku 2003 do 2015
ms.date: 11/04/2016
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: ae21a81869bd68c5a2641dba47b89d7e10b67567
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371925"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ co&#39;s nowego od roku 2003 do 2015

Ta strona zbiera wszystkie "co nowego jest" strony dla wszystkich wersji programu Visual C++ z programu Visual Studio 2015 do 2003. Te informacje są dostarczane dla wygody w przypadku, gdy może okazać się przydatne w przypadku uaktualniania z wcześniejszych wersji programu Visual C++.

> [!NOTE]
> Aby uzyskać informacje o bieżącej wersji programu Visual Studio, zobacz [co nowego w języku Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodności w programie Visual C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co nowego w języku C++ w programie Visual Studio 2015

W programie Visual Studio 2015 i nowszych najnowsze ulepszenia do zgodności kompilatora czasami można zmienić sposób kompilator rozpoznaje istniejącego kodu źródłowego. W takim przypadku mogą wystąpić błędy innym, podczas kompilacji lub różnice w zachowaniu nawet w kodzie, który wcześniej utworzone i sprawiał by działała poprawnie.

Na szczęście tych różnic mają niewielkiego lub żadnego wpływu na większość kodu źródłowego i gdy kodu źródłowego lub inne zmiany są potrzebne, aby rozwiązać te różnice, poprawki są zwykle małe i proste. Uwzględniliśmy wiele przykładów kodu źródłowego wcześniej dopuszczalne, który może być konieczne, można zmienić *(przed)* i poprawki, aby je rozwiązać *(po)*.

Mimo że te różnice mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają na zgodność binarną między aktualizacjami do wersji Visual C++. Inne poważne rodzaju zmiany, *zmiana powodująca niezgodność* mogą wpływać na zgodność binarną, ale miejsce tylko tego rodzaju podziały zgodność binarną między wersje główne środowiska Visual C++. Na przykład między Visual C++ 2013 i Visual C++ 2015. Aby uzyskać informacje na temat przełomowych zmian, między programem Visual C++ 2013 i Visual C++ 2015, zobacz [Visual C++ — Historia latach 2003 – 2015 zmian](../porting/visual-cpp-change-history-2003-2015.md).

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 1](#VS_Update1)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 2](#VS_Update2)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a> Ulepszenia zgodności w programie Visual Studio 2015

- **Opcja /Zc:forScope-**

   Opcja kompilatora `/Zc:forScope-` jest przestarzały i zostanie usunięta w przyszłej wersji.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Aby umożliwić kod niestandardowy, który używa pętli zmiennych po punkcie, w którym, zgodnie ze standardem, ich powinien zniknie z zakresu zwykle użyto opcji. Konieczne było tylko wtedy, gdy kompilujesz przy użyciu `/Za` opcji, ponieważ bez `/Za`przy użyciu zmiennej pętli po końcu pętli jest zawsze dozwolona. Jeśli nie dba o zgodność ze standardami (na przykład, jeśli kod nie jest przeznaczona do przenośne na inne kompilatory), możesz całkowicie wyłączyć `/Za` opcja (lub ustaw **Wyłącz rozszerzenia języka** właściwość **nr** ). Jeśli interesujące Cię pisania kodu przenośnego, zgodnych ze standardami, należy napisać ponownie kodu tak, aby jest zgodny ze standardem, przenosząc deklaracji takich zmiennych do punktu poza pętlę.

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

- **ZG-opcja kompilatora.**

   `/Zg` — Opcja kompilatora (Generuj prototypy funkcji) nie jest już dostępna. Tę opcję kompilatora wcześniej została zakończona.

- Nie można uruchomić testy jednostkowe z C++sposób niezamierzony z wiersza polecenia przy użyciu mstest.exe. Zamiast tego należy użyć vstest.console.exe

- **Mutable — słowo kluczowe.**

   **Mutable** specyfikatora klasy magazynu nie jest już dozwolona w miejscach, w którym, wcześniej skompilowany go bez błędów. Teraz, kompilator wyświetla błąd C2071 (niedozwolona Klasa magazynu). Zgodnie ze standardem specyfikator modyfikowalny mogą być stosowane tylko do nazwy elementów członkowskich danych klasy, nie można zastosować do nazwy zadeklarowane const lub statyczne i nie można zastosować do odwoływać się do elementów członkowskich.

   Na przykład rozważmy następujący kod:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Poprzednie wersje kompilatora Visual C++ są akceptowane z tego, ale kompilator zapewnia obecnie następujący błąd:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Aby naprawić błąd, po prostu usuń zbędną **mutable** — słowo kluczowe.

- **char_16_t i char32_t**

   Nie można korzystać `char16_t` lub `char32_t` jako aliasów w typedef, ponieważ te typy są teraz traktowane jako wbudowane. Było typowe dla użytkowników i autorzy biblioteki, aby zdefiniować `char16_t` i `char32_t` jako aliasy `uint16_t` i `uint32_t`, odpowiednio.

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

   Aby zaktualizować swój kod, należy usunąć **typedef** deklaracje i Zmień nazwę innych identyfikatorów, które kolidują z tych nazw.

- **Parametry szablonu bez typu**

   Pewność, że kod, który obejmuje parametry szablonu bez typu są teraz prawidłowo sprawdzane pod kątem zgodności typów po podaniu jawnych argumentów szablonów. Na przykład poniższy kod kompilowany bez błędów w poprzednich wersjach programu Visual C++.

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

   Bieżący kompilatora prawidłowo zwraca błąd, ponieważ argument szablonu nie pasuje do typu parametru szablonu (parametr jest wskaźnik do składowej const, ale funkcja f jest niestały):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Aby rozwiązać ten błąd w kodzie, należy upewnić się, że typ argumentu szablonu jest zgodny z typem zadeklarowany parametr szablonu.

- **__declspec(align)**

   Kompilator nie będzie akceptował `__declspec(align)` funkcji. To zawsze ignorowane, ale teraz generuje błąd kompilatora.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracją funkcji. Ponieważ miała żadnego efektu, usuwając go nie zmian.

- **Obsługa wyjątków**

   Istnieje kilka zmian do obsługi wyjątków. Po pierwsze obiekty wyjątków muszą być kopiowania lub przenośne. Poniższy kod skompilowany w programie Visual Studio 2013, ale nie można skompilować w programie Visual Studio 2015:

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

   Problem polega na tym, że Konstruktor kopiujący jest prywatny, więc nie można skopiować obiektu, ponieważ miało miejsce w trakcie normalnego przebiegu Obsługa wyjątku. To samo dotyczy, gdy Konstruktor kopiujący jest zadeklarowany **jawne**.

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

   Aby zaktualizować swój kod, upewnij się, Konstruktor kopiujący obiektu wyjątku jest publiczny i nie oznaczone **jawne**.

   Przechwytywanie wyjątku przez wartość wymaga także obiekt wyjątku do kopiowania. Poniższy kod skompilowany w programie Visual Studio 2013, ale nie można skompilować w programie Visual Studio 2015:

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

   Możesz rozwiązać ten problem, zmieniając typ parametru dla **catch** do odwołania.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Literały ciągu, a następnie makra**

   Kompilator obsługuje teraz literały zdefiniowane przez użytkownika. W konsekwencji literałów ciągów następuje makra bez żadnych pośredniczące białe znaki będą interpretowane jako literały definiowane przez użytkownika, które może powodować generowanie błędów lub nieoczekiwane wyniki. Na przykład w poprzednim kompilatory następujący kod został pomyślnie skompilowany:

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

   Kompilator interpretowana to jako ciąg literału "hello" makra jest rozwinięta, "Brak", a następnie, a następnie literałów ciągów dwóch zostały połączone w jedną. W programie Visual Studio 2015 kompilator interpretuje to jako literału zdefiniowanego przez użytkownika, ale ponieważ nie ma żadnych pasujących zdefiniowanych przez użytkownika literału _x zdefiniowane, przekazuje błąd.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Aby rozwiązać ten problem, Dodaj odstęp między literałem ciągu i makra.

- **Literały ciągów sąsiadujących**

   Podobnie do poprzedniego, z powodu powiązanych zmian podczas analizowania ciągu, sąsiadujących literałów ciągu (albo literały ciągów znaków szeroki lub wąski) bez żadnych odstępów zostały interpretowane jako pojedynczy ciąg połączonych w poprzednich wersjach Visaul C++. W programie Visual Studio 2015 możesz teraz dodać odstęp między dwa ciągi. Na przykład można zmienić następujący kod:

   ```cpp
    char * str = "abc""def";
   ```

   Po prostu dodać spację między dwa ciągi.

   ```cpp
    char * str = "abc" "def";
   ```

- **Położenie nowych i delete**

   Zmiana została wprowadzona do **Usuń** operatora, aby zapewnić zgodność z C ++ 14 standardowych. Szczegółowe informacje o zmianie standardów znajduje się w temacie [cofania alokacji o rozmiarze w języku C++](http://isocpp.org/files/papers/n3778.html). Zmiany dodać formularz globalnego **Usuń** operator, który przyjmuje parametr rozmiaru. Istotną zmianę jest to, że jeśli wcześniej używano operator **Usuń** z tym samym podpisie (z **umieszczania nowych** operator), otrzymasz błąd kompilatora (C2956, który ma miejsce w punkcie gdzie **umieszczania nowych** jest używany, ponieważ jest pozycja w kodzie, gdzie kompilator próbuje zidentyfikować odpowiednie dopasowania **Usuń** operator).

   Funkcja `void operator delete(void *, size_t)` został **delete umieszczania** operator odpowiadający **umieszczania nowych** funkcji `void * operator new(size_t, size_t)` w C ++ 11. Za pomocą języka C ++ 14 wielkości dezalokacji, to **Usuń** funkcja jest obecnie *funkcji dezalokacji zwykle* (globalne **Usuń** operator). Standardowe wymaga tego przypadku użycia **umieszczania nowych** wyszukuje odpowiednie **Usuń** funkcji i znajduje funkcję zwykle dezalokacji program jest nieprawidłowo sformułowany.

   Załóżmy, że Twój kod określa zarówno **umieszczania nowych** i **delete umieszczania**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   Występuje problem ze względu na dopasowanie w sygnaturach funkcji między **delete umieszczania** operator zdefiniowany przez użytkownika i nowe globalne, wielkości **Usuń** operatora. Należy wziąć pod uwagę, czy możesz używać innego typu innego niż `size_t` dla każdego **umieszczania nowych** i **Usuń** operatorów.  Należy pamiętać, że typ `size_t` **— typedef** jest zależna od kompilatora; jest **typedef** dla **unsigned int** w programie Visual C++. Dobrym rozwiązaniem jest używać typu wyliczeniowego, takie jak to:

   ```cpp
    enum class my_type : size_t {};
   ```

   Następnie Zmień swoją definicję umieszczania **nowe** i **Usuń** można użyć tego typu jako drugi argument zamiast `size_t`. Należy również zaktualizować wywołania **umieszczania nowych** do przekazania nowego typu (na przykład za pomocą `static_cast<my_type>` Aby przekonwertować wartość całkowitą) i aktualizowanie definicji **nowe** i  **Usuń** można rzutować typu Liczba całkowita. Nie trzeba używać **wyliczenia** tego; klasa to typ `size_t` Członkowskich również będzie działać.

   Alternatywnym rozwiązaniem jest, że można wyeliminować **umieszczania nowych** całkowicie. Jeśli kod używa **umieszczania nowych** do zaimplementowania puli pamięci, której argument umieszczania jest rozmiar jest obiekt przydzielony lub został usunięty, a następnie funkcja dezalokacji wielkości może być zastąpienie własnego kodu puli pamięci niestandardowe i można pozbyć się funkcji umieszczania i po prostu Użyj własnych dwuargumentową **Usuń** operator zamiast funkcji umieszczania.

   Jeśli nie chcesz natychmiast zaktualizować kod, możesz przywrócić starsze zachowanie za pomocą opcji kompilatora `/Zc:sizedDealloc-`. W przypadku użycia tej opcji dwuargumentową **Usuń** funkcji nie istnieje i nie będzie powodować konfliktu z Twojej **delete umieszczania** operatora.

- **Elementy członkowskie danych Unii**

   Składowe danych Unii może już typy odwołań. Następujący kod został pomyślnie skompilowany w programie Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

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

   Powyższy kod generuje następujące błędy:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Aby rozwiązać ten problem, zmień typy odwołań do wskaźnika lub wartość. Zmiana typu do wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola Unii. Zmiana kodu do wartości zmieniłby danych przechowywanych w Unii, który ma wpływ na inne pola, ponieważ pola w typy Unii udostępnianie tej samej pamięci. W zależności od rozmiaru wartość może on również zmienić rozmiar Unii.

- **Związki anonimowe**

   są teraz więcej zgodność ze standardem. Poprzednie wersje kompilatora generowane jawny Konstruktor i destruktor związki anonimowe. Zostaną one usunięte w programie Visual Studio 2015.

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

   Powyższy kod generuje następujący błąd w programie Visual Studio 2015:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Aby rozwiązać ten problem, podaj własne definicje Konstruktor i/lub destruktor.

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

- **Unie przy użyciu struktury anonimowe**

   Aby można było zgodne ze standardem, zachowanie środowiska uruchomieniowego zmienił się dla elementów członkowskich struktury anonimowe w Unii. Konstruktora dla elementów członkowskich struktury anonimowe Unii są nie już wywoływany niejawnie po utworzeniu takiej Unii. Ponadto destruktor dla elementów członkowskich struktury anonimowe Unii nie jest już niejawnie jest wywoływana, gdy Unii wykracza poza zakres. Należy wziąć pod uwagę następujący kod, w której Unii U zawiera anonimowa struktura zawierający element, który jest nazwany struktury S, który ma destruktor.

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

   W programie Visual Studio 2013 Konstruktor S jest wywoływana, gdy jest tworzony Unii i destruktor dla S jest wywoływana, gdy stos funkcji f jest czyszczony. Jednak w programie Visual Studio 2015, Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie dotyczące tej zmiany zachowania.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Aby przywrócić oryginalne zachowanie, nazwij anonimowa Struktura. Zachowanie środowiska uruchomieniowego struktury anonimowe są takie same, niezależnie od wersji kompilatora.

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

   Alternatywnie spróbuj przenieść kod Konstruktor i destruktor do nowych funkcji, a następnie dodaj wywołania tych funkcji z Konstruktor i destruktor dla Unii.

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

- **Rozdzielczość szablon**

   Wprowadzono zmiany do rozpoznawania nazw dla szablonów. W języku C++, rozważając kandydatami do rozpoznawania nazw można go tak, że jedną lub więcej nazw pod uwagę jako potencjalny dopasowania tworzy wystąpienia szablonu jest nieprawidłowa. Zazwyczaj te nieprawidłowe wystąpień nie powodują błędy kompilatora, zasady, który jest znany jako SFINAE (podstawienie jest nie błąd).

   Teraz Jeśli SFINAE wymaga kompilatora do utworzenia wystąpienia specjalizacji szablonu klasy, wszelkie błędy, które występują w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator będzie ignorować takie błędy. Na przykład rozważmy następujący kod:

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

   Jeśli kompilujesz z opcją kompilatora bieżącej, zostanie wyświetlony następujący błąd:

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

   Jest to spowodowane punkcie pierwsze wywołanie is_base_of — klasa będzie "nie został jeszcze zdefiniowany.

   W tym przypadku poprawki jest nie należy używać tych cech typu, dopóki nie została zdefiniowana klasa. Jeśli przeniesiesz definicje B i D na początku pliku kodu błąd został rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność instrukcje dołączania dla pliki nagłówkowe upewnić się, że wszystkie definicje klas są kompilowane przed szablony problematyczny są używane.

- **Kopiowanie konstruktorów**

   W programie Visual Studio 2013 i Visual Studio 2015 kompilator generuje konstruktora kopiującego dla klasy, jeśli klasa ma Konstruktor przenoszący zdefiniowanych przez użytkownika, ale bez konstruktora kopiującego zdefiniowanego przez użytkownika. W Dev14 to Konstruktor kopiujący niejawnie wygenerowanego jest również oznaczone jako "= delete".

### <a name="VS_Update1"></a> Ulepszenia zgodności w programie Visual Studio 2015 Update 1

- **Prywatne wirtualne klasy podstawowe i pośredniego dziedziczenia**

   Poprzednie wersje kompilatora mogą wywołać funkcji składowej klasy pochodnej jego *pośrednio pochodzi* `private virtual` klas bazowych. To zachowanie starej była nieprawidłowa i nie jest zgodny ze standardem C++. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2280 w wyniku.

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

  \-lub —

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Przeciążony operator nowy i delete — operator**

   Poprzednie wersje kompilatora mogą nieczłonkowskie **nowy operator** i nieczłonkowską **operatora delete** zostać zadeklarowany jako statyczny i być deklarowane w przestrzeni nazw, innym niż globalnej przestrzeni nazw.  To zachowanie starej utworzone ryzyko, że program nie może wywołać **nowe** lub **Usuń** implementacja operatora, zamierzony potwierdzeniu programisty, wynikające zachowanie dyskretnej nieprawidłowe środowisko uruchomieniowe. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2323 zamiast tego.

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

   Ponadto mimo że kompilator nie zapewnia określonych diagnostyczne, nowy operator wbudowane są uznawane za źle sformułowane.

- **Wywołanie "operator *typu*()" (konwersja zdefiniowana przez użytkownika) na typach klasy korporacyjnej** poprzednie wersje kompilatora mogą "operator *typu*()" do wywoływania na typach klasy korporacyjnej, natomiast w trybie dyskretnym zostaną zignorowane. To zachowanie starej utworzony ryzyko wygenerowanie dyskretnej złego kodu, co środowisko uruchomieniowe nieprzewidywalne zachowanie. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2228 zamiast tego.

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

- **Nadmiarowe typename w specyfikatory typów uszczegółowionych** poprzednie wersje kompilatora mogą **typename** w specyfikatory typów uszczegółowionych; kodu napisanego w ten sposób jest semantycznie nieprawidłowe. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C3406 zamiast tego.

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

- **Ustalanie magazynowymi pochodzącymi od listy inicjalizatora typu** poprzednie wersje kompilatora nie obsługują wnioskowanie typu tablic z listy inicjalizatora. Kompilator obsługuje teraz ten formularz wnioskowanie typu i, co w efekcie wywołań szablonów funkcji przy użyciu listy inicjatorów teraz może być niejednoznaczna lub innego przeciążenia mogą zostać wybrane niż w poprzedniej wersji kompilatora. Aby uniknąć tych problemów, program teraz należy jawnie określić przeciążenia, które są przeznaczone na potwierdzeniu programisty.

   To nowe zachowanie powoduje, że funkcja rozpoznawania przeciążeń do rozważenia dodatkowych Release candidate, który jest równie dobrze jako kandydata historycznych, wywołanie staje się niejednoznaczny i dlatego kompilator generuje błąd kompilatora C2668.

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

   Gdy to nowe zachowanie powoduje, że funkcja rozpoznawania przeciążeń do rozważenia dodatkowych Release candidate, który jest lepsze dopasowane niż historyczne Release candidate, wywołanie jest rozpoznawana jako jednoznacznie nowego kandydata powoduje zmianę zachowania programu jest prawdopodobnie inna niż programista przeznaczone.

   Przykład 2: zmiany w przeciążeniu rozdzielczości (przed)

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

   Przykład 2: zmiany w przeciążeniu rozdzielczości (po)

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

- **Przywracanie ostrzeżenia instrukcji switch**

   Poprzednia wersję kompilatora usunięte uprzednio istniejące ostrzeżenia dotyczące **Przełącz** instrukcji; te ostrzeżenia zostały przywrócone. Kompilator generuje teraz przywróconej ostrzeżenia, a związane z określonych przypadków (w tym przypadku domyślnym) są teraz wyświetlane ostrzeżenia w wierszu zawierającym naruszającym przypadek, a nie w ostatnim wierszu instrukcji switch. W rezultacie teraz wystawiających tych ostrzeżeń w różnych wierszach niż w przeszłości, ostrzeżeń wcześniej pominięty przy użyciu `#pragma warning(disable:####)` nie będzie można pominąć zgodnie z oczekiwaniami. Aby pominąć te ostrzeżenia, zgodnie z oczekiwaniami, może być konieczne przeniesienie `#pragma warning(disable:####)` dyrektywę wiersz powyżej pierwszym przypadku potencjalnie naruszeń. Poniżej przedstawiono przywróconej ostrzeżenia.

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

   Przykłady przywróconej ostrzeżeń, które znajdują się w dokumentacji.

- **#include: użycie specyfikatora katalog nadrzędny "." w pathname** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył użycie specyfikatora katalog nadrzędny "." w nazwie ścieżki `#include` dyrektywy. Kod napisany w ten sposób jest zwykle przeznaczona do obejmują nagłówki, które istnieją poza projektem za pomocą niepoprawnie ścieżek względnych projektu. To zachowanie starej utworzony ryzyka, że program można kompilować przez dołączenie pliku innego źródła, programista przeznaczone lub że tych ścieżek względnych nie jest przenośny do innych środowisk kompilacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia C4464, ostrzeżenia kompilatora, opcjonalnie, jeśli włączona.

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

   Ponadto, mimo że kompilator nie daje określonych diagnostyczne, również zalecamy specyfikator katalog nadrzędny "." Uwaga stosuje się do określenia katalogi dołączane projektu.

- **#pragma optimize() wykracza poza końcem pliku nagłówkowego** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył zmiany w ustawieniach flagi optymalizacji, które ucieczki pliku nagłówka, w ramach jednostki translacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i problemy z kompilatora opcjonalne ostrzeżenie C4426 w lokalizacji naruszeń `#include`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli konflikt zmiany za pomocą flagi optymalizacji ustawione przez argumenty wiersza polecenia kompilatora.

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

- **Niezgodność #pragma warning(push)** i **#pragma warning(pop)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył `#pragma warning(push)` stan zmieni się on sparowany z `#pragma warning(pop)` stanu zmiany w pliku innego źródła, które rzadko są przeznaczone. To zachowanie starej utworzone ryzyko program będzie skompilowany z innym zestawem ostrzeżenia włączone niż programisty planowano, przez co dyskretnej nieprawidłowe działanie. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia C5031 w lokalizacji odpowiedniego ostrzeżenia kompilatora, opcjonalnie `#pragma warning(pop)`, jeśli jest włączona. To ostrzeżenie zawiera uwagi odwołujące się do lokalizacji odpowiadającego `#pragma warning(push)`.

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

   Chociaż rzadko, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest wrażliwa na zmiany w `#include` kolejność; Jeśli jest to możliwe, firma Microsoft zaleca, pliki kodu źródłowego, zarządzanie stan ostrzegawczy w sposób niezależny.

- **Niedopasowane #pragma warning(push)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryto niedopasowane `#pragma warning(push)` stanu zmiany na końcu jednostki translacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i problemy z kompilatora opcjonalne ostrzeżenie C5032 w lokalizacji niedopasowane `#pragma warning(push)`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli nie ma żadnych błędów kompilacji w jednostce translacji.

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

- **Dodatkowe ostrzeżenia może zostać wygenerowany w wyniku śledzenia stanu ostrzeżenia #pragma ulepszone**

   Poprzednie wersje kompilatora śledzone `#pragma warning` zmianie stanu wystarczająco dobrze do wystawiania zamierzony wszystkie ostrzeżenia. To zachowanie utworzony o podwyższonym ryzyku to pewność, że ostrzeżenia będzie efektywnie pomijane w sytuacjach różni się od programisty przeznaczone. Kompilator jest teraz śledzi `#pragma warning` stanu bardziej niezawodnie — szczególnie związane z `#pragma warning` stan zmieni się wewnątrz szablonów — i opcjonalnie wystawia nowe ostrzeżenia C5031 i C5032, które mają na celu pomóc programisty, zlokalizuj niezamierzone zastosowań `#pragma warning(push)` i `#pragma warning(pop)`.

   Na ulepszone `#pragma warning` śledzenia zmian stanu, wcześniej niepoprawnie pominięte ostrzeżenia lub ostrzeżenia dotyczące problemów, które wcześniej misdiagnosed teraz może zostać wygenerowany.

- **Ulepszono proces identyfikacji nieosiągalnego kodu**

   Zmiany standardowej biblioteki języka C++ i ulepszona możliwość wywołania funkcji wbudowanych w porównaniu z poprzednimi wersjami kompilatora może umożliwić kompilatorowi udowodnić, że niektóre kodu jest nieosiągalny. To nowe zachowanie może powodować nowych i innych często wystawione wystąpień ostrzeżenie C4720.

   ```Output
    warning C4720: unreachable code
   ```

   W wielu przypadkach to ostrzeżenie mogą być wystawiane tylko podczas kompilowania z włączonymi optymalizacjami, od optymalizacji mogą wbudowane bardziej wywołaniach funkcji, wyeliminować nadmiarowy kod lub w przeciwnym razie należy można określić, że niektóre kodu jest nieosiągalny. Zauważyliśmy, że nowe wystąpienia ostrzeżenie C4720 często miały miejsce w **bloku try/catch** blokuje, szczególnie w odniesieniu do użytkowania [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

### <a name="VS_Update2"></a> Ulepszenia zgodności w programie Visual Studio 2015 Update 2

- **Dodatkowe ostrzeżenia i błędy, które mogły zostać wydane w wyniku częściowa Obsługa wyrażenie SFINAE**

   Poprzednie wersje kompilatora nie jest przetwarzany niektórych rodzajów wyrażenia wewnątrz **decltype** specyfikatory ze względu na brak obsługi wyrażenie SFINAE. To zachowanie starej była nieprawidłowa i nie jest zgodny ze standardem C++. Kompilator teraz analizuje te wyrażenia i ma częściowa Obsługa wyrażenie SFINAE ze względu na ulepszenia trwającą zgodności. W rezultacie kompilator generuje teraz ostrzeżenia i błędy znalezione w wyrażeniach, że poprzednie wersje kompilatora nie jest przetwarzany.

   Gdy to nowe zachowanie analizuje **decltype** wyrażenia zawierającego typ, który nie został jeszcze zadeklarowany, kompilator generuje błąd kompilatora C2039 w wyniku.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Przykład 1: Użyj typu Niezadeklarowany (przed)

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

   Po przeanalizowaniu to nowe zachowanie **decltype** wyrażenie, które nie ma potrzeby stosowania **typename** słowo kluczowe, aby określić, że zależna nazwa jest typem, kompilator generuje ostrzeżenia C4346 kompilatora wraz z błąd kompilatora C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Przykład 2: zależna nazwa nie jest typem (przed)

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

- `volatile` **zmienne Członkowskie zapobiec niejawnie zdefiniowanych konstruktorów i operatory przypisania** poprzednie wersje kompilatora mogą klasy, która ma **volatile** zmienne Członkowskie mają domyślne kopiowania/przenoszenia konstruktorów i Operatory przypisania kopiowania/przenoszenia domyślne generowane automatycznie. To zachowanie starej była nieprawidłowa i nie jest zgodny ze standardem C++. Kompilator traktuje teraz klasę, która ma zmiennych Członkowskich volatile nietrywialnymi konstrukcji i operatory przypisania co uniemożliwia automatyczne generowanie domyślnej implementacji tych operatorów. Jeśli taka klasa jest elementem członkowskim Unii (lub anonimowej Unii wewnątrz klasy), konstruktorach kopiowania/przenoszenia i operatory przypisania kopiowania/przenoszenia Unii (lub klasy zawierającej Unii unonymous) będzie można niejawnie zdefiniowany jako usunięty. Próbuje utworzyć lub skopiować Unii (lub klasa zawierająca anonimowej Unii) bez jawne określenie ich jest błędne błąd kompilatora problemów kompilatora C2280 w wyniku.

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

- **Statyczne funkcje Członkowskie nie obsługują kwalifikatory cv.**

   Poprzednie wersje programu Visual C++ 2015 dozwolone statyczne funkcje Członkowskie mają kwalifikatory cv. Takie zachowanie wynika z regresji w Visual C++ 2015 i Visual C++ 2015 Update 1; Visual C++ 2013 i wcześniejszych wersjach programu Visual C++ odrzucić kodu napisanego w ten sposób. Zachowanie Visual C++ 2015 i Visual C++ 2015 Update 1 jest nieprawidłowy i nie jest zgodny ze standardem C++.  Visual Studio 2015 Update 2 odrzuca kodu napisanego w ten sposób i generuje błąd kompilatora C2511 zamiast tego.

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

- **Deklaracja wyliczenia jest niedozwolone w kodzie WinRT** (ma wpływ na `/ZW` tylko)

   Kod kompilowany dla środowiska uruchomieniowego Windows (WinRT) nie zezwala na **wyliczenia** typów do przodu zgłaszane, podobnie jak podczas kompilowania kodu zarządzanego C++ dla programu .net Framework za pomocą `/clr` przełącznika kompilatora. To zachowanie jest gwarantuje, że rozmiar wyliczenie zawsze jest znany i może być poprawnie przekazywany do systemu typów WinRT. Kompilator odrzuca kodu napisanego w ten sposób i generuje błąd kompilatora C2599 wraz z błąd kompilatora C3197.

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

- **Przeciążony operator składowej nowych i operatora delete nie mogą być deklarowane wbudowane** (poziom 1 (`/W1`) na domyślnie)

   Poprzednie wersje kompilatora nie generuje ostrzeżenia podczas nieczłonkowskie **nowy operator** i **operatora delete** funkcje są zadeklarowane w tekście. Kod napisany w ten sposób jest nieprawidłowo sformułowany (Diagnostyka nie jest wymagane) i może spowodować, że pamięć problemy wynikające z nowych niezgodne i delete — operatory (zwłaszcza gdy jest używany z cofania alokacji o rozmiarze), które mogą być trudne do zdiagnozowania. Kompilator generuje teraz C4595 ułatwiają identyfikację kodu napisanego w ten sposób ostrzeżenia kompilatora.

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

   Naprawianie kodu, który jest zapisywany w ten sposób może wymagać, że definicje operator zostać przeniesiona z pliku nagłówka oraz odpowiadający mu plik źródłowy.

### <a name="VS_Update3"></a> Ulepszenia zgodności w programie Visual Studio 2015 Update 3

- **STD::is_convertable teraz wykrywa przypisanie własne** poprzednie wersje (standardowa biblioteka) `std::is_convertable` cechy typu niepoprawnie wykrywa przypisanie własne typu klasy, gdy jego Konstruktor kopiujący został usunięty lub prywatnej. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie **false** w przypadku zastosowania do typu klasy za pomocą konstruktora kopiującego usunięty lub jest prywatny.

   Nie ma żadnych diagnostyki kompilatora skojarzone z tą zmianą.

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

   W poprzednich wersjach programu Visual C++, statycznej potwierdzenia w dolnej części w tym przykładzie przekazać, ponieważ `std::is_convertable<>::value` została niepoprawnie ustawiona na **true**. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie **false**, powodując statyczne potwierdzenia nie powiedzie się.

- **Przyjmujące wartości domyślne lub usunął kopię prosta i przenieść specyfikatory dostępu względem konstruktorów**

   Poprzednie wersje kompilatora Sprawdź specyfikator dostępu ustawionych domyślnie lub usuniętych trivial kopii i nie konstruktory przenoszenia przed umożliwieniem do wywołania. To zachowanie starej była nieprawidłowa i nie jest zgodny ze standardem C++. W niektórych przypadkach to stare zachowanie utworzony ryzyko wygenerowanie dyskretnej złego kodu, co środowisko uruchomieniowe nieprzewidywalne zachowanie. Kompilator teraz sprawdza specyfikator dostępu ustawionych domyślnie lub usuniętych kopii prosta i przenoszenie konstruktorów w celu ustalenia, czy można wywołać, a jeśli nie, problemy z ostrzeżenia kompilatora, C2248 w wyniku.

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

- **Amortyzacja opartego na atrybutach Obsługa kodu biblioteki ATL** (poziom 1 (`/W1`) na domyślnie)

   Poprzednie wersje kompilatora obsługiwane opartego na atrybutach kodu biblioteki ATL. Jako do następnej fazy Rezygnacja z obsługi ATL z atrybutami kod, który [rozpoczął się w programie Visual C++ 2008](https://msdn.microsoft.com/library/bb384632), opartego na atrybutach kodu biblioteki ATL jest przestarzałe. Kompilator generuje teraz C4467, aby ułatwić zidentyfikowanie tego rodzaju przestarzały kod ostrzeżenia kompilatora.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Jeśli chcesz kontynuować korzystanie z atrybutami kodu biblioteki ATL, do momentu usunięcia z kompilatora pomocy technicznej, możesz wyłączyć to ostrzeżenie, przekazując `/Wv:18` lub `/wd4467` argumenty wiersza polecenia kompilatora lub dodając `#pragma warning(disable:4467)` w kodzie źródłowym.

   Przykład 1 (przed)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Przykład 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Czasami może być konieczne lub do utworzenia pliku IDL plik, aby uniknąć użycia przestarzałe atrybutów ATL, tak jak poniższego przykładowego kodu

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

   Najpierw utwórz plik *.idl; Plik vc140.idl generowane może służyć do uzyskiwania \*pliku .idl, zawierający interfejsów i adnotacji.

   Następnie dodaj krok MIDL do kompilacji w taki sposób, aby upewnić się, że definicje interfejsu C++ są generowane.

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

   Następnie należy użyć biblioteki ATL, bezpośrednio w pliku implementacji, tak jak poniższego przykładowego kodu.

   Przykład 2 wdrożenia (po)

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

- **Prekompilowanych plików nagłówka (PCH) i niezgodny # dyrektywy include** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowane niezgodny `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacje, korzystając z prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowana przez kompilator. Kompilator teraz niezgodny CC4598, aby ułatwić zidentyfikowanie ostrzeżenia kompilatora, problemy z `#include` dyrektywy podczas korzystania z plików PCH.

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

- **Prekompilowanych plików nagłówka (PCH) i niezgodne katalogi dołączania** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowane, niezgodny katalog dołączania (`-I`) argumenty wiersza polecenia dla kompilatora między `-Yc` i `-Yu` kompilacje, korzystając z prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowana przez kompilator.   Katalog dołączania kompilatora teraz CC4599, aby ułatwić zidentyfikowanie ostrzeżenia kompilatora, problemów niezgodność (`-I`) argumenty wiersza polecenia podczas korzystania z plików PCH.

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

### <a name="improved-iso-cc-standards-support"></a>Obsługa standardów C/C++ ulepszone ISO

#### <a name="compiler"></a>Kompilator

Kompilator Microsoft Visual C++ obsługuje te funkcje ISO C ++ 11 język:

- Domyślne argumenty szablonu dla szablonów funkcji.
- Konstrukty delegujące
- Jawne operatory konwersji.
- Listy inicjatorów i jednolite inicjowanie.
- Surowe Literały ciągu.
- Szablony Wariadyczne.
- Szablony aliasów.
- Funkcje usunięte.
- Dane niestatycznych inicjatorów składowych (NSDMIs).
- Funkcje domyślne. \*
- Obsługuje te funkcje językowe ISO C99:
- _Bool
- Złożone literały.
- Inicjatory wyznaczone.
- Mieszanie deklaracji z kodem.
- Ciąg może być niedozwolona konwersja literału do modyfikowalnych wartości przy użyciu nowej opcji kompilatora `/Zc:strictStrings`. W języku C++ 98 konwersja z literałów ciągów do `char*` (i szerokich literałów ciągów do `wchar_t*`) została zakończona. W języku C++ 11 Konwersja została usunięta całkowicie. Mimo że kompilator może ściśle przestrzegać standardu, zamiast tego zapewnia `/Zc:strictStrings` opcji, dzięki czemu można kontrolować konwersję. Domyślnie opcja jest wyłączona. Należy pamiętać, że gdy używasz tej opcji w trybie debugowania, STL nie zostanie skompilowany.
- Rzuty referencji rvalue/lvalue. Dzięki odwołaniom rvalue C ++ 11 może jasno rozróżnić między lvalues i rvalues. Wcześniej kompilator nie zapewniał tego w określonych scenariuszach rzutowania. Nową opcję kompilatora, `/Zc:rvalueCast`, została dodana do zgodności kompilatora z C++ Paper(see section 5.4, [expr.cast]/1) pracy języka. Domyślne zachowanie, gdy ta opcja nie jest określona, jest taka sama, jak w programie Visual Studio 2012.

> [!NOTE]
> Dla funkcji domyślnych, używających = default, aby zażądać konstruktorów przeniesienia memberwise i przenieść, operatory przypisania nie jest obsługiwana.

### <a name="c99-libraries"></a>Biblioteki C99

Deklaracje i implementacje są dodawane do brakujących funkcji w tych nagłówkach: math.h, ctype.h, wctype.h, stdio.h, stdlib.h i wchar.h. Dodawane są również nowe complex.h nagłówków, w nich zadeklarowane stdbool.h fenv.h i inttypes.h i implementacje dla wszystkich funkcji. Istnieje nowe nagłówki otoki C++ (ccomplex cfenv, cinttypes, ctgmath) i wiele innych są zaktualizowane (ccomplex cctype —, clocale —, cmath, cstdint, cstdio —, cstring, cwchar — i cwctype —).

### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

Obsługa języka C ++ 11 jawne operatory konwersji, list inicjatorów, Typy wyliczeniowe i szablony wariadyczne.
Wszystkie kontenery obsługuje teraz C ++ 11 element szczegółowych wymagań.
Obsługa tych funkcji C ++ 14:

- "Przezroczyste funktory operatora" mniej <>, większa <>, a także <>, mnoży <> i tak dalej.
- make_unique<T>(argumenty...) i make_unique < T [] > (n)
- Funkcje nieczłonkowskie cbegin()/cend(), rbegin()/rend() i crbegin()/crend().
- \<niepodzielne > otrzymał wiele udoskonaleń zwiększających wydajność.
- \<type_traits > otrzymał główną stabilizację i Kod poprawki.

### <a name="breaking-changes"></a>Fundamentalne zmiany

Tym Ulepszona obsługa standardów ISO C/C++ może wymagać zmian w istniejącym kodzie, który jest zgodny z C ++ 11 i skompilowany poprawnie w programie Visual C++ w programie Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Zwiększenia biblioteki Visual C++

- C++ REST SDK zostanie dodany. Posiada nowoczesną implementację C++ usług REST.
- Został rozszerzony o obsługę tekstury języka C++ AMP. Obejmuje teraz obsługę mipmap i nowe tryby pobierania próbek.
- Zadania PPL obsługuje wiele technologii planowania i debugowania asynchronicznego. Nowe interfejsy API umożliwiają tworzenie zadań PPL dla wyników normalnych i wyjątkowych warunków.

### <a name="c-application-performance"></a>Wydajność aplikacji C++

- Auto-Vectorizer teraz rozpoznaje i optymalizuje więcej wzorców C++, aby sprawić, że kod działają szybciej.
- Platforma ARM i mikro architektura Micro Atom poprawki jakości kodu.
- __vectorcall Konwencja wywoływania zostanie dodany. Przekaż argumenty typu wektorowego przy użyciu __vectorcall Konwencja wywoływania, aby skorzystać z rejestrów wektorowych.
- Nowe opcje konsolidatora. `/Gw` (Kompilatora) i `/Gy` przełączników (asemblera) umożliwiają optymalizacje konsolidatora w celu utworzenia bardziej efektywnych danych binarnych.
- C++ AMP obsługa pamięci wspólnej do zmniejszenia lub wyeliminowania kopiowania danych między GPU i CPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Profil rozszerzenia profilowana Optymalizacja (PGO)

- Poprawa wydajności wynikająca ze zmniejszenia w zestawie roboczym aplikacji, które są zoptymalizowane przy użyciu PGO.
- Nowe PGO do Windows Runtime tworzenia aplikacji.

### <a name="windows-runtime-app-development-support"></a>Obsługa projektowania aplikacji środowiska wykonawczego Windows

- **Obsługa dla opakowany typów w strukturach wartości.**

   Teraz można zdefiniować typy wartości przy użyciu pól, które może mieć wartości null — na przykład `IBox<int>^` w przeciwieństwie do **int**. Oznacza to, że pola mogą mieć wartość lub być taka sama jak **nullptr**.

- **Bogatsze informacje o wyjątku.**

   C++/CX obsługuje nowy model błędu Windows, który umożliwia przechwytywania i propagację informacje o wyjątku sformatowanym między interfejsem binarnym aplikacji (ABI); obejmuje to stosy wywołań i ciągi komunikatów niestandardowych.

- **Object:: ToString() teraz jest wirtualny.**

   Możesz teraz zastąpić ToString w zdefiniowanych przez użytkownika typach ref środowiska wykonawczego Windows.

- **Obsługa przestarzałych API.**

   Publicznych interfejsów API środowiska uruchomieniowego Windows mogą teraz oznaczone jako przestarzałe i podane jako wiadomość niestandardowa, która pojawia się jako ostrzeżenie kompilacji i może stanowić wskazówkę migracji.

- **Ulepszenia debugera.**

   Obsługa debugowania międzyoperacyjnego native/JavaScript, diagnoza wyjątków środowiska wykonawczego Windows i kod asynchroniczny debugowania (Windows Runtime i PPL).

> [!NOTE]
> Oprócz specyficznych dla języka C++ funkcji i ulepszeń, które są opisane w tej sekcji inne ulepszenia w programie Visual Studio również mogą ułatwić tworzenie lepszych aplikacji środowiska wykonawczego Windows.

### <a name="diagnostics-enhancements"></a>Rozszerzenia diagnostyki

- Ulepszenia debugera. Obsługa debugowania asynchronicznego i debugowania tylko mój kod.
- Kategorie analizy kodu. Możesz teraz wyświetlić skategoryzowane dane wejściowe z analizy kodu, aby pomóc Ci znaleźć i naprawić usterki kodu.
- Diagnostyka XAML. Możesz teraz zdiagnozować wrażliwość interfejsu użytkownika i problem zużycia baterii w swojej XAML.
- Grafika i ulepszenia debugowania GPU.
- Zdalne nagrywanie i odtwarzanie na rzeczywistych urządzeniach.
- Jednoczesne C++ AMP i debugowania CPU.
- Ulepszona diagnostyka środowiska uruchomieniowego C++ AMP.
- HLSL debugowanie śledzenia cieniowania obliczenia.

### <a name="3-d-graphics-enhancements"></a>Udoskonalenia grafiki 3D

- Obraz Obsługa potoku zawartości dla wstępnie przemnożonego kanału alfa DDS.
- Edytor obrazów używa wewnętrznie wstępnie przemnożonego alfa do renderowania i tym samym pozwala uniknąć renderowania artefaktów, takich jak ciemne otoczki.
- Obraz i edytory modelu. Tworzenie filtrów zdefiniowanych przez użytkownika jest teraz obsługiwane w projektancie programu do cieniowania w edytorze obrazu i edytora modelu.

### <a name="ide-and-productivity"></a>IDE i produktywność

**Ulepszone formatowanie kodu**. Można zastosować więcej ustawień formatowania dla swojego kodu C++. Za pomocą tych ustawień, można kontrolować rozmieszczenie w nowych wierszach nawiasów klamrowych i słów kluczowych, wcięć, odstępów i zawijania. Kod jest automatycznie sformatowany po wykonaniu instrukcji i bloków i Wklej kod do pliku.

**Zakończenie nawiasu klamrowego.** Kod języka C++ teraz automatycznie uzupełnia znaki zamknięcia, które odnoszą się do tych znaków otwarcia:

- {(nawias klamrowy)
- [(nawias kwadratowy)
- ((nawiasów)
- ' (apostrof)
- "(cudzysłowami)

**Funkcje dodatkowe C++ Autouzupełnianie.**

- Dodaje średnik dla typu klasy.
- Kończy nawiasami okrągłymi dla surowych literałów ciągów.
- Kończy Komentarze wielowierszowe (/\* \*/)

**Znajdź wszystkie odwołania** teraz automatycznie rozpoznaje i filtruje odniesienia w tle po wyświetleniu listy trafień tekstowych.

**Członek oparty na kontekście filtrowanie listy.** Członkowie niedostępni są odfiltrowani z listy elementów członkowskich IntelliSense. Na przykład prywatne składowe nie są wyświetlane na liście elementów członkowskich, chyba że zmodyfikujesz kod, który implementuje ten typ. Gdy listę elementów członkowskich jest otwarta, możesz nacisnąć przycisk **Ctrl**+**"j"** usunąć jeden poziom filtrowania (dotyczy tylko bieżącego elementu członkowskiego okna listy). Możesz nacisnąć przycisk **Ctrl**+**"j"** ponownie, aby usunąć filtrowanie tekstowe i pokazać każdy element członkowski.

**Parametr pomocy przewijania.** Sygnatura funkcji wyświetlana w etykietce narzędzia parametru pomocy teraz zmienia się na podstawie liczby parametrów, które rzeczywiście zostały wpisane, a nie po prostu pokazując dowolną sygnaturę i nie aktualizując jej na podstawie bieżącego kontekstu. Parametr pomocy również funkcjonuje poprawnie, kiedy jest wyświetlany na funkcjach zagnieżdżonych.

**Przełącz nagłówek/plik kodu.** Możesz przełączać między nagłówkiem i jego odpowiadającym mu plikiem kodu przy użyciu polecenia na menu skrótu lub skrótu klawiszowego.

**Okno właściwości projektu C++ o zmiennym rozmiarze**

**Autogenerowanie kod obsługi zdarzeń w C++/CX i C++sposób niezamierzony.**  Kiedy wpisujesz kod, aby dodać program obsługi zdarzeń w C++/CX lub C++pliku kodu w sposób niezamierzony, edytor może automatycznie generować definicji delegata wystąpienie i program obsługi zdarzeń. Zostanie wyświetlone okno etykietki narzędzia, gdy kod obsługi zdarzenia mogą być generowane automatycznie.

**Wzmocnienie świadomości DPI.** Ustawienie DPI Awareness dla plików manifestu aplikacji teraz obsługuje ustawienie "Na Monitor High DPI Aware".

**Szybsze przełączanie konfiguracji.** W przypadku dużych aplikacji, przełączanie konfiguracji — zwłaszcza przełączenia kolejnych operacji — działa znacznie szybciej.

**Efektywność czasu kompilacji.** Liczne optymalizacje i wykorzystanie procesorów wielordzeniowych przyspiesza kompilację, szczególnie w przypadku dużych projektów. Kompilacje przyrostowe aplikacji C++, które mają odwołania do C++ WinMD są również znacznie szybsze.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co nowego w języku C++ w programie Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Ulepszone C ++ 11 standardów pomocy technicznej

#### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

- Obsługa nowe nagłówki STL: \<atomic >, \<chrono >, \<condition_variable >, \<filesystem >, \<przyszłych >, \<mutex >, \<współczynnik >, i \< Wątek >.
- W celu zoptymalizowania użycia zasobów pamięci, kontenery są mniejsze. Na przykład w x86 tryb wydania przy użyciu ustawień domyślnych `std::vector` został zmniejszony z 16 bajtów w programie Visual Studio 2010 do 12 bajtów w programie Visual Studio 2012 i `std::map` został zmniejszony z 16 bajtów w programie Visual Studio 2010 lub 8 bajtów w programie Visual Studio 2012.
- Dozwolone, ale nie jest wymagane przez Standard C ++ 11 Iteratory SCARY zostały wdrożone.

#### <a name="other-c11-enhancements"></a>Inne C ++ 11 rozszerzenia

- Oparta na zakresie pętli for. Można napisać bardziej niezawodnych pętli, które działają z tablicami, kontenerami STL i środowiska uruchomieniowego Windows kolekcje w formularzu dla (dla zakresu — deklaracja: wyrażenie). Jest to część obsługi rdzenia języka.
- Bezstanowe lambdy, które znajdują się bloki kodu, które zaczynają się od [] introducer pusty lambda i przechwytywania nie zmiennych lokalnych, teraz są niejawnie konwertowane na wskaźniki funkcji wymagane przez Standard C ++ 11.
- Obsługa wyliczeń objętych zakresem. C++ wyliczenia enum klucz klasy jest teraz obsługiwane. Poniższy kod demonstruje, jak ten klucz wyliczenia różni się od poprzedniego zachowania wyliczenia.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Obsługa projektowania aplikacji środowiska wykonawczego Windows

- **Natywny model interfejsu użytkownika opartego na XAML**. W przypadku aplikacji środowiska wykonawczego Windows można użyć nowego modelu natywnego interfejsu użytkownika opartego na XAML.
- **Visual C++ Component Extensions**. Te rozszerzenia upraszczają zużycia obiektów środowiska wykonawczego Windows, które są niezbędne część aplikacji środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [plan for Windows Runtime używających C++ ](../windows/universal-windows-apps-cpp.md) i [Visual C++ Skorowidz języka (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Gry DirectX**. Możesz tworzyć atrakcyjne gry przy użyciu nowej funkcji obsługi DirectX dla aplikacji środowiska wykonawczego Windows.
- **Współdziałanie XAML/DirectX**. Środowisko uruchomieniowe Windows aplikacje korzystające z technologii DirectX i XAML teraz współdziałać wydajnie.
- **Tworzenie biblioteki DLL składnika środowiska wykonawczego Windows**. Tworzenie biblioteki DLL składnika sprawia, że środowisko wykonawcze Windows extensible.

### <a name="compiler-and-linker"></a>Kompilatora i konsolidatora

- **Auto-vectorizer**. Kompilator analizuje pętli w kodzie i, w przypadku, gdy to możliwe, emituje rejestruje instrukcje, które używają wektora i instrukcje, które są obecne w nowoczesnych wszystkie procesory w systemie. Dzięki temu pętli działają szybciej. (Instrukcje procesora są nazywane SSE, aby uzyskać Streaming SIMD Extensions). Nie masz do włączania lub zażądać tego rodzaju optymalizacji, ponieważ nie jest stosowana automatycznie.
- **Automatycznego zrównoleglacza**. Kompilator można analizować pętli w kodzie i emitowanie instrukcji, które rozkładają się obliczenia na wiele rdzeni lub procesorów. Dzięki temu może być pętli działają szybciej. Należy zażądać tego rodzaju optymalizacji, ponieważ nie jest włączona domyślnie. W wielu przypadkach warto uwzględnić `#pragma loop(hint_parallel(N))` w kodzie, bezpośrednio przed pętli, które mają być równoległego.
- Automatycznego zrównoleglacza i automatycznego wektoryzera programu można współpracują ze sobą, dzięki czemu obliczenia są dystrybuowane na wiele rdzeni i kod na każdy rdzeń używa jej rejestrów wektorowych.

### <a name="new-in-visual-studio-2012-update-1"></a>Nowość w programie Visual Studio 2012 Update 1

Celem Windows XP, podczas kompilowania kodu C++.
Można użyć kompilatora języka Visual C++ i bibliotek target Windows XP i Windows Server 2003.

#### <a name="parallel-programming-support"></a>Równoległe programowanie pomocy technicznej.

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP przyspiesza wykonywanie kodu C++ wykorzystując sprzęt zrównoleglający dane, które zwykle występujący jako GPU na karcie graficznej. Model programowania C++ AMP zawiera tablice wielowymiarowe, indeksowanie, transfer pamięci, fragmentacji i bibliotekę funkcji matematycznych. Za pomocą rozszerzeń języka C++ AMP i ograniczenia dotyczące kompilatora, można kontrolować, jak dane są przenoszone z procesora CPU do procesora GPU i z powrotem.

**Debugowanie.** Debugowanie aplikacji, które używają języka C++ AMP pod kątem procesora GPU jest podobne do debugowania w innych aplikacjach C++. Dotyczy to również nowy równoległych, debugowanie dodatki, które zostały wymienione wcześniej.

**Profilowanie.** Obecnie trwa profilowanie obsługę aktywność procesora GPU, oparty na C++ AMP i innych modeli programowania oparty na Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Ulepszenia programowania równoległego ogólne

Na sprzęcie, przejście do architektury wielordzeniowych oraz wielordzeniowe deweloperów już polegać na coraz większej szybkości zegara od pojedynczego rdzenia. Programowanie pomocy technicznej w środowisku uruchomieniowym współbieżności: równoległe umożliwia deweloperom korzystanie z zalet tych nowych architektur.
W programie Visual Studio 2010 zaawansowanych bibliotek języka C++ przetwarzania równoległego, takich jak biblioteka równoległych wzorców zostały wprowadzone, wraz z funkcjami, aby móc korzystać z współbieżności przez wyrażenie potoki przepływu danych zaawansowane. W programie Visual Studio 2012 rozszerzono zapewniające lepszą wydajność, więcej kontroli i więcej obsługę równoległych wzorców, że deweloperzy muszą większość tych bibliotek. Szerokie oferty zawiera teraz:

- Rozbudowane opartego na zadaniach model programowania obsługującego asynchroniczności i kontynuacji.
- Równoległe algorytmy, które obsługują równoległości przyłączaniem do rozwidlenia (parallel_for, parallel_for koligacji, parallel_for_each, parallel_sort —, parallel_reduce, funkcja parallel_transform).
- Bezpieczne pod względem współbieżności kontenery, które zapewniają wątkowo wersje standardowe struktur danych, takich jak priority_queue —, kolejki, wektora i mapy.
- Bibliotekę asynchronicznych agentów, które deweloperzy mogą używać programu express potoki przepływu danych, które naturalnie rozkładania na równoczesne jednostki.
- Można dostosować harmonogram Menedżera zasobów i ułatwiają bezproblemowe kompozycji wzorców na tej liście.

##### <a name="general-parallel-debugging-enhancements"></a>Ulepszenia debugowania równoległych ogólne

Oprócz **zadań równoległych** okna i **stosów równoległych** okna programu Visual Studio 2012 oferuje nową **równoległego wyrażenia kontrolnego** okna tak, aby sprawdzić wartości wyrażenie we wszystkich wątków procesów i wykonać sortowanie i filtrowanie na wynik. Umożliwia także własne wizualizatorów można rozszerzyć okna i korzystać z zalet nowej funkcji obsługi wielu procesów, we wszystkich okien narzędzi.

### <a name="ide"></a>IDE

**Szablony programu Visual Studio obsługuje.** Można teraz używać technologii szablony programu Visual Studio do tworzenie C++ szablonów projektów i elementów.

**Ładowanie rozwiązań asynchronicznych.** Projekty są teraz ładowane asynchronicznie — kluczowe elementy rozwiązania pierwszy — tak, aby uruchomić działa szybciej.

**Zautomatyzowane wdrażanie na potrzeby debugowania zdalnego.** Wdrażanie plików dla zdalnego debugowania w programie Visual C++ zostały uproszczone. **Wdróż** opcję z menu kontekstowego projektu automatycznie kopiuje komputer zdalny, pliki, które są określone we właściwościach konfiguracji debugowania. Ręczne kopiowanie plików na komputerze zdalnym nie jest już wymagane.

**C++/CLI IntelliSense.** C++/ Interfejs wiersza polecenia ma teraz pełną obsługę technologii IntelliSense. Funkcja IntelliSense funkcje takie jak szybka podpowiedź, parametr pomocy, listę elementów członkowskich i automatyczne uzupełnianie teraz działa dla C++sposób niezamierzony. Oprócz innych technologii IntelliSense i środowisko IDE rozszerzenia wymienione w niniejszym dokumencie są również działać dla C++sposób niezamierzony.

**Richer IntelliSense Tooltips.** Informacje dotyczące stylu etykietki szybka podpowiedź funkcji IntelliSense języka C++ teraz zawierać bogatsze komentarze dokumentacji XML. Jeśli używasz interfejsu API z poziomu biblioteki — na przykład, C++ AMP — ma komentarze dokumentacji XML, a następnie etykietka funkcji IntelliSense zawiera więcej informacji, niż tylko deklaracji. Ponadto jeśli kod ma komentarze dokumentacji XML, etykietki narzędzi IntelliSense pokaże bogatsze informacje.

**Konstrukcje kodu w języku C++.** Szkielet kodu jest dostępna dla przełącznika if-else, pętli i innych konstrukcji kodu podstawowego, na liście rozwijanej listę elementów członkowskich. Wybierz fragment kodu z listy, aby wstawić je do kodu, a następnie wprowadź wymagane logiki. Można również utworzyć własne niestandardowe fragmenty kodu do użycia w edytorze.

**Lista elementów członkowskich rozszerzeń.** **List Members** listy rozwijanej pojawia się automatycznie podczas pisania kodu w edytorze kodu. Wyniki są filtrowane tak, aby tylko odpowiednie elementy członkowskie są wyświetlane podczas wpisywania. Można kontrolować rodzaj logikę filtrowania, który jest używany przez listę elementów członkowskich — w **opcje** okno dialogowe, w obszarze **edytora tekstów** > **C/C++**  >  **Zaawansowane**.

**Związane z kolorystyką.** Typy, wyliczenia, makr i innymi tokenami C++ powstał kolorowanie domyślnie.

**Wyróżnianie odwołań.** Teraz wybranie symbolu wyróżnia wszystkie wystąpienia znaku w bieżącym pliku. Naciśnij klawisz **Ctrl**+**Shift**+**Strzałka w górę** lub **Ctrl**+**Shift**  + **Strzałkę w dół** Aby poruszać się między do wyróżnionych odwołań. Możesz wyłączyć tę funkcję **opcje** dialogowego **edytora tekstów** > **C/C++** > **zaawansowane**.

### <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

#### <a name="static-code-analysis"></a>Statyczna analiza kodu

Zaktualizowano analizę statyczną dla języka C++ umożliwia bogatszych błąd informacji kontekstowych, więcej reguł analizy, i analizy lepsze wyniki. W nowym oknie analizy kodu możesz filtrować wiadomości według słów kluczowych, projekt i ważności. Po wybraniu komunikat w oknie wiersz w kodzie, w którym wyzwolono wiadomości jest wyróżniony w edytorze kodu. W przypadku niektórych C++ — ostrzeżenia, komunikat wyświetla listę wierszy źródłowych, przedstawiających ścieżki wykonywania, który prowadzi do ostrzeżenie; punkty decyzyjne i przyczyny biorąc tej konkretnej ścieżki są wyróżnione.
Analiza kodu znajduje się w większości wersji programu Visual Studio 2012. W Professional, Premium i Ultimate Edition zawarte są wszystkie reguły. W wersji Express for Windows 8 i Windows Phone po prostu najważniejszych ostrzeżenia są uwzględniane. Analiza kodu jest niedostępna w wersji Express for Web.
Poniżej przedstawiono niektóre inne rozszerzenia analizy kodu:

- Nowe ostrzeżenia współbieżności pomóc uniknąć błędów współbieżności, upewniając się, że używasz prawidłowe zasady blokowania, w przypadku programów wielowątkowych C/C++. Analizator wykrywa potencjalnych sytuacji wyścigu, odwrócenie kolejności blokady, wywołujący/wywoływany blokowania naruszenia Umowy, operacje synchronizacji niedopasowanych i inne usterki współbieżności.
- Można określić, że reguły języka C++, chcesz zastosować do kodu przebiegi analizy przy użyciu zestawów reguł.
- W **analizy kodu** okna, można wstawić do kodu źródłowego pragmę, której pomija wybranych ostrzeżeń.
- Przy użyciu nowej wersji języka adnotacji kod źródłowy firmy Microsoft (SAL) do opisywania, jak funkcja używa jego parametrów założenia fakt, że o ich i gwarancje, które dział it może zwiększyć dokładność i kompletności statycznej analizy kodu sprawia, że po zakończeniu tej operacji.
- Obsługa 64-bitowy projektów w języku C++.

#### <a name="updated-unit-test-framework"></a>Zaktualizowano testów jednostkowych

Użyj nowej struktury testowej jednostki C++ w programie Visual Studio do pisania testów jednostkowych C++. Dodaj nową jednostkę projekt testu do istniejącego rozwiązania do języka C++, znajdując szablonu projektu testu jednostkowego języka C++ do kategorii aplikacji Visual C++ w oknie dialogowym Nowy projekt. Rozpocznij pisanie testów jednostkowych w wygenerowanym szkieletu kodu TEST_METHOD w pliku Unittest1.cpp. Gdy kod testu są zapisywane, Skompiluj rozwiązanie. Aby uruchomić testy, należy otworzyć **Eksplorator testów jednostkowych** okna, wybierając **widoku** > **Windows inne** > **testu jednostkowego Eksplorator**, a następnie w menu skrótów dla przypadku testowego, ma wybierz **Uruchom wybrane testy**. Po zakończeniu przebiegu testu, można wyświetlić wyników testów oraz informacje o śladzie stosu dodatkowe w tym samym oknie.

#### <a name="architecture-dependency-graphs"></a>Wykresy zależności architektury

Aby lepiej zrozumieć swój kod, można wygenerować wykresy zależności dla binarnego, klasy, przestrzeni nazw i Dołącz pliki w rozwiązaniu. Na pasku menu wybierz **architektury** > **Generuj wykres zależności**, a następnie **dla rozwiązania** lub **dla załącz plik**do wygenerowania wykresu zależności. Po zakończeniu generowania wykresu można Dowiedz się więcej, rozwijając każdego węzła, Dowiedz się relacji zależności, przenosząc je między węzłami i przeglądania kodu źródłowego, wybierając **Wyświetl zawartość** menu skrótów dla węzła. Aby wygenerować wykres zależności dla plików dołączanych, w menu skrótów dla \*pliku kodu źródłowego .cpp lub \*.h nagłówka pliku, wybierz polecenie **generowania wykresu z pliki dołączane**.

#### <a name="architecture-explorer"></a>Eksplorator architektury

Za pomocą **Eksploratora architektury**, możesz zapoznać się z zasobami w rozwiązaniu języka C++, projekty lub pliki. Na pasku menu wybierz **architektury** > **Windows** > **Eksploratora architektury**. Można wybrać węzła, czy chcesz się dowiedzieć, na przykład **Widok klas**. W takim przypadku po prawej stronie okna narzędzi jest rozwinięta, z listy obszarów nazw. Jeśli wybierzesz obszaru nazw, nowa kolumna pokazuje listę klas, struktur i wyliczeń w tej przestrzeni nazw. Można nadal zapoznaj się z tymi zasobami, lub wróć do kolumny na końcu z lewej strony można uruchomić inne zapytanie. Zobacz **wyszukiwanie kodu za pomocą narzędzia Architecture Explorer**.

#### <a name="code-coverage"></a>Pokrycie kodu

Pokrycie kodu został zaktualizowany do dynamicznie instrument binarnych w czasie wykonywania. Zmniejsza obciążenie konfiguracji oraz zapewnia lepszą wydajność. Może również zbierać dane pokrycia kodu z testów jednostkowych dla aplikacji C++. Po utworzeniu testów jednostkowych C++ można użyć **Eksplorator testów jednostkowych** mógł odnaleźć testów w rozwiązaniu. Aby uruchomić testy jednostkowe i zbieranie danych pokrycia kodu dla nich w **Eksplorator testów jednostkowych**, wybierz **Analizuj pokrycie kodu**. Można sprawdzić wyniki pokrycia kodu w **wyniki pokrycia kodu** okna — na pasku menu wybierz **testu** > **Windows**  >   **Wyniki pokrycia kodu**.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co nowego w języku C++ w programie Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Kompilator języka C++ i konsolidatora

**auto Keyword.** **Automatycznie** — słowo kluczowe ma nowy cel. Użyj domyślnego rozumieniu **automatycznie** — słowo kluczowe, aby zadeklarować zmienną, którego typ jest ustalić na podstawie wyrażenia inicjowania w deklaracji zmiennej. `/Zc:auto` — Opcja kompilatora wywołuje nowy lub poprzedniego znaczenie **automatycznie** — słowo kluczowe.

**decltype — Specyfikator typu.** **Decltype** Specyfikator typu zwraca typ określonego wyrażenia. Użyj **decltype** Specyfikator typu w połączeniu z **automatycznie** — słowo kluczowe do deklarowania typu złożonego lub znanego tylko w kompilatorze. Na przykład użyć kombinacji do deklarowania funkcji szablonu, którego typem zwracanym jest zależna od typów argumentów szablonu. Można również zadeklarować funkcji szablonu, który wywołuje inną funkcję, a następnie zwraca typ zwracany funkcji o nazwie.

**Lambda Expressions.** Funkcje lambda mają treści funkcji, ale bez nazwy. Funkcje lambda łączą najlepsze cechy wskaźników funkcji i obiektów funkcyjnych. Użycie funkcji lambda przez siebie, jako parametr funkcji szablonu zamiast obiektu funkcyjnego lub wraz z **automatycznie** — słowo kluczowe, aby zadeklarować zmienną, którego typ jest wyrażeniem lambda.

**Odwołanie Rvalue.** Deklarator odwołania do r-wartości (& &) deklaruje odwołanie rvalue. Umożliwia odwołanie rvalue, których możesz użyć przenoszenie semantyki i doskonałe przekazywanie do pisania konstruktorów bardziej wydajne, funkcji i szablony.

**static_assert Declaration.** A **static_assert** deklaracji testuje asercję oprogramowania w czasie kompilacji, w przeciwieństwie do innych mechanizmów potwierdzenia, które testują w czasie wykonywania. Jeśli potwierdzenie nie powiedzie się, kompilacja nie powiedzie się i wystawiono określony komunikat o błędzie.

**nullptr i __nullptr słów kluczowych.** Kompilator języka Visual C++ pozwala na używanie **nullptr** — słowo kluczowe z kodu macierzystego lub kodu zarządzanego. **Nullptr** słowo kluczowe wskazuje, że dojście do obiektu, posługiwanie się nimi wskaźnika lub typu wskaźnik natywny nie wskazuje obiektu. Kompilator interpretuje **nullptr** jako kodu zarządzanego, gdy używasz `/clr` — opcja kompilatora i kodu natywnego, gdy nie używasz `/clr` opcji.
Specyficzne dla firmy Microsoft **__nullptr** — słowo kluczowe ma takie samo znaczenie jak **nullptr**, ale dotyczy ona tylko kodu natywnego. Jeśli kompilujesz natywnego kodu C/C++ za pomocą `/clr` — opcja kompilatora, kompilator nie może określić czy **nullptr** — słowo kluczowe jest natywny lub terminów zarządzanych. Aby zamiaru Wyczyść, aby kompilator, użyj nullptr — słowo kluczowe, aby określić termin zarządzanych i **__nullptr** Aby określić termin natywnych.

**/ Zc: trigraphs — opcja kompilatora.** Domyślnie pomoc techniczna dotycząca trójznaków jest wyłączona. Użyj `/Zc:trigraphs` opcję kompilatora, aby włączyć obsługę trójznaków.
Trójznak składa się z dwóch następujących po sobie znaki zapytania (?) następuje znak trzeci unikatowy. Kompilator zastępuje trójznak odpowiedni znak interpunkcyjny. Na przykład, kompilator zamienia? = — trigram znakiem # (znak liczby). Używać trójznaków w plikach źródłowych języka C, korzystających z zestawu znaków, który nie zawiera niektóre znaki interpunkcyjne.

**Nowa opcja optymalizacji sterowanej profilem.** PogoSafeMode to nowa opcja optymalizacji sterowanej profilem, co pozwala określić, czy ma być używany tryb awaryjny lub trybie szybkim, podczas optymalizacji aplikacji. Tryb awaryjny jest bezpieczna dla wątków, ale wolniejsza niż w trybie szybkim. Tryb szybki jest zachowaniem domyślnym.

**Nowe /clr:nostdlib opcji środowiska uruchomieniowego języka wspólnego (CLR).** Nowa opcja jest dodawany do `/clr` (kompilacja języka wspólnego środowiska uruchomieniowego). Jeśli dołączono różne wersje tego samego bibliotek, zgłaszany jest błąd kompilacji. Nowa opcja umożliwia wykluczenie domyślne biblioteki środowiska CLR, tak aby program może użyć określonej wersji.

**Nowe detect_mismatch dyrektywy pragma.** Detect_mismatch dyrektywy pragma umożliwia Umieść znacznik w plikach, które są porównywane do innych tagów, które mają taką samą nazwę. W przypadku wielu wartości dla tej samej nazwie, konsolidator generuje błąd.

**Funkcje wewnętrzne XOP FMA4 funkcje wewnętrzne i LWP funkcje wewnętrzne.** Nowe funkcje wewnętrzne zostały dodane do obsługi XOP dodane funkcje wewnętrzne dla programu Visual Studio 2010 z dodatkiem SP1, dodano funkcje wewnętrzne FMA4 dla programu Visual Studio 2010 z dodatkiem SP1 i dodaje funkcje wewnętrzne LWP dla technologii programu Visual Studio 2010 SP1 procesora. Użyj __cpuid, __cpuidex, aby określić technologii procesora, które są obsługiwane na określonym komputerze.

### <a name="visual-c-projects-and-the-build-system"></a>Projekty języka Visual C++ i systemu kompilacji

**MSBuild.** Visual C++ rozwiązania i projekty są teraz tworzone przy użyciu MSBuild.exe, która zastępuje VCBuild.exe. Program MSBuild jest tego samego narzędzia kompilacji elastycznych funkcji, rozszerzalne, oparte na języku XML, który jest używany przez inne języki Visual Studio i typów projektów. Ze względu na tę zmianę pliki projektu Visual C++ teraz używać pliku w formacie XML i mają rozszerzenie nazwy pliku .vcxproj. Pliki projektu Visual C++ z wcześniejszych wersji programu Visual Studio automatycznie są konwertowane na nowy format pliku.

**Katalogi VC ++.** Katalogi VC ++ ustawienie teraz znajduje się w dwóch miejscach. Użyj strony właściwości projektu, aby ustawić wartości na projekt katalogi VC ++. Użyj **Menedżer właściwości** i arkusz właściwości do ustawienia globalne, wartości dla konfiguracji katalogi VC ++.

**Zależności projektu do projektu.** We wcześniejszych wersjach zdefiniowanych współzależności między projektami są przechowywane w pliku rozwiązania. Jeśli te rozwiązania są konwertowane na nowy format pliku projektu, zależności są konwertowane na odwołania projekt projekt. Ta zmiana może mieć wpływ na aplikacje, ponieważ pojęcia zależności rozwiązanie i odwołania projekt projekt są różne.

**Makra i zmiennych środowiskowych.** Nowe makro _ITERATOR_DEBUG_LEVEL wywołuje obsługę debugowania dla iteratorów. Użyj tego makra zamiast starszych _SECURE_SCL i _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

**Biblioteki środowiska uruchomieniowego współbieżności.** Struktura środowiska uruchomieniowego współbieżności obsługuje aplikacje i składniki, które są uruchamiane jednocześnie, a to architektura programowania aplikacji współbieżnych w programie Visual C++. Aby zapewnić obsługę programowania aplikacji współbieżnych, biblioteka równoległych wzorców (PPL) zapewnia kontenery ogólnego przeznaczenia i algorytmów do wykonywania równoległość drobnoziarnistą. Bibliotekę asynchronicznych agentów zapewnia model programowania oparty na aktora i komunikat, przekazując interfejsów gruboziarnistych przepływu danych i przetwarzanie potokowe zadania.

**Standardowa biblioteka języka C++.** Na poniższej liście opisano wiele zmian, które zostały wprowadzone do standardowej biblioteki C++.

- Aby zaimplementować semantykę przenoszenia i doskonałe przekazywanie do przodu dla wielu funkcji w standardowej biblioteki szablonów został użyty z nowej funkcji języka C++ odwołanie rvalue. Semantyki przenoszenia i doskonałe przekazywanie do przodu znacznie zwiększyć wydajność operacji alokacji lub przypisania zmiennych i parametrów.
- Odwołania wartościowane prawostronnie są również używane do wdrożenia nowego `unique_ptr` klasy, która jest typu inteligentnego wskaźnika bezpieczniejsze niż `auto_ptr` klasy. `unique_ptr` Klasy jest ruchome, ale nie kopiowania implementuje semantykę strict własność bez wywierania wpływu na bezpieczeństwo i dobrze działa z kontenerów, które rozpoznają odwołań r-wartości. `auto_ptr` Klasy jest przestarzały.
- Piętnastu Państw nowe funkcje, na przykład `find_if_not`, `copy_if`, i `is_sorted`, zostały dodane do \<algorytm > nagłówka.
- W \<pamięci > nagłówka, nowa funkcja make_shared jest wygodne, niezawodne i efektywne sposobem utworzenia wspólny wskaźnik do obiektu w tym samym czasie, obiekt jest konstruowany.
- Pojedynczo połączoną listy są obsługiwane przez \<forward_list > nagłówka.
- Nowy `cbegin`, `cend`, `crbegin`, i `crend` zapewniają funkcje Członkowskie `const_iterator` , przechodzi do przodu lub wstecz przez kontener.
- \<System_error > Nagłówek i powiązanych szablonów obsługuje przetwarzanie błędów niskiego poziomu systemu. Elementy członkowskie `exception_ptr` klasy może służyć do transportu wyjątków między wątkami.
- \<Codecvt > nagłówka obsługuje konwertowania kodowań znaków Unicode do innego kodowania.
- \<Buforów > nagłówka definiuje kilka szablonów, które pomagają przydzielać i zwalniać bloki pamięci dla kontenerów opartych na węźle.
- Istnieje wiele aktualizacji do \<losowy > nagłówka.

### <a name="microsoft-foundation-class-mfc-library"></a>Bibliotekę Microsoft Foundation Class (MFC)

**Funkcje Windows 7.** Biblioteka MFC obsługuje wiele funkcji Windows 7, na przykład wstążki interfejsu użytkownika (UI), pasek zadań, listy szybkiego dostępu, miniatury z kartami, miniatury, pasek postępu, nakładkę ikony funkcji i indeksowanie wyszukiwania. Ponieważ MFC automatycznie obsługuje wiele funkcji Windows 7, nie trzeba zmodyfikować istniejącą aplikację. Do obsługi innych funkcji w nowych aplikacji, umożliwia określenie funkcjonalność, którą chcesz używać Kreatora aplikacji MFC.

**Rozpoznawanie wielodotyku.** Biblioteka MFC obsługuje aplikacje, które mają za pomocą interfejsu użytkownika Wielodotyk, na przykład w przypadku aplikacji, które zostały napisane dla systemu operacyjnego Microsoft Surface. Aplikacja wielodotyku może obsługiwać Windows touch wiadomości i gestów wiadomości, które są kombinacjami touch wiadomości. Po prostu Zarejestruj swoją aplikację na dotyk i zdarzenia gestu i system operacyjny będzie kierowanie zdarzeń usługi wielodotyku inne programy obsługi zdarzeń.

**Informowanie o wysokiej rozdzielczości DPI.** Domyślnie aplikacjach MFC są wysoka-obsługującą ustawienia DPI. W przypadku aplikacji o wysokiej rozdzielczości (o dużej liczbie punktów na cal) wiedzieć, systemu operacyjnego można skalować system windows, tekst i inne elementy interfejsu użytkownika dla bieżącej rozdzielczości ekranu. Oznacza to, że skalowany obraz jest bardziej prawdopodobne rozmieszczony prawidłowo i nie jest przycinana lub podzielony na piksele.

**Ponownie uruchom Menedżera.** Menedżera ponownego uruchamiania zapisuje dokumenty i automatycznie spowoduje ponowne uruchomienie aplikacji, jeśli nieoczekiwane zamknięcie lub ponowne uruchomienie. Na przykład można użyć Menedżera ponownego uruchamiania, aby uruchomić aplikację po zamknięciu, automatycznych aktualizacji. Aby uzyskać więcej informacji o sposobie konfigurowania aplikacji do użycia Menedżera ponownego uruchamiania, zobacz **jak: Dodawanie obsługi Menedżera ponownego uruchamiania**.

**CTaskDialog.** `CTaskDialog` Klasa może być używana zamiast standardowego `AfxMessageBox` okno komunikatu. `CTaskDialog` Klasy Wyświetla i zbiera więcej informacji, niż w polu standardową wiadomość.

#### <a name="safeint-library"></a>Biblioteka SafeInt

Nowa biblioteka SafeInt wykonuje operacje arytmetyczne bezpieczne tego konta dla przepełnienia liczby całkowitej. Ta biblioteka również porównuje różne rodzaje liczb całkowitych.

#### <a name="new-active-template-library-atl-macros"></a>Nowe makra Active Template Library (ATL)

Nowe makra zostały dodane do biblioteki ATL, aby rozszerzyć funkcjonalność PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE i PROP_ENTRY_INTERFACE_EX pozwalają dodać listę CLSID prawidłowe. PROP_ENTRY_INTERFACE_CALLBACK i PROP_ENTRY_INTERFACE_CALLBACK_EX umożliwiają określenie funkcji wywołania zwrotnego w celu ustalenia, czy identyfikator CLSID jest nieprawidłowy.

#### <a name="analyze-warnings"></a>/ analyze ostrzeżenia

Większość `/analyze` ostrzeżenia (analiza kodu przedsiębiorstwa) zostały usunięte z bibliotek C Run-Time (CRT), MFC i ATL.

#### <a name="animation-and-d2d-support"></a>Animacja i D2D pomocy technicznej

Biblioteka MFC obsługuje teraz animacji i grafiki Direct2D. Biblioteka MFC zawiera kilka nowych klas MFC i funkcje, aby obsługiwać tę funkcję. Istnieją również dwa nowe wypróbowanie pokazują, jak dodawanie obiektu D2D i obiekt animacji do projektu. Te wskazówki są **instruktażu: Dodawanie obiektu D2D do projektu MFC** i **instruktażu: Dodawanie animacji do projektu MFC**.

### <a name="ide"></a>IDE

**Ulepszona funkcja IntelliSense.** Funkcja IntelliSense dla języka Visual C++ został całkowicie przeprojektowany być szybsze, bardziej precyzyjne i może obsługiwać większe projekty. Aby osiągnąć to ulepszenie, IDE rozróżnia jak Projektant wyświetla i modyfikuje kodu źródłowego i jak IDE używa ustawień źródła kodu i projektu do zbudowania rozwiązania.
Ze względu na to podział obowiązków przeglądania funkcje takie jak **Widok klas** i nowych **przejdź do** okno dialogowe, są obsługiwane przez system, który jest oparty na nowy serwer SQL database pulpitu (.sdf) pliku zastępuje stare nie skompiluj plik przeglądania (.NCB —). Funkcje IntelliSense, takie jak skróconych informacji, automatyczne uzupełnianie i pomocy parametru przeanalizować jednostki translacji, tylko wtedy, gdy jest to wymagane. Funkcje hybrydowe, takie jak nowy **hierarchię wywołań** okna, należy użyć zestawienia funkcji IntelliSense i przeglądania.
Ponieważ technologia IntelliSense przetwarza tylko te informacje, które wymagają w tej chwili, IDE jest zwiększyć szybkość reakcji. Ponadto ponieważ bardziej aktualne informacje, IDE, widokach i oknach są bardziej precyzyjne operacje. Na koniec ponieważ infrastruktury IDE jest lepiej zorganizowany bardziej możliwością i bardziej skalowalna, może obsługiwać większe projekty.

**Ulepszona funkcja IntelliSense błędy.** IDE lepiej wykrywa błędy, które mogłyby spowodować utratę funkcji IntelliSense i wyświetla czerwone faliste podkreślenia w ramach nich. Ponadto środowisko IDE zgłasza błędy funkcji IntelliSense do **okno listy błędów**. Aby wyświetlić kod, który jest przyczyną problemu, klikaj dwukrotnie poszczególne błędy w **okno listy błędów**.

**# Auto-Complete Feature include.** IDE obsługuje automatyczne uzupełnianie dla `#include` — słowo kluczowe. Podczas wpisywania `#include`, IDE tworzy pole listy rozwijanej plików prawidłowego nagłówka. Jeśli będziesz kontynuować, wpisując nazwę pliku, IDE filtrowanie listy oparte na zgłoszenia użytkownika. W dowolnym momencie można wybrać z listy plików, które mają zostać uwzględnione. Dzięki temu można szybko dołączać pliki bez znajomości dokładnej nazwy pliku.

**Przejdź do.** **Przejdź do** okna dialogowego pole pozwala wyszukiwać wszystkie pliki w projekcie, które odpowiadają określony ciąg i symbole. Wyniki wyszukiwania są natychmiast zmieniony podczas wpisywania dodatkowe znaki w wyszukiwanym ciągu. **Wyniki** pole informacji zwrotnych informuje, liczba odnalezionych elementów i pomoże Ci zdecydować, czy ograniczyć wyszukiwanie. **Rodzaj/zakresu**, **lokalizacji**, i **Podgląd** odwołania pól opinii pomagają ujednoznacznić elementy, które mają podobne nazwy. Ponadto można rozszerzyć tę funkcję w celu obsługi innych języków programowania.

**Równoległe debugowania i profilowania.** Debuger programu Visual Studio jest świadome współbieżności środowiska wykonawczego i ułatwia rozwiązywanie problemów z aplikacjami do przetwarzania równoległego. Aby zwizualizować ogólne działanie aplikacji, można użyć tego nowego narzędzia profiler współbieżności. Ponadto możesz użyć nowego okna narzędzi wizualizować stan zadań i ich stosy wywołań.

**Projektant wstążki.** **Projektanta wstążki** jest edytor graficzny, która umożliwia tworzenie i modyfikowanie MFC wstążki interfejsu użytkownika. Interfejs użytkownika końcowego wstążki jest reprezentowany przez plik zasobów opartych na języku XML (.mfcribbon-ms). W przypadku istniejących aplikacji można przechwycić bieżący interfejs użytkownika wstążki tymczasowo dodając kilka wierszy kodu, a następnie wywoływania **projektanta wstążki**. Utworzony plik zasobów wstążki z wstążki pisma odręcznego kodu interfejsu użytkownika można zastąpić kilka instrukcji, które ładują zasób wstążki.

**Hierarchia wywołań.** **Hierarchię wywołań** okno umożliwia przejdź do wszystkich funkcji, które są wywoływane przez konkretną funkcję lub do wszystkich funkcji, które wywołują konkretną funkcję.

### <a name="tools"></a>Narzędzia

**Kreator klas MFC.** Visual C++ 2010 powoduje zwrócenie cenionym narzędzie Kreator klas MFC. Kreator klas MFC jest wygodny sposób, aby dodać klasy, wiadomości i zmienne do projektu bez konieczności ręcznego modyfikowania zestawy plików źródłowych.

**Kreator kontrolki ATL.** Kreator kontrolki ATL nie będzie automatycznie wypełnia `ProgID` pola. Jeśli nie ma kontrolki ATL `ProgID`, inne narzędzia mogą nie działać z nim. Jednym z przykładów to narzędzie, które wymaga formantów, aby `ProgID` jest **Wstaw aktywny formant** okno dialogowe. Aby uzyskać więcej informacji na temat okna dialogowego, zobacz **okno dialogowe Wstawianie kontrolki ActiveX**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

Dodanie ymmword — typ danych obsługuje 256-bitowego multimedialnych argumenty operacji, które są zawarte w instrukcjach Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co nowego w języku C++ w programie Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Visual C++ zintegrowanego środowiska programistycznego (IDE)

- Okna dialogowe, które są tworzone w aplikacji Win32, ATL i MFC, teraz są zgodne z wytycznymi dotyczącymi stylu Windows Vista. Podczas tworzenia nowego projektu za pomocą programu Visual Studio 2008, wszystkich oknach dialogowych, które wstawić w aplikacji będą stosować się wytyczne dotyczące stylu Windows Vista. Jeśli należy ponownie skompilować projekt, który został utworzony we wcześniejszej wersji programu Visual Studio, wszystkie istniejące okna dialogowe zachowają wyglądają tak samo, który wcześniej mieli oni. Aby uzyskać więcej informacji o tym, jak można wstawić okien dialogowych do aplikacji, zobacz **Edytor okien dialogowych**.

- **Projekt ATL** kreatora zawiera teraz opcję by zarejestrować komponenty dla wszystkich użytkowników. Począwszy od programu Visual Studio 2008 składniki COM i bibliotek typów, które są tworzone przez **Projekt ATL** kreatora są zarejestrowane w węźle HKEY_CURRENT_USER rejestru dopiero po wybraniu **składnik rejestru dla wszystkich użytkowników**.
- **Projekt ATL** kreatora nie zawiera już opcji tworzenia opartego na atrybutach projektach ATL. Począwszy od programu Visual Studio 2008, **Projekt ATL** Kreator ma opcję, aby zmienić stan opartego na atrybutach nowy projekt. Wszystkie nowe projekty ATL, tworzonych przez kreatora są teraz unattributed.
- Zapisywanie w rejestrze mogą zostać przekierowane. Wraz z wprowadzeniem systemu Windows Vista zapis do określonych obszarów rejestru wymaga program ma być uruchomiony w trybie podniesionych uprawnień. Nie jest pożądane, aby zawsze uruchomić program Visual Studio w trybie podniesionych uprawnień. Przekierowanie na użytkownika automatycznie przekierowuje zapisu rejestru z HKEY_CLASSES_ROOT do HKEY_CURRENT_USER bez wprowadzania żadnych zmian programowania.
- **Projektanta klas** teraz ma ograniczoną obsługę dla kodu natywnego języka C++. We wcześniejszych wersjach programu Visual Studio **projektanta klas** działały tylko z Visual C# i Visual Basic. C++, użytkownicy mogą teraz używać **projektanta klas**, ale tylko w trybie tylko do odczytu. Aby uzyskać więcej informacji o sposobie używania **projektanta klas** przy użyciu języka C++, zobacz **Praca z kodem Visual C++ w Projektancie klas**.
- Kreator projektu nie ma już opcję, aby utworzyć projekt C++ programu SQL Server. Począwszy od programu Visual Studio 2008 Kreator nowego projektu nie ma opcji, aby utworzyć projekt C++ programu SQL Server. SQL Server — projekty utworzone za pomocą starszej wersji programu Visual Studio skompiluje i działać poprawnie.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

#### <a name="general"></a>Ogólne

- Aplikacje może być powiązana z określonych wersji bibliotek Visual C++. Czasami aplikacja jest zależna od aktualizacji, które zostały wprowadzone do bibliotek języka Visual C++ po wydaniu. W przypadku uruchamiania aplikacji na komputerze, który ma wcześniejszą wersję biblioteki może spowodować nieoczekiwane zachowanie. Teraz można powiązać aplikacji do określonej wersji biblioteki, tak, aby nie będzie działać na komputerze, na którym jest starsza wersja bibliotek.

#### <a name="stlclr-library"></a>Biblioteka STL/CLR

- Visual C++ zawiera teraz biblioteki STL/CLR. Biblioteka STL/CLR to opakowanie standardowych szablon biblioteki (STL), podzbiór standardowej biblioteki C++, do użytku z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). STL/CLR można teraz użyć wszystkich kontenerów, iteratorów i algorytmów STL w zarządzanym środowisku.

#### <a name="mfc-library"></a>MFC Library

- Windows Vista obsługuje formanty standardowe. Ponad 150 metod 18 klas nowego lub istniejącego dodano do obsługi funkcji Windows Vista lub do poprawienia funkcji w bieżącym klas MFC.
- Nowy `CNetAddressCtrl` klasy umożliwia wprowadzania i sprawdzania poprawności adresów IPv4 i IPv6 lub nazwy DNS.
- Nowy `CPagerCtrl` klasa upraszcza korzystanie z kontroli pagera Windows.
- Nowy `CSplitButton` klasa upraszcza korzystanie z kontrolki splitbutton Windows, aby wybrać domyślne lub opcjonalne działanie.

#### <a name="c-support-library"></a>Biblioteka obsługi języka C++

- C++ wprowadza Biblioteka dotycząca organizowania. Biblioteka dotycząca organizowania umożliwia łatwe i zoptymalizowane do organizowania danych między środowiskami macierzystymi i zarządzanymi. Biblioteka stanowi alternatywę do bardziej złożona i mniej wydajne rozwiązanie metody, na przykład za pomocą funkcji PInvoke. Zobacz **Overview of Marshaling w C++** Aby uzyskać więcej informacji.

#### <a name="atl-server"></a>Aplikacji serwera ATL.

- Serwer ATL jest wydawane jako projekt źródłowy udostępniony.
- Większość bazy kodu serwera ATL zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio 2008. Kilka plików skojarzonych z aplikacji serwera ATL. nie są już częścią Visual Studio. Aby uzyskać listę usuniętych plików, zobacz **usunięte pliki serwera ATL**.
- Dane, kodowania i dekodowania klas z atlenc.h wraz z narzędziem funkcji i klas z atlutil.h i atlpath.h są teraz częścią biblioteki ATL.
- Firmy Microsoft będą w dalszym ciągu obsługuje wersje aplikacji serwera ATL. uwzględnionych we wcześniejszych wersjach programu Visual Studio, tak długo, jak te wersje programu Visual Studio są obsługiwane. CodePlex będzie kontynuować tworzenie kodu aplikacji serwera ATL. jako projekt społeczności. Firma Microsoft nie obsługuje CodePlex wersję aplikacji serwera ATL.

### <a name="visual-c-compiler-and-linker"></a>Kompilator języka Visual C++ i Konsolidatorze

#### <a name="compiler-changes"></a>Compiler Changes

- Kompilator obsługuje zarządzane kompilacje przyrostowe. Gdy ta opcja jest określona, kompilator nie będzie ponownie kompilować kodu, gdy ulegnie zmianie przywoływanego zestawu. Zamiast tego zostanie przeprowadzone kompilacji przyrostowej. Pliki są ponownie kompilowane tylko wtedy, gdy zmiany wpływają na kod zależny od.
- Atrybuty powiązane z aplikacji serwera ATL. nie są już obsługiwane. Kompilator nie obsługuje już kilka atrybutów, które zostały bezpośrednio z aplikacji serwera ATL. Aby uzyskać pełną listę atrybutów, które usunięto Zobacz fundamentalne zmiany.
- Kompilator obsługuje mikroarchitektury Intel Core. Kompilator zawiera automatycznego dostrajania dla mikroarchitektury Intel Core podczas generowania kodu. Domyślnie to dostrajanie znajduje się na i nie można wyłączyć, ponieważ ułatwia również Pentium 4 i inne procesory.
- Funkcje wewnętrzne obsługuje nowszych procesory AMD i Intel. Kilka nowych instrukcji wewnętrzne obsługuje większą funkcjonalność w nowych procesory AMD i Intel. Aby uzyskać więcej informacji na temat nowych funkcji wewnętrznych, zobacz **dodatkowe Streaming SIMD Extensions 3 instrukcje**, **Streaming SIMD Extensions 4 instrukcje**, **SSE4A i zaawansowane bitowe Funkcje wewnętrzne manipulowania**, **funkcje wewnętrzne AES**, **_mm_clmulepi64_si128**, i **__rdtscp**.
- `__cpuid` Aktualizować funkcji. `__cpuid`, `__cpuidex` Funkcje obsługują teraz kilka nowych funkcji z najnowszej wersje procesory AMD i Intel. `__cpuidex` Wewnętrzne nowego i gromadzi informacji od najnowszych procesorów.
- `/MP` — Opcja kompilatora skraca czas całkowity kompilacji. `/MP` Opcji mogą znacznie zmniejszyć całkowity czas do kompilowania kilku plików źródłowych, tworząc kilka procesów jednocześnie kompilowane pliki. Ta opcja jest szczególnie przydatne, na komputerach obsługujących wielowątkowość, wiele procesorów lub wiele rdzeni.
- `/Wp64` — Opcja kompilatora i **__w64** — słowo kluczowe są przestarzałe. `/Wp64` — Opcja kompilatora i **__w64** słowo kluczowe, które wykryć problemy z przenośnością 64-bitowych, są przestarzałe i zostanie usunięta w przyszłej wersji kompilatora. Zamiast — opcja kompilatora i — słowo kluczowe należy użyć kompilator języka Visual C++ tej platformy cele 64-bitowego.
- `/Qfast_transcendentals` generuje kod wbudowanej funkcji przestępne.
- `/Qimprecise_fwaits` Usuwa polecenia fwait wewnętrzny, aby spróbować bloków, korzystając z `/fp:except` — opcja kompilatora.

### <a name="linker-changes"></a>Linker Changes

- Informacje o kontroli konta użytkownika jest teraz osadzona w plikach manifestu dla plików wykonywalnych przez Visual C++ łączący (link.exe). Ta funkcja jest włączona domyślnie. Aby uzyskać więcej informacji na temat sposobu wyłączania tej funkcji lub jak zmodyfikować zachowanie domyślne, zobacz `/MANIFESTUAC` (osadza informacje UAC w manifeście).
- Konsolidator ma teraz `/DYNAMICBASE` opcję, aby włączyć funkcję randomizacji układu przestrzeni adresowej systemu Windows Vista. Ta opcja modyfikuje nagłówek pliku wykonywalnego, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co nowego w języku C++ w programie Visual Studio 2005

Nowość w Visual C++ 2005 z dodatkiem Service Pack 1 wprowadzono następujące funkcje:

### <a name="intrinsics-for-x86-and-x64"></a>Funkcje wewnętrzne x86 i x64

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

### <a name="intrinsics-for-x64-only"></a>Funkcje wewnętrzne x64 tylko

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Nowych słów kluczowych języka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nowe funkcje kompilatora

Kompilator zawiera istotne zmiany w tej wersji.

- natywne "64-bitowe i kompilatory krzyżowe.
- `/analyze` Dodano — opcja kompilatora (analiza kodu przedsiębiorstwa).
- `/bigobj` dodano opcję kompilatora.
- `/clr:pure`, `/clr:safe`, i `/clr:oldSyntax` zostały dodane. (Później przestarzałe w programie Visual Studio 2015 i usunięto w programie Visual Studio 2017)
- Przestarzałe — opcje kompilatora: wiele opcji kompilatora zostały zaniechane w tej wersji; zobacz **przestarzałe opcje kompilatora** Aby uzyskać więcej informacji.
- Podwójna konwersja bitowa w `/clr` kodu jest ograniczone; zobacz **podwójna konwersja bitowa adresów (C++)** Aby uzyskać więcej informacji.
- `/EH` (Model obsługi wyjątku) lub `/EHs` nie będzie można przechwycić wyjątek, który jest wywoływany z coś innego niż throw; użyj `/EHa`.
- `/errorReport` Dodano — opcja kompilatora (zgłaszaj wewnętrzne błędy kompilatora).
- `/favor` (Optymalizuj dla 64) — opcja kompilatora został dodany.
- `/FA`, `/Fa` — Opcja kompilatora (plik z listą) został dodany.
- `/FC` Opcja kompilatora (pełna ścieżka z pliku kodu źródłowego w diagnostyce) został dodany.
- `/fp` (Określenie zachowania zmiennopozycyjna) — opcja kompilatora został dodany.
- `/G` (Optymalizuj dla procesora) Dodano opcje — opcja kompilatora.
- `/G` (Optymalizuj dla procesora) Dodano opcje — opcja kompilatora.
- `/G3`, `/G4`, `/G5`, `/G6`, `/G7`, i `/GB` opcje kompilatora zostały usunięte. Kompilator używa teraz "mieszany model", który podejmuje próbę utworzenia najlepsze pliku wyjściowego dla wszystkich architektur.
- `/Gf` została usunięta. Użyj `/GF` (eliminowanie ciągów zduplikowanych) zamiast tego.
- `/GL` (Optymalizacja Całoprogramowa) jest teraz zgodna z `/CLRHEADER`.
- `/GR` jest teraz domyślnie włączone.
- `/GS` (Bufora sprawdzanie zabezpieczeń) udostępnia teraz ochronę dla parametrów wskaźnika na ataki. `/GS` jest teraz domyślnie włączone. `/GS` obecnie działa także w funkcjach skompilowanych do MSIL przy użyciu `/clr` (kompilacja języka wspólnego środowiska uruchomieniowego).
- `/homeparams` Dodano — opcja kompilatora (Kopiuj Parametry rejestru do stosu).
- `/hotpatch` (Utwórz obraz Hotpatchable) dodano opcję kompilatora.
- Zaktualizowano wbudowanej funkcji heurystyki; zobacz **wbudowane**, **__inline**, **__forceinline** i **inline_depth** Aby uzyskać więcej informacji
- Dodano wiele nowych funkcji wewnętrznych i opisano wiele obiektów wewnętrznych Nieudokumentowany wcześniej.
- Domyślnie każde wywołanie do nowego, który zakończy się niepowodzeniem, spowoduje zgłoszenie wyjątku.
- `/ML` i `/MLd` opcje kompilatora zostały usunięte. Visual C++ nie obsługuje już jednowątkowe, statycznie łączonych Obsługa biblioteki CRT.
- Kompilator zaimplementowane optymalizacji nazwanej zwracanej wartości, która jest włączona, podczas kompilowania z `/O1`, `/O2` (Minimalizuj rozmiar, Maksymalizuj szybkość), `/Og` (optymalizacje globalne) i `/Ox` (Pełna optymalizacja).
- `/Oa` — Opcja kompilatora zostało usunięte, ale będzie można dyskretnie ignorowana; Użyj `noalias` lub `restrict__declspec` modyfikatorów, aby określić, jak kompilator wykonuje aliasów.
- `/Op` — Opcja kompilatora miał zostało usunięte. Użyj `/fp` (określenie zachowania zmiennoprzecinkowego) zamiast tego.
- OpenMP, jest teraz obsługiwana przez Visual C++.
- `/openmp` Dodano — opcja kompilatora (Włącz obsługę OpenMP 2.0).
- `/Ow` — Opcja kompilatora zostało usunięte, ale będzie dyskretnie ignorowana. Użyj `noalias` lub `restrict__declspec` modyfikatorów, aby określić, jak kompilator wykonuje aliasów.

### <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

- `/QI0f` została usunięta.
- `/QIfdiv` została usunięta.
- `/QIPF_B` Dodano — opcja kompilatora (errata do krokowego procesora CPU B).
- `/QIPF_C` Dodano — opcja kompilatora (errata do krokowego procesora CPU C).
- `/QIPF_fr32` (Czy nie Użyj górnej 96 liczb zmiennoprzecinkowych punktu rejestruje) dodano opcję kompilatora.
- `/QIPF_noPIC` (Generuj kod zależny od położenia) dodano opcję kompilatora.
- `/QIPF_restrict_plabels` (Przyjmowane jest nie funkcji utworzone w środowisku uruchomieniowym) dodano opcję kompilatora.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

- `/vd` (Wyłącz przemieszczanie konstrukcji) umożliwia teraz użyć dynamic_cast Operator dla obiektu budowany (/ vd2)
- `/YX` Usunięto opcję kompilatora. Użyj `/Yc` (Utwórz prekompilowany plik nagłówkowy) lub `/Yu` (Korzystaj Prekompilowanego pliku nagłówka) zamiast tego. Jeśli usuniesz `/YX` z konfiguracjami kompilacji i zastąp go nothing, może to skutkować szybszymi kompilacjami.
- `/Zc:forScope` jest teraz domyślnie włączone.
- `/Zc:wchar_t` jest teraz domyślnie włączone.
- `/Zd` Usunięto opcję kompilatora. Numer wiersza, tylko informacje o debugowaniu nie jest już obsługiwana. Użyj `/Zi` zamiast (zobacz **/z7, / zi, /ZI (Format informacji debugowania)** Aby uzyskać więcej informacji).
- `/Zg` jest teraz prawidłowa tylko na plikach kodu źródłowego C, a nie na pliki kodu źródłowego języka C++.
- `/Zx` Dodano — opcja kompilatora (debugowanie zoptymalizowanego Itanium kodu).

### <a name="new-language-features"></a>Nowe funkcje języka

- Attributeattribute jest już przestarzały.
- `appdomain__declspec` Modyfikator został dodany.
- `__clrcall` Konwencja wywoływania został dodany.
- przestarzałe (C++) **declspec** modyfikator umożliwia teraz określić ciąg, który będzie wyświetlany w czasie kompilacji, gdy użytkownik próbuje uzyskać dostęp przestarzałe klasy lub funkcji.
- **dynamic_cast** Operator ma istotne zmiany.
- Teraz natywnych typów wyliczeniowych pozwalają na określenie podstawowego typu.
- `jitintrinsicdeclspec` Modyfikator został dodany.
- `noaliasdeclspec` Modyfikator został dodany.
- `process__declspec` Modyfikator został dodany.
- **abstrakcyjna**, **zastąpienia**, i **zapieczętowanego** są prawidłowe dla macierzystych.
- **Element __restrict** — słowo kluczowe został dodany.
- `restrictdeclspec` Modyfikator został dodany.
- **__thiscall** teraz jest słowem kluczowym.
- **__unaligned** — słowo kluczowe jest udokumentowany.
- **volatile** (C++) został zaktualizowany zachowanie w odniesieniu do optymalizacji.

### <a name="new-preprocessor-features"></a>Nowe funkcje preprocesora

- __CLR_VER dodano wstępnie zdefiniowane makro.
- Dyrektywy komentarza (C/C++) będzie teraz akceptować `/MANIFESTDEPENDENCY` jako komentarz konsolidatora. Opcja exestr, aby dodać komentarz jest już przestarzały.
- `embedded_idl` atrybut ( `#import` dyrektywy) teraz przyjmuje opcjonalny parametr.
- `fenv_access` Dyrektywy pragma
- `float_control` Dyrektywy pragma
- `fp_contract` Dyrektywy pragma
- Zmienne globalne nie zostaną zainicjowane w kolejności, w której są deklarowane, jeśli zmienne globalne pragma zarządzane, niezarządzane i niezarządzanych. To potencjalne istotnej zmiany, jeśli na przykład niezarządzanych zmienna globalna jest inicjowany za pomocą zarządzanych zmiennych globalnych i pełni skonstruowanego obiektu zarządzanego jest wymagana.
- Sekcje określony za pomocą init_seg są teraz tylko do odczytu i nie odczytu/zapisu w poprzednich wersjach.
- domyślne inline_depth jest teraz 16. Domyślnie 16 została również obowiązywać w Visual C++ .NET 2003.
- Wstępnie zdefiniowane makro _INTEGRAL_MAX_BITS dodane, zobacz wstępnie zdefiniowane makra.
- _M_CEE _M_CEE_PURE i _M_CEE_SAFE wstępnie zdefiniowane makra dodane, zobacz wstępnie zdefiniowane makra.
- _M_IX86_FP dodano wstępnie zdefiniowane makro.
- _M_X64 dodano wstępnie zdefiniowane makro.
- `make_public` Dyrektywy pragma
- `managed`, `unmanaged` zaktualizowano składnię pragma (ma teraz `push` i `pop`)
- Aby biblioteka mscorlib.dll teraz niejawnie odwołuje się `#using` dyrektywy we wszystkich `/clr` kompilacje.
- _OPENMP dodano wstępnie zdefiniowane makro.
- optymalizacji pragma została zaktualizowana, a i w nie są już prawidłowe parametry.
- #import no_registry — atrybut został dodany.
- `region`, `endregion` dodaje dyrektywy pragma
- _VC_NODEFAULTLIB dodano wstępnie zdefiniowane makro.
- Makra Wariadyczne są teraz zaimplementowane.
- `vtordisp` jest przestarzały i zostanie usunięta w przyszłej wersji programu Visual C++.
- `warning` Pragma ma teraz specyfikator Pomiń.

### <a name="new-linker-features"></a>Nowe funkcje konsolidatora

- Moduły (plików wyjściowych inne niż zestawu MSIL) są teraz dozwolone jako dane wejściowe do konsolidatora.
- `/ALLOWISOLATION` Dodano opcję konsolidatora (wyszukiwania plików manifestu).
- `/ASSEMBLYRESOURCE` (Osadź zarządzany zasób) został zaktualizowany, aby teraz umożliwiają określenie nazwy zasobu w zestawie oraz do określania, czy zasób jest prywatny w zestawie.
- `/CLRIMAGETYPE` (Określenie typu obrazu CLR) została dodana — opcja konsolidatora.
- `/CLRSUPPORTLASTERROR` Dodano opcję konsolidatora (Zachowaj kod ostatniego błędu dla wywołań PInvoke).
- `/CLRTHREADATTRIBUTE` Dodano opcję konsolidatora (atrybut wątku CLR zestawu).
- `/CLRUNMANAGEDCODECHECK` (Dodaj atrybut SuppressUnmanagedCodeSecurityAttribute) został dodany — opcja konsolidatora.
- `/ERRORREPORT` Dodano opcję konsolidatora (zgłaszaj wewnętrzne błędy konsolidatora).
- `/EXETYPE` — Opcja konsolidatora zostało usunięte. Konsolidator nie obsługuje już tworzenia sterowników urządzeń Windows 95 i Windows 98. Użyj odpowiedniego DDK, aby utworzyć te sterowniki urządzeń. EXETYPE — słowo kluczowe nie jest już prawidłowy dla pliki definicji modułu.
- `/FUNCTIONPADMIN` (Utwórz obraz Hotpatchable) — opcja konsolidatora został dodany.
- `/LTCG` — Opcja konsolidatora jest teraz obsługiwana dla modułów skompilowanych z `/clr`. `/LTCG` został także zaktualizowany do obsługi optymalizacje sterowane profilem.
- `/MANIFEST` (Tworzenie manifestu Side-by-Side) — opcja konsolidatora został dodany.
- `/MANIFESTDEPENDENCY` (Określ zależności manifestu) został dodany — opcja konsolidatora.
- `/MANIFESTFILE` Dodano opcję konsolidatora (nazwa pliku manifestu).
- `/MAPINFO:LINES` — Opcja konsolidatora zostało usunięte.
- `/NXCOMPAT` (Zgodny z zapobieganiem wykonywaniu danych) — opcja konsolidatora został dodany.
- `/PGD` (Określ bazę danych dla optymalizacji Profile-Guided) został dodany — opcja konsolidatora.
- `/PROFILE` Dodano opcję konsolidatora (Profiler narzędzi wydajności).
- `/SECTION` (Określ atrybuty sekcji) — opcja konsolidatora obsługuje teraz negacji atrybutu i nie obsługuje już L lub D atrybutów (powiązane VxD).
- Obsługa formatu Unicode w kompilatorze i konsolidatorze
- `/VERBOSE` Teraz — opcja konsolidatora (Drukuj komunikaty o postępie) akceptuje także Zapora połączenia internetowego i REF.
- `/VXD` — Opcja konsolidatora zostało usunięte. Konsolidator nie obsługuje już tworzenia sterowników urządzeń Windows 95 i Windows 98. Użyj odpowiedniego DDK, aby utworzyć te sterowniki urządzeń. VXD — słowo kluczowe nie jest już prawidłowy dla pliki definicji modułu.
- `/WS` — Opcja konsolidatora zostało usunięte. `/WS` został użyty do modyfikowania obrazów przeznaczony dla systemu Windows NT 4.0. IMAGECFG.exe, nazwa_pliku -R można użyć zamiast `/WS`. IMAGECFG.exe znajduje się na dysku CD z systemu Windows NT 4.0 w SUPPORT\DEBUG\I386\IMAGECFG. PLIK EXE.
- `/WX` (Traktuj ostrzeżenia konsolidatora jak błędy) — opcja konsolidatora został udokumentowany.

### <a name="new-linker-utility-features"></a>Nowe funkcje narzędzi konsolidatora

- `/ALLOWISOLATION` Dodano — opcja polecenia editbin
- Instrukcja plik definicji modułu opis zostanie usunięta. Konsolidator nie obsługuje już tworzenia sterowniki urządzeń wirtualnych.
- `/ERRORREPORT` dodano opcję bscmake.exe dumpbin.exe, editbin.exe oraz lib.exe.
- `/LTCG` lib — opcja został dodany.
- `/NXCOMPAT` — opcja polecenia editbin został dodany.
- `/RANGE` opcja polecenia dumpbin został dodany.
- `/TLS` opcja polecenia dumpbin został dodany.
- `/WS` opcja polecenia editbin została usunięta. `/WS` został użyty do modyfikowania obrazów przeznaczony dla systemu Windows NT 4.0. IMAGECFG.exe, nazwa_pliku -R można użyć zamiast `/WS`. IMAGECFG.exe znajduje się na dysku CD z systemu Windows NT 4.0 w SUPPORT\DEBUG\I386\IMAGECFG. PLIK EXE.
- /WX [: NO] została dodana opcja lib.

### <a name="new-nmake-features"></a>Nowe funkcje w NMAKE

- `/ERRORREPORT` został dodany.
- `/G` został dodany.
- Wstępnie zdefiniowane zasady zostały zaktualizowane.
- Makra $(MAKE), która jest udokumentowany w makra rekursji, teraz umożliwia pełną ścieżkę do nmake.exe.

### <a name="new-masm-features"></a>Nowe funkcje MASM

- Wyrażenia MASM są teraz wartości 64-bitowe. W poprzednich wersjach MASM wyrażenia były wartości 32-bitowe.
- Int __asm instrukcji 3 powoduje teraz funkcję, która ma zostać skompilowana do natywnego.
- ALIAS (MASM) został udokumentowany.
- `/ERRORREPORT` Opcja ml.exe i ml64.exe zostanie dodany.
- . FPO został udokumentowany.
- H2INC.exe nie będą dostarczane w programie Visual C++ 2005. Jeśli musisz nadal używać H2INC, należy użyć H2INC.exe z poprzedniej wersji programu Visual C++.
- imagerel — operator został dodany.
- high32 — operator został dodany.
- low32 — operator został dodany.
- ml64.exe jest wersją MASM x64 architektury. Jego składa x64 plików .asm x64 obiektu plików. Język asemblera wbudowanego nie jest obsługiwana w x64 kompilatora. Ml64.exe (x64) dodano następujące dyrektywy MASM:
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME. Ponadto, PROC — dyrektywa został zaktualizowany przy użyciu składni tylko do x64.
- Dodano mmword — dyrektywa
- `/omf` (Opcja wiersza polecenia ML.exe) oznacza teraz `/c`. ML.exe nie obsługuje łączenie OMF format obiektów.
- SEGMENT — dyrektywa teraz obsługuje dodatkowe atrybuty.
- sectionrel — operator został dodany.
- Dodano xmmword — dyrektywa

### <a name="new-crt-features"></a>Nowe funkcje CRT

- Bezpieczne wersje niektóre funkcje zostały dodane. Te funkcje obsługi błędów w lepszy sposób i wymuszać bardziej rygorystyczne kontrole dla buforów, aby zapobiec powstawaniu typowe luki w zabezpieczeniach. Nowe wersje bezpieczne są identyfikowane za pomocą **_s** sufiks.
- Istniejące mniej bezpieczne wersje wielu funkcji zostało zdeprecjonowanych. Aby wyłączyć ostrzeżeń dotyczących zakończenia obsługi, należy zdefiniować _CRT_SECURE_NO_WARNINGS.
- Wiele istniejących funkcji teraz sprawdzają poprawność swoich parametrów i wywołania nieprawidłowy parametr uchwytu, gdy przekazany nieprawidłowy parametr.
- Teraz ustawić wiele istniejących funkcji `errno` gdzie ta funkcjonalność była niedostępna przed nie.
- Typedef `errno_t` za pomocą typu Liczba całkowita został dodany. `errno_t` jest używana zawsze, gdy typ zwracany funkcji lub parametru zajmuje się kodami błędów z `errno`. `errno_t` zastępuje `errcode`.
- Funkcje zależne od ustawień regionalnych teraz mają wersje przyjmujące ustawień regionalnych jako parametr zamiast bieżących ustawień regionalnych. Te nowe funkcje mają **_l** sufiks. Do pracy z obiektami ustawień regionalnych dodano kilka nowych funkcji. Nowe funkcje obejmują `_get_current_locale`, `_create_locale` i `_free_locale`.
- Nowe funkcje zostały dodane do obsługi blokowaniem i odblokowywaniem dojścia do plików.
- `_spawn` Rodziny funkcji nie powoduje resetowania errno zero w przypadku powodzenia, tak jak w poprzednich wersjach.
- Wersje `printf` rodziny funkcji, które pozwalają na określenie kolejności, w którym są używane argumenty są dostępne.
- Unicode jest teraz obsługiwana długość tekstu formatu. Funkcja `_open` obsługuje _O_TEXTW, _O_UTF8 i _O_UTF16 atrybuty. `fopen` Obsługuje funkcję "ccs = ENCODING" metodę określania formatu Unicode.
- Nową wersję biblioteki CRT, utworzone w kodzie zarządzanym (MSIL) jest teraz dostępna i jest używany podczas kompilowania za pomocą `/clr` opcji (kompilacja języka wspólnego środowiska uruchomieniowego).
- _fileinfo — zostało usunięte.
- Domyślny rozmiar `time_t` jest teraz 64-bitowy, który rozszerza zakres `time_t` i kilka funkcji czasu się roku 3000.
- CRT obsługuje teraz ustawienia regionalne na zasadzie na wątek. Funkcja `_configthreadlocale` została dodana do obsługi tej funkcji.
- `_statusfp2` i `__control87_2` funkcje zostały dodane, aby zezwolić na dostęp do i kontrolę nad liczb zmiennoprzecinkowych słowa sterującego punktu na obu x87 i zmiennoprzecinkowego SSE2 punktu procesora.
- `_mkgmtime` i `_mkgmtime64` funkcje zostały dodane w celu zapewnienia obsługi konwersji razy (struktura tm) czas uniwersalny Greenwich (GMT).
- Wprowadzono zmiany `swprintf` i `vswprintf` lepiej są zgodne ze standardem.
- Nowy plik nagłówkowy, INTRIN. Godz., udostępnia prototypy niektóre funkcje wewnętrzne.
- `fopen` Funkcji ma teraz atrybut N.
- `_open` Funkcji ma teraz _O_NOINHERIT atrybutu.
- `atoi` Działa teraz zwraca INT_MAX i zestawy `errno` do ERANGE przy przepełnieniu. W poprzednich wersjach zachowanie przepełnienie nie została zdefiniowana.
- `printf` Rodziny zmiennoprzecinkowa obsługuje funkcje w formacie szesnastkowym, dane wyjściowe zaimplementowane zgodnie ze standardem ANSI C99 przy użyciu specyfikatorów typ formatu %a i %A.
- `printf` Rodzina obsługuje teraz rozmiar przedrostka "ll" (long long).
- `_controlfp` Funkcji został zoptymalizowany dla zapewnienia lepszej wydajności.
- Wersje debugowania niektóre funkcje zostały dodane.
- Dodano `_chgsignl` i `_cpysignl` (liczba typu double wersji).
- Dodano `_locale_t` do typu tabeli.
- Nowe makro `_countof` — makro dodane do obliczenia liczby elementów w tablicy.
- W każdym temacie funkcja została dodana z sekcji odpowiedników .NET Framework.
- Kilka funkcji ciągu jest teraz dostępna opcja obcinanie ciągów, a nie kończy się niepowodzeniem, gdy Bufory wyjściowe są zbyt małe; zobacz **_TRUNCATE**.
- `_set_se_translator` teraz wymaga użycia `/EHa` — opcja kompilatora.
- `fpos_t` jest teraz **__int64** w obszarze `/Za` (dla kodu C) i kiedy __STDC__ ręcznie ustawić (dla C++ kodu). Kiedyś **struktury**.
- _CRT_DISABLE_PERFCRIT_LOCKS może poprawić wydajność operacji We/Wy jednowątkowe programów.
- POSIX — nazwy zostały zaniechane i zastąpione nazwami zgodność ISO C++ (na przykład użyć `_getch` zamiast `getch`).
- Nowe pliki .obj opcje łącza są dostępne dla pure tryb czysty
- `_recalloc` łączy funkcje `realloc` i `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co nowego w języku C++ w Visual Studio 2003

### <a name="compiler"></a>Kompilator

- Informacje na temat sposobu uruchamiania zarządzanych rozszerzeń dla aplikacji C++ za pomocą bieżącej wersji kompilatora w oparciu poprzednią wersję środowiska uruchomieniowego.
- Rozszerzenia Managed Extensions for C++ często zadawane pytania.
- Dodano przewodnik pokazujący sposób portu istniejącego, natywnego aplikacji na potrzeby zarządzanych rozszerzeń języka C++: Przewodnik: Przenoszenie istniejących aplikacji natywnych języka C++ pod kątem współdziałania z składników .NET Framework.
- Teraz można utworzyć delegata dla metody typu wartości.
- Znacznie rozszerzono kompilatora zgodności ze standardem C++ dla Visual C++ .NET 2003.
- `/arch` — Opcja kompilatora jest dodawany.
- `/Gf` jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual C++.
- `/G7` — Opcja kompilatora jest dodawany.
- `/GS` — Opcja kompilatora zostało ulepszone, aby ułatwić ochronę zmienne lokalne bezpośrednie przekroczenia buforu.
- `/noBool` — Opcja kompilatora została usunięta. Kompilator pozwala teraz **bool** pojawiają się tylko słowo kluczowe (a nie identyfikatora,) w C++ pliku kodu źródłowego.
- **Long long** typu jest teraz dostępny jako **typedef** z **__int64** należy pamiętać, że istnieje, ale nie została jeszcze Obsługa **long long** w CRT.
- `/Zm` Teraz — opcja kompilatora określa limit alokacji pamięci prekompilowanego nagłówka.
- Wewnętrzne _InterlockedCompareExchange udokumentowany.
- Wewnętrzne _InterlockedDecrement udokumentowany.
- Wewnętrzne _InterlockedExchange udokumentowany.
- _Interlockedexchangeadd — wewnętrzne udokumentowany.
- Wewnętrzne _InterlockedIncrement udokumentowany.
- _Readwritebarrier — funkcja dodane.

### <a name="attributes"></a>Atrybuty

- `implements` Atrybut został udokumentowany.

### <a name="linker-features"></a>Funkcje konsolidatora

Dodano następujące przełączniki konsolidatora:

- / ASSEMBLYDEBUG
- / ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- / KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

. SAFESEH — dyrektywa i `/safeseh` opcji ml.exe zostały dodane.

## <a name="see-also"></a>Zobacz także

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
