---
title: "Literały ciągów i znakowe (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: R
dev_langs: C++
helpviewer_keywords:
- L constant
- escape sequences
- Null strings, null-terminated strings
- literal strings, C++
- Null strings
- string literals, syntax
- string literals
- literal strings
- strings [C++], string literals
- NULL, character constant
- wide characters, strings
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 37e5b86dfdef9c49e0e59c28d36ba4622238eced
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="string-and-character-literals--c"></a>Literały ciągów i znakowe (C++)
C++ obsługuje różne typy ciągów i znakowe i zapewnia sposobów express wartości literałów dla każdego z tych typów. W kodzie źródłowym express jest zawartość z literały znaków i ciąg, przy użyciu zestawu znaków. Uniwersalne nazwy znaków i znaki specjalne umożliwia express dowolny ciąg przy użyciu zestawu znaków podstawowego źródła. Nieprzetworzonego literału ciągu pozwala uniknąć przy użyciu znaki specjalne i może służyć do express wszystkie typy literałów ciągów. Można również utworzyć literałów std::string bez konieczności wykonać kroki konwersji lub dodatkowe konstrukcji.  
  
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
  
 Literały ciągu nie może mieć bez prefiksu lub `u8`, `L`, `u`, i `U` prefiksów w celu określenia zawęzić odpowiednio znaków (jednobajtowe i wielobajtowe), znaków UTF-8, dwubajtowe (UCS 2 lub UTF-16), UTF-16 i kodowania UTF-32. Może mieć nieprzetworzonego literału ciągu `R`, `u8R`, `LR`, `uR` i `UR` prefiksów dla odpowiedników pierwotnych wersji tych kodowania.  Do tworzenia wartości tymczasowej lub statycznej std::string, można użyć literałów ciągów lub literały nieprzetworzony ciąg z `s` sufiks. Aby uzyskać więcej informacji zobacz sekcję literałów ciągu poniżej. Aby uzyskać więcej informacji na znak źródłowy podstawowego zestawu uniwersalne nazwy znaków i przy użyciu znaków z rozszerzonego strony kodowe w kodzie źródłowym, zobacz [zestawów znaków](../cpp/character-sets2.md).  
  
## <a name="character-literals"></a>Literały znaków  
 A *literał znaku* składa się z stałej znaków. Odpowiada on ujęta w cudzysłów pojedynczy znak. Istnieje pięć rodzajów literały znaków:  
  
-   Literały znaków zwykłej typu `char`, na przykład`'a'`  
  
-   Literały znaków UTF-8 typu `char`, na przykład`u8'a'`  
  
-   Literały znaków dwubajtowych typu `wchar_t`, na przykład`L'a'`  
  
-   Literały znaków UTF-16 typu `char16_t`, na przykład`u'a'`  
  
