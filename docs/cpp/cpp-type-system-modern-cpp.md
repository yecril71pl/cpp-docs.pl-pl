---
title: System typów języka C++ (Modern C++)
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 4dfbf408654ccc92c92d6855c15238cb07c01b58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392288"
---
# <a name="c-type-system-modern-c"></a>System typów języka C++ (Modern C++)

Pojęcie *typu* jest bardzo ważna w języku C++. Zwracana wartość każdej zmiennej, argumentu funkcji oraz funkcji musi mieć typ, aby mogła zostać skompilowana. Ponadto, kompilator niejawnie nadaje typ każdemu wyrażeniu (w tym wartości literału), zanim zostanie on oceniony. Niektóre przykłady typów uwzględniają **int** do przechowywania wartości całkowitych **double** do przechowywania wartości zmiennoprzecinkowych (znany także jako *skalarne* typy danych), lub klasa biblioteki standardowej [std::basic_string](../standard-library/basic-string-class.md) do przechowywania tekstu. Możesz utworzyć swój własny typ definiując **klasy** lub **struktury**. Typ określa wielkość pamięci, która zostanie zaalokowana dla zmiennej (lub wyniku wyrażenia), rodzaje wartości, które mogą być przechowywane w tej zmiennej, sposób interpretacji tych wartości (jako wzorców bajtów) oraz operacje, jakie mogą zostać na nich wykonane. Ten artykuł zawiera nieformalny przegląd głównych funkcji systemu typów C++.

## <a name="terminology"></a>Terminologia

**Zmienna**: Symboliczna nazwa ilości danych, aby nazwa może służyć do uzyskania dostępu do danych odwołuje się do w całym zakresie kodu, w którym jest zdefiniowana. W języku C++ *zmiennej* jest zazwyczaj używane do odwoływania się do wystąpienia skalarnych typów danych, natomiast instancje innych typów są zwykle nazywane *obiektów*.

**Obiekt**: Dla uproszczenia i zachowania spójności, w tym artykule używany jest termin *obiektu* do odwoływania się do dowolnego wystąpienia klasy lub struktury, a gdy jest używany w ogólnym sensie, obejmuje wszystkie typy, nawet zmienne skalarne.

**Typ POD** (zwykłe stare dane): Ta nieformalna kategoria typów danych języka C++ odnosi się do typów, które są skalarne (patrz sekcja: typy podstawowe) lub *klasy POD*. Klasa POD nie ma żadnych statycznych składowych danych, które nie są również POD, i nie ma zdefiniowanych przez użytkownika konstruktorów, zdefiniowanych przez użytkownika destruktorów ani zdefiniowanych przez użytkownika operatorów przypisania. Klasa POD nie ma też żadnych funkcji wirtualnych, nie ma klasy podstawowej ani żadnych prywatnych lub chronionych niestatycznych składowych danych. Typy POD są często używane do wymiany danych zewnętrznych, na przykład przy użyciu modułu napisanego w języku C (który ma tylko typy POD).

## <a name="specifying-variable-and-function-types"></a>Określanie typów zmiennych i funkcji

Język C++ jest *silnie typizowane* język jest również *typowany statycznie*; każdy obiekt ma typ i ten typ nigdy nie zmieni (nie należy mylić z obiektami danych statycznych).
**Kiedy Deklarujesz zmienną** w kodzie, użytkownik musi określić jawnie jej typ, albo użyj **automatycznie** — słowo kluczowe, aby poinstruować kompilator, aby wywnioskował typ z inicjatora.
**Kiedy Deklarujesz funkcję** w kodzie, musisz określić typ każdego argumentu i jego wartość zwrotną lub **void** Jeśli żadna wartość nie jest zwrócona przez funkcję. Wyjątek występuje podczas korzystania z szablonów funkcji, które pozwalają na argumenty dowolnego typu.

Po pierwszym zdeklarowaniu zmiennej nie można później zmienić jej typu. Możesz jednak skopiować wartość zmiennej lub wartość zwracaną przez funkcję do innej zmiennej innego typu. Operacje takie są zwane *konwersje typów*, które są czasem niezbędne, ale również są potencjalnymi przyczynami utraty lub nieprawidłowości danych.

Kiedy deklarujesz zmienną typu POD, stanowczo zalecamy jej inicjalizację, co oznacza nadanie jej początkowej wartości. Dopóki zmienna nie zostanie zainicjalizowana, ma ona wartość „śmieciową”, składającą się z bitów, które poprzednio znajdowały się w tej lokalizacji pamięci. Jest to ważny aspekt C++ warty zapamiętania, szczególnie jeżeli praca odbywała się wcześniej w innym języku, który automatycznie obsługuje inicjalizację. Gdy deklarujesz zmienną typu innego niż klasa POD, konstruktor obsługuje inicjalizację.

