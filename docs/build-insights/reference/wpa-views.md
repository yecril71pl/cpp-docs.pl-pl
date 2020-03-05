---
title: 'Odwołanie: widoki Analizatora wydajności systemu Windows'
description: Informacje o C++ widokach usługi Build Insights dostępnych w analizatorze wydajności systemu Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eb3e20ed3ca4231b10efaf36310f6fbc0f5980bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332237"
---
# <a name="reference-windows-performance-analyzer-views"></a>Odwołanie: widoki Analizatora wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Ten artykuł zawiera szczegółowe informacje dotyczące każdego z C++ widoków kompilacji Insights dostępnych w narzędziu Windows Performance ANALYZER (WPA). Ta strona służy do znajdowania:

- opisy kolumn danych; lub
- dostępne ustawienia wstępne dla każdego widoku, w tym ich zamierzone użycie i preferowany tryb wyświetlania.

Jeśli dopiero zaczynasz korzystanie z protokołu WPA, zalecamy zapoznanie się z [podstawowymi informacjami o protokole WPA dla C++ usługi Build Insights](/cpp/build-insights/tutorials/wpa-basics).

## <a name="build-explorer"></a>Build Explorer

Widok Eksplorator kompilacji służy do:

- Diagnozuj problemy z równoległością,
- Ustal, czy czas kompilacji jest zdominowany przez analizowanie, generowanie kodu lub łączenie, oraz
- Identyfikuj wąskie gardła i nietypowo długotrwałe działania kompilacji.

### <a name="build-explorer-view-data-columns"></a>Przeglądanie kolumn danych w Eksploratorze kompilacji

| Nazwa kolumny | Opis |
|-|-|
| BuildTimelineDescription | Tekstowy opis osi czasu, w której występuje bieżące działanie lub właściwość. |
| BuildTimelineId          | Identyfikator (liczony od zera) dla osi czasu, w której występuje bieżące działanie lub właściwość. |
| Składnik                | Składnik, który jest kompilowany lub połączony, gdy bieżące zdarzenie zostało emitowane. Wartość tej kolumny jest *\<wywołań informacji X\>* , gdy żaden składnik nie jest skojarzony z tym zdarzeniem. X jest unikatowym identyfikatorem liczbowym dla wywołania, które jest wykonywane w momencie wygenerowania zdarzenia. Ten identyfikator jest taki sam jak w kolumnie InvocationId dla tego zdarzenia. |
| Licznik                    | Liczba działań lub właściwości reprezentowanych przez ten wiersz danych. Ta wartość jest zawsze 1 i jest przydatna tylko w scenariuszach agregacji w przypadku grupowania wielu wierszy. |
| ExclusiveCPUTime         | Ilość czasu procesora CPU w milisekundach używana przez to działanie. Czas spędzony na działaniach podrzędnych nie jest uwzględniony w tej wartości. |
| ExclusiveDuration        | Czas trwania działania w milisekundach. Czas trwania działań podrzędnych nie jest uwzględniony w tej wartości. |
| InclusiveCPUTime         | Ilość czasu procesora CPU w milisekundach używana przez to działanie i wszystkie działania podrzędne. |
| InclusiveDuration        | Czas trwania tego działania w milisekundach, w tym wszystkie działania podrzędne. |
| InvocationDescription    | Tekstowy opis wywołania, w którym wystąpiło to zdarzenie. Opis zawiera plik *CL. exe* lub *link. exe*i unikatowy identyfikator wywołania numerycznego. Jeśli ma to zastosowanie, obejmuje pełną ścieżkę do składnika skompilowanego lub połączonego podczas wywołania. W przypadku wywołań, które nie kompilują żadnego składnika lub dla tych, które kompilują wiele składników, ścieżka jest pusta. Identyfikator wywołania jest taki sam jak w kolumnie InvocationId. |
| InvocationId             | Unikatowy identyfikator liczbowy wywołania, w którym wystąpiło zdarzenie. |
| Nazwa                     | Nazwa działania lub Właściwości reprezentowanej przez to zdarzenie. |
| Godzina                     | Sygnatura czasowa identyfikująca czas wystąpienia zdarzenia. |
| Narzędzie                     | Narzędzie wykonywane po wystąpieniu tego zdarzenia. Wartość tej kolumny jest równa CL lub link. |
| Typ                     | Typ bieżącego zdarzenia. Ta wartość to działanie lub właściwość. |
| Wartość                    | Jeśli bieżące zdarzenie jest właściwością, ta kolumna zawiera jej wartość. Ta kolumna jest pusta, gdy bieżące zdarzenie jest działaniem. |

### <a name="build-explorer-view-presets"></a>Widok ustawień Eksploratora kompilacji

