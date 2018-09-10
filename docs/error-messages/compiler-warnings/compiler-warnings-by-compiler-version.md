---
title: Ostrzeżenia kompilatora według wersji kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- devlang-cpp
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6645bb81a1fd4a2b42eb7419a0d008b9ac7692ad
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319087"
---
# <a name="compiler-warnings-by-compiler-version"></a>Ostrzeżenia kompilatora według wersji kompilatora

Kompilator może pominąć ostrzeżenia, które zostały wprowadzone po wersji, należy określić za pomocą [WV](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora. Jest to przydatne do zarządzania proces kompilacji, gdy wprowadzenia nowej wersji zestawu narzędzi, a chcesz tymczasowo pominąć nowe ostrzeżenia. Ta opcja odrzuca nowe komunikaty o błędach. Firma Microsoft nie zaleca się pominąć wszystkie nowe ostrzeżenia trwale! Firma Microsoft zaleca, zawsze Kompiluj na najwyższym poziomie ostrzeżenia regularnych, __/W4__i Usuń __WV__ opcji kompilacji tak szybko, jak to możliwe.

Te wersje kompilatora wprowadzono nowe ostrzeżenia:

| Produkt | Numer wersji kompilatora |
|-|-|
| Visual C++ 2002 | 13.00.9466 |
| Visual C++ 2003 | 13.10.3077 |
| Visual C++ 2005 | 14.00.50727.762 |
| Visual C++ 2008 | 15.00.21022.08 |
| Visual C++ 2010 | 16.00.40219.01 |
| Visual C++ 2012 | 17.00.51106.1 |
| Visual C++ 2013 | 18.00.21005.1 |
| Visual C++ 2015 RTM | 19.00.23026.0 |
| Visual C++ 2015 Update 1 | 19.00.23506.0 |
| Visual C++ 2015 Update 2 | 19.00.23918.0 |
| Visual C++ 2015 Update 3 | 19.00.24215.1 |
| Visual C++ 2017 RTM | 19.10.25017.0 |
| Visual C++ 2017 wersja 15.3 | 19.11.25506.0 |
| Visual C++ 2017, wersja 15.5 | 19.12.25830.0 |
| Visual C++ 2017 w wersji 15.6 | 19.13.26128.0 |
| Visual C++ 2017 w wersji 15.7 | 19.14.26428.0 |

Można określić tylko główny numer, głównych i pomocniczych numerów lub głównych i pomocniczych i tworzyć numery __WV__ opcji. Kompilator zgłasza wszystkie ostrzeżenia, które odpowiadają wersji, które zaczynają się od podanej liczbie i wyłącza wszystkie ostrzeżenia dla wersji większy niż określoną liczbę. Na przykład __/Wv:17__ raportuje wszystkie ostrzeżenia wprowadzone w lub przed dowolnej wersji programu Visual Studio 2012 i wyłącza wszystkie ostrzeżenia wprowadzone za pomocą dowolnego kompilatora z programu Visual Studio 2013 (wersja 18) lub nowszego. Aby pominąć ostrzeżenia wprowadzone w programie Visual Studio 2015 update 2 i później, możesz użyć __/Wv:19.00.23506__. Użyj __/Wv:19.11__ zgłosić wszystkie ostrzeżenia wprowadzone w dowolnej wersji programu Visual Studio przed Visual Studio 2017 w wersji 15.5, ale pomija ostrzeżenia wprowadzone w programie Visual Studio 2017 w wersji 15.5 lub nowszej.

W poniższych sekcjach wymieniono ostrzeżenia wynikające z każdą wersją programu Visual C++, który można pominąć za pomocą __WV__ — opcja kompilatora. __WV__ opcji nie można pominąć ostrzeżenia, które nie zostały wymienione, które powstały wcześniej niż określona wersji kompilatora.

## <a name="warnings-introduced-in-visual-c-2017-version-157-compiler-version-1914264280"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 wersji 15.7 (wersja kompilatora 19.14.26428.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.13__.

|||
|-|-|
C4642|"*problem*": nie można zaimportować ograniczeń dla parametru ogólnego "*parametr*"
C5045|Kompilator wstawi zaradcze dla luki Spectre dla obciążenia pamięci Jeśli przełącznik/qspectre określonych

## <a name="warnings-introduced-in-visual-c-2017-version-156-compiler-version-1913261280"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 w wersji 15.6 (wersja kompilatora 19.13.26128.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.12__.

|||
|-|-|
C5044|Argument opcji wiersza polecenia *opcji* wskazuje ścieżkę "*ścieżki*' który nie istnieje

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258300"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 w wersji 15.5 (wersja kompilatora 19.12.25830.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.11__.

|||
|-|-|
C4843|"*type1*": procedura obsługi wyjątków odwołania do typu funkcji lub tablicy jest nieosiągalna, użyj "*type2*" zamiast niego
C4844|"Eksportuj modułu *nazwa_modułu*;" jest teraz preferowana składnia do deklarowania interfejsu modułu
C5039|"*funkcja*": wskaźnik lub odwołanie do funkcji potencjalnie zgłaszającej wyjątek przekazano do funkcji extern języka C w ramach - EHc. Niezdefiniowane zachowanie może wystąpić, jeśli ta funkcja zgłosi wyjątek.
C5040|specyfikacje wyjątków dynamicznych są prawidłowe tylko w języku C ++ 14 i starszych wersji; traktowanie jako opcja noexcept(false)
C5041|"*definicji*": definicja końca wiersza dla składowej danych statycznych constexpr jest niepotrzebna i jest przestarzała w języku C ++ 17
C5042|"*deklaracji*": deklaracje funkcji w zakresie bloku nie może być określone jako "inline" w standardzie języka C++; Usuń specyfikator "inline"
C5043|"*specyfikacji*': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 w wersji 15.3 (wersja kompilatora 19.11.25506.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.10__.

|||
|-|-|
C4597|Niezdefiniowane zachowanie: *opis*
C4604|"*typu*": przekazywanie argumentów poprzez wartość granicę natywne i zarządzane wymaga prawidłowej kopii konstruktora. W przeciwnym razie działanie środowiska uruchomieniowego jest niezdefiniowane
C4749|warunkowo obsługiwane: *opis*
C4768|atrybuty __declspec przed specyfikacją konsolidacji są ignorowane.
C4834|Odrzucanie zwracanej wartości funkcji z atrybutem "nodiscard"
C4841|użyto niestandardowego rozszerzenia: *rozszerzenia*
C4842|nie gwarantuje wynik makra "offsetof" zastosować do typu używającego wielu dziedziczeń będzie spójny między wydaniami kompilatora
C4869|"nodiscard" można stosować tylko w przypadku klas, wyliczeń i funkcji z typem zwracanym niż void
C5033|"*klasę magazynu*" nie jest już obsługiwaną klasą magazynu
C5034|Użyj wewnętrznych "*wewnętrzne*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa
C5035|Użyj funkcji "*funkcji*" powoduje, że funkcja *funkcja* jest kompilowana jako kod gościa
C5036|Konwersja wskaźnika funkcji typu varargs podczas kompilowania za pomocą /hybrid:x86arm64 "*type1*"to"*type2*"
C5037|"*funkcja elementu członkowskiego*": definicja końca wiersza składowej szablonu klasy nie może mieć argumentów domyślnych
C5038|element członkowski danych "*Członek1*"zostanie zainicjowany po element członkowski danych"*członek2*"

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-1910250170"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2017 RTM (wersja kompilatora 19.10.25017.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.00__.

|||
|-|-|
C4468|"fallthrough": atrybut musi następować etykieta case lub default
C4698|"*funkcji*" jest przeznaczony wyłącznie do celów oceny i może ulec zmianie, albo usunięty w przyszłych aktualizacjach.
C4839|niestandardowe użycie klasy*klasy*"jako argumentu do funkcji ze zmienną liczbą argumentów
C4840|nieprzenośne użycie klasy*klasy*"jako argumentu do funkcji ze zmienną liczbą argumentów

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 3 (wersja kompilatora 19.00.24215.1)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.00.23918__.

|||
|-|-|
C4467|Korzystanie z atrybutów ATL jest przestarzałe.
C4596|"*nazwa*": niedozwolona kwalifikowana nazwa w deklaracji składowej
C4598|"#include \< *nagłówka*\>": numer nagłówka *numer* w *źródła* nie odpowiada *źródła* w tym stanowisko
C4599|"*argument*": *źródła* numerem argumentu *numer* nie odpowiada *źródła*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 2 (wersja kompilatora 19.00.23918.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.00.23506__.

|||
|-|-|
C4466|Nie można wykonać sterty dla koprocedury
C4595|"*klasy*": nowy operator składowej ani funkcje delete nie mogą być deklarowane wbudowane
C4828|Plik zawiera znak rozpoczynający się od przesunięcia 0 x*wartość* jest niedozwolony w bieżącym zestawie znaków źródła (strona kodowa *numer*).
C4868|Kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjatora w nawiasach klamrowych

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 Update 1 (wersja kompilatora 19.00.23506.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:19.00.23026__.

|||
|-|-|
C4426|flagi optymalizacji zmieniły się po dołączeniu nagłówka, może być #pragma Optimize()
C4654|Kod umieszczony przed elementem obejmują wstępnie skompilowanego nagłówka wiersza zostaną zignorowane. Dodaj kod do wstępnie skompilowanego nagłówka.
C5031|#pragma warning(pop): prawdopodobnie niezgodność, stan ostrzeżenia wypychany w innym pliku o wyświetlaniu
C5032|Wykryto #pragma warning(push) nie odpowiedniego #pragma warning(pop)

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2015 RTM (wersja kompilatora 19.00.23026.0)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/WV: 18__.

|||
|-|-|
C4427|"*błąd*": przepełnienie w czasie dzielenia stałej, niezdefiniowane zachowanie
C4438|"*typu*": nie można bezpiecznie wywołać / await: clrcompat trybu. Jeśli "*typu*" wywołuje środowisko CLR może spowodować uszkodzenie nagłówka środowiska CLR
C4455|"operator *nazwa*": identyfikatory sufiksu literału, które nie rozpoczynają się od znaku podkreślenia są zarezerwowane
C4456|Deklaracja "*nazwa*" powoduje ukrycie poprzedniej deklaracji lokalnej
C4457|Deklaracja "*nazwa*" powoduje ukrycie parametru funkcji
C4458|Deklaracja "*nazwa*" powoduje ukrycie składowej klasy
C4459|Deklaracja "*nazwa*" powoduje ukrycie deklaracji globalnej
C4462|"*typu*": nie można określić GUID typu. Program może ulec awarii w czasie wykonywania.
C4463|przepełnienie; Przypisywanie *wartość* do pola bitowego, która może zawierać wartości z *wartość* do *wartość*
C4473|"*funkcja*": przekazano za mało argumentów dla ciągu formatu
C4474|"*funkcja*": przekazano zbyt wiele argumentów dla ciągu formatowania
C4475|"*funkcja*": modyfikator długości "*modyfikator*"nie może być stosowany ze znakiem pola typu"*znak*" w specyfikatorze formatu
C4476|"*funkcja*": nieznany znak pola typu "*znak*" w specyfikatorze formatu
C4477|"*— funkcja*": ciąg formatu "*ciąg*"wymaga argumentu typu"*typu*", ale ze zmienną liczbą argumentów *numer* ma typ "*typu*"
C4478|"*funkcja*": nie można łączyć pozycyjnych i niepozycyjnych symbole zastępcze w tym samym ciągu formatu
C4494|"*typu*": Ignorowanie __declspec(allocator), ponieważ typ zwracany funkcji nie jest wskaźnikiem lub odwołaniem
C4495|użyto niestandardowego rozszerzenia "__super": Zamień jawną nazwę klasy bazowej
C4496|użyto niestandardowego rozszerzenia "for each": Zamień na instrukcję ranged-for
C4497|użyto niestandardowego rozszerzenia "sealed": Zamień "final"
C4498|użyto niestandardowego rozszerzenia: "*rozszerzenia*"
C4499|"*specjalizacji*": jawna specjalizacja nie może zawierać klasy magazynu (zignorowany)
C4576|Typ ujęty w nawiasy, następuje lista inicjalizatora jest składnia konwersji typu jawnego niestandardowych
C4577|"noexcept" używane z nie trybu; obsługi wyjątków Zakończenie na wyjątek nie jest gwarantowana. Określ/ehsc
C4578|"abs": konwersja z "*typu*"to"*typu*", możliwa utrata danych (Czy chodziło Ci o wywołanie "*nazwa*" lub #include \<cmath >?)
C4582|"*typu*": Konstruktor nie jest wywoływany niejawnie
C4583|"*typu*": destruktor nie jest wywoływany niejawnie
C4587|"*typu*": Zmiana zachowania: Konstruktor nie jest już niejawnie jest wywoływany.
C4588|"*typu*": Zmiana zachowania: destruktor jest wywoływany nie jest już niejawnie
C4589|Konstruktor klasy abstrakcyjnej*typu*"ignoruje inicjatora w przypadku wirtualnej klasy bazowej"*typu*"
C4591|limit głębokości wywołań wyrażeń "constexpr" *numer* przekracza (/ constexpr: DEPTH\<liczba >)
C4592|"*typu*": symbol zostanie dynamicznie zainicjowany (ograniczenie implementacji)
C4593|"*typu*": "constexpr" wywołanie oceny kroku limit *wartość* przekroczyła; Użyj/constexpr: Steps\<numer > Aby zwiększyć limit
C4647|Zmiana zachowania: __is_pod (*typu*) ma inną wartość w poprzednich wersjach
C4648|Atrybut standardowy "carries_dependency" jest ignorowany.
C4649|atrybuty są ignorowane w tym kontekście
C4753|Nie można odnaleźć granic wskaźnika; Zignorowano funkcję wewnętrzną MPX
C4771|Granice muszą zostać utworzone przy użyciu wskaźnika prostego; Zignorowano funkcję wewnętrzną MPX
C4774|"*opis*": ciąg oczekiwany w argumencie formatu *numer* nie jest ciągiem literału
C4775|użyto niestandardowego rozszerzenia w ciągu formatu "*ciąg*"funkcji"*funkcja*"
C4776|"%*znak*"nie jest dozwolony w ciągu formatowania lub funkcji"*funkcja*"
C4777|"*opis*": ciąg formatu "*ciąg*"wymaga argumentu typu"*typu*", ale ze zmienną liczbą argumentów *numer* ma typ "*typu*"
C4778|"*opis*": niezakończony ciąg formatu "*ciąg*"
C4838|Konwersja z "*typu*"to"*typu*" wymaga konwersji zawężającej
C5022|"*typu*": określono wiele konstruktorów przenoszenia
C5023|"*typu*": określono wiele operatorów przypisania przenoszenia
C5024|"*deklaracji*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty
C5025|"*deklaracji*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty
C5026|"*typu*": Konstruktor przenoszenia został niejawnie zdefiniowany jako usunięty
C5027|"*typu*": Przenieś operator przypisania został niejawnie zdefiniowany jako usunięty
C5028|"*nazwa*": wyrównanie określone we wcześniejszej deklaracji (*numer*) nie jest określona w definicji
C5029|użyto niestandardowego rozszerzenia: atrybuty wyrównania w języku C++ dotyczą zmiennych, składowych danych i tylko dla typów tagów
C5030|atrybut "*atrybut*" nie został rozpoznany

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2013 (wersja kompilatora 18.00.21005.1)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:17__.

|||
|-|-|
C4301|"*typu*": przesłanianie wirtualnej funkcji różni się tylko od "*deklaracji*" kwalifikatorem const/volatile
C4316|"*typu*": obiekt przydzielony na stosie może nie wyrównany *numer*
C4380|"*typu*": Konstruktor domyślny nie staną się przestarzałe
C4388|"*tokenu*": niezgodność ze znakiem/bez znaku
C4423|'std::bad_alloc': zostanie przechwycony przez klasę ('*typu*") w wierszu *numer*
C4424|przechwycenie '*typu*'poprzedzone przez'*typu*"w wierszu *numer*; nieprzewidywalne zachowanie może powodować, jeśli zostanie zgłoszony 'std::bad_alloc'
C4425|Nie można zastosować adnotacji SAL do "..."
C4464|względna ścieżka dołączania zawiera ".."
C4575|"__vectorcall" jest niezgodna z "/ clr" opcja: konwertowanie na "__stdcall"
C4609|"*typu*"pochodzi z domyślnym interfejsem"*typu*"w typie"*typu*". Użyj innego interfejsu domyślnego dla "*typu*", lub przerwać relację bazową/dziedziczoną.
C4754|Reguły konwersji dla operacji arytmetycznych w porównaniu na *opis*(*numer*) oznacza, że jedna gałąź nie może być wykonywane. Rzutowania "*typu*"to"*typu*" (lub podobny typ o *numer* bajtów).
C4755|Reguły konwersji dla operacji arytmetycznych w porównaniu na *opis*(*numer*) oznacza, że jedna gałąź nie można wykonać w funkcji śródwierszowych. Rzutowania "*typu*"to"*typu*" (lub podobny typ o *numer* bajtów).
C4767|Nazwa sekcji '*nazwa*"jest dłuższa niż 8 znaków i zostanie obcięta przez konsolidator
C4770|częściowo zweryfikowane wyliczenie "*nazwa*" używane jako indeks
C4827|Publiczne Metoda 'ToString' o 0 parametrach powinna być oznaczona jako virtual i zastąpienia
C4882|przekazywanie funktorów z operatorami niestały wywołania do concurrency::parallel_for_each jest przestarzałe
C4973|"*typu*": oznaczone jako przestarzałe
C4974|"*typu*": oznaczone jako przestarzałe
C4981|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ zawiera semantykę wyjątku
C4990|Warbird: *wiadomości*
C4991|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ poziom ochrony przed wstawianiem do treści jest większy niż element nadrzędny
C4992|Warbird: funkcja "*deklaracji*" oznaczona jako __forceinline nie jest śródwierszowa, ponieważ zawiera wstawiony zestaw, który nie może być chroniony

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2012 (wersja kompilatora 17.00.51106.1)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:16__.

|||
|-|-|
C4330|atrybut "*atrybut*"w sekcji"*sekcji*" zignorowany
C4415|duplicate __declspec(code_seg('*name*'))
C4416|__declspec(code_seg(...)) zawiera pusty ciąg: ignorowane
C4417|utworzenie wystąpienia jawnego szablonu nie może mieć __declspec(code_seg(...)): ignorowane
C4418|__declspec(code_seg(...)) został zignorowany w wyliczeniu
C4419|"*nazwa*"nie ma wpływu podczas zastosowane do prywatnej klasy ref"*typu*".
C4435|"*typu*": układ obiektu pod/vd2 zmieni się z powodu bazy wirtualnej "*typu*"
C4436|dynamic_cast z bazy wirtualnej "*typu*"to"*typu*" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem
C4437|dynamic_cast z bazy wirtualnej "*typu*"to"*typu*" może nie działać w niektórych kontekstach
C4443|Oczekiwano wartości parametru pragma "0", "1" lub "2"
C4446|"*typu*": nie można mapować składowej "*nazwa*" do tego typu, ze względu na konflikt z nazwą typu. Metoda została zmieniona na "*nazwa*"
C4447|podpis "main" bez modelu wątkowości. Rozważ użycie "int głównego (Platform::Array\<Platform::String ^ > ^ args)".
C4448|"*typu*" nie ma domyślnego interfejsu określonego w metadanych. Pobrania: "*typu*", która może ulec awarii w czasie wykonywania.
C4449|"*typu*" typ niezapieczętowany powinien być oznaczony jako "[WebHostHidden]"
C4450|"*typu*"powinien być oznaczony jako "[WebHostHidden]" ponieważ dziedziczy"*typu*"
C4451|"*typu*": użycie klasy ref*typu*' wewnątrz tego kontekstu może doprowadzić do nieprawidłowego kierowania obiektami między kontekstami
C4452|"*typu*": typ publiczny nie może być w zakresie globalnym. Musi być w przestrzeni nazw, który jest elementem podrzędnym nazwy wyjściowego pliku .winmd.
C4453|"*typu*": typ "[WebHostHidden]", nie powinien być używany na publikowanej powierzchni typu publicznego, który nie jest "[WebHostHidden]"
C4454|"*typu*" jest przeciążony przez więcej niż liczba parametrów wejściowych bez konieczności [DefaultOverload] określony. Pobrania "*deklaracji*" jako domyślne przeciążenie
C4471|"*nazwa*": deklaracja zapowiadająca wyliczenia nieobjętego zakresem musi mieć podstawowy typ (zakładany jest int)
C4472|"*nazwa*" jest natywnym wyliczeniem: Dodaj specyfikator dostępu (private/public), aby zadeklarować wyliczenie zarządzane/WinRT
C4492|"*typu*": dopasowuje metody bazowej klasy referencyjnej "*typu*", ale nie jest oznaczona modyfikatorem "override"
C4493|Usuń wyrażenie nie przynosi efektu jako destruktor "*typu*" nie ma dostępności "public"
C4585|"*typu*": WinRT "public ref class" musi być zapieczętowana lub dziedziczyć po istniejącej niezamkniętej klasie
C4586|"*typu*": typ publiczny nie można zadeklarować w przestrzeni nazw najwyższego poziomu o nazwie "Windows"
C4695|#pragma execution_character_set: "*argument*" jest nieobsługiwanym argumentem: obecnie tylko "UTF-8" jest obsługiwany.
C4703|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej "*nazwa*" używane
C4728|/ Opcja Yl-zignorowane, ponieważ wymagane jest odwołanie do PCH
C4745|nietrwały dostęp "*nazwa*" nie może zostać wdrożona z powodu jego rozmiaru
C4746|nietrwały dostęp "*nazwa*" podlega/volatile:\<iso\|ms >; Rozważ użycie funkcji wewnętrznych __iso_volatile_load/store funkcje wewnętrzne
C4872|dzielenie liczby zmiennoprzecinkowej przez zero wykryta podczas kompilacji wykresu wywołań dla concurrency::parallel_for_each: "*opis*"
C4880|Rzutowanie z "*typu*"to"*typu*": stałości ze wskaźnika lub odwołania może spowodować niezdefiniowane zachowanie w zastrzeżonej funkcji amp
C4881|Konstruktor i/lub destruktor nie zostaną wywołane dla zmiennej tile_static "*typu*"
C4966|"*opis*" ma adnotację __code_seg z nieobsługiwaną nazwą segmentu, adnotacja została zignorowana
C4988|"*typu*": Zmienna zadeklarowana poza zakresem klasy/funkcji
C4989|"*opis*": Typ ma definicje powodujące konflikt.

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2010 (wersja kompilatora 16.00.40219.01)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:15__.

|||
|-|-|
C4352|"*nazwa*": wewnętrzna funkcja już zdefiniowana
C4573|użycie "*typu*" wymaga kompilator do przechwytywania "this" ale nie zezwala na to domyślny tryb przechwytywania bieżącego
C4574|"*nazwa*'jest zdefiniowane jako ' 0': czy zamierzałeś użyć ' #if *nazwa*"?
C4689|"*znak*": nieobsługiwany znak w dyrektywie #pragma detect_mismatch; #pragma ignorowane
C4751|flagi/arch AVX nie ma zastosowania do Intel(R) Streaming SIMD Extensions, się wewnątrz wbudowanego ASM
C4752|Znaleziono Intel(R) Advanced Vector Extensions; należy rozważyć użycie odpowiednich flagi/arch AVX
C4837|Wykryto trójznak: "? *znak*"zastępuje"*znak*"
C4986|"*deklaracji*': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją
C4987|użyto rozszerzenia niestandardowego: 'throw (...)'

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2008 (wersja kompilatora 15.00.21022.08)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:14__.

|||
|-|-|
C4396|"*typu*": wbudowany specyfikator nie można użyć, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji
C4413|"*deklaracji*": składowa odwołania jest zainicjowana do tymczasowej, która nie jest zachowana po zakończeniu konstruktora
C4491|"*opis*": ma niedozwolony format wersji języka IDL
C4603|"*nazwa*": makro jest niezdefiniowane lub definicja różni się po użyciu prekompilowanego nagłówka
C4627|"*opis*": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka
C4750|"*opis*": funkcja zawierająca _alloca() została wbudowana w pętlę
C4910|"*typu*": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem
C4985|"*deklaracji*": Brak atrybutów w poprzedniej deklaracji.

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2005 (wersja kompilatora 14.00.50727.762)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:13__.

|||
|-|-|
C4000|Nieznane ostrzeżenie, wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji
C4272|"*typu*": jest oznaczony jako __declspec(dllimport); należy określić natywną Konwencję wywoływania podczas importu funkcji.
C4333|"*wyrażenie*": przesunięcie w prawo o zbyt dużą liczbę, utrata danych
C4334|"*wyrażenie*": wynik 32-bitowe przesunięcia niejawnie skonwertowano do 64 bitów (była 64-bitowe przesunięcie przeznaczone?)
C4335|Wykryto format pliku Mac: Skonwertuj plik źródłowy do formatu DOS lub systemu UNIX
C4342|Zmiana zachowania: "*typu*" o nazwie, ale operator składowej został wywołany w poprzednich wersjach
C4350|Zmiana zachowania: "*deklaracji*"o nazwie zamiast"*deklaracji*"
C4357|Znaleziono argument tablicy parametrów w liście formalnych argumentów dla delegata "*deklaracji*"zignorowano podczas generowania"*typu*"
C4358|"*wyrażenie*": zwracany typ połączonych delegatów nie jest "void"; zwrócona wartość jest niezdefiniowana
C4359|"*typu*": specyfikator wyrównania jest mniejszy niż rzeczywiste wyrównanie (*numer*) i zostaną zignorowane.
C4362|"*typu*": wyrównanie większe niż 8 bajtów nie jest obsługiwana przez CLR
C4364|#using dla zestawu '*nazwa*"poprzednio widziano w *opis*(*numer*) bez atrybutu as_friend; nie stosowane as_friend
C4365|"*wyrażenie*': konwersja z"*typu*"to"*typu*', niezgodność ze znakiem/bez znaku
C4366|Wynik jednoargumentowy "*operator*" operator może być niewyrównany
C4367|Konwersja z "*typu*"to"*typu*" może spowodować wyjątek niespójności typu danych
C4368|Nie można zdefiniować "*nazwa*"as "zarządzane przez członkiem*typu*": mieszane typy nie są obsługiwane.
C4369|"*typu*": moduł wyliczający wartość "*numer*"nie może być reprezentowany jako"*typu*", wartość to"*numer*"
C4374|"*deklaracji*": metoda interfejsu nie będzie zaimplementowana przez niewirtualną metodę "*deklaracji*"
C4375|Niepubliczna metoda "*deklaracji*"nie przesłania"*deklaracji*"
C4376|specyfikatorze dostępu "*specyfikator*:" nie jest już obsługiwany: Użyj "*specyfikator*:" zamiast niego
C4377|typy natywne są domyślnie; prywatny -d1PrivateNativeTypes jest przestarzały
C4378|Należy uzyskać wskaźniki do funkcji, aby uruchomić inicjatory; należy wziąć pod uwagę system::ModuleHandle:: resolvemethodhandle
C4379|Wersja *wersji* common language runtime nie jest obsługiwana przez ten kompilator. Korzystanie z tej wersji może spowodować nieoczekiwane wyniki
C4381|"*deklaracji*": metoda interfejsu nie będzie zaimplementowana przez niepubliczna metoda "*deklaracji*"
C4382|Zgłaszanie "*typu*": typ z destruktorem __clrcall lub konstruktorem kopiującym można tylko przechwycić w/CLR: pure modułu
C4383|"*typu*": znaczenie usunięcia odwołania do dojścia można zmienić, gdy zdefiniowana przez użytkownika "*operator*" operator istnieje; Zapisz operator jako funkcję statyczną aby była niejawna przy korzystaniu z operandu
C4384|#pragma "*dyrektywy*" należy używać tylko w zakresie globalnym
C4393|"*typu*": const nie ma wpływu *opis* element członkowski danych; ignorowany
C4394|"*typu*": symbol per-appdomain nie powinien być oznaczony przez __declspec (*wartość*)
C4395|"*typu*": funkcja składowa zostanie wywołana na kopii składowej danych initonly "*typu*"
C4397|DefaultCharSetAttribute jest ignorowany
C4398|"*typu*": globalny obiekt dla poszczególnych procesu mogą nie działać poprawnie z wieloma domenami aplikacji; należy wziąć pod uwagę użycie __declspec(appdomain)
C4399|"*typu*": symbol w procesie nie powinien być oznaczony przez __declspec (*wartość*) gdy skompilowano z opcją/CLR: pure
C4400|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.
C4412|"*deklaracji*': podpis funkcji podpis zawiera typ"*typu*'; Obiekty C++ są bezpieczne przekazywanie między kodem czystym i mieszanym lub macierzystym.
C4429|możliwe niekompletne lub niepoprawnie uformowane universal-character-name
C4430|brak specyfikatora typu — zakładany int. Uwaga: C++ nie obsługuje domyślnie typu int
C4431|brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnego int
C4434|statyczny Konstruktor musi posiadać prywatną dostępność; Zmiana na prywatny dostęp
C4439|"*typu*": definicja funkcji z zarządzanym typem w sygnaturze musi mieć konwencję wywołania __clrcall
C4441|Konwencja wywoływania '*Konwencji*"ignorowane. "*Konwencji*" zamiast tego użyć
C4445|"*deklaracji*": w typie zarządzane WinRT nie może być prywatny metody wirtualnej
C4460|CLR/WinRT operatora "*typu*", ma parametr przekazywany przez odwołanie. CLR/WinRT operatora "*operator*"ma semantykę różną od operatora C++"*operator*", czy zamierzasz przekazać przez wartość?
C4461|"*typu*": Ta klasa ma finalizator "! *Typ*"ale nie ma destruktora" ~*typu*"
C4470|dyrektywy pragma sterowania zmiennoprzecinkowego zignorowane z opcją/CLR
C4480|użyte rozszerzenie niestandardowe: Określanie typu podstawowego dla wyliczenia "*typu*"
C4481|użyte rozszerzenie niestandardowe: specyfikator override "*specyfikator*"
C4482|używane niestandardowe rozszerzeni: enum '*typu*"użyte w nazwie kwalifikowanej
C4483|Błąd składniowy: Oczekiwano słowa kluczowego języka C++
C4484|"*typu*": pasuje metody bazowej klasy referencyjnej "*typu*", ale nie jest oznaczona modyfikatorem "virtual", "new" lub "override"; przyjęto "new" (a nie "virtual")
C4485|"*typu*": dopasowania metody bazowej klasy referencyjnej "*typu*", ale nie jest oznaczona "new" ani "override"; przyjęto "new" (i "virtual")
C4486|"*typu*": prywatna metoda wirtualna klasy referencyjnej lub klasy wartości powinna być oznaczona jako "sealed"
C4487|"*typu*": pasuje dziedziczone metody niewirtualnej "*typu*", ale to nie jawnie oznaczona modyfikatorem "new"
C4488|"*typu*": wymaga "*— słowo kluczowe*"słowo kluczowe, aby zaimplementować metodę interfejsu"*typu*"
C4489|"*— słowo kluczowe*": niedozwolony dla metody interfejsu "*nazwa*"; zastąpienie specyfikatorów są dozwolone tylko dla metod klasy ref i klas wartości
C4490|"*— słowo kluczowe*": Niepoprawne użycie specyfikatora override; "*typu*" nie odpowiada metodzie bazowej klasy referencyjnej
C4538|"*typu*": kwalifikatory const/volatile dla tego typu nie są obsługiwane.
C4559|"*typu*": zmiana definicji; __declspec zyski — funkcja (*wartość*)
C4565|"*typu*": zmiana definicji; symbol został poprzednio zadeklarowany za pomocą __declspec (*wartość*)
C4566|znaku, reprezentowane przez universal-character-name "*znak*" nie może być przedstawiony w bieżącej stronie kodowej (*numer*)
C4568|"*typu*": żadne składowe nie odpowiadają sygnaturze jawnego przesłaniania
C4569|"*typu*": żadne składowe nie odpowiadają sygnaturze jawnego przesłaniania
C4570|"*typu*": nie jest jawnie zadeklarowana jako abstrakcyjna, ale ma funkcje abstrakcyjne
C4571|Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane
C4572|Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." zamiast niego
C4580|[attribute] jest przestarzały; zamiast niego określ *określonego*atrybutu jako klasę bazową
C4581|zachowanie przestarzałe: ' "*nazwa*" "zastąpione"*nazwa*"Aby przetwarzać atrybut
C4606|Ostrzeżenie #pragma: "*numer*" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń
C4631|Oprogramowanie MSXML lub XPath niedostępna, dokumentu XML, które nie będą przetwarzane komentarze. *Opis elementu*
C4632|Komentarz dokumentu XML: *opis* — odmowa dostępu: *opis*
C4633|Komentarz dokumentu XML*opis*: błąd: *opis*
C4634|Komentarz dokumentu XML*opis*: nie można zastosować: *opis*
C4635|Komentarz dokumentu XML*opis*: niewłaściwie sformułowany kod XML: *opis*
C4636|Komentarz dokumentu XML*opis*: tag wymaga niepustego "*opis*" atrybutu.
C4637|Komentarz dokumentu XML*opis*: \<obejmują > tag odrzucone. *Opis elementu*
C4638|Komentarz dokumentu XML*opis*: odwołanie do nieznanego symbolu "*opis*".
C4639|Błąd oprogramowania MSXML, dokumentu XML, które nie będą przetwarzane komentarze. *Opis elementu*
C4641|Komentarz dokumentu XML ma niejednoznaczne odwołanie:
C4678|Klasa bazowa*deklaracji*"jest mniej dostępny niż"*nazwa*"
C4679|"*opis*": nie można zaimportować składowej
C4687|"*typu*": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "*typu*"
C4688|"*nazwa*": Lista ograniczeń zawiera prywatny typ zestawu "*deklaracji*"
C4690|\[ emitidl (pop)]: więcej zdejmowań niż włożeń
C4691|"*typu*": oczekiwano typu odwołania w bez odwołań *modułu* "*opis*", typ zdefiniowany w bieżącej jednostce tłumaczenia, zamiast tego użyć
C4692|"*nazwa*': podpis z nieprywatnej składowej zawiera natywny prywatny typ zestawu"*deklaracji*"
C4693|"*typu*": zapieczętowana klasa abstrakcyjna nie może mieć żadnych składowych wystąpienia*nazwa*"
C4694|"*typu*": zapieczętowana klasa abstrakcyjna nie może mieć klasy bazowej*typu*"
C4720|wbudowane raporty asemblera: "*opis*"
C4721|"*opis*": nie jest dostępna jako funkcja wewnętrzna
C4722|"*opis*": destruktor nigdy nie powraca, Potencjalny przeciek pamięci
C4726|ARM arch4/4T obsługuje "\<cpsr_f > lub \<spsr_f >" z adresowaniem natychmiastowym
C4727|PCH o nazwie *nazwa* z tą samą sygnaturą czasową w *nazwa* i *nazwa*.  Za pomocą pierwszego układu PCH.
C4729|Funkcja za duża dla grafu przepływu na podstawie ostrzeżenia
C4730|"*opis*": połączenie typu _m64 i zmiennoprzecinkowa wyrażeń może spowodować niepoprawny kod
C4731|"*opis*": rejestr wskaźnika ramki "*zarejestrować*" zmodyfikowany przez wbudowany kod asemblera
C4732|wewnętrzne "*wewnętrzne*" nie jest obsługiwana w ramach tej architektury
C4733|Przypisanie w wbudowanym do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa
C4734|Więcej niż 64 KB numery wierszy w COFF debugowania sekcji informacji. Zatrzymaj emitowanie numerów linii debugowania formatu COFF dla modułu "*modułu*"
C4738|przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności
C4739|Odwołanie do zmiennej "*zmiennej*" przekracza jego miejsce do magazynowania
C4740|przepływ w lub wyjścia wbudowanego kodu asemblera pomija optymalizację globalną
C4742|"*zmiennej*"ma inne wyrównanie "*lokalizacji*"i"*lokalizacji*": *numer* i *numer*
C4743|"*nazwa*"ma inny rozmiar "*lokalizacji*"i"*lokalizacji*": *numer* i *numer* bajtów
C4744|"*nazwa*"ma inny typ "*lokalizacji*"i"*lokalizacji*": "*typu*"i"*typu*"
C4747|Wywołanie zarządzanego "*typu*": kod zarządzany nie mogą być uruchamiane w ramach blokady modułu ładującego, włączając w to punkt wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL
C4761|Niezgodność rozmiaru całkowitego w argumencie; podano konwersję
C4764|Nie można wyrównać obiektów przechwytywania do więcej niż 16 bajtów
C4788|"*identyfikator*": identyfikator został obcięty do "*numer*" znaków
C4789|bufor "*nazwa*" o rozmiarze *numer* bajtów zostanie przepełniony; *numer* bajtów zostanie zapisane zaczynając od przesunięcia *numer*
C4801|Zwracanie przez odwołanie nie jest możliwe do zweryfikowania: *opis*
C4819|Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (*numer*). Zapisz plik w formacie Unicode, aby zapobiec utracie danych
C4826|Konwersja z "*typu*"to"*typu*' jest rozszerzona o znak. Może to spowodować nieoczekiwane zachowanie.
C4829|Prawdopodobnie niepoprawne parametry funkcji głównego. Należy wziąć pod uwagę "int głównego (Platform::Array\<Platform::String ^ > ^ argv)"
C4835|"*typu*": Inicjator dla eksportowanych danych nie będzie działać, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta
C4867|"*typu*": niestandardowa składnia; Użyj "&", aby utworzyć wskaźnik do składowej
C4936|Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure
C4937|"*nazwa*"i"*nazwa*"są nierozróżnialne jako argumenty"*opcji*"
C4938|"*typu*": zmiennoprzecinkowy zmiennej redukcji punktu może spowodować niespójne wyniki w obszarze/FP: strict lub #pragma fenv_access
C4939|#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++
C4947|"*typu*": oznaczony jako przestarzały
C4949|dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"
C4950|"*typu*": oznaczony jako przestarzały
C4955|"*opis*": Importowanie zostało zignorowane; zaimportowano już z "*źródła*"
C4956|"*typu*": ten typ nie jest możliwe do zweryfikowania
C4957|"*wyrażenie*": jawne rzutowanie z "*typu*"to"*typu*" nie jest możliwe do zweryfikowania
C4958|"*wyrażenie*": arytmetyka wskaźnika nie jest możliwe do zweryfikowania
C4959|Nie można zdefiniować niezarządzanego *klasy* "*typu*" w/CLR: Safe, ponieważ dostęp do jego składowych daje nieweryfikowalny kod
C4960|"*opis*" jest zbyt duży do profilowania
C4961|Dane profilowe nie zostały scalone z "*lokalizacji*", profilowana Optymalizacja została wyłączona
C4962|"*opis*': optymalizacje profilowane wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu
C4963|"*opis*": nie znaleziono danych profilowych; różne opcje kompilatora zostały użyte w kompilacji instrumentowanej
C4964|Opcje optymalizacji nie zostały określone; informacje profilowe nie zostaną zebrane.
C4965|niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania
C4970|Konstruktor delegaty: obiekt docelowy ignorowane od "*deklaracji*" jest statyczny
C4971|Kolejność argumentów: \<obiekt docelowy >, \<docelowa funkcja > dla konstruktora delegaty jest przestarzały, użyj \<docelowa funkcja >, \<obiekt docelowy >
C4972|Nie jest bezpośrednia modyfikacja lub traktowanie wyniku operacji odpakowywania wartościowanego lewostronnie

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2003 (wersja kompilatora 13.10.3077)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:13.00.9466__.

|||
|-|-|
C4343|#pragma optimize (*opis*, wyłączona) przesłania opcję /Og
C4344|Zmiana zachowania: użycie wyników argumentów niejawnego szablonu w wywołaniu elementu "*deklaracji*"
C4346|"*typu*": zależna nazwa nie jest typem
C4348|"*deklaracji*": ponowna definicja domyślnego parametru: parametr *numer*
C4356|"*typu*": nie można zainicjować statycznej składowej danych za pośrednictwem pochodnej klasy
C4408|anonimowe *struktury* nie zadeklarował żadnych składowych danych
C4544|"*deklaracji*": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu
C4545|wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów
C4546|wywołanie funkcji przed przecinkiem, brak listy argumentów
C4547|"*wyrażenie*": operator przed przecinkiem nie przynosi efektu; oczekiwany operator, który przynosi efekt
C4548|wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt
C4549|"*wyrażenie*": operator przed przecinkiem nie ma wpływu; czy chodziło Ci "*wyrażenie*"?
C4628|dwuznaki nieobsługiwane z -Ze. Znak sekwencji "*sekwencji*'nie jest interpretowana jako alternatywny token dla'*tokenu*"
C4629|użyto dwuznaku, sekwencja znaków "*sekwencji*"zinterpretowana jako token"*tokenu*" (Wstaw spację między dwoma znakami, jeśli to nie mają)
C4671|"*opis*": Konstruktor kopiujący jest niedostępny
C4676|"*opis*": destruktor jest niedostępny
C4677|"*nazwa*': podpis z nieprywatnej składowej zawiera prywatny typ zestawu"*deklaracji*"
C4686|"*typu*': możliwe zmiany w zachowaniu, zmiana UDT zwracają konwencji wywoływania
C4812|przestarzała deklaracja stylu: Użyj "*typu*::*nazwa*" zamiast niego
C4813|"*typu*": funkcja zaprzyjaźniona klasy lokalnej musi musiała zostać poprzednio zadeklarowana
C4821|Nie można określić typu kodowania Unicode, Zapisz plik z podpisem (znacznik BOM)
C4822|"*typu*": funkcja składowa klasy lokalnej nie ma treści
C4823|"*typu*": używa, ale operacja unwind unieruchamiania wskaźników semantyki nie są włączone. Rozważ użycie opcji/eha
C4913|Użytkownik zdefiniowany operator binarny "," istnieje, ale żadne przeciążenie nie może konwertować wszystkich argumentów operacji, domyślnego, wbudowanego operatora binarnego "," używane
C4948|zwracany typ "*deklaracji*" jest niezgodny z typem ostatniego parametru odpowiadającej mu metody ustawiającej
C4951|"*opis*" został wyedytowany od profilu dane zostały zebrane, nieużywane dane profilu funkcji
C4952|"*opis*": nie znaleziono danych profilowych w bazie danych programu "*opis*"
C4953|Wbudowany "*opis*" został wyedytowany od profilu dane zostały zebrane, dane profilu nieużywane
C4954|"*opis*": nieprofilowany (zawiera wyrażenie switch __int64)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Ostrzeżenia wprowadzone w programie Visual C++ 2002 (wersja kompilatora 13.00.9466)

Ostrzeżenia te i wszystkie ostrzeżenia w nowszych wersjach, które są pomijane przy użyciu opcji kompilatora __/Wv:12__.

|||
|-|-|
C4096|"*typu*": interfejs nie jest interfejsem COM; nie będzie emitowany do IDL
C4097|Oczekiwano wartości parametru pragma "Restore" lub "off"
C4165|"HRESULT" jest konwertowana na "bool"; Czy na pewno jest to, co chcesz zrobić?
C4183|"*nazwa*": Brak typu zwracanego; założono, że jest funkcją składową zwracającą "int"
C4199|*Opis elementu*
C4255|"*nazwa*": nie podano prototypu funkcji: konwertowanie '()"na"(void)"
C4256|"*deklaracji*": konstruktor dla klasy z bazami wirtualnymi ma "..."; wywołania mogą nie być zgodne ze starszymi wersjami programu Visual C++
C4258|"*nazwa*": definicja z pętli for jest zignorowana; służy definicji z otaczającego zakresu
C4263|"*deklaracji*": funkcja składowa nie zastępuje żadnej funkcji składowej wirtualnej klasy bazowej
C4264|"*deklaracji*': niedostępne zastąpienie dla funkcji wirtualnej składowej z podstawowej"*klasy*'; funkcja jest ukryta
C4265|"*typu*": klasa ma funkcje wirtualne, ale destruktor nie jest wirtualny wystąpienia tej klasy może nie być prawidłowo niszczone
C4266|"*deklaracji*': niedostępne zastąpienie dla funkcji wirtualnej składowej z podstawowej"*klasy*'; funkcja jest ukryta
C4267|"*wyrażenie*': konwersja z"size_t"do"*typu*", możliwa utrata danych
C4274|#ident ignorowane. zobacz dokumentację dla #pragma comment (exestr, "string")
C4277|importowany element '*typu*::*nazwa*"istnieje zarówno jako element członkowski danych i funkcja składowa; składowa danych została zignorowana
C4278|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest już makrem; Użyj kwalifikatora "rename"
C4279|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest słowem kluczowym, użyj kwalifikatora "rename"
C4287|"*wyrażenie*": niezgodność stałej bez znaku/ujemnej
C4288|użyto niestandardowego rozszerzenia: "*nazwa*": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for; jest w konflikcie z deklaracją w zewnętrznym zakresie
C4289|użyto niestandardowego rozszerzenia: "*nazwa*": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for
C4293|"*wyrażenie*": licznik przesunięć ujemny lub zbyt duży, niezdefiniowane zachowanie
C4295|"*typu*": tablica jest zbyt mała, aby uwzględnić znak końcowy null
C4296|"*wyrażenie*": wyrażenie ma zawsze wartość *wartość*
C4297|"*typu*": Funkcja przyjmuje się, że nie zgłasza wyjątku, ale nie
C4298|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest już makrem; zmiana nazwy na "__*nazwa*"
C4299|"*nazwa*": identyfikator w bibliotece typów "*opis*" jest słowem kluczowym, zmiana nazwy na "__*nazwa*"
C4302|"*wyrażenie*': obcinanie z '*typu*"to"*typu*"
C4303|*Konwersja* z "*typu*"to"*typu*" jest przestarzały, użyj static_cast, __try_cast lub dynamic_cast
C4314|Oczekiwano wartości parametru pragma "32" lub "64"
C4315|"*typu*": wskaźnik "this" dla elementu członkowskiego "*typu*" może nie wyrównany *numer* zgodnie z oczekiwaniami, Konstruktor
C4318|przekazanie stałej o wartości zero jako długość do funkcji memset
C4319|"*wyrażenie*": zero rozszerzanie "*typu*"to"*typu*' o większym rozmiarze
C4321|automatycznie generowane IID dla interfejsu "*typu*"
C4322|automatycznie generowane CLSID dla klasy*typu*"
C4323|ponowne wykorzystanie zarejestrowanego identyfikatora CLSID dla klasy*typu*"
C4324|"*typu*": struktura została wzmocniona ze względu na specyfikator wyrównania
C4325|atrybuty dla standardowej sekcji "*opis*" zignorowany
C4326|zwracany typ "*nazwa*powinien być*typu*"zamiast z"*typu*"
C4327|"*wyrażenie*": operator pośredni wyrównania LHS (*numer*) jest większy niż RHS (*numer*)
C4328|"*opis*": operator pośredni wyrównania formalnego parametru *numer* (*numer*) jest większy niż rzeczywisty argument wyrównania (*numer*)
C4329|Specyfikator wyrównania jest ignorowany w wyliczeniu
C4336|Importowanie biblioteki typów odsyłaczy "*biblioteki*"przed importem"*opis*"
C4337|Biblioteka typów odsyłaczy "*biblioteki*"in"*opis*" jest automatycznie importowana
C4338|#pragma *opis*: standardowa sekcja "*sekcji*" jest używany
C4339|"*typu*": użycie niezdefiniowanego typu wykryte w CLR/WinRT meta-data - użycie tego typu może prowadzić do wyjątku czasu wykonywania
C4353|użyto niestandardowego rozszerzenia: stała 0 jako wyrażenie funkcyjne.  Zamiast tego użyj funkcji wewnętrznej "__noop" wewnętrzne
C4370|"*deklaracji*": układ klasy zmienił się z poprzedniej wersji kompilatora ze względu na lepsze pakowanie
C4371|"*deklaracji*": układ klasy mógł się zmienić z poprzedniej wersji kompilatora ze względu na lepsze pakowanie składowej '*elementu członkowskiego*"
C4373|"*typu*": przesłonięcia funkcji wirtualnych*deklaracji*", poprzednie wersje kompilatora nie przesłaniały, gdy parametry różnił się tylko przez kwalifikatory const/volatile
C4387|"*opis*': została uznana za
C4389|"*wyrażenie*": niezgodność ze znakiem/bez znaku
C4391|"*deklaracji*": nieprawidłowy typ zwracany dla wewnętrznej funkcji, oczekiwano "*typu*"
C4392|"*deklaracji*": Nieprawidłowa liczba argumentów dla wewnętrznej funkcji, oczekiwano "*numer*" argumentów
C4407|Wykonuj rzutowania między różnych reprezentacjami wskaźników do składowej, kompilator może wygenerować niepoprawny kod
C4420|"*nazwa*": operator nie jest dostępny, za pomocą "*nazwa*" zamiast niego; kontrola czasu wykonania mogą być narażone na ataki
C4440|wywoływanie ponowną definicję Konwencji wywołań z "*opis*"to"*opis*" zignorowany
C4442|osadzony terminator o wartości null w argumencie __annotation.  Wartość zostanie obcięta.
C4444|"*nazwa*": najwyższego poziomu '__unaligned' nie jest zaimplementowany w tym kontekście
C4526|"*typu*": funkcja statycznej składowej nie można przesłonić funkcji wirtualnej '*deklaracji*"zastąpienie zignorowane, funkcja wirtualna zostanie ukryta
C4531|Obsługa wyjątków języka C++ nie jest dostępny na Windows CE. Użyj wyjątków strukturalnych
C4532|"*opis*": przeskoczyć poza *na koniec* bloku ma niezdefiniowane zachowanie podczas obsługi zakończenia
C4533|Inicjalizacja "*deklaracji*" jest pomijana przy "goto *deklaracji*"
C4534|"*deklaracji*" nie będzie konstruktorem domyślnym dla *klasy* "*typu*" z powodu argumentu domyślnego
C4535|Wywołanie funkcji _set_se_translator() wymaga/eha
C4536|"*opis*': Nazwa typu przekracza limit meta-data"*numer*"znaków
C4537|"*deklaracji*": "." zastosowany do typu innego niż UDT
C4542|Pomijanie generowania scalonego wstrzykniętego pliku tekstowego, nie można zapisać *typu* pliku: "*filename*": *błąd*
C4543|Wprowadzony tekst pominięty przez atrybut "nie\_injected_text"
C4555|wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt
C4557|"__assume" zawiera efekt '*efekt*"
C4558|wartość operandu "*numer*"jest poza zakresem"*numer* - *numer*"
C4561|Wywołanie "__fastcall" niezgodne z "/ clr" opcja: konwertowanie na "__stdcall"
C4562|w pełni prototypowane są wymagane w przypadku "/ clr" opcja: konwertowanie '()"na"(void)"
C4564|Metoda "*nazwa*" z *klasy* "*typu*"definiuje nieobsługiwany parametr domyślny"*parametr*"
C4584|"*typu*": klasy bazowej*deklaracji*"jest już klasą bazową dla"*deklaracji*"
C4608|Inicjowanie wielu składowych Unii: "*typu*"i"*typu*"
C4619|Ostrzeżenie #pragma: Brak ma numeru ostrzeżenia '*numer*"
C4623|"*typu*": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty
C4624|"*typu*": destruktor został niejawnie zdefiniowany jako usunięty
C4625|"*typu*": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty
C4626|"*typu*": operator przypisania został niejawnie zdefiniowany jako usunięty
C4645|Funkcja zadeklarowana ze specyfikatorem "noreturn" zawiera instrukcję return
C4646|Funkcja zadeklarowana ze specyfikatorem "noreturn" ma typ zwracany niż void
C4659|#pragma "*opis*": użycie zastrzeżonego segmentu "*nazwa*" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)
C4667|"*deklaracji*": nie zdefiniowanego szablonu funkcji, który pasuje do wymuszonego wystąpienia
C4668|"*nazwa*'nie jest zdefiniowany jako makro preprocesora, zastępowanie przez '0' dla'*wartość*"
C4669|"*wyrażenie*": niebezpieczna konwersja: "*typu*" jest obiektem typu zarządzanego WinRT
C4674|"*nazwa*" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr
C4680|"*typu*": klasa coclass nie określa domyślnego interfejsu
C4681|"*typu*": klasa coclass nie określa domyślnego interfejsu, który jest źródłem zdarzenia
C4682|"*typu*": nie określono atrybutu kierunkowego parametru, domyślnie na [in]
C4683|"*deklaracji*": źródło zdarzenia ma "out" — parametru; wskazana jest ostrożność podczas podłączania wielu obsług zdarzeń
C4684|"*opis*": ostrzeżenie!! atrybut może powodować generowanie nieprawidłowego kodu: Używaj ostrożnie
C4685|Oczekiwano znaku ">>" znaleziono ">>" podczas analizowania parametrów szablonu
C4700|niezainicjowanej zmiennej lokalnej "*nazwa*" używane
C4701|Użycie potencjalnie niezainicjowanej zmiennej lokalnej "*nazwa*" używane
C4702|nieosiągalny kod
C4711|Funkcja "*nazwa*" wybrane do automatycznego rozwinięcia funkcji wbudowanej
C4714|Funkcja "*deklaracji*" oznaczona jako __forceinline nie jest śródwierszowa
C4715|"*funkcja*": niewszystkie ścieżki kodu zwracają wartość
C4716|"*funkcja*": musi zwracać wartość
C4717|"*funkcja*": cykliczne we wszystkich ścieżkach, funkcja spowoduje przepełnienie stosu środowiska uruchomieniowego
C4718|"*funkcja*": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie
C4719|Stała typu Double znaleziona, gdy określono parametr Qfast - użyj opcji "f" jako przyrostka, aby wskazać pojedynczą precyzję
C4723|potencjalne dzielenie przez 0
C4724|potencjalne dzielenie modulo przez 0
C4725|Instrukcja może być niedokładna na niektórych procesorach Pentium
C4757|Indeks dolny jest dużą wartością bez znaku, czy nie było planowane ujemną stałą?
C4772|#import odwołanie do typu z brakującej biblioteki typów; "*opis*" używana jako symbol zastępczy
C4792|Funkcja "*funkcja*" zadeklarowana za pomocą sysimport i odwołania z kodu natywnego; zaimportuj bibliotekę wymaganą do połączenia
C4794|segment zmiennej lokalny magazyn wątków "*nazwa*"zmieniła się z"*segmentu*"to"*segmentu*"
C4798|natywny kod generowany dla funkcji p-code "*nazwa*" z obsługą wyjątków lub semantyką rozwinięć
C4799|Funkcja "*nazwa*" nie ma instrukcji EMMS
C4803|"*deklaracji*": podniesiona metoda ma klasę magazynu inną od zdarzenia, "*deklaracji*"
C4810|Wartość dyrektywy pragma pack(show) == *numer*
C4811|Wartość dyrektywy pragma conform (forScope, show) == *wartość*
C4820|"*typu*": "*numer*" bajtów dopełnienie dodane po *typu* "*typu*"
C4905|literał ciągu dwubajtowego rzutowany na '*typu*"
C4906|literał ciągu rzutowany na '*typu*"
C4912|"*atrybut*": atrybut ma niezdefiniowane zachowanie w zagnieżdżonym UDT
C4916|Aby uzyskać identyfikator dispid, "*typu*": musi zostać wprowadzony przez interfejs
C4917|"*typu*": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw
C4918|"*znak*": nieprawidłowy znak na liście optymalizacji pragma
C4920|wyliczenia *nazwa* elementu członkowskiego *nazwa*=*numer* już widoczna w typie wyliczeniowym *nazwa* jako *nazwa* = *numer*
C4921|"*nazwa*": wartość atrybutu "*wartość*" nie powinien być określony wielokrotnie
C4925|"*deklaracji*": metoda interfejsu dispinterface nie może być wywoływana ze skryptu
C4926|"*deklaracji*": symbol jest już zdefiniowany: atrybuty zostały zignorowane
C4927|Niedozwolona konwersja; więcej niż jedna konwersja zdefiniowana przez użytkownika została zastosowana niejawnie
C4928|nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika
C4929|"*opis*": Biblioteka typów zawiera Unię; ignorowanie kwalifikatora "embedded_idl"
C4930|"*deklaracji*": prototypowana funkcja nie wywołana (czy definicja zmiennej była przeznaczona?)
C4931|Zakładamy, biblioteka typów została skompilowana dla *numer*-bitowych wskaźników
C4932|__identifier (*opis*) i __identifier (*opis*) są nierozróżnialne
C4934|"__delegate(multicast)" jest przestarzały, należy użyć "__delegate" zamiast niego
C4935|Specyfikator dostępu do zestawu zmodyfikowany z "*opis*"
C4944|"*nazwa*": nie można zaimportować symbolu z "*źródła*": jako*deklaracji*"już istnieje w bieżącym zakresie
C4945|"*nazwa*": nie można zaimportować symbolu z "*źródła*": jako*deklaracji*"został już zaimportowany z innego zestawu"*źródła*"
C4946|reinterpret_cast używane między pokrewnymi klasami: '*deklaracji*"i"*deklaracji*"
C4995|"*nazwa*': nazwa została oznaczona jako przestarzała #pragma
C4996|"*problem*": *opis*
C4997|"*typu*": klasa coclass nie implementuje interfejsu COM lub pseudointerfejsu
C4998|Oczekiwanie nie powiodło się: *opis*(*numer*)

## <a name="see-also"></a>Zobacz także

- [WV — opcja kompilatora](../../build/reference/compiler-option-warning-level.md)
- [Ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
- [ostrzeżenie](../../preprocessor/warning.md)