Poniższy przykład pokazuje kilka prostych deklaracji zmiennych z opisami każdej z nich. W przykładzie pokazano również, jak kompilator używa informacji o typie, aby umożliwiać lub uniemożliwiać pewne kolejne operacje na zmiennej.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Podstawowe (wbudowane) typy

W odróżnieniu do innych języków, C++ nie ma uniwersalnego typu bazowego, z którego wywodzą się wszystkie inne typy. Implementacja języka Visual C++ języka zawiera wiele *podstawowych typów*, znane również jako *wbudowanych typów*. Obejmuje to typy liczbowe takich jak **int**, **double**, **długie**, **bool**, plus **char** i **wchar_t** typy znaków ASCII i UNICODE, odpowiednio. Większość typów podstawowych (z wyjątkiem **bool**, **double**, **wchar_t** i pokrewne typy) mają wszystkie niepodpisane wersje co modyfikuje zakres wartości, które mogą być przechowywane w zmiennej. Na przykład **int**, która przechowuje 32-bitowe podpisane liczby całkowitej, może reprezentować wartość od -2,147,483,648 do 2 147 483 647. **Unsigned int**, który także jest przechowywany jako 32-bitowy, można przechowywać wartości od 0 do 4 294 967 295. Całkowita liczba możliwych wartości w każdym przypadku jest taka sama, zmienia się tylko zakres.

Podstawowe typy są rozpoznawane przez kompilator, który posiada wbudowane reguły rządzące tym, jakie operacje można na nich wykonywać i jak mogą być konwertowane na inne typy podstawowe. Aby uzyskać pełną listę wbudowanych typów i ich wielkości i ograniczeń numerycznych, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

Na poniższej ilustracji przedstawiono względne wielkości typów wbudowanych:

![Rozmiar w bajtach wbudowane&#45;w typach](../cpp/media/built-intypesizes.png "wbudowane rozmiar w bajtach&#45;w typach")

Poniższa tabela wymienia najczęściej używane typy podstawowe:

|Typ|Rozmiar|Komentarz|
|----------|----------|-------------|
|int|4 bajty|Wybór domyślny dla wartości całkowitych.|
|double|8 bajtów|Wybór domyślny dla wartości zmiennopozycyjnych.|
|bool|1 bajt|Przedstawia wartości, które mogą być prawdziwe lub fałszywe.|
|char|1 bajt|Używaj dla znaków ASCII w starszych ciągach typu C lub obiektach std::string, które nigdy nie będą musiały zostać skonwertowane na UNICODE.|
|wchar_t|2 bajty|Przedstawia wartości znaku „szerokiego”, które mogą być zakodowane w formacie UNICODE (UTF-16 w systemie Windows, inne systemy operacyjne mogą się różnić). Jest to typ znaku, który jest używany w ciągach typu `std::wstring`.|
|niepodpisane&nbsp;char|1 bajt|C++ nie ma wbudowanej `byte` typu.  Używaj unsigned char, aby reprezentować wartość bajtową.|
|unsigned int|4 bajty|Wybór domyślny dla flag bitowych.|
|long long|8 bajtów|Przedstawia bardzo duże wartości całkowitoliczbowe.|

## <a name="the-void-type"></a>Typ void (pusty).

**Void** typ to specjalny typ; nie można zadeklarować zmienną typu **void**, ale można zadeklarować zmienną typu __void \*__  (wskaźnik do **void**), co jest czasami konieczne przy alokacji pamięci (bez typu). Jednakże wskaźniki do **void** są nie bezpieczne, a ich stosowanie jest zdecydowanie odradzane w nowoczesnym języku C++. W deklaracji funkcji **void** zwracana wartość oznacza, że funkcja nie zwraca wartości; jest to typowe i dopuszczalne wykorzystanie z **void**. Podczas gdy język C wymagał funkcji, które posiadają parametry zero do zadeklarowania **void** na liście parametrów, na przykład `fou(void)`, te praktyki są odradzane w nowoczesnym C++ i powinny być zadeklarowane `fou()`. Aby uzyskać więcej informacji, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>kwalifikator typu const

Dowolny wbudowany lub zdefiniowany przez użytkownika typ może być zakwalifikowany według słowa kluczowego const. Ponadto funkcje elementów członkowskich mogą być **const**-wykwalifikowanych, a nawet **const**-przeciążone. Wartość **const** nie można zmodyfikować typu, po jego zainicjowaniu.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

**Const** kwalifikator jest szeroko stosowany w deklaracjach funkcji i zmiennych i "poprawność const" jest bardzo ważnym pojęciem języka C++; zasadniczo oznacza wykorzystanie **const** w celu zagwarantowania, w czasie kompilacji czy wartości nie zostaną zmodyfikowane przypadkowo. Aby uzyskać więcej informacji, zobacz [const](../cpp/const-cpp.md).

A **const** typu różni się od jego wartości niestałej wersji; na przykład **const int** jest typem samodzielnym z **int**. Możesz użyć C++ **const_cast** operatora w tych rzadkich przypadkach kiedy konieczne jest usunięcie *const-ness* ze zmiennej. Aby uzyskać więcej informacji, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Typy ciągu

Ściśle rzecz ujmując C++ języka nie ma wbudowanych parametry typu; **char** i **wchar_t** przechowywania pojedynczych znaków — należy zadeklarować tablicy tych typów w celu uzyskania przybliżonego ciągu, dodanie końcowej wartości zerowej (na przykład ASCII `'\0'`) do elementu tablicy po ostatnim prawidłowym znakiem (nazywane również *ciąg stylu C*). Ciągi stylu C wymagały znacznie więcej kodu lub korzystania z funkcji zewnętrznej biblioteki obsługującej ciągi. Ale w nowoczesnym C++, mamy standardową biblioteki typów `std::string` (dla 8-bitowych **char**-typów ciągów znaków) lub `std::wstring` (dla 16-bitowych **wchar_t**-typów ciągów znaków). Te kontenery standardowej biblioteki języka C++ mogą być uważane za natywne typy ciągów, ponieważ są one częścią standardowych bibliotek, które są zawarte w zgodnym środowisku kompilacji C++. Po prostu użyć `#include <string>` dyrektywy, aby te typy były dostępe w programie. (Jeśli używasz biblioteki ATL lub MFC, klasa CString jest również dostępna, ale nie jest częścią standardowego języka C++.) Używanie tablic zakończonych znakiem zerowym (wcześniej wspomniane ciągi stylu C) jest odradzane w nowoczesnym C++.

## <a name="user-defined-types"></a>Typy definiowane przez użytkownika

Podczas definiowania **klasy**, **struktury**, **Unii**, lub **wyliczenia**, ten koncept jest wykorzystywany w reszcie kodu, tak jakby był to typ podstawowy . Zajmuje znany obszar w pamięci, a niektóre zasady sposobu, w jaki można go używać, dotyczą sprawdzania w czasie kompilacji i w trakcie uruchomienia, przez cały okres istnienia programu. Główne różnice między głównymi wbudowanymi typami a typami definiowanymi przez użytkownika są następujące:

- Kompilator nie ma wbudowanej wiedzy o typie zdefiniowanym przez użytkownika. Informacje tego typu po pierwszym napotkaniu definicji podczas procesu kompilacji.

- Ty określasz, jakie operacje mogą zostać przeprowadzone na typie i jak może on zostać przekonwertowany do innych typów, definiując (przez przeciążenie) odpowiednie operatory, albo jako funkcje składowych, albo jako funkcje, które nie są składowymi. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md)

