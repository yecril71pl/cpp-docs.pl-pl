---
title: Wprowadzenie do C++ usługi Build Insights
description: Ogólne omówienie sposobu korzystania z narzędzi do analizy wydajności czasu kompilacji, które są częścią usługi C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c31d317cd7b9c6465362e3e532db2128303f602
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633106"
---
# <a name="get-started-with-c-build-insights"></a>Wprowadzenie do C++ usługi Build Insights

::: moniker range="<=vs-2017"

Narzędzia C++ Build Insights są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights to zbiór narzędzi, które zapewniają lepszy wgląd w łańcuch narzędzi Microsoft Visual C++ (MSVC). Narzędzia zbierają dane o C++ kompilacjach i są wyświetlane w formacie, który może pomóc odpowiedzieć na często zadawane pytania, takie jak:

- Czy moje kompilacje są wystarczająco równoległe?
- Co należy uwzględnić we wstępnie skompilowanym nagłówku (PCH)?
- Czy istnieje określone wąskie gardło, na które należy się skoncentrować, aby zwiększyć szybkość kompilacji?

Dwa główne składniki tej technologii to narzędzie wiersza polecenia *vcperf. exe* i dodatek dla przeglądarki śledzenia wydajności Windows Performance ANALYZER (WPA). Narzędzie służy do zbierania śladów kompilacji, podczas gdy dodatek umożliwia wyświetlanie ich w WPA. Wykonaj następujące kroki, aby rozpocząć korzystanie z tych dwóch narzędzi.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1. Instalowanie i Konfigurowanie analizatora wydajności systemu Windows

WPA to przeglądarka śledzenia dostępna w zestawie do oceny i wdrażania systemu Windows (ADK). Jest to osobne narzędzie, które nie jest częścią składników, które można zainstalować za pomocą Instalatora programu Visual Studio.

