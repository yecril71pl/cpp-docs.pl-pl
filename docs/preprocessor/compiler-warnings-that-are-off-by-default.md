---
title: Ostrzeżenia kompilatora, które są domyślnie wyłączone | Dokumentacja firmy Microsoft
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b5a4551387716c81766ae99759f8188410497be
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466336"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Ostrzeżenia kompilatora, które są domyślnie wyłączone
Kompilator zawiera ostrzeżenia, które są domyślnie wyłączone, ponieważ większość programistów nie chce ich widzieć. W niektórych przypadkach ich reprezentuje wybór stylistyczne, są typowe idiomy starszego kodu lub korzystać z rozszerzeń firmy Microsoft dla języka. W innych przypadkach wskazują obszar, w którym programistów często wprowadzać nieprawidłowe wartości domyślne, które mogą prowadzić do nieoczekiwanych lub niezdefiniowane zachowanie. Niektóre z tych ostrzeżeń mogą być bardzo hałas w nagłówkach biblioteki. Biblioteki środowiska uruchomieniowego C i C++ standardowych bibliotek, które są przeznaczone do emitować nie ostrzeżeń tylko na poziomie ostrzeżenia [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Włącz ostrzeżenia, które są domyślnie wyłączone

Można włączyć ostrzeżeń, które są normalnie wyłączone domyślnie przy użyciu jednej z następujących opcji:

- **Ostrzeżenie #pragma (domyślne:** *warning_number* **)**

   Określone ostrzeżenie (*warning_number*) jest włączona na poziomie domyślnym. Dokumentacja dla ostrzeżenia zawiera domyślny poziom ostrzeżeń.

- **Ostrzeżenie #pragma (** *warning_level* **:** *warning_number* **)**

   Określone ostrzeżenie (*warning_number*) jest włączone na określonym poziomie (*warning_level*).

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` Włącza wszystkie ostrzeżenia, które są domyślnie wyłączone. Jeśli używasz tej opcji, możesz wyłączyć poszczególne ostrzeżenia, za pomocą [/wd](../build/reference/compiler-option-warning-level.md) opcji.

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Dzięki temu ostrzeżenie *nnnn* na poziomie *L*.

## <a name="warnings-that-are-off-by-default"></a>Ostrzeżenia, które są domyślnie wyłączone

Następujące ostrzeżenia są domyślnie wyłączone w programie Visual Studio 2015 i nowszych wersjach:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (poziom 4)|Moduł wyliczający "*identyfikator*'w przełączniku enum'*wyliczenie*" nie jest jawnie obsługiwany przez etykietę case|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (poziom 4)|Moduł wyliczający "*identyfikator*'w przełączniku enum'*wyliczenie*" nie jest obsługiwany|
|C4191 (poziom 3)|"*operator*": niebezpieczna konwersja z "*type_of_expression*"to"*type_required*"|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (poziom 4)|"*identyfikator*': konwersja z"*type1*"to"*type2*", możliwa utrata danych|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (poziom 4)|"*operator*': konwersja z"*type1*"to"*type2*", możliwa utrata danych|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (poziom 4)|"*funkcja*": nie podano prototypu funkcji: konwertowanie '()"na"(void)"|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (poziom 4)|"*funkcja*": funkcja składowa nie zastępuje żadnej funkcji składowej wirtualnej klasy bazowej|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (poziom 1)|"*virtual_function*': niedostępne zastąpienie dla funkcji wirtualnej składowej z podstawowej"*klasy*'; funkcja jest ukryta|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (poziom 3)|"*klasy*": klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (poziom 4)|"*funkcji*': niedostępne zastąpienie dla funkcji wirtualnej składowej z podstawowej"*typu*'; funkcja jest ukryta|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (poziom 3)|"*operator*": niezgodność stałej bez znaku/ujemnej|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (poziom 4)|użyto niestandardowego rozszerzenia: "*var*": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (poziom 4)|"*operator*": wyrażenie ma zawsze wartość false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (poziom 4)|"*typu*": użycie niezdefiniowanego typu wykryte w meta danych CLR — stosowanie tego typu może prowadzić do wyjątku czasu wykonywania|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (poziom 1)|Zmiana zachowania: "*funkcja*" o nazwie, ale operator składowej został wywołany w poprzednich wersjach|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (poziom 1)|Zmiana zachowania: "*Członek1*"o nazwie zamiast"*członek2*"|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this': używany na liście inicjatora bazowego elementu członkowskiego|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (poziom 4)|"*akcji*': konwersja z"*typ_1*"to"*typ_2*', niezgodność ze znakiem/bez znaku|
|C4370 (poziom 3)|układ klasy zmienił się z poprzedniej wersji kompilatora ze względu na lepsze pakowanie|
|[C4371](../error-messages/compiler-warnings/c4371.md) (poziom 3)|"*classname*": układ klasy mógł się zmienić z poprzedniej wersji kompilatora ze względu na lepsze pakowanie składowej '*elementu członkowskiego*"|
|C4388 (poziom 4)|niezgodność ze znakiem/bez znaku|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (poziom 2)|"*funkcja*': podpis funkcji podpis zawiera typ"*typu*'; Obiekty C++ są bezpieczne przekazywanie między kodem czystym i mieszanym lub macierzystym|
|C4426 (poziom 1)|flagi optymalizacji zmieniły się po dołączeniu nagłówka, może być #pragma Optimize() <sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (poziom 4)|"*klasa1*": układ obiektu pod/vd2 zmieni się z powodu bazy wirtualnej "*klasa2*"|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (poziom 4)|dynamic_cast z bazy wirtualnej "*klasa1*"to"*klasa2*" może nie działać w niektórych kontekstach|
|C4444 (poziom 3)|'__unaligned' najwyższego poziomu nie jest zaimplementowany w tym kontekście|
|[C4464](../error-messages/compiler-warnings/c4464.md) (poziom 4)|względna ścieżka dołączania zawiera ".."|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (poziom 4)|Deklaracja zapowiadająca wyliczenia nieobjętego zakresem musi mieć podstawowy typ (zakładany jest int) <sup>jako trwałą</sup>|
|C4472 (poziom 1)|"*identyfikator*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (private/public), aby zadeklarować wyliczenie zarządzane|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (poziom 4)|"*funkcja*': Usunięto nieużywaną funkcję wbudowaną|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (poziom 4)|'Nazwa typu': Nazwa typu przekracza limit meta-data "*limit*" znaków|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (poziom 1)|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (poziom 1)|wywołanie funkcji przed przecinkiem, brak listy argumentów|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (poziom 1)|"*operator*": operator przed przecinkiem nie przynosi efektu; oczekiwany operator, który przynosi efekt|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (poziom 1)|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (poziom 1)|"*operator1*": operator przed przecinkiem nie ma wpływu; czy chodziło Ci "*operator2*"?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (poziom 1)|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (poziom 3)|"__assume" zawiera efekt '*efekt*"|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (poziom 4)|Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane|
|C4574 (poziom 4)|"*identyfikator*'jest zdefiniowane jako ' 0': czy zamierzałeś użyć ' #if *identyfikator*"?|
|C4577 (poziom 1)|"noexcept" używane z nie trybu; obsługi wyjątków Zakończenie na wyjątek nie jest gwarantowana. Określ/ehsc|
|C4582 (poziom 4)|"*typu*": Konstruktor nie jest wywoływany niejawnie|
|C4583 (poziom 4)|"*typu*": destruktor nie jest wywoływany niejawnie|
|C4587 (poziom 1)|"*anonymous_structure*": Zmiana zachowania: Konstruktor nie jest już niejawnie jest wywoływany.|
|C4588 (poziom 1)|"*anonymous_structure*": Zmiana zachowania: destruktor jest wywoływany nie jest już niejawnie|
|C4596 (poziom 4)|"*identyfikator*": niedozwolona kwalifikowana nazwa w deklaracji składowej <sup>14,3</sup> <sup>jako trwałą</sup>|
|C4598 (poziom 1 i poziom 3)|"#include"*nagłówka*"": numer nagłówka *numer* WE prekompilowanym nagłówku jest niezgodna bieżącej kompilacji w tej pozycji <sup>14,3</sup>|
|C4599 (poziom 3)|"*opcji* *ścieżki*": numer argumentu wiersza polecenia *numer* jest niezgodna z wstępnie skompilowanym nagłówkiem <sup>14,3</sup>|
|C4605 (poziom 1)|"/D *— makro*" określona w bieżącym wierszu polecenia, ale nie określono skompilowanych prekompilowanego nagłówka|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (poziom 3)|"*union_member*"został już zainicjowany przez inny element członkowski Unii na liście inicjatora"*union_member*" <sup>jako trwałą</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (poziom 3)|Ostrzeżenie #pragma: Brak ma numeru ostrzeżenia '*numer*"|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (poziom 4)|„klasa pochodna”: nie można wygenerować konstruktora domyślnego, ponieważ domyślny konstruktor klasy bazowej jest niedostępny|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (poziom 4)|„klasa pochodna”: nie można wygenerować konstruktora kopiowania, ponieważ konstruktor kopiowania klasy bazowej jest niedostępny|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (poziom 4)|„klasa pochodna”: nie można wygenerować operatora przypisania, ponieważ operator przypisania klasy bazowej jest niedostępny|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (poziom 1)|dwuznaki nieobsługiwane z -Ze. Znak sekwencji "*dwuznak*'nie jest interpretowana jako alternatywny token dla'*char*"|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (poziom 3)|"*wystąpienia*': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna dla wątków|
|C4647 (poziom 3)|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach|
|C4654 (poziom 4)|Kod umieszczony przed elementem obejmują wstępnie skompilowanego nagłówka wiersza zostaną zignorowane. Dodaj kod do wstępnie skompilowanego nagłówka. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (poziom 4)|"*symbol*'nie jest zdefiniowany jako makro preprocesora, zastępowanie przez '0' dla'*dyrektywy*"|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (poziom 4)|"*symbol*": nie określono atrybutu kierunkowego parametru, domyślnie na [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (poziom 3)|"*typu zdefiniowanego przez użytkownika*': możliwe zmiany w zachowaniu, zmiana UDT zwracają konwencji wywoływania|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (poziom 1)|"*funkcja*': podpis z nieprywatnej składowej zawiera natywny prywatny typ zestawu"*native_type*"|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (poziom 4)|"*funkcja*": funkcja niewbudowana|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (poziom 3)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp "*wyrażenie*" podlega/volatile:\<iso&#124;ms >; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store funkcje wewnętrzne|
|C4749 (poziom 4)|warunkowo obsługiwane: makro offsetof zastosowano do typu nienależące niestandardowym układzie "*typu*"|
|C4767 (poziom 4)|Nazwa sekcji '*symbol*"jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|C4768 (poziom 3)|atrybuty __declspec przed specyfikacją konsolidacji są ignorowane.|
|C4774 (poziom 4)|"*ciąg*": ciąg oczekiwany w argumencie formatu *numer* nie jest ciągiem literału|
|C4777 (poziom 4)|"*— funkcja*": ciąg formatu "*ciąg*"wymaga argumentu typu"*type1*", ale ze zmienną liczbą argumentów *numer* ma typ "*type2*"|
|C4786 (poziom 3)|"*symbol*': Nazwa obiektu została obcięta do '*numer*' znaków w informacjach debugowania|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (poziom 4)|"*bajtów*"bajtów dopełnienie dodane po konstrukcji"*member_name*"|
|C4826 (poziom 2)|Konwersja z "*type1*"to"*type2*' jest rozszerzona o znak. Może to spowodować nieoczekiwane zachowanie.|
|C4837 (poziom 4)|Wykryto trójznak: "? *znak*"zastępuje"*znak*"|
|C4841 (poziom 4)|użyto niestandardowego rozszerzenia: desygnator złożonej składowej użyty w makrze offsetof|
|C4842 (poziom 4)|nie gwarantuje wynik makra "offsetof" zastosować do typu używającego wielu dziedziczeń będzie spójny między wydaniami kompilatora|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (poziom 4)|"_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej w listy inicjowania w nawiasach|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (poziom 1)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (poziom 1)|literał ciągu rzutowany na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (poziom 1)|"*deklaratora*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (poziom 1)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (poziom 4)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (poziom 1)|reinterpret_cast używane między pokrewnymi klasami: '*klasa1*"i"*klasa2*"|
|C4962|"*funkcja*': optymalizacje profilowane wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (poziom 4)|"*symbol*': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją|
|C4987 (poziom 4)|użyto rozszerzenia niestandardowego: 'throw (...)'|
|C4988 (poziom 4)|"*symbol*": Zmienna zadeklarowana poza zakresem klasy/funkcji|
|C5022|"*typu*": określono wiele konstruktorów przenoszenia|
|C5023|"*typu*": określono wiele operatorów przypisania przenoszenia|
|C5024 (poziom 4)|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5025 (poziom 4)|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|C5026 (poziom 1 i 4)|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5027 (poziom 1 i 4)|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|C5029 (poziom 4)|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, składowych danych i tylko dla typów tagów|
|C5031 (poziom 4)|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu <sup>14.1</sup>|
|C5032 (poziom 4)|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop) <sup>14.1</sup>|
|C5034|Użyj wewnętrznych "*wewnętrzne*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa <sup>15.3</sup>|
|C5035|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa <sup>15.3</sup>|
|C5036 (poziom 1)|Konwersja wskaźnika funkcji typu varargs podczas kompilowania za pomocą /hybrid:x86arm64 "*type1*"to"*type2*" <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (poziom 4)|element członkowski danych "*Członek1*"zostanie zainicjowany po element członkowski danych"*członek2*" <sup>15.3</sup>|
|C5039 (poziom 4)|"*funkcja*": wskaźnik lub odwołanie do funkcji potencjalnie zgłaszającej wyjątek przekazano do funkcji extern języka C w ramach - EHc. Niezdefiniowane zachowanie może wystąpić, jeśli ta funkcja zgłosi wyjątek. <sup>wersji 15.5</sup>|
|C5042 (poziom 3)|"*funkcja*": deklaracje funkcji w zakresie bloku nie może być określone jako "inline" w standardzie języka C++; Usuń specyfikator "inline" <sup>15.5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Kompilator wstawi krokami zaradczymi dla luki środki zaradcze w przypadku obciążenia pamięci, jeśli zostanie określony przełącznik/qspectre <sup>wersji 15.7</sup>|

<sup>14.1</sup> to ostrzeżenie jest dostępna, począwszy od programu Visual Studio 2015 Update 1.  
<sup>14,3</sup> to ostrzeżenie jest dostępna, począwszy od programu Visual Studio 2015 Update 3.  
<sup>15.3</sup> to ostrzeżenie jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.3.  
<sup>15.5</sup> to ostrzeżenie jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.5.  
<sup>15.7</sup> to ostrzeżenie jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.7.  
<sup>Jako trwałą</sup> to ostrzeżenie jest wyłączone, chyba że [/ permissive-](../build/reference/permissive-standards-conformance.md) ustawiono opcję kompilatora.  

## <a name="warnings-off-by-default-in-earlier-versions"></a>Ostrzeżenia wyłączone domyślnie we wcześniejszych wersjach

Ostrzeżenia te zostały wyłączone domyślnie wersji kompilatora przed Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (poziom 2)|"*konwersji*': obcinanie z '*type1*"to"*type2*"|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (poziom 1)|"*zmiennej*': obcinanie wskaźnika z"*typu*"to"*typu*"|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (poziom 1)|"*operacji*': konwersja z"*type1*"to"*type2*' o większym rozmiarze|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (poziom 1)|"*operator*": zero rozszerzanie "*type1*"to"*type2*' o większym rozmiarze|

To ostrzeżenie zostało wyłączone domyślnie wersji kompilatora przed Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (poziom 4)|brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnego int|

## <a name="see-also"></a>Zobacz też

[ostrzeżenie](../preprocessor/warning.md)