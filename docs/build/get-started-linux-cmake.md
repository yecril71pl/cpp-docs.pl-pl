---
title: Tworzenie międzyplatformowych projektów w języku C++ w programie Visual Studio
description: Sposób konfigurowania, kompilowania i debugowania projektu typu open source CMake języka C++ w programie Visual Studio, który jest przeznaczony dla systemów Linux i Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328742"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Samouczek: Tworzenie projektów dla wielu platform C++ w programie Visual Studio

Programowanie Visual Studio C i C++ nie jest już przeznaczone tylko dla systemu Windows. W tym samouczku pokazano, jak używać programu Visual Studio do tworzenia aplikacji międzyplatformowych w języku C++ w systemach Windows i Linux. Jest on oparty na CMake, więc nie trzeba tworzyć ani generować projektów programu Visual Studio. Po otwarciu folderu zawierającego plik CMakeLists. txt program Visual Studio automatycznie konfiguruje ustawienia funkcji IntelliSense i kompilacji. Możesz szybko rozpocząć edytowanie, kompilowanie i debugowanie kodu lokalnie w systemie Windows. Następnie Zmień konfigurację tak, aby była taka sama w systemie Linux, a wszystko to w programie Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Klonowanie projektu CMake Open Source z usługi GitHub
> * Otwórz projekt w programie Visual Studio
> * Kompiluj i Debuguj obiekt docelowy wykonywalny w systemie Windows
> * Dodawanie połączenia z maszyną z systemem Linux
> * Kompiluj i Debuguj ten sam element docelowy w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

* Konfigurowanie programu Visual Studio na potrzeby programowania w języku C++ dla wielu platform
  * Najpierw [Zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/) i wybierz **Programowanie aplikacji klasycznych w języku c++** i **Linux przy użyciu obciążeń języka c++**. Ta minimalna instalacja jest tylko 3 GB. W zależności od szybkości pobierania instalacja nie powinna trwać dłużej niż 10 minut.

