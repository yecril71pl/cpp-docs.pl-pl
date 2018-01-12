---
title: "Konfigurowanie programów dla systemu Windows XP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff80109c1f3a5e03ecb85406cdaea24804f96783
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurowanie programów dla systemu Windows XP
Ponieważ program Visual Studio obsługuje wiele platform procesami, można kierować systemów operacyjnych i bibliotek środowiska uruchomieniowego, które nie są obsługiwane przez zestaw domyślny. Na przykład, przełączając zestaw narzędzi platformy służy C ++ 11, języka C ++ 14 i C ++ 17 języka ulepszenia obsługiwane przez kompilator języka Visual C++ w programie Visual Studio do tworzenia aplikacji przeznaczonych [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Można również obsługa zgodnych binarnie starszego kodu za pomocą starszej procesami platformy i nadal korzystać z najnowszych funkcji środowiska IDE programu Visual Studio.  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)], musisz zainstalować [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] aktualizacji 4, aby dodać zestaw narzędzi platformy obsługiwane [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Aby pobrać i zainstalować kopię [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] aktualizacji 4, zobacz [programu Microsoft Visual Studio Express 2012 for Windows Desktop](http://go.microsoft.com/fwlink/p/?linkid=265464) w programie Microsoft Download Center. Następnie zainstaluj [programu Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/p/?linkid=335900) można pobrać zestaw narzędzi platformy v110_xp. Użyj usługi Windows Update do uzyskania najnowszych aktualizacji oprogramowania po instalacji.  
  
## <a name="windows-xp-targeting-experience"></a>Windows XP przeznaczonych dla środowiska  
 Zestaw narzędzi platformy systemu Windows XP, który znajduje się w programie Visual Studio jest wersja [!INCLUDE[win7](../build/includes/win7_md.md)] zestawu SDK, który został uwzględniony w [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], ale używa bieżącej kompilatora języka C++. Konfiguruje również właściwości projektu do odpowiednich wartości domyślnych — na przykład specyfikację zgodne konsolidatora przeznaczony do niższego poziomu. Tylko Windows aplikacji klasycznych, które są tworzone za pomocą zestawu narzędzi platformy systemu Windows XP, uruchom na [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], ale tych aplikacji można również uruchomić na nowszą systemów operacyjnych Windows.  
  
#### <a name="to-target-windows-xp"></a>Pod kątem systemu Windows XP  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.  
  
2.  W **strony właściwości** okno dialogowe dla projektu, w obszarze **właściwości konfiguracji**, **ogólne**ustaw **zestaw narzędzi platformy** Właściwość żądany zestaw narzędzi systemu Windows XP. Na przykład wybrać **Visual Studio 2015 — Windows XP (wersji140_xp)** utworzyć kod [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] przy użyciu kompilatora programu Microsoft Visual C++ 2015.  
  
### <a name="c-runtime-support"></a>Obsługa środowiska uruchomieniowego języka C++  
 Wraz z zestawu narzędzi platformy systemu Windows XP, C Runtime Library (CRT), standardowa biblioteka C++, Active Template Library (ATL), biblioteka środowiska uruchomieniowego współbieżności (ConCRT), równoległe biblioteki wzorców (PLL), Microsoft Foundation Class biblioteki (MFC) i C++ AMP (C++ Przyspieszania programowania ogromną) biblioteki obejmują obsługę środowiska uruchomieniowego [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Dla tych systemów operacyjnych są minimalne obsługiwane wersje [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) dla x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) dla x64, i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) dla x x86 i x64.  
  
 Biblioteki te są obsługiwane przez procesami platformy zainstalowany przez program Visual Studio, w zależności od celu:  
  
|Biblioteka|Domyślna platforma zestawu narzędzi określania wartości docelowej aplikacji klasycznych systemu Windows|Domyślne obsługiwane zestaw narzędzi platformy [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacji|Obsługiwane zestaw narzędzi platformy systemu Windows XP [!INCLUDE[winxp](../build/includes/winxp_md.md)],[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|  
|-------------|-------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|Standardowa biblioteka C++|X|X|X|  
|ATL|X|X|X|  
|ConCRT/PPL|X|X|X|  
|MFC|X||X|  
|C++ AMP|X|X||  
  
> [!NOTE]
>  Aplikacje, które zostały napisane w języku C + +/ CLI i obiekt docelowy programu .NET Framework 4 należy uruchomić na [!INCLUDE[winxp](../build/includes/winxp_md.md)] i [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  
  
### <a name="differences-between-the-toolsets"></a>Różnice między procesami  
 Z powodu różnic w pomocy technicznej platformy i biblioteki środowisko programistyczne dotyczące aplikacji korzystających z zestawu narzędzi platformy systemu Windows XP nie jest jako ukończonych, jak w przypadku aplikacji korzystających z zestawu narzędzi platformy Visual Studio domyślne.  
  
-   **Funkcje języka C++**  
  
     Tylko funkcje języka C++ zaimplementowana w [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy v110_xp. Tylko funkcje języka C++ zaimplementowana w [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] są obsługiwane w aplikacjach korzystających z zestawu narzędzi platformy v120_xp. Visual Studio będzie korzystać odpowiedniego kompilatora podczas tworzenia przy użyciu starszej procesami platformy. Użyj najnowszych zestaw narzędzi platformy systemu Windows XP, aby korzystać z dodatkowych funkcji języka C++ zaimplementowana w tej wersji kompilator.  
  
-   **Debugowanie zdalne**  
  
     Zdalne narzędzia dla programu Visual Studio nie obsługuje zdalnego debugowania na [!INCLUDE[winxp](../build/includes/winxp_md.md)] lub [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Debugowanie aplikacji uruchomionej [!INCLUDE[winxp](../build/includes/winxp_md.md)] lub [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], debuger ze starszej wersji programu Visual Studio umożliwia debugowanie go lokalnie lub zdalnie. Przypomina to środowisko debugowania aplikacji w systemie Windows Vista, który jest elementem docelowym środowiska uruchomieniowego zestaw narzędzi platformy, ale nie zdalnego debugowania docelowej.  
  
-   **Analizy statycznej**  
  
     Procesami platformy systemu Windows XP nie obsługuje analizy statycznej, ponieważ adnotacji SAL dla [!INCLUDE[win7](../build/includes/win7_md.md)] zestawu SDK i bibliotek środowiska uruchomieniowego są niezgodne. Jeśli chcesz wykonać analizy statycznej aplikacji obsługującej [!INCLUDE[winxp](../build/includes/winxp_md.md)] lub [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], tymczasowo Przełącz rozwiązania pod kątem zestawu narzędzi platformy domyślne do przeprowadzenia analizy, a następnie przełączać się do zestawu narzędzi platformy systemu Windows XP do kompilacji aplikacja.  
  
-   **Debugowanie grafiki DirectX**  
  
     Ponieważ debugera grafiki nie obsługuje interfejsu API programu Direct3D 9, nie można użyć do debugowania aplikacji, które używają Direct3D na [!INCLUDE[winxp](../build/includes/winxp_md.md)] lub [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Jednak jeśli aplikacja korzysta alternatywnych modułu renderowania Direct3D 10 lub interfejsów API programu Direct3D 11, debugera grafiki może służyć do diagnozowania problemów podczas korzystania z tych interfejsów API.  
  
-   **Kompilowanie HLSL**  
  
     Domyślnie zestaw narzędzi systemu Windows XP nie skompilować plików kodu źródłowego HLSL. Aby skompilować HLSL pliki, Pobierz i zainstaluj 2010 czerwca zestawu SDK programu DirectX, a następnie ustaw projekt elementu VC katalogi w celu dołączenia go. Aby uzyskać więcej informacji, zobacz "DirectX SDK nie rejestruje ścieżki Include/biblioteki z programu Visual Studio 2010" sekcji [czerwca 2010 strona pobierania zestawu SDK programu DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).