---
title: 'Przewodnik: Wdrażanie Twojego programu (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 4232edd10b71c70097002511ef4ee663e67d6598
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708133"
---
# <a name="walkthrough-deploying-your-program-c"></a>Przewodnik: Wdrażanie Twojego programu (C++)

Teraz, gdy utworzono aplikację wykonując wcześniej pokrewne instruktaże, ostatnim krokiem jest utworzenie Instalatora, tak aby inni użytkownicy mogli zainstalować program na swoich komputerach. Dla Instalatora dodasz nowy projekt do istniejącego rozwiązania. Dane wyjściowe tego nowego projektu to plik setup.exe, który zainstaluje twoją aplikację na innym komputerze.

Przewodnik pokazuje, jak wdrożyć aplikację przy użyciu Instalatora Windows. Można również użyć ClickOnce do wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../windows/clickonce-deployment-for-visual-cpp-applications.md). Aby uzyskać więcej informacji o wdrażaniu ogólnie rzecz biorąc, zobacz [wdrażania aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Wymagania wstępne

- Przewodnik zakłada, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Nie można ukończyć instruktażu w wersjach Express programu Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Instalowanie programu Visual Studio szablonu projektu instalacji i wdrożenia

Kroki opisane w tej sekcji różnią się w zależności od zainstalowanej wersji programu Visual Studio. Upewnij się, że selektor wersji, w lewym górnym rogu tej strony została prawidłowo ustawiona.

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Aby zainstalować instalacja i wdrożenie szablonu projektu dla Visual Studio 2019 r.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie programu Microsoft projektów Instalatora programu Visual Studio. Rozszerzenie jest bezpłatna dla deweloperów programu Visual Studio i dodaje funkcje instalacji i wdrażania szablonów projektu do programu Visual Studio. Po połączeniu się z Internetem, w programie Visual Studio, wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**. W obszarze **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **Online** kartę i typ *projektów Instalatora programu Visual Studio Microsoft* w polu wyszukiwania. Trafienia **Enter**, wybierz opcję **programu Microsoft Visual Studio \<wersji > Projekty Instalatora**i kliknij przycisk **Pobierz**. Możliwość uruchamiania i zainstaluj rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu programu Visual Studio, wybierz **pliku** > **niedawne projekty i rozwiązania**, a następnie wybierz polecenie ponownie otworzyć projekt.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe. W polu wyszukiwania wpisz "Setup", a z listy wyników wybierz **projektu Instalatora**.

1. Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. W **rozwiązania** listy rozwijanej wybierz **Dodaj do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystenta pliku (nazwa_projektu)** zostanie otwarta karta w oknie edytora.

1. Kliknij prawym przyciskiem myszy **folderu aplikacji** a następnie wybierz węzeł **Dodaj** > **dane wyjściowe projektu** otworzyć **Dodaj grupę wyjściową projektu**okno dialogowe.

1. W oknie dialogowym wybierz **podstawowe wyjście** i kliknij przycisk **OK**. Nowy element o nazwie **podstawowe dane wyjściowe z gry (aktywny)** pojawia się.

1. Wybierz element, który **podstawowe dane wyjściowe z gry (aktywny)**, kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót podstawowe wyjście z gry (aktywny)**. Nowy element o nazwie **skrót do podstawowe wyjście z gry (aktywny)** pojawia się.

1. Zmień nazwę elementu Skrót do *gry*, a następnie przeciągnij i upuść element do **Menu programy użytkownika** węzła w lewej części okna.

1. W **Eksploratora rozwiązań**, wybierz opcję **Instalator gry** projektu, a następnie wybierz **widoku** > **okno właściwości** lub kliknij przycisk  **F4** otworzyć **właściwości** okna.

1. Podaj dodatkowe szczegóły, jak mają się pojawiać w Instalatorze.  Na przykład użyć *Contoso* dla **producenta**, *Instalator gry* dla **nazwa produktu**, i *http\://www.contoso.com* dla **SupportUrl**.

1. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**. W **projektu** tabeli, w obszarze **kompilacji** kolumny, zaznacz pole **Instalator gry**. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** do tworzenia projektu gier i projektu Instalatora gier.

1. W folderze rozwiązania zlokalizuj program setup.exe, który został zbudowany z projektu Instalatora gry, a następnie uruchom go w celu zainstalowania aplikacji gier na komputerze. Możesz skopiować ten plik (i GameInstaller.msi) do zainstalowania aplikacji i jej wymagane pliki biblioteki na innym komputerze.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Aby zainstalować instalacja i wdrożenie szablonu projektu programu Visual Studio 2017 i jego starszych wersji

1. Po połączeniu się z Internetem, w programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

1. W obszarze **rozszerzenia i aktualizacje**, wybierz opcję **Online** kartę i typ *projektów Instalatora programu Visual Studio Microsoft* w polu wyszukiwania. Trafienia **Enter**, wybierz opcję **programu Microsoft Visual Studio \<wersji > Projekty Instalatora**i kliknij przycisk **Pobierz**.

1. Wybierz zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz **pliku** > **niedawne projekty i rozwiązania**, a następnie wybierz **gry** rozwiązania, aby otworzyć go ponownie.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Aby utworzyć projekt instalacyjny i zainstalować Twój program

1. Zmień konfigurację aktywngo rozwiązania do wydania. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**. W **programu Configuration Manager** dialogowym **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz **wersji**. Wybierz **Zamknij** przycisk, aby zapisać konfigurację.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **nowy projekt** okno dialogowe.

1. W lewym okienku okna dialogowego, rozwiń **zainstalowane** > **inne typy projektów** węzłów, a następnie wybierz **Instalatora programu Visual Studio**. W środkowym okienku wybierz **projektu Instalatora**.

1. Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. W tym przykładzie wprowadź *Instalator gry*. W **rozwiązania** listy rozwijanej wybierz **Dodaj do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystenta pliku (Instalator gry)** zostanie otwarta karta w oknie edytora.

1. Kliknij prawym przyciskiem myszy **folderu aplikacji** a następnie wybierz węzeł **Dodaj** > **dane wyjściowe projektu** otworzyć **Dodaj grupę wyjściową projektu**okno dialogowe.

1. W oknie dialogowym wybierz **podstawowe wyjście** i kliknij przycisk **OK**. Nowy element o nazwie **podstawowe dane wyjściowe z gry (aktywny)** pojawia się.

1. Wybierz element, który **podstawowe dane wyjściowe z gry (aktywny)**, kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót podstawowe wyjście z gry (aktywny)**. Nowy element o nazwie **skrót do podstawowe wyjście z gry (aktywny)** pojawia się.

1. Zmień nazwę elementu Skrót do *gry*, a następnie przeciągnij i upuść element do **Menu programy użytkownika** węzła w lewej części okna.

1. W **Eksploratora rozwiązań**, wybierz opcję **Instalator gry** projektu, a następnie wybierz **widoku** > **okno właściwości** lub kliknij przycisk  **F4** otworzyć **właściwości** okna.

1. Podaj dodatkowe szczegóły, jak mają się pojawiać w Instalatorze.  Na przykład użyć *Contoso* dla **producenta**, *Instalator gry* dla **nazwa produktu**, i *http\://www.contoso.com* dla **SupportUrl**.

1. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**. W **projektu** tabeli, w obszarze **kompilacji** kolumny, zaznacz pole **Instalator gry**. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** do tworzenia projektu gier i projektu Instalatora gier.

1. W folderze rozwiązania zlokalizuj program setup.exe, który został zbudowany z projektu Instalatora gry, a następnie uruchom go w celu zainstalowania aplikacji gier na komputerze. Możesz skopiować ten plik (i GameInstaller.msi) do zainstalowania aplikacji i jej wymagane pliki biblioteki na innym komputerze.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Przewodnik: Debugowanie projektu (C++)](walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
[Wdrażanie aplikacji komputerowych](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
