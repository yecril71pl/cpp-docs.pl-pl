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
dev_langs: C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 030a5e287d18884a2bbf49613a464c9d3c98f8d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co &#39; s nowe 2003 za pośrednictwem 2015

**Uwaga** informacji o programie Visual Studio 2017 znajduje się w temacie [nowości w języku Visual C++ w programie Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodność w programie Visual C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md).

W programie Visual C++ 2015 lub nowszego oraz bieżące ulepszenia kompilatora zgodność czasami można zmienić sposób kompilator rozumie istniejącego kodu źródłowego. W takim przypadku nowe lub inne błędy mogą wystąpić podczas kompilacji lub nawet behawioralnej różnice w kodzie, który uprzednio utworzony i z działała poprawnie.  
  
 Na szczęście tych różnic mają niewielkiego lub żadnego wpływu na większości kodu źródłowego i kiedy kodu źródłowego lub inne zmiany są potrzebne w celu rozwiązania tych różnic, poprawki są zwykle małe i proste. Dodaliśmy wiele przykładów kodu źródłowego wcześniej dopuszczalne, który może zaistnieć konieczność zmiany *(przed)* i poprawki, aby je poprawić *(po)*.  
  
 Mimo że te różnice mogą wpływać na kodu źródłowego lub pozostałych artefaktów kompilacji, nie wpływają na binarne zgodność aktualizacji do wersji Visual C++. Inne poważne rodzaju zmiany, *fundamentalne zmiany* może mieć wpływ na zgodność binarną, ale tego rodzaju podziały zgodność binarną występować tylko między główne wersje programu Visual C++. Na przykład między Visual C++ 2013 i Visual C++ 2015. Informacje dotyczące zmian podziału między Visual C++ 2013 i Visual C++ 2015 znajdują się w temacie [Historia 2003 2015 zmian Visual C++](../porting/visual-cpp-change-history-2003-2015.md).  
  
