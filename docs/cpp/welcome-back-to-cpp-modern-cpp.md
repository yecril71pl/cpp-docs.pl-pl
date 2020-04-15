---
title: Witamy z powrotem w C++ - Modern C++
description: Opisuje nowe idiomy programowania w modern C++ i ich uzasadnienie.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369493"
---
# <a name="welcome-back-to-c---modern-c"></a>Witamy z powrotem w C++ - Modern C++

Od momentu powstania C++ stał się jednym z najczęściej używanych języków programowania na świecie. Dobrze napisane programy C++ są szybkie i wydajne. Język jest bardziej elastyczny niż inne języki: może działać na najwyższych poziomach abstrakcji i w dół na poziomie krzemu. C++ dostarcza wysoce zoptymalizowane biblioteki standardowe. Umożliwia dostęp do niskopoziomowych funkcji sprzętowych, aby zmaksymalizować szybkość i zminimalizować wymagania dotyczące pamięci. Za pomocą języka C++, można utworzyć szeroką gamę aplikacji. Gry, sterowniki urządzeń i wysokowydajne oprogramowanie naukowe. Programy osadzone. Aplikacje klienckie systemu Windows. Nawet biblioteki i kompilatory dla innych języków programowania są zapisywane w języku C++.

Jednym z oryginalnych wymagań dla języka C++ była zgodność wsteczna z językiem C. W rezultacie C++ zawsze dozwolone programowania w stylu C, z nieprzetworzonych wskaźników, tablice, ciągi znaków zakończone z wartością null i inne funkcje. Mogą one umożliwić doskonałą wydajność, ale może również odlać błędy i złożoność. Ewolucja języka C++ podkreśliła funkcje, które znacznie zmniejszają potrzebę używania idiomów w stylu C. Stare urządzenia do programowania C są tam, gdy ich potrzebujesz, ale z nowoczesnym kodem C++ powinieneś ich potrzebować coraz mniej. Nowoczesny kod C++ jest prostszy, bezpieczniejszy, bardziej elegancki i wciąż tak szybki, jak zawsze.

W poniższych sekcjach przedstawiono przegląd głównych cech nowoczesnego języka C++. O ile nie zaznaczono inaczej, funkcje wymienione w tym miejscu są dostępne w języku C++11 i nowszych. W kompilatorze Języka Microsoft C++ można ustawić opcję [kompilatora /std,](../build/reference/std-specify-language-standard-version.md) aby określić, która wersja standardu ma być używana dla projektu.

## <a name="resources-and-smart-pointers"></a>Zasoby i inteligentne wskaźniki

Jedną z głównych klas błędów w programowaniu w stylu C jest *wyciek pamięci.* Przecieki są często spowodowane przez niepodwołowe **wywołanie delete** dla pamięci, która została przydzielona z **nowym**. Modern C++ podkreśla zasadę *pozyskiwania zasobów jest inicjowanie* (RAII). Pomysł jest prosty. Zasoby (pamięć sterty, uchwyty plików, gniazda itd.) powinny być *własnością* obiektu. Ten obiekt tworzy lub odbiera nowo przydzielony zasób w jego konstruktorze i usuwa go w jego destruktora. Zasada RAII gwarantuje, że wszystkie zasoby są prawidłowo zwracane do systemu operacyjnego, gdy obiekt będący właścicielem wykracza poza zakres.

