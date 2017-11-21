---
title: "Krok 0 - zainstalować obsługi języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Zainstaluj obsługę programu Visual Studio dla programu Visual C++"
ms.custom: mvc
ms.date: 10/17/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 840f23d894e8aacc53a735fa8e1c25a671ed3a2a
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="install-c-support-in-visual-studio"></a>Instalowanie obsługi języka C++ w programie Visual Studio

Jeśli nie zostały pobrane i jeszcze zainstalowany program Visual Studio i narzędzia Visual C++, Oto jak rozpocząć pracę.

## <a name="prerequisites"></a>Wymagania wstępne

- Połączenie szerokopasmowe. Instalator programu Visual Studio można pobrać kilka GB danych.

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepsze środowisko programistyczne. Upewnij się, że najnowsze aktualizacje są stosowane do systemu, przed zainstalowaniem programu Visual Studio.

- Za mało wolnego miejsca na dysku. Visual Studio wymaga co najmniej 7GB miejsca na dysku i może zająć 50GB lub więcej, jeśli zainstalowano wiele typowych opcji. Firma Microsoft zaleca się, że należy ją zainstalować na dysku C:.

Szczegółowe informacje dotyczące miejsca na dysku i wymagania dotyczące systemu operacyjnego, zobacz [wymagania systemowe 2017 r w usłudze Visual Studio](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Instalator raporty ilość miejsca na dysku jest wymagana dla opcji, którą wybierzesz.

## <a name="installation"></a>Instalacja

1. Pobierz najnowszą wersję Instalatora programu Visual Studio 2017 r dla systemu Windows.

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&utm_source=docs&utm_medium=clickbutton">Zainstaluj program Visual Studio 2017 Community</a>

   >[!Tip]
   > Wersja Community to dla indywidualnych deweloperów, uczenie klasy academic badań i rozwoju typu open source. Do innych celów, należy zainstalować <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Professional</a> lub <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Enterprise</a>.

1. Znajdź plik Instalatora należy pobrać i uruchom go. Może być wyświetlany w przeglądarce lub może go znaleźć w folderze pobrane. Instalator wymaga uprawnień administratora do uruchomienia. Może zostać wyświetlony **Kontrola konta użytkownika** okno dialogowe z pytaniem, aby udzielić uprawnień, aby umożliwić Instalator wprowadzić zmiany w systemie; wybierz **tak**. Jeśli masz problem, Znajdź pobrany plik w Eksploratorze plików, kliknij prawym przyciskiem myszy ikonę Instalatora, a następnie wybierz pozycję **Uruchom jako Administrator** z menu kontekstowego.

   ![Uruchom Instalatora programu Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "uruchom Instalator programu Visual Studio")

1. Instalator wyświetla listę obciążeń, grup powiązane opcje dla rozwoju określonych obszarów. Obsługa dla języka C++ jest obecnie częścią opcjonalne obciążeń, które nie są instalowane domyślnie.

   ![Tworzenie pulpitu za pomocą języka C++](../build/media/desktop-development-with-cpp.png "tworzenia klasycznych aplikacji w języku C++")

    Dla języka C++, wybierz **tworzenia klasycznych aplikacji w języku C++** obciążenia, a następnie wybierz **zainstalować**.

   ![Instalowanie tworzenia klasycznych aplikacji przy użyciu języka C++ obciążenia](../build/media/vscpp-concierge-choose-workload.gif "instalowanie tworzenia klasycznych aplikacji przy użyciu obciążenia C++")

1. Po zakończeniu instalacji wybierz **uruchamianie** przycisk, aby uruchomić program Visual Studio.

   Przy pierwszym uruchomieniu programu Visual Studio, zostanie wyświetlona prośba o zalogowanie się Account Microsoft. Jeśli nie masz, można utworzyć jedną bezpłatnie. Należy wybrać motywu. Nie martw się, można zmienić go później, jeśli chcesz. 

   Visual Studio może potrwać kilka minut w celu przygotowania do użycia przy pierwszym uruchomieniu go. Oto, co wygląda w szybkiego ujęć poklatkowych:

   ![Zaloguj się do niego Visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "programu Visual Studio 2017 Zaloguj")

   Visual Studio rozpoczyna się znacznie szybciej, gdy zostanie uruchomiony ponownie.

1. Po otwarciu programu Visual Studio należy sprawdzić, czy zostanie wyróżniona ikony flagi na pasku tytułu:

   ![Flaga powiadomienia usługi Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "flagę powiadomienia programu Visual Studio 2017 r.")

   Podświetlony, zaznacz go, aby otworzyć **powiadomienia** okna. Jeśli wszystkie aktualizacje są dostępne dla programu Visual Studio, zaleca się ich teraz zainstalować. Po zakończeniu instalacji uruchom ponownie program Visual Studio.

Po uruchomieniu programu Visual Studio można przystąpić do przejdź do następnego kroku.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Krok 1: Tworzenie projektu C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
