---
title: Zapraszamy ponownie do języka C++ (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63e73657c7e018d2a4eb71170561e310aeba9d5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="welcome-back-to-c-modern-c"></a>Zapraszamy ponownie do języka C++ (Modern C++)
C++ jest jednym z najpopularniejszych języków programowania na świecie. Programy dobrze napisane w języku C++ są szybkie i wydajne. Język jest bardziej elastyczna niż innych języków, ponieważ służy do tworzenia szerokiej gamy aplikacji — od fun i gry atrakcyjnych, wysokiej wydajności naukowych oprogramowaniem, sterowników urządzeń, osadzonych programy i aplikacje klienta systemu Windows. Ponad 20 lat C++ został użyty do rozwiązywania problemów, takich jak te i wiele innych. Co może być niemożliwe jest coraz programistów języka C++ ma złożony dowdy programowania stylu języka C wczoraj oraz ma zamiast tego donned nowoczesnych wersji języka C++.  
  
 Jeden z oryginalnego wymagania dla języka C++ jest zgodność z poprzednimi wersjami z językiem C. Od tego czasu powstał C++ za pomocą kilku iteracji — C za pomocą klasy, a następnie oryginalnego specyfikacja języka C++ i następnie wiele udoskonaleń kolejnych. C++ z powodu tego dziedzictwa jest często określany jako języka programowania wielu modelu. W języku C++ możesz to zrobić wyłącznie procedurach programowania stylu języka C, która obejmuje raw wskaźników, tablic ciągów znaków zakończony znakiem null, struktur danych niestandardowych i inne funkcje, które mogą umożliwić doskonałą wydajność, ale można też zduplikować usterki i złożoności.  Ponieważ programowania w języku C-style jest zawsze duże perils, takich jak te, jednym z celów założenia dla języka C++ było programy zarówno bezpieczne i łatwiejsze do zapisu, rozszerzać i konserwacji. Na wczesnym etapie C++ przyjętych wzorcami programowania, takich jak programowanie zorientowane obiektowo. Całościowo funkcje zostały dodane do języka, wraz z wysokiej przetestowane standardowych bibliotek struktur danych i algorytmów. Jest te dodatki, które mają możliwe stylu modern C++.  
  
 Zwrócono szczególną uwagę na nowoczesnych wersji języka C++:  
  
-   Zakres opartego na stosie, zamiast stosu lub statycznego zakresu globalnego.  
  
-   Wnioskowanie o typie automatycznie zamiast jawnego typu nazw.  
  
-   Wskaźniki inteligentne zamiast wskaźniki raw.  
  
-   `std::string` i `std::wstring` typów (zobacz [ \<ciąg >](../standard-library/string.md)) zamiast raw `char[]` tablic.  
  
-   [Standardowa biblioteka C++](../standard-library/cpp-standard-library-header-files.md) , takich jak kontenery `vector`, `list`, i `map` zamiast tablice raw lub niestandardowych kontenerów. Zobacz [ \<wektor >](../standard-library/vector.md), [ \<listy >](../standard-library/list.md), i [ \<mapy >](../standard-library/map.md).  
  
-   Standardowa biblioteka C++ [algorytmy](../standard-library/algorithm.md) zamiast ręcznie kodowanego te.  
  
-   Wyjątki, raport i obsługi błędów.  
  
-   Blokady bez komunikacji między wątku przy użyciu standardowej biblioteki C++ `std::atomic<>` (zobacz [ \<atomic >](../standard-library/atomic.md)) zamiast innych mechanizmów komunikacji między wątku.  
  
-   Wbudowany [funkcje lambda](../cpp/lambda-expressions-in-cpp.md) zamiast małe funkcje zaimplementowana oddzielnie.  
  
-   Na podstawie zakresu dla pętli do zapisania pętle bardziej niezawodne, które współpracują z tablic, kontenery standardowa biblioteka C++ i środowiska wykonawczego systemu Windows w postaci `for ( for-range-declaration : expression )`. Jest to część obsługi języka podstawowego. Aby uzyskać więcej informacji, zobacz [opartej na zakresie — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md).  
  
 Również powstał języka C++, do samej siebie. Porównaj poniższe fragmenty kodu. Ta pokazuje, jak używać w języku C++:  
  
```cpp  

#include <vector>

void f()
{
    // Assume circle and shape are user-defined types  
    circle* p = new circle( 42 );   
    vector<shape*> v = load_shapes();  

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {  
        if( *i && **i == *p )  
            cout << **i << " is a match\n";  
    }  

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();  
            i != v.end(); ++i ) {  
        delete *i; // not exception safe  
    }  

    // Don't forget to delete this, too.  
    delete p;  
} // end f()
```

 Oto jak to samo odbywa się w nowoczesnych wersji języka C++:  
  
```cpp

#include <memory>  
#include <vector>  

void f()
{
    // ...  
    auto p = make_shared<circle>( 42 );  
    vector<shared_ptr<shape>> v = load_shapes();  

    for( auto& s : v ) 
    {  
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}

```

 W nowoczesnych wersji języka C++ nie trzeba używać nowych lub usuń lub obsługi, ponieważ wskaźniki inteligentne mogą używać zamiast niej jawne wyjątków. Jeśli używasz `auto` wpisz wnioskowanie i [funkcja lambda](../cpp/lambda-expressions-in-cpp.md), można napisać kod szybszy, zwiększyć jego i zrozumienie go lepiej. I opartej na zakresie `for` pętla jest czyszczący, łatwiejsza w użyciu i mniej podatna na błędy niezamierzone niż stylu języka C `for` pętli. Schematyczny wraz z minimalnym wierszy kodu można użyć do pisania aplikacji. I wprowadzić ten kod wyjątek bezpieczny i bezpieczne pamięci i mieć żadnych kodów alokacji/dezalokacji lub błąd radzenia sobie z.  
  
 Modern C++ zawiera dwa rodzaje polimorfizm: kompilacji, za pomocą szablonów i środowiska wykonawczego, za pośrednictwem dziedziczenia i wirtualizacji. Można mieszać dwa rodzaje polimorfizm w celu dużą. Standardowa biblioteka C++ szablonu `shared_ptr` używa wewnętrznego metod wirtualnych celu jego usunięcia najwyraźniej łatwe typu. Ale nie nadmiernie wirtualizacji dla polimorfizm kiedy szablon jest lepszym rozwiązaniem. Szablony mogą być bardzo zaawansowane.  
  
 Jeśli w przypadku wychodzącego C++ w innym języku, szczególnie ze zarządzanego języka, w której większość typów są typy referencyjne i są bardzo nieliczne typy wartości, należy sprawdzić, czy klasy C++ są typy wartości domyślne. Można jednak określić ich jako typów referencyjnych, aby włączyć polimorficznych zachowania, która obsługuje programowanie zorientowane obiektowo. Przydatne perspektywy: typy wartości są więcej informacji o pamięci i formant układu, typy referencyjne więcej informacji na temat klas podstawowych i funkcji wirtualnych do obsługi polimorfizm. Typy wartości są domyślnie copyable — każdy z nich ma konstruktora kopiującego i operatora przypisania kopii. Po określeniu typu odwołania, ustawić klasę z systemem innym niż copyable — Wyłącz konstruktora kopiującego i operatora przypisania kopii — i użyj destruktor wirtualny, który obsługuje polimorfizm. Typy wartości są również dotyczące zawartości, które, gdy są one kopiowane zapewniają dwa niezależne wartości, które można modyfikować oddzielnie. Typy odwołań są o tożsamości, ale — co rodzaj obiektu jest — i z tego powodu są czasami określane jako typach polimorficznych.  
  
 C++ występują odrodzenia ponieważ zasilania jest najważniejsza ponownie. W językach Java i C# są dobrym programisty wydajności jest ważne, ale pokazywały ich ograniczenia, gdy mocy i wydajności są podstawowym. Wysokiej wydajności i zasilania, szczególnie w przypadku urządzeń, które mają ograniczoną sprzętu nic nie uderzeń nowoczesnych wersji języka C++.  
  
 Nie tylko język jest nowoczesnych, narzędzi programistycznych są zbyt. [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] powoduje, że wszystkie części cyklu programowanie niezawodny i efektywny. Obejmuje narzędzia do zarządzania cyklem życia aplikacji (ALM), IDE ulepszenia, takie jak IntelliSense, narzędzie przyjaznego mechanizmów XAML i kompilowanie, debugowanie i wiele innych narzędzi.  
  
 Artykuły w tej części dokumentacji zawierają ogólne wskazówki i najlepsze rozwiązania dotyczące najważniejszych funkcjach i techniki pisanie programów modern C++.  
  
-   [System typów języka C++](../cpp/cpp-type-system-modern-cpp.md)  
  
-   [Jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
-   [Okres istnienia obiektów i zarządzanie zasobami](../cpp/object-lifetime-and-resource-management-modern-cpp.md)  
  
-   [Obiekty posiadają zasoby (RAII)](../cpp/objects-own-resources-raii.md)  
  
-   [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)  
  
-   [Mechanizm pimpl hermetyzacji w czasie kompilacji w czasie](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)  
  
-   [Kontenery](../cpp/containers-modern-cpp.md)  
  
-   [Algorytmy](../cpp/algorithms-modern-cpp.md)  
  
-   [Ciągów i we/wy formatowania (Modern C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)  
  
-   [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)  
  
-   [Przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)  
  
 Aby uzyskać więcej informacji, zobacz artykuł StackOverflow [idioms C++, które zostały uznane za przestarzałe w języku C ++ 11](http://go.microsoft.com/fwlink/p/?linkid=402836)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)  
 [Visual zgodność języka C++](../visual-cpp-language-conformance.md)  
