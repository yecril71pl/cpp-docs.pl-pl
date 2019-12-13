---
title: Zapraszamy ponownie do języka C++ (Modern C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 2739da77fbfa973ca716abc6d8fa4920b81095d9
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303333"
---
# <a name="welcome-back-to-c-modern-c"></a>Zapraszamy ponownie do języka C++ (Modern C++)

W ciągu ostatnich 25 lat C++ była jednym z najczęściej używanych języków programowania na świecie. Dobrze napisania C++ programy są szybkie i wydajne. Język jest bardziej elastyczny niż inne języki, ponieważ umożliwia dostęp do funkcji sprzętu niskiego poziomu, co pozwala zmaksymalizować szybkość i zminimalizować wymagania dotyczące pamięci. Można jej używać do tworzenia szerokiej gamy aplikacji — od gier, do wysokiej wydajności oprogramowania naukowego, sterowników urządzeń, osadzonych programów, bibliotek i kompilatorów dla innych języków programowania, aplikacji klienckich systemu Windows i wielu innych.

Jedno z oryginalnych wymagań w zakresie C++ zgodności z poprzednimi wersjami w języku C. Z tego powodu C++ zawsze dozwolone programowanie w stylu C z nieprzetworzonymi wskaźnikami, tablicami, ciągami znaków zakończonymi znakiem null, niestandardowymi strukturami danych i innymi funkcjami, które mogą zapewnić doskonałą wydajność, ale mogą także powodować duplikowanie usterek i złożoności. Ewolucja C++ ma wyróżnione funkcje, które znacząco zmniejszają potrzebę używania Idiomy w stylu języka C. Stare urządzenia programistyczne C są tam, gdzie są potrzebne, ale z nowoczesnym C++ kodem, które powinny być mniej i mniejsze. Nowoczesny C++ kod jest łatwiejszy, bezpieczniejszy, bardziej elegancki i ciągle tak szybko, jak kiedykolwiek.

Poniższe sekcje zawierają omówienie głównych funkcji nowoczesnych C++. O ile nie zaznaczono inaczej, funkcje wymienione w tym miejscu są dostępne w języku C++ 11 i nowszych. W kompilatorze C++ Microsoft można ustawić opcję kompilatora [/STD](../build/reference/std-specify-language-standard-version.md) , aby określić, która wersja standardu ma być używana dla projektu.

## <a name="raii-and-smart-pointers"></a>RAII i inteligentne wskaźniki

Jedną z głównych klas błędów w programowaniu w stylu języka C jest *przeciek pamięci* z powodu niepowodzenia wywołania metody **delete** dla pamięci, która została przypisana do **nowej**. Nowoczesne C++ podkreśla zasadę *pozyskiwania zasobów* , która stwierdza, że każdy zasób (pamięć sterty, dojścia do pliku, gniazda itd.) powinien *należeć do* obiektu, który tworzy lub odbiera, nowo przydzielonego zasobu w jego konstruktorze i usuwa go w jego destruktorze. Zgodnie z zasadą RAII gwarantujemy, że wszystkie zasoby zostaną prawidłowo zwrócone do systemu operacyjnego, gdy obiekt będący właścicielem wykracza poza zakres. Aby obsłużyć proste wdrażanie zasad RAIIymi C++ , biblioteka standardowa zawiera trzy typy inteligentnych wskaźników: [std:: unique_ptr](../standard-library/unique-ptr-class.md), [std:: shared_ptr](../standard-library/shared-ptr-class.md)i [std:: weak_ptr](../standard-library/weak-ptr-class.md). Inteligentny wskaźnik obsługuje alokację i usunięcie pamięci, do której należy. Poniższy przykład przedstawia klasę z elementem członkowskim tablicy przydzielonym na stercie w wywołaniu do `make_unique()`. Wywołania **New** i **delete** są hermetyzowane przez klasę `unique_ptr`. Gdy obiekt `widget` wykracza poza zakres, destruktor unique_ptr zostanie wywołany i zwolni pamięć, która została przypisana do tablicy.  

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

## <a name="stdstring-and-stdstring_view"></a>std:: String i std:: string_view

Ciągi w stylu języka C są innym głównym źródłem błędów. Za pomocą [std:: String i std:: wstring](../standard-library/basic-string-class.md) można wyeliminować praktycznie wszystkie błędy związane z ciągami w stylu języka C i uzyskać korzyści dla funkcji Członkowskich do wyszukiwania, dołączania, oczekiwania i tak dalej. Obie są wysoce zoptymalizowane pod kątem szybkości. Podczas przekazywania ciągu do funkcji, która wymaga tylko dostępu tylko do odczytu, w (C++ 17) można użyć [std:: string_view](../standard-library/basic-string-view-class.md) , aby uzyskać lepszą wydajność.

## <a name="stdvector-and-other-standard-library-containers"></a>std:: Vector i inne kontenery biblioteki standardowej

Wszystkie kontenery biblioteki standardowej są zgodne z zasadą RAII, zapewniają Iteratory do bezpiecznego przechodzenia elementów, są wysoce zoptymalizowane pod kątem wydajności i zostały dokładnie przetestowane pod kątem poprawności. Korzystając z tych kontenerów zawsze, gdy jest to możliwe, eliminujesz potencjalną usterkę lub nieefektywność, którą można wprowadzić w niestandardowych strukturach danych. Domyślnie użyj [wektora](../standard-library/vector-class.md) jako preferowanego kontenera sekwencyjnego w C++. Jest to równoważne `List<T>` w językach .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Użyj [mapy](../standard-library/map-class.md) (nie `unordered_map`) jako domyślnego kontenera asocjacyjnego. Używaj [zestawów](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)i [zestawów wielokrotnych](../standard-library/multiset-class.md) do degeneracji i wielu przypadków.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

W przypadku konieczności optymalizacji wydajności należy rozważyć użycie:

- Typ [tablicy](../standard-library/array-class-stl.md) podczas osadzania jest ważny, na przykład jako element członkowski klasy.

- Nieuporządkowane Kontenery asocjacyjne, takie jak [unordered_map](../standard-library/unordered-map-class.md). Są to mniejsze obciążenie poszczególnych elementów i wyszukiwanie w czasie stałym, ale mogą być trudniejsze do użycia poprawnie i wydajnie.

- Posortowane `vector`. Aby uzyskać więcej informacji, zobacz [algorytmy](../cpp/algorithms-modern-cpp.md).

Nie używaj tablic stylów języka C. W przypadku starszych interfejsów API, które wymagają bezpośredniego dostępu do danych, należy użyć metod dostępu, takich jak `f(vec.data(), vec.size());`. Aby uzyskać więcej informacji na temat kontenerów, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorytmy biblioteki standardowej

Przed założeniem, że musisz napisać niestandardowy algorytm dla programu, najpierw zapoznaj się z C++ [algorytmami](../standard-library/algorithm.md)biblioteki standardowej. Standardowa biblioteka zawiera ciągle rosnące asortymenty algorytmów dla wielu typowych operacji, takich jak wyszukiwanie, sortowanie, filtrowanie i generowanie losowe. Biblioteka matematyczna jest obszerna. Począwszy od języka C++ 17, dostępne są równoległe wersje wielu algorytmów.

Oto kilka ważnych przykładów:

- **for_each**, domyślny algorytm przechodzenia (razem z pętlami opartymi na zakresie dla pętli). 

- **transformacja**dla modyfikacji nieznajdującej się w miejscu elementów kontenera

- **find_if**, domyślny algorytm wyszukiwania.

- **Sortuj**, **lower_bound**i inne domyślne algorytmy sortowania i wyszukiwania.

Aby napisać komparator, użyj ścisłego **<** i Użyj *nazwanych wyrażeń lambda* , gdy to możliwe.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>Autouzupełnianie zamiast jawnych nazw typów

W języku c++ 11 wprowadzono słowo kluczowe [Autotekstu](auto-cpp.md) do użycia w deklaracjach zmiennych, funkcji i szablonu. **Funkcja** autoinstruuje kompilator, aby wywnioskować typ obiektu, aby nie trzeba było go jawnie pisać. **Funkcja autouzupełniania** jest szczególnie przydatna, gdy typem wywnioskowanym jest szablon zagnieżdżony:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Pętle oparte na zakresie

Iteracja w stylu języka C w odniesieniu do tablic i kontenerów jest podatna na błędy indeksowania i jest również żmudnym do wpisywania. Aby wyeliminować te błędy i zwiększyć czytelność kodu, należy użyć opartych na przedziale dla pętli z kontenerami biblioteki standardowej, jak również tablic nieprzetworzonych. Aby uzyskać więcej informacji, zobacz [zakres instrukcji for](../cpp/range-based-for-statement-cpp.md).

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

Makra w języku C C++ i są tokenami, które są przetwarzane przez preprocesor przed kompilacją. Każde wystąpienie tokenu makra jest zastępowane jego zdefiniowaną wartością lub wyrażeniem przed skompilowaniem pliku. Makra są często używane w programowaniu w stylu języka C do definiowania wartości stałych czasu kompilacji. Jednak makra są podatne na błędy i trudno debugować. W nowoczesnych C++, należy preferować zmienne [constexpr](constexpr-cpp.md) dla stałych czasu kompilacji:

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednolite inicjowanie

W nowoczesnych C++, można użyć inicjowania nawiasów klamrowych dla dowolnego typu. Ta forma inicjalizacji jest szczególnie przydatna podczas inicjowania tablic, wektorów lub innych kontenerów. W poniższym przykładzie `v2` jest inicjowane z 3 wystąpieniami `S`. `v3` jest inicjowana z 3 wystąpieniami `S`, które są inicjowane w nawiasach klamrowych. Kompilator wnioskuje typ każdego elementu na podstawie zadeklarowanego typu `v3`.

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

Nowoczesne C++ zapewnia *semantykę przenoszenia* , która umożliwia wyeliminowanie niepotrzebnych kopii pamięci, które we wcześniejszych wersjach języka nie były nieuniknione w niektórych sytuacjach. Operacja *przenoszenia* przenosi własność zasobu z jednego obiektu do drugiego bez tworzenia kopii. Podczas implementowania klasy, do której należy zasób, taki jak pamięć sterty, dojścia do plików i tak dalej, można zdefiniować *Konstruktor przenoszący* i *operator przypisania przenoszenia* . Kompilator wybierze tych specjalnych członków podczas rozpoznawania przeciążenia w sytuacjach, gdy kopia nie jest wymagana. Typy kontenerów biblioteki standardowej wywołują Konstruktor przenoszenia dla obiektów, jeśli jest zdefiniowany. Aby uzyskać więcej informacji, zobacz [przenoszenie konstruktorów i operatory przypisaniaC++przenoszenia ()](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Wyrażenia lambda

W programowaniu w stylu języka C funkcja może być przenoszona do innej funkcji za pomocą *wskaźnika funkcji*. Wskaźniki funkcji są niewygodne do utrzymania i zrozumienia, ponieważ funkcja, do której się odwołuje, może być zdefiniowana w innym miejscu kodu źródłowego, daleko od momentu, w którym jest wywoływana. Ponadto nie są bezpieczne dla typów. Nowoczesne C++ udostępnia obiekty funkcji, klasy, które przesłaniają operator [()](function-call-operator-parens.md) , który umożliwia ich wywoływanie jak funkcję. Najbardziej wygodnym sposobem tworzenia obiektów funkcji jest z wbudowanymi [wyrażeniami lambda](../cpp/lambda-expressions-in-cpp.md). Poniższy przykład pokazuje, jak używać wyrażenia lambda do przekazywania obiektu funkcji, który funkcja `for_each` będzie wywoływała dla każdego elementu w wektorze:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Wyrażenie lambda `[=](int i) { return i > x && i < y; }` może być odczytywane jako "funkcja, która przyjmuje pojedynczy argument typu `int` i zwraca wartość logiczną wskazującą, czy wyrażenie ma wartość true. Należy zauważyć, że zmienne `x` i `y` z otaczającego kontekstu mogą być używane w wyrażeniach lambda. `[=]` określa, że te zmienne są *przechwytywane* przez wartość; Innymi słowy wyrażenie lambda ma własne kopie tych wartości.

## <a name="exceptions"></a>Wyjątki

Ogólnie rzecz biorąc, nowoczesne C++ wyróżnia wyjątki, a nie kody błędów, co najlepszym sposobem na raportowanie i obsługę warunków błędów. Aby uzyskać więcej informacji, [Zobacz C++ współczesne najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std:: inatomowej

Użyj struktury C++ standardowej biblioteki [std::](../standard-library/atomic-structure.md) informal i powiązanych typów dla mechanizmów komunikacji między wątkami.

## <a name="stdvariant-c17"></a>std:: Variant (C++ 17)

Unii są często używane w programowaniu w stylu języka C, aby zaoszczędzić pamięć przez umożliwienie członkom różnych typów zajmowania tej samej lokalizacji pamięci. Jednak unie nie są bezpieczne dla typów i podatne na błędy programowania. Język c++ 17 wprowadza klasę [std:: Variant](../standard-library/variant-class.md) jako bardziej niezawodną i bezpieczną alternatywę dla Unii. Funkcja [std:: odwiedzi](../standard-library/variant-functions.md#visit) może służyć do uzyskiwania dostępu do elementów członkowskich typu `variant` w sposób bezpieczny dla typów.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Tabela C++ zgodności języka firmy Microsoft](../overview/visual-cpp-language-conformance.md)