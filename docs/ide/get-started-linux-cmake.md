---
title: Tworzenie projektów dla wielu platform w języku C++ w programie Visual Studio
description: W tym samouczku przedstawiono sposób konfigurowania, kompilowania i debugowania projektu narzędzia CMake typu open source w języku C++ w programie Visual Studio, który jest przeznaczony dla systemu Linux i Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: 5802c3f3fc82de9c43f34b93910e5837424cdd0c
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566929"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Samouczek: Tworzenie projektów dla wielu platform w języku C++ w programie Visual Studio 

Tylko dla Windows nie jest już rozwoju Visual Studio C i C++. W tym samouczku pokazano, jak używać programu Visual Studio dla języka C++, Programowanie oparte na CMake, bez konieczności tworzenia i generowanie projektów programu Visual Studio wieloplatformowych. Po otwarciu folderu zawierającego plik CMakeLists.txt, Visual Studio konfiguruje ustawienia funkcji IntelliSense i kompilacja automatycznie. Można szybko edycji, tworzenia i debugowania kodu lokalnie na Windows, a następnie przełączyć konfigurację tak, aby zrobić to samo w systemie Linux z poziomu programu Visual Studio.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * klonowanie projektu narzędzia CMake typu open source z serwisu GitHub
> * Otwórz projekt w programie Visual Studio 
> * Twórz i Debuguj obiektu docelowego pliku wykonywalnego na Windows
> * Dodawanie połączenia do maszyny z systemem Linux
> * Twórz i Debuguj tej samej wartości docelowej w systemie Linux

## <a name="prerequisites"></a>Wymagania wstępne

