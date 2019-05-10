---
title: Literały ciągów i znakowe (C++)
ms.date: 05/07/2019
f1_keywords:
- R
helpviewer_keywords:
- literal strings [C++]
- string literals [C++]
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: d3c85854256816d5553959a16526ad0d13cf14b4
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221972"
---
# <a name="string-and-character-literals--c"></a>Literały ciągów i znakowe (C++)

C++ obsługuje różne typy ciągów i znakowe i zapewnia metody do wyrażenia wartości literału w każdej z tych typów. W kodzie źródłowym można wyrazić zawartość literały znakowe i przy użyciu zestawu znaków. Uniwersalne nazwy znaków i znaków ucieczki umożliwiają express dowolny ciąg przy użyciu tylko zestaw znaków podstawowego źródła. Nieprzetworzony literał ciągu pozwala uniknąć przy użyciu znaków ucieczki i może służyć do express wszystkie rodzaje literałów ciągów. Można również utworzyć literały std::string, bez konieczności wykonywania dodatkowych konstrukcji lub konwersji kroki.

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

Literały ciągów może mieć żadnego prefiksu lub `u8`, `L`, `u`, i `U` prefiksów do oznaczania zawęzić odpowiednio znak (pojedynczych bajtów lub wielobajtowego), UTF-8, szerokości znaków (UCS-2 lub UTF-16), UTF-16 i kodowania UTF-32. Nieprzetworzony literał ciągu może zawierać `R`, `u8R`, `LR`, `uR` i `UR` prefiksów odpowiedników pierwotnych wersji tych kodowaniach.  Aby utworzyć tymczasowy lub statycznych std::string wartości, można użyć literałów ciągu lub surowe Literały ciągu z `s` sufiks. Aby uzyskać więcej informacji zobacz sekcję Literały ciągu poniżej. Aby uzyskać więcej informacji na temat znaków podstawowgoe źródła Ustaw uniwersalne nazwy znaków i za pomocą znaków z rozszerzonych strony kodowe w kodzie źródłowym, zobacz [zestawów znaków](../cpp/character-sets.md).

## <a name="character-literals"></a>Literały znakowe

A *literału znakowego* składa się ze stałych znaków. Reprezentowany jest przez znak ujęty w znaki pojedynczego cudzysłowu. Istnieje pięć rodzaje literałów znakowych:

- Zwykły znak literały ciągów typu **char**, na przykład `'a'`

- Literały znaków UTF-8 typu **char**, na przykład `u8'a'`

- Szerokie literały znakowe typu `wchar_t`, na przykład `L'a'`

- Literały znaków UTF-16 typu `char16_t`, na przykład `u'a'`

- Literały znaków UTF-32 typu `char32_t`, na przykład `U'a'`

