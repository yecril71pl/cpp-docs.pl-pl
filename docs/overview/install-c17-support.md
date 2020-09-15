---
title: Instalowanie obsługi C11 i C17 w programie Visual Studio
description: Instalowanie Windows SDK i obsługi CRT dla C11 i C17 w programie Visual Studio
ms.date: 09/11/2020
helpviewer_keywords:
- Install preview Windows SDK
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 86de38feb66ab0a057005140d22cf0dd3b03d4cf
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079123"
---
# <a name="install-c11-and-c17-support-in-visual-studio"></a>Instalowanie obsługi C11 i C17 w programie Visual Studio

::: moniker range="<=vs-2017"

Obsługa standardów C11 i C17 wymaga programu Visual Studio 2019 w wersji 16,8 lub nowszej. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range="vs-2019"

Obsługa standardów C11 i C17 jest dostępna w programie Visual Studio 2019 w wersji 16,8. Obsługa wymaga zaktualizowanego środowiska uruchomieniowego języka uniwersalnego C (UCRT) i najnowszych aktualizacji Windows SDK, aby działała prawidłowo z preprocesorem preprocesora ( [`/Zc:preprocessor`](../build/reference/zc-preprocessor.md) ).

Wersje Windows SDK są zgodne z wersjami systemu operacyjnego Windows. Ponieważ nie była dostępna wersja systemu Windows z tymi zmianami, musisz mieć *Windows SDK w wersji zapoznawczej*. Jest to wersja zapoznawcza Windows SDK, która jest zgodna z kompilacjami systemu Windows, *które są obecnie*przetwarzane lub testowane przez niejawnych testerów systemu Windows. Po zainstalowaniu zestawu SDK systemu Windows 10 w wersji zapoznawczej projekty programu Visual Studio skonfigurowane do korzystania z najnowszych Windows SDK będą korzystać z wersji zapoznawczej programu testów.

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio 2019 w wersji 16,8 Preview 3 lub nowszej zainstalowany na komputerze. W instalacji Uwzględnij Programowanie aplikacji klasycznych w języku C++. Najnowszą wersję zapoznawczą możesz pobrać ze strony [wersji zapoznawczej programu Visual Studio](https://visualstudio.microsoft.com/vs/preview/) . Jeśli nie zainstalowano jeszcze programu Visual Studio, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md) , aby uzyskać instrukcje dotyczące instalacji.

## <a name="step-1-sign-in-by-using-an-insider-microsoft-account"></a>Krok 1. Logowanie przy użyciu konta Microsoft

Każdy może utworzyć bezpłatny [konto Microsoft](https://signup.live.com/) a następnie zadecydować o programie testów. Przejdź do strony [niejawnego programu testów systemu Windows dla deweloperów](https://insider.windows.com/for-developers) , wybierz pozycję **zarejestruj**i zaloguj się.

Po zarejestrowaniu można rozpocząć pracę z wersjami programu testów systemu Windows. Ten krok nie jest konieczny do pobierania i używania zestawu SDK systemu Windows 10 dla programu testów. Po zarejestrowaniu się w usłudze niejawny program testów systemu Windows nie wybiera automatycznie nowych lotów systemu Windows.

Po wyświetleniu strony **Witamy w programie niejawnego programu testów systemu Windows** nie musisz teraz wybierać opcji **locie**. Przejdź do następnego kroku, aby pobrać zestaw SDK systemu Windows 10 w wersji zapoznawczej.

## <a name="step-2-download-the-insider-preview-windows-10-sdk"></a>Krok 2. Pobieranie zestawu SDK systemu Windows 10 w wersji zapoznawczej

Możesz zainstalować niejawną wersję zapoznawczą Windows SDK na stronie [pobierania podglądu niejawnego programu testów systemu Windows](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) . Jeśli zobaczysz komunikat "musisz być członkiem niejawnego programu testów systemu Windows", upewnij się, że użytkownik jest zalogowany. Użyj tego samego konto Microsoft użytego w programie testów niejawnych. Jeśli zobaczysz komunikat informujący o tym, że nie można znaleźć żądanej strony, spróbuj zmienić ustawienia regionalne w adresie URL na *en-us*.

Na stronie programu testów jest wymagane użycie systemu operacyjnego Windows 10 w wersji zapoznawczej. Jest to tylko prawdziwe w przypadku niektórych zawartości zawartych w Windows SDK. Ta zawartość może zależeć od nowych interfejsów API nieobecnych we wcześniejszych wersjach systemu Windows. Jednak nagłówki systemu Windows i uniwersalnego środowiska uruchomieniowego języka C można instalować i korzystać z nich bez systemu operacyjnego.

Wybierz pozycję **Pobierz wersję zapoznawczą niejawnego testera zestawu SDK — kompilacja 20211** (lub nowsza), aby rozpocząć pobieranie. Nowsze wersje Windows SDK również będą działały.

## <a name="step-3-install-the-insider-preview-windows-10-sdk"></a>Krok 3. Instalowanie zestawu SDK systemu Windows 10 w wersji zapoznawczej

Wersja zapoznawcza programu testowego Windows SDK pobierana jako *`.iso`* plik. Otwórz folder zawierający pobrany plik w Eksploratorze plików. Zainstaluj *`.iso`* plik, a następnie uruchom polecenie, *`WinSDKSetup.exe`* Aby rozpocząć instalację.

Na stronie **Określanie lokalizacji** wybierz pozycję **Zainstaluj zestaw Windows Software Development Kit — \<version> na tym komputerze**, a następnie wybierz przycisk **dalej**. Na stronie **prywatność zestawów Windows Kit** wybierz, czy zezwolić firmie Microsoft na zbieranie szczegółowych informacji dotyczących zestawów Windows 10, a następnie wybierz przycisk **dalej**. Wybierz pozycję **Akceptuj** , aby zaakceptować umowę licencyjną. Na stronie **Wybierz funkcje, które chcesz zainstalować** wybierz tylko te funkcje:  

- Narzędzia do podpisywania Windows SDK dla aplikacji klasycznych

- Windows SDK aplikacji zarządzanych przez platformy UWP

- Windows SDK dla aplikacji platformy UWP C++

- Windows SDK dla aplikacji klasycznych C++ x86 (Jeśli planujesz kompilację dla procesorów x86)

- Windows SDK dla aplikacji klasycznych w języku C++ (Jeśli planujesz kompilację dla amd64)

- Windows SDK aplikacji platformy C++ dla komputerów stacjonarnych (Jeśli planujesz kompilację w usłudze ARM)

- Windows SDK dla aplikacji programu Desktop C++ arm64 (Jeśli planujesz kompilację dla arm64)

![Zrzut ekranu przedstawiający Instalatora Windows SDK, pokazujący składniki wybrane do zainstalowania](media/c11-7-windows-sdk-installer-select-features.png)

Wybierz pozycję **Zainstaluj** , aby zainstalować wybrane składniki zestawu SDK. Ukończenie instalacji zestawu SDK trwa kilka minut. Po zakończeniu Otwórz program Visual Studio.

## <a name="step-4-configuring-c11-or-c17-mode-in-visual-studio"></a>Krok 4. Konfigurowanie trybu C11 lub C17 w programie Visual Studio

W programie Visual Studio Otwórz nowy lub istniejący projekt C, a następnie otwórz okno dialogowe **strony właściwości** projektu.

Ustaw projekt, aby korzystał z wersji zapoznawczej zestawu SDK systemu Windows 10 dla niejawnych testerów. Na stronie **Ogólne właściwości konfiguracji**  >  **General** ustaw właściwość **wersja Windows SDK** na **10,0 (Najnowsza zainstalowana wersja)** lub na zainstalowaną wersję zapoznawczą.

Zobaczysz również nową opcję: **Standard języka C**. Ustaw tę właściwość na **ISO C11 Standard ( `/std:c11` )** lub **ISO C17 (2018) Standard ( `/std:c17` )**.  

![Zrzut ekranu przedstawiający okno dialogowe strony właściwości na stronie Ogólne właściwości konfiguracji, w którym zostanie wyświetlona lista rozwijana standardowa języka C wybrana jako ISO C 17](media/c11-9-project-property-page-c-language-standard.png)

Standard języka C++ jest używany, gdy język jest w języku C++. Jest to wartość domyślna, gdy rozszerzenie pliku to *`.cpp`* . Wersja Standard języka C jest używana, gdy język to C. Jest to wartość domyślna, gdy rozszerzenie pliku to *`.c`* . Aby skompilować przy użyciu C11 lub C17, umieść kod źródłowy w *`.c`* pliku lub ustaw kod do skompilowania jako C. Właściwość dla projektu można ustawić na stronie Zaawansowane **Właściwości konfiguracji**  >  **C/C++**  >  **Advanced** . Ustaw właściwość **Kompiluj jako** na **Kompiluj jako kod C (/TC)**.

Gratulacje, masz już wszystko, czego potrzebujesz do kompilowania kodu C11 i C17 w programie Visual Studio 2019 w wersji 16,8 Preview 3!

## <a name="see-also"></a>Zobacz także

[`/std` (Określ wersję standardową języka)](../build/reference/std-specify-language-standard-version.md)

::: moniker-end