## <a name="pointer-types"></a>Typy wskaźnika

Sięga do najwcześniejszej wersji języka C, C++ nadal pozwala zadeklarować zmienną typu wskaźnik przy użyciu specjalnego deklaratora `*` (gwiazdka). Typ wskaźnika przechowuje adres lokalizacji w pamięci, gdzie jest przechowywana rzeczywista wartość danych. W nowoczesnym C++, są one określane jako *surowych wskaźników*i są dostępne w kodzie za pomocą specjalnych operatorów `*` (gwiazdka) lub `->` (kreska z większą-niż). Jest to nazywane *wyłuskaniem*, a które z nich, którego używasz zależy od tego, czy wyłuskujesz wskaźniki do skalaru lub wskaźnik do elementu członkowskiego w obiekcie. Praca z typami wskaźników od dawna jest jednym z najtrudniejszych i najbardziej dezorientujących aspektów tworzenia programów w C i C++. Ten rozdział nakreśla zagadnienia i praktyki umożliwiające zastosowanie surowych wskaźników, jeżeli chcesz, jednak w nowoczesnym języku C++, jego nie jest już wymagane (lub zalecane) stosowanie surowych wskaźników dla właścicielstwa obiektów, ze względu na ewolucję [inteligentny wskaźnik](../cpp/smart-pointers-modern-cpp.md) () szczególe na końcu tego rozdziału). Nadal jest użyteczne i bezpieczne używanie surowych wskaźników do obserwacji obiektów, ale jeśli musisz użyć ich do własności obiektu, należy to zrobić z ostrożnością i po bardzo starannym rozważeniu sposobu, w jaki obiekty przez nie posiadane są tworzone i niszczone.

