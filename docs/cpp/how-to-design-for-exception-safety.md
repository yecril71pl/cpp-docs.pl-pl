---
title: 'How to: Design for exception safety'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
ms.openlocfilehash: 48a2f5a94eb2695c0a08a0ae397d02080e7e1261
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246517"
---
# <a name="how-to-design-for-exception-safety"></a>How to: Design for exception safety

Jedna z zalet mechanizmu wyjątków polega na tym, że wykonywanie, wraz z danymi o wyjątku, przechodzi bezpośrednio z instrukcji generującej wyjątek do pierwszej instrukcji „catch” zdolnej go obsłużyć. Program obsługi może się znajdować o dowolną liczbę poziomów wyżej w stosie wywołań. Funkcje wywoływane między instrukcjami „try” i „throw” nie muszą nic wiedzieć o zgłaszanym wyjątku.  Muszą jednak być zaprojektowane w taki sposób, aby mogły wykroczyć poza zakres „niespodziewanie” w każdym momencie, gdy istnieje ryzyko rozpowszechnienia wyjątku z niższego poziomu, nie pozostawiając przy tym za sobą żadnych częściowo utworzonych obiektów, przecieków pamięci ani struktur danych w bezużytecznych stanach.

## <a name="basic-techniques"></a>Basic techniques

Zasady obsługi wyjątków powinny być odpowiednio zaawansowane, starannie przemyślane i stanowić integralną część procesu projektowania. Zazwyczaj większość wyjątków jest wykrywanych i zgłaszanych w niższych warstwach modułów oprogramowania, jednak zwykle warstwy te dysponują za małą ilością kontekstu, aby odpowiednio postępować z błędami lub wysyłać komunikaty użytkownikom końcowym. W środkowych warstwach funkcje mogą przechwytywać wyjątki i je ponownie zgłaszać w trakcie badania obiektów powodujących wyjątki albo zawierają dodatkowe przydatne informacje, które mogą przekazywać na wyższe warstwy ostatecznie przechwytujące te wyjątki. Funkcja powinna wychwytywać i „wchłaniać” wyjątek tylko wtedy, gdy po takiej operacji jest w stanie całkowicie wrócić do normalnego działania. W wielu przypadkach właściwym działaniem w środkowych warstwach jest zezwolenie na przekazanie wyjątku w górę stosu. Nawet w najwyższej warstwie odpowiednim zachowaniem może być pozwolenie nieobsługiwanemu wyjątkowi na przerwanie działania programu, jeśli miałby on pozostawić program w stanie nie gwarantującym jego poprawnego działania.

Bez względu na to, jak funkcja obsługuje wyjątek, w celu zagwarantowania jej „bezpieczeństwa pod względem wyjątków” musi być zaprojektowana zgodnie z poniższymi podstawowymi zasadami.

### <a name="keep-resource-classes-simple"></a>Keep resource classes simple

When you encapsulate manual resource management in classes, use a class that does nothing except manage a single resource. By keeping the class simple, you reduce the risk of introducing resource leaks. Use [smart pointers](smart-pointers-modern-cpp.md) when possible, as shown in the following example. Przykład jest celowo sztuczny i uproszczony, aby podkreślić różnice względem stosowania wskaźników `shared_ptr`.

```cpp
// old-style new/delete version
class NDResourceClass {
private:
    int*   m_p;
    float* m_q;
public:
    NDResourceClass() : m_p(0), m_q(0) {
        m_p = new int;
        m_q = new float;
    }

    ~NDResourceClass() {
        delete m_p;
        delete m_q;
    }
    // Potential leak! When a constructor emits an exception,
    // the destructor will not be invoked.
};

// shared_ptr version
#include <memory>

using namespace std;

class SPResourceClass {
private:
    shared_ptr<int> m_p;
    shared_ptr<float> m_q;
public:
    SPResourceClass() : m_p(new int), m_q(new float) { }
    // Implicitly defined dtor is OK for these members,
    // shared_ptr will clean up and avoid leaks regardless.
};

// A more powerful case for shared_ptr

class Shape {
    // ...
};

class Circle : public Shape {
    // ...
};

class Triangle : public Shape {
    // ...
};

class SPShapeResourceClass {
private:
    shared_ptr<Shape> m_p;
    shared_ptr<Shape> m_q;
public:
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }
};
```

### <a name="use-the-raii-idiom-to-manage-resources"></a>Use the RAII idiom to manage resources

To be exception-safe, a function must ensure that objects that it has allocated by using `malloc` or **new** are destroyed, and all resources such as file handles are closed or released even if an exception is thrown. The *Resource Acquisition Is Initialization* (RAII) idiom ties management of such resources to the lifespan of automatic variables. Kiedy funkcja wykracza poza swój zakres, powracając do stanu wyjściowego normalnie lub z powodu wyjątku, następuje wywołanie destruktorów wszystkich w pełni skonstruowanym automatycznych zmiennych. Obiekt otoki idiomu RAII, taki jak inteligentny wskaźnik, wywołuje w destruktorze odpowiednią funkcje usunięcia lub zamknięcia. W kodzie bezpiecznym pod względem wyjątków kluczowe znaczenie ma natychmiastowe przekazywanie własności każdego zasobu do jakiegoś obiektu RAII. Note that the `vector`, `string`, `make_shared`, `fstream`, and similar classes handle acquisition of the resource for you.  However, `unique_ptr` and traditional `shared_ptr` constructions are special because resource acquisition is performed by the user instead of the object; therefore, they count as *Resource Release Is Destruction* but are questionable as RAII.

## <a name="the-three-exception-guarantees"></a>The three exception guarantees

