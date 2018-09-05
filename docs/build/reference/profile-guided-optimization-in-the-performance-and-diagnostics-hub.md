---
title: Optymalizacja sterowana profilem w Centrum wydajności i diagnostyki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 275d65cdf4f0f5986ff80e65898732dadbd5f61f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691098"
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>Optymalizacja sterowana profilem w Visual Studio 2013 Centrum wydajności i diagnostyki

Jeśli używasz programu Visual Studio 2013, optymalizacja sterowana profilem Visual c++ dla dodatku typu plug-in w Centrum wydajności i diagnostyki usprawnia proces optymalizacji profilowe z przewodnikiem dla deweloperów. Możesz [Pobierz wtyczkę](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) z witryny sieci Web programu Visual Studio. Wtyczka nie jest obsługiwana w nowszych wersjach programu Visual Studio.

Profilowe z przewodnikiem Optymalizacja (PGO) pomaga tworzyć kompilacje x86 i x64 aplikacje natywne, które są zoptymalizowane pod kątem przez użytkowników wchodzić w interakcje z nimi. PGO to proces obejmujący wiele kroków: tworzenie kompilacji aplikacji, który został zinstrumentowany na potrzeby profilowania, a następnie wykonaj "szkoleniowe." Oznacza to, że uruchamiasz instrumentowanej aplikacji przy użyciu typowych scenariuszy interakcji użytkownika. Zapisanie przechwycone dane profilowania i ponownie skompiluj aplikację za pomocą wyników przeprowadzenie optymalizacji całego programu. Mimo że te kroki można wykonać osobno w programie Visual Studio lub w wierszu polecenia, wtyczka PGO centralizuje i upraszcza ten proces. Wtyczka PGO Ustawia wszystkie wymagane opcje, przeprowadzi Cię przez kolejne kroki, dowiesz się, analizę i następnie używa wyników do konfigurowania kompilacji, aby zoptymalizować każdej funkcji dla rozmiar lub prędkość. Wtyczka PGO również ułatwia ponowne uruchomienie aplikacji szkolenia i zaktualizować dane optymalizacji kompilacji, ponieważ zmian w kodzie.

## <a name="prerequisites"></a>Wymagania wstępne

Należy najpierw [Pobierz wtyczkę PGO](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) i zainstaluj go w programie Visual Studio, zanim użyjesz go w Centrum wydajności i diagnostyki.

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Przewodnik: Używanie PGO wtyczka do optymalizacji aplikacji

Najpierw utworzymy podstawową aplikację pulpitu Win32 w programie Visual Studio. Jeśli masz już aplikację natywną, którą chcesz zoptymalizować, możesz go użyć i pominąć ten krok.

### <a name="to-create-an-app"></a>Aby utworzyć aplikację

1. Na pasku menu wybierz **pliku**, **New**, **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane**, **szablony**, **Visual C++**, a następnie wybierz pozycję  **MFC**.

1. W środkowym okienku wybierz **aplikacji MFC**.

1. Określ nazwę dla projektu — na przykład **SamplePGOProject**— w **nazwa** pole. Wybierz **OK** przycisku.

1. Na **Przegląd** strony **Kreator aplikacji MFC** okna dialogowego wybierz **Zakończ** przycisku.

Następnie ustaw dla konfiguracji kompilacji aplikacji do wersji na "gotowy" on PGO kompilacji i kroki szkolenia.

### <a name="to-set-the-build-configuration"></a>Aby ustawić konfigurację kompilacji

1. Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.

1. W **programu Configuration Manager** okna dialogowego wybierz **aktywną konfigurację rozwiązania** przycisk listy rozwijanej i wybierz pozycję **wersji**. Wybierz **Zamknij** przycisku.

Otwórz Centrum wydajności i diagnostyki, na pasku menu wybierz **analizy**, **wydajności i diagnostyki**. Spowoduje to otwarcie strony sesji diagnostyki, która dysponuje narzędziami analizy, które są dostępne dla danego typu projektu.

