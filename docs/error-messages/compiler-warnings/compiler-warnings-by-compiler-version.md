---
title: "Ostrzeżenia kompilatora w wersji kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
ms.assetid: 886c5a66-088c-4a4b-908b-aa3ec189e595
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52513b156ee8c86d8358be84a27c28d15eb86641
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warnings-by-compiler-version"></a>Ostrzeżenia kompilatora w wersji kompilatora  
  
Kompilator można pominąć, ostrzeżeń, które zostały wprowadzone po wersji, można określić za pomocą [/Wv](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora. Jest to przydatne do zarządzania procesu kompilacji podczas wprowadzenie nowej wersji zestawu narzędzi, a chcesz tymczasowo pominąć nowego ostrzeżenia. Ta opcja nie odrzuca nowe komunikaty o błędach. Nie zaleca się Pomiń wszystkie ostrzeżenia nowe trwale! Zaleca się zawsze kompilacji na najwyższym poziomie ostrzeżenie regularne, __/W4__i Usuń __/Wv__ opcja tak szybko, jak to możliwe w kompilacji.  
  
Te wersje kompilatora zostały wprowadzone nowe ostrzeżenia:

| Produkt | Numer wersji kompilatora |  
|-|-|  
| Visual C++ 2002 | 13.00.9466 |  
| Program Visual C++ 2003 | 13.10.3077 |  
| Visual C++ 2005 | 14.00.50727.762 |  
| Visual C++ 2008 | 15.00.21022.08 |  
| Visual C++ 2010 | 16.00.40219.01 |  
| Visual C++ 2012 | 17.00.51106.1 |  
| Visual C++ 2013 | 18.00.21005.1 |  
| Visual C++ 2015 RTM | 19.00.23026.0 |  
| Visual C++ 2015 Update 1 | 19.00.23506.0 |  
| Visual C++ 2015 Update 2 | 19.00.23918.0 |  
| Visual C++ 2015 Update 3 | 19.00.24215.1 |  
| Visual C++ 2017 RTM | 19.10.24903.0 |  
| Visual C++ 2017 Update 1 | 19.10.25017.0 |  
  
Można określić tylko główny numer, liczby główne i pomocnicze lub głównych i pomocniczych oraz numery do kompilacji __/Wv__ opcja, która wyłącza wszystkie ostrzeżenia dla w wersjach nowszych niż określona liczba. Na przykład, aby pominąć ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 2 lub nowszym, służy __/Wv:19.00.23900__. Aby pominąć wszystkie ostrzeżenia w programie Visual C++ 2013 i nowsze, można użyć __/WV: 18__.  
  
W poniższych sekcjach wymieniono ostrzeżenia wprowadzone przez każda wersja programu Visual C++, który można pominąć przy użyciu __/Wv__ — opcja kompilatora. __/Wv__ opcja pomija ostrzeżenia, które nie są wyświetlane, które przed powstaniem określona wersji kompilatora.
  
## <a name="warnings-introduced-in-visual-c-2017-update-1"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 Update 1
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19.10.25000__.  
  
|||  
|-|-|  
C4597|Niezdefiniowane zachowanie: *opis*  
C4604|"*typu*": przekazywanie argumentów poprzez wartość granicy natywnych i zarządzanych wymaga prawidłowej kopii konstruktora. W przeciwnym razie zachowania w czasie wykonywania jest niezdefiniowana  
C4749|obsługiwane warunkowo: *opis*  
C4768|atrybuty __declspec przed Specyfikacja powiązania są ignorowane  
C4834|Odrzucanie wartości zwracanej przez funkcję z atrybutem "nodiscard"  
C4841|użyte rozszerzenie niestandardowe: *rozszerzenia*
C4842|Aby było spójne między wersjami kompilatora nie jest gwarantowana wynik "makra offsetof" zastosowane do typu przy użyciu dziedziczenie wielokrotne  
C4869|"nodiscard" można stosować tylko do klasy, wyliczenia i funkcje z typem zwracanym inny niż void  
C5033|"*klasy magazynowania*" nie jest już klasy obsługiwanej magazynu  
C5034|Użycie wewnętrznej "*wewnętrzne*" powoduje, że funkcja *funkcja* ma zostać skompilowana jako gość kodu  
C5035|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* ma zostać skompilowana jako gość kodu  
C5036|varargs funkcji konwersja wskaźnika podczas kompilowania przy użyciu /hybrid:x86arm64 "*type1*"do"*type2*"  
C5037|"*funkcji członkowskiej*": definicja wiersza elementu członkowskiego szablonu klasy nie może mieć argumentów domyślnych  
  
## <a name="warnings-introduced-in-visual-c-2017-rtm"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 RTM  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19.10__.  
  
|||  
|-|-|  
C4468|"przepuszczająca": atrybut musi następować etykiety case lub etykiety domyślnej
C4698|"*funkcji*" jest do oceny tylko celów i mogą ulec zmianie lub usuwania w przyszłych aktualizacji.
C4839|Użycie niestandardowej klasy*klasy*"jako argument do funkcji ze zmienną liczbą argumentów
C4840|Użycie nieprzenośne klasy*klasy*"jako argument do funkcji ze zmienną liczbą argumentów
  
## <a name="warnings-introduced-in-visual-c-2015-update-3"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 3  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19.00.24000__.  
  
|||  
|-|-|  
C4467|Korzystanie z atrybutów ATL jest przestarzałe.
C4596|"*nazwa*": niedozwolona nazwa kwalifikowana w deklaracji elementu członkowskiego
C4598|"#include \< *nagłówka*\>": numer nagłówka *numer* w *źródła* niezgodny *źródła* w tym stanowisko
C4599|"*argument*": *źródła* numer argumentu *numer* niezgodny *źródła*
  
## <a name="warnings-introduced-in-visual-c-2015-update-2"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 2  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19.00.23900__.  
  
|||  
|-|-|  
C4466|Nie można wykonać sterty dla koprocedury
C4595|"*klasy*": nowy operator niebędący elementem członkowskim ani funkcje delete nie można zadeklarować wbudowany
C4828|Plik zawiera znak rozpoczynający się od przesunięcia 0 x*wartość* jest niedozwolony w bieżącym zestawie znaków źródła (strona kodowa *numer*).
C4868|Kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjatora w nawiasach klamrowych
  
## <a name="warnings-introduced-in-visual-c-2015-update-1"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 1  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19.00.23500__.  
  
|||  
|-|-|  
C4426|flagi optymalizacji zmieniły się po dołączeniu nagłówka, może #pragma Optimize()
C4654|Kod umieszczony przed obejmują prekompilowanego nagłówka wiersza zostanie zignorowany. Dodaj kod do wstępnie skompilowanego nagłówka.
C5031|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu
C5032|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop)
  
## <a name="warnings-introduced-in-visual-c-2015-rtm"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 RTM  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:19__.  
  
