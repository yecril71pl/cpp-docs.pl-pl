---
title: "Są domyślnie wyłączone ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: cpp-tools
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1dec9728679629f25ddbea93956fd25d9b29ef59
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Domyślnie wyłączone ostrzeżenia kompilatora

Kompilator zawiera ostrzeżenia, które są domyślnie wyłączone, ponieważ większość użytkowników nie chce ich widzieć. Możesz jednak włączyć te ostrzeżenia przy użyciu jednej z następujących opcji.

`#pragma warning(default : warning_number )`  
Ostrzeżenie określony (`warning_number`) jest włączona na poziomie domyślnej. Dokumentacja dla ostrzeżenia zawiera domyślny poziom ostrzeżeń.

`#pragma warning( warning_level : warning_number )`  
Ostrzeżenie określony (`warning_number`) jest włączona na określonym poziomie (`warning_level`).

[/ Wall](../build/reference/compiler-option-warning-level.md)  
**/ Ścian** włącza wszystkie ostrzeżenia, które są domyślnie wyłączone.

Następujące ostrzeżenia są domyślnie wyłączone.

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (poziom 4)|moduł wyliczający 'identyfikator' w przełączniku enum 'wyliczenie' nie jest jawnie obsługiwany przez etykietę case|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (poziom 4)|moduł wyliczający 'identyfikator' w przełączniku enum 'wyliczenie' nie jest jawnie obsługiwany|
|C4191 (poziom 3)|'operator/operacja': niebezpieczna konwersja z 'typ wyrażenia' na 'typ wymagany'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (poziom 4)|'identyfikator': konwersja z 'typ1' na 'typ2', możliwa utrata danych|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (poziom 4)|'operator': konwersja z 'typ1' na 'typ2', możliwa utrata danych|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (poziom 4)|'funkcja': nie podano prototypu funkcji: konwertowanie '()' na '(void)'|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (poziom 4)|'funkcja': funkcja elementu członkowskiego nie zastępuje żadnej funkcji wirtualnego elementu członkowskiego klasy podstawowej|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (poziom 1)|'virtual_function': niedostępne zastąpienie dla funkcji wirtualnego elementu członkowskiego z klasy podstawowej 'class'; funkcja jest ukryta|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (poziom 3)|'class': klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (poziom 4)|'funkcja': niedostępne zastąpienie dla funkcji wirtualnego elementu członkowskiego z typu podstawowego 'type'; funkcja jest ukryta|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (poziom 3)|'operator': niezgodność stałej bez znaku/ujemnej|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (poziom 4)|użyte rozszerzenie niestandardowe: 'var' : zmienna sterowania pętlą zadeklarowana w pętli for jest używana poza zakresem pętli for|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (poziom 4)|'operator': wyrażenie ma zawsze wartość false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (poziom 4)|'typ' : użycie niezdefiniowanego typu wykryte w metadanych CLR — stosowanie tego typu może prowadzić do wyjątku czasu wykonywania|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (poziom 1)|zmiana zachowania: wywołano funkcję 'funkcja', ale operator elementu członkowskiego wywołano w poprzednich wersjach|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (poziom 1)|zmiana zachowania: wywołano element członkowski 'członek1' zamiast 'członek2'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this': używany na liście inicjatora bazowego elementu członkowskiego|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (poziom 4)|'działanie': konwersja z 'typ_1' na 'typ_2', niezgodność ze znakiem/bez znaku|
|C4370 (poziom 3)|układ klasy zmienił się z poprzedniej wersji kompilatora ze względu na lepsze pakowanie|
|C4371 (poziom 3)|układ klasy mógł się zmienić z poprzedniej wersji kompilatora ze względu na lepsze pakowanie elementu członkowskiego 'członek'|
|C4388 (poziom 4)|niezgodność ze znakiem/bez znaku|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (poziom 2)|'funkcja': podpis funkcji podpis zawiera typ 'typ'; nie jest bezpieczne przekazywanie obiektów C++ między kodem czystym i mieszanym lub macierzystym|
|C4426 (poziom 1)|flagi optymalizacji zmieniły się po dołączeniu nagłówka, może #pragma Optimize()|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (poziom 4)|'klasa1': Układ obiektu pod /vd2 zmieni się ze względu na wirtualną klasę podstawową 'klasa2'|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (poziom 4)|dynamic_cast z podstawowej klasy wirtualnej 'klasa1' na 'klasa2' może nie działać w niektórych sytuacjach|
|C4444 (poziom 3)|'__unaligned' najwyższego poziomu nie jest zaimplementowany w tym kontekście|
|C4464 (poziom 4)|względna ścieżka dołączania zawiera ".."|
|C4472 (poziom 1)|'identyfikator' to wyliczenie macierzyste: dodaj specyfikator dostępu (private/public), aby zadeklarować wyliczenie zarządzane|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (poziom 4)|'funkcja': usunięto nieużywaną funkcję wbudowaną|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (poziom 4)|'nazwa typu': nazwa typu przekracza limit metadanych znaków 'limit'|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (poziom 1)|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (poziom 1)|wywołanie funkcji przed przecinkiem, brak listy argumentów|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (poziom 1)|'operator': operator przed przecinkiem nie przynosi efektu; oczekiwany operator, który przynosi efekt|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (poziom 1)|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (poziom 1)|'operator': operator przed przecinkiem nie przynosi efektu; czy 'operator' był zamierzony?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (poziom 1)|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (poziom 3)|'__assume' zawiera efekt 'efekt'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (poziom 4)|Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane|
|C4574 (poziom 4)|'identyfikator' jest definiowany jako '0': czy chodziło o 'identyfikator #if'?|
|C4582 (poziom 4)|"*typu*": Konstruktor nie jest wywoływany niejawnie|
|C4583 (poziom 4)|"*typu*": destruktor nie jest wywoływany niejawnie|
|C4587 (poziom 1)|"*anonymous_structure*": Zmiana zachowania: konstruktor jest nie już wywoływany niejawnie|
|C4588 (poziom 1)|"*anonymous_structure*": Zmiana zachowania: destruktor jest nie już wywoływany niejawnie|
|C4598 (poziom 1 i poziom 3)|"#include"*nagłówka*"": numer nagłówka *numer* w prekompilowanego nagłówka nie odpowiada bieżącej kompilacji na tej pozycji|
|C4599 (poziom 3)|"*opcji* *ścieżki*": numer argumentu wiersza polecenia *numer* nie pasuje do wstępnie skompilowanym nagłówkiem|
|C4605 (poziom 1)|"/D*makro*" określony w bieżącym wierszu polecenia, ale nie została określona, gdy został skompilowany prekompilowanego nagłówka|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (poziom 3)|ostrzeżenie #pragma: nie ma numeru ostrzeżenia 'numer'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (poziom 4)|'klasa pochodna': nie można wygenerować konstruktora domyślnego, ponieważ domyślny konstruktor klasy podstawowej jest niedostępny|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (poziom 4)|'klasa pochodna': nie można wygenerować konstruktora kopiowania, ponieważ konstruktor kopiowania klasy podstawowej jest niedostępny|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (poziom 4)|'klasa pochodna': nie można wygenerować operatora przypisania, ponieważ operator przypisania klasy podstawowej jest niedostępny|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (poziom 1)|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków 'dwuznak' nie jest interpretowana jako alternatywny token dla 'char'|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (poziom 3)|'instancja': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna pod względem wątków|
|C4647 (poziom 3)|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach|
|C4654 (poziom 4)|Kod umieszczony przed obejmują prekompilowanego nagłówka wiersza zostanie zignorowany. Dodaj kod do wstępnie skompilowanego nagłówka.|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (poziom 4)|"*symbol*"nie jest zdefiniowany jako preprocesor makra, zastępując "0" do"*dyrektywy*"|
|C4682 (poziom 4)|"*symbol*": nie określonego atrybutu parametru bezpośredniego, domyślnie na [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (poziom 3)|"*typ zdefiniowany przez użytkownika*": możliwe zmiany w zachowaniu, zmiana UDT zwracać konwencji wywoływania|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (poziom 1)|"*funkcja*": podpis z innych niż nieprywatnego elementu członkowskiego zawiera prywatny typ macierzysty "native_type" zestawu|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (poziom 4)|"*funkcja*": funkcja nie została wbudowana|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (poziom 3)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp "*wyrażenie*" podlega/volatile:\<iso &#124; ms > ustawienie; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store|
|C4749 (poziom 4)|obsługiwane warunkowo: makro offsetof zastosowane do typu non standard układu "*typu*"|
|C4767 (poziom 4)|Nazwa sekcji '*symbol*"jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|C4768 (poziom 3)|atrybuty __declspec przed Specyfikacja powiązania są ignorowane|
|C4774 (poziom 4)|"*ciąg*": Oczekiwano argumentu ciąg formatu *numer* nie jest ciągiem literału|
|C4786 (poziom 3)|"*symbol*": Nazwa obiektu została obcięta do "number" znaków w informacji debugowania|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (poziom 4)|'bajty' dopełnienie bajtami dodane po konstrukcji 'member_name'|
|C4826 (poziom 2)|Konwersja z "*type1*"do"*type2*" jest ze znakiem. Może to spowodować nieoczekiwane zachowanie.|
|C4837 (poziom 4)|Wykryto — trigram: "? *znak*"zastąpione przez"*znak*"|
|C4841 (poziom 4)|użyte rozszerzenie niestandardowe: używane w makra offsetof oznaczeniem złożony element członkowski|
|C4842 (poziom 4)|Aby było spójne między wersjami kompilatora nie jest gwarantowana wynik "makra offsetof" zastosowane do typu przy użyciu dziedziczenie wielokrotne|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (poziom 4)|"_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjowanie w nawiasach klamrowych|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (poziom 1)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (poziom 1)|literał ciągu rzutowany na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (poziom 1)|'deklarator': identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzenią nazw|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (poziom 1)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (poziom 4)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (poziom 1)|reinterpret_cast używane między pokrewnymi klasami: 'klasa1' i 'klasa2'|
|C4962|'funkcja': optymalizacje profilowane wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (poziom 4)|"*symbol*": specyfikacja wyjątku jest niezgodna z poprzednią deklaracją|
|C4987 (poziom 4)|użyto rozszerzenia niestandardowego: 'throw (...)'|
|C4988 (poziom 4)|"*symbol*": Zmienna zadeklarowana poza zakresem klasy/funkcji|
|C5022|"*typu*": określono wiele konstruktorów przenoszenia|
|C5023|"*typu*": określono wiele operatorów przypisania przenoszenia|
|C5024 (poziom 4)|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5025 (poziom 4)|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|C5026 (poziom 1 i poziom 4)|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|C5027 (poziom 1 i poziom 4)|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|C5029 (poziom 4)|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, elementów członkowskich danych i typów tagów tylko|
|C5031 (poziom 4)|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu|
|C5032 (poziom 4)|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop)|
|C5035|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* ma zostać skompilowana jako gość kodu|
|C5036 (poziom 1)|varargs funkcji konwersja wskaźnika podczas kompilowania przy użyciu /hybrid:x86arm64 "*type1*"do"*type2*"|

Tych ostrzeżeń są wyłączone, chyba że [/ ograniczająca-](../build/reference/permissive-standards-conformance.md) ustawiono opcję kompilatora:

|||
|-|-|
|[C4471 (poziom 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)|deklaracja zapowiadająca wyliczenia nieobjętego zakresem musi mieć podstawowy typ (zakładany jest int)|
|[C4608 (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|"Unii\_elementu członkowskiego" został już zainicjowany przez inny element członkowski typu union na liście inicjatora "union_member"|


Ostrzeżenia zostały wyłączone domyślnie wersji kompilatora przed Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (poziom 2)|'konwersja': obcinanie z 'typ1' do "typ2"|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (poziom 1)|'zmienna' : obcinanie wskaźnika z 'typ do 'typ'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (poziom 1)|'operacja' : konwersja z 'typ1' na 'typ2' o większym rozmiarze|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (poziom 1)|"operator": zero rozszerzanie "type1" na "type2" większego rozmiaru|

Ostrzeżenia zostały wyłączone domyślnie wersji kompilatora przed programu Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (poziom 4)|brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnego int|

## <a name="see-also"></a>Zobacz też

[Ostrzeżenie](../preprocessor/warning.md)