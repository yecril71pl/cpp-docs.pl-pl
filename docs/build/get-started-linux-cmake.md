---
title: Tworzenie C++ projektów dla wielu platform w programie Visual Studio
description: W tym samouczku przedstawiono sposób konfigurowania, kompilowania i debugowania projektu C++ typu open source CMAKE w programie Visual Studio, który jest przeznaczony dla systemów Linux i Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: cd01d5e389bda46fbb05d297ece8e68ef2265725
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960727"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Samouczek: Tworzenie C++ projektów dla wielu platform w programie Visual Studio 

Program Visual Studio C C++ i programowanie nie tylko dla systemu Windows. W tym samouczku pokazano, jak używać programu C++ Visual Studio do tworzenia aplikacji międzyplatformowych w oparciu o CMAKE bez konieczności tworzenia lub generowania projektów programu Visual Studio. Po otwarciu folderu zawierającego plik CMakeLists. txt program Visual Studio automatycznie konfiguruje ustawienia funkcji IntelliSense i kompilacji. Możesz szybko edytować, kompilować i debugować swój kod lokalnie w systemie Windows, a następnie zmienić konfigurację tak, aby była taka sama w systemie Linux, a wszystko to w programie Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Klonowanie projektu CMake Open Source z usługi GitHub
> * Otwórz projekt w programie Visual Studio 
> * Kompiluj i Debuguj obiekt docelowy wykonywalny w systemie Windows
> * Dodawanie połączenia z maszyną z systemem Linux
> * Kompiluj i Debuguj ten sam element docelowy w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

