---
title: 'Odwołanie: Widoki analizatora wydajności systemu Windows'
description: Odwołanie do widoków analizy kompilacji języka C++ dostępnych w analizatorze wydajności systemu Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b54b1b76d83b77ec7b8d8d3309d81ed9eb2db2d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323237"
---
# <a name="reference-windows-performance-analyzer-views"></a>Odwołanie: Widoki analizatora wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia aplikacji Skompilowanie kompilacji języka C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

Ten artykuł zawiera szczegółowe informacje na temat każdego z widoków analizy kompilacji języka C++ dostępnych w analizatorze wydajności systemu Windows (WPA). Użyj tej strony, aby znaleźć:

- opisy kolumn danych; I
- dostępne ustawienia wstępne dla każdego widoku, w tym ich przeznaczenie i preferowany tryb wyświetlania.

Jeśli jesteś nowym użytkownikiem WPA, zalecamy zapoznanie się z [podstawami WPA dla aplikacji C++ Build Insights.](/cpp/build-insights/tutorials/wpa-basics)

## <a name="build-explorer"></a>Eksplorator kompilacji

Widok Eksplorator kompilacji jest używany do:

- diagnozowanie problemów równoległości,
- określić, czy czas kompilacji jest zdominowany przez analizowanie, generowanie kodu lub łączenie oraz
- identyfikować wąskie gardła i niezwykle długie działania związane z budowaniem.

### <a name="build-explorer-view-data-columns"></a>Kolumny danych widoku Eksploratora kompilacji

| Nazwa kolumny | Opis |
|-|-|
| Deska opisu linii BuildTimeline | Opis tekstowy osi czasu bieżącego działania lub właściwości występuje na. |
| KompilacjaCzasuj.          | Identyfikator od zera dla osi czasu bieżącego działania lub właściwości występuje na. |
| Składnik                | Składnik jest kompilowany lub połączony podczas emitowania bieżącego zdarzenia. Wartością tej kolumny jest * \<Invocation X Info,\> * gdy żaden składnik nie jest skojarzony z tym zdarzeniem. X jest unikatowym identyfikatorem liczbowym dla wywołania wykonywanego w momencie emisji zdarzenia. Ten identyfikator jest taki sam jak w kolumnie InvocationId dla tego zdarzenia. |
| Liczba                    | Liczba działań lub właściwości reprezentowanych przez ten wiersz danych. Ta wartość jest zawsze 1 i jest przydatna tylko w scenariuszach agregacji, gdy wiele wierszy są zgrupowane. |
| ExclusiveCPUTime         | Czas procesora CPU w milisekundach używany przez to działanie. Czas spędzony na zajęciach dla dzieci nie jest uwzględniony w tej kwocie. |
| Wyłącznośćducja        | Czas trwania milisekundy działania. Czas trwania zajęć podrzędnych nie jest uwzględniony w tej kwocie. |
| InclusiveCPUTime         | Ilość czasu procesora CPU w milisekundach używane przez to działanie i wszystkie działania podrzędne. |
| InclusiveDuration (InclusiveDuration)        | Czas trwania milisekundy tego działania, w tym wszystkie działania podrzędne. |
| InwokacjaWyscription    | Tekstowy opis wywołania tego zdarzenia wystąpił w. Opis zawiera informacje o tym, czy był to *plik cl.exe,* czy *plik łącz.exe,* oraz unikatowy identyfikator wywołania numerycznego. W stosownych przypadkach zawiera pełną ścieżkę do składnika skompilowanego lub połączonego podczas wywołania. W przypadku wywołań, które nie budują żadnego składnika lub tych, które budują wiele składników, ścieżka jest pusta. Identyfikator wywołania jest taki sam jak identyfikator w kolumnie InvocationId. |
| InvocationId (InvocationIdId)             | Unikatowy identyfikator numeryczny dla wywołania, w którego wystąpiło to zdarzenie. |
| Nazwa                     | Nazwa działania lub właściwości reprezentowanej przez to zdarzenie. |
| Time                     | Sygnatura czasowa identyfikująca wystąpienie zdarzenia. |
| Narzędzie                     | Narzędzie wykonujące, gdy wystąpiło to zdarzenie. Wartość tej kolumny to CL lub Link. |
| Typ                     | Typ bieżącego zdarzenia. Ta wartość jest działanie lub właściwość. |
| Wartość                    | Jeśli bieżące zdarzenie jest właściwością, ta kolumna zawiera jego wartość. Ta kolumna pozostaje pusta, gdy bieżące zdarzenie jest działaniem. |

### <a name="build-explorer-view-presets"></a>Ustawienia predefiniowane widoku Eksploratora kompilacji