Aby ułatwić wdrażanie zasad RAII, standardowa biblioteka C++ udostępnia trzy inteligentne typy wskaźników: [std::unique_ptr](../standard-library/unique-ptr-class.md), [std::shared_ptr](../standard-library/shared-ptr-class.md)i [std::weak_ptr](../standard-library/weak-ptr-class.md). Inteligentny wskaźnik obsługuje alokacji i usuwania pamięci, której jest właścicielem. Poniższy przykład przedstawia klasę z elementem członkowskim tablicy, który `make_unique()`jest przydzielany na stercie w wywołaniu do . Wywołania **nowych** i **delete** są hermetyzowane przez `unique_ptr` klasę. Gdy `widget` obiekt wykracza poza zakres, unique_ptr destruktora zostanie wywołana i zwolni pamięć, która została przydzielona dla tablicy.  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Jeśli to możliwe, użyj inteligentnego wskaźnika podczas przydzielania pamięci sterty. Jeśli musisz użyć nowych i usunąć operatorów jawnie, postępuj zgodnie z zasadą RAII. Aby uzyskać więcej informacji, zobacz [Okres istnienia obiektu i zarządzanie zasobami (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>std::string i std::string_view

Ciągi w stylu C są kolejnym głównym źródłem błędów. Za pomocą [std::string i std::wstring](../standard-library/basic-string-class.md), można wyeliminować praktycznie wszystkie błędy skojarzone z ciągami w stylu C. Można również uzyskać korzyści z funkcji członkowskich do wyszukiwania, dołączania, poprzedzania i tak dalej. Oba są bardzo zoptymalizowane pod kątem prędkości. Podczas przekazywania ciągu do funkcji, która wymaga tylko dostępu tylko do odczytu, w języku C++17 można użyć [std::string_view](../standard-library/basic-string-view-class.md) dla jeszcze większej wydajności korzyści.

## <a name="stdvector-and-other-standard-library-containers"></a>std::wektor i inne kontenery biblioteki standardowej

Kontenery biblioteki standardowej są zgodne z zasadą RAII. Zapewniają one iteratory dla bezpiecznego przechodzenia elementów. I, są one bardzo zoptymalizowane pod kątem wydajności i zostały dokładnie przetestowane pod kątem poprawności. Za pomocą tych kontenerów, można wyeliminować możliwość błędów lub nieefektywności, które mogą być wprowadzone w strukturach danych niestandardowych. Zamiast nieprzetworzonych tablic należy użyć [wektora](../standard-library/vector-class.md) jako sekwencyjnego kontenera w języku C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [mapy](../standard-library/map-class.md) `unordered_map`(nie) jako domyślnego kontenera zespolowego. Użyj [zestawu,](../standard-library/set-class.md) [multimapy](../standard-library/multimap-class.md)i [zestawu wielokrotnego](../standard-library/multiset-class.md) dla zdegenerowanych i wielu przypadków.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Jeśli potrzebna jest optymalizacja wydajności, należy rozważyć użycie:

- Typ [tablicy](../standard-library/array-class-stl.md) podczas osadzania jest ważne, na przykład jako element członkowski klasy.

- Nieuiszczone kontenery asocenacyjna, takie jak [unordered_map](../standard-library/unordered-map-class.md). Mają one niższe narzutu na element i wyszukiwania w czasie stałym, ale mogą być trudniejsze w użyciu poprawnie i wydajnie.

- Posortowane `vector`. Aby uzyskać więcej informacji, zobacz [Algorytmy](../cpp/algorithms-modern-cpp.md).

Nie używaj tablic w stylu C. W przypadku starszych interfejsów API, które wymagają bezpośredniego `f(vec.data(), vec.size());` dostępu do danych, należy użyć metod akcesorowych, takich jak zamiast tego. Aby uzyskać więcej informacji o kontenerach, zobacz [Kontenery biblioteki standardowej języka C++.](../standard-library/stl-containers.md)

## <a name="standard-library-algorithms"></a>Algorytmy biblioteki standardowej

Zanim założysz, że musisz napisać niestandardowy algorytm dla swojego programu, najpierw przejrzyj [algorytmy](../standard-library/algorithm.md)biblioteki standardowej języka C++ . Biblioteka standardowa zawiera stale rosnący asortyment algorytmów dla wielu typowych operacji, takich jak wyszukiwanie, sortowanie, filtrowanie i randomizowanie. Biblioteka matematyczna jest obszerna. Począwszy od języka C++ 17, dostępne są równoległe wersje wielu algorytmów.

Oto kilka ważnych przykładów:

- **for_each**, domyślny algorytm przechodzenia (wraz z zakresem opartym na pętlach).

- **przekształcenie,** do niewmiejeniem modyfikacji elementów kontenera

- **find_if**, domyślny algorytm wyszukiwania.

- **sortuj** **, lower_bound**, a inne domyślne algorytmy sortowania i wyszukiwania.

Aby napisać komparator, **<** należy użyć ścisłego i użyć *nazwanych lambdas,* gdy można.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto zamiast jawnych nazw typów

W języku C++11 wprowadzono [automatyczne](auto-cpp.md) słowo kluczowe do użycia w deklaracjach zmiennych, funkcji i szablonów. **auto** informuje kompilatora, aby wywniedywać typ obiektu, tak aby nie trzeba wpisywać go jawnie. **auto** jest szczególnie przydatne, gdy wywnioskowany typ jest szablonem zagnieżdżanym:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Oparte na zasięgu pętle

Iteracja w stylu C za pomocą tablic i kontenerów jest podatna na błędy indeksowania i jest również nużąca do typu. Aby wyeliminować te błędy i uczynić kod bardziej czytelnym, użyj pętli opartych na zakresie z kontenerami biblioteki standardowej i tablicami nieprzetworzonymi. Aby uzyskać więcej informacji, zobacz [zakres oparty na instrukcji](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>wyrażenia constexpr zamiast makr

Makra w języku C i C++ są tokeny, które są przetwarzane przez preprocesor przed kompilacją. Każde wystąpienie tokenu makra jest zastępowane jego zdefiniowaną wartością lub wyrażeniem przed skompilowanym plikiem. Makra są powszechnie używane w programowaniu w stylu C do definiowania wartości stałych w czasie kompilacji. Jednak makra są podatne na błędy i trudne do debugowania. W nowoczesnym języku C++ należy preferować zmienne [constexpr](constexpr-cpp.md) dla stałych w czasie kompilacji:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednolita inicjalizacja

W nowoczesnym języku C++ można użyć inicjowania nawiasów klamrowych dla dowolnego typu. Ta forma inicjowania jest szczególnie wygodne podczas inicjowania tablice, wektory lub inne kontenery. W poniższym `v2` przykładzie jest inicjowany z trzech wystąpień `S`. `v3`jest inicjowany z `S` trzech wystąpień, które są same zainicjowane przy użyciu nawiasów klamrowych. Kompilator wywnioskować typ każdego elementu `v3`na podstawie zadeklarowanego typu .

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

Aby uzyskać więcej informacji, zobacz [Inicjowanie nawiasów klamrowych](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Przenoszenie semantyki

Nowoczesny C++ zapewnia *semantyce przenoszenia,* które umożliwiają wyeliminowanie niepotrzebnych kopii pamięci. We wcześniejszych wersjach języka kopie były nieuniknione w niektórych sytuacjach. Operacja *przenoszenia* przenosi własność zasobu z jednego obiektu do następnego bez tworzenia kopii. Podczas implementowania klasy, która jest właścicielem zasobu (takich jak pamięć sterty, uchwyty plików i tak dalej), można zdefiniować *konstruktora przenoszenia* i *przenieść operator przydziału* dla niego. Kompilator wybierze te specjalne elementy członkowskie podczas rozpoznawania przeciążenia w sytuacjach, gdy kopia nie jest potrzebna. Typy kontenerów biblioteki standardowej wywołać konstruktora przenoszenia na obiekty, jeśli jest zdefiniowany. Aby uzyskać więcej informacji, zobacz [Przenoszenie konstruktorów i Przenoszenie operatorów przydziałów (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Wyrażenia lambda

W programowaniu w stylu C funkcję można przekazać do innej funkcji za pomocą *wskaźnika funkcji*. Wskaźniki funkcji są niewygodne do utrzymania i zrozumienia. Funkcja, do której się odnoszą, może być zdefiniowana w innym miejscu w kodzie źródłowym, z dala od punktu, w którym jest wywoływana. Ponadto, nie są one bezpieczne dla typu. Modern C++ udostępnia *obiekty funkcji*, klasy, które zastępują [()](function-call-operator-parens.md) operator, który umożliwia ich wywoływanie jak funkcja. Najwygodniejszym sposobem tworzenia obiektów funkcyjnych jest [wyrażeń lambda wbudowanych](../cpp/lambda-expressions-in-cpp.md). Poniższy przykład pokazuje, jak używać wyrażenia lambda do `for_each` przekazywania obiektu funkcji, który funkcja będzie wywoływać na każdy element wektora:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Wyrażenie lambda `[=](int i) { return i > x && i < y; }` można odczytać jako "funkcję, która `int` przyjmuje pojedynczy argument typu i zwraca wartość `x` logiczną, `y`która wskazuje, czy argument jest większy niż i mniejszy niż ." Należy zauważyć, `x` że `y` zmienne i z otaczającego kontekstu mogą być używane w lambda. Określa, `[=]` że te zmienne są *przechwytywane* przez wartość; innymi słowy, wyrażenie lambda ma własne kopie tych wartości.

## <a name="exceptions"></a>Wyjątki

Modern C++ podkreśla wyjątki, a nie kody błędów jako najlepszy sposób raportowania i obsługi warunków błędów. Aby uzyskać więcej informacji, zobacz [Nowoczesne c++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std::atomowy

Użyj C++ Standardowa biblioteka [std::atomic](../standard-library/atomic-structure.md) struct i pokrewnych typów dla mechanizmów komunikacji między wątkami.

## <a name="stdvariant-c17"></a>std::variant (C++17)

Związki są powszechnie używane w programowaniu w stylu C, aby oszczędzać pamięć, umożliwiając członkom różnych typów zajmowanie tej samej lokalizacji pamięci. Jednak związki nie są bezpieczne dla typu i są podatne na błędy programowania. C++17 wprowadza klasę [std::variant](../standard-library/variant-class.md) jako bardziej solidną i bezpieczną alternatywę dla związków. Funkcja [std::visit](../standard-library/variant-functions.md#visit) może służyć do uzyskiwania `variant` dostępu do elementów członkowskich typu w sposób bezpieczny dla typu.

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)\
[Wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md)\
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)\
[Tabela zgodności języka języka Microsoft C++](../overview/visual-cpp-language-conformance.md)