| Nazwa ustawienia wstępnego           | Preferowany tryb widoku | Jak używać |
|-----------------------|---------------------|------------|
| Statystyka działań   | Wykres/tabela       | To ustawienie wstępne służy do wyświetlania zagregowanych danych statystycznych dla wszystkich działań w programie Build Explorer. W trybie tabeli poinformuj o tym natychmiast, jeśli kompilacja jest zdominowana przez analizowanie, generowanie kodu lub konsolidator. Zagregowane czasy trwania dla każdego działania są sortowane w kolejności malejącej. Przechodzenie do szczegółów przez rozwijanie górnego węzła w celu łatwego znajdowania, które wywołania pobierają najwięcej czasu dla tych najważniejszych działań. Jeśli chcesz, możesz dostosować ustawienia protokołu WPA, aby pokazać średnie lub inne typy agregacji. W trybie grafu, zobacz, kiedy każde działanie jest aktywne podczas kompilacji. |
| Wywołań           | Graph               | Przewiń w dół listę wywołań w widoku wykresu posortowanych według czasu rozpoczęcia. Można jej użyć razem z widokiem procesora CPU (próbkowanym) w celu znalezienia wywołań, które są wyrównane do małych stref użycia procesora CPU. Wykrywaj równoległe problemy. |
| Właściwości wywołania | tabela               | Szybkie znajdowanie najważniejszych informacji o danym kompilatorze lub wywołaniu konsolidatora. Określ wersję, katalog roboczy lub pełny wiersz polecenia, który zostanie użyty do jego wywołania. |
| osie czasu             | Graph               | Zobacz wykres słupkowy sposobu, w jaki Twoja kompilacja została równoległa. Szybko Identyfikuj problemy równoległe i wąskie gardła. Skonfiguruj protokół WPA, aby przypisać różne średnie do pasków zgodnie z potrzebami. Wybierz pozycję opisy wywołań jako ostatnią zgrupowaną kolumnę, aby wyświetlić wykres słupkowy kodowany kolorem wszystkich wywołań. Ułatwia ona szybkie identyfikowanie czasochłonnych culprits. Następnie Powiększ i wybierz nazwę działania jako ostatnią zgrupowaną kolumnę, aby zobaczyć najdłuższe części. |

## <a name="files"></a>Pliki

Widok plików służy do:

- Ustal, które nagłówki są najczęściej uwzględniane.
- pomoc w wyborze, co należy uwzględnić we wstępnie skompilowanym nagłówku (PCH).

### <a name="files-view-data-columns"></a>Kolumny danych widoku plików

| Nazwa kolumny              | Opis |
|--------------------------|-------------|
| ActivityName             | Działanie w toku podczas emitowania tego zdarzenia pliku. Obecnie ta wartość jest zawsze *analizowany*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Składnik                | * |
| Licznik                    | * |
| ścisł                    | Pozycja od zera w drzewie dołączania, w której znajduje się ten plik. Zliczanie zaczyna się od elementu głównego drzewa include. Wartość 0 zazwyczaj odnosi się do pliku. cpp. |
| ExclusiveDuration        | * |
| IncludedBy               | Pełna ścieżka pliku, który zawiera bieżący plik. |
| IncludedPath             | Pełna ścieżka bieżącego pliku. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Sygnatura czasowa, która reprezentuje czas, w którym bieżące zdarzenie pliku zostało wyemitowane. |
| Narzędzie                     | * |

\* wartość tej kolumny jest taka sama jak w widoku [Eksplorator kompilacji](#build-explorer-view-data-columns) .

### <a name="files-view-presets"></a>Ustawienia wyświetlania plików

| Nazwa ustawienia wstępnego | Preferowany tryb widoku | Jak używać |
|-------------|---------------------|------------|
| Statystyki  | tabela               | Zobacz, które pliki mają największy zagregowany czas analizowania, przeglądając listę w kolejności malejącej. Te informacje ułatwiają restrukturyzację nagłówków lub decydowanie o tym, co należy uwzględnić w Twoim PCH. |

## <a name="functions"></a>Funkcje

Widok funkcji służy do identyfikowania funkcji z nadmiernie długim czasem generowania kodu.

### <a name="functions-view-data-columns"></a>Kolumny danych widoku funkcji

| Nazwa kolumny              | Opis |
|--------------------------|-------------|
| ActivityName             | Działanie w toku podczas emitowania tego zdarzenia funkcji. Obecnie ta wartość jest zawsze *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Składnik                | * |
| Licznik                    | * |
| Czas trwania                 | Czas trwania działania generowania kodu dla tej funkcji. |
| FunctionName             | Nazwa funkcji, która jest w trakcie generowania kodu. |
| InvocationId             | * |
| StartTime                | Sygnatura czasowa, która reprezentuje, kiedy bieżące zdarzenie funkcji zostało emitowane. |
| Narzędzie                     | * |

\* wartość tej kolumny jest taka sama jak w widoku [Eksplorator kompilacji](#build-explorer-view-data-columns) .

### <a name="functions-view-presets"></a>Ustawienia wstępne widoku funkcji

| Nazwa ustawienia wstępnego | Preferowany tryb widoku | Jak używać |
|-------------|---------------------|------------|
| Statystyki  | tabela               | Zobacz, które funkcje mają największy zagregowany czas generowania kodu, przeglądając listę w kolejności malejącej. Mogą one mieć wskazówkę, w której kod używa słowa kluczowego **__forceinline** lub że niektóre funkcje mogą być zbyt duże. |
| osie czasu   | Graph               | Spójrz na ten wykres słupkowy, aby poznać lokalizację i czas trwania funkcji, które pobierają najwięcej czasu. Sprawdź, czy w widoku Eksploratora kompilacji są wyrównane z wąskimi gardłami. Jeśli tak, podejmij odpowiednie działania, aby zmniejszyć czas generowania kodu i korzystać z czasów kompilacji. |

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do C++ usługi Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Reference: polecenia vcperf](vcperf-commands.md)\
[Samouczek: podstawowe informacje na temat analizatora wydajności systemu Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
