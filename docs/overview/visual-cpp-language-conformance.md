---
title: Tabela zgodności języka języka Microsoft C++
description: Tabela aktualizacji zgodności programu Microsoft C++ według wersji programu Visual Studio.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 18f8db28fab83f795baced82a346f07d73256716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365234"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabela zgodności języka języka Microsoft C++

Zgodność ze standardami kompilatora Języka Microsoft C++ w programie Visual Studio (MSVC) jest w toku. Oto podsumowanie naszego standardowego języka i biblioteki ISO Standard C++ według wersji programu Visual Studio. Każdy kompilator i standardowa nazwa funkcji biblioteki łączy się z dokumentem propozycji STANDARD ISO C++, który opisuje tę funkcję, jeśli jest dostępna w czasie publikacji. **Obsługiwana kolumna** zawiera listę wersji programu Visual Studio, w której po raz pierwszy pojawiła się obsługa tej funkcji.

Aby uzyskać szczegółowe informacje na temat ulepszeń zgodności programu Visual Studio 2017 lub Visual Studio 2019 MSVC, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio.](cpp-conformance-improvements.md) Aby uzyskać listę innych zmian, zobacz [Co nowego w programie Visual C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Aby uzyskać zmiany zgodności we wcześniejszych wersjach, zobacz [Historia zmian języka Visual C++](../porting/visual-cpp-change-history-2003-2015.md) i Visual [C++ What's New 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Aby uzyskać aktualne informacje z zespołu C++, odwiedź [blog zespołu C++](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Nie ma żadnych zmian podziału binarnego między programami Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019. Aby uzyskać więcej informacji, zobacz [Zgodność binarna języka C++ między programami Visual Studio 2015, 2017 i 2019](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>Funkcje kompilatora

|  |  |
|--|--|
| __C++03/11 Podstawowe funkcje językowe__ | __Obsługiwane__ |
| &nbsp;&nbsp;Wszystko | VS 2015 <sup> [A](#note_A)</sup> |
| &nbsp;&nbsp;Wyszukiwanie nazw dwufazowych | VS 2017 15,7 <sup> [B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 Wyrażenie SFINAE](https://wg21.link/N2634) | VS 2017 15,7 |
| &nbsp;&nbsp;[Preprocesor N1653 C99](https://wg21.link/N1653) | Częściowe <sup> [C](#note_C)</sup> |
| __Podstawowe funkcje języka języka C++14__ | __Obsługiwane__ |
| &nbsp;&nbsp;[N3323 Poprawione sformułowanie dla konwersji kontekstowych](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 Literały binarne](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 typy zwrotów automatycznych i decltype(auto)](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-captures](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 Jagnięta rodzajowe](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[Atrybut N3760 \[ \[\] \] przestarzały](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[Alokacja wielkości N3778](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[Separatory cyfr N3781](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[Szablony zmiennych N3651](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 Rozszerzone constexpr](https://wg21.link/n3652) | VS 2017 15,0 |
| &nbsp;&nbsp;[N3653 Domyślne inicjatory elementów członkowskich dla agregatów](https://wg21.link/n3653) | VS 2017 15,0 |
| __C++17 Podstawowe funkcje językowe__ | __Obsługiwane__ |
| &nbsp;&nbsp;[N4086 Usuwanie trójgrafów](https://wg21.link/n4086) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 Nowe reguły dla auto z usztywnionymi listami init](https://wg21.link/n3922) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Nazwa typu N4051 w szablonie-parametrów](https://wg21.link/n4051) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Atrybuty N4266 dla obszarów nazw i wyliczaczy](https://wg21.link/n4266) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Literały znaków N4267 u8](https://wg21.link/n4267) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Definicje zagnieżdżonych obszarów nazw N4230](https://wg21.link/n4230) | VS 2015.3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 Terse static_assert](https://wg21.link/n3928) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 Uogólnione pętle dla pętli opartych na zakresie](https://wg21.link/p0184r0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Atrybut upadek\] P0188R1 \[ \[\]](https://wg21.link/p0188r1) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 Usuwanie słowa kluczowego rejestru](https://wg21.link/p0001r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 Usuwanie operatora++ dla bool](https://wg21.link/p0002r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 Przechwytywanie *to według wartości](https://wg21.link/p0018r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 Korzystanie z obszarów nazw atrybutów bez powtarzania](https://wg21.link/p0028r4) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[has_include P0061R1 \_ \_](https://wg21.link/p0061r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Direct-list-init stałych wyliczenia z liczby całkowitej](https://wg21.link/p0138r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 constexpr lambdas](https://wg21.link/p0170r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Atrybut nodiscard \[ \[\] \] P0189R1](https://wg21.link/p0189r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Atrybut maybe_unused\] P0212R1 \[ \[\]](https://wg21.link/p0212r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Wiązania strukturalne P0217R3](https://wg21.link/p0217r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if-statements P0292R2 constexpr if-statements P0292R2 constexpr if-statements P0](https://wg21.link/p0292r2) | VS 2017 15,3 <sup> [D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 Instrukcje wyboru z inicjatorami](https://wg21.link/p0305r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Literały hexfloat](https://wg21.link/p0245r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 Zezwala na więcej argumentów szablonów innych niż typ](https://wg21.link/n4268) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Wyrażenia krotnie N4295](https://wg21.link/n4295) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Usuwanie specyfikacji wyjątków dynamicznych](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 Dodawanie noexcept do systemu typu](https://wg21.link/p0012r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 Przerównana alokacja pamięci dynamicznej](https://wg21.link/p0035r4) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 Zmienne wbudowane](https://wg21.link/p0386r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 Dopasowanie parametrów szablonu do zgodnych argumentów](https://wg21.link/p0522r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 Usuwanie pustych, niewymiernych fałd](https://wg21.link/p0036r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 Ustalanie konwersji kwalifikacji](https://wg21.link/n4261) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Inicjowanie agregacji rozszerzonej](https://wg21.link/p0017r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0091R3 Potrącenie argumentu szablonu dla szablonów klas](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 Problemy z potrąceniem argumentu szablonu klasy](https://wg21.link/p0512r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 Deklarowanie parametrów szablonu nienakłowego za pomocą auto](https://wg21.link/p0127r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 Gwarantowana kopia elision](https://wg21.link/p0135r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0136R1 Rewording konstruktorów dziedziczenia](https://wg21.link/p0136r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::pranie](https://wg21.link/p0137r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 Kolejność oceny wyrażenia rafinacji](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 Kolejność oceny argumentów funkcyjnych](https://wg21.link/p0400r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0195R2 Rozszerzenia pakietów w deklaracjach użycia](https://wg21.link/p0195r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 Ignorowanie nierozpoznanych atrybutów](https://wg21.link/p0283r2) | VS 2015 <sup> [14](#note_14)</sup> |
| __Funkcje języka C++17 Podstawowe (raporty o wadach)__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0702R1 Ustalanie potrącenia argumentu szablonu klasy dla ctorów listy inicjatorów](https://wg21.link/p0702r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 Rozluźnienie zasad znajdowania punktów dostosowywania wiązań strukturalnych](https://wg21.link/p0961r1) | VS 2019 16.0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 Zezwalanie na wiązania strukturalne dla dostępnych elementów członkowskich](https://wg21.link/p0969r0) | VS 2019 16.0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 Upraszczanie niejawnego przechwytywania lambda](https://wg21.link/p0588r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[ \[nodiscard\] \] dla konstruktorów](https://wg21.link/p1771r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 Scalone sformułowanie dla P0527R1 i P1155R3, bardziej niejawne ruchy](https://wg21.link/p1825r0) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 Sprawdzanie typów klas abstrakcyjnych](https://wg21.link/P0929R2) | Nie |
| &nbsp;&nbsp;[P0962R2 Rozluźnienie reguł znajdowania punktu dostosowywania pętli](https://wg21.link/p0962r1) | Nie |
| &nbsp;&nbsp;[P0859R0 CWG 1581: Kiedy zdefiniowano funkcje członkowskie constexpr](https://wg21.link/p0859r0) | Nie |
| &nbsp;&nbsp;[P1009R2 Potrącenie rozmiaru tablicy w nowych wyrażeniach](https://wg21.link/P1009R2) | Nie |
| &nbsp;&nbsp;[P1286R2 Contra CWG DR1778](https://wg21.link/P1286R2) | Nie |
| __Podstawowe funkcje języka C++20__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0704R1 Mocowanie const lvalue ref-kwalifikowanych wskaźników do członków](https://wg21.link/p0704r1) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 Aby literały char16_t/char32_t być UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 Zmiana aktywnego członka związku wewnątrz constexpr](https://wg21.link/P1330R0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 noexcept \<Dla chrono> zero(), min(), max()](https://wg21.link/P0972R0) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Operator porównania trójdrożnego (statku kosmicznego) <=>](https://wg21.link/P0515R3) | VS 2019 16.0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 Makra testu funkcji](https://wg21.link/P0941R2) | VS 2019 16.0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 Zakaz agregatów z konstruktorami zadeklarowanych przez użytkownika](https://wg21.link/P1008R1) | VS 2019 16.0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 Inicjowanie wyznaczone](https://wg21.link/p0329r4) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 ADL i szablony funkcji, które nie są widoczne](https://wg21.link/P0846R0) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 Umożliwiające przechwytywanie \[lambda =,\]](https://wg21.link/p0409r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 Znana składnia szablonu dla generycznych lambd](https://wg21.link/p0428r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 Domyślne konstruowalne i przypisywalne bezpaństwowe lambdy](https://wg21.link/P0624R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 Umożliwia rozszerzenie pakietu w lambda init-capture](https://wg21.link/P0780R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 Przestarzałe niejawne przechwytywanie tego za pośrednictwem\[=\]](https://wg21.link/P0806R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 Poprawa spójności dla <=> i innych operatorów porównania](https://wg21.link/P1120R0) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \< = \> != ==](https://wg21.link/P1185R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[Pojęcia P0734R0](https://wg21.link/P0734R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 Luki w funkcjach mocowania w wiązaniach](https://wg21.link/P0857R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 Dzisiejsze wymagania dotyczące zwrotu są niewystarczające](https://wg21.link/P1084R2) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 Warunkowe jawne](https://wg21.link/P0892R2) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 Rozszerzanie wiązań strukturalnych, aby były bardziej jak deklaracje zmienne](https://wg21.link/P1091R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 Korzystanie z wyliczenia](https://wg21.link/P1099R5) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3 Kiedy faktycznie używasz\<=>](https://wg21.link/P1186R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 Statek kosmiczny potrzebuje tune-up](https://wg21.link/P1630R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 \_ \_Dodanie VA_OPT\_ \_ do usunięcia przecinka i przecinka](https://wg21.link/P0306R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 Pętle na bazie zasięgu z inicjatorami](https://wg21.link/P0614R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 Domyślne inicjatory elementów członkowskich dla pól bitowych](https://wg21.link/P0683R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 try-catch bloków w constexpr funkcji](https://wg21.link/P1002R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 Przestarzałe zastosowania operatora przecinka w wyrażeniach dolnego](https://wg21.link/P1161R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[ \[nodiscard("wiadomość")\]\]](https://wg21.link/P1301R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 Rozpoznawanie importu jednostki nagłówka wymaga pełnego wstępnego przetwarzania](https://wg21.link/P1703R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Zezwalaj na domyślne porównania według wartości](https://wg21.link/P1946R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[Niezgodność konsytu P0641R2 z domyślnym konstruktorem kopii](https://wg21.link/P0641R2) | Częściowo |
| &nbsp;&nbsp;[P0912R5 Coroutyny](https://wg21.link/P0912R5) | Częściowo |
| &nbsp;&nbsp;[Moduły P1103R3](https://wg21.link/P1103R3) | Częściowo |
| &nbsp;&nbsp;[P0315R4 Zezwalanie na lambdę w nieocenionych kontekstach](https://wg21.link/P0315R4) | Nie |
| &nbsp;&nbsp;[P0388R4 Zezwalaj na konwersje do tablic o nieznanej granicy](https://wg21.link/P0388R4) | Nie |
| &nbsp;&nbsp;[P0479R5 \[ \[\] \] prawdopodobne \[ \[i\] \] mało prawdopodobne atrybuty](https://wg21.link/P0479R5) | Nie |
| &nbsp;&nbsp;[P0634R3 W dół z typename!](https://wg21.link/P0634R3) | Nie |
| &nbsp;&nbsp;[P0692R1 Kontrola dostępu chyli podczas specjalizacji](https://wg21.link/P0692R1) | Nie |
| &nbsp;&nbsp;[P0722R3 Efektywne usuwanie wielkości dla klas o zmiennym rozmiarze](https://wg21.link/P0722R3) | Nie |
| &nbsp;&nbsp;[Typy klas P0732R2 w parametrach szablonu nienakładowego](https://wg21.link/P0732R2) | Nie |
| &nbsp;&nbsp;[P0735R1 Interakcja memory_order_consume z sekwencjami uwalniania](https://wg21.link/P0735R1) | Nie |
| &nbsp;&nbsp;[P0784R7 Więcej kontenerów constexpr](https://wg21.link/P0784R7) | Nie |
| &nbsp;&nbsp;[Atrybut \[ \[P0840R2 no_unique_address\] \]](https://wg21.link/P0840R2) | Nie |
| &nbsp;&nbsp;[P0848R3 Warunkowo trywialne funkcje specjalne elementów członkowskich](https://wg21.link/P0848R3) | Nie |
| &nbsp;&nbsp;[P0960R3 Zezwalaj na inicjowanie agregatów z listy wartości w nawiasach](https://wg21.link/P0960R3) | Nie |
| &nbsp;&nbsp;[P1064R0 Zezwalanie na wywołania funkcji wirtualnych w wyrażeniach stałych](https://wg21.link/P1064R0) | Nie |
| &nbsp;&nbsp;[P1073R3 Funkcje natychmiastowe](https://wg21.link/P1073R3) | Nie |
| &nbsp;&nbsp;[P1094R2 Zagnieżdżone wbudowane wbudowane przestrzenie nazw](https://wg21.link/P1094R2) | Nie |
| &nbsp;&nbsp;[P1139R2 Rozwiązywanie problemów związanych z ISO 10646](https://wg21.link/P1139R2) | Nie |
| &nbsp;&nbsp;[P1141R2 Kolejne podejście do deklaracji z ograniczeniami](https://wg21.link/P1141R2) | Nie |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Nie |
| &nbsp;&nbsp;[P1152R4 Przestarzałe](https://wg21.link/P1152R4) | Nie |
| &nbsp;&nbsp;[P1236R1 Podpisane liczby całkowite są uzupełnieniem dwóch](https://wg21.link/P1236R1) | Nie |
| &nbsp;&nbsp;[P1327R1 Zezwalanie na dynamic_cast, polimorficzny typid w wyrażeniach stałych](https://wg21.link/P1327R1) | Nie |
| &nbsp;&nbsp;[P1331R2 Zezwalanie na trywialne inicjowanie domyślne w kontekstach constexpr](https://wg21.link/P1331R2) | Nie |
| &nbsp;&nbsp;[P1353R0 Brak makr testowych funkcji](https://wg21.link/P1353R0) | Nie |
| &nbsp;&nbsp;[P1381R1 Przechwytywanie odniesienia opraw strukturalnych](https://wg21.link/P1381R1) | Nie |
| &nbsp;&nbsp;[P1452R2 Na nieujemniejszej semantyki wymagań typu zwrotu](https://wg21.link/P1452R2) | Nie |
| &nbsp;&nbsp;[P1616R1 Korzystanie z nieograniczonych ttp z ograniczonymi szablonami](https://wg21.link/P1616R1) | Nie |
| &nbsp;&nbsp;[P1668R1 Zezwalanie na nieoceniony zestaw wbudowany w funkcjach constexpr](https://wg21.link/P1668R1) | Nie |
| &nbsp;&nbsp;[P1766R1 Łagodzenie drobnych dolegliwości modułów](https://wg21.link/P1766R1) | Nie |
| &nbsp;&nbsp;[P1811R0 Złagodzenie ograniczeń redefinicji dla odporności na reeksport](https://wg21.link/P1811R0) | Nie |
| &nbsp;&nbsp;[P1814R0 CTAD dla szablonów aliasów](https://wg21.link/P1814R0) | Nie |
| &nbsp;&nbsp;[P1816R0 CTAD dla agregatów](https://wg21.link/P1816R0) | Nie |
| &nbsp;&nbsp;[P1874R1 Kolejność inicjowania dynamicznego zmiennych nielokalnych w modułach](https://wg21.link/P1874R1) | Nie |
| &nbsp;&nbsp;[P1907R1 Niespójności z parametrami szablonu nienakłowego](https://wg21.link/P1907R1) | Nie |
| &nbsp;&nbsp;[P1971R0 Podstawowe zmiany dla uwag NB na posiedzeniu w listopadzie 2019 r. (Belfast)](https://wg21.link/P1971R0) | Nie |
| &nbsp;&nbsp;[P1972R0 US105 Sprawdzanie zadowolenia z ograniczeń dla nie-szablonów podczas tworzenia wskaźnika do funkcji](https://wg21.link/P1972R0) | Nie |
| &nbsp;&nbsp;[P1975R0 Ustalanie brzmienia inicjowania zagregowanego nawiasów](https://wg21.link/P1975R0) | Nie |
| &nbsp;&nbsp;[P1979R0 Rozdzielczość do US086](https://wg21.link/P1979R0) | Nie |
| &nbsp;&nbsp;[P1980R0 CA096: Dopasowanie deklaracji dla nienieleżących klauzul wymaganych](https://wg21.link/P1980R0) | Nie |

## <a name="standard-library-features"></a>Standardowe funkcje biblioteki

|  |  |
|--|--|
| __Funkcje biblioteki standardowej języka C++20__ | __Obsługiwane__ |
| &nbsp;&nbsp;[P0809R0 Porównanie nieurządzonych kontenerów](https://wg21.link/p0809r0) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0 Constexpr Iterator Wymagania](https://wg21.link/p0858r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 Unikanie niepotrzebnego próchnicy](https://wg21.link/p0777r1) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 Intuicyjnie create_directory()](https://wg21.link/P1164R1) | VS 2019 16.0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[remove_cvref P0550R2](https://wg21.link/p0550r2) | VS 2019 16.0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with()/ends_with() dla basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 zawiera() dla zamówionych i nieuiszczonych kontenerów zespolonych](https://wg21.link/p0458r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 lista/forward_list remove()/remove_if()/unique() Powrót size_type](https://wg21.link/p0646r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](https://wg21.link/p0769r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6\<atomowy pływak>,\<atomowy podwójny>, atomowy\<długi podwójny>](https://wg21.link/p0020r6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: Typ znaków i ciągów UTF-8](https://wg21.link/P0482R6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[ \[nodiscard\] \] dla STL, część 1](https://wg21.link/p0600r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<wersja>](https://wg21.link/p0754r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 noexcept Dla std::function's Move Constructor](https://wg21.link/P0771R1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1>> operatora mocującego(basic_istream&, CharT*)](https://wg21.link/P0487R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 Korzystanie z \<move() w>numerycznej](https://wg21.link/p0616r0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[Pojęcia dotyczące standardowej biblioteki P0898R3](https://wg21.link/P0898R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 Heterogeniczne wyszukiwanie nieurządzonych pojemników](https://wg21.link/P0919R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 Zmień nazwę koncepcji na standard_case](https://wg21.link/P1754R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array od LFTS z aktualizacjami](https://wg21.link/P0325R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 underlying_type przyjazny dla SFINAE](https://wg21.link/P0340R3) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 klasa wyliczenia memory_order](https://wg21.link/p0439r0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bit> funkcje obracania i liczenia](https://wg21.link/P0553R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[Numery P0631R8 \<> stałe matematyczne](https://wg21.link/P0631R8) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 istream_iterator Oczyszczanie](https://wg21.link/P0738R2) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 Przestarzałe is_pod](https://wg21.link/P0767R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 ciąg::reserve() nie należy kurczyć](https://wg21.link/P0966R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if(), wymazywanie()](https://wg21.link/P1209R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 Podpisany std::ssize(), Niepodpisany zakres::size()](https://wg21.link/P1227R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Wąski kontrakt na ceil2()](https://wg21.link/P1355R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 Przeniesienie endian \<do bit>](https://wg21.link/P1612R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() nie powinny reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 Rafinacja Heterogenicznych wyszukiwania nieurządzonych pojemników](https://wg21.link/P1690R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 Brak makr testu funkcji 2017-2019](https://wg21.link/P1902R1) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | Nie |
| &nbsp;&nbsp;[>strumienia synchronizacji \<P0053R7](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[Manipulatory osyncstream P0753R2](https://wg21.link/p0753r2) | Nie |
| &nbsp;&nbsp;[P0122R7 \<>rozpiętości](https://wg21.link/p0122r7) | Nie |
| &nbsp;&nbsp;[P0202R3 constexpr \<Dla algorytmu> i exchange()](https://wg21.link/p0202r3) | Nie |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6) | Nie |
| &nbsp;&nbsp;[P0355R7 \<chrono> kalendarze i strefy czasowe](https://wg21.link/p0355r7) | Nie |
| &nbsp;&nbsp;[P0357R3 obsługa niekompletnych typów w reference_wrapper](https://wg21.link/P0357R3) | Nie |
| &nbsp;&nbsp;[P0415R1 constexpr \<Dla złożonych> (Ponownie)](https://wg21.link/p0415r1) | Nie |
| &nbsp;&nbsp;[P0475R1 Gwarantowana kopia Elision do konstrukcji fragmentaryzowej](https://wg21.link/P0475R1) | Nie |
| &nbsp;&nbsp;[P0476R2 \<> bit_cast](https://wg21.link/P0476R2) | Nie |
| &nbsp;&nbsp;[P0528R3 Atomowej porównanie i wymiany z bitów wyściółki](https://wg21.link/P0528R3) | Nie |
| &nbsp;&nbsp;[P0591R4 Funkcje użytkowe do zastosowań-alokatora budowy](https://wg21.link/P0591R4) | Nie |
| &nbsp;&nbsp;[P0608R3 Ulepszanie konstruktora/przydziału konwersji wariantu](https://wg21.link/P0608R3) | Nie |
| &nbsp;&nbsp;[P0619R4 Usuwanie c++17-przestarzałe funkcje w C++20](https://wg21.link/P0619R4) | Nie |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | Nie |
| &nbsp;&nbsp;[P0655R1\<wizyta R>()](https://wg21.link/P0655R1) | Nie |
| &nbsp;&nbsp;[P0674R1 make_shared() dla macierzy](https://wg21.link/p0674r1) | Nie |
| &nbsp;&nbsp;[P0718R2\<shared_ptr atomowy\<T>>,\<weak_ptr atomowy\<T>>](https://wg21.link/p0718r2) | Nie |
| &nbsp;&nbsp;[Obsługa biblioteki P0768R1 dla operatora porównania statków kosmicznych\<=>](https://wg21.link/p0768r1) | Nie |
| &nbsp;&nbsp;[P0811R3 punkt środkowy(), lerp()](https://wg21.link/P0811R3) | Nie |
| &nbsp;&nbsp;[P0879R0 constexpr do wymiany funkcji](https://wg21.link/P0879R0) | Nie |
| &nbsp;&nbsp;[Zakresy P0896R4 \<\>](https://wg21.link/P0896R4) | Nie |
| &nbsp;&nbsp;[P0912R5 Obsługa biblioteki dla coroutyn](https://wg21.link/P0912R5) | Nie |
| &nbsp;&nbsp;[P0920R2 Wstępnie obliczone wyszukiwanie wartości skrótu](https://wg21.link/P0920R2) | Nie |
| &nbsp;&nbsp;[P0935R0 Eliminacja niepotrzebnie jawnych domyślnych konstruktorów](https://wg21.link/P0935R0) | Nie |
| &nbsp;&nbsp;[Wykonanie P1001R2::unseq](https://wg21.link/P1001R2) | Nie |
| &nbsp;&nbsp;[P1006R1 constexpr Dla pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1) | Nie |
| &nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3) | Nie |
| &nbsp;&nbsp;[Tworzenie inteligentnego wskaźnika P1020R1 z domyślną inicjacją](https://wg21.link/P1020R1) | Nie |
| &nbsp;&nbsp;[P1023R0 constexpr Dla std::array Porównania](https://wg21.link/P1023R0) | Nie |
| &nbsp;&nbsp;[P1032R1 Różne constexpr](https://wg21.link/P1032R1) | Nie |
| &nbsp;&nbsp;[P1165R1 Konsekwentnie propagowanie alokatorów stanowych w basic_string operatora+()](https://wg21.link/P1165R1) | Nie |
| &nbsp;&nbsp;[P1285R0 Poprawa wymagań dotyczących kompletności cech typu](https://wg21.link/P1285R0) | Nie |
| __Funkcje biblioteki standardowej języka C++17__ | __Obsługiwane__ |
| &nbsp;&nbsp;[LWG 2221 Sformatowany operator wyjściowy dla nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16,1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 Bezpieczne konwersje w\<unique_ptr T[]>](https://wg21.link/n4089) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 Usuwanie auto_ptr, random_shuffle() i stare \<funkcjonalne rzeczy>](https://wg21.link/n4190) | VS 2015 <sup> [rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 noexcept Cleanups](https://wg21.link/n4258) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 Trywialnie reference_wrapper do kopiowania](https://wg21.link/n4277) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() Dla mapy/unordered_map](https://wg21.link/n4279) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 size(), empty(), data()](https://wg21.link/n4280) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 Precyzyjnie ograniczające przypisanie unique_ptr](https://wg21.link/n4366) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 Poprawa pary i krotka](https://wg21.link/n4387) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[bool_constant N4389](https://wg21.link/n4389) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (bez przestojów)](https://wg21.link/n4508) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 Obsługa niekompletnych typów wektora/listy/forward_list](https://wg21.link/n4510) | VS 2013 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<algorytm> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15,0 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<dowolny>](https://wg21.link/n4562#any) | VS 2017 15,0 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<memory_resource>](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Usuwanie przypisania polymorphic_allocator](https://wg21.link/p0337r0) | VS 2017 15,6 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<opcjonalne>](https://wg21.link/n4562#optional) | VS 2017 15,0 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<string_view>](https://wg21.link/n4562#string.view) | VS 2017 15,0 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: \<krotka> apply()](https://wg21.link/n4562#tuple) | VS 2017 15,0 |
| &nbsp;&nbsp;[Podstawy biblioteki N4562: Wyszukiwanie Boyer-Moore()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Naprawianie typy powrotu wyszukiwarki](https://wg21.link/p0253r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Usuwanie dynamicznych specyfikacji wyjątków](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 Usuwanie przestarzałych aliasów Iostreamów](https://wg21.link/p0004r1) | VS 2015.2 <sup> [rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 Poprawki dla not_fn()](https://wg21.link/p0358r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Szablony zmiennych P0006R0 dla cech typu (is_same_v itp.)](https://wg21.link/p0006r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Cechy typu operatora logicznego P0013R1 (spójnik itp.)](https://wg21.link/p0013r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Algorytmy równoległe P0024R2](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 Zmiana nazwy zasad wykonywania równoległego](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 Algorytmy równoległe powinny zakończyć() dla wyjątków](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 Ujednolicenie \<algorytmów> równoległych>](https://wg21.link/p0452r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[Zacisk P0025R1()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0031R0 constexpr \<Dla> tablicy \<(Ponownie) I iterator>](https://wg21.link/p0031r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 Interfejs jednorodny dla wariantu/dowolnego/opcjonalnego](https://wg21.link/p0032r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0033R1 enable_shared_from_this przeredagowanie](https://wg21.link/p0033r1) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 Rozszerzające narzędzia do zarządzania pamięcią](https://wg21.link/p0040r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Biblioteka standardowa P0063R3 C11](https://wg21.link/p0063r3) | VS 2015 <sup> [C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[Konwersje ciągów elementarnych P0067R5](https://wg21.link/p0067r5) | VS 2019 16.4 <sup> [charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0083R3 Łączenie map i zestawów](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 insert_return_type wyjaśniający](https://wg21.link/p0508r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Typ zwrotu miejsca](https://wg21.link/p0084r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[wariant P0088R3 \<>](https://wg21.link/p0088r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> podłoga(), ceil(), round(), abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomowy::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size itp.](https://wg21.link/p0154r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 lock_guard](https://wg21.link/p0156r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 Zmiana nazwy variadic\_lock\_guard na blokadę z zakresem](https://wg21.link/p0156r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0174R2 Przestarzałe części biblioteki szczątkowej](https://wg21.link/p0174r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0218R1 \<>systemu plików](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[P0219R1 Ścieżki względne dla systemu plików](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[Buforowanie wpisów katalogu P0317R1 dla systemu plików](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 string_view w ścieżkach systemu plików](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 Obsługa systemów plików innych niż POSIX](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 Rozwiązywanie uwag NB dla systemu plików](https://wg21.link/p0492r2) | VS 2017 15,7 <sup> [E](#note_E)</sup> |
| &nbsp;&nbsp;[Podstawy biblioteki P0220R1 V1](https://wg21.link/p0220r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0226R1 Matematyczne funkcje specjalne](https://wg21.link/p0226r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0254R2 Integrowanie string_view i std::string](https://wg21.link/p0254r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[has_unique_object_representations P0258R2](https://wg21.link/p0258r2) | VS 2017 15,3 <sup> [G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd(), lcm()](https://wg21.link/p0295r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::bajt](https://wg21.link/p0298r3) | VS 2017 15,3 <sup> [17](#note_17),&nbsp;[bajt](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 Usuwanie obsługi alokatora w std::function](https://wg21.link/p0302r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 Ponowne wprowadzenie opcjonalnego większego równości](https://wg21.link/p0307r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0393R3 Wariant dokonujący większego równego](https://wg21.link/p0393r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0403R1 UDLs \<dla string_view> ("meow" sv, itp.)](https://wg21.link/p0403r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 shared_ptr mocowania dla macierzy](https://wg21.link/p0497r0) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 memory_order compare_exchange atomowej](https://wg21.link/p0418r2) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr dla char_traits](https://wg21.link/p0426r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0433R2 Integrowanie odliczeń szablonów klas w standardowej bibliotece](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 Usprawnienie integracji dedukcji argumentu szablonu klasy z biblioteką standardową](https://wg21.link/p0739r0) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0435R1 common_type remontowe](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Szczypanie\_wspólny typ i czas trwania](https://wg21.link/p0548r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 Powrót in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](https://wg21.link/p0504r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0505R0 constexpr \<Do> chrono (Ponownie)](https://wg21.link/p0505r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 Odrzucanie wariantów niczego, tablice, odniesienia i niekompletne typy](https://wg21.link/p0510r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0513R0 Zatrucie hash](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept hash](https://wg21.link/p0599r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Znakowanie P0516R0 shared_future kopiowanie jako nieznikustawy](https://wg21.link/p0516r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 Future_error konstrukująca od future_errc](https://wg21.link/p0517r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Przestarzałe shared_ptr::unique()](https://wg21.link/p0521r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 Rozwiązywanie\<atomowej T> o nazwie niespójności klasy podstawowej](https://wg21.link/p0558r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 Propagacja kopiowania/przenoszenia trywialność w wariancie/opcjonalnie](https://wg21.link/P0602R4) | VS 2017 15,3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 Zmiana\_jest\_wywoływana/wynik\_Wywołać\_wynik, jest invocable, jest\_nothrow\_invocable](https://wg21.link/p0604r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Zmienne wbudowane P0607R0 dla biblioteki standardowej](https://wg21.link/p0607r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 Przestarzałe \<kodekowanie>](https://wg21.link/p0618r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 Naprawa podstawowych konwersji ciągów](https://wg21.link/P0682R1) | VS 2015 15,7 <sup> [17](#note_17)</sup> |
| __Funkcje biblioteki standardowej języka C++14__ | __Obsługiwane__ |
| &nbsp;&nbsp;[result_of przyjazny dla N3462 SFINAE](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr \<Dla złożonych>](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr \<Dla>chrono](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr \<Dla>tablicowych](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr \<Do> initializer_list, \<krotki>, \<>użytkowej](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDLs \<Dla> chrono, \<> strun (1729ms, "meow" s, itp.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Puste iteratory do przodu](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 notowany()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Heterogeniczne wyszukiwanie zespolające](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (czas)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 exchange()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 Mocowanie constexpr funkcje członkowskie bez const](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670\<dostać T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 Dual-Range równe(), is_permutation(), niezgodność()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[Lokalizacja wielkości N3778](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDLs \<Dla złożonych> (3.14i, itp.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr \<Do>funkcjonalnych](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[tuple_element_t N3887](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 Zmiana nazwy shared_mutex (timed) do shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[Wymagania dotyczące minimalnego elementu kontenera N3346](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 Transparent Operator Functors (mniej\<>, itp.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[Szablony aliasów N3655 dla \<> type_traits (decay_t itp.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

Grupa dokumentów wymienionych razem wskazuje funkcję Standardowa wraz z co najmniej jedną zatwierdzoną poprawą lub rozszerzeniami. Te funkcje są implementowane razem.

### <a name="supported-values"></a>Obsługiwane wartości

__Żaden__ środek nie został jeszcze zaimplementowany.\
__Częściowe__ oznacza, że implementacja jest niekompletna. Aby uzyskać więcej informacji, zobacz sekcję Notatki.\
__Vs 2010__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2010.\
__VS 2013__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2013.\
__Vs 2015__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2015 (RTW).\
__VS 2015.2__ i __VS 2015.3__ wskazują funkcje, które są obsługiwane w programie Visual Studio 2015 Update 2 i Visual Studio 2015 Update 3, odpowiednio.\
__VS 2017 15.0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.0 (RTW).\
__VS 2017 15.3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.3.\
__VS 2017 15.5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.5.\
__VS 2017 15.7__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2017 w wersji 15.7.\
__VS 2019 16.0__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.0 (RTW).\
__VS 2019 16.1__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.1.\
__VS 2019 16.2__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.2.\
__VS 2019 16.3__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.3.\
__VS 2019 16.4__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.4.\
__VS 2019 16.5__ wskazuje funkcje, które są obsługiwane w programie Visual Studio 2019 w wersji 16.5.

### <a name="notes"></a>Uwagi

<a name="note_A"></a>__A__ W [trybie /std:c++14](../build/reference/std-specify-language-standard-version.md) dynamiczne specyfikacje wyjątków `throw()` pozostają niezaimplementowane `__declspec(nothrow)`i nadal są traktowane jako synonim . W języku C++17 dynamiczne specyfikacje wyjątków zostały w większości usunięte przez P0003R5, pozostawiając jeden `throw()` ślad: `noexcept`jest przestarzały i musi zachowywać się jako synonim dla . W [trybie /std:c++17](../build/reference/std-specify-language-standard-version.md) msvc jest teraz `throw()` zgodny ze `noexcept`standardem, dając takie samo zachowanie jak , czyli wymuszanie przez zakończenie.

Opcja kompilatora [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) żąda `__declspec(nothrow)`naszego starego zachowania . Prawdopodobnie zostanie on `throw()` usunięty w języku C++20. Aby pomóc w migracji kodu w odpowiedzi na te zmiany w standardzie i naszej implementacji, dodano nowe ostrzeżenia kompilatora dla problemów ze specyfikacją wyjątków w obszarze [/std:c++17](../build/reference/std-specify-language-standard-version.md) i [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ Obsługiwane w [trybie /permissive-](../build/reference/permissive-standards-conformance.md) w programie Visual Studio 2017 w wersji 15.7. Aby uzyskać więcej informacji, zobacz [Obsługa wyszukiwania nazw dwufazowych jest dostępna w u klienta MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ Obsługa kompilatora dla reguł preprocesora C99 jest niekompletna w programie Visual Studio 2017. Jesteśmy remontu preprocesora i rozpoczął wysyłkę tych zmian w programie Visual Studio 2017 w wersji 15.8 z [przełącznikiem kompilatora /experimental:preprocessor.](../build/reference/experimental-preprocessor.md)

<a name="note_D"></a>__D__ Obsługiwane w obszarze [/std:c++14](../build/reference/std-specify-language-standard-version.md) z ostrzeżeniem tłumiącym, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>__E__ Jest to całkowicie nowa implementacja, `std::experimental` niezgodna z poprzednią wersją, niezbędna przez obsługę dowiązań symbolicznych, poprawki błędów i zmiany w zachowaniu wymaganym przez standard. Obecnie, w \<tym system plików> `std::filesystem` zapewnia nowe `std::experimental::filesystem`i \<poprzednie , w tym eksperymentalne / system plików> zapewnia tylko stare eksperymentalne implementacji. Eksperymentalna implementacja zostanie usunięta w następnej wersji bibliotek z podziałem ABI.

<a name="note_G"></a>__G__ Obsługiwane przez kompilator wewnętrzne.

<a name="note_14"></a>__14__ Te funkcje C++ 17/20 są zawsze włączone, nawet wtedy, gdy [/std:c++14](../build/reference/std-specify-language-standard-version.md) (wartość domyślna) jest określona. Powodem jest albo dlatego, że funkcja została zaimplementowana przed **wprowadzeniem opcji /std** lub, ponieważ implementacja warunkowa była niepożądanie złożona.

<a name="note_17"></a>__17__ Te funkcje są włączone przez [/std:c++17](../build/reference/std-specify-language-standard-version.md) (lub [/std:c++latest)](../build/reference/std-specify-language-standard-version.md)opcja kompilatora.

<a name="note_20"></a>__20__ Te funkcje są włączone przez [/std:c++ostatni](../build/reference/std-specify-language-standard-version.md) kompilator opcji. Po zakończeniu implementacji języka C++20 zostanie dodana nowa opcja kompilatora **/std:c++20,** w ramach której będą również dostępne te funkcje.

<a name="note_byte"></a>__bajt__ `std::byte` jest włączony przez [/std:c++17](../build/reference/std-specify-language-standard-version.md) (lub [/std:c++latest),](../build/reference/std-specify-language-standard-version.md)ale ponieważ może kolidować z nagłówkami windows SDK w niektórych przypadkach, ma szczegółowe makro opt-out. Można go wyłączyć, `_HAS_STD_BYTE` definiując jako `0`.

<a name="note_C11"></a>__C11 ( c11 )__ Universal CRT zaimplementował części standardowej biblioteki C11, które są wymagane przez C++17, z wyjątkiem alternatywnych specyfikatorów konwersji C99 `strftime()` E/O, trybu wyłącznego C11 `fopen()` i C11 `aligned_alloc()`. Ten ostatni jest mało prawdopodobne, aby zostać `aligned_alloc()` zaimplementowane, ponieważ C11 `free()`określone w sposób, który jest niezgodny z implementacją firmy Microsoft: a mianowicie, które `free()` muszą być w stanie obsługiwać alokacje wysoce wyrównane.

<a name="note_rem"></a>__rem__ Funkcje usunięte po określeniu opcji kompilatora [/std:c++17](../build/reference/std-specify-language-standard-version.md) (lub [/std:c++latest).](../build/reference/std-specify-language-standard-version.md) Funkcje te można ponownie włączyć, aby ułatwić przejście do nowszych trybów `_HAS_FUNCTION_ALLOCATOR_SUPPORT` `_HAS_OLD_IOSTREAMS_MEMBERS`językowych `_HAS_UNEXPECTED`za pomocą tych makr: `_HAS_AUTO_PTR_ETC`, , i .

<a name="note_charconv"></a>__charconv__ `from_chars()` `to_chars()` i są dostępne dla liczby całkowitej. Oś czasu dla `from_chars()` zmiennoprzecinkowych i zmiennoprzecinkowych `to_chars()` jest następująca:

- VS 2017 15.7: `from_chars()` Całkowita `to_chars()`i .
- VS 2017 15.8: `from_chars()`Zmiennoprzecinka .
- VS 2017 15.9: `to_chars()` Przeciążenia zmiennoprzecinkowe dla najkrótszego miejsca dziesiętnego.
- VS 2019 16.0: `to_chars()` Przeciążenia zmiennoprzecinkowe dla najkrótszego hexu i precyzyjnego hexu.
- VS 2019 16.2: `to_chars()` Przeciążenia zmiennoprzecinkowe dla precyzyjnych stałych i precyzyjnych naukowych.
- VS 2019 16.4: Przeciążenie zmiennoprzecinkowe `to_chars()` dla precyzyjnego generała.

<a name ="note_parallel"></a>__równolegle__ Biblioteka algorytmów równoległych języka C++ 17 została ukończona. Complete nie oznacza, że każdy algorytm jest równoległy w każdym przypadku. Najważniejsze algorytmy zostały zrównoleglizowany i podpisy zasad wykonywania są dostarczane nawet wtedy, gdy algorytmy nie są równoległe. Centralny nagłówek wewnętrzny naszej implementacji, yvals_core.h, zawiera następujące "Analogowe uwagi algorytmów": C++ umożliwia implementację implementacji algorytmów równoległych jako wywołania algorytmów szeregowych. Ta implementacja równoległa kilka typowych wywołań algorytmu, ale nie wszystkie.

Następujące algorytmy są równoległe:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Następujące nie są obecnie równoległe:

- Brak zauważalnej poprawy wydajności równoległości na sprzęcie docelowym; wszystkie algorytmy, które jedynie kopiują lub permutują elementy bez gałęzi, są zazwyczaj ograniczone przepustowością pamięci:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Istnieje zamieszanie związane z wymaganiami dotyczącymi równoległości użytkowników; prawdopodobnie w powyższej kategorii tak:
  - `generate`, `generate_n`
- Efektywny równoległość podejrzewa, że jest nie do zakonywalny:
  - `partial_sort`, `partial_sort_copy`
- Jeszcze nie oceniono; równoległość może być wdrożona w przyszłym wydaniu i podejrzewa się, że jest korzystna:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)\
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)\
[Ulepszenia zgodności języka C++ w programie Visual Studio](cpp-conformance-improvements.md)\
[Co nowego w programie Visual C++ w programie Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ historia zmian od 2003 do 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Visual C++ Co nowego od 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[Blog zespołu języka C++](https://devblogs.microsoft.com/cppblog/)
