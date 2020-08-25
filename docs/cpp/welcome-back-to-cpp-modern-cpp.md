---
title: Witamy w języku C++ — nowoczesny C++
description: Opisuje nowy idiomy programistyczny w nowoczesnej C++ i ich racjonalny sposób.
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: f2b9159e74ba7ce37c7eab1513826da939a3be49
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2020
ms.locfileid: "87232199"
---
# <a name="welcome-back-to-c---modern-c"></a>Witamy w języku C++ — nowoczesny C++

Od momentu jego utworzenia język C++ stał się jednym z najczęściej używanych języków programowania na świecie. Dobrze przygotowane programy C++ są szybkie i wydajne. Język jest bardziej elastyczny niż inne języki: może to posłużyć na najwyższych poziomach abstrakcji i nie tylko na poziomie krzemu. Język C++ zapewnia wysoce zoptymalizowane biblioteki standardowe. Umożliwia dostęp do funkcji sprzętu niskiego poziomu, co pozwala zmaksymalizować szybkość i zminimalizować wymagania dotyczące pamięci. Za pomocą języka C++ można utworzyć szeroką gamę aplikacji. Gry, sterowniki urządzeń i oprogramowanie naukowe o wysokiej wydajności. Programy osadzone. Aplikacje klienckie systemu Windows. Nawet biblioteki i kompilatory dla innych języków programowania są zapisywane w języku C++.

Jedno z oryginalnych wymagań dotyczących języka C++ było zgodne z poprzednimi wersjami języka C. W związku z tym język C++ zawsze dopuszcza programowanie w stylu C, z nieprzetworzonymi wskaźnikami, tablicami, ciągami znaku zakończonych znakiem null i innymi funkcjami. Mogą one zapewnić doskonałą wydajność, ale mogą również powiększać błędy i złożoność. Ewolucja języka C++ ma wyróżnione funkcje, które znacząco zmniejszają potrzebę używania Idiomy w stylu C. Stare środowiska programistyczne C są tam, gdzie ich potrzebujesz, ale przy użyciu nowoczesnego kodu C++ należy je potrzebować mniej i mniej. Nowoczesny kod języka C++ jest łatwiejszy, bezpieczniejszy, bardziej elegancki i nadal tak szybko, jak kiedykolwiek.

Poniższe sekcje zawierają omówienie głównych funkcji nowoczesnego języka C++. O ile nie zaznaczono inaczej, funkcje wymienione w tym miejscu są dostępne w języku C++ 11 i nowszych. W kompilatorze języka Microsoft C++ można ustawić [`/std`](../build/reference/std-specify-language-standard-version.md) opcję kompilatora, aby określić, która wersja standardu ma być używana dla projektu.

## <a name="resources-and-smart-pointers"></a>Zasoby i inteligentne wskaźniki

Jedną z głównych klas błędów w programowaniu w stylu języka C jest *przeciek pamięci*. Przecieki są często spowodowane błędem wywołania **`delete`** pamięci przydzielonej za pomocą **`new`** . Nowoczesne C++ kładzie nacisk na zasadę *pozyskiwania zasobów* (RAII). Pomysł jest prosty. Zasoby (pamięć sterty, dojścia do plików, gniazda itd.) powinny *należeć do* obiektu. Ten obiekt tworzy lub odbiera nowo przydzielony zasób w jego konstruktorze i usuwa go w jego destruktorze. Zasada RAII gwarantuje, że wszystkie zasoby są prawidłowo zwracane do systemu operacyjnego, gdy obiekt będący właścicielem wykracza poza zakres.

Aby obsłużyć proste wdrażanie zasad RAIIymi, standardowa biblioteka języka C++ udostępnia trzy typy inteligentnych wskaźników: [`std::unique_ptr`](../standard-library/unique-ptr-class.md) , [`std::shared_ptr`](../standard-library/shared-ptr-class.md) i [`std::weak_ptr`](../standard-library/weak-ptr-class.md) . Inteligentny wskaźnik obsługuje alokację i usunięcie pamięci, do której należy. Poniższy przykład przedstawia klasę z elementem członkowskim tablicy przydzielonym na stercie w wywołaniu `make_unique()` . Wywołania **`new`** i **`delete`** są hermetyzowane przez `unique_ptr` klasę. Gdy `widget` obiekt wykracza poza zakres, zostanie wywołany destruktor unique_ptr, który zwolni pamięć, która została przypisana do tablicy.  

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

