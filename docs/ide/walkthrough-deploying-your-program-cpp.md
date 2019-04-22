---
title: 'Przewodnik: Wdrażanie Twojego programu (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: aa0e1cd6ec7c27b8d3ccc1e327f3cb8da526d4f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769267"
---
# <a name="walkthrough-deploying-your-program-c"></a>Przewodnik: Wdrażanie Twojego programu (C++)

Teraz, gdy utworzono aplikację wykonując wcześniej pokrewne instruktaże, ostatnim krokiem jest utworzenie Instalatora, tak aby inni użytkownicy mogli zainstalować program na swoich komputerach. Dla Instalatora dodasz nowy projekt do istniejącego rozwiązania. Dane wyjściowe tego nowego projektu to plik setup.exe, który zainstaluje twoją aplikację na innym komputerze.

Przewodnik pokazuje, jak wdrożyć aplikację przy użyciu Instalatora Windows. Można również użyć ClickOnce do wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../windows/clickonce-deployment-for-visual-cpp-applications.md). Aby uzyskać więcej informacji o wdrażaniu ogólnie rzecz biorąc, zobacz [wdrażania aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Wymagania wstępne

- Przewodnik zakłada, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Nie można ukończyć instruktażu w wersjach Express programu Visual Studio.

- Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie Microsoft projektów Instalatora programu Visual Studio, zgodnie z opisem w dalszych krokach później. Rozszerzenie jest bezpłatna dla deweloperów programu Visual Studio i dodaje funkcje instalacji i wdrażania szablonów projektu do programu Visual Studio.

### <a name="to-install-the-visual-studio-setup-and-deployment-project-template"></a>Aby zainstalować szablonu projektu instalacji i wdrożenia programu Visual Studio

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

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Przewodnik: Debugowanie projektu (C++)](walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
[Wdrażanie aplikacji komputerowych](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
