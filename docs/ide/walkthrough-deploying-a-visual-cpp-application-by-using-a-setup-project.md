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
ms.openlocfilehash: a9e781a311f965dc71bb64425a4d1354d6b38e1a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416568"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu instalacji projektu

W tym artykule opisano, jak wdrażanie aplikacji Visual C++ za pomocą projektu Instalatora.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Komputer z programu Visual Studio 2012.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Aby wdrożyć aplikację przy użyciu projektu instalacji

1. Użyj **MFC ApplicationWizard** do tworzenia nowego rozwiązania programu Visual Studio. Można znaleźć kreatora z **nowy projekt** okna dialogowego rozwiń **Visual C++** węzeł **MFC**, wybierz opcję **aplikacji MFC**, wprowadź Nazwa projektu, a następnie kliknij przycisk **OK**.

1. Zmień konfigurację aktywngo rozwiązania, aby **wersji**. Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**. Z **programu Configuration Manager** okno dialogowe, wybierz opcję **wersji** z **Konfiguracja rozwiązania aktywnego** pole listy rozwijanej.

1. Naciśnij klawisz F7, aby skompilować aplikację. Lub na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Dzięki temu projektu Instalatora, aby użyć danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, Pobierz InstallShield Limited Edition (ISLE), która jest bezpłatna dla deweloperów programu Visual Studio i zastępuje funkcje szablonów projektu w programie Visual Studio dla instalacji i wdrożenia. Po nawiązaniu połączenia z Internetem, otwórz **nowy projekt** okno dialogowe, wybierając **pliku**, **New**, **projektu** menu paska lub przez Kliknij prawym przyciskiem myszy rozwiązania w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj**, **nowy projekt**. Rozwiń **inne typy projektów** węzła, wybierz **Włącz InstallShield Limited Edition** w **instalacja i wdrożenie** węzeł i postępuj zgodnie z wyświetlanymi instrukcjami. Po pobrane, zainstalowane i aktywowane InstallShield Limited Edition, zamknij program Visual Studio i otwórz go ponownie.

1. Otwórz **nowy projekt** okno dialogowe ponownie, rozwiń węzeł **inne typy projektów** węzeł i wybierz polecenie **projekt InstallShield Limited Edition** w  **InstallShield Limited Edition** węzła.

1. Postępuj zgodnie z instrukcjami wyświetlanymi w **wprowadzenie** węzła projektu Instalatora utworzonej przez szablon programu InstallShield Limited Edition, można dodać odwołania danych wyjściowych do projektu programu Visual Studio MFC.

1. Tworzenie projektu Instalatora, aby utworzyć plik Instalatora (setup.exe). Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu Instalatora w **Eksploratora rozwiązań** i wybierz **kompilacji**.

   InstallShield Limited Edition tworzy plik Instalatora w drzewie projektu Instalatora (domyślnie go może znajdować się w podfolderze Express\SingleImage\DiskImages\DISK1 projektu Instalatora).

1. Uruchom program instalacyjny na drugim komputerze, który nie ma bibliotek języka Visual C++.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](../ide/deployment-examples.md)