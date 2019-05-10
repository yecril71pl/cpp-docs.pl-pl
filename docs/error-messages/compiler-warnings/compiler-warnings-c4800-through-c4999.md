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
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
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
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
ms.openlocfilehash: 93ff809d640efab6852e855f85e7b6e0109d9c1d
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857443"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Ostrzeżenia kompilatora — od C4800 do C5999

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty ostrzegawcze, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Komunikaty ostrzegawcze

|Ostrzeżenie|Message|
|-------------|------------|
|[Ostrzeżenie kompilatora (poziom 4) C4800](compiler-warning-level-3-c4800.md)| Niejawna konwersja z "*typu*" na wartość logiczna. Prawdopodobieństwo utraty informacji możliwych |
|[Ostrzeżenie kompilatora (poziom 1) C4803](compiler-warning-level-1-c4803.md)|"*metoda*": podniesiona metoda ma klasę magazynu inną od zdarzenia, "*zdarzeń*"|
|[Ostrzeżenie kompilatora (poziom 1) C4804](compiler-warning-level-1-c4804.md)|"*operacji*": niebezpieczne użycie typu "bool" w operacji|
|[Ostrzeżenie kompilatora (poziom 1) C4805](compiler-warning-level-1-c4805.md)|"*operacji*": niebezpieczne połączenie typu "*type1*"i typie"*type2*" w operacji|
|[Ostrzeżenie kompilatora (poziom 1) C4806](compiler-warning-level-1-c4806.md)|"*operacji*": niebezpieczna operacja: żadna wartość typu "*type1*"podwyższona do typu"*type2*" może być równa podanej stałej|
|[Ostrzeżenie kompilatora (poziom 1) C4807](compiler-warning-level-1-c4807.md)|"*operacji*": niebezpieczne połączenie typu "*type1*"i podpisany pola bitowego typu"*type2*"|
|Ostrzeżenie kompilatora (poziom 1) C4808|przypadek "*wartość*" jest nieprawidłowa wartość dla warunku instrukcji switch typu "bool"|
|Ostrzeżenie kompilatora (poziom 1) C4809|Instrukcja switch zawiera etykietę nadmiarowy "default"; podane są wszystkie możliwe etykiety "case"|
|[Ostrzeżenie kompilatora (poziom 1) C4810](compiler-warning-level-1-c4810.md)|Wartość dyrektywy pragma pack(show) == n|
|[Ostrzeżenie kompilatora (poziom 1) C4811](compiler-warning-level-1-c4811.md)|Wartość dyrektywy pragma conform (forScope, show) == wartość|
|[Ostrzeżenie kompilatora (poziom 1) C4812](compiler-warning-level-1-c4812.md)|przestarzała deklaracja stylu: Użyj "*new_syntax*" zamiast niego|
|[Ostrzeżenie kompilatora (poziom 1) C4813](compiler-warning-level-1-c4813.md)|"*funkcja*": funkcja zaprzyjaźniona klasy lokalnej musi musiała zostać poprzednio zadeklarowana|
|[Ostrzeżenie kompilatora (poziom 4) C4816](compiler-warning-level-4-c4816.md)|"*param*": parametr ma tablicę o rozmiarze zerowym, która zostanie obcięta (chyba że obiekt jest przekazywany przez odwołanie)|
|[Ostrzeżenie kompilatora (poziom 1) C4817](compiler-warning-level-1-c4817.md)|"*elementu członkowskiego*": niedozwolone użycie "." na dostęp do tej składowej, zostało zastąpione przez kompilator za pomocą "->"|
|[Ostrzeżenie kompilatora (poziom 1) C4819](compiler-warning-level-1-c4819.md)|Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (liczba). Zapisz plik w formacie Unicode, aby zapobiec utracie danych|
|[Ostrzeżenie kompilatora (poziom 4) C4820](compiler-warning-level-4-c4820.md)|"*bajtów*"bajtów dopełnienie dodane po konstrukcji"*member_name*"|
|[Ostrzeżenie kompilatora (poziom 1) C4821](compiler-warning-level-1-c4821.md)|Nie można określić typu kodowania Unicode, Zapisz plik z podpisem (znacznik BOM)|
|[Ostrzeżenie kompilatora (poziom 1) C4822](compiler-warning-level-1-c4822.md)|"Funkcja elementu członkowskiego": funkcja składowa klasy lokalnej nie ma treści|
|[Ostrzeżenie kompilatora (poziom 3) C4823](compiler-warning-level-3-c4823.md)|"*funkcja*": używa, ale operacja unwind unieruchamiania wskaźników semantyki nie są włączone. Rozważ użycie opcji/eha|
|Ostrzeżenie kompilatora (poziom 2) C4826|Konwersja z "*type1*"to"*type2*' jest rozszerzona o znak. Może to spowodować nieoczekiwane zachowanie.|
|Ostrzeżenie kompilatora (poziom 3) C4827|Publiczne Metoda 'ToString' o 0 parametrach powinna być oznaczona jako virtual i zastąpienia|
|[Ostrzeżenie kompilatora (poziom 1) C4829](compiler-warning-level-1-c4829.md)|Prawdopodobnie niepoprawne parametry funkcji głównego. Należy wziąć pod uwagę "int głównego (Platform::Array\<Platform::String ^ > ^ argv)"|
|[Ostrzeżenie kompilatora (poziom 1) C4835](compiler-warning-level-1-c4835.md)|"*zmiennej*": Inicjator dla eksportowanych danych nie będzie działać, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta|
|Ostrzeżenie kompilatora (poziom 4) C4837|Wykryto trójznak: "? *znak*"zastępuje"*znak*"|
|[Ostrzeżenie kompilatora (poziom 1) C4838](compiler-warning-level-1-c4838.md)|Konwersja z "*typ_1*"to"*typ_2*" wymaga konwersji zawężającej|
|[Ostrzeżenie kompilatora (poziom 3) C4839](compiler-warning-level-3-c4839.md)|niestandardowe użycie klasy*typu*"jako argumentu do funkcji ze zmienną liczbą argumentów|
|[Ostrzeżenie kompilatora (poziom 4) C4840](compiler-warning-level-4-c4840.md)|nieprzenośne użycie klasy*typu*"jako argumentu do funkcji ze zmienną liczbą argumentów|
|Ostrzeżenie kompilatora (poziom 4) C4841|użyto niestandardowego rozszerzenia: desygnator złożonej składowej użyty w makrze offsetof|
|Ostrzeżenie kompilatora (poziom 4) C4842|nie gwarantuje wynik makra "offsetof" zastosować do typu używającego wielu dziedziczeń będzie spójny między wydaniami kompilatora|
|C4843 ostrzeżenia kompilatora|"*type1*": Procedura obsługi wyjątków odwołania do typu funkcji lub tablicy jest nieosiągalna, użyj "*type2*" zamiast niego|
|C4844 ostrzeżenia kompilatora|"Eksportuj modułu *nazwa_modułu*;" jest teraz preferowana składnia do deklarowania interfejsu modułu|
| Ostrzeżenie kompilatora (poziom 4) C4845 | "\_\_declspec (nie\_init\_all)" jest ignorowana, jeśli "/ d1initall\[0\|1\|2\|3]' nie została określona w wierszu polecenia |
| Ostrzeżenie kompilatora (poziom 4) C4846 | "*wartość*" nie jest prawidłowym argumentem dla "/ d1initall": właściwości wiersza polecenia są ignorowane |
| Ostrzeżenie kompilatora (poziom 4) C4847 | "\_\_declspec (nie\_init\_all)" będzie stosowany tylko do funkcji, typem klasy lub zmiennej lokalnej: ignorowane |
| Ostrzeżenie kompilatora (poziom 1) C4848 | Obsługa atrybut standardowy "nie\_unikatowy\_adres w języku C ++ 17 i wcześniejszych wersjach to rozszerzenie dostawcy |
|[Ostrzeżenie kompilatora (poziom 4) C4866](c4866.md)| Kompilator może nie wymusić kolejności oceny od lewej do prawej dla wywołania *operator_name*|
|[Kompilator ostrzeżenie C4867 (błąd)](compiler-warning-c4867.md)|"*funkcja*": wywołania funkcji brakuje listy argumentów; Użyj "*wywołania*" Aby utworzyć wskaźnik do składowej|
|[Ostrzeżenie kompilatora (poziom 4) C4868](compiler-warning-c4868.md)|"_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej w listy inicjowania w nawiasach|
|Ostrzeżenie kompilatora (poziom 2) C4872|dzielenie liczby zmiennoprzecinkowej przez zero wykryta podczas kompilacji wykresu wywołań dla concurrency::parallel_for_each: "*lokalizacji*"|
|Ostrzeżenie kompilatora (poziom 1) C4880|Rzutowanie z "const *typ_1*"to"*typ_2*": stałości ze wskaźnika lub odwołania może spowodować niezdefiniowane zachowanie w zastrzeżonej funkcji amp|
|Ostrzeżenie kompilatora (poziom 4) C4881|Konstruktor i/lub destruktor nie zostaną wywołane dla zmiennej tile_static "*zmiennej*"|
|Ostrzeżenie kompilatora (poziom 1) C4882|przekazywanie funktorów z operatorami niestały wywołania do concurrency::parallel_for_each jest przestarzałe|
|[C4900 ostrzeżenia kompilatora](compiler-warning-level-1-c4900.md)|Niezgodność IL między "*tool1*"version"*version1*"i"*tool2*"version"*version2*"|
|[Ostrzeżenie kompilatora (poziom 1) C4905](compiler-warning-level-1-c4905.md)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[Ostrzeżenie kompilatora (poziom 1) C4906](compiler-warning-level-1-c4906.md)|literał ciągu rzutowany na 'LPWSTR'|
|[Ostrzeżenie kompilatora (poziom 1) C4910](compiler-warning-level-1-c4910.md)|"\<identyfikator >: deklaracje" __declspec(dllexport)"i"extern"są niezgodne z jawnym wystąpieniem|
|[Ostrzeżenie kompilatora (poziom 1) C4912](compiler-warning-level-1-c4912.md)|"*atrybut*": atrybut ma niezdefiniowane zachowanie w zagnieżdżonym UDT|
|[Ostrzeżenie kompilatora (poziom 4) C4913](compiler-warning-level-4-c4913.md)|Użytkownik zdefiniowany operator binarny "," istnieje, ale żadne przeciążenie nie może konwertować wszystkich argumentów operacji, domyślnego, wbudowanego operatora binarnego "," używane|
|Ostrzeżenie kompilatora (poziom 1) C4916|Aby uzyskać identyfikator dispid, "*opis*": musi zostać wprowadzony przez interfejs|
|[Ostrzeżenie kompilatora (poziom 1) C4917](compiler-warning-level-1-c4917.md)|"*deklaratora*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw|
|[Ostrzeżenie kompilatora (poziom 4) C4918](compiler-warning-level-4-c4918.md)|"*znak*": nieprawidłowy znak na liście optymalizacji pragma|
|[Ostrzeżenie kompilatora (poziom 1) C4920](compiler-warning-level-1-c4920.md)|member_1 elementu członkowskiego wyliczenia typu wyliczeniowego = value_1 już występuje w typie wyliczeniowym wyliczenia jako member_2 = value_2|
|Ostrzeżenie kompilatora (poziom 3) C4921|"*opis*": wartość atrybutu "*atrybut*' nie powinien być określony wielokrotnie|
|[Ostrzeżenie kompilatora (poziom 1) C4925](compiler-warning-level-1-c4925.md)|"*metoda*": metoda interfejsu dispinterface nie może być wywoływana ze skryptu|
|[Ostrzeżenie kompilatora (poziom 1) C4926](compiler-warning-level-1-c4926.md)|"*identyfikator*": symbol jest już zdefiniowany: atrybuty zostały zignorowane|
|[Ostrzeżenie kompilatora (poziom 1) C4927](compiler-warning-level-1-c4927.md)|Niedozwolona konwersja; więcej niż jedna konwersja zdefiniowana przez użytkownika została zastosowana niejawnie|
|[Ostrzeżenie kompilatora (poziom 1) C4928](compiler-warning-level-1-c4928.md)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[Ostrzeżenie kompilatora (poziom 1) C4929](compiler-warning-level-1-c4929.md)|"*pliku*": Biblioteka typów zawiera Unię; ignorowanie kwalifikatora "embedded_idl"|
|[Ostrzeżenie kompilatora (poziom 1) C4930](compiler-warning-level-1-c4930.md)|"*prototypu*": prototypowana funkcja nie wywołana (czy definicja zmiennej była przeznaczona?)|
|[Ostrzeżenie kompilatora (poziom 4) C4931](compiler-warning-level-4-c4931.md)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|[Ostrzeżenie kompilatora (poziom 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*identyfikator*) i \__identyfikatorów (*identyfikator*) są nierozróżnialne|
|Ostrzeżenie kompilatora (poziom 1) C4934|"__delegate(multicast)" jest przestarzała, użyj "\__delegate" zamiast niego|
|[Ostrzeżenie kompilatora (poziom 1) C4935](compiler-warning-level-1-c4935.md)|Specyfikator dostępu do zestawu zmodyfikowany z "*dostępu*"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4936](compiler-warning-c4936.md)|Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure|
|[Ostrzeżenie kompilatora (poziom 4) C4937](compiler-warning-level-4-c4937.md)|"*text1*"i"*text2*"są nierozróżnialne jako argumenty"*dyrektywy*"|
|[Ostrzeżenie kompilatora (poziom 4) C4938](compiler-warning-level-4-c4938.md)|"*var*": Zmiennoprzecinkowe zmiennej redukcji punktu może spowodować niespójne wyniki w obszarze/FP: strict lub #pragma fenv_access|
|[C4939 ostrzeżenia kompilatora](compiler-warning-level-1-c4939.md)|#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++|
|[Ostrzeżenie kompilatora (poziom 1) C4944](compiler-warning-level-1-c4944.md)|"*symbol*": nie można zaimportować symbolu z "*assembly1*": jako*symbol*"już istnieje w bieżącym zakresie|
|[Ostrzeżenie kompilatora (poziom 1) C4945](compiler-warning-level-1-c4945.md)|"*symbol*": nie można zaimportować symbolu z "*assembly1*": jako*symbol*"został już zaimportowany z innego zestawu"*assembly2* '|
|[Ostrzeżenie kompilatora (poziom 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast używane między pokrewnymi klasami: '*klasa1*"i"*klasa2*"|
|[Ostrzeżenie kompilatora (poziom 1) C4947](compiler-warning-level-1-c4947.md)|"*type_or_member*": oznaczony jako przestarzały|
|[Ostrzeżenie kompilatora (poziom 2) C4948](compiler-warning-level-2-c4948.md)|zwracany typ "*akcesor*" jest niezgodny z typem ostatniego parametru odpowiadającej mu metody ustawiającej|
|[Ostrzeżenie kompilatora (poziom 1 i 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4950](compiler-warning-c4950.md)|"*type_or_member*": oznaczony jako przestarzały|
|[Ostrzeżenie kompilatora (poziom 1) C4951](compiler-warning-level-1-c4951.md)|"*funkcja*" został wyedytowany od profilu dane zostały zebrane, nieużywane dane profilu funkcji|
|[Ostrzeżenie kompilatora (poziom 1) C4952](compiler-warning-level-1-c4952.md)|"*funkcja*": nie znaleziono danych profilowych w bazie danych programu "*pgd_file*"|
|[Ostrzeżenie kompilatora (poziom 1) C4953](compiler-warning-level-1-c4953.md)|Wbudowany "*funkcja*" został wyedytowany od profilu dane zostały zebrane, dane profilu nieużywane|
|C4954 ostrzeżenia kompilatora|"*funkcja*": nieprofilowany (zawiera wyrażenie switch __int64)|
|C4955 ostrzeżenia kompilatora|"*import2*": Importowanie zostało zignorowane; zaimportowano już z "*import1*"|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4956](compiler-warning-c4956.md)|"*typu*": ten typ nie jest możliwe do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4957](compiler-warning-c4957.md)|"*rzutowania*": jawne rzutowanie z "*cast_from*"to"*cast_to*" nie jest możliwe do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4958](compiler-warning-c4958.md)|"*operacji*": arytmetyka wskaźnika nie jest możliwe do zweryfikowania|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4959](compiler-warning-c4959.md)|Nie można zdefiniować typu niezarządzanego "*typu*" w/CLR: Safe, ponieważ dostęp do jego składowych daje nieweryfikowalny kod|
|[Ostrzeżenie kompilatora (poziom 4) C4960](compiler-warning-level-4-c4960.md)|"*funkcja*" jest zbyt duży do profilowania|
|[Ostrzeżenie kompilatora (poziom 1) C4961](compiler-warning-c4961.md)|Dane profilowe nie zostały scalone z "plik .pgd", profilowana Optymalizacja została wyłączona|
|[Ostrzeżenie kompilatora (poziom 4) C4962](compiler-warning-c4962.md)|"*funkcja*": Optymalizacje sterowane profilem wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu|
|Ostrzeżenie kompilatora (poziom 1) C4963|"*opis*": nie znaleziono danych profilowych; różne opcje kompilatora zostały użyte w kompilacji instrumentowanej|
|[Ostrzeżenie kompilatora (poziom 1) C4964](compiler-warning-level-1-c4964.md)|Opcje optymalizacji nie zostały określone; informacje profilowe nie zostaną zebrane.|
|[Ostrzeżenie kompilatora (poziom 1) C4965](compiler-warning-level-1-c4965.md)|niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania|
|Ostrzeżenie kompilatora (poziom 1) C4966|"*funkcja*" ma adnotację __code_seg z nieobsługiwaną nazwą segmentu, adnotacja została zignorowana|
|C4970 ostrzeżenia kompilatora|Konstruktor delegaty: obiekt docelowy ignorowane od "*typu*" jest statyczny|
|Ostrzeżenie kompilatora (poziom 1) C4971|Kolejność argumentów: \<obiekt docelowy >, \<docelowa funkcja > dla konstruktora delegaty jest przestarzały, użyj \<docelowa funkcja >, \<obiekt docelowy = "" >|
|[Ostrzeżenie kompilatora (poziom 1, błąd) C4972](compiler-warning-c4972.md)|Nie jest bezpośrednia modyfikacja lub traktowanie wyniku operacji odpakowywania wartościowanego lewostronnie|
|Ostrzeżenie kompilatora (poziom 1) C4973|"*symbol*": oznaczone jako przestarzałe|
|Ostrzeżenie kompilatora (poziom 1) C4974|"*symbol*": oznaczone jako przestarzałe|
|Ostrzeżenie kompilatora (poziom 3) C4981|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ zawiera semantykę wyjątku|
|Ostrzeżenie kompilatora (poziom 3) C4985|Nazwa symbolu ": Brak atrybutów w poprzedniej deklaracji.|
|[C4986 ostrzeżenia kompilatora](compiler-warning-c4986.md)|"*deklaracji*': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją|
|Ostrzeżenie kompilatora (poziom 4) C4987|użyto rozszerzenia niestandardowego: 'throw (...)'|
|Ostrzeżenie kompilatora (poziom 4) C4988|"*zmiennej*": Zmienna zadeklarowana poza zakresem klasy/funkcji|
|Ostrzeżenie kompilatora (poziom 4) C4989|"*typu*": Typ ma definicje powodujące konflikt.|
|Ostrzeżenie kompilatora (poziom 3) C4990|Warbird: *message*|
|Ostrzeżenie kompilatora (poziom 3) C4991|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ poziom ochrony przed wstawianiem do treści jest większy niż element nadrzędny|
|Ostrzeżenie kompilatora (poziom 3) C4992|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ zawiera wstawiony zestaw, który nie może być chroniony|
|[Ostrzeżenie kompilatora (poziom 3) C4995](compiler-warning-level-3-c4995.md)|"*funkcja*': nazwa została oznaczona jako przestarzała #pragma|
|[Ostrzeżenie kompilatora (poziom 3) C4996](compiler-warning-level-3-c4996.md)|"*opis*": *wiadomości*|
|[Ostrzeżenie kompilatora (poziom 1) C4997](compiler-warning-level-1-c4997.md)|"*klasy*": klasa coclass nie implementuje interfejsu COM lub pseudointerfejsu|
|Ostrzeżenie kompilatora (poziom 1) C4998|Oczekiwanie nie powiodło się: *oczekiwania*(*wartość*)|
|[C4999 ostrzeżenia kompilatora](compiler-warning-level-1-c4999.md)|Nieznane ostrzeżenie, wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|C5022 ostrzeżenia kompilatora|"*typu*": określono wiele konstruktorów przenoszenia|
|C5023 ostrzeżenia kompilatora|"*typu*": określono wiele operatorów przypisania przenoszenia|
|Ostrzeżenie kompilatora (poziom 4) C5024|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 4) C5025|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i 4) C5026|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i 4) C5027|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1) C5028|"*nazwa*": Wyrównanie określone we wcześniejszej deklaracji (*numer*) nie jest określona w definicji|
|Ostrzeżenie kompilatora (poziom 4) C5029|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, składowych danych i tylko dla typów tagów|
|Ostrzeżenie kompilatora (poziom 3) C5030|atrybut "*atrybut*" nie został rozpoznany|
|Ostrzeżenie kompilatora (poziom 4) C5031|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu|
|Ostrzeżenie kompilatora (poziom 4) C5032|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop)|
|Ostrzeżenie kompilatora (poziom 1) C5033|"*klasę magazynu*" nie jest już obsługiwaną klasą magazynu|
|C5034 ostrzeżenia kompilatora|Użyj wewnętrznych "*wewnętrzne*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa|
|C5035 ostrzeżenia kompilatora|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa|
|Ostrzeżenie kompilatora (poziom 1) C5036|Konwersja wskaźnika funkcji typu varargs podczas kompilowania za pomocą /hybrid:x86arm64 "*type1*"to"*type2*"|
|Ostrzeżenie kompilatora (błąd) C5037|"*funkcja elementu członkowskiego*": definicja końca wiersza składowej szablonu klasy nie może mieć argumentów domyślnych|
|[Ostrzeżenie kompilatora (poziom 4) C5038](c5038.md)|element członkowski danych "*Członek1*"zostanie zainicjowany po element członkowski danych"*członek2*"|
|Ostrzeżenie kompilatora (poziom 4) C5039|"*funkcja*": wskaźnik lub odwołanie do funkcji potencjalnie zgłaszającej wyjątek przekazano do funkcji extern języka C w ramach - EHc. Niezdefiniowane zachowanie może wystąpić, jeśli ta funkcja zgłosi wyjątek.|
|Ostrzeżenie kompilatora (poziom 3) C5040|specyfikacje wyjątków dynamicznych są prawidłowe tylko w języku C ++ 14 i starszych wersji; traktowanie jako opcja noexcept(false)|
|Ostrzeżenie kompilatora (poziom 1) C5041|"*definicji*": definicja końca wiersza dla składowej danych statycznych constexpr jest niepotrzebna i jest przestarzała w języku C ++ 17|
|Ostrzeżenie kompilatora (poziom 3) C5042|"*deklaracji*": deklaracje funkcji w zakresie bloku nie może być określone jako "inline" w standardzie języka C++; Usuń specyfikator "inline"|
|Ostrzeżenie kompilatora (poziom 2) C5043|"*specyfikacji*': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją|
|Ostrzeżenie kompilatora (poziom 4) C5044|Argument opcji wiersza polecenia *opcji* wskazuje ścieżkę "*ścieżki*' który nie istnieje|
|[C5045 ostrzeżenia kompilatora](c5045.md)|Kompilator wstawi zaradcze dla luki Spectre dla obciążenia pamięci Jeśli przełącznik/qspectre określonych|
|[Ostrzeżenie kompilatora (poziom 2) C5046](c5046.md)|"*funkcja*": Obejmujące typu z wewnętrznym powiązaniem Niezdefiniowany symbol|
| Ostrzeżenie kompilatora (poziom 1) C5047 | Korzystanie z niestandardowych \_ \_Jeśli\_istnieje przy użyciu modułów nie jest obsługiwane |
| Ostrzeżenie kompilatora (poziom 1) C5048 | Użyj makra "*makra*" może spowodować-deterministycznych danych wyjściowych |
| Ostrzeżenie kompilatora (poziom 1) C5049 | "*ciąg*": Pełna ścieżka do osadzania może spowodować w danych wyjściowych zależnych od maszyny |
| Ostrzeżenie kompilatora (poziom 1) C5050 | Możliwe niezgodne środowisko podczas importowania modułu "*nazwa_modułu*": *problem* |
| Ostrzeżenie kompilatora (poziom 1) C5100 | \_\_Oceny luk w zabezpieczeniach\_ARGS\_ \_ jest zarezerwowany do użytku w makra wariadyczne |
| Ostrzeżenie kompilatora (poziom 1) C5101 | Użycie dyrektywy preprocesora na liście argumentów funkcyjne makro jest niezdefiniowane zachowanie |
| Ostrzeżenie kompilatora (poziom 1) C5102 | ignorowanie nieprawidłowa wiersza polecenia definicja makra "*wartość*" |
| Ostrzeżenie kompilatora (poziom 1) C5103 | wklejanie "*token1*"i"*token2*" nie powoduje prawidłowy token przetwarzania wstępnego |
| Ostrzeżenie kompilatora (poziom 1) C5104 | znaleziono "*ciąg1*#*ciąg2*"na liście zastąpienie makra, czy chodziło Ci o"*ciąg1*" "#*ciąg2*"? |
| Ostrzeżenie kompilatora (poziom 1) C5105 | rozwinięciu makra w produkcji "defined" ma niezdefiniowane zachowanie |
| Ostrzeżenie kompilatora (poziom 1) C5106 | ponownie zdefiniowany przy użyciu nazwy różnych parametrów — makro |
| Ostrzeżenie kompilatora (poziom 1) C5107 | Brak przerywa "*char*" znak |

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Ostrzeżenia kompilatora od C4000 - C5999](compiler-warnings-c4000-c5999.md)