Typically, exception safety is discussed in terms of the three exception guarantees that a function can provide: the *no-fail guarantee*, the *strong guarantee*, and the *basic guarantee*.

### <a name="no-fail-guarantee"></a>No-fail guarantee

Gwarancja braku niepowodzenia (lub „braku zgłaszania wyjątków”) jest najsilniejszą gwarancją, jaką może zapewnić funkcja. Stwierdza, że funkcja nie będzie generować wyjątków ani nie pozwoli ich rozpowszechnianie. Gwarancji takiej można wiarygodnie udzielić tylko w przypadku, gdy (a) wiadomo, że wszystkie funkcje wywoływane przez tę funkcję również zapewniają brak niepowodzeń, lub (b) wiadomo, że wszystkie zgłaszane wyjątki są przechwytywane zanim dotrą do tej funkcji, lub (c) wiadomo, jak poprawnie przechwytywać i obsługiwać wszystkie wyjątki mogące docierać do tej funkcji.

Zarówno gwarancja silna, jak i gwarancja podstawowa bazują na założeniu, że destruktory gwarantują brak niepowodzenia. Wszystkie kontenery i typy w bibliotece standardowej gwarantują, że ich destruktory nie zgłaszają wyjątków. Istnieje również wymóg przeciwny: biblioteka standardowa wymaga, aby przekazywane do niej typy zdefiniowane przez użytkownika, na przykład jako argumenty szablonu, zawierały destruktory niezgłaszające wyjątków.

### <a name="strong-guarantee"></a>Strong guarantee

Silna gwarancja stwierdza, że jeśli funkcja wykroczy poza swój zakres z powodu wyjątku, nie nastąpi w niej przeciek pamięci, a stan programu nie ulegnie zmianie. Funkcja zapewniająca silną gwarancję jest zasadniczo transakcją o semantyce zatwierdzenia lub wycofania. Albo kończy się pełnym sukcesem, albo nie powoduje żadnego efektu.

### <a name="basic-guarantee"></a>Basic guarantee

Gwarancja podstawowa jest najsłabsza. Może być jednak najlepszym rozwiązaniem, jeśli silna gwarancja zbyt mocno obciąża pamięć albo inne zasoby systemu. Stwierdza, iż w przypadku wystąpienia wyjątku nie następuje przeciek pamięci, a obiekt nadal znajduje się użytecznym stanie, chociaż jego dane mogły ulec modyfikacji.

## <a name="exception-safe-classes"></a>Exception-safe classes

Klasa może pomagać gwarantować swoje własne bezpieczeństwo pod względem wyjątków, nawet jeśli jest wykorzystywana przez niezabezpieczone funkcje. Wystarczy, że uniemożliwia swoje częściowe konstruowanie i częściowe niszczenie. Jeśli działanie konstruktora klasy zostaje przerwane przed zakończeniem całego procesu, obiekt nie powstaje i konstruktor nigdy nie będzie wywoływany. Mimo iż będą wywoływane konstruktory zmiennych automatycznych zainicjowanych przed zaistnieniem wyjątku, dojdzie do przecieku dynamicznie przydzielonej pamięć lub zasobów, które nie są zarządzane przez inteligentny wskaźnik lub podobną zmienną automatyczną.

Wszystkie typy wbudowane gwarantują brak niepowodzenia, a typy w bibliotece standardowej obsługują co najmniej gwarancję podstawową. Dla wszystkich typów zdefiniowanych przez użytkownika, które muszą być bezpieczne pod względem wyjątków, należy przestrzegać następujących wytycznych:

- Do zarządzania wszystkimi zasobami używaj inteligentnych wskaźników lub innych otok typu RAII. Staraj się nie umieszczać funkcji zarządzania zasobami w destruktorach klas, ponieważ gdy konstruktor zgłosi wyjątek, destruktor nie będzie wywoływany. Jeśli jednak klasa jest dedykowanym menedżerem zasobów kontrolującym dokładnie jeden zasób, można użyć destruktora do zarządzania zasobami.

- Pamiętaj, że wyjątek zgłoszony w konstruktorze klasy bazowej nie może zostać wchłonięty w konstruktorze klasy pochodnej. Jeśli chcesz dokonać translacji wyjątku klasy bazowej i wygenerować go ponownie w konstruktorze klasy pochodnej, użyj bloku funkcji „try”.

- Rozważ, czy wszystkie stany klasy mają być przechowywane w składowej danych opakowanej w inteligentny wskaźnik, szczególnie jeśli klasę utworzono według koncepcji „inicjalizacja, która może się zakończyć niepowodzeniem”. Mimo iż język C++ dopuszcza niezainicjowane składowe danych, nie obsługuje niezainicjowanych ani częściowo zainicjowanych wystąpień klas. Działanie konstruktora musi się kończyć się sukcesem lub niepowodzeniem. Jeśli konstruktor nie wykona swojego pełnego procesu, nie zostanie utworzony żaden obiekt.

- Nie pozwól, aby jakikolwiek wyjątek został pominięty przez destruktora. Podstawowy aksjomat języka C++ mówi, że destruktory nigdy nie powinny pozwalać na przekazywanie wyjątków do wyższych poziomów stosu wywołań. Jeśli destruktor musi wykonać operację, która może się skończyć zgłoszeniem wyjątku, musi zrobić to w bloku „try catch” i wchłonąć wyjątek. Standardowa biblioteka zapewnia tę gwarancję wszystkim destruktorom, które definiuje.

## <a name="see-also"></a>Zobacz także

[Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)<br/>
[Instrukcje: interfejs między kodem obsługi wyjątków a innym kodem](how-to-interface-between-exceptional-and-non-exceptional-code.md)
