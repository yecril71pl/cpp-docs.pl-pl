---
title: Wdrażanie aplikacji przy użyciu pakietu redystrybucyjnego (C++)
ms.date: 09/17/2018
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: ccf6b74096894c2e48258e6e0a60b807c7c6c5b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787536"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Przewodnik: Wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++

W tym artykule opisano sposób użycia pakietu redystrybucyjnego Visual C++ do wdrożenia aplikacji w języku Visual C++.

## <a name="prerequisites"></a>Wymagania wstępne

Konieczne jest posiadanie tych składników w celu przeprowadzenia tego instruktażu:

- Komputer, który jest zainstalowany program Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Na potrzeby wdrażania aplikacji przez pakiet redystrybucyjny Visual C++

1.  Tworzenie i tworzenie aplikacji MFC, wykonując kroki opisane w [instruktażu: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalacji](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Utwórz plik, nadaj jej nazwę setup.bat i dodaj następujące polecenia do niego. Zmiana `MyMFCApplication` do nazwy projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Utwórz samowyodrębniający się plik konfiguracji:

   1. Polecenie w wierszu polecenia lub w **Uruchom** okna, uruchom iexpress.exe.

   1. Wybierz **Utwórz nowy plik dyrektywy wyodrębniania Self** , a następnie wybierz **dalej** przycisku.

   1. Wybierz **wyodrębnić pliki, a następnie uruchom polecenie instalacji** , a następnie wybierz **dalej**.

   1. W polu tekstowym wprowadź nazwę aplikacji MFC, a następnie wybierz **dalej**.

   1. Na **monit o potwierdzenie** wybierz opcję **wiersz nr** , a następnie wybierz **dalej**.

   1. Na **umowę licencyjną** wybierz opcję **nie są wyświetlane licencję** , a następnie wybierz **dalej**.

   1. Na **spakowane pliki** strony, Dodaj następujące pliki, a następnie wybierz **dalej**.

      - Aplikacja MFC (plik .exe).

      - vcredist_x86.exe. Ten plik znajduje się w \Program Files (x86) \Microsoft Visual Studio \<wersji > \SDK\Bootstrapper\Packages\. Możesz również pobrać ten plik z [Microsoft](https://www.microsoft.com/download/confirmation.aspx?id=5555).

      - Plik setup.bat, który został utworzony w poprzednim kroku.

   1. Na **Zainstaluj Program do uruchomienia** stronie **Zainstaluj Program** polu tekstowym wprowadź następujące polecenie w wierszu, a następnie wybierz **dalej**.

      **cmd.exe /c "setup.bat"**

   1. Na **okno Pokaż** wybierz opcję **domyślne** , a następnie wybierz **dalej**.

   1. Na **Zakończono komunikat** wybierz opcję **żaden komunikat** , a następnie wybierz **dalej**.

   1. Na **nazwę pakietu i opcje** strony, wprowadź nazwę dla samorozpakowujący się plik Instalatora, wybierz opcję **Store plików za pomocą długa nazwa pliku w pakiecie** opcji, a następnie wybierz **dalej**. Na końcu nazwy pliku musi być na przykład Setup.exe—for *MyMFCApplicationSetup.exe*.

   1. Na **skonfigurować ponowne uruchomienie** wybierz opcję **bez ponownego uruchamiania** , a następnie wybierz **dalej**.

   1. Na **Zapisz dyrektywy wyodrębniania Self** wybierz opcję **pliku Zapisz Self wyodrębniania — dyrektywa (SED)** , a następnie wybierz **dalej**.

   1. Na **Utwórz pakiet** wybierz **dalej**. Wybierz **Zakończ**.

1. Przetestuj samowyodrębniający się plik instalacji na innym komputerze, który nie ma bibliotek języka Visual C++:

   1. Na innym komputerze Pobierz kopię pliku konfiguracji, a następnie zainstalować ją, uruchamiając go, a następnie zgodnie z krokami, które zawiera. W zależności od opcji wybranych, instalacja może wymagać **Uruchom jako administrator** polecenia.

   1. Uruchamianie aplikacji MFC.

      Samorozpakowujący się plik instalacyjny instaluje aplikacji MFC, który znajduje się w folderze, który określono w kroku 2. Aplikacja zostanie uruchomiona pomyślnie, ponieważ Instalator pakiet redystrybucyjny Visual C++ jest uwzględniony w samorozpakowujący się plik instalacyjny.

      > [!IMPORTANT]
      > Aby określić, która wersja środowiska uruchomieniowego jest zainstalowana, Instalator sprawdza \HKLM\SOFTWARE\Microsoft\VisualStudio klucza rejestru\\\<wersji > \VC\Runtimes\\<platform>. Jeśli aktualnie zainstalowana wersja jest nowsza niż wersja, która Instalator podejmuje próbę instalacji, Instalator zwraca sukces bez konieczności instalowania starszej wersji i pozostawia dodatkowe wpis na stronie zainstalowanych programów w Panelu sterowania.

## <a name="see-also"></a>Zobacz także

[Przykłady wdrożeń](deployment-examples.md)<br/>
