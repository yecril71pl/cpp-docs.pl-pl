---
title: 'Samouczek: vcperf i analizator wydajności systemu Windows'
description: Samouczek na temat używania vcperf i WPA do analizowania śladów kompilacji języka C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323411"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Samouczek: vcperf i analizator wydajności systemu Windows

::: moniker range="<=vs-2017"

Narzędzia aplikacji Skompilowanie kompilacji języka C++ są dostępne w programie Visual Studio 2019. Aby zapoznać się z dokumentacją dla tej wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range="vs-2019"

W tym samouczku dowiesz się, jak używać *vcperf.exe* do zbierania śladu kompilacji języka C++. Dowiesz się również, jak wyświetlić ten ślad w analizatorze wydajności systemu Windows.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1: Instalowanie i konfigurowanie analizatora wydajności systemu Windows

WPA to przeglądarka śledzenia dostępna w zestawie oceny i wdrażania systemu Windows (ADK). Jest to oddzielne narzędzie, które nie jest częścią składników, które można zainstalować za pomocą instalatora programu Visual Studio.

Wersja usługi WPA obsługująca usługę C++ Build Insights jest obecnie dostępna tylko w wersji Preview programu Windows ADK Insider. Aby uzyskać dostęp do tej wersji zapoznawczej, należy zarejestrować się w [niejawnym programie testów systemu Windows](https://insider.windows.com). Aby uzyskać podgląd pakietu Windows ADK, nie trzeba instalować systemu operacyjnego Windows 10 Insider Preview. Wystarczy zarejestrować swoje konto Microsoft w niejawnym programie testów systemu Windows.

### <a name="to-download-and-install-wpa"></a>Aby pobrać i zainstalować WPA

UWAGA: System Windows 8 lub nowszy jest wymagany do zainstalowania analizatora wydajności systemu Windows.

1. Przejdź do [strony pobierania](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)programu Windows ADK Insider Preview .

1. Pobierz niejawny tester systemu Windows ADK Preview. Jest to obraz dysku.

1. Otwórz obraz dysku i uruchom instalator *adksetup.exe.*

1. Po wyświetleniu monitu o zainstalowanie funkcji wybierz **zestaw narzędzi wydajności systemu Windows**. Możesz wybrać inne funkcje, jeśli chcesz, ale nie są one wymagane do zainstalowania WPA.

   ![Ekran wyboru funkcji instalatora analizatora wydajności systemu Windows](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>Aby skonfigurować usługi Build Insights

1. Uruchom WPA.

1. Wybierz **tabele** > wyboru okna **(eksperymentalne)**.

1. Przewiń w dół do sekcji **Diagnostyka.**

1. Zaznacz wszystkie widoki MSVC Build Insights.

   ![Panel wyboru tabeli analizatora wydajności systemu Windows](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2: Śledzenie kompilacji za pomocą vcperf.exe

Aby wyświetlić dane usługi C++ Build Insights, najpierw zbierz je w pliku śledzenia, wykonując następujące kroki:

1. Otwórz natywne narzędzia lub wiersz poleceń dewelopera narzędzi krzyżowych dla programu Visual Studio 2019 w trybie administratora. (Kliknij prawym przyciskiem myszy element menu Start i wybierz polecenie **Więcej** > **uruchom jako administrator).**

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf.exe /start _SessionName_**

   Wybierz nazwę sesji, którą zapamiętasz dla *SessionName*.

1. Tworzenie projektu, jak zwykle. Nie trzeba używać tego samego okna wiersza polecenia do kompilacji.

1. W oknie wiersza polecenia wprowadź następujące polecenie:

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   Użyj tej samej nazwy sesji, którą wcześniej wybrano dla *SessionName.* Wybierz odpowiednią nazwę dla pliku śledzenia *traceFile.etl.*

Oto jak wygląda typowa sekwencja poleceń *vcperf.exe* w oknie wiersza polecenia dewelopera:

![Prosty scenariusz użycia vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Ważne uwagi na temat vcperf.exe

- Uprawnienia administratora są wymagane do uruchomienia lub zatrzymania śledzenia *vcperf.exe.* Użyj otwartego okna wiersza polecenia dewelopera przy użyciu **polecenia Uruchom jako administrator**.

- Tylko jedna sesja śledzenia naraz może działać na komputerze.

- Pamiętaj, aby zapamiętać nazwę sesji użytą do rozpoczęcia śledzenia. Zatrzymanie uruchomionej sesji bez znajomości jej nazwy może być kłopotliwe.

- Podobnie jak *cl.exe* i *link.exe*, narzędzie wiersza polecenia *vcperf.exe* jest zawarte w instalacji MSVC. Aby uzyskać ten składnik, nie są wymagane żadne dodatkowe kroki.

- *vcperf.exe* zbiera informacje o wszystkich narzędziach MSVC uruchomionych w systemie. W rezultacie nie trzeba uruchamiać kompilacji z tego samego wiersza polecenia, który był używany do zbierania śledzenia. Projekt można utworzyć z innego wiersza polecenia lub nawet w programie Visual Studio.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3: Wyświetlanie śladu w analizatorze wydajności systemu Windows

Uruchom WPA i otwórz zebrany właśnie ślad. WPA powinien rozpoznać go jako śledzenia usługi Buduj w języku C++, a następujące widoki powinny pojawić się w panelu Eksploratora wykresu po lewej stronie:

- Eksplorator kompilacji
- Pliki
- Funkcja

Jeśli nie widzisz tych widoków, sprawdź, czy WPA jest poprawnie skonfigurowany, zgodnie z opisem w [kroku 1](#configuration-steps). Można wyświetlić dane kompilacji, przeciągając widoki do pustego okna analizy po prawej stronie, jak pokazano poniżej:

![Wyświetlanie śledzenia aplikacji Szczegółowe informacje o kompilacji języka C++ w analizatorze wydajności systemu Windows](media/wpa-viewing-trace.gif)

Inne widoki są dostępne w panelu Eksplorator wykresów. Przeciągnij je do okna Analiza, gdy jesteś zainteresowany zawartymi w nich informacjami. Przydatny jest widok PROCESORA (Sampled), który pokazuje wykorzystanie procesora CPU w całej kompilacji.

## <a name="more-information"></a>Więcej informacji

[Samouczek: Podstawy analizatora wydajności systemu Windows](wpa-basics.md)\
Dowiedz się więcej o typowych operacjach WPA, które mogą pomóc w analizowaniu śladów kompilacji.

[Referencje: polecenia vcperf](/cpp/build-insights/reference/vcperf-commands)\
Odwołanie do polecenia *vcperf.exe* zawiera listę wszystkich dostępnych opcji polecenia.

[Odwołanie: Widoki analizatora wydajności systemu Windows](/cpp/build-insights/reference/wpa-views)\
Zapoznaj się z tym artykułem, aby uzyskać szczegółowe informacje na temat widoków usługi C++ Build Insights w WPA.

[Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficjalna strona dokumentacji WPA.

::: moniker-end
