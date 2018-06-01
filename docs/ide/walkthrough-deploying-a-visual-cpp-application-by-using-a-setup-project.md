---
title: Wdrażanie aplikacji Visual C++ przy użyciu instalacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33332783"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu instalacji projektu
Opisuje sposób instalacji projektu umożliwia wdrażanie aplikacji Visual C++.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Komputer z [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] zainstalowane.  
  
-   Dodatkowy komputer, który nie ma bibliotek języka Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Aby wdrożyć aplikację przy użyciu instalacji projektu  
  
1.  Użyj **MFC ApplicationWizard** Aby utworzyć nowe rozwiązanie Visual Studio. Kreator, z **nowy projekt** okna dialogowego rozwiń **Visual C++** węzła, wybierz opcję **MFC**, wybierz pozycję **aplikacji MFC**, wprowadź Nazwa projektu, a następnie kliknij przycisk **OK**.  
  
2.  Zmień konfigurację aktywne rozwiązanie, aby **wersji**. Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**. Z **programu Configuration Manager** okno dialogowe, wybierz opcję **wersji** z **aktywnej konfiguracji rozwiązania** pole listy rozwijanej.  
  
3.  Naciśnij klawisz F7 do skompilowania aplikacji. Lub na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Dzięki temu projektu Instalatora, aby użyć danych wyjściowych tego projektu aplikacji MFC.  
  
4.  Jeśli nie zostało to jeszcze zrobione, Pobierz InstallShield Limited Edition (Wyspa), który jest bezpłatna dla deweloperów programu Visual Studio i zastępuje funkcjonalność szablony projektów programu Visual Studio instalacji i wdrażania. Po nawiązaniu połączenia z Internetem, otwórz **nowy projekt** okno dialogowe, wybierając **pliku**, **nowy**, **projektu** menu paska lub przez prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj**, **nowy projekt**. Rozwiń węzeł **inne typy projektów** węzła, wybierz **Włącz InstallShield Limited Edition** w **instalacji i wdrażania** węzeł i postępuj zgodnie z instrukcjami wyświetlanymi. Po zostały pobrane, zainstalowane i aktywowane InstallShield Limited Edition, zamknij program Visual Studio i otwórz go ponownie.  
  
5.  Otwórz **nowy projekt** okno dialogowe ponownie, rozwiń węzeł **inne typy projektów** węzeł i wybierz polecenie **InstallShield Limited Edition projektu** w  **InstallShield Limited Edition** węzła.  
  
6.  Postępuj zgodnie z instrukcjami wyświetlanymi w **wprowadzenie** węzła projektu Instalatora utworzonej przez szablon InstallShield Limited Edition, aby dodać odwołanie do danych wyjściowych do projektu programu Visual Studio MFC.  
  
7.  Tworzenie projektu Instalatora, aby utworzyć plik Instalatora (setup.exe). Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu Instalatora w **Eksploratora rozwiązań** i wybierz **kompilacji**.  
  
     InstallShield Limited Edition tworzy plik Instalatora w drzewie projektu Instalatora (domyślnie mogą być umieszczone w podfolderze Express\SingleImage\DiskImages\DISK1 projektu Instalatora).  
  
8.  Uruchom program instalacyjny na innym komputerze, który nie ma bibliotek języka Visual C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady wdrożeń](../ide/deployment-examples.md)