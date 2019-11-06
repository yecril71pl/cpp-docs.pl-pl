---
title: Zapraszamy ponownie do języka C++ (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 1f59395001722244cb407ef07ed8a301f08df85b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624759"
---
# <a name="welcome-back-to-c-modern-c"></a>Zapraszamy ponownie do języka C++ (Modern C++)

C++jest jednym z najczęściej używanych języków programowania na świecie. Dobrze napisania C++ programy są szybkie i wydajne. Język jest bardziej elastyczny niż inne języki, ponieważ można go używać do tworzenia szerokiej gamy aplikacji — od zabawnych i atrakcyjnych gier, do wysokiej wydajności oprogramowania naukowego, sterowników urządzeń, programów osadzonych i aplikacji klienckich systemu Windows. Przez ponad 20 lat została użyta w celu rozwiązania problemów, C++ takich jak te i wiele innych. To, czego nie wiadomo, jest to, że coraz C++ więcej programistów ma zagiętą wyświechtanego programowanie w stylu C wczoraj i miała zamiast tego C++ nowoczesny donned.

Jedno z oryginalnych wymagań w zakresie C++ zgodności z poprzednimi wersjami w języku C. Od tego czasu C++ program został rozwijający przez kilka iteracji — C z klasami, a C++ następnie oryginalną specyfikacją języka, a następnie wiele kolejnych ulepszeń. Ze względu na to C++ dziedzictwo, często określa się jako język programowania wieloodmianowego. W C++programie można wykonać czysto proceduralne programowanie w stylu C, które obejmuje surowe wskaźniki, tablice, ciągi znaków zakończonych znakiem null, niestandardowe struktury danych i inne funkcje, które mogą zapewnić doskonałą wydajność, ale mogą również spowodować błędy i złożoność.  Ponieważ programowanie w stylu języka C jest fraught z powstawanie, takimi jak te, jeden z celów C++ , dla którego miało na celu zapewnienie, że programy są bezpieczne i łatwiejsze do pisania, zwiększania i konserwowania. Wczesne, C++ założenia programistyczne, takie jak programowanie zorientowane obiektowo. W ciągu lat funkcje zostały dodane do języka wraz z wysoce przetestowanymi standardowymi bibliotekami struktur i algorytmów danych. Są to dodatki, które miały nowoczesne C++ style.

Akcent C++ nowoczesny:

- Zakres oparty na stosie zamiast sterty lub statycznego zakresu globalnego.

- Nie należy wpisywać nazw, a nie typów jawnych.

- Inteligentne wskaźniki zamiast nieprzetworzonych wskaźników.

- typy `std::string` i `std::wstring` (zobacz [\<ciąg >](../standard-library/string.md)) zamiast nieprzetworzonych tablic `char[]`.

- Kontenery biblioteki standardowej, takie jak `vector`, `list`i `map` zamiast nieprzetworzonych tablic lub kontenerów niestandardowych. [ C++ ](../standard-library/cpp-standard-library-header-files.md) Zobacz [\<wektor >](../standard-library/vector.md), [\<listę >](../standard-library/list.md)i [\<mapy](../standard-library/map.md)>.

- C++[Algorytmy](../standard-library/algorithm.md) biblioteki standardowej zamiast ręcznie zakodowane.

- Wyjątki, raportowanie i obsługa błędów.

- Niezależna od blokady komunikacja między wątkami przy użyciu C++ standardowej biblioteki `std::atomic<>` (zobacz [\<niepodzielne >](../standard-library/atomic.md)) zamiast innych mechanizmów komunikacji między wątkami.

- Wbudowane [Funkcje lambda](../cpp/lambda-expressions-in-cpp.md) zamiast małych funkcji wdrożonych osobno.

- Oparte na zakresie pętle do pisania bardziej niezawodnych pętli, które pracują z tablicami, C++ kontenerami biblioteki standardowej i kolekcjami środowisko wykonawcze systemu Windows w `for ( for-range-declaration : expression )`formularzy. Jest to część podstawowej obsługi języka. Aby uzyskać więcej informacji, zobacz [zakres na podstawie instrukcji (C++)](../cpp/range-based-for-statement-cpp.md).

Sam C++ język uległ również ewolucji. Porównaj Poniższe fragmenty kodu. W C++tym przykładzie pokazano, jak są używane następujące elementy:

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

Oto jak te same czynności są wykonywane w nowoczesnej C++:

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

W nowoczesnych C++systemach nie trzeba używać nowych/usuwania ani jawnej obsługi wyjątków, ponieważ zamiast tego można użyć inteligentnych wskaźników. W przypadku korzystania z funkcji odejmowania typu **Autowypełniania** i [lambda](../cpp/lambda-expressions-in-cpp.md)można napisać kod szybciej, wzmocnić go i zrozumieć lepszy. Natomiast pętla **for** oparta na zakresie jest oczyszczarki, łatwiejsza do użycia i mniej podatna na niezamierzone błędy niż w stylu C **dla** pętli. Można używać standardowych razem z minimalnymi wierszami kodu do pisania aplikacji. Można również sprawić, że ten wyjątek kodu jest bezpieczny i bezpieczny dla pamięci i nie ma żadnych alokacji/dealokacji lub kodów błędów, z którymi należy się zająć.

Nowoczesny C++ obejmuje dwa rodzaje polimorfizmu: czas kompilowania, za poorednictwem szablonów i czas wykonywania przez dziedziczenie i wirtualizację. Możesz mieszać dwa rodzaje polimorfizmu, aby uzyskać doskonały efekt. Szablon C++ standardowej biblioteki `shared_ptr` używa wewnętrznych metod wirtualnych do osiągnięcia niełatwego typu, który można wymazać. Jednak nie używaj wirtualizacji w przypadku polimorfizmu, gdy szablon jest lepszym wyborem. Szablony mogą być bardzo wydajne.

C++ Jeśli jesteś w innym języku, szczególnie w języku zarządzanym, w którym większość typów to typy odwołań, a bardzo kilka jest typami wartości, należy pamiętać, że C++ domyślnie klasy są typy wartości. Ale można je określić jako typy referencyjne, aby umożliwić stosowanie zachowań polimorficznych, które obsługują programowanie zorientowane obiektowo. Przydatna perspektywa: typy wartości więcej informacji o pamięci i kontroli układu, typy odwołań są więcej informacji o klasach bazowych i funkcjach wirtualnych do obsługi polimorfizmu. Domyślnie typy wartości są kopiowane — każda z nich ma Konstruktor kopiujący i operator przypisania kopiowania. Po określeniu typu referencyjnego należy sprawić, aby Klasa nie była kopiowana — Wyłącz Konstruktor kopiujący i operator przypisania kopiowania, a następnie użyj destruktora wirtualnego, który obsługuje polimorfizm. Typy wartości są również informacjami o zawartości, które podczas kopiowania są podające dwie niezależne wartości, które można oddzielnie modyfikować. Jednak typy odwołań dotyczą tożsamości — rodzaju obiektu, a z tego powodu są czasami określane jako typy polimorficzne.

C++występuje Renaissance, ponieważ ponownie nastąpiła odmowa. Języki takie jak Java C# i są dobre, gdy produktywność programisty jest ważna, ale pokazują swoje ograniczenia, gdy moc i wydajność są najważniejsze. Aby zapewnić wysoką wydajność i moc, zwłaszcza na urządzeniach z ograniczoną sprzętem, nic nie C++dotyczy nowoczesnego oprogramowania.

Nie tylko język jest nowoczesny, a także narzędzia programistyczne. Program Visual Studio sprawia, że wszystkie części cyklu programowania są niezawodne i wydajne. Obejmuje to narzędzia do zarządzania cyklem życia aplikacji (ALM), usprawnienia środowiska IDE, takie jak IntelliSense, przyjazne dla narzędzia mechanizmy, takie jak XAML i kompilowanie, debugowanie i wiele innych narzędzi.

Artykuły w tej części dokumentacji zawierają ogólne wskazówki i najlepsze rozwiązania dotyczące najważniejszych funkcji i technik pisania nowoczesnych C++ programów.

- [C++System typów](../cpp/cpp-type-system-modern-cpp.md)

- [Jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Okres istnienia obiektu i zarządzanie zasobami](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Obiekty posiadają zasoby (RAII)](../cpp/objects-own-resources-raii.md)

- [Inteligentne wskaźniki](../cpp/smart-pointers-modern-cpp.md)

- [Mechanizm pimpl hermetyzacji do hermetyzacji czasu kompilowania](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Kontenery](../cpp/containers-modern-cpp.md)

- [Algorytmy](../cpp/algorithms-modern-cpp.md)

- [Formatowanie ciągów i we/wy (nowoczesny C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Aby uzyskać więcej informacji, zobacz artykuł Stack Overflow [, C++ które idiomy są przestarzałe w języku c++ 11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Tabela C++ zgodności języka firmy Microsoft](../overview/visual-cpp-language-conformance.md)