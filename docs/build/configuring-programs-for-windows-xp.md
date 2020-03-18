---
title: Konfigurowanie programów dla systemu Windows XP
description: Jak zainstalować zestawy narzędzi C++ systemu Windows XP i korzystać z nich w programie Visual Studio.
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440481"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurowanie programów dla systemu Windows XP

Program Visual Studio obsługuje wiele zestawów narzędzi platformy. Oznacza to, że istnieje możliwość docelowości systemów operacyjnych i bibliotek środowiska uruchomieniowego, które nie są obsługiwane przez domyślny zestaw narzędzi. Na przykład przez przełączenie zestawu narzędzi platformy można użyć kompilatora programu Visual Studio 2017 C++ do tworzenia aplikacji przeznaczonych dla systemów Windows XP i windows Server 2003. Możesz również użyć starszych zestawów narzędzi platformy, aby zachować starszy kod zgodny ze standardem Binary i nadal korzystać z najnowszych funkcji środowiska IDE programu Visual Studio.

::: moniker range="vs-2019"

Zestaw narzędzi v142 dostarczony w programie Visual Studio 2019 nie obejmuje obsługi tworzenia kodu dla systemu Windows XP. Obsługa programowania systemu Windows XP przy użyciu zestawu narzędzi programu Visual Studio 2017 v141_xp jest dostępna jako opcja poszczególnych składników w Instalator programu Visual Studio.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Zainstaluj zestaw narzędzi platformy dla systemu Windows XP

::: moniker range="<=vs-2017"

Aby uzyskać zestaw narzędzi i składników platformy Visual Studio 2017 dla systemu Windows XP i Windows Server 2003, uruchom Instalator programu Visual Studio. Podczas pierwszej instalacji programu Visual Studio lub podczas modyfikowania istniejącej instalacji upewnij się, że wybrano opcję **Programowanie na C++ pulpicie z** obciążeniem. Na liście składników opcjonalnych dla tego obciążenia wybierz opcję **Obsługa systemu Windows XP dla C++** programu, a następnie wybierz opcję **Zainstaluj** lub **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

Aby uzyskać zestaw narzędzi platformy v141_xp i składników przeznaczonych dla systemów Windows XP i Windows Server 2003, uruchom Instalator programu Visual Studio. Podczas pierwszej instalacji programu Visual Studio lub podczas modyfikowania istniejącej instalacji upewnij się, że wybrano opcję **Programowanie na pulpicie C++ z** obciążeniem. Na karcie **poszczególne składniki** w obszarze **kompilatory, narzędzia kompilacji i środowiska uruchomieniowe**wybierz  **C++ pozycję Windows XP Support Tools for vs 2017 (najnowsze 141), \[przestarzałe]** , a następnie wybierz **Zainstaluj** lub **zmodyfikuj**.

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Środowisko docelowe systemu Windows XP

Zestaw narzędzi platformy systemu Windows XP, który jest dołączony do programu Visual Studio, jest wersją zestawu Windows 7 SDK, ale używa kompilatora programu Visual C++ Studio 2017. Konfiguruje także właściwości projektu do odpowiednich wartości domyślnych, na przykład specyfikacji zgodnego konsolidatora dla określania wartości docelowej niskiego poziomu. Tylko aplikacje klasyczne systemu Windows utworzone przy użyciu zestawu narzędzi platformy systemu Windows XP można uruchamiać w systemach Windows XP i Windows Server 2003. Te aplikacje mogą również działać w nowszych systemach operacyjnych Windows.

### <a name="to-target-windows-xp"></a>Aby docelowa była wersja systemu Windows XP

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** dla projektu wybierz pozycję **Właściwości konfiguracji** > **Ogólne**. Ustaw właściwość zestawu **narzędzi platformy** na preferowany zestaw narzędzi systemu Windows XP. Na przykład wybierz **program Visual studio 2017 — Windows XP (v141_xp)** , aby utworzyć kod dla systemów Windows XP i windows Server 2003 przy użyciu C++ kompilatora firmy Microsoft w programie Visual Studio 2017.

### <a name="c-runtime-support"></a>C++Obsługa środowiska uruchomieniowego

