---
title: Wdrażanie aplikacji przy użyciu pakietu redystrybucyjnego (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: d2bd0794a67cf70b9da0499e3d2cafa553531fe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370253"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++

W tym artykule krok po kroku opisano, jak używać pakietu redystrybucyjnego Visual C++ do wdrażania aplikacji Visual C++.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktajaż, musisz mieć następujące składniki:

- Komputer z zainstalowanym programem Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Aby wdrożyć aplikację za pomocą pakietu redystrybucyjnego języka Visual C++

1. Tworzenie i tworzenie aplikacji MFC, wykonując kroki opisane w [przewodniku: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Utwórz plik, nazwij go setup.bat i dodaj do niego następujące polecenia. Zmień `MyMFCApplication` nazwę projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Utwórz samorozdysmujący się plik instalacyjny:

   1. W wierszu polecenia lub w oknie **Uruchom** uruchom plik iexpress.exe.

   1. Wybierz **pozycję Utwórz nowy plik dyrektywy samodzielnego wyodrębniania,** a następnie wybierz przycisk **Dalej.**

   1. Wybierz **pozycję Wyodrębnij pliki i uruchom polecenie instalacji,** a następnie wybierz pozycję **Dalej**.

   1. W polu tekstowym wprowadź nazwę aplikacji MFC, a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Monit o potwierdzenie** wybierz pozycję Nie **monituj,** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Umowa licencyjna** wybierz pozycję **Nie wyświetlaj licencji,** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Spakowane pliki** dodaj następujące pliki, a następnie wybierz pozycję **Dalej**.

      - Twoja aplikacja MFC (plik exe).

      - vcredist_x86.exe. W programie Visual Studio 2015 ten plik znajduje się w *%VCINSTALLDIR%redist\\1033\\*. W programach Visual Studio 2017 i Visual Studio 2019 ten plik znajduje się w *%VCToolsRedistDir%*. Można również [pobrać najnowszy obsługiwany plik redist z firmy Microsoft](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Plik setup.bat utworzony we wcześniejszym kroku.

   1. Na stronie **Zainstaluj program do uruchomienia** w polu tekstowym Zainstaluj **program** wprowadź następujący wiersz polecenia, a następnie wybierz pozycję **Dalej**.

      **cmd.exe /c "setup.bat"**

   1. Na stronie **Okna Pokazywalenie** wybierz pozycję **Domyślne,** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Zakończono wiadomość** wybierz pozycję **Brak wiadomości,** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Nazwa i opcje pakietu** wprowadź nazwę samodzielnego wyodrębniania pliku instalacyjnego, wybierz opcję Przechowuj pliki przy użyciu opcji Długa nazwa pliku wewnątrz **pakietu,** a następnie wybierz pozycję **Dalej**. Koniec nazwy pliku musi być setup.exe — na przykład *MyMFCApplicationSetup.exe*.

   1. Na stronie **Konfigurowanie ponownego uruchamiania** wybierz pozycję **Brak ponownego uruchomienia,** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Zapisz dyrektywę o samodzielnym ekstrakcji** wybierz **pozycję Zapisz plik dyrektywy sed (Self Extraction Directive),** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Tworzenie pakietu** wybierz pozycję **Dalej**. Wybierz **pozycję Zakończ**.

1. Przetestuj plik instalacyjny samorozdysobowywania się na innym komputerze, który nie ma bibliotek visual c++:

   1. Na drugim komputerze pobierz kopię pliku instalacyjnego, a następnie zainstaluj go, uruchamiając go i wykonując kroki, które zapewnia. W zależności od wybranych opcji instalacja może wymagać polecenia **Uruchom jako administrator.**

   1. Uruchom aplikację MFC.

      Samorozdyskłany plik instalacyjny instaluje aplikację MFC znajdującą się w folderze określonym w kroku 2. Aplikacja działa pomyślnie, ponieważ instalator pakietu redystrybucyjnego Visual C++ znajduje się w pliku instalacyjnym samorozdyskłania.

      > [!IMPORTANT]
      > Aby ustalić, która wersja środowiska wykonawczego jest zainstalowana, \\instalator\\sprawdza\\\\klucz rejestru\\HKLM\\SOFTWARE\\Microsoft VisualStudio_wersja_\\VC Runtimes_platformy_\\Wersja. Jeśli aktualnie zainstalowana wersja jest nowsza niż wersja, którą instalator próbuje zainstalować, instalator zwraca powodzenie bez instalowania starszej wersji i pozostawia dodatkowy wpis na stronie zainstalowane programy w Panelu sterowania.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](deployment-examples.md)<br/>