![PGO w Centrum wydajności i diagnostyki](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")

W **dostępnych narzędzi**, wybierz opcję **profilowana Optymalizacja** pole wyboru. Wybierz **Start** przycisk, aby uruchomić dodatek typu plug-in PGO.

![Strona wprowadzenia PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")

**Profilowana Optymalizacja** strony opisano kroki, używa wtyczki, aby zwiększyć wydajność aplikacji. Wybierz **Start** przycisku.

![Strona Instrumentacji PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")

W **Instrumentacji** sekcji, możesz użyć **szkolenia początkowo jest włączona** opcję, aby wybrać, czy mają zostać dołączone do fazy uruchamiania aplikacji w ramach szkolenia. Jeśli ta opcja nie jest zaznaczone, dane szkoleniowe nie została zarejestrowana w uruchomionej aplikacji instrumentowanych, aż jawnie włączyć szkolenia.

Wybierz **Instrument** przycisk, aby utworzyć aplikację przy użyciu specjalnego zestawu opcji kompilatora. Kompilator wstawia sondy instrukcje w wygenerowanym kodzie. Te instrukcje rejestrowania danych profilowania w fazie szkolenia.

![Strona kompilację instrumentowaną PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")

Aplikacja jest uruchomiane automatycznie po zakończeniu kompilacji instrumentowanej aplikacji.

Jeśli występują błędy lub ostrzeżenia podczas kompilowania, popraw je, a następnie wybierz **ponowne uruchomienie kompilacji** ponownie uruchomić kompilację instrumentowaną.

Gdy aplikacja jest uruchomiona, można użyć **Rozpocznij szkolenie** i **szkolenia Wstrzymaj** linki w **szkolenia** sekcji, aby kontrolować podczas profilowania informacje są rejestrowane. Możesz użyć **Zatrzymaj aplikację** i **Uruchom aplikację** łącza, aby zatrzymać i ponownie uruchom aplikację.

![Strony szkolenia PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")

Podczas szkolenia, przechodzą przez scenariuszy użytkownika do przechwytywania informacji profilowania, wymagającym PGO wtyczka do optymalizacji kodu. Po zakończeniu szkolenia, zamknij aplikację, lub wybierz **Zatrzymaj aplikację** łącza. Wybierz **analizy** przycisk, aby rozpocząć krok analizy.

Po zakończeniu analizy **analizy** sekcji przedstawiono raport z informacjami profilowania, przechwyconą w fazie szkolenia scenariusza użytkownika. Ten raport służy do sprawdzenia, które funkcje aplikacji o nazwie większość i wydano najwięcej czasu w. Wtyczka PGO informacje są używane do określenia aplikacji, która działa pod kątem szybkości i którego ma zostać Optymalizuj pod kątem rozmiaru. Wtyczka PGO konfiguruje optymalizacje kompilacji do utworzenia aplikacji najmniejsza, fastest dla scenariuszy użytkowników, które rejestrowane podczas szkolenia.

![Strona analizy PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")

Jeśli szkolenia przechwytywane oczekiwane informacje profilowania, możesz wybrać **Zapisz zmiany** można zapisać danych profilu przeanalizowany w projekcie, aby zoptymalizować kompilacji w przyszłości. Aby odrzucić dane profilu i szkolenie za pośrednictwem są uruchamiane od początku, wybierz opcję **ponownie przeprowadzić szkolenia**.

Plik danych profilu jest zapisywany w projekcie w **dane szkoleniowe PGO** folderu. Te dane są używane do kontrolowania ustawień optymalizacji kompilatora kompilacji w swojej aplikacji.

![Plik danych PGO w Eksploratorze rozwiązań](../../build/reference/media/pgofig6data.png "PGOFig6Data")

Po analizie usługa PGO wtyczka Ustawia opcje kompilacji w projekt, aby użyć danych profilowych selektywnie zoptymalizować aplikację, podczas kompilacji. Można modyfikować i tworzenie aplikacji przy użyciu tych samych danych profilu. Podczas kompilowania aplikacji, dane wyjściowe kompilacji raporty, jak wiele funkcji i instrukcje, które zostały zoptymalizowane przy użyciu danych profilu.

![PGO dane wyjściowe diagnostyki](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")

Po wprowadzeniu zmian w kodzie istotne podczas projektowania może być konieczne ponowne szkolenie aplikację, aby uzyskać najlepszą optymalizację. Firma Microsoft zaleca ponowne szkolenie aplikację, kiedy dane wyjściowe kompilacji, mniej niż 80 procent, funkcji lub instrukcje zostały zoptymalizowane przy użyciu danych profilu.