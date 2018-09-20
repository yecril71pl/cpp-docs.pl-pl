---
title: Wdrażanie aplikacji przy użyciu pakietu redystrybucyjnego (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e213d5d91c229f7f07bc383f0a0158d85c05cf2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434508"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++

W tym artykule opisano sposób użycia pakietu redystrybucyjnego Visual C++ do wdrożenia aplikacji w języku Visual C++.

## <a name="prerequisites"></a>Wymagania wstępne

Konieczne jest posiadanie tych składników w celu przeprowadzenia tego instruktażu:

- Komputer, który jest zainstalowany program Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Na potrzeby wdrażania aplikacji przez pakiet redystrybucyjny Visual C++

1. Utwórz i skompiluj aplikację MFC, wykonując trzy pierwsze kroki w [wskazówki: Wdrażanie Visual C++ Application By Using projektu Instalatora](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

2. Utwórz plik, nadaj jej nazwę setup.bat i dodaj następujące polecenia do niego. Zmiana `MyMFCApplication` do nazwy projektu.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

3. Utwórz samowyodrębniający się plik konfiguracji:

   1. Polecenie w wierszu polecenia lub w **Uruchom** okna, uruchom iexpress.exe.

   2. Wybierz **Utwórz nowy plik dyrektywy wyodrębniania Self** , a następnie wybierz **dalej** przycisku.

   3. Wybierz **wyodrębnić pliki, a następnie uruchom polecenie instalacji** , a następnie wybierz **dalej**.

   4. W polu tekstowym wprowadź nazwę aplikacji MFC, a następnie wybierz **dalej**.

   5. Na **monit o potwierdzenie** wybierz opcję **wiersz nr** , a następnie wybierz **dalej**.

   6. Na **umowę licencyjną** wybierz opcję **nie są wyświetlane licencję** , a następnie wybierz **dalej**.

   7. Na **spakowane pliki** strony, Dodaj następujące pliki, a następnie wybierz **dalej**.

      - Aplikacja MFC (plik .exe).

      - VCRedist_x86.exe. Ten plik znajduje się w \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.

      - Plik setup.bat, który został utworzony w poprzednim kroku.

   8. Na **Zainstaluj Program do uruchomienia** stronie **Zainstaluj Program** polu tekstowym wprowadź następujące polecenie w wierszu, a następnie wybierz **dalej**.

      **cmd.exe /c "setup.bat"**

   9. Na **okno Pokaż** wybierz opcję **domyślne** , a następnie wybierz **dalej**.

   10. Na **Zakończono komunikat** wybierz opcję **żaden komunikat** , a następnie wybierz **dalej**.

   11. Na **nazwę pakietu i opcje** strony, wprowadź nazwę dla samorozpakowujący się plik Instalatora, wybierz opcję **Store plików za pomocą długa nazwa pliku w pakiecie** opcji, a następnie wybierz **dalej**. Na końcu nazwy pliku musi być Setup.exe—for przykład MyMFCApplicationSetup.exe.

   12. Na **skonfigurować ponowne uruchomienie** wybierz opcję **bez ponownego uruchamiania** , a następnie wybierz **dalej**.

   13. Na **Zapisz dyrektywy wyodrębniania Self** wybierz opcję **pliku Zapisz Self wyodrębniania — dyrektywa (SED)** , a następnie wybierz **dalej**.

   14. Na **Utwórz pakiet** wybierz **dalej**.

4. Przetestuj samowyodrębniający się plik instalacji na innym komputerze, który nie ma bibliotek języka Visual C++:

   1. Na innym komputerze Pobierz kopię pliku konfiguracji, a następnie zainstalować ją, uruchamiając go, a następnie zgodnie z krokami, które zawiera.

   2. Uruchamianie aplikacji MFC.

      Samorozpakowujący się plik instalacyjny instaluje aplikacji MFC, który znajduje się w folderze, który określono w kroku 2. Aplikacja zostanie uruchomiona pomyślnie, ponieważ Instalator pakiet redystrybucyjny Visual C++ jest uwzględniony w samorozpakowujący się plik instalacyjny.

      > [!IMPORTANT]
      > Aby określić, która wersja środowiska uruchomieniowego jest zainstalowana, Instalator sprawdza \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes klucza rejestru\\[platforma]. Jeśli aktualnie zainstalowana wersja jest nowsza niż wersja, która Instalator podejmuje próbę instalacji, Instalator zwraca sukces bez konieczności instalowania starszej wersji i pozostawia dodatkowe wpis na stronie zainstalowanych programów w Panelu sterowania.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](../ide/deployment-examples.md)