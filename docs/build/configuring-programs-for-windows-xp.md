---
title: Konfigurowanie programów pod kątem Windows XP
ms.date: 02/02/2018
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 73fc66c358f2bfa390177557da2f114f225cec1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582745"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurowanie programów pod kątem Windows XP

Ponieważ program Visual Studio obsługuje wiele zestawów narzędzi platformy, mogą kierować systemów operacyjnych i bibliotek środowiska uruchomieniowego, które nie są obsługiwane przez domyślny zestaw narzędzi. Na przykład, przełączając zestawu narzędzi platformy, służy C ++ 11, C ++ 14 i C ++ 17 języka ulepszenia obsługiwane przez kompilator języka Visual C++ w programie Visual Studio do tworzenia aplikacji przeznaczonych dla Windows XP i Windows Server 2003. Można również używać starszych zestawów narzędzi platformy do obsługi starszego kodu zgodne dane binarne i nadal korzystaj z najnowszych funkcji środowiska IDE programu Visual Studio.

## <a name="install-the-windows-xp-platform-toolset"></a>Zainstaluj zestaw narzędzi platformy Windows XP

Aby uzyskać zestaw narzędzi platformy i składników do obiektu docelowego Windows XP i Windows Server 2003 w programie Visual Studio 2017, uruchom Instalatora programu Visual Studio. Podczas pierwszej instalacji programu Visual Studio lub w przypadku wybrania **Modyfikuj** modyfikowania istniejącej instalacji, upewnij się, że **programowanie aplikacji klasycznych w języku C++** obciążenie jest zaznaczone. Na liście opcjonalnych składników dla tego obciążenia, wybierz opcję **podporu Windows XP Pro C++**, a następnie wybierz **zainstalować** lub **Modyfikuj**.

## <a name="windows-xp-targeting-experience"></a>Windows XP kierowania

Zestaw narzędzi platformy Windows XP, który znajduje się w programie Visual Studio jest wersją Windows 7 SDK, ale używa bieżącej kompilator języka C++. Konfiguruje również właściwości projektu, aby odpowiednich wartości domyślnych, na przykład Specyfikacja zgodne konsolidatora języka niskiego poziomu. Tylko Windows aplikacji klasycznych, które są tworzone za pomocą narzędzi platformy Windows XP, systemem Windows XP i Windows Server 2003, ale te aplikacje można również uruchomić na nowsze systemy operacyjne Windows.

#### <a name="to-target-windows-xp"></a>Pod kątem Windows XP

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W **stron właściwości** okno dialogowe dla projektu, w obszarze **właściwości konfiguracji** > **ogólne**ustaw **zestawnarzędziplatformy** właściwość żądany zestaw narzędzi Windows XP. Na przykład wybrać **Visual Studio 2017 — Windows XP (v141_xp)** do pisania kodu dla Windows XP i Windows Server 2003 za pomocą kompilatora Microsoft Visual C++ 2017.

### <a name="c-runtime-support"></a>Obsługa środowiska uruchomieniowego języka C++

Wraz z zestawu narzędzi platformy Windows XP, biblioteka środowiska uruchomieniowego C (CRT), standardowej biblioteki języka C++, Active Template Library (ATL), biblioteka środowiska uruchomieniowego współbieżności (ConCRT), biblioteki wzorców równoległych (PPL), Microsoft Foundation Class Library (MFC) i C++ AMP (C++ Accelerated Massive programowania) biblioteki obsługę środowiska uruchomieniowego Windows XP i Windows Server 2003. Dla tych systemów operacyjnych minimalne obsługiwane wersje to Windows XP Service Pack 3 (SP3) dla x86, Windows XP z dodatkiem Service Pack 2 (SP2), x64 i systemu Windows Server 2003 usługi dodatkiem Service Pack 2 (SP2) dla x86 i x64.

Biblioteki te są obsługiwane przez zestawy narzędzi platformy, instalowane przez Visual Studio, w zależności od docelowej:

