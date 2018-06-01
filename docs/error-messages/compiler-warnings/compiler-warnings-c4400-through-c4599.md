---
title: C4400 ostrzeżenia kompilatora za pośrednictwem C4599 | Dokumentacja firmy Microsoft
ms.date: 05/30/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
dev_langs:
- C++
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71dbf1817c43c5511f8ee711abf3ff3566f314c9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704688"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>C4400 ostrzeżenia kompilatora za pośrednictwem C4599

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty ostrzegawcze, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Komunikat|
|-------------|-------------|
|[Ostrzeżenie kompilatora (poziom 1) C4600](compiler-warning-level-1-c4600.md)|#pragma "*nazwy makra*": Oczekiwano prawidłowym ciągiem niepustym|
|[Ostrzeżenie kompilatora (poziom 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.|
|[Ostrzeżenie kompilatora (poziom 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|"*bitfield*": element członkowski jest polem bitowym|
|[Ostrzeżenie kompilatora (poziom 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|należy użyć operatora PTR|
|[Ostrzeżenie kompilatora (poziom 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|Niedozwolony operator PTR|
|[Ostrzeżenie kompilatora (poziom 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|Zignorowano okres na dyrektywę|
|[Ostrzeżenie kompilatora (poziom 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|"*identyfikator*": identyfikator jest zarezerwowanym słowem|
|[Ostrzeżenie kompilatora (poziom 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|Zignorowano operand na dyrektywę|
|[Ostrzeżenie kompilatora (poziom 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|Rzutowanie pomiędzy innego wskaźnika do reprezentacji elementu członkowskiego, kompilator może wygenerować niepoprawny kod|
|[Ostrzeżenie kompilatora (poziom 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anonimowe "struct&#124;union' nie zadeklarował żadnych elementów członkowskich danych|
|[Ostrzeżenie kompilatora (poziom 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|Niedozwolona instrukcja rozmiaru|
|[Ostrzeżenie kompilatora (poziom 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|Niedozwolony rozmiar operandu|
|[Ostrzeżenie kompilatora (poziom 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|"*identyfikator*": symbol rozpoznawany jako przemieszczenie rejestru|
|[Ostrzeżenie kompilatora (poziom 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|"*funkcja*": sygnatura funkcji zawiera typ "*typu*'; Obiektami C++ są bezpieczne między czystym kodzie i mieszanego lub macierzystego.|
|Ostrzeżenie C4413 kompilatora|"classname::member": element członkowski odwołania jest zainicjowany jako tymczasowy, który nie jest zachowany po zakończeniu działania konstruktora|
|[Ostrzeżenie kompilatora (poziom 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|"*funkcja*": krótki przeskok do funkcji konwertowanej do umieszczonej blisko|
|Ostrzeżenie kompilatora (poziom 1) C4415|duplicate __declspec(code_seg('*name*'))|
|Ostrzeżenie kompilatora (poziom 1) C4416|__declspec(code_seg(...)) zawiera pusty ciąg: ignorowane|
|Ostrzeżenie kompilatora (poziom 1) C4417|utworzenie wystąpienia jawnego szablonu nie może mieć __declspec(code_seg(...)): ignorowane|
|Ostrzeżenie kompilatora (poziom 1) C4418|__declspec(code_seg(...)) został zignorowany w wyliczeniu|
|Ostrzeżenie kompilatora (poziom 3) C4419|"*symbol*"nie ma żadnego skutku, gdy zastosowane do prywatnej klasy ref"*klasy*".|
|[Ostrzeżenie kompilatora (poziom 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|"*checked_operator*": operator nie jest dostępny, za pomocą "*operator*" zamiast niego; kontrola czasu wykonania może być naruszona|
|Ostrzeżenie kompilatora (poziom 3) C4421|"*parametru*": parametr odwołania dla funkcji wznawialnych jest potencjalnie niebezpieczne|
|Ostrzeżenie kompilatora (poziom 3) C4423|'std::bad_alloc': zostanie przechwycony przez klasę ('*typu*") w wierszu *numer*|
|Ostrzeżenie kompilatora (poziom 3) C4424|przechwycenie '*type1*'poprzedzone przez'*type2*"w wierszu *numer*; nieprzewidywalne zachowanie może spowodować, jeśli zostanie zgłoszony 'std::bad_alloc'|
|Ostrzeżenie kompilatora (poziom 1) C4425|Nie można zastosować adnotacji SAL do "..."|
|Ostrzeżenie kompilatora (poziom 1) C4426|flagi optymalizacji zmieniły się po dołączeniu nagłówka, może #pragma Optimize()|
|Ostrzeżenie kompilatora (poziom 1) C4427|"*operator*": przepełnienie w czasie dzielenia stałej, niezdefiniowane zachowanie|
|[Ostrzeżenie kompilatora (poziom 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|możliwa niekompletna lub nieprawidłowo sformułowana universal-character-name|
|[Kompilator C4430 ostrzeżenie (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|brak specyfikatora typu — zakładany int. Uwaga: C++ nie obsługuje domyślnie typu int|
|[Ostrzeżenie kompilatora (poziom 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnego int|
|[Ostrzeżenie kompilatora (poziom 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|statyczny Konstruktor musi posiadać prywatną dostępność; Zmiana na prywatny dostęp|
|[Ostrzeżenie kompilatora (poziom 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|"*derived_class*": układ obiektów w/vd2 zmieni się z powodu bazy wirtualnej "*base_class*"|
|[Ostrzeżenie kompilatora (poziom 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dynamiczne\_rzutowania z wirtualnej podstawy "*base_class*"do"*derived_class*" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem|
|[Ostrzeżenie kompilatora (poziom 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dynamiczne\_rzutowania z wirtualnej podstawy "*base_class*"do"*derived_class*" może zakończyć się niepowodzeniem w niektórych kontekstach|
|Ostrzeżenie C4438 kompilatora|"*funkcja*": nie można bezpiecznie wywołać / await: clrcompat tryb. Jeśli "*funkcja*" wywołania do środowiska CLR może spowodować uszkodzenie nagłówka środowiska CLR|
|[Kompilator C4439 ostrzeżenie (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|"*funkcja*": definicja funkcji z zarządzanym typem w sygnaturze musi mieć konwencję wywołania __clrcall|
|[Ostrzeżenie kompilatora (poziom 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|wywoływanie definicję Konwencji wywołań z "*calling_convention1*"do"*calling_convenction2*" ignorowane|
|[Ostrzeżenie kompilatora (poziom 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|Konwencja wywoływania '*calling_convention1*"ignorowane. "*calling_convention2*" zamiast tego użyć|
|Ostrzeżenie kompilatora (poziom 1) C4442|osadzony terminatorem null w argumencie __annotation.  Wartość zostanie obcięta.|
|Ostrzeżenie kompilatora (poziom 1) C4443|Oczekiwano wartości parametru pragma "0", "1" lub "2"|
|Ostrzeżenie kompilatora (poziom 3) C4444|"*identyfikator*": element "__unaligned" najwyższego poziomu nie jest zaimplementowana w tym kontekście|
|[Ostrzeżenie kompilatora (poziom 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|"*funkcja*": w "WinRT&#124;zarządzanych" typ metody wirtualnej nie może być prywatne|
|Ostrzeżenie kompilatora (poziom 1) C4446|"*typu*": nie można mapować elementu członkowskiego "*Nazwa1*" do tego typu z powodu konfliktu z nazwą typu. Metoda została zmieniona na "*Nazwa2*"|
|Ostrzeżenie kompilatora (poziom 1) C4447|podpis "main" bez modelu wątków. Rozważ użycie "int main (Platform::Array\<Platform::String ^ > ^ args)".|
|Ostrzeżenie C4448 kompilatora|"*typu*1" nie ma domyślnego interfejsu określonego w metadanych. Pobrania: "*type2*", która może ulec awarii w czasie wykonywania.|
|Ostrzeżenie C4449 kompilatora|"*typu*" jako niezamknięty typ powinien być oznaczony jako "[WebHostHidden]"|
|Ostrzeżenie C4450 kompilatora|"*type1*"powinien być oznaczony jako "[WebHostHidden]" ponieważ dziedziczy po"*type2*"|
|Ostrzeżenie kompilatora (poziom 4) C4451|"classname1::member": użycie klasy ref "classname2::member' wewnątrz tego kontekstu może doprowadzić do nieprawidłowego kierowania obiektami między kontekstami|
|Ostrzeżenie kompilatora (poziom 1) C4452|"*identyfikator*": typ publiczny nie może być w zakresie globalnym. Musi być w przestrzeni nazw, która jest elementem podrzędnym nazwy wyjściowego pliku .winmd.|
|Ostrzeżenie kompilatora (poziom 1) C4453|"*typu*": typ '[WebHostHidden]' nie powinien być używany na publikowanej powierzchni typu publicznego, który nie jest "[WebHostHidden]"|
|Ostrzeżenie kompilatora (poziom 1) C4454|"*funkcja*" jest przeciążony przez więcej niż liczba parametrów wejściowych bez konieczności [DefaultOverload] określona. Pobrania "*deklaracji*" jako domyślne przeciążenie|
|Ostrzeżenie kompilatora (poziom 1) C4455|"operator *operator*": identyfikatory sufiksu literału, które nie rozpoczynają się od znaku podkreślenia są zarezerwowane|
|[Ostrzeżenie kompilatora (poziom 4) C4456](compiler-warning-level-4-c4456.md)|Deklaracja "*identyfikator*" powoduje ukrycie poprzedniej deklaracji lokalnej|
|[Ostrzeżenie kompilatora (poziom 4) C4457](compiler-warning-level-4-c4457.md)|Deklaracja "*identyfikator*" powoduje ukrycie parametru funkcji|
|[Ostrzeżenie kompilatora (poziom 4) C4458](compiler-warning-level-4-c4458.md)|Deklaracja "*identyfikator*" powoduje ukrycie elementu członkowskiego klasy|
|[Ostrzeżenie kompilatora (poziom 4) C4459](compiler-warning-level-4-c4459.md)|Deklaracja "*identyfikator*" powoduje ukrycie deklaracji globalnej|
|[Ostrzeżenie kompilatora (poziom 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|"WinRT&#124;zarządzanych" operator "*operator*", ma parametr przekazywany przez odwołanie. "WinRT&#124;zarządzanych" operator "*operator*"ma semantykę różną od operatora C++"*cpp_operator*", czy zamierzasz przekazanie przez wartość?|
|[Ostrzeżenie kompilatora (poziom 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|"*classname*": Ta klasa ma finalizator "! *finalizator*", ale nie ma destruktora" ~*dtor*"|
|[Kompilator ostrzegawcze (poziom 1, błąd) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|"*typu*": nie można określić GUID typu. Program może ulec awarii w czasie wykonywania.|
|[Ostrzeżenie kompilatora (poziom 4) C4463](compiler-warning-level-4-c4463.md)|przepełnienie; Przypisywanie "*wartość*"do pola bitowego, która może zawierać wartości z"*min_value*"do"*max_value*"|
|[Ostrzeżenie kompilatora (poziom 4) C4464](../../error-messages/compiler-warnings/c4464.md)|względna ścieżka dołączania zawiera ".."|
|[Ostrzeżenie kompilatora (poziom 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|Formant zmiennoprzecinkowych pragm zignorowane z opcją/CLR|
|[Ostrzeżenie kompilatora (poziom 4) C4471](compiler-warning-level-4-c4471.md)|"*wyliczenie*": deklaracja przekazująca dalej wyliczenie niebędące w zakresie musi być typu podstawowego (założono typ int)|
|Ostrzeżenie kompilatora (poziom 1) C4472|"*identyfikator*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (private/public), aby zadeklarować "WinRT&#124;zarządzanych" wyliczenia|
|[Ostrzeżenie kompilatora (poziom 1) C4473](c4473.md)|"*funkcja*": przekazano niewystarczającą liczbę argumentów dla ciągu formatowania|
|Ostrzeżenie kompilatora (poziom 3) C4474|"*funkcja*": przekazano za dużo argumentów dla ciągu formatowania|
|Ostrzeżenie kompilatora (poziom 3) C4475|"*funkcja*": modyfikator długości "*modyfikator*"nie może być stosowany ze znakiem pola typu"*znak*" w specyfikatorze formatu|
|Ostrzeżenie kompilatora (poziom 3) C4476|"*funkcja*': nieznany znak pola typu"*znak*"w specyfikatorze formatu|
|[Ostrzeżenie kompilatora (poziom 1) C4477](c4477.md)|"*funkcji*": ciąg formatu "*ciąg*"wymaga argumentu typu"*typu*", ale argument ze zmienną liczbą argumentów *numer* ma typ "*typu*"|
|Ostrzeżenie kompilatora (poziom 1) C4478|"*funkcja*": nie można łączyć pozycyjnych i niepozycyjnych symbole zastępcze w tym samym ciągu formatu|
|Kompilator/ostrzeżenie C4480 (błąd)|użyto niestandardowego rozszerzenia: Określanie typu podstawowego dla wyliczenia "*wyliczenie*"|
|[Ostrzeżenie kompilatora (poziom 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|użyto niestandardowego rozszerzenia: specyfikator przesłonięcia "*— słowo kluczowe*"|
|Ostrzeżenie C4482 kompilatora|użyto niestandardowego rozszerzenia: enum "*wyliczenie*" użyte w nazwie kwalifikowanej|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4483|Błąd składniowy: Oczekiwano słowa kluczowego języka C++|
|[Kompilator C4484 ostrzeżenie (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|"*override_function*": pasuje metody podstawowej klasy referencyjnej "*base_class_function*", ale nie jest oznaczony jako "virtual", "new" lub "override"; Założono "new" (ale nie "virtual")|
|[Kompilator C4485 ostrzeżenie (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|"*override_function*": pasuje metody podstawowej klasy referencyjnej "*base_class_function*", ale nie jest oznaczony jako "new" lub "override"; Założono "new" (i "virtual")|
|[Ostrzeżenie kompilatora (poziom 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|"*funkcja*": prywatna metoda wirtualna klasy referencyjnej lub klasy wartości powinna być oznaczona jako "sealed"|
|[Ostrzeżenie kompilatora (poziom 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|"*derived_class_function*": pasuje dziedziczone metody niewirtualnej "*base_class_function*", ale nie jest jawnie oznaczony jako "new"|
|[Ostrzeżenie kompilatora (poziom 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|"*funkcja*": wymaga "*— słowo kluczowe*"słowo kluczowe, aby zaimplementować metodę interfejsu"*interface_method*"|
|[Ostrzeżenie kompilatora (poziom 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|"*specyfikator*": niedozwolony dla metody interfejsu "*metody*"; specyfikatory są dozwolone tylko dla metod klasy referencyjnej klasy i wartość zastąpienia|
|[Ostrzeżenie kompilatora (poziom 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|"override": nieprawidłowe użycie specyfikatora override; "*funkcja*" jest niezgodny z metody podstawowej klasy referencyjnej|
|Ostrzeżenie kompilatora (poziom 1) C4491|"*nazwa*": ma niedozwolony format wersji języka IDL|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4492|"*function1*": pasuje metody podstawowej klasy referencyjnej "*function2*", ale nie jest oznaczony jako "override"|
|Ostrzeżenie kompilatora (poziom 3, błąd) C4493|wyrażenie usunięcia nie obowiązuje jako destruktor "*typu*" nie ma dostępności "public"|
|Ostrzeżenie kompilatora (poziom 1) C4494|"*funkcja*": Ignorowanie funkcji __declspec(allocator), ponieważ typ zwracany funkcji nie jest wskaźnikiem lub odwołaniem|
|Ostrzeżenie C4495 kompilatora|użyto niestandardowego rozszerzenia "__super": Zamień jawną nazwę klasy podstawowej|
|Ostrzeżenie C4496 kompilatora|użyto niestandardowego rozszerzenia "for each": Zamień na instrukcję ranged-for|
|Ostrzeżenie C4497 kompilatora|użyto niestandardowego rozszerzenia "sealed": Zamień "final"|
|Ostrzeżenie C4498 kompilatora|użyto niestandardowego rozszerzenia: "*rozszerzenia*"|
|Ostrzeżenie kompilatora (poziom 4) C4499|"*funkcja*": jawna specjalizacja nie może mieć klasy magazynu (zignorowano) "|
|[Ostrzeżenie kompilatora (poziom 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|"*Specyfikacja powiązania*" wymaga użycia słowa kluczowego "extern" i musi poprzedzać wszystkie inne specyfikatory|
|[Ostrzeżenie kompilatora (poziom 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|"*identyfikator*": przekroczona długość nazwy, dekorowanej nazwa została obcięta|
|[Ostrzeżenie kompilatora (poziom 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|"*funkcja*": Usunięto nieużywane funkcji lokalnej|
|[Ostrzeżenie kompilatora (poziom 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|Brak definicji dla funkcji wbudowanej "*funkcja*"|
|[Ostrzeżenie kompilatora (poziom 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|"*funkcja*": funkcja powinna zwrócić wartość; Założono typ zwracany "void"|
|Ostrzeżenie C4509 kompilatora|użyto niestandardowego rozszerzenia: "*funkcja*" używa SEH, a "*obiektu*" ma destruktor|
|[Ostrzeżenie kompilatora (poziom 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|"*klasy*": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|"*klasy*": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|"*klasy*": operator przypisania został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|"*klasy*": destruktor został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|"*funkcja*": nieużywane wbudowana funkcja została usunięta.|
|[Ostrzeżenie kompilatora (poziom 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|"*przestrzeni nazw*": przestrzeń nazw używa sama siebie|
|[Ostrzeżenie kompilatora (poziom 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|"class::symbol": deklaracje dostępu są przestarzałe; deklaracje using elementu członkowskiego zapewniają lepszą alternatywę|
|[Ostrzeżenie kompilatora (poziom 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|deklaracje dostępu są przestarzałe; deklaracje using elementu członkowskiego zapewniają lepszą alternatywę|
|[Ostrzeżenie kompilatora (poziom 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|"*specyfikator*": specyfikator(y) klasy magazynu lub typ nieoczekiwany; zignorowane|
|Kompilator ostrzeżenie C4519 (błąd)|argumenty szablonu domyślnego są dozwolone tylko dla szablonu klasy|
|[Ostrzeżenie kompilatora (poziom 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|"*klasy*": określono wiele konstruktorów kopiujących|
|[Ostrzeżenie kompilatora (poziom 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|"*klasy*": określono wiele operatorów przypisania|
|[Ostrzeżenie kompilatora (poziom 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|"*klasy*": określono wiele destruktorów|
|[Ostrzeżenie kompilatora (poziom 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|"*funkcja*": statycznej funkcji członkowskiej nie można przesłonić funkcji wirtualnej '*funkcji wirtualnej*"zastąpienie zignorowane, funkcja wirtualna zostanie ukryta|
|[Ostrzeżenie kompilatora (poziom 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Obsługa wyjątków języka C++ używane, ale semantyka rozwinięć nie są włączone. Określ/ehsc|
|Ostrzeżenie kompilatora (poziom 1) C4531|C++, obsługa wyjątków nie jest dostępna w systemie Windows CE. Użyj Obsługa wyjątków strukturalnych|
|[Ostrzeżenie kompilatora (poziom 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|"continue": skok poza bloku "__finally/finally" ma niezdefiniowane zachowanie podczas obsługi zakończenia|
|[Ostrzeżenie kompilatora (poziom 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|Inicjowanie "*zmiennej*"jest pomijana przy"*etykieta goto*"|
|[Ostrzeżenie kompilatora (poziom 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|"*Konstruktor*"nie będzie domyślnego konstruktora dla "w klasie/strukturze" "*identyfikator*" z powodu argumentu domyślnego|
|[Ostrzeżenie kompilatora (poziom 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|Wywołanie _set_se_translator() wymaga/eha|
|[Ostrzeżenie kompilatora (poziom 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|"*typename*": Nazwa typu przekracza limit meta-data "*character_limit*' znaków|
|[Ostrzeżenie kompilatora (poziom 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|"*obiektu*": "." zastosowany do typu z systemem innym niż UDT|
|[Ostrzeżenie kompilatora (poziom 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.|
|[Ostrzeżenie kompilatora (poziom 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast służący do konwertowania do niedostępnej lub niejednoznacznej podstawy; test czasu wykonywania zakończy się niepowodzeniem ("*type1*"do"*type2*")|
|[Ostrzeżenie kompilatora (poziom 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|"*identyfikator*"użyty na typie polimorficznym"*typu*" z/GR-; może spowodować nieprzewidywalne zachowanie|
|Ostrzeżenie kompilatora (poziom 1) C4542|Pomijanie generowania scalonego wstrzykniętego pliku tekstowego, nie można zapisać *filetype* pliku: "*problem*": *wiadomości*|
|[Ostrzeżenie kompilatora (poziom 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Wprowadzić tekst pominięty przez atrybut "nie\_injected_text"|
|[Ostrzeżenie kompilatora (poziom 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|"*deklaracji*": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu|
|[Ostrzeżenie kompilatora (poziom 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|wywołanie funkcji przed przecinkiem, brak listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|"*operator*": operator przed przecinkiem nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym|
|[Ostrzeżenie kompilatora (poziom 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[Ostrzeżenie kompilatora (poziom 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|"*operator*": operator przed przecinkiem nie ma żadnego wpływu; czy miało być "*operator*"?|
|[Ostrzeżenie kompilatora (poziom 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|wyrażenie daje w wyniku funkcję, której brakuje listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|Wywołanie funkcji brakuje listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|"*operator*": operator nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym|
|[Ostrzeżenie kompilatora (poziom 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|"*operator*": operator nie ma żadnego wpływu; czy miało być "operator?|
|[Kompilatora (poziom 3) ostrzeżenie C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|"*operator*": Sprawdź ustawienie pierwszeństwa operatora w poszukiwaniu możliwych błędów; Użyj nawiasów, aby wyjaśnić ustawienie pierwszeństwa|
|[Ostrzeżenie kompilatora (poziom 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[Ostrzeżenie kompilatora (poziom 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|wartość wewnętrznego argumentu natychmiastowego "*wartość*"jest poza zakresem"*lower_bound* - *upper_bound*"|
|[Ostrzeżenie kompilatora (poziom 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|"__assume" zawiera efekt "*efekt*"|
|[Ostrzeżenie kompilatora (poziom 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|wartość operandu "*wartość*"jest poza zakresem"*lower_bound* - *upper_bound*"|
|[Ostrzeżenie kompilatora (poziom 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|"*funkcja*": zmiana definicji; __declspec(modifier) zyski — funkcja|
|[Ostrzeżenie kompilatora (poziom 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|Wywołanie "__fastcall" niezgodny z "/ clr" opcja: konwertowanie na "__stdcall"|
|Ostrzeżenie kompilatora (poziom 4) C4562|funkcje w pełni prototypowane są wymagane w przypadku "/ clr" opcja: konwertowanie "()", "(void)"|
|[Ostrzeżenie kompilatora (poziom 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|Metoda "*— metoda*"klasy"" "*classname*"definiuje nieobsługiwany parametr domyślny"*parametru*"|
|[Ostrzeżenie kompilatora (poziom 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|"*funkcja*": zmiana definicji; symbol został wcześniej zadeklarowany z __declspec(modifier)|
|[Ostrzeżenie kompilatora (poziom 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|znak reprezentowany przez universal-character-name "*char*" nie może być reprezentowany w bieżącej stronie kodowej (*numer*)|
|Ostrzeżenie kompilatora (poziom 1) C4568|"*funkcja*": Brak członkowie nie odpowiadają podpisowi jawnego przesłaniania|
|Ostrzeżenie kompilatora (poziom 3) C4569|"*funkcja*": Brak członkowie nie odpowiadają podpisowi jawnego przesłaniania|
|[Ostrzeżenie kompilatora (poziom 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|"*typu*": nie jest jawnie zadeklarowana jako abstrakcyjna, ale ma funkcje abstrakcyjne|
|[Ostrzeżenie kompilatora (poziom 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane|
|[Ostrzeżenie kompilatora (poziom 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." zamiast niego|
|Ostrzeżenie kompilatora (poziom 1) C4573|użycie "*funkcja lambda*" wymaga przechwytywania "this" ale kompilator nie zezwala na to bieżący domyślny tryb przechwytywania|
|Ostrzeżenie kompilatora (poziom 4) C4574|"*Identyfikator*'jest zdefiniowany jako ' 0': czy zamierzałeś użyć '#if identyfikator'?|
|Ostrzeżenie kompilatora (poziom 1) C4575|"__vectorcall" jest niezgodny z "/ clr" opcja: konwertowanie na "__stdcall"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4576|Wpisz ujętego w nawiasy, a następnie lista inicjalizatora jest składnia konwersji typu jawnego niestandardowych|
|Ostrzeżenie kompilatora (poziom 1, Off) C4577|słowo kluczowe "noexcept" używane z nie określając; trybu obsługi wyjątków Zakończenie na wyjątku nie jest gwarantowana. Określ/ehsc|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4578|"abs": konwersja z "*type1*"do"*type2*", możliwa utrata danych (Czy chodziło Ci o wywołania "*funkcja*" lub do #include \<cmath >?)|
|[Ostrzeżenie kompilatora (poziom 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] jest przestarzały; Zamiast tego określ System::Attribute lub Platform::Metadata jako klasa podstawowa|
|[Ostrzeżenie kompilatora (poziom 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|zachowanie przestarzałe: ' "*ciąg*" "zastąpione"*ciąg*"Aby przetwarzać atrybut|
|Ostrzeżenie kompilatora (poziom 4) C4582|"*typu*": Konstruktor nie jest wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 4) C4583|"*typu*": destruktor nie jest wywoływany niejawnie|
|[Ostrzeżenie kompilatora (poziom 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|"*class1*": klasy podstawowej*class2*"jest już klasą podstawową elementu"*class3*"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4585|"*klasy*": A WinRT "public ref class" musi być zamknięta lub dziedziczyć po istniejącej niezamkniętej klasie|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4586|"*typu*": typ publiczny nie można zadeklarować w przestrzeni nazw najwyższego poziomu o nazwie "Windows"|
|Ostrzeżenie kompilatora (poziom 1) C4587|"*anonymous_structure*": Zmiana zachowania: konstruktor jest nie już wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 1) C4588|"*anonymous_structure*": Zmiana zachowania: destruktor jest nie już wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 1) C4591|limit głębokości wywołań "constexpr" *numer* Przekroczono (/ constexpr: DEPTH\<liczba >)|
|Ostrzeżenie kompilatora (poziom 3) C4592|"*funkcja*": ocena wywołania "constexpr" nie powiodła się; funkcja zostanie wywołana w czasie wykonywania|
|Ostrzeżenie kompilatora (poziom 1) C4593|"*funkcja*": "constexpr" wywołanie oceny krok limit równy "*limit*" przekroczony; Użyj Steps\<numer > Aby zwiększyć limit|
|Ostrzeżenie kompilatora (poziom 3) C4594|"*typu*": destruktor nie zostanie niejawnie wywołany, jeśli wyjątek|
|Ostrzeżenie kompilatora (poziom 1) C4595|"*typu*": Zmiana zachowania: destruktor będzie już niejawnie wywołania w przypadku jest zwracany wyjątek|
|Ostrzeżenie kompilatora (poziom 4) C4596|"*identyfikator*": niedozwolona nazwa kwalifikowana w deklaracji elementu członkowskiego|
|Ostrzeżenie kompilatora (błąd) C4597|Niezdefiniowane zachowanie: makro offsetof zastosowane do elementu członkowskiego wirtualnej podstawy|
|Ostrzeżenie kompilatora (poziom 1 i 3) C4598|"#include"*nagłówka*"": numer nagłówka *numer* w prekompilowanego nagłówka nie odpowiada bieżącej kompilacji na tej pozycji|
|Ostrzeżenie kompilatora (poziom 3) C4599|"*flagi* *ścieżki*": numer argumentu wiersza polecenia *numer* niezgodny prekompilowanego nagłówka|
