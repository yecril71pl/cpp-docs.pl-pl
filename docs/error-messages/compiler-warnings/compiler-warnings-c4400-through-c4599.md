---
title: Ostrzeżenia kompilatora — od C4400 do C4599
ms.date: 04/21/2019
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
- C4452
- C4453
- C4454
- C4455
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
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: d1a4da3d5e721c85879441a53ef4bc00549b587d
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230485"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Ostrzeżenia kompilatora — od C4400 do C4599

Artykuły w tej sekcji dokumentacji wyjaśniają podzestaw komunikatów ostrzegawczych generowanych przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Message|
|-------------|-------------|
|[Ostrzeżenie kompilatora (poziom 1) C4600](compiler-warning-level-1-c4600.md)|#pragma "*Nazwa makra*": oczekiwano prawidłowego ciągu niepustego|
|[Ostrzeżenie kompilatora (poziom 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|"*Type*": kwalifikatory const/volatile dla tego typu nie są obsługiwane|
|[Ostrzeżenie kompilatora (poziom 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|"*pole bitowe*": składowa jest polem bitowym|
|[Ostrzeżenie kompilatora (poziom 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|musi korzystać z operatora PTR|
|[Ostrzeżenie kompilatora (poziom 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|niedozwolony operator PTR|
|[Ostrzeżenie kompilatora (poziom 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|Zignorowano okres na dyrektywę|
|[Ostrzeżenie kompilatora (poziom 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|"*Identyfikator*": Identyfikator jest zarezerwowanym słowem|
|[Ostrzeżenie kompilatora (poziom 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|Zignorowano operand dla dyrektywy|
|[Ostrzeżenie kompilatora (poziom 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|Rzutowanie między różnymi wskaźnikami do przedstawienia elementu członkowskiego, kompilator może wygenerować niepoprawny kod|
|[Ostrzeżenie kompilatora (poziom 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|Anonimowy element "&#124;struct Union" nie zadeklarował żadnych składowych danych|
|[Ostrzeżenie kompilatora (poziom 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|niedozwolony rozmiar instrukcji|
|[Ostrzeżenie kompilatora (poziom 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|niedozwolony rozmiar operandu|
|[Ostrzeżenie kompilatora (poziom 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|"*Identyfikator*": symbol jest rozpoznawany jako przemieszczenie rejestru|
|[Ostrzeżenie kompilatora (poziom 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|"*Function*": Sygnatura funkcji zawiera typ "*Type*"; C++ obiekty nie są bezpieczne do przechodzenia między czystym kodem a mieszanym lub natywnym.|
|Ostrzeżenie kompilatora C4413|"ClassName:: member": składowa odwołania jest zainicjowana jako tymczasowa, która nie jest utrwalana po zakończeniu działania konstruktora|
|[Ostrzeżenie kompilatora (poziom 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|"*Function*": Krótki przeskok do funkcji konwertowanej na blisko|
|Ostrzeżenie kompilatora (poziom 1) C4415|duplicate __declspec(code_seg('*name*'))|
|Ostrzeżenie kompilatora (poziom 1) C4416|__declspec (code_seg (...)) zawiera pusty ciąg: zignorowano|
|Ostrzeżenie kompilatora (poziom 1) C4417|utworzenie wystąpienia jawnego szablonu nie może mieć __declspec (code_seg (...)): zignorowano|
|Ostrzeżenie kompilatora (poziom 1) C4418|__declspec (code_seg (...)) został zignorowany w wyliczeniu|
|Ostrzeżenie kompilatora (poziom 3) C4419|element "*symbol*" nie ma wpływu, gdy jest stosowany do prywatnej klasy ref "*Class*".|
|[Ostrzeżenie kompilatora (poziom 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|"*checked_operator*": operator nie jest dostępny, zamiast niego używa "*operator*"; Sprawdzanie w czasie wykonywania może być naruszone|
|Ostrzeżenie kompilatora (poziom 3) C4421|"*Parameter*": parametr Reference funkcji możliwością wznowienia jest potencjalnie niebezpieczny|
|Ostrzeżenie kompilatora (poziom 3) C4423|"std:: bad_alloc": zostanie przechwycony przez klasę ("*Type*") w *numerze* wiersza|
|Ostrzeżenie kompilatora (poziom 3) C4424|Catch for "*Type1*" poprzedzony znakiem "*Type2*" w *numerze*wiersza; nieprzewidywalne zachowanie może wynikać, jeśli zostanie zgłoszony element "std:: bad_alloc"|
|Ostrzeżenie kompilatora (poziom 1) C4425|Nie można zastosować adnotacji SAL do "..."|
|Ostrzeżenie kompilatora (poziom 1) C4426|flagi optymalizacji zostały zmienione po dołączeniu nagłówka, może to być spowodowane #pragma optymalizacją ()|
|Ostrzeżenie kompilatora (poziom 1) C4427|"*operator*": przepełnienie w ramach dzielenia stałej, niezdefiniowane zachowanie|
|[Ostrzeżenie kompilatora (poziom 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|możliwa niekompletna lub nieprawidłowo sformułowana nazwa znaku uniwersalnego|
|[Ostrzeżenie kompilatora (error) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|brak specyfikatora typu — zakładany int. Uwaga: C++nie obsługuje domyślnego-int|
|[Ostrzeżenie kompilatora (poziom 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|brak specyfikatora typu — zakładany int. Uwaga: Język C nie obsługuje już domyślnego-int|
|[Ostrzeżenie kompilatora (poziom 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|Konstruktor statyczny musi mieć prywatną dostępność; Zmiana dostępu prywatnego|
|[Ostrzeżenie kompilatora (poziom 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|"*derived_class*": Układ obiektu w obszarze/VD2 zmieni zmieni się ze względu na wirtualną podstawową "*BASE_CLASS*"|
|[Ostrzeżenie kompilatora (poziom 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dynamiczne\_rzutowanie z wirtualnej bazy danych "*BASE_CLASS*" na "*derived_class*" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem|
|[Ostrzeżenie kompilatora (poziom 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dynamiczne\_rzutowanie z wirtualnej bazy danych "*BASE_CLASS*" na "*derived_class*" może zakończyć się niepowodzeniem w niektórych kontekstach|
|Ostrzeżenie kompilatora C4438|"*Function*": nie można bezpiecznie wywołać w trybie/await: clrcompat. W przypadku wywołania*funkcji "Function*" do środowiska CLR może to spowodować uszkodzenie elementu CLR|
|[Ostrzeżenie kompilatora (error) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|"*Function*": definicja funkcji z typem zarządzanym w podpisie musi mieć konwencję wywoływania __clrcall|
|[Ostrzeżenie kompilatora (poziom 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|Zignorowano ponowną definicję konwencji wywoływania z "*calling_convention1*" na "*calling_convenction2*"|
|[Ostrzeżenie kompilatora (poziom 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|Zignorowano konwencję wywoływania elementu "*calling_convention1*"; Zamiast tego użyto "*calling_convention2*"|
|Ostrzeżenie kompilatora (poziom 1) C4442|osadzony terminator o wartości null w argumencie __annotation.  Wartość zostanie obcięta.|
|Ostrzeżenie kompilatora (poziom 1) C4443|Oczekiwano wartości parametru pragma "0", "1" lub "2"|
|Ostrzeżenie kompilatora (poziom 3) C4444|"*Identyfikator*": najwyższego poziomu "__unaligned" nie jest zaimplementowany w tym kontekście|
|[Ostrzeżenie kompilatora (poziom 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|"*Function*": w typie "Managed&#124;WinRT" metoda wirtualna nie może być prywatna|
|Ostrzeżenie kompilatora (poziom 1) C4446|"*Type*": nie można zamapować składowej "*Name1*" na ten typ, ze względu na konflikt z nazwą typu. Nazwa metody została zmieniona na "*NAME2*"|
|Ostrzeżenie kompilatora (poziom 1) C4447|znaleziono podpis "Main" bez modelu wątkowości. Rozważ użycie metody "int Main (platform::\<Array platform:: String ^ > ^ args)".|
|Ostrzeżenie kompilatora C4448|*Typ*1 nie ma domyślnego interfejsu określonego w metadanych. Wybór: "*Type2*", który może zakończyć się niepowodzeniem w czasie wykonywania.|
|Ostrzeżenie kompilatora C4449|Typniezapieczętowany powinien być oznaczony jako "[WebHostHidden]"|
|Ostrzeżenie kompilatora C4450|element "*Type1*" powinien być oznaczony jako "[WebHostHidden]", ponieważ pochodzi od "*Type2*"|
|Ostrzeżenie kompilatora (poziom 4) C4451|"classname1:: member": Użycie klasy ref "classname2:: member" wewnątrz tego kontekstu może prowadzić do nieprawidłowego kierowania obiektu w różnych kontekstach|
|Ostrzeżenie kompilatora (poziom 1) C4452|"*Identyfikator*": Typ publiczny nie może być w zakresie globalnym. Musi znajdować się w przestrzeni nazw, która jest elementem podrzędnym nazwy wyjściowego pliku winmd.|
|Ostrzeżenie kompilatora (poziom 1) C4453|"*Typ*": Typ "[WebHostHidden]" nie powinien być używany na publikowanej powierzchni typu publicznego, który nie jest "[WebHostHidden]"|
|Ostrzeżenie kompilatora (poziom 1) C4454|element "*Function*" jest przeciążony przez więcej niż liczbę parametrów wejściowych bez określonego parametru [DefaultOverload]. Wybieranie "*deklaracji*" jako domyślnego przeciążenia|
|Ostrzeżenie kompilatora (poziom 1) C4455|" *operator*operatora": identyfikatory sufiksu literału, które nie rozpoczynają się od podkreślenia, są zarezerwowane|
|[Ostrzeżenie kompilatora (poziom 4) C4456](compiler-warning-level-4-c4456.md)|Deklaracja elementu "*Identifier*" powoduje ukrycie poprzedniej deklaracji lokalnej|
|[Ostrzeżenie kompilatora (poziom 4) C4457](compiler-warning-level-4-c4457.md)|Deklaracja elementu "*Identifier*" powoduje ukrycie parametru funkcji|
|[Ostrzeżenie kompilatora (poziom 4) C4458](compiler-warning-level-4-c4458.md)|Deklaracja elementu "*Identifier*" powoduje ukrycie składowej klasy|
|[Ostrzeżenie kompilatora (poziom 4) C4459](compiler-warning-level-4-c4459.md)|Deklaracja elementu "*Identifier*" powoduje ukrycie deklaracji globalnej|
|[Ostrzeżenie kompilatora (poziom 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|"Operator&#124;" Managed "operator" ma parametr zakończony przez odwołanie. Operator "&#124;operator zarządzany" mainną semantykę z C++ operatora "*cpp_operator*", czy chodziło o wartość?|
|[Ostrzeżenie kompilatora (poziom 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|"*ClassName*": Ta klasa ma finalizator "! *finalizator*"~*dtor*"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|"*Type*": nie można określić identyfikatora GUID typu. Program może ulec awarii w czasie wykonywania.|
|[Ostrzeżenie kompilatora (poziom 4) C4463](compiler-warning-level-4-c4463.md)|przepływ Przypisywanie "*Value*" do pola bitowego, które może zawierać tylko wartości z "*MIN_VALUE*" na "*MAX_VALUE*"|
|[Ostrzeżenie kompilatora (poziom 4) C4464](../../error-messages/compiler-warnings/c4464.md)|względna ścieżka dołączania zawiera ".."|
|[Ostrzeżenie kompilatora (poziom 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|dyrektywy kontroli zmiennoprzecinkowej zostały zignorowane w opcji/CLR|
|[Ostrzeżenie kompilatora (poziom 4) C4471](compiler-warning-level-4-c4471.md)|"*Wyliczenie*": Deklaracja do przodu wyliczenia nienależącego do zakresu musi mieć typ podstawowy (założono int)|
|Ostrzeżenie kompilatora (poziom 1) C4472|element "*Identifier*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (Private/Public), aby zadeklarować Wyliczenie&#124;"zarządzane Managed"|
|[Ostrzeżenie kompilatora (poziom 1) C4473](c4473.md)|"*Function*": nie przeszedł wystarczającej liczby argumentów dla ciągu formatu|
|Ostrzeżenie kompilatora (poziom 3) C4474|"*Function*": przeszedł zbyt wiele argumentów dla ciągu formatu|
|Ostrzeżenie kompilatora (poziom 3) C4475|"*Function*": modyfikator długości "*modyfikator*" nie może być używany z znakiem pola typu "*Character*" w specyfikatorze formatu|
|Ostrzeżenie kompilatora (poziom 3) C4476|"*Function*": nieznany znak pola typu "*Character*" w specyfikatorze formatu|
|[Ostrzeżenie kompilatora (poziom 1) C4477](c4477.md)|"*Function*": ciąg formatu "*String*" wymaga argumentu typu "*Type*", ale *numer* argumentu wariadyczne ma typ "*Type*"|
|Ostrzeżenie kompilatora (poziom 1) C4478|"*Function*": symbole zastępcze pozycyjne i niepozycyjne nie mogą być mieszane w tym samym ciągu formatu|
|Ostrzeżenie kompilatora (error) C4480|użyto niestandardowego rozszerzenia: Określanie typu podstawowego*dla wyliczenia wyliczenia*|
|[Ostrzeżenie kompilatora (poziom 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|użyto niestandardowego rozszerzenia: override specyfikator "*słowo kluczowe*"|
|Ostrzeżenie kompilatora C4482|użyto niestandardowego rozszerzenia:*Wyliczenie*wyliczeniowy "enum" użyte w nazwie kwalifikowanej|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4483|Błąd składniowy: oczekiwano C++ słowa kluczowego|
|[Ostrzeżenie kompilatora (error) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|"*override_function*": pasuje do metody bazowej klasy referencyjnej "*base_class_function*", ale nie jest oznaczona modyfikatorem "Virtual", "New" ani "override"; Założono modyfikator "New" (ale nie "Virtual")|
|[Ostrzeżenie kompilatora (error) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|"*override_function*": pasuje do metody bazowej klasy referencyjnej "*base_class_function*", ale nie jest oznaczona modyfikatorem "New" ani "override"; Założono modyfikator "New" (i "Virtual")|
|[Ostrzeżenie kompilatora (poziom 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|"*Function*": prywatna metoda wirtualna klasy referencyjnej lub klasy wartości powinna być oznaczona jako "Sealed"|
|[Ostrzeżenie kompilatora (poziom 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|"*derived_class_function*": pasuje do dziedziczonej metody niewirtualnej "*base_class_function*", ale nie jest jawnie oznaczona jako "New"|
|[Ostrzeżenie kompilatora (poziom 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|"*Function*": wymaga słowa kluczowego "*słowo kluczowe*", aby zaimplementować metodę interfejsu "*interface_method*"|
|[Ostrzeżenie kompilatora (poziom 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|*specyfikator*": niedozwolony dla metody interfejsu"*Method*"; Specyfikatory przesłonięcia są dozwolone tylko w metodach klasy referencyjnej i klasie wartości|
|[Ostrzeżenie kompilatora (poziom 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|"override": Niepoprawne użycie specyfikatora override; *Funkcja "Function*" nie pasuje do metody bazowej klasy referencyjnej|
|Ostrzeżenie kompilatora (poziom 1) C4491|"*name*": ma format niedozwolonej wersji języka IDL|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4492|"*function1*": pasuje do metody bazowej klasy referencyjnej "*function2*", ale nie jest oznaczona jako "override"|
|Ostrzeżenie kompilatora (poziom 3, błąd) C4493|wyrażenie usuwania nie ma żadnego efektu, ponieważ destruktor typu "*Type*" nie ma dostępności "Public"|
|Ostrzeżenie kompilatora (poziom 1) C4494|"*Function*": Ignorowanie __declspec (alokatora), ponieważ typ zwracany funkcji nie jest wskaźnikiem ani odwołaniem|
|Ostrzeżenie kompilatora C4495|użyto niestandardowego rozszerzenia "__super": Zamień je na jawną nazwę klasy podstawowej|
|Ostrzeżenie kompilatora C4496|nie można użyć niestandardowego rozszerzenia "for each": Zamień je na instrukcję z zakresem-for|
|Ostrzeżenie kompilatora C4497|użyto niestandardowego rozszerzenia "Sealed": Zamień je na element "Final"|
|Ostrzeżenie kompilatora C4498|użyto niestandardowego rozszerzenia: "*Extension*"|
|Ostrzeżenie kompilatora (poziom 4) C4499|"*Function*": Jawna specjalizacja nie może mieć klasy magazynu (ignorowana) "|
|[Ostrzeżenie kompilatora (poziom 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|"*Specyfikacja powiązania*" wymaga użycia słowa kluczowego "extern" i musi poprzedzać wszystkie inne specyfikatory|
|[Ostrzeżenie kompilatora (poziom 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|"*Identyfikator*": przekroczono długość nazwy dekoracyjnej, nazwa została obcięta|
|[Ostrzeżenie kompilatora (poziom 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|"*Function*": funkcja lokalna, do której nie istnieje odwołanie, została usunięta|
|[Ostrzeżenie kompilatora (poziom 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|Brak definicji dla funkcji wbudowanej "*Function*"|
|[Ostrzeżenie kompilatora (poziom 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|"*Function*": funkcja powinna zwrócić wartość; Założono typ zwracany "void"|
|Ostrzeżenie kompilatora C4509|użyto niestandardowego rozszerzenia: funkcja "*Function*" używa SEH, a element "*Object*" ma destruktor|
|[Ostrzeżenie kompilatora (poziom 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|"*Class*": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|"*Class*": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|"*Class*": operator przypisania został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|"*Class*": destruktor został niejawnie zdefiniowany jako usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|"*Function*": funkcja wbudowana, do której nie istnieje odwołanie, została usunięta|
|[Ostrzeżenie kompilatora (poziom 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|"*przestrzeń nazw*": przestrzeń nazw używa samego siebie|
|[Ostrzeżenie kompilatora (poziom 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|"Class:: symbol": deklaracje dostępu są przestarzałe; deklaracje using składowej zapewniają lepszą alternatywę|
|[Ostrzeżenie kompilatora (poziom 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|deklaracje dostępu są przestarzałe; deklaracje using składowej zapewniają lepszą alternatywę|
|[Ostrzeżenie kompilatora (poziom 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|"*specyfikator*": nieoczekiwany w tym miejscu Klasa magazynu lub Specyfikatory typu; Ignoruj|
|Ostrzeżenie kompilatora (error) C4519|argumenty szablonu domyślnego są dozwolone tylko w szablonie klasy|
|[Ostrzeżenie kompilatora (poziom 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|"*Class*": określono wiele konstruktorów kopiujących|
|[Ostrzeżenie kompilatora (poziom 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|"*Class*": określono wiele operatorów przypisania|
|[Ostrzeżenie kompilatora (poziom 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|"*Class*": określono wiele destruktorów|
|[Ostrzeżenie kompilatora (poziom 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|"*Function*": statyczna funkcja członkowska nie może przesłonić ignorowania funkcji wirtualnej "*funkcja wirtualna*" została zignorowana, funkcja wirtualna zostanie ukryta|
|[Ostrzeżenie kompilatora (poziom 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++użyta procedura obsługi wyjątków, ale nie włączono semantyki operacji unwind. Określ/EHsc|
|Ostrzeżenie kompilatora (poziom 1) C4531|C++Obsługa wyjątków nie jest dostępna na Windows CE. Użyj strukturalnej obsługi wyjątków|
|[Ostrzeżenie kompilatora (poziom 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|"Kontynuuj": Wyskocz z bloku "__finally/finally" ma niezdefiniowane zachowanie podczas obsługi zakończenia|
|[Ostrzeżenie kompilatora (poziom 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|Inicjalizacja elementu "*Variable*" jest pomijana przez element "*goto Label*"|
|[Ostrzeżenie kompilatora (poziom 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|Konstruktor*nie*będzie konstruktorem domyślnym dla*identyfikatora*"Class/struct" "z powodu argumentu domyślnego|
|[Ostrzeżenie kompilatora (poziom 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|Wywołanie _set_se_translator () wymaga/EHa|
|[Ostrzeżenie kompilatora (poziom 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|"*TypeName*": nazwa typu przekracza limit meta danych znaków "*character_limit*"|
|[Ostrzeżenie kompilatora (poziom 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|"*Object*": "." zastosowany do typu innego niż UDT|
|[Ostrzeżenie kompilatora (poziom 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|"*Type*": kwalifikatory const/volatile dla tego typu nie są obsługiwane|
|[Ostrzeżenie kompilatora (poziom 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast używany do konwertowania na niedostępną lub niejednoznaczną podstawę; test czasu wykonywania zakończy się niepowodzeniem ("*Type1*" na "*Type2*")|
|[Ostrzeżenie kompilatora (poziom 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|element "*Identifier*" jest używany w typie polimorficznym "*Type*" z/gr-; może to spowodować nieprzewidywalne zachowanie|
|Ostrzeżenie kompilatora (poziom 1) C4542|Pomijanie generowania scalonego, wstrzykniętego pliku tekstowego; nie *można zapisać pliku* typu plików: "*problem*": *komunikat*|
|[Ostrzeżenie kompilatora (poziom 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Wstrzykiwany tekst został pominięty przez atrybut "\_No injected_text"|
|[Ostrzeżenie kompilatora (poziom 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|"*Deklaracja*": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu|
|[Ostrzeżenie kompilatora (poziom 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|wywołanie funkcji przed przecinkiem, brak listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|operator "*operator*": przed przecinkiem nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym|
|[Ostrzeżenie kompilatora (poziom 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[Ostrzeżenie kompilatora (poziom 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|operator "*operator*": przed przecinkiem nie ma żadnego wpływu; Czy chodziło o "*operator*"?|
|[Ostrzeżenie kompilatora (poziom 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|wyrażenie daje w wyniku funkcję, której brakuje listy argumentów|
|[Ostrzeżenie kompilatora (poziom 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|Brak listy argumentów wywołania funkcji|
|[Ostrzeżenie kompilatora (poziom 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|"*operator*": operator nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym|
|[Ostrzeżenie kompilatora (poziom 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|"*operator*": operator nie ma żadnego wpływu; Czy jesteś "operatorem"?|
|[Ostrzeżenie kompilatora (poziom 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|"*operator*": Sprawdź pierwszeństwo operatorów dla możliwego błędu; Użyj nawiasów, aby wyjaśnić pierwszeństwo|
|[Ostrzeżenie kompilatora (poziom 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt|
|[Ostrzeżenie kompilatora (poziom 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|wartość wewnętrznego argumentu bezpośredniego "*Value*" jest poza zakresem "*lower_bound* - *upper_bound*"|
|[Ostrzeżenie kompilatora (poziom 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|"__assume" zawiera efekt "*efekt*"|
|[Ostrzeżenie kompilatora (poziom 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|wartość operandu "*Value*" jest poza zakresem "*lower_bound* - *upper_bound*"|
|[Ostrzeżenie kompilatora (poziom 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|"*Function*": zmiana definicji; Funkcja zyskuje __declspec (modyfikator)|
|[Ostrzeżenie kompilatora (poziom 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|element "__fastcall" jest niezgodny z opcją "/CLR": konwertowanie na "__stdcall"|
|Ostrzeżenie kompilatora (poziom 4) C4562|w pełni prototypowe funkcje są wymagane z opcją "/CLR": konwertowanie "()" na "(void)"|
|[Ostrzeżenie kompilatora (poziom 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|Metoda "*Method*" elementu "Class" "*ClassName*" definiuje nieobsługiwany parametr domyślny "*Parameter*"|
|[Ostrzeżenie kompilatora (poziom 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|"*Function*": zmiana definicji; Symbol został poprzednio zadeklarowany za pomocą __declspec (modyfikator)|
|[Ostrzeżenie kompilatora (poziom 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|znak reprezentowany przez nazwę typu uniwersalnego "*char*" nie może być przedstawiony w bieżącej stronie kodowej (*Number*)|
|Ostrzeżenie kompilatora (poziom 1) C4568|"*Function*": żadne składowe nie odpowiadają sygnaturze jawnego przesłaniania|
|Ostrzeżenie kompilatora (poziom 3) C4569|"*Function*": żadne składowe nie odpowiadają sygnaturze jawnego przesłaniania|
|[Ostrzeżenie kompilatora (poziom 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|"*Type*": nie jest jawnie zadeklarowany jako abstrakcyjny, ale ma funkcje abstrakcyjne|
|[Ostrzeżenie kompilatora (poziom 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|informacyjne: semantyka catch (...) zmieniła się C++ od Visual 7,1; wyjątki strukturalne (SEH) nie są już przechwytywane|
|[Ostrzeżenie kompilatora (poziom 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." INSTEAD|
|Ostrzeżenie kompilatora (poziom 1) C4573|Użycie*wyrażenia "lambda Function*" wymaga, aby kompilator przechwycić element "This", ale bieżący domyślny tryb przechwytywania nie zezwala na to|
|Ostrzeżenie kompilatora (poziom 4) C4574|"*Identyfikator*" jest zdefiniowany jako "0": Czy chodziło o użycie "#if identyfikator"?|
|Ostrzeżenie kompilatora (poziom 1) C4575|element "__vectorcall" jest niezgodny z opcją "/CLR": konwertowanie na "__stdcall"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4576|Typ ujęty w nawiasy, po którym następuje lista inicjatora, to niestandardowa składnia konwersji typu jawnego|
|[Ostrzeżenie kompilatora (poziom 1, off) C4577](../../error-messages/compiler-warnings/compiler-warning-level-1-c4577.md)|użyto "noexcept" bez określonego trybu obsługi wyjątków; zakończenie przy wyjątku nie jest gwarantowane. Określ/EHsc|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4578|"ABS": konwersja z "*Type1*" na "*Type2*", możliwa utrata danych (Czy chodziło o wywołanie "*Function*" lub #include \<cmath >?)|
|[Ostrzeżenie kompilatora (poziom 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[Attribute] jest przestarzały; Zamiast tego należy określić system:: Attribute lub platform:: Metadata jako klasę bazową|
|[Ostrzeżenie kompilatora (poziom 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|przestarzałe zachowanie: element ""*String*"został zastąpiony*ciągiem" String*", aby przetworzyć atrybut|
|Ostrzeżenie kompilatora (poziom 4) C4582|"*Type*": Konstruktor nie jest wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 4) C4583|"*Type*": destruktor nie jest wywoływany niejawnie|
|[Ostrzeżenie kompilatora (poziom 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|"*Class1*": Klasa bazowa " *'klasa*" jest już klasą bazową "*class3*"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4585|"*Klasa*": Element WinRT "Public ref class" musi być zapieczętowany lub pochodzić z istniejącej niezapieczętowanej klasy|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4586|"*Typ*": Typ publiczny nie może być zadeklarowany w przestrzeni nazw najwyższego poziomu o nazwie "Windows"|
|Ostrzeżenie kompilatora (poziom 1) C4587|"*anonymous_structure*": zmiana zachowania: Konstruktor nie jest już wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 1) C4588|"*anonymous_structure*": zmiana zachowania: destruktor nie jest już wywoływany niejawnie|
|Ostrzeżenie kompilatora (poziom 1) C4591|Przekroczono limit *liczby* wywołań "constexpr" (/constexpr: numer głębokości\<>)|
|Ostrzeżenie kompilatora (poziom 3) C4592|"*Function*": Obliczanie wywołania "constexpr" nie powiodło się; Funkcja zostanie wywołana w czasie wykonywania|
|Ostrzeżenie kompilatora (poziom 1) C4593|"*Function*": przekroczono limit kroku oceny wywołania "constexpr" elementu "*Limit*"; Użyj/constexpr: kroki\<numer >, aby zwiększyć limit|
|Ostrzeżenie kompilatora (poziom 3) C4594|"*Type*": destruktor nie zostanie wywołany niejawnie, jeśli wystąpi wyjątek|
|Ostrzeżenie kompilatora (poziom 1) C4595|"*Type*": zmiana zachowania: destruktor nie będzie już wywoływany niejawnie, jeśli wystąpi wyjątek|
|[Ostrzeżenie kompilatora (poziom 4) C4596](../../error-messages/compiler-warnings/c4596.md)|"*Identyfikator*": niedozwolona kwalifikowana nazwa w deklaracji składowej|
|Ostrzeżenie kompilatora (error) C4597|niezdefiniowane zachowanie: makro OffsetOf zastosowana do elementu członkowskiego wirtualnej bazy|
|Ostrzeżenie kompilatora (poziom 1 i poziom 3) C4598|*nagłówek*"#include" ": *numer* numeru nagłówka w prekompilowanym nagłówku nie jest zgodny z bieżącą kompilacją w tej pozycji|
|Ostrzeżenie kompilatora (poziom 3) C4599|"*Flaga flagi* *":* *numer* argumentu wiersza polecenia nie pasuje do prekompilowanego nagłówka|

## <a name="see-also"></a>Zobacz także

[Błędy iC++ ostrzeżenia narzędzi języka C/kompilatora i kompilacji](../compiler-errors-1/c-cpp-build-errors.md) \
[Ostrzeżenia kompilatora C4000-C5999](compiler-warnings-c4000-c5999.md)
