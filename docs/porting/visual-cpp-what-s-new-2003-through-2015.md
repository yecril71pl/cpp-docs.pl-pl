---
title: C++ Wizualizacja&#39;, co nowego 2003 do 2015
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 1e5454e749d93a817caa9ca13553e203f96e038b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446489"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>C++ Wizualizacja&#39;, co nowego 2003 do 2015

Na tej stronie zebrano wszystkie strony "co nowego" dla wszystkich wersji wizualizacji C++ z programu visual Studio 2015 z powrotem do 2003. Te informacje są udostępniane jako wygoda w przypadku uaktualniania z wcześniejszych wersji programu Visual Studio.

> [!NOTE]
> Aby uzyskać informacje o bieżącej wersji programu Visual Studio, zobacz [co nowego w wizualizacji C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodności w C++ ](../overview/cpp-conformance-improvements.md)wizualizacji w programie Visual Studio.

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co nowego C++ w programie Visual Studio 2015

W programie Visual Studio 2015 i nowszych, ciągłe udoskonalenia zgodności kompilatora mogą czasami zmienić sposób, w jaki kompilator rozumie istniejący kod źródłowy. W takim przypadku mogą wystąpić nowe lub inne błędy podczas kompilacji, a nawet różnice w zachowaniu kodu, które wcześniej zostały skompilowane i były prawidłowo wykonywane.

Na szczęście te różnice mają niewielki lub nie wpływ na większość kodu źródłowego, a gdy kod źródłowy lub inne zmiany są konieczne w celu rozwiązania tych różnic, poprawki są zwykle małe i proste — do przodu. Dodaliśmy wiele przykładów wcześniej akceptowalnego kodu źródłowego, który może wymagać zmiany *(przed)* i poprawek w celu ich skorygowania *(po)* .