* Konfigurowanie maszyny z systemem Linux na potrzeby programowania w języku C++ dla wielu platform
  * Program Visual Studio nie wymaga żadnej konkretnej dystrybucji systemu Linux. System operacyjny może działać na komputerze fizycznym, na maszynie wirtualnej lub w chmurze. Można również użyć podsystemu Windows dla systemu Linux (WSL). Jednak w tym samouczku jest wymagane środowisko graficzne. WSL nie jest zalecana w tym miejscu, ponieważ jest zaprojektowana głównie dla operacji wiersza polecenia.
  * Program Visual Studio wymaga tych narzędzi na komputerze z systemem Linux: kompilatory C++, GDB, SSH, rsync, ninja i zip. W systemach opartych na systemie Debian można użyć tego polecenia, aby zainstalować te zależności:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Program Visual Studio wymaga najnowszej wersji programu CMake na komputerze z systemem Linux z włączonym trybem serwera (co najmniej 3,8). Firma Microsoft tworzy uniwersalną kompilację CMake, którą można zainstalować na dowolnym komputerze z systemem Linux. Zalecamy użycie tej kompilacji, aby upewnić się, że masz najnowsze funkcje. Pliki binarne CMake można pobrać z [rozwidlenia firmy Microsoft repozytorium CMAKE](https://github.com/Microsoft/CMake/releases) w witrynie GitHub. Przejdź do tej strony i Pobierz wersję zgodną z architekturą systemu na komputerze z systemem Linux, a następnie oznacz ją jako plik wykonywalny:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Opcje uruchamiania skryptu można znaleźć w `-–help`temacie. Zalecamy użycie `–prefix` opcji w celu określenia instalacji w ścieżce **/usr** , ponieważ **/usr/bin** jest domyślną lokalizacją, w której program Visual Studio szuka CMAKE. Poniższy przykład przedstawia skrypt z systemem Linux x86_64. Zmień go zgodnie z potrzebami, jeśli używasz innej platformy docelowej.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Narzędzie git dla systemu Windows zainstalowane na komputerze z systemem Windows.
* Konto usługi GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonowanie projektu CMake Open Source z usługi GitHub

W tym samouczku jest wykorzystywany punktowy zestaw SDK w serwisie GitHub. Zapewnia wykrywanie kolizji i symulacje fizyki dla wielu aplikacji. Zestaw SDK zawiera przykładowe programy wykonywalne, które kompilują i uruchamiają bez konieczności pisania dodatkowego kodu. Ten samouczek nie modyfikuje żadnego kodu źródłowego ani skryptów kompilacji. Aby rozpocząć, Sklonuj repozytorium *bullet3* z usługi GitHub na komputerze, na którym zainstalowano program Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. W menu głównym programu Visual Studio wybierz pozycję **plik > otwórz > CMAKE**. Przejdź do pliku CMakeLists. txt w folderze głównym repozytorium bullet3, które właśnie pobrałeś.

    ![Menu programu Visual Studio dla plików > Otwórz > CMake](media/cmake-open-cmake.png)

    Po otwarciu folderu struktura folderów zostanie wyświetlona w **Eksplorator rozwiązań**.

    ![Widok folderu programu Visual Studio Eksplorator rozwiązań](media/cmake-bullet3-solution-explorer.png)

    Ten widok przedstawia dokładnie zawartość dysku, a nie Widok logiczny lub przefiltrowany. Domyślnie nie są wyświetlane ukryte pliki.

1. Wybierz przycisk **Pokaż wszystkie pliki** , aby wyświetlić wszystkie pliki w folderze.

    ![Przycisk Pokaż wszystkie pliki w programie Visual Studio Eksplorator rozwiązań](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Przełącz do widoku elementów docelowych

Po otwarciu folderu, który używa CMake, program Visual Studio automatycznie generuje pamięć podręczną CMake. Ta operacja może potrwać kilka minut, w zależności od wielkości projektu.

1. W **okno dane wyjściowe**wybierz pozycję **Pokaż dane wyjściowe z** , a następnie wybierz pozycję **CMAKE** , aby monitorować stan procesu generowania pamięci podręcznej. Po zakończeniu operacji zostanie wyświetlony komunikat "Ekstrakcja docelowa informacja została zakończona".

   ![Okno danych wyjściowych programu Visual Studio pokazujące dane wyjściowe z CMake](media/cmake-bullet3-output-window.png)

   Po zakończeniu tej operacji funkcja IntelliSense jest skonfigurowana. Można skompilować projekt i debugować aplikację. Program Visual Studio wyświetla teraz logiczny widok rozwiązania na podstawie obiektów docelowych określonych w plikach CMakeLists.

1. Użyj przycisku **rozwiązania i foldery** w **Eksplorator rozwiązań** , aby przełączyć się do widoku obiektów docelowych CMAKE.

   ![Przycisk rozwiązania i foldery w Eksplorator rozwiązań, aby pokazać widok elementów docelowych CMake](media/cmake-bullet3-show-targets.png)

   Oto jak wygląda ten widok dla zestawu SDK:

   ![Widok elementów docelowych Eksplorator rozwiązań CMake](media/cmake-bullet3-targets-view.png)

   Widok elementów docelowych zapewnia bardziej intuicyjny widok tego, co znajduje się w tej bazie źródłowej. Niektóre elementy docelowe mogą być widoczne dla bibliotek, a inne to pliki wykonywalne.

1. Rozwiń węzeł w widoku CMake targets, aby wyświetlić jego pliki kodu źródłowego, wszędzie tam, gdzie te pliki mogą znajdować się na dysku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Dodaj jawną konfigurację systemu Windows x64-Debug

Program Visual Studio tworzy domyślną konfigurację **x64-Debug** dla systemu Windows. Konfiguracje to sposób, w jaki program Visual Studio rozumie, który obiekt docelowy platformy ma być używany na potrzeby CMake. Konfiguracja domyślna nie jest reprezentowana na dysku. W przypadku jawnego dodawania konfiguracji program Visual Studio tworzy plik o nazwie *pliku cmakesettings. JSON*. Jest ona wypełniana ustawieniami dla wszystkich określonych konfiguracji.

1. Dodaj nową konfigurację. Otwórz listę rozwijaną **Konfiguracja** na pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami**.

   ![Lista rozwijana zarządzania konfiguracją](media/cmake-bullet3-manage-configurations.png)

   Zostanie otwarty [Edytor ustawień CMAKE](customize-cmake-settings.md) . Zaznacz zielony znak plus po lewej stronie edytora, aby dodać nową konfigurację. Zostanie wyświetlone okno dialogowe **Dodawanie konfiguracji do pliku cmakesettings** .

   ![Dodawanie konfiguracji do okna dialogowego pliku cmakesettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   W tym oknie dialogowym są wyświetlane wszystkie konfiguracje dołączone do programu Visual Studio oraz wszystkie niestandardowe konfiguracje, które tworzysz. Jeśli chcesz kontynuować korzystanie z konfiguracji **x64-Debug** , należy ją dodać do pierwszej. Wybierz pozycję **x64-Debug**, a następnie wybierz przycisk **Wybierz** . Program Visual Studio tworzy plik pliku cmakesettings. JSON z konfiguracją dla programu **x64-Debug**i zapisuje go na dysku. Możesz użyć dowolnych nazw dla konfiguracji, zmieniając parametr name bezpośrednio w pliku pliku cmakesettings. JSON.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Ustawianie punktu przerwania, kompilowania i uruchamiania w systemie Windows

W tym kroku poprowadzimy do debugowania przykładowego programu, który demonstruje bibliotekę fizyki.
  
1. W **Eksplorator rozwiązań**wybierz pozycję AppBasicExampleGui i rozwiń ją.

1. Otwórz plik `BasicExample.cpp`.

1. Ustaw punkt przerwania, który zostanie trafiony po kliknięciu w działającej aplikacji. Zdarzenie kliknięcia jest obsługiwane w metodzie w ramach klasy pomocnika. Aby szybko uzyskać dostęp do tego:

   1. Wybierz `CommonRigidBodyBase` , z której `BasicExample` struktury pochodzi. Jest to około 30 wierszy.

   1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Przejdź do definicji**. Teraz jesteś w nagłówku CommonRigidBodyBase. h.

   1. W widoku przeglądarki powyżej źródła zobaczysz, że jesteś w `CommonRigidBodyBase`. Z prawej strony można wybrać członków do sprawdzenia. Otwórz listę rozwijaną i wybierz pozycję `mouseButtonCallback` , aby przejść do definicji tej funkcji w nagłówku.

      ![Pasek narzędzi listy członków programu Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umieść punkt przerwania w pierwszym wierszu w tej funkcji. Zostanie trafiony po kliknięciu przycisku myszy w oknie aplikacji, gdy zostanie on uruchomiony w debugerze programu Visual Studio.

1. Aby uruchomić aplikację, wybierz listę rozwijaną uruchamiania na pasku narzędzi. Jest to ten z zieloną ikoną odtwarzania "Wybierz element startowy". Z listy rozwijanej wybierz pozycję AppBasicExampleGui. exe. Nazwa pliku wykonywalnego jest teraz wyświetlana na przycisku uruchamiania:

   ![Lista rozwijana uruchamiania paska narzędzi programu Visual Studio dla pozycji Wybierz element startowy](media/cmake-bullet3-launch-button.png)

1. Wybierz przycisk Uruchom, aby skompilować aplikację i wymagane zależności, a następnie uruchom ją z dołączonym debugerem programu Visual Studio. Po kilku chwilach zostanie wyświetlona uruchomiona aplikacja:

   ![Debugowanie aplikacji systemu Windows w programie Visual Studio](media/cmake-bullet3-launched.png)

1. Przenieś mysz do okna aplikacji, a następnie kliknij przycisk, aby wyzwolić punkt przerwania. Punkt przerwania powoduje przywrócenie programu Visual Studio do pierwszego planu, a w edytorze widoczny jest wiersz, w którym wykonywanie zostało wstrzymane. Można sprawdzać zmienne aplikacji, obiekty, wątki i pamięć, a także interaktywnie krokowo. Wybierz pozycję **Kontynuuj** , aby umożliwić wznowienie działania aplikacji, a następnie zamknij ją normalnie. Lub zatrzymać wykonywanie w programie Visual Studio za pomocą przycisku Zatrzymaj.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Dodawanie konfiguracji systemu Linux i nawiązywanie połączenia z maszyną zdalną

1. Dodaj konfigurację systemu Linux. Kliknij prawym przyciskiem myszy plik pliku cmakesettings. JSON w widoku **Eksplorator rozwiązań** i wybierz polecenie **Dodaj konfigurację**. Zostanie wyświetlona ta sama okno dialogowe Dodaj konfigurację do pliku cmakesettings. Wybierz pozycję **Linux — Debuguj** ten czas, a następnie Zapisz plik pliku cmakesettings. JSON (Ctrl + s).

1. Na liście rozwijanej konfiguracja wybierz pozycję **Linux-Debug** .

   ![Lista rozwijana uruchamiania konfiguracji z opcjami debugowania x64 i Linux](media/cmake-bullet3-linux-configuration-item.png)

   Jeśli łączysz się z systemem Linux po raz pierwszy, zostanie wyświetlone okno dialogowe **łączenie z systemem zdalnym** .

   ![Okno dialogowe programu Visual Studio Connect z systemem zdalnym](media/cmake-bullet3-connection-manager.png)

   Jeśli połączenie zdalne zostało już dodane, możesz otworzyć to okno, przechodząc do **opcji narzędzia > opcje > Międzyplatformowy > Menedżer połączeń**.

1. Podaj [Informacje o połączeniu z maszyną z systemem Linux](/cpp/linux/connect-to-your-remote-linux-computer) i wybierz pozycję **Połącz**. Program Visual Studio dodaje tę maszynę do pliku cmakesettings. JSON jako domyślne połączenie dla **systemu Linux-Debug**. Pobiera również nagłówki z komputera zdalnego, dzięki czemu można uzyskać [IntelliSense dla tego połączenia zdalnego](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Następnie program Visual Studio wysyła pliki do maszyny zdalnej i generuje pamięć podręczną CMake w systemie zdalnym. Te kroki mogą zająć trochę czasu, w zależności od szybkości sieci i możliwości komputera zdalnego. Wiadomo, że zostanie ona ukończona, gdy komunikat "zakończenie wyodrębniania informacji Target" zostanie wyświetlony w oknie danych wyjściowych CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Ustawianie punktu przerwania, kompilowania i uruchamiania w systemie Linux

Ponieważ jest to aplikacja klasyczna, należy podać dodatkowe informacje konfiguracyjne dla konfiguracji debugowania.

1. W widoku obiekty docelowe CMake kliknij prawym przyciskiem myszy pozycję AppBasicExampleGui i wybierz polecenie **Debuguj i Uruchom ustawienia** , aby otworzyć plik Launch. vs. JSON znajdujący się w folderze Hidden **. vs** . Ten plik jest lokalny dla środowiska deweloperskiego. Możesz przenieść go do katalogu głównego projektu, jeśli chcesz go zaewidencjonować i zapisać z zespołem. W tym pliku została dodana konfiguracja AppBasicExampleGui. Te ustawienia domyślne działają w większości przypadków, ale nie w tym miejscu. Ponieważ jest to aplikacja klasyczna, należy podać dodatkowe informacje niezbędne do uruchomienia programu, aby można było go zobaczyć na komputerze z systemem Linux.

1. Aby znaleźć wartość zmiennej `DISPLAY` środowiskowej na komputerze z systemem Linux, uruchom następujące polecenie:

   ```cmd
   echo $DISPLAY
   ```

   W konfiguracji dla AppBasicExampleGui istnieje tablica parametrów "pipeArgs". Zawiera wiersz: "$ {debuggerCommand}". Jest to polecenie uruchamiające GDB na maszynie zdalnej. Program Visual Studio musi wyeksportować ekran do tego kontekstu przed uruchomieniem tego polecenia. Na przykład, jeśli wartość ekranu jest `:1`równa, należy zmodyfikować ten wiersz w następujący sposób:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Uruchamianie i debugowanie aplikacji. Otwórz listę rozwijaną **Wybierz element startowy** na pasku narzędzi i wybierz pozycję **AppBasicExampleGui**. Następnie wybierz zieloną ikonę odtwarzania na pasku narzędzi lub naciśnij klawisz **F5**. Aplikacja i jej zależności są tworzone na zdalnym komputerze z systemem Linux, a następnie uruchamiane z dołączonym debugerem programu Visual Studio. Na komputerze zdalnym z systemem Linux zostanie wyświetlone okno aplikacji.

1. Przenieś mysz do okna aplikacji, a następnie kliknij przycisk. Punkt przerwania jest trafień. Wstrzymanie wykonywania programu, program Visual Studio przechodzi do pierwszego planu i zobaczysz punkt przerwania. W programie Visual Studio należy również wyświetlić okno konsoli systemu Linux. Okno zawiera dane wyjściowe ze zdalnego komputera z systemem Linux, a także akceptuje dane wejściowe `stdin`. Podobnie jak w przypadku dowolnego okna programu Visual Studio, możesz go zadokować, gdzie wolisz go zobaczyć. Jego pozycja jest utrwalana w przyszłych sesjach.

   ![Okno konsoli programu Visual Studio Linux](media/cmake-bullet3-linux-console.png)

1. Możesz sprawdzić zmienne aplikacji, obiekty, wątki, pamięć i krokowo za pośrednictwem kodu przy użyciu programu Visual Studio. Jednak ten czas wykonujesz wszystko na zdalnym komputerze z systemem Linux, a nie w lokalnym środowisku systemu Windows. Możesz wybrać pozycję **Kontynuuj** , aby wznowić działanie aplikacji i zakończyć normalne działanie. Możesz też wybrać przycisk Zatrzymaj, tak jak w przypadku lokalnego wykonania.

1. Sprawdź okno stosu wywołań i Wyświetl wywołania do `x11OpenGLWindow` programu, ponieważ program Visual Studio uruchomił aplikację w systemie Linux.

   ![Okno stosu wywołań przedstawiające stos wywołań systemu Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Podsumowanie

W tym samouczku Sklonowano bazę kodu bezpośrednio z usługi GitHub. Skompilowane, wykonane i debugowane w systemie Windows bez modyfikacji. Następnie użyto tej samej bazy kodu z drobnymi zmianami konfiguracji, aby kompilować, uruchamiać i debugować na zdalnym komputerze z systemem Linux.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o konfigurowaniu i debugowaniu projektów CMake w programie Visual Studio:

> [!div class="nextstepaction"]
> [CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Dostosowywanie ustawień kompilacji narzędzia CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)
>