Pierwszą rzeczą, którą należy wiedzieć przy deklarowaniu zmiennej surowego wskaźnika, jest to, że zmienna przydzieli tylko pamięć, która jest niezbędna do przechowania adresu lokalizacji pamięci, do którego odwoła się wskaźnik po wyłuskaniu. Alokacja pamięci dla samych wartości danych (nazywane również *magazyn zapasowy*) nie jest jeszcze przydzielone. Innymi słowy, przez zadeklarowanie zmiennej surowego wskaźnika tworzysz zmienną adresu pamięci, a nie zmienną rzeczywistych danych. \Wyłuskanie zmiennej wskaźnika przed upewnieniem się, że zawiera ona prawidłowy adres magazynu zapasowego, spowoduje niezdefiniowane zachowanie (zwykle błąd krytyczny) w programie. Poniższy przykład przedstawia ten rodzaj błędu:

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

Przykład wyłuskuje typ wskaźnika, bez przydzielania pamięci na przechowywanie rzeczywistych danych całkowitoliczbowych lub prawidłowego przypisanego adresu pamięci. Poniższy kod poprawia te błędy:

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

Poprawiony kod przykład wykorzystuje lokalną pamięć stosu do utworzenia zapasowy magazyn, który `pNumber` wskazuje. Dla uproszczenia używamy podstawowego typu. W praktyce magazyn zapasowy wskaźników to większość typów zdefiniowane przez użytkownika, które są dynamicznie przydzielane w obszarze pamięci o nazwie *sterty* (lub *wolnym magazynie*) przy użyciu **nowe** wyrażenia słowa kluczowego (w programowaniu w stylu języka C, starszy `malloc()` użyto funkcji biblioteki środowiska uruchomieniowego C). Po przydzieleniu, te zmienne są zwykle określane jako obiekty, zwłaszcza, jeśli są one oparte na definicji klasy. Pamięć, która została przydzielona z **nowe** musi zostać usunięta przez odpowiednią **Usuń** instrukcji (lub, jeśli użyto `malloc()` funkcji do jej przydzielenia, funkcja środowiska uruchomieniowego języka C `free()`).

Jednak to łatwo zapomnieć o usunięciu dynamicznie przydzielanego obiektu szczególnie w złożonym kodzie, co powoduje błąd zasobu o nazwie *przeciek pamięci*. Z tego powodu zdecydowanie odradza się stosowanie surowych wskaźników w nowoczesnym języku C++. Prawie zawsze jest lepiej owinąć surowy wskaźnik w [inteligentny wskaźnik](../cpp/smart-pointers-modern-cpp.md), który automatycznie zwolni pamięć, gdy jego destruktor jest wywoływany (gdy kod wykracza poza zakres sprytnego wskaźnika); za pomocą inteligentnego wskaźnika można praktycznie wyeliminować całą klasę usterek w programach języka C++. W poniższym przykładzie przyjęto założenie, `MyClass` jest typ zdefiniowany przez użytkownika, który posiada publiczną metodę `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Aby uzyskać więcej informacji dotyczących inteligentnych wskaźników, zobacz [inteligentne wskaźniki](../cpp/smart-pointers-modern-cpp.md).

Aby uzyskać więcej informacji dotyczących konwersji wskaźników, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Aby uzyskać więcej informacji o wskaźnikach, zobacz [wskaźniki](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Typy danych Windows

W klasycznym programowaniu Win32 w językach C i C++, większość funkcji korzysta definicje typów języka specyficznego dla Windows i #define makr (zdefiniowane w `windef.h`) aby określić typy parametrów i wartości zwracane. Te typy danych Windows są w przeważającej części jedynie specjalnymi nazwami (aliasami) do typy wbudowane C/C++. Aby uzyskać pełną listę definicji typów i definicji preprocesora, zobacz [typy danych Windows](/windows/desktop/WinProg/windows-data-types). Niektóre z tych definicji typów, takie jak HRESULT i LCID, są użyteczne i opisowe. Inne, takie jak INT, nie mają specjalnego znaczenia i są po prostu aliasami dla podstawowych typów C++. Inne typy danych systemu Windows mają nazwy pochodzące z czasów programowania w C i procesorów 16-bitowych. Nie mają one żadnego celu ani znaczenia w przypadku nowoczesnego sprzętu lub systemu operacyjnego. Istnieją również specjalne typy danych powiązane z biblioteką środowiska wykonawczego Windows, na liście jako [Windows Runtime podstawowych typów danych](/windows/desktop/WinRT/base-data-types). W nowoczesnym C++, ogólną wytyczną jest preferowanie typów podstawowych języka C++, chyba że typ Windows komunikuje jakieś dodatkowe znaczenie o sposobie interpretowania wartości.

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji dotyczących typu systemu C++, zobacz następujące tematy.

|||
|-|-|
|[Typy wartości](../cpp/value-types-modern-cpp.md)|W tym artykule opisano *typy wartości* oraz zagadnienia odnoszące się do ich wykorzystania.|
|[Konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Opisuje typowe problemy przy konwersji typu i pokazuje, jak ich unikać.|

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