- Konfigurowanie programu Visual Studio do tworzenia aplikacji C++ międzyplatformowych
    - Najpierw musisz mieć [zainstalowany program Visual Studio](https://visualstudio.microsoft.com/vs/). Następnie upewnij się, że masz zainstalowane **aplikacje klasyczne C++**  i **opracowywanie systemu Linux C++ z zainstalowanymi obciążeniami** . Ta minimalna instalacja jest tylko 3 GB, w zależności od instalacji szybkości pobierania nie może trwać więcej niż 10 minut.
- Konfigurowanie maszyny z systemem Linux na potrzeby tworzenia C++ aplikacji na wiele platform
    - Program Visual Studio nie wymaga żadnej konkretnej dystrybucji systemu Linux. System operacyjny może działać na komputerze fizycznym, w chmurze lub w podsystemie Windows dla systemu Linux (WSL). Jednak dla tego samouczka jest wymagane środowisko graficzne; w związku z tym WSL nie jest zalecany, ponieważ jest przeznaczony głównie do operacji wiersza polecenia.
    - Narzędzia wymagane przez program Visual Studio na komputerze z systemem Linux to C++ : COMPILERS, GDB, SSH, rsync i zip. W systemach opartych na systemie Debian można zainstalować te zależności w następujący sposób.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb rsync zip
    ```
    - Program Visual Studio wymaga, aby na komputerze z systemem Linux była zainstalowana najnowsza wersja programu CMake z włączonym trybem serwera (co najmniej 3,8). Firma Microsoft tworzy uniwersalną kompilację CMake, którą można zainstalować na dowolnym komputerze z systemem Linux. Zalecamy użycie tej kompilacji, aby upewnić się, że masz najnowsze funkcje. Pliki binarne CMake można pobrać z [rozwidlenia firmy Microsoft repozytorium CMAKE](https://github.com/Microsoft/CMake/releases) w witrynie GitHub. Przejdź do tej strony i Pobierz wersję zgodną z architekturą systemu na komputerze z systemem Linux, a następnie oznacz ją jako plik wykonywalny:
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Możesz wyświetlić opcje uruchamiania skryptu z `-–help`. Zalecamy użycie opcji `–prefix` w celu określenia instalacji w ścieżce **/usr/local** , ponieważ jest to domyślna lokalizacja, w której program Visual Studio szuka CMAKE. Poniższy przykład przedstawia skrypt linux-x86_64. Zmień to w razie konieczności, jeśli używasz innej platformy docelowej. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Narzędzie git dla systemu Windows zainstalowane na komputerze z systemem Windows.
- Konto usługi GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonowanie projektu CMake Open Source z usługi GitHub

W tym samouczku jest używany zestaw fizyka-The Bullet SDK w witrynie GitHub, który zapewnia wykrywanie kolizji i symulacje fizyki dla różnych różnych aplikacji. Zawiera przykładowe programy wykonywalne, które kompilują i uruchamiają bez konieczności pisania dodatkowego kodu. Ten samouczek nie modyfikuje żadnego kodu źródłowego ani skryptów kompilacji. Aby rozpocząć, Sklonuj repozytorium bullet3 z usługi GitHub na komputerze, na którym zainstalowano program Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. Z menu głównego programu Visual Studio wybierz kolejno pozycje **plik > otwórz > CMAKE** i przejdź do pliku CMakeLists. txt w katalogu głównym repozytorium bullet3, które zostało właśnie pobrane.

    ![Menu programu Visual Studio dla plików > Otwórz > CMake](media/cmake-open-cmake.png)

    Po otwarciu folderu struktura folderów będzie widoczna w **Eksplorator rozwiązań**.

    ![Widok folderu programu Visual Studio Eksplorator rozwiązań](media/cmake-bullet3-solution-explorer.png)

    Ten widok przedstawia dokładnie zawartość dysku, a nie Widok logiczny lub przefiltrowany. Domyślnie nie są wyświetlane ukryte pliki. 

2. Naciśnij przycisk **Pokaż wszystkie pliki** , aby wyświetlić wszystkie pliki w folderze.

    ![Przycisk Pokaż wszystkie pliki w programie Visual Studio Eksplorator rozwiązań](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Przełącz do widoku elementów docelowych

Po otwarciu folderu, który używa CMake, program Visual Studio automatycznie generuje pamięć podręczną CMake. Ta operacja może potrwać kilka minut, w zależności od wielkości projektu. 

1. W **okno dane wyjściowe**wybierz pozycję **Pokaż dane wyjściowe z** , a następnie wybierz pozycję **CMAKE** , aby monitorować stan procesu generowania pamięci podręcznej. Po zakończeniu operacji zostanie wyświetlony komunikat "Ekstrakcja docelowa informacja została zakończona".

    ![Okno danych wyjściowych programu Visual Studio pokazujące dane wyjściowe z CMake](media/cmake-bullet3-output-window.png)

    Po zakończeniu tej operacji technologia IntelliSense jest konfigurowana, projekt może być skompilowany i można debugować aplikację. Program Visual Studio może teraz zapewnić logiczny widok rozwiązania na podstawie obiektów docelowych określonych w plikach CMakeLists. 

2. Użyj przycisku **rozwiązania i foldery** w **Eksplorator rozwiązań** , aby przełączyć się do widoku obiektów docelowych CMAKE.

    ![Przycisk rozwiązania i foldery w Eksplorator rozwiązań, aby pokazać widok elementów docelowych CMake](media/cmake-bullet3-show-targets.png)

    Oto jak wygląda ten widok dla zestawu SDK:

    ![Widok elementów docelowych Eksplorator rozwiązań CMake](media/cmake-bullet3-targets-view.png)

    Widok elementów docelowych zapewnia bardziej intuicyjny widok tego, co znajduje się w tej bazie źródłowej. Niektóre elementy docelowe mogą być widoczne dla bibliotek, a inne to pliki wykonywalne. 

3. Rozwiń węzeł w widoku CMake targets, aby wyświetlić jego pliki kodu źródłowego, wszędzie tam, gdzie te pliki mogą znajdować się na dysku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Dodaj jawną konfigurację systemu Windows x64-Debug

Program Visual Studio tworzy domyślną konfigurację **x64-Debug** dla systemu Windows. Konfiguracje to sposób, w jaki program Visual Studio rozumie, który obiekt docelowy platformy ma być używany na potrzeby CMake. Konfiguracja domyślna nie jest reprezentowana na dysku. W przypadku jawnego dodawania konfiguracji program Visual Studio tworzy plik o nazwie pliku cmakesettings. JSON, który jest wypełniany ustawieniami dla wszystkich określonych konfiguracji. 

1. Aby dodać nową konfigurację, kliknij listę rozwijaną konfiguracja na pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami...**

    ![Lista rozwijana zarządzania konfiguracją](media/cmake-bullet3-manage-configurations.png)

    Spowoduje to otwarcie [edytora ustawień CMAKE](customize-cmake-settings.md). Zaznacz zielony znak plus po lewej stronie edytora, aby dodać nową konfigurację. Zostanie wyświetlone okno dialogowe **Dodawanie konfiguracji do pliku cmakesettings** .

    ![Dodawanie konfiguracji do okna dialogowego pliku cmakesettings](media/cmake-bullet3-add-configuration-x64-debug.png)

    To okno dialogowe zawiera wszystkie konfiguracje, które są dołączone do programu Visual Studio, a także wszelkie konfiguracje niestandardowe, które można utworzyć. Jeśli chcesz kontynuować korzystanie z konfiguracji **x64-Debug** , należy ją dodać do pierwszej. Wybierz opcję **x64-Debug** i kliknij przycisk **Wybierz**. Spowoduje to utworzenie pliku pliku cmakesettings. JSON z konfiguracją dla programu **x64-Debug** i zapisanie konfiguracji na dysku. Możesz użyć dowolnych nazw dla konfiguracji, zmieniając parametr name bezpośrednio w pliku pliku cmakesettings. JSON.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Ustawianie punktu przerwania, kompilowania i uruchamiania w systemie Windows 

W tym kroku poprowadzimy do debugowania przykładowego programu, który demonstruje bibliotekę fizyki.
  
1. W **Eksplorator rozwiązań**wybierz pozycję AppBasicExampleGui i rozwiń ją. 
1. Otwórz plik `BasicExample.cpp`. 
1. Ustaw punkt przerwania, który zostanie trafiony po kliknięciu w działającej aplikacji. Zdarzenie kliknięcia jest obsługiwane w metodzie w ramach klasy pomocnika. Aby szybko uzyskać dostęp do tego:

    1. Wybierz `CommonRigidBodyBase`, że struktura `BasicExample` jest pochodną od wiersza 30.
    1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Przejdź do definicji**. Jesteś teraz w nagłówku CommonRigidBodyBase. h. 
    1. W widoku przeglądarki powyżej, Twoje źródło powinno zobaczyć, że jesteś w `CommonRigidBodyBase`. Z prawej strony można wybrać członków do sprawdzenia. Kliknij listę rozwijaną i wybierz pozycję `mouseButtonCallback`, aby przejść do definicji tej funkcji w nagłówku.

        ![Pasek narzędzi listy członków programu Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umieść punkt przerwania w pierwszym wierszu w tej funkcji. Ten element zostanie trafiony po kliknięciu przycisku myszy w oknie aplikacji, gdy zostanie on uruchomiony w debugerze programu Visual Studio.

1. Aby uruchomić aplikację, wybierz listę rozwijaną uruchamiania z ikoną odtwarzania "Wybierz element startowy" na pasku narzędzi. Z listy rozwijanej wybierz pozycję AppBasicExampleGui. exe. Nazwa pliku wykonywalnego jest teraz wyświetlana na przycisku uruchamiania:

    ![Lista rozwijana uruchamiania paska narzędzi programu Visual Studio dla pozycji Wybierz element startowy](media/cmake-bullet3-launch-button.png)

5.  Naciśnij przycisk Uruchom, aby skompilować aplikację i niezbędne zależności, a następnie uruchom ją z dołączonym debugerem programu Visual Studio. Po kilku chwilach zostanie wyświetlona uruchomiona aplikacja:

    ![Debugowanie aplikacji systemu Windows w programie Visual Studio](media/cmake-bullet3-launched.png)

6. Przenieś mysz do okna aplikacji, a następnie kliknij przycisk, aby wyzwolić punkt przerwania. Spowoduje to przywrócenie programu Visual Studio do pierwszego planu przy użyciu edytora pokazującego wiersz, w którym wykonywanie zostało wstrzymane. Będzie można sprawdzić zmienne aplikacji, obiekty, wątki i pamięć. Możesz przejść przez kod interaktywnie. Możesz kliknąć pozycję **Kontynuuj** , aby umożliwić wznowienie działania aplikacji i zamknąć ją normalnie lub przerwać wykonywanie w programie Visual Studio przy użyciu przycisku Zatrzymaj.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Dodawanie konfiguracji systemu Linux i nawiązywanie połączenia z maszyną zdalną

1. Teraz Dodaj konfigurację systemu Linux. Kliknij prawym przyciskiem myszy plik pliku cmakesettings. JSON w widoku **Eksplorator rozwiązań** i wybierz polecenie **Dodaj konfigurację**. Zostanie wyświetlona ta sama okno dialogowe Dodaj konfigurację do pliku cmakesettings. Wybierz pozycję **Linux — Debuguj** ten czas, a następnie Zapisz plik pliku cmakesettings. JSON (Ctrl + s). 
2. Teraz wybierz pozycję **Linux-Debug** na liście rozwijanej konfiguracja.

    ![Lista rozwijana uruchamiania konfiguracji z opcjami debugowania x64 i Linux](media/cmake-bullet3-linux-configuration-item.png)

    Jeśli łączysz się z systemem Linux po raz pierwszy, zostanie wyświetlone okno dialogowe **łączenie z systemem zdalnym** .

    ![Okno dialogowe programu Visual Studio Connect z systemem zdalnym](media/cmake-bullet3-connection-manager.png)

    Jeśli połączenie zdalne zostało już dodane, możesz otworzyć to okno, przechodząc do **opcji narzędzia > opcje > Międzyplatformowy > Menedżer połączeń**.
 
3. Podaj [informacje o połączeniu z maszyną z systemem Linux] (Connect-to-Remote-Linux-computer.md] i kliknij pozycję **Połącz**. Program Visual Studio dodaje tę maszynę do pliku cmakesettings. JSON jako domyślne połączenie dla **systemu Linux-Debug**. Spowoduje to również ściągnięcie nagłówków z komputera zdalnego, dzięki czemu uzyskasz funkcję [IntelliSense specyficzną dla tego połączenia zdalnego](https://docs.microsoft.com/en-us/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Teraz program Visual Studio wyśle pliki na maszynę zdalną i wygeneruje pamięć podręczną CMake w systemie zdalnym. Te kroki mogą zająć trochę czasu w zależności od szybkości sieci i możliwości komputera zdalnego. Wiadomo, że zostanie ona ukończona, gdy komunikat "zakończenie wyodrębniania informacji Target" pojawi się w oknie danych wyjściowych CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Ustawianie punktu przerwania, kompilowanie i uruchamianie w systemie Linux

Ponieważ jest to aplikacja klasyczna, należy podać dodatkowe informacje konfiguracyjne do konfiguracji debugowania. 

1. W widoku obiekty docelowe CMake kliknij prawym przyciskiem myszy pozycję AppBasicExampleGui i wybierz polecenie **Debuguj i Uruchom ustawienia** , aby otworzyć plik Launch. vs. JSON znajdujący się w folderze Hidden **. vs** . Ten plik jest lokalny dla środowiska deweloperskiego. Możesz przenieść go do katalogu głównego projektu, jeśli chcesz go zaewidencjonować i zapisać z zespołem. W tym pliku została dodana konfiguracja do AppBasicExampleGui. Te ustawienia domyślne działają w większości przypadków, ale ponieważ jest to aplikacja klasyczna, należy podać dodatkowe informacje niezbędne do uruchomienia programu w sposób, w jaki można go zobaczyć na naszej maszynie z systemem Linux. 
2. Musisz znać wartość zmiennej środowiskowej `DISPLAY` na komputerze z systemem Linux, Uruchom to polecenie, aby je pobrać.

    ```cmd
    echo $DISPLAY
    ```

    W konfiguracji dla AppBasicExampleGui istnieje tablica parametrów "pipeArgs". W tym miejscu istnieje wiersz "$ {debuggerCommand}". Jest to polecenie uruchamiające GDB na maszynie zdalnej. Program Visual Studio musi wyeksportować ekran do tego kontekstu przed uruchomieniem tego polecenia. Na przykład, jeśli wartość ekranu: 1, zmodyfikuj ten wiersz w następujący sposób:

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Teraz, aby uruchomić i debugować aplikację, wybierz listę rozwijaną **Wybierz element startowy** na pasku narzędzi i wybierz pozycję AppBasicExampleGui. Teraz naciśnij ten przycisk lub kliknij klawisz **F5**. Spowoduje to skompilowanie aplikacji i jej zależności na zdalnym komputerze z systemem Linux, a następnie uruchomienie jej z dołączonym debugerem programu Visual Studio. Na komputerze zdalnym z systemem Linux zostanie wyświetlone okno aplikacji.

4. Przenieś mysz do okna aplikacji, kliknij przycisk i zostanie trafiony punkt przerwania. Wstrzymanie wykonywania programu, program Visual Studio wraca do pierwszego planu i będzie znajdował się w punkcie przerwania. W programie Visual Studio należy również wyświetlić okno konsoli systemu Linux. To okno zawiera dane wyjściowe ze zdalnego komputera z systemem Linux, a także akceptuje dane wejściowe dla `stdin`. Podobnie jak w przypadku dowolnego okna programu Visual Studio, można je zadokować, gdy wolisz go zobaczyć, a jej położenie zostanie utrwalone w przyszłych sesjach.

    ![Okno konsoli programu Visual Studio Linux](media/cmake-bullet3-linux-console.png)

5. Możesz sprawdzić zmienne aplikacji, obiekty, wątki, pamięć i krokowo za pośrednictwem kodu przy użyciu programu Visual Studio. Jednak ten czas wykonujesz wszystko na zdalnym komputerze z systemem Linux, a nie w lokalnym środowisku systemu Windows. Możesz kliknąć pozycję **Kontynuuj** , aby pozwolić aplikacji na wznowienie i normalne działanie, lub nacisnąć przycisk Zatrzymaj, tak jak w przypadku lokalnego wykonania.

6. Sprawdź okno stosu wywołań i Wyświetl wywołania `x11OpenGLWindow`, ponieważ program Visual Studio uruchomił aplikację w systemie Linux.

    ![Okno stosu wywołań przedstawiające stos wywołań systemu Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Zdobyte informacje 

W tym samouczku przedstawiono bazę kodu sklonowaną bezpośrednio z usługi GitHub oraz skompilowaną, uruchamianą i debugowaną w systemie Windows bez żadnych modyfikacji. Ta baza kodu pochodzi z niewielkimi zmianami konfiguracji, została skompilowana, uruchomiona i debugowana na zdalnym komputerze z systemem Linux. 

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o konfigurowaniu i debugowaniu projektów CMake w programie Visual Studio:

> [!div class="nextstepaction"]
> [CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Dostosuj ustawienia kompilacji CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)
> 
