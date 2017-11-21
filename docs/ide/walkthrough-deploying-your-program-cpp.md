---
title: "Wskazówki: Wdrażanie Twojego programu (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6cec4d77ec1c5bcc010a061065516ef132ec88c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-deploying-your-program-c"></a>Wskazówki: wdrażanie Twojego programu (C++)
Teraz, po utworzeniu aplikacji, wykonując wcześniej powiązane wskazówki, które są wymienione w [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), ostatnim krokiem jest utworzenie Instalatora, aby inni użytkownicy mogą Zainstaluj program na swoich komputerach. Aby to zrobić, będzie dodać nowy projekt do istniejącego rozwiązania. Dane wyjściowe tego nowego projektu jest plik setup.exe, który zainstaluje aplikację na innym komputerze.  
  
 W tym przewodniku pokazano, jak wdrożyć aplikację za pomocą Instalatora Windows. Umożliwia także ClickOnce do wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md). Aby uzyskać więcej informacji na temat wdrażania ogólnie rzecz biorąc, zobacz [wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku przyjęto założenie, że rozumiesz podstawowe informacje na temat języka C++.  
  
-   Założono również, że zostały wykonane wcześniej powiązane wskazówki, które są wymienione w [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Nie można ukończyć tego przewodnika w wersji Express programu Visual Studio.  
  
-   Jeśli jeszcze tego nie zrobiono, Pobierz InstallShield Limited Edition (Wyspa), jak opisano w krokach w dalszej części tego artykułu. Wyspa jest bezpłatna dla deweloperów programu Visual Studio i zastępuje funkcjonalność szablony projektów instalacji i wdrażania we wcześniejszych wersjach programu Visual Studio.  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>Aby zainstalować Wyspa szablonu projektu instalacji i wdrażania  
  
1.  Po nawiązaniu połączenia z Internetem, na pasku menu wybierz **pliku**, **nowy**, **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  W lewym okienku okna dialogowego rozwiń **zainstalowana**, **szablony**, i **inne typy projektów** węzłów, a następnie wybierz **instalacji i wdrażania**. W środkowym okienku wybierz **Włącz InstallShield Limited Edition** , a następnie wybierz **OK** przycisku.  
  
3.  Postępuj zgodnie z instrukcjami, aby zainstalować InstallShield Limited Edition dla programu Visual Studio (Wyspa).  
  
4.  Po zostały pobrane, zainstalowane i aktywowane Wyspa, zamknij program Visual Studio i otwórz go ponownie.  
  
5.  Na pasku menu wybierz **pliku**, **ostatnie projekty i rozwiązania**, a następnie wybierz pozycję **gry** rozwiązanie, aby otworzyć go ponownie.  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>Do tworzenia projektu Instalatora i zainstaluj program  
  
1.  Zmień aktywnej konfiguracji rozwiązania do wydania. Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**. W **programu Configuration Manager** na okna dialogowego **aktywnej konfiguracji rozwiązania** listy rozwijanej wybierz **wersji**. Wybierz **Zamknij** przycisk, aby zapisać konfigurację.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
3.  W lewym okienku okna dialogowego rozwiń **zainstalowana**, **szablony**, i **inne typy projektów** węzłów, a następnie wybierz **instalacji i wdrażania**. W środkowym okienku wybierz **InstallShield Limited Edition projektu**.  
  
4.  Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. Na przykład wprowadź **Instalator gry**. W **rozwiązania** listy rozwijanej wybierz **dodać do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystentem projektu (Instalator gry)** Otwiera kartę w oknie edytora.  
  
5.  W dolnej części **Asystentem projektu (Instalator gry)** , wybierz pozycję **informacje o aplikacji** łącza.  
  
6.  Na **informacje o aplikacji** Podaj nazwę firmy, jaka ma występować w Instalatorze. Można korzystać z własnej nazwy firmy lub w tym przykładzie należy użyć **Contoso**. Podaj nazwę swojej aplikacji; w tym przykładzie należy określić **gry**. Podaj adres sieci web firmy lub w tym przykładzie należy użyć **http://www.contoso.com**.  
  
7.  W dolnej części **Asystentem projektu (Instalator gry)** , wybierz pozycję **rozmowy instalacji** łącza.  
  
8.  Na **rozmowy instalacji** w obszarze **czy chcesz wyświetlić okno dialogowe umowy licencyjnej**, wybierz pozycję **nr** przycisk opcji. W obszarze **będzie monitować użytkowników o wprowadzenie nazwy firmy i nazwa użytkownika**, wybierz pozycję **nr** przycisk opcji.  
  
9. W **Eksploratora rozwiązań**, rozwiń węzeł **Instalator gry** projektu, rozwiń **organizowanie Your Instalatora** węzeł, a następnie otwórz **informacjeogólne** strony.  
  
10. Na **informacje ogólne (Instalator gry)** karty w oknie edytora, określ **identyfikator twórcy Tag**, na przykład **regid.2012 12.com.Contoso**.  
  
11. W **Eksploratora rozwiązań**w obszarze **Instalator gry** projektu, rozwiń **Określ dane aplikacji** węzeł, a następnie otwórz **plików** Strona.  
  
12. Na **plików (Instalator gry)** karty w oknie edytora w obszarze **komputera pliki źródłowe**, otwórz menu skrótów **głównej dane wyjściowe z aplikacji Game** i wybierz polecenie **Kopiowania**.  
  
13. Otwórz menu skrótów w obszarze, w obszarze **nazwa** kolumny w **plików na komputerze docelowym**i wybierz polecenie **Wklej**. Nowy element o nazwie **dane wyjściowe Game.Primary** pojawi się.  
  
14. W **Eksploratora rozwiązań**w obszarze **Określ dane aplikacji** otworzyć węzła **pakietów redystrybucyjnych** strony.  
  
15. Na **pakietów redystrybucyjnych (Instalator gry)** karty w oknie edytora, wybierz opcję **Visual C++ 11.0 CRT (x86)** pole wyboru.  
  
16. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie** do tworzenia gier projektu i projektu Instalatora gier.  
  
17. W folderze rozwiązania zlokalizować program setup.exe, który został utworzony z projektu Instalatora grę, a następnie uruchom go w celu zainstalowania aplikacji gry na komputerze. Możesz skopiować ten plik do zainstalowania aplikacji i jego pliki biblioteki wymaganej na innym komputerze.  
  
18. Można ustawić wiele opcji, w projekcie Instalatora ze swoimi potrzebami. Aby uzyskać więcej informacji w **Eksploratora rozwiązań**w obszarze **Instalator gry** otwarciu projektu **wprowadzenie** strony, a następnie wybierz klawisz F1, aby otworzyć Wyspa biblioteki Pomocy.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [wskazówki: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)