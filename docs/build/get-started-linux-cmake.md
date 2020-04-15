---
title: Tworzenie międzyplatformowych projektów w języku C++ w programie Visual Studio
description: Jak skonfigurować, skompilować i debugować CMake projektu CMake c++ w programie Visual Studio, który jest przeznaczony dla systemu Linux i Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328742"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Samouczek: Tworzenie projektów międzyplatformowych w programie Visual Studio w języku C++

Program Visual Studio C i C++ development nie jest już tylko dla systemu Windows. W tym samouczku pokazano, jak używać programu Visual Studio dla tworzenia wielu platform języka C++ w systemach Windows i Linux. Jest on oparty na CMake, więc nie trzeba tworzyć ani generować projektów programu Visual Studio. Po otwarciu folderu zawierającego plik CMakeLists.txt program Visual Studio automatycznie konfiguruje ustawienia intellisense i kompilacji. Możesz szybko rozpocząć edytowanie, tworzenie i debugowanie kodu lokalnie w systemie Windows. Następnie przełącz konfigurację, aby zrobić to samo w systemie Linux, wszystkie z poziomu programu Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * klonować projekt CMake open source z GitHub
> * otwieranie projektu w programie Visual Studio
> * tworzenie i debugowanie pliku docelowego w systemie Windows
> * dodawanie połączenia z komputerem z systemem Linux
> * tworzenie i debugowanie tego samego celu w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

* Konfigurowanie programu Visual Studio for Cross Platform C++ Development
  * Najpierw [zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/) i wybierz **program rozwoju pulpitu z programem C++** i **Linux z obciążeniami języka C++.** Ta minimalna instalacja to tylko 3 GB. W zależności od szybkości pobierania instalacja nie powinna trwać dłużej niż 10 minut.

