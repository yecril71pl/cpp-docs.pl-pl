---
title: "C4800 ostrzeżenia kompilatora za pośrednictwem C5999 | Dokumentacja firmy Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4840
- C4841
- C4842
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
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
- C4997
- C4998
- C4999
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
- C5038
dev_langs: C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bf919fbb1959af6fad031a7f32262466f6f49ff
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4800-through-c5999"></a>C4800 ostrzeżenia kompilatora za pośrednictwem C5999

Artykuły w tej części dokumentacji zawierają informacje o podzbioru ostrzeżeń kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w oknie danych wyjściowych w programie Visual Studio można wybrać numer błędu, a następnie naciśnij klawisz F1.

> [!NOTE]
> Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błąd lub ostrzeżenie jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).

## <a name="in-this-section"></a>W tej sekcji

|Ostrzeżenie|Komunikat|
|-------------|-------------|
|[Ostrzeżenie (poziom 3) kompilatora C4800](compiler-warning-level-3-c4800.md)|'type': Wymuszanie wartości logicznej "true" lub "fałsz" (ostrzeżenie wydajności)|
|[Kompilator C4803 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4803.md)|"metoda": podniesiona metoda ma klasę magazynu inną od zdarzenia, "event"|
|[Kompilator C4804 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4804.md)|"operacji": niebezpieczne użycie typu "bool" w operacji|
|[Kompilator C4805 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4805.md)|"operacji": niebezpieczne połączenie typu "type" i typie "type" w operacji|
|Ostrzeżenie kompilatora (poziom 1) C4806|"operacji": niebezpieczna operacja: żadna wartość typu "type", po której poziom jest podwyższany do typu "type" nie może być równa podanej stałej|
|Ostrzeżenie kompilatora (poziom 1) C4807|"operacji": niebezpieczne połączenie typu "type" oraz pola bitowego podpisem typu "type"|
|Ostrzeżenie kompilatora (poziom 1) C4808|przypadek "wartość" nie jest prawidłową wartością dla warunku instrukcji switch typu "bool"|
|Ostrzeżenie kompilatora (poziom 1) C4809|Instrukcja Switch ma etykiety nadmiarowe "default"; podane są wszystkie możliwe etykiety "case"|
|Ostrzeżenie kompilatora (poziom 1) C4810|Wartość dyrektywy pragma pack(show) == n|
|Ostrzeżenie kompilatora (poziom 1) C4811|Wartość dyrektywy pragma conform (forScope, show) == wartość|
|Ostrzeżenie kompilatora (poziom 1) C4812|przestarzała deklaracja stylu: zamiast tego użyj "new_syntax"|
|Ostrzeżenie kompilatora (poziom 1) C4813|"Funkcja": funkcja zaprzyjaźniona klasy lokalnej zostało wcześniej zadeklarowane|
|Ostrzeżenie kompilatora (poziom 4) C4816|"param": parametr ma zerowy rozmiar tablicy, która zostanie obcięta (chyba że obiekt jest przekazywana przez odwołanie)|
|Ostrzeżenie kompilatora (poziom 1) C4817|"członek": niedozwolone użycie "." można uzyskać dostępu do tego elementu członkowskiego; Kompilator zastąpione "->"|
|[Kompilator C4819 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4819.md)|Plik zawiera znak, który nie może być reprezentowany w bieżącej stronie kodowej (numer). Zapisz plik w formacie Unicode, aby zapobiec utracie danych|
|[Kompilator C4820 ostrzegawcze (poziom 4)](compiler-warning-level-4-c4820.md)|'bajty' dopełnienie bajtami dodane po konstrukcji 'member_name'|
|[Kompilator C4821 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4821.md)|Nie można określić typu kodowania Unicode, Zapisz plik z podpisem (znacznik BOM)|
|Ostrzeżenie kompilatora (poziom 1) C4822|"Funkcja członkowska": funkcja członkowska klasy lokalnej nie ma treści|
|[Kompilator C4823 ostrzegawcze (poziom 3)](compiler-warning-level-3-c4823.md)|"Funkcja": używa wskaźników przypinanych ale unwind semantyki nie są włączone. Należy rozważyć użycie opcji/eha|
|Ostrzeżenie kompilatora (poziom 2) C4826|Konwersja z "*type1*"do"*type2*" jest ze znakiem. Może to spowodować nieoczekiwane zachowanie.|
|Ostrzeżenie kompilatora (poziom 3) C4827|Publiczną metodę 'ToString' o 0 parametrach powinna być oznaczona jako virtual i override|
|[Kompilator C4829 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4829.md)|Prawdopodobnie niepoprawne parametry funkcji main. Należy wziąć pod uwagę "int main (Platform::Array\<Platform::String ^ > ^ ARGV —)"|
|[Kompilator C4835 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4835.md)|"Zmienna": Inicjator dla eksportowanych danych nie zostaną uruchomione, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta|
|Ostrzeżenie kompilatora (poziom 4) C4837|Wykryto — trigram: "? *znak*"zastąpione przez"*znak*"|
|[Kompilator C4838 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4838.md)|Konwersja z "type_1" na "type_2" wymaga konwersji zawężającej|
|[Ostrzeżenie kompilatora (poziom 3) C4839](compiler-warning-level-3-c4839.md)|Użycie niestandardowej klasy*typu*"jako argument do funkcji ze zmienną liczbą argumentów|
|Ostrzeżenie kompilatora (poziom 4) C4840|Użycie nieprzenośne klasy*typu*"jako argument do funkcji ze zmienną liczbą argumentów|
|Ostrzeżenie kompilatora (poziom 4) C4841|użyte rozszerzenie niestandardowe: używane w makra offsetof oznaczeniem złożony element członkowski|
|Ostrzeżenie kompilatora (poziom 4) C4842|Aby było spójne między wersjami kompilatora nie jest gwarantowana wynik "makra offsetof" zastosowane do typu przy użyciu dziedziczenie wielokrotne|
|[Kompilator C4867 ostrzeżenie (błąd)](compiler-warning-c4867.md)|"Funkcja": wywołanie funkcji brakuje listy argumentów; Użyj "call", aby utworzyć wskaźnik do elementu członkowskiego|
|[Kompilator C4868 ostrzegawcze (poziom 4)](compiler-warning-c4868.md)|"_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjowanie w nawiasach klamrowych|
|Ostrzeżenie kompilatora (poziom 2) C4872|dzielenie liczby zmiennoprzecinkowej przez zero wykryta podczas kompilacji wykresu wywołań dla concurrency::parallel_for_each w:: "*lokalizacji*"|
|Ostrzeżenie kompilatora (poziom 1) C4880|Rzutowanie z "const type_1" na "type_2": odrzucenie stałości ze wskaźnika lub odwołania może spowodować niezdefiniowane zachowanie w zastrzeżonej funkcji amp|
|Ostrzeżenie kompilatora (poziom 4) C4881|Konstruktor i/lub destruktor nie zostaną wywołane dla zmiennej tile_static "Zmienna"|
|Ostrzeżenie kompilatora (poziom 1) C4882|przekazywanie funktorów z operatorami niestałymi wywołania do concurrency::parallel_for_each jest przestarzałe.|
|Ostrzeżenie C4900 kompilatora|Niezgodność IL "tool1" "version1" i "tool2" wersja "version2"|
|[Kompilator C4905 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4905.md)|literał ciągu dwubajtowego rzutowany na 'LPSTR'|
|[Kompilator C4906 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4906.md)|literał ciągu rzutowany na 'LPWSTR'|
|Ostrzeżenie kompilatora (poziom 1) C4910|"\<identyfikator >:"__declspec(dllexport)"i"extern"są niezgodne z jawnym wystąpieniem|
|Ostrzeżenie kompilatora (poziom 1) C4912|"attribute": atrybut ma niezdefiniowane zachowanie w zagnieżdżonym UDT|
|Ostrzeżenie kompilatora (poziom 4) C4913|Użytkownik zdefiniowany operator binarny "," istnieje, ale żadne przeciążenie nie może konwertować wszystkich argumentów operacji, domyślny wbudowany operator binarny "," używane|
|Ostrzeżenie kompilatora (poziom 1) C4916|Aby uzyskać identyfikator dispid, "*opis*": musi zostać wprowadzony przez interfejs|
|[Kompilator C4917 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4917.md)|"deklarator": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw|
|Ostrzeżenie kompilatora (poziom 4) C4918|"znak": nieprawidłowy znak na liście optymalizacji pragma|
|Ostrzeżenie kompilatora (poziom 1) C4920|member_1 elementu członkowskiego wyliczenia wyliczenia = value_1 już występuje w elemencie enum wyliczenia jako member_2 = value_2|
|Ostrzeżenie kompilatora (poziom 3) C4921|"*opis*": wartość atrybutu "*atrybutu*" nie powinna być określona wielokrotnie|
|Ostrzeżenie kompilatora (poziom 1) C4925|"metoda": metoda interfejsu dispinterface nie może być wywoływana ze skryptu|
|Ostrzeżenie kompilatora (poziom 1) C4926|'Identyfikator': symbol jest już zdefiniowany: atrybuty zostały zignorowane|
|[Kompilator C4927 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4927.md)|Niedozwolona konwersja; więcej niż jedna konwersja zdefiniowana przez użytkownika została zastosowana niejawnie|
|[Kompilator C4928 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4928.md)|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika|
|[Kompilator C4929 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4929.md)|'Plik': Biblioteka typów zawiera Unię; ignorowanie kwalifikatora "embedded_idl"|
|[Kompilator C4930 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4930.md)|"prototyp": prototypowana funkcja nie została wywołana (czy definicja zmiennej była przeznaczona?)|
|[Kompilator C4931 ostrzegawcze (poziom 4)](compiler-warning-level-4-c4931.md)|zakładamy, że biblioteka typów została zbudowana dla wskaźników liczba-bit|
|Ostrzeżenie kompilatora (poziom 4) C4932|__identifier (*identyfikator*) i \__identifier (*identyfikator*) są nierozróżnialne|
|Ostrzeżenie kompilatora (poziom 1) C4934|"__delegate(multicast)" jest przestarzała, użyj "\__delegate" zamiast niego|
|Ostrzeżenie kompilatora (poziom 1) C4935|Specyfikator dostępu do zestawu zmodyfikowany z "access"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4936|Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure|
|Ostrzeżenie kompilatora (poziom 4) C4937|"Tekst1" i "Tekst2" są nierozróżnialne jako argumenty "dyrektywy"|
|Ostrzeżenie kompilatora (poziom 4) C4938|"var": zmienna reduktywna przestawne może spowodować niespójne wyniki z opcją/FP: strict lub dyrektywą #pragma fenv_access|
|Ostrzeżenie C4939 kompilatora|#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++|
|Ostrzeżenie kompilatora (poziom 1) C4944|"symbol": nie można zaimportować symbolu z "zestaw1": ponieważ "symbol" już istnieje w bieżącym zakresie|
|[Kompilator C4945 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4945.md)|"symbol": nie można zaimportować symbolu z "zestaw1": ponieważ "symbol" został już zaimportowany z innego zestawu "assembly2"|
|[Kompilator C4946 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4946.md)|reinterpret_cast używane między pokrewnymi klasami: 'klasa1' i 'klasa2'|
|Ostrzeżenie kompilatora (poziom 1) C4947|"type_or_member": oznaczony jako przestarzały|
|[Kompilator C4948 ostrzegawcze (poziom 2)](compiler-warning-level-2-c4948.md)|zwracany typ "metody dostępu" jest niezgodny z typem ostatniego parametru odpowiadającej mu metody ustawiającej|
|[Kompilator C4949 ostrzegawcze (poziom 1 i 4)](compiler-warning-level-1-and-level-4-c4949.md)|dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4950|"type_or_member": oznaczony jako przestarzały|
|Ostrzeżenie kompilatora (poziom 1) C4951|"Funkcja" został wyedytowany od profil, który został zebrany danych, dane profilu funkcji nie zostały użyte|
|Ostrzeżenie kompilatora (poziom 1) C4952|"Funkcja": nie znaleziono danych profilowych w bazie danych programu "pgd_file"|
|Ostrzeżenie kompilatora (poziom 1) C4953|Element Wbudowywany "function" został wyedytowany od profil, który zebrania danych profilu dane nie zostały użyte|
|Ostrzeżenie C4954 kompilatora|"Funkcja": nieprofilowany (zawiera wyrażenie przełącznika __int64)|
|Ostrzeżenie C4955 kompilatora|"import2": importu ignorowane. zaimportowano już z "import1"|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4956|'type': ten typ nie jest możliwe do zweryfikowania|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4957|Instrukcja "cast": jawne rzutowanie z "rzutowanie z" na "cast_to" nie jest możliwe do zweryfikowania|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4958|"operacji": arytmetyka wskaźnika nie jest możliwe do zweryfikowania|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4959|Nie można zdefiniować niezarządzanego typu "type" w/CLR: Safe, ponieważ dostęp do jego elementów członkowskich implikuje kod niemożliwy do zweryfikowania|
|Ostrzeżenie kompilatora (poziom 4) C4960|"Funkcja" jest zbyt duży, aby zostać profilowanym|
|Ostrzeżenie kompilatora (poziom 1) C4961|Żadne dane profilu nie scalono "plik .pgd", profilowana Optymalizacja została wyłączona|
|Ostrzeżenie kompilatora (poziom 4) C4962|"Funkcja": profilowana Optymalizacja została wyłączona, ponieważ optymalizacje spowodowały niespójność danych profilu|
|Ostrzeżenie kompilatora (poziom 1) C4963|"*opis*": nie znaleziono danych profilowych; różne opcje kompilatora zostały użyte w kompilacji instrumentowanej|
|[Kompilator C4964 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4964.md)|Optymalizacja nie określono żadnych opcji; informacje o profilu nie będą zbierane.|
|[Kompilator C4965 ostrzegawcze (poziom 1)](compiler-warning-level-1-c4965.md)|niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania|
|Ostrzeżenie kompilatora (poziom 1) C4966|"*funkcja*" ma adnotację __code_seg z nieobsługiwaną nazwą segmentu, adnotacja została zignorowana|
|Ostrzeżenie C4970 kompilatora|Konstruktor delegata: obiekt docelowy ignorowane od "*typu*" jest statyczny|
|Ostrzeżenie kompilatora (poziom 1) C4971|Kolejność argumentów: \<obiektu docelowego >, \<docelowa funkcja > dla konstruktora delegaty jest przestarzały, użyj \<docelowa funkcja >, \<obiektu docelowego = "" >|
|Ostrzeżenie kompilatora (poziom 1, błąd) C4972|Nie jest bezpośrednia modyfikacja lub traktowanie wyniku operacji odpakowywania wartościowanego lewostronnie|
|Ostrzeżenie kompilatora (poziom 1) C4973|"*symbol*': oznaczono jako przestarzały|
|Ostrzeżenie kompilatora (poziom 1) C4974|"*symbol*': oznaczono jako przestarzały|
|Ostrzeżenie kompilatora (poziom 3) C4981|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie została wbudowana ponieważ zawiera ona semantyki wyjątku|
|Ostrzeżenie kompilatora (poziom 3) C4985|Nazwa symbolu ": Brak atrybutów w poprzedniej deklaracji.|
|[C4986 ostrzeżenia kompilatora](compiler-warning-c4986.md)|"*deklaracji*": specyfikacja wyjątku jest niezgodna z poprzednią deklaracją|
|Ostrzeżenie kompilatora (poziom 4) C4987|użyto rozszerzenia niestandardowego: 'throw (...)'|
|Ostrzeżenie kompilatora (poziom 4) C4988|"*zmiennej*": Zmienna zadeklarowana poza zakresem klasy/funkcji|
|Ostrzeżenie kompilatora (poziom 4) C4989|"*typu*": Typ ma definicje powodujące konflikt.|
|Ostrzeżenie kompilatora (poziom 3) C4990|Warbird: *wiadomości*|
|Ostrzeżenie kompilatora (poziom 3) C4991|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie została wbudowana ponieważ poziom ochrony przed wstawianiem do treści jest większy niż element nadrzędny|
|Ostrzeżenie kompilatora (poziom 3) C4992|Warbird: funkcja "*funkcja*" oznaczona jako __forceinline nie została wbudowana ponieważ zawiera wstawiony zestaw, który nie może być chroniony|
|[Kompilator C4995 ostrzegawcze (poziom 3)](compiler-warning-level-3-c4995.md)|"Funkcja": nazwa została oznaczona jako przestarzała #pragma|
|[Kompilator C4996 ostrzegawcze (poziom 3)](compiler-warning-level-3-c4996.md)|"*opis*": *wiadomości*|
|Ostrzeżenie kompilatora (poziom 1) C4997|"class": klasa coclass nie implementuje interfejsu COM lub pseudointerfejsu|
|Ostrzeżenie kompilatora (poziom 1) C4998|Nie można zrealizować oczekiwania: *oczekiwania*(*wartość*)|
|Ostrzeżenie C4999 kompilatora|Nieznane Ostrzeżenie Wybierz polecenie Pomoc techniczna w menu Pomoc programu Visual C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|Ostrzeżenie C5022 kompilatora|"*typu*": określono wiele konstruktorów przenoszenia|
|Ostrzeżenie C5023 kompilatora|"*typu*": określono wiele operatorów przypisania przenoszenia|
|Ostrzeżenie kompilatora (poziom 4) C5024|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 4) C5025|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i 4) C5026|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1 i 4) C5027|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty|
|Ostrzeżenie kompilatora (poziom 1) C5028|"*nazwa*": wyrównanie określone we wcześniejszej deklaracji (*numer*) nie jest określona w definicji|
|Ostrzeżenie kompilatora (poziom 4) C5029|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, elementów członkowskich danych i typów tagów tylko|
|Ostrzeżenie kompilatora (poziom 3) C5030|atrybut "*atrybutu*" nie został rozpoznany|
|Ostrzeżenie kompilatora (poziom 4) C5031|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu|
|Ostrzeżenie kompilatora (poziom 4) C5032|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop)|
|Ostrzeżenie kompilatora (poziom 1) C5033|"*klasy magazynowania*" nie jest już klasy obsługiwanej magazynu|
|Ostrzeżenie C5034 kompilatora|Użycie wewnętrznej "*wewnętrzne*" powoduje, że funkcja *funkcja* ma zostać skompilowana jako gość kodu|
|Ostrzeżenie C5035 kompilatora|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* ma zostać skompilowana jako gość kodu|
|Ostrzeżenie kompilatora (poziom 1) C5036|varargs funkcji konwersja wskaźnika podczas kompilowania przy użyciu /hybrid:x86arm64 "*type1*"do"*type2*"|
|Ostrzeżenie kompilatora (błąd) C5037|"*funkcji członkowskiej*": definicja wiersza elementu członkowskiego szablonu klasy nie może mieć argumentów domyślnych|
