---
title: "C4600 ostrzeżenia kompilatora za pośrednictwem C4799 | Dokumentacja firmy Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs: C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 456d35247f25d20684e8b6957d61428a2b113ca0
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4600-through-c4799"></a>C4600 ostrzeżenia kompilatora za pośrednictwem C4799

Artykuły w tej części dokumentacji zawierają informacje o podzbioru ostrzeżeń kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w oknie danych wyjściowych w programie Visual Studio można wybrać numer błędu, a następnie naciśnij klawisz F1.

> [!NOTE]
> Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błąd lub ostrzeżenie jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).

## <a name="in-this-section"></a>W tej sekcji

|Ostrzeżenie|Komunikat|
|-------------|-------------|
|[Kompilator C4600 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma "Nazwa makra": Oczekiwano prawidłowym ciągiem niepustym|
|Ostrzeżenie kompilatora (poziom 1) C4602|#pragma pop_macro: "Nazwa makra" nie poprzedniej dyrektywy #pragma push_macro dla tego identyfikatora|
|Ostrzeżenie kompilatora (poziom 1) C4603|"*identyfikator*": makro jest niezdefiniowane lub definicja różni się po użyciu prekompilowanego nagłówka|
|Ostrzeżenie kompilatora (poziom 1) C4604|"*typu*": przekazywanie argumentów poprzez wartość granicy natywnych i zarządzanych wymaga prawidłowej kopii konstruktora. W przeciwnym razie zachowania w czasie wykonywania jest niezdefiniowana|
|Ostrzeżenie kompilatora (poziom 1) C4605|"/D*makro*" określony w bieżącym wierszu polecenia, ale nie została określona, gdy został skompilowany prekompilowanego nagłówka|
|[Kompilator C4606 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|Ostrzeżenie #pragma: "ostrzeżenie numer" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń|
|[Kompilator ostrzegawcze (poziom 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|"union_member" został już zainicjowany przez inny element członkowski typu union na liście inicjatora "union_member"|
|Ostrzeżenie kompilatora (poziom 3, błąd) C4609|"*type1*"dziedziczy po interfejsie domyślnym"*interfejsu*"w typie"*type2*". Użyj innego interfejsu domyślnego dla "*type1*", lub przerwać relację bazową/dziedziczoną.|
|[Kompilator C4610 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|obiekt "class" nigdy nie mogą zostać utworzone - wymagany Konstruktor zdefiniowany przez użytkownika|
|[Kompilator C4611 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|Interakcja między "function" i zniszczeniem obiektu języka C++ nie jest przenośna|
|Ostrzeżenie kompilatora (poziom 1) C4612|Błąd w nazwie pliku dołączanego|
|Ostrzeżenie kompilatora (poziom 1) C4613|"*symbol*": klasa segmentu nie można zmienić.|
|[Kompilator C4615 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|Ostrzeżenie #pragma: Nieznany typ ostrzeżenia użytkownika|
|[Kompilator C4616 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|Ostrzeżenie #pragma: ostrzeżenie numer "number" nie jest prawidłowym ostrzeżeniem kompilatora|
|[Kompilator C4618 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|Parametry dyrektywy pragma zawierają ciąg pusty; dyrektywa pragma została zignorowana|
|[Kompilator C4619 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|ostrzeżenie #pragma: nie ma numeru ostrzeżenia 'numer'|
|Ostrzeżenie kompilatora (poziom 1) C4620|nie przyrostkowej formy "operator ++" znaleziono dla typu "type", użyta zostanie forma przedrostkowa|
|[Kompilator C4621 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|nie przyrostkowej formy "operator--" znaleziono dla typu "type", użyta zostanie forma przedrostkowa|
|Ostrzeżenie kompilatora (poziom 3) C4622|Zastępowanie informacji o debugowaniu utworzonej podczas tworzenia prekompilowanego nagłówka w pliku obiektu: 'Plik'.|
|[Kompilator C4623 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|"pochodzi z klasy": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty, ponieważ domyślny konstruktor klasy podstawowej jest niedostępne lub zostały usunięte|
|[Kompilator C4624 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|"pochodzi z klasy": destruktor został niejawnie zdefiniowany jako usunięty, ponieważ destruktor klasy podstawowej jest niedostępne lub zostały usunięte|
|[Kompilator C4625 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|"pochodzi z klasy": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiujący klasa podstawowa jest niedostępne lub zostały usunięte|
|[Kompilator C4626 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|"pochodzi z klasy": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasa podstawowa jest niedostępne lub zostały usunięte|
|[Kompilator C4627 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka|
|[Kompilator C4628 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków "dwuznaku" nie jest interpretowany jako alternatywny token dla "%s"|
|Ostrzeżenie kompilatora (poziom 4) C4629|użyto dwuznaku, sekwencja znaków "dwuznaku" interpretowane jako tokenu "char" (Wstaw spację między dwoma znakami, jeśli to nie mają)|
|[Kompilator C4630 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|"symbol": Specyfikator klasy magazynu "extern" jest niedozwolony w definicji elementu członkowskiego|
|Ostrzeżenie kompilatora (poziom 2) C4631|Oprogramowanie MSXML lub XPath niedostępny, nie będą przetwarzane komentarze dokumentu XML. Przyczyna|
|[Kompilator C4632 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentarz dokumentu XML: plik — dostęp zabroniony: Przyczyna|
|[Kompilator C4633 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Docelowy komentarza dokumentu XML: błąd: Przyczyna|
|Ostrzeżenie kompilatora (poziom 4) C4634|Docelowy komentarza dokumentu XML: nie można zastosować: Przyczyna|
|Ostrzeżenie kompilatora (poziom 3) C4635|Docelowy komentarza dokumentu XML: nieprawidłowo sformułowany kod XML: Przyczyna|
|Ostrzeżenie kompilatora (poziom 3) C4636|Stosowane do skonstruowania komentarza dokumentu XML: tag wymaga niepustym atrybutu ' atrybut '.|
|Ostrzeżenie kompilatora (poziom 3 i 4) C4637|Docelowy komentarza dokumentu XML: \<obejmują > tag odrzucone. Przyczyna|
|Ostrzeżenie kompilatora (poziom 3) C4638|Docelowy komentarza dokumentu XML: odwołanie do nieznanego symbolu "symbol".|
|[Kompilator C4639 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Błąd oprogramowania MSXML, nie będą przetwarzane komentarze dokumentu XML. Przyczyna|
|[Kompilator C4640 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancja': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna pod względem wątków|
|[Kompilator C4641 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentarz dokumentu XML ma niejednoznaczne odwołanie:|
|Ostrzeżenie kompilatora (poziom 3) C4645|Funkcja zadeklarowana ze __declspec(noreturn) zawiera instrukcję return|
|Ostrzeżenie kompilatora (poziom 3) C4646|Funkcja zadeklarowana ze __declspec(noreturn) ma typ zwracany inny niż void|
|Ostrzeżenie kompilatora (poziom 3) C4647|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach|
|Ostrzeżenie kompilatora (poziom 3) C4648|Atrybut standardowy "carries_dependency" zostanie zignorowany.|
|Ostrzeżenie kompilatora (poziom 3) C4649|atrybuty są ignorowane w tym kontekście|
|[Kompilator C4650 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne nagłówka będą dostępne|
|[Kompilator C4651 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|"definition" określony dla prekompilowanego nagłówka, ale nie dla bieżącej kompilacji|
|[Kompilator C4652 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|— Opcja kompilatora "option" niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza poleceń przesłoni zdefiniowaną WE prekompilowanym nagłówku|
|[Kompilator C4653 ostrzegawcze (poziom 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|— Opcja kompilatora "option" niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza polecenia została zignorowana|
|Ostrzeżenie kompilatora (poziom 4) C4654|Kod umieszczony przed obejmują prekompilowanego nagłówka wiersza zostanie zignorowany. Dodaj kod do wstępnie skompilowanego nagłówka.|
|Ostrzeżenie kompilatora (poziom 1) C4655|"symbol": typ zmiennej jest nowy od czasu ostatniej kompilacji lub jest zdefiniowany w różny sposób w innym miejscu|
|[Kompilatora (poziom 1) ostrzeżenia C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|"symbol": typ danych jest nowa lub została zmieniona od czasu ostatniej kompilacji lub jest zdefiniowany w różny sposób w innym miejscu|
|Ostrzeżenie kompilatora (poziom 1) C4657|wyrażenie zawiera typ danych, który jest nowy od czasu ostatniej kompilacji|
|Ostrzeżenie kompilatora (poziom 1) C4658|"Funkcja": prototyp funkcji jest nowy od czasu ostatniej kompilacji lub został inaczej w innym miejscu|
|[Kompilator C4659 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma "pragma": użycie zastrzeżonego segmentu "segmentu" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)|
|[Kompilator C4661 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'Identyfikator': Brak odpowiedniej definicji dostarczonej dla jawnego żądania wystąpienia szablonu|
|Ostrzeżenie kompilatora (poziom 1) C4662|jawne utworzenie wystąpienia; szablonu klasy "identifier1" nie ma definicji, z której można wyspecjalizować "identifier2"|
|[Kompilator C4667 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|"Funkcja": Brak zdefiniowanego szablonu funkcji, która pasuje do wymuszonego wystąpienia|
|[Kompilator C4668 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|"symbol" nie jest zdefiniowany jako preprocesor makra, zastępując "0" dla "dyrektywy"|
|[Kompilator C4669 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|Instrukcja "cast": niebezpieczna konwersja: "class" jest obiektem typu zarządzanego|
|Ostrzeżenie kompilatora (poziom 4) C4670|'Identyfikator': Ta klasa podstawowa jest niedostępna|
|Ostrzeżenie kompilatora (poziom 4) C4671|"identyfikator": Konstruktor kopiujący jest niedostępny|
|Ostrzeżenie kompilatora (poziom 4) C4672|"identifier1": niejednoznaczne. Pierwszy raz widziane jako "identifier2"|
|[Kompilator C4673 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|wyrzucanie "identyfikator" następujących typów, nie zostanie uwzględniony w obszarze przechwytywania|
|Ostrzeżenie kompilatora (poziom 1) C4674|"metoda" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr|
|Ostrzeżenie kompilatora (poziom 4) C4676|"%s": destruktor jest niedostępny|
|[Kompilator C4677 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|"Funkcja": podpis elementu z systemem innym niż nieprywatnego elementu członkowskiego zawiera prywatny typ zestawu "private_type"|
|Ostrzeżenie kompilatora (poziom 1) C4678|Klasa podstawowa "base_type" jest mniej dostępny niż "derived_type"|
|[Kompilator C4679 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|"członek": nie można zaimportować elementu członkowskiego|
|[Kompilator C4680 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|"class": klasa coclass nie określa domyślnego interfejsu|
|Ostrzeżenie kompilatora (poziom 4) C4681|"class": klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia|
|Ostrzeżenie kompilatora (poziom 4) C4682|"parametr": nie określonego atrybutu parametru bezpośredniego, domyślnie na [in]|
|[Kompilator C4683 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|"Funkcja": źródło zdarzenia ma "out" — parametr; należy zachować ostrożność podczas podłączania wielu obsług zdarzeń|
|[Kompilator C4684 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': ostrzeżenie!! atrybut może powodować generowanie nieprawidłowego kodu: Używaj ostrożnie|
|Ostrzeżenie kompilatora (poziom 1) C4685|Oczekiwano ">>" znaleziono ' >> ' podczas analizowania parametrów szablonu|
|[Kompilator C4686 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'typ zdefiniowany przez użytkownika': możliwe zmiany w zachowaniu, zmiana w konwencji wywoływania zwrotu UDT|
|[Kompilator C4687 ostrzeżenie (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|"class": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "interface"|
|Ostrzeżenie kompilatora (poziom 1) C4688|"ograniczenia": Lista ograniczeń zawiera prywatny typ zestawu "type"|
|Ostrzeżenie kompilatora (poziom 1) C4689|"%c": nieobsługiwany znak w #pragma detect_mismatch; #pragma ignorowane|
|Ostrzeżenie kompilatora (poziom 4) C4690|[emitidl (pop)]: więcej zdejmowań niż włożeń|
|[Kompilator C4691 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': oczekiwano typu odwołania w zestawie nieużywane 'Plik' typu zdefiniowanego w bieżącej jednostce tłumaczenia, zamiast tego użyć|
|[Kompilator C4692 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'funkcja': podpis z nieprywatnego elementu członkowskiego zawiera typ macierzysty 'native_type' zestawu prywatnego|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|"class": zapieczętowana klasa abstrakcyjna nie może mieć żadnych wystąpienia elementów członkowskich "wystąpienia elementu członkowskiego"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|"class": zapieczętowana klasa abstrakcyjna nie może mieć klasy podstawowej "base_class"|
|Ostrzeżenie kompilatora (poziom 1) C4695|#pragma execution_character_set: "zestaw znaków" nie jest nieobsługiwanym argumentem: obecnie tylko "UTF-8" jest obsługiwana.|
|Ostrzeżenie kompilatora (poziom 1) C4696|/ Opcja ZBvalue1 poza zakresem; Zakładając, że 'wartość2'|
|[Kompilator C4700 ostrzegawcze (poziom 1 i 4)](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|niezainicjowanej zmiennej lokalnej "name" używane|
|[Kompilator C4701 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|Użycie potencjalnie niezainicjowanej zmiennej lokalnej "name" używane|
|[Kompilator C4702 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|nieosiągalny kod|
|[Kompilator C4703 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej "%s" jest używane|
|[Kompilator C4706 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|Przypisanie wewnątrz wyrażenia warunkowego|
|[Kompilator C4709 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operator przecinka wewnątrz wyrażenia indeksu tablicy|
|[Kompilator C4710 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'funkcja: funkcja niewbudowana|
|[Kompilator C4711 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|Funkcja "function" wybrane do automatycznego rozwinięcia funkcji wbudowanej|
|[Kompilator C4714 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|Funkcja "function" oznaczona jako __forceinline nie została wbudowana|
|[Kompilator C4715 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|"Funkcja": nie niewszystkie ścieżki kodu zwracają wartość|
|[Kompilator C4716 ostrzegawcze (poziom 1, błąd)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|"Funkcja": musi zwracać wartość|
|[Kompilator C4717 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|"Funkcja": cykliczne we wszystkich ścieżkach kontroli, funkcja spowoduje przepełnienie stosu w czasie wykonywania|
|Ostrzeżenie kompilatora (poziom 4) C4718|"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie|
|Ostrzeżenie kompilatora (poziom 1) C4719|Jeśli określono parametr Qfast - użyj opcji "f" jako przyrostka, aby wskazać pojedynczą precyzję znaleziony stała typu Double|
|Ostrzeżenie kompilatora (poziom 2) C4720|Raporty asemblera wiersza: "komunikat"|
|Ostrzeżenie kompilatora (poziom 1) C4721|"Funkcja": nie jest dostępna jako funkcja wewnętrzna|
|Ostrzeżenie kompilatora (poziom 1) C4722|"Funkcja": destruktor nigdy nie powraca, potencjalny wyciek pamięci|
|[Kompilator C4723 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potencjalne dzielenie przez 0|
|Ostrzeżenie kompilatora (poziom 3) C4724|potencjalne dzielenie modulo przez 0|
|Ostrzeżenie kompilatora (poziom 3) C4725|Instrukcja może być niedokładna na niektórych procesorach Pentium|
|[Kompilator C4727 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Układ PCH o nazwie pch_file z tą samą sygnaturą czasową w obj_file_1 i obj_file_2.  Za pomocą pierwszego układu PCH.|
|Ostrzeżenie kompilatora (poziom 1) C4728|/ Opcja Yl-zignorowany, ponieważ wymagane jest odwołanie PCH|
|Ostrzeżenie kompilatora (poziom 4) C4729|Funkcja za duża dla przepływu wykres na podstawie ostrzeżenia|
|[Ostrzeżenie (poziom 1) C4730 kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)ostrzeżenie kompilatora (poziom 1) C4730|"main": połączenie typu _m64 i liczb zmiennoprzecinkowych wyrażenia może spowodować niepoprawny kod|
|[Kompilator C4731 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|"wskaźnik": "register" zmodyfikowany przez wbudowany kod asemblera rejestr wskaźnika ramki|
|Ostrzeżenie kompilatora (poziom 1) C4732|wewnętrzne "%s" nie jest obsługiwana w ramach tej architektury|
|[Kompilator C4733 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Wbudowanego asm przypisanie do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa|
|[Kompilator C4738 ostrzegawcze (poziom 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|Ostrzeżenie kompilatora (poziom 1) C4739|Odwołanie do zmiennej "var" przekracza jego miejsce do magazynowania|
|[Kompilator C4740 ostrzegawcze (poziom 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|Przepływ wejścia lub wyjścia wbudowanego kodu asemblera pomija optymalizację globalną|
|[Kompilator C4742 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|"var" ma inne wyrównanie w 'plik1' i 'plik2': numer i|
|[Kompilator C4743 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' ma inny rozmiar 'plik1' i 'plik2': liczbę i liczba bajtów|
|[Kompilator C4744 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|"var" ma inny typ w 'plik1' i 'plik2': "type1" i "type2".|
|[C4746 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp "*wyrażenie*" podlega/volatile:\<iso &#124; ms > ustawienie; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store|
|[Kompilator C4747 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Wywołanie zarządzanego entrypoint: kodu zarządzanego nie mogą być uruchamiane w obszarze blokady modułu ładującego, włączając punktu wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL|
|Ostrzeżenie kompilatora (poziom 4) C4749|obsługiwane warunkowo: makro offsetof zastosowane do typu non standard układu "*typu*"|
|Ostrzeżenie kompilatora (poziom 1) C4750|"identyfikator": funkcja zawierająca _alloca() została wbudowana w pętlę|
|Ostrzeżenie kompilatora (poziom 4) C4751|/ arch: avx nie ma zastosowania do Intel(R) Streaming SIMD Extensions, które znajduje się wewnątrz wbudowanego kodu Asemblera|
|Ostrzeżenie kompilatora (poziom 4) C4752|Znaleziono Intel(R) Advanced Vector Extensions; należy rozważyć użycie/arch: avx|
|Ostrzeżenie kompilatora (poziom 4) C4754|Reguły konwersji dla operacji arytmetycznych w porównaniu %s(%d) oznaczają, że jedna gałąź nie może zostać wykonana. Rzutowanie "%s" do "%s" (lub podobny typ o %d bajtach).|
|Ostrzeżenie C4755 kompilatora|Reguły konwersji dla operacji arytmetycznych w porównaniu %s(%d) oznaczają, że jedna gałąź nie można wykonać w funkcji śródwierszowych. Rzutowanie "%s" do "%s" (lub podobny typ o %d bajtach).|
|[Kompilator C4756 ostrzegawcze (poziom 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|przepełnienie w arytmetyce stałej|
|Ostrzeżenie kompilatora (poziom 4) C4757|Indeks dolny jest dużą wartością bez znaku, czy miało być ujemną stałą?|
|Ostrzeżenie kompilatora (poziom 4) C4764|Nie można wyrównać obiektów przechwytywania do więcej niż 16 bajtów|
|Ostrzeżenie kompilatora (poziom 4) C4767|Nazwa sekcji "%s" jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|Ostrzeżenie kompilatora (poziom 3) C4768|atrybuty __declspec przed Specyfikacja powiązania są ignorowane|
|Ostrzeżenie C4770 kompilatora|częściowo zweryfikowane wyliczenie "*nazwa*" używana jako indeks|
|Ostrzeżenie C4771 kompilatora|Granice muszą zostać utworzone przy użyciu wskaźnika prostego; Zignorowano funkcję wewnętrzną MPX|
|[Kompilator C4772 ostrzegawcze (poziom 1, błąd)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odwołuje się do typu z brakującej biblioteki typów; "missing_type" użyty jako element zastępczy|
|Ostrzeżenie kompilatora (poziom 4) C4774|"*ciąg*": Oczekiwano argumentu ciąg formatu *numer* nie jest ciągiem literału|
|Ostrzeżenie kompilatora (poziom 3) C4775|użyto niestandardowego rozszerzenia w ciągu formatu "*ciąg*"funkcji"*funkcja*"|
|Ostrzeżenie kompilatora (poziom 1) C4776|"%*znak*"nie jest dozwolony w ciągu formatowania lub funkcji"*funkcja*"|
|Ostrzeżenie kompilatora (poziom 4) C4777|"*funkcja*": ciąg formatu "*ciąg*"wymaga argumentu typu"*type1*", ale argumentu ze zmienną liczbą argumentów *numer* ma typ "*type2*"|
|Ostrzeżenie kompilatora (poziom 3) C4778|"*funkcja*": niezakończony ciąg formatu "*ciąg*"|
|[Kompilator C4788 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'Identyfikator': identyfikator został obcięty do "number" znaków|
|[Kompilator C4789 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|Bufor identyfikator i N bajtów zostanie przepełniony; M bajtów zostanie zapisane zaczynając od przesunięcia L|
|Ostrzeżenie kompilatora (poziom 2) C4792|Funkcja "%s" zadeklarowana za pomocą sysimport i odwoływać się z kodu natywnego; Importowanie biblioteki wymagane do połączenia|
|[Kompilator ostrzegawcze (poziom 1 i 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|"Funkcja": funkcja skompilowana jako natywny: \n\t'reason "|
|Ostrzeżenie kompilatora (poziom 1) C4794|Segment lokalny magazyn wątków zmiennej "%s" zmiany z "%s" na "%s"|
|[Kompilator C4799 ostrzegawcze (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|Funkcja "function" nie ma instrukcji EMMS|