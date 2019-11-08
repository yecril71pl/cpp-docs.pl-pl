---
title: Tabela C++ zgodności języka firmy Microsoft
ms.date: 10/31/2019
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: e3e86acb81120af1b663b56681ff0f8c41036b5a
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754073"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabela C++ zgodności języka firmy Microsoft

Ten temat zawiera podsumowanie standardów języka ISO C++ 03, C++ 11, c++ 14, C++ 17 i C++ 20 zgodne z funkcjami kompilatora i standardowymi funkcjami biblioteki dla kompilatora firmy Microsoft C++ w programie Visual Studio 2019 i jego wcześniejszych wersjach. Każda nazwa funkcji biblioteki kompilatora i standardowa zawiera linki do standardowego C++ dokumentu PROpozycji ISO opisującego funkcję, jeśli jest ona dostępna w czasie publikacji. W kolumnie obsługiwane są wyświetlane wersje programu Visual Studio, w których najpierw pojawiły się obsługa funkcji.

Aby uzyskać szczegółowe informacje dotyczące ulepszeń zgodności i innych zmian w programie Visual Studio 2017 lub Visual Studio 2019, ustaw selektor wersji w lewym górnym rogu tej strony, a następnie zobacz [ C++ ulepszenia zgodności w programie Visual Studio](cpp-conformance-improvements.md) i nowości [dla wizualizacji C++w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Aby uzyskać zgodność ze zmianami we wcześniejszych wersjach, zobacz temat [historia zmian wizualnych C++ ](../porting/visual-cpp-change-history-2003-2015.md) i [wizualizacja C++ nowości 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). W przypadku aktualnych wiadomości C++ od zespołu odwiedź [ C++ Blog zespołu](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Między programem Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 nie ma żadnych zmian binarnych.

## <a name="compiler-features"></a>Funkcje kompilatora

| | |
|----|---|
|__Podstawowe funkcje języka c++ 03/11__|__Obsługiwał__|
|&nbsp;&nbsp;wszystkie inne|VS 2015 <sup> [A](#note_A)</sup>|
|&nbsp;&nbsp;dwufazowe wyszukiwanie nazw|VS 2017 15,7 <sup> [B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 wyrażeń SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15,7|
|&nbsp;&nbsp;[N1653 C99 preprocesora](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Część <sup> [C](#note_C)</sup>|
|__Podstawowe funkcje języka c++ 14__|__Obsługiwał__|
|&nbsp;&nbsp;[N3323 dostosowanie wyrazów dla konwersji kontekstowych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 literałów binarnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 autoi decltype (Auto) typy zwracane](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init-przechwytywania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 rodzajowe wyrażenia lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 \[\[przestarzałe\]\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[dealokacji N3778 o rozmiarze](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[separatory cyfr N3781](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[szablonów zmiennych N3651](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015,2|
|&nbsp;&nbsp;[N3652 rozszerzonego elementu constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017 15,0|
|&nbsp;&nbsp;[N3653 domyślnych inicjatorów elementów członkowskich dla agregacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017 15,0|
|__Podstawowe funkcje języka c++ 17__|__Obsługiwał__|
|&nbsp;&nbsp;[N4086 usuwania trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nowe reguły dla automatycznego z klamrami-init-list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 w szablonie szablonu — parametry](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[atrybuty N4266 dla przestrzeni nazw i modułów wyliczających](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 literały znaków U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup> [14](#note_14)</sup>|
|[definicje zagnieżdżonych przestrzeni nazw](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html) &nbsp;&nbsp;N4230|VS 2015,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 zwięzła static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 15,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 uogólnione, oparte na zakresie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 15,0 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 \[\[fallthrough\]\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 15,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 usunięcie słowa kluczowego Register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 usunięcie operatora + + dla elementu bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 przechwytywania * to przez wartość](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 przy użyciu przestrzeni nazw atrybutów bez powtórzenia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 \_\_has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Direct-list-init stałych wyliczeń z liczb całkowitych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 wyrażenie lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 \[\[nodiscard\]\] Attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 \[\[maybe_unused\]\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 powiązania strukturalne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 constexpr if-Statement](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15,3 <sup> [D](#note_D)</sup>|
|&nbsp;&nbsp;[instrukcji wyboru P0305R1 z inicjatorami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 literały Hexfloat](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268, co pozwala na więcej argumentów szablonu bez typu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|wyrażenia &nbsp;&nbsp;[N4295](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 usuwania specyfikacji dynamicznych-Exception](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 Dodawanie noexcept do systemu typów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 z nadmiernym przydziałem pamięci dynamicznej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 zmiennych wbudowanych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 dopasowuje szablon szablonu do zgodnych argumentów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 usuwania pustego zgięcia jednoargumentowego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 naprawianie kwalifikacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 rozszerzona Inicjalizacja agregacji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|[odliczanie argumentu &nbsp;&nbsp;szablonu P0091R3 dla szablonów klas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br/>&nbsp;&nbsp;[P0512R0nia argumentów szablonu klasy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 deklarujących parametry szablonu bez typu z typem](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 z gwarancją Copy dla koprocedury](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15,6|
|&nbsp;&nbsp;[P0136R1 odword dziedziczenia konstruktorów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std:: pranie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 poprawiaj kolejność szacowania wyrażeń](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br/>&nbsp;&nbsp;[P0400R0 kolejności oceny argumentów funkcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[rozwinięcia pakietu P0195R2 w deklaracjach using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 ignorowanie nierozpoznanych atrybutów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup> [14](#note_14)</sup>|
|__Podstawowe funkcje języka c++ 17 (raporty o defektach)__|__Obsługiwał__|
|&nbsp;&nbsp;[P0702R1 naprawianie argumentów szablonu klasy dla inicjatora listy ctor](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15,7 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0961R1 złagodzeniu wymagań dotyczących reguł odnajdowania powiązań strukturalnych](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|VS 2019 16,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0969R0 Zezwalanie na powiązania strukturalne z dostępnymi elementami członkowskimi](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|VS 2019 16,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 upraszczają niejawne przechwytywanie lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Nie|
|&nbsp;&nbsp;[P0962R2 złagodzeniu wymagań dotyczących, zakres-dla punktu dostosowania pętli Znajdowanie reguły wyszukiwania](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Nie|
|&nbsp;&nbsp;[P0929R2 sprawdzanie typów klas abstrakcyjnych](https://wg21.link/P0929R2)|Nie|
|&nbsp;&nbsp;[P1009R2nia rozmiaru tablicy w nowych wyrażeniach](https://wg21.link/P1009R2)|Nie|
|&nbsp;&nbsp;[P1286R2 CWG DR1778](https://wg21.link/P1286R2)|Nie|
|__Podstawowe funkcje języka c++ 20__|__Obsługiwał__|
|&nbsp;&nbsp;[P0704R1 naprawianie stałych lvalue z kwalifikatorami kwalifikowanymi do elementów członkowskich](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P1041R4 char16_t/char32_t literały ciągu to UTF-16/32](https://wg21.link/P1041R4)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P1330R0 zmiana aktywnego elementu członkowskiego Unii w elemencie constexpr](https://wg21.link/P1330R0)|VS 2017 15,0 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0972R0 noexcept For \<chrono > zero (), min (), Max ()](https://wg21.link/P0972R0)|VS 2017 15,7 <sup> [14](#note_14)</sup>|
|&nbsp;[wyznaczono inicjalizację &nbsp;P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0409R2 umożliwiający przechwytywanie lambda \[=, to\]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0515R3 Spaceship, < = >](https://wg21.link/P0515R3)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0941R2 funkcji — makra testowe](https://wg21.link/P0941R2)|VS 2019 16,0 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P1008R1 zakazania agregacji za pomocą konstruktorów zadeklarowanych przez użytkownika](https://wg21.link/P1008R1)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0846R0 ADL i szablonów funkcji, które nie są widoczne](https://wg21.link/P0846R0)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0641R2 const niezgodność z domyślnym konstruktorem kopiującym](https://wg21.link/P0641R2)|Częściowe|
|&nbsp;&nbsp;[P0306R4 dodawanie \_\_VA_OPT\_\_ do pominięcia przecinka i usuwania przecinków](https://wg21.link/P0306R4)|Nie|
|&nbsp;&nbsp;[P0315R4 zezwalania na wyrażenia lambda w nieoszacowanych kontekstach](https://wg21.link/P0315R4)|Nie|
|&nbsp;&nbsp;[P0428R2 znaną składnią szablonu dla rodzajowych wyrażeń lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Nie|
|&nbsp;&nbsp;[P0479R5 \[\[prawdopodobnie\]\] i \[\[,](https://wg21.link/P0479R5)\]\] atrybutów|Nie|
|&nbsp;&nbsp;[kontrakty P0542R5](https://wg21.link/P0542R5)|Nie|
|&nbsp;&nbsp;[P0614R1 oparte na zakresie dla pętli z inicjatorami](https://wg21.link/P0614R1)|Nie|
|&nbsp;&nbsp;[P0624R2 domyślne konstrukcyjną i można przypisać bezstanowe wyrażenia lambda](https://wg21.link/P0624R2)|Nie|
|&nbsp;&nbsp;[P0634R3 z atrybutem TypeName!](https://wg21.link/P0634R3)|Nie|
|&nbsp;&nbsp;[P0683R1 domyślnych inicjatorów elementów członkowskich dla pól bitowych](https://wg21.link/P0683R1)|Nie|
|&nbsp;&nbsp;[P0692R1 sprawdzanie dostępu dla specjalizacji](https://wg21.link/P0692R1)|Nie|
|&nbsp;&nbsp;[P0722R3 do usunięcia dla klas o zmiennym rozmiarze](https://wg21.link/P0722R3)|Nie|
|&nbsp;&nbsp;[typy klas P0732R2 w parametrach szablonu bez typu](https://wg21.link/P0732R2)|Nie|
|&nbsp;&nbsp;[P0734R0 pojęć](https://wg21.link/P0734R0)|Nie|
|&nbsp;&nbsp;[P0780R2 umożliwia rozwinięcie pakietu w funkcji lambda init-Capture](https://wg21.link/P0780R2)|Nie|
|&nbsp;&nbsp;[P0806R2 zaniechania niejawnego przechwytywania przez \[=\]](https://wg21.link/P0806R2)|Nie|
|&nbsp;&nbsp;[P0840R2 \[\[no_unique_address\]\]](https://wg21.link/P0840R2)|Nie|
|&nbsp;&nbsp;[P0857R0 naprawianie luk w ograniczeniach](https://wg21.link/P0857R0)|Nie|
|&nbsp;&nbsp;[P0892R2 warunkowo Explicit](https://wg21.link/P0892R2)|Nie|
|&nbsp;[procedury współprocedurowe &nbsp;P0912R5](https://wg21.link/P0912R5)|Nie|
|&nbsp;&nbsp;[P0960R3 umożliwiają inicjowanie agregacji ze ujętej w nawiasy listy wartości](https://wg21.link/P0960R3)|Nie|
|&nbsp;&nbsp;[P1002R1 bloki try-catch w funkcjach constexpr](https://wg21.link/P1002R1)|Nie|
|&nbsp;&nbsp;[P1064R0 Zezwalanie na wywołania funkcji wirtualnych w wyrażeniach stałych](https://wg21.link/P1064R0)|Nie|
|&nbsp;[funkcje natychmiastowe &nbsp;P1073R3](https://wg21.link/P1073R3)|Nie|
|&nbsp;&nbsp;[P1084R2 dzisiejszego typu — wymagania są niewystarczające](https://wg21.link/P1084R2)|Nie|
|&nbsp;&nbsp;[P1091R3 rozszerzające powiązania strukturalne, aby były bardziej podobne do deklaracji zmiennych](https://wg21.link/P1091R3)|Nie|
|&nbsp;&nbsp;[P1094R2 zagnieżdżonej wbudowanej przestrzeni nazw](https://wg21.link/P1094R2)|Nie|
|&nbsp;&nbsp;[modułów P1103R3](https://wg21.link/P1103R3)|Nie|
|&nbsp;&nbsp;[P1120R0 ulepszeń spójności < = > i innych operatorów porównania](https://wg21.link/P1120R0)|Nie|
|&nbsp;&nbsp;[P1139R2 problemy dotyczące tekstów związanych z ISO 10646](https://wg21.link/P1139R2)|Nie|
|&nbsp;&nbsp;[P1141R2 jeszcze inne podejście dla deklaracji z ograniczeniami](https://wg21.link/P1141R2)|Nie|
|&nbsp;&nbsp;[P1185R2 \<=\>! = = =](https://wg21.link/P1185R2)|Nie|
|&nbsp;&nbsp;[P1236R1 z liczbami całkowitymi, są uzupełnieniem dwóch](https://wg21.link/P1236R1)|Nie|
|&nbsp;&nbsp;[P1289R1 kontroli dostępu w warunkach kontraktu](https://wg21.link/P1289R1)|Nie|
|&nbsp;&nbsp;[P1323R2 kontraktu warunki końcowe i odliczania typu zwracanego](https://wg21.link/P1323R2)|Nie|
|&nbsp;&nbsp;[P1327R1 umożliwiający dynamic_cast, polimorficzny typeid w wyrażeniach stałych](https://wg21.link/P1327R1)|Nie|
|&nbsp;&nbsp;[P1353R0 brakujące makra testów funkcji](https://wg21.link/P1353R0)|Nie|
|&nbsp;&nbsp;[P1381R1 przechwytywania strukturalnego powiązań](https://wg21.link/P1381R1)|Nie|

## <a name="standard-library-features"></a>Standardowe funkcje biblioteki

| | |
|---|---|
|__Standardowe funkcje biblioteki c++ 20__|__Obsługiwał__|
|&nbsp;&nbsp;[P0809R0 porównując nieuporządkowane kontenery](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0858R0, wymagania iteratora constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0777R1 uniknięcie niepotrzebnego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) uszkodzenia|VS 2017 15,7 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0318r1.pdf)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0457R2 starts_with ()/ends_with () dla basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0458R2 zawiera () dla uporządkowanych i nieuporządkowanych kontenerów asocjacyjnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0458r2.html)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0646R1 list/forward_list Remove ()/remove_if ()/Unique () return size_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0646r1.pdf)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0769R2 shift_left (), shift_right ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0769r2.pdf)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf)|VS 2019 16,1 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8)|Nie|
|&nbsp;&nbsp;[P0020R6ą niepodzielną\<zmiennoprzecinkową >, niepodzielną\<podwójną >, niepodzielną\<long double >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Nie|
|&nbsp;&nbsp;[P0053R7 \<syncstream >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br/>&nbsp;&nbsp;[P0753R2 osyncstream](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Nie|
|&nbsp;&nbsp;[P0122R7 \<zakres >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Nie|
|&nbsp;&nbsp;[P0202R3 constexpr dla algorytmu \<> i Exchange ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Nie|
|&nbsp;&nbsp;[P0339R6 polymorphic_allocator < >](https://wg21.link/P0339R6)|Nie|
|&nbsp;&nbsp;[P0340R3 SFINAE — przyjazny underlying_type](https://wg21.link/P0340R3)|Nie|
|&nbsp;&nbsp;[P0355R7 \<chrono > kalendarze i strefy czasowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Nie|
|&nbsp;&nbsp;[P0356R5 bind_front ()](https://wg21.link/P0356R5)|Nie|
|&nbsp;&nbsp;[P0357R3 obsługę niekompletnych typów w reference_wrapper](https://wg21.link/P0357R3)|Nie|
|&nbsp;&nbsp;[P0415R1 constexpr dla \<złożonych > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Nie|
|&nbsp;&nbsp;[P0439R0 Wyliczenie klasy memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Nie|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Nie|
|&nbsp;&nbsp;[P0475R1 z gwarancją Copy dla koprocedury dla konstrukcji rozkład elementowy](https://wg21.link/P0475R1)|Nie|
|&nbsp;&nbsp;[P0476R2 <bit> bit_cast](https://wg21.link/P0476R2)|Nie|
|&nbsp;&nbsp;[P0482R6 char8_t: typ dla znaków UTF-8 i ciągów](https://wg21.link/P0482R6)|Nie|
|&nbsp;&nbsp;[P0487R1 > > (basic_istream &, wykres *)](https://wg21.link/P0487R1)|Nie|
|&nbsp;&nbsp;[P0528R3 niepodzielne porównanie i wymianę z bitami uzupełniania](https://wg21.link/P0528R3)|Nie|
|&nbsp;&nbsp;[P0556R3 <bit> ispow2 (), ceil2 (), floor2 (), log2p1 ()](https://wg21.link/P0556R3)|Nie|
|&nbsp;&nbsp;[funkcje narzędzia P0591R4 do użycia — konstrukcja alokatora](https://wg21.link/P0591R4)|Nie|
|&nbsp;&nbsp;[P0600R1 \[\[nodiscard\]\] dla STL, część 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Nie|
|&nbsp;&nbsp;[P0608R3 ulepszania konstruktora/przydziału konwersji wariantu](https://wg21.link/P0608R3)|Nie|
|&nbsp;&nbsp;[P0616R0 przy użyciu polecenia Move () w \<liczbowej >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Nie|
|&nbsp;&nbsp;[P0619R4 usunięcie przestarzałych funkcji języka C + +17 w języku c++ 20](https://wg21.link/P0619R4)|Nie|
|&nbsp;&nbsp;[P0653R2 to_address ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Nie|
|&nbsp;&nbsp;[P0655R1<R>()](https://wg21.link/P0655R1)|Nie|
|&nbsp;&nbsp;[P0674R1 make_shared () dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Nie|
|&nbsp;&nbsp;[P0718R2\<shared_ptr\<t > >, niepodzielną\<weak_ptr\<t > >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Nie|
|&nbsp;&nbsp;[P0738R2 istream_iterator](https://wg21.link/P0738R2)|Nie|
|&nbsp;&nbsp;[P0754R2 \<wersja >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Nie|
|&nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1)|Nie|
|&nbsp;&nbsp;[P0767R1 przestarzałe is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Nie|
|&nbsp;&nbsp;[obsługę biblioteki P0768R1 dla operatora porównania Spaceship \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Nie|
|&nbsp;&nbsp;[P0771R1 noexcept for std:: Function — Konstruktor przenoszenia](https://wg21.link/P0771R1)|Nie|
|&nbsp;&nbsp;[P0811R3 środkowe (), Lerp ()](https://wg21.link/P0811R3)|Nie|
|&nbsp;&nbsp;[P0879R0 constexpr dla funkcji wymiany](https://wg21.link/P0879R0)|Nie|
|&nbsp;&nbsp;[P0896R4 \<zakresy\>](https://wg21.link/P0896R4)|Nie|
|&nbsp;&nbsp;[P0898R3 pojęć dotyczących biblioteki standardowej](https://wg21.link/P0898R3)|Nie|
|&nbsp;&nbsp;[obsługi biblioteki P0912R5 dla procedur wspólnych](https://wg21.link/P0912R5)|Nie|
|&nbsp;&nbsp;[P0919R3 wyszukiwanie heterogeniczne dla kontenerów nieuporządkowanych](https://wg21.link/P0919R3)|Nie|
|P0920R2 &nbsp;[wyszukania wstępnie obliczonej wartości skrótu](https://wg21.link/P0920R2) &nbsp;|Nie|
|&nbsp;&nbsp;[P0935R0 zwalczenia niekoniecznie jawnych konstruktorów domyślnych](https://wg21.link/P0935R0)|Nie|
|&nbsp;&nbsp;[P0966R1 String:: Reserve () nie należy zmniejszać](https://wg21.link/P0966R1)|Nie|
|&nbsp;&nbsp;[wykonywania P1001R2:: unseq](https://wg21.link/P1001R2)|Nie|
|&nbsp;&nbsp;[P1006R1 constexpr dla pointer_traits < t * >::p ointer_to ()](https://wg21.link/P1006R1)|Nie|
|&nbsp;&nbsp;[P1007R3 assume_aligned ()](https://wg21.link/P1007R3)|Nie|
|&nbsp;&nbsp;[P1020R1 do tworzenia inteligentnego wskaźnika przy użyciu domyślnej inicjalizacji](https://wg21.link/P1020R1)|Nie|
|&nbsp;&nbsp;[P1023R0 constexpr dla porównywania std:: Array](https://wg21.link/P1023R0)|Nie|
|&nbsp;&nbsp;[P1032R1 różne wyrażenie constexpr](https://wg21.link/P1032R1)|Nie|
|&nbsp;&nbsp;[P1165R1 spójnie propagowanie przydzielania stanów w operatorze basic_string's + ()](https://wg21.link/P1165R1)|Nie|
|&nbsp;&nbsp;[P1209R0 erase_if (), wymazywanie ()](https://wg21.link/P1209R0)|Nie|
|&nbsp;&nbsp;[P1227R2 podpisany std:: sSize (), niepodpisany zakres:: size ()](https://wg21.link/P1227R2)|Nie|
|&nbsp;&nbsp;[P1285R0 poprawę kompletności dla cech typu](https://wg21.link/P1285R0)|Nie|
|&nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1)|Nie|
|__Standardowe funkcje biblioteki c++ 17__|__Obsługiwał__|
|&nbsp;&nbsp;[LWG 2221 — operator danych wyjściowych sformatowanych dla nullptr](https://cplusplus.github.io/LWG/issue2221)|VS 2019 16,1|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 bezpieczne konwersje w unique_ptr\<t [] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 usuwania auto_ptr, random_shuffle () i starych \<funkcjonalnych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup> [REM](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 w sposób niereference_wrappery](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign ()/try_emplace () dla mapy/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 (), puste (), dane ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 precyzyjne ograniczanie przydziału unique_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4387 ulepszania pary i krotki](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (czas nieprzekroczony)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 obsługę niekompletnych typów w wektorze/liście/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4562 Library: algorytm \<> przykład ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017 15,0|
|&nbsp;&nbsp;[N4562 Library: \<wszystkie >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017 15,0|
|&nbsp;&nbsp;[N4562 Library: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 usuwania przypisania polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15,6|
|&nbsp;&nbsp;[N4562 biblioteki podstawowej: \<opcjonalne >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 15,0|
|&nbsp;&nbsp;[N4562 Library: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017 15,0|
|&nbsp;&nbsp;[Biblioteka N4562: \<krotka > Zastosuj ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017 15,0|
|&nbsp;&nbsp;[Biblioteka N4562: Boyer-Moore Search ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 naprawianie typów zwracanych przez wyszukiwarkę](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 usuwania specyfikacji wyjątków dynamicznych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0004R1 usuwania przestarzałych aliasów iostreams](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015,2 <sup> [REM](#note_rem)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br/>&nbsp;&nbsp;[P0358R1 poprawek dla not_fn ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[szablonów zmiennych P0006R0 dla cech typu (is_same_v itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[cech typów logicznego operatora P0013R1 (razem itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|[algorytmy równoległe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) &nbsp;&nbsp;P0024R2<br/>&nbsp;&nbsp;[P0336R1 zmiana nazw zasad wykonywania równoległego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br/>[algorytmy równoległe &nbsp;&nbsp;P0394R4 powinny kończyć () dla wyjątków](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br/>&nbsp;&nbsp;[P0452R1 ujednolicenie \<> algorytmów równoległych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15,7|
|&nbsp;&nbsp;[P0025R1 ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015,3|
|&nbsp;&nbsp;[P0030R1 hypot — (x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15,7|
|&nbsp;&nbsp;[P0031R0 constexpr dla \<tablicy > (ponownie) i \<iterator >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0032R3 jednorodnego interfejsu dla wariantu/dowolnego/opcjonalnego](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0033R1 enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15,5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0040R3 rozszerzanie narzędzi do zarządzania pamięcią](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0063R3 biblioteki standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup> [C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0067R5 podstawowe konwersje ciągów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15,7 <sup> [charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0083R3 łączenie map i zestawów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br/>&nbsp;&nbsp;[P0508R0 wyjaśnienie insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 emplace typ zwracany](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0088R3 \<wariantów >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0092R1 \<chrono > Floor (), ceil — (), Round (), ABS ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0152R1 niepodzielną:: is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size itd.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R0 wariadyczne lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015,2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R2 zmiana nazwy wariadyczne blokady\_Guard na\_blokadę zakresu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0163R0 shared_ptr:: weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0174R2 przestarzałych części biblioteki szczątkowe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015,3|
|&nbsp;&nbsp;[P0209R2 make_from_tuple ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0218R1 \<systemu plików >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br/>&nbsp;&nbsp;[ścieżki względne P0219R1 dla systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br/>&nbsp;&nbsp;[P0317R1 wpisów w katalogu dla systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br/>&nbsp;&nbsp;[P0392R0 obsługę String_view w ścieżkach systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br/>&nbsp;&nbsp;[P0430R2 obsługujący systemy plików innych niż POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br/>&nbsp;&nbsp;[P0492R2 rozpoznawania komentarzy NB dla systemu plików](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15,7 <sup> [E](#note_E)</sup>|
|&nbsp;&nbsp;[P0220R1 — podstawowe informacje o bibliotece 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15,6|
|&nbsp;&nbsp;[funkcji specjalnych matematycznych P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15,7|
|&nbsp;&nbsp;[P0254R2 integrujący String_view i std:: String](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15,3 <sup> [G](#note_G)</sup>|
|&nbsp;&nbsp;[P0272R1 nieconst basic_string::d ATA ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015,3|
|&nbsp;&nbsp;[P0295R0 GCD (), LCM ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std:: Byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15,3 <sup> [17](#note_17),&nbsp;[bajt](#note_byte)</sup>|
|&nbsp;&nbsp;[P0302R1 usuwania obsługi alokatora w funkcji std:: Function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0307R2, aby ponownie zwiększyć wartość opcjonalną](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0393R3, dzięki czemu wariant jest większy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0403R1 UDL dla > \<string_view ("meow" SV itd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<t [] > shared_ptr\<t [N] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br/>&nbsp;&nbsp;[P0497R0 naprawianie Shared_ptr dla tablic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15,5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0418R2 compare_exchange niepodzielnymi wymaganiami memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0426R1 constexpr dla char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15,7|
|&nbsp;&nbsp;[P0433R2 integrujące odliczanie szablonów dla szablonów klas w bibliotece standardowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br/>&nbsp;&nbsp;[P0739R0 ulepszania integracji argumentu szablonu klasy z biblioteką standardową](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15,7|
|&nbsp;&nbsp;[P0435R1 common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br/>&nbsp;&nbsp;[P0548R1 Dostosowywanie typowego typu\_i czasu trwania](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0504R0 odwiedzania in_place_t/in_place_type_t\<t >/in_place_index_t\<I >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0505R0 constexpr dla \<chrono > (ponownie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0510R0 odrzucania wariantów elementów Nothing, tablic, odwołań i niekompletnych typów](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[skrótu zatrucia P0513R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br/>&nbsp;&nbsp;[P0599R1 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 oznaczanie kopiowania Shared_future jako noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 konstruowania Future_error z future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 przestarzałe shared_ptr:: Unique ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0558R1 rozpoznawania niepodzielnych\<t > klasy podstawowej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15,3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0595R2 std:: is_constant_evaluated ()](https://wg21.link/P0595R2)|Nie|
|&nbsp;&nbsp;[P0602R4 propagowanie niezmiennej kopiowania/przenoszenia w elemencie Variant/Optional](https://wg21.link/P0602R4)|VS 2017 15,3<sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0604R0 zmiana jest\_wywoływanie/wynik\_do wywołania\_wyniku, jest\_wywoływać, jest\_nothrow\_wywoływać](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15,3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 zmiennych wbudowanych dla standardowej biblioteki](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 przestarzałe \<codecvt >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0682R1 naprawione podstawowe konwersje ciągów](https://wg21.link/P0682R1)|VS 2015 15,7 <sup> [17](#note_17)</sup>|
|__C++ 14 — funkcje biblioteki standardowej__|__Obsługiwał__|
|&nbsp;&nbsp;[N3462 SFINAE — przyjazny result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015,2|
|&nbsp;&nbsp;[N3302 constexpr dla \<złożonych >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr dla \<chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr dla tablicy \<](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr dla \<initializer_list >, \<spójnej kolekcji](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html) > \<|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant:: operator () ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL For \<chrono >, \<ciąg > (1729ms, "meow" itd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Iteratory do przodu o wartości null](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Heterogeniczne wyszukiwanie asocjacyjne](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (czas)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 Exchange ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 naprawianie funkcji Członkowskich constexpr bez stałej](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670\<t > ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 podwójnego zakresu (), is_permutation (), niezgodność ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[dealokacji N3778 o rozmiarze](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL dla \<złożonych > (3.14 i itp.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr dla \<funkcjonalnej >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 zmiana nazwy shared_mutex (czas) na shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 minimalnych wymagań dotyczących elementów kontenera](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 przezroczystego operatora funktory (mniej\<> itd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[Szablony aliasów N3655 dla \<type_traits > (decay_t itd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|

Grupa papierów wymienionych razem wskazuje, że funkcja została zagłosowana w standardzie, a następnie jeden lub więcej dokumentów w celu ulepszenia lub rozszerzenia tej funkcji zostało również pożądany. Te funkcje są implementowane razem.

### <a name="supported-values"></a>Obsługiwane wartości

__Nie oznacza,__ że jeszcze nie zaimplementowano.<br/>
__Częściowe__ oznacza, że implementacja nie jest kompletna. Aby uzyskać więcej informacji, zobacz sekcję Uwagi.<br/>
__VS 2010__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2010.<br/>
__VS 2013__ wskazuje funkcje, które są obsługiwane w Visual Studio 2013.<br/>
__VS 2015__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2015 RTW.<br/>
__Vs 2015,2__ i __vs 2015,3__ wskazują funkcje, które są odpowiednio obsługiwane w programie Visual Studio 2015 Update 2 i Visual Studio 2015 Update 3.<br/>
__VS 2017 15,0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,0 (RTW).<br/>
__VS 2017 15,3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,3.<br/>
__VS 2017 15,5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,5.<br/>
__VS 2017 15,7__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,7.<br/>
__VS 2019 16,0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,0 (RTW).<br/>
__VS 2019 16,1__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,1.

### <a name="notes"></a>Uwagi

<a name="note_A"></a>__A__ w [/std: tryb c++ 14](../build/reference/std-specify-language-standard-version.md) , dynamiczne specyfikacje wyjątków pozostają niezaimplementowane, a `throw()` jest nadal traktowany jako synonim dla `__declspec(nothrow)`. W języku C++ 17 dynamiczne specyfikacje wyjątków zostały przed chwilą usunięte przez P0003R5, pozostawiając jedną vestigeę: `throw()` jest przestarzała i wymagane do zachowania synonimu `noexcept`. W trybie [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) , MSVC teraz jest zgodna z normą, dając `throw()` takie samo zachowanie jak `noexcept`, tj. wymuszanie przez zakończenie.

Opcja kompilatora [/Zc: noexceptTypes](../build/reference/zc-noexcepttypes.md) żąda starego zachowania `__declspec(nothrow)`. Prawdopodobnie `throw()` zostanie usunięta w języku C++ 20. Aby ułatwić Migrowanie kodu w odpowiedzi na te zmiany w standardzie i naszej implementacji, nowe ostrzeżenia kompilatora dotyczące problemów ze specyfikacją wyjątków zostały dodane w obszarze [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) i [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ obsługiwane w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) w programie Visual Studio 2017 w wersji 15,7. Aby uzyskać więcej informacji [, zobacz dwuetapowa obsługa wyszukiwania nazw jest MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) .

<a name="note_C"></a>__C__ obsługa reguł preprocesora C99 przez kompilator jest niekompletna w programie Visual Studio 2017. Przeniesiemy preprocesor i zaczniemy przedostawać te zmiany w programie Visual Studio 2017 w wersji 15,8 z przełącznikiem kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) .

<a name="note_D"></a>__D__ obsługiwane w obszarze [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) z suppressible ostrzeżenie, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>__E__ jest to zupełnie nowa implementacja, niezgodna z poprzednią wersją `std::experimental`, wymagającą pomocy technicznej link symboliczny, poprawek błędów i zmian w zachowaniu standardowym. Obecnie w tym \<> systemu plików udostępnia nowy `std::filesystem` i poprzednią `std::experimental::filesystem`, a także \<eksperymentalny/system plików > zapewnia tylko starą implementację eksperymentalną. Implementacja eksperymentalna zostanie usunięta w następnej ABIej wersji biblioteki.

<a name="note_G"></a>__G__ obsługiwane przez wewnętrznie kompilator.

<a name="note_14"></a>__14__ te funkcje języka c++ 17/20 są zawsze włączone, nawet w przypadku określenia [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) (wartość domyślna). Jest to spowodowane tym, że funkcja została zaimplementowana przed wprowadzeniem opcji **/STD** lub że implementacja warunkowa była niecelowo złożona.

<a name="note_17"></a>__17__ te funkcje są włączane przez opcję kompilatora [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + +](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a>__20__ te funkcje są włączane przez [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) opcja kompilatora. Po zakończeniu implementacji języka C++ 20 zostanie dodana nowa opcja kompilatora **/std: c++ 20** , w której te funkcje będą również dostępne.

<a name="note_byte"></a>`std::byte` __bajty__ jest włączane przez [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md)), ale ponieważ w niektórych przypadkach może powodować konflikt z nagłówkami Windows SDK, ma ono szczegółowe makro z szczegółowymi krokami. Można ją wyłączyć, definiując `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ Uniwersalna CRT wdrożyła części standardowej biblioteki C11, które są wymagane przez C++ 17, z wyjątkiem `strftime()` C99ych alternatywnych specyfikatorów konwersji, C11 `fopen()` trybu wyłącznego i C11 `aligned_alloc()`. Ten ostatni jest mało prawdopodobne, ponieważ C11 określony `aligned_alloc()` w sposób, który jest niezgodny z implementacją firmy Microsoft `free()`, to znaczy, że `free()` musi być w stanie obsłużyć wysoce wyrównane alokacje.

<a name="note_rem"></a>__REM__ Funkcje usunięte w przypadku wybrania opcji kompilatora [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + +](../build/reference/std-specify-language-standard-version.md)). Te funkcje można włączyć w celu ułatwienia przejścia do nowszych trybów języka przy użyciu następujących makr: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`i `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` i `to_chars()` są dostępne dla liczb całkowitych. Oś czasu dla `from_chars()` zmiennoprzecinkowych i zmiennoprzecinkowych `to_chars()` jest następująca:
- VS 2017 15,7: liczba całkowita `from_chars()` i `to_chars()`.
- VS 2017 15,8: `from_chars()`zmiennoprzecinkowe.
- VS 2017 15,9: przeciążania zmiennoprzecinkowe `to_chars()` dla najkrótszej liczby dziesiętnej.
- VS 2019 16,0: przeciążania zmiennoprzecinkowe `to_chars()` dla najkrótszej wartości szesnastkowej i dokładności.
- VS 2019 16,2: przeciążania zmiennoprzecinkowe `to_chars()` dla stałych i precyzyjnej precyzji.
- Jeszcze nie zaimplementowano: zmiennoprzecinkowe `to_chars()` Przeciążenie dla precyzji ogólnej. 

<a name ="note_parallel"></a>__równolegle__ Biblioteka algorytmów równoległych języka c++ 17 została ukończona. Nie oznacza to, że każdy algorytm jest równoległy w każdym przypadku; Najważniejsze algorytmy zostały przekształcone i sygnatury zasad wykonywania są udostępniane, nawet jeśli algorytmy nie są równoległe. Główny nagłówek wewnętrzny yvals_core. h, zawiera następujące "informacje o algorytmach równoległych": C++ umożliwia implementację implementującą algorytmy równoległe jako wywołania do algorytmów szeregowych.  Ta implementacja parallelizes kilka typowych wywołań algorytmu, ale nie wszystkich.

Następujące algorytmy są równoległe:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Następujące elementy nie są obecnie równoległe:

- Brak pozornej poprawy wydajności równoległości na sprzęcie docelowym; wszystkie algorytmy, które tylko kopiują lub Permute — elementy bez rozgałęzień, są zwykle ograniczone przepustowością pamięci:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Istnieje pomylenie wymagań równoległości użytkowników; na ogół w powyższej kategorii nadal:
  - `generate`, `generate_n`
- Skuteczna równoległość prawdopodobnie jest niewykonalna:
  - `partial_sort`, `partial_sort_copy`
- Jeszcze nie oceniono; równoległość może zostać zaimplementowana w przyszłej wersji i prawdopodobnie jest korzystna:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md)<br/>
[Co nowego w wizualizacji C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historia C++ zmian wizualnych 2003 do 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Visual C++ — co nowego od roku 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[C++Blog zespołu](https://devblogs.microsoft.com/cppblog/)
