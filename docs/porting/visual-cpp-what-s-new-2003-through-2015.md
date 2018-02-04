---
title: "Visual C++ Co &#39; s nowe 2003 za pośrednictwem 2015 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e730d7d47a8742d3c4f1f7c4636aabd8785cc93
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co &#39; s nowe 2003 za pośrednictwem 2015

Ta strona zbiera wszystkie "What's New" strony dla wszystkich wersji programu Visual C++ z programu Visual Studio 2015 do 2003. Te informacje jest udostępniane dla wygody, w przypadku może okazać się przydatne podczas uaktualniania z wcześniejszych wersji programu Visual C++.

**Uwaga** informacji o programie Visual Studio 2017 znajduje się w temacie [nowości w języku Visual C++ w programie Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodność w programie Visual C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Nowości dla języka C++ w programie Visual Studio 2015

W programie Visual Studio 2015 lub nowszego oraz bieżące ulepszenia kompilatora zgodność czasami można zmienić sposób kompilator rozumie istniejącego kodu źródłowego. W takim przypadku nowe lub inne błędy mogą wystąpić podczas kompilacji lub nawet behawioralnej różnice w kodzie, który uprzednio utworzony i z działała poprawnie.

 Na szczęście tych różnic mają niewielkiego lub żadnego wpływu na większości kodu źródłowego i kiedy kodu źródłowego lub inne zmiany są potrzebne w celu rozwiązania tych różnic, poprawki są zwykle małe i proste. Dodaliśmy wiele przykładów kodu źródłowego wcześniej dopuszczalne, który może zaistnieć konieczność zmiany *(przed)* i poprawki, aby je poprawić *(po)*.

 Mimo że te różnice mogą wpływać na kodu źródłowego lub pozostałych artefaktów kompilacji, nie wpływają na binarne zgodność aktualizacji do wersji Visual C++. Inne poważne rodzaju zmiany, *fundamentalne zmiany* może mieć wpływ na zgodność binarną, ale tego rodzaju podziały zgodność binarną występować tylko między główne wersje programu Visual C++. Na przykład między Visual C++ 2013 i Visual C++ 2015. Informacje dotyczące zmian podziału między Visual C++ 2013 i Visual C++ 2015 znajdują się w temacie [Historia 2003 2015 zmian Visual C++](../porting/visual-cpp-change-history-2003-2015.md).

- [Ulepszenia zgodność programu Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodność w programie Visual Studio 2015 Update 1](#VS_Update1)

- [Ulepszenia zgodność w programie Visual Studio 2015 Update 2](#VS_Update2)

- [Ulepszenia zgodność w programie Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a>Ulepszenia zgodność programu Visual Studio 2015

- **Opcja /Zc:forScope-** — opcja kompilatora **/Zc:forScope-** jest przestarzała i zostanie usunięta w przyszłej wersji.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Zazwyczaj użyto opcji w celu umożliwienia niestandardowy kod, który używa zmiennych w pętli od momentu, gdy zgodnie ze standardowego, ich powinien przeszły poza zakresem. Konieczne było tylko gdy kompilacja z opcją /Za od bez /Za, za pomocą zmiennej pętli po zakończeniu pętli zawsze jest dozwolone. Jeśli nie interesują o standardach zgodności (na przykład, jeśli kod nie jest przeznaczone do przenośnych do inne kompilatory), użytkownik może wyłączyć opcję /Za (lub ustaw właściwość Wyłącz rozszerzenia języka nie). Jeśli interesują dotyczące pisania kodu przenośnego, zgodnych ze standardami, dzięki czemu jest zgodny ze standardem przenosząc deklaracji tych zmiennych do punktu poza pętli powinien ponownego zapisywania kodu.

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

- **ZG-opcja kompilatora.** Opcja kompilatora /Zg (Generuj prototypy funkcji) nie jest już dostępny. Ta opcja kompilatora wcześniej została uznana za przestarzałą.

- Nie można uruchomić testów jednostkowych z C + +/ CLI w wierszu polecenia z mstest.exe. Zamiast tego należy użyć vstest.console.exe

- **Mutable — słowo kluczowe.** `mutable` Specyfikator klasy magazynu nie jest dozwolony w miejscach, w którym, wcześniej skompilowane go bez błędów. Teraz, kompilator zapewnia błąd C2071 (niedozwolona Klasa magazynu). Zgodnie z standard specyfikator modyfikowalny mogą być stosowane tylko do nazwy klasy elementy członkowskie danych, nie można zastosować do zadeklarować jako const lub statycznej nazwy i nie można zastosować do odwołań do elementów członkowskich.

   Rozważmy na przykład następujący kod:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Poprzednie wersje kompilatora Visual C++ zaakceptowane to, ale teraz kompilator zapewnia następujący błąd:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Aby naprawić błąd, po prostu Usuń nadmiarowe mutable — słowo kluczowe.

- **char_16_t i char32_t** nie są już używane `char16_t` lub `char32_t` jako aliasów w instrukcji typedef, ponieważ te typy, teraz są traktowane jako wbudowanych. Znajdował się w przypadku użytkowników i autorów biblioteki, aby zdefiniować `char16_t` i `char32_t` jako aliasy `uint16_t` i `uint32_t`odpowiednio.

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

   Zaktualizuj kod, Usuń deklaracje typedef i Zmień nazwę innych identyfikatorów, które powodują kolizję z tych nazw.

- **Parametry szablonu bez typu** niektórych kod, który obejmuje parametrów szablonu bez typu są teraz prawidłowo sprawdzane pod kątem zgodności typu podając jawne argumenty szablonu. Na przykład następujący kod skompilowany bez błędów w poprzednich wersjach programu Visual C++.

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

   Kompilator bieżącego poprawnie zwraca błąd, ponieważ argument szablonu nie jest zgodny z typem parametru szablonu (parametr jest wskaźnik do stały element członkowski, ale funkcja f jest wartością stałą):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Aby rozwiązać ten błąd w kodzie, należy upewnić się, że typ argumentu szablonu jest zgodny z typem zadeklarowanym parametru szablonu.

- **__declspec(align)** kompilator nie będzie akceptował `__declspec(align)` na funkcje. To zawsze została zignorowana, ale teraz generuje błąd kompilatora.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracją funkcji. Ponieważ nie miał żadnego skutku, usuwając go nie zmian.

- **Obsługa wyjątków** istnieje kilka zmian do obsługi wyjątków. Po pierwsze obiekty wyjątków muszą być copyable lub przenośne. Poniższy kod skompilowany w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nie Kompiluj w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

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

   Problem jest Konstruktor kopiujący jest prywatny, więc nie można skopiować obiektu, ponieważ odbywa się w trakcie normalnego przebiegu Obsługa wyjątku. Dotyczy to Konstruktor kopiujący jest zadeklarowany jako `explicit`.

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

   Aby zaktualizować kodu, upewnij się, że Konstruktor kopiujący dla obiekt wyjątku jest publiczna i nie oznaczone `explicit`.

   Przechwytywanie wyjątku przez wartość wymaga również być copyable obiekt wyjątku. Poniższy kod skompilowany w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nie Kompiluj w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

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

   Można rozwiązać ten problem, zmieniając typ parametru `catch` do odwołania.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Literały następuje makra ciągu** kompilator obsługuje teraz literały zdefiniowanych przez użytkownika. W rezultacie następuje makra bez żadnych spacji pośredniczące literałów ciągów są interpretowane jako literały zdefiniowane przez użytkownika, które spowodują błędy lub nieoczekiwane wyniki. Na przykład w poprzednim kompilatory następujący kod powiodło:

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

   Kompilator interpretowana to jako ciąg literału "hello" następuje makra jest rozwinięta "Brak", a następnie literałów ciągów dwóch zostały połączone w jeden. W [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], kompilator interpretuje jako literału zdefiniowanego przez użytkownika, ale ponieważ nie ma żadnych pasujących zdefiniowane przez użytkownika literału _x zdefiniowane, zawiera błąd.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Aby rozwiązać ten problem, Dodaj odstęp między literałem ciągu i makra.

- **Literały ciągu sąsiadujących ze sobą** podobnie jak poprzednie, z powodu zmiany podczas analizy ciągu, literałów ciągów sąsiadujących ze sobą (albo literałów ciągów znaków szerokości lub wąskie) bez żadnych spacji zostały interpretowane jako pojedynczy ciąg połączonych w poprzednie wersje programu Visaul C++. W [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], teraz należy dodać odstępu między dwa ciągi. Na przykład można zmienić następujący kod:

   ```cpp
    char * str = "abc""def";
   ```

   Po prostu Dodaj odstęp między dwa ciągi.

   ```cpp
    char * str = "abc" "def";
   ```

- **Umieszczania nowych i delete** dokonano zmian dla operatora delete w celu dostosowania do zgodność z C ++ 14 standardowa. Szczegółowe informacje o zmianie standardów można znaleźć w folderze [cofania alokacji o rozmiarze w języku C++](http://isocpp.org/files/papers/n3778.html). Zmiany dodać formę operatora delete globalny, który przyjmuje parametr rozmiaru. Istotne zmiany jest, że jeśli zostały wcześniej za pomocą operatora delete o tej samej sygnaturze (odpowiadającą operatora new umieszczania), zostanie wyświetlony błąd kompilatora (C2956, co następuje w momencie, gdzie nowe umieszczania są używane, ponieważ to jest operator delete pozycji w kodzie, w którym kompilator podejmie próbę identyfikacji odpowiadającym odpowiednią).

   Funkcja `void operator delete(void *, size_t)` został umieszczania operatora delete, odpowiadające nowej funkcji umieszczania "void \* nowy operator (size_t, size_t)" w języku C ++ 11. Z języka C ++ 14 dezalokacji rozmiarze, ta funkcja delete jest teraz *funkcja dezalokacji zwykle* (operator delete globalne). Standard wymaga użycia nowego położenia wyszukuje odpowiedniej funkcji usuwania, znajduje się funkcja dezalokacji zwykle program źle sformułowane.

   Na przykład załóżmy, że kod definiuje zarówno nowego położenia i usuwania umieszczania:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;

   ```

   Wystąpił problem z powodu dopasowania w podpisach funkcja między umieszczania operatora delete, które zdefiniowany przez użytkownika, a nowy operator delete o rozmiarze globalnych. Należy rozważyć, czy można użyć innego typu niż size_t do dowolnego umieszczania nowych i delete — operatory.  Należy pamiętać, że typ size_t typedef zależne od kompilatora; jest typedef dla unsigned int w programie Visual C++. Dobrym rozwiązaniem jest używany typ wyliczeniowy takich jak ta:

   ```cpp
    enum class my_type : size_t {};

   ```

   Zmień definicja umieszczania nowe, a następnie, Usuń, aby użyć tego typu jako drugi argument zamiast size_t. Należy również zaktualizować wywołania do umieszczenia nowego przekazać nowy typ (na przykład za pomocą `static_cast<my_type>` do przekonwertowania z wartością całkowitą) i nowych aktualizacji definicji i Usuń można rzutować typu Liczba całkowita. Nie trzeba używać wyliczenia dla tej; Typ klasy z elementem członkowskim size_t również będzie działać.

   Alternatywnego rozwiązania jest, że można całkowicie wyeliminować umieszczania nowej. Jeśli kod używa umieszczania nowej implementacji puli pamięci, gdy argument umieszczania rozmiar jest obiekt przydzielony lub usunięty, to funkcja cofania alokacji o rozmiarze może być swoim własnym kodem puli pamięci niestandardowych zastąpienie i można pozbyć się z umieszczanie funkcje i użyć własnych operatora delete dwuargumentowej zamiast funkcji umieszczania.

   Jeśli nie chcesz natychmiast zaktualizować kodu, możesz przywrócić poprzednie działanie przy użyciu opcji kompilatora /Zc:sizedDealloc-. Jeśli używasz tej opcji, funkcje delete dwuargumentowej nie istnieje i nie powoduje konfliktu z operatorem delete umieszczania.

- **Elementy członkowskie danych Unii**

   Elementy członkowskie danych Unii nie mogą mieć typów referencyjnych. Poniższy kod skompilowany pomyślnie w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale powoduje błąd w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].

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

   Poprzedni kod tworzy następujące błędy:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Aby rozwiązać ten problem, zmień typy odwołań do wskaźnika lub wartość. Zmiana typu do wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola union. Zmiana kodu do wartości zmieniłby danych przechowywanych w Unii, który ma wpływ na inne pola, ponieważ pola w Unii mieć tej samej pamięci. W zależności od rozmiaru wartość może on również zmienić rozmiar Unii.

- **Związki anonimowe** są teraz więcej zgodność ze standardem. Poprzednie wersje kompilatora generowane jawny Konstruktor i destruktor dla elementu związki anonimowe. Są one usuwane z [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].

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

   Poprzedni kod generuje następujący błąd w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Aby rozwiązać ten problem, należy podać własne definicje Konstruktor i/lub destruktor.

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

- **Unie z anonimowego struktury** są zgodne ze standardem, w celu zachowania w czasie wykonywania została zmieniona dla elementów członkowskich struktury anonimowe w uniach. Konstruktor elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie po utworzeniu takiej Unii.   Ponadto destruktor dla elementu elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie przypadku Unii wykracza poza zakres. Rozważmy następujący kod, w którym Unii U zawiera strukturę anonimowe, zawierający element, który jest strukturą nazwanego S, która ma destruktor.

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

   W [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], Konstruktor S jest wywoływana po utworzeniu Unii, a destruktor dla elementu S jest wywoływane, gdy jest wyczyszczone stosu dla funkcji f. Jednak [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie o tej zmianie zachowanie.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Aby przywrócić oryginalne zachowanie, nadaj struktury anonimowe nazwę. Zachowanie środowiska uruchomieniowego struktur nieanonimowych jest taki sam, niezależnie od wersji kompilatora.

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

   Alternatywnie spróbuj przenieść kod Konstruktor i destruktor do nowych funkcji, a następnie dodaj wywołań funkcji z Konstruktor i destruktor dla Unii.

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

- **Szablon rozwiązania** wprowadzono zmiany do rozpoznawania nazw dla szablonów. W języku C++, rozważając kandydatów do rozpoznawania nazw można go sprawę, że jedną lub więcej nazw pod uwagę jako potencjalny dopasowań powoduje utworzenie wystąpienia szablonu jest nieprawidłowa. Te nieprawidłowe wystąpień nie powodują zwykle błędy kompilatora, zasady, znany jako techniki SFINAE (podstawienie niepowodzenia nie błąd jest).

   Teraz Jeśli techniki SFINAE wymaga kompilatora, można utworzyć wystąpienia specjalizacji szablonu klasy, wszystkie błędy w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator będzie ignorować takie błędy. Rozważmy na przykład następujący kod:

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

   Jeśli kompilacja z kompilatorem bieżący, otrzymasz następujący błąd:

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

   Wynika to z faktu w punkcie pierwsze wywołanie is_base_of — klasa będzie "jeszcze nie został zdefiniowany.

   W takim przypadku będzie nie należy używać tych cech typu w kompilatorze, dopóki ta klasa została zdefiniowana. Jeśli przeniesiesz definicje B i D na początku pliku kodu błędu, zostaje rozwiązany. Jeśli definicje znajdują się w pliki nagłówkowe, sprawdź, aby pliki nagłówkowe upewnić się, że wszystkie definicje klas są kompilowane przed problematyczne szablony są używane instrukcje include.

- **Kopiowanie konstruktorów** zarówno [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] i programu Visual Studio 2015, kompilator generuje Konstruktor kopiujący dla klasy, jeśli tej klasy ma Konstruktor przenoszący zdefiniowane przez użytkownika, ale nie Konstruktor kopiujący zdefiniowane przez użytkownika. W Dev14 ten Konstruktor kopiujący niejawnie wygenerowany jest również oznaczone jako "= delete".

### <a name="VS_Update1"></a>Ulepszenia zgodność w programie Visual Studio 2015 Update 1

- **Prywatne wirtualne klasy podstawowe i pośredniego dziedziczenia** poprzednie wersje kompilatora dozwolone klasy pochodnej w celu wywołania funkcji Członkowskich jego *pośrednio pochodzi* `private virtual` klasy podstawowej. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator nie akceptuje kod napisany w ten sposób i w związku z tym problemów błąd kompilatora C2280.

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

  —lub—

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Przeciążony operator new ani operator delete** poprzednie wersje kompilatora dozwolone niebędący elementem członkowskim `operator new` i niebędący elementem członkowskim `operator delete` być zadeklarowany jako statyczny i można zadeklarować w przestrzeni nazw innej niż globalna przestrzeń nazw.  To zachowanie starego utworzone ryzyko, że program nie może wywołać `new` lub `delete` implementacji operator, który przeznaczony programistę, co powoduje zachowanie dyskretnej zły środowiska wykonawczego. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2323 zamiast tego.

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

      Additionally, although the compiler doesn't give a specific diagnostic, inline operator new is considered ill-formed.

- **Wywołanie "operator *typu*()" (konwersja zdefiniowana przez użytkownika) dla typów innych niż klasa** poprzednie wersje kompilatora dozwolone "operator *typu*()" ma być wywoływana dla typów innych niż klasa podczas dyskretnie zostanie on zignorowany. To zachowanie starego utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2228 zamiast tego.

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

- **Nadmiarowe typename w specyfikatorze typu specyfikatory** poprzednie wersje kompilatora dozwolone `typename` w specyfikatorze typu rozwinięciem; kod napisany w ten sposób jest semantycznie nieprawidłowy. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C3406 zamiast tego.

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

- **Wpisz wnioskowanie tablic z listy inicjalizatora** poprzednie wersje kompilatora nie obsługują wnioskowanie typów tablic z listy inicjatorów. Kompilator obsługuje teraz ten formularz wnioskowanie typu i, w związku z tym wywołań szablonów funkcji przy użyciu listy inicjatorów teraz może być niejednoznaczna lub innego przeciążenia może wybrany niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program teraz należy jawnie określić zamierzony przez programistę przeciążenia.

   Gdy to nowe zachowanie powoduje Rozpoznanie przeciążenia wziąć pod uwagę dodatkowe kandydujących, który jest równie candidate historycznych, wywołanie staje się niejednoznaczne i kompilator generuje błąd kompilatora C2668 w związku z tym.

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

   Gdy Rozpoznanie przeciążenia wziąć pod uwagę dodatkowe kandydujących, będący lepszym dopasowaniem niż candidate historycznych, wywołanie jest rozpoznawany jako jednoznacznie candidate nowe, powoduje to nowe zachowanie powoduje zmianę zachowania programu prawdopodobnie różni się od programista przeznaczone.

   Przykład 2: zmiana Rozpoznanie przeciążenia (przed)

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

   Przykład 2: zmiana Rozpoznanie przeciążenia (po)

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

- **Przywracanie ostrzeżenia instrukcji switch** A poprzedniej wersji kompilatora usunięte uprzednio istniejące ostrzeżenia dotyczące `switch` instrukcje; te ostrzeżenia zostały przywrócone. Kompilator generuje teraz przywróconej ostrzeżenia, a powiązane z szczególnych przypadkach (w tym przypadku domyślnego) są teraz wyświetlane ostrzeżenia na wiersz zawierający w przypadku ataku, a nie w ostatnim wierszu instrukcji switch. W związku z tym teraz wydawania tych ostrzeżeń w wierszach innego niż w przeszłości, ostrzeżenia poprzednio pominąć przy użyciu `#pragma warning(disable:####)` nie może zostać pominięta, zgodnie z założeniami. Aby pominąć te ostrzeżenia, zgodnie z założeniami, może być konieczne przenieść `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszym przypadku potencjalnie naruszeń. Poniżej przedstawiono przywróconej ostrzeżenia.

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

   Przykłady przywróconej ostrzeżenia znajdują się w dokumentacji.

- **#include: użycie specyfikatora katalogu nadrzędnego '..' w pathname** (dotyczy tylko/Wall /WX)

     Poprzednie wersje kompilatora nie wykrył użycie specyfikatora katalogu nadrzędnego '..' w nazwie ścieżki `#include` dyrektywy. Kod napisany w ten sposób ma zwykle obejmują nagłówki, które istnieją poza projektem za pomocą nieprawidłowo ścieżek względnych projektu. To zachowanie starego utworzony ryzyko, że program można kompilować przez dołączenie pliku źródłowego innego niż programisty przeznaczone lub że nie jest przenoszony do innego środowiska kompilacji tych ścieżek względnych. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C4464, jeśli włączone.

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

   Ponadto, mimo że kompilator nie daje określonych diagnostyki, również zaleca się specyfikator katalogu nadrzędnego ".." Uwaga należy określić katalogi dołączenia projektu.

- **#pragma optimize() rozciąga się poza koniec pliku nagłówka** (dotyczy tylko/Wall /WX)

   Poprzednie wersje kompilatora nie wykrył zmiany ustawień flagi optymalizacji, które escape uwzględnionych w jednostce tłumaczenia pliku nagłówka. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C4426 w lokalizacji naruszeń `#include`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli konflikt zmian z flagi optymalizacji przez kompilator argumenty wiersza polecenia.

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

- **Niezgodne #pragma warning(push)** i **#pragma warning(pop)** (dotyczy tylko/Wall /WX)

   Poprzednie wersje kompilatora nie wykrył `#pragma warning(push)` stan zmieni się łączyć się z `#pragma warning(pop)` stanu zmian w pliku innego źródła, które rzadko są przeznaczone. To zachowanie starego utworzone zagrożenie program będzie można skompilować z innym zestawem ostrzeżenia włączone niż programisty przeznaczone, prawdopodobnie co powoduje zachowanie dyskretnej zły środowiska wykonawczego. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C5031 w lokalizacji dopasowywania `#pragma warning(pop)`, jeśli jest włączona. To ostrzeżenie obejmuje uwagi odwołujące się do lokalizacji odpowiedniego #pragma warning(push).

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

   Chociaż jest to rzadko, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest czułe na zmiany `#include` kolejność; Jeśli to możliwe, firma Microsoft zaleca, aby pliki kodu źródłowego Zarządzanie stan ostrzegawczy w sposób niezależny.

- **Niedopasowane #pragma warning(push)** (ma wpływ tylko na wx/Wall) poprzednie wersje kompilatora nie wykrył niedopasowane `#pragma warning(push)` zmiany na końcu jednostce tłumaczenia stanów. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C5032 w lokalizacji niedopasowane #pragma warning(push), jeśli włączone. To ostrzeżenie zostanie wyświetlone tylko, jeśli nie ma żadnych błędów kompilacji w jednostce tłumaczenia.

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

- **Może zostać wygenerowany dodatkowych ostrzeżeń wyniku śledzenia stanu ostrzeżenia #pragma ulepszone** poprzednie wersje kompilatora śledzone ostrzeżenia #pragma zmian stanu niewystarczająco również do wystawienia przeznaczone wszystkie ostrzeżenia. To zachowanie utworzony ryzyka to pewność, że ostrzeżenia będzie efektywnie pomijane w sytuacjach innych niż programisty przeznaczone. Kompilator teraz śledzi stan ostrzeżenia #pragma bardziej niezawodnie — szczególnie odnoszących się do zmian stanu ostrzeżenia #pragma wewnątrz szablonów — i opcjonalnie wystawia nowe ostrzeżenia C5031 i C5032, które mają pomóc programisty zlokalizować niezamierzone zastosowań `#pragma warning(push)` i `#pragma warning(pop)`.

   Wyniku ulepszone #pragma zmian stanu śledzenia, ostrzeżenia wcześniej niepoprawnie pominięte lub ostrzeżenia dotyczące problemów, które wcześniej misdiagnosed mogą teraz być ostrzeżenie.

- **Ulepszone identyfikacji nieosiągalny kod** zmiany standardowa biblioteka C++ i ulepszona możliwość wywołania funkcji wbudowanej w porównaniu z poprzednimi wersjami kompilatora mogą zezwalać kompilator, aby udowodnić, że niektóre kodu jest nieosiągalny. To nowe zachowanie może spowodować nowych i innych często wydane wystąpień ostrzeżenie C4720.

   ```Output
    warning C4720: unreachable code
   ```

   W wielu przypadkach to ostrzeżenie może być wystawiane tylko podczas kompilowania z włączonymi optymalizacjami, od optymalizacji mogą wbudowanego więcej wywołania funkcji, wyeliminować nadmiarowy kod lub w przeciwnym razie była możliwość określenia, że niektóre kod jest nieosiągalny. Zaobserwowano, że nowe wystąpienia ostrzeżenia C4720 często wystąpiły w blokach try/catch, szczególnie w związku z korzystaniem z [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

### <a name="VS_Update2"></a>Ulepszenia zgodność w programie Visual Studio 2015 Update 2

- **Dodatkowych ostrzeżeń i błędów może zostać utworzony w wyniku częściowej obsługi techniki SFINAE wyrażeń** poprzednie wersje kompilatora nie jest przetwarzany niektóre rodzaje wyrażeń wewnątrz `decltype` specyfikatory z powodu braku obsługi w wyrażeniu TECHNIKI SFINAE. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator teraz analizuje tych wyrażeń i ma częściowej obsługi techniki SFINAE wyrażeń, z powodu trwającej zgodność ulepszenia. W związku z tym kompilator generuje teraz ostrzeżenia i błędy znalezione w wyrażeniach, że poprzednie wersje kompilatora nie jest przetwarzany.

   Gdy to nowe zachowanie analizuje `decltype` wyrażenie zawiera typ, którego nie ma jeszcze zadeklarowana, kompilator generuje błąd kompilatora C2039 w związku z tym.

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

   Gdy to nowe zachowanie analizuje `decltype` wyrażenie, które nie ma potrzeby stosowania `typename` — słowo kluczowe, aby określić, że typem, kompilator jest zależna nazwa generuje ostrzeżenie C4346 wraz z błąd kompilatora C2923 kompilatora.

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

- `volatile`**zmienne Członkowskie zapobiec niejawnie zdefiniowanych konstruktorów i operatory przypisania** poprzednie wersje kompilatora dozwolone klasy, która ma `volatile` zmienne Członkowskie mają domyślne skopiowania/przeniesienia konstruktory i domyślne Kopiuj/Przenieś operatory przypisania generowane automatycznie. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator uwzględnia teraz klasę, która ma zmiennych Członkowskich volatile nieuproszczony konstrukcji i operatory przypisania co zapobiega domyślnej implementacji tych operatorów są generowane automatycznie.  Jeśli taka klasa jest elementem członkowskim Unii (lub anonimowego związku wewnątrz klasy), konstruktorach kopiowania/przenoszenia i operatory przypisania skopiowania/przeniesienia Unii (lub klasy zawierającej Unii unonymous) będzie można niejawnie zdefiniowany jako usunięty. Podjęto próbę utworzenia lub skopiuj Unii (lub klasa zawierająca anonimowa Unia) bez jawnie definiując je w związku z tym jest błąd i błąd kompilatora problemów kompilatora C2280.

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

- **Statyczne funkcje Członkowskie nie obsługują kwalifikatorów cv.** Poprzednie wersje programu Visual C++ 2015 dozwolone statycznych funkcji Członkowskich mają kwalifikatorów cv. To zachowanie jest spowodowane Regresja w programie Visual C++ 2015 i Visual C++ 2015 Update 1; Visual C++ 2013 i poprzednie wersje programu Visual C++ odrzucić kod napisany w ten sposób. Zachowanie środowiska Visual C++ 2015 i Visual C++ 2015 Update 1 jest nieprawidłowa i nie odpowiada C++ standard.  Visual Studio 2015 Update 2 odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2511 zamiast tego.

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

- **Deklaracja przekazująca dalej wyliczenie nie jest dozwolona w kodzie WinRT** (dotyczy tylko /ZW) kodu skompilowanego dla środowiska uruchomieniowego systemu Windows (WinRT) nie zezwala na `enum` typów do przodu, podobnie do podczas kompilowania kodu zarządzanego języka C++ dla programu .net Framework za pomocą przełącznika kompilatora/CLR. Jest to zachowanie gwarantuje, że rozmiar wyliczenie zawsze jest znany i może zostać poprawnie przedstawione w systemie typu WinRT. Kompilator odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2599 wraz z błąd kompilatora C3197.

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

- **Przeciążony operator niebędący elementem członkowskim nowe ani operator delete nie można zadeklarować wbudowanego** (poziom 1 (/ W1) na domyślnie) poprzednie wersje kompilatora nie ostrzeżenie podczas niebędący elementem członkowskim operator new ani operator delete funkcje są zadeklarowana śródwierszowo . Kod napisany w ten sposób jest niepoprawnie sformułowanych (Diagnostyka nie jest wymagane) i może spowodować pamięci problemy wynikające z niezgodne new i delete — operatory (zwłaszcza gdy jest używany z cofania alokacji o rozmiarze), które mogą być trudne do diagnozowania.   Kompilator generuje teraz kompilatora ostrzeżenie C4595 zidentyfikować kod napisany w ten sposób.

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

   Ustalenie kodu, który jest zapisany w ten sposób mogą wymagać czy definicje operatora można przenieść pliku nagłówka i do odpowiadający mu plik źródłowy.

### <a name="VS_Update3"></a>Ulepszenia zgodność w programie Visual Studio 2015 Update 3

- **STD::is_convertable teraz wykrywane jest przypisanie własne** (standardowa biblioteka) poprzednie wersje `std::is_convertable` typu cechy nie poprawnie wykrył przypisanie własne typu klasy, po usunięciu jej Konstruktor kopiujący lub prywatnej. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie `false` po zastosowaniu do typu klasy z konstruktorami kopiowania usunięte lub prywatnej.

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

   W poprzednich wersjach programu Visual C++, statyczne potwierdzenia w dolnej części w tym przykładzie przekazać, ponieważ `std::is_convertable<>::value` została niepoprawnie ustawiona `true`. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie `false`, powoduje statycznych potwierdzenia się niepowodzeniem.

- **Domyślnie lub usunięty trivial kopiowania i przenoszenia konstruktorów przestrzegać specyfikatory dostępu** poprzednie wersje kompilatora nie Sprawdź specyfikator dostępu etykietą default lub usunięto trivial kopii i Przenieś konstruktorów przed umożliwieniem jej do wywołania. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. W niektórych przypadkach to stare zachowanie utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator teraz sprawdza specyfikator dostępu do kopii trivial domyślne lub został usunięty i Przenieś konstruktorów w celu ustalenia, czy można wywołać, a jeśli nie, kompilator problemów w związku z tym ostrzeżenie C2248.

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

- **Amortyzacja oparte na atrybutach obsługi kodu ATL** (poziom 1 (/ W1) na domyślnie) kodu biblioteki ATL przypisanych poprzednie wersje kompilatora obsługiwane. Jako następnej fazy usunięta obsługa ATL z atrybutami kod, który [rozpoczął się w programie Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), oparte na atrybutach kodu biblioteki ATL jest przestarzałe. Kompilator generuje teraz C4467 do identyfikowania tego rodzaju przestarzały kod ostrzeżenia kompilatora.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Jeśli chcesz nadal używać oparte na atrybutach kodu biblioteki ATL z kompilatora została usunięta obsługa można wyłączyć to ostrzeżenie, przekazując `/Wv:18` lub `/wd4467` argumenty wiersza polecenia do kompilatora lub dodając `#pragma warning(disable:4467)` w kodzie źródłowym.

   Przykład 1 (przed)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Przykład 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};

   ```

   Czasami może być konieczne lub chcesz utworzyć IDL plik, aby uniknąć użycia przestarzałe atrybutów ATL, tak jak poniżej przykładowy kod

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

   Najpierw należy utworzyć plik *.idl; vc140.idl wygenerowany plik może zostać użyty do uzyskania \*zawierający interfejsów i adnotacje pliku .idl.

   Następnie dodaj krok MIDL do kompilacji, aby upewnić się, że definicje interfejsu C++ są generowane.

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

   Następnie należy użyć ATL bezpośrednio w pliku implementacji, tak jak przykładowy kod poniżej.

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

- **Prekompilowanych plików nagłówka (PCH) i jest niezgodny # dyrektywy include** (ma wpływ tylko na wx/Wall) poprzednie wersje kompilatora zaakceptowane niezgodne `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Kompilator teraz niezgodne kompilatora problemów ostrzeżenie CC4598 zidentyfikować `#include` dyrektywy podczas korzystania z plików PCH.

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

- **Prekompilowanych plików nagłówka (PCH) i jest niezgodny Dołącz katalogi** katalog dołączania (ma wpływ tylko na wx/Wall) poprzednie wersje kompilatora zaakceptowane niezgodne (`-I`) argumenty wiersza polecenia dla kompilatora między `-Yc`i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Katalog dołączania kompilatora teraz kompilatora problemów ostrzeżenie CC4599 zidentyfikować niezgodne (`-I`) argumenty wiersza polecenia, korzystając z plików PCH.

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Nowości dla języka C++ w programie Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Obsługa standardów C/C++ ulepszone ISO

#### <a name="compiler"></a>Kompilatora

Kompilator Microsoft Visual C++ obsługuje te ISO języka C ++ 11 funkcje języka:

- Argumenty szablonu domyślnego dla szablonów funkcji.
- Delegowanie konstruktorów
- Operatory jawnej konwersji.
- Listy inicjatorów i jednolite inicjowanie.
- Literały ciągu RAW.
- Szablony ze zmienną liczbą argumentów.
- Szablony alias.
- Funkcje usunięte.
- Inicjatorów elementów członkowskich danych Niestatyczne (NSDMIs).
- Funkcje domyślne. *
- Obsługuje te funkcje języka ISO C99:
- _Bool
- Literały złożone.
- Inicjatory wyznaczonych.
- Mieszanie deklaracji z kodem.
- Ciąg literału konwersji wartości można modyfikować można niedozwolone przy użyciu nowej opcji kompilatora **/Zc: strictstrings**. W języku C ++ 98 konwersji literałów ciągów na char\* (i wielu ciągów literałów na wchar_t\*) została uznana za przestarzałą. W języku C ++ 11 konwersja usunięto całkowicie. Mimo że kompilator ściśle może odpowiadać standardowego, zamiast tego zapewnia **/Zc: strictstrings** opcję, dzięki czemu można kontrolować konwersji. Domyślnie opcja jest wyłączona. Należy pamiętać, że jeśli używasz tej opcji w trybie debugowania, STL nie zostanie skompilowany.
- r-wartości/l-wartością rzutowania odwołania. Z odwołaniami do r-wartości C ++ 11 mogą umożliwić łatwe rozróżnienie dwóch lvalues i rvalues. Wcześniej kompilator nie dostarczył to w scenariuszach określonych rzutowania. Nową opcję kompilatora, **/Zc: rvaluecast**, dodano dokonanie zgodność kompilatora z Paper(see section 5.4, [expr.cast]/1) pracy języka C++. Domyślne zachowanie, gdy ta opcja nie jest określona, jest taka sama, jak w programie Visual Studio 2012.
  - Uwaga: Aby funkcje domyślne przy użyciu = domyślnie do żądania konstruktorów przenoszenia memberwise i Przenieś operatory przypisania nie jest obsługiwane.

### <a name="c99-libraries"></a>Biblioteki C99

Deklaracje i implementacji są dodawane do brakujące funkcje w nagłówku: math.h, ctype.h wctype.h, stdio.h, stdlib.h i wchar.h. Dodano także są nowe complex.h nagłówków, stdbool.h, fenv.h oraz implementacji dla wszystkich funkcji i inttypes.h zadeklarowany w nich. Istnieją nowe nagłówki otoki C++ (ccomplex, cfenv, cinttypes, ctgmath) i wiele innych są aktualizowane (ccomplex, cctype — clocale —, cmath, cstdint, cstdio —, cstring —, cwchar — i cwctype —).

### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

Obsługa operatory 11 jawnej konwersji języka C ++, listy inicjatorów, zakresami wyliczeń i szablony ze zmienną liczbą argumentów.
Wszystkie kontenery obsługuje teraz C ++ 11 element szczegółowe wymagania.
Obsługa tych funkcji C ++ 14.

- "Operator przezroczysty funktorów" mniej <>, większa <>, a także <>, mnoży <> i tak dalej.
- make_unique<T>(argumentów...) i make_unique < T [] > (n)
- Funkcje Członkowskie z systemem innym niż cbegin()/cend(), rbegin()/rend() i crbegin()/crend().
- \<niepodzielne > otrzymano wiele usprawnień wydajności.
- \<type_traits > Odebrano głównych poprawki stabilizacji i kod.

### <a name="breaking-changes"></a>Fundamentalne zmiany

To lepszą obsługę normy ISO C/C++ może wymagać zmiany istniejącego kodu, który odpowiada C ++ 11 i kompiluje poprawnie w programie Visual C++ w programie Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Ulepszenia biblioteka języka Visual C++

- C++ REST SDK jest dodawany. Ma ona nowoczesnych implementacji C++ REST usług.
- Podnosi poziom obsługi języka C++ AMP tekstury. Teraz obejmuje obsługę nowych trybach próbkowania i mipmapy.
- Zadania PPL obsługuje wiele technologii planowania i debugowania asynchronicznego. Nowe interfejsy API umożliwiają tworzenie zadań PPL dla wyników normalne i warunków wyjątków.

### <a name="c-application-performance"></a>Wydajność aplikacji C++

- Teraz Wektoryzowania automatycznego rozpoznaje i optymalizuje więcej wzorców C++ w celu uczynienia kodu szybsze.
- Platforma ARM i poprawy jakości kodu micro architektura Atom.
- dodawany jest __vectorcall Konwencja wywoływania. Przekazywanie argumentów typu wektora przy użyciu konwencji wywoływania __vectorcall do użycia wektora rejestrów.
- Nowe opcje konsolidatora. /Gw (kompilator) i przełączniki /Gy (asembler) Włącz optymalizacje konsolidatora do produkcji leaner plików binarnych.
- C++ AMP udostępnionego pamięci umożliwiają ograniczenie lub wyeliminowanie danych kopiowanie między procesora CPU i procesora GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Profil rozszerzenia profilowana Optymalizacja (PGO)

- Zwiększona wydajność ze zmniejszenia w zestawie roboczym aplikacji, które są zoptymalizowane przy użyciu PGO.
- Tworzenie nowej aplikacji PGO dla Sklepu Windows.

### <a name="windows-store-app-development-support"></a>Obsługę programowania aplikacji ze Sklepu Windows

- **Struktury obsługi dla opakowany typów w wartości.** Teraz można zdefiniować typów wartości za pomocą pola, które mogą mieć wartości null — na przykład IBox<int>^ przeciwieństwie int. Oznacza to, że pola może mieć wartość lub równa nullptr.
- **Bardziej rozbudowane informacje o wyjątku.** C + +/ CX obsługuje nowy model błąd systemu Windows, który umożliwia przechwytywanie i propagowania informacji o wyjątkach sformatowanego między interfejsu binarne aplikacji (ABI); obejmuje to stosy wywołań i ciągi niestandardowych komunikatów.
- **Obiekt:: ToString() jest teraz wirtualnego.** Teraz można zastąpić ToString w zdefiniowanych przez użytkownika typów ref środowiska wykonawczego systemu Windows.
- **Obsługa przestarzałe interfejsy API.** Publiczne interfejsy API środowiska wykonawczego systemu Windows można teraz oznaczony jako przestarzały i podany niestandardowy komunikat, który jest wyświetlany jako ostrzeżenie kompilacji i zapewniają wskazówki dotyczące migracji.
- **Debuger ulepszenia.** Obsługa debugowania międzyoperacyjnego native/JavaScript, diagnozowanie wyjątków środowiska wykonawczego systemu Windows i kod async debugowania (środowisko wykonawcze systemu Windows i PLL).
  - Uwaga: Oprócz specyficzne dla języka C++ funkcji i ulepszeń, które zostały opisane w tej sekcji, inne rozszerzenia w programie Visual Studio również pomocnych lepsze aplikacje ze Sklepu Windows.

### <a name="diagnostics-enhancements"></a>Ulepszenia diagnostyki

- Debuger ulepszenia. Obsługa debugowania async i debugowania tylko mój kod.
- Kod analizy kategorii. Możesz teraz przeglądać dane wyjściowe skategoryzowane analizator kodu ułatwiają znajdowanie i rozwiązywanie problemów defektów kodu.
- Diagnostyka XAML. Można teraz diagnozować czasu odpowiedzi interfejsu użytkownika i problemy zużycie baterii w Twojej XAML.
- Grafika i ulepszenia debugowania GPU.
- Zdalnej rejestracji i odtwarzania rzeczywistego urządzenia.
- Jednoczesne C++ AMP i profilowanie procesora CPU.
- Ulepszoną diagnostykę środowiska uruchomieniowego C++ AMP.
- HLSL obliczeniowe programu do cieniowania śledzenia debugowania.

### <a name="3-d-graphics-enhancements"></a>Ulepszenia 3-grafiki

- Format obrazu zawartości potoku obsługę wstępnie pomnożonych alfa DDS.
- Edytor obrazów używa wewnętrznie wstępnie pomnożonych alfa do renderowania i co pozwala uniknąć renderowania artefaktów, takich jak otoczek ciemny.
- Obraz i edytory modelu. Tworzenie użytkownika filtru jest teraz obsługiwana w projektancie programu do cieniowania w edytorze modeli i edytor obrazów.

### <a name="ide-and-productivity"></a>IDE i produktywność

**Ulepszone formatowanie kodu**. Więcej ustawień formatowania można stosować do kod w języku C++. Przy użyciu tych ustawień, można kontrolować nowy wiersz położenie nawiasów klamrowych i słów kluczowych, wcięcia, odstępy i zawijania. Kod jest formatowana automatycznie po ukończeniu instrukcji i bloków i Wklej kod do pliku.

**Uzupełnianie nawiasu klamrowego.** Kod w języku C++ teraz auto zakończeniu znaki zamknięcia, które odpowiadają te znaki otwierania:

- {(nawias klamrowy)
- [(nawias kwadratowy)
- ((nawiasów)
- ' (pojedynczy cudzysłów)
- "(cudzysłowami)

**Funkcje dodatkowe C++ automatycznego uzupełniania.**

- Dodaje średnik dla typów klasy.
- Kończy nawiasów literałów ciągów raw.
- Kończy Komentarze wielowierszowe (/ * * /)

**Znajdź wszystkie odwołania** teraz automatycznie rozpoznaje i filtry odwołań w tle po wyświetli listę tekstową dopasowań.

**Kontekstowa elementu członkowskiego filtrowanie listy.** Elementy członkowskie niedostępne są odfiltrowywane z list Członkowskich IntelliSense. Na przykład prywatne elementy członkowskie nie są wyświetlane na liście elementów członkowskich, chyba że w przypadku modyfikowania kodu, który implementuje typu. Po otwarciu listy elementów członkowskich, możesz nacisnąć klawisze Ctrl + J, aby usunąć jeden poziom filtrowania (dotyczy tylko bieżące okno listy Członkowskie). Możesz nacisnąć klawisze Ctrl + J ponownie, aby usunąć tekstową filtrowania i wyświetlić każdy element członkowski.

**Parametr pomocy przewijania.** Podpis funkcji wyświetlany w etykietce narzędzia pomocy parametru teraz zmiany związane z liczbą parametrów, które zostały faktycznie wpisane, a nie tylko przedstawiający dowolne podpisu i nie jest ona aktualizowana na podstawie bieżącego kontekstu. Parametr pomocy również działa prawidłowo po wyświetleniu go na zagnieżdżonych funkcji.

**Przełącznik nagłówek/kod pliku.** Możesz teraz przełączać nagłówka i jego odpowiadający plik kodu przy użyciu polecenia w menu skrótów lub skrótów klawiaturowych.

**Okno właściwości projektu C++ o zmiennych rozmiarach**

**Automatyczne generowanie kod obsługi zdarzeń w języku C + +/ CX i C + +/ CLI.**  Podczas pisania kodu, aby dodać obsługę zdarzeń w języku C + +/ CX lub C + +/ CLI pliku kodu, edytor może automatycznie generować definicji delegata wystąpienia i program obsługi zdarzeń. Okna etykietki narzędzia jest wyświetlany, gdy kod obsługi zdarzenia mogą być generowane automatycznie.

**Uszczegółowienie świadomości DPI.** Ustawienie DPI świadomości dla plików manifestu aplikacji teraz obsługuje ustawienie "Na Monitor wysokiej rozdzielczości DPI pamiętać".

**Szybsze przełączanie konfiguracji.** Dla dużych aplikacji przełączania konfiguracje — szczególnie kolejnych operacji przełączania — wykonanie znacznie szybciej.

**Tworzenie wydajność w czasie.** Wiele optymalizacji i użycie wielordzeniowych przyspieszyć kompilacji, zwłaszcza w przypadku dużych projektów. Kompilacje przyrostowe dla aplikacji C++, które odwołują się do C++ WinMD również jest znacznie szybsze.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Nowości dla języka C++ w programie Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Obsługuje ulepszone C ++ 11 standardów

#### <a name="standard-template-library"></a>Standardowa biblioteka szablonów

- Obsługa nowe nagłówki STL: \<atomic >, \<chrono >, \<condition_variable — >, \<filesystem >, \<przyszłych >, \<obiektu mutex >, \<stosunek >, i \< Wątek >.
- Aby zoptymalizować użycie zasobów pamięci, kontenery są mniejsze. Na przykład w x86 wersji trybie przy użyciu ustawień domyślnych, std::vector został zmniejszony z 16 bajtów w Visual Studio 2010 do 12 bajtów w programie Visual Studio 2012 i std::map został zmniejszony z 16 bajtów w Visual Studio 2010 do 8 bajtów w programie Visual Studio 2012.
- Jako dozwolone, ale niewymagane norma C ++ 11 Iteratory PRZERAŻENIE zaimplementowana.

#### <a name="other-c11-enhancements"></a>Inne C ++ 11 rozszerzenia

- Oparta na zakresie dla pętli. Można napisać pętle bardziej niezawodne, które współpracują z tablic, kontenery STL i środowiska wykonawczego systemu Windows w postaci dla (dla zakresem deklaracja: wyrażenie). Jest to część obsługi języka podstawowego.
- Bezstanowych wyrażeń lambda, które są bloki kodu, które rozpoczyna się od [introducer] pusty lambda i przechwytywania nie zmiennych lokalnych, są teraz umożliwiają niejawnej konwersji na wskaźników funkcji, co jest wymagane przez C ++ 11 Standard.
- Wyliczenia w zakresie obsługi. Klasa wyliczenia C++ wyliczenia — klucz jest teraz obsługiwane. Poniższy kod przedstawia sposób klucza enum różni się od poprzedniej zachowanie wyliczenia.

   ```cpp
enum class Element { Hydrogen, Helium, Lithium, Beryllium };
void func1(Element e);
func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
func1(Element::Helium); // OK
   ```

### <a name="windows-store-app-development-support"></a>Obsługę programowania aplikacji ze Sklepu Windows

- **Natywnego modelu opartych na języku XAML interfejsu użytkownika**. Dla aplikacji ze Sklepu Windows można użyć nowego modelu natywnego opartych na języku XAML interfejsu użytkownika.
- **Visual C++ Component Extensions**. Te rozszerzenia uprościć zużycie obiektów środowiska wykonawczego systemu Windows, które są niezbędne część aplikacji ze Sklepu Windows. Aby uzyskać więcej informacji, zobacz plan dla Sklepu Windows przy użyciu języka C++ i dokumentacja języka języka Visual C++ (C + +/ CX)
- **Gry DirectX**. Można tworzyć atrakcyjne gry przy użyciu nowa funkcja obsługi DirectX dla aplikacji ze Sklepu Windows.
- **Współdziałanie XAML/DirectX**. Aplikacje Sklepu Windows, które teraz używać języka XAML i DirectX współdziałać wydajnie.
- **Programowanie biblioteki DLL składnika środowiska wykonawczego systemu Windows**. Programowanie biblioteki DLL składnika sprawia, że środowisko wykonawcze systemu Windows rozszerzonego.

### <a name="compiler-and-linker"></a>Kompilatorze i Konsolidatorze

- **Wektoryzowania automatycznego**. Kompilator analizuje pętli w kodzie i, w przypadku, gdy to możliwe, emituje rejestruje instrukcje, które używają wektora i instrukcje, które znajdują się w nowoczesnych wszystkie procesory w systemie. Dzięki temu szybsze pętli. (Instrukcje procesora są nazywane SSE, dla Streaming SIMD Extensions). Nie trzeba włączyć lub zażądać tego rodzaju optymalizacji, ponieważ nie jest stosowana automatycznie.
- **Automatyczny paralelizator**. Kompilator można analizować pętli w kodzie i Emituj instrukcje, które rozłożyć obliczeń na wiele rdzeni lub procesorów. Ułatwia to pętle szybsze. Należy zażądać tego rodzaju optymalizacji, ponieważ nie jest włączona domyślnie. W wielu przypadkach pomaga obejmują #pragma loop(hint_parallel(N)) w kodzie bezpośrednio przed pętli, które mają być zrównoleglone.
- Wektoryzowania automatycznego i automatycznej paralelizacji mogą współdziałać ze sobą, dzięki czemu obliczenia są rozkładane między wieloma rdzeniami i kodu w każdym core używa jej rejestrów wektora.

### <a name="new-in-visual-studio-2012-update-1"></a>Nowość w programie Visual Studio 2012 Update 1

Docelowym systemem Windows XP w przypadku kompilowania kodu C++.
Można użyć kompilatora Visual C++ i bibliotek docelowy z systemem Windows XP i Windows Server 2003.

#### <a name="parallel-programming-support"></a>Obsługa programowania równoległego

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP przyspiesza wykonywania kodu C++, wykorzystując są zwykle dostępne jako GPU na karcie odrębne grafika sprzęt równoległe danych. Model programowania C++ AMP zawiera tablice wielowymiarowe, indeksowania, transfer pamięci, kafelków i bibliotekę matematyczna funkcji. Przy użyciu rozszerzeń języka C++ AMP i ograniczenia kompilatora, można kontrolować sposób przenoszenia danych z Procesora GPU i na odwrót.

**Debugowanie.** Działanie debugowania dla aplikacji używających C++ AMP pod kątem procesora GPU jest podobnie jak debugowanie dla innych aplikacji C++. Dotyczy to również nowy równoległe, debugowanie uzupełnień, które zostały wymienione wcześniej.

**Profilowanie.** Jest teraz profilowania obsługę aktywności procesora GPU, oparty na C++ AMP i modele programowania innych Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Ulepszenia Programowanie równoległe ogólne

Ze sprzętem przechodzenia do architektury wielordzeniowych i wiele rdzeni deweloperzy już może polegać na coraz większe szybkości zegara z jednego rdzenia. Równoległe Obsługa współbieżność środowiska wykonawczego programowania umożliwia deweloperom korzystać z tych nowych architektur.
W programie Visual Studio 2010 zaawansowane biblioteki paralelizacja języka C++, takie jak biblioteka równoległych wzorców zostały wprowadzone, wraz z funkcjami przeprowadzać współbieżności przeprowadzili potoki przepływu danych zaawansowane. W programie Visual Studio 2012 zostały rozszerzone zapewniające lepszą wydajność, więcej kontroli i bardziej zaawansowane funkcje obsługi równoległych wzorców, że deweloperzy muszą większość tych bibliotek. Szerokość oferty zawiera teraz:

- Rozbudowane opartego na zadaniach model programowania obsługującego asynchrony i kontynuacje.
- Algorytmy równoległe, obsługujące równoległości rozwidlenia sprzężenia (parallel_for, parallel_for koligacji, parallel_for_each, parallel_sort —, parallel_reduce —, parallel_transform —).
- Kontenery bezpieczne współbieżności, które zawiera wątkowo wersji Standard struktury danych, takich jak priority_queue —, kolejki, vector i mapy.
- Asynchroniczne biblioteki agentów, której deweloperzy mogą używać do express potoki przepływu danych, dzielących naturalnie na równoczesnych jednostki.
- Można dostosować harmonogram i zasobów Menedżer ułatwiające smooth kompozycji wzorców na tej liście.

##### <a name="general-parallel-debugging-enhancements"></a>Ulepszenia debugowania równoległe ogólne

Oprócz tych okno zadań równoległych i okna stosów równoległych programu Visual Studio 2012 oferuje nowe okno czujki równoległej, dzięki czemu można zbadać wartości wyrażenia we wszystkich wątków i procesów i sortowanie i filtrowanie wyniku. Umożliwia także własne wizualizatorów rozszerzyć okna i we wszystkich okien narzędzi można skorzystać z nowych obsługi wieloprocesowa.

### <a name="ide"></a>IDE

**Szablony Visual Studio obsługują.** Można teraz używać technologii szablony Visual Studio C++ Tworzenie szablonów projektów i elementów.

**Ładowania rozwiązania asynchronicznego.** Projekty są obecnie ładowane asynchronicznie — części klucza rozwiązania pierwszy — tak, aby uruchomić pracy szybciej.

**Zautomatyzowane wdrażanie na potrzeby debugowania zdalnego.** Wdrażanie plików do zdalnego debugowania w programie Visual C++ zostały uproszczone. Opcja wdrażania w menu kontekstowym projektu automatycznie kopiuje z komputerem zdalnym pliki, które są określone we właściwościach konfiguracji debugowania. Ręczne kopiowanie plików do komputera zdalnego nie jest już wymagane.

**C + +/ CLI IntelliSense.** C + +/ CLI ma teraz pełną obsługę funkcji IntelliSense. Funkcje IntelliSense, takich jak szybka podpowiedź, parametr pomocy lista składników i automatycznego uzupełniania teraz pracy C + +/ CLI. Ponadto inne IntelliSense i IDE ulepszenia wymienione w niniejszym dokumencie są również działać dla języka C + +/ CLI.

**Bardziej zaawansowane funkcje IntelliSense etykietek narzędzi.** C++ IntelliSense szybka podpowiedź Pokaż bardziej rozbudowane komentarze dokumentacji XML informacji o stylu. Jeśli używasz interfejsu API z biblioteki — na przykład C++ AMP — mający komentarze dokumentacji XML, a następnie IntelliSense tooltip Wyświetla informacje o więcej niż tylko deklaracji. Ponadto jeśli kod ma komentarze dokumentacji XML, IntelliSense etykietki narzędzi Pokaż bardziej rozbudowane informacje.

**Tworzy kod w języku C++.** Szkielet kodu jest dostępna dla przełącznika if-else, pętli i innych konstrukcji kodu podstawowego, na liście rozwijanej listy członków. Wybierz fragment kodu z listy, aby wstawić je do kodu, a następnie wypełnij wymagane logiki. Można też utworzyć własne niestandardowe fragmentów kodu do użycia w edytorze.

**Lista elementów członkowskich rozszerzeń.** Lista członków listy rozwijanej pojawia się automatycznie podczas pisania kodu w edytorze kodu. Wyniki są filtrowane, tak aby tylko odpowiednie elementy członkowskie są wyświetlane podczas pisania. Można kontrolować rodzaj logiki filtrowania, który jest używany przez listy elementów członkowskich — w oknie dialogowym Opcje edytora tekstu, C/C++, zaawansowane.

**Kolorowanie semantyczne.** Typy, wyliczenia makra i innych tokenów C++ już kolorowania domyślnie.

**Podświetlanie odwołań.** Teraz wybranie symbolu prezentuje wszystkie wystąpienia symbol w bieżącym pliku. Naciśnij klawisze Ctrl + Shift + Strzałka w górę Strzałka lub Ctrl + Shift + Strzałka w dół, strzałki poruszanie się po podświetlony odwołania. Można wyłączyć tę funkcję w oknie dialogowym Opcje w obszarze **Edytor tekstu, C/C++, zaawansowane**.

### <a name="application-lifecycle-management-tools"></a>Narzędzia do zarządzania cyklem życia aplikacji

#### <a name="static-code-analysis"></a>Statycznej analizy kodu

Analizę statyczną dla języka C++ została zaktualizowana, aby podać informacje kontekstu błąd bardziej rozbudowane, więcej reguł analizy, a wyniki analizy lepsze. W nowym oknie analizy kodu można filtrować komunikaty — słowo kluczowe, projektu i ważności. Po wybraniu komunikat w oknie wiersza kodu, w której został wyzwolony komunikat zostanie wyróżniona w edytorze kodu. Dla niektórych C++ — ostrzeżenia, komunikat zawiera listę wierszy źródłowych, które zawierają ścieżka wykonywania prowadząca do ostrzeżenie; wyróżniono punkty decyzyjne i powodów do wykonywania tej określonej ścieżki.
Kod — analiza znajduje się w większości wersji programu Visual Studio 2012. W ostatecznej wersji Professional, Premium i uwzględniane są wszystkie reguły. W wersji Express dla systemu Windows 8 i Windows Phone po prostu najważniejszych ostrzeżenia są uwzględniane. Kod — analiza nie jest uwzględniony w wersji Express for Web.
Poniżej przedstawiono niektóre inne rozszerzenia analizy kodu:

- Nowe ostrzeżenia współbieżności pomóc w uniknięciu usterki współbieżności upewniając się, że używasz prawidłowe zasady blokowania w wielowątkowe programów C/C++. Analizatora wykrywa potencjalnych sytuacji wyścigu, obrotów kolejności blokady wywołujący/wywoływany blokowania naruszenia Umowy, operacje synchronizacji niedopasowanych i innych błędów współbieżności.
- Można określić języka C++ zasady, że chcesz zastosować do kodu za pomocą zestawów reguł analizy działa.
- W oknie analizy kodu można wstawić do kodu źródłowego pragma, które pomijają wybranego ostrzeżenie.
- Za pomocą nowej wersji języka Microsoft kodu źródłowego adnotacji (SAL) do opisywania, jak funkcja wykorzystuje jego parametrów założenia fakt, że o ich i zabezpieczeń it może zwiększyć dokładność i kompletności statycznej analizy kodu powoduje, że po jej zakończeniu.
- Obsługa 64-bitowych projektów C++.

#### <a name="updated-unit-test-framework"></a>Frameworka testów jednostkowych zaktualizowane

Należy użyć nowego frameworka testów jednostkowych C++ w programie Visual Studio, aby zapisać testy jednostkowe C++. Dodaj nową jednostkę Testowanie projektu do istniejącego rozwiązania C++ dzięki umieszczeniu szablonu projektu testu jednostki C++ kategorii Visual C++ w oknie dialogowym Nowy projekt. Rozpoczyna zapis testy jednostkowe w wygenerowanym TEST_METHOD szkielet kodu w pliku Unittest1.cpp. Gdy kod testu są zapisywane, Skompiluj rozwiązanie. Jeśli chcesz uruchomić testy, Otwórz okno Eksploratora testów jednostkowych, wybierając pozycję Widok, inne okna Eksploratora testów jednostkowych, a następnie w menu skrótów dla tego przypadku testowego ma, wybierz uruchomienia wybranego testu. Po zakończeniu uruchomienia testu, w tym samym oknie można wyświetlić wyniki testów i informacje śledzenia stosu dodatkowe.

#### <a name="architecture-dependency-graphs"></a>Architektura wykresy zależności

Do lepszego zrozumienia kodu, można wygenerować wykresy zależności w klasie binarny, przestrzeń nazw i Dołącz pliki w rozwiązaniu. Na pasku menu wybierz architektury, Generuj wykres zależności, a następnie dla rozwiązania lub dla plik dołączany do generowania wykresu zależności. Po zakończeniu generowania wykresu można eksplorować go rozwijając każdy węzeł, Dowiedz się relacji zależności za pomocą przenoszenia między węzłami i przeglądać kodu źródłowego, wybierając pozycję Wyświetl zawartość, w menu skrótów węzła. Aby Generuj wykres zależności dla plików dołączanych, w menu skrótów dla pliku kodu źródłowego *.cpp lub *.h nagłówek pliku, wybierz pozycję Generuj wykres z pliki dołączane.

#### <a name="architecture-explorer"></a>Eksplorator architektury

Za pomocą Eksploratora architektury, można sprawdzić zasoby w rozwiązaniu C++, projektów lub plików. Na pasku menu wybierz architektury, Windows, Eksploratora architektury. Można wybrać węzła odpowiednio do potrzeb, na przykład widoku klasy. W takim przypadku rogu okna narzędzia jest rozwinięta z listą obszarów nazw. W przypadku wybrania przestrzeni nazw nowej kolumny zawiera listę klas, struktur i typy wyliczeniowe w tej przestrzeni nazw. Można nadal Eksploruj tych zasobów lub wróć do kolumny w lewo można uruchomić inne zapytanie. Zobacz znaleźć kodu za pomocą Eksploratora architektury.

#### <a name="code-coverage"></a>Pokrycie kodu

Pokrycie kodu został zaktualizowany do dynamicznie dokumentu binarnych w czasie wykonywania. Obniża koszty konfiguracji oraz zapewnia lepszą wydajność. Może również zbierać dane pokrycia kodu z testów jednostkowych dla aplikacji C++. Po utworzeniu testy jednostkowe C++, można użyć narzędzia Eksplorator testów jednostkowych odnaleźć testów w rozwiązaniu. Uruchom testy jednostkowe i zbierania kodu dane pokrycia ich w Eksploratorze testów jednostkowych, wybierz Analizuj pokrycie kodu. Można sprawdzić wyniki pokrycia kodu w oknie wyników pokrycia kodu — na pasku menu Wybierz wyniki pokrycia kodu badania, Windows,.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Nowości dla języka C++ w programie Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Kompilator języka C++ i konsolidatora

**Auto — słowo kluczowe.** Auto — słowo kluczowe ma nowy cel. Auto — słowo kluczowe znaczenie domyślne umożliwiają zadeklarować zmiennej o typie jest ustalane z wyrażenia inicjowania w deklaracji zmiennej. Opcja kompilatora/Zc: Auto wywołuje nowy lub poprzednich znaczenie auto — słowo kluczowe.

**decltype specyfikatora typu.** Specyfikator typu decltype zwraca typ określonego wyrażenia. Użycie specyfikatora typu decltype w połączeniu z auto — słowo kluczowe w celu zadeklarowania typu złożonego lub znanych tylko do kompilatora. Na przykład użyć kombinacji do zadeklarowania funkcji szablonu, którego typ zwracany zależy od typów argumentów szablonu. Lub zadeklarowania funkcji szablonu, który wywołuje innej funkcji, a następnie zwraca typ zwracany wywoływana funkcja.

**Wyrażenia lambda.** Funkcje lambda mieć treści funkcji, ale bez nazwy. Funkcje lambda łączą najlepsze cechy wskaźników funkcji i funkcji obiektów.
Użyj funkcji lambda przez siebie, jako parametr funkcji szablonu zamiast obiektem funkcji lub wraz z automatycznie — słowo kluczowe w celu zadeklarowania zmiennej o typie jest wyrażenie lambda.

**Odwołanie do r-wartości.** Deklarator odwołania do r-wartości (& &) deklaruje odwołanie do r-wartości. Umożliwia odwołanie do r-wartości korzystanie z przenieść semantykę i doskonałego przekazywania dalej do zapisania konstruktorów bardziej wydajne, funkcje i szablony.

**static_assert deklaracji.** Deklaracja static_assert testy potwierdzenia oprogramowania, w czasie kompilacji, w przeciwieństwie do innych mechanizmów potwierdzenia, które testów w czasie wykonywania. Jeśli potwierdzenie nie powiedzie się, kompilacja zakończy się niepowodzeniem i wygenerowaniu określony komunikat o błędzie.

**słowa kluczowe nullptr i __nullptr.** Kompilator Visual C++ pozwala Użyj nullptr — słowo kluczowe z kodu natywnego lub zarządzanego kodu. Nullptr — słowo kluczowe wskazuje, że dojście do obiektu, wskaźnik wewnętrzny lub typu wskaźnika natywnego nie punktu do obiektu. Kompilator interpretuje nullptr jako kod zarządzany, korzystając z/CLR — opcja kompilatora i kodu natywnego, gdy nie należy używać opcji/CLR.
Specyficzne dla firmy Microsoft __nullptr — słowo kluczowe ma takie samo znaczenie jak nullptr, ale dotyczy tylko kodu natywnego. Jeśli kompilacja kodu natywnego C/C++ za pomocą/CLR — opcja kompilatora, kompilator nie może ustalić, czy nullptr — słowo kluczowe jest natywny lub terminów zarządzanych. Aby wyczyścić kompilator masz zamiar, umożliwia określenie terminów zarządzanych i __nullptr, aby określić termin natywny nullptr — słowo kluczowe.

**/ Zc: trigraphs — opcja kompilatora.** Domyślnie Obsługa elementów trigraph jest wyłączona. Aby włączyć obsługę trigramów, należy użyć opcji kompilatora/Zc: trigraphs.
— Trigram składa się z dwóch następujących po sobie znaki zapytania (?) następuje znak trzeci unikatowy. Kompilator zastępuje — trigram odpowiedni znak interpunkcyjny. Na przykład kompilator zastępuje? = — trigram znakiem # (znak liczby). Użyj trigramów w plikach źródłowych C, korzystających z zestawu znaków, która nie zawiera niektórych znaków interpunkcyjnych.

**Nowa opcja Optymalizacja sterowana profilem.** PogoSafeMode jest nową opcję optymalizacji, która umożliwia określenie, czy ma być używany tryb awaryjny lub trybu szybkiego podczas optymalizacji aplikacji. Tryb awaryjny jest bezpieczne wątkowo, ale jest wolniejsze od trybu szybkiego. Trybu szybkiego jest zachowaniem domyślnym.

**Nowe /clr:nostdlib opcji środowiska uruchomieniowego języka wspólnego (CLR).** Nowa opcja jest dodawany do/CLR (kompilacja języka wspólnego środowiska uruchomieniowego). Jeśli są różne wersje tej samej biblioteki dołączony, zgłaszany jest błąd kompilacji. Nowa opcja umożliwia wykluczenie biblioteki CLR domyślne, tak, aby program może użyć określonej wersji.

**Nowe detect_mistmatch dyrektywy pragma.** Detect_mismatch dyrektywy pragma umożliwia umieszczanie tag w plikach, które jest porównywany do innych tagów, które mają taką samą nazwę. Jeśli istnieje wiele wartości dla tej samej nazwie, konsolidator generuje błąd.

**Element XOP funkcje wewnętrzne, funkcje wewnętrzne FMA4 i LWP funkcje wewnętrzne.** Nowe funkcje wewnętrzne zostały dodane do obsługi XOP dodane funkcje wewnętrzne dla programu Visual Studio 2010 z dodatkiem SP1, dodać funkcje wewnętrzne FMA4 dla programu Visual Studio 2010 z dodatkiem SP1 i dodaje funkcje wewnętrzne LWP dla technologii procesora Visual Studio 2010 z dodatkiem SP1. Użyj __cpuid, __cpuidex, aby określić technologii procesora, które są obsługiwane na określonym komputerze.

### <a name="visual-c-projects-and-the-build-system"></a>Projekty Visual C++ i systemu kompilacji

**MSBuild.** Visual C++ rozwiązania i projekty są teraz utworzony przez przy użyciu narzędzia MSBuild.exe, która zastępuje VCBuild.exe. MSBuild jest tego samego narzędzia kompilacji elastyczne, rozszerzalny, opartych na języku XML, używany przez inne języki Visual Studio i typów projektów. Z powodu tej zmiany plików projektu Visual C++ teraz używać formatu pliku XML i mają rozszerzenie nazwy pliku .vcxproj. Pliki projektu Visual C++ z wcześniejszych wersji programu Visual Studio automatycznie są konwertowane na nowy format pliku.

**Katalogi VC ++.** Katalogi VC ++ ustawienie teraz znajduje się w dwóch miejscach. Użyj strony właściwości projektu, aby ustawić wartości na projekt katalogi VC ++. Użyj Menedżera właściwości i arkusz właściwości do ustawienia globalnego, wartości na konfiguracji katalogi VC ++.

**Zależności projektu do projektu.** We wcześniejszych wersjach zdefiniowanych współzależności między projektami były przechowywane w pliku rozwiązania. Jeśli te rozwiązania są konwertowane na nowy format pliku projektu, zależności są konwertowane na odwołania projektu do projektu. Ta zmiana może wpływać na aplikacje, ponieważ różnią się pojęcia zależności rozwiązania i odwołania projektu do projektu.

**Makra i zmiennych środowiskowych.** Nowe makro _ITERATOR_DEBUG_LEVEL wywołuje debugowania obsługę Iteratory. Używanie tego makra zamiast starsze _SECURE_SCL i _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

**Współbieżność środowiska wykonawczego bibliotek.** Współbieżność środowiska wykonawczego framework obsługuje aplikacji i składników, które są uruchamiane jednocześnie i framework programowania aplikacjami w programie Visual C++. Aby zapewnić obsługę programowania aplikacji równoczesnych, biblioteka równoległych wzorców (PLL) umożliwia kontenery ogólnego przeznaczenia i algorytmów w celu wykonania równoległości szczegółowych. Biblioteki agentów asynchronicznych oferuje aktora na podstawie modelu programowania i przekazywanie interfejsy coarse-grained przepływu danych i przetwarzanie potokowe zadania.

**Standardowa biblioteka języka C++.** Na poniższej liście opisano wiele zmian, które zostały wprowadzone do standardowej biblioteki C++.

- Nowa funkcja języka C++ odwołanie do r-wartości został użyty do zaimplementowania semantyki przenoszenia i doskonałego przekazywania dalej dla funkcji w standardowej biblioteki szablonów. Przenieś semantykę i doskonałego przekazywania dalej znacząco poprawić wydajność działania, których alokacji lub przypisać zmiennych i parametrów.
- Odwołania wartościowane prawostronnie są również używane do implementowania nowej klasy unique_ptr, który jest typem wskaźnika inteligentnego bezpieczniejsze niż klasa auto_ptr. Klasa unique_ptr jest ruchomy, ale nie copyable implementuje semantykę strict własność bez wpływu na bezpieczeństwo i dobrze działa z kontenerów, które rozpoznają odwołania do r-wartości. Auto_ptr — klasa jest przestarzały.
- Piętnastu nowych funkcji, na przykład find_if_not —, copy_if i is_sorted, zostały dodane do \<algorytm > nagłówka.
- W \<pamięci > Nagłówek, nowej funkcji make_shared — jest wygodne, niezawodny i efektywny sposobem tworzenia udostępnionego wskaźnika do obiektu w tym samym czasie konstruowania obiektu.
- Pojedynczo połączonej listy są obsługiwane przez \<forward_list — > nagłówka.
- Nowe funkcje Członkowskie cbegin, cend crbegin i crend zapewniają const_iterator, który przenosi do przodu i do tyłu przez kontener.
- \<System_error — > nagłówka i powiązane szablony obsługuje przetwarzanie błędy niskiego poziomu systemu. Członkowie klasy exception_ptr może służyć do transport wyjątków między wątkami.
- \<Codecvt > nagłówka obsługuje konwertowania kodowań znaków Unicode do innego kodowania.
- \<Allocators — > nagłówka definiuje kilka szablonów, które pomagają przydzielić i zwolnij bloki pamięci dla kontenerów na podstawie węzła.
- Istnieje wiele aktualizacji \<losowe > nagłówka.

### <a name="microsoft-foundation-class-mfc-library"></a>Biblioteka Microsoft Foundation Class (MFC)

**Funkcje systemu Windows 7.** MFC obsługuje wiele funkcji systemu Windows 7, na przykład wstążki interfejsu użytkownika (UI), pasek zadań, listy szybkiego dostępu, z kartami miniatur, miniatur, pasek postępu, nakładkę ikony i indeksowanie wyszukiwania. Ponieważ MFC automatycznie obsługuje wiele funkcji systemu Windows 7, nie masz do modyfikowania istniejącej aplikacji. Do obsługi innych funkcji w nowych aplikacji, umożliwia określenie funkcji, który ma być używany Kreator aplikacji MFC.

**Obsługa wielodotyku świadomości.** MFC obsługuje aplikacje, które ma interfejsu użytkownika wielodotyku, na przykład aplikacje, które zostały napisane dla systemu operacyjnego Microsoft Surface. Aplikacja wielodotyku może obsługiwać wiadomości touch z systemem Windows i gestu wiadomości, które są kombinacje touch wiadomości. Po prostu zarejestrować aplikację dla touch i gestu zdarzenia i system operacyjny będzie przekierowywać zdarzenia wielodotyku programu obsługi zdarzeń.

**Rozpoznawanie wysokiej rozdzielczości.** Domyślnie aplikacje MFC są wysokiej-obsługującą ustawienia DPI. Jeśli aplikacja jest wysokiej rozdzielczości (wysoka punkty na cal) wiedzieć, systemu operacyjnego można skalować systemu windows, tekst i inne elementy interfejsu użytkownika dla bieżącej rozdzielczości ekranu. To oznacza, że skalowanie obrazu jest bardziej prawdopodobne poprawnie poukładany, a nie przycinana lub podzielony na piksele.

**Ponownie uruchom Menedżera.** Menedżer ponownego uruchamiania automatycznie zapisuje dokumenty i ponowne uruchomienie aplikacji, jeśli nieoczekiwane zamknięcie lub ponowne uruchomienie. Na przykład można użyć Menedżera ponownego uruchomienia można uruchomić aplikacji, po jego zamknięciu aktualizacji automatycznych. Aby uzyskać więcej informacji na temat konfigurowania aplikacji za pomocą Menedżera ponownego uruchomienia, zobacz porady: Dodawanie obsługi Menedżera ponownego uruchomienia.

**Obiektu CTaskDialog.** Klasa obiektu CTaskDialog może być używana zamiast standardowego pola wiadomości AfxMessageBox. Klasa obiektu CTaskDialog Wyświetla i zbiera informacje o więcej niż standardowy komunikat nie.

#### <a name="safeint-library"></a>Biblioteka SafeInt

Nowe Biblioteka safeint — przeprowadza bezpieczne operacje arytmetyczne tego konta przepełnienie liczby całkowitej. Ta biblioteka także porównanie różnych rodzajów liczb całkowitych.

#### <a name="new-active-template-library-atl-macros"></a>Nowe makra Active Template Library (ATL)

Nowe makra zostały dodane do biblioteki ATL, aby rozszerzyć funkcjonalność PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE i PROP_ENTRY_INTERFACE_EX można dodać listę CLSID prawidłowe. PROP_ENTRY_INTERFACE_CALLBACK i PROP_ENTRY_INTERFACE_CALLBACK_EX pozwalają określić funkcję wywołania zwrotnego do ustalenia, czy CLSID jest nieprawidłowy.

#### <a name="analyze-warnings"></a>/ analyze ostrzeżenia

Najbardziej / analyze (Enterprise analiza kodu) zostały usunięte z bibliotek C Run-Time (CRT), MFC i ATL ostrzeżenia.

#### <a name="animation-and-d2d-support"></a>Obsługa animacji i D2D

MFC obsługuje teraz animacji i grafiki Direct2D. Biblioteki MFC ma kilka nowych klas MFC i funkcje do obsługi tej funkcji. Istnieją również dwa nowe wskazówki do pokazują, jak dodawanie obiektu D2D i obiektu animacji do projektu. Wskazówki te są wskazówki: Dodawanie obiektu D2D do projektu MFC i wskazówki: Dodawanie animacji do projektu MFC.

### <a name="ide"></a>IDE

**Ulepszone IntelliSense.** IntelliSense dla języka Visual C++ został zaprojektowany zupełnie być szybsze, bardziej dokładne i możliwość obsługi większych projektów. Umożliwia to ulepszenie IDE rozróżnia jak Projektant widoków i modyfikuje kodu źródłowego i jak IDE używa ustawienia źródła kodu i projektu umożliwiają utworzenie rozwiązania do.
Ze względu na to podział obowiązków funkcji przeglądania, takich jak Widok klas i przejdź do okno dialogowe Nowy są obsługiwane przez system, który jest oparty na nowy plik pulpitu bazy danych (.sdf) programu SQL Server, który zastępuje stary kompilacji nie Przeglądaj plik (.ncb). Funkcje IntelliSense, takie jak szybkie informacje, automatycznego uzupełniania i parametr pomocy przeanalizować jednostki tłumaczenia tylko wtedy, gdy jest to wymagane. Hybrydowe funkcje, takie jak nowe okno hierarchii wywołań używa się kombinacji funkcji IntelliSense i przeglądania.
Ponieważ IntelliSense przetwarza tylko te informacje, która jest wymagana w tej chwili, w jakim jest IDE poprawę reakcji. Ponadto ponieważ bardziej aktualne informacje, widoki IDE i windows są bardziej dokładne. Ponadto ponieważ infrastruktury IDE jest lepiej zorganizowany więcej stanie i skalowalność, może obsługiwać większych projektów.

**Błędy ulepszonych funkcji IntelliSense.** IDE lepiej wykrywa błędy, które mogły spowodować utratę IntelliSense i wyświetla czerwone faliste podkreślenie pod nimi. Ponadto IDE raporty błędy funkcji IntelliSense w oknie Lista błędów. Aby wyświetlić kod, który powoduje problem, kliknij dwukrotnie ten błąd w oknie Lista błędów.

**#include funkcja automatycznego zakończenia.** IDE obsługuje Autouzupełniania dla #include — słowo kluczowe. Podczas wpisywania #include, IDE tworzy pliki prawidłowego nagłówka w polu listy rozwijanej. Jeśli będziesz kontynuować, wpisując nazwę pliku, IDE filtry oparte na wpisu listy. W dowolnym momencie można wybrać z listy plików, które chcesz dołączyć. Dzięki temu można szybko Dołącz pliki bez znajomości dokładnej nazwy pliku.

**Przejdź do.** Okno dialogowe Przejdź do umożliwia wyszukanie wszystkich symboli i pliki w projekcie, zgodne z określonego ciągu. Wyniki wyszukiwania są natychmiast zaktualizowany wpisywania dodatkowe znaki w ciągu wyszukiwania. Pole opinii wyniki informuje, liczba odnalezionych elementów i pomoże Ci zdecydować, czy Ogranicz wyszukiwanie. Rodzaj/zakres, lokalizacji i Podgląd pola opinie pomóc odróżniania elementów, które mają podobne nazwy. Ponadto można rozszerzyć tę funkcję w celu obsługi innych języków programowania.

**Równoległe, debugowanie i profilowania.** Debuger programu Visual Studio zna współbieżności środowiska wykonawczego i pomaga w rozwiązywaniu problemów aplikacji przetwarzania równoległego. Narzędzie profilera współbieżności umożliwia wizualizowanie ogólne działanie aplikacji. Ponadto można użyć nowego okna narzędzi do wizualizacji stan zadań i ich stosy wywołań.

**Projektant wstążki.** Projektant wstążki jest edytora graficznego, który umożliwia tworzenie i modyfikowanie wstążki MFC interfejsu użytkownika. Interfejs użytkownika wstążki końcowego jest reprezentowana przez plik zasobów opartych na języku XML (.mfcribbon ms). Istniejących aplikacji można przechwycić bieżącego interfejs użytkownika wstążki tymczasowo dodając kilka wierszy kodu, a następnie wywoływania projektanta wstążki. Po utworzeniu pliku zasobu wstążki z odręcznie wstążki kodu interfejsu użytkownika można zastąpić kilka instrukcji, które ładowanie zasobu wstążki.

**Hierarchia wywołań.** Okno hierarchii wywołań umożliwia przejdź do wszystkich funkcji wywoływanych przez konkretną funkcję lub do wszystkich funkcji, które wywołują danej funkcji.

### <a name="tools"></a>Narzędzia

**Kreator klas MFC.** Visual C++ 2010 powrotem przełącza cenionym narzędzia Kreator klas MFC. Kreator klas MFC to wygodny sposób, aby dodać klasy, wiadomości i zmiennych z projektem bez konieczności ręcznego modyfikowania zestawów plików źródłowych.

**Kreator formantu ATL.** Kreator formantu ATL już automatycznie wypełni pola identyfikatora ProgID. Jeśli formant ATL nie ma identyfikator ProgID, inne narzędzia mogą nie działać z nim. Przykładem narzędzia, która wymaga formantów ma identyfikator ProgID jest okno dialogowe Wstaw aktywny formant. Aby uzyskać więcej informacji na temat okna dialogowego Zobacz okno dialogowe Wstaw formant ActiveX.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

Dodanie ymmword — typ danych obsługuje 256-bitowego multimedialnych argumentów operacji, które znajdują się w instrukcjach Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Nowości dla języka C++ w programie Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Visual C++ zintegrowane środowisko programistyczne (IDE)

- Okien dialogowych, które są tworzone w aplikacji ATL i MFC, Win32, teraz są zgodne z wytycznymi styl systemu Windows Vista. Podczas tworzenia nowego projektu za pomocą programu Visual Studio 2008, wszystkie okna dialogowe wstawione do aplikacji będą stosować się wytyczne styl systemu Windows Vista. Jeśli Skompiluj projekt, który został utworzony we wcześniejszej wersji programu Visual Studio, wszelkie istniejące okien dialogowych zachowa wyglądają tak samo, która wcześniej była. Aby uzyskać więcej informacji o tym, jak można umieścić okna dialogowe w aplikacji Zobacz Edytor okien dialogowych.

- Kreator projektu ATL ma teraz możliwość zarejestrowania składników dla wszystkich użytkowników. Począwszy od programu Visual Studio 2008 składniki COM i biblioteki typów, które są tworzone przez Kreator projektu ATL są rejestrowane w węźle HKEY_CURRENT_USER rejestru dopiero po wybraniu składnika rejestru dla wszystkich użytkowników.
- Kreator projektu ATL zawiera już opcji tworzenia przypisanych projektów ATL. Począwszy od programu Visual Studio 2008, Kreator projektu ATL nie ma możliwość zmiany stanu oparte na atrybutach nowego projektu. Wszystkie nowe projekty ATL, które kreator tworzy są teraz unattributed.
- Zapisywanie w rejestrze mogą zostać przekierowane. Wraz z wprowadzeniem systemu Windows Vista zapisywanie w niektórych obszarach rejestru wymaga program do uruchomienia w trybie podniesionych uprawnień. Nie jest pożądane, aby zawsze uruchomić program Visual Studio w trybie podniesionych uprawnień. Przekierowanie na użytkownika przekierowuje automatycznie zapisuje rejestru z HKEY_CLASSES_ROOT do HKEY_CURRENT_USER bez wprowadzania żadnych zmian programowania.
- Projektant klas teraz ma ograniczoną obsługę kodu natywnego języka C++. We wcześniejszych wersjach programu Visual Studio Projektant klas działał tylko z Visual C# i Visual Basic. Użytkownicy C++ mogą teraz używać Projektant klas, ale tylko w trybie tylko do odczytu. Aby uzyskać więcej informacji na temat korzystania z C++ Projektant klas zapoznaj się z kodem Visual C++ w Projektancie klas praca.
- Kreator projektu nie ma już opcję, aby utworzyć projekt C++ programu SQL Server. Począwszy od programu Visual Studio 2008, Kreator nowego projektu nie ma opcji tworzenia projektu C++ programu SQL Server. Projektów programu SQL Server utworzonych za pomocą wcześniejszej wersji programu Visual Studio będą nadal skompilować i działa poprawnie.

### <a name="visual-c-libraries"></a>Biblioteki Visual C++

#### <a name="general"></a>Ogólne

- Aplikacje może być powiązana z określonych wersji bibliotek języka Visual C++. Czasami aplikacji zależy od aktualizacji, które zostały wprowadzone do bibliotek języka Visual C++ po zlecenia. W przypadku uruchamiania aplikacji na komputerze, który ma wcześniejszych wersji biblioteki może spowodować nieoczekiwane zachowanie. Można teraz powiązać aplikacji do określonej wersji bibliotek tak, aby nie zostanie uruchomiony na komputerze, który ma wcześniejszą wersję bibliotek.

#### <a name="stlclr-library"></a>Biblioteka STL/CLR

- Visual C++ zawiera teraz biblioteki STL/CLR. Biblioteka STL/CLR jest opakowania z standardowego szablonu biblioteki (STL), podzbiór standardowa biblioteka C++ do użycia z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). STL/CLR można teraz używać wszystkich kontenerów, Iteratory i algorytmy STL w środowisku zarządzanym.

#### <a name="mfc-library"></a>Biblioteki MFC

- Windows Vista obsługuje formantów standardowych. Ponad 150 metod 18 nowych lub istniejących klas zostały dodane do obsługi funkcji w systemie Windows Vista lub zwiększające funkcjonalność w bieżącej klasy MFC.
- Nowa klasa CNetAddressCtrl umożliwia danych wejściowych i sprawdzania poprawności adresów IPv4 i IPv6 lub nazwy DNS.
- Nowa klasa CPagerCtrl upraszcza korzystanie z formantu modułu stronicowania systemu Windows.
- Nowa klasa CSplitButton upraszcza korzystanie z formantu splitbutton systemu Windows, aby wybrać domyślne lub opcjonalne działanie.

#### <a name="c-support-library"></a>Biblioteka obsługi języka C++

- C++ wprowadza biblioteki marshalingu. Biblioteka marshalingu umożliwia łatwe i zoptymalizowane do organizowania danych między środowiskach natywnych i zarządzanych. Biblioteka stanowi alternatywę do bardziej złożona i mniej wydajne podejścia, takie jak za pomocą funkcji PInvoke. Aby uzyskać więcej informacji, zobacz Omówienie z Marshalingu w języku C++.

#### <a name="atl-server"></a>Serwer ATL

- Serwer ATL jest publikowany jako projektu udostępnionego źródła.
- Większość podstawowy kod serwera ATL zostało zwolnione jako projektu udostępnionego źródła w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio 2008. Kilka pliki skojarzone z serwerem ATL nie są już częścią programu Visual Studio. Aby uzyskać listę plików usuniętych Zobacz usunąć plików serwera ATL.
- Część biblioteki ATL są teraz danych kodowania i dekodowania klasy z funkcji atlenc.h i narzędzie i klasy z atlutil.h i atlpath.h.
- Firma Microsoft będzie obsługiwać wersji serwera ATL, które znajdują się we wcześniejszych wersjach programu Visual Studio, tak długo, jak te wersje programu Visual Studio są obsługiwane. Witrynie CodePlex będzie programowanie kodu biblioteki ATL Server jako projekt społeczności. Microsoft nie obsługuje ATL Server w wersji witrynie CodePlex.

### <a name="visual-c-compiler-and-linker"></a>Kompilator Visual C++ i konsolidatora

#### <a name="compiler-changes"></a>Zmiany kompilatora

- Kompilator obsługuje zarządzanych kompilacji przyrostowej. Po określeniu tej opcji, kompilator nie będzie ponownie kompilować kodu, gdy zostanie zmieniona przywoływanego zestawu. Zamiast tego zostanie przeprowadzone kompilacji przyrostowej. Pliki są ponownie skompilowana, tylko w przypadku zmiany wpływają na kod zależnych.
- Atrybuty powiązane z biblioteki ATL Server nie są już obsługiwane. Kompilator nie obsługuje już kilka atrybutów, które zostały bezpośrednio związane z biblioteki ATL Server. Pełną listę usuniętych atrybutów Zobacz fundamentalne zmiany.
- Kompilator obsługuje mikroarchitektury Intel Core. Kompilator zawiera dostrajania dla mikroarchitektury Intel Core podczas generowania kodu. Domyślnie to dostrajanie znajduje się na i nie można wyłączyć jako pomaga również Pentium 4, a inne procesory.
- Funkcje wewnętrzne obsługuje nowszej procesory AMD i Intel. Kilka nowych wewnętrznej instrukcji obsługuje większą funkcjonalność w nowych procesorów AMD i Intel. Aby uzyskać więcej informacji na temat nowych funkcji wewnętrznych Zobacz uzupełniające Streaming SIMD Extensions 3 instrukcje, Streaming SIMD Extensions 4 instrukcje SSE4A i zaawansowane funkcje manipulowania Bit wewnętrzne, funkcje wewnętrzne AES, _mm_clmulepi64_si128 i __rdtscp.
- Funkcja __cpuid jest aktualizowana. __Cpuid, funkcje __cpuidex teraz obsługuje kilka nowych funkcji z najnowszej wersji procesorów AMD i Intel. Wewnętrzna __cpuidex nowego i zbiera więcej informacji z ostatnich procesorów.
- /MP — opcja kompilatora skraca czas kompilacji całkowitej. Opcja /MP można znacznie zmniejszyć całkowity czas do skompilowania kilka plików źródłowych przez utworzenie kilku procesów, które jednocześnie Kompiluj pliki. Ta opcja jest szczególnie przydatna na komputerach, które obsługują wielowątkowość wiele procesorów i wiele rdzeni.
- /Wp64 — opcja kompilatora i __w64 — słowo kluczowe są przestarzałe. /Wp64 — opcja kompilatora i __w64 — słowo kluczowe, które wykrywać problemy związane z przenośnością 64-bitowych, są przestarzałe i zostanie usunięta w przyszłej wersji kompilatora. Zamiast tego — opcja kompilatora i słowo kluczowe Użyj kompilatora Visual C++ tej platformy 64-bitowych obiektów docelowych.
- / Qfast_transcendentals generuje kodu wbudowanego przestępne funkcji.
- / Qimprecise_fwaits usuwa polecenia fwait wewnętrzny, aby bloki try, korzystając z / FP: except — opcja kompilatora.

### <a name="linker-changes"></a>Zmiany konsolidatora

- Informacje o kontroli konta użytkownika jest teraz osadzony w plikach manifestu dla plików wykonywalnych przez konsolidator Visual C++ (link.exe). Ta funkcja jest włączona domyślnie.   Aby uzyskać więcej informacji na temat wyłączyć tę funkcję lub zmodyfikować zachowanie domyślne Zobacz /MANIFESTUAC (osadza informacje UAC w manifeście).
- Konsolidator ma teraz opcję /DYNAMICBASE, aby włączyć funkcję randomizacji układu przestrzeni adresowej systemu Windows Vista. Ta opcja modyfikuje nagłówka pliku wykonywalnego, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czas ładowania.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Nowości dla języka C++ w programie Visual Studio 2005

Nowa w programie Visual C++ 2005 z dodatkiem Service Pack 1 zostały następujące funkcje:

### <a name="intrinsics-for-x86-and-x64"></a>Funkcje wewnętrzne dla x86 i x64

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

### <a name="intrinsics-for-x64-only"></a>Funkcje wewnętrzne dla tylko x64

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

Kompilator ma fundamentalne zmiany w tej wersji.

- natywne "64-bitowe i między kompilatory.
- / analyze (analiza kodu Enterprise) dodano opcję kompilatora.
- / bigobj — opcja kompilatora został dodany.
- / CLR: pure, / CLR: Safe i: oldsyntax zostały dodane.
- Przestarzałe — opcje kompilatora: wiele opcji kompilatora są przestarzałe w tej wersji; Aby uzyskać więcej informacji, zobacz przestarzałe — opcje kompilatora.
- Podwójna konwersja bitowa adresów w kodzie/CLR, zostanie zmniejszona; Aby uzyskać więcej informacji, zobacz podwójna konwersja bitowa adresów (C++).
- /EH (Model obsługi wyjątku) lub/EHS nie będzie można przechwytywać wyjątku, który jest uruchamiany z inną niż throw; Użyj/eha.
- Dodano — opcja kompilatora/errorreport (zgłaszaj wewnętrzne błędy kompilatora).
- / favor (Optymalizacja 64) pod — opcja kompilatora został dodany.
- / FA, /Fa (wyświetlanie listy plików) — opcja kompilatora został dodany.
- /FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce) — opcja kompilatora został dodany.
- /FP (określenie zachowania Floating-Point) — opcja kompilatora został dodany.
- Opcje (Optymalizuj dla procesora) /G — opcja kompilatora został dodany.
- Opcje (Optymalizuj dla procesora) /G — opcja kompilatora został dodany.
- / Opcje kompilatora G3, /G4 /G5, G6, G7 i /GB zostały usunięte. Kompilator używa teraz "mieszanych modelu", który próbuje utworzyć najlepsze pliku wyjściowego dla wszystkich architektur.
- /GF została usunięta. Zamiast tego użyj /GF (eliminowanie ciągów zduplikowanych).
- /GL (optymalizacja całego programu) jest teraz zgodne z /CLRHEADER.
- GR jest teraz włączona domyślnie.
- /GS (Sprawdzanie zabezpieczeń bufora) udostępnia teraz zabezpieczenia dla parametrów narażone wskaźnika. / GS jest teraz włączona domyślnie. / GS również działa teraz w funkcjach skompilowanych do MSIL z/CLR (kompilacja języka wspólnego środowiska uruchomieniowego).
- Dodano — opcja kompilatora/homeparams (Kopiuj Parametry rejestru do stosu).
- Dodano — opcja kompilatora/hotpatch (Utwórz obraz możliwych).
- Zaktualizowano wbudowanej funkcji heurystyki; Zobacz wbudowany, __inline, __forceinline i inline_depth, aby uzyskać więcej informacji
- Dodano wiele nowych funkcji wewnętrznych, i opisano wiele wcześniej nieudokumentowanej funkcje wewnętrzne.
- Domyślnie wywołania do nowego, który zakończy się niepowodzeniem, spowoduje zgłoszenie wyjątku.
- /ML i /MLd — opcje kompilatora zostały usunięte. Visual C++ nie obsługuje już Obsługa bibliotek CRT jednowątkowe, statycznie połączone.
- Kompilator zaimplementowana o nazwie zwrócić wartość optymalizacji, która jest włączana podczas kompilowania z/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość), /Og (optymalizacje globalne) i /Ox (Pełna optymalizacja).
- Porównuje — opcja kompilatora został usunięty, ale zostaną dyskretnie zignorowane; Modyfikatory noalias lub restrict__declspec umożliwia określenie, jak aliasów przez kompilator.
- — Opcja kompilatora /OP miał została usunięta. Zamiast tego użyj/FP (Określ zachowanie Floating-Point).
- OpenMP — jest teraz obsługiwana przez Visual C++.
- Dodano — opcja kompilatora/OpenMP (Włącz obsługę OpenMP 2.0).
- — Opcja kompilatora /ow został usunięty, ale zostaną zignorowane trybie dyskretnym. Modyfikatory noalias lub restrict__declspec umożliwia określenie, jak aliasów przez kompilator.

### <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem

- / QI0f została usunięta.
- / QIfdiv została usunięta.
- / Dodano — opcja kompilatora QIPF_B (erracie dla Stepping Procesora B).
- / Dodano — opcja kompilatora QIPF_C (erracie dla Stepping Procesora C).
- / Dodano — opcja kompilatora QIPF_fr32 (czy nie Użyj górny 96 zmiennoprzecinkową punktu rejestruje).
- / Dodano — opcja kompilatora QIPF_noPIC (Generowanie kodu zależnego pozycji).
- / Dodano — opcja kompilatora QIPF_restrict_plabels (założono nr funkcje utworzone w czasie wykonywania).

### <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

- /VD (Wyłącz przemieszczanie konstrukcji) umożliwia teraz użyć operatora dynamic_cast użytego dla obiektu budowany (/ vd2)
- Opcja kompilatora /YX została usunięta. Zamiast tego użyj /Yc (Utwórz prekompilowany plik nagłówka) lub /Yu (Korzystaj Prekompilowanego pliku nagłówka). Jeśli Usuń /YX z konfiguracji kompilacji i zamień ją na niczego, może spowodować szybsze kompilacji.
- / Zc: forscope jest teraz włączona domyślnie.
- / Zc: jest teraz włączona domyślnie.
- /Zd — opcja kompilatora została usunięta. Numer wiersza tylko informacje o debugowaniu nie jest już obsługiwana. Użyj/zi (/ z7, / zi, /ZI (Format informacji debugowania), aby uzyskać więcej informacji zobacz).
- /ZG jest obecnie tylko prawidłowe pliki kodu źródłowego C i nie plików kodu źródłowego języka C++.
- Dodano — opcja kompilatora /ZX (debugowania zoptymalizowanych pod kątem Itanium kodu).

### <a name="new-language-features"></a>Nowe funkcje językowe

- Attributeattribute jest już przestarzały.
- Modyfikator appdomain__declspec został dodany.
- Konwencja wywoływania __clrcall został dodany.
- teraz przestarzałe modyfikator declspec (C++) pozwala na określenie ciągu, który będzie wyświetlany w czasie kompilacji, gdy użytkownik próbuje uzyskać dostęp przestarzałe klasy lub funkcji.
- dynamic_cast Operator ma fundamentalne zmiany.
- Natywnych typów wyliczeniowych umożliwiają teraz określić typ bazowy.
- Modyfikator jitintrinsicdeclspec został dodany.
- Modyfikator noaliasdeclspec został dodany.
- Modyfikator process__declspec został dodany.
- Abstract, Przesłoń i zapieczętowany są prawidłowe w kompilacjach kodu natywnego.
- __restrict — słowo kluczowe został dodany.
- Modyfikator restrictdeclspec został dodany.
- Konwencja __thiscall jest teraz słowem kluczowym.
- __unaligned — słowo kluczowe jest udokumentowany.
- volatile (c) została zaktualizowana zachowanie względem optymalizacji.

### <a name="new-preprocessor-features"></a>Nowe funkcje preprocesora

- __Clr_ver — dodano wstępnie zdefiniowanego makra.
- Pragma komentarz (C/C++) akceptuje teraz /MANIFESTDEPENDENCY jako komentarz konsolidatora. Opcję exestr, aby dodać komentarz jest już przestarzały.
- embedded_idl — atrybut (#import — dyrektywa) teraz przyjmuje opcjonalny parametr.
- fenv_access pragma
- float_control pragma
- fp_contract pragma
- Zmienne globalne nie zostaną zainicjowane w kolejności, które zostały zgłoszone jeśli zmienne globalne pragma zarządzane, niezarządzane, jak i niezarządzanych sekcje. To potencjalne istotne zmiany, jeśli na przykład niezarządzane zmiennej globalnej jest inicjowany z zarządzanego zmienne globalne i pełni skonstruowanego obiektu zarządzanego jest wymagana.
- Sekcje określony za pomocą init_seg są teraz tylko do odczytu i nie odczytu/zapisu co w poprzednich wersjach.
- domyślne inline_depth jest teraz 16. Domyślnie 16 było również w obiekcie w programie Visual C++ .NET 2003.
- _Integral_max_bits — makro wstępnie zdefiniowanych dodany, zobacz wstępnie zdefiniowane makra.
- _M_cee —, _m_cee_pure — i _m_cee_safe — wstępnie zdefiniowane makra dodany, zobacz wstępnie zdefiniowane makra.
- _M_ix86_fp — dodano wstępnie zdefiniowanego makra.
- _M_x64 — dodano wstępnie zdefiniowanego makra.
- make_public pragma
- zarządzane, zaktualizowano składnię pragma niezarządzane (ma teraz wypychania i pop)
- mscorlib.dll teraz niejawnie odwołuje się # dyrektywa using we wszystkich kompilacjach/CLR.
- _Openmp — dodano wstępnie zdefiniowanego makra.
- optymalizacji pragma została zaktualizowana, a i w nie są już prawidłowe parametry.
- Atrybut no_registry #import został dodany.
- region, pragm endregion — dodano
- _Vc_nodefaultlib — dodano wstępnie zdefiniowanego makra.
- Makra Wariadyczne są teraz zaimplementowane.
- vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++.
- Pragma ostrzeżenie ma teraz specyfikator Pomiń.

### <a name="new-linker-features"></a>Nowe funkcje konsolidatora

- Jako dane wejściowe konsolidatora teraz mogą modułów (z systemem innym niż zestaw MSIL pliki wyjściowe).
- / Dodano — opcja konsolidatora ALLOWISOLATION (Manifest wyszukiwania).
- / ASSEMBLYRESOURCE (Osadź zarządzany zasób) została zaktualizowana do teraz umożliwiają określenie nazwy zasobu w zestawie oraz określ, czy zasób jest prywatna w zestawie.
- / — Opcja konsolidatora CLRIMAGETYPE (określenie typu z obrazu CLR) została dodana.
- / Dodano — opcja konsolidatora CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke).
- / Dodano — opcja konsolidatora CLRTHREADATTRIBUTE (Ustaw CLR wątku atrybutu).
- / Dodano — opcja konsolidatora CLRUNMANAGEDCODECHECK (Dodaj SupressUnmanagedCodeSecurityAttribute).
- / Dodano — opcja konsolidatora ERRORREPORT (zgłaszaj wewnętrzne błędy konsolidatora).
- / Opcja konsolidatora EXETYPE została usunięta. Konsolidator już nie obsługuje tworzenia sterowników urządzeń z systemem Windows 95 i Windows 98. Odpowiednie DDK umożliwia utworzenie te sterowniki urządzeń. EXETYPE — słowo kluczowe nie jest już prawidłowe dla pliki definicji modułu.
- / Dodano — opcja konsolidatora FUNCTIONPADMIN (Utwórz obraz możliwych).
- / LTCG — opcja konsolidatora jest teraz obsługiwana w modułach kompilowanych z/CLR. / LTCG również została zaktualizowana do obsługi optymalizacje sterowane profilem.
- / Dodano — opcja konsolidatora MANIFEST (Manifest zestawu utworzyć Side-by-Side).
- / Dodano — opcja konsolidatora MANIFESTDEPENDENCY (Określ zależności manifestu).
- / Dodano — opcja konsolidatora MANIFESTFILE (nazwa pliku manifestu).
- Opcja konsolidatora /MAPINFO:Lines została usunięta.
- / Dodano — opcja konsolidatora NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych).
- / Dodano — opcja konsolidatora PGD (Określ bazę danych dla optymalizacji Profile-Guided).
- / Dodano — opcja konsolidatora PROFILE (Profiler narzędzi wydajności).
- / — Opcja konsolidatora SECTION (Określ atrybuty sekcji) obsługuje teraz negacji atrybutu i nie obsługuje już L lub D atrybutów (związane z VxD).
- Obsługa formatu Unicode w kompilatorze i konsolidatorze
- / VERBOSE (Drukuj komunikaty o postępie) — opcja konsolidatora teraz również akceptuje Zapora połączenia internetowego i REF.
- / Opcja konsolidatora VXD została usunięta. Konsolidator już nie obsługuje tworzenia sterowników urządzeń z systemem Windows 95 i Windows 98. Odpowiednie DDK umożliwia utworzenie te sterowniki urządzeń. VXD — słowo kluczowe nie jest już prawidłowe dla pliki definicji modułu.
- Opcja konsolidatora /ws została usunięta. /WS był używany do modyfikowania obrazów przeznaczony dla systemu Windows NT 4.0. Nazwa pliku -R IMAGECFG.exe służy zamiast /WS. IMAGECFG.exe znajduje się na dysku CD z systemu Windows NT 4.0 w SUPPORT\DEBUG\I386\IMAGECFG. WYWOŁANIE PLIKU EXE.
- /WX (Traktuj ostrzeżenia konsolidatora jako błędy) — opcja konsolidatora jest udokumentowany.

### <a name="new-linker-utility-features"></a>Nowe funkcje narzędzi konsolidatora

- / Dodano ALLOWISOLATION — opcja polecenia editbin
- Instrukcja plik definicji modułu opis zostanie usunięta. Konsolidator już nie obsługuje tworzenia sterowniki urządzeń wirtualnych.
- / ERRORREPORT — opcja dodano bscmake.exe dumpbin.exe, editbin.exe i lib.exe.
- / LTCG — opcja lib został dodany.
- / NXCOMPAT — opcja polecenia editbin został dodany.
- / RANGE — opcja dumpbin został dodany.
- / TLS — opcja polecenia dumpbin został dodany.
- Opcja polecenia editbin /ws została usunięta. /WS był używany do modyfikowania obrazów przeznaczony dla systemu Windows NT 4.0. Nazwa pliku -R IMAGECFG.exe służy zamiast /WS. IMAGECFG.exe znajduje się na dysku CD z systemu Windows NT 4.0 w SUPPORT\DEBUG\I386\IMAGECFG. WYWOŁANIE PLIKU EXE.
- /WX [: NO] lib — opcja został dodany.

### <a name="new-nmake-features"></a>Nowe funkcje w NMAKE

- / ERRORREPORT został dodany.
- /G został dodany.
- Wstępnie zdefiniowane zasady zostały zaktualizowane.
- Makra $(MAKE), która jest udokumentowany w makra rekursji, umożliwia teraz pełną ścieżkę do nmake.exe.

### <a name="new-masm-features"></a>Nowe funkcje MASM

- Wyrażenia MASM są teraz 64-bitowej wartości. W poprzednich wersjach MASM są wartości 32-bitowe.
- Int __asm instrukcji 3 teraz powoduje, że funkcja ma być kompilowana Native.
- ALIAS (MASM) jest udokumentowany.
- / ERRORREPORT — opcja ml.exe i ml64.exe jest dodawany.
- . FPO jest udokumentowany.
- H2INC.exe nie będzie wysyłać w programie Visual C++ 2005. Jeśli chcesz nadal używać H2INC, użyj H2INC.exe z poprzedniej wersji programu Visual C++.
- Operator IMAGEREL został dodany.
- Operator HIGH32 został dodany.
- Operator LOW32 został dodany.
- ml64.exe to wersja MASM dla x64 architektury. Go składana x64 .asm plików do x64 obiekt plików. Język asemblera wbudowanego nie jest obsługiwany w x64 kompilatora. Dodano następujące dyrektywy MASM ml64.exe (x64):
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME oprócz, dyrektywy PROC został zaktualizowany o składni tylko x64.
- Dodano mmword — dyrektywa
- / omf (opcja wiersza polecenia ML.exe) teraz oznacza /c. ML.exe nie obsługuje tworzenia połączeń obiektów format OMF.
- Dyrektywa segmentu obsługuje teraz dodatkowe atrybuty.
- Operator SECTIONREL został dodany.
- Dodano xmmword — dyrektywa

### <a name="new-crt-features"></a>Nowe funkcje CRT

- Dodano bezpiecznego wersji kilka funkcji. Te funkcje obsługi błędów w lepszy sposób i wymuszać bardziej rygorystyczne formantów dla buforów, aby uniknąć typowych luk w zabezpieczeniach. Nowe wersje bezpiecznego są identyfikowane przez sufiks _s.
- Istniejące wersje mniej bezpieczne wielu funkcje są przestarzałe. Aby wyłączyć ostrzeżenia dotyczące zaniechania, zdefiniuj _CRT_SECURE_NO_WARNINGS.
- Wiele funkcji istniejących teraz walidację ich parametrów i wywołania program obsługi nieprawidłowych parametrów, gdy przekazany nieprawidłowy parametr.
- Errno gdy przedtem nie można teraz ustawić w wielu istniejących funkcji.
- Dodano errno_t typedef z typu integer. errno_t jest używana zawsze, gdy funkcja zwracany typ lub parametr dotyczy kodów błędów z numer błędu. errno_t zastępuje errcode.
- Funkcje zależne od ustawień regionalnych został wersji przyjmujących ustawień regionalnych jako parametr, a nie przy użyciu bieżących ustawień regionalnych. Te nowe funkcje mają sufiks _l. Dodano kilka nowych funkcji do pracy z obiektami ustawień regionalnych. Nowe funkcje obejmują _get_current_locale —, _create_locale i _free_locale —.
- Nowe funkcje zostały dodane do obsługi blokowaniem i odblokowywaniem dojść do plików.
- Rodziny _spawn funkcji nie powoduje resetowania errno zero w przypadku powodzenia, tak jak w poprzednich wersjach.
- Wersje systemów z rodziny printf funkcji, dzięki którym można określić kolejność, w którym są używane argumenty są dostępne.
- Unicode jest teraz obsługiwane formacie. _Otwórz funkcja obsługuje _O_TEXTW, _O_UTF8 i _O_UTF16 atrybuty. Fopen — funkcja obsługuje "ccs = ENCODING" metodę określania Unicode format.
- Nowa wersja bibliotek CRT wbudowane kodu zarządzanego (MSIL) jest teraz dostępna i jest używany podczas kompilowania przy użyciu opcji/CLR (kompilacja języka wspólnego środowiska uruchomieniowego).
- _fileinfo została usunięta.
- Domyślny rozmiar time_t — jest teraz 64-bitowy, która rozszerza zakres time_t — i niektóre funkcje czasu limit roku 3000.
- CRT obsługuje teraz, ustawienia regionalne na podstawie na wątek. _Configthreadlocale — funkcja została dodana do obsługi tej funkcji.
- _Statusfp2 — i __control87_2 — funkcje zostały dodane do zezwalania na dostęp do i kontrolę nad punkt kontroli słowo na obu x87 SSE2 przestawionych i punktu procesora.
- Dodano funkcje The_mkgmtime i _mkgmtime64 — zapewnia obsługę Konwertowanie godzin (tm struktury) czas uniwersalny Greenwich (GMT).
- Aby lepiej jest zgodny ze standardem swprintf — i vswprintf — zostały wprowadzone zmiany.
- Nowy plik nagłówka, INTRIN. H, zapewnia prototypy niektóre funkcje wewnętrzne.
- Fopen — funkcja teraz ma atrybut N.
- Funkcja _otwórz ma teraz atrybut _O_NOINHERIT.
- Atoi — funkcja teraz zwraca int_max — i ustawia errno erange — na przepełnienia. W poprzednich wersjach zachowanie przepełnienia jest niezdefiniowany.
- Rodziny printf szesnastkowy obsługuje funkcje zmiennoprzecinkowa output zaimplementowana ze standardem ANSI C99 używanie specyfikatorów formatu typu %a i %A.
- Rodzina printf obsługuje teraz prefiks rozmiar "wszystko" (long long).
- _Controlfp — funkcja został zoptymalizowany w celu zapewnienia lepszej wydajności.
- Dodano wersji debugowania niektórych funkcji.
- _Chgsignl — dodano i _cpysignl (wersje podwójnej długości).
- _Locale_t — dodany do typu tabeli.
- Nowe _countof — makro makro dodawany do przetwarzania danych Liczba elementów w tablicy.
- W każdym temacie funkcji dodano sekcję na odpowiedniki .NET Framework.
- Funkcje ciągów kilka teraz dostępna opcja obcinanie ciągów znaków, a nie niepowodzeniem, jeśli buforów danych wyjściowych jest za mały; Zobacz _truncate —.
- _set_se_translator — teraz wymaga użycia opcji/eha kompilatora.
- fpos_t — jest teraz __int64 w obszarze /Za (dla kodu C) i kiedy __STDC__ ustawiono ręcznie (dla kodu C++). Zwykle struktury.
- _Crt_disable_perfcrit_locks — może poprawić wydajność We/Wy jednowątkowe programów.
- Nazwy POSIX ma została zastąpiona ISO C++ zgodność nazwy (na przykład _getch — Użyj zamiast getch —).
- Nowe pliki .obj opcje łącza są dostępne dla pure tryb czysty
- _recalloc — łączy funkcje realloc i calloc —.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Nowości dla języka C++ w programie Visual Studio 2003

### <a name="compiler"></a>Kompilatora

- Informacje na temat uruchamiania zarządzanych rozszerzeń języka C++ aplikacji skompilowanej za pomocą bieżącej wersji kompilatora w poprzedniej wersji środowiska uruchomieniowego.
- Rozszerzenia Managed Extensions for C++ — często zadawane pytania.
- Dodano przewodnik pokazujący sposób portu istniejących, natywnych aplikacji za pomocą rozszerzeń zarządzanych dla języka C++: wskazówki: eksportowanie istniejących aplikacji C++ natywnej do Interoperate z składników .NET Framework.
- Teraz można utworzyć delegata w metodzie typu wartości.
- Kompilatora zgodności ze standardem C++ zostały znacznie rozszerzone Visual C++ .NET 2003.
- / — Opcja kompilatora architektury zostanie dodany.
- /GF jest przestarzała i zostanie usunięta w przyszłych wersjach programu Visual C++.
- / Opcja kompilatora G7 jest dodawany.
- /GS — opcja kompilatora zostało rozszerzone, aby lepiej chronić zmienne lokalne z bezpośrednie przekroczenia buforu.
- Opcja kompilatora /noBool została usunięta. Kompilator umożliwia teraz bool były wyświetlane tylko jako słowo kluczowe (a nie identyfikator) w pliku kodu źródłowego języka C++.
- Typu long long jest teraz dostępna jako typedef __int64 należy pamiętać, że jest jeszcze nie obsługuje długich długo w CRT.
- /Zm — opcja kompilatora teraz określa limit alokacji pamięci prekompilowanego nagłówka.
- Wewnętrzna _InterlockedCompareExchange udokumentowany.
- Wewnętrzna _InterlockedDecrement udokumentowany.
- Wewnętrzna _InterlockedExchange udokumentowany.
- _InterlockedExchangeAdd — wewnętrzne udokumentowany.
- Wewnętrzna _InterlockedIncrement udokumentowany.
- _ReadWriteBarrier — funkcja dodana.

### <a name="attributes"></a>Atrybuty

- `implements`atrybut jest udokumentowany.

### <a name="linker-features"></a>Funkcje konsolidatora

Dodano następujące przełączniki linker:

- / ASSEMBLYDEBUG
- / ASSEMBLYLINKRESOURCE
- DELAYSIGN
- / KEYFILE
- / KEYCONTAINER.
- / SAFESEH

### <a name="masm"></a>MASM

. Dodano opcję ml.exe dyrektywy i opcja/SAFESEH SAFESEH.

## <a name="see-also"></a>Zobacz też

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
