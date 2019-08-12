---
title: Literały ciągów i znaków (C++)
description: Jak deklarować i definiować literały ciągów i znaków w C++.
ms.date: 08/06/2019
f1_keywords:
- R
- L
- u
- u8
- LR
- uR
- u8R
helpviewer_keywords:
- literal strings [C++]
- string literals [C++]
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: df690bea81b9799b30ae91313ce7157400ef8413
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866091"
---
# <a name="string-and-character-literals-c"></a>Literały ciągów i znaków (C++)

C++obsługuje różne typy ciągów i znaków oraz zapewnia sposoby wyrażania wartości literałów każdego z tych typów. W kodzie źródłowym można wyrazić zawartość znaków i literałów ciągów przy użyciu zestawu znaków. Uniwersalne nazwy znaków i znaki ucieczki umożliwiają wyrażenie dowolnego ciągu przy użyciu tylko podstawowego zestawu znaków źródła. Nieprzetworzony literał ciągu pozwala uniknąć używania znaków ucieczki i może służyć do wyrażenia wszystkich typów literałów ciągów. Można również tworzyć `std::string` literały bez konieczności wykonywania dodatkowych kroków konstrukcyjnych lub konwersji.

```cpp
#include <string>
using namespace std::string_literals; // enables s-suffix for std::string literals

int main()
{
    // Character literals
    auto c0 =   'A'; // char
    auto c1 = u8'A'; // char
    auto c2 =  L'A'; // wchar_t
    auto c3 =  u'A'; // char16_t
    auto c4 =  U'A'; // char32_t

    // Multicharacter literals
    auto m0 = 'abcd'; // int, value 0x61626364

    // String literals
    auto s0 =   "hello"; // const char*
    auto s1 = u8"hello"; // const char*, encoded as UTF-8
    auto s2 =  L"hello"; // const wchar_t*
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32

    // Raw string literals containing unescaped \ and "
    auto R0 =   R"("Hello \ world")"; // const char*
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32

    // Combining string literals with standard s-suffix
    auto S0 =   "hello"s; // std::string
    auto S1 = u8"hello"s; // std::string
    auto S2 =  L"hello"s; // std::wstring
    auto S3 =  u"hello"s; // std::u16string
    auto S4 =  U"hello"s; // std::u32string

    // Combining raw string literals with standard s-suffix
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32
}
```