-   [Ulepszenia zgodność w programie Visual C++ 2015](#VS_RTM)  
  
-   [Ulepszenia zgodność aktualizacji 1](#VS_Update1)  
  
-   [Ulepszenia zgodność aktualizacji 2](#VS_Update2)  
  
-   [Ulepszenia zgodność aktualizacji 3](#VS_Update3)  
  
##  <a name="VS_RTM"></a>Ulepszenia zgodność w programie Visual C++ 2015  
  
-   Opcja /Zc:forScope-  
  
     Opcja kompilatora **/Zc:forScope-** jest przestarzała i zostanie usunięta w przyszłej wersji.  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Zazwyczaj użyto opcji w celu umożliwienia niestandardowy kod, który używa zmiennych w pętli od momentu, gdy zgodnie ze standardowego, ich powinien przeszły poza zakresem. Konieczne było tylko gdy kompilacja z opcją /Za od bez /Za, za pomocą zmiennej pętli po zakończeniu pętli zawsze jest dozwolone. Jeśli nie interesują o standardach zgodności (na przykład, jeśli kod nie jest przeznaczone do przenośnych do inne kompilatory), użytkownik może wyłączyć opcję /Za (lub ustaw właściwość Wyłącz rozszerzenia języka nie). Jeśli interesują dotyczące pisania kodu przenośnego, zgodnych ze standardami, dzięki czemu jest zgodny ze standardem przenosząc deklaracji tych zmiennych do punktu poza pętli powinien ponownego zapisywania kodu.  
  
    ```  
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
  
-   **/ZG — opcja kompilatora**  
  
     Opcja kompilatora /Zg (Generuj prototypy funkcji) nie jest już dostępny. Ta opcja kompilatora wcześniej została uznana za przestarzałą.  
  
-   Nie można uruchomić testów jednostkowych z C + +/ CLI w wierszu polecenia z mstest.exe. Zamiast tego należy użyć vstest.console.exe. Zobacz [opcje wiersza polecenia VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).  
  
-   **Mutable — słowo kluczowe**  
  
     `mutable` Specyfikator klasy magazynu nie jest dozwolony w miejscach, w którym, wcześniej skompilowane go bez błędów. Teraz, kompilator zapewnia błąd C2071 (niedozwolona Klasa magazynu). Zgodnie z standard specyfikator modyfikowalny mogą być stosowane tylko do nazwy klasy elementy członkowskie danych, nie można zastosować do zadeklarować jako const lub statycznej nazwy i nie można zastosować do odwołań do elementów członkowskich.  
  
     Rozważmy na przykład następujący kod:  
  
    ```  
    struct S {  
        mutable int &r;  
    };  
    ```  
  
     Poprzednie wersje kompilatora Visual C++ zaakceptowane to, ale teraz kompilator zapewnia następujący błąd:  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     Aby naprawić błąd, po prostu Usuń nadmiarowe mutable — słowo kluczowe.  
  
-   **char_16_t i char32_t**  
  
     Nie można korzystać `char16_t` lub `char32_t` jako aliasów w instrukcji typedef, ponieważ te typy, teraz są traktowane jako wbudowanych. W przypadku użytkowników i autorów biblioteki do definiowania char16_t i char32_t jako aliasów uint16_t i uint32_t, odpowiednio było.  
  
    ```  
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
  
-   **Parametry szablonu bez typu**  
  
     Niektóre kodu, który wymaga parametrów szablonu bez typu są teraz prawidłowo sprawdzane pod kątem zgodności typu podając jawne argumenty szablonu. Na przykład następujący kod skompilowany bez błędów w poprzednich wersjach programu Visual C++.  
  
    ```  
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
  
-   **__declspec(align)**  
  
     Kompilator nie będzie akceptował `__declspec(align)` na funkcje. To zawsze została zignorowana, ale teraz generuje błąd kompilatora.  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracją funkcji. Ponieważ nie miał żadnego skutku, usuwając go nie zmian.  
  
-   **Obsługa wyjątków**  
  
     Istnieje kilka zmian do obsługi wyjątków. Po pierwsze obiekty wyjątków muszą być copyable lub przenośne. Poniższy kod skompilowany w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nie Kompiluj w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
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
  
    ```  
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
  
    ```  
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
  
    ```  
    catch(D& d)  
    {  
    }  
    ```  
  
-   **Literały ciągu następuje makra**  
  
     Kompilator obsługuje teraz literały zdefiniowanych przez użytkownika. W rezultacie następuje makra bez żadnych spacji pośredniczące literałów ciągów są interpretowane jako literały zdefiniowane przez użytkownika, które spowodują błędy lub nieoczekiwane wyniki. Na przykład w poprzednim kompilatory następujący kod powiodło:  
  
    ```  
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
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     Aby rozwiązać ten problem, Dodaj odstęp między literałem ciągu i makra.  
  
-   **Literały ciągu sąsiadujących ze sobą**  
  
     Podobnie do poprzedniego, z powodu zmiany podczas analizy ciągu, literałów ciągów sąsiadujących ze sobą (albo literałów ciągów znaków szerokości lub wąskie) bez żadnych spacji zostały interpretowane jako pojedynczy ciąg połączonych w poprzednich wersjach Visaul C++. W [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], teraz należy dodać odstępu między dwa ciągi. Na przykład można zmienić następujący kod:  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     Po prostu Dodaj odstęp między dwa ciągi.  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **Umieszczania nowych i delete**  
  
     Dokonano zmian dla operatora delete w celu dostosowania do zgodność z języka C ++ 14 standardowa. Szczegółowe informacje o zmianie standardów można znaleźć w folderze [cofania alokacji o rozmiarze w języku C++](http://isocpp.org/files/papers/n3778.html). Zmiany dodać formę operatora delete globalny, który przyjmuje parametr rozmiaru. Istotne zmiany jest, że jeśli zostały wcześniej za pomocą operatora delete o tej samej sygnaturze (odpowiadającą operatora new umieszczania), zostanie wyświetlony błąd kompilatora (C2956, co następuje w momencie, gdzie nowe umieszczania są używane, ponieważ to jest operator delete pozycji w kodzie, w którym kompilator podejmie próbę identyfikacji odpowiadającym odpowiednią).  
  
     Funkcja `void operator delete(void *, size_t)` został umieszczania operatora delete, odpowiadające nowej funkcji umieszczania "void \* nowy operator (size_t, size_t)" w języku C ++ 11. Z języka C ++ 14 dezalokacji rozmiarze, ta funkcja delete jest teraz *funkcja dezalokacji zwykle* (operator delete globalne). Standard wymaga użycia nowego położenia wyszukuje odpowiedniej funkcji usuwania, znajduje się funkcja dezalokacji zwykle program źle sformułowane.  
  
     Na przykład załóżmy, że kod definiuje zarówno nowego położenia i usuwania umieszczania:  
  
    ```  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     Wystąpił problem z powodu dopasowania w podpisach funkcja między umieszczania operatora delete, które zdefiniowany przez użytkownika, a nowy operator delete o rozmiarze globalnych. Należy rozważyć, czy można użyć innego typu niż size_t do dowolnego umieszczania nowych i delete — operatory.  Należy pamiętać, że typ size_t typedef zależne od kompilatora; jest typedef dla unsigned int w programie Visual C++. Dobrym rozwiązaniem jest używany typ wyliczeniowy takich jak ta:  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     Zmień definicja umieszczania nowe, a następnie, Usuń, aby użyć tego typu jako drugi argument zamiast size_t. Należy również zaktualizować wywołania do umieszczenia nowego przekazać nowy typ (na przykład za pomocą `static_cast<my_type>` do przekonwertowania z wartością całkowitą) i nowych aktualizacji definicji i Usuń można rzutować typu Liczba całkowita. Nie trzeba używać wyliczenia dla tej; Typ klasy z elementem członkowskim size_t również będzie działać.  
  
     Alternatywnego rozwiązania jest, że można całkowicie wyeliminować umieszczania nowej. Jeśli kod używa umieszczania nowej implementacji puli pamięci, gdy argument umieszczania rozmiar jest obiekt przydzielony lub usunięty, to funkcja cofania alokacji o rozmiarze może być swoim własnym kodem puli pamięci niestandardowych zastąpienie i można pozbyć się z umieszczanie funkcje i użyć własnych operatora delete dwuargumentowej zamiast funkcji umieszczania.  
  
     Jeśli nie chcesz natychmiast zaktualizować kodu, możesz przywrócić poprzednie działanie przy użyciu opcji kompilatora /Zc:sizedDealloc-. Jeśli używasz tej opcji, funkcje delete dwuargumentowej nie istnieje i nie powoduje konfliktu z operatorem delete umieszczania.  
  
-   **Elementy członkowskie danych Unii**  
  
     Elementy członkowskie danych Unii nie mogą mieć typów referencyjnych. Poniższy kod skompilowany pomyślnie w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale powoduje błąd w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
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
  
-   Związki anonimowe są teraz więcej zgodność ze standardem. Poprzednie wersje kompilatora generowane jawny Konstruktor i destruktor dla elementu związki anonimowe. Są one usuwane z [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
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
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     Aby rozwiązać ten problem, należy podać własne definicje Konstruktor i/lub destruktor.  
  
    ```  
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
  
-   **Unie z struktury anonimowe**  
  
     Aby można było zgodne ze standardem, zachowania w czasie wykonywania została zmieniona dla elementów członkowskich struktury anonimowe w Unii. Konstruktor elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie po utworzeniu takiej Unii. Ponadto destruktor dla elementu elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie przypadku Unii wykracza poza zakres. Rozważmy następujący kod, w którym Unii U zawiera strukturę anonimowe, zawierający element, który jest strukturą nazwanego S, która ma destruktor.  
  
    ```  
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
  
    ```  
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
  
    ```  
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
  
-   **Szablon rozwiązania**  
  
     Zmiany zostały wprowadzone do rozpoznawania nazw dla szablonów. W języku C++, rozważając kandydatów do rozpoznawania nazw można go sprawę, że jedną lub więcej nazw pod uwagę jako potencjalny dopasowań powoduje utworzenie wystąpienia szablonu jest nieprawidłowa. Te nieprawidłowe wystąpień nie powodują zwykle błędy kompilatora, zasady, znany jako techniki SFINAE (podstawienie niepowodzenia nie błąd jest).  
  
     Teraz Jeśli techniki SFINAE wymaga kompilatora, można utworzyć wystąpienia specjalizacji szablonu klasy, wszystkie błędy w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator będzie ignorować takie błędy. Rozważmy na przykład następujący kod:  
  
    ```  
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
  
-   **Kopiowanie konstruktorów**  
  
     W obu [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] i programu Visual Studio 2015, kompilator generuje Konstruktor kopiujący dla klasy, jeśli tej klasy ma Konstruktor przenoszący zdefiniowane przez użytkownika, ale nie Konstruktor kopiujący zdefiniowane przez użytkownika. W Dev14 ten Konstruktor kopiujący niejawnie wygenerowany jest również oznaczone jako "= delete".  
  
##  <a name="VS_Update1"></a>Ulepszenia zgodność aktualizacji 1  
  
-   **Prywatne wirtualne klasy podstawowe i pośredniego dziedziczenia**  
  
     Poprzednie wersje kompilatora dozwolone klasy pochodnej w celu wywołania funkcji Członkowskich jego *pośrednio pochodzi* `private virtual` klasy podstawowej. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator nie akceptuje kod napisany w ten sposób i w związku z tym problemów błąd kompilatora C2280.  
  
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
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **Przeciążony operator new ani operator delete**  
  
     Poprzednie wersje kompilatora dozwolone niebędący elementem członkowskim `operator new` i niebędący elementem członkowskim `operator delete` być zadeklarowany jako statyczny i można zadeklarować w przestrzeni nazw innej niż globalna przestrzeń nazw.  To zachowanie starego utworzone ryzyko, że program nie może wywołać `new` lub `delete` implementacji operator, który przeznaczony programistę, co powoduje zachowanie dyskretnej zły środowiska wykonawczego. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2323 zamiast tego.  
  
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
  
     Ponadto mimo że kompilator nie zapewnia określonych diagnostyczne, nowy operator wbudowanego jest uważany za źle sformułowane.  
  
-   **Wywołanie "operator *typu*()" (konwersja zdefiniowana przez użytkownika) dla typów innych niż klasa**  
  
     Poprzednie wersje kompilatora dozwolone "operator *typu*() ' ma być wywoływana dla typów innych niż klasa podczas w trybie dyskretnym zostanie on zignorowany. To zachowanie starego utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2228 zamiast tego.  
  
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
  
-   **Nadmiarowe typename w specyfikatorze specyfikatorze typu**  
  
     Poprzednie wersje kompilatora dozwolone `typename` w specyfikatorze typu rozwinięciem; kod napisany w ten sposób jest semantycznie nieprawidłowy. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C3406 zamiast tego.  
  
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
  
-   **Wnioskowanie typów tablic z listy inicjatora**  
  
     Poprzednie wersje kompilatora nie obsługuje wnioskowanie typów tablic z listy inicjatorów. Kompilator obsługuje teraz ten formularz wnioskowanie typu i, w związku z tym wywołań szablonów funkcji przy użyciu listy inicjatorów teraz może być niejednoznaczna lub innego przeciążenia może wybrany niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program teraz należy jawnie określić zamierzony przez programistę przeciążenia.  
  
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
  
-   **Przywracanie ostrzeżenia instrukcji switch**  
  
     Poprzedni wersji kompilatora usunięte uprzednio istniejące ostrzeżenia dotyczące `switch` instrukcje; te ostrzeżenia zostały przywrócone. Kompilator generuje teraz przywróconej ostrzeżenia, a powiązane z szczególnych przypadkach (w tym przypadku domyślnego) są teraz wyświetlane ostrzeżenia na wiersz zawierający w przypadku ataku, a nie w ostatnim wierszu instrukcji switch. W związku z tym teraz wydawania tych ostrzeżeń w wierszach innego niż w przeszłości, ostrzeżenia poprzednio pominąć przy użyciu `#pragma warning(disable:####)` nie może zostać pominięta, zgodnie z założeniami. Aby pominąć te ostrzeżenia, zgodnie z założeniami, może być konieczne przenieść `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszym przypadku potencjalnie naruszeń. Poniżej przedstawiono przywróconej ostrzeżenia.  
  
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
  
-   **#include: użycie specyfikatora katalogu nadrzędnego '..' w pathname** (dotyczy tylko/Wall /WX)  
  
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
  
-   **#pragma optimize() rozciąga się poza koniec pliku nagłówka** (dotyczy tylko/Wall /WX)  
  
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
  
-   **Niezgodne #pragma warning(push)** i **#pragma warning(pop)** (dotyczy tylko/Wall /WX)  
  
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
  
-   **Niedopasowane #pragma warning(push)** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora nie wykrył niedopasowane `#pragma warning(push)` zmiany na końcu jednostce tłumaczenia stanów. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C5032 w lokalizacji niedopasowane #pragma warning(push), jeśli włączone. To ostrzeżenie zostanie wyświetlone tylko, jeśli nie ma żadnych błędów kompilacji w jednostce tłumaczenia.  
  
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
  
-   **Może zostać wygenerowany dodatkowych ostrzeżeń wyniku śledzenia stanu ostrzeżenia #pragma ulepszone**  
  
     Poprzednie wersje kompilatora śledzone ostrzeżenia #pragma zmian stanu niewystarczająco również do wystawienia przeznaczone wszystkie ostrzeżenia. To zachowanie utworzony ryzyka to pewność, że ostrzeżenia będzie efektywnie pomijane w sytuacjach innych niż programisty przeznaczone. Kompilator teraz śledzi stan ostrzeżenia #pragma bardziej niezawodnie — szczególnie odnoszących się do zmian stanu ostrzeżenia #pragma wewnątrz szablonów — i opcjonalnie wystawia nowe ostrzeżenia C5031 i C5032, które mają pomóc programisty zlokalizować niezamierzone zastosowań `#pragma warning(push)` i `#pragma warning(pop)`.  
  
     Wyniku ulepszone #pragma zmian stanu śledzenia, ostrzeżenia wcześniej niepoprawnie pominięte lub ostrzeżenia dotyczące problemów, które wcześniej misdiagnosed mogą teraz być ostrzeżenie.  
  
-   **Ulepszenia identyfikacji nieosiągalny kod**  
  
     Standardowa biblioteka C++ zmiany i ulepszona możliwość wywołania funkcji wbudowanej w porównaniu z poprzednimi wersjami kompilatora mogą zezwalać kompilator, aby udowodnić, że niektóre kodu jest nieosiągalny. To nowe zachowanie może spowodować nowych i innych często wydane wystąpień ostrzeżenie C4720.  
  
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
  
##  <a name="VS_Update2"></a>Ulepszenia zgodność aktualizacji 2  
  
-   **Dodatkowych ostrzeżeń i błędów może zostać utworzony w wyniku częściowej obsługi techniki SFINAE wyrażeń**  
  
     Poprzednie wersje kompilatora nie jest przetwarzany niektóre rodzaje wyrażeń wewnątrz `decltype` specyfikatory ze względu na brak obsługi techniki SFINAE wyrażeń. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator teraz analizuje tych wyrażeń i ma częściowej obsługi techniki SFINAE wyrażeń, z powodu trwającej zgodność ulepszenia. W związku z tym kompilator generuje teraz ostrzeżenia i błędy znalezione w wyrażeniach, że poprzednie wersje kompilatora nie jest przetwarzany.  
  
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
  
-   `volatile`**zmienne Członkowskie zapobiec niejawnie zdefiniowanych konstruktorów i operatory przypisania**  
  
     Poprzednie wersje kompilatora dozwolone klasy, która ma `volatile` skopiowania/przeniesienia konstruktorów zmienne Członkowskie mają domyślne i domyślne operatory przypisania kopiowania/przenoszenia generowane automatycznie. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator uwzględnia teraz klasę, która ma zmiennych Członkowskich volatile nieuproszczony konstrukcji i operatory przypisania co zapobiega domyślnej implementacji tych operatorów są generowane automatycznie.  Jeśli taka klasa jest elementem członkowskim Unii (lub anonimowego związku wewnątrz klasy), konstruktorach kopiowania/przenoszenia i operatory przypisania skopiowania/przeniesienia Unii (lub klasy zawierającej Unii unonymous) będzie można niejawnie zdefiniowany jako usunięty. Podjęto próbę utworzenia lub skopiuj Unii (lub klasa zawierająca anonimowa Unia) bez jawnie definiując je w związku z tym jest błąd i błąd kompilatora problemów kompilatora C2280.  
  
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
  
-   **Statyczne funkcje Członkowskie nie obsługują kwalifikatorów cv.**  
  
     Poprzednie wersje programu Visual C++ 2015 dozwolone statycznych funkcji Członkowskich mają kwalifikatorów cv. To zachowanie jest spowodowane Regresja w programie Visual C++ 2015 i Visual C++ 2015 Update 1; Visual C++ 2013 i poprzednie wersje programu Visual C++ odrzucić kod napisany w ten sposób. Zachowanie środowiska Visual C++ 2015 i Visual C++ 2015 Update 1 jest nieprawidłowa i nie odpowiada C++ standard.  Visual Studio 2015 Update 2 odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2511 zamiast tego.  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     Przykład (przed)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Przykład (po)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **Deklaracja przekazująca dalej wyliczenie nie jest dozwolona w kodzie WinRT** (dotyczy tylko /ZW)  
  
     Kodu skompilowanego dla środowiska uruchomieniowego systemu Windows (WinRT) nie zezwala na `enum` typów do przodu, podobnie do podczas kompilowania kodu zarządzanego języka C++ dla programu .net Framework za pomocą kompilatora/CLR przełącznika. Jest to zachowanie gwarantuje, że rozmiar wyliczenie zawsze jest znany i może zostać poprawnie przedstawione w systemie typu WinRT. Kompilator odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2599 wraz z błąd kompilatora C3197.  
  
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
  
-   **Przeciążony operator niebędący elementem członkowskim nowe ani operator delete nie można zadeklarować wbudowanego** (poziom 1 (/ W1) na domyślnie)  
  
     Poprzednie wersje kompilatora nie ostrzeżenie podczas niebędący elementem członkowskim operator new ani operator delete funkcje są deklarowane jako śródwierszowe. Kod napisany w ten sposób jest niepoprawnie sformułowanych (Diagnostyka nie jest wymagane) i może spowodować pamięci problemy wynikające z niezgodne new i delete — operatory (zwłaszcza gdy jest używany z cofania alokacji o rozmiarze), które mogą być trudne do diagnozowania.   Kompilator generuje teraz kompilatora ostrzeżenie C4595 zidentyfikować kod napisany w ten sposób.  
  
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
  
##  <a name="VS_Update3"></a>Ulepszenia zgodność aktualizacji 3  
  
-   **STD::is_convertable teraz wykrywane jest przypisanie własne** (standardowa biblioteka)  
  
     Poprzednie wersje `std::is_convertable` typu cechy nie poprawnie wykrył przypisanie własne typu klasy, po usunięciu jej Konstruktor kopiujący lub prywatnej. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie `false` po zastosowaniu do typu klasy z konstruktorami kopiowania usunięte lub prywatnej.  
  
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
  
-   **Domyślnie lub usunięty trivial kopiowania i przenoszenia specyfikatory dostępu względem konstruktorów**  
  
     Poprzednie wersje kompilatora nie Sprawdź specyfikator dostępu do kopii trivial domyślne lub został usunięty i Przenieś konstruktorów przed umożliwieniem jej do wywołania. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. W niektórych przypadkach to stare zachowanie utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator teraz sprawdza specyfikator dostępu do kopii trivial domyślne lub został usunięty i Przenieś konstruktorów w celu ustalenia, czy można wywołać, a jeśli nie, kompilator problemów w związku z tym ostrzeżenie C2248.  
  
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
  
-   **Amortyzacja oparte na atrybutach obsługi kodu ATL** (poziom 1 (/ W1) na domyślnie)  
  
     Poprzednie wersje kompilatora obsługiwane przypisane kodu biblioteki ATL. Jako następnej fazy usunięta obsługa ATL z atrybutami kod, który [rozpoczął się w programie Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), oparte na atrybutach kodu biblioteki ATL jest przestarzałe. Kompilator generuje teraz C4467 do identyfikowania tego rodzaju przestarzały kod ostrzeżenia kompilatora.  
  
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
  
-   **Prekompilowanych plików nagłówka (PCH) i jest niezgodny # dyrektywy include** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora zaakceptowane niezgodne `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Kompilator teraz niezgodne kompilatora problemów ostrzeżenie CC4598 zidentyfikować `#include` dyrektywy podczas korzystania z plików PCH.  
  
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
  
-   **Prekompilowanych plików nagłówka (PCH) i jest niezgodny Dołącz katalogi** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora zaakceptowane niezgodne katalog dołączania (`-I`) argumenty wiersza polecenia dla kompilatora między `-Yc` i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Katalog dołączania kompilatora teraz kompilatora problemów ostrzeżenie CC4599 zidentyfikować niezgodne (`-I`) argumenty wiersza polecenia, korzystając z plików PCH.  
  
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