| Nazwa predefiniowane           | Preferowany tryb widoku | Jak używać |
|-----------------------|---------------------|------------|
| Statystyki aktywności   | Wykres / Tabela       | To ustawienie predefiniowane służy do wyświetlania zagregowanych statystyk dla wszystkich działań Eksploratora kompilacji. W trybie tabeli, powiedz na pierwszy rzut oka, jeśli kompilacja jest zdominowany przez analizowanie, generowanie kodu lub konsolidatora. Zagregowane czasy trwania dla każdego działania są sortowane w kolejności malejącej. Wy drążą, rozwijając węzeł górny, aby łatwo znaleźć, które wywołania zajmują najwięcej czasu dla tych najlepszych działań. Jeśli chcesz, możesz dostosować ustawienia WPA, aby wyświetlić średnie lub inne typy agregacji. W trybie wykresu, zobacz, kiedy każde działanie jest aktywne podczas kompilacji. |
| Wywołania           | Graph               | Przewiń w dół listę wywołań w widoku wykresu posortowane według czasu rozpoczęcia. Można go używać razem z widokiem CPU (Sampled), aby znaleźć wywołania, które są zgodne ze strefami niskiego wykorzystania procesora CPU. Wykryj problemy z równoległością. |
| Właściwości wywołania | Tabela               | Szybko znajdź kluczowe informacje o danym wywołaniu kompilatora lub konsolidatora. Określ jego wersję, katalog roboczy lub pełny wiersz polecenia używany do wywoływania go. |
| Osie czasu             | Graph               | Zobacz wykres słupkowy, jak kompilacja była równoległa. Zidentyfikuj problemy równoległości i wąskie gardła na pierwszy rzut oka. Skonfiguruj WPA, aby przypisywać różne znaczenia do pasków zgodnie z potrzebami. Wybierz opisy wywołań jako ostatnią kolumnę zgrupowane, aby wyświetlić kolorowy wykres słupkowy wszystkich wywołań. To pomaga szybko zidentyfikować czasochłonne winowajców. Następnie powiększ i wybierz nazwę działania jako ostatnią zgrupowane kolumny, aby wyświetlić najdłuższe części. |

## <a name="files"></a>Pliki

Widok Pliki służy do:

- określić, które nagłówki są najczęściej uwzględniane, oraz
- pomóc zdecydować, co należy uwzględnić w wstępnie skompilowanym nagłówku (PCH).

### <a name="files-view-data-columns"></a>Kolumny danych widoku plików

| Nazwa kolumny              | Opis |
|--------------------------|-------------|
| Nazwa działania             | Działanie w toku podczas emisji tego zdarzenia pliku. Obecnie ta wartość jest zawsze *analizowanie*. |
| Deska opisu linii BuildTimeline | * |
| KompilacjaCzasuj.          | * |
| Składnik                | * |
| Liczba                    | * |
| Głębokość                    | Pozycja oparta na wartości zero w drzewie dołączania, w którym znajduje się ten plik. Inwentaryzacji rozpoczyna się w katalogu głównym drzewa include. Wartość 0 zazwyczaj odpowiada plikowi .c/.cpp. |
| Wyłącznośćducja        | * |
| W zestawie               | Pełna ścieżka pliku zawierającego bieżący plik. |
| Ścieżka uwzględniona             | Pełna ścieżka bieżącego pliku. |
| InclusiveDuration (InclusiveDuration)        | * |
| InvocationId (InvocationIdId)             | * |
| StartTime                | Sygnatura czasowa reprezentująca czas, w którym zostało wyemitowane bieżące zdarzenie pliku. |
| Narzędzie                     | * |

\*Wartość tej kolumny jest taka sama jak w widoku [Eksploratora kompilacji.](#build-explorer-view-data-columns)

### <a name="files-view-presets"></a>Ustawienia predefiniowane widoku plików

| Nazwa predefiniowane | Preferowany tryb widoku | Jak używać |
|-------------|---------------------|------------|
| Statystyki  | Tabela               | Zobacz, które pliki miały najwyższy czas analizowania zagregowanych, patrząc na listę w porządku malejącym. Te informacje ułatwiają restrukturyzację nagłówków lub podjęcie decyzji o tym, co należy uwzględnić w pch. |

## <a name="functions"></a>Funkcje

Widok Funkcje służy do identyfikowania funkcji o zbyt długim czasie generowania kodu.

### <a name="functions-view-data-columns"></a>Funkcje wyświetlą kolumny danych

| Nazwa kolumny              | Opis |
|--------------------------|-------------|
| Nazwa działania             | Działanie w toku po emisji tego zdarzenia funkcji. Obecnie ta wartość jest zawsze *CodeGeneration*. |
| Deska opisu linii BuildTimeline | * |
| KompilacjaCzasuj.          | * |
| Składnik                | * |
| Liczba                    | * |
| Czas trwania                 | Czas trwania działania generowania kodu dla tej funkcji. |
| FunctionName             | Nazwa funkcji poddawanych generowaniu kodu. |
| InvocationId (InvocationIdId)             | * |
| StartTime                | Sygnatura czasowa reprezentująca po emisji bieżącego zdarzenia funkcji. |
| Narzędzie                     | * |

\*Wartość tej kolumny jest taka sama jak w widoku [Eksploratora kompilacji.](#build-explorer-view-data-columns)

### <a name="functions-view-presets"></a>Ustawienia predefiniowane widoku funkcji

| Nazwa predefiniowane | Preferowany tryb widoku | Jak używać |
|-------------|---------------------|------------|
| Statystyki  | Tabela               | Zobacz, które funkcje miały najwyższy czas generowania zagregowanego kodu, patrząc na listę w porządku malejącym. Mogą one wskazywać, gdzie kod overuses **__forceinline** słowa kluczowego lub że niektóre funkcje mogą być zbyt duże. |
| Osie czasu   | Graph               | Spójrz na ten wykres słupkowy, aby dowiedzieć się, lokalizacja i czas trwania funkcji, które zajmują najwięcej czasu, aby wygenerować. Sprawdź, czy są one zgodne z wąskimi gardłami w widoku Eksploratora kompilacji. Jeśli tak, podjąć odpowiednie działania, aby zmniejszyć ich czas generowania kodu i korzyści czas kompilacji. |

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do usługi C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Referencje: polecenia vcperf](vcperf-commands.md)\
[Samouczek: Podstawy analizatora wydajności systemu Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