Literały ciągu nie mogą mieć prefiksu, `u8`, `L`, `u`i `U` prefiksów, aby określić wąski znak (jednobajtowy lub wielobajtowy), UTF-8, szeroki znak (UCS-2 lub UTF-16), odpowiednio kodowania UTF-16 i UTF-32. Nieprzetworzony literał ciągu może mieć `R`, `u8R`, `LR` `uR`,, i `UR` prefiksy dla odpowiedników wersji pierwotnej tych kodowań.  Aby utworzyć wartości tymczasowe lub `std::string` statyczne, można użyć literałów ciągów lub nieprzetworzonych literałów ciągów `s` z sufiksem. Aby uzyskać więcej informacji, zobacz sekcję [literały ciągu](#string-literals) poniżej. Aby uzyskać więcej informacji na temat podstawowego zestawu znaków źródła, uniwersalnych nazw znaków i używania znaków z rozszerzonych danych kodowych w kodzie źródłowym, zobacz [zestawy znaków](../cpp/character-sets.md).

## <a name="character-literals"></a>Literały znaków

*Literał znakowy* składa się ze znaku stałej. Jest reprezentowana przez znak ujęty w znaki pojedynczego cudzysłowu. Istnieje pięć rodzajów literałów znakowych:

- Zwykłe literały znaków typu **char**, na przykład`'a'`

- Literały znakowe UTF-8 typu **char** (**char8_t** w c++ 20), na przykład`u8'a'`

- Literały szerokich znaków typu `wchar_t`, na przykład`L'a'`

- Literały znaków UTF-16 typu `char16_t`, na przykład`u'a'`

- Literały znaku UTF-32 typu `char32_t`, na przykład`U'a'`

Znak używany dla literału znakowego może być dowolnym znakiem, z wyjątkiem znaków zarezerwowanych, ukośnika\\odwrotnego (' '), pojedynczego cudzysłowu (') lub nowego wiersza. Znaki zastrzeżone można określić przy użyciu sekwencji unikowej. Znaki można określić za pomocą uniwersalnych nazw znaków, o ile typ jest wystarczająco duży, aby pomieścić znak.

### <a name="encoding"></a>Kodowanie

Literały znakowe są zakodowane inaczej na podstawie ich prefiksu.

- Literał znakowy bez prefiksu jest zwykłym literałem znaków. Wartość zwykłego literału znakowego zawierającego pojedynczy znak, sekwencję ucieczki lub uniwersalne nazwy znaków, które mogą być reprezentowane w zestawie znaków wykonywania, ma wartość równą wartości liczbowej jego kodowania w zestawie znaków wykonania. Zwykły literał znakowy, który zawiera więcej niż jeden znak, sekwencję ucieczki lub uniwersalne nazwy znaków, jest literałem wieloznakowego. Literał wieloznakowy lub zwykły literał znakowy, którego nie można przedstawić w zestawie znaków wykonywania, ma typ **int**, a jego wartość jest zdefiniowana przez implementację. W przypadku usługi MSVC zapoznaj się z sekcją charakterystyczną dla **firmy Microsoft** .

- Literał znakowy zaczynający się od `L` prefiksu jest literałem znaków dwubajtowych. Wartość literału dwubajtowego zawierającego pojedynczy znak, sekwencję ucieczki lub nazwę uniwersalnego znaku ma wartość równą wartości liczbowej jego kodowania w zestawie znaków dwubajtowych wykonywania, chyba że literał znakowy nie ma reprezentacji w wykonanie zestawu znaków dwubajtowych, w którym przypadku wartość jest definiowana przez implementację. Wartość literału dwubajtowego zawierającego wiele znaków, sekwencje ucieczki lub uniwersalne nazwy znaków jest definiowana przez implementację. W przypadku usługi MSVC zapoznaj się z sekcją charakterystyczną dla **firmy Microsoft** .

- Literał znakowy zaczynający się od `u8` prefiksu jest literałem w formacie UTF-8. Wartość literału znakowego UTF-8 zawierającego pojedynczy znak, sekwencję ucieczki lub nazwę uniwersalnego znaku ma wartość równą wartości punktu kodu ISO 10646, jeśli może być reprezentowana przez pojedynczą jednostkę kodu UTF-8 (odpowiadającą kontrolkom C0 i łaciński podstawowy) Blok Unicode). Jeśli wartość nie może być reprezentowana przez pojedynczą jednostkę kodu UTF-8, program jest źle sformułowany. Literał znaku UTF-8 zawierający więcej niż jeden znak, sekwencję ucieczki lub nazwę uniwersalnego znaku jest źle sformułowany.

- Literał znakowy zaczynający się od `u` prefiksu jest literałem UTF-16. Wartość literału znakowego UTF-16 zawierającego pojedynczy znak, sekwencję ucieczki lub nazwę uniwersalnego znaku ma wartość równą wartości punktu kodu ISO 10646, jeśli może być reprezentowana przez pojedynczą jednostkę kodu UTF-16 (odpowiadającą podstawowej płaszczyźnie z obsługą wielu języków). ). Jeśli wartość nie może być reprezentowana przez pojedynczą jednostkę kodu UTF-16, program jest źle sformułowany. Literał znaku UTF-16 zawierający więcej niż jeden znak, sekwencję ucieczki lub nazwę uniwersalnego znaku jest źle sformułowany.

- Literał znakowy zaczynający się od `U` prefiksu jest literałem w formacie UTF-32. Wartość literału znakowego UTF-32 zawierającego pojedynczy znak, sekwencję ucieczki lub nazwę uniwersalnego znaku ma wartość równą wartości punktu kodu ISO 10646. Literał znaku UTF-32 zawierający więcej niż jeden znak, sekwencję ucieczki lub nazwę uniwersalnego znaku jest źle sformułowany.

###  <a name="bkmk_Escape"></a>Sekwencje unikowe

Istnieją trzy rodzaje sekwencji unikowych: proste, ósemkowe i szesnastkowe. Sekwencje unikowe mogą być następujące:

|Wartość|Sekwencja ucieczki|
|-----------|---------------------|
| nowy wiersz | \\n |
| ukośnika odwrotnego | \\\\ |
| tabulator poziomy | \\t |
| znak zapytania | ? lub \\? |
| tabulator pionowy | \\v |
| pojedynczy cytat | \\' |
| BACKSPACE | \\b |
| podwójny cudzysłów | \\" |
| powrót karetki | \\® |
| znak null | \\0 |
| Wysuw strony | \\n |
| ósemkowy | \\ooo |
| Alert (dzwonek) | \\a |
| szesnastkowo | \\xhhh |

Ósemkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje sekwencja od jednej do trzech cyfr ósemkowych. Ósemkowa sekwencja ucieczki kończy się przy pierwszym znaku, który nie jest cyfrą ósemkową, jeśli napotka się wcześniej niż trzecia cyfra. Najwyższa możliwa wartość ósemkowa to `\377`.

Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym `x`następuje znak, po którym następuje sekwencja co najmniej jednej cyfry szesnastkowej. Zera wiodące są ignorowane. W przypadku zwykłego lub dwubajtowego literału znakowego najwyższa wartość szesnastkowa to 0xFF. W przypadku prefiksu dwubajtowego lub ze wstępnie ustalonym literałem, najwyższa wartość szesnastkowa to 0xFFFF. W literale ze znakiem dwubajtowym z prefiksem, najwyższa wartość szesnastkowa to 0xFFFFFFFF.

Ten przykładowy kod pokazuje kilka przykładów znaków ucieczki przy użyciu zwykłych literałów znakowych. Ta sama składnia sekwencji unikowej jest prawidłowa dla innych typów literałów znakowych.

```cpp
#include <iostream>
using namespace std;

int main() {
    char newline = '\n';
    char tab = '\t';
    char backspace = '\b';
    char backslash = '\\';
    char nullChar = '\0';

    cout << "Newline character: " << newline << "ending" << endl; // Newline character:
                                                                  //  ending
    cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending
    cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending
    cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending
    cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending
}
```

Znak ukośnika odwrotnego\\() jest znakiem kontynuacji wiersza, gdy jest umieszczony na końcu wiersza. Jeśli chcesz, aby znak ukośnika odwrotnego był wyświetlany jako literał znakowy, musisz wpisać dwa ukośniki odwrotne w wierszu`\\`(). Aby uzyskać więcej informacji na temat znaku kontynuacji wiersza, zobacz [etapy tłumaczenia](../preprocessor/phases-of-translation.md).

**Microsoft specific**