Wersja usługi WPA, która obsługuje C++ usługi Build Insights, jest obecnie dostępna tylko w wersji zapoznawczej programu Windows ADK. Aby uzyskać dostęp do tej wersji zapoznawczej, musisz utworzyć konto dla [niejawnego programu testów systemu Windows](https://insider.windows.com). Nie musisz instalować systemu operacyjnego Windows 10 w wersji zapoznawczej w celu uzyskania podglądu zestawu Windows ADK w wersji zapoznawczej. Musisz zarejestrować konto Microsoft w Niejawnym programie testów systemu Windows.

### <a name="to-download-and-install-wpa"></a>Aby pobrać i zainstalować protokół WPA

1. Przejdź do [strony pobierania](https://www.microsoft.com/software-download/windowsinsiderpreviewADK)wersji zapoznawczej podglądu zestawu Windows ADK.

1. Pobierz wersję zapoznawczą programu Windows ADK. Jest to obraz dysku.

1. Otwórz obraz dysku i uruchom Instalatora programu *adksetup. exe* .

1. Po wyświetleniu monitu o funkcje, które chcesz zainstalować, wybierz **zestaw narzędzi wydajności systemu Windows**. Jeśli chcesz, możesz wybrać inne funkcje, ale nie są one wymagane do zainstalowania protokołu WPA.

   ![Ekran wyboru funkcji Instalatora analizatora wydajności systemu Windows](media/wpa-installation.png)

### <a name="configuration-steps"></a>Aby skonfigurować szczegółowe informacje o kompilacji

1. Uruchom Protokół WPA.

1. Wybierz **okno** > **Wybierz tabele (eksperymentalne)** .

1. Przewiń w dół do sekcji **Diagnostyka** .

1. Zaznacz wszystkie widoki MSVC Build Insights.

   ![Panel wyboru tabeli analizatora wydajności systemu Windows](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2. śledzenie kompilacji za pomocą vcperf. exe

Aby wyświetlić C++ dane usługi Build Insights, najpierw Zbierz je do pliku śledzenia, wykonując następujące czynności:

1. Otwórz wiersz polecenia narzędzi macierzystych lub narzędzia Cross Tools dla deweloperów dla programu Visual Studio 2019 w trybie administratora. (Kliknij prawym przyciskiem myszy element menu Start i wybierz polecenie **więcej** > **Uruchom jako administrator**).

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf. exe/Start _nazwa_sesji_**

   Wybierz *nazwę sesji,* która będzie zapamiętać.

1. Kompilowanie projektu w zwykły sposób. Nie musisz używać tego samego okna wiersza polecenia do kompilowania.

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf. exe/Stop _SESSIONNAME_ _TraceFile. etl_**

   Użyj tej samej nazwy sesji, którą wybrano dla *sesji SESSIONNAME* . Wybierz odpowiednią nazwę pliku śledzenia *TraceFile. etl* .

Poniżej przedstawiono opis typowej sekwencji poleceń *vcperf. exe* w oknie wiersza polecenia dla deweloperów:

![Prosty scenariusz użycia vcperf. exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Ważne uwagi dotyczące vcperf. exe

- Do uruchamiania lub zatrzymywania śledzenia programu *vcperf. exe* wymagane są uprawnienia administratora. Użyj okna wiersza polecenia dla deweloperów, które jest otwierane za pomocą **Uruchom jako administrator**.

- Na komputerze może działać tylko jedna sesja śledzenia naraz.

- Pamiętaj, aby zapamiętać nazwę sesji, która została użyta do rozpoczęcia śledzenia. Może być problematycznych, aby zatrzymać działającą sesję bez znajomości jej nazwy.

- Podobnie jak *CL. exe* i *link. exe*, narzędzie wiersza polecenia *vcperf. exe* jest zawarta w instalacji programu MSVC. Do uzyskania tego składnika nie są wymagane żadne dodatkowe kroki.

- *vcperf. exe* zbiera informacje o wszystkich narzędziach MSVC uruchomionych w systemie. W związku z tym nie trzeba uruchamiać kompilacji z tego samego wiersza polecenia, który został użyty do zebrania śladu. Projekt można skompilować z innego wiersza polecenia lub nawet w programie Visual Studio.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3. Wyświetlanie śladu w analizatorze wydajności systemu Windows

Uruchom Protokół WPA i Otwórz właśnie zebrane dane śledzenia. WPA powinien rozpoznać go jako ślad C++ usługi Build Insights, a następujące widoki powinny być wyświetlane w panelu Eksplorator programu Graph po lewej stronie:

- Build Explorer
- Pliki
- Funkcja

Jeśli te widoki nie są widoczne, należy dokładnie sprawdzić, czy protokół WPA jest skonfigurowany prawidłowo, zgodnie z opisem w [kroku 1](#configuration-steps). Możesz wyświetlić dane kompilacji, przeciągając widoki do pustego okna analizy po prawej stronie, jak pokazano poniżej:

![Wyświetlanie śladu usługi C++ Build Insights w analizatorze wydajności systemu Windows](media/wpa-viewing-trace.gif)

Inne widoki są dostępne w panelu Eksplorator programu Graph. Przeciągnij je do okna analizy, gdy interesujesz się informacjami, które zawierają. Przydatnym jednym z nich jest widok procesora CPU (próbkowany), który pokazuje użycie procesora przez cały czas kompilacji.

## <a name="more-information"></a>Więcej informacji

[Podstawy analizatora wydajności systemu Windows](wpa-basics.md)\
Zapoznaj się z typowymi operacjami WPA, które mogą ułatwić analizowanie śladów kompilacji.

[vcperf. exe — informacje referencyjne](vcperf-reference.md)\
W dokumentacji poleceń *vcperf. exe* wymieniono wszystkie dostępne opcje poleceń.

[Informacje dotyczące widoków analizatora wydajności systemu Windows](wpa-views-reference.md)\
Zobacz ten artykuł, C++ Aby uzyskać szczegółowe informacje o widokach usługi Build Insights w protokole WPA.

\ [analizatora wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)
Oficjalna witryna dokumentacji protokołu WPA.

::: moniker-end
