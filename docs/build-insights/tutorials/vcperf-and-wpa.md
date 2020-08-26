---
title: 'Samouczek: vcperf i Analizator wydajności systemu Windows'
description: Samouczek dotyczący sposobu używania vcperf i WPA do analizowania śladów kompilacji w języku C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f3a0b4a9c57fd55c6788481adbf91c48e362444e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833403"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Samouczek: vcperf i Analizator wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia do tworzenia szczegółowych danych w języku C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

W tym samouczku dowiesz się, jak za pomocą *vcperf.exe* zbierać ślady kompilacji w języku C++. Dowiesz się również, jak wyświetlić ten ślad w analizatorze wydajności systemu Windows.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1. Instalowanie i Konfigurowanie analizatora wydajności systemu Windows

WPA to przeglądarka śledzenia dostępna w zestawie do oceny i wdrażania systemu Windows (ADK). Jest to osobne narzędzie, które nie jest częścią składników, które można zainstalować za pomocą Instalatora programu Visual Studio.

Wersja protokołu WPA obsługująca szczegółowe informacje o kompilacji w języku C++ jest obecnie dostępna tylko w wersji zapoznawczej zestawu Windows ADK. Aby uzyskać dostęp do tej wersji zapoznawczej, musisz utworzyć konto dla [niejawnego programu testów systemu Windows](https://insider.windows.com). Nie musisz instalować systemu operacyjnego Windows 10 w wersji zapoznawczej w celu uzyskania podglądu zestawu Windows ADK w wersji zapoznawczej. Musisz zarejestrować konto Microsoft w Niejawnym programie testów systemu Windows.

### <a name="to-download-and-install-wpa"></a>Aby pobrać i zainstalować protokół WPA

Uwaga: Aby zainstalować Analizator wydajności systemu Windows, wymagany jest system Windows 8 lub nowszy.

1. Przejdź do [strony pobierania](/windows-hardware/get-started/adk-install)zestawu Windows ADK.

1. Pobierz i zainstaluj najnowszą wersję zestawu Windows ADK.

1. Po wyświetleniu monitu o funkcje, które chcesz zainstalować, wybierz **zestaw narzędzi wydajności systemu Windows**. Jeśli chcesz, możesz wybrać inne funkcje, ale nie są one wymagane do zainstalowania protokołu WPA.

   ![Ekran wyboru funkcji Instalatora analizatora wydajności systemu Windows](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> Aby skonfigurować protokół WPA

Wyświetlanie śladów w usłudze C++ build Insights w protokole WPA wymaga specjalnego dodatku. Wykonaj następujące kroki, aby ją zainstalować:

1. Uzyskaj dodatek, pobierając jeden z poniższych składników. Nie musisz uzyskać obu tych metod. Wybierz ten, który jest najbardziej wygodny.
    1. [Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/), lub
    1. [Pakiet NuGet usługi Build Insights dla języka C++](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/).

1. Skopiuj `perf_msvcbuildinsights.dll` plik do katalogu instalacyjnego protokołu WPA.
    1. W programie Visual Studio 2019 w wersji 16,6 lub nowszej ten plik znajduje się tutaj: `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}` .
    1. W pakiecie NuGet usługi Build Insights w wersji C++ ten plik znajduje się tutaj: `wpa\{Architecture}` .
    1. W powyższych ścieżkach Zastąp zmienne ujęte w nawiasy klamrowe w następujący sposób:
        1. `{Edition}` to wersja programu Visual Studio 2019, taka jak Community, Professional lub Enterprise.
        1. `{Version}` to wersja MSVC. Wybierz najwyższą dostępną wartość.
        1. `{Architecture}`: Wybierz, `x64` czy masz 64-bitową wersję systemu Windows. W przeciwnym razie wybierz opcję `x86` .
    1. Katalog instalacji WPA zazwyczaj: `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit` .

1. W katalogu instalacyjnym WPA, Otwórz `perfcore.ini` plik i Dodaj wpis dla `perf_msvcbuildinsights.dll` .

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2. śledzenie kompilacji za pomocą vcperf.exe

Aby wyświetlić dane kompilacji w języku C++, należy najpierw zebrać je do pliku śledzenia, wykonując następujące czynności:

1. Otwórz **architekturę x64** lub **wiersz polecenia narzędzi x86 Native Tools dla programu vs 2019** w trybie administratora. (Kliknij prawym przyciskiem myszy element menu Start i wybierz polecenie **więcej**  >  **Uruchom jako administrator**.)
    1. Wybierz **x64** , jeśli masz 64-bitową wersję systemu Windows. W przeciwnym razie wybierz pozycję **x86**.

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf.exe/Start _SESSIONNAME_**

   Wybierz *nazwę sesji,* która będzie zapamiętać.

1. Kompilowanie projektu w zwykły sposób. Nie musisz używać tego samego okna wiersza polecenia do kompilowania.

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf.exe/Stop _SESSIONNAME_ _TraceFile. etl_**

   Użyj tej samej nazwy sesji, którą wybrano dla *sesji SESSIONNAME* . Wybierz odpowiednią nazwę pliku śledzenia *TraceFile. etl* .

Poniżej przedstawiono typowe sekwencje poleceń *vcperf.exe* w oknie wiersza polecenia dla deweloperów:

![Prosty scenariusz użycia vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Ważne uwagi dotyczące vcperf.exe

- Do uruchamiania lub zatrzymywania śledzenia *vcperf.exe* są wymagane uprawnienia administratora. Użyj okna wiersza polecenia dla deweloperów, które jest otwierane za pomocą **Uruchom jako administrator**.

- Na komputerze może działać tylko jedna sesja śledzenia naraz.

- Pamiętaj, aby zapamiętać nazwę sesji, która została użyta do rozpoczęcia śledzenia. Może być problematycznych, aby zatrzymać działającą sesję bez znajomości jej nazwy.

- Podobnie jak *cl.exe* i *link.exe*, *vcperf.exe* narzędzi wiersza polecenia jest zawarta w instalacji MSVC. Do uzyskania tego składnika nie są wymagane żadne dodatkowe kroki.

- *vcperf.exe* zbiera informacje o wszystkich narzędziach MSVC uruchomionych w systemie. W związku z tym nie trzeba uruchamiać kompilacji z tego samego wiersza polecenia, który został użyty do zebrania śladu. Projekt można skompilować z innego wiersza polecenia lub nawet w programie Visual Studio.

### <a name="vcperfexe-is-open-source"></a>vcperf.exe jest otwartym źródłem

Jeśli chcesz skompilować i uruchomić własną wersję *vcperf.exe*, możesz ją sklonować z [repozytorium GitHub vcperf](https://github.com/microsoft/vcperf).

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3. Wyświetlanie śladu w analizatorze wydajności systemu Windows

Uruchom Protokół WPA i Otwórz właśnie zebrane dane śledzenia. WPA powinien rozpoznać go jako śladu kompilacji w języku C++, a następujące widoki powinny być wyświetlane w panelu Eksplorator programu Graph po lewej stronie:

- Eksplorator kompilacji
- Files
- Funkcje
- Wystąpienia szablonu

Jeśli te widoki nie są widoczne, należy dokładnie sprawdzić, czy protokół WPA jest skonfigurowany prawidłowo, zgodnie z opisem w [kroku 1](#configuration-steps). Możesz wyświetlić dane kompilacji, przeciągając widoki do pustego okna analizy po prawej stronie, jak pokazano poniżej:

![Wyświetlanie śladu kompilacji usługi C++ build w analizatorze wydajności systemu Windows](media/wpa-viewing-trace.gif)

Inne widoki są dostępne w panelu Eksplorator programu Graph. Przeciągnij je do okna analizy, gdy interesujesz się informacjami, które zawierają. Przydatnym jednym z nich jest widok procesora CPU (próbkowany), który pokazuje użycie procesora przez cały czas kompilacji.

## <a name="more-information"></a>Więcej informacji

[Samouczek: podstawowe informacje dotyczące analizatora wydajności systemu Windows](wpa-basics.md)\
Zapoznaj się z typowymi operacjami WPA, które mogą ułatwić analizowanie śladów kompilacji.

[Reference: polecenia vcperf](/cpp/build-insights/reference/vcperf-commands)\
Informacje dotyczące poleceń *vcperf.exe* są wyświetlane we wszystkich dostępnych opcjach poleceń.

[Odwołanie: widoki Analizatora wydajności systemu Windows](/cpp/build-insights/reference/wpa-views)\
Zapoznaj się z tym artykułem, aby uzyskać szczegółowe informacje o widokach kompilacji w języku C++ w protokole WPA.

[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficjalna witryna dokumentacji protokołu WPA.

::: moniker-end
