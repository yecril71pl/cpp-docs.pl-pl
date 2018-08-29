---
title: Instalowanie obsługi języka C++ w programie Visual Studio 2017 | Dokumentacja firmy Microsoft
description: Instalowanie obsługi programu Visual Studio dla języka Visual C++
ms.custom: mvc
ms.date: 06/21/2018
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ee0763608edde0f7ceff81983a324190b605ff7
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130894"
---
# <a name="install-c-support-in-visual-studio"></a>Instalowanie obsługi języka C++ w programie Visual Studio

Jeśli nie zostały pobrane i jeszcze zainstalowany program Visual Studio 2017 i narzędzi Visual C++, Oto jak rozpocząć pracę.

## <a name="prerequisites"></a>Wymagania wstępne

- Połączenie szerokopasmowe. Instalator programu Visual Studio można pobrać kilku gigabajtów danych.

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepszego komfortu programowania. Upewnij się, że najnowsze aktualizacje są stosowane do systemu, przed zainstalowaniem programu Visual Studio.

- Za mało wolnego miejsca na dysku. Visual Studio wymaga co najmniej 7GB miejsca na dysku i może potrwać 50GB lub więcej, jeśli zainstalowano wiele typowych opcji. Zaleca się, że masz zainstalowane na dysku C:.

Aby uzyskać szczegółowe informacje dotyczące miejsca na dysku i wymagania dotyczące systemu operacyjnego, zobacz [wymagania systemowe rodziny produktów Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalator raporty, ilość miejsca na dysku jest wymagana dla wybranych opcji.

## <a name="visual-studio-2015-installation"></a>Instalacja programu Visual Studio 2015

 Aby zainstalować program Visual Studio 2015, przejdź do [pobieranie starszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny, a następnie wybierz **Instalacja niestandardowa** , a następnie wybierz składnik C++. 

 Ogólnie rzecz biorąc zdecydowanie zaleca się użycie programu Visual Studio 2017, nawet wtedy, gdy należy przeprowadzić kompilowanie kodu przy użyciu kompilatora Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](../porting/use-native-multi-targeting.md).

## <a name="visual-studio-2017-installation"></a>Instalacja programu Visual Studio 2017

1. Pobierz najnowszą wersję Instalatora programu Visual Studio 2017 for Windows.

   > [!div class="nextstepaction"]
   > [Zainstaluj program Visual Studio Community 2017 r.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Wersja Community to dla indywidualnych deweloperów, edukacyjne, badań akademickich i programowania typu open source. Do innych celów, należy zainstalować [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Znajdź plik Instalatora został pobrany i uruchom go. Może być wyświetlany w przeglądarce lub może okazać się w folderze pobrane. Instalator wymaga uprawnień administratora do uruchomienia. Może zostać wyświetlony **Kontrola konta użytkownika** okno dialogowe z monitem o nadanie uprawnień umożliwiających Instalatora, wprowadzić zmiany do systemu; wybierz **tak**. Jeśli występują problemy, Znajdź pobrany plik w Eksploratorze plików, kliknij prawym przyciskiem myszy na ikonie Instalatora, a następnie wybierz **Uruchom jako Administrator** z menu kontekstowego.

   ![Uruchom Instalatora programu Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "uruchom Instalatora programu Visual Studio")

1. Instalator przedstawia listy obciążeń, powiązane opcje obszary rozwoju określonych grup. Podpora androidu Pro C++ jest teraz częścią opcjonalne obciążeń, które nie są instalowane domyślnie.

   ![Programowanie aplikacji klasycznych w języku C++](../build/media/desktop-development-with-cpp.png "programowanie aplikacji klasycznych w języku C++")

    Dla języka C++, wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, a następnie wybierz **zainstalować**.

   ![Zainstaluj programowanie aplikacji klasycznych w języku C++](../build/media/vscpp-concierge-choose-workload.gif "zainstalować programowanie aplikacji klasycznych w języku C++")

1. Po zakończeniu instalacji wybierz **Uruchom** przycisk, aby uruchomić program Visual Studio.

   Podczas pierwszego uruchomienia programu Visual Studio, zostanie wyświetlony monit o zalogowanie Account firmy Microsoft. Jeśli nie masz, możesz go utworzyć za darmo. Należy także wybrać motyw. Nie martw się, możesz go zmienić później, jeśli chcesz. 

   Visual Studio może potrwać kilka minut w celu przygotowania do użycia przy pierwszym uruchomieniu. Poniżej przedstawiono, jak to wygląda w ujęć poklatkowych szybkie:

   ![Zaloguj się do niego programu Visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "Zaloguj się do niego programu Visual Studio 2017")

   Program Visual Studio rozpoczyna się znacznie szybciej, gdy zostanie uruchomiony ponownie.

1. Po otwarciu programu Visual Studio, należy sprawdzić, jeśli zostanie wyróżniona ikonę flagi na pasku tytułu:

   ![Flaga powiadomienia w usłudze Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "flagę powiadomienia programu Visual Studio 2017")

   Jeśli jest wyróżniona, zaznacz ją, aby otworzyć **powiadomienia** okna. Jeśli istnieją jakiekolwiek aktualizacje dostępne dla programu Visual Studio, zalecamy możesz zainstalować je teraz. Po zakończeniu instalacji uruchom ponownie program Visual Studio.

Po uruchomieniu programu Visual Studio jesteś gotowy przejść do następnego kroku.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Tworzenie projektu C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