Jeśli to możliwe, Użyj inteligentnego wskaźnika podczas alokowania pamięci sterty. Jeśli musisz użyć operatorów New i DELETE jawnie, postępuj zgodnie z zasadą RAII. Aby uzyskać więcej informacji, zobacz temat [okres istnienia obiektu i zarządzanie zasobami (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>`std::string` i `std::string_view`

Ciągi w stylu języka C są innym głównym źródłem błędów. Za pomocą [ `std::string` i `std::wstring` ](../standard-library/basic-string-class.md), można wyeliminować praktycznie wszystkie błędy związane z ciągami stylu języka C. Możesz również skorzystać z funkcji Członkowskich do wyszukiwania, dołączania, oczekiwania i tak dalej. Obie są wysoce zoptymalizowane pod kątem szybkości. W przypadku przekazywania ciągu do funkcji wymagającej tylko dostępu tylko do odczytu w języku C++ 17 można użyć [`std::string_view`](../standard-library/basic-string-view-class.md) jeszcze większej wydajności.

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector` i inne kontenery biblioteki standardowej

Wszystkie kontenery biblioteki standardowej są zgodne z zasadą RAII. Zapewniają Iteratory do bezpiecznego przechodzenia elementów. Są one wysoce zoptymalizowane pod kątem wydajności i zostały dokładnie przetestowane pod kątem poprawności. Korzystając z tych kontenerów, można wyeliminować potencjalne błędy lub nieefektywność, które mogą zostać wprowadzone w niestandardowych strukturach danych. Zamiast tablic nieprzetworzonych Użyj [`vector`](../standard-library/vector-class.md) jako kontenera sekwencyjnego w języku C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [`map`](../standard-library/map-class.md) (nie `unordered_map` ) jako domyślnego kontenera asocjacyjnego. Używanie [`set`](../standard-library/set-class.md) , [`multimap`](../standard-library/multimap-class.md) , i [`multiset`](../standard-library/multiset-class.md) do wygenerowania i wiele przypadków.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

W przypadku konieczności optymalizacji wydajności należy rozważyć użycie:

- [`array`](../standard-library/array-class-stl.md)Typ podczas osadzania jest ważny, na przykład jako element członkowski klasy.

- Nieuporządkowane Kontenery asocjacyjne, takie jak [`unordered_map`](../standard-library/unordered-map-class.md) . Są to mniejsze obciążenie poszczególnych elementów i wyszukiwanie w czasie stałym, ale mogą być trudniejsze do użycia poprawnie i wydajnie.

- Posortowane `vector` . Aby uzyskać więcej informacji, zobacz [algorytmy](../cpp/algorithms-modern-cpp.md).

Nie używaj tablic stylów języka C. W przypadku starszych interfejsów API, które wymagają bezpośredniego dostępu do danych, należy użyć metod dostępu, takich jak `f(vec.data(), vec.size());` zamiast. Aby uzyskać więcej informacji na temat kontenerów, zobacz [kontenery standardowej biblioteki języka C++](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorytmy biblioteki standardowej

Przed założeniem, że musisz napisać niestandardowy algorytm dla programu, najpierw zapoznaj się z [algorytmami](../standard-library/algorithm.md)standardowej biblioteki języka C++. Standardowa biblioteka zawiera ciągle rosnące asortymenty algorytmów dla wielu typowych operacji, takich jak wyszukiwanie, sortowanie, filtrowanie i generowanie losowe. Biblioteka matematyczna jest obszerna. Począwszy od języka C++ 17, dostępne są równoległe wersje wielu algorytmów.

Oto kilka ważnych przykładów:

- `for_each`, domyślny algorytm przechodzenia (wraz z pętlami opartymi na zakresie `for` ).

- `transform`w przypadku niew miejscu modyfikacji elementów kontenera

- `find_if`, domyślny algorytm wyszukiwania.

- `sort`, `lower_bound` i inne domyślne algorytmy sortowania i wyszukiwania.

Aby napisać komparator, użyj funkcji Strict **`<`** i, jeśli to możliwe, użyj *nazwanych lambda* .

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto` zamiast jawnych nazw typów

Język c++ 11 wprowadził [`auto`](auto-cpp.md) słowo kluczowe do użycia w deklaracjach zmiennych, funkcji i szablonu. **`auto`** instruuje kompilator, aby wywnioskować typ obiektu, aby nie trzeba było go jawnie pisać. **`auto`** jest szczególnie przydatne, gdy typ wywnioskowany jest szablonem zagnieżdżonym:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Pętle zależne od zakresu `for`

Iteracja w stylu języka C w odniesieniu do tablic i kontenerów jest podatna na błędy indeksowania i jest również żmudnym do wpisywania. Aby wyeliminować te błędy i zwiększyć czytelność kodu, należy użyć pętli opartych na zakresie **`for`** zarówno w przypadku kontenerów biblioteki standardowej, jak i nieprzetworzonych tablic. Aby uzyskać więcej informacji, zobacz [ `for` instrukcje oparte na zakresie](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr` wyrażenia zamiast makr

Makra w języku C i C++ są tokenami przetworzonymi przez preprocesor przed kompilacją. Każde wystąpienie tokenu makra jest zastępowane jego zdefiniowaną wartością lub wyrażeniem przed skompilowaniem pliku. Makra są często używane w programowaniu w stylu języka C do definiowania wartości stałych czasu kompilacji. Jednak makra są podatne na błędy i trudno debugować. W nowoczesnych językach C++ należy preferować [`constexpr`](constexpr-cpp.md) zmienne dla stałych czasu kompilacji:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednolite inicjowanie

W nowoczesnych językach C++ można użyć inicjowania nawiasów klamrowych dla dowolnego typu. Ta forma inicjalizacji jest szczególnie przydatna podczas inicjowania tablic, wektorów lub innych kontenerów. W poniższym przykładzie `v2` jest inicjowane z trzema wystąpieniami `S` . `v3` jest inicjowany z trzema wystąpieniami `S` , które są inicjowane za pomocą nawiasów klamrowych. Kompilator wnioskuje typ każdego elementu na podstawie zadeklarowanego typu `v3` .

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

Nowoczesne C++ zapewnia *semantykę przenoszenia*, co umożliwia wyeliminowanie niepotrzebnych kopii pamięci. We wcześniejszych wersjach języka kopie były w pewnych sytuacjach nieuniknione. Operacja *przenoszenia* przenosi własność zasobu z jednego obiektu do drugiego bez tworzenia kopii. Niektóre klasy są zasobami, takimi jak pamięć sterty, dojścia do plików i tak dalej. Podczas implementowania klasy będącej właścicielem zasobów można zdefiniować *Konstruktor przenoszący* i *operator przypisania przenoszenia* . Kompilator wybiera te specjalne elementy członkowskie podczas rozpoznawania przeciążenia w sytuacjach, gdy kopia nie jest wymagana. Typy kontenerów biblioteki standardowej wywołują Konstruktor przenoszenia dla obiektów, jeśli jest zdefiniowany. Aby uzyskać więcej informacji, zobacz [przenoszenie konstruktorów i operatory przypisania przenoszenia (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Wyrażenia lambda

W programowaniu w stylu języka C funkcja może zostać przeniesiona do innej funkcji za pomocą *wskaźnika funkcji*. Wskaźniki funkcji są niewygodne do utrzymania i zrozumienia. Funkcja, do której się odwołuje, może być zdefiniowana w innym miejscu kodu źródłowego, daleko od momentu, w którym jest wywoływana. Ponadto nie są one bezpieczne dla typów. Nowoczesne C++ zawiera *obiekty funkcji*, klasy, które zastępują [`operator()`](function-call-operator-parens.md) operator, co umożliwia ich wywoływanie jak funkcję. Najbardziej wygodnym sposobem tworzenia obiektów funkcji jest z wbudowanymi [wyrażeniami lambda](../cpp/lambda-expressions-in-cpp.md). Poniższy przykład pokazuje, jak używać wyrażenia lambda do przekazywania obiektu funkcji, który `for_each` zostanie wywołany dla każdego elementu w wektorze:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Wyrażenie lambda `[=](int i) { return i > x && i < y; }` może być odczytane jako "funkcja, która przyjmuje pojedynczy argument typu **`int`** i zwraca wartość logiczną wskazującą, czy argument jest większy niż `x` i mniejszy niż `y` ". Należy zauważyć, że zmienne `x` i `y` z otaczającego kontekstu mogą być używane w wyrażeniach lambda. `[=]`Określa, że te zmienne są *przechwytywane* przez wartość; innymi słowy, wyrażenie lambda ma własne kopie tych wartości.

## <a name="exceptions"></a>Wyjątki

Nowoczesne C++ wyróżnia wyjątki, a nie kody błędów, co najlepszym sposobem na raportowanie i obsługę warunków błędów. Aby uzyskać więcej informacji, zobacz [współczesne najlepsze rozwiązania C++ dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md).

## `std::atomic`

Używaj struktury standardowej biblioteki C++ [`std::atomic`](../standard-library/atomic-structure.md) i powiązanych typów dla mechanizmów komunikacji między wątkami.

## <a name="stdvariant-c17"></a>`std::variant` (C++ 17)

Unii są często używane w programowaniu w stylu języka C, aby zaoszczędzić pamięć przez umożliwienie członkom różnych typów zajmowania tej samej lokalizacji pamięci. Jednak unie nie są bezpieczne dla typów i podatne na błędy programowania. Język c++ 17 wprowadza [`std::variant`](../standard-library/variant-class.md) klasę jako bardziej niezawodną i bezpieczną alternatywę dla Unii. [`std::visit`](../standard-library/variant-functions.md#visit)Funkcja może służyć do uzyskiwania dostępu do elementów członkowskich `variant` typu w sposób bezpieczny dla typu.

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)\
[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)\
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)\
[Tabela zgodności języka Microsoft C++](../overview/visual-cpp-language-conformance.md)