|Biblioteka|Domyślne platform toolset określania wartości docelowej Windows aplikacji klasycznych|Domyślne aplikacje Store docelowy zestaw narzędzi platformy|Zestaw narzędzi platformy Windows XP przeznaczonych dla Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Standardowa biblioteka C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Aplikacje napisane w języku C + +/ interfejsu wiersza polecenia i docelowych programu .NET Framework 4 systemem Windows XP i Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Różnice między procesami

Ze względu na różnice w obsłudze platformy i biblioteki środowisko programistyczne dla aplikacji korzystających z zestawu narzędzi platformy Windows XP nie jest tak kompletny, jak w przypadku aplikacji, które korzystają z domyślnego zestawu narzędzi platformy Visual Studio.

- **Funkcje języka C++**

   Tylko takie funkcje języka C++, zaimplementowane w Visual Studio 2012 są obsługiwane w aplikacjach, które używają v110\_xp zestaw narzędzi platformy. Tylko takie funkcje języka C++, zaimplementowane w Visual Studio 2013 są obsługiwane w aplikacjach, które używają v120\_xp zestaw narzędzi platformy. Tylko takie funkcje języka C++, zaimplementowane w Visual Studio 2015 są obsługiwane w aplikacjach korzystających z wersji 140\_xp zestaw narzędzi platformy. Visual Studio używa odpowiednich kompilatora podczas kompilacji, przy użyciu starszych zestawów narzędzi platformy. Użyj najnowszych narzędzi platformy Windows XP, aby móc korzystać z dodatkowych funkcji języka C++ zaimplementowany w tej wersji kompilatora.

- **Debugowanie zdalne**

   Remote Tools for Visual Studio nie obsługuje zdalnego debugowania na Windows XP lub Windows Server 2003. Aby debugować aplikację, gdy działa on Windows XP lub Windows Server 2003, można użyć debugera ze starszej wersji programu Visual Studio do debugowania, lokalnie lub zdalnie. Przypomina to środowisko debugowania aplikacji w systemie Windows Vista, czyli miejsca docelowego środowiska uruchomieniowego z zestawu narzędzi platformy, ale nie obiekt docelowy debugowania zdalnego.

- **Analizy statycznej**

   Zestawy narzędzi platformy Windows XP nie obsługuje analizy statycznej, ponieważ adnotacji SAL, Windows 7 SDK i bibliotek środowiska uruchomieniowego są niezgodne. Jeśli chcesz przeprowadzić analizę statyczną na aplikację, która obsługuje Windows XP lub Windows Server 2003, można tymczasowo Przełącz rozwiązania pod kątem domyślnego zestawu narzędzi platformy do przeprowadzenia analizy i przejdź z powrotem do kompilacji zestawu narzędzi platformy Windows XP aplikacja.

- **Debugowanie grafiki DirectX**

   Ponieważ debuger grafiki nie obsługuje interfejsu API programu Direct3D 9, nie można używać do debugowania aplikacji, które używają programu Direct3D na Windows XP lub Windows Server 2003. Jednakże jeśli aplikacja korzysta alternatywny moduł renderowania, korzystającą z programów Direct3D 10 lub interfejsów API programu Direct3D 11, debuger grafiki może służyć do diagnozowania problemów z użyciem tych interfejsów API.

- **Tworzenie HLSL**

   Domyślnie zestaw narzędzi Windows XP nie kompiluje pliki kodu źródłowego języka HLSL. Aby skompilować plikach HLSL, Pobierz i zainstaluj czerwca 2010 zestawu SDK programu DirectX, a następnie ustaw projekt zachowania VC katalogi w celu dołączenia go. Aby uzyskać więcej informacji, zobacz "DirectX SDK nie rejestruje ścieżki Include/biblioteki za pomocą programu Visual Studio 2010" sekcji [czerwca 2010 strona pobierania zestawu SDK programu DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