Aby utworzyć wartość z wąskiego literału wieloznakowego, kompilator konwertuje znak lub sekwencję znaków między pojedynczymi cudzysłowami na wartości 8-bitowe w ramach 32-bitowej liczby całkowitej. Wiele znaków w literale wypełnia odpowiednie bajty, w razie potrzeby, od wysokiej kolejności do niskiego rzędu. Następnie kompilator konwertuje liczbę całkowitą na typ docelowy zgodnie z zwykłymi regułami. Na przykład, aby utworzyć wartość **char** , kompilator pobiera bajt o niskiej kolejności. Aby utworzyć **wchar_t** lub `char16_t` wartość, kompilator pobiera wyraz o niskiej kolejności. Kompilator ostrzega o tym, że wynik jest obcinany, jeśli wszystkie bity powyżej przypisanego bajtu lub wyrazu są ustawione powyżej.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
int i0     = 'abcd';    // 0x61626364
```

Ósemkowa sekwencja ucieczki, która wydaje się zawierać więcej niż trzy cyfry, jest traktowana jako 3-cyfrowy porządek ósemkowy, a następnie kolejne cyfry jako znaki w literale wieloznakowym, które mogą dać wyniki zaskakujące. Na przykład:

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Sekwencje unikowe, które wyglądają, aby zawierały znaki inne niż ósemkowe, są oceniane jako liczba ósemkowa w górę do ostatniego znaku ósemkowego, a następnie pozostałe znaki w literale wieloznakowym. Ostrzeżenie C4125 jest generowane, jeśli pierwszy znak inny niż ósemkowy jest cyfrą dziesiętną. Przykład:

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Ósemkowa sekwencja ucieczki o wyższej wartości `\377` , która powoduje wystąpienie błędu C2022: "*wartość-in-Decimal*": za duży dla znaku.

Sekwencja unikowa, która wydaje się mieć szesnastkowe i nieszesnastkowe znaki, jest szacowana jako literał wieloznakowy, który zawiera szesnastkową sekwencję ucieczki do ostatniego znaku szesnastkowego, po którym następują znaki inne niż szesnastkowe. Szesnastkowa sekwencja ucieczki, która nie zawiera cyfr szesnastkowych powoduje błąd kompilatora C2153: "literały szesnastkowe muszą mieć co najmniej jedną cyfrę szesnastkową".

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Jeśli literał znaku dwubajtowego z `L` prefiksem zawiera sekwencję wieloznakową, wartość jest pobierana z pierwszego znaku, a kompilator zgłasza C4066 ostrzegawczy. Kolejne znaki są ignorowane, w przeciwieństwie do zachowania równoważnego zwykłego literału wieloznakowego.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**Zakończenie określonych przez firmę Microsoft**

###  <a name="bkmk_UCN"></a>Uniwersalne nazwy znaków

Literały znakowe i natywne (niesurowe) literały ciągu, dowolny znak może być reprezentowany przez nazwę uniwersalnego znaku.  Uniwersalne nazwy znaków są tworzone przez prefiks `\U` , a po nich osiem-cyfrowy punkt kodu Unicode lub przez prefiks `\u` , po którym następuje czwarty dwucyfrowy punkt kodu Unicode. Wszystkie osiem lub cztery cyfry odpowiednio, muszą być obecne, aby można było poprawnie sformatować nazwę uniwersalnego znaku.

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Pary zastępcze

Uniwersalne nazwy znaków nie mogą kodować wartości w zakresie punktu kodu zastępczego D800-DFFF. W przypadku par surogatów Unicode Określ nazwę uniwersalnego znaku przy `\UNNNNNNNN`użyciu, gdzie nnnnnnnn jest 8-cyfrowym punktem kodu dla znaku. Kompilator generuje parę zastępczą w razie potrzeby.

W języku C++ 03 język dozwolony jest tylko podzbiór znaków, które mają być reprezentowane przez ich uniwersalne nazwy znaków, i dozwolone są niektóre uniwersalne nazwy znaków, które w rzeczywistości nie reprezentują żadnych prawidłowych znaków Unicode. Ten błąd został rozwiązany w standardzie C++ 11. W języku C++ 11 zarówno literały znakowe, jak i ciągi oraz identyfikatory mogą używać uniwersalnych nazw znaków.  Aby uzyskać więcej informacji na temat uniwersalnych nazw znaków, zobacz [zestawy znaków](../cpp/character-sets.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [Unicode](https://msdn.microsoft.com/library/dd374081). Aby uzyskać więcej informacji na temat par zastępczych, zobacz [pary zastępcze i znaki dodatkowe](/windows/desktop/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Literały ciągu

Literał ciągu reprezentuje sekwencję znaków, które razem tworzą ciąg zakończony znakiem null. Znaki muszą być ujęte w podwójny cudzysłów. Istnieją następujące rodzaje literałów ciągów:

### <a name="narrow-string-literals"></a>Wąskie literały ciągu

Wąski literał ciągu nie jest prefiksem o wartości, które nie są poprzedzone znakiem cudzysłowu, tablicą zakończoną `const char[n]`zerem typu, gdzie n to długość tablicy w bajtach. Wąski literał ciągu może zawierać dowolny znak graficzny, z wyjątkiem podwójnego cudzysłowu`"`(), ukośnika`\`odwrotnego () lub znaku nowego wiersza. Wąski literał ciągu może również zawierać sekwencje unikowe wymienione powyżej i uniwersalne nazwy znaków, które pasują do bajtu.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Zakodowane ciągi UTF-8