Znak używany dla literału znakowego może być dowolnym znakiem, z wyjątkiem znaków zarezerwowanych kreski ułamkowej odwróconej ("\\"), pojedynczego cudzysłowu (') lub nowego wiersza. Zastrzeżone znaki można określić przy użyciu sekwencji unikowej. Znaki mogą być określone przy użyciu uniwersalne nazwy znaków, tak długo, jak typ jest wystarczająco duży, aby pomieścić znak.

### <a name="encoding"></a>Kodowanie

Literały znaków są zakodowane w różny sposób na podstawie ich prefiks.

- Znak literału bez prefiksu to zwykły znak literału. Wartość zwykły znak literału zawierający pojedynczy znak sekwencji unikowej lub znaki uniwersalne nazwę, którą można przedstawić w zestawie znaków wykonywania ma wartość równą wartości liczbowej kodowania w zestawie znaków wykonywania. Zwykły znak literału zawierającego więcej niż jeden znak, sekwencja unikowa lub znaki uniwersalne nazwy to *literał wieloznakowy*. Literał wieloznakowe lub literałem zwykły znak, który nie może być przedstawiony w zestawie znaków wykonywania jest warunkowo obsługiwane, ma typ int, a jego wartość jest zdefiniowane w implementacji.

- Literał znakowy, który zaczyna się od prefiksu L jest literałem znaków dwubajtowych. Wartość literału znaku dwubajtowego, zawierający pojedynczy znak, sekwencja unikowa lub znaki uniwersalne nazwy ma wartość równą wartości liczbowej jego kodowania znaków dwubajtowych wykonywania ustawić, chyba że literału znakowego nie ma reprezentacji zestaw znaków dwubajtowych wykonania, w takim przypadku wartość jest zdefiniowane w implementacji. Wartość literału znaku dwubajtowego zawierające wiele znaków, sekwencji unikowych lub uniwersalne nazwy znaków zależy od implementacji.

- Literał znakowy, który rozpoczyna się prefiksem u8 jest literał znakowy UTF-8. Wartość literału znaku UTF-8 zawierający pojedynczy znak sekwencji unikowej lub znaki uniwersalne nazwy ma wartość równą wartości punktu kodu ISO 10646, jeśli może być reprezentowany przez pojedynczą jednostkę kodu UTF-8 (odpowiadający C0 kontrolek i Łaciński podstawowy Blok Unicode). Jeśli wartość nie może być przedstawiona przez pojedynczą jednostkę kodu UTF-8, program jest nieprawidłowo sformułowany. Literału zawierającego więcej niż jeden znak, sekwencja unikowa lub znaki uniwersalne nazwy znaków UTF-8 jest nieprawidłowo sformułowany.

- Literał znakowy, który rozpoczyna się od prefiksu u jest literał znakowy UTF-16. Wartość literału znaku UTF-16 zawierający pojedynczy znak sekwencji unikowej lub znaki uniwersalne nazwy ma wartość równą jej wartość punktu kodu ISO 10646, jeśli może być reprezentowany przez pojedynczą jednostkę kodu UTF-16 (odpowiadający płaszczyzny wielojęzycznej podstawowe ). Jeśli wartość nie może być przedstawiona przez pojedynczą jednostkę kodu UTF-16, program jest nieprawidłowo sformułowany. Literału zawierającego więcej niż jeden znak, sekwencja unikowa lub znaki uniwersalne nazwy znaków UTF-16 jest nieprawidłowo sformułowany.

- Literał znakowy, który rozpoczyna się od prefiksu U jest literał znakowy UTF-32. Wartość literału znaku UTF-32 zawierający pojedynczy znak sekwencji unikowej lub znaki uniwersalne nazwa ma wartość równą jej wartość punktu kodu ISO 10646. Literału zawierającego więcej niż jeden znak, sekwencja unikowa lub znaki uniwersalne nazwy znaków UTF-8 jest nieprawidłowo sformułowany.

###  <a name="bkmk_Escape"></a> Sekwencje unikowe

Istnieją trzy typy sekwencji wyjścia: prosta, ósemkowa i szesnastkowa. Sekwencje ucieczki mogą być jednym z następujących czynności:

|Wartość|Sekwencja unikowa|
|-----------|---------------------|
| nowy wiersz | \\n |
| Ukośnik odwrotny | \\\\ |
| tabulator poziomy | \\t |
| znak zapytania | ? lub \\? |
| tabulator pionowy | \\v |
| pojedynczy cudzysłów | \\' |
| BACKSPACE | \\b |
| podwójny cudzysłów | \\" |
| powrót karetki | \\r |
| znak null | \\0 |
| Wysuw strony | \\f |
| ósemkowy | \\ooo |
| alert (dzwonek) | \\a |
| szesnastkowo | \\xhhh |

Poniższy kod przedstawia kilka przykładów znaki ucieczki przestają być za pomocą literałów zwykły znak. Tej samej składni sekwencji ucieczki jest prawidłowy dla innych typów literałów znaków.

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

**Microsoft Specific**

Aby utworzyć wartość z zakresu od zwykły znak literału (te bez prefiksu), kompilator konwertuje znaku lub sekwencji znaków między apostrofy do wartości 8-bitowa w 32-bitową liczbę całkowitą. Wielu znaków w literale wypełnienia odpowiednich bajtów, zgodnie z potrzebami z wyższego rzędu do niskiego rzędu. Aby utworzyć **char** wartości, kompilator zajmuje mniej znaczący bajt. Aby utworzyć **wchar_t** lub `char16_t` wartości, kompilator przyjmuje word niskiego rzędu. Kompilator wyświetla ostrzeżenie, że wynik został obcięty, jeśli wszystkie bity są ustawione powyżej przydzielonych bajtów lub word.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
```

Sekwencja unikowa ósemkowa jest ukośnikiem sekwencji z maksymalnie 3 cyframi ósemkowymi. Zachowanie ósemkowej sekwencji ucieczki, mogą zawierać więcej niż trzy cyfry jest traktowany jako sekwencja ósemkową 3-cyfrowy i kolejne cyfry jako znaki; może to dawać Zaskakujące wyniki. Na przykład:

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Sekwencje unikowe, które mogą zawierać znaki inne niż ósemkowe, są oceniane jako ósemkowej sekwencji do ostatniego znaku ósemkową, następuje pozostałe znaki. Na przykład:

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje znak `x`, a następnie sekwencja znaków szesnastkowych. Sekwencja wyjścia niezawierająca cyfr szesnastkowych powoduje błąd kompilatora C2153: "literały szesnastkowe muszą mieć co najmniej jedną cyfrę szesnastkową". Zera wiodące są ignorowane. Sekwencja unikowa, która ma znaki szesnastkowe i nieszesnastkowe, zostanie potraktowana jako szesnastkowa sekwencja unikowa maksymalnie ostatnich znaków szesnastkowych następują znaki inne niż szesnastkowe.   W zwykłych i prefiksem u8 literał znakowy najwyższa wartość szesnastkowa to 0xFF. W prefiksem L lub prefiks u szeroki literał znakowy najwyższa wartość szesnastkowa to 0xFFFF. W prefiks U szerokiego literału znakowego najwyższa wartość szesnastkowa to 0xFFFFFFFF.

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Jeśli szeroki literał znakowy prefiks `L` zawiera więcej niż jeden znak, wartość jest pobierana z pierwszego znaku. Kolejne znaki są ignorowane, w odróżnieniu od zachowania równoważne zwykły znak literału.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**END specyficzny dla Microsoft**

Znak ukośnika odwrotnego (\\) jest znakiem kontynuacji wiersza umieszczone na końcu wiersza. Jeśli chcesz, aby znak ukośnika odwrotnego, tak aby pojawiało się jako literał znakowy, należy wpisać dwa ukośniki odwrotne w wierszu (`\\`). Aby uzyskać więcej informacji na temat wstawić znak kontynuacji wiersza, zobacz [etapy translacji](../preprocessor/phases-of-translation.md).

###  <a name="bkmk_UCN"></a> Uniwersalne nazwy znaków

Literały znakowe i (natywnego innego niż surowe) Literały ciągu dowolny znak może być reprezentowany przez nazwę znaki uniwersalne.  Uniwersalne nazwy znaków są utworzone przez prefiks, który \U, a następnie przez punkt kodu Unicode osiem cyfr lub \u prefiks następuje punkt kodu Unicode czterocyfrowa. Odpowiednio wszystkich osiem lub cztery cyfry, musi być obecny można utworzyć nazwy sformułowany znaki uniwersalne.

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Pary zastępcze

Uniwersalne nazwy znaków nie może zakodować wartości w zakresie punkt kodu D800 DFFF zastępczy. Dla pary zastępcze Unicode, należy określić nazwę znaki uniwersalne za pomocą `\UNNNNNNNN`, gdzie NNNNNNNN jest punkt 8 cyfrowym kodem znaku. Kompilator generuje parę zastępczą, jeśli jest to wymagane.

W języku C ++ 03 język tylko podzestaw znaków, które mają być reprezentowane przez ich uniwersalne nazwy znaków mogą oraz dozwolone niektóre uniwersalne nazwy znaków, które faktycznie nie reprezentują żadnych prawidłowych znaków Unicode. Ten problem został rozwiązany w standardem C ++ 11. W języku C ++ 11 zarówno literały znakowe i i identyfikatory mogą używać uniwersalne nazwy znaków.  Aby uzyskać więcej informacji na temat uniwersalne nazwy znaków, zobacz [zestawów znaków](../cpp/character-sets.md). Aby uzyskać więcej informacji na temat systemu Unicode, zobacz [Unicode](https://msdn.microsoft.com/library/dd374081). Aby uzyskać więcej informacji dotyczących par zastępczych, zobacz [pary zastępcze i znaki dodatkowe](/windows/desktop/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Literały ciągu

Literał ciągu znaków reprezentuje sekwencję znaków, które razem tworzą ciąg zakończony znakiem null. Znaki muszą być ujęte w znaki podwójnego cudzysłowu. Istnieją następujące rodzaje literałów ciągów:

### <a name="narrow-string-literals"></a>Wąskie literały.

Wąskiego literału ciągu jest — prefiks, podwójny cudzysłów tablicy rozdzielany, zakończony wartością null typu `const char[n]`, gdzie n to długość tablicy bajtów. Wąski literał ciągu może zawierać dowolny znak graficzny oprócz podwójnego cudzysłowu (`"`), ukośnika odwrotnego (`\`), lub znak nowego wiersza. Wąski literał ciągu może również zawierać nazwy wymienione powyżej i uniwersalnych znaków sekwencji ucieczki, które mieszczą się w bajt.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Ciągi kodowany w formacie UTF-8

Ciąg kodowany w formacie UTF-8 jest prefiksem u8, podwójny cudzysłów tablicy rozdzielany, zakończony wartością null typu `const char[n]`, gdzie n to długość zakodowanego tablicy bajtów. Literał ciągu prefiksem u8 mogą zawierać dowolny znak graficzny oprócz podwójnego cudzysłowu (`"`), ukośnika odwrotnego (`\`), lub znak nowego wiersza. Literał ciągu prefiksem u8 może również zawierać znak ucieczki, który sekwencje wymienionych powyżej i dowolną nazwę znaki uniwersalne.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Literały szerokiego ciągu

Szerokiego literału ciągu jest tablicą zakończoną znakiem null stałej **wchar_t** , jest poprzedzony przez "`L`" i zawiera dowolny znak graficzny oprócz podwójnego cudzysłowu ("), ukośnika odwrotnego (\\), lub znak nowego wiersza. Szerokiego literału ciągu może zawierać znak ucieczki, który sekwencje wymienionych powyżej i dowolną nazwę znaki uniwersalne.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16t-and-char32t-c11"></a>char16_t i char32_t (C ++ 11)

C ++ 11 wprowadza przenośnym `char16_t` (16-bitowych Unicode) i `char32_t` (32-bitowych Unicode) typów znaków:

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Surowe Literały ciągu (C ++ 11)

Literał ciągu surowego jest tablicą zakończoną znakiem null — dowolnego znaku typu — zawierającą dowolny znak graficzny, w tym podwójny cudzysłów ("), ukośnika odwrotnego (\\), lub znak nowego wiersza. Surowe Literały ciągu są często używane w wyrażeniach regularnych, które używają klas znaku, a także w ciągach HTML i XML. Aby uzyskać przykłady zobacz następujący artykuł: [Bjarne'a Stroustrupa często zadawane pytania dotyczące języka C ++ 11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Ogranicznik jest zdefiniowane przez użytkownika sekwencją do 16 znaków bezpośrednio poprzedza nawias otwierający nieprzetworzonego literału ciągu, który następuje bezpośrednio po jego nawiasie zamykającym.  Na przykład w `R"abc(Hello"\()abc"` jest sekwencja ogranicznika `abc` , a zawartość ciągu `Hello"\(`. Aby zapewnić rozróżnianie ciągów pierwotne, które zawierają znaki cudzysłowu podwójnego i nawiasy, można użyć ogranicznika. To powoduje błąd kompilatora:

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

Ale ogranicznik rozwiązuje to:

```cpp
const char* good_parens = R"xyz()")xyz";
```

Możesz utworzyć nieprzetworzony literał ciągu w którym znajduje się nowy wiersz (nie znak wyjścia) w źródle:

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>STD::String literały (C ++ 14)

literały STD::String są biblioteki standardowej implementacji literały definiowane przez użytkownika (patrz poniżej), które są reprezentowane jako "xyx" s (ze `s` sufiks). Tego rodzaju literału ciągu tworzy tymczasowego obiektu tego typu std::string, std::wstring, std::u32string lub std::u16string w zależności od prefiks, który jest określony. Gdy używany jest żadnego prefiksu, jak powyżej, std::string jest generowany. L "xyz" s, produkuje std::wstring. Tworzy s u "xyz" [std::u16string](../standard-library/string-typedefs.md#u16string)i tworzy s U "xyz" [std::u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

Sufiks s może być również na surowe Literały ciągu:

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

literały STD::String są zdefiniowane w przestrzeni nazw `std::literals::string_literals` w \<ciągu > pliku nagłówka. Ponieważ `std::literals::string_literals`, i `std::literals` jako są deklarowane [wbudowane przestrzenie nazw](../cpp/namespaces-cpp.md), `std::literals::string_literals` jest automatycznie traktowany tak, jakby należała bezpośrednio w przestrzeni nazw `std`.

### <a name="size-of-string-literals"></a>Rozmiar literałów ciągu

Dla znaków ANSI\* ciągów i innych pojedynczych bajtów kodowania (nie UTF-8), rozmiar (w bajtach) literału ciągu jest liczbą znaków plus 1 w przypadku końcowego znaku null. Dla wszystkich innych typów ciągów rozmiar nie jest ściśle powiązany do liczby znaków. UTF-8 używa do czterech elementów char do zakodowania niektóre *jednostki kodu*i char16_t lub wchar_t zakodowane jako UTF-16 może na użytek dwa elementy (łącznie z czterech bajtów) do zakodowania pojedynczej *jednostki kodu*.   W tym przykładzie przedstawiono rozmiar szerokiego ciągu literału w bajtach:

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Należy zauważyć, że `strlen()` i `wcslen()` nie zawierają rozmiaru kończącego znaku null, którego rozmiar jest równy rozmiarowi elementu typu string: jeden bajt na znak\* ciąg dwóch bajtów na wchar_t\* lub char16_t\*ciągów i cztery bajty na char32_t\* ciągów.

Maksymalna długość literału ciągu wynosi 65 535 bajtów. Ten limit dotyczy zarówno literałów wąskich, jak i szerokich.

### <a name="modifying-string-literals"></a>Modyfikowanie literałów ciągów

Ponieważ literały ciągów (z wykluczeniem literały std:string) są stałe, próba zmodyfikowania ich — na przykład `str[2] = 'A'`— powoduje wystąpienie błędu kompilatora.

**Microsoft Specific**

W programie Microsoft C++ literału ciągu można użyć do zainicjowania wskaźnika do wartości innej niż stała **char** lub **wchar_t**. Jest dozwolona w kodzie C99, ale jest przestarzała w języku C ++ 98 i usunięte w C ++ 11. Próba zmodyfikowania ciągu powoduje naruszenie zasad dostępu, jak w poniższym przykładzie:

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Użytkownik może spowodować, że kompilator będzie emitował błąd, gdy literał ciągu jest konwertowana na wskaźnik znak non_const po ustawieniu [/Zc: strictstrings (Wyłączanie konwersji typów literału ciągu)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) — opcja kompilatora. Firma Microsoft zaleca zgodnych ze standardami kodu przenośnego. Jest również dobrym rozwiązaniem, aby użyć **automatycznie** — słowo kluczowe do deklarowania wskaźników zainicjowanych literałami ciągów, ponieważ jest on rozpoznawany jako poprawny typ (const). Na przykład w tym przykładzie kodu przechwytywana próba zapisu do literału ciągu w czasie kompilacji:

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

W niektórych przypadkach mogą być połączone identyczne literały ciągów, aby zaoszczędzić miejsce w pliku wykonywalnym. W grupowaniu literałów ciągów kompilator powoduje, że wszystkie odwołania do określonego literału ciągu wskazują w tej samej lokalizacji w pamięci, a nie każde odwołanie wskaż osobne wystąpienie literału ciągu. Aby włączyć buforowanie ciągów, należy użyć [/GF](../build/reference/gf-eliminate-duplicate-strings.md) — opcja kompilatora.

**End specyficzny dla Microsoft**

### <a name="concatenating-adjacent-string-literals"></a>Powiązanie literałów ciągów sąsiadujących

Literały ciągów sąsiadujących szeroki lub wąski są łączone. Deklaracja ta:

```cpp
char str[] = "12" "34";
```

jest identyczny z niniejszą deklaracją:

```cpp
char atr[] = "1234";
```

i do tej deklaracji:

```cpp
char atr[] =  "12\
34";
```

Używanie osadzonych szesnastkowych kodów wyjścia do określania literałów ciągów może spowodować nieoczekiwane rezultaty. Poniższy przykład jest przeznaczony do tworzenia ciągu literału zawierającego znak ASCII 5, a następnie znaki f, i, v i e:

```cpp
"\x05five"
```

Rzeczywisty wynik jest szesnastkową 5F, co w kodzie ASCII, podkreślenie, następują znaki i, v i e. Aby uzyskać odpowiedni wynik, użyj jednej z tych:

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

literały STD::String, ponieważ są one typy std::string, mogą być łączone z + — operator, który jest zdefiniowany dla [basic_string](../standard-library/basic-string-class.md) typów. Mogą one również być łączone w taki sam sposób jak w przylegającymi literałami ciągu. W obu przypadkach muszą być zgodne kodowanie ciągu i sufiksu:

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Literały ciągów ze uniwersalne nazwy znaków

(Natywne inne niż surowe) Literały ciągu można używać uniwersalne nazwy znaków do reprezentowania dowolny znak, tak długo, jak nazwa znaki uniwersalne mogą być zakodowane jako jeden lub więcej znaków w typu string.  Na przykład nazwę znaki uniwersalne reprezentujący znak rozszerzony nie może zostać zakodowana w ciągu wąskiego przy użyciu strony kodowej ANSI, ale mogą być zakodowane w ciągach wąskie w niektórych stron kodu wielobajtowego lub UTF-8 ciągów lub ciąg znaków dwubajtowych. W języku C ++ 11, char16_t rozszerzoną obsługę standardu Unicode\* i char32_t\* typów ciągów:

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

[Zestawy znaków](../cpp/character-sets.md)<br/>
[Literały numeryczne, wartości logicznych i wskaźników](../cpp/numeric-boolean-and-pointer-literals-cpp.md)<br/>
[Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md)