* Konfigurowanie komputera z systemem Linux do programowania międzyplatformowego C++
  * Visual Studio nie wymaga żadnej określonej dystrybucji systemu Linux. System operacyjny może być uruchomiony na komputerze fizycznym, na maszynie wirtualnej lub w chmurze. Można również użyć podsystemu Windows dla systemu Linux (WSL). Jednak w tym samouczku wymagane jest środowisko graficzne. WSL nie jest zalecane w tym miejscu, ponieważ jest przeznaczony głównie do operacji wiersza polecenia.
  * Visual Studio wymaga tych narzędzi na komputerze z systemem Linux: kompilatory C++, gdb, ssh, rsync, ninja i zip. W systemach opartych na Debianie możesz użyć tego polecenia, aby zainstalować następujące zależności:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio wymaga najnowszej wersji CMake na komputerze z systemem Linux, który ma włączony tryb serwera (co najmniej 3.8). Microsoft produkuje uniwersalną kompilację CMake, którą można zainstalować na dowolnej dystrybucji Linuksa. Firma Microsoft zaleca użycie tej kompilacji, aby upewnić się, że masz najnowsze funkcje. Pliki binarne CMake można uzyskać z [rozwidlień microsoftu repozytorium CMake](https://github.com/Microsoft/CMake/releases) w usłudze GitHub. Przejdź do tej strony i pobierz wersję, która pasuje do architektury systemu na komputerze z systemem Linux, a następnie oznacz ją jako plik wykonywalny:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Możesz zobaczyć opcje uruchamiania skryptu za pomocą programu `-–help`. Zaleca się użycie `–prefix` opcji do określenia instalacji w **/usr** ścieżki, ponieważ **/usr/bin** jest domyślną lokalizacją, w której visual studio szuka CMake. W poniższym przykładzie przedstawiono skrypt x86_64 systemu Linux. Zmień ją w razie potrzeby, jeśli używasz innej platformy docelowej.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git dla systemu Windows zainstalowany na komputerze z systemem Windows.
* Konto usługi GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonowanie projektu CMake open source z gitHub

W tym samouczku użyto zestawu SDK fizyki bulleta w usłudze GitHub. Zapewnia wykrywanie kolizji i symulacje fizyki dla wielu zastosowań. Zestaw SDK zawiera przykładowe programy wykonywalne, które kompilują i uruchamiają bez konieczności pisania dodatkowego kodu. Ten samouczek nie modyfikuje żadnego kodu źródłowego ani skryptów kompilacji. Aby rozpocząć, sklonować repozytorium *bullet3* z gitHub na komputerze, na którym masz zainstalowany program Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. W menu głównym programu Visual Studio wybierz polecenie **Plik > Otwórz > CMake**. Przejdź do pliku CMakeLists.txt w katalogu głównym repozytorium bullet3, które właśnie pobrano.

    ![Menu programu Visual Studio dla > otwartych > CMake](media/cmake-open-cmake.png)

    Po otwarciu folderu struktura folderów staje się widoczna w **Eksploratorze rozwiązań**.

    ![Widok folderu Eksploratora rozwiązań programu Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Ten widok pokazuje dokładnie to, co znajduje się na dysku, a nie widok logiczny lub filtrowany. Domyślnie nie pokazuje ukrytych plików.

1. Wybierz przycisk **Pokaż wszystkie pliki,** aby wyświetlić wszystkie pliki w folderze.

    ![Przycisk Eksploratora rozwiązań programu Visual Studio Pokaż wszystkie pliki](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Przełączanie do widoku obiektów docelowych

Po otwarciu folderu, który używa CMake, Visual Studio automatycznie generuje cMake pamięci podręcznej. Ta operacja może potrwać kilka chwil, w zależności od rozmiaru projektu.

1. W **oknie dane wyjściowe**wybierz pozycję **Pokaż dane wyjściowe,** a następnie wybierz **pozycję CMake,** aby monitorować stan procesu generowania pamięci podręcznej. Po zakończeniu operacji jest na osłania "Target info extraction done".

   ![Okno dane wyjściowe programu Visual Studio z obrazem wyjściowym z programu CMake](media/cmake-bullet3-output-window.png)

   Po zakończeniu tej operacji intellisense jest skonfigurowany. Można utworzyć projekt i debugować aplikację. Visual Studio pokazuje teraz logiczny widok rozwiązania, na podstawie obiektów docelowych określonych w plikach CMakeLists.

1. Użyj przycisku **Rozwiązania i foldery** w **Eksploratorze rozwiązań,** aby przełączyć się do widoku CMake Targets.

   ![Przycisk Rozwiązania i foldery w Eksploratorze rozwiązań, aby wyświetlić widok CMake targets](media/cmake-bullet3-show-targets.png)

   Oto, jak ten widok wygląda dla SDK Bullet:

   ![Widok obiektów docelowych Eksploratora rozwiązań](media/cmake-bullet3-targets-view.png)

   Widok obiektów docelowych zapewnia bardziej intuicyjny widok tego, co znajduje się w tej bazie źródłowej. Widać, że niektóre obiekty docelowe są bibliotekami, a inne są plikami wykonywalnymi.

1. Rozwiń węzeł w widoku celów CMake, aby wyświetlić jego pliki kodu źródłowego, gdziekolwiek te pliki mogą znajdować się na dysku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Dodawanie jawnej konfiguracji systemu Windows x64-Debug

Program Visual Studio tworzy domyślną konfigurację **debugowania x64** dla systemu Windows. Konfiguracje są jak Visual Studio rozumie, jaki docelowej platformy będzie używany dla CMake. Domyślna konfiguracja nie jest reprezentowana na dysku. Podczas jawnego dodawania konfiguracji program Visual Studio tworzy plik o nazwie *CMakeSettings.json*. Jest wypełniona ustawieniami dla wszystkich konfiguracji, które określisz.

1. Dodaj nową konfigurację. Otwórz pozycję rozwijaną **Konfiguracja** na pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami**.

   ![Zarządzanie rozwijaną Konfiguracja](media/cmake-bullet3-manage-configurations.png)

   Zostanie otwarty [Edytor ustawień CMake.](customize-cmake-settings.md) Wybierz zielony znak plus po lewej stronie edytora, aby dodać nową konfigurację. Zostanie wyświetlone okno dialogowe **Dodaj konfigurację do CMakeSettings.**

   ![Okno dialogowe Dodawanie konfiguracji do cMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   W tym oknie dialogowym są wyświetlane wszystkie konfiguracje dołączone do programu Visual Studio oraz wszystkie utworzone konfiguracje niestandardowe. Jeśli chcesz nadal używać konfiguracji **x64-Debug,** to powinien być pierwszy dodać. Wybierz **x64-Debug**, a następnie wybierz przycisk **Wybierz.** Program Visual Studio tworzy plik CMakeSettings.json z konfiguracją **dla x64-Debug**i zapisuje go na dysku. Można użyć dowolnej nazwy dla konfiguracji, zmieniając parametr name bezpośrednio w CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Ustawianie punktu przerwania, kompilacji i uruchamiania w systemie Windows

W tym kroku będziemy debugować przykładowy program, który pokazuje bullet fizyki biblioteki.
  
1. W **Eksploratorze rozwiązań**wybierz appbasicexamplegui i rozwiń go.

1. Otwórz plik `BasicExample.cpp`.

1. Ustaw punkt przerwania, który zostanie trafiony po kliknięciu uruchomionej aplikacji. Zdarzenie click jest obsługiwane w metodzie w klasie pomocnika. Aby szybko się tam dostać:

   1. Wybierz, `CommonRigidBodyBase` z `BasicExample` których pochodzi struktura. Jest wokół linii 30.

   1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Przejdź do definicji**. Teraz jesteś w nagłówku CommonRigidBodyBase.h.

   1. W widoku przeglądarki nad źródłem powinieneś zobaczyć, `CommonRigidBodyBase`że jesteś w pliku . Po prawej stronie można wybrać członków do zbadania. Otwórz listy rozwijane `mouseButtonCallback` i wybierz, aby przejść do definicji tej funkcji w nagłówku.

      ![Pasek narzędzi listy elementów członkowskich programu Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umieść punkt przerwania w pierwszym wierszu w ramach tej funkcji. Zostanie trafiony po kliknięciu przycisku myszy w oknie aplikacji, po uruchomieniu w debugerze programu Visual Studio.

1. Aby uruchomić aplikację, wybierz pozycję rozwijaną uruchamiania na pasku narzędzi. Jest to ten z zieloną ikoną odtwarzania, która mówi "Wybierz element startowy". Z listy rozwijanej wybierz appbasicexampleGui.exe. Nazwa wykonywalna jest teraz wyświetlana na przycisku uruchamiania:

   ![Z listy rozwijanej uruchamiania paska narzędzi programu Visual Studio dla wybranych elementów startowych](media/cmake-bullet3-launch-button.png)

1. Wybierz przycisk uruchamiania, aby utworzyć aplikację i niezbędne zależności, a następnie uruchom ją z dołączonym debugerem programu Visual Studio. Po kilku chwilach pojawia się uruchomiona aplikacja:

   ![Debugowanie aplikacji systemu Windows w programie Visual Studio](media/cmake-bullet3-launched.png)

1. Przenieś mysz do okna aplikacji, a następnie kliknij przycisk, aby wyzwolić punkt przerwania. Punkt przerwania przywraca program Visual Studio na pierwszy plan, a edytor pokazuje wiersz, w którym wstrzymane jest wykonywanie. Można sprawdzić zmienne aplikacji, obiekty, wątki i pamięci lub krok po kroku kodu interaktywnie. Wybierz pozycję **Kontynuuj,** aby umożliwić wznowienie aplikacji, a następnie zamknij ją normalnie. Lub wstrzymać wykonywanie w programie Visual Studio przy użyciu przycisku zatrzymania.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Dodawanie konfiguracji systemu Linux i łączenie się z komputerem zdalnym

1. Dodaj konfigurację linuksa. Kliknij prawym przyciskiem myszy plik CMakeSettings.json w widoku **Eksploratora rozwiązań** i wybierz polecenie **Dodaj konfigurację**. Zobaczysz to samo okno dialogowe Dodaj konfigurację do CMakeSettings jak poprzednio. Wybierz **Linux-Debug** tym razem, a następnie zapisz plik CMakeSettings.json (ctrl + s).

1. Wybierz **Linux-Debug** w konfiguracji listy rozwijanej.

   ![Uruchom menu rozwijane konfiguracji z opcjami X64-Debug i Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Jeśli po raz pierwszy łączysz się z systemem Linux, zostanie wyświetlone okno dialogowe **Połącz z systemem zdalnym.**

   ![Okno dialogowe Połącz z systemem zdalnym w programie Visual Studio](media/cmake-bullet3-connection-manager.png)

   Jeśli dodano już połączenie zdalne, możesz otworzyć to okno, przechodząc do **pozycji Narzędzia > Opcje > Menedżer połączenia międzyplatformowe >**.

1. Podaj [informacje o połączeniu z komputerem z systemem Linux](/cpp/linux/connect-to-your-remote-linux-computer) i wybierz pozycję **Połącz**. Visual Studio dodaje, że komputer co do CMakeSettings.json jako domyślne połączenie dla **Linuksa-Debug**. To również ściąga nagłówki z komputera zdalnego, dzięki czemu można uzyskać [IntelliSense specyficzne dla tego połączenia zdalnego](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Następnie program Visual Studio wysyła pliki do komputera zdalnego i generuje pamięć podręczną CMake w systemie zdalnym. Te kroki mogą zająć trochę czasu, w zależności od szybkości sieci i mocy komputera zdalnego. Będziesz wiedzieć, że jest kompletny, gdy komunikat "Target info extraction done" pojawia się w oknie wyjściowym CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Ustawianie punktu przerwania, kompilacji i uruchamiania w systemie Linux

Ponieważ jest to aplikacja klasyczna, należy podać pewne dodatkowe informacje o konfiguracji do konfiguracji debugowania.

1. W widoku CMake cele kliknij prawym przyciskiem myszy AppBasicExampleGui i wybierz polecenie **Debugowanie i uruchom ustawienia,** aby otworzyć plik launch.vs.json znajdujący się w ukrytym podfolderze **.vs.** Ten plik jest lokalny dla środowiska programistycznego. Możesz przenieść go do katalogu głównego projektu, jeśli chcesz go zaewidencjonować i zapisać wraz ze swoim zespołem. W tym pliku dodano konfigurację dla AppBasicExampleGui. Te ustawienia domyślne działają w większości przypadków, ale nie tutaj. Ponieważ jest to aplikacja komputerowa, musisz podać dodatkowe informacje, aby uruchomić program, aby można go było zobaczyć na komputerze z systemem Linux.

1. Aby znaleźć wartość zmiennej `DISPLAY` środowiskowej na komputerze z systemem Linux, uruchom następujące polecenie:

   ```cmd
   echo $DISPLAY
   ```

   W konfiguracji dla AppBasicExampleGui istnieje tablica parametrów "pipeArgs". Zawiera wiersz: "${debuggerCommand}". Jest to polecenie, które uruchamia gdb na komputerze zdalnym. Visual Studio musi wyeksportować wyświetlanie w tym kontekście przed jego uruchomieniu. Na przykład, jeśli wartością `:1`ekranu jest , zmodyfikuj tę linię w następujący sposób:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Uruchom i debuguj aplikację. Otwórz pozycję Rozwijaną **Wybierz element startowy** na pasku narzędzi i wybierz pozycję **AppBasicExampleGui**. Następnie wybierz zieloną ikonę odtwarzania na pasku narzędzi lub naciśnij **klawisz F5**. Aplikacja i jej zależności są zbudowane na zdalnym komputerze z systemem Linux, a następnie uruchamiane z dołączonym debugerem programu Visual Studio. Na zdalnym komputerze z systemem Linux powinno zostać wyświetlone okno aplikacji.

1. Przenieś mysz do okna aplikacji i kliknij przycisk. Punkt przerwania zostanie trafiony. Wstrzymanie wykonywania programu, Visual Studio wraca na pierwszy plan i zobaczysz punkt przerwania. W programie Visual Studio powinno być również widoczne okno konsoli systemu Linux. Okno zawiera dane wyjściowe ze zdalnego komputera z `stdin`systemem Linux, a także może akceptować dane wejściowe dla . Podobnie jak w każdym oknie programu Visual Studio, można zadokować go w dowolnym miejscu, w którym chcesz go zobaczyć. Jego pozycja utrzymuje się w kolejnych sesjach.

   ![Okno konsoli systemu Linux w programie Visual Studio](media/cmake-bullet3-linux-console.png)

1. Można sprawdzić zmienne aplikacji, obiekty, wątki, pamięci i krok po kroku za pomocą kodu interaktywnie za pomocą programu Visual Studio. Ale tym razem robisz to wszystko na zdalnym komputerze z systemem Linux zamiast lokalnego środowiska Windows. Można wybrać **Kontynuuj,** aby umożliwić działanie aplikacji i zakończyć normalnie lub można wybrać przycisk zatrzymania, podobnie jak w wykonaniu lokalnym.

1. Spójrz na okno Stos wywołań `x11OpenGLWindow` i wyświetl wywołania od programu Visual Studio uruchomił aplikację w systemie Linux.

   ![Okno Stos wywołań z układem wywoławym linuxowym](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Podsumowanie

W tym samouczku sklonowałeś bazę kodu bezpośrednio z usługi GitHub. Zostałeś zbudowany, uruchomiony i debugowany w systemie Windows bez modyfikacji. Następnie użyto tej samej bazy kodu, z niewielkimi zmianami konfiguracji, do tworzenia, uruchamiania i debugowania na zdalnym komputerze z systemem Linux.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o konfigurowaniu i debugowaniu projektów CMake w programie Visual Studio:

> [!div class="nextstepaction"]
> [CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Dostosowywanie ustawień kompilacji narzędzia CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CZrobe wstępnie zdefiniowane odwołanie do konfiguracji](cmake-predefined-configuration-reference.md)
>
