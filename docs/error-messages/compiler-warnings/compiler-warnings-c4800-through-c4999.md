---
title: Ostrzeżenia kompilatora — od C4800 do C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 7e715dcbac9dc59fe09ee1f917c02a23b3c4db14
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230475"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Ostrzeżenia kompilatora — od C4800 do C5999

Artykuły w tej sekcji dokumentacji wyjaśniają podzestaw komunikatów ostrzegawczych generowanych przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Message|
|-------------|------------|
|[Ostrzeżenie kompilatora (poziom 4) C4800](compiler-warning-level-3-c4800.md)| Niejawna konwersja z*typu "Type*" na typ bool. Możliwa utrata informacji |
|[Ostrzeżenie kompilatora (poziom 1) C4803](compiler-warning-level-1-c4803.md)|"*Metoda*": Metoda podniesienia ma inną klasę magazynu od zdarzenia, "*Event*"|
|[Ostrzeżenie kompilatora (poziom 1) C4804](compiler-warning-level-1-c4804.md)|"*Operation*": niebezpieczne użycie typu "bool" w operacji|
|[Ostrzeżenie kompilatora (poziom 1) C4805](compiler-warning-level-1-c4805.md)|"*Operation*": niebezpieczne połączenie typu "*Type1*" i typu "*Type2*" w operacji|
|[Ostrzeżenie kompilatora (poziom 1) C4806](compiler-warning-level-1-c4806.md)|"*Operation*": niebezpieczna operacja: żadna wartość typu "*Type1*" podwyższana do typu "*Type2*" nie może być równa podanych stałej|
|[Ostrzeżenie kompilatora (poziom 1) C4807](compiler-warning-level-1-c4807.md)|"*Operation*": niebezpieczne połączenie typu "*Type1*" i podpisane pole bitowe typu "*Type2*"|
|Ostrzeżenie kompilatora (poziom 1) C4808|wielkość liter "*Value*" nie jest prawidłową wartością dla warunku przełącznika typu "bool"|
|Ostrzeżenie kompilatora (poziom 1) C4809|Instrukcja Switch ma nadmiarową etykietę "default"; wszystkie możliwe etykiety "Case" są podawane|
|[Ostrzeżenie kompilatora (poziom 1) C4810](compiler-warning-level-1-c4810.md)|wartość dyrektywy pragma Pack (show) = = n|
|[Ostrzeżenie kompilatora (poziom 1) C4811](compiler-warning-level-1-c4811.md)|wartość dyrektywy pragma jest zgodna (forScope, show) = = Value|
|[Ostrzeżenie kompilatora (poziom 1) C4812](compiler-warning-level-1-c4812.md)|przestarzała deklaracja stylu: zamiast tego należy użyć "*new_syntax*"|
|[Ostrzeżenie kompilatora (poziom 1) C4813](compiler-warning-level-1-c4813.md)|"*Function*": funkcja zaprzyjaźniona klasy lokalnej musiała zostać poprzednio zadeklarowana|
|[Ostrzeżenie kompilatora (poziom 4) C4816](compiler-warning-level-4-c4816.md)|"*param*": parametr ma tablicę o rozmiarze zerowym, która zostanie obcięta (chyba że obiekt jest przesyłany przez odwołanie)|
|[Ostrzeżenie kompilatora (poziom 1) C4817](compiler-warning-level-1-c4817.md)|"*member*": niedozwolone użycie "." w celu uzyskania dostępu do tego elementu członkowskiego; Kompilator zamieniono na "->"|
|[Ostrzeżenie kompilatora (poziom 1) C4819](compiler-warning-level-1-c4819.md)|Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (Number). Zapisz plik w formacie Unicode, aby zapobiec utracie danych|
|[Ostrzeżenie kompilatora (poziom 4) C4820](compiler-warning-level-4-c4820.md)|dopełnienie bajtów "*Bytes*" po konstrukcji "*MEMBER_NAME*"|
|[Ostrzeżenie kompilatora (poziom 1) C4821](compiler-warning-level-1-c4821.md)|Nie można określić typu kodowania Unicode, Zapisz plik z podpisem (BOM)|
|[Ostrzeżenie kompilatora (poziom 1) C4822](compiler-warning-level-1-c4822.md)|"funkcja członkowska": Funkcja składowa klasy lokalnej nie ma treści|
|[Ostrzeżenie kompilatora (poziom 3) C4823](compiler-warning-level-3-c4823.md)|"*Function*": używa przypiętych wskaźników, ale semantyka nieprzewinięcia nie jest włączona. Rozważ użycie/EHa|
|Ostrzeżenie kompilatora (poziom 2) C4826|Konwersja z "*Type1*" na "*Type2*" jest rozszerzona. Może to spowodować nieoczekiwane zachowanie w czasie wykonywania.|
|Ostrzeżenie kompilatora (poziom 3) C4827|Publiczna Metoda "ToString" z 0 parametrami powinna być oznaczona jako Virtual i override|
|[Ostrzeżenie kompilatora (poziom 1) C4829](compiler-warning-level-1-c4829.md)|Prawdopodobnie nieprawidłowe parametry dla funkcji main. Rozważmy element "int Main (platform:\<: Array platform:: String ^ > ^ argv)"|
|[Ostrzeżenie kompilatora (poziom 1) C4835](compiler-warning-level-1-c4835.md)|"*zmienna*": inicjator dla eksportowanych danych nie zostanie uruchomiony, dopóki kod zarządzany nie zostanie uruchomiony po raz pierwszy w zestawie hosta|
|Ostrzeżenie kompilatora (poziom 4) C4837|Wykryto trójznaków: "?? *znak*"zastąpiony"*znakiem*"|
|[Ostrzeżenie kompilatora (poziom 1) C4838](compiler-warning-level-1-c4838.md)|Konwersja z "*type_1*" na "*type_2*" wymaga konwersji z zawężaniem|
|[Ostrzeżenie kompilatora (poziom 3) C4839](compiler-warning-level-3-c4839.md)|niestandardowe użycie klasy "*Type*" jako argumentu funkcji wariadyczne|
|[Ostrzeżenie kompilatora (poziom 4) C4840](compiler-warning-level-4-c4840.md)|nieprzenośne użycie klasy "*Type*" jako argumentu funkcji wariadyczne|
|Ostrzeżenie kompilatora (poziom 4) C4841|użyto niestandardowego rozszerzenia: wyznaczenie złożonego elementu członkowskiego użytego w makro OffsetOf|
|Ostrzeżenie kompilatora (poziom 4) C4842|wynik elementu "makro OffsetOf" zastosowanego do typu używającego wielu dziedziczeń nie jest gwarantowany spójny między wydaniami kompilatora|
|Ostrzeżenie kompilatora C4843|"*Type1*": Procedura obsługi wyjątków odwołująca się do typu Array lub Function jest nieosiągalna. zamiast niej użyj elementu "*Type2*"|
|Ostrzeżenie kompilatora C4844|"Export module *module_name*;" to teraz preferowana składnia do deklarowania interfejsu modułu|
| Ostrzeżenie kompilatora (poziom 4) C4845 | wartość\_"\_\|\[\|declspec (\|bezinit\_All)" jest ignorowana, jeśli w wierszu polecenia nie określono wartości "/d1initall 0 1 2 3]"\_ |
| Ostrzeżenie kompilatora (poziom 4) C4846 | element "*Value*" nie jest prawidłowym argumentem dla elementu "/d1initall": zignorowano flagę wiersza polecenia |
| Ostrzeżenie kompilatora (poziom 4) C4847 | element\_"\_declspec (\_bezinit\_All)" może być stosowany tylko do funkcji, typu klasy lub zmiennej lokalnej: zignorowano |
| Ostrzeżenie kompilatora (poziom 1) C4848 | Obsługa standardowego atrybutu "No\_Unique\_Address" w języku c++ 17 i starszych jest rozszerzeniem dostawcy |
|[Ostrzeżenie kompilatora (poziom 4) C4866](c4866.md)| Kompilator nie może wymusić kolejności oceny od lewej do prawej na potrzeby wywołania do *operator_name*|
|[Ostrzeżenie kompilatora (error) C4867](compiler-warning-c4867.md)|"*Function*": wywołanie funkcji nie ma listy argumentów; Użyj elementu "*call*", aby utworzyć wskaźnik do składowej|
|[Ostrzeżenie kompilatora (poziom 4) C4868](compiler-warning-c4868.md)|Kompilator "_File_(*line_number*)" nie może wymusić kolejności oceny od lewej do prawej na liście inicjalizacji z nawiasami klamrowymi|
|Ostrzeżenie kompilatora (poziom 2) C4872|Wykryto dzielenie liczby zmiennoprzecinkowej przez zero podczas kompilowania grafu wywołań dla concurrency::p arallel_for_each w: "*Location*"|
|Ostrzeżenie kompilatora (poziom 1) C4880|Rzutowanie z "const *type_1*" na "*type_2*": odrzucanie const ze wskaźnika lub odwołania może spowodować niezdefiniowane zachowanie w funkcji ograniczonej przez amp|
|Ostrzeżenie kompilatora (poziom 4) C4881|Konstruktor i/lub destruktor nie zostaną wywołane dla zmiennej tile_static "*Variable*"|
|Ostrzeżenie kompilatora (poziom 1) C4882|przekazywanie funktory z niestałymi operatorami wywołań do concurrency::p arallel_for_each jest przestarzałe|
|[Ostrzeżenie kompilatora C4900](compiler-warning-level-1-c4900.md)|Niezgodność Il między "*Tool1*" w wersji "*version1*" i "*Tool2*" w wersji "*Version2*"|
|[Ostrzeżenie kompilatora (poziom 1) C4905](compiler-warning-level-1-c4905.md)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[Ostrzeżenie kompilatora (poziom 1) C4906](compiler-warning-level-1-c4906.md)|literał ciągu rzutowany na 'LPWSTR'|
|[Ostrzeżenie kompilatora (poziom 1) C4910](compiler-warning-level-1-c4910.md)|"\<identyfikator >:" __declspec (dllexport) "i" extern "są niezgodne z jawnym wystąpieniem|
|[Ostrzeżenie kompilatora (poziom 1) C4912](compiler-warning-level-1-c4912.md)|"*Attribute*": atrybut ma niezdefiniowane zachowanie w ZAGNIEŻDŻONym UDT|
|[Ostrzeżenie kompilatora (poziom 4) C4913](compiler-warning-level-4-c4913.md)|Istnieje zdefiniowany przez użytkownika operator binarny ",", ale żadne Przeciążenie nie może konwertować wszystkich argumentów operacji, użyto domyślnego, wbudowanego operatora binarnego ","|
|Ostrzeżenie kompilatora (poziom 1) C4916|Aby uzyskać identyfikator DISPID, "*Description*": musi zostać wprowadzony przez interfejs|
|[Ostrzeżenie kompilatora (poziom 1) C4917](compiler-warning-level-1-c4917.md)|"*deklarator*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzenią nazw|
|[Ostrzeżenie kompilatora (poziom 4) C4918](compiler-warning-level-4-c4918.md)|"*Character*": nieprawidłowy znak na liście optymalizacji pragma|
|[Ostrzeżenie kompilatora (poziom 1) C4920](compiler-warning-level-1-c4920.md)|element członkowski wyliczenia wyliczenia member_1 = value_1 już występował w wyliczeniu wyliczenia jako member_2 = value_2|
|Ostrzeżenie kompilatora (poziom 3) C4921|"*Description*": atrybut value "*Attribute*" nie powinien być określony jako przemnożony|
|[Ostrzeżenie kompilatora (poziom 1) C4925](compiler-warning-level-1-c4925.md)|"*Method*": nie można wywołać metody dispinterface z poziomu skryptu|
|[Ostrzeżenie kompilatora (poziom 1) C4926](compiler-warning-level-1-c4926.md)|"*Identyfikator*": symbol jest już zdefiniowany: atrybuty zostały zignorowane|
|[Ostrzeżenie kompilatora (poziom 1) C4927](compiler-warning-level-1-c4927.md)|niedozwolona konwersja; więcej niż jedna konwersja zdefiniowana przez użytkownika została zastosowana niejawnie|
|[Ostrzeżenie kompilatora (poziom 1) C4928](compiler-warning-level-1-c4928.md)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[Ostrzeżenie kompilatora (poziom 1) C4929](compiler-warning-level-1-c4929.md)|"*plik*": Biblioteka typów zawiera Unię; ignorowanie kwalifikatora "embedded_idl"|
|[Ostrzeżenie kompilatora (poziom 1) C4930](compiler-warning-level-1-c4930.md)|"*prototyp*": funkcja prototypowa nie została wywołana (czy definicja zmiennej była zamierzona?)|
|[Ostrzeżenie kompilatora (poziom 4) C4931](compiler-warning-level-4-c4931.md)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|[Ostrzeżenie kompilatora (poziom 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*Identyfikator*) i \__identifier (*Identyfikator*) są nierozróżniane|
|Ostrzeżenie kompilatora (poziom 1) C4934|"__delegate (Multicast)" jest przestarzałe, użyj "\__Delegate" zamiast niego|
|[Ostrzeżenie kompilatora (poziom 1) C4935](compiler-warning-level-1-c4935.md)|specyfikator dostępu do zestawu został zmodyfikowany z "*Access*"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4936](compiler-warning-c4936.md)|Ta deklaracja __declspec jest obsługiwana tylko, gdy skompilowano z opcją/CLR lub/CLR: Pure|
|[Ostrzeżenie kompilatora (poziom 4) C4937](compiler-warning-level-4-c4937.md)|"*Tekst1*" i "*Tekst2*" są nierozróżniane jako argumenty*dyrektywy*"|
|[Ostrzeżenie kompilatora (poziom 4) C4938](compiler-warning-level-4-c4938.md)|"*var*": Zmienna redukcji zmiennoprzecinkowej może spowodować niespójne wyniki w obszarze/FP: Strict lub #pragma fenv_access|
|[Ostrzeżenie kompilatora C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji wizualizacjiC++|
|[Ostrzeżenie kompilatora (poziom 1) C4944](compiler-warning-level-1-c4944.md)|"*symbol*": nie można zaimportować symbolu z "*assembly1*": ponieważ "*symbol*" istnieje już w bieżącym zakresie|
|[Ostrzeżenie kompilatora (poziom 1) C4945](compiler-warning-level-1-c4945.md)|"*symbol*": nie można zaimportować symbolu z "*assembly1*": ponieważ "*symbol*" został już zaimportowany z innego zestawu "*Assembly2*"|
|[Ostrzeżenie kompilatora (poziom 1) C4946](compiler-warning-level-1-c4946.md)|użyto operatora reinterpret_cast między powiązanymi klasami: "*Class1*" i " *'klasa*"|
|[Ostrzeżenie kompilatora (poziom 1) C4947](compiler-warning-level-1-c4947.md)|"*type_or_member*": oznaczono jako przestarzały|
|[Ostrzeżenie kompilatora (poziom 2) C4948](compiler-warning-level-2-c4948.md)|zwracany typ elementu "*akcesor*" jest niezgodny z typem ostatniego parametru odpowiadającej mu metody ustawiającej|
|[Ostrzeżenie kompilatora (poziom 1 i poziom 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|dyrektywy pragma "Managed" i "Unmanaged" mają znaczenie tylko wtedy, gdy skompilowano z opcją "/CLR [: Option]"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4950](compiler-warning-c4950.md)|"*type_or_member*": oznaczono jako przestarzały|
|[Ostrzeżenie kompilatora (poziom 1) C4951](compiler-warning-level-1-c4951.md)|*Funkcja "Function*" została edytowana od czasu zebrania danych profilowych, dane profilu funkcji nie zostały użyte|
|[Ostrzeżenie kompilatora (poziom 1) C4952](compiler-warning-level-1-c4952.md)|"*Function*": nie znaleziono danych profilowych w bazie danych "*pgd_file*" programu|
|[Ostrzeżenie kompilatora (poziom 1) C4953](compiler-warning-level-1-c4953.md)|*Funkcja "Function*" została edytowana od czasu zebrania danych profilowych, dane profilowe nie są używane|
|Ostrzeżenie kompilatora C4954|"*Function*": nie profilowano (zawiera wyrażenie __int64 Switch)|
|Ostrzeżenie kompilatora C4955|"*import2*": Importowanie zostało zignorowane; zaimportowano już z "*Import1*"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4956](compiler-warning-c4956.md)|"*Type*": ten typ nie jest możliwy do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4957](compiler-warning-c4957.md)|"*Cast*": jawne rzutowanie z "*cast_from*" na "*cast_to*" nie jest możliwe do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4958](compiler-warning-c4958.md)|"*Operation*": arytmetyka wskaźnika nie jest możliwa do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4959](compiler-warning-c4959.md)|nie można zdefiniować niezarządzanego typu "*Type*" w/CLR: Safe, ponieważ dostęp do jego składowych daje kod niemożliwy do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 4) C4960](compiler-warning-level-4-c4960.md)|element "*Function*" jest zbyt duży, aby można go było profilować|
|[Ostrzeżenie kompilatora (poziom 1) C4961](compiler-warning-c4961.md)|Żadne dane profilowe nie zostały scalone z plikiem ". PGD", optymalizacje oparte na profilach zostały wyłączone|
|[Ostrzeżenie kompilatora (poziom 4) C4962](compiler-warning-c4962.md)|"*Function*": Optymalizacje profilowane zostały wyłączone, ponieważ optymalizacje powodowały niespójność danych profilowych|
|Ostrzeżenie kompilatora (poziom 1) C4963|"*Description*": nie znaleziono danych profilowych; inne opcje kompilatora zostały użyte w kompilacji Instrumentacji|
|[Ostrzeżenie kompilatora (poziom 1) C4964](compiler-warning-level-1-c4964.md)|Nie określono opcji optymalizacji; Informacje o profilu nie będą zbierane|
|[Ostrzeżenie kompilatora (poziom 1) C4965](compiler-warning-level-1-c4965.md)|niejawne pole z liczbą całkowitą 0; Użyj nullptr lub jawnego rzutowania|
|Ostrzeżenie kompilatora (poziom 1) C4966|*Funkcja "Function*" ma __code_seg adnotację z nieobsługiwaną nazwą segmentu, ignorowanie adnotacji|
|Ostrzeżenie kompilatora C4970|Konstruktor delegata: obiekt docelowy został zignorowany, ponieważ element "*Type*" jest statyczny|
|Ostrzeżenie kompilatora (poziom 1) C4971|Kolejność argumentów: \<obiekt docelowy >, \<> funkcji docelowej dla konstruktora delegatów jest przestarzały, \<Użyj funkcji docelowej > \<, obiekt docelowy = "" >|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4972](compiler-warning-c4972.md)|Bezpośrednie modyfikowanie lub potraktowanie wyniku operacji Unbox jako lvalue jest niemożliwy do zweryfikowania|
|Ostrzeżenie kompilatora (poziom 1) C4973|"*symbol*": oznaczono jako przestarzały|
|Ostrzeżenie kompilatora (poziom 1) C4974|"*symbol*": oznaczono jako przestarzały|
|Ostrzeżenie kompilatora (poziom 3) C4981|Warbird: funkcja "*Function*" oznaczona jako __forceinline nie została wbudowana, ponieważ zawiera semantykę wyjątku|
|[Ostrzeżenie kompilatora C4984](compiler-warning-c4984.md)|"If constexpr" jest rozszerzeniem języka C++ 17|
|Ostrzeżenie kompilatora (poziom 3) C4985|"*symbol_name*": atrybuty nieobecne w poprzedniej deklaracji.|
|[Ostrzeżenie kompilatora C4986](compiler-warning-c4986.md)|"*Deklaracja*": Specyfikacja wyjątku nie jest zgodna z poprzednią deklaracją|
|Ostrzeżenie kompilatora (poziom 4) C4987|użyto rozszerzenia niestandardowego: 'throw (...)'|
|Ostrzeżenie kompilatora (poziom 4) C4988|"*zmienna*": zmienna zadeklarowana poza zakresem klasy/funkcji|
|Ostrzeżenie kompilatora (poziom 4) C4989|"*Type*": typ ma definicje powodujące konflikt.|
|Ostrzeżenie kompilatora (poziom 3) C4990|Warbird: *komunikat*|
|Ostrzeżenie kompilatora (poziom 3) C4991|Warbird: funkcja "*Function*" oznaczona jako __forceinline nie została wbudowana, ponieważ poziom ochrony jest większy niż element nadrzędny|
|Ostrzeżenie kompilatora (poziom 3) C4992|Warbird: funkcja "*Function*" oznaczona jako __forceinline nie została wbudowana, ponieważ zawiera wbudowany zestaw, który nie może być chroniony|
|[Ostrzeżenie kompilatora (poziom 3) C4995](compiler-warning-level-3-c4995.md)|"*Function*": nazwa została oznaczona jako przestarzała #pragma|
|[Ostrzeżenie kompilatora (poziom 3) C4996](compiler-warning-level-3-c4996.md)|"*przestarzałe-deklaracja*": *przestarzałe — komunikat* (lub "został zadeklarowany jako przestarzały")|
|[Ostrzeżenie kompilatora (poziom 1) C4997](compiler-warning-level-1-c4997.md)|"*Class*": Klasa coclass nie IMPLEMENTUJE interfejsu com lub pseudo-Interface|
|Ostrzeżenie kompilatora (poziom 1) C4998|OCZEKIWANie nie powiodło się: *oczekiwanie*(*wartość*)|
|[Ostrzeżenie kompilatora C4999](compiler-warning-level-1-c4999.md)|Nieznane ostrzeżenie wybierz polecenie Pomoc techniczna w menu Pomoc wizualna C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|Ostrzeżenie kompilatora C5022|"*Type*": określono wiele konstruktorów przenoszenia|
|Ostrzeżenie kompilatora C5023|"*Type*": określono wiele operatorów przypisania przenoszenia|
|Ostrzeżenie kompilatora (poziom 4) C5024|"*Type*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 4) C5025|"*Type*": operator przypisania przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i poziom 4) C5026|"*Type*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i poziom 4) C5027|"*Type*": operator przypisania przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1) C5028|"*Nazwa*": Wyrównanie określone we wcześniejszej deklaracji (*Number*) nie jest określone w definicji|
|Ostrzeżenie kompilatora (poziom 4) C5029|użyto niestandardowego rozszerzenia: atrybuty wyrównania w C++ zastosowaniu do zmiennych, elementów członkowskich danych i typów tagów|
|Ostrzeżenie kompilatora (poziom 3) C5030|atrybut "*Attribute*" nie został rozpoznany|
|Ostrzeżenie kompilatora (poziom 4) C5031|Ostrzeżenie #pragma (pop): dopuszczalna niezgodność, usuwanie stan ostrzeżenia wypychane w innym pliku|
|Ostrzeżenie kompilatora (poziom 4) C5032|Wykryto Ostrzeżenie #pragma (push) bez odpowiadającego mu #pragma ostrzeżenie (pop)|
|Ostrzeżenie kompilatora (poziom 1) C5033|"*Storage-Class*" nie jest już obsługiwaną klasą magazynu|
|Ostrzeżenie kompilatora C5034|Użycie wewnętrznego elementu "*wewnętrzna*" powoduje skompilowanie *funkcji* funkcji jako kodu gościa|
|Ostrzeżenie kompilatora C5035|Użycie funkcji "*Feature*" powoduje skompilowanie *funkcji* funkcji jako kodu gościa|
|Ostrzeżenie kompilatora (poziom 1) C5036|Konwersja wskaźnika funkcji typu VarArgs podczas kompilowania z/Hybrid: x86arm64 "*Type1*" do "*Type2*"|
|Ostrzeżenie kompilatora (error) C5037|"*member-Function*": Definicja poza wierszem elementu członkowskiego szablonu klasy nie może mieć argumentów domyślnych|
|[Ostrzeżenie kompilatora (poziom 4) C5038](c5038.md)|składowa danych "*member1*" zostanie zainicjowana po elemencie członkowskim danych "*member2*"|
|Ostrzeżenie kompilatora (poziom 4) C5039|"*Function*": wskaźnik lub odwołanie do potencjalnie wyrzucanej funkcji, która została przeniesiona do funkcji extern C w EHC. Niezdefiniowane zachowanie może wystąpić, jeśli ta funkcja zgłosi wyjątek.|
|Ostrzeżenie kompilatora (poziom 3) C5040|dynamiczne specyfikacje wyjątków są prawidłowe tylko w języku C++ 14 i starszych wersjach. traktowanie jako noexcept (false)|
|Ostrzeżenie kompilatora (poziom 1) C5041|"*Definicja*": Definicja poza wierszem elementu członkowskiego danych statycznych constexpr nie jest wymagana i jest przestarzała w języku c++ 17|
|Ostrzeżenie kompilatora (poziom 3) C5042|"*Deklaracja*": deklaracje funkcji w zakresie bloku nie mogą być określone jako "inline" w standardzie C++; Usuń specyfikator "inline"|
|Ostrzeżenie kompilatora (poziom 2) C5043|"*Specyfikacja*": Specyfikacja wyjątku nie jest zgodna z poprzednią deklaracją|
|Ostrzeżenie kompilatora (poziom 4) C5044|Argument dla *opcji* wiersza polecenia*wskazuje ścieżkę,* która nie istnieje|
| [Ostrzeżenie kompilatora C5045](c5045.md) | Kompilator wstawi środki zaradcze Spectre na potrzeby ładowania pamięci, jeśli określono przełącznik/Qspectre |
| [Ostrzeżenie kompilatora (poziom 2) C5046](c5046.md) | "*Function*": Nie zdefiniowano symbolu powiązanego z typem z wewnętrznym powiązaniem |
| Ostrzeżenie kompilatora (poziom 1) C5047 | Użycie niestandardowych \_ \_Jeśliistniejezmodułaminiejestobsługiwane\_ |
| Ostrzeżenie kompilatora (poziom 1) C5048 | Użycie makra "*Macroname*" może spowodować niedeterministyczne dane wyjściowe |
| Ostrzeżenie kompilatora (poziom 1) C5049 | "*String*": Osadzenie pełnej ścieżki może spowodować wyjście zależne od maszyny |
| Ostrzeżenie kompilatora (poziom 1) C5050 | Możliwe niezgodne środowisko podczas importowania modułu "*module_name*": *problem* |
| Ostrzeżenie kompilatora (poziom 1) C5100 | \_\_Argumenty\_\_ VAsązarezerwowanedoużyciawmakrachwariadyczne\_ |
| Ostrzeżenie kompilatora (poziom 1) C5101 | Użycie dyrektywy preprocesora w liście argumentów makra przypominającej funkcję jest niezdefiniowane zachowanie |
| Ostrzeżenie kompilatora (poziom 1) C5102 | ignorowanie nieprawidłowej definicji makra wiersza polecenia "*Value*" |
| Ostrzeżenie kompilatora (poziom 1) C5103 | wklejanie elementów "*token1*" i "*token2*" nie powoduje prawidłowego tokenu przetwarzania wstępnego |
| Ostrzeżenie kompilatora (poziom 1) C5104 | znaleziono "*ciąg1*#*ciąg2*" na liście zastąpień makra, czy chodziło o "*ciąg1*" "#*ciąg2*"? |
| [Ostrzeżenie kompilatora (poziom 1) C5105](c5105.md) | niezdefiniowane zachowanie podczas tworzenia makra "defined" |
| Ostrzeżenie kompilatora (poziom 1) C5106 | makro ponownie zdefiniowane z innymi nazwami parametrów |
| Ostrzeżenie kompilatora (poziom 1) C5107 | brak zamykającego znaku "*char*" |

## <a name="see-also"></a>Zobacz także

[Błędy iC++ ostrzeżenia narzędzi języka C/kompilatora i kompilacji](../compiler-errors-1/c-cpp-build-errors.md) \
[Ostrzeżenia kompilatora C4000-C5999](compiler-warnings-c4000-c5999.md)
