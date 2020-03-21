---
title: Tabela C++ zgodności języka firmy Microsoft
description: Tabela aktualizacji zgodności C++ firmy Microsoft według wersji programu Visual Studio.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 8a5ffb5b3ab4bc80cb200b41752b19d1c958ece6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079371"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabela C++ zgodności języka firmy Microsoft

Zgodność ze standardami dla kompilatora Microsoft C++ w programie Visual Studio (MSVC) jest w toku. Poniżej znajduje się podsumowanie naszych standardowych C++ języków i bibliotek ISO zgodne z wersją programu Visual Studio. Każda nazwa funkcji biblioteki kompilatora i standardowa zawiera linki do standardowego C++ dokumentu PROpozycji ISO opisującego funkcję, jeśli jest ona dostępna w czasie publikacji. W kolumnie **obsługiwane** są wyświetlane wersje programu Visual Studio, w których najpierw pojawiły się obsługa funkcji.

Aby uzyskać szczegółowe informacje na temat ulepszeń zgodności programu Visual Studio 2017 lub Visual Studio 2019, zobacz [ C++ ulepszenia zgodności w programie Visual Studio](cpp-conformance-improvements.md). Aby zapoznać się z listą innych zmian, zobacz [co nowego C++ ](what-s-new-for-visual-cpp-in-visual-studio.md)w programie Visual Studio. Aby uzyskać zgodność ze zmianami we wcześniejszych wersjach, zobacz temat [historia zmian wizualnych C++ ](../porting/visual-cpp-change-history-2003-2015.md) i [wizualizacja C++ nowości 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). W przypadku aktualnych wiadomości C++ od zespołu odwiedź [ C++ Blog zespołu](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Między programem Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 nie ma żadnych zmian binarnych. Aby uzyskać więcej informacji, zobacz [ C++ zgodność binarna między programem Visual Studio 2015, 2017 i 2019](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>Funkcje kompilatora

|  |  |
|--|--|
| __Podstawowe funkcje języka c++ 03/11__ | __Obsługiwane__ |
| &nbsp;&nbsp;wszystkie inne | VS 2015 <sup> [A](#note_A)</sup> |
| &nbsp;&nbsp;dwufazowe wyszukiwanie nazw | VS 2017 15,7 <sup> [B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 wyrażeń SFINAE](https://wg21.link/N2634) | VS 2017 15.7 |
| &nbsp;&nbsp;[N1653 C99 preprocesora](https://wg21.link/N1653) | Część <sup> [C](#note_C)</sup> |
| __Podstawowe funkcje języka c++ 14__ | __Obsługiwane__ |
| &nbsp;&nbsp;[N3323 dostosowanie wyrazów dla konwersji kontekstowych](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 literałów binarnych](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 autoi decltype (Auto) typy zwracane](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-przechwytywania](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 rodzajowe wyrażenia lambda](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[N3760 \[\[przestarzałe\]\]](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[dealokacji N3778 o rozmiarze](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[separatory cyfr N3781](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[szablonów zmiennych N3651](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 rozszerzonego elementu constexpr](https://wg21.link/n3652) | VS 2017 15.0 |
| &nbsp;&nbsp;[N3653 domyślnych inicjatorów elementów członkowskich dla agregacji](https://wg21.link/n3653) | VS 2017 15.0 |
| __Podstawowe funkcje języka c++ 17__ | __Obsługiwane__ |
| &nbsp;&nbsp;[N4086 usuwania trigraphs](https://wg21.link/n4086) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 nowe reguły dla automatycznego z klamrami-init-list](https://wg21.link/n3922) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 w szablonie szablonu — parametry](https://wg21.link/n4051) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[atrybuty N4266 dla przestrzeni nazw i modułów wyliczających](https://wg21.link/n4266) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 literały znaków U8](https://wg21.link/n4267) | VS 2015 <sup> [14](#note_14)</sup> |
| [definicje zagnieżdżonych przestrzeni nazw](https://wg21.link/n4230) &nbsp;&nbsp;N4230 | VS 2015,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 zwięzła static_assert](https://wg21.link/n3928) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 uogólnione, oparte na zakresie](https://wg21.link/p0184r0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0188R1 \[\[fallthrough\]\]](https://wg21.link/p0188r1) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 usunięcie słowa kluczowego Register](https://wg21.link/p0001r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 usunięcie operatora + + dla elementu bool](https://wg21.link/p0002r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 przechwytywania * to przez wartość](https://wg21.link/p0018r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 przy użyciu przestrzeni nazw atrybutów bez powtórzenia](https://wg21.link/p0028r4) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_\_has_include](https://wg21.link/p0061r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Direct-list-init stałych wyliczeń z liczb całkowitych](https://wg21.link/p0138r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 wyrażenie lambda](https://wg21.link/p0170r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[\[nodiscard\]\] Attribute](https://wg21.link/p0189r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0212R1 \[\[maybe_unused](https://wg21.link/p0212r1)\]\] | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 powiązania strukturalne](https://wg21.link/p0217r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if-Statement](https://wg21.link/p0292r2) | VS 2017 15,3 <sup> [D](#note_D)</sup> |
| &nbsp;&nbsp;[instrukcji wyboru P0305R1 z inicjatorami](https://wg21.link/p0305r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 literały Hexfloat](https://wg21.link/p0245r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268, co pozwala na więcej argumentów szablonu bez typu](https://wg21.link/n4268) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| wyrażenia &nbsp;&nbsp;[N4295](https://wg21.link/n4295) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 usuwania specyfikacji dynamicznych-Exception](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 Dodawanie noexcept do systemu typów](https://wg21.link/p0012r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 z nadmiernym przydziałem pamięci dynamicznej](https://wg21.link/p0035r4) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 zmiennych wbudowanych](https://wg21.link/p0386r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 dopasowuje szablon szablonu do zgodnych argumentów](https://wg21.link/p0522r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 usuwania pustego zgięcia jednoargumentowego](https://wg21.link/p0036r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 naprawianie kwalifikacji](https://wg21.link/n4261) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 rozszerzona Inicjalizacja agregacji](https://wg21.link/p0017r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| [odliczanie argumentu &nbsp;&nbsp;szablonu P0091R3 dla szablonów klas](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0nia argumentów szablonu klasy](https://wg21.link/p0512r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 deklarujących parametry szablonu bez typu z typem](https://wg21.link/p0127r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 z gwarancją Copy dla koprocedury](https://wg21.link/p0135r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0136R1 odword dziedziczenia konstruktorów](https://wg21.link/p0136r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std:: pranie](https://wg21.link/p0137r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 poprawiaj kolejność szacowania wyrażeń](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 kolejności oceny argumentów funkcji](https://wg21.link/p0400r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[rozwinięcia pakietu P0195R2 w deklaracjach using](https://wg21.link/p0195r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 ignorowanie nierozpoznanych atrybutów](https://wg21.link/p0283r2) | VS 2015 <sup> [14](#note_14)</sup> |
| __Podstawowe funkcje języka c++ 17 (raporty o defektach)__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0702R1 naprawianie argumentów szablonu klasy dla inicjatora listy ctor](https://wg21.link/p0702r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 złagodzeniu wymagań dotyczących reguł odnajdowania powiązań strukturalnych](https://wg21.link/p0961r1) | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 Zezwalanie na powiązania strukturalne z dostępnymi elementami członkowskimi](https://wg21.link/p0969r0) | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 upraszczają niejawne przechwytywanie lambda](https://wg21.link/p0588r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[\[nodiscard\]\] dla konstruktorów](https://wg21.link/p1771r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 scalone sformułowanie dla P0527R1 i P1155R3, bardziej niejawne ruchy](https://wg21.link/p1825r0) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 sprawdzanie typów klas abstrakcyjnych](https://wg21.link/P0929R2) | Nie |
| &nbsp;&nbsp;[P0962R2 złagodzeniu wymagań dotyczących, zakres-dla punktu dostosowania pętli Znajdowanie reguły wyszukiwania](https://wg21.link/p0962r1) | Nie |
| &nbsp;&nbsp;[P0859R0 CWG 1581: Kiedy są zdefiniowane funkcje składowe constexpr](https://wg21.link/p0859r0) | Nie |
| &nbsp;&nbsp;[P1009R2nia rozmiaru tablicy w nowych wyrażeniach](https://wg21.link/P1009R2) | Nie |
| &nbsp;&nbsp;[P1286R2 CWG DR1778](https://wg21.link/P1286R2) | Nie |
| __Podstawowe funkcje języka c++ 20__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0704R1 naprawianie stałych lvalue z kwalifikatorami kwalifikowanymi do elementów członkowskich](https://wg21.link/p0704r1) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 char16_t/char32_t literały ciągu to UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 zmiana aktywnego elementu członkowskiego Unii w elemencie constexpr](https://wg21.link/P1330R0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 noexcept For \<chrono > zero (), min (), Max ()](https://wg21.link/P0972R0) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Spaceship, < = >](https://wg21.link/P0515R3) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 funkcji — makra testowe](https://wg21.link/P0941R2) | VS 2019 16,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 zakazania agregacji za pomocą konstruktorów zadeklarowanych przez użytkownika](https://wg21.link/P1008R1) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;[wyznaczono inicjalizację &nbsp;P0329R4](https://wg21.link/p0329r4) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 ADL i szablonów funkcji, które nie są widoczne](https://wg21.link/P0846R0) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 umożliwiający przechwytywanie lambda \[=, to\]](https://wg21.link/p0409r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 znaną składnią szablonu dla rodzajowych wyrażeń lambda](https://wg21.link/p0428r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 domyślne konstrukcyjną i można przypisać bezstanowe wyrażenia lambda](https://wg21.link/P0624R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 umożliwia rozwinięcie pakietu w funkcji lambda init-Capture](https://wg21.link/P0780R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 zaniechania niejawnego przechwytywania przez \[=\]](https://wg21.link/P0806R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 ulepszeń spójności < = > i innych operatorów porównania](https://wg21.link/P1120R0) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \<=\>! = = =](https://wg21.link/P1185R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 pojęć](https://wg21.link/P0734R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 naprawianie luk w ograniczeniach](https://wg21.link/P0857R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 dzisiejszego typu — wymagania są niewystarczające](https://wg21.link/P1084R2) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 warunkowo Explicit](https://wg21.link/P0892R2) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 rozszerzające powiązania strukturalne, aby były bardziej podobne do deklaracji zmiennych](https://wg21.link/P1091R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 przy użyciu wyliczenia](https://wg21.link/P1099R5) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3, gdy rzeczywiście używasz \<=>](https://wg21.link/P1186R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 Spaceship wymaga dostrajania](https://wg21.link/P1630R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 dodawanie \_\_VA_OPT\_\_ do pominięcia przecinka i usuwania przecinków](https://wg21.link/P0306R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 oparte na zakresie dla pętli z inicjatorami](https://wg21.link/P0614R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 domyślnych inicjatorów elementów członkowskich dla pól bitowych](https://wg21.link/P0683R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 bloki try-catch w funkcjach constexpr](https://wg21.link/P1002R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 przestarzałe użycie operatora przecinka w wyrażeniach indeksu dolnego](https://wg21.link/P1161R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[\[nodiscard ("Message")\]\]](https://wg21.link/P1301R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 rozpoznawanie importowanych jednostek nagłówka wymaga pełnego przetwarzania wstępnego](https://wg21.link/P1703R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Zezwalaj na domyślne porównania według wartości](https://wg21.link/P1946R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 const niezgodność z domyślnym konstruktorem kopiującym](https://wg21.link/P0641R2) | Częściowo |
| &nbsp;[procedury współprocedurowe &nbsp;P0912R5](https://wg21.link/P0912R5) | Częściowo |
| &nbsp;&nbsp;[modułów P1103R3](https://wg21.link/P1103R3) | Częściowo |
| &nbsp;&nbsp;[P0315R4 zezwalania na wyrażenia lambda w nieoszacowanych kontekstach](https://wg21.link/P0315R4) | Nie |
| &nbsp;&nbsp;[P0388R4 zezwolenia na konwersje na tablice nieznanego powiązania](https://wg21.link/P0388R4) | Nie |
| &nbsp;&nbsp;[P0479R5 \[\[prawdopodobnie\]\] i \[\[,](https://wg21.link/P0479R5)\]\] atrybutów | Nie |
| &nbsp;&nbsp;[P0634R3 z atrybutem TypeName!](https://wg21.link/P0634R3) | Nie |
| &nbsp;&nbsp;[P0692R1 sprawdzanie dostępu dla specjalizacji](https://wg21.link/P0692R1) | Nie |
| &nbsp;&nbsp;[P0722R3 do usunięcia dla klas o zmiennym rozmiarze](https://wg21.link/P0722R3) | Nie |
| &nbsp;&nbsp;[typy klas P0732R2 w parametrach szablonu bez typu](https://wg21.link/P0732R2) | Nie |
| &nbsp;&nbsp;[P0735R1 interakcji memory_order_consume z sekwencjami wersji](https://wg21.link/P0735R1) | Nie |
| &nbsp;&nbsp;[P0784R7 więcej kontenerów constexpr](https://wg21.link/P0784R7) | Nie |
| &nbsp;&nbsp;[P0840R2 \[\[no_unique_address](https://wg21.link/P0840R2)\]\] | Nie |
| &nbsp;&nbsp;[P0848R3 warunkowo specjalne funkcje składowe](https://wg21.link/P0848R3) | Nie |
| &nbsp;&nbsp;[P0960R3 umożliwiają inicjowanie agregacji ze ujętej w nawiasy listy wartości](https://wg21.link/P0960R3) | Nie |
| &nbsp;&nbsp;[P1064R0 Zezwalanie na wywołania funkcji wirtualnych w wyrażeniach stałych](https://wg21.link/P1064R0) | Nie |
| &nbsp;[funkcje natychmiastowe &nbsp;P1073R3](https://wg21.link/P1073R3) | Nie |
| &nbsp;&nbsp;[P1094R2 zagnieżdżonej wbudowanej przestrzeni nazw](https://wg21.link/P1094R2) | Nie |
| &nbsp;&nbsp;[P1139R2 problemy dotyczące tekstów związanych z ISO 10646](https://wg21.link/P1139R2) | Nie |
| &nbsp;&nbsp;[P1141R2 jeszcze inne podejście dla deklaracji z ograniczeniami](https://wg21.link/P1141R2) | Nie |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Nie |
| &nbsp;&nbsp;[P1152R4 przestarzałe](https://wg21.link/P1152R4) | Nie |
| &nbsp;&nbsp;[P1236R1 z liczbami całkowitymi, są uzupełnieniem dwóch](https://wg21.link/P1236R1) | Nie |
| &nbsp;&nbsp;[P1327R1 umożliwiający dynamic_cast, polimorficzny typeid w wyrażeniach stałych](https://wg21.link/P1327R1) | Nie |
| &nbsp;&nbsp;[P1331R2 Zezwalanie na inicjowanie prostej domyślnej w kontekstach constexpr](https://wg21.link/P1331R2) | Nie |
| &nbsp;&nbsp;[P1353R0 brakujące makra testów funkcji](https://wg21.link/P1353R0) | Nie |
| &nbsp;&nbsp;[P1381R1 przechwytywania strukturalnego powiązań](https://wg21.link/P1381R1) | Nie |
| &nbsp;&nbsp;[P1452R2 na niejednorodnej semantyki dla wymagań typu Return](https://wg21.link/P1452R2) | Nie |
| &nbsp;&nbsp;[P1616R1 przy użyciu nieograniczonego TTPs z ograniczonymi szablonami](https://wg21.link/P1616R1) | Nie |
| &nbsp;&nbsp;[P1668R1 Zezwalanie na nieoszacowany zestaw wbudowany w funkcjach constexpr](https://wg21.link/P1668R1) | Nie |
| &nbsp;&nbsp;[P1766R1 łagodzenie modułów pomocniczych maladies](https://wg21.link/P1766R1) | Nie |
| &nbsp;&nbsp;[P1811R0 ograniczenia definicji złagodzeniu wymagań dotyczących w celu zapewnienia niezawodnego eksportu](https://wg21.link/P1811R0) | Nie |
| &nbsp;&nbsp;[P1814R0 CTAD dla szablonów aliasów](https://wg21.link/P1814R0) | Nie |
| &nbsp;&nbsp;[P1816R0 CTAD dla agregacji](https://wg21.link/P1816R0) | Nie |
| &nbsp;&nbsp;[P1874R1 dynamiczną kolejność inicjacji zmiennych nielokalnych w modułach](https://wg21.link/P1874R1) | Nie |
| &nbsp;&nbsp;[P1907R1 niespójności przy użyciu parametrów szablonu, które nie są typu](https://wg21.link/P1907R1) | Nie |
| &nbsp;&nbsp;[P1971R0 podstawowe zmiany w komentarzach do NB na spotkaniu 2019 (Belfast)](https://wg21.link/P1971R0) | Nie |
| &nbsp;&nbsp;[P1972R0 US105 Sprawdź, czy istnieją ograniczenia dotyczące nieszablonów podczas tworzenia wskaźnika do funkcji](https://wg21.link/P1972R0) | Nie |
| &nbsp;&nbsp;[P1975R0 ustalanie wyrazów inicjalizacji agregacji agregowanej](https://wg21.link/P1975R0) | Nie |
| &nbsp;&nbsp;[P1979R0 rozwiązanie do US086](https://wg21.link/P1979R0) | Nie |
| &nbsp;&nbsp;[P1980R0 CA096: Deklaracja dopasowania dla niezależnych klauzul WHERE](https://wg21.link/P1980R0) | Nie |

## <a name="standard-library-features"></a>Standardowe funkcje biblioteki

|  |  |
|--|--|
| __Standardowe funkcje biblioteki c++ 20__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0809R0 porównując nieuporządkowane kontenery](https://wg21.link/p0809r0) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0, wymagania iteratora constexpr](https://wg21.link/p0858r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 uniknięcie niepotrzebnego](https://wg21.link/p0777r1) uszkodzenia | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1, tworząc create_directory () intuicyjny](https://wg21.link/P1164R1) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with ()/ends_with () dla basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 zawiera () dla uporządkowanych i nieuporządkowanych kontenerów asocjacyjnych](https://wg21.link/p0458r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 listy/forward_list Remove ()/remove_if ()/Unique () Return size_type](https://wg21.link/p0646r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left (), shift_right ()](https://wg21.link/p0769r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6ą niepodzielną\<zmiennoprzecinkową >, niepodzielną\<podwójną >, niepodzielną\<long double >](https://wg21.link/p0020r6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: typ dla znaków UTF-8 i ciągów](https://wg21.link/P0482R6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[\[nodiscard\]\] dla STL, część 1](https://wg21.link/p0600r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address ()](https://wg21.link/p0653r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<wersja >](https://wg21.link/p0754r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 noexcept for std:: Function — Konstruktor przenoszenia](https://wg21.link/P0771R1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 > > (basic_istream &, wykres *)](https://wg21.link/P0487R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 przy użyciu polecenia Move () w \<liczbowej >](https://wg21.link/p0616r0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0898R3 pojęć dotyczących biblioteki standardowej](https://wg21.link/P0898R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 wyszukiwanie heterogeniczne dla kontenerów nieuporządkowanych](https://wg21.link/P0919R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 pojęć związanych z zmianami w standard_case](https://wg21.link/P1754R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array z usługi LFTS z aktualizacjami](https://wg21.link/P0325R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 SFINAE — przyjazny underlying_type](https://wg21.link/P0340R3) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front ()](https://wg21.link/P0356R5) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 Wyliczenie klasy memory_order](https://wg21.link/p0439r0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bitowy > rotacja i funkcje zliczania](https://wg21.link/P0553R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit > ispow2 (), ceil2 (), floor2 (), log2p1 ()](https://wg21.link/P0556R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated ()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<liczb > obliczeń matematycznych](https://wg21.link/P0631R8) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 Istream_iterator Cleanup](https://wg21.link/P0738R2) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 przestarzałe is_pod](https://wg21.link/P0767R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 String:: Reserve () nie należy zmniejszać](https://wg21.link/P0966R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if (), wymazywanie ()](https://wg21.link/P1209R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 podpisany std:: sSize (), niepodpisany zakres:: size ()](https://wg21.link/P1227R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Narrow ceil2 ()](https://wg21.link/P1355R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 przenoszeniu endian do \<bitowego >](https://wg21.link/P1612R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front () nie powinien rozwinięcia reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1, aby udoskonalać wyszukiwanie heterogeniczne dla kontenerów nieuporządkowanych](https://wg21.link/P1690R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 brakującej funkcji — makra testów 2017-2019](https://wg21.link/P1902R1) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | Nie |
| &nbsp;&nbsp;[P0053R7 \<syncstream >](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2 osyncstream](https://wg21.link/p0753r2) | Nie |
| &nbsp;&nbsp;[P0122R7 \<zakres >](https://wg21.link/p0122r7) | Nie |
| &nbsp;&nbsp;[P0202R3 constexpr dla algorytmu \<> i Exchange ()](https://wg21.link/p0202r3) | Nie |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator < >](https://wg21.link/P0339R6) | Nie |
| &nbsp;&nbsp;[P0355R7 \<chrono > kalendarze i strefy czasowe](https://wg21.link/p0355r7) | Nie |
| &nbsp;&nbsp;[P0357R3 obsługujące niekompletne typy w reference_wrapper](https://wg21.link/P0357R3) | Nie |
| &nbsp;&nbsp;[P0415R1 constexpr dla \<złożonych > (ponownie)](https://wg21.link/p0415r1) | Nie |
| &nbsp;&nbsp;[P0475R1 z gwarancją Copy dla koprocedury dla konstrukcji rozkład elementowy](https://wg21.link/P0475R1) | Nie |
| &nbsp;&nbsp;[P0476R2 \<bitowy > bit_cast](https://wg21.link/P0476R2) | Nie |
| &nbsp;&nbsp;[P0528R3 niepodzielne porównanie i wymianę z bitami uzupełniania](https://wg21.link/P0528R3) | Nie |
| &nbsp;&nbsp;[funkcje narzędzia P0591R4 do użycia — konstrukcja alokatora](https://wg21.link/P0591R4) | Nie |
| &nbsp;&nbsp;[P0608R3 ulepszania konstruktora/przydziału konwersji wariantu](https://wg21.link/P0608R3) | Nie |
| &nbsp;&nbsp;[P0619R4 usunięcie przestarzałych funkcji języka C + +17 w języku c++ 20](https://wg21.link/P0619R4) | Nie |
| &nbsp;&nbsp;[P0653R2 to_address ()](https://wg21.link/p0653r2) | Nie |
| &nbsp;&nbsp;[P0655R1 odwiedź stronę\<R > ()](https://wg21.link/P0655R1) | Nie |
| &nbsp;&nbsp;[P0674R1 make_shared () dla tablic](https://wg21.link/p0674r1) | Nie |
| &nbsp;&nbsp;[P0718R2 niepodzielną\<shared_ptr\<t > >, niepodzielną](https://wg21.link/p0718r2)\<Weak_ptr\<t > > | Nie |
| &nbsp;&nbsp;[obsługę biblioteki P0768R1 dla operatora porównania Spaceship \<=>](https://wg21.link/p0768r1) | Nie |
| &nbsp;&nbsp;[P0811R3 środkowe (), Lerp ()](https://wg21.link/P0811R3) | Nie |
| &nbsp;&nbsp;[P0879R0 constexpr dla funkcji wymiany](https://wg21.link/P0879R0) | Nie |
| &nbsp;&nbsp;[P0896R4 \<zakresy\>](https://wg21.link/P0896R4) | Nie |
| &nbsp;&nbsp;[obsługi biblioteki P0912R5 dla procedur wspólnych](https://wg21.link/P0912R5) | Nie |
| P0920R2 &nbsp;[wyszukania wstępnie obliczonej wartości skrótu](https://wg21.link/P0920R2) &nbsp; | Nie |
| &nbsp;&nbsp;[P0935R0 zwalczenia niekoniecznie jawnych konstruktorów domyślnych](https://wg21.link/P0935R0) | Nie |
| &nbsp;&nbsp;[wykonywania P1001R2:: unseq](https://wg21.link/P1001R2) | Nie |
| &nbsp;&nbsp;[P1006R1 constexpr dla pointer_traits < t * >::p ointer_to ()](https://wg21.link/P1006R1) | Nie |
| &nbsp;&nbsp;[P1007R3 assume_aligned ()](https://wg21.link/P1007R3) | Nie |
| &nbsp;&nbsp;[P1020R1 do tworzenia inteligentnego wskaźnika przy użyciu domyślnej inicjalizacji](https://wg21.link/P1020R1) | Nie |
| &nbsp;&nbsp;[P1023R0 constexpr dla porównywania std:: Array](https://wg21.link/P1023R0) | Nie |
| &nbsp;&nbsp;[P1032R1 różne wyrażenie constexpr](https://wg21.link/P1032R1) | Nie |
| &nbsp;&nbsp;[P1165R1 spójnie rozpowszechniać przydzielenie stanowe w operatorze basic_string + ()](https://wg21.link/P1165R1) | Nie |
| &nbsp;&nbsp;[P1285R0 poprawę kompletności dla cech typu](https://wg21.link/P1285R0) | Nie |
| __Standardowe funkcje biblioteki c++ 17__ | __Obsługiwane__ |
| &nbsp;&nbsp;[LWG 2221 — operator danych wyjściowych sformatowanych dla nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 bezpieczne konwersje w unique_ptr\<t [] >](https://wg21.link/n4089) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 ()](https://wg21.link/n4169) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 usuwania auto_ptr, random_shuffle () i starych \<funkcjonalnych](https://wg21.link/n4190) > | VS 2015 <sup> [REM](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 noexcept](https://wg21.link/n4258) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions ()](https://wg21.link/n4259) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 do kopiowania reference_wrapper](https://wg21.link/n4277) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign ()/try_emplace () dla mapy/unordered_map](https://wg21.link/n4279) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 (), puste (), dane ()](https://wg21.link/n4280) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 precyzyjne ograniczenie Przypisywania unique_ptr](https://wg21.link/n4366) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 ulepszania pary i krotki](https://wg21.link/n4387) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (nieprzekroczony czas)](https://wg21.link/n4508) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 obsługę niekompletnych typów w wektorze/liście/forward_list](https://wg21.link/n4510) | VS 2013 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 Library: algorytm \<> przykład ()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Library: \<wszystkie >](https://wg21.link/n4562#any) | VS 2017 15.0 |
| &nbsp;&nbsp;[Biblioteka N4562: \<memory_resource >](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 usuwania przypisania polymorphic_allocator](https://wg21.link/p0337r0) | VS 2017 15,6 |
| &nbsp;&nbsp;[N4562 biblioteki podstawowej: \<opcjonalne >](https://wg21.link/n4562#optional) | VS 2017 15.0 |
| &nbsp;&nbsp;[Biblioteka N4562: \<string_view >](https://wg21.link/n4562#string.view) | VS 2017 15.0 |
| &nbsp;&nbsp;[Biblioteka N4562: \<krotka > Zastosuj ()](https://wg21.link/n4562#tuple) | VS 2017 15.0 |
| &nbsp;&nbsp;[Biblioteka N4562: Boyer-Moore Search ()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 naprawianie typów zwracanych przez wyszukiwarkę](https://wg21.link/p0253r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 usuwania specyfikacji wyjątków dynamicznych](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 usuwania przestarzałych aliasów iostreams](https://wg21.link/p0004r1) | VS 2015,2 <sup> [REM](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn ()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 poprawek dla not_fn ()](https://wg21.link/p0358r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[szablonów zmiennych P0006R0 dla cech typu (is_same_v itd.)](https://wg21.link/p0006r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const ()](https://wg21.link/p0007r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[cech typów logicznego operatora P0013R1 (razem itp.)](https://wg21.link/p0013r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| [algorytmy równoległe](https://wg21.link/p0024r2) &nbsp;&nbsp;P0024R2<br/>&nbsp;&nbsp;[P0336R1 zmiana nazw zasad wykonywania równoległego](https://wg21.link/p0336r1)<br/>[algorytmy równoległe &nbsp;&nbsp;P0394R4 powinny kończyć () dla wyjątków](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 ujednolicenie \<> algorytmów równoległych](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 ()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot — (x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 constexpr dla \<tablicy > (ponownie) i \<iterator >](https://wg21.link/p0031r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 jednorodnego interfejsu dla wariantu/dowolnego/opcjonalnego](https://wg21.link/p0032r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0033R1 enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 rozszerzanie narzędzi do zarządzania pamięcią](https://wg21.link/p0040r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0063R3 biblioteki standardowej](https://wg21.link/p0063r3) | VS 2015 <sup> [C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 podstawowe konwersje ciągów](https://wg21.link/p0067r5) | VS 2019 16,4 <sup> [charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0083R3 łączenie map i zestawów](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 wyjaśnienie insert_return_type](https://wg21.link/p0508r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 emplace typ zwracany](https://wg21.link/p0084r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<wariantów >](https://wg21.link/p0088r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0092R1 \<chrono > Floor (), ceil — (), Round (), ABS ()](https://wg21.link/p0092r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 niepodzielną:: is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size itd.](https://wg21.link/p0154r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 wariadyczne lock_guard](https://wg21.link/p0156r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 zmiana nazwy wariadyczne blokady\_Guard na\_blokadę zakresu](https://wg21.link/p0156r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr:: weak_type](https://wg21.link/p0163r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0174R2 przestarzałych części biblioteki szczątkowe](https://wg21.link/p0174r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple ()](https://wg21.link/p0209r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0218R1 \<systemu plików >](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[ścieżki względne P0219R1 dla systemu plików](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[P0317R1 wpisów w katalogu dla systemu plików](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 obsługę String_view w ścieżkach systemu plików](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 obsługujący systemy plików innych niż POSIX](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 rozpoznawania komentarzy NB dla systemu plików](https://wg21.link/p0492r2) | VS 2017 15,7 <sup> [E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 — podstawowe informacje o bibliotece 1](https://wg21.link/p0220r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[funkcji specjalnych matematycznych P0226R1](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 integrację String_view i std:: String](https://wg21.link/p0254r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15,3 <sup> [G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 niestałe basic_string::d ATA ()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 GCD (), LCM ()](https://wg21.link/p0295r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std:: Byte](https://wg21.link/p0298r3) | VS 2017 15,3 <sup> [17](#note_17),&nbsp;[bajt](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 usuwania obsługi alokatora w funkcji std:: Function](https://wg21.link/p0302r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2, aby ponownie zwiększyć wartość opcjonalną](https://wg21.link/p0307r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0393R3, dzięki czemu wariant jest większy](https://wg21.link/p0393r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0403R1 UDL dla \<string_view > ("meow" SV itd.)](https://wg21.link/p0403r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<t [] > shared_ptr\<t [N] >](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 naprawianie Shared_ptr dla tablic](https://wg21.link/p0497r0) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 niepodzielne Compare_exchange wymagania memory_order](https://wg21.link/p0418r2) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr dla char_traits](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 integrujące odliczanie szablonów dla szablonów klas w bibliotece standardowej](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 ulepszania integracji argumentu szablonu klasy z biblioteką standardową](https://wg21.link/p0739r0) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Dostosowywanie typowego typu\_i czasu trwania](https://wg21.link/p0548r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 odwiedzania in_place_t/in_place_type_t\<t >/in_place_index_t\<I >](https://wg21.link/p0504r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0505R0 constexpr dla \<chrono > (ponownie)](https://wg21.link/p0505r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 odrzucania wariantów elementów Nothing, tablic, odwołań i niekompletnych typów](https://wg21.link/p0510r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[skrótu zatrucia P0513R0](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept](https://wg21.link/p0599r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 oznaczania Shared_future kopiowania jako noexcept](https://wg21.link/p0516r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 konstruowania Future_error z future_errc](https://wg21.link/p0517r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 przestarzałe shared_ptr:: Unique ()](https://wg21.link/p0521r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 rozpoznawania niepodzielnych\<t > klasy podstawowej](https://wg21.link/p0558r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std:: is_constant_evaluated ()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 propagowanie niezmiennej kopiowania/przenoszenia w elemencie Variant/Optional](https://wg21.link/P0602R4) | VS 2017 15,3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 zmiana jest\_wywoływanie/wynik\_do wywołania\_wyniku, jest\_wywoływać, jest\_nothrow\_wywoływać](https://wg21.link/p0604r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 zmiennych wbudowanych dla standardowej biblioteki](https://wg21.link/p0607r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 przestarzałe \<codecvt >](https://wg21.link/p0618r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 naprawione podstawowe konwersje ciągów](https://wg21.link/P0682R1) | VS 2015 15,7 <sup> [17](#note_17)</sup> |
| __C++ 14 — funkcje biblioteki standardowej__ | __Obsługiwane__ |
| &nbsp;&nbsp;[N3462 SFINAE — przyjazny result_of](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr dla \<złożonych >](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr dla \<chrono >](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr dla tablicy \<>](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr dla \<initializer_list >, \<> spójnej kolekcji, \<narzędzi >](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant:: operator () ()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDL For \<chrono >, \<ciąg > (1729ms, "meow" itd.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Iteratory do przodu o wartości null](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 ()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Heterogeniczne wyszukiwanie asocjacyjne](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (czas)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 Exchange ()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 naprawianie funkcji Członkowskich constexpr bez stałej](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670\<t > ()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 podwójnego zakresu (), is_permutation (), niezgodność ()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[dealokacji N3778 o rozmiarze](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDL dla \<złożonych > (3.14 i itp.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr dla \<funkcjonalnej >](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 zmianę nazwy shared_mutex (czas) na shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 minimalnych wymagań dotyczących elementów kontenera](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 przezroczystego operatora funktory (mniej\<> itd.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[Szablony aliasów N3655 dla \<type_traits > (decay_t itd.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique ()](https://wg21.link/n3656) | VS 2013 |

Grupa papierów wymienionych razem wskazuje standardowe funkcje wraz z co najmniej jednym zatwierdzonym udoskonaleniem lub rozszerzeniem. Te funkcje są implementowane razem.

### <a name="supported-values"></a>Obsługiwane wartości

__Nie oznacza,__ że jeszcze nie zaimplementowano. \
__Częściowe__ oznacza, że implementacja nie jest kompletna. Aby uzyskać więcej informacji, zobacz sekcję Uwagi.
__VS 2010__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2010. \
__VS 2013__ wskazuje funkcje, które są obsługiwane w Visual Studio 2013. \
__VS 2015__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2015 (RTW). \
__Vs 2015,2__ i __vs 2015,3__ wskazują funkcje, które są odpowiednio obsługiwane w programie Visual Studio 2015 Update 2 i Visual Studio 2015 Update 3. \
__VS 2017 15,0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,0 (RTW). \
__VS 2017 15,3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,3. \
__VS 2017 15,5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,5. \
__VS 2017 15,7__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15,7. \
__VS 2019 16,0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,0 (RTW). \
__VS 2019 16,1__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,1. \
__VS 2019 16,2__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,2. \
__VS 2019 16,3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,3. \
__VS 2019 16,4__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,4. \
__VS 2019 16,5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16,5.

### <a name="notes"></a>Uwagi

<a name="note_A"></a>__A__ w [/std: tryb c++ 14](../build/reference/std-specify-language-standard-version.md) , dynamiczne specyfikacje wyjątków pozostają niezaimplementowane, a `throw()` jest nadal traktowany jako synonim dla `__declspec(nothrow)`. W języku C++ 17 dynamiczne specyfikacje wyjątków zostały przed chwilą usunięte przez P0003R5, pozostawiając jedną vestigeę: `throw()` jest przestarzała i wymagane do zachowania synonimu `noexcept`. W trybie [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) , MSVC teraz jest zgodna z normą, dając `throw()` takie samo zachowanie jak `noexcept`, czyli wymuszanie przez zakończenie.

Opcja kompilatora [/Zc: noexceptTypes](../build/reference/zc-noexcepttypes.md) żąda starego zachowania `__declspec(nothrow)`. Prawdopodobnie `throw()` zostanie usunięta w języku C++ 20. Aby ułatwić Migrowanie kodu w odpowiedzi na te zmiany w standardzie i naszej implementacji, nowe ostrzeżenia kompilatora dotyczące problemów ze specyfikacją wyjątków zostały dodane w obszarze [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) i [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ obsługiwane w trybie [/permissive-](../build/reference/permissive-standards-conformance.md) w programie Visual Studio 2017 w wersji 15,7. Aby uzyskać więcej informacji, zobacz [dwuetapowa obsługa wyszukiwania nazw jest MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ obsługa reguł preprocesora C99 przez kompilator jest niekompletna w programie Visual Studio 2017. Przeniesiemy preprocesor i zaczniemy przedostawać te zmiany w programie Visual Studio 2017 w wersji 15,8 z przełącznikiem kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) .

<a name="note_D"></a>__D__ obsługiwane w obszarze [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) z suppressible ostrzeżenie, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>Jest __to w__ pełni nowa implementacja, niezgodna z poprzednią wersją `std::experimental`, która jest wymagana przez pomoc techniczną link symboliczny, poprawki błędów i zmiany w zachowaniu standardowym. Obecnie w tym \<> systemu plików udostępnia nowy `std::filesystem` i poprzednią `std::experimental::filesystem`, a także \<eksperymentalny/system plików > zapewnia tylko starą implementację eksperymentalną. Implementacja eksperymentalna zostanie usunięta w następnej ABIej wersji biblioteki.

<a name="note_G"></a>__G__ obsługiwane przez wewnętrznie kompilator.

<a name="note_14"></a>__14__ te funkcje języka c++ 17/20 są zawsze włączone, nawet w przypadku określenia [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) (wartość domyślna). Przyczyną jest to, że funkcja została zaimplementowana przed wprowadzeniem opcji **/STD** lub że implementacja warunkowa była niecelowo złożona.

<a name="note_17"></a>__17__ te funkcje są włączane przez opcję kompilatora [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + +](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a>__20__ te funkcje są włączane przez [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md) opcja kompilatora. Po zakończeniu implementacji języka C++ 20 zostanie dodana nowa opcja kompilatora **/std: c++ 20** , w której te funkcje będą również dostępne.

<a name="note_byte"></a>`std::byte` __bajty__ jest włączane przez [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md)), ale ponieważ w niektórych przypadkach może powodować konflikt z nagłówkami Windows SDK, ma ono szczegółowe makro z szczegółowymi krokami. Można ją wyłączyć, definiując `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ Uniwersalna CRT wdrożyła części standardowej biblioteki C11, które są wymagane przez C++ 17, z wyjątkiem `strftime()` C99ych alternatywnych specyfikatorów konwersji, C11 `fopen()` trybu wyłącznego i C11 `aligned_alloc()`. Ten ostatni jest mało prawdopodobne, ponieważ C11 określony `aligned_alloc()` w sposób, który jest niezgodny z implementacją firmy Microsoft `free()`: mianowicie, `free()` musi być w stanie obsługiwać wysoce wyrównane alokacje.

<a name="note_rem"></a>__REM__ Funkcje usunięte w przypadku wybrania opcji kompilatora [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (lub [/std: c + +](../build/reference/std-specify-language-standard-version.md)). Te funkcje można włączyć w celu ułatwienia przejścia do nowszych trybów języka przy użyciu następujących makr: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`i `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` i `to_chars()` są dostępne dla liczb całkowitych. Oś czasu dla `from_chars()` zmiennoprzecinkowych i zmiennoprzecinkowych `to_chars()` jest następująca:
- VS 2017 15,7: liczba całkowita `from_chars()` i `to_chars()`.
- VS 2017 15,8: `from_chars()`zmiennoprzecinkowe.
- VS 2017 15,9: przeciążania zmiennoprzecinkowe `to_chars()` dla najkrótszej liczby dziesiętnej.
- VS 2019 16,0: przeciążania zmiennoprzecinkowe `to_chars()` dla najkrótszej wartości szesnastkowej i dokładności.
- VS 2019 16,2: przeciążania zmiennoprzecinkowe `to_chars()` dla stałych i precyzyjnej precyzji.
- VS 2019 16,4: zmiennoprzecinkowe `to_chars()` Przeciążenie dla ogólnego stopnia precyzji.

<a name ="note_parallel"></a>__równolegle__ Biblioteka algorytmów równoległych języka c++ 17 została ukończona. Zakończenie nie oznacza, że każdy algorytm jest równoległy w każdym przypadku. Najważniejsze algorytmy zostały przełączone i są udostępniane sygnatury zasad wykonywania, nawet w przypadku których algorytmy nie są równoległe. Główny nagłówek wewnętrzny, yvals_core. h, zawiera następujące "informacje o algorytmach równoległych": C++ umożliwia implementację implementującą algorytmy równoległe jako wywołania do algorytmów szeregowych. Ta implementacja parallelizes kilka typowych wywołań algorytmu, ale nie wszystkich.

Następujące algorytmy są równoległe:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Następujące elementy nie są obecnie równoległe:

- Niezauważalne zwiększenie wydajności dla sprzętu docelowego; wszystkie algorytmy, które tylko kopiują lub Permute — elementy bez rozgałęzień, są zwykle ograniczone przepustowością pamięci:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Istnieje pomylenie wymagań równoległości użytkowników; na ogół w powyższej kategorii nadal:
  - `generate`, `generate_n`
- Skuteczna równoległość prawdopodobnie jest niewykonalna:
  - `partial_sort`, `partial_sort_copy`
- Jeszcze nie oceniono; równoległość może zostać zaimplementowana w przyszłej wersji i prawdopodobnie jest korzystna:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Zobacz też

Informacje dotyczące języka\ [ C++ ](../cpp/cpp-language-reference.md)
[ C++\ biblioteki standardowej](../standard-library/cpp-standard-library-reference.md)
[ulepszenia zgodności w programie Visual Studio\ C++ ](cpp-conformance-improvements.md)
[Co nowego w wizualizacji C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historia C++ zmian wizualnych 2003 do 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Wizualizacja C++ nowości od 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[C++Blog zespołu](https://devblogs.microsoft.com/cppblog/)
