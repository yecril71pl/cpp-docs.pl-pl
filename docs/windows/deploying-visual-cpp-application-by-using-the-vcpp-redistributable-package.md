---
title: Wdrażanie aplikacji przy użyciu pakietu redystrybucyjnego (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: 1e09debc53e5b1b3e1eeaa6a63924b04fd2b7ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443892"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++

W tym artykule krok po kroku opisano sposób użycia pakietu redystrybucyjnego C++ Visual w celu wdrożenia aplikacji wizualnej C++ .

## <a name="prerequisites"></a>Wymagania wstępne

Te składniki muszą być dostępne do wykonania w tym instruktażu:

- Komputer, na którym jest zainstalowany program Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek wizualizacji C++ .

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Aby użyć pakietu redystrybucyjnego Visual C++ do wdrożenia aplikacji

1.  Utwórz i skompiluj aplikację MFC, wykonując czynności opisane w [przewodniku: wdrażanie aplikacji wizualnej C++ przy użyciu projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Utwórz plik, nazwij go Setup. bat i Dodaj do niego następujące polecenia. Zmień `MyMFCApplication` na nazwę projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Utwórz samowyodrębniający się plik instalacyjny:

   1. W wierszu polecenia lub w oknie **uruchamiania** , uruchom program IExpress. exe.

   1. Wybierz opcję **Utwórz nowy plik dyrektywy samowyodrębniania** , a następnie wybierz przycisk **dalej** .

   1. Wybierz pozycję **Wyodrębnij pliki i uruchom polecenie instalacji** , a następnie wybierz przycisk **dalej**.

   1. W polu tekstowym wprowadź nazwę aplikacji MFC, a następnie wybierz przycisk **dalej**.

   1. Na stronie **monitu o potwierdzenie** wybierz pozycję **Brak monitu** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Umowa licencyjna** wybierz pozycję nie **Wyświetlaj licencji** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **spakowane pliki** Dodaj następujące pliki, a następnie wybierz przycisk **dalej**.

      - Aplikacja MFC (plik exe).

      - vcredist_x86.exe. W programie Visual Studio 2015 ten plik znajduje się w lokalizacji *% VCINSTALLDIR% Redist\\1033\\* . W programie Visual Studio 2017 i Visual Studio 2019 ten plik znajduje się w lokalizacji *% VCToolsRedistDir%* . Możesz również [pobrać najnowszy obsługiwany plik Redist od firmy Microsoft](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Plik Setup. bat, który został utworzony w poprzednim kroku.

   1. Na stronie **Zainstaluj program do uruchomienia** w polu tekstowym **Zainstaluj program** wprowadź następujący wiersz polecenia, a następnie wybierz przycisk **dalej**.

      **cmd. exe/c "Setup. bat"**

   1. Na stronie **Pokaż okno** wybierz pozycję **domyślne** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Zakończono wiadomość** wybierz pozycję **Brak komunikatu** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Nazwa pakietu i opcje** wprowadź nazwę pliku instalacyjnego samowyodrębniającym się, wybierz opcję **Zapisz pliki przy użyciu długiej nazwy pliku w pakiecie** , a następnie wybierz przycisk **dalej**. Na końcu nazwy pliku musi być Setup. exe — na przykład *MyMFCApplicationSetup. exe*.

   1. Na stronie **Konfigurowanie ponownego uruchamiania** wybierz pozycję **nie uruchamiaj ponownie** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Zapisywanie dyrektywy samowyodrębniania** wybierz pozycję **Zapisz plik dyrektywy autowyodrębniania (SED)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Tworzenie pakietu** wybierz pozycję **dalej**. Wybierz pozycję **Zakończ**.

1. Przetestuj plik instalacyjny samodzielnego wyodrębniania na innym komputerze, który nie ma bibliotek wizualizacji C++ :

   1. Na innym komputerze Pobierz kopię pliku instalacyjnego, a następnie zainstaluj ją, uruchamiając ją i wykonując czynności, które zapewnia. W zależności od wybranych opcji instalacja może wymagać polecenia **Uruchom jako administrator** .

   1. Uruchom aplikację MFC.

      Plik instalacyjny samodzielnego programu instaluje aplikację MFC, która znajduje się w folderze określonym w kroku 2. Aplikacja została uruchomiona pomyślnie, ponieważ Instalator C++ pakietu redystrybucyjnego wizualizacji został uwzględniony w pliku instalacyjnym samowyodrębniającym się.

      > [!IMPORTANT]
      > Aby określić, która wersja środowiska uruchomieniowego jest zainstalowana, Instalator sprawdza klucz rejestru \\HKLM\\oprogramowania\\Microsoft\\VisualStudio\\_wersja_\\VC\\Runtimes\\_platform_\\wersja. Jeśli aktualnie zainstalowana wersja jest nowsza niż wersja, którą Instalator próbuje zainstalować, Instalator zwróci sukces bez instalowania starszej wersji i pozostawia dodatkowy wpis na stronie zainstalowane programy w panelu sterowania.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](deployment-examples.md)<br/>
