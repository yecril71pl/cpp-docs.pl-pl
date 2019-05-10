---
title: Ostrzeżenia kompilatora — od C4600 do C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 3df17b115797f4d68621854d072c41aca14a0fd8
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857564"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Ostrzeżenia kompilatora — od C4600 do C4799

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty ostrzegawcze, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Message|
|-------------|-------------|
|[Ostrzeżenie kompilatora (poziom 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma "makra name": oczekiwano prawidłowego ciągu niepustego|
|[Ostrzeżenie kompilatora (poziom 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: "name — makro" nie poprzedniej dyrektywy #pragma push_macro dla tego identyfikatora|
|[Ostrzeżenie kompilatora (poziom 1) C4603](compiler-warning-level-1-c4603.md)|"*identyfikator*": makro jest niezdefiniowane lub definicja różni się po użyciu prekompilowanego nagłówka|
|Ostrzeżenie kompilatora (poziom 1) C4604|"*typu*": przekazywanie argumentów poprzez wartość granicę natywne i zarządzane wymaga prawidłowej kopii konstruktora. W przeciwnym razie działanie środowiska uruchomieniowego jest niezdefiniowane|
|Ostrzeżenie kompilatora (poziom 1) C4605|"/D *— makro*" określona w bieżącym wierszu polecenia, ale nie określono skompilowanych prekompilowanego nagłówka|
|[Ostrzeżenie kompilatora (poziom 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|Ostrzeżenie #pragma: "ostrzeżenie numer" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń|
|[Ostrzeżenie kompilatora (poziom 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|"union_member" został już zainicjowany przez inny element członkowski Unii na liście inicjatora, "union_member"|
|Ostrzeżenie kompilatora (poziom 3, błąd) C4609|"*type1*"pochodzi z domyślnym interfejsem"*interfejsu*"w typie"*type2*". Użyj innego interfejsu domyślnego dla "*type1*", lub przerwać relację bazową/dziedziczoną.|
|[Ostrzeżenie kompilatora (poziom 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|obiekt "class" nigdy nie może zostać utworzone - wymagany Konstruktor zdefiniowany przez użytkownika|
|[Ostrzeżenie kompilatora (poziom 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|Interakcja między "function" i zniszczeniem obiektu języka C++ nie jest przenośna|
|[Ostrzeżenie kompilatora (poziom 1) C4612](compiler-warning-level-1-c4612.md)|Błąd w nazwie pliku dołączanego|
|[Ostrzeżenie kompilatora (poziom 1) C4613](compiler-warning-level-1-c4613.md)|"*symbol*": klasa segmentu nie można jej zmienić.|
|[Ostrzeżenie kompilatora (poziom 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|Ostrzeżenie #pragma: Nieznany typ ostrzeżenia użytkownika|
|[Ostrzeżenie kompilatora (poziom 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|Ostrzeżenie #pragma: ostrzeżenie numer "number" nie jest prawidłowym ostrzeżeniem kompilatora|
|[Ostrzeżenie kompilatora (poziom 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|Parametry dyrektywy pragma zawierają dołączony ciąg pusty; dyrektywa pragma została zignorowana|
|[Ostrzeżenie kompilatora (poziom 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|ostrzeżenie #pragma: nie ma numeru ostrzeżenia 'numer'|
|[Ostrzeżenie kompilatora (poziom 1) C4620](compiler-warning-level-1-c4620.md)|nie przyrostkowej formy "operator ++" znaleziono dla typu "type" forma przedrostkowa|
|[Ostrzeżenie kompilatora (poziom 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|nie przyrostkowej formy "operator--" znaleziono dla typu "type" forma przedrostkowa|
|[Ostrzeżenie kompilatora (poziom 3) C4622](compiler-warning-level-3-c4622.md)|zastępowanie informacji o debugowaniu utworzonych podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: 'Plik'|
|[Ostrzeżenie kompilatora (poziom 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|"Klasa pochodna": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty, ponieważ domyślny konstruktor klasy bazowej jest niedostępny lub usunięty|
|[Ostrzeżenie kompilatora (poziom 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|"Klasa pochodna": destruktor został niejawnie zdefiniowany jako usunięty, ponieważ destruktor klasy podstawowej jest niedostępne lub zostały usunięte|
|[Ostrzeżenie kompilatora (poziom 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|"Klasa pochodna": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiowania klasy bazowej jest niedostępne lub zostały usunięte|
|[Ostrzeżenie kompilatora (poziom 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|"Klasa pochodna": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasy bazowej jest niedostępne lub zostały usunięte|
|[Ostrzeżenie kompilatora (poziom 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka|
|[Ostrzeżenie kompilatora (poziom 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków 'dwuznak' nie jest interpretowana jako alternatywny token dla "%s"|
|[Ostrzeżenie kompilatora (poziom 4) C4629](compiler-warning-level-4-c4629.md)|użyto dwuznaku, sekwencja znaków 'dwuznak' zinterpretowana jako token "char" (Wstaw spację między dwoma znakami, jeśli to nie mają)|
|[Ostrzeżenie kompilatora (poziom 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': Specyfikator klasy składującej "extern" jest niedozwolony w definicji składowej|
|Ostrzeżenie kompilatora (poziom 2) C4631|Oprogramowanie MSXML lub XPath niedostępna, dokumentu XML, które nie będą przetwarzane komentarze. Przyczyna|
|[Ostrzeżenie kompilatora (poziom 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentarz dokumentu XML: pliku — odmowa dostępu: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Docelowy komentarza dokumentu XML: błąd: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 4) C4634](compiler-warning-level-4-c4634.md)|Docelowy komentarza dokumentu XML: nie można zastosować: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4635](compiler-warning-level-3-c4635.md)|Docelowy komentarza dokumentu XML: niewłaściwie sformułowany kod XML: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4636](compiler-warning-level-3-c4636.md)|Stosowany do konstruowania komentarza dokumentu XML: tag wymaga niepustego atrybutu ' atrybut '.|
|[Ostrzeżenie kompilatora (poziom 3 i 4) C4637](compiler-warning-level-3-c4637.md)|Docelowy komentarza dokumentu XML: \<obejmują > tag odrzucone. Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4638](compiler-warning-level-3-c4638.md)|Docelowy komentarza dokumentu XML: odwołanie do nieznanego symbolu "symbol".|
|[Ostrzeżenie kompilatora (poziom 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Błąd oprogramowania MSXML, dokumentu XML, które nie będą przetwarzane komentarze. Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancja': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna pod względem wątków|
|[Ostrzeżenie kompilatora (poziom 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentarz dokumentu XML ma niejednoznaczne odwołanie:|
|[Ostrzeżenie kompilatora (poziom 3) C4645](compiler-warning-level-3-c4645.md)|Funkcja zadeklarowana ze __declspec(noreturn) zawiera instrukcję return|
|[Ostrzeżenie kompilatora (poziom 3) C4646](compiler-warning-level-3-c4646.md)|Funkcja zadeklarowana ze __declspec(noreturn) ma typ zwracany niż void|
|Ostrzeżenie kompilatora (poziom 3) C4647|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach|
|Ostrzeżenie kompilatora (poziom 3) C4648|Atrybut standardowy "carries_dependency" jest ignorowany.|
|Ostrzeżenie kompilatora (poziom 3) C4649|atrybuty są ignorowane w tym kontekście|
|[Ostrzeżenie kompilatora (poziom 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne z nagłówka będą dostępne|
|[Ostrzeżenie kompilatora (poziom 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|"definition" określony dla prekompilowanego nagłówka, ale nie dla bieżącej kompilacji|
|[Ostrzeżenie kompilatora (poziom 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|— Opcja kompilatora "opcji" niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza poleceń przesłoni opcję zdefiniowane we prekompilowanym nagłówku|
|[Ostrzeżenie kompilatora (poziom 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|— Opcja kompilatora "opcji" niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza polecenia została zignorowana|
|Ostrzeżenie kompilatora (poziom 4) C4654|Kod umieszczony przed elementem obejmują wstępnie skompilowanego nagłówka wiersza zostaną zignorowane. Dodaj kod do wstępnie skompilowanego nagłówka.|
|[Ostrzeżenie kompilatora (poziom 1) C4655](compiler-warning-level-1-c4655.md)|'symbol': typ zmiennej jest nowy od czasu ostatniej kompilacji lub zdefiniowanej w różny sposób w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': typ danych nowego została zmieniona od czasu ostatniej kompilacji lub zdefiniowanej w różny sposób w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4657](compiler-warning-level-1-c4657.md)|wyrażenie zawiera typ danych, który jest nowy od czasu ostatniej kompilacji|
|Ostrzeżenie kompilatora (poziom 1) C4658|'Funkcja': prototyp funkcji jest nowy od czasu ostatniej kompilacji lub został inaczej w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma "dyrektywy": użycie zastrzeżonego segmentu "segmentu" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)|
|[Ostrzeżenie kompilatora (poziom 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'Identyfikator': Brak odpowiedniej definicji dostarczonej dla jawnego żądania wystąpienia szablonu|
|[Ostrzeżenie kompilatora (poziom 1) C4662](compiler-warning-level-1-c4662.md)|jawne wystąpienie; szablon klasy "identifier1" nie ma definicji, z której można wyspecjalizować "identifier2"|
|[Ostrzeżenie kompilatora (poziom 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'Funkcja': nie zdefiniowanego szablonu funkcji, który pasuje do wymuszonego wystąpienia|
|[Ostrzeżenie kompilatora (poziom 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' nie jest zdefiniowany jako makro preprocesora, zastępowanie przez '0' dla 'dyrektywy'|
|[Ostrzeżenie kompilatora (poziom 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|Instrukcja "cast": niebezpieczna konwersja: "class" jest obiektem typu zarządzanego|
|[Ostrzeżenie kompilatora (poziom 4) C4670](compiler-warning-level-4-c4670.md)|'Identyfikator': Ta klasa bazowa jest niedostępna|
|Ostrzeżenie kompilatora (poziom 4) C4671|"identyfikator": Konstruktor kopiujący jest niedostępny|
|[Ostrzeżenie kompilatora (poziom 4) C4672](compiler-warning-level-4-c4672.md)|"identifier1": niejednoznaczne. Pierwszy raz widziane jako "identifier2"|
|[Ostrzeżenie kompilatora (poziom 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|Zgłaszanie 'Identyfikator' następujących typów, nie zostanie uwzględniony w obszarze przechwytywania|
|[Ostrzeżenie kompilatora (poziom 1) C4674](compiler-warning-level-1-c4674.md)|"method" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr|
|Ostrzeżenie kompilatora (poziom 4) C4676|"%s": destruktor jest niedostępny|
|[Ostrzeżenie kompilatora (poziom 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'Funkcja': podpis z nieprywatnej składowej zawiera prywatny typ zestawu "private_type"|
|[Ostrzeżenie kompilatora (poziom 1) C4678](compiler-warning-level-1-c4678.md)|Klasa bazowa "base_type" jest mniej dostępny niż "derived_type"|
|[Ostrzeżenie kompilatora (poziom 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'składowa': nie można zaimportować składowej|
|[Ostrzeżenie kompilatora (poziom 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|"class": klasa coclass nie określa domyślnego interfejsu|
|[Ostrzeżenie kompilatora (poziom 4) C4681](compiler-warning-level-4-c4681.md)|"class": klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia|
|[Ostrzeżenie kompilatora (poziom 4) C4682](compiler-warning-level-4-c4682.md)|"parametru": nie określono atrybutu kierunkowego parametru, domyślnie na [in]|
|[Ostrzeżenie kompilatora (poziom 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'Funkcja': źródło zdarzenia ma "out"-parameter; należy zachować ostrożność podczas podłączania wielu obsług zdarzeń|
|[Ostrzeżenie kompilatora (poziom 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|"attribute": OSTRZEŻENIE!! atrybut może powodować generowanie nieprawidłowego kodu: Używaj ostrożnie|
|[Ostrzeżenie kompilatora (poziom 1) C4685](compiler-warning-level-1-c4685.md)|Oczekiwano znaku ">>" znaleziono ">>" podczas analizowania parametrów szablonu|
|[Ostrzeżenie kompilatora (poziom 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'typ zdefiniowany przez użytkownika': możliwe zmiany w zachowaniu, zmiana w konwencji wywoływania zwrotu UDT|
|[Kompilator ostrzeżenie C4687 (błąd)](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|"class": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "interface"|
|[Ostrzeżenie kompilatora (poziom 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|"ograniczenia": Lista ograniczeń zawiera prywatny typ zestawu "type"|
|Ostrzeżenie kompilatora (poziom 1) C4689|"%c": nieobsługiwany znak w dyrektywie #pragma detect_mismatch; #pragma ignorowane|
|[Ostrzeżenie kompilatora (poziom 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: więcej zdejmowań niż włożeń|
|[Ostrzeżenie kompilatora (poziom 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|"type": oczekiwano typu odwołania w zestawie nieużywanej 'Plik' typ zdefiniowany w bieżącej jednostce tłumaczenia, zamiast tego użyć|
|[Ostrzeżenie kompilatora (poziom 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'funkcja': podpis z nieprywatnego elementu członkowskiego zawiera typ macierzysty 'native_type' zestawu prywatnego|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|"class": zapieczętowana klasa abstrakcyjna nie może mieć wszystkie wystąpienia elementów członkowskich 'składowa'|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|"class": zapieczętowana klasa abstrakcyjna nie może mieć klasy bazowej "element $base_class"|
|Ostrzeżenie kompilatora (poziom 1) C4695|#pragma execution_character_set: "zestaw znaków" jest nieobsługiwanym argumentem: obecnie tylko "UTF-8" jest obsługiwany.|
|Ostrzeżenie kompilatora (poziom 1) C4696|/ Opcja ZBvalue1 poza zakresem; Zakładając, że "wartość2"|
|[Ostrzeżenie kompilatora (poziom 1 i 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|niezainicjowanej zmiennej lokalnej "name" jest używany|
|[Ostrzeżenie kompilatora (poziom 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|Użycie potencjalnie niezainicjowanej zmiennej lokalnej "name" jest używany|
|[Ostrzeżenie kompilatora (poziom 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|nieosiągalny kod|
|[Ostrzeżenie kompilatora (poziom 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej "%s" jest używany|
|[Ostrzeżenie kompilatora (poziom 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|Przypisanie wewnątrz wyrażenia warunkowego|
|[Ostrzeżenie kompilatora (poziom 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operator przecinka wewnątrz wyrażenia indeksu tablicy|
|[Ostrzeżenie kompilatora (poziom 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'funkcja: funkcja niewbudowana|
|[Ostrzeżenie kompilatora (poziom 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|funkcji "function" wybrane do automatycznego rozwinięcia funkcji wbudowanej|
|[Ostrzeżenie kompilatora (poziom 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|funkcji "function" oznaczona jako __forceinline nie jest śródwierszowa|
|[Ostrzeżenie kompilatora (poziom 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'Funkcja': niewszystkie ścieżki kodu zwracają wartość|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'Funkcja': musi zwracać wartość|
|[Ostrzeżenie kompilatora (poziom 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'Funkcja': cykliczne we wszystkich ścieżkach, funkcja spowoduje przepełnienie stosu środowiska uruchomieniowego|
|[Ostrzeżenie kompilatora (poziom 4) C4718](compiler-warning-level-4-c4718.md)|"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie|
|Ostrzeżenie kompilatora (poziom 1) C4719|Stała typu Double znaleziona, gdy określono parametr Qfast - użyj opcji "f" jako przyrostka, aby wskazać pojedynczą precyzję|
|Ostrzeżenie kompilatora (poziom 2) C4720|wbudowane raporty asemblera: "message"|
|Ostrzeżenie kompilatora (poziom 1) C4721|'Funkcja': nie jest dostępna jako funkcja wewnętrzna|
|[Ostrzeżenie kompilatora (poziom 1) C4722](compiler-warning-level-1-c4722.md)|'Funkcja': destruktor nigdy nie powraca, Potencjalny przeciek pamięci|
|[Ostrzeżenie kompilatora (poziom 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potencjalne dzielenie przez 0|
|[Ostrzeżenie kompilatora (poziom 3) C4724](compiler-warning-level-3-c4724.md)|potencjalne dzielenie modulo przez 0|
|Ostrzeżenie kompilatora (poziom 3) C4725|Instrukcja może być niedokładna na niektórych procesorach Pentium|
|[Ostrzeżenie kompilatora (poziom 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Układ PCH o nazwie pch_file z tą samą sygnaturą czasową w obj_file_1 i obj_file_2.  Za pomocą pierwszego układu PCH.|
|Ostrzeżenie kompilatora (poziom 1) C4728|/ Opcja Yl-zignorowane, ponieważ wymagane jest odwołanie do PCH|
|Ostrzeżenie kompilatora (poziom 4) C4729|Funkcja za duża dla grafu przepływu na podstawie ostrzeżenia|
|[Ostrzeżenie (poziom 1) C4730 kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)ostrzeżenie kompilatora (poziom 1) C4730|"main": połączenie typu _m64 i zmiennoprzecinkowa wyrażeń może spowodować niepoprawny kod|
|[(Poziom 1) C4731 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|"wskaźnik": rejestr wskaźnika "register" zmodyfikowany przez wbudowany kod asemblera ramki|
|Ostrzeżenie kompilatora (poziom 1) C4732|wewnętrzne "%s" nie jest obsługiwana w ramach tej architektury|
|[(Poziom 1) C4733 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Przypisanie w wbudowanym do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa|
|[(Poziom 3) C4738 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|[Ostrzeżenie kompilatora (poziom 1) C4739](compiler-warning-level-1-c4739.md)|Odwołanie do zmiennej "var" przekracza jego miejsce do magazynowania|
|[(Poziom 4) C4740 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|przepływ w lub wyjścia wbudowanego kodu asemblera pomija optymalizację globalną|
|[(Poziom 1) C4742 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|"var" ma inne wyrównanie w 'plik1' i 'plik2': i numer|
|[(Poziom 1) C4743 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|"type" ma inny rozmiar w 'plik1' i 'plik2': liczbę i liczba bajtów|
|[(Poziom 1) C4744 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|"var" ma inny typ w 'plik1' i 'plik2': 'Typ1' i 'type2'|
|[C4746 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp "*wyrażenie*" podlega/volatile:\<iso&#124;ms >; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store funkcje wewnętrzne|
|[Ostrzeżenie kompilatora (poziom 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Wywołanie zarządzanego "punkt wejścia": Kod zarządzany nie mogą być uruchamiane w ramach blokady modułu ładującego, włączając w to punkt wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL|
|Ostrzeżenie kompilatora (poziom 4) C4749|warunkowo obsługiwane: makro offsetof zastosowano do typu nienależące niestandardowym układzie "*typu*"|
|[Ostrzeżenie kompilatora (poziom 1) C4750](compiler-warning-level-1-c4750.md)|'Identyfikator': funkcja zawierająca _alloca() została wbudowana w pętlę|
|Ostrzeżenie kompilatora (poziom 4) C4751|/ arch: nie ma zastosowania do Intel(R) Streaming SIMD Extensions, się wewnątrz wbudowanego ASM|
|Ostrzeżenie kompilatora (poziom 4) C4752|Znaleziono Intel(R) Advanced Vector Extensions; należy rozważyć użycie/arch:|
|[Ostrzeżenie kompilatora (poziom 4) C4754](compiler-warning-level-4-c4754.md)|Reguły konwersji dla operacji arytmetycznych w porównaniu %s(%d) oznaczają, że jedna gałąź nie może być wykonywane. Rzutowanie "%s" do "%s" (lub podobny typ o %d bajtach).|
|C4755 ostrzeżenia kompilatora|Reguły konwersji dla operacji arytmetycznych w porównaniu %s(%d) oznaczają, że jedna gałąź nie można wykonać w funkcji śródwierszowych. Rzutowanie "%s" do "%s" (lub podobny typ o %d bajtach).|
|[Ostrzeżenie kompilatora (poziom 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|przepełnienie w arytmetyce stałej|
|Ostrzeżenie kompilatora (poziom 4) C4757|Indeks dolny jest dużą wartością bez znaku, czy nie było planowane ujemną stałą?|
|[Ostrzeżenie kompilatora (poziom 4) C4764](compiler-warning-level-4-c4764.md)|Nie można wyrównać obiektów przechwytywania do więcej niż 16 bajtów|
|Ostrzeżenie kompilatora (poziom 4) C4767|Nazwa sekcji "%s" jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|Ostrzeżenie kompilatora (poziom 3) C4768|atrybuty __declspec przed specyfikacją konsolidacji są ignorowane.|
|C4770 ostrzeżenia kompilatora|częściowo zweryfikowane wyliczenie "*nazwa*" używane jako indeks|
|C4771 ostrzeżenia kompilatora|Granice muszą zostać utworzone przy użyciu wskaźnika prostego; Zignorowano funkcję wewnętrzną MPX|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odwołanie do typu z brakującej biblioteki typów; "missing_type" jest używana jako symbol zastępczy|
|Ostrzeżenie kompilatora (poziom 4) C4774|"*ciąg*": ciąg oczekiwany w argumencie formatu *numer* nie jest ciągiem literału|
|Ostrzeżenie kompilatora (poziom 3) C4775|użyto niestandardowego rozszerzenia w ciągu formatu "*ciąg*"funkcji"*funkcja*"|
|Ostrzeżenie kompilatora (poziom 1) C4776|"%*znak*"nie jest dozwolony w ciągu formatowania lub funkcji"*funkcja*"|
|Ostrzeżenie kompilatora (poziom 4) C4777|"*— funkcja*": ciąg formatu "*ciąg*"wymaga argumentu typu"*type1*", ale ze zmienną liczbą argumentów *numer* ma typ "*type2*"|
|Ostrzeżenie kompilatora (poziom 3) C4778|"*funkcja*": niezakończony ciąg formatu "*ciąg*"|
|[(Poziom 1) C4788 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'Identyfikator': identyfikator został obcięty do 'Liczba' znaków|
|[(Poziom 1) C4789 ostrzeżenia kompilatora](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|Bufor identyfikator i N liczba bajtów zostanie przepełniony; M bajtów zostanie zapisane zaczynając od przesunięcia L|
|Ostrzeżenie kompilatora (poziom 2) C4792|Funkcja "%s" zadeklarowana za pomocą sysimport i odwołania z kodu natywnego; Zaimportuj bibliotekę wymaganą do połączenia|
|[Ostrzeżenie kompilatora (poziom 1 i 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|"Funkcja': funkcja skompilowana jako natywny: \n\t'reason"|
|[Ostrzeżenie kompilatora (poziom 1) C4794](compiler-warning-level-1-c4794.md)|segment pamięci lokalnej wątku zmiennej "%s" zmieniła się z "%s" do "%s"|
|[Ostrzeżenie kompilatora (poziom 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|funkcji "function" nie ma instrukcji EMMS|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Ostrzeżenia kompilatora od C4000 - C5999](compiler-warnings-c4000-c5999.md)