|||  
|-|-|  
C4427|"*błąd*": przepełnienie w czasie dzielenia stałej, niezdefiniowane zachowanie
C4438|"*typu*": nie można bezpiecznie wywołać / await: clrcompat tryb. Jeśli "*typu*" wywołania do środowiska CLR może spowodować uszkodzenie nagłówka środowiska CLR
C4455|"operator *nazwa*": identyfikatory sufiksu literału, które nie rozpoczynają się od znaku podkreślenia są zarezerwowane
C4456|Deklaracja "*nazwa*" powoduje ukrycie poprzedniej deklaracji lokalnej
C4457|Deklaracja "*nazwa*" powoduje ukrycie parametru funkcji
C4458|Deklaracja "*nazwa*" powoduje ukrycie elementu członkowskiego klasy
C4459|Deklaracja "*nazwa*" powoduje ukrycie deklaracji globalnej
C4462|"*typu*": nie można określić GUID typu. Program może ulec awarii w czasie wykonywania.
C4463|przepełnienie; Przypisywanie *wartość* do pola bitowego, która może zawierać wartości z *wartość* do *wartości*
C4473|"*opis*": przekazano niewystarczającą liczbę argumentów dla ciągu formatowania
C4474|"*opis*": przekazano za dużo argumentów dla ciągu formatowania
C4475|"*opis*": modyfikator długości "*modyfikator*"nie może być stosowany ze znakiem pola typu"*znak*" w specyfikatorze formatu
C4476|"*opis*': nieznany znak pola typu"*znak*"w specyfikatorze formatu
C4477|"*opis*": ciąg formatu "*ciąg*"wymaga argumentu typu"*typu*", ale argument ze zmienną liczbą argumentów *numer* ma typ "*typu*"
C4478|"*opis*": nie można łączyć pozycyjnych i niepozycyjnych symbole zastępcze w tym samym ciągu formatu
C4494|"*typu*": Ignorowanie funkcji __declspec(allocator), ponieważ typ zwracany funkcji nie jest wskaźnikiem lub odwołaniem
C4495|użyto niestandardowego rozszerzenia "__super": Zamień jawną nazwę klasy podstawowej
C4496|użyto niestandardowego rozszerzenia "for each": Zamień na instrukcję ranged-for
C4497|użyto niestandardowego rozszerzenia "sealed": Zamień "final"
C4498|użyto niestandardowego rozszerzenia: "*rozszerzenia*"
C4499|"*specjalizacji*": jawna specjalizacja nie może mieć klasy magazynu (zignorowano)
C4576|Wpisz ujętego w nawiasy, a następnie lista inicjalizatora jest składnia konwersji typu jawnego niestandardowych
C4577|słowo kluczowe "noexcept" używane z nie określając; trybu obsługi wyjątków Zakończenie na wyjątku nie jest gwarantowana. Określ/ehsc
C4578|"abs": konwersja z "*typu*"do"*typu*", możliwa utrata danych (Czy chodziło Ci o wywołania "*nazwa*" lub do #include <cmath>?)
C4582|"*typu*": Konstruktor nie jest wywoływany niejawnie
C4583|"*typu*": destruktor nie jest wywoływany niejawnie
C4587|"*typu*": Zmiana zachowania: konstruktor jest nie już wywoływany niejawnie
C4588|"*typu*": Zmiana zachowania: destruktor jest nie już wywoływany niejawnie
C4589|Konstruktor klasy abstrakcyjnej*typu*"ignoruje inicjatora w przypadku wirtualnej klasy podstawowej"*typu*"
C4591|limit głębokości wywołań "constexpr" *numer* Przekroczono (/ constexpr: DEPTH<NUMBER>)
C4592|"*typu*": symbol zostanie dynamicznie zainicjowany (ograniczenie implementacji)
C4593|"*typu*": "constexpr" wywołanie oceny krok limit *wartość* przekroczony; Użyj Steps<NUMBER> Aby zwiększyć limit
C4647|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach
C4648|Atrybut standardowy "carries_dependency" zostanie zignorowany.
C4649|atrybuty są ignorowane w tym kontekście
C4753|Nie można odnaleźć granic wskaźnika; Zignorowano funkcję wewnętrzną MPX
C4771|Granice muszą zostać utworzone przy użyciu wskaźnika prostego; Zignorowano funkcję wewnętrzną MPX
C4774|"*opis*": Oczekiwano argumentu ciąg formatu *numer* nie jest ciągiem literału
C4775|użyto niestandardowego rozszerzenia w ciągu formatu "*ciąg*"funkcji"*funkcja*"
C4776|"%*znak*"nie jest dozwolony w ciągu formatowania lub funkcji"*funkcja*"
C4777|"*opis*": ciąg formatu "*ciąg*"wymaga argumentu typu"*typu*", ale argument ze zmienną liczbą argumentów *numer* ma typ "*typu*"
C4778|"*opis*": niezakończony ciąg formatu "*ciąg*"
C4838|Konwersja z "*typu*"do"*typu*" wymaga konwersji zawężającej
C5022|"*typu*": określono wiele konstruktorów przenoszenia
C5023|"*typu*": określono wiele operatorów przypisania przenoszenia
C5024|"*deklaracji*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty
C5025|"*deklaracji*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty
C5026|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty
C5027|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty
C5028|"*nazwa*": wyrównanie określone we wcześniejszej deklaracji (*numer*) nie jest określona w definicji
C5029|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, elementów członkowskich danych i typów tagów tylko
C5030|atrybut "*atrybutu*" nie został rozpoznany
  
## <a name="warnings-introduced-in-visual-c-2013"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2013  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/WV: 18__.  
  
|||  
|-|-|  
C4301|"*typu*": przesłanianie wirtualnej funkcji różni się tylko z "*deklaracji*" kwalifikatorem const/volatile
C4316|"*typu*": obiekt przydzielony na stosie nie może być wyrównane *numer*
C4380|"*typu*": Konstruktor nie może być przestarzały
C4388|"*tokenu*": niezgodność podpisany niepodpisane
C4423|'std::bad_alloc': zostanie przechwycony przez klasę ('*typu*") w wierszu *numer*
C4424|przechwycenie '*typu*'poprzedzone przez'*typu*"w wierszu *numer*; nieprzewidywalne zachowanie może spowodować, jeśli zostanie zgłoszony 'std::bad_alloc'
C4425|Nie można zastosować adnotacji SAL do "..."
C4464|względna ścieżka dołączania zawiera ".."
C4575|"__vectorcall" jest niezgodny z "/ clr" opcja: konwertowanie na "__stdcall"
C4609|"*typu*"dziedziczy po interfejsie domyślnym"*typu*"w typie"*typu*". Użyj innego interfejsu domyślnego dla "*typu*", lub przerwać relację bazową/dziedziczoną.
C4754|Reguły konwersji dla operacji arytmetycznych w porównaniu na *opis*(*numer*) oznacza, że jedna gałąź nie może zostać wykonana. Rzutowanie "*typu*"do"*typu*" (lub podobny typ o *numer* bajtów).
C4755|Reguły konwersji dla operacji arytmetycznych w porównaniu na *opis*(*numer*) oznacza, że jedna gałąź nie można wykonać w funkcji śródwierszowych. Rzutowanie "*typu*"do"*typu*" (lub podobny typ o *numer* bajtów).
C4767|Nazwa sekcji '*nazwa*"jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator
C4770|częściowo zweryfikowane wyliczenie "*nazwa*" używana jako indeks
C4827|Publiczną metodę 'ToString' o 0 parametrach powinna być oznaczona jako virtual i override
C4882|przekazywanie funktorów z operatorami niestałymi wywołania do concurrency::parallel_for_each jest przestarzałe.
C4973|"*typu*': oznaczono jako przestarzały
C4974|"*typu*': oznaczono jako przestarzały
C4981|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie została wbudowana ponieważ zawiera ona semantyki wyjątku
C4990|Warbird: *wiadomości*
C4991|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie została wbudowana ponieważ poziom ochrony przed wstawianiem do treści jest większy niż element nadrzędny
C4992|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie została wbudowana ponieważ zawiera wstawiony zestaw, który nie może być chroniony
  
## <a name="warnings-introduced-in-visual-c-2012"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2012  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:17__.  
  
|||  
|-|-|  
C4330|atrybut "*atrybutu*"dla sekcji"*sekcji*" ignorowane
C4415|zduplikowane __declspec (code_seg ("*nazwa*"))
C4416|__declspec(code_seg(...)) zawiera pusty ciąg: ignorowane
C4417|utworzenie wystąpienia jawnego szablonu nie może mieć __declspec(code_seg(...)): ignorowane
C4418|__declspec(code_seg(...)) został zignorowany w wyliczeniu
C4419|"*nazwa*"nie ma żadnego skutku, gdy zastosowane do prywatnej klasy ref"*typu*".
C4435|"*typu*": układ obiektów w/vd2 zmieni się z powodu bazy wirtualnej "*typu*"
C4436|dynamic_cast z bazy wirtualnej "*typu*"do"*typu*" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem
C4437|dynamic_cast z bazy wirtualnej "*typu*"do"*typu*" może zakończyć się niepowodzeniem w niektórych kontekstach
C4443|Oczekiwano wartości parametru pragma "0", "1" lub "2"
C4446|"*typu*": nie można mapować elementu członkowskiego "*nazwa*" do tego typu z powodu konfliktu z nazwą typu. Metoda została zmieniona na "*nazwa*"
C4447|podpis "main" bez modelu wątków. Rozważ użycie "int main (Platform::Array\<Platform::String ^ > ^ args)".
C4448|"*typu*" nie ma domyślnego interfejsu określonego w metadanych. Pobrania: "*typu*", która może ulec awarii w czasie wykonywania.
C4449|"*typu*" jako niezamknięty typ powinien być oznaczony jako "[WebHostHidden]"
C4450|"*typu*"powinien być oznaczony jako "[WebHostHidden]" ponieważ dziedziczy po"*typu*"
C4451|"*typu*": użycie klasy ref*typu*' wewnątrz tego kontekstu może doprowadzić do nieprawidłowego kierowania obiektami między kontekstami
C4452|"*typu*": typ publiczny nie może być w zakresie globalnym. Musi być w przestrzeni nazw, która jest elementem podrzędnym nazwy wyjściowego pliku .winmd.
C4453|"*typu*": typ '[WebHostHidden]' nie powinien być używany na publikowanej powierzchni typu publicznego, który nie jest "[WebHostHidden]"
C4454|"*typu*" jest przeciążony przez więcej niż liczba parametrów wejściowych bez konieczności [DefaultOverload] określona. Pobrania "*deklaracji*" jako domyślne przeciążenie
C4471|"*nazwa*": deklaracja przekazująca dalej wyliczenie niebędące w zakresie musi być typu podstawowego (założono typ int)
C4472|"*nazwa*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (private/public), aby zadeklarować wyliczenie managed WinRT
C4492|"*typu*": dopasowań metody podstawowej klasy referencyjnej "*typu*", ale nie jest oznaczony jako "override"
C4493|wyrażenie usunięcia nie obowiązuje jako destruktor "*typu*" nie ma dostępności "public"
C4585|"*typu*": A WinRT "public ref class" musi być zamknięta lub dziedziczyć po istniejącej niezamkniętej klasie
C4586|"*typu*": typ publiczny nie można zadeklarować w przestrzeni nazw najwyższego poziomu o nazwie "Windows"
C4695|#pragma execution_character_set: "*argument*" nie jest nieobsługiwanym argumentem: obecnie tylko "UTF-8" jest obsługiwana.
C4703|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej "*nazwa*" używane
C4728|/ Opcja Yl-zignorowany, ponieważ wymagane jest odwołanie PCH
C4745|nietrwały dostęp "*nazwa*" nie można go uznać z powodu jego rozmiaru
C4746|nietrwały dostęp "*nazwa*" podlega/volatile:\<iso\|MS > ustawienie; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store
C4872|dzielenie liczby zmiennoprzecinkowej przez zero wykryta podczas kompilacji wykresu wywołań dla concurrency::parallel_for_each w:: "*opis*"
C4880|Rzutowanie z "*typu*"do"*typu*": odrzucenie stałości ze wskaźnika lub odwołania może spowodować niezdefiniowane zachowanie w zastrzeżonej funkcji amp
C4881|Konstruktor i/lub destruktor nie zostaną wywołane dla zmiennej tile_static "*typu*"
C4966|"*opis*" ma adnotację __code_seg z nieobsługiwaną nazwą segmentu, adnotacja została zignorowana
C4988|"*typu*": Zmienna zadeklarowana poza zakresem klasy/funkcji
C4989|"*opis*": Typ ma definicje powodujące konflikt.
  
## <a name="warnings-introduced-in-visual-c-2010"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2010  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:16__.  
  
|||  
|-|-|  
C4352|"*nazwa*": wewnętrzna funkcja już zdefiniowana
C4573|użycie "*typu*" wymaga przechwytywania "this" ale kompilator nie zezwala na to bieżący domyślny tryb przechwytywania
C4574|"*nazwa*'jest zdefiniowany jako ' 0': czy zamierzałeś użyć ' #if *nazwa*"?
C4689|"*znak*": nieobsługiwany znak w #pragma detect_mismatch; #pragma ignorowane
C4751|/ arch flagi AVX nie ma zastosowania do Intel(R) Streaming SIMD Extensions, które znajduje się wewnątrz wbudowanego kodu Asemblera
C4752|Znaleziono Intel(R) Advanced Vector Extensions; należy rozważyć użycie odpowiednich/arch flagi AVX
C4837|Wykryto — trigram: "? *znak*"zastąpione przez"*znak*"
C4986|"*deklaracji*": specyfikacja wyjątku jest niezgodna z poprzednią deklaracją
C4987|użyto rozszerzenia niestandardowego: 'throw (...)'
  
## <a name="warnings-introduced-in-visual-c-2008"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2008  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:15__.  
  
|||  
|-|-|  
C4396|"*typu*": wbudowany specyfikator nie można użyć, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji
C4413|"*deklaracji*": element członkowski odwołania jest zainicjowany jako tymczasowy, który nie jest zachowany po zakończeniu działania konstruktora
C4491|"*opis*": ma niedozwolony format wersji języka IDL
C4603|"*nazwa*": makro jest niezdefiniowane lub definicja różni się po użyciu prekompilowanego nagłówka
C4627|"*opis*": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka
C4750|"*opis*": funkcja zawierająca _alloca() została wbudowana w pętlę
C4910|"*typu*": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem
C4985|"*deklaracji*": Brak atrybutów w poprzedniej deklaracji.
  
## <a name="warnings-introduced-in-visual-c-2005"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2005  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:14__.  
  
|||  
|-|-|  
C4000|Nieznane Ostrzeżenie Wybierz polecenie Pomoc techniczna w menu Pomoc programu Visual C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji
C4272|"*typu*": jest oznaczony jako __declspec(dllimport); należy określić natywną Konwencję wywoływania podczas importu funkcji.
C4333|"*wyrażenie*": przesunięcie w prawo o zbyt dużą liczbę, utrata danych
C4334|"*wyrażenie*": wynik 32-bitowe przesunięcia niejawnie skonwertowano do 64 bitów (czy 64-bitowe przesunięcie było zamierzone?)
C4335|Wykryto format pliku Mac: Skonwertuj plik źródłowy do formatu DOS lub systemu UNIX
C4342|Zmiana zachowania: "*typu*" o nazwie, ale operator elementu członkowskiego został wywołany w poprzednich wersjach
C4350|Zmiana zachowania: "*deklaracji*"wywołana zamiast"*deklaracji*"
C4357|Znaleziono argument tablicy parametrów na liście formalnych argumentów dla delegata "*deklaracji*"zignorowano podczas generowania"*typu*"
C4358|"*wyrażenie*": zwracany typ połączonych delegatów nie jest "void"; zwrócona wartość jest niezdefiniowana
C4359|"*typu*": specyfikator wyrównania jest mniejszy niż rzeczywiste wyrównanie (*numer*) i zostaną zignorowane.
C4362|"*typu*": wyrównanie większe niż 8 bajtów nie jest obsługiwane przez CLR
C4364|#using dla zestawu "*nazwa*" poprzednio widziano w *opis*(*numer*) bez atrybutu as_friend; nie zastosować as_friend
C4365|"*wyrażenie*": konwersja z "*typu*"do"*typu*", niezgodność podpisany niepodpisane
C4366|Wynik jednoargumentowego "*operator*" operator może być niewyrównany
C4367|Konwersja z "*typu*"do"*typu*" może spowodować wyjątek niespójności typu danych
C4368|Nie można zdefiniować "*nazwa*"jako członka zarządzany"*typu*": mieszane typy nie są obsługiwane.
C4369|"*typu*': moduł wyliczający wartość"*numer*"nie może być reprezentowany jako"*typu*", wartość to"*numer*"
C4374|"*deklaracji*": metoda interfejsu nie będzie zaimplementowana przez niewirtualną metodę "*deklaracji*"
C4375|Metoda niepubliczna "*deklaracji*"nie przesłania"*deklaracji*"
C4376|Specyfikator dostępu "*specyfikator*:" nie jest już obsługiwany: Użyj "*specyfikator*:" zamiast niego
C4377|typy natywne są domyślnie; prywatne -d1PrivateNativeTypes jest przestarzały
C4378|Należy uzyskać wskaźniki do funkcji, aby uruchomić inicjatory; należy wziąć pod uwagę system::ModuleHandle:: resolvemethodhandle
C4379|Wersja *wersji* wspólnego języka środowiska uruchomieniowego nie jest obsługiwany przez ten kompilator. Używanie tej wersji może spowodować nieoczekiwane wyniki
C4381|"*deklaracji*": metoda interfejsu nie będzie zaimplementowana przez niewirtualną metodę "*deklaracji*"
C4382|wyrzucanie "*typu*": typ z destruktorem __clrcall lub konstruktorem kopiującym można tylko przechwycić w/CLR: pure modułu
C4383|"*typu*": znaczenie usunięcia odwołania do dojścia można zmienić, gdy zdefiniowane przez użytkownika "*operator*" operator istnieje; Zapisz operator jako funkcję statyczną aby była niejawna przy korzystaniu z operandu
C4384|#pragma "*dyrektywy*" powinny być używane tylko w zakresie globalnym
C4393|"*typu*": const nie ma wpływu *opis* element członkowski danych; ignorowany
C4394|"*typu*": symbol per-appdomain nie powinien być oznaczony przez __declspec (*wartość*)
C4395|"*typu*": funkcja członkowska zostanie wywołana na kopii elementu członkowskiego danych initonly "*typu*"
C4397|DefaultCharSetAttribute jest ignorowana.
C4398|"*typu*": globalny obiekt dla procesu może nie działać poprawnie z wieloma domenami aplikacji; należy wziąć pod uwagę użycie __declspec(appdomain)
C4399|"*typu*": symbol w procesie nie powinien być oznaczony przez __declspec (*wartość*) gdy skompilowano z opcją/CLR: pure
C4400|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.
C4412|"*deklaracji*": sygnatura funkcji zawiera typ "*typu*'; Obiektami C++ są bezpieczne między czystym kodzie i mieszanego lub macierzystego.
C4429|możliwa niekompletna lub nieprawidłowo sformułowana universal-character-name
C4430|brak specyfikatora typu — zakładany int. Uwaga: C++ nie obsługuje domyślnie typu int
C4431|brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnego int
C4434|statyczny Konstruktor musi posiadać prywatną dostępność; Zmiana na prywatny dostęp
C4439|"*typu*": definicja funkcji z zarządzanym typem w sygnaturze musi mieć konwencję wywołania __clrcall
C4441|Konwencja wywoływania '*Konwencji*"ignorowane. "*Konwencji*" zamiast tego użyć
C4445|"*deklaracji*": w typie managed WinRT nie może być prywatny metody wirtualnej
C4460|Operator CLR i WinRT "*typu*", ma parametr przekazywany przez odwołanie. Operator CLR i WinRT "*operator*"ma semantykę różną od operatora C++"*operator*", czy zamierzasz przekazanie przez wartość?
C4461|"*typu*": Ta klasa ma finalizator "! *Typ*", ale nie ma destruktora" ~*typu*"
C4470|Formant zmiennoprzecinkowych pragm zignorowane z opcją/CLR
C4480|użyto niestandardowego rozszerzenia: Określanie typu podstawowego dla wyliczenia "*typu*"
C4481|użyto niestandardowego rozszerzenia: specyfikator przesłonięcia "*specyfikator*"
C4482|użyto niestandardowego rozszerzenia: enum "*typu*" użyte w nazwie kwalifikowanej
C4483|Błąd składniowy: Oczekiwano słowa kluczowego języka C++
C4484|"*typu*": dopasowań metody podstawowej klasy referencyjnej "*typu*", ale nie jest oznaczony jako "virtual", "new" lub "override"; Założono "new" (ale nie "virtual")
C4485|"*typu*": dopasowań metody podstawowej klasy referencyjnej "*typu*", ale nie jest oznaczony jako "new" lub "override"; Założono "new" (i "virtual")
C4486|"*typu*": prywatna metoda wirtualna klasy referencyjnej lub klasy wartości powinna być oznaczona jako "sealed"
C4487|"*typu*": pasuje dziedziczone metody niewirtualnej "*typu*", ale nie jest jawnie oznaczony jako "new"
C4488|"*typu*": wymaga "*— słowo kluczowe*"słowo kluczowe, aby zaimplementować metodę interfejsu"*typu*"
C4489|"*— słowo kluczowe*": niedozwolony dla metody interfejsu "*nazwa*"; specyfikatory są dozwolone tylko dla metod klasy referencyjnej klasy i wartość zastąpienia
C4490|"*— słowo kluczowe*": nieprawidłowe użycie specyfikatora override; "*typu*" jest niezgodny z metody podstawowej klasy referencyjnej
C4538|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.
C4559|"*typu*": zmiana definicji; funkcja __declspec zyski (*wartość*)
C4565|"*typu*": zmiana definicji; symbol został wcześniej zadeklarowany z __declspec (*wartość*)
C4566|znak reprezentowany przez universal-character-name "*znak*" nie może być reprezentowany w bieżącej stronie kodowej (*numer*)
C4568|"*typu*": Brak członkowie nie odpowiadają podpisowi jawnego przesłaniania
C4569|"*typu*": Brak członkowie nie odpowiadają podpisowi jawnego przesłaniania
C4570|"*typu*": nie jest jawnie zadeklarowana jako abstrakcyjna, ale ma funkcje abstrakcyjne
C4571|Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane
C4572|Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." zamiast niego
C4580|[attribute] jest przestarzały; Zamiast tego można określić *określonego*Attribute jako klasę podstawową
C4581|zachowanie przestarzałe: ' "*nazwa*" "zastąpione"*nazwa*"Aby przetwarzać atrybut
C4606|Ostrzeżenie #pragma: "*numer*" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń
C4631|Oprogramowanie MSXML lub XPath niedostępny, nie będą przetwarzane komentarze dokumentu XML. *Opis elementu*
C4632|Komentarz dokumentu XML: *opis* — odmowa dostępu: *opis*
C4633|Komentarz dokumentu XML*opis*: błąd: *opis*
C4634|Komentarz dokumentu XML*opis*: nie można zastosować: *opis*
C4635|Komentarz dokumentu XML*opis*: nieprawidłowo sformułowany kod XML: *opis*
C4636|Komentarz dokumentu XML*opis*: tag wymaga niepustym "*opis*" atrybutu.
C4637|Komentarz dokumentu XML*opis*: <include> tag odrzucone. *Opis elementu*
C4638|Komentarz dokumentu XML*opis*: odwołanie do nieznanego symbolu "*opis*".
C4639|Błąd oprogramowania MSXML, nie będą przetwarzane komentarze dokumentu XML. *Opis elementu*
C4641|Komentarz dokumentu XML ma niejednoznaczne odwołanie: 
C4678|Klasa podstawowa*deklaracji*"jest mniej dostępny niż"*nazwa*"
C4679|"*opis*": nie można zaimportować elementu członkowskiego
C4687|"*typu*": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "*typu*"
C4688|"*nazwa*": Lista ograniczeń zawiera prywatny typ zestawu "*deklaracji*"
C4690|[ emitidl( pop ) ]: więcej zdejmowań niż włożeń
C4691|"*typu*": oczekiwano typu odwołania w których nie ma odwołań *modułu* "*opis*", typ zdefiniowany w bieżącej jednostce tłumaczenia, zamiast tego użyć
C4692|"*nazwa*": podpis elementu z systemem innym niż nieprywatnego elementu członkowskiego zawiera prywatny typ macierzysty zestawu "*deklaracji*"
C4693|"*typu*": zapieczętowana klasa abstrakcyjna nie może mieć żadnych członków wystąpienia*nazwa*"
C4694|"*typu*": zapieczętowana klasa abstrakcyjna nie może mieć klasy podstawowej*typu*"
C4720|Raporty asemblera wiersza: "*opis*"
C4721|"*opis*": nie jest dostępna jako funkcja wewnętrzna
C4722|"*opis*": destruktor nigdy nie powraca, potencjalny wyciek pamięci
C4726|ARM arch4/4T obsługuje "< cpsr_f > lub < spsr_f >" o wartości bezpośrednim
C4727|PCH o nazwie *nazwa* z tą samą sygnaturą czasową w *nazwa* i *nazwa*.  Za pomocą pierwszego układu PCH.
C4729|Funkcja za duża dla przepływu wykres na podstawie ostrzeżenia
C4730|"*opis*": połączenie typu _m64 i liczb zmiennoprzecinkowych wyrażenia może spowodować niepoprawny kod
C4731|"*opis*": rejestr wskaźnika ramki "*zarejestrować*" zmodyfikowany przez wbudowany kod asemblera
C4732|wewnętrzne "*wewnętrzne*" nie jest obsługiwana w ramach tej architektury
C4733|Wbudowanego asm przypisanie do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa
C4734|Więcej niż 64 KB numery wierszy COFF debugowania sekcji informacji o; Zatrzymaj emitowanie numerów linii debugowania formatu COFF dla modułu "*modułu*"
C4738|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności
C4739|Odwołanie do zmiennej "*zmiennej*" przekracza jego miejsce do magazynowania
C4740|Przepływ wejścia lub wyjścia wbudowanego kodu asemblera pomija optymalizację globalną
C4742|"*zmiennej*"ma inne wyrównanie "*lokalizacji*"i"*lokalizacji*": *numer* i *numer*
C4743|"*nazwa*"ma inny rozmiar "*lokalizacji*"i"*lokalizacji*": *numer* i *numer* bajtów
C4744|"*nazwa*"ma inny typ "*lokalizacji*"i"*lokalizacji*": "*typu*"i"*typu*"
C4747|Wywołanie zarządzanego "*typu*": kodu zarządzanego nie mogą być uruchamiane w obszarze blokady modułu ładującego, włączając punktu wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL
C4761|Niezgodność rozmiaru całkowitego w argumencie; podano konwersję
C4764|Nie można wyrównać obiektów przechwytywania do więcej niż 16 bajtów
C4788|"*identyfikator*": identyfikator został obcięty do "*numer*' znaków
C4789|bufor "*nazwa*" rozmiaru *numer* bajtów zostanie przepełniony; *numer* bajtów zostanie zapisane zaczynając od przesunięcia *numer*
C4801|Zwracanie przez odwołanie nie jest możliwe do zweryfikowania: *opis*
C4819|Plik zawiera znak, który nie może być reprezentowany w bieżącej stronie kodowej (*numer*). Zapisz plik w formacie Unicode, aby zapobiec utracie danych
C4826|Konwersja z "*typu*"do"*typu*" jest ze znakiem. Może to spowodować nieoczekiwane zachowanie.
C4829|Prawdopodobnie niepoprawne parametry funkcji main. Należy wziąć pod uwagę "int main (Platform::Array\<Platform::String ^ > ^ ARGV —)"
C4835|"*typu*": Inicjator dla eksportowanych danych nie zostaną uruchomione, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta
C4867|"*typu*": niestandardowa składnia; Użyj "&", aby utworzyć wskaźnik do elementu członkowskiego
C4936|Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure
C4937|"*nazwa*"i"*nazwa*"są nierozróżnialne jako argumenty"*opcji*"
C4938|"*typu*": zmienna reduktywna przestawne może spowodować niespójne wyniki z opcją/FP: strict lub dyrektywą #pragma fenv_access
C4939|#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++
C4947|"*typu*": oznaczony jako przestarzały
C4949|dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"
C4950|"*typu*": oznaczony jako przestarzały
C4955|"*opis*": Importowanie zostało zignorowane; zaimportowano już z "*źródła*"
C4956|"*typu*": ten typ nie jest możliwe do zweryfikowania
C4957|"*wyrażenie*": jawne rzutowanie z "*typu*"do"*typu*" nie jest możliwe do zweryfikowania
C4958|"*wyrażenie*": arytmetyka wskaźnika nie jest możliwe do zweryfikowania
C4959|Nie można zdefiniować niezarządzanego *klasy* "*typu*" w/CLR: Safe, ponieważ dostęp do jego elementów członkowskich implikuje kod niemożliwy do zweryfikowania
C4960|"*opis*" jest zbyt duży, aby zostać profilowanym
C4961|Nie scalono żadnych danych profilu "*lokalizacji*", profilowana Optymalizacja została wyłączona
C4962|"*opis*": profilowana Optymalizacja została wyłączona, ponieważ optymalizacje spowodowały niespójność danych profilu
C4963|"*opis*": nie znaleziono danych profilowych; różne opcje kompilatora zostały użyte w kompilacji instrumentowanej
C4964|Optymalizacja nie określono żadnych opcji; informacje o profilu nie będą zbierane.
C4965|niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania
C4970|Konstruktor delegata: obiekt docelowy ignorowane od "*deklaracji*" jest statyczny
C4971|Kolejność argumentów: \<obiektu docelowego >, \<docelowa funkcja > dla konstruktora delegaty jest przestarzały, użyj \<docelowa funkcja >, \<obiekt docelowy >
C4972|Nie jest bezpośrednia modyfikacja lub traktowanie wyniku operacji odpakowywania wartościowanego lewostronnie
  
## <a name="warnings-introduced-in-visual-c-2003"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2003  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:13.10__.  
  
|||  
|-|-|  
C4343|Optymalizacja #pragma (*opis*, off) przesłania opcję /Og
C4344|Zmiana zachowania: użycie wyników argumentów niejawnego szablonu w wywołaniu elementu "*deklaracji*"
C4346|"*typu*": zależna nazwa nie jest typem
C4348|"*deklaracji*": ponowna definicja domyślnego parametru: parametr *numer*
C4356|"*typu*": nie można zainicjować statycznego elementu członkowskiego danych za pośrednictwem pochodnej klasy
C4408|anonimowe *struktury* nie zadeklarował żadnych elementów członkowskich danych
C4544|"*deklaracji*": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu
C4545|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów
C4546|wywołanie funkcji przed przecinkiem, brak listy argumentów
C4547|"*wyrażenie*": operator przed przecinkiem nie ma żadnego wpływu; Oczekiwano operatora z efektem ubocznym
C4548|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt
C4549|"*wyrażenie*": operator przed przecinkiem nie ma żadnego wpływu; czy miało być "*wyrażenie*"?
C4628|dwuznaki nieobsługiwane z -Ze. Sekwencja znaków "*sekwencji*"nie zinterpretowana jako alternatywny token dla"*tokenu*"
C4629|użyto dwuznaku, sekwencja znaków "*sekwencji*"interpretowane jako token"*tokenu*" (Wstaw spację między dwoma znakami, jeśli to nie mają)
C4671|"*opis*": Konstruktor kopiujący jest niedostępny
C4676|"*opis*": destruktor jest niedostępny
C4677|"*nazwa*": podpis elementu z systemem innym niż nieprywatnego elementu członkowskiego zawiera prywatny typ zestawu "*deklaracji*"
C4686|"*typu*": możliwe zmiany w zachowaniu, zmiana UDT zwracać konwencji wywoływania
C4812|przestarzała deklaracja stylu: Użyj "*typu*::*nazwa*" zamiast niego
C4813|"*typu*": funkcja zaprzyjaźniona klasy lokalnej zostało wcześniej zadeklarowane
C4821|Nie można określić typu kodowania Unicode, Zapisz plik z podpisem (znacznik BOM)
C4822|"*typu*": funkcja członkowska klasy lokalnej nie ma treści
C4823|"*typu*": używa wskaźników przypinanych ale unwind semantyki nie są włączone. Należy rozważyć użycie opcji/eha
C4913|Użytkownik zdefiniowany operator binarny "," istnieje, ale żadne przeciążenie nie może konwertować wszystkich argumentów operacji, domyślny wbudowany operator binarny "," używane
C4948|zwracany typ "*deklaracji*" jest niezgodny z typem ostatniego parametru odpowiadającej mu metody ustawiającej
C4951|"*opis*" został wyedytowany od czasu zebrania danych profilu dane profilu funkcji nie zostały użyte
C4952|"*opis*": nie znaleziono danych profilowych w bazie danych programu "*opis*"
C4953|Element Wbudowywany "*opis*" został zmodyfikowany od czasu zebrania danych profilu dane nie zostały użyte
C4954|"*opis*": nieprofilowany (zawiera wyrażenie przełącznika __int64)
  
## <a name="warnings-introduced-in-visual-c-2002"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2002  
  
Te ostrzeżenia i wszystkie ostrzeżenia w nowszych wersjach są pomijane przy użyciu opcji kompilatora __/Wv:13__.  
  
|||  
|-|-|  
C4096|"*typu*": interfejs nie jest interfejsem COM; nie będzie emitowany do IDL
C4097|Oczekiwano wartości parametru pragma "Restore" lub "off"
C4165|"HRESULT" jest konwertowany na "bool"; Czy na pewno jest to, co chcesz zrobić?
C4183|"*nazwa*": Brak typu zwracanego; założono, że to funkcją członkowską zwracającą "int"
C4199|*Opis elementu*
C4255|"*nazwa*": nie podano prototypu funkcji: konwertowanie "()", "(void)"
C4256|"*deklaracji*": konstruktor dla klasy z wirtualnymi typami podstawowymi ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami programu Visual C++
C4258|"*nazwa*": definicja z pętli for jest zignorowana; służy definicji z otaczającego zakresu
C4263|"*deklaracji*": funkcja członkowska nie przesłania wszelkie klasa podstawowa wirtualnej funkcji członkowskiej
C4264|"*deklaracji*": Brak dostępnego przesłonięcia dla wirtualnej funkcji członkowskiej z podstawowej "*klasy*"; funkcja jest ukryta.
C4265|"*typu*": klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny wystąpienia tej klasy może nie być prawidłowo niszczone
C4266|"*deklaracji*": Brak dostępnego przesłonięcia dla wirtualnej funkcji członkowskiej z podstawowej "*klasy*"; funkcja jest ukryta.
C4267|"*wyrażenie*": konwersja z "size_t" do "*typu*", możliwa utrata danych
C4274|#ident ignorowane. zobacz dokumentację dla #pragma comment (exestr, "string")
C4277|importowany element "*typu*::*nazwa*" istnieje zarówno jako element członkowski danych i funkcja członkowska; element członkowski danych ignorowane
C4278|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest już makrem; Użyj kwalifikatora "rename"
C4279|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest słowem kluczowym, użyj kwalifikatora "rename"
C4287|"*wyrażenie*": niezgodność stałej bez znaku ujemna
C4288|użyto niestandardowego rozszerzenia: "*nazwa*": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli; jest w konflikcie z deklaracją w zewnętrznym zakresie
C4289|użyto niestandardowego rozszerzenia: "*nazwa*": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for
C4293|"*wyrażenie*": licznik przesunięć ujemny lub zbyt duży, niezdefiniowane zachowanie
C4295|"*typu*": tablica jest zbyt mała, aby uwzględnić znak końcowy null
C4296|"*wyrażenie*": wyrażenie jest zawsze *wartość*
C4297|"*typu*": funkcja nie zakłada się, że zgłosić wyjątek, ale nie
C4298|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest już makrem; zmiana nazwy na "__*nazwa*"
C4299|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest słowem kluczowym, zmiana nazwy na "__*nazwa*"
C4302|"*wyrażenie*": obcięcie z "*typu*"do"*typu*"
C4303|*Konwersja* z "*typu*"do"*typu*" jest przestarzały, użyj static_cast, __try_cast lub dynamic_cast
C4314|Oczekiwano wartości parametru pragma "32" lub "64"
C4315|"*typu*": wskaźnik "this" dla elementu członkowskiego "*typu*" nie może być wyrównane *numer* zgodnie z oczekiwaniami konstruktora
C4318|przekazanie stałej o wartości zero jako długość do funkcji memset
C4319|"*wyrażenie*": zero rozszerzanie "*typu*"do"*typu*" większego rozmiaru
C4321|automatycznie generowane IID dla interfejsu "*typu*"
C4322|automatycznie generowane CLSID dla klasy*typu*"
C4323|ponowne wykorzystanie zarejestrowanego identyfikatora CLSID dla klasy*typu*"
C4324|"*typu*": struktura została wzmocniona ze względu na specyfikator wyrównania
C4325|atrybuty dla standardowej sekcji "*opis*" ignorowane
C4326|zwracany typ "*nazwa*powinien być*typu*"zamiast elementu"*typu*"
C4327|"*wyrażenie*": operator pośredni wyrównania LHS (*numer*) jest większy niż RHS (*numer*)
C4328|"*opis*": operator pośredni wyrównania formalnego parametru *numer* (*numer*) jest większy niż rzeczywisty argument wyrównania (*numer*)
C4329|Specyfikator wyrównania jest ignorowany w wyliczeniu
C4336|Importowanie biblioteki typów odsyłaczy "*biblioteki*"przed zaimportowaniem"*opis*"
C4337|Biblioteka typów odsyłaczy "*biblioteki*"in"*opis*' jest automatycznie importowana
C4338|#pragma *opis*: standardowa sekcja "*sekcji*" jest używana
C4339|"*typu*": użycie niezdefiniowanego typu wykryte w CLR i WinRT meta-data - użycie tego typu może spowodować wyjątek czasu wykonywania
C4353|użyto niestandardowego rozszerzenia: stała 0 jako wyrażenie funkcyjne.  Zamiast tego użyj funkcji "__noop" — wewnętrzne
C4370|"*deklaracji*": układ klasy zmienił się od poprzedniej wersji kompilatora, ze względu na lepsze pakowanie
C4371|"*deklaracji*": układ klasy mógł ulec zmianie z poprzedniej wersji kompilatora, ze względu na lepsze pakowanie elementu członkowskiego "*typu*"
C4373|"*typu*": przesłonięcia funkcji wirtualnych*deklaracji*", poprzednie wersje kompilatora nie przesłaniały, gdy parametry różniły się tylko przez kwalifikatory const/volatile
C4387|"*opis*": został uznany za
C4389|"*wyrażenie*": niezgodność podpisany niepodpisane
C4391|"*deklaracji*": nieprawidłowy typ zwracany dla wewnętrznej funkcji, oczekiwano "*typu*"
C4392|"*deklaracji*": Nieprawidłowa liczba argumentów dla wewnętrznej funkcji, oczekiwano "*numer*" argumentów
C4407|Rzutowanie pomiędzy innego wskaźnika do reprezentacji elementu członkowskiego, kompilator może wygenerować niepoprawny kod
C4420|"*nazwa*": operator nie jest dostępny, za pomocą "*nazwa*" zamiast niego; kontrola czasu wykonania może być naruszona
C4440|wywoływanie definicję Konwencji wywołań z "*opis*"do"*opis*" ignorowane
C4442|osadzony terminatorem null w argumencie __annotation.  Wartość zostanie obcięta.
C4444|"*nazwa*": element "__unaligned" najwyższego poziomu nie jest zaimplementowana w tym kontekście
C4526|"*typu*": funkcja statyczny element członkowski nie może przesłonić funkcji wirtualnej "*deklaracji*" zastąpienie ignorowane, funkcja wirtualna zostanie ukryta
C4531|C++, obsługa wyjątków nie jest dostępna w systemie Windows CE. Użyj Obsługa wyjątków strukturalnych
C4532|"*opis*": przejście z *koniec* bloku ma niezdefiniowane zachowanie podczas obsługi zakończenia
C4533|Inicjowanie "*deklaracji*" jest pomijana przy "goto *deklaracji*"
C4534|"*deklaracji*" nie będzie konstruktorem domyślnym dla *klasy* "*typu*" z powodu argumentu domyślnego
C4535|Wywołanie _set_se_translator() wymaga/eha
C4536|"*opis*": Nazwa typu przekracza limit meta-data "*numer*' znaków
C4537|"*deklaracji*": "." zastosowany do typu z systemem innym niż UDT
C4542|Pomijanie generowania scalonego wstrzykniętego pliku tekstowego, nie można zapisać *typu* pliku: "*filename*": *błąd*
C4543|Wprowadzić tekst pominięty przez atrybut "nie\_injected_text"
C4555|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt
C4557|"__assume" zawiera efekt "*efekt*"
C4558|wartość operandu "*numer*"jest poza zakresem"*numer* - *numer*"
C4561|Wywołanie "__fastcall" niezgodny z "/ clr" opcja: konwertowanie na "__stdcall"
C4562|funkcje w pełni prototypowane są wymagane w przypadku "/ clr" opcja: konwertowanie "()", "(void)"
C4564|Metoda "*nazwa*" z *klasy* "*typu*"definiuje nieobsługiwany parametr domyślny"*parametru*"
C4584|"*typu*": klasy podstawowej*deklaracji*"jest już klasą podstawową elementu"*deklaracji*"
C4608|Inicjowanie wielu elementów członkowskich Unii: "*typu*"i"*typu*"
C4619|Ostrzeżenie #pragma: istnieje ostrzeżenie o numerze "*numer*"
C4623|"*typu*": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty
C4624|"*typu*": destruktor został niejawnie zdefiniowany jako usunięty
C4625|"*typu*": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty
C4626|"*typu*": operator przypisania został niejawnie zdefiniowany jako usunięty
C4645|Funkcja zadeklarowana ze specyfikatorem "noreturn" zawiera instrukcję return
C4646|Funkcja zadeklarowana ze specyfikatorem "noreturn" ma typ zwracany inny niż void
C4659|#pragma "*opis*": użycie zastrzeżonego segmentu "*nazwa*" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)
C4667|"*deklaracji*": Brak zdefiniowanego szablonu funkcji, która pasuje do wymuszonego wystąpienia
C4668|"*nazwa*"nie jest zdefiniowany jako preprocesor makra, zastępując "0" do"*wartość*"
C4669|"*wyrażenie*": niebezpieczna konwersja: "*typu*" jest obiektem typu zarządzanego WinRT
C4674|"*nazwa*" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr
C4680|"*typu*": klasa coclass nie określa domyślnego interfejsu
C4681|"*typu*": klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia
C4682|"*typu*": nie określonego atrybutu parametru bezpośredniego, domyślnie na [in]
C4683|"*deklaracji*": źródło zdarzenia ma "out"-parametru; wskazana jest ostrożność podczas podłączania wielu obsług zdarzeń
C4684|"*opis*": ostrzeżenie!! atrybut może powodować generowanie nieprawidłowego kodu: Używaj ostrożnie
C4685|Oczekiwano ">>" znaleziono ' >> ' podczas analizowania parametrów szablonu
C4700|niezainicjowanej zmiennej lokalnej "*nazwa*" używane
C4701|Użycie potencjalnie niezainicjowanej zmiennej lokalnej "*nazwa*" używane
C4702|nieosiągalny kod
C4711|Funkcja "*nazwa*" wybrane do automatycznego rozwinięcia funkcji wbudowanej
C4714|Funkcja "*deklaracji*" oznaczona jako __forceinline nie została wbudowana
C4715|"*funkcja*": niewszystkie ścieżki kodu zwracają wartość
C4716|"*funkcja*": musi zwracać wartość
C4717|"*funkcja*": cykliczne we wszystkich ścieżkach kontroli, funkcja spowoduje przepełnienie stosu w czasie wykonywania
C4718|"*funkcja*": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie
C4719|Jeśli określono parametr Qfast - użyj opcji "f" jako przyrostka, aby wskazać pojedynczą precyzję znaleziony stała typu Double
C4723|potencjalne dzielenie przez 0
C4724|potencjalne dzielenie modulo przez 0
C4725|Instrukcja może być niedokładna na niektórych procesorach Pentium
C4757|Indeks dolny jest dużą wartością bez znaku, czy miało być ujemną stałą?
C4772|#import odwołuje się do typu z brakującej biblioteki typów; "*opis*' użyty jako element zastępczy
C4792|Funkcja "*funkcja*" zadeklarowane za pomocą sysimport i do którego istnieje odwołanie z kodu natywnego; zaimportuj bibliotekę wymaganą do połączenia
C4794|segment zmiennej magazynu lokalnego wątku "*nazwa*"zmieniła się z"*segmentu*"do"*segmentu*"
C4798|Kod natywny wygenerowany dla funkcji p-code "*nazwa*" z obsługą wyjątków lub semantyką rozwinięć
C4799|Funkcja "*nazwa*" nie ma instrukcji EMMS
C4803|"*deklaracji*": podniesiona metoda ma klasę magazynu inną od zdarzenia, "*deklaracji*"
C4810|Wartość dyrektywy pragma pack(show) == *numer*
C4811|Wartość dyrektywy pragma conform (forScope, show) == *wartość*
C4820|"*typu*": "*numer*" bajtów zostało dodane po *typu* "*typu*"
C4905|Rzutowanie na szerokiego literału ciągu "*typu*"
C4906|Rzutowanie na literału ciągu znaków "*typu*"
C4912|"*atrybutu*": atrybut ma niezdefiniowane zachowanie w zagnieżdżonym UDT
C4916|Aby uzyskać identyfikator dispid, "*typu*": musi zostać wprowadzony przez interfejs
C4917|"*typu*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw
C4918|"*znak*": nieprawidłowy znak na liście optymalizacji pragma
C4920|wyliczenia *nazwa* elementu członkowskiego *nazwa*=*numer* już widoczny w typie wyliczeniowym *nazwa* jako *nazwa* = *numer*
C4921|"*nazwa*": wartość atrybutu "*wartość*" nie powinna być określona wielokrotnie
C4925|"*deklaracji*": metoda interfejsu dispinterface nie może być wywoływana ze skryptu
C4926|"*deklaracji*": symbol jest już zdefiniowany: atrybuty zostały zignorowane
C4927|Niedozwolona konwersja; więcej niż jedna konwersja zdefiniowana przez użytkownika została zastosowana niejawnie
C4928|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika
C4929|"*opis*": Biblioteka typów zawiera Unię; ignorowanie kwalifikatora "embedded_idl"
C4930|"*deklaracji*": prototypowana funkcja nie została wywołana (czy definicja zmiennej była przeznaczona?)
C4931|przyjęto, biblioteka typów została skompilowana dla *numer*-bitowych wskaźników
C4932|__identifier (*opis*) i __identifier (*opis*) są nierozróżnialne
C4934|"__delegate(multicast)" jest przestarzały, użyj "__delegate" zamiast niego
C4935|Specyfikator dostępu do zestawu zmodyfikowany z "*opis*"
C4944|"*nazwa*": nie można zaimportować symbolu z "*źródła*": jako*deklaracji*"już istnieje w bieżącym zakresie
C4945|"*nazwa*": nie można zaimportować symbolu z "*źródła*": jako*deklaracji*"został już zaimportowany z innego zestawu"*źródła*"
C4946|reinterpret_cast zostało użyte między powiązanymi klasami: "*deklaracji*"i"*deklaracji*"
C4995|"*nazwa*": nazwa została oznaczona jako przestarzała #pragma
C4996|"*problem*": *opis*
C4997|"*typu*": klasa coclass nie implementuje interfejsu COM lub pseudointerfejsu
C4998|Nie można zrealizować oczekiwania: *opis*(*numer*)
  
## <a name="see-also"></a>Zobacz też  
[/WV — opcja kompilatora](../../build/reference/compiler-option-warning-level.md)  
[Są domyślnie wyłączone ostrzeżenia kompilatora](../../preprocessor/compiler-warnings-that-are-off-by-default.md)  
[ostrzeżenie](../../preprocessor/warning.md)  
