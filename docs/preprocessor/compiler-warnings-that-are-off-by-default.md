---
title: Domyślnie wyłączone ostrzeżenia kompilatora
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: d497886b22c7a90ab7cda47e46dc13daf297b192
ms.sourcegitcommit: b4572ffcc71e6bdb0ca23221f9476cfaf4528406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71314458"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Domyślnie wyłączone ostrzeżenia kompilatora

Kompilator obsługuje ostrzeżenia, które są domyślnie wyłączone, ponieważ większość deweloperów nie można ich używać. W niektórych przypadkach są one ostrzegane o wyborze stylistycznej lub o typowych Idiomy w starszym kodzie. Inne ostrzeżenia dotyczą korzystania z rozszerzenia Microsoft w języku. W innych przypadkach wskazują obszar, w którym programiści często wprowadzają błędne założenia, co może prowadzić do nieoczekiwanego lub niezdefiniowanego zachowania. Jeśli ta funkcja jest włączona, niektóre z tych ostrzeżeń mogą występować wiele razy w nagłówkach biblioteki. Biblioteki środowiska uruchomieniowego języka C C++ i biblioteki standardowe są przeznaczone do wysyłania ostrzeżeń tylko na poziomie ostrzeżenia [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Włącz ostrzeżenia, które są domyślnie wyłączone

Ostrzeżenia, które są zwykle wyłączone domyślnie, można włączyć przy użyciu jednej z następujących opcji:

- **ostrzeżenie #pragma (domyślnie:** *warning_number* **)**

   Określone ostrzeżenie (*warning_number*) jest włączone na jego domyślnym poziomie. Dokumentacja dla ostrzeżenia zawiera domyślny poziom ostrzeżeń.

- **Ostrzeżenie #pragma (** *warning_level* **:** *warning_number* **)**

   Określone ostrzeżenie (*warning_number*) jest włączone na określonym poziomie (*warning_level*).

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall`włącza wszystkie ostrzeżenia, które są domyślnie wyłączone. W przypadku użycia tej opcji można wyłączyć poszczególne ostrzeżenia przy użyciu opcji [/WD](../build/reference/compiler-option-warning-level.md) .

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Ta opcja włącza ostrzeżenie *nnnn* na poziomie *L*.

## <a name="warnings-that-are-off-by-default"></a>Ostrzeżenia, które są domyślnie wyłączone

Następujące ostrzeżenia są domyślnie wyłączone w programie Visual Studio 2015 i jego nowszych wersjach:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (poziom 4)|moduł wyliczający "*Identifier*" w przełączniku wyliczenia *"enum" nie*jest jawnie obsługiwany przez etykietę case|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (poziom 4)|moduł wyliczający "*Identifier*" w przełączniku wyliczenia *"enum" nie*jest obsługiwany|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (poziom 1) | "HRESULT" jest konwertowany na "bool"; Czy na pewno chcesz to zrobić? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (poziom 3)|"*operator*": niebezpieczna konwersja z "*type_of_expression*" na "*type_required*"|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (poziom 4)|"*Identyfikator*": konwersja z "*Type1*" na "*Type2*", możliwa utrata danych|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (poziom 4)|"*operator*": konwersja z "*Type1*" na "*Type2*", możliwa utrata danych|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (poziom 4)|"*Function*": nie podaną prototypu funkcji: konwertowanie "()" na "(void)"|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (poziom 4)|"*Function*": funkcja członkowska nie przesłania żadnej wirtualnej funkcji składowej klasy bazowej|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (poziom 1)|"*virtual_function*": Brak dostępnego przesłonięcia dla wirtualnej funkcji składowej z klasy podstawowej "*Class*"; Funkcja jest ukryta|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (poziom 3)|"*Class*": Klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (poziom 4)|"*Function*": Brak dostępnego przesłonięcia dla wirtualnej funkcji składowej z elementu Base "*Type*"; Funkcja jest ukryta|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (poziom 3)|"*operator*": niezgodność stałej ze znakiem/bez znaku|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (poziom 4)|użyto niestandardowego rozszerzenia: "*var*": Zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (poziom 4)|"*operator*": wyrażenie ma zawsze wartość false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (poziom 4)|"*Type*": użycie niezdefiniowanego typu wykryte w metadanych CLR — użycie tego typu może prowadzić do wyjątku czasu wykonywania|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (poziom 1)|zmiana zachowania: wywołano*funkcję "Function*", ale operator składowej został wywołany w poprzednich wersjach|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (poziom 1)|zmiana zachowania: wywołano "*member1*" zamiast "*member2*"|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this': używany na liście inicjatora bazowego elementu członkowskiego|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (poziom 4)|"*Action*": konwersja z "*type_1*" na "*type_2*", niezgodność ze znakiem/bez znaku|
|C4370 (poziom 3)|układ klasy zmienił się z poprzedniej wersji kompilatora ze względu na lepsze pakowanie|
|[C4371](../error-messages/compiler-warnings/c4371.md) (poziom 3)|"*ClassName*": układ klasy może ulec zmianie z poprzedniej wersji kompilatora, ze względu na lepsze pakowanie składowej "*member*"|
|C4388 (poziom 4)|niezgodność ze znakiem/bez znaku|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (poziom 2)|"*Function*": Sygnatura funkcji zawiera typ "*Type*"; C++ obiekty nie są bezpieczne do przekazania między czystym kodem a mieszanym lub natywnym|
|C4426 (poziom 1)|flagi optymalizacji zostały zmienione po dołączeniu nagłówka, może to być spowodowane #pragma optymalizacją () <sup>14,1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (poziom 4)|"*Class1*": Układ obiektu w obszarze/VD2 zmieni zmieni się ze względu na wirtualną podstawową " *'klasa*"|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (poziom 4)|dynamic_cast z wirtualnej bazy "*Class1*" do " *'klasa*" może zakończyć się niepowodzeniem w niektórych kontekstach|
|C4444 (poziom 3)|'__unaligned' najwyższego poziomu nie jest zaimplementowany w tym kontekście|
|[C4464](../error-messages/compiler-warnings/c4464.md) (poziom 4)|względna ścieżka dołączania zawiera ".."|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (poziom 4)|Deklaracja do przodu wyliczenia nienależącego do zakresu musi mieć typ podstawowy (założono int) <sup>uprawnienie</sup>|
|C4472 (poziom 1)|element "*Identifier*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (Private/Public), aby zadeklarować zarządzane Wyliczenie|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (poziom 4)|"*Function*": funkcja wbudowana, do której nie istnieje odwołanie, została usunięta|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (poziom 4)|"type name": nazwa typu przekracza limit meta danych znaków "*Limit*"|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (poziom 1)|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (poziom 1)|wywołanie funkcji przed przecinkiem, brak listy argumentów|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (poziom 1)|operator "*operator*": przed przecinkiem nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (poziom 1)|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (poziom 1)|"*operator1*": operator przed przecinkiem nie ma żadnego wpływu; Czy chodziło o "*operator2*"?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (poziom 1)|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (poziom 3)|"__assume" zawiera efekt "*efekt*"|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (poziom 4)|informacyjne: semantyka catch (...) zmieniła się C++ od Visual 7,1; wyjątki strukturalne (SEH) nie są już przechwytywane|
|C4574 (poziom 4)|"*Identyfikator*" jest zdefiniowany jako "0": Czy chodziło o użycie "#if *Identyfikator*"?|
|C4577 (poziom 1)|użyto "noexcept" bez określonego trybu obsługi wyjątków; zakończenie przy wyjątku nie jest gwarantowane. Określ/EHsc|
|C4582 (poziom 4)|"*Type*": Konstruktor nie jest wywoływany niejawnie|
|C4583 (poziom 4)|"*Type*": destruktor nie jest wywoływany niejawnie|
|C4587 (poziom 1)|"*anonymous_structure*": zmiana zachowania: Konstruktor nie jest już wywoływany niejawnie|
|C4588 (poziom 1)|"*anonymous_structure*": zmiana zachowania: destruktor nie jest już wywoływany niejawnie|
|[C4596](../error-messages/compiler-warnings/c4596.md) (poziom 4)|"*Identyfikator*": niedozwolona kwalifikowana nazwa w deklaracji składowej <sup>14,3</sup> <sup>uprawnienie</sup>|
|C4598 (poziom 1 i 3)|*nagłówek*"#include" ": *numer* numeru nagłówka w prekompilowanym nagłówku nie jest zgodny z bieżącą kompilacją w tym miejscu <sup>14,3</sup>|
|C4599 (poziom 3)|" *ścieżka*opcji": *numer* argumentu wiersza polecenia nie pasuje do wstępnie skompilowanego nagłówka <sup>14,3</sup>|
|C4605 (poziom 1)|"/D*makro*" określone w bieżącym wierszu polecenia, ale nie zostało określone podczas kompilowania prekompilowanego nagłówka|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (poziom 3)|"*union_member*" został już zainicjowany przez inny element członkowski Unii na liście inicjatora "*union_member*" <sup>uprawnienie</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (poziom 3)|Ostrzeżenie #pragma: Brak ostrzeżenia numer "*numer*"|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (poziom 4)|„klasa pochodna”: nie można wygenerować konstruktora domyślnego, ponieważ domyślny konstruktor klasy bazowej jest niedostępny|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (poziom 4)|„klasa pochodna”: nie można wygenerować konstruktora kopiowania, ponieważ konstruktor kopiowania klasy bazowej jest niedostępny|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (poziom 4)|„klasa pochodna”: nie można wygenerować operatora przypisania, ponieważ operator przypisania klasy bazowej jest niedostępny|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (poziom 1)|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków "*ungraph*" nie jest interpretowana jako alternatywny token dla "*char*"|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (poziom 3)|"*wystąpienie*": konstrukcja lokalnego obiektu statycznego nie jest bezpieczna wątkowo|
| C4643 (poziom 4) | Deklarowanie "*Identyfikator*" w przestrzeni nazw std nie jest dozwolone przez C++ Standard. <sup>15.8</sup> |
|C4647 (poziom 3)|zmiana zachowania: __is_pod (*Typ*) ma inną wartość w poprzednich wersjach|
|C4654 (poziom 4)|Kod umieszczony przed dołączeniem do wiersza prekompilowanego nagłówka zostanie zignorowany. Dodaj kod do prekompilowanego nagłówka. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (poziom 4)|"*symbol*" nie jest zdefiniowany jako makro preprocesora, zastępując znakiem "0" dla*dyrektywy*"|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (poziom 4)|"*symbol*": brak określonego atrybutu parametru kierunkowego, wartość domyślna to [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (poziom 3)|"*Typ zdefiniowany przez użytkownika*": możliwa zmiana w zachowaniu, zmiana w Konwencji WYWOŁYWANIA powrotu UDT|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (poziom 1)|"*Function*": Sygnatura nieprywatnej składowej zawiera natywny prywatny Typ zestawu "*NATIVE_TYPE*"|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (poziom 4)|"*Function*": funkcja nie została wbudowana|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (poziom 3)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp elementu "*Expression*" podlega/volatile:\<ustawienia&#124;ISO MS >. Rozważ użycie funkcji wewnętrznych __iso_volatile_load/Store|
|C4749 (poziom 4)|warunkowo obsługiwane: makro OffsetOf zastosowany do typu układu niestandardowym "*Type*"|
|C4767 (poziom 4)|Nazwa sekcji "*symbol*" jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|C4768 (poziom 3)|atrybuty __declspec przed specyfikacją konsolidacji są ignorowane|
|C4774 (poziom 4)|"*String*": ciąg formatu oczekiwany w *numerze* argumentu nie jest literałem ciągu|
|C4777 (poziom 4)|"*Function*": ciąg formatu "*String*" wymaga argumentu typu "*Type1*", ale wariadyczne argument *Number* ma typ "*Type2*"|
|C4786 (poziom 3)|"*symbol*": Nazwa obiektu została obcięta do znaków "*Number*" w informacjach o debugowaniu|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (poziom 4) | Niejawna konwersja z*typu "Type*" na typ bool. Możliwa utrata informacji <sup>16,0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (poziom 4)|dopełnienie bajtów "*Bytes*" po konstrukcji "*MEMBER_NAME*"|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (poziom 1) | "*member*": Funkcja składowa klasy lokalnej nie ma treści |
|C4826 (poziom 2)|Konwersja z "*Type1*" na "*Type2*" jest rozszerzona. Może to spowodować nieoczekiwane zachowanie w czasie wykonywania.|
|C4837 (poziom 4)|Wykryto trójznaków: "?? *znak*"zastąpiony"*znakiem*"|
|C4841 (poziom 4)|użyto niestandardowego rozszerzenia: wyznaczenie złożonego elementu członkowskiego użytego w makro OffsetOf|
|C4842 (poziom 4)|wynik elementu "makro OffsetOf" zastosowanego do typu używającego wielu dziedziczeń nie jest gwarantowany spójny między wydaniami kompilatora|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (poziom 4)|Kompilator "_File_(*line_number*)" nie może wymusić kolejności oceny od lewej do prawej na liście inicjalizacji z nawiasami klamrowymi|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (poziom 1)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (poziom 1)|literał ciągu rzutowany na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (poziom 1)|"*deklarator*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzenią nazw|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (poziom 1)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (poziom 4)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (poziom 1)|użyto operatora reinterpret_cast między powiązanymi klasami: "*Class1*" i " *'klasa*"|
|C4962|"*Function*": optymalizacje profilowane zostały wyłączone, ponieważ optymalizacje powodowały niespójność danych profilowych|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (poziom 4)|"*symbol*": Specyfikacja wyjątku nie jest zgodna z poprzednią deklaracją|
|C4987 (poziom 4)|użyto rozszerzenia niestandardowego: 'throw (...)'|
|C4988 (poziom 4)|"*symbol*": zmienna zadeklarowana poza zakresem klasy/funkcji|
|C5022|"*Type*": określono wiele konstruktorów przenoszenia|
|C5023|"*Type*": określono wiele operatorów przypisania przenoszenia|
|C5024 (poziom 4)|"*Type*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5025 (poziom 4)|"*Type*": operator przypisania przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5026 (poziom 1 i 4)|"*Type*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5027 (poziom 1 i 4)|"*Type*": operator przypisania przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5029 (poziom 4)|użyto niestandardowego rozszerzenia: atrybuty wyrównania w C++ zastosowaniu do zmiennych, elementów członkowskich danych i typów tagów|
|C5031 (poziom 4)|Ostrzeżenie #pragma (pop): dopuszczalna niezgodność, usuwanie stan ostrzeżenia wypychane w innym pliku <sup>14,1</sup>|
|C5032 (poziom 4)|Wykryto Ostrzeżenie #pragma (push) bez odpowiadającego #pragma ostrzeżenie (pop) <sup>14,1</sup>|
|C5034|Użycie wewnętrznego elementu "*wewnętrzna*" powoduje skompilowanie *funkcji* funkcji jako kodu gościa <sup>15,3</sup>|
|C5035|Użycie funkcji "*Feature*" powoduje skompilowanie *funkcji* funkcji jako kodu gościa <sup>15,3</sup>|
|C5036 (poziom 1)|Konwersja wskaźnika funkcji typu VarArgs podczas kompilowania z/Hybrid: x86arm64 "*Type1*" do "*Type2*" <sup>15,3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (poziom 4)|element członkowski danych "*member1*" zostanie zainicjowany po elemencie członkowskim danych "*member2*" <sup>15,3</sup>|
|C5039 (poziom 4)|"*Function*": wskaźnik lub odwołanie do potencjalnie wyrzucanej funkcji, która została przeniesiona do funkcji extern C w EHC. Niezdefiniowane zachowanie może wystąpić, jeśli ta funkcja zgłosi wyjątek. <sup>15.5</sup>|
|C5042 (poziom 3)|"*Function*": deklaracje funkcji w zakresie bloku nie mogą być określone jako "inline" w standardzie C++; Usuń specyfikator "inline" <sup>15,5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Kompilator wstawi środki zaradcze Spectre na potrzeby ładowania pamięci, jeśli przełącznik/Qspectre określony <sup>15,7</sup>|

<sup>14,1</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2015 Update 1.\\ <sup>14,3</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2015 Update 3.\\ <sup>15,3</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2017 w wersji 15,3.\\ <sup>15,5</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2017 w wersji 15,5.\\ <sup>15,7</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2017 w wersji 15,7.\\ <sup>15,8</sup> to ostrzeżenie jest dostępne począwszy od programu Visual Studio 2017 w wersji 15,8.\\ <sup>16,0</sup> to ostrzeżenie jest dostępne od wersji Visual Studio 2019 RTM.\\ <sup>Uprawnienie</sup> To ostrzeżenie jest wyłączone, chyba że opcja kompilatora [/permissive-](../build/reference/permissive-standards-conformance.md) jest ustawiona.

## <a name="warnings-off-by-default-in-earlier-versions"></a>Ostrzeżenia są domyślnie wyłączone we wcześniejszych wersjach

Te ostrzeżenia były domyślnie wyłączone w wersjach kompilatora przed Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (poziom 2)|"*Conversion*": obcinanie z "*Type1*" do "*Type2*"|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (poziom 1)|"*zmienna*": obcinanie wskaźnika z "*Type*" do "*Type*"|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (poziom 1)|"*Operation*": konwersja z "*Type1*" na "*Type2*" o większym rozmiarze|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (poziom 1)|"*operator*": zero rozszerzające wartość "*Type1*" na "*Type2*" o większym rozmiarze|

To ostrzeżenie zostało domyślnie wyłączone w wersjach kompilatora przed Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (poziom 4)|brak specyfikatora typu — zakładany int. Uwaga: Język C nie obsługuje już domyślnego-int|

## <a name="see-also"></a>Zobacz także

[ostrzeżenie](../preprocessor/warning.md)
