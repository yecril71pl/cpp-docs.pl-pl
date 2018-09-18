---
title: Witamy z powrotem na C++ (Modern C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8bb45f18c38323f8c5e56a7b9bd6148bb1ca6142
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070839"
---
# <a name="welcome-back-to-c-modern-c"></a>Zapraszamy ponownie do języka C++ (Modern C++)

Język C++ jest jednym z najczęściej używanych języków programowania na świecie. Dobrze napisane programy ++ są szybkie i wydajne. Język jest bardziej elastyczny niż inne języki, ponieważ służy do tworzenia szerokiej gamy aplikacji — od zabawnych i emocjonujących gier do wysokiej wydajności naukowego oprogramowania, sterowników urządzeń, programów osadzonych i aplikacji klienckich Windows. Ponad 20 lat firma C++ został użyty do rozwiązywania problemów, takich jak te i wiele innych. Co możesz nie znać jest, że rosnąca liczba programistów C++ ma składanych zapasową wyświechtanego stylu programowania C już przeszłość i przyjęła nowoczesny C++, zamiast tego.

Jednym z pierwotnych wymagań w zakresie języka C++ była zgodność ze starszymi wersjami przy użyciu języka C. Od tamtej pory C++ został przekształcony za pomocą kilku iteracji — C z klasami, a następnie pierwotną specyfikacją języka C++ i następnie wieloma kolejnymi rozszerzeniami. Z powodu tego dziedzictwa C++ często nazywa się wielo paradygmowym językiem programowania. W języku C++ można wykonać czysto proceduralne programowania stylu C, które obejmuje surowe wskaźniki, tablice, ciągi znaków zakończone symbolem null, struktury danych niestandardowych i inne funkcje, które mogą umożliwić doskonałą wydajność, ale także mogą mnożyć błędy i złożoności.  Ponieważ programowania stylu C jest obarczone zagrożeniami takimi jak te, jednym z celów założenia dla języka C++ jest wykonywanie programów zarówno bezpiecznego typu i łatwiejsze do pisania, rozszerzenia i utrzymywania. Na wczesnym etapie C++ przyjął modele programowania takich jak programowanie zorientowane obiektowo. W ciągu lat funkcje zostały dodane do języka, łącznie z wysoce testowanymi bibliotekami standardowymi struktur danych i algorytmów. To te dodatki, które umożliwiły współczesny styl C++ możliwe.

Podkreśla nowoczesny język C++:

- Zakres oparty na stosie, zamiast stosu lub stercie lub globalnego zakresu statycznego.

- Auto wnioskowanie zamiast nazw typu jawnego.

- Sprytne wskaźniki zamiast surowych wskaźników.

- `std::string` i `std::wstring` typów (zobacz [ \<ciągu >](../standard-library/string.md)) a nie raw `char[]` tablic.

- [Standardowa biblioteka C++](../standard-library/cpp-standard-library-header-files.md) kontenery `vector`, `list`, i `map` zamiast surowych tablic czy kontenerów niestandardowych. Zobacz [ \<wektor >](../standard-library/vector.md), [ \<listy >](../standard-library/list.md), i [ \<mapy >](../standard-library/map.md).

- Standardowa biblioteka C++ [algorytmy](../standard-library/algorithm.md) zamiast ręcznie kodowanych.

- Wyjątki, raport i obsługują warunki błędu.

- Komunikacja między wątku komunikacji przy użyciu standardowej biblioteki języka C++ wolne od blokady `std::atomic<>` (zobacz [ \<atomic >](../standard-library/atomic.md)) zamiast innych mechanizmów komunikacji między wątku.

- Wbudowane [funkcje lambda](../cpp/lambda-expressions-in-cpp.md) zamiast małych funkcji realizowanych oddzielnie.

- Zakresu pętli for opierających do pisania bardziej niezawodnych pętli, współpracujących z tablic, kontenery standardowej biblioteki języka C++ i środowiska wykonawczego Windows w postaci `for ( for-range-declaration : expression )`. Jest to część obsługi rdzenia języka. Aby uzyskać więcej informacji, zobacz [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

Sam język C++ także się rozwinął. Porównaj następujące fragmenty kodu. To pokazuje jak kiedyś w języku C++:

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

Poniżej przedstawiono, jak to samo jest realizowane w nowoczesnym C++:

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

W nowoczesnym C++ nie trzeba używać nowy/Usuń lub obsługi jawnych wyjątków ponieważ zamiast tego można użyć sprytnych wskaźników. Kiedy używasz **automatycznie** Ustalanie typu z i [funkcji lambda](../cpp/lambda-expressions-in-cpp.md), można napisać kod szybciej, zacieśniać go i lepiej zrozumieć. I opartej na zakresie **dla** pętla jest bardziej przejrzysty, łatwiejszy w obsłudze i mniej podatny na błędy niezamierzone niż stylu C **dla** pętli. Standardowy wraz z minimalnym wierszy kodu można użyć, aby napisać własną aplikację. I sprawić, że kod wyjątku i pamięci są bezpieczne i mają nie alokacji/dezalokacji ani kodów błędu do przeciwdziałania.

Nowoczesny język C++ zawiera dwa rodzaje polimorfizmu: kompilacji, za pomocą szablonów i środowisko wykonawcze, poprzez dziedziczenie i wirtualizację. Możesz mieszać dwa rodzaje polimorfizmu, aby efekt. Szablon standardowej biblioteki języka C++ `shared_ptr` używa wewnętrznych metod wirtualnych, aby wykonać jego usunięcie pozoru typu. Ale nie nadużywaj na wirtualizacji dla polimorfizmu, gdy szablon jest lepszym rozwiązaniem. Szablony mogą być bardzo skuteczne.

Jeśli podchodzisz do języka C++ w innym języku, zwłaszcza z języka zarządzanego, w którym większość typów stanowią typy odwołań, i tylko kilka to typy wartości, należy wiedzieć, że klasy C++ są domyślnie typami wartości. Jednak możesz je określić jako typy odwołań, aby umożliwić zachowanie polimorficzne, która obsługuje programowanie zorientowane obiektowo. Pomocne perspektywy: typy wartości są są więcej informacji na temat pamięci a układ sterowania, typy odwołań bardziej dotyczą klas podstawowych i funkcji wirtualnych do obsługi polimorfizmu. Typy wartości są domyślnie możliwe do kopiowania — każda z nich Konstruktor kopiujący i operator przypisania kopiowania. Kiedy określasz typ odwołania, Zmień klasę niekopiowalnych — Wyłącz konstruktora kopii i operatora zadań kopiowania — i użyj wirtualnego destruktora, który obsługuje polimorfizm. Typy wartości są również związane z zawartości, które, gdy są one kopiowane zapewniają dwie niezależne wartości, które możesz oddzielnie modyfikować. Ale są typy odwołań dotyczących tożsamości — jaki rodzaj obiektu jest — i z tego powodu są czasami określane jako polimorficzne typy.

C++ przeżywa odrodzenia, ponieważ moc jest ponownie królem. W językach Java i C# są dobre, gdy wydajność pracy programisty jest ważna, ale wykazują swoje ograniczenia, gdy moc i wydajność mają ogromne znaczenie. Wysokiej wydajności i mocy, zwłaszcza na urządzeniach, które mają ograniczenia sprzętowe nic nie uderzeń nowoczesnym języku C++.

Nie tylko język jest nowoczesny, narzędzia programistyczne są zbyt. Program Visual Studio sprawia, że wszystkie części cyklu rozwoju odporne i wydajne. Obejmuje narzędzia do zarządzania cyklem życia aplikacji (ALM), ulepszenia IDE, takie jak IntelliSense, mechanizmy z przyjaznymi narzędzie narzędziami jak XAML i kompilowanie, debugowanie i wiele innych narzędzi.

Artykuły w tej części dokumentacji zapewniają wytyczne wysokiego poziomu i najlepsze praktyki dotyczące najważniejszych funkcji i technik pisania nowoczesnych programów w C++.

- [System typów języka C++](../cpp/cpp-type-system-modern-cpp.md)

- [Jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Okres istnienia obiektów i zarządzanie zasobami](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Obiekty posiadają zasoby (RAII)](../cpp/objects-own-resources-raii.md)

- [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)

- [Mechanizm Pimpl hermetyzacji w czasie kompilacji](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Kontenery](../cpp/containers-modern-cpp.md)

- [Algorytmy](../cpp/algorithms-modern-cpp.md)

- [Ciągów i we/wy formatowanie (Modern C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Aby uzyskać więcej informacji, zobacz artykuł StackOverflow [jakie idiomy C++ zostały zaniechane w C ++ 11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Wizualne zgodność języka C++](../visual-cpp-language-conformance.md)