Wraz z zestawem narzędzi platformy systemu Windows XP kilka bibliotek obejmuje obsługę środowiska uruchomieniowego dla systemów Windows XP i Windows Server 2003. Te biblioteki: Biblioteka środowiska uruchomieniowego języka C (CRT) C++ , biblioteka standardowa, Active Template Library (ATL), biblioteka środowisko uruchomieniowe współbieżności Library (ConcRT), Biblioteka równoległych wzorców (PPL), biblioteka MFC (MFC C++ ) iC++ amp (przyspieszone środowisko programistyczne). W tych systemach operacyjnych Minimalna obsługiwana wersja to: Windows XP z dodatkiem Service Pack 3 (SP3) dla procesorów x86, Windows XP z dodatkiem Service Pack 2 (SP2) dla procesorów x64 i Windows Server 2003 z dodatkiem Service Pack 2 (SP2) dla procesorów x86 i x64.

Te biblioteki są obsługiwane przez zestawy narzędzi platformy zainstalowane przez program Visual Studio, w zależności od lokalizacji docelowej:

|Biblioteka|Domyślny zestaw narzędzi platformy przeznaczony dla aplikacji klasycznych systemu Windows|Domyślne zestawy narzędzi platformy ukierunkowane na aplikacje ze sklepu|Zestaw narzędzi platformy systemu Windows XP przeznaczony dla systemu Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Standardowa biblioteka C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Aplikacje, które są zapisywane C++w/CLI i przeznaczone dla .NET Framework 4 działają w systemach Windows XP i windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Różnice między zestawami narzędzi

Ze względu na różnice w zakresie obsługi platformy i biblioteki środowisko programistyczne dla aplikacji korzystających z zestawu narzędzi platformy systemu Windows XP nie jest tak kompletne jak w przypadku aplikacji korzystających z domyślnego zestawu narzędzi platformy programu Visual Studio.

- **C++funkcje języka**

   Tylko C++ funkcje języka zaimplementowane w programie Visual Studio 2012 są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy v110\_XP. Tylko C++ funkcje języka zaimplementowane w Visual Studio 2013 są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy v120\_XP. Tylko C++ funkcje języka zaimplementowane w programie Visual Studio 2015 są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy wersji 140\_XP. Tylko C++ funkcje języka zaimplementowane w programie Visual Studio 2017 są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy najnowsze 141\_XP. Program Visual Studio używa odpowiedniego kompilatora podczas kompilacji przy użyciu starszych zestawów narzędzi platformy. Użyj najnowszego zestawu narzędzi platformy systemu Windows XP, aby skorzystać z C++ dodatkowych funkcji języka wdrożonych w tej wersji kompilatora.

- **Debugowanie zdalne**

   Remote Tools for Visual Studio nie obsługuje zdalnego debugowania w systemie Windows XP lub Windows Server 2003. Aby debugować aplikację lokalnie lub zdalnie w systemie Windows XP lub Windows Server 2003, użyj debugera ze starszej wersji programu Visual Studio. Jest to podobne do debugowania aplikacji w systemie Windows Vista, która jest miejscem docelowym środowiska uruchomieniowego zestawu narzędzi platformy, ale nie z docelowym debugowaniem zdalnym.

- **Analiza statyczna**

   Zestawy narzędzi platformy systemu Windows XP nie obsługują analizy statycznej, ponieważ adnotacje SAL dla zestawu SDK systemu Windows 7 i bibliotek środowiska uruchomieniowego są niezgodne. Nadal można przeprowadzić analizę statyczną aplikacji, która obsługuje system Windows XP lub Windows Server 2003. Tymczasowo Przełącz rozwiązanie pod kątem domyślnego zestawu narzędzi platformy do analizy, a następnie przełącz się z powrotem do zestawu narzędzi platformy systemu Windows XP, aby skompilować aplikację.

- **Debugowanie grafiki DirectX**

   Ponieważ debuger grafiki nie obsługuje interfejsu API programu Direct3D 9, nie można go używać do debugowania aplikacji korzystających z programu Direct3D w systemie Windows XP lub Windows Server 2003. Jeśli jednak aplikacja implementuje alternatywny moduł renderowania oparty na interfejsie API Direct3D 10 lub Direct3D 11, można użyć debugera grafiki do diagnozowania problemów.

- **Kompilowanie HLSL**

   Zestaw narzędzi systemu Windows XP nie kompiluje domyślnie plików kodu źródłowego HLSL. Aby skompilować pliki HLSL, Pobierz i Zainstaluj zestaw SDK programu DirectX 2010 z czerwca, a następnie ustaw Katalogi VC projektu, aby uwzględnić je. Aby uzyskać więcej informacji, zobacz sekcję "zestaw SDK programu DirectX nie rejestruje ścieżek dołączania/biblioteki z programem Visual Studio 2010" na [stronie pobierania zestawu SDK programu directx 2010](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
