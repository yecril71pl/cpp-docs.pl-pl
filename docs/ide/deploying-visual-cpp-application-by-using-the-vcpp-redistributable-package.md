---
title: "Wdrażanie aplikacji przy użyciu pakietu redystrybucyjnego (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52e3b048f896f0cfd532cb3000617756af2dca92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++
W tym artykule opisano sposób umożliwia wdrażanie aplikacji Visual C++ pakiet redystrybucyjny Visual C++.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Musi mieć tych składników, w tym przewodniku:  
  
-   Komputer, który ma zainstalowanego programu Visual Studio.  
  
-   Dodatkowy komputer, który nie ma bibliotek języka Visual C++.  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Aby użyć pakietu redystrybucyjnego Visual C++ do wdrożenia aplikacji  
  
1.  Tworzenie i kompilacja aplikacji MFC przez pierwsze trzy kroki w [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą instalacji projektu](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
2.  Utwórz plik, nadaj jej nazwę pliku setup.bat i Dodaj do niej następujące polecenia. Zmień `MyMFCApplication` nazwę projektu.  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  Utwórz samowyodrębniający się plik Instalatora:  
  
    1.  W wierszu polecenia lub w **Uruchom** okna, uruchom iexpress.exe.  
  
    2.  Wybierz **Utwórz nowy plik dyrektywy wyodrębniania samoobsługowego** , a następnie wybierz **dalej** przycisku.  
  
    3.  Wybierz **Wyodrębnij pliki i uruchom polecenie instalacji** , a następnie wybierz **dalej**.  
  
    4.  W polu tekstowym wprowadź nazwę aplikacji MFC, a następnie wybierz pozycję **dalej**.  
  
    5.  Na **monit o potwierdzenie** wybierz pozycję **wierszu nr** , a następnie wybierz **dalej**.  
  
    6.  Na **umowę licencyjną** wybierz pozycję **nie wyświetlaj licencji** , a następnie wybierz **dalej**.  
  
    7.  Na **umieszczone pliki** strony, Dodaj następujące pliki, a następnie wybierz pozycję **dalej**.  
  
        -   Aplikacji MFC (pliku .exe).  
  
        -   VCRedist_x86.exe. Ten plik znajduje się w \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.  
  
        -   Plik pliku setup.bat, który został utworzony w poprzednim kroku.  
  
    8.  Na **Zainstaluj Program do uruchomienia** strony w **Zainstaluj Program** polu tekstowym, wpisz następujące polecenie w wierszu, a następnie wybierz pozycję **dalej**.  
  
         **cmd.exe /c "pliku setup.bat"**  
  
    9. Na **okna Pokaż** wybierz pozycję **domyślne** , a następnie wybierz **dalej**.  
  
    10. Na **Zakończono komunikat** wybierz pozycję **żaden komunikat** , a następnie wybierz **dalej**.  
  
    11. Na **nazwę pakietu i opcje** wprowadź nazwę samorozpakowujący się plik Instalatora, wybierz pozycję **przechowywania plików przy użyciu długie nazwy plików w pakiecie** opcji, a następnie wybierz pozycję **dalej**. Na końcu nazwy pliku musi być Setup.exe—for przykład MyMFCApplicationSetup.exe.  
  
    12. Na **skonfigurować ponowne uruchomienie** wybierz pozycję **bez ponownego uruchamiania** , a następnie wybierz **dalej**.  
  
    13. Na **zapisać dyrektywy wyodrębniania samoobsługowego** wybierz pozycję **pliku Zapisz samoobsługowego wyodrębniania — dyrektywa (Mniejszyć)** , a następnie wybierz **dalej**.  
  
    14. Na **Utwórz pakiet** wybierz pozycję **dalej**.  
  
4.  Przetestuj samowyodrębniający się plik Instalatora na innym komputerze, który nie ma bibliotek języka Visual C++:  
  
    1.  Na innym komputerze Pobierz kopię pliku konfiguracji, a następnie zainstaluj go przez uruchomienie jej i następujące kroki, które zawiera.  
  
    2.  Uruchom aplikację MFC.  
  
         Samorozpakowujący się plik Instalatora instaluje aplikacji MFC, która znajduje się w folderze, który określono w kroku 2. Aplikacja zostanie wykonane pomyślnie, ponieważ znajduje się Instalator pakiet redystrybucyjny Visual C++ w samowyodrębniający się plik Instalatora.  
  
        > [!IMPORTANT]
        >  Aby określić, która wersja środowiska uruchomieniowego jest zainstalowana, Instalator sprawdza \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes klucza rejestru\\[platforma]. Jeśli aktualnie zainstalowana wersja jest nowsza niż wersja, która próbuje zainstalować Instalator, Instalator zwraca sukces bez instalowania starszej wersji i pozostawia dodatkowy zapis na stronie zainstalowanych programów w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady wdrożeń](../ide/deployment-examples.md)