Chociaż różnice te mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają na zgodność binarną między C++ aktualizacjami wersji wizualizacji. Bardziej silna *zmiana może wpływać na zgodność* binarną, ale te rodzaje binarnych podziałów zgodności występują tylko między głównymi wersjami wizualizacji C++. Na przykład między elementami Visual C++ 2013 i Visual C++ 2015. Aby uzyskać informacje na temat istotnych zmian, które wystąpiły między elementami Visual C++ 2013 i Visual C++ 2015, zobacz temat [historia zmian wizualnych C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 1](#VS_Update1)

- [Ulepszenia zgodności w programie Visual Studio 2015 Update 2](#VS_Update2)

- [Udoskonalenia zgodności w programie Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a>Ulepszenia zgodności w programie Visual Studio 2015

- **/Zc: forScope — opcja**

   Opcja kompilatora `/Zc:forScope-` jest przestarzała i zostanie usunięta w przyszłej wersji.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Opcja została zwykle użyta w celu zezwalania na niestandardowy kod, który używa zmiennych pętli po punkcie, w którym, zgodnie ze standardem, powinny znajdować się poza zakresem. Jest to konieczne tylko w przypadku kompilowania z opcją `/Za`, ponieważ bez `/Za`, przy użyciu zmiennej pętli for po zakończeniu pętli jest zawsze dozwolone. Jeśli nie zamierzasz zachować zgodności ze standardami (na przykład jeśli Twój kod nie jest przeznaczony do pracy w innych kompilatorach), możesz wyłączyć opcję `/Za` (lub ustawić właściwość **Wyłącz rozszerzenia językowe** na wartość **nie**). Jeśli chcesz zadbać o pisanie kodu przenośnego, zgodnego ze standardami, należy ponownie napisać kod, aby był zgodny ze standardem poprzez przeniesienie deklaracji takich zmiennych do punktu poza pętlą.

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

- **Zg — opcja kompilatora.**

   Opcja kompilatora `/Zg` (Generuj prototypy funkcji) nie jest już dostępna. Ta opcja kompilatora była wcześniej przestarzała.

- Nie można już uruchamiać testów jednostkowych z C++/CLI z wiersza polecenia za pomocą MSTest. exe. Zamiast tego należy użyć VSTest. Console. exe

- **mutable — słowo kluczowe.**

   Specyfikator klasy magazynu **modyfikowalnego** nie jest już dozwolony w miejscach, w których poprzednio został skompilowany bez błędu. Teraz kompilator daje Błąd C2071 (niedozwolona Klasa magazynu). Zgodnie ze standardem, specyfikator modyfikowalny może być stosowany tylko do nazw składowych danych klasy i nie można go stosować do nazw zadeklarowanych jako const lub static i nie można go stosować do elementów członkowskich odwołania.

   Rozważmy na przykład następujący kod:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Poprzednie wersje kompilatora Microsoft C++ zaakceptowały to, ale teraz kompilator nadaje następujący błąd:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Aby naprawić ten błąd, po prostu usuń nadmiarowe słowo kluczowe **mutable** .

- **char_16_t i char32_t**

   Nie można już używać `char16_t` lub `char32_t` jako aliasów w elemencie typedef, ponieważ te typy są teraz traktowane jako wbudowane. Była wspólna dla użytkowników i autorów biblioteki w celu zdefiniowania `char16_t` i `char32_t` jako aliasów odpowiednio `uint16_t` i `uint32_t`.

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

   Aby zaktualizować kod, Usuń deklaracje **typedef** i Zmień nazwy innych identyfikatorów, które kolidują z tymi nazwami.

- **Parametry szablonu bez typu**

   Pewien kod, który obejmuje parametry szablonu bez typu, jest teraz poprawnie sprawdzony pod kątem zgodności typów, gdy podajesz jawne argumenty szablonu. Na przykład poniższy kod został skompilowany bez błędu w poprzednich wersjach programu Visual C++.

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

   Bieżący kompilator prawidłowo podaje błąd, ponieważ typ parametru szablonu nie jest zgodny z argumentem szablonu (parametr jest wskaźnikiem do składowej const, ale funkcja f nie jest stałą):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Aby rozwiązać ten błąd w kodzie, upewnij się, że typ argumentu szablonu jest zgodny z zadeklarowanym typem parametru szablonu.

- **__declspec (Wyrównaj)**

   Kompilator nie akceptuje już `__declspec(align)` w funkcjach. Ten element był zawsze ignorowany, ale teraz generuje błąd kompilatora.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracji funkcji. Ponieważ nie ma żadnego efektu, usunięcie go nie zmienia niczego.

- **Obsługa wyjątków**

   Istnieje kilka zmian w obsłudze wyjątków. Najpierw obiekty wyjątków muszą mieć możliwość kopiowania lub Movable. Poniższy kod został skompilowany w Visual Studio 2013, ale nie kompiluje się w programie Visual Studio 2015:

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

   Problem polega na tym, że Konstruktor kopiujący jest prywatny, dlatego nie można skopiować obiektu w normalnym czasie obsługi wyjątku. Ta sama zasada ma zastosowanie, gdy Konstruktor kopiujący jest zadeklarowany jako **jawny**.

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

   Aby zaktualizować swój kod, upewnij się, że Konstruktor kopiujący dla obiektu wyjątku jest publiczny i nie jest oznaczony jako **jawny**.

   Przechwycenie wyjątku przez wartość wymaga również, aby obiekt wyjątku mógł być kopiowany. Poniższy kod został skompilowany w Visual Studio 2013, ale nie kompiluje się w programie Visual Studio 2015:

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

   Możesz rozwiązać ten problem, zmieniając typ parametru dla **catch** do Reference.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Literały ciągu, po których następuje makra**

   Kompilator obsługuje teraz literały zdefiniowane przez użytkownika. W związku z tym literały ciągów, po których następuje makro bez żadnych spacji, są interpretowane jako literały zdefiniowane przez użytkownika, co może spowodować błędy lub nieoczekiwane wyniki. Na przykład w poprzednich kompilatorach pomyślnie skompilowano następujący kod:

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

   Kompilator interpretuje ten element jako literał ciągu "Hello", po którym następuje makro, które jest rozwinięte "tam", a następnie dwa literały ciągu zostały połączone w jeden. W programie Visual Studio 2015 kompilator interpretuje jako literał zdefiniowany przez użytkownika, ale ponieważ nie ma żadnego zgodnego zdefiniowanego przez użytkownika literału _x zdefiniowanego, występuje błąd.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Aby rozwiązać ten problem, Dodaj spację między literałem ciągu a makrem.

- **Sąsiadujące literały ciągu**

   Podobnie jak w poprzednim, ze względu na powiązane zmiany w analizie ciągów, sąsiadujące literały ciągu (literały ciągów szerokich lub wąskich) nie mogą być interpretowane jako jeden ciąg połączony w poprzednich wersjach C++Visaul. W programie Visual Studio 2015 musisz teraz dodać odstęp między dwoma ciągami. Na przykład należy zmienić następujący kod:

   ```cpp
    char * str = "abc""def";
   ```

   Wystarczy dodać odstęp między dwoma ciągami.

   ```cpp
    char * str = "abc" "def";
   ```

- **Umieszczanie nowych i usuwanie**

   Wprowadzono zmiany w operatorze **delete** w celu zapewnienia zgodności ze standardem c++ 14. Szczegóły zmiany standardów można znaleźć w [ C++ obszarze cofanie alokacji](https://isocpp.org/files/papers/n3778.html). Zmiany dodają postać globalnego operatora **usuwania** , który pobiera parametr size. Istotna zmiana polega na tym, że jeśli wcześniej użyto operatora **delete** z tym samym podpisem (w celu odłożenia operatora **umieszczania** ), zostanie wyświetlony błąd kompilatora (C2956, który występuje w punkcie, w którym jest używane **nowe miejsce umieszczania** ), ponieważ jest to pozycja w kodzie, gdzie kompilator próbuje zidentyfikować odpowiedni pasujący operator **delete** ).

   Funkcja `void operator delete(void *, size_t)` była operatorem **usuwania umieszczania** odpowiadającym **nowej funkcji umieszczania** `void * operator new(size_t, size_t)` w języku c++ 11. W przypadku cofnięcia alokacji o rozmiarze w języku C++ 14 ta funkcja **usuwania** jest teraz *zwykłą funkcją* cofania alokacji (operatorem **delete** globalnym). Standard wymaga, aby Jeśli użycie **położenia nowego** wyszukuje odpowiednią funkcję **usuwania** i odnajdzie zwykłą funkcję dealokacji, program jest źle sformułowany.

   Załóżmy na przykład, że kod definiuje zarówno **położenie nowe** , jak i **usuwanie położenia**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   Problem występuje z powodu dopasowania w sygnaturach funkcji między zdefiniowanym operatorem **usuwania rozmieszczenia** i nowym operatorem **usuwania** rozmiaru globalnego. Należy rozważyć, czy można użyć innego typu innego niż `size_t` dla wszystkich operatorów **umieszczania nowych** i **usuwania** .  Należy zauważyć, że typ `size_t` **typedef** jest zależny od kompilatora; jest to **element typedef** dla **niepodpisanej** liczby C++całkowitej w wizualizacji. Dobrym rozwiązaniem jest użycie typu wyliczeniowego, takiego jak:

   ```cpp
    enum class my_type : size_t {};
   ```

   Następnie Zmień definicję umieszczania **nowe** i **Usuń** , aby użyć tego typu jako drugiego argumentu zamiast `size_t`. Należy również zaktualizować wywołania **umieszczania nowej** , aby przekazać nowy typ (na przykład przy użyciu `static_cast<my_type>` do konwersji z wartości całkowitej) i zaktualizować definicję funkcji **New** i **delete** , aby wycofać dane do typu Integer. Nie musisz używać **wyliczenia** dla tego elementu; Typ klasy z elementem członkowskim `size_t` również będzie działał.

   Alternatywne rozwiązanie polega na tym, że można całkowicie wyeliminować **nowe rozmieszczenie** . Jeśli kod używa funkcji **umieszczania New** w celu zaimplementowania puli pamięci, w której argument umieszczania jest rozmiarem obiektu, który jest przydzielany lub usuwany, funkcja cofania alokacji o określonym rozmiarze może być odpowiednia do zastąpienia własnego niestandardowego kodu puli pamięci i można wycofać funkcje umieszczania i po prostu użyć własnego operatora **usuwania** dwuargumentowego zamiast funkcji umieszczania.

   Jeśli nie chcesz natychmiast aktualizować kodu, możesz przywrócić stare zachowanie przy użyciu opcji kompilatora `/Zc:sizedDealloc-`. Jeśli używasz tej opcji, funkcje **usuwania** z dwoma argumentami nie istnieją i nie spowodują konfliktu z operatorem **usuwania umieszczania** .

- **Składowe danych Union**

   Elementy członkowskie danych Unii nie mogą już mieć typów referencyjnych. Poniższy kod został pomyślnie skompilowany w Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

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

   Aby rozwiązać ten problem, Zmień typy odwołań na wskaźnik lub wartość. Zmiana typu wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola Union. Zmiana kodu na wartość spowoduje zmianę danych przechowywanych w Unii, co wpływa na inne pola, ponieważ pola w typach Unii współużytkują tę samą pamięć. W zależności od rozmiaru wartości może również zmienić rozmiar związku.

- **Anonimowe Unii**

   są teraz bardziej zgodne ze standardem. Poprzednie wersje kompilatora wygenerowały jawny Konstruktor i destruktor dla Unii anonimowych. Są one usuwane w programie Visual Studio 2015.

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

   Aby rozwiązać ten problem, należy podać własne definicje konstruktora i/lub destruktora.

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

- **Unii z anonimowymi strukturami**

   Aby zapewnić zgodność ze standardem, zachowanie środowiska uruchomieniowego zostało zmienione dla elementów członkowskich struktur anonimowych w Unii. Konstruktor dla elementów członkowskich struktury anonimowej w Unii nie jest już wywoływany niejawnie podczas tworzenia takiego związku. Ponadto destruktor dla elementów członkowskich struktury anonimowej w Unii nie jest już niejawnie wywoływany, gdy Unia wykracza poza zakres. Rozważmy następujący kod, w którym Unia U zawiera anonimową strukturę, która zawiera składową o nazwie "Structure", która ma destruktor.

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

   W Visual Studio 2013 Konstruktor dla S jest wywoływany, gdy Unia zostanie utworzona, i destruktor dla S jest wywoływany, gdy stos funkcji f zostanie oczyszczony. Jednak w programie Visual Studio 2015 Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie dotyczące zmiany tego zachowania.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Aby przywrócić oryginalne zachowanie, nadaj strukturze anonimowej nazwę. Zachowanie środowiska uruchomieniowego struktur nieanonimowych jest takie samo, niezależnie od wersji kompilatora.

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

   Alternatywnie możesz spróbować przenieść Konstruktor i destruktor do nowych funkcji i dodać wywołania tych funkcji z konstruktora i destruktora dla Unii.

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

- **Rozwiązanie szablonu**

   Wprowadzono zmiany w rozpoznawaniu nazw dla szablonów. W C++programie, podczas rozważania kandydatów do rozpoznawania nazw, może być przypadek, że jedna lub więcej nazw rozważanych jako potencjalne dopasowania tworzy wystąpienie nieprawidłowego szablonu. Te nieprawidłowe wystąpienia zwykle nie powodują błędów kompilatora, a zasada znana jako SFINAE (niepowodzenie podstawiania nie jest błędem).

   Teraz, Jeśli SFINAE wymaga kompilatora, aby utworzyć wystąpienie specjalizacji szablonu klasy, wówczas wszystkie błędy występujące w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator zignoruje takie błędy. Rozważmy na przykład następujący kod:

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

   Jeśli kompilujesz za pomocą bieżącego kompilatora, zostanie wyświetlony następujący błąd:

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

   Jest to spowodowane tym, że w punkcie pierwszego wywołania is_base_of Klasa "'D" nie została jeszcze zdefiniowana.

   W takim przypadku poprawka nie jest używana do tego typu cech, dopóki Klasa nie zostanie zdefiniowana. Jeśli przeniesiesz definicje B i D na początku pliku kodu, błąd zostanie rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność instrukcji include dla plików nagłówkowych, aby upewnić się, że wszystkie definicje klas zostały skompilowane przed użyciem nieproblematycznych szablonów.

- **Kopiuj konstruktory**

   W obu Visual Studio 2013 i w programie Visual Studio 2015 kompilator generuje Konstruktor kopiujący dla klasy, jeśli ta klasa ma zdefiniowany przez użytkownika Konstruktor przenoszący, ale nie ma zdefiniowanego przez użytkownika konstruktora kopiującego. W Dev14, ten niejawnie wygenerowany Konstruktor kopiujący jest również oznaczony jako "= Delete".

### <a name="VS_Update1"></a>Ulepszenia zgodności w programie Visual Studio 2015 Update 1

- **Prywatne wirtualne klasy bazowe i dziedziczenie pośrednie**

   Poprzednie wersje kompilatora dopuszczają klasę pochodną, aby wywoływać funkcje składowe swoich *pośrednio pochodnych* klas podstawowych `private virtual`. To stare zachowanie było nieprawidłowe i nie jest zgodne ze C++ standardem. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia błąd kompilatora C2280 w wyniku.

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

- **Przeciążony operator new i operator delete**

   Poprzednie wersje kompilatora umożliwiły **operatorowi** nienależącemu do elementu członkowskiego nowe i nieskładowe **, które mają** być zadeklarowane jako statyczne i mogą być deklarowane w przestrzeniach nazw innych niż globalna przestrzeń nazw.  To stare zachowanie spowodowało ryzyko, że program nie wywoła implementacji operatora **New** lub **delete** , który jest przeznaczony dla programisty, co skutkuje nieprawidłowym zachowaniem środowiska uruchomieniowego. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C2323 błąd kompilatora.

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

   Ponadto mimo że kompilator nie daje określonej diagnostyki, wbudowany operator new jest traktowany jako źle sformułowany.

- **Wywoływanie "operator *Type*()" (konwersja zdefiniowana przez użytkownika) dla typów nieklasowych** , które mogą być wywoływane w poprzednich wersjach kompilatora " *Typ*operatora ()", aby można było wywołać dla typów niebędących klasami, podczas ich dyskretnego ignorowania. To stare zachowanie spowodowało ryzyko pominięcia nieprawidłowego generowania kodu, co skutkuje nieprzewidywalnym zachowaniem środowiska uruchomieniowego. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C2228 błąd kompilatora.

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

- **Nadmiarowa nazwa elementu TypeName w wypracowanych specyfikatorach typu**  Poprzednie wersje kompilatora dozwolone dla elementu **TypeName** w złożonych specyfikatorach typu; kod zapisany w ten sposób jest semantycznie niepoprawny. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C3406 błąd kompilatora.

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

- **Typ odejmowania tablic z listy inicjatorów**  Poprzednie wersje kompilatora nie obsługiwały odejmowania typów tablic z listy inicjatorów. Kompilator obsługuje teraz tę formę odejmowania typu, a w rezultacie wywołania szablonów funkcji korzystających z list inicjatorów mogą teraz być niejednoznaczne lub można wybrać inne Przeciążenie niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program musi teraz jawnie określić Przeciążenie, którego zaplanowano programista.

   Gdy to nowe zachowanie powoduje rozwiązanie przeciążenia w celu uwzględnienia dodatkowego kandydata, który jest równie dobry jak kandydat historyczny, wywołanie stanie się niejednoznaczne i kompilator wystawia błąd kompilatora C2668 w wyniku.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Przykład 1: niejednoznaczne wywołanie przeciążonej funkcji (przed)

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

   Gdy to nowe zachowanie powoduje rozwiązanie przeciążenia w celu uwzględnienia dodatkowego kandydata, który jest lepszym rozwiązaniem niż kandydat historyczny, wywołanie jest rozpoznawane jednoznacznie do nowego kandydata, powodując zmianę zachowania programu, która prawdopodobnie jest inna niż programista zamierzony.

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

- **Przywracanie ostrzeżeń instrukcji switch**

   Poprzednia wersja kompilatora usunęła wcześniej istniejące ostrzeżenia dotyczące instrukcji **Switch** ; te ostrzeżenia zostały teraz przywrócone. Kompilator wystawia teraz przywrócone ostrzeżenia i ostrzeżenia związane z określonymi przypadkami (w tym przypadkiem domyślnym) są teraz wydawane w wierszu zawierającym przypadek, w którym występują problemy, a nie na ostatnim wierszu instrukcji switch. W wyniku wydawania tych ostrzeżeń w różnych wierszach niż w przeszłości ostrzeżenia poprzednio pomijane za pomocą `#pragma warning(disable:####)` mogą nie być już pomijane jako zamierzone. Aby pominąć te ostrzeżenia zgodnie z oczekiwaniami, może być konieczne przeniesienie dyrektywy `#pragma warning(disable:####)` do wiersza powyżej pierwszego potencjalnie powodującego przypadek. Poniżej znajdują się przywrócone ostrzeżenia.

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

   Przykłady innych przywróconych ostrzeżeń znajdują się w dokumentacji.

- **#include: użycie specyfikatora katalogu nadrzędnego ".." w nazwie ścieżki** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryły użycia specyfikatora katalogu nadrzędnego ".." w nazwie ścieżki `#include` dyrektyw. Kod zapisany w ten sposób jest zwykle przeznaczony do uwzględniania nagłówków istniejących poza projektem przez nieprawidłowe użycie ścieżek względnych dla projektu. To stare zachowanie polega na tym, że program może zostać skompilowany przez dołączenie innego pliku źródłowego niż programista lub ścieżki względne nie zostaną przenośne do innych środowisk kompilacji. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i generuje opcjonalne Ostrzeżenie kompilatora C4464, jeśli jest włączone.

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

   Ponadto mimo że kompilator nie zapewnia określonej diagnostyki, zalecamy również, aby specyfikator katalogu nadrzędnego ".." był używany do określania katalogów dołączania projektu.

- **#pragma Optymalizuj () wykracza poza koniec pliku nagłówkowego** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryły zmian w ustawieniach flagi optymalizacji, które wyłączają plik nagłówka w jednostce translacji. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C4426 w lokalizacji `#include`, jeśli to możliwe. To ostrzeżenie jest wysyłane tylko wtedy, gdy zmiany powodują konflikt z flagami optymalizacji ustawionymi przez argumenty wiersza polecenia do kompilatora.

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

- **Niezgodność #pragma warning (push)** i **#pragma warning (pop)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryły, że zmiany stanu `#pragma warning(push)` są sparowane ze zmianami stanu `#pragma warning(pop)` w innym pliku źródłowym, co jest rzadko zamierzone. To stare zachowanie spowodowało ryzyko, że program został skompilowany z innym zestawem ostrzeżeń włączonym od programisty, prawdopodobnie z powodu nieprawidłowego zachowania środowiska uruchomieniowego. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C5031 w lokalizacji pasujących `#pragma warning(pop)`, jeśli jest włączone. To ostrzeżenie zawiera uwagę odwołującą się do lokalizacji odpowiednich `#pragma warning(push)`.

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

   Chociaż nietypowy, kod pisany w ten sposób jest czasami celowo. Kod zapisany w ten sposób jest poufny dla zmian w kolejności `#include`. Jeśli to możliwe, zalecamy, aby pliki kodu źródłowego zarządzać stanem ostrzegawczym w sposób samodzielny.

- **Niedopasowane #pragma ostrzeżenie (push)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryły niedopasowanych zmian stanu `#pragma warning(push)` na końcu jednostki tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C5032 w lokalizacji niedopasowanych `#pragma warning(push)`, jeśli jest włączone. To ostrzeżenie jest wysyłane tylko wtedy, gdy w jednostce tłumaczenia nie występują błędy kompilacji.

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

- **Dodatkowe ostrzeżenia mogą być wydawane w wyniku ulepszonego śledzenia stanu ostrzeżenia #pragma**

   Poprzednie wersje kompilatora prześledzone `#pragma warning` zmiany stanu niewystarczającego do wystawienia wszystkich zamierzonych ostrzeżeń. To zachowanie spowodowało utworzenie ryzyka, że niektóre ostrzeżenia byłyby skutecznie pomijane w okolicznościach innych niż programista. Kompilator teraz śledzi stan `#pragma warning` bardziej niezawodnie — szczególnie powiązane ze zmianami stanu `#pragma warning` wewnątrz szablonów — i opcjonalnie wystawią nowe ostrzeżenia C5031 i C5032, które są przeznaczone do ułatwienia programistom lokalizowania niezamierzonych użycia `#pragma warning(push)` i `#pragma warning(pop)`.

   W wyniku ulepszonego `#pragma warning` śledzenia zmian stanu pojawiły się ostrzeżenia dawniej pominięte lub ostrzeżenia związane z problemami, które były wcześniej zdiagnozowane, mogą zostać wystawione.

- **Ulepszona identyfikacja nieosiągalnego kodu**

   C++Zmiany w bibliotece standardowej i lepsza możliwość wywołania funkcji wbudowanych w porównaniu z poprzednimi wersjami kompilatora mogą pozwolić kompilatorowi udowodnić, że określony kod jest teraz nieosiągalny. To nowe zachowanie może spowodować nowe i bardziej często wystawione wystąpienia ostrzeżenia C4720.

   ```Output
    warning C4720: unreachable code
   ```

   W wielu przypadkach to ostrzeżenie może zostać wystawione tylko w przypadku kompilowania z włączonymi optymalizacjami, ponieważ optymalizacje mogą zawierać więcej wywołań funkcji, wyeliminować nadmiarowy kod lub w inny sposób określić, że określony kod jest nieosiągalny. Zaobserwowano, że nowe wystąpienia ostrzeżenia C4720 często występowały w blokach **try/catch** , szczególnie w odniesieniu do użycia klasy [std:: find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

### <a name="VS_Update2"></a>Ulepszenia zgodności w programie Visual Studio 2015 Update 2

- **Dodatkowe ostrzeżenia i błędy mogą być wydawane w wyniku częściowego wsparcia dla SFINAE wyrażeń**

   Poprzednie wersje kompilatora nie przeanalizują niektórych rodzajów wyrażeń wewnątrz specyfikatorów **decltype** ze względu na brak obsługi wyrażenia SFINAE. To stare zachowanie było nieprawidłowe i nie jest zgodne ze C++ standardem. Kompilator analizuje teraz te wyrażenia i ma częściową obsługę wyrażenia SFINAE z powodu bieżących ulepszeń zgodności. W związku z tym kompilator wystawia ostrzeżenia i błędy Znalezione w wyrażeniach, których poprzednie wersje kompilatora nie zostały przeanalizowane.

   Gdy to nowe zachowanie analizuje wyrażenie **decltype** , które zawiera typ, który nie został jeszcze zadeklarowany, kompilator wystawia błąd kompilatora C2039 w wyniku.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Przykład 1: użycie niezadeklarowanego typu (przed)

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

   Gdy to nowe zachowanie analizuje wyrażenie **decltype** , które nie ma niepotrzebnego użycia słowa kluczowego **TypeName** , aby określić, że nazwa zależna jest typem, kompilator wystawia ostrzeżenia kompilatora C4346 razem z błędem kompilatora C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Przykład 2: Nazwa zależna nie jest typem (przed)

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

- `volatile` **zmienne składowe uniemożliwiają niejawnie zdefiniowanym konstruktorom i operatorom przypisania** poprzednie wersje kompilatora dozwolone klasy, która ma zmienne składowe **volatile** , mające domyślny konstruktory kopiowania/przenoszenia oraz domyślne operatory przypisania kopiowania/przenoszenia. To stare zachowanie było nieprawidłowe i nie jest zgodne ze C++ standardem. Kompilator traktuje teraz klasę, która ma zmienne składowe lotne, aby mieć nieuproszczone operatory konstrukcji i przypisania, które uniemożliwiają automatyczne generowanie domyślnych implementacji tych operatorów. Gdy taka Klasa jest członkiem Unii (lub anonimowej Unii wewnątrz klasy), konstruktory kopiowania/przenoszenia oraz operatory przypisania kopiowania/przenoszenia Unii (lub klasy zawierającej Unię unonymous) zostaną niejawnie zdefiniowane jako usunięte. Podjęto próbę skonstruowania lub skopiowania Unii (lub klasy zawierającej Unię anonimową) bez jawnego definiowania ich, a kompilator wygeneruje błąd kompilatora C2280 w wyniku.

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

- **Statyczne funkcje członkowskie nie obsługują kwalifikatorów OKS.**

   Poprzednie wersje Visual C++ 2015 dozwolone statyczne funkcje składowe mają kwalifikatory OKS. To zachowanie jest spowodowane regresją w Visual C++ 2015 i Visual C++ 2015 Update 1. Visual C++ 2013 i wcześniejsze wersje wizualne C++ odrzucają kod w ten sposób. Zachowanie programów Visual C++ 2015 i Visual C++ 2015 Update 1 jest nieprawidłowe i nie jest zgodne ze C++ standardem.  Program Visual Studio 2015 Update 2 odrzuca kod zapisany w ten sposób i wystawia C2511 błąd kompilatora.

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

- **Deklaracja "forward" wyliczenia jest niedozwolona w kodzie WinRT** (dotyczy tylko `/ZW`)

   Kod skompilowany dla środowisko wykonawcze systemu Windows (WinRT) nie zezwala na deklarowanie typów **wyliczeniowych** , podobnie jak w przypadku C++ kompilowania kodu zarządzanego dla programu .NET Framework przy użyciu przełącznika kompilatora `/clr`. To zachowanie zapewnia, że rozmiar wyliczenia jest zawsze znany i może być prawidłowo rzutowany na system typów WinRT. Kompilator odrzuca kod zapisany w ten sposób i wystawia błąd kompilatora C2599 razem z błędem kompilatora C3197.

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

- **Przeciążony operator, który nie jest elementem członkowskim New i operator delete nie może być zadeklarowany w tekście** (poziom 1 (`/W1`) na poziomie domyślnym)

   Poprzednie wersje kompilatora nie generują ostrzeżenia, gdy funkcje operatora Non-member **New** i **operator delete** są zadeklarowane w tekście. Kod zapisany w ten sposób jest źle sformułowany (nie jest wymagana żadna Diagnostyka) i może powodować problemy z pamięcią, które wynikają z niedopasowanych operatorów New i Delete (szczególnie w przypadku używania razem z cofnięciem alokacji rozmiaru), które mogą być trudne do zdiagnozowania. Kompilator wystawia teraz ostrzeżenia kompilatora C4595, aby ułatwić zidentyfikowanie kodu w ten sposób.

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

   Naprawianie kodu, który jest pisany w ten sposób, może wymagać, aby definicje operatora były przenoszone poza plik nagłówka i do odpowiedniego pliku źródłowego.

### <a name="VS_Update3"></a>Udoskonalenia zgodności w programie Visual Studio 2015 Update 3

- Funkcja **std:: is_convertable teraz wykrywa** poprzednie wersje `std::is_convertable`, które nie wykryły samodzielnego przypisywania typu klasy, gdy jego Konstruktor kopiujący został usunięty lub prywatny. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **false** w przypadku zastosowania do typu klasy z usuniętym lub prywatnym konstruktorem kopiującym.

   Brak diagnostyki kompilatora skojarzonej z tą zmianą.

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

   W poprzednich wersjach wizualizacji C++, statyczne potwierdzenia w dolnej części tego przykładu są **przekazywane z powodu**nieprawidłowego ustawienia `std::is_convertable<>::value`. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **wartość false**, co spowoduje niepowodzenie nieprawidłowych potwierdzeń statycznych.

- **Domyślne lub usunięte proste konstruktory kopiujące i przenoszenia respektują specyfikatory dostępu**

   Poprzednie wersje kompilatora nie sprawdzają, czy specyfikator dostępu został domyślnie usunięty, i nie usunięto konstruktorów, a następnie nie można ich wywołać. To stare zachowanie było nieprawidłowe i nie jest zgodne ze C++ standardem. W niektórych przypadkach to stare zachowanie spowodowało ryzyko pominięcia nieprawidłowego generowania kodu, co skutkuje nieprzewidywalnym zachowaniem środowiska uruchomieniowego. Kompilator sprawdzi teraz specyfikator dostępu domyślnie, a następnie usunął konstruktory, aby określić, czy można go wywołać, a jeśli nie, wystawia ostrzeżenia kompilatora C2248 w wyniku.

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

- **Przestarzała obsługa kodu ATL z atrybutami** (poziom 1 (`/W1`) na poziomie domyślnym)

   Poprzednie wersje kompilatora obsługują kod ATL z atrybutami. W następnej fazie usuwania obsługi kodu ATL z atrybutami, który [pojawił się w Visual C++ 2008](#whats-new-for-c-in-visual-studio-2008), kod ATL ma atrybut przestarzały. Kompilator wystawia teraz ostrzeżenia kompilatora C4467, aby pomóc w zidentyfikowaniu tego rodzaju przestarzałego kodu.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Aby nadal używać kodu ATL z atrybutami, dopóki nie zostanie usunięta z kompilatora, można wyłączyć to ostrzeżenie przez przekazanie argumentów wiersza polecenia `/Wv:18` lub `/wd4467` do kompilatora lub przez dodanie `#pragma warning(disable:4467)` w kodzie źródłowym.

   Przykład 1 (przed)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Przykład 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Czasami może być konieczne lub chcieć utworzyć plik IDL, aby uniknąć używania przestarzałych atrybutów ATL, jak w poniższym przykładzie kodu

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

   Najpierw utwórz plik *. idl; plik wygenerowany vc140. idl może służyć do uzyskania pliku \*. idl zawierającego interfejsy i adnotacje.

   Następnie Dodaj krok MIDL do kompilacji, aby upewnić się, że definicje C++ interfejsu są generowane.

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

   Następnie użyj biblioteki ATL bezpośrednio w pliku implementacji, jak w poniższym przykładzie kodu.

   Przykład 2 implementacji (po)

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

- **Prekompilowane pliki nagłówka (pch) i niezgodne dyrektywy #include** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowały niezgodne dyrektywy `#include` w plikach źródłowych między kompilacjami `-Yc` i `-Yu` przy użyciu prekompilowanych plików nagłówkowych (PCH). Kod zapisany w ten sposób nie jest już akceptowany przez kompilator. Kompilator emituje teraz CC4598 ostrzeżenia kompilatora, aby pomóc w zidentyfikowaniu niezgodnych dyrektyw `#include` podczas korzystania z plików PCH.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Przykład (przed):

   X. cpp (-YCC. h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z. cpp (-Yuc. h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Przykład (po)

   X. cpp (-YCC. h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z. cpp (-Yuc. h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Prekompilowany plik nagłówkowy (pch) i niezgodne katalogi dołączane** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowały niezgodne argumenty wiersza polecenia Include Directory (`-I`) do kompilatora między `-Yc` i `-Yu` kompilacjami przy użyciu prekompilowanych plików nagłówkowych (PCH). Kod zapisany w ten sposób nie jest już akceptowany przez kompilator.   Kompilator wystawia teraz ostrzeżenia kompilatora CC4599, aby ułatwić identyfikację niezgodnych argumentów wiersza polecenia Include Directory (`-I`) podczas korzystania z plików PCH.

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co nowego C++ w programie w Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Ulepszona obsługa standardówC++ ISO C/standard

#### <a name="compiler"></a>Compiler

MSVC obsługuje te funkcje języka ISO C++ 11:

- Domyślne argumenty szablonu dla szablonów funkcji.
- Delegowanie konstruktorów
- Operatory jawnej konwersji.
- Listy inicjatorów i jednolite inicjowanie.
- Surowe literały ciągu.
- Szablony wariadyczne.
- Szablony aliasów.
- Funkcje usunięte.
- Inicjatory niestatycznych elementów członkowskich danych (NSDMIs).
- Funkcje domyślne. \*
- Obsługuje te funkcje języka ISO C99:
- _Bool
- Literały złożone.
- Wyznaczono inicjatory.
- Mieszanie deklaracji z kodem.
- Konwersja literału ciągu na wartości modyfikowalne może być niedozwolona przy użyciu nowej opcji kompilatora `/Zc:strictStrings`. W języku C++ 98 konwersja z literałów ciągu do `char*` (i szerokich literałów ciągów do `wchar_t*`) była przestarzała. W języku C++ 11 konwersja została całkowicie usunięta. Chociaż kompilator może być ściśle zgodny ze standardem, zamiast tego udostępnia opcję `/Zc:strictStrings`, aby można było kontrolować konwersję. Domyślnie opcja jest wyłączona. Należy pamiętać, że w przypadku korzystania z tej opcji w trybie debugowania, STL nie zostanie skompilowany.
- Rzutowania odwołań rvalue/lvalue. Z odwołaniami rvalue C++ 11 może wyraźnie rozróżnić między lvalues i rvalues. Wcześniej kompilator nie zapewniał tego w określonych scenariuszach rzutowania. Dodano nową opcję kompilatora, `/Zc:rvalueCast`, aby kompilator zgodna z C++ językiem roboczym języka (patrz sekcja 5,4, [expr. Cast]/1). Zachowanie domyślne, gdy ta opcja nie jest określona, jest taka sama jak w programie Visual Studio 2012.

> [!NOTE]
> W przypadku funkcji domyślnych używanie wartości = Default do żądania konstruktorów przenoszenia składowych i operatorów przypisania przenoszenia nie jest obsługiwane.

### <a name="c99-libraries"></a>Biblioteki C99

Deklaracje i implementacje są dodawane dla brakujących funkcji w następujących nagłówkach: Math. h, CType. h, wctype. h, stdio. h, STDLIB. h i WCHAR. h. Dodawane są również nowe nagłówki złożone. h, stdbool. h, fenv. h i inttypes. h oraz implementacje dla wszystkich funkcji zadeklarowanych w nich. Istnieją nowe C++ nagłówki otoki (ccomplex, cfenv, cinttypes, ctgmath) i wiele innych są aktualizowane (ccomplex, cctype, CLocale, cmath, cstdint, cstdio, CString, cwchar i cwctype).

### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

Obsługa operatorów jawnej konwersji języka C++ 11, list inicjatorów, typów wyliczeniowych w zakresie i szablonów wariadyczne.
Wszystkie kontenery obsługują teraz wymagania dotyczące szczegółowych elementów języka C++ 11.
Obsługa tych funkcji języka C++ 14:

- "Transparent operatora funktory" Less < >, większe < >, plus < >, mnoży < > i tak dalej.
- make_unique\<T > (args...) i make_unique < T [] > (n)
- cbegin ()/cend (), rbegin ()/rend () i crbegin — ()/crend ().
- \<niepodzielne > otrzymały liczne ulepszenia wydajności.
- \<type_traits > otrzymały istotną stabilizację i poprawki kodu.

### <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Ta ulepszona obsługa standardów ISO CC++ /Standard może wymagać zmian w istniejącym kodzie, tak aby była zgodna z c++ 11 i była skompilowana prawidłowo w C++ wizualizacji Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Ulepszenia C++ biblioteki wizualnej

- C++Zestaw SDK REST został dodany. Ma nowoczesne C++ implementacje usług REST.
- C++Obsługa tekstury AMP jest ulepszona. Obejmuje ona teraz obsługę mipmapy i nowych trybów próbkowania.
- Zadania PPL obsługują wiele technologii planowania i debugowanie asynchroniczne. Nowe interfejsy API umożliwiają tworzenie zadań PPL zarówno dla normalnych wyników, jak i warunków wyjątków.

### <a name="c-application-performance"></a>C++Wydajność aplikacji

- Funkcja autowektoryzator teraz rozpoznaje i optymalizuje więcej C++ wzorców w celu przyspieszenia wykonywania kodu.
- Udoskonalenia jakości kodu i mikroarchitekturze platformy ARM.
- dodawana jest Konwencja wywoływania __vectorcall. Przekazanie argumentów typu Vector przy użyciu konwencji wywoływania __vectorcall, aby użyć rejestrów wektorów.
- Nowe Opcje konsolidatora. Przełączniki `/Gw` (kompilator) i `/Gy` (asembler) umożliwiają optymalizację konsolidatora w celu tworzenia plików binarnych Leaning.
- C++Obsługa pamięci współdzielonej AMP w celu zmniejszenia lub wyeliminowania kopiowania danych między procesorami CPU i procesora GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Udoskonalenia optymalizacji profilowanej (PGO)

- Poprawa wydajności z obniżki zestawu roboczego aplikacji, które są zoptymalizowane przy użyciu PGO.
- Nowe PGO dla opracowywania aplikacji środowisko wykonawcze systemu Windows.

### <a name="windows-runtime-app-development-support"></a>Obsługa programowania aplikacji środowisko wykonawcze systemu Windows

- **Obsługa typów opakowanych w strukturach wartości.**

   Można teraz definiować typy wartości przy użyciu pól, które mogą mieć wartość null, na przykład `IBox<int>^` zamiast **int**. Oznacza to, że pola mogą mieć wartość lub być równe **nullptr**.

- **Bogatsze informacje o wyjątku.**

   C++/CX obsługuje nowy model błędów systemu Windows, który umożliwia przechwytywanie i propagację zaawansowanych informacji o wyjątkach w interfejsie binarnym aplikacji (ABI); obejmuje to stosy wywołań i niestandardowe ciągi komunikatów.

- **Obiekt:: ToString () jest teraz wirtualny.**

   Teraz można przesłonić metody ToString w zdefiniowanych przez użytkownika środowisko wykonawcze systemu Windows typach referencyjnych.

- **Obsługa przestarzałych interfejsów API.**

   Publiczne środowisko wykonawcze systemu Windows interfejsów API można teraz oznaczyć jako przestarzałe i uzyskać niestandardowy komunikat, który pojawia się jako ostrzeżenie kompilacji i może zapewnić wskazówki dotyczące migracji.

- **Ulepszenia debugera.**

   Obsługa debugowania natywnego/JavaScript, środowisko wykonawcze systemu Windows diagnozy wyjątków i asynchronicznego debugowania kodu (zarówno środowisko wykonawcze systemu Windows, jak i PPL).

> [!NOTE]
> Oprócz C++specyficznych funkcji i ulepszeń, które zostały opisane w tej sekcji, inne ulepszenia programu Visual Studio mogą pomóc w zapisaniu lepszego środowisko wykonawcze systemu Windows aplikacji.

### <a name="diagnostics-enhancements"></a>Ulepszenia diagnostyki

- Ulepszenia debugera. Obsługa debugowania asynchronicznego i debugowania Tylko mój kod.
- Kategorie analizy kodu. Można teraz wyświetlać skategoryzowane dane wyjściowe z analizatora kodu, aby ułatwić znajdowanie i rozwiązywanie wad kodu.
- Diagnostyka XAML. Teraz można zdiagnozować problemy dotyczące interfejsu użytkownika i użycia baterii w kodzie XAML.
- Ulepszenia debugowania grafiki i procesora GPU.
- Zdalne przechwytywanie i odtwarzanie na rzeczywistych urządzeniach.
- Jednoczesne C++ debugowanie amp i CPU.
- Ulepszona C++ Diagnostyka środowiska uruchomieniowego amp.
- Debugowanie śledzenia cieniowania obliczeń HLSL.

### <a name="3-d-graphics-enhancements"></a>Udoskonalenia grafiki trójwymiarowej

- Obsługa potoku zawartości obrazu dla wstępnie przemnożonego formatu Alpha DDS.
- Edytor obrazów używa wewnętrznie wstępnie przemnożonego kanału alfa do renderowania i w związku z tym unika artefaktów renderowania, takich jak ciemne otoczki.
- Edytory obrazów i modeli. Tworzenie filtrów zdefiniowanych przez użytkownika jest teraz obsługiwane w projektancie cieniowania w edytorze obrazów i edytorze modelu.

### <a name="ide-and-productivity"></a>Środowisko IDE i produktywność

**Ulepszone formatowanie kodu**. Do C++ kodu można zastosować więcej ustawień formatowania. Za pomocą tych ustawień można kontrolować nowe rozmieszczenie nawiasów klamrowych i słów kluczowych, wcięcia, odstępy i zawijanie wierszy. Kod jest automatycznie formatowany po zakończeniu instrukcji i bloków, a po wklejeniu kodu do pliku.

**Uzupełnianie nawiasów klamrowych.** C++teraz trwa Autouzupełnianie znaków zamykających, które odpowiadają tym znakom otwierającym:

- {(nawias klamrowy)
- [(nawias kwadratowy)
- ((nawiasy)
- "(pojedynczy cudzysłów)
- "(cudzysłowami)

**Dodatkowe C++ funkcje automatycznego uzupełniania.**

- Dodaje średnika dla typów klas.
- Kończy nawiasy dla nieprzetworzonych literałów ciągów.
- Wykonuje Komentarze wielowierszowe (/\* \*/)

**Znajdź wszystkie odwołania** teraz automatycznie rozwiązuje i filtruje odwołania w tle po wyświetleniu listy dopasowań tekstowych.

**Filtrowanie listy elementów członkowskich opartych na kontekście.** Niedostępni członkowie są odfiltrowani z list elementów członkowskich IntelliSense. Na przykład prywatne elementy członkowskie nie są wyświetlane na liście elementów członkowskich, chyba że modyfikujesz kod implementujący typ. Gdy lista elementów członkowskich jest otwarta, możesz nacisnąć klawisz **Ctrl**+**J** , aby usunąć jeden poziom filtrowania (dotyczy tylko bieżącego okna Lista elementów członkowskich). Możesz ponownie nacisnąć klawisz **Ctrl**+**J** , aby usunąć filtrowanie tekstu i pokazać każdy element członkowski.

**Przewinięcie pomocy do parametrów.** Sygnatura funkcji wyświetlanej w etykietce narzędzia w pomocy zawiera teraz zmiany w zależności od liczby wpisanych parametrów, a nie tylko wyświetlania dowolnego podpisu i nieaktualizowania go na podstawie bieżącego kontekstu. Pomoc dotycząca parametrów również działa prawidłowo, gdy jest wyświetlana w zagnieżdżonych funkcjach.

**Przełącz nagłówek/plik kodu.** Teraz można przełączać się między nagłówkiem a odpowiadającym mu plikiem kodu przy użyciu polecenia w menu skrótów lub skrótu klawiaturowego.

**Okno właściwości C++ projektu o zmiennym rozmiarze**

**Automatyczne generowanie kodu programu obsługi zdarzeń w C++/CX i/CLI. C++**  Gdy wpisujesz kod, aby dodać procedurę obsługi zdarzeń w pliku z C++kodem/CX C++lub/CLI, Edytor może automatycznie generować wystąpienie delegata i definicję programu obsługi zdarzeń. Zostanie wyświetlone okno etykietki narzędzi, gdy można automatycznie wygenerować kod programu obsługi zdarzeń.

**Zwiększenie świadomości rozdzielczości DPI.** Ustawienie rozdzielczości DPI plików manifestu aplikacji obsługuje teraz ustawienie "na monitor o wysokiej rozdzielczości DPI".

**Szybsze przełączanie konfiguracji.** W przypadku dużych aplikacji przełączanie konfiguracji — szczególnie kolejne operacje przełączania — wykonuj dużo więcej.

**Efektywność czasu kompilacji.** Liczne optymalizacje i użycie z wieloma rdzeniami sprawiają szybsze kompilacje, szczególnie w przypadku dużych projektów. Kompilacje przyrostowe dla C++ aplikacji, które C++ mają odwołania do winmd, są również znacznie szybsze.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co nowego C++ w programie Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Ulepszona obsługa standardów języka C++ 11

#### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

- Obsługa nowych nagłówków STL: \<niepodzielne >, \<Chrono >, \<condition_variable >, \<systemu plików > \<przyszłe >, \<> muteksy, \<współczynnik > i \<> wątku.
- Aby zoptymalizować użycie zasobów pamięci, kontenery są teraz mniejsze. Na przykład w trybie wersji x86 z ustawieniami domyślnymi `std::vector` został zmniejszony z 16 bajtów w programie Visual Studio 2010 do 12 bajtów w programie Visual Studio 2012 i `std::map` został zmniejszony z 16 bajtów w programie Visual Studio 2010 do 8 bajtów w programie Visual Studio 2012.
- Zgodnie z dozwolonymi, ale nie wymaganymi przez standard C++ 11, implementacje SCARY zostały zaimplementowane.

#### <a name="other-c11-enhancements"></a>Inne ulepszenia języka C++ 11

- Pętle oparte na zakresie. Można napisać bardziej niezawodne pętle, które współpracują z tablicami, kontenerami STL i kolekcjami środowisko wykonawcze systemu Windows w formie (dla deklaracji zakresu: wyrażenie). Jest to część podstawowej obsługi języka.
- Bezstanowe wyrażenia lambda, które są blokami kodu, które zaczynają się od pustego znaku lambda [] i nie przechwytują zmiennych lokalnych, są teraz niejawnie konwertowane na wskaźniki funkcji, zgodnie z wymaganiami standardu C++ 11.
- Obsługa wyliczeń w zakresie. Klucz C++ wyliczenia klasy wyliczeniowej jest teraz obsługiwany. Poniższy kod ilustruje sposób, w jaki ten klucz enum różni się od zachowania poprzedniego wyliczenia.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Obsługa programowania aplikacji środowisko wykonawcze systemu Windows

- **Natywny model interfejsu użytkownika oparty na języku XAML**. W przypadku aplikacji środowisko wykonawcze systemu Windows można użyć nowego natywnego modelu interfejsu użytkownika opartego na języku XAML.
- **Rozszerzenia C++ składników wizualnych**. Te rozszerzenia upraszczają korzystanie z środowisko wykonawcze systemu Windows obiektów, które są niezbędne do środowisko wykonawcze systemu Windows aplikacji. Aby uzyskać więcej informacji, zobacz [Plan for środowisko wykonawcze systemu Windows Apps C++ using](../cppcx/universal-windows-apps-cpp.md) i [Visual C++ Language ReferenceC++(/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Gry DirectX**. Możesz tworzyć interesujące gry, korzystając z nowej obsługi DirectX dla środowisko wykonawcze systemu Windows aplikacji.
- **Międzyoperacyjność XAML/DirectX**. Środowisko wykonawcze systemu Windows aplikacje, które używają jednocześnie programów XAML i DirectX, współdziałają wydajnie.
- **Środowisko wykonawcze systemu Windows tworzenia bibliotek DLL składników**. Tworzenie bibliotek DLL składników sprawia, że środowisko środowisko wykonawcze systemu Windows jest rozszerzalne.

### <a name="compiler-and-linker"></a>Kompilator i konsolidator

- **Autowektoryzator**. Kompilator analizuje pętle w kodzie i, jeśli to możliwe, emituje instrukcje korzystające z rejestrów wektorowych i instrukcji, które są obecne we wszystkich nowoczesnych procesorach. Powoduje to szybsze działanie pętli. (Instrukcje procesora są znane jako SSE, dla Streaming SIMD Extensions). Nie musisz włączać ani żądać tej optymalizacji, ponieważ jest ona stosowana automatycznie.
- **Autoparalelizacji**. Kompilator może analizować pętle w kodzie i emitować instrukcje, które rozdzielają obliczenia na wiele rdzeni lub procesorów. Może to spowodować szybsze działanie pętli. Musisz zażądać tej optymalizacji, ponieważ nie jest ona domyślnie włączona. W wielu przypadkach pomocne jest uwzględnienie `#pragma loop(hint_parallel(N))` w kodzie bezpośrednio przed pętlami, które mają być równoległe.
- Funkcja autowektoryzator i autoparalelizacji może współdziałać ze sobą, aby obliczenia były rozłożone na wiele rdzeni, a kod na każdym rdzeniu używa jego rejestrów wektorów.

### <a name="new-in-visual-studio-2012-update-1"></a>Nowość w programie Visual Studio 2012 Update 1

Docelowa wersja systemu Windows XP C++ podczas kompilowania kodu.
Do systemu Windows XP i C++ windows Server 2003 można użyć kompilatora i bibliotek firmy Microsoft.

#### <a name="parallel-programming-support"></a>Obsługa programowania równoległego

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++AMP przyspiesza wykonywanie C++ kodu przez skorzystanie ze sprzętu równoległego danych, który jest zwykle obecny jako procesor GPU na dyskretnej karcie graficznej. Model C++ programowania amp obejmuje tablice wielowymiarowe, indeksowanie, transfer pamięci, fragmentację i bibliotekę funkcji matematycznych. Korzystając C++ z rozszerzeń języków amp i ograniczeń kompilatora, można kontrolować sposób przenoszenia danych z procesora CPU do procesora GPU i z powrotem.

**Debugera.** Środowisko debugowania dla aplikacji korzystających C++ z funkcji amp do kierowania procesora GPU jest podobne do debugowania dla C++ innych aplikacji. Obejmuje to nowe dodatki debugowania równoległego, które zostały wymienione wcześniej.

**Profil.** Obecnie istnieje możliwość profilowania obsługi aktywności procesora GPU, która jest oparta C++ na modelach programowania opartych na technologii Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Ogólne ulepszenia programowania równoległego

Po przeniesieniu sprzętu na wielordzeniowe i wielordzeniowe architektury deweloperzy nie mogą już korzystać z ciągle rosnących szybkości zegara z jednego rdzenia. Obsługa programowania równoległego w środowisko uruchomieniowe współbieżności umożliwia deweloperom korzystanie z tych nowych architektur.
W programie Visual Studio 2010 wprowadzono C++ zaawansowane biblioteki przetwarzanie równoległe, takie jak Biblioteka wzorców równoległych, a także funkcje umożliwiające korzystanie z współbieżności przez wyznaczanie zaawansowanych potoków przepływu danych. W programie Visual Studio 2012 te biblioteki zostały rozszerzone, aby zapewnić lepszą wydajność, większą kontrolę i bogatszą obsługę wzorców równoległych, których deweloperzy potrzebują. Szerokość oferty obejmuje teraz:

- Bogaty oparty na zadaniach model programowania obsługujący asynchroniczności i kontynuacje.
- Algorytmy równoległe, które obsługują równoległość przyłączania (parallel_for, parallel_for z koligacją, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Kontenery bezpieczne z współbieżnością, które zapewniają bezpieczne dla wątków wersje STD danych, takie jak priority_queue, Queue, Vector i map.
- Biblioteka agentów asynchronicznych, której deweloperzy mogą używać do wyrażenia przepływu danych potoków, które w naturalny sposób dzielą się na współbieżne jednostki.
- Dostosowywalny harmonogram i Menedżer zasobów, aby ułatwić płynne składanie wzorców na tej liście.

##### <a name="general-parallel-debugging-enhancements"></a>Ogólne ulepszenia debugowania równoległego

Oprócz okna **zadania równoległe** i okna **stosów równoległych** program Visual Studio 2012 oferuje nowe okno **czujki równoległej** , dzięki czemu można sprawdzać wartości wyrażenia we wszystkich wątkach i procesach, a także wykonywać sortowanie i filtrowanie w wyniku. Możesz również użyć własnych wizualizatorów, aby zwiększyć okno, i możesz skorzystać z nowej obsługi wielu procesów we wszystkich oknach narzędzi.

### <a name="ide"></a>IDE

**Obsługa szablonów programu Visual Studio.** Możesz teraz używać technologii szablonów programu Visual Studio do tworzenia C++ szablonów projektów i elementów.

**Asynchroniczne ładowanie rozwiązań.** Projekty są teraz ładowane asynchronicznie — najpierw najważniejsze części rozwiązania, dzięki czemu można szybko rozpocząć pracę.

**Zautomatyzowane wdrażanie dla zdalnego debugowania.** Wdrażanie plików dla zdalnego debugowania w wizualizacji C++ zostało uproszczone. Opcja **Wdróż** w menu kontekstowym projektu automatycznie kopiuje do komputera zdalnego pliki określone we właściwościach konfiguracji debugowania. Ręczne kopiowanie plików na komputer zdalny nie jest już wymagane.

**C++/CLI IntelliSense.** C++/CLI ma teraz pełną obsługę technologii IntelliSense. Funkcje IntelliSense, takie jak szybkie informacje, pomoc w parametrach, członkowie listy i funkcja automatycznego uzupełniania, działają teraz w przypadku C++/CLI. Ponadto inne udoskonalenia funkcji IntelliSense i środowiska IDE wymienione w tym dokumencie również działają dla C++/CLI.

**Bogatsze etykietki narzędzi IntelliSense.** C++Etykietki narzędzi funkcji IntelliSense Quick info teraz wyświetlają bogatsze informacje o stylu dokumentacji XML. Jeśli używasz interfejsu API z biblioteki — na przykład C++ amp — zawierającego komentarze dokumentacji XML, wówczas etykietka narzędzia IntelliSense zawiera więcej informacji niż tylko deklaracja. Ponadto, jeśli kod zawiera komentarze dokumentacji XML, etykietki narzędzi IntelliSense będą zawierać bogatsze informacje.

**C++Konstrukcje kodu.** Kod szkieletu jest dostępny dla przełącznika, if-else, pętli i innych podstawowych konstrukcji kodu, z listy rozwijanej listy członków. Wybierz fragment kodu z listy, aby wstawić go do kodu, a następnie wypełnij wymaganą logikę. Możesz również utworzyć własne niestandardowe fragmenty kodu do użycia w edytorze.

**Udoskonalenia listy członków.** Lista rozwijana **członków listy** jest wyświetlana automatycznie podczas wpisywania kodu w edytorze kodu. Wyniki są filtrowane, dzięki czemu podczas pisania są wyświetlane tylko odpowiednie elementy członkowskie. Można kontrolować rodzaj logiki filtrowania używanej przez listę elementów członkowskich — w oknie dialogowym **Opcje** w obszarze **Edytor tekstu** > **C++ C/**  > **Advanced**.

**Kolorowanie semantyczne.** Typy, wyliczenia, makra i inne C++ tokeny teraz domyślnie mają kolorowanie.

**Wyróżnianie odwołań.** Wybranie symbolu spowoduje teraz wyróżnienie wszystkich wystąpień symbolu w bieżącym pliku. Naciśnij **klawisze Ctrl**+**SHIFT**+**strzałka w górę** lub **Ctrl**+**SHIFT**+**strzałkę w dół** , aby przejść między wyróżnionymi odwołaniami. Tę funkcję można wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu** > **C++ C/**  > **Advanced**.

### <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

#### <a name="static-code-analysis"></a>Statyczna analiza kodu

Analiza statyczna C++ dla programu została zaktualizowana w celu zapewnienia bardziej szczegółowych informacji kontekstu błędów, większej liczby reguł analizy i lepszych wyników analizy. W nowym oknie analizy kodu można filtrować wiadomości według słów kluczowych, projektu i ważności. Po wybraniu komunikatu w oknie, wiersz w kodzie, w którym wiadomość została wyzwolona, jest wyróżniony w edytorze kodu. W przypadku C++ niektórych ostrzeżeń komunikat zawiera listę wierszy źródłowych pokazujących ścieżkę wykonywania prowadzącą do ostrzeżenia; punkty decyzyjne i powody podjęcia tej konkretnej ścieżki są wyróżnione.
Analiza kodu jest zawarta w większości wydań programu Visual Studio 2012. W wersjach Professional, Premium i Ultimate są uwzględniane wszystkie reguły. W wersjach Express dla systemu Windows 8 i Windows Phone są uwzględniane tylko najważniejsze ostrzeżenia. Analiza kodu nie jest zawarta w wersji Express dla sieci Web.
Oto kilka innych ulepszeń analizy kodu:

- Nowe ostrzeżenia współbieżności pomagają uniknąć błędów współbieżności, upewniając się, że używasz właściwych dyscyplin blokowania w wielowątkowych C/C++ programach. Analizator wykrywa potencjalne sytuacje wyścigu, niezgodności z kolejnością blokowania, wywoływanie i blokowanie naruszeń kontraktu, niezgodne operacje synchronizacji i inne usterki współbieżności.
- Można określić C++ reguły, które mają być stosowane do analizy kodu, przy użyciu zestawów reguł.
- W oknie **Analiza kodu** można wstawić do kodu źródłowego pragma, która pomija wybrane ostrzeżenie.
- Można zwiększyć dokładność i kompletność analizy kodu statycznego za pomocą nowej wersji języka adnotacji kodu źródłowego firmy Microsoft (SAL) do opisywania, w jaki sposób funkcja używa swoich parametrów, przyjętych przez niego założeń i gwarantuje, że Po zakończeniu.
- Obsługa projektów 64 C++ -bitowych.

#### <a name="updated-unit-test-framework"></a>Zaktualizowana struktura testów jednostkowych

Użyj nowej C++ struktury testów jednostkowych w programie Visual Studio, C++ aby napisać testy jednostkowe. Dodaj nowy projekt testu jednostkowego do istniejącego C++ rozwiązania, lokalizując szablon projektu C++ test jednostkowy w kategorii wizualizacji C++ w oknie dialogowym Nowy projekt. Zacznij pisać testy jednostkowe w wygenerowanej TEST_METHOD kodzie zastępczym w pliku UnitTest1. cpp. Po napisaniu kodu testowego Skompiluj rozwiązanie. Gdy chcesz uruchomić testy, Otwórz okno **Eksplorator testów jednostkowych** , wybierając opcję **Wyświetl** > innym **Eksploratorze testów jednostkowych** **systemu Windows** > , a następnie w menu skrótów dla przypadku testowego, wybierz **Uruchom wybrany test**. Po zakończeniu przebiegu testu można wyświetlić wyniki testów i dodatkowe informacje o śledzeniu stosu w tym samym oknie.

#### <a name="architecture-dependency-graphs"></a>Wykresy zależności architektury

Aby lepiej zrozumieć kod, można teraz generować wykresy zależności dla plików binarnych, klas, przestrzeni nazw i dołączać pliki w rozwiązaniu. Na pasku menu wybierz pozycję **architektura** > **Generuj wykres zależności**, a następnie **dla rozwiązania** lub **dla pliku dołączanego** , aby wygenerować wykres zależności. Po zakończeniu generowania grafu można eksplorować go przez rozwinięcie poszczególnych węzłów, poznać relacje zależności przez przechodzenie między węzłami i przeglądać kod źródłowy, wybierając opcję **Wyświetl zawartość** w menu skrótów dla węzła. Aby wygenerować wykres zależności dla plików dołączanych, w menu skrótów dla pliku kodu źródłowego \*. cpp lub pliku nagłówkowego \*. h wybierz polecenie **Generuj Graf plików dołączanych**.

#### <a name="architecture-explorer"></a>Eksplorator architektury

Korzystając z **Eksploratora architektury**, można eksplorować zasoby w C++ rozwiązaniu, projektach lub plikach. Na pasku menu wybierz **architektura** > **Windows** > **Architektura Eksploratora**. Możesz wybrać interesujący Cię węzeł, na przykład **Widok klasy**. W takim przypadku po prawej stronie okna narzędzia zostanie rozwinięta lista przestrzeni nazw. W przypadku wybrania przestrzeni nazw w nowej kolumnie zostanie wyświetlona lista klas, struktur i typów wyliczeniowych w tej przestrzeni nazw. Możesz kontynuować Eksplorowanie tych zasobów lub wrócić do kolumny po lewej stronie, aby rozpocząć kolejne zapytanie. Zobacz sekcję **Znajdowanie kodu przy użyciu Eksploratora architektury**.

#### <a name="code-coverage"></a>Pokrycie kodu

Pokrycie kodu zostało zaktualizowane do dynamicznego oprzyrządowania plików binarnych w czasie wykonywania. Zmniejsza to obciążenie związane z konfiguracją i zapewnia lepszą wydajność. Możesz również zbierać dane pokrycia kodu z testów jednostkowych dla C++ aplikacji. Po utworzeniu C++ testów jednostkowych możesz użyć **Eksploratora testów jednostkowych** , aby odnaleźć testy w rozwiązaniu. Aby uruchomić testy jednostkowe i zebrać dla nich dane pokrycia kodu, w **Eksploratorze testów jednostkowych**wybierz pozycję **Analizuj pokrycie kodu**. Wyniki pokrycia kodu można sprawdzić w oknie **wyników pokrycia kodu** — na pasku menu wybierz **Test** > **Windows** > **wyniki pokrycia kodu**.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co nowego C++ w programie Visual Studio 2010

### <a name="c-compiler-and-linker"></a>C++Kompilator i konsolidator

**Słowo kluczowe auto.** Słowo kluczowe " **Autouzupełnianie** " ma nowy cel. Użyj domyślnego znaczenia słowa kluczowego słowo **kluczowe, aby** zadeklarować zmienną, której typ jest wywnioskowany na podstawie wyrażenia inicjowania w deklaracji zmiennej. Opcja kompilatora `/Zc:auto` wywołuje nowe lub poprzednie **znaczenie słowa** kluczowego autosłowo kluczowe.

**Specyfikator typu decltype.** Specyfikator typu **decltype** zwraca typ określonego wyrażenia. Użyj specyfikatora typu **decltype** w połączeniu z słowem kluczowym autosłowo **kluczowe, aby** zadeklarować typ, który jest złożony lub znany tylko dla kompilatora. Na przykład użyj kombinacji, aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Lub Zadeklaruj funkcję szablonu, która wywołuje inną funkcję, a następnie zwraca zwracany typ wywołanej funkcji.

**Wyrażenia lambda.** Funkcje lambda mają treść funkcji, ale nie mają nazwy. Funkcje lambda łączą najlepsze cechy wskaźników funkcji i obiektów funkcyjnych. Użyj funkcji lambda, jako parametru funkcji szablonu zamiast obiektu funkcji, lub razem z słowem kluczowym autosłowo kluczowe **, aby** zadeklarować zmienną, której typem jest lambda.

**Odwołanie rvalue.** Odwołanie rvalue deklarator (& &) deklaruje odwołanie do rvalue. Odwołanie rvalue umożliwia korzystanie z semantyki przenoszenia i doskonałego przekazywania do tworzenia bardziej wydajnych konstruktorów, funkcji i szablonów.

**Deklaracja static_assert.** Deklaracja **static_assert** sprawdza poprawność oprogramowania w czasie kompilacji, w przeciwieństwie do innych mechanizmów potwierdzania, które sprawdzają się w czasie wykonywania. Jeśli potwierdzenie nie powiedzie się, kompilacja zakończy się niepowodzeniem i zostanie wystawiony określony komunikat o błędzie.

**nullptr i __nullptr słowa kluczowe.** MSVC umożliwia użycie słowa kluczowego **nullptr** z kodem natywnym lub z kodem zarządzanym. Słowo kluczowe **nullptr** wskazuje, że uchwyt obiektu, wskaźnik wewnętrzny lub typ wskaźnika natywnego nie wskazuje na obiekt. Kompilator interpretuje **nullptr** jako kod zarządzany, jeśli używasz opcji kompilatora `/clr` i kodu natywnego, jeśli nie używasz opcji `/clr`.
Słowo kluczowe **__nullptr** specyficzne dla firmy Microsoft ma takie samo znaczenie jak **nullptr**, ale ma zastosowanie tylko do kodu natywnego. Jeśli kompilujesz natywny kodC++ C/Code przy użyciu opcji kompilatora `/clr`, kompilator nie może określić, czy słowo kluczowe **nullptr** jest warunkiem natywnym, czy zarządzanym. Aby zapewnić, że zamierzone jest wyczyszczenie kompilatora, użyj słowa kluczowego nullptr, aby określić zarządzany termin, i **__nullptr** , aby określić termin macierzysty.

**/Zc: trigraphs — opcja kompilatora.** Domyślnie obsługa trigraphs jest wyłączona. Użyj opcji kompilatora `/Zc:trigraphs`, aby włączyć obsługę trigraphs.
Trójznaków składa się z dwóch następujących po sobie znaków zapytania (??), po których następuje unikatowy trzeci znak. Kompilator zastępuje trójznaków z odpowiadającym znakiem interpunkcji. Na przykład kompilator zastępuje? = trójznaków ze znakiem # (Number). Użyj trigraphs w plikach źródłowych języka C, które używają zestawu znaków, który nie zawiera niektórych znaków interpunkcyjnych.

**Nowa opcja optymalizacji z przewodnikiem.** PogoSafeMode to nowa opcja optymalizacji z przewodnikiem, która pozwala określić, czy podczas optymalizowania aplikacji używać trybu awaryjnego czy szybkiego. Tryb bezpieczny jest bezpieczny dla wątków, ale jest wolniejszy niż tryb szybki. Tryb szybki jest zachowaniem domyślnym.

**Nowa opcja środowiska uruchomieniowego języka wspólnego (CLR)/CLR: nostdlib.** Dodano nową opcję dla `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego). Jeśli są uwzględniane różne wersje tych samych bibliotek, zostanie wystawiony błąd kompilacji. Nowa opcja umożliwia wykluczenie domyślnych bibliotek CLR, aby program mógł użyć określonej wersji.

**Nowa dyrektywa pragma detect_mismatch.** Dyrektywa pragma detect_mismatch umożliwia umieszczenie znacznika w plikach, który jest porównywany z innymi tagami o tej samej nazwie. Jeśli istnieje wiele wartości o tej samej nazwie, konsolidator wystawia błąd.

**XOP wewnętrzne, wewnętrzne FMA4 i LWP wewnętrzne.** Dodano nowe funkcje wewnętrzne obsługujące wewnętrzne XOP dodane dla programu Visual Studio 2010 z dodatkiem SP1, wewnętrzne FMA4 dodane dla programu Visual Studio 2010 z dodatkiem SP1 i LWP wewnętrzne dodane dla technologii procesora programu Visual Studio 2010 SP1. Użyj __cpuid, __cpuidex, aby określić, które technologie procesora są obsługiwane na określonym komputerze.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Projekty programu C++ Visual Studio i system kompilacji

**MSBuild.** Visual C++ Solutions i projekty są teraz kompilowane przy użyciu programu MSBuild. exe, który zastępuje vcbuild. exe. Program MSBuild jest tym samym elastycznym, rozszerzalnym narzędziem do kompilacji opartym na języku XML, które jest używane przez inne języki programu Visual Studio i typy projektów. Ze względu na tę zmianę pliki C++ projektu programu Visual Studio używają teraz formatu pliku XML i mają rozszerzenie nazwy pliku. vcxproj. Pliki projektu C++ programu Visual Studio z wcześniejszych wersji programu Visual Studio są automatycznie konwertowane do nowego formatu pliku.

**Katalogi VC + +.** Ustawienia katalogów VC + + znajdują się teraz w dwóch miejscach. Strony właściwości projektu służą do ustawiania wartości dla poszczególnych projektów dla katalogów VC + +. Użyj **Menedżer właściwości** i arkusza właściwości, aby ustawić globalne wartości dla katalogów VC + +.

**Zależności między projektami.** We wcześniejszych wersjach zdefiniowane zależności między projektami były przechowywane w pliku rozwiązania. Gdy te rozwiązania są konwertowane na nowy format pliku projektu, zależności są konwertowane na odwołania między projektami. Ta zmiana może mieć wpływ na aplikacje, ponieważ koncepcje zależności rozwiązań i odwołania projektu do projektu są różne.

**Makra i zmienne środowiskowe.** Nowe makro _ITERATOR_DEBUG_LEVEL wywołuje obsługę debugowania dla iteratorów. Użyj tego makra zamiast starszych _SECURE_SCL i _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

**Biblioteki środowisko uruchomieniowe współbieżności.** Platforma środowisko uruchomieniowe współbieżności obsługuje aplikacje i składniki, które działają jednocześnie, i to platforma do programowania współbieżnych aplikacji w wizualizacji C++. W celu zapewnienia obsługi współbieżnych aplikacji Biblioteka wzorców równoległych (PPL) zawiera kontenery ogólnego przeznaczenia i algorytmy do wykonywania precyzyjnych równoległości. Biblioteka agentów asynchronicznych udostępnia model programowania oparty na aktorze i umożliwia przekazywanie interfejsów w celu uzyskania grubych zadań przepływu danych i potokowych.

**Biblioteka C++ standardowa.** Poniższa lista zawiera opis wielu zmian wprowadzonych w standardowej C++ bibliotece.

- Nowa funkcja języka referencyjnego C++ rvalue została użyta w celu zaimplementowania semantyki przenoszenia i doskonałego przekazywania dla wielu funkcji w standardowej bibliotece szablonów. Przenoszenie semantyki i doskonałe przekazywanie znacznie zwiększa wydajność operacji, które przydzielą lub przypisują zmienne lub parametry.
- Odwołania rvalue są również używane do implementowania nowej klasy `unique_ptr`, która jest bezpieczniejszym typem wskaźnika, niż Klasa `auto_ptr`. Klasa `unique_ptr` jest Movable, ale nie do kopiowania, implementuje semantykę ścisłej własności bez wpływu na bezpieczeństwo i współpracuje z kontenerami, które są świadome odwołań rvalue. Klasa `auto_ptr` jest przestarzała.
- Do nagłówka \<> dodano 15 nowych funkcji, na przykład `find_if_not`, `copy_if`i `is_sorted`.
- W nagłówku \<pamięci > Nowa funkcja make_shared jest wygodnym, niezawodnym i wydajnym sposobem, aby udostępnić wspólny wskaźnik do obiektu w tym samym czasie, gdy obiekt jest skonstruowany.
- Odrębnie połączone listy są obsługiwane przez \<forward_list > nagłówka.
- Nowe funkcje elementów członkowskich `cbegin`, `cend`, `crbegin`i `crend` `const_iterator` umożliwiają przechodzenie do przodu lub do tyłu przez kontener.
- \<system_error > nagłówka i powiązane szablony obsługują przetwarzanie błędów systemu niskiego poziomu. Elementy członkowskie klasy `exception_ptr` mogą służyć do transportowania wyjątków między wątkami.
- Nagłówek \<codecvt > obsługuje konwertowanie różnych kodowań znaków Unicode na inne kodowania.
- \<przypisania > nagłówku definiuje kilka szablonów, które ułatwiają przydzielanie i zwalnianie bloków pamięci dla kontenerów opartych na węzłach.
- Istnieje wiele aktualizacji nagłówka > losowo \<.

### <a name="microsoft-foundation-class-mfc-library"></a>Biblioteka Microsoft Foundation Class (MFC)

**Funkcje systemu Windows 7.** MFC obsługuje wiele funkcji systemu Windows 7, na przykład interfejs użytkownika wstążki (UI), pasek zadań, listy szybkiego dostępu, miniatury z kartami, podglądy miniatur, pasek postępu, nakładka ikon i indeksowanie wyszukiwania. Ponieważ MFC obsługuje automatycznie wiele funkcji systemu Windows 7, nie trzeba modyfikować istniejącej aplikacji. Aby zapewnić obsługę innych funkcji w nowych aplikacjach, należy użyć Kreatora aplikacji MFC do określenia funkcji, których chcesz użyć.

**Świadomość wielodotykowa.** MFC obsługuje aplikacje, które mają wielodotykowy interfejs użytkownika, na przykład aplikacje, które są zapisywane dla systemu operacyjnego firmy Microsoft. Aplikacja wielodotykowa może obsługiwać wiadomości touch z systemem Windows i komunikaty gestów, które są kombinacją komunikatów dotykowych. Po prostu zarejestruj aplikację pod kątem zdarzeń dotknięcia i gestu, a system operacyjny będzie kierować zdarzenia wielodotykowe do programów obsługi zdarzeń.

**Świadomość wysokiej rozdzielczości DPI.** Domyślnie aplikacje MFC są teraz o wysokiej rozdzielczości DPI. Jeśli aplikacja ma świadomość wysokiej rozdzielczości DPI (duże punkty na cal), system operacyjny może skalować okna, tekst i inne elementy interfejsu użytkownika do bieżącej rozdzielczości ekranu. Oznacza to, że obraz skalowany jest bardziej wydajny i nie jest przycinany ani pixelated.

**Uruchom ponownie Menedżera.** Menedżer ponownego uruchamiania automatycznie zapisuje dokumenty i uruchamia ponownie aplikację, jeśli zostanie nieoczekiwanie zamknięte lub ponownie uruchomione. Można na przykład użyć Menedżera ponownego uruchamiania, aby uruchomić aplikację po jej zamknięciu przez automatyczną aktualizację. Aby uzyskać więcej informacji o sposobie konfigurowania aplikacji do korzystania z Menedżera ponownego uruchamiania, zobacz **How to: Add restart Manager support**.

**Obiektu CTaskDialog.** Zamiast standardowego okna komunikatu `AfxMessageBox`, można użyć klasy `CTaskDialog`. Klasa `CTaskDialog` wyświetla i zbiera więcej informacji niż w przypadku standardowego okna komunikatów.

#### <a name="safeint-library"></a>Biblioteka SafeInt

Nowa Biblioteka SafeInt wykonuje bezpieczne operacje arytmetyczne w przypadku przepełnienia liczby całkowitej. Ta biblioteka porównuje również różne rodzaje liczb całkowitych.

#### <a name="new-active-template-library-atl-macros"></a>Nowe makra Active Template Library (ATL)

Do biblioteki ATL dodano nowe makra, które rozszerzają funkcjonalność PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE i PROP_ENTRY_INTERFACE_EX pozwalają dodać listę prawidłowych identyfikatorów CLSID. PROP_ENTRY_INTERFACE_CALLBACK i PROP_ENTRY_INTERFACE_CALLBACK_EX umożliwiają określenie funkcji wywołania zwrotnego, aby określić, czy identyfikator CLSID jest prawidłowy.

#### <a name="analyze-warnings"></a>/analyze ostrzeżenia

Większość `/analyze` (analiza kodu przedsiębiorstwa) ostrzeżeń została usunięta z bibliotek środowiska uruchomieniowego C (CRT), MFC i ATL.

#### <a name="animation-and-d2d-support"></a>Obsługa animacji i D2D

MFC obsługuje teraz animacje i Direct2D grafiki. Biblioteka MFC ma kilka nowych klas MFC i funkcji do obsługi tej funkcji. Istnieją również dwa nowe instruktaże pokazujące, jak dodać obiekt D2D i obiekt animacji do projektu. Instruktaże te są wskazówki **: Dodawanie obiektu D2D do projektu MFC** i **Przewodnik: dodawanie animacji do projektu MFC**.

### <a name="ide"></a>IDE

**Ulepszona funkcja IntelliSense.** Technologia IntelliSense dla C++ wizualizacji została całkowicie przeprojektowana w taki sposób, aby była szybsza, bardziej dokładna i możliwa do obsługi większych projektów. Aby osiągnąć to ulepszenie, środowisko IDE wykonuje rozróżnienie między widokiem dewelopera i modyfikuje kod źródłowy oraz jak środowisko IDE używa kodu źródłowego i ustawień projektu do kompilowania rozwiązania.
W związku z tym rozdzieleniem obowiązków, takich jak **Widok klasy** i nowe okno dialogowe **Przejdź do** , jest obsługiwane przez system, który jest oparty na nowym pliku SQL Server Desktop Database (SDF), który zastępuje stary plik w poszukiwaniu kompilacji (NCB). Funkcje IntelliSense, takie jak szybkie informacje, Autouzupełnianie i pomoc, przeanalizują jednostki translacji tylko wtedy, gdy jest to wymagane. Funkcje hybrydowe, takie jak nowe okno **hierarchii wywołań** , używają kombinacji funkcji przeglądania i IntelliSense.
Ponieważ technologia IntelliSense przetwarza tylko te informacje, które są w tej chwili wymagane, środowisko IDE ma więcej odpowiedzi. Ponadto ze względu na to, że informacje są bardziej aktualne, widoki i okna środowiska IDE są dokładniejsze. Na koniec, ponieważ infrastruktura IDE jest lepiej zorganizowana, bardziej wydajna i bardziej skalowalna, może obsługiwać większe projekty.

**Ulepszone błędy funkcji IntelliSense.** Środowisko IDE lepiej wykrywa błędy, które mogą spowodować utratę IntelliSense i wyświetla czerwoną falistą podkreślenie. Ponadto IDE raportuje błędy funkcji IntelliSense do **okna Lista błędów**. Aby wyświetlić kod powodujący problem, kliknij dwukrotnie błąd w **oknie Lista błędów**.

**Funkcja autouzupełniania #include.** IDE obsługuje Autouzupełnianie dla słowa kluczowego `#include`. Po wpisaniu `#include`, IDE tworzy pole listy rozwijanej prawidłowych plików nagłówkowych. Jeśli będziesz kontynuować, wpisując nazwę pliku, IDE filtruje listę na podstawie wpisu. W dowolnym momencie możesz wybrać z listy plik, który ma zostać uwzględniony. Dzięki temu można szybko dołączać pliki bez znajomości dokładnej nazwy pliku.

**Przejdź do.** Okno dialogowe **Przejdź do** umożliwia wyszukanie wszystkich symboli i plików w projekcie, które pasują do określonego ciągu. Wyniki wyszukiwania są natychmiast korygowane po wpisaniu dodatkowych znaków w ciągu wyszukiwania. Pole opinii o **wynikach** informuje o liczbie znalezionych elementów i pomaga zdecydować, czy należy ograniczyć wyszukiwanie. Pola **rodzaj/zakres**, **Lokalizacja**i informacje zwrotne w **wersji zapoznawczej** ułatwiają odróżnienie elementów mających podobne nazwy. Ponadto można zwiększyć tę funkcję w celu obsługi innych języków programowania.

**Równoległe debugowanie i profilowanie.** Debuger programu Visual Studio ma świadomość środowisko uruchomieniowe współbieżności i pomaga w rozwiązywaniu problemów z przetwarzaniem równoległym aplikacji. Możesz użyć nowego narzędzia do profilowania współbieżności, aby wizualizować ogólne zachowanie aplikacji. Ponadto można użyć nowych okien narzędzi do wizualizacji stanu zadań i ich stosów wywołań.

**Projektant wstążki.** **Projektant wstążki** jest edytorem graficznym, który umożliwia tworzenie i modyfikowanie interfejsu użytkownika wstążki MFC. Końcowy interfejs użytkownika wstążki jest reprezentowany przez plik zasobów oparty na formacie XML (. mfcribbon-ms). W przypadku istniejących aplikacji można przechwycić bieżący interfejs użytkownika wstążki, tymczasowo dodając kilka wierszy kodu, a następnie wywołując **projektanta wstążki**. Po utworzeniu pliku zasobów wstążki można zastąpić napisany ręcznie kod interfejsu użytkownika wstążki przy użyciu kilku instrukcji, które ładują zasób wstążki.

**Hierarchia wywołań.** Okno **Hierarchia wywołań** umożliwia przechodzenie do wszystkich funkcji, które są wywoływane przez określoną funkcję lub do wszystkich funkcji wywołujących konkretną funkcję.

### <a name="tools"></a>Narzędzia

**Kreator klas MFC.** Visual C++ 2010 powoduje przywrócenie dobrze uznanego narzędzia kreatora klas MFC. Kreator klas MFC jest wygodnym sposobem dodawania klas, komunikatów i zmiennych do projektu bez konieczności ręcznego modyfikowania zestawów plików źródłowych.

**Kreator kontrolki ATL.** Kreator kontrolki ATL nie wypełnia już automatycznie pola `ProgID`. Jeśli formant ATL nie ma `ProgID`, inne narzędzia mogą nie współpracować z nim. Jednym z przykładów narzędzia, które wymaga, aby formanty miały `ProgID` jest okno dialogowe **Wstawianie aktywnego formantu** . Aby uzyskać więcej informacji na temat okna dialogowego, zobacz **Wstawianie kontrolki ActiveX okno dialogowe**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

Dodanie typu danych YMMWORD obsługuje 256-bitowe argumenty operacji, które są zawarte w instrukcji Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co nowego C++ w programie Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>C++ Zintegrowane środowisko programistyczne (IDE)

- Okna dialogowe, które są tworzone w aplikacjach ATL, MFC i Win32, są teraz zgodne z wytycznymi dotyczącymi stylu systemu Windows Vista. Podczas tworzenia nowego projektu przy użyciu programu Visual Studio 2008 wszystkie okna dialogowe, które można wstawić do aplikacji, będą zgodne z wytycznymi dotyczącymi stylu systemu Windows Vista. W przypadku ponownego skompilowania projektu, który został utworzony przy użyciu wcześniejszej wersji programu Visual Studio, wszystkie istniejące okna dialogowe będą mieć taki sam wygląd jak wcześniej. Aby uzyskać więcej informacji na temat wstawiania okien dialogowych do aplikacji, zobacz **Edytor okien dialogowych**.

- Kreator **projektu ATL** ma teraz opcję rejestrowania składników dla wszystkich użytkowników. Począwszy od programu Visual Studio 2008, składniki COM i biblioteki typów, które są tworzone przez kreatora **projektu ATL** , są rejestrowane w węźle HKEY_CURRENT_USER rejestru, chyba że zostanie wybrana opcja **Zarejestruj składnik dla wszystkich użytkowników**.
- Kreator **projektu ATL** nie udostępnia już opcji tworzenia projektów ATL z atrybutami. Począwszy od programu Visual Studio 2008, Kreator **projektu ATL** nie ma opcji zmiany stanu atrybutu nowego projektu. Wszystkie nowe projekty ATL tworzone przez kreatora są teraz nieprzypisane.
- Można przekierować zapis do rejestru. Po wprowadzeniu systemu Windows Vista zapis do określonych obszarów rejestru wymaga, aby program działał w trybie podniesionych uprawnień. Nie jest wymagane, aby zawsze uruchamiać program Visual Studio w trybie podniesionych uprawnień. Przekierowanie na użytkownika automatycznie przekierowuje zapisy rejestru z HKEY_CLASSES_ROOT do HKEY_CURRENT_USER bez żadnych zmian programistycznych.
- **Projektant klas** teraz ma ograniczoną obsługę kodu natywnego C++ . We wcześniejszych wersjach programu Visual Studio **Projektant klas** działał tylko z wizualizacjami C# i Visual Basic. C++Użytkownicy mogą teraz używać **Projektant klas**, ale tylko w trybie tylko do odczytu. Aby uzyskać więcej informacji na temat korzystania z **Projektant klas** w C++programie, zobacz **Praca z C++ kodem wizualizacji w Projektant klas**.
- Kreator projektu nie ma już opcji tworzenia projektu C++ SQL Server. Począwszy od programu Visual Studio 2008, Kreator nowego projektu nie ma opcji tworzenia projektu C++ SQL Server. Projekty SQL Server utworzone przy użyciu wcześniejszej wersji programu Visual Studio będą nadal kompilowane i działały prawidłowo.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

#### <a name="general"></a>Ogólne

- Aplikacje mogą być powiązane z określonymi wersjami bibliotek wizualizacji C++ . Czasami aplikacja zależy od aktualizacji, które zostały wprowadzone do bibliotek wizualizacji C++ po wydaniu. W takim przypadku uruchomienie aplikacji na komputerze z wcześniejszymi wersjami bibliotek może spowodować nieoczekiwane zachowanie. Teraz można powiązać aplikację z określoną wersją bibliotek, dzięki czemu nie zostanie ona uruchomiona na komputerze, na którym znajduje się starsza wersja bibliotek.

#### <a name="stlclr-library"></a>Biblioteka STL/CLR

- Wizualizacja C++ zawiera teraz bibliotekę STL/CLR. Biblioteka STL/CLR jest opakowaniem standardowej biblioteki szablonów (STL), podzbiorem standardowej C++ biblioteki, do użytku z C++ i .NET Framework środowiska uruchomieniowego języka wspólnego (CLR). Za pomocą STL/CLR można teraz używać wszystkich kontenerów, iteratorów i algorytmów STL w środowisku zarządzanym.

#### <a name="mfc-library"></a>Biblioteka MFC

- System Windows Vista obsługuje typowe formanty. Ponad 150 metod w 18 nowych lub istniejących klasach zostało dodanych do obsługi funkcji w systemie Windows Vista lub w celu poprawy funkcjonalności dla bieżących klas MFC.
- Nowa Klasa `CNetAddressCtrl` umożliwia wprowadzanie i weryfikowanie adresów IPv4 i IPv6 oraz nazw DNS.
- Nowa Klasa `CPagerCtrl` upraszcza korzystanie z kontrolki pager systemu Windows.
- Nowa Klasa `CSplitButton` upraszcza użycie formantu SplitButton systemu Windows w celu wybrania domyślnej lub opcjonalnej akcji.

#### <a name="c-support-library"></a>Biblioteka obsługi języka C++

- C++wprowadza bibliotekę organizowania. Biblioteka organizowania zapewnia łatwy i zoptymalizowany sposób organizowania danych między środowiskami macierzystymi i zarządzanymi. Biblioteka jest alternatywą dla bardziej złożonych i mniej wydajnych metod, takich jak używanie funkcji PInvoke. Zobacz **Omówienie organizowania w programie C++**  , aby uzyskać więcej informacji.

#### <a name="atl-server"></a>Serwer ATL

- Serwer ATL jest wydawany jako udostępniony projekt źródłowy.
- Większość bazy kodu ATL Server została wydana jako udostępniony projekt źródłowy w programie CodePlex i nie jest zainstalowana jako część programu Visual Studio 2008. Kilka plików skojarzonych z serwerem ATL nie jest już częścią programu Visual Studio. Aby zapoznać się z listą usuniętych plików, zobacz **usunięte pliki serwera ATL**.
- Klasy kodowania i dekodowania danych z atlenc. h i funkcje narzędzi oraz klasy z atlutil. h i atlpath. h są teraz częścią biblioteki ATL.
- Firma Microsoft będzie nadal obsługiwać wersje programu ATL Server, które są zawarte we wcześniejszych wersjach programu Visual Studio, o ile te wersje programu Visual Studio są obsługiwane. CodePlex będzie kontynuował opracowywanie kodu serwera ATL jako projektu społecznościowego. Firma Microsoft nie obsługuje CodePlex wersji serwera ATL.

### <a name="visual-c-compiler-and-linker"></a>Kompilator C++ wizualny i konsolidator

#### <a name="compiler-changes"></a>Zmiany kompilatora

- Kompilator obsługuje zarządzane Kompilacje przyrostowe. Po określeniu tej opcji kompilator nie będzie ponownie kompilować kodu w przypadku zmiany zestawu, do którego się odwołuje. Zamiast tego wykona kompilację przyrostową. Pliki są ponownie kompilowane tylko wtedy, gdy zmiany wpłyną na kod zależny.
- Atrybuty powiązane z serwerem ATL nie są już obsługiwane. Kompilator nie obsługuje już kilku atrybutów, które były bezpośrednio powiązane z serwerem ATL. Aby zapoznać się z pełną listą usuniętych atrybutów, zobacz artykuł dotyczący zmiany.
- Kompilator obsługuje mikroarchitekturę Intel Core. Kompilator zawiera dostrajania dla mikroarchitektury Intel Core podczas generowania kodu. Domyślnie to dostrajanie jest włączone i nie można go wyłączyć, ponieważ ułatwia także Pentium 4 i inne procesory.
- Funkcje wewnętrzne obsługują nowsze procesory AMD i Intel. Niektóre nowe instrukcje wewnętrzne obsługują większą funkcjonalność w przypadku nowszych procesorów AMD i Intel. Aby uzyskać więcej informacji o nowych funkcjach wewnętrznych, zobacz **uzupełniające Streaming SIMD Extensions 3 instrukcje**, **Streaming SIMD Extensions 4 instrukcje**, **SSE4A i zaawansowane operacje operowania bitowym**, **wewnętrzne elementy AES**, **_mm_clmulepi64_si128**i **__rdtscp**.
- Funkcja `__cpuid` jest aktualizowana. `__cpuid`funkcja `__cpuidex` obsługuje teraz kilka nowych funkcji z najnowszych wersji procesorów AMD i Intel. `__cpuidex` wewnętrzna jest nowością i gromadzi więcej informacji z ostatnich procesorów.
- Opcja kompilatora `/MP` zmniejsza łączny czas kompilacji. Opcja `/MP` może znacząco skrócić łączny czas kompilowania kilku plików źródłowych przez utworzenie kilku procesów, które jednocześnie kompilują pliki. Ta opcja jest szczególnie przydatna na komputerach, które obsługują wielowątkowość, wiele procesorów lub wiele rdzeni.
- Opcja kompilatora `/Wp64` i słowo kluczowe **__w64** są przestarzałe. Opcja kompilatora `/Wp64` i słowo kluczowe **__w64** , które wykrywają 64-bitowe problemy z przenośnością, są przestarzałe i zostaną usunięte w przyszłej wersji kompilatora. Zamiast tej opcji kompilatora i słowa kluczowego, należy użyć MSVC, który jest przeznaczony dla platformy 64-bitowej.
- `/Qfast_transcendentals` generuje kod wbudowany dla funkcji przestępną.
- `/Qimprecise_fwaits` usuwa polecenia fwait wewnętrznie w celu wypróbowania bloków przy użyciu opcji kompilatora `/fp:except`.

### <a name="linker-changes"></a>Zmiany konsolidatora

- Informacje kontroli konta użytkownika są teraz osadzone w plikach manifestu dla plików wykonywalnych przez konsolidator C++ wizualny (link. exe). Ta funkcja jest domyślnie włączona. Aby uzyskać więcej informacji o tym, jak wyłączyć tę funkcję lub jak zmodyfikować zachowanie domyślne, zobacz `/MANIFESTUAC` (osadza informacje UAC w manifeście).
- Program łączący ma teraz opcję `/DYNAMICBASE`, aby włączyć funkcję losowego generowania układu przestrzeni adresowej w systemie Windows Vista. Ta opcja modyfikuje nagłówek pliku wykonywalnego, aby wskazać, czy aplikacja powinna być losowo zmieniona w czasie ładowania.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co nowego C++ w programie Visual Studio 2005

Następujące funkcje były Nowość w programie Visual C++ 2005 Service Pack 1:

### <a name="intrinsics-for-x86-and-x64"></a>Elementy wewnętrzne dla architektury x86 i x64

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

### <a name="intrinsics-for-x64-only"></a>Elementy wewnętrzne tylko dla architektury x64

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Nowe słowa kluczowe języka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nowe funkcje kompilatora

Kompilator ma istotne zmiany w tej wersji.

- "64-bitowe natywne i międzykompilatorowe.
- dodano opcję kompilatora `/analyze` (analiza kodu przedsiębiorstwa).
- dodano opcję kompilatora `/bigobj`.
- dodano `/clr:pure`, `/clr:safe`i `/clr:oldSyntax`. (Nowsze przestarzałe w programie Visual Studio 2015 i usunięte w programie Visual Studio 2017).
- Przestarzałe opcje kompilatora: wiele opcji kompilatora zostało przestarzałych w tej wersji. Aby uzyskać więcej informacji, zobacz **Opcje kompilatora przestarzałe** .
- Podwójna podwójnej precyzji w kodzie `/clr`. Aby uzyskać więcej informacji, zobacz **podwójny podwójna (C++)** .
- `/EH` (model obsługi wyjątków) lub `/EHs` nie może być już używany do przechwytywania wyjątku, który jest wywoływany z coś innego niż throw; Użyj `/EHa`.
- dodano opcję kompilatora `/errorReport` (zgłaszaj wewnętrzne błędy kompilatora).
- `/favor` (Optymalizacja dla 64) została dodana opcja kompilatora.
- `/FA`, dodano opcję kompilatora `/Fa` (lista plików).
- `/FC` (Pełna ścieżka pliku kodu źródłowego w diagnostyce) została dodana opcja kompilatora.
- `/fp` (Określ zachowanie zmiennoprzecinkowe) dodano opcję kompilatora.
- Opcja kompilatora `/G` (Optymalizacja dla procesora) została dodana.
- Opcja kompilatora `/G` (Optymalizacja dla procesora) została dodana.
- `/G3`, `/G4`, `/G5`, `/G6`, `/G7`i `/GB` opcje kompilatora zostały usunięte. Kompilator używa teraz "modelu mieszanego", który podejmuje próbę utworzenia najlepszego pliku wyjściowego dla wszystkich architektury.
- `/Gf` został usunięty. Zamiast tego użyj `/GF` (wyeliminować zduplikowane ciągi).
- `/GL` (Optymalizacja całego programu) jest teraz zgodna z `/CLRHEADER`.
- `/GR` jest teraz domyślnie włączona.
- `/GS` (sprawdzanie zabezpieczeń bufora) zapewnia teraz ochronę zabezpieczeń dla niechronionych parametrów wskaźnika. `/GS` jest teraz domyślnie włączona. `/GS` teraz również działa na funkcjach skompilowanych do MSIL z `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego).
- dodano opcję kompilatora `/homeparams` (Kopiuj parametry rejestru do stosu).
- dodano opcję kompilatora `/hotpatch` (Create możliwy do poprawiania Image).
- Algorytmy heurystyczne funkcji wbudowanych zostały zaktualizowane; Aby uzyskać więcej informacji, zobacz **inline**, **__inline**, **__forceinline** i **inline_depth** .
- Dodano wiele nowych funkcji wewnętrznych, a wiele wcześniej nieudokumentowanych elementów wewnętrznych zostało udokumentowane.
- Domyślnie każde wywołanie metody New, która nie powiedzie się, zgłosi wyjątek.
- Opcje kompilatora `/ML` i `/MLd` zostały usunięte. Wizualizacja C++ nie obsługuje już jednowątkowego, statycznie połączonej biblioteki CRT.
- Kompilator zaimplementował silną optymalizację wartości zwracanej, która jest włączana podczas kompilowania z `/O1`, `/O2` (Minimalizuj rozmiar, maksymalizuj szybkość), `/Og` (optymalizacje globalne) i `/Ox` (pełna optymalizacja).
- Opcja kompilatora `/Oa` została usunięta, ale zostanie zignorowana w trybie dyskretnym; Użyj modyfikatorów `noalias` lub `restrict__declspec`, aby określić sposób tworzenia aliasów przez kompilator.
- Opcja kompilatora `/Op` została usunięta. Zamiast tego użyj `/fp` (Określ zachowanie zmiennoprzecinkowe).
- Program OpenMP jest teraz obsługiwany przez C++wizualizację.
- dodano opcję kompilatora `/openmp` (Włącz obsługę OpenMP 2,0).
- Opcja kompilatora `/Ow` została usunięta, ale zostanie zignorowana w trybie dyskretnym. Użyj modyfikatorów `noalias` lub `restrict__declspec`, aby określić sposób tworzenia aliasów przez kompilator.

### <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

- `/QI0f` został usunięty.
- `/QIfdiv` został usunięty.
- `/QIPF_B` (krok Errata for B CPU) dodano opcję kompilatora.
- dodano opcję kompilatora `/QIPF_C` (Errata for C CPU).
- `/QIPF_fr32` (nie należy używać górnych rejestrów zmiennoprzecinkowych 96) — dodano opcję kompilatora.
- dodano opcję kompilatora `/QIPF_noPIC` (Generuj kod zależny od pozycji).
- `/QIPF_restrict_plabels` (założono, że nie utworzono żadnych funkcji w czasie wykonywania) opcja kompilatora została dodana.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

- `/vd` (Wyłącz przemieszczanie konstrukcji) teraz pozwala na użycie operatora dynamic_cast na skonstruowanym obiekcie (/VD2 zmieni)
- Opcja kompilatora `/YX` została usunięta. Użyj `/Yc` (Utwórz prekompilowany plik nagłówkowy) lub `/Yu` (Użyj prekompilowanego pliku nagłówkowego). Jeśli usuniesz `/YX` z konfiguracji kompilacji i zastąpisz ją bez żadnej operacji, może to skutkować szybszymi kompilacjami.
- `/Zc:forScope` jest teraz domyślnie włączona.
- `/Zc:wchar_t` jest teraz domyślnie włączona.
- Opcja kompilatora `/Zd` została usunięta. Tylko numer wiersza informacje debugowania nie są już obsługiwane. Zamiast tego użyj `/Zi` (zobacz **/Z7,/Zi,/ZI (format informacji o debugowaniu)** , aby uzyskać więcej informacji.
- `/Zg` jest teraz prawidłowy tylko dla plików kodu źródłowego języka C, a nie C++ plików kodu źródłowego.
- dodano opcję kompilatora `/Zx` (kod zoptymalizowany pod kątem debugowania).

### <a name="new-language-features"></a>Nowe funkcje języka

- Atrybutattribute jest obecnie przestarzały.
- dodano modyfikator `appdomain__declspec`.
- dodano konwencję wywoływania `__clrcall`.
- przestarzałe (C++) modyfikator **declspec** teraz pozwala określić ciąg, który będzie wyświetlany w czasie kompilacji, gdy użytkownik próbuje uzyskać dostęp do przestarzałej klasy lub funkcji.
- **dynamic_cast** Dla operatora wprowadzono istotne zmiany.
- Natywne wyliczenia umożliwiają teraz określenie typu podstawowego.
- dodano modyfikator `jitintrinsicdeclspec`.
- dodano modyfikator `noaliasdeclspec`.
- dodano modyfikator `process__declspec`.
- **abstrakcyjne**, **przesłonięcie**i **zapieczętowane** są prawidłowe dla kompilacji natywnych.
- dodano **__restrict** słowo kluczowe.
- dodano modyfikator `restrictdeclspec`.
- **__thiscall** jest teraz słowem kluczowym.
- **__unaligned** słowo kluczowe jest teraz udokumentowane.
- **volatile** (C++) zaktualizował zachowanie w odniesieniu do optymalizacji.

### <a name="new-preprocessor-features"></a>Nowe funkcje preprocesora

- Dodano wstępnie zdefiniowane makro __CLR_VER.
- Dyrektywa pragma komentarzaC++(C/) teraz akceptuje `/MANIFESTDEPENDENCY` jako komentarz konsolidatora. Opcja exestr z komentarzem jest obecnie przestarzała.
- atrybut `embedded_idl` (dyrektywa `#import`) przyjmuje teraz opcjonalny parametr.
- `fenv_access` pragma
- `float_control` pragma
- `fp_contract` pragma
- Zmienne globalne nie będą inicjowane w kolejności, w której zostały zadeklarowane, jeśli istnieją zmienne globalne w sekcjach zarządzanych, niezarządzanych i niezarządzanych. Jest to potencjalna zmiana, jeśli na przykład niezarządzana zmienna globalna zostanie zainicjowana przy użyciu zarządzanych zmiennych globalnych i jest wymagany w pełni skonstruowany obiekt zarządzany.
- Sekcje określone za pomocą init_seg są teraz tylko do odczytu i nie odczytu/zapisu tak jak w poprzednich wersjach.
- inline_depth wartość domyślna to teraz 16. W programie Visual C++ .NET 2003 wprowadzono również wartość domyślną 16.
- _INTEGRAL_MAX_BITS dodane wstępnie zdefiniowane makro, zobacz wstępnie zdefiniowane makra.
- _M_CEE, _M_CEE_PURE i _M_CEE_SAFE dodane wstępnie zdefiniowane makra Zobacz wstępnie zdefiniowane makra.
- Dodano wstępnie zdefiniowane makro _M_IX86_FP.
- Dodano wstępnie zdefiniowane makro _M_X64.
- `make_public` pragma
- `managed``unmanaged` Zaktualizowano składnię pragma (teraz ma `push` i `pop`)
- plik mscorlib. dll jest teraz niejawnie przywoływany przez dyrektywę `#using` we wszystkich kompilacjach `/clr`.
- Dodano wstępnie zdefiniowane makro _OPENMP.
- Optymalizacja dyrektywy pragma została zaktualizowana, a i w nie są już prawidłowymi parametrami.
- dodano atrybut no_registry # import.
- `region``endregion` dodano dyrektywy pragma
- Dodano wstępnie zdefiniowane makro _VC_NODEFAULTLIB.
- Makra wariadyczne są teraz zaimplementowane.
- `vtordisp` jest przestarzała i zostanie usunięta w przyszłej wersji wizualizacji C++.
- `warning` pragma zawiera teraz specyfikator pomijania.

### <a name="new-linker-features"></a>Nowe funkcje konsolidatora

- Moduły (pliki wyjściowe MSIL poza zestawem) są teraz dozwolone jako dane wejściowe dla konsolidatora.
- dodano opcję konsolidatora `/ALLOWISOLATION` (odnośnik manifestu).
- `/ASSEMBLYRESOURCE` (Osadź zarządzany zasób) został teraz zaktualizowany, aby można było określić nazwę zasobu w zestawie i określić, że zasób jest prywatny w zestawie.
- `/CLRIMAGETYPE` (Określ typ obrazu CLR) opcja konsolidatora została dodana.
- dodano `/CLRSUPPORTLASTERROR` (Zachowaj kod ostatniego błędu dla wywołań PInvoke) opcja konsolidatora została dodana.
- `/CLRTHREADATTRIBUTE` (ustaw atrybut wątku CLR) opcja konsolidatora została dodana.
- dodano opcję konsolidatora `/CLRUNMANAGEDCODECHECK` (Add SuppressUnmanagedCodeSecurityAttribute).
- dodano opcję konsolidatora `/ERRORREPORT` (zgłaszaj wewnętrzne błędy konsolidatora).
- `/EXETYPE` opcji konsolidatora została usunięta. Konsolidator nie obsługuje już tworzenia sterowników urządzeń z systemami Windows 95 i Windows 98. Użyj odpowiedniego zestawu DDK, aby utworzyć te sterowniki urządzeń. Słowo kluczowe EXETYPE nie jest już prawidłowe dla plików definicji modułu.
- dodano opcję konsolidatora `/FUNCTIONPADMIN` (Create możliwy do poprawiania Image).
- `/LTCG` opcja konsolidatora jest teraz obsługiwana w modułach skompilowanych przy użyciu `/clr`. `/LTCG` został także zaktualizowany do obsługi optymalizacji z przewodnikiem.
- `/MANIFEST` (Utwórz manifest zestawu równoległego) — opcja konsolidatora została dodana.
- dodano opcję konsolidatora `/MANIFESTDEPENDENCY` (Określ zależności manifestu).
- dodano opcję konsolidatora `/MANIFESTFILE` (Nazwa manifestu pliku).
- `/MAPINFO:LINES` opcji konsolidatora została usunięta.
- dodano opcję konsolidatora `/NXCOMPAT` (zgodna z funkcją zapobiegania wykonywaniu danych).
- `/PGD` (Określ bazę danych dla optymalizacji profilowanych) opcja konsolidatora została dodana.
- dodano opcję konsolidatora `/PROFILE` (Profiler narzędzi wydajności).
- `/SECTION` (Określ atrybuty sekcji) opcja konsolidatora obsługuje teraz negację atrybutu i nie obsługuje już atrybutów L ani D ("z VxD").
- Obsługa formatu Unicode w kompilatorze i konsolidatorze
- `/VERBOSE` (drukowanie komunikatów o postępie) opcja konsolidatora akceptuje teraz również zapory ICF i REF.
- `/VXD` opcji konsolidatora została usunięta. Konsolidator nie obsługuje już tworzenia sterowników urządzeń z systemami Windows 95 i Windows 98. Użyj odpowiedniego zestawu DDK, aby utworzyć te sterowniki urządzeń. Słowo kluczowe VXD nie jest już prawidłowe dla plików definicji modułu.
- `/WS` opcji konsolidatora została usunięta. `/WS` został użyty do modyfikacji obrazów przeznaczonych dla systemu Windows NT 4,0. IMAGECFG. exe-R filename można użyć zamiast `/WS`. IMAGECFG. exe można znaleźć na dysku CD-ROM z systemem Windows NT 4,0 w SUPPORT\DEBUG\I386\IMAGECFG. EXE.
- `/WX` (Traktuj ostrzeżenia konsolidatora jako błędy) opcja konsolidatora jest teraz udokumentowana.

### <a name="new-linker-utility-features"></a>Nowe funkcje narzędzia konsolidatora

- dodano opcję `/ALLOWISOLATION` polecenia EDITBIN
- Instrukcja pliku definicji modułu opisu jest usuwana. Konsolidator nie obsługuje już kompilowania sterowników urządzeń wirtualnych.
- Opcja `/ERRORREPORT` została dodana do BSCMAKE. exe, polecenia DUMPBIN. exe, polecenia EDITBIN. exe i lib. exe.
- dodano opcję `/LTCG` lib.
- dodano opcję `/NXCOMPAT` polecenia EDITBIN.
- dodano opcję `/RANGE` polecenia DUMPBIN.
- dodano opcję `/TLS` polecenia DUMPBIN.
- `/WS` opcji polecenia EDITBIN został usunięty. `/WS` został użyty do modyfikacji obrazów przeznaczonych dla systemu Windows NT 4,0. IMAGECFG. exe-R filename można użyć zamiast `/WS`. IMAGECFG. exe można znaleźć na dysku CD-ROM z systemem Windows NT 4,0 w SUPPORT\DEBUG\I386\IMAGECFG. EXE.
- /WX [: NO] została dodana opcja lib.

### <a name="new-nmake-features"></a>Nowe funkcje NMAKE

- `/ERRORREPORT` został dodany.
- `/G` został dodany.
- Wstępnie zdefiniowane reguły zostały zaktualizowane.
- Makro $ (MAKE), które jest udokumentowane w makrach rekursji, zapewnia teraz pełną ścieżkę do NMAKE. exe.

### <a name="new-masm-features"></a>Nowe funkcje MASM

- Wyrażenia MASM są teraz 64-bitowe wartości. W poprzednich wersjach wyrażenia MASM były 32-bitowe wartości.
- Instrukcja __asm int 3 spowoduje teraz skompilowanie funkcji do kodu natywnego.
- ALIAS (MASM) jest teraz udokumentowany.
- dodano opcję `/ERRORREPORT` ml. exe i ml64. exe.
- . FPO jest teraz udokumentowane.
- H2INC. exe nie będzie dostarczany w programie C++ Visual 2005. Jeśli musisz nadal używać H2INC, użyj H2INC. exe z poprzedniej wersji programu Visual C++.
- dodano operatora IMAGEREL.
- dodano operatora HIGH32.
- dodano operatora LOW32.
- ml64. exe jest wersją programu MASM dla architektury x64. Powoduje to umieszczenie plików x64. asm w plikach obiektów x64. Wbudowany język asemblera nie jest obsługiwany w kompilatorze x64. Dodano następujące dyrektywy MASM dla ml64. exe (x64):
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME — Ponadto dyrektywa PROC została zaktualizowana przy użyciu składni zawierającej tylko architekturę x64.
- Dodano dyrektywę MMWORD
- `/omf` (opcja wiersza polecenia ML. exe) teraz oznacza `/c`. Program ML. exe nie obsługuje łączenia obiektów OMF format.
- Dyrektywa segmentu obsługuje teraz dodatkowe atrybuty.
- dodano operatora SECTIONREL.
- Dodano dyrektywę XMMWORD

### <a name="new-crt-features"></a>Nowe funkcje CRT

- Dodano bezpieczne wersje kilku funkcji. Te funkcje obsługują błędy w lepszy sposób i wymuszają bardziej rygorystyczne kontrole buforów, aby uniknąć typowych problemów z zabezpieczeniami. Nowe bezpieczne wersje są identyfikowane za pomocą sufiksu **_s** .
- Istniejące mniej bezpieczne wersje wielu funkcji są przestarzałe. Aby wyłączyć ostrzeżenia o zaniechaniu, zdefiniuj _CRT_SECURE_NO_WARNINGS.
- Wiele istniejących funkcji teraz sprawdza poprawność swoich parametrów i wywołuje procedurę obsługi nieprawidłowego parametru podczas przekazywania nieprawidłowego parametru.
- Wiele istniejących funkcji jest teraz ustawionych `errno`, w których nie zostały wcześniej.
- Element typedef `errno_t` z typem Integer został dodany. `errno_t` jest używane za każdym razem, gdy zwracany typ lub parametr funkcji zawiera kody błędów z `errno`. `errno_t` zastępuje `errcode`.
- Funkcje zależne od ustawień regionalnych mają teraz wersje, które przyjmują ustawienia regionalne jako parametry zamiast korzystać z bieżących ustawień regionalnych. Te nowe funkcje mają sufiks **_l** . Dodano kilka nowych funkcji do pracy z obiektami regionalnymi. Nowe funkcje obejmują `_get_current_locale`, `_create_locale` i `_free_locale`.
- Dodano nowe funkcje do obsługi blokowania i odblokowywania plików.
- Rodzina funkcji `_spawn` nie resetuje errno na zero, ponieważ była w poprzednich wersjach.
- Wersje `printf`ej rodziny funkcji, które umożliwiają określenie kolejności, w której są używane argumenty są dostępne.
- Format Unicode jest teraz obsługiwanym formatem tekstowym. Funkcja `_open` obsługuje atrybuty _O_TEXTW, _O_UTF8 i _O_UTF16. Funkcja `fopen` obsługuje metodę "CCS = ENCODING" określającą format Unicode.
- Nowa wersja bibliotek CRT wbudowanych w kodzie zarządzanym (MSIL) jest teraz dostępna i jest używana podczas kompilowania z użyciem opcji `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego).
- _fileinfo został usunięty.
- Domyślny rozmiar `time_t` wynosi teraz 64 bitów, który rozszerza zakres `time_t` i kilka funkcji czasu do roku 3000.
- CRT obsługuje teraz ustawienie ustawień regionalnych dla poszczególnych wątków. `_configthreadlocale` funkcji została dodana do obsługi tej funkcji.
- Dodano funkcje `_statusfp2` i `__control87_2`, aby umożliwić dostęp do i kontrolę nad słowem kontrolki zmiennoprzecinkowej na procesorze zmiennoprzecinkowym x87 i SSE2.
- Dodano funkcje `_mkgmtime` i `_mkgmtime64`, aby zapewnić obsługę konwersji czasu (struktura TM) na czas uniwersalny Greenwich (GMT).
- Wprowadzono zmiany `swprintf` i `vswprintf` do lepszego zgodności ze standardem.
- Nowy plik nagłówka, INTRIN. H, zawiera prototypy dla niektórych funkcji wewnętrznych.
- Funkcja `fopen` ma teraz atrybut N.
- Funkcja `_open` ma teraz atrybut _O_NOINHERIT.
- Funkcja `atoi` teraz zwraca INT_MAX i ustawia `errno` na ERANGE przy przepełnieniu. W poprzednich wersjach zachowanie przepełnienia było niezdefiniowane.
- `printf` Rodzina funkcji obsługuje szesnastkowe dane wyjściowe zmiennoprzecinkowe zaimplementowane zgodnie ze standardem ANSI C99 przy użyciu specyfikatorów typu format% a i% A.
- Rodzina `printf` obsługuje teraz prefiks rozmiaru "szystkie" (long long).
- Funkcja `_controlfp` została zoptymalizowana pod kątem lepszej wydajności.
- Dodano wersje debugowania niektórych funkcji.
- Dodano `_chgsignl` i `_cpysignl` (długie podwójne wersje).
- Dodano typ `_locale_t` do tabeli Type.
- Dodano nowe makro `_countof` makro do obliczania liczby elementów w tablicy.
- W każdym temacie funkcji została dodana sekcja na .NET Framework odpowiedników.
- Kilka funkcji ciągów zawiera teraz opcję obcinania ciągów, a nie niepowodzeniem, gdy bufory wyjściowe są zbyt małe. Zobacz **_TRUNCATE**.
- `_set_se_translator` teraz wymaga użycia opcji kompilatora `/EHa`.
- `fpos_t` jest teraz **__int64** w obszarze `/Za` (dla kodu C) i gdy __STDC__ jest ustawiony ręcznie ( C++ dla kodu). Używany jako **Struktura**.
- _CRT_DISABLE_PERFCRIT_LOCKS może zwiększyć wydajność operacji we/wy programów jednowątkowych.
- Nazwy POSIX są przestarzałe na rzecz nazw zgodnych C++ ze standardem ISO (na przykład użyj `_getch`, a nie `getch`).
- Nowe opcje linku. pliki obj są dostępne dla trybu czystego
- `_recalloc` łączy funkcje `realloc` i `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co nowego C++ w programie Visual Studio 2003

### <a name="compiler"></a>Compiler

- Informacje na temat sposobu uruchamiania rozszerzeń zarządzanych dla C++ aplikacji utworzonej przy użyciu kompilatora bieżącej wersji w poprzedniej wersji środowiska uruchomieniowego.
- Zarządzane rozszerzenia dla C++ często zadawanych pytań.
- Dodano Przewodnik pokazujący, jak przenieść istniejącą aplikację natywną do korzystania z rozszerzeń zarządzanych dla C++: Przewodnik: przenoszenie istniejącej aplikacji natywnej C++ w celu współpracy ze składnikami .NET Framework.
- Teraz można utworzyć delegata dla metody typu wartości.
- Zgodność kompilatora ze C++ standardem została znacznie ulepszona dla programu Visual C++ .NET 2003.
- dodano opcję kompilatora `/arch`.
- `/Gf` jest przestarzały i zostanie usunięty w następnej wersji wizualizacji C++.
- dodano opcję kompilatora `/G7`.
- Opcja kompilatora `/GS` została ulepszona w celu ułatwienia ochrony zmiennych lokalnych przed przepełnieniem buforu bezpośredniego.
- Opcja kompilatora `/noBool` została usunięta. Kompilator umożliwia teraz, aby **bool** pojawiał się tylko jako słowo kluczowe (a nie identyfikator) w C++ pliku kodu źródłowego.
- Typ **Long Long** jest teraz dostępny jako **element typedef** **__int64** należy zwrócić uwagę, że nie jest jeszcze obsługiwane **długotrwałe** w CRT.
- Opcja kompilatora `/Zm` teraz określa limit alokacji pamięci prekompilowanego nagłówka.
- _InterlockedCompareExchange, które zostały udokumentowane wewnętrznie.
- _InterlockedDecrement, które zostały udokumentowane wewnętrznie.
- _InterlockedExchange, które zostały udokumentowane wewnętrznie.
- _InterlockedExchangeAdd, które zostały udokumentowane wewnętrznie.
- _InterlockedIncrement, które zostały udokumentowane wewnętrznie.
- _ReadWriteBarrier dodane wewnętrznie.

### <a name="attributes"></a>Atrybuty

- atrybut `implements` jest teraz udokumentowany.

### <a name="linker-features"></a>Funkcje konsolidatora

Dodano następujące przełączniki konsolidatora:

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Polu. Dodano dyrektywę SAFESEH i `/safeseh` ml. exe.

## <a name="see-also"></a>Zobacz też

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
