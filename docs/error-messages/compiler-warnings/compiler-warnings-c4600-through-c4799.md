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
- C4728
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
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 638af32b27f8d66086f3a39b74ecd46fdbb4649d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438168"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Ostrzeżenia kompilatora — od C4600 do C4799

Artykuły w tej sekcji dokumentacji wyjaśniają podzestaw komunikatów ostrzegawczych generowanych przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Komunikat|
|-------------|-------------|
|[Ostrzeżenie kompilatora (poziom 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma "Nazwa makra": oczekiwano prawidłowego ciągu niepustego|
|[Ostrzeżenie kompilatora (poziom 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: "Nazwa makra" nie Poprzednia #pragma push_macro dla tego identyfikatora|
|[Ostrzeżenie kompilatora (poziom 1) C4603](compiler-warning-level-1-c4603.md)|"*Identyfikator*": makro nie jest zdefiniowane lub definicja różni się po użyciu prekompilowanego nagłówka|
|Ostrzeżenie kompilatora (poziom 1) C4604|"*Type*": przekazywanie argumentu przez wartość w obrębie natywnej i zarządzanej granicy wymaga prawidłowego konstruktora kopiującego. W przeciwnym razie zachowanie środowiska uruchomieniowego jest niezdefiniowane|
|Ostrzeżenie kompilatora (poziom 1) C4605|"/D*makro*" określone w bieżącym wierszu polecenia, ale nie zostało określone podczas kompilowania prekompilowanego nagłówka|
|[Ostrzeżenie kompilatora (poziom 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma Ostrzeżenie: zignorowano komunikat "Warning number"; Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń|
|[Ostrzeżenie kompilatora (poziom 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|element "union_member" został już zainicjowany przez inny element członkowski Unii na liście inicjatora "union_member"|
|Ostrzeżenie kompilatora (poziom 3, błąd) C4609|element "*Type1*" pochodzi od domyślnego interfejsu "*Interface*" w typie "*Type2*". Użyj innego domyślnego interfejsu dla elementu "*Type1*" lub Przerwij relację bazową/pochodną.|
|[Ostrzeżenie kompilatora (poziom 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|nie można utworzyć wystąpienia obiektu "Class" — wymagany Konstruktor zdefiniowany przez użytkownika|
|[Ostrzeżenie kompilatora (poziom 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|Interakcja między "funkcją" C++ i zniszczeniem obiektu nie jest przenośna|
|[Ostrzeżenie kompilatora (poziom 1) C4612](compiler-warning-level-1-c4612.md)|błąd w nazwie pliku dołączanego|
|[Ostrzeżenie kompilatora (poziom 1) C4613](compiler-warning-level-1-c4613.md)|"*symbol*": Klasa segmentu nie może być zmieniona|
|[Ostrzeżenie kompilatora (poziom 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|Ostrzeżenie #pragma: nieznany typ ostrzeżenia użytkownika|
|[Ostrzeżenie kompilatora (poziom 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|Ostrzeżenie #pragma: numer ostrzegawczy "number" nie jest prawidłowym ostrzeżeniem kompilatora|
|[Ostrzeżenie kompilatora (poziom 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|parametry dyrektywy pragma zawierają pusty ciąg; pragma ignorowana|
|[Ostrzeżenie kompilatora (poziom 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|ostrzeżenie #pragma: nie ma numeru ostrzeżenia 'numer'|
|[Ostrzeżenie kompilatora (poziom 1) C4620](compiler-warning-level-1-c4620.md)|nie znaleziono przyrostkowej formy "operator + +" dla typu "Type", przy użyciu formy prefiksu|
|[Ostrzeżenie kompilatora (poziom 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|nie znaleziono przyrostkowej formy "operator--" dla typu "Type", przy użyciu formy prefiksu|
|[Ostrzeżenie kompilatora (poziom 3) C4622](compiler-warning-level-3-c4622.md)|Zastępowanie informacji o debugowaniu utworzonych podczas tworzenia prekompilowanego nagłówka w pliku obiektu: "plik"|
|[Ostrzeżenie kompilatora (poziom 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|"Klasa pochodna": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty, ponieważ domyślny Konstruktor klasy bazowej jest niedostępny lub usunięty|
|[Ostrzeżenie kompilatora (poziom 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|"Klasa pochodna": destruktor został niejawnie zdefiniowany jako usunięty, ponieważ destruktor klasy bazowej jest niedostępny lub usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|"Klasa pochodna": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiujący klasy bazowej jest niedostępny lub usunięty|
|[Ostrzeżenie kompilatora (poziom 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|"Klasa pochodna": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasy bazowej jest niedostępny lub usunięty|
|[Ostrzeżenie kompilatora (poziom 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka|
|[Ostrzeżenie kompilatora (poziom 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków "ungraph" nie jest interpretowana jako alternatywny token dla "% s"|
|[Ostrzeżenie kompilatora (poziom 4) C4629](compiler-warning-level-4-c4629.md)|użyto podgrafu, sekwencja znaków "regraf" interpretowana jako token "char" (Wstaw spację między dwoma znakami, jeśli nie jest to zamierzone)|
|[Ostrzeżenie kompilatora (poziom 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|"symbol": specyfikator klasy magazynu "extern" jest niedozwolony w definicji składowej|
|Ostrzeżenie kompilatora (poziom 2) C4631|Program MSXML lub XPath nie jest dostępny, komentarze dokumentu XML nie zostaną przetworzone. reason|
|[Ostrzeżenie kompilatora (poziom 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentarz dokumentu XML: odmowa dostępu do pliku: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Obiekt docelowy komentarza dokumentu XML: błąd: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 4) C4634](compiler-warning-level-4-c4634.md)|Obiekt docelowy komentarza dokumentu XML: nie można zastosować: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4635](compiler-warning-level-3-c4635.md)|Obiekt docelowy komentarza dokumentu XML: nieprawidłowo sformułowany kod XML: Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4636](compiler-warning-level-3-c4636.md)|Komentarz dokumentu XML zastosowany do konstrukcji: tag wymaga niepustego atrybutu "Attribute".|
|[Ostrzeżenie kompilatora (poziom 3 i poziom 4) C4637](compiler-warning-level-3-c4637.md)|Obiekt docelowy komentarza dokumentu XML: \<zawiera znacznik > odrzucony. Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4638](compiler-warning-level-3-c4638.md)|Obiekt docelowy komentarza dokumentu XML: odwołanie do nieznanego symbolu "symbol".|
|[Ostrzeżenie kompilatora (poziom 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Błąd MSXML, komentarze dokumentu XML nie zostaną przetworzone. Przyczyna|
|[Ostrzeżenie kompilatora (poziom 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancja': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna pod względem wątków|
|[Ostrzeżenie kompilatora (poziom 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentarz dokumentu XML ma niejednoznaczne odwołanie:|
|[Ostrzeżenie kompilatora (poziom 3) C4645](compiler-warning-level-3-c4645.md)|Funkcja zadeklarowana z __declspec (noreturn) zawiera instrukcję return|
|[Ostrzeżenie kompilatora (poziom 3) C4646](compiler-warning-level-3-c4646.md)|Funkcja zadeklarowana z elementem __declspec (noreturn) ma typ inny niż void|
|Ostrzeżenie kompilatora (poziom 3) C4647|zmiana zachowania: __is_pod (*Typ*) ma inną wartość w poprzednich wersjach|
|Ostrzeżenie kompilatora (poziom 3) C4648|atrybut standardowy "carries_dependency" jest ignorowany|
|Ostrzeżenie kompilatora (poziom 3) C4649|w tym kontekście atrybuty są ignorowane|
|[Ostrzeżenie kompilatora (poziom 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informacje debugowania nie są w prekompilowanym nagłówku; dostępne są tylko symbole globalne z nagłówka|
|[Ostrzeżenie kompilatora (poziom 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|określono element "Definition" dla prekompilowanego nagłówka, ale nie dla bieżącego kompilowania|
|[Ostrzeżenie kompilatora (poziom 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|Opcja kompilatora "Option" jest niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza polecenia spowoduje przesłonięcie zdefiniowanej w prekompilowanym nagłówku|
|[Ostrzeżenie kompilatora (poziom 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|Opcja kompilatora "Option" jest niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza poleceń została zignorowana|
|Ostrzeżenie kompilatora (poziom 4) C4654|Kod umieszczony przed dołączeniem do wiersza prekompilowanego nagłówka zostanie zignorowany. Dodaj kod do prekompilowanego nagłówka.|
|[Ostrzeżenie kompilatora (poziom 1) C4655](compiler-warning-level-1-c4655.md)|"symbol": typ zmiennej jest nowy od czasu ostatniej kompilacji lub został inaczej zdefiniowany w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|"symbol": typ danych jest nowy lub został zmieniony od czasu ostatniej kompilacji lub został inaczej zdefiniowany w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4657](compiler-warning-level-1-c4657.md)|wyrażenie zawiera typ danych, który jest nowy od czasu ostatniej kompilacji|
|Ostrzeżenie kompilatora (poziom 1) C4658|"Function": prototyp funkcji jest nowy od czasu ostatniej kompilacji lub został inaczej zadeklarowany w innym miejscu|
|[Ostrzeżenie kompilatora (poziom 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma "pragma": użycie zastrzeżonego segmentu "segment" ma niezdefiniowane zachowanie, użyj #pragma komentarza (Konsolidator,...)|
|[Ostrzeżenie kompilatora (poziom 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|"Identyfikator": brak odpowiedniej definicji dostarczonej dla jawnego żądania wystąpienia szablonu|
|[Ostrzeżenie kompilatora (poziom 1) C4662](compiler-warning-level-1-c4662.md)|jawne utworzenie wystąpienia; Klasa szablonu "Identifier1" nie ma definicji, z której można specjalizacji "identifier2"|
|[Ostrzeżenie kompilatora (poziom 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|"Function": Brak zdefiniowanego szablonu funkcji pasującego do wymuszonego utworzenia wystąpienia|
|[Ostrzeżenie kompilatora (poziom 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|element "symbol" nie jest zdefiniowany jako makro preprocesora, zastępując element "0" dla dyrektywy "|
|[Ostrzeżenie kompilatora (poziom 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|"CAST": niebezpieczna konwersja: "Class" jest obiektem typu zarządzanego|
|[Ostrzeżenie kompilatora (poziom 4) C4670](compiler-warning-level-4-c4670.md)|"Identyfikator": Ta klasa bazowa jest niedostępna|
|Ostrzeżenie kompilatora (poziom 4) C4671|"Identyfikator": Konstruktor kopiujący jest niedostępny|
|[Ostrzeżenie kompilatora (poziom 4) C4672](compiler-warning-level-4-c4672.md)|"Identifier1": niejednoznaczny. Pierwszy widziany jako "identifier2"|
|[Ostrzeżenie kompilatora (poziom 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|Zgłaszanie "Identyfikator" następujących typów nie będzie brane pod uwagę w witrynie catch|
|[Ostrzeżenie kompilatora (poziom 1) C4674](compiler-warning-level-1-c4674.md)|element "Method" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr|
|Ostrzeżenie kompilatora (poziom 4) C4676|"% s": destruktor jest niedostępny|
|[Ostrzeżenie kompilatora (poziom 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|"Function": Sygnatura nieprywatnej składowej zawiera prywatny Typ zestawu "private_type"|
|[Ostrzeżenie kompilatora (poziom 1) C4678](compiler-warning-level-1-c4678.md)|Klasa bazowa "base_type" jest mniej dostępna niż "derived_type"|
|[Ostrzeżenie kompilatora (poziom 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|"członek": nie można zaimportować składowej|
|[Ostrzeżenie kompilatora (poziom 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|"Class": Klasa coclass nie określa domyślnego interfejsu|
|[Ostrzeżenie kompilatora (poziom 4) C4681](compiler-warning-level-4-c4681.md)|"Class": Klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia|
|[Ostrzeżenie kompilatora (poziom 4) C4682](compiler-warning-level-4-c4682.md)|"parameter": brak określonego atrybutu parametru kierunkowego, wartość domyślna to [in]|
|[Ostrzeżenie kompilatora (poziom 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|"Function": Źródło zdarzenia ma parametr "parametr"; należy zachować ostrożność podczas podłączania obsługi wielu zdarzeń|
|[Ostrzeżenie kompilatora (poziom 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|"Attribute": Ostrzeżenie!! atrybut może spowodować nieprawidłowe generowanie kodu: należy używać z zachowaniem ostrożności|
|[Ostrzeżenie kompilatora (poziom 1) C4685](compiler-warning-level-1-c4685.md)|Oczekiwano "> >" znaleziono "> >" podczas analizowania parametrów szablonu|
|[Ostrzeżenie kompilatora (poziom 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'typ zdefiniowany przez użytkownika': możliwe zmiany w zachowaniu, zmiana w konwencji wywoływania zwrotu UDT|
|[Ostrzeżenie kompilatora (error) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|"Class": zapieczętowana Klasa abstrakcyjna nie może implementować interfejsu "Interface"|
|[Ostrzeżenie kompilatora (poziom 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|"Constraint": Lista ograniczeń zawiera prywatny Typ zestawu "Type"|
|Ostrzeżenie kompilatora (poziom 1) C4689|"% c": nieobsługiwany znak w #pragma detect_mismatch; #pragma zignorowane|
|[Ostrzeżenie kompilatora (poziom 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: więcej punktów obecności niż wypychanie|
|[Ostrzeżenie kompilatora (poziom 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|"Type": Oczekiwano typu odwołania w nieużywanym zestawie "File", w zamian użyto typu zdefiniowanego w bieżącej jednostce tłumaczenia|
|[Ostrzeżenie kompilatora (poziom 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'funkcja': podpis z nieprywatnego elementu członkowskiego zawiera typ macierzysty 'native_type' zestawu prywatnego|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|"Class": zapieczętowana Klasa abstrakcyjna nie może mieć żadnych składowych wystąpienia "|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|"Class": zapieczętowana Klasa abstrakcyjna nie może mieć klasy bazowej "base_class"|
|Ostrzeżenie kompilatora (poziom 1) C4695|#pragma execution_character_set: "zestaw znaków" nie jest obsługiwanym argumentem: obecnie obsługiwane jest tylko kodowanie "UTF-8"|
|Ostrzeżenie kompilatora (poziom 1) C4696|Opcja/ZBvalue1 poza zakresem; przyjęto "wartość2"|
|[Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|użyto niezainicjowanej zmiennej lokalnej "name"|
|[Ostrzeżenie kompilatora (poziom 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|użyto potencjalnie niezainicjowanej zmiennej lokalnej "name"|
|[Ostrzeżenie kompilatora (poziom 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|nieosiągalny kod|
|[Ostrzeżenie kompilatora (poziom 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|użyto potencjalnie niezainicjowanej zmiennej wskaźnika lokalnego "% s"|
|[Ostrzeżenie kompilatora (poziom 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|przypisanie w wyrażeniu warunkowym|
|[Ostrzeżenie kompilatora (poziom 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operator przecinka wewnątrz wyrażenia indeksu tablicy|
|[Ostrzeżenie kompilatora (poziom 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'funkcja: funkcja niewbudowana|
|[Ostrzeżenie kompilatora (poziom 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|Funkcja "Function" została wybrana do automatycznego rozwinięcia wbudowanego|
|[Ostrzeżenie kompilatora (poziom 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|Funkcja "Function" oznaczona jako __forceinline nie została wbudowana|
|[Ostrzeżenie kompilatora (poziom 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|"Function": nie wszystkie ścieżki sterujące zwracają wartość|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|"Function": musi zwracać wartość|
|[Ostrzeżenie kompilatora (poziom 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|"Function": rekursywnie we wszystkich ścieżkach kontroli, funkcja spowoduje przepełnienie stosu środowiska uruchomieniowego|
|[Ostrzeżenie kompilatora (poziom 4) C4718](compiler-warning-level-4-c4718.md)|"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie|
|Ostrzeżenie kompilatora (poziom 1) C4719|Znaleziono podwójną stałą, gdy określony określono parametr qfast — Użyj "f" jako sufiksu, aby wskazać pojedynczą precyzję|
|Ostrzeżenie kompilatora (poziom 2) C4720|Raporty asemblera wbudowanego: "Message"|
|Ostrzeżenie kompilatora (poziom 1) C4721|"Function": niedostępne jako wewnętrzne|
|[Ostrzeżenie kompilatora (poziom 1) C4722](compiler-warning-level-1-c4722.md)|"Function": destruktor nigdy nie zwraca, potencjalny przeciek pamięci|
|[Ostrzeżenie kompilatora (poziom 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potencjalne dzielenie przez 0|
|[Ostrzeżenie kompilatora (poziom 3) C4724](compiler-warning-level-3-c4724.md)|potencjalne dzielenie modulo przez 0|
|Ostrzeżenie kompilatora (poziom 3) C4725|Instrukcja może być niedokładna na niektórych procesorach Pentium|
|[Ostrzeżenie kompilatora (poziom 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH o nazwie pch_file z tą samą sygnaturą czasową znalezioną w obj_file_1 i obj_file_2.  Przy użyciu pierwszego PCH.|
|Ostrzeżenie kompilatora (poziom 1) C4728|Opcja/yl-została została zignorowana, ponieważ wymagane jest odwołanie do PCH|
|Ostrzeżenie kompilatora (poziom 4) C4729|Funkcja za duża dla ostrzeżeń opartych na grafie Flow|
|[Ostrzeżenie kompilatora (poziom 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md) Ostrzeżenie kompilatora (poziom 1) C4730|"Main": mieszanie _m64 i wyrażeń zmiennoprzecinkowych może spowodować niewłaściwy kod|
|[Ostrzeżenie kompilatora (poziom 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|"wskaźnik": Rejestr wskaźnika ramki "Register" został zmodyfikowany przez wbudowany kod asemblera|
|Ostrzeżenie kompilatora (poziom 1) C4732|wewnętrzne "% s" nie jest obsługiwane w tej architekturze|
|[Ostrzeżenie kompilatora (poziom 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Wbudowana kompilacja ASM przypisze do "FS: 0": obsługa nie jest zarejestrowana jako bezpieczna procedura obsługi|
|[Ostrzeżenie kompilatora (poziom 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności|
|[Ostrzeżenie kompilatora (poziom 1) C4739](compiler-warning-level-1-c4739.md)|odwołanie do zmiennej "var" przekracza jego miejsce w magazynie|
|[Ostrzeżenie kompilatora (poziom 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|przepływ wewnątrz lub z wbudowanego kodu ASM pomija optymalizację globalną|
|[Ostrzeżenie kompilatora (poziom 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|element "var" ma inne wyrównanie w "plik1" i "plik2": Number i Number|
|[Ostrzeżenie kompilatora (poziom 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|Typ "Type" ma inny rozmiar w "plik1" i "plik2": liczba i liczba bajtów|
|[Ostrzeżenie kompilatora (poziom 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|element "var" ma inny typ w "plik1" i "plik2": "type1" i "type2"|
|[Ostrzeżenie kompilatora C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|nietrwały dostęp elementu "*Expression*" podlega/volatile:\<iso&#124;MS > Setting; Rozważ użycie funkcji wewnętrznych w programie __iso_volatile_load/Store|
|[Ostrzeżenie kompilatora (poziom 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Wywoływanie funkcji "EntryPoint": kod zarządzany nie może być uruchamiany w ramach blokady modułu ładującego, w tym punktu wejścia biblioteki DLL i wywołań uzyskanych z punktu wejścia biblioteki DLL|
|Ostrzeżenie kompilatora (poziom 4) C4749|warunkowo obsługiwane: makro OffsetOf zastosowany do typu układu niestandardowym "*Type*"|
|[Ostrzeżenie kompilatora (poziom 1) C4750](compiler-warning-level-1-c4750.md)|"Identyfikator": funkcja zawierająca _alloca () została wbudowana w pętlę|
|Ostrzeżenie kompilatora (poziom 4) C4751|/arch: AVX nie ma zastosowania do Streaming SIMD Extensions Intel (R), które znajdują się wewnątrz wbudowanego ASM|
|Ostrzeżenie kompilatora (poziom 4) C4752|znaleziono zaawansowane rozszerzenia wektora Intel (R); Rozważ użycie/arch: AVX|
|[Ostrzeżenie kompilatora (poziom 4) C4754](compiler-warning-level-4-c4754.md)|Reguły konwersji dla operacji arytmetycznych w porównaniu z% s (% d) oznaczają, że jedna gałąź nie może być wykonana. Rzutowanie elementu "% s" na "% s" (lub podobnego typu% d b).|
|Ostrzeżenie kompilatora C4755|Reguły konwersji dla operacji arytmetycznych w porównaniu z% s (% d) oznaczają, że jedna gałąź nie może być wykonana w funkcji wbudowanej. Rzutowanie elementu "% s" na "% s" (lub podobnego typu% d b).|
|[Ostrzeżenie kompilatora (poziom 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|przepełnienie w stałej arytmetycznej|
|Ostrzeżenie kompilatora (poziom 4) C4757|Indeks dolny jest dużą wartością bez znaku, czy miał być ujemną stałą?|
|[Ostrzeżenie kompilatora (poziom 4) C4764](compiler-warning-level-4-c4764.md)|Nie można wyrównać obiektów przechwytywania do więcej niż 16 bajtów|
|Ostrzeżenie kompilatora (poziom 4) C4767|Nazwa sekcji "% s" jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator|
|Ostrzeżenie kompilatora (poziom 3) C4768|atrybuty __declspec zanim Specyfikacja powiązania są ignorowane|
|Ostrzeżenie kompilatora C4770|częściowo zweryfikowane Wyliczenie "*name*" użyte jako indeks|
|Ostrzeżenie kompilatora C4771|Granice muszą zostać utworzone przy użyciu wskaźnika prostego; Zignorowano funkcję wewnętrzną MPX|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odwołuje się do typu z brakującej biblioteki typów; "missing_type" używany jako symbol zastępczy|
|Ostrzeżenie kompilatora (poziom 4) C4774|"*String*": ciąg formatu oczekiwany w *numerze* argumentu nie jest literałem ciągu|
|Ostrzeżenie kompilatora (poziom 3) C4775|niestandardowe rozszerzenie użyte w ciągu formatu "*String*" funkcji "*Function*"|
|Ostrzeżenie kompilatora (poziom 1) C4776|element "%*Character*" jest niedozwolony w ciągu formatu funkcji "*Function*"|
|Ostrzeżenie kompilatora (poziom 4) C4777|"*Function*": ciąg formatu "*String*" wymaga argumentu typu "*Type1*", ale wariadyczne argument *Number* ma typ "*Type2*"|
|Ostrzeżenie kompilatora (poziom 3) C4778|"*Function*": niezakończony ciąg formatu "*String*"|
|[Ostrzeżenie kompilatora (poziom 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|"Identyfikator": identyfikator został obcięty do znaków "number"|
|[Ostrzeżenie kompilatora (poziom 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|bufor "Identyfikator" o rozmiarze N bajtów zostanie przepełniony; M bajtów zostanie zapisany, rozpoczynając od przesunięcia L|
|Ostrzeżenie kompilatora (poziom 2) C4792|Funkcja "% s" została zadeklarowana przy użyciu SysImport i przywoływana z kodu natywnego; Biblioteka importowana wymagana do konsolidacji|
|[Ostrzeżenie kompilatora (poziom 1 i 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|"Function": funkcja skompilowana jako natywna: \ n\t "Przyczyna"|
|[Ostrzeżenie kompilatora (poziom 1) C4794](compiler-warning-level-1-c4794.md)|segment zmiennej lokalnego magazynu wątku "% s" został zmieniony z "% s" na "% s"|
|[Ostrzeżenie kompilatora (poziom 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|Funkcja "Function" nie ma instrukcji EMMS|

## <a name="see-also"></a>Zobacz też

[Błędy iC++ ostrzeżenia narzędzi języka C/kompilatora i kompilacji](../compiler-errors-1/c-cpp-build-errors.md) \
[Ostrzeżenia kompilatora C4000-C5999](compiler-warnings-c4000-c5999.md)