-   Literały znaków UTF-32 typu `char32_t`, na przykład`U'a'`  
  
 Znak używany dla literał znakowy może być dowolny znak, z wyjątkiem ukośnik odwrotny zarezerwowanych znaków ("\\"), apostrofu (') lub znakami nowego wiersza. Zarezerwowanych znaków można określić przy użyciu sekwencji ucieczki. Znaki można określić za pomocą uniwersalne nazwy znaków, tak długo, jak typ jest wystarczająco duży, aby pomieścić znak.  
  
### <a name="encoding"></a>Kodowanie  
 Literały znaków są zakodowane inaczej na podstawie ich prefiks.  
  
-   Bez prefiksu literał znakowy jest literał znakowy zwykłej. Wartość literału znaku zwykłej zawierający pojedynczy znak sekwencji specjalnej lub nazwa zawierająca znaki uniwersalne, który może być reprezentowany w zestaw znaków wykonania ma wartość równą wartości liczbowe Kodowanie zestawu znaków wykonywania. Zwykłe literał znakowy zawierający więcej niż jeden znak sekwencji ucieczki i Uniwersalna nazwa znaku jest *literał wieloznakowy*. Literał literał lub literał zwykłej znaku, który nie może być reprezentowany w zestaw znaków wykonania jest warunkowo obsługiwane, ma typ int i jej wartość jest zdefiniowane w implementacji.  
  
-   Literał znaku, który rozpoczyna się od prefiksu L jest literałem znaków dwubajtowych. Wartość literału znaków dwubajtowych zawierający pojedynczy znak, sekwencja unikowa lub Uniwersalna nazwa znaku ma wartość równą wartości liczbowe jego kodowania znaków dwubajtowych wykonywania ustawić, chyba że literał znaków nie ma reprezentacji zestaw znaków dwubajtowych wykonywania, w takim przypadku wartość jest zdefiniowane w implementacji. Wartość literału znaków dwubajtowych zawierający wiele znaki unikowe i uniwersalne nazwy znaków jest zdefiniowane w implementacji.  
  
-   Literał znaku, który rozpoczyna się od prefiksu u8 jest literału znaku UTF-8. Wartość literału znaku UTF-8 zawierający pojedynczy znak sekwencji specjalnej lub Uniwersalna nazwa znaku ma wartość równą jej wartość punktu kodu ISO 10646, jeśli może być reprezentowany przez pojedynczą jednostkę kodu UTF-8 (odpowiadający C0 kontrolek i Łaciński podstawowy Blok Unicode). Jeśli wartość nie może być reprezentowany przez pojedynczą jednostkę kodu UTF-8, program jest źle sformułowany. Zawierających więcej niż jeden znak, sekwencja unikowa lub Uniwersalna nazwa znaku literału znaku UTF-8 jest źle sformułowany.  
  
-   Literał znaku, który rozpoczyna się od prefiksu u jest literału znaku UTF-16. Wartość literału znaku UTF-16 zawierający pojedynczy znak sekwencji specjalnej lub Uniwersalna nazwa znaku ma wartość równą jej wartość punktu kodu ISO 10646, jeśli może być reprezentowany przez pojedynczą jednostkę kodu UTF-16 (odpowiadający podstawowe płaszczyzny wielu języków ). Jeśli wartość nie może być reprezentowany przez pojedynczą jednostkę kodu UTF-16, program jest źle sformułowany. Zawierających więcej niż jeden znak, sekwencja unikowa lub Uniwersalna nazwa znaku literału znaku UTF-16 jest źle sformułowany.  
  
-   Literał znaku, który rozpoczyna się od prefiksu U jest literału znaku UTF-32. Wartość literału znaku UTF-32 zawierający pojedynczy znak sekwencji specjalnej lub Uniwersalna nazwa znaku ma wartość równą jej wartość punktu kodu ISO 10646. Zawierających więcej niż jeden znak, sekwencja unikowa lub Uniwersalna nazwa znaku literału znaku UTF-8 jest źle sformułowany.  
  
###  <a name="bkmk_Escape"></a>Sekwencje unikowe  
 Istnieją trzy rodzaje sekwencji unikowych: prosty, ósemkowe i szesnastkowe. Sekwencje unikowe może być jedną z następujących czynności:  
  
|Wartość|Sekwencja specjalna|Wartość|Sekwencja specjalna|  
|-----------|---------------------|-----------|---------------------|  
|nowy wiersz|\n|ukośnik odwrotny|\\\|  
|Tabulator poziomy|\t|znak zapytania|? lub \\?|  
|Tabulator pionowy|\v|pojedynczy cudzysłów|\\'|  
|BACKSPACE|\b|podwójnego cudzysłowu|\\"|  
|powrót karetki|\r|znak null|\0|  
|Wysuw strony|\f|ósemkowy|\ooo|  
|Alert (dzwonka)|\a|szesnastkowo|\xhhh|  
  
 Poniższy kod przedstawia niektóre przykłady znaków zmienionym przy użyciu zwykłej znak literały. Taka sama składnia sekwencji ucieczki jest prawidłowa dla innych typów literału znaku.  
  
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
  
 **Dotyczące firmy Microsoft**  
  
 Aby utworzyć wartość ze zwykłej literał znakowy (tych bez prefiksu), kompilator konwertuje znak lub sekwencja znaków między apostrofy do wartości 8-bitową w 32-bitową liczbę całkowitą. Wielu znaków w literale wypełnienia odpowiednich bajtów odpowiednio z znaczących znaczącymi bitami. Aby utworzyć `char` wartość, kompilator zajmuje mniej znaczącego bajtu. Aby utworzyć `wchar_t` lub `char16_t` wartość, kompilator przyjmuje word znaczącymi bitami. Kompilator ostrzega, że wynik został obcięty, jeśli wszystkie bity zostały ustawione powyżej przydzielonych bajtów lub word.  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'  
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 Ósemkowa sekwencja unikowa jest ukośnik odwrotny następuje sekwencję maksymalnie 3 ósemkowe cyfr. Zachowanie ósemkową sekwencja, które może zawierać więcej niż trzech cyfr jest traktowane jako ósemkowe sekwencję 3-cyfrowy następuje kolejnych cyfr jako znaków; daje to zaskakująco wyników. Na przykład:  
  
```cpp  
char c1 = '\100';   // '@'  
char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 Sekwencje unikowe, które ma zawierać znaków — są oceniane jako ósemkową sekwencja maksymalnie po ostatnim znaku ósemkowe następuje pozostałych znaków. Na przykład:  
  
```cpp  
char c3 = '\009';   // '9'  
char c4 = '\089';   // C4305, C4309, truncates to '9'  
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 Szesnastkowa sekwencja unikowa się ukośnikiem odwrotnym i znakiem `x`, a następnie sekwencji cyfr szesnastkowych. Błąd kompilatora C2153 powoduje — sekwencja specjalna zawierający nie cyfr szesnastkowych: "literały szesnastkowe musi mieć co najmniej jedną cyfrę szesnastkową". Zera wiodące są ignorowane. Sekwencja specjalna, który wydaje się być znaków szesnastkowych i inny niż szesnastkowy jest szacowana jako szesnastkowa sekwencja unikowa maksymalnie ostatnich znaków szesnastkowych, następują znaki inny niż szesnastkowy.   W zwykłych i prefiksem u8 literał znakowy największa wartość szesnastkowa jest 0xFF. W prefiksem L lub prefiksem u literał znaków typu wide największa wartość szesnastkowa jest 0xFFFF. W prefiksem U literał znaków typu wide największa wartość szesnastkowa jest 0xFFFFFFFF.  
  
```cpp  
char c6 = '\x0050'; // 'P'  
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 Jeśli literał znaków typu wide prefiksem `L` zawiera więcej niż jeden znak, wartość jest pobierana z pierwszego znaku. W przeciwieństwie do zachowania równoważne literał znakowy zwykłej kolejne znaki są ignorowane.  
  
```cpp  
wchar_t w1 = L'\100';   // L'@'  
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored   
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored  
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored  
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored  
wchar_t w6 = L'\x0050'; // L'P'  
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Znak ukośnika odwrotnego (\\) jest znak kontynuacji wiersza, gdy znajduje się na końcu linii. Jeśli chcesz, aby były wyświetlane jako literał znakowy ukośnikiem odwrotnym, należy wpisać dwa razy w wierszu (`\\`). Aby uzyskać więcej informacji na temat znak kontynuacji wiersza, zobacz [fazy tłumaczenia](../preprocessor/phases-of-translation.md).  
  
###  <a name="bkmk_UCN"></a>Uniwersalne nazwy znaków  
 Literały znaków i literały macierzystego (z systemem innym niż — raw) ciągu znaków mogą być reprezentowane przez nazwa zawierająca znaki uniwersalne.  Uniwersalne nazwy znaków są utworzone przez prefiks, który \U po której następują, 8 cyfrowy kod znaku Unicode, lub \u prefiks następuje punkt kodu Unicode czterocyfrowej. Wszystkie osiem lub cztery cyfry, odpowiednio, musi występować aby nazwa zawierająca znaki uniwersalne poprawnie sformułowany.  
  
```cpp  
char u1 = 'A';          // 'A'  
char u2 = '\101';       // octal, 'A'   
char u3 = '\x41';       // hexadecimal, 'A'  
char u4 = '\u0041';     // \u UCN 'A'  
char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **Znaki dwuskładnikowe**  
  
 Uniwersalne nazwy znaków nie można zakodować wartości zakresu punktów kodowych Surogat D800 DFFF. Dla Znaki dwuskładnikowe Unicode, należy określić nazwa zawierająca znaki uniwersalne za pomocą `\UNNNNNNNN`, gdzie NNNNNNNN jest punkt 8 cyfrowy kod znaku. Kompilator generuje para zastępcza, jeśli jest to wymagane.  
  
 W języku C ++ 03 języka tylko dozwolone podzbiór znaków może być reprezentowana przez ich uniwersalne nazwy znaków oraz dozwolone niektóre uniwersalne nazwy znaków, które faktycznie nie reprezentują żadnych prawidłowych znaków Unicode. Problem został rozwiązany w standardem C ++ 11. W języku C ++ 11 zarówno znaków i ciągu literałów i identyfikatory mogą używać uniwersalne nazwy znaków.  Aby uzyskać więcej informacji dotyczących uniwersalne nazwy znaków, zobacz [zestawów znaków](../cpp/character-sets2.md). Aby uzyskać więcej informacji na temat Unicode, zobacz [Unicode](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx). Aby uzyskać więcej informacji na temat Znaki dwuskładnikowe, zobacz [Znaki dwuskładnikowe i dodatkowe znaki](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx).  
  
## <a name="string-literals"></a>Literały ciągu  
 Literał ciągu reprezentuje sekwencji znaków, które tworzą ciąg znaków zakończony znakiem null. Znaki muszą być ujęte w cudzysłów podwójny. Dostępne są następujące rodzaje literałów ciągu:  
  
### <a name="narrow-string-literals"></a>Literały ciągu wąskie  
 Literał ciągu wąskie jest-prefiksem, podwójnego cudzysłowu rozdzielone, zerem tablicą typu `const char[n]`, gdzie n to długość tablicy w bajtach. Literał ciągu wąskie może zawierać znaków grafiki, z wyjątkiem podwójnego cudzysłowu (`"`), ukośnik odwrotny (`\`), lub znakiem nowego wiersza. Literał ciągu wąskie może również zawierać nazwy znaków wymienionych powyżej i uniwersalnych sekwencji ucieczki, które mieszczą się w bajt.  
  
```cpp  
const char *narrow = "abcd";  
  
// represents the string: yes\no  
const char *escaped = "yes\\no";  
```  
  
#### <a name="utf-8-encoded-strings"></a>Ciągi kodowany w formacie UTF-8  
  
 Ciąg kodowany w formacie UTF-8 jest prefiksem u8, podwójnego cudzysłowu rozdzielone, zerem tablicą typu `const char[n]`, gdzie n to długość zakodowanego tablicy w bajtach. Literał ciągu prefiksem u8 może zawierać znaków grafiki, z wyjątkiem podwójnego cudzysłowu (`"`), ukośnik odwrotny (`\`), lub znakiem nowego wiersza. Literał ciągu prefiksem u8 może również zawierać specjalne, które sekwencje wymienione powyżej i wszelkie Uniwersalna nazwa znaku.  
  
```cpp  
const char* str1 = u8"Hello World";  
const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### <a name="wide-string-literals"></a>Literały ciągu typu Wide  
 Literał ciągu typu wide jest tablicą zerem stałej `wchar_t` który prefiks "`L`" i zawiera wszystkie graficzne znaku z wyjątkiem podwójnego cudzysłowu ("), ukośnik odwrotny (\\), lub znakiem nowego wiersza. Szerokiego literału ciągu może zawierać specjalne, które sekwencje wymienione powyżej i wszelkie Uniwersalna nazwa znaku.  
  
```cpp  
const wchar_t* wide = L"zyxw";  
const wchar_t* newline = L"hello\ngoodbye";  
```  
  
#### <a name="char16t-and-char32t-c11"></a>char16_t i char32_t (C ++ 11)  
  
 C ++ 11 wprowadza komputer przenośny `char16_t` (16-bitowych Unicode) i `char32_t` (32-bitowych Unicode) typów znaków:  
  
```cpp  
auto s3 = u"hello"; // const char16_t*  
auto s4 = U"hello"; // const char32_t*  
```  
  
### <a name="raw-string-literals-c11"></a>Literały ciągu surowego (C ++ 11)  
 Nieprzetworzonego literału ciągu jest tablicą zerem — dowolnego typu znak — zawiera dowolny znak grafiki, w tym podwójny cudzysłów ("), ukośnik odwrotny (\\), lub znakiem nowego wiersza. Literały ciągu pierwotnych są często używane w wyrażeniach regularnych korzystających z klas znaków i ciągi kodu HTML i XML ciągów. Aby uzyskać przykłady, zobacz następujący artykuł: [Bjarne Stroustrup — często zadawane pytania na C ++ 11](http://go.microsoft.com/fwlink/p/?linkid=401172).  
  
```cpp  
// represents the string: An unescaped \ character  
const char* raw_narrow = R"(An unescaped \ character)";  
const wchar_t* raw_wide = LR"(An unescaped \ character)";  
const char*       raw_utf8  = u8R"(An unescaped \ character)";  
const char16_t* raw_utf16 = uR"(An unescaped \ character)";  
const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 Ogranicznik jest zdefiniowane przez użytkownika sekwencją maksymalnie 16 znaków bezpośrednio przed otwierającym nawiasem nieprzetworzonego literału ciągu, który poniższą jego nawiasu zamykającego.  Na przykład w `R"abc(Hello"\()abc"` jest sekwencja ogranicznika `abc` , a zawartość ciągu `Hello"\(`. Ogranicznik służy do odróżniania raw ciągi, które zawierają cudzysłowy podwójne i nawiasy. Powoduje to błąd kompilatora:  
  
```cpp  
// meant to represent the string: )"  
const char* bad_parens = R"()")";  // error C2059  
```  
  
 Ale ogranicznik rozpoznaje ją:  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 Można utworzyć nieprzetworzonego literału ciągu w którym w źródle jest nowym wierszem (nie ze zmienionym znaczeniem znaku):  
  
```cpp  
// represents the string: hello  
//goodbye  
const wchar_t* newline = LR"(hello  
goodbye)";  
```  
  
### <a name="stdstring-literals-c14"></a>STD::String literały (C ++ 14)  
 literały STD::String są biblioteki standardowej implementacji literały definiowane przez użytkownika (patrz poniżej), które są prezentowane w postaci "xyx" s (z `s` sufiks). Tego rodzaju literału ciągu tworzy tymczasowy obiekt typu std::string, std::wstring, std::u32string lub std::u16string w zależności od prefiks, który został określony. W przypadku bez prefiksu jako powyżej, std::string jest generowany. L "xyz" s tworzy std::wstring. Tworzy s u "xyz" [std::u16string](../standard-library/string-typedefs.md#u16string)i tworzy s U "xyz" [std::u32string](../standard-library/string-typedefs.md#u32string).  
  
```cpp  
//#include <string>  
//using namespace std::string_literals;  
string str{ "hello"s };  
string str2{ u8"Hello World" };  
wstring str3{ L"hello"s };  
u16string str4{ u"hello"s };  
u32string str5{ U"hello"s };  
```  
  
 Sufiks s może być również używany na literały nieprzetworzony ciąg:  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 literały STD::String są zdefiniowane w przestrzeni nazw `std::literals::string_literals` w \<ciągu > pliku nagłówka. Ponieważ `std::literals::string_literals`, i `std::literals` jako są zadeklarowane [przestrzenie nazw wbudowanego](../cpp/namespaces-cpp.md), `std::literals::string_literals` automatycznie jest traktowana tak, jakby należały go bezpośrednio w przestrzeni nazw `std`.  
  
### <a name="size-of-string-literals"></a>Rozmiar literałów ciągu  
 Dla znaków ANSI\* ciągów i innych jednobajtowe kodowania (nie UTF-8), rozmiar (w bajtach) literału ciągu jest to liczba znaków plus 1 znak końcowy null. Dla wszystkich innych typów ciąg rozmiar nie jest ściśle powiązana z liczby znaków. UTF-8 używa maksymalnie cztery elementy char do kodowania niektóre *kodu jednostki*i char16_t lub wchar_t zakodowane jako UTF-16 może Użyj dwa elementy (dla wszystkich czterech bajtów) do kodowania pojedynczy *jednostki kodu*.   Ten przykład przedstawia literału w bajtach rozmiar ciąg typu wide:  
  
```cpp  
const wchar_t* str = L"Hello!";  
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 Zwróć uwagę, że `strlen()` i `wcslen()` nie dołączaj rozmiar znak końcowy null, którego rozmiar jest równy rozmiarowi elementu typu string: jednego bajtu na ciąg znaków *, dwa bajty na wchar_t\* lub char16_t\* ciągów, i czterech bajtów na char32_t\* ciągów.  
  
 Maksymalna długość literału ciągu znaków wynosi 65 535 bajtów. Ten limit dotyczy zarówno literały wąski ciąg, jak i literały ciągu typu wide.  
  
### <a name="modifying-string-literals"></a>Modyfikowanie literałów ciągów  
 Ponieważ literałów ciągu (nie w tym literały std:string) są stałe, w trakcie modyfikowania ich — na przykład str [2] = "A" — powoduje błąd kompilatora.  
  
 **Dotyczące firmy Microsoft**  
  
 W programie Visual C++ można użyć literału ciągu do zainicjowania wskaźnika do elementu niebędącego stałą `char` lub `wchar_t`. To jest dozwolona w kodzie C99, ale jest przestarzała w języku C ++ 98 i usunąć w języku C ++ 11. Próba zmodyfikować ciąg spowoduje naruszenie zasad dostępu, jak w poniższym przykładzie:  
  
```cpp  
wchar_t* str = L"hello";  
str[2] = L'a'; // run-time error: access violation  
```  
  
 Może spowodować kompilatora emitować wystąpił błąd podczas konwersji literału ciągu na wskaźnik znak non_const po ustawieniu [/Zc: strictstrings (Wyłączanie konwersji typów literału ciągu)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) — opcja kompilatora. Firma Microsoft zaleca zgodny ze standardami kodu przenośnego. Jest również dobrym rozwiązaniem, aby użyć `auto` — słowo kluczowe, aby zadeklarować ciąg zainicjować literał wskaźników, ponieważ rozpoznawany poprawnego typu (const). Na przykład w tym przykładzie kodu przechwytuje próba zapisu z ciągiem literału w czasie kompilacji:  
  
```cpp  
auto str = L"hello";  
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 W niektórych przypadkach można stosować literały ciągu identyczne aby zaoszczędzić miejsce w pliku wykonywalnego. W puli literał ciągu przyczyny kompilatora wszystkie odwołania do konkretnego literału ciągu na punkt w tej samej lokalizacji w pamięci, zamiast odwołanie do każdego punktu do oddzielnego wystąpienia literału ciągu. Aby włączyć buforowanie ciągów, za pomocą [/GF](../build/reference/gf-eliminate-duplicate-strings.md) — opcja kompilatora.  
  
 **Końcowy określonych firmy Microsoft**  
  
### <a name="concatenating-adjacent-string-literals"></a>Łączenie literałów ciągu sąsiadujących ze sobą  
 Literały sąsiadujących ze sobą szeroki lub wąski ciąg są połączone. Ta deklaracja:  
  
```cpp  
char str[] = "12" "34";  
```  
  
 jest taka sama jak tej deklaracji:  
  
```cpp  
char atr[] = "1234";  
```  
  
 i tej deklaracji:  
  
```cpp  
char atr[] =  "12\  
34";  
```  
  
 Za pomocą kody osadzonych szesnastkowe ESC, aby określić Literały ciągu może spowodować nieoczekiwane wyniki. Poniższy przykład zamierza utworzyć literał ciągu zawiera znak ASCII 5, a następnie f znaków i v i e:  
  
```cpp  
"\x05five"  
```  
  
 Rzeczywisty wynik jest 5F szesnastkowa, która jest kod znaku podkreślenia poprzedzającą znaki ASCII i v i e. Aby uzyskać poprawny wynik, użyj jednej z tych:  
  
```cpp  
"\005five"     // Use octal literal.  
"\x05" "five"  // Use string splicing.  
```  
  
 literały STD::String, ponieważ są one typy std::string może zostać połączony z + — operator, który jest zdefiniowany dla [basic_string —](../standard-library/basic-string-class.md) typów. Mogą one również zostać połączony w taki sam sposób jak literały ciągu sąsiadujących ze sobą. W obu przypadkach musi być zgodna z kodowaniem ciągu i sufiksu:  
  
```cpp  
auto x1 = "hello" " " " world"; // OK  
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix  
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes  
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### <a name="string-literals-with-universal-character-names"></a>Literały ciągu z uniwersalne nazwy znaków  
 Literały macierzystego ciągu (z systemem innym niż — raw) można używać uniwersalne nazwy znaków do reprezentowania dowolny znak, tak długo, jak nazwa zawierająca znaki uniwersalne mogą być kodowane jako co najmniej jeden znak w typu ciąg.  Na przykład nazwa zawierająca znaki uniwersalne reprezentujący rozszerzonego znaków nie może zostać zakodowany w ciągu typu narrow przy użyciu strony kodowej ANSI, ale mogą być kodowane w ciągach wąskie niektóre strony kodowe wielobajtowe, ani ciągi znaków UTF-8 lub ciąg typu wide. W języku C ++ 11, obsługi formatu Unicode zostanie przedłużony char16_t * i char32_t\* ciągu typów:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy znaków](../cpp/character-sets2.md)   
 [Liczbowe, Boolean i literały wskaźnika](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md)