- Konfigurowanie programu Visual Studio Wieloplatformowego programowania aplikacji C++
    - Najpierw musisz mieć [zainstalowanego programu Visual Studio](https://visualstudio.microsoft.com/vs/). Następnie upewnij się, że masz **programowanie aplikacji klasycznych w języku C++** i **programowanie dla systemu Linux z obciążeniami C++** zainstalowane. Tej minimalnej instalacji jest tylko 3 GB, w zależności od pobierania instalacji szybkość powinno to zająć wiele więcej niż 10 minut.
- Konfigurowanie maszyny z systemem Linux dla Wieloplatformowego programowania aplikacji C++
    - Program Visual Studio nie wymaga żadnych szczególnych dystrybucja systemu Linux. System operacyjny może być uruchomiony na komputerze fizycznym, na maszynie Wirtualnej, chmury lub podsystemu Windows dla systemu Linux (WSL). Jednak w tym samouczku pśrodowisku graficznym jest wymagana; w związku z tym WSL nie jest zalecane, ponieważ jest ono przeznaczone przede wszystkim dla operacji wiersza polecenia.
    - Dostępne są następujące narzędzia, które program Visual Studio wymaga na maszyny z systemem Linux: Kompilatory języka C++, GDB, ssh, a zip. Na systemów Debian można zainstalować te zależności w następujący sposób.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Program Visual Studio wymaga, że maszyny z systemem Linux ma najnowszą wersję narzędzia CMake, który został włączony tryb server (co najmniej 3.8). Firma Microsoft tworzy universal kompilacji cmake, który można zainstalować na dowolnym dystrybucja systemu Linux. Firma Microsoft zaleca, aby upewnić się, czy masz najnowsze funkcje przy użyciu tej kompilacji. Można uzyskać plików binarnych narzędzia CMake z [Microsoft rozwidlenia repozytorium narzędzia CMake](https://github.com/Microsoft/CMake/releases) w witrynie GitHub. Przejdź do tej strony i pobranie wersji, który pasuje do Twojej architektury systemu na maszynie z systemem Linux, a następnie oznacz ją jako plik wykonywalny:
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Zawiera opcje uruchamiania skryptu `-–help`. Firma Microsoft zaleca użycie `–prefix` opcję, aby określić, instalowanie **/usr/lokalnego** ścieżki ponieważ jest to domyślna lokalizacja, gdzie Visual Studio szuka narzędzia CMake. Poniższy przykład pokazuje skrypt x86_64 systemu Linux. Zmień, jeśli używasz innej docelowej platformy. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git dla systemu windows zainstalowaną na komputerze Windows.
- Konto usługi GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonowanie projektu narzędzia CMake typu open source z serwisu GitHub

W tym samouczku użyto zestawu SDK fizyki punktor w serwisie GitHub, co zapewnia wykrywanie kolizji i symulacje fizyki dla wielu różnych aplikacji. Zawiera przykładowe programy wykonywalne, które skompilować i uruchomić bez konieczności pisania dodatkowego kodu. W tym samouczku nie modyfikować kod źródłowy i tworzyć skrypty. Aby rozpocząć, sklonuj bullet3 repozytorium z repozytorium GitHub na maszynie, w którym masz zainstalowany program Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. Wybierz z menu głównego programu Visual Studio **Plik > Otwórz > CMake** i przejdź do pliku CMakeLists.txt w katalogu głównym repozytorium bullet3, który został pobrany.

    ![Visual Studio menu Plik > Otwórz > Narzędzia CMake](media/cmake-open-cmake.png)

    Zaraz po otwarciu folderu, będą widoczne w strukturze folderów **Eksploratora rozwiązań**.

    ![Widok folderu Eksploratora rozwiązań programu Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Ten widok przedstawia dokładnie co znajduje się na dysku, nie widok logiczny lub filtrowane. Domyślnie nie pokazuje ukryte pliki. 

2. Naciśnij klawisz **Pokaż wszystkie pliki** przycisk, aby wyświetlić wszystkie pliki w folderze.

    ![Visual Studio Explorer Pokaż wszystkie pliki rozwiązania przycisku](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Przełącz na widok elementów docelowych

Podczas otwierania folderu, który używa narzędzia CMake programu Visual Studio automatycznie generuje pamięci podręcznej narzędzia CMake. Ta operacja może potrwać kilka minut w zależności od wielkości projektu. 

1. W **okno danych wyjściowych**, wybierz opcję **Pokaż dane wyjściowe z** , a następnie wybierz **CMake** do monitorowania stanu procesu tworzenia pamięci podręcznej. Po zakończeniu operacji jest wyświetlany komunikat "Zakończono wyodrębnianie informacji docelowej".

    ![Wizualne okno danych wyjściowych Studio wyświetlanie danych wyjściowych z narzędzia CMake](media/cmake-bullet3-output-window.png)

    Po zakończeniu tej operacji, IntelliSense jest skonfigurowany, można utworzyć projektu i można debugować aplikację. Program Visual Studio umożliwia teraz widok logiczny rozwiązania na podstawie celów określona w plikach list narzędzia Cmake. 

2. Użyj **rozwiązania i foldery** znajdujący się w **Eksploratora rozwiązań** przełączyć na widok elementów docelowych narzędzia CMake.

    ![Przycisk rozwiązania i foldery w Eksploratorze rozwiązań, aby wyświetlić narzędzia CMake jest przeznaczony dla widoku](media/cmake-bullet3-show-targets.png)

    Oto, jakie widoku wygląda podobnie do zestawu SDK punktor:

    ![Widok elementów docelowych narzędzia CMake w Eksploratorze rozwiązań](media/cmake-bullet3-targets-view.png)

    Widok elementów docelowych zapewnia bardziej intuicyjne widok nowości w tej bazie źródła. Zobaczysz niektóre cele są bibliotek i inne pliki wykonywalne. 

3. Rozwiń węzeł w widoku elementów docelowych narzędzia CMake, aby wyświetlić jego plików kodu źródłowego, wszędzie tam, gdzie tych plików może znajdować się na dysku.

## <a name="set-a-breakpoint-build-and-run"></a>Ustaw punkt przerwania, kompilowanie i uruchamianie

W tym kroku możemy debugować przykładowy program demonstrujący biblioteki fizyki punktor.
  
1. W **Eksploratora rozwiązań**AppBasicExampleGui wybierz i rozwiń go. 
1. Otwórz plik `BasicExample.cpp`. 
1. Ustaw punkt przerwania, który będzie wskazywać po kliknięciu w działającej aplikacji. Zdarzenie kliknięcia odbywa się w metodzie w obrębie klasy pomocnika. Aby szybko dostać się tam:

    1. Wybierz `CommonRigidBodyBase` , struktura `BasicExample` pochodzi od około 30 wiersza.
    1. Kliknij prawym przyciskiem myszy i wybierz polecenie **przejdź do definicji**. Teraz są w nagłówku CommonRigidBodyBase.h. 
    1. W widoku przeglądarki powyżej źródła powinien zostać wyświetlony, że jesteś w `CommonRigidBodyBase`. Z prawej strony możesz wybrać elementy członkowskie do sprawdzenia. Kliknij listę rozwijaną i wybierz pozycję `mouseButtonCallback` można przejść do definicji tej funkcji w nagłówku.

        ![Pasek narzędzi Visual Studio elementu członkowskiego listy](media/cmake-bullet3-member-list-toolbar.png)

1. Umieść punkt przerwania w pierwszym wierszu w ramach tej funkcji. To spowoduje osiągnięcie, po kliknięciu przycisku myszy w oknie aplikacji, w przypadku uruchomienia w debugerze programu Visual Studio.

1. Aby uruchomić aplikację, wybierz uruchamiania listę rozwijaną z ikoną play, który jest wyświetlany komunikat "Wybierz element startowy" na pasku narzędzi. W AppBasicExampleGui.exe wybierz listę rozwijaną. Nazwa pliku wykonywalnego są teraz wyświetlane na przycisku uruchamiania:

    ![Visual Studio pasek narzędzi Uruchom z menu rozwijanego wybierz element startowy](media/cmake-bullet3-launch-button.png)

5.  Naciśnij przycisk Uruchom, aby skompilować aplikację i zależnościami, a następnie uruchomić go w debugerze programu Visual Studio. Po kilku chwilach pojawia się uruchomionej aplikacji:

    ![Visual Studio debugowanie aplikacji Windows](media/cmake-bullet3-launched.png)

6. Przenieś wskaźnik myszy w oknie aplikacji, a następnie kliknij przycisk, aby wyzwolić punkt przerwania. Wybranie tej opcji powoduje programu Visual Studio na pierwszy plan za pomocą edytora przedstawiający wiersz, której wykonywanie jest wstrzymane. Będzie można sprawdzić zmiennych wniosek, obiekty, wątki i pamięci. Możesz przejrzeć kod interaktywnie. Możesz kliknąć pozycję **Kontynuuj** umożliwi aplikacji, wznowić i zakończyć zwykle lub zaprzestanie wykonywanie w programie Visual Studio, korzystając z przycisku Zatrzymaj.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Dodawanie jawnej konfiguracji debugowania x64 Windows

Do tej pory był używany domyślnie **x64 debugowania** configuration for Windows. Konfiguracje są, jak Visual Studio obsługuje platformy docelowej będzie znajdował się na użytek narzędzia CMake. Domyślna konfiguracja nie jest reprezentowane na dysku. Gdy użytkownik jawnie doda do konfiguracji programu Visual Studio tworzy plik o nazwie pliku CMakeSettings.json, który jest wypełniana ustawieniami w przypadku wszystkich konfiguracji, które określisz. 

1. Dodaj nową konfigurację, klikając pozycję konfiguracji listy rozwijanej na pasku narzędzi i wybierając polecenie **Zarządzanie konfiguracjami...**

    ![Zarządzanie konfiguracją listy rozwijanej](media/cmake-bullet3-manage-configurations.png)

    **Dodawanie konfiguracji do pliku cmakesettings na pozycji** pojawi się okno dialogowe.

    ![Dodaj konfigurację do pliku cmakesettings na pozycji okna dialogowego](media/cmake-bullet3-add-configuration-x64-debug.png)

    To okno dialogowe zawiera wszystkie konfiguracje, które są dołączone do programu Visual Studio, a także wszystkie konfiguracje niestandardowe, które mogą zostać utworzone. Jeśli chcesz użyć domyślnej w dalszym ciągu **x64 debugowania** konfiguracji, który powinien być pierwszy z nich możesz dodać. Dodanie tej konfiguracji, można przełączać się między Windows i Linux konfiguracji. Wybierz **debugowania x64** i kliknij przycisk **wybierz**. Za pomocą konfiguracji dla spowoduje to utworzenie pliku CMakeSettings.json **debugowania x64** i przełączniki Visual Studio, aby użyć tej konfiguracji zamiast domyślnego. Zostaną wyświetlone listy rozwijanej konfiguracji nie jest wyświetlany komunikat "(wartość domyślna)" jako część nazwy. Można użyć dowolnych nazw dla swojej konfiguracji, zmieniając parametr name bezpośrednio w pliku CMakeSettings.json.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Dodaj konfigurację systemu Linux i połączyć z komputerem zdalnym

1. Teraz można dodać konfiguracji systemu Linux. Kliknij prawym przyciskiem myszy plik CMakeSettings.json **Eksploratora rozwiązań** wyświetlać i wybierać **Dodawanie konfiguracji**. Zobaczysz taką samą konfigurację Dodaj okno dialogowe pliku cmakesettings na pozycji jako przed. Wybierz **debugowania dla systemu Linux** wskazanego terminu, a następnie zapisz plik CMakeSettings.json. 
2. Teraz wybierz **debugowania dla systemu Linux** w listy rozwijanej konfiguracji.

    ![Uruchamianie konfiguracji listy rozwijanej z X64 debugowania, jak i opcje debugowania dla systemu Linux](media/cmake-bullet3-linux-configuration-item.png)

    Jeśli jest to po raz pierwszy łączysz się z systemem Linux **nawiązywanie połączenia z systemem zdalnym** pojawi się okno dialogowe.

    ![Visual Studio Connect do okna dialogowego systemu zdalnego](media/cmake-bullet3-connection-manager.png)

    Jeśli dodano już połączenia zdalnego, przechodząc do węzła, można otworzyć to okno **Narzędzia > Opcje > wiele Platform > Menedżer połączeń**.
 
3. Podaj informacje o połączeniu z maszyną z systemem Linux, a następnie kliknij przycisk **Connect**. Visual Studio dodaje tej maszyny do pliku CMakeSettings.json jako domyślne dla **debugowania dla systemu Linux**. Umożliwia ona również pobranie szczegółów nagłówków z komputera zdalnego, aby technologia IntelliSense specyficzne dla tego komputera podczas korzystania. Teraz program Visual Studio spowoduje wysłanie plików do maszyny zdalnej, a następnie wygeneruj pamięć podręczna CMake ma i zostanie to zrobione programu Visual Studio zostanie skonfigurowana na potrzeby przy użyciu tego samego podstawowego źródła, z tym komputerem zdalnym systemu Linux. Te kroki może potrwać pewien czas w zależności od szybkości sieci i zasilania komputera zdalnego. Będzie wiadomo, że jest to kompletny, gdy pojawi się komunikat "Zakończono wyodrębnianie informacji docelowej" w oknie danych wyjściowych narzędzia CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Ustaw punkt przerwania, skompilować i uruchomić w systemie Linux

Ponieważ jest to aplikacja komputerowa, konieczne jest podanie pewnych informacji dodatkowej konfiguracji do konfiguracji debugowania. 

1. W widoku elementów docelowych narzędzia CMake, kliknij prawym przyciskiem myszy AppBasicExampleGui, a następnie wybierz **ustawienia debugowania i uruchamiania** do otwierania pliku launch.vs.json w ukrytym **.vs** podfolderu. Ten plik jest lokalny dla swojego środowiska projektowego. Można przenieść go do katalogu głównego projektu Jeśli chcesz sprawdzić, czy w i zapisać go ze swoim zespołem. W tym pliku konfiguracji dodano AppBasicExampleGui. Te ustawienia domyślne działać w większości przypadków, ale ponieważ jest to aplikacja komputerowa, należy podać niektóre dodatkowe informacje, aby uruchomić program w taki sposób, można go było wyświetlić na maszyny z systemem Linux. 
2. Musisz znać wartości zmiennej środowiskowej `DISPLAY` na maszynie z systemem Linux, uruchom następujące polecenie, aby z niej skorzystać.

    ```cmd
    echo $DISPLAY
    ```

    W konfiguracji dla AppBasicExampleGui jest tablicą parametrów "pipeArgs". W ramach miejsca jest linią "${debuggerCommand}". To polecenie, które uruchamia gdb na komputerze zdalnym. Program Visual Studio wymaga do wyeksportowania wyświetlania, w tym kontekście, przed uruchomieniem tego polecenia. Na przykład jeśli wartość wyświetlania: 1, zmodyfikuj tę linię w następujący sposób:

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Teraz w celu uruchamiania i debugowania aplikacji, należy wybrać **wybierz element startowy** listy rozwijanej na pasku narzędzi i wybierz polecenie AppBasicExampleGui. Teraz naciśnij ten przycisk, lub kliknij przycisk **F5**. Spowoduje to utworzenie aplikacji i jej zależności na zdalnym komputerze z systemem Linux następnie uruchom go debugerze programu Visual Studio. Na maszynie zdalnej systemu Linux powinien zostać wyświetlony pojawiają się okna aplikacji.

4. Przenieś wskaźnik myszy w oknie aplikacji kliknij przycisk, a punkt przerwania zostanie osiągnięty. Wstrzymuje wykonywanie programu, Visual Studio wróci do pierwszego planu i będzie w punkt przerwania. Powinno również zostać wyświetlone okno konsoli systemu Linux są wyświetlane w programie Visual Studio. To okno zawiera dane wyjściowe z komputera zdalnego systemu Linux, a także może akceptować dane wejściowe na potrzeby `stdin`. Podobnie jak wszystkie okna programu Visual Studio może zadokowane, której chcesz zobaczyć, jak to i jego położenie zostaną utrwalone w przyszłych sesjach.

    ![Visual Studio Linux Console Window](media/cmake-bullet3-linux-console.png)

5. Za pomocą kodu interaktywnie przy użyciu programu Visual Studio, można sprawdzić zmiennych wniosek, obiekty, wątki, pamięci i kroku. Jednak tym razem robisz to na komputerze zdalnym z systemem Linux zamiast lokalnego środowiska Windows. Możesz kliknąć pozycję **Kontynuuj** umożliwi aplikacji, wznowić i zamknąć okno zwykle lub naciśniesz przycisk Zatrzymaj, podobnie jak w przypadku lokalnego wykonywania.

6. Spójrz na okno stosu wywołań i wyświetlić wywołania `x11OpenGLWindow` od programu Visual Studio uruchomiona aplikacja dla systemu Linux.

    ![Stos wywołań, okno przedstawiający stos wywołań w systemie Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Zdobytą wiedzę 

W ramach tego samouczka wiesz już sklonowany bezpośrednio z serwisu GitHub i utworzonych, wykonywania i debugowania na podstawie Windows bez żadnych modyfikacji kodu. To pochodzi kodu bazowego, wprowadzając zmiany w konfiguracji pomocniczych, zostało utworzone, uruchamiania i debugowania na komputerze zdalnym z systemem Linux. 

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o konfigurowaniu i debugowania projektów CMake w programie Visual Studio:

> [!div class="nextstepaction"]
> [Narzędzia CMake w języku Visual C++](../ide/cmake-tools-for-visual-cpp.md)<br/><br/>
> [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Podłącz do komputera zdalnego systemu Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Dostosowywanie ustawień kompilacji CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurowanie narzędzia CMake sesjami debugowania](configure-cmake-debugging-sessions.md)<br/><br/>
> [Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](cmake-predefined-configuration-reference.md)
> 