Zakodowany ciąg UTF-8 jest tablicą z prefiksem U8, z `const char[n]`podwójnym cudzysłowem, która została zakończona wartością null, gdzie *n* to długość zakodowanej tablicy w bajtach. Literał ciągu z prefiksem U8 może zawierać dowolny znak graficzny, z wyjątkiem podwójnego cudzysłowu`"`(), ukośnika`\`odwrotnego () lub znaku nowego wiersza. Literał ciągu z prefiksem U8 może również zawierać sekwencje ucieczki wymienione powyżej i dowolną nazwę uniwersalnego znaku.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Szerokie literały ciągu

Szeroki literał ciągu jest tablicą **wchar_t** stałą o wartości null, która jest poprzedzona znakiem "`L`", i zawiera dowolny symbol graficzny, z wyjątkiem podwójnego cudzysłowu ("),\\ukośnika odwrotnego () lub znaku nowego wiersza. Szeroki literał ciągu może zawierać sekwencje wyjścia wymienione powyżej i dowolną nazwę uniwersalnego znaku.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16_t-and-char32_t-c11"></a>char16_t i char32_t (C++ 11)

W języku c++ 11 wprowadzono `char16_t` przenośne (16-bitowe Unicode) `char32_t` i (32-bitowe Unicode) typy znaków:

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Nieprzetworzone literały ciągu (C++ 11)

Nieprzetworzony literał ciągu jest tablicą zakończoną znakiem null — dowolnego typu znaku — zawierającą dowolny znak graficzny, w tym podwójny cudzysłów ("), ukośnik odwrotny (\\) lub znak nowego wiersza. Surowe literały ciągu są często używane w wyrażeniach regularnych, które używają klas znaków, oraz w ciągach HTML i ciągach XML. Aby zapoznać się z przykładami, zobacz następujący artykuł: [Często zadawane pytania dotyczące Bjarne'a Stroustrupa w języku c++ 11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Ogranicznik jest zdefiniowaną przez użytkownika sekwencją do 16 znaków, która bezpośrednio poprzedza nawias otwierający nieprzetworzonego literału ciągu i od razu następuje po nawiasie zamykającym.  Na przykład, w `R"abc(Hello"\()abc"` sekwencji ogranicznika jest `abc` i zawartość ciągu to `Hello"\(`. Ogranicznika można użyć do rozróżnienia nieprzetworzonych ciągów, które zawierają znaki podwójnego cudzysłowu i nawiasy. Ten literał ciągu powoduje błąd kompilatora:

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

Ale ogranicznik ten rozwiązuje:

```cpp
const char* good_parens = R"xyz()")xyz";
```

Można skonstruować nieprzetworzony literał ciągu, który zawiera wiersz (nie znak ucieczki) w źródle:

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>std:: String — literały (C++ 14)

`std::string`Literały są standardowymi implementacjami literałów zdefiniowanych przez użytkownika (patrz poniżej), które są reprezentowane `"xyz"s` jako ( `s` z sufiksem). Ten rodzaj `std::string`literału ciągu tworzy tymczasowy obiekt typu, `std::wstring`, `std::u32string`, lub `std::u16string`, w zależności od określonego prefiksu. Gdy nie jest używany żaden prefiks, `std::string` jest tworzony, jak powyżej. `L"xyz"s``std::wstring`tworzy. `u"xyz"s`tworzy [std:: u16string](../standard-library/string-typedefs.md#u16string)i `U"xyz"s` tworzy [std:: u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

`s` Sufiks może być również używany w przypadku nieprzetworzonych literałów ciągów:

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

`std::string`Literały są zdefiniowane w przestrzeni nazw `std::literals::string_literals` \<w pliku nagłówkowym >. Ponieważ `std::literals::string_literals`, i `std::literals` są zadeklarowane jako [wbudowane przestrzenie nazw](../cpp/namespaces-cpp.md), `std::literals::string_literals` są automatycznie traktowane tak, jakby należały bezpośrednio `std`do przestrzeni nazw.

### <a name="size-of-string-literals"></a>Rozmiar literałów ciągu

W przypadku `char*` ciągów ANSI i innych kodowań jednobajtowych (ale nie UTF-8) rozmiar (w bajtach) literału ciągu jest liczbą znaków plus 1 dla kończącego znaku null. Dla wszystkich innych typów ciągów rozmiar nie jest ściśle powiązany z liczbą znaków. UTF-8 używa maksymalnie czterech elementów **char** do kodowania niektórych *jednostek kodu*i `char16_t` lub `wchar_t` zakodowanych w formacie UTF-16 może używać dwóch elementów (dla ogółu czterech bajtów) do kodowania pojedynczej *jednostki kodu*. Ten przykład pokazuje rozmiar szerokiego literału ciągu w bajtach:

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Zwróć uwagę `strlen()` , `wcslen()` że i nie dołączaj rozmiaru kończącego znaku null, którego rozmiar jest równy rozmiarowi elementu typu String `char*` : jeden bajt w ciągu, dwa bajty na `wchar_t*` lub `char16_t*` ciągi i cztery bajtów w `char32_t*` ciągach.

Maksymalna długość literału ciągu to 65 535 bajtów. Ten limit dotyczy zarówno literałów wąskich ciągów, jak i szerokich literałów ciągów.

### <a name="modifying-string-literals"></a>Modyfikowanie literałów ciągów

Ponieważ literały ciągu (bez `std::string` literałów) są stałymi, spróbuj je zmodyfikować — na `str[2] = 'A'`przykład — powoduje błąd kompilatora.

**Microsoft specific**

W firmie C++Microsoft można użyć literału ciągu, aby zainicjować wskaźnik do niestałego **znaku** lub **wchar_t**. Ta niestała Inicjalizacja jest dozwolona w kodzie C99, ale jest przestarzała w języku C++ 98 i została usunięta w języku C++ 11. Próba zmodyfikowania ciągu powoduje naruszenie zasad dostępu, jak w poniższym przykładzie:

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Można spowodować, że kompilator emituje błąd w przypadku przekonwertowania literału ciągu na wskaźnik niestały, gdy ustawisz opcję kompilatora [/Zc: strictStrings (Wyłącz konwersję typu literału ciągu)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) . Zalecamy jej używanie kodu przenośnego zgodnego ze standardami. Dobrym sposobem jest użycie słowa kluczowego autosłowo kluczowe do deklarowania wskaźników inicjacji literału ciągu, ponieważ jest ono rozpoznawane jako poprawny typ (const). Na przykład ten kod przykład przechwytuje próbę zapisu do literału ciągu w czasie kompilacji:

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

W niektórych przypadkach identyczne literały ciągu mogą być w puli, aby zaoszczędzić miejsce w pliku wykonywalnym. W przypadku buforowania literałów ciągów kompilator powoduje, że wszystkie odwołania do określonego literału ciągu wskazują tę samą lokalizację w pamięci, a nie każdemu punktowi odwołania do oddzielnego wystąpienia literału ciągu. Aby włączyć buforowanie ciągów, użyj opcji kompilatora [/GF](../build/reference/gf-eliminate-duplicate-strings.md) .

**Zakończenie określonych przez firmę Microsoft**

### <a name="concatenating-adjacent-string-literals"></a>Łączenie sąsiadujących literałów ciągu

Sąsiednie lub wąskie literały ciągu są łączone. Ta deklaracja:

```cpp
char str[] = "12" "34";
```

jest identyczny z tą deklaracją:

```cpp
char atr[] = "1234";
```

i do tej deklaracji:

```cpp
char atr[] =  "12\
34";
```

Użycie osadzonych szesnastkowych kodów ucieczki do określenia literałów ciągu może spowodować nieoczekiwane wyniki. Poniższy przykład umożliwia utworzenie literału ciągu, który zawiera znak ASCII 5, a po nim znaki f, i, v i e:

```cpp
"\x05five"
```

Rzeczywisty wynik to szesnastkowa 5F, która jest kodem ASCII znaku podkreślenia, po którym następuje znaki i, v i e. Aby uzyskać prawidłowy wynik, możesz użyć jednego z następujących elementów:

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

`std::string`literały, ponieważ są `std::string` typami, można łączyć `+` z operatorem, który jest zdefiniowany dla typów [basic_string](../standard-library/basic-string-class.md) . Można je również łączyć w taki sam sposób jak sąsiadujące literały ciągu. W obu przypadkach kodowanie ciągu i sufiks muszą być zgodne:

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Literały ciągu z uniwersalnymi nazwami znaków

Literały ciągu natywnego (niesurowego) mogą używać uniwersalnych nazw znaków do reprezentowania dowolnego znaku, o ile nazwa znaku uniwersalnego może być zakodowana jako jeden lub więcej znaków w typie ciągu.  Na przykład uniwersalna nazwa znaku reprezentująca znak rozszerzony nie może być zakodowana w wąskim ciągu przy użyciu strony kodowej ANSI, ale może być zakodowana w wąskich ciągach w niektórych wielobajtowych stronach kodowych lub w ciągach UTF-8 lub w ciągu szerokim. W języku c++ 11 obsługa Unicode jest rozszerzona o `char16_t*` typy `char32_t*` ciągów i:

```cpp
// ASCII smiling face
const char*     s1 = ":-)";

// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";

// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)
const char*     s3 = u8"😇 = \U0001F607 is O:-)";

// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)
const char16_t* s4 = u"😃 = \U0001F603 is :-D";

// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)
const char32_t* s5 = U"😎 = \U0001F60E is B-)";
```

## <a name="see-also"></a>Zobacz także

[Zestawy znaków](../cpp/character-sets.md)\
[Literały numeryczne, wartości logicznych i wskaźników](../cpp/numeric-boolean-and-pointer-literals-cpp.md)\
[Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md)
