---
title: "Optymalizacja sterowana profilem w Centrum diagnostyki i wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a51cab03c1361c178846e8b7f00ba7111dc8d731
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimization-in-the-performance-and-diagnostics-hub"></a>Optymalizacja sterowana profilem w Centrum Wydajności i Diagnostyki
Optymalizacja sterowana profilem w języku Visual C++ wtyczki w Centrum diagnostyki i wydajności usprawnia proces optymalizacji oparte na profilach dla deweloperów. Możesz [pobrać](http://go.microsoft.com/fwlink/p/?LinkId=327915) z witryny sieci Web programu Visual Studio.  
  
 Oparte na profilach optymalizacji (PGO) ułatwia tworzenie kompilacji x86 i x64 natywnych aplikacji, które są zoptymalizowane pod kątem użytkowników sposób interakcji z użytkownikiem. PGO jest procesem wieloetapowych: tworzenie kompilowania aplikacji, który został zinstrumentowany na potrzeby profilowania, a następnie wykonać "szkolenia" — to znaczy Uruchom instrumentowanej aplikacji za pośrednictwem typowych scenariuszy interakcji użytkownika. Zapisz przechwycone dane profilowania, a następnie ponownie aplikację przy użyciu wyniki prowadzące optymalizacji całego programu. Chociaż te kroki można wykonać oddzielnie w programie Visual Studio lub w wierszu polecenia, wtyczka PGO centralizuje i upraszcza proces. Wtyczka PGO Ustawia wszystkie wymagane opcje, przeprowadzi Cię przez każdy krok, pokazuje analizy, a następnie używa wyniki do skonfigurowania kompilacji w celu zoptymalizowania każdej funkcji dla rozmiaru i szybkości. Wtyczka PGO również ułatwia ponownie do szkolenia aplikacji i aktualizacji danych optymalizacji kompilacji, jak zmienić swój kod.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy [Pobieranie wtyczki PGO](http://go.microsoft.com/fwlink/p/?LinkId=327915) i zainstaluj go w programie Visual Studio przed użyciem w Centrum diagnostyki i wydajności.  
  
## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Wskazówki: Używanie PGO wtyczki do optymalizowania aplikacji  
 Najpierw utworzysz podstawowe aplikacji klasycznej Win32 w programie Visual Studio. Jeśli masz już natywnych aplikacji, który chcesz zoptymalizować, można go używać i pominąć ten krok.  
  
#### <a name="to-create-an-app"></a>Aby utworzyć aplikację  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowana**, **szablony**, **Visual C++**, a następnie wybierz  **MFC**.  
  
3.  W środkowym okienku wybierz **aplikacji MFC**.  
  
4.  Określ nazwę dla projektu — na przykład **SamplePGOProject**— w **nazwa** pole. Wybierz **OK** przycisku.  
  
5.  Na **omówienie** strony **Kreator aplikacji MFC** oknie dialogowym wybierz **Zakończ** przycisku.  
  
 Następnie ustaw dla konfiguracji kompilacji aplikacji, do wersji, aby przygotować go PGO kompilacji i kroki szkolenia.  
  
#### <a name="to-set-the-build-configuration"></a>Aby ustawić konfigurację kompilacji  
  
1.  Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.  
  
2.  W **programu Configuration Manager** oknie dialogowym wybierz **aktywną konfigurację rozwiązania** przycisku rozwijanego i wybierz **wersji**. Wybierz **Zamknij** przycisku.  
  
 Otwórz Centrum diagnostyki i wydajności — na pasku menu wybierz **Analizuj**, **wydajności i diagnostyki**. Spowoduje to otwarcie strony sesji diagnostyki zawierającej narzędzi analizy, które są dostępne dla danego typu projektu.  
  
 ![PGO w Centrum diagnostyki i wydajności](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")  
  
 W **dostępne narzędzia**, wybierz pozycję **profilowana Optymalizacja** pole wyboru. Wybierz **Start** przycisk, aby uruchomić PGO wtyczki.  
  
 ![Strona wprowadzenia PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")  
  
 **Profilowana Optymalizacja** stronie opisano kroki używa wtyczki, aby poprawić wydajność aplikacji. Wybierz **Start** przycisku.  
  
 ![Strona Instrumentacji PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")  
  
 W **Instrumentacji** sekcji, użyj **początkowo włączono szkolenia** opcję, aby wybrać, czy dołączać jako część szkolenia na etapie uruchamiania aplikacji. Jeśli ta opcja nie jest zaznaczona, dane szkoleniowe nie została zarejestrowana w uruchomionej aplikacji instrumentowanych, dopóki nie zostanie jawnie włączona szkolenia.  
  
 Wybierz **dokumentu** przycisku do tworzenia aplikacji za pomocą specjalnego zestawu opcji kompilatora. Instrukcje sondowania zostanie wstawiona w wygenerowanym kodzie. Te instrukcje rejestrowania danych profilowania w fazie szkolenia.  
  
 ![Strona kompilacji instrumentowanej PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")  
  
 Aplikacja jest uruchamiana automatycznie po ukończeniu kompilacji instrumentowanej aplikacji.  
  
 Jeśli występują błędy lub ostrzeżenia wystąpi podczas kompilacji, popraw je, a następnie wybierz pozycję **ponowne uruchomienie kompilacji** ponowne uruchomienie kompilacji instrumentowanej.  
  
 Po uruchomieniu aplikacji, można użyć **rozpocząć szkolenie** i **szkolenia Wstrzymaj** łączy w **szkolenia** sekcji, aby kontrolować, gdy informacje dotyczące profilowania jest rejestrowany. Można użyć **Zatrzymaj aplikację** i **Uruchom aplikację** łącza, aby zatrzymać i ponownie uruchom aplikację.  
  
 ![Strony szkolenia PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")  
  
 Podczas uczenia, przejdź do scenariuszy użytkownika do przechwycenia profilowania informacje wymagające PGO wtyczka do optymalizacji kodu. Po ukończeniu szkolenia, zamknij aplikację, lub wybierz **Zatrzymaj aplikację** łącza. Wybierz **Analizuj** przycisk, aby uruchomić krok analizy.  
  
 Po zakończeniu analizy **analizy** sekcja zawiera raport z informacjami profilowania, przechwyconych podczas fazy szkolenia scenariusza użytkownika. Ten raport służy do sprawdzenia, które funkcji o nazwie większość i zużyte najwięcej czasu w aplikacji. Wtyczka PGO informacje są używane do określenia aplikacji funkcje, które mają Optymalizuj pod kątem szybkości, a które Optymalizuj dla rozmiaru. Wtyczka PGO konfiguruje optymalizacje kompilacji do utworzenia aplikacji najmniejszą, fastest dla scenariuszy użytkownika, zapisanych podczas uczenia.  
  
 ![Strona analizy PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")  
  
 Jeśli szkolenia przechwycone oczekiwane informacje profilowania, można wybrać **Zapisz zmiany** można zapisać danych profilu przeanalizowane w projekcie w celu zoptymalizowania kompilacji w przyszłości. Aby odrzucić dane profilu i Rozpoczęcie szkolenia od początku, wybierz **wykonaj ponownie szkolenia**.  
  
 Plik danych profilu jest zapisywany w projekcie **dane szkoleniowe PGO** folderu. Te dane są używane do kontrolowania ustawień optymalizacji kompilatora kompilacji w aplikacji.  
  
 ![Plik danych PGO w Eksploratorze rozwiązań](../../build/reference/media/pgofig6data.png "PGOFig6Data")  
  
 Po analizie wtyczki PGO Ustawia opcje kompilacji w swoim projekcie selektywnie Optymalizowanie aplikacji podczas kompilowania przy użyciu danych profilu. Możesz zmodyfikować i kompilowania aplikacji za pomocą tych samych danych profilu. Podczas tworzenia aplikacji, danych wyjściowych kompilacji raporty, jak wiele funkcji oraz instrukcje, które zostały zoptymalizowane przy użyciu danych profilu.  
  
 ![PGO dane wyjściowe diagnostyki](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")  
  
 Jeśli podczas tworzenia istotne zmiany kodu, może być konieczne ponownie ucz aplikację, aby uzyskać najlepsze optymalizacji. Firma Microsoft zaleca retrain aplikacji, gdy dane wyjściowe kompilacji zgłasza, że mniej niż 80 procent funkcji lub instrukcji zostały zoptymalizowane przy użyciu danych profilu.