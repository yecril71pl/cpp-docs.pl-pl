---
title: Projekty CMake w programie Visual Studio
ms.date: 06/12/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f2bafb75aae2eabb4e8f289435ddaeb61e6aabf4
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042658"
---
# <a name="cmake-projects-in-visual-studio"></a>Projekty CMake w programie Visual Studio

Narzędzie CMake to narzędzie dla wielu platform, typu open-source Definiowanie procesów kompilacji, które są uruchamiane na wielu platformach. W tym artykule przyjęto założenie, że czytelnik zna za pomocą narzędzia CMake. Dowiedz się więcej na temat na stronie [kompilacji, testów i pakietów usługi oprogramowania za pomocą narzędzia CMake](https://cmake.org/). 

> [!NOTE]
> Narzędzia CMake ma stają się coraz bardziej zintegrowane z programem Visual Studio w poprzednich wersjach kilka. Aby wyświetlić poprawne informacje o wersji, którego używasz, upewnij się, że poprawnie selektor wersji, w lewym górnym rogu tej strony. 

::: moniker range="vs-2019"

Visual Studio 2019 wprowadza **edytora ustawienia narzędzia CMake** i innych ulepszeń w programie Visual Studio 2017. **C++ Narzędzia CMake dla Windows** składnik używa **Otwórz Folder** funkcję, aby włączyć środowisko IDE będzie korzystają z plików projektu narzędzia CMake (na przykład pliku CMakeLists.txt) bezpośrednio na potrzeby funkcji IntelliSense i Przeglądanie. Generatory Ninja i programu Visual Studio są obsługiwane. Jeśli używasz generator programu Visual Studio, tymczasowy plik projektu zostanie wygenerowany i przekazane do msbuild.exe, ale nigdy nie jest załadowany do celów przeglądaniu lub IntelliSense. Można także zaimportować istniejący pamięć podręczną CMake. 

## <a name="installation"></a>Instalacja

**C++Narzędzia CMake dla Windows** jest instalowany domyślnie w jako część **programowanie aplikacji klasycznych przy użyciu C++**  obciążenia i w ramach **Linux Development przy użyciu C++**  obciążenia. Zobacz [projektów CMake dla wielu platform](../linux/cmake-linux-project.md) Aby uzyskać więcej informacji.

![Składnik narzędzia CMake w obciążeniu C++ na komputerach](media/cmake-install-2019.png)

Aby uzyskać więcej informacji, zobacz [Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja środowiska IDE

Po wybraniu **pliku | Otwórz | Folder** aby otworzyć folder zawierający plik CMakeLists.txt, się zdarzyć, następujące elementy:

- Program Visual Studio dodaje **CMake** elementy do **projektu** menu za pomocą poleceń do wyświetlania i edytowania skryptów narzędzia CMake.

- **Eksplorator rozwiązań** wyświetla strukturę folderów i plików.

- Program Visual Studio uruchamia CMake.exe i opcjonalnie generuje pamięci podręcznej narzędzia CMake dla domyślnej *konfiguracji*, czyli x86 debugowania. W wierszu polecenia CMake są wyświetlane w **okno danych wyjściowych**, wraz z dodatkowych danych wyjściowych z narzędzia CMake.

- W tle programu Visual Studio uruchamia do indeksowania plików źródłowych, aby włączyć technologię IntelliSense, informacji o przeglądaniu, Refaktoryzacja i tak dalej. Podczas pracy programu Visual Studio monitoruje zmiany w edytorze, a także na dysku w celu synchronizowania jej indeks ze źródłami.

Możesz otworzyć foldery zawierające dowolną liczbę projekty narzędzia CMake. Visual Studio wykrywa i skonfiguruje wszystkie pliki CMakeLists.txt "root" w obszarze roboczym. Operacje CMake (Konfigurowanie, tworzenie, debugowanie) również funkcji C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![Projekt narzędzia CMake z wielu katalogów głównych](media/cmake-multiple-roots.png)

Można również wyświetlić swoje projekty logicznie uporządkowane według elementów docelowych. Wybierz **jest przeznaczony dla widoku** z listy rozwijanej w **Eksploratora rozwiązań** narzędzi:

![Przycisk Widok elementów docelowych narzędzia CMake](media/cmake-targets-view.png)

Program Visual Studio używa pliku o nazwie **CMakeSettings.json** do przechowywania zmiennych środowiskowych lub opcji wiersza polecenia dla Cmake.exe. **CMakeSettings.json** również umożliwia definiowanie i przechowywanie wielu CMake konfiguracje kompilacji i łatwo przełączać się między nimi w środowisku IDE. W programie Visual Studio 2019 r **edytora ustawienia narzędzia CMake** oferuje wygodny sposób, aby edytować ustawienia. Zobacz [CMake dostosować ustawienia](customize-cmake-settings.md) Aby uzyskać więcej informacji.

W przeciwnym razie użyj **CMakeLists.txt** tak samo jak w każdym projekcie CMake, wybierz pliki źródłowe, Znajdź bibliotek, ustaw opcje kompilatora i konsolidatora i określ inny system kompilacji będzie można powiązane informacje.

Jeśli potrzebujesz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **launch.vs.json**. W niektórych przypadkach program Visual Studio automatycznie wygeneruje tych plików; można edytować je ręcznie. Mogą również samodzielnie utworzyć plik.

> [!NOTE]
> Dla innych rodzajów projektów Otwórz Folder są używane dwa dodatkowe pliki JSON: **Plik CppProperties.json** i **tasks.vs.json**. Oba te są odpowiednie dla projektów narzędzia CMake.

## <a name="import-an-existing-cache"></a>Importowanie istniejąca pamięć podręczna

Podczas importowania istniejącego pliku CMakeCache.txt programu Visual Studio wyodrębnia niestandardowe zmienne i automatycznie tworzy wstępnie wypełnionych **CMakeSettings.json** na ich podstawie plików. Oryginalny pamięci podręcznej nie jest modyfikowany w dowolny sposób i nadal można używać z poziomu wiersza polecenia lub przy użyciu dowolnego narzędzia lub IDE został użyty do jego wygenerowania. Nowy **CMakeSettings.json** plik zostanie umieszczony obok projektu głównego pliku CMakeLists.txt. Program Visual Studio generuje nową pamięć podręczną na podstawie pliku ustawień. Można zastąpić Generowanie automatyczne pamięci podręcznej w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

Nie wszystkie elementy w pamięci podręcznej jest importowany.  Właściwości, takie jak generator i lokalizację kompilatorów są zastępowane przy użyciu ustawień domyślnych, które są znane do pracy ze środowiska IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejąca pamięć podręczna

1. W menu głównym wybierz **pliku | Otwórz | Narzędzie CMake**:

   ![Otwórz narzędzie CMake](media/cmake-file-open.png "pliku, Otwórz, narzędzia CMake")

   Spowoduje to przejście **importu CMake z pamięci podręcznej** kreatora.

2. Przejdź do pliku CMakeCache.txt, który chcesz zaimportować, a następnie kliknij przycisk **OK**. **Importowania projektu narzędzia CMake z pamięci podręcznej** pojawi się Kreator:

   ![Importowanie pamięci podręcznej narzędzia CMake](media/cmake-import-wizard.png "Otwórz kreatora pamięci podręcznej narzędzia CMake importu")

   Po zakończeniu działania kreatora, można wyświetlić nowy plik CMakeCache.txt w **Eksploratora rozwiązań** obok głównego pliku CMakeLists.txt w projekcie.

## <a name="building-cmake-projects"></a>Kompilowanie projektów narzędzia CMake

Aby skompilować projekt CMake, masz następujące opcje:

1. Na pasku narzędzi ogólne, Znajdź **konfiguracje** listy rozwijanej; domyślnie prawdopodobnie jest widoczny "Linux-Debug" lub "x64 debugowanie". Wybierz żądaną konfiguracją i naciśnij klawisz **F5**, lub kliknij przycisk **Uruchom** (zielony trójkąt) przycisk na pasku narzędzi. Automatycznie kompilacje projektu po pierwsze, podobnie jak rozwiązanie programu Visual Studio.

1. Kliknij prawym przyciskiem myszy pliku CMakeLists.txt i wybierz pozycję **kompilacji** z menu kontekstowego. Jeśli masz wiele elementów docelowych w strukturze folderów, można tworzyć wszystkie lub tylko jeden określony element docelowy.

1. W menu głównym wybierz **kompilacji | Tworzenie rozwiązania** (**F7** lub **Ctrl + Shift + B**). Upewnij się, czy docelowych narzędzia CMake została już wybrana w **element startowy** liście rozwijanej **ogólne** paska narzędzi.

![Polecenia menu kompilacji CMake](media/cmake-build-menu.png "menu poleceń kompilacji CMake")

Konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia można dostosować bez modyfikowania pliku CMakeLists.txt przy użyciu **edytora ustawienia narzędzia CMake**. Aby uzyskać więcej informacji, zobacz [CMake dostosować ustawienia](customize-cmake-settings.md).

Jak można oczekiwać wyników kompilacji są wyświetlane w **okno danych wyjściowych** i **lista błędów**.

![Błędy kompilacji CMake](media/cmake-build-errors.png "błędy kompilacji CMake")

W folderze o wiele obiektów docelowych kompilacji, można wybrać **kompilacji** elementu na **CMake** menu lub **CMakeLists.txt** menu kontekstowym, aby określić, które docelowej narzędzia CMake do kompilacji. Naciśnięcie klawisza **Ctrl + Shift + B** w CMake projekt jest kompilowany bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów narzędzia CMake

Aby debugować projekt CMake, wybierz żądaną konfiguracją i naciśnij klawisz **F5**, lub naciśnij **Uruchom** przycisku na pasku narzędzi. Jeśli **Uruchom** przycisk jest wyświetlany komunikat "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz cel, który chcesz uruchomić. (W projekcie programu CMake, "bieżący dokument" opcja jest prawidłowa tylko dla plików .cpp.)

![Przycisk Uruchom narzędzie CMake](media/cmake-run-button.png "przycisk Uruchom narzędzia CMake")

**Uruchom** lub **F5** polecenia najpierw skompilować projekt, jeśli zostały zmienione od poprzedniej kompilacji.

Można dostosować CMake z sesji debugowania przez ustawienie właściwości **launch.vs.json** pliku. Aby uzyskać więcej informacji, zobacz [konfigurowania CMake sesjami debugowania](configure-cmake-debugging-sessions.md).

## <a name="vcpkg-integration"></a>Vcpkg integracji

Jeśli zainstalowano [vcpkg](vcpkg.md), projekty narzędzia CMake otwierane w programie Visual Studio automatycznie zostanie zintegrowana usługa vcpkg pliku łańcucha narzędzi. Oznacza to, że żadne dodatkowe czynności konfiguracyjne wymagane jest wprowadzenie vcpkg dotyczącą projektów narzędzia CMake. Ta funkcja działa w przypadku instalacji lokalnej vcpkg i vcpkg instalacji na komputerach zdalnych, które są przeznaczone dla. To zachowanie jest automatycznie wyłączane po określeniu dowolnego łańcucha narzędzi w konfiguracji ustawienia narzędzia CMake.

## <a name="just-my-code-for-cmake-projects"></a>Tylko mój kod dla projektów narzędzia CMake

Podczas tworzenia dla Windows za pomocą kompilatora MSVC w projektach CMake są teraz obsługiwane tylko mój kod debugowania w kompilatorze i konsolidatorze Jeśli opcja jest włączona w programie Visual Studio. Aby zmienić to ustawienie, przejdź do **narzędzia** > **opcje** > **debugowanie** > **ogólne**.

## <a name="customize-configuration-feedback"></a>Dostosowywanie konfiguracji opinii

Domyślnie większość konfiguracji komunikaty są pomijane, chyba że wystąpi błąd. Możesz wyświetlić wszystkie komunikaty, włączenie tej funkcji w **narzędzia** > **opcje** > **CMake**.

   ![Konfigurowanie opcji diagnostycznych CMake](media/vs2019-cmake-configure-options.png "CMake opcje diagnostyki")

## <a name="editing-cmakeliststxt-files"></a>Edytowanie pliku CMakeLists.txt plików

Aby edytować plik CMakeLists.txt, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku paska stanu żółty pojawia się i informuje o spowoduje zaktualizowanie funkcji IntelliSense i daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacji dotyczących pliku CMakeLists.txt, zobacz [dokumentacji narzędzia CMake](https://cmake.org/documentation/).

   ![Edytowanie pliku CMakeLists.txt](media/cmake-cmakelists.png "edycji pliku CMakeLists.txt")

Bezpośrednio po zapisaniu pliku kroku konfiguracji automatycznie ponownie uruchomiona i wyświetli informacje zawarte w **dane wyjściowe** okna. Błędy i ostrzeżenia są wyświetlane w **lista błędów** lub **dane wyjściowe** okna. Kliknij dwukrotnie błąd w **lista błędów** można przejść do problematycznych wierszy w pliku CMakeLists.txt.

   ![Błędy w pliku CMakeLists.txt](media/cmake-cmakelists-error.png "błędy w pliku CMakeLists.txt")


## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Gdy istotnych zmian do **CMakeSettings.json** lub do pliku CMakeLists.txt plików, programu Visual Studio automatycznie uruchamia ponownie narzędzia CMake krok konfigurowania. Jeśli krok konfiguracja zakończy się bez błędów, zbieranych informacji są dostępne w funkcji C++ IntelliSense i usług językowych również w kompilacji i debugowania operacji.

Korzystając z wielu projektów CMake taką samą nazwę konfiguracji narzędzia CMake (na przykład x86-Debug), wszystkie z nich są konfigurowane i wbudowane (folder główny własne kompilacji) po wybraniu tej konfiguracji. Można debugować cele ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji narzędzia CMake.

   ![Kompilacji CMake tylko element menu](media/cmake-build-only.png "kompilacji CMake tylko element menu")

Ogranicz kompilacji i debugowania sesji podzestaw projektów w obszarze roboczym, Utwórz nową konfigurację o unikatowej nazwie w **CMakeSettings.json** pliku i dotyczy tylko tych projektów. Po wybraniu tej konfiguracji IntelliSense i kompilacja i debugowanie poleceń są włączone tylko dla tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej narzędzia CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej narzędzia CMake, aby zdiagnozować problem, otwórz **CMake** menu głównego lub **CMakeLists.txt** menu kontekstowego w **Eksploratora rozwiązań**do uruchamiania jednego z następujących poleceń:

- **Wyświetlanie pamięci podręcznej** otwiera plik CMakeCache.txt wobec folderu głównego kompilacji w edytorze. (Wszystkie zmiany wprowadzone w tym miejscu CMakeCache.txt są wyczyszczone, jeśli czyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są zachowywane po czyszczeniu pamięci podręcznej, zobacz [CMake dostosować ustawienia](customize-cmake-settings.md).)

- **Otwórz Folder pamięci podręcznej** zostanie otwarte okno Eksploratora do folderu głównego kompilacji.

- **Czyszczenie pamięci podręcznej** usuwa folder główny kompilacji CMake dalej skonfigurowania uruchamia krok z czystą pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza krok Wygeneruj, aby uruchomić, nawet jeśli program Visual Studio traktuje środowiska aktualne.

Generowanie pamięci podręcznej automatycznego można wyłączyć w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

## <a name="single-file-compilation"></a>Pojedynczy plik kompilacji

Aby utworzyć pojedynczy plik projektu narzędzia CMake, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **skompilować**. Można także utworzyć plik który jest obecnie otwarty w edytorze za pomocą menu głównego narzędzia CMake:

![Narzędzie CMake pojedynczy plik kompilacji](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Wykonywania CMake z wiersza polecenia

Po zainstalowaniu narzędzia CMake z Instalatora programu Visual Studio, można uruchomić go z wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiedni vsdevcmd.bat — x86/x64 64. Zobacz [tworzenia w wierszu polecenia](building-on-the-command-line.md) Aby uzyskać więcej informacji.

1. Przejdź do folderu wyjściowego.

1. Wykonywania CMake kompilacji/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2017"

Program Visual Studio 2017 zawiera szeroką obsługę narzędzia CMake, w tym [projekty narzędzia CMake dla wielu platform](../linux/cmake-linux-project.md). **Visual C++ Tools for CMake** składnik używa **Otwórz Folder** funkcję, aby włączyć środowisko IDE będzie korzystają z plików projektu narzędzia CMake (na przykład pliku CMakeLists.txt) bezpośrednio na potrzeby funkcji IntelliSense i przeglądania. Generatory Ninja i programu Visual Studio są obsługiwane. Jeśli używasz generator programu Visual Studio, tymczasowy plik projektu zostanie wygenerowany i przekazane do msbuild.exe, ale nigdy nie jest załadowany do celów przeglądaniu lub IntelliSense. Można też zaimportować istniejący pamięć podręczną CMake. 

## <a name="installation"></a>Instalacja

**Visual C++ Tools for CMake** jest instalowany domyślnie w jako część **programowanie aplikacji klasycznych w języku C++** obciążenia i w ramach **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

![Składnik narzędzia CMake w obciążeniu C++ na komputerach](media/cmake-install.png)

Aby uzyskać więcej informacji, zobacz [Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja środowiska IDE

Po wybraniu **pliku | Otwórz | Folder** aby otworzyć folder zawierający plik CMakeLists.txt, się zdarzyć, następujące elementy:

- Program Visual Studio dodaje **CMake** element menu do menu głównego, za pomocą poleceń do wyświetlania i edytowania skryptów narzędzia CMake.

- **Eksplorator rozwiązań** wyświetla strukturę folderów i plików.

- Program Visual Studio uruchamia CMake.exe i opcjonalnie generuje pamięci podręcznej narzędzia CMake dla domyślnej *konfiguracji*, czyli x86 debugowania. W wierszu polecenia CMake są wyświetlane w **okno danych wyjściowych**, wraz z dodatkowych danych wyjściowych z narzędzia CMake.

- W tle programu Visual Studio uruchamia do indeksowania plików źródłowych, aby włączyć technologię IntelliSense, informacji o przeglądaniu, Refaktoryzacja i tak dalej. Podczas pracy programu Visual Studio monitoruje zmiany w edytorze, a także na dysku w celu synchronizowania jej indeks ze źródłami.

Możesz otworzyć foldery zawierające dowolną liczbę projekty narzędzia CMake. Visual Studio wykrywa i skonfiguruje wszystkie pliki CMakeLists.txt "root" w obszarze roboczym. Operacje CMake (Konfigurowanie, tworzenie, debugowanie) również funkcji C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![Projekt narzędzia CMake z wielu katalogów głównych](media/cmake-multiple-roots.png)

Można również wyświetlić swoje projekty logicznie uporządkowane według elementów docelowych. Wybierz **jest przeznaczony dla widoku** z listy rozwijanej w **Eksploratora rozwiązań** narzędzi:

![Przycisk Widok elementów docelowych narzędzia CMake](media/cmake-targets-view.png)

Program Visual Studio używa pliku o nazwie **CMakeSettings.json** do przechowywania zmiennych środowiskowych lub opcji wiersza polecenia dla Cmake.exe. **CMakeSettings.json** również umożliwia definiowanie i przechowywanie wielu CMake konfiguracje kompilacji i łatwo przełączać się między nimi w środowisku IDE. 

W przeciwnym razie użyj **CMakeLists.txt** tak samo jak w każdym projekcie CMake, wybierz pliki źródłowe, Znajdź bibliotek, ustaw opcje kompilatora i konsolidatora i określ inny system kompilacji będzie można powiązane informacje.

Jeśli potrzebujesz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **launch.vs.json**. W niektórych przypadkach program Visual Studio automatycznie wygeneruje tych plików; można edytować je ręcznie. Mogą również samodzielnie utworzyć plik.

> [!NOTE]
> Dla innych rodzajów projektów Otwórz Folder są używane dwa dodatkowe pliki JSON: **Plik CppProperties.json** i **tasks.vs.json**. Oba te są odpowiednie dla projektów narzędzia CMake.

## <a name="import-an-existing-cache"></a>Importowanie istniejąca pamięć podręczna

Podczas importowania istniejącego pliku CMakeCache.txt programu Visual Studio wyodrębnia niestandardowe zmienne i automatycznie tworzy wstępnie wypełnionych **CMakeSettings.json** na ich podstawie plików. Oryginalny pamięci podręcznej nie jest modyfikowany w dowolny sposób i nadal można używać z poziomu wiersza polecenia lub przy użyciu dowolnego narzędzia lub IDE został użyty do jego wygenerowania. Nowy **CMakeSettings.json** plik zostanie umieszczony obok projektu głównego pliku CMakeLists.txt. Program Visual Studio generuje nową pamięć podręczną na podstawie pliku ustawień. Można zastąpić Generowanie automatyczne pamięci podręcznej w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

Nie wszystkie elementy w pamięci podręcznej jest importowany.  Właściwości, takie jak generator i lokalizację kompilatorów są zastępowane przy użyciu ustawień domyślnych, które są znane do pracy ze środowiska IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejąca pamięć podręczna

1. W menu głównym wybierz **pliku | Otwórz | Narzędzie CMake**:

   ![Otwórz narzędzie CMake](media/cmake-file-open.png "pliku, Otwórz, narzędzia CMake")

   Spowoduje to przejście **importu CMake z pamięci podręcznej** kreatora.

2. Przejdź do pliku CMakeCache.txt, który chcesz zaimportować, a następnie kliknij przycisk **OK**. **Importowania projektu narzędzia CMake z pamięci podręcznej** pojawi się Kreator:

   ![Importowanie pamięci podręcznej narzędzia CMake](media/cmake-import-wizard.png "Otwórz kreatora pamięci podręcznej narzędzia CMake importu")

   Po zakończeniu działania kreatora, można wyświetlić nowy plik CMakeCache.txt w **Eksploratora rozwiązań** obok głównego pliku CMakeLists.txt w projekcie.

## <a name="building-cmake-projects"></a>Kompilowanie projektów narzędzia CMake

Aby skompilować projekt CMake, masz następujące opcje:

1. Na pasku narzędzi ogólne, Znajdź **konfiguracje** listy rozwijanej; domyślnie prawdopodobnie jest widoczny "Linux-Debug" lub "x64 debugowanie". Wybierz żądaną konfiguracją i naciśnij klawisz **F5**, lub kliknij przycisk **Uruchom** (zielony trójkąt) przycisk na pasku narzędzi. Automatycznie kompilacje projektu po pierwsze, podobnie jak rozwiązanie programu Visual Studio.

1. Kliknij prawym przyciskiem myszy pliku CMakeLists.txt i wybierz pozycję **kompilacji** z menu kontekstowego. Jeśli masz wiele elementów docelowych w strukturze folderów, można tworzyć wszystkie lub tylko jeden określony element docelowy.

1. W menu głównym wybierz **kompilacji | Tworzenie rozwiązania** (**F7** lub **Ctrl + Shift + B**). Upewnij się, czy docelowych narzędzia CMake została już wybrana w **element startowy** liście rozwijanej **ogólne** paska narzędzi.

![Polecenia menu kompilacji CMake](media/cmake-build-menu.png "menu poleceń kompilacji CMake")

Konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia można dostosować bez modyfikowania pliku CMakeLists.txt przy użyciu **CMakeSettings.json** pliku. Aby uzyskać więcej informacji, zobacz [CMake dostosować ustawienia](customize-cmake-settings.md).

Jak można oczekiwać wyników kompilacji są wyświetlane w **okno danych wyjściowych** i **lista błędów**.

![Błędy kompilacji CMake](media/cmake-build-errors.png "błędy kompilacji CMake")

W folderze o wiele obiektów docelowych kompilacji, można wybrać **kompilacji** elementu na **CMake** menu lub **CMakeLists.txt** menu kontekstowym, aby określić, które docelowej narzędzia CMake do kompilacji. Naciśnięcie klawisza **Ctrl + Shift + B** w CMake projekt jest kompilowany bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów narzędzia CMake

Aby debugować projekt CMake, wybierz żądaną konfiguracją i naciśnij klawisz **F5**, lub naciśnij **Uruchom** przycisku na pasku narzędzi. Jeśli **Uruchom** przycisk jest wyświetlany komunikat "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz cel, który chcesz uruchomić. (W projekcie programu CMake, "bieżący dokument" opcja jest prawidłowa tylko dla plików .cpp.)

![Przycisk Uruchom narzędzie CMake](media/cmake-run-button.png "przycisk Uruchom narzędzia CMake")

**Uruchom** lub **F5** polecenia najpierw skompilować projekt, jeśli zostały zmienione od poprzedniej kompilacji.

Można dostosować CMake z sesji debugowania przez ustawienie właściwości **launch.vs.json** pliku. Aby uzyskać więcej informacji, zobacz [konfigurowania CMake sesjami debugowania](configure-cmake-debugging-sessions.md).


## <a name="editing-cmakeliststxt-files"></a>Edytowanie pliku CMakeLists.txt plików

Aby edytować plik CMakeLists.txt, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku paska stanu żółty pojawia się i informuje o spowoduje zaktualizowanie funkcji IntelliSense i daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacji dotyczących pliku CMakeLists.txt, zobacz [dokumentacji narzędzia CMake](https://cmake.org/documentation/).

   ![Edytowanie pliku CMakeLists.txt](media/cmake-cmakelists.png "edycji pliku CMakeLists.txt")

Bezpośrednio po zapisaniu pliku kroku konfiguracji automatycznie ponownie uruchomiona i wyświetli informacje zawarte w **dane wyjściowe** okna. Błędy i ostrzeżenia są wyświetlane w **lista błędów** lub **dane wyjściowe** okna. Kliknij dwukrotnie błąd w **lista błędów** można przejść do problematycznych wierszy w pliku CMakeLists.txt.

   ![Błędy w pliku CMakeLists.txt](media/cmake-cmakelists-error.png "błędy w pliku CMakeLists.txt")


## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Gdy istotnych zmian do **CMakeSettings.json** lub do pliku CMakeLists.txt plików, programu Visual Studio automatycznie uruchamia ponownie narzędzia CMake krok konfigurowania. Jeśli krok konfiguracja zakończy się bez błędów, zbieranych informacji są dostępne w funkcji C++ IntelliSense i usług językowych również w kompilacji i debugowania operacji.

Korzystając z wielu projektów CMake taką samą nazwę konfiguracji narzędzia CMake (na przykład x86-Debug), wszystkie z nich są konfigurowane i wbudowane (folder główny własne kompilacji) po wybraniu tej konfiguracji. Można debugować cele ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji narzędzia CMake.

   ![Kompilacji CMake tylko element menu](media/cmake-build-only.png "kompilacji CMake tylko element menu")

Ogranicz kompilacji i debugowania sesji podzestaw projektów w obszarze roboczym, Utwórz nową konfigurację o unikatowej nazwie w **CMakeSettings.json** pliku i dotyczy tylko tych projektów. Po wybraniu tej konfiguracji IntelliSense i kompilacja i debugowanie poleceń są włączone tylko dla tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej narzędzia CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej narzędzia CMake, aby zdiagnozować problem, otwórz **CMake** menu głównego lub **CMakeLists.txt** menu kontekstowego w **Eksploratora rozwiązań**do uruchamiania jednego z następujących poleceń:

- **Wyświetlanie pamięci podręcznej** otwiera plik CMakeCache.txt wobec folderu głównego kompilacji w edytorze. (Wszystkie zmiany wprowadzone w tym miejscu CMakeCache.txt są wyczyszczone, jeśli czyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są zachowywane po czyszczeniu pamięci podręcznej, zobacz [CMake dostosować ustawienia](customize-cmake-settings.md).)

- **Otwórz Folder pamięci podręcznej** zostanie otwarte okno Eksploratora do folderu głównego kompilacji.

- **Czyszczenie pamięci podręcznej** usuwa folder główny kompilacji CMake dalej skonfigurowania uruchamia krok z czystą pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza krok Wygeneruj, aby uruchomić, nawet jeśli program Visual Studio traktuje środowiska aktualne.

Generowanie pamięci podręcznej automatycznego można wyłączyć w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

## <a name="single-file-compilation"></a>Pojedynczy plik kompilacji

Aby utworzyć pojedynczy plik projektu narzędzia CMake, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **skompilować**. Można także utworzyć plik który jest obecnie otwarty w edytorze za pomocą menu głównego narzędzia CMake:

![Narzędzie CMake pojedynczy plik kompilacji](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Wykonywania CMake z wiersza polecenia

Po zainstalowaniu narzędzia CMake z Instalatora programu Visual Studio, można uruchomić go z wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiedni vsdevcmd.bat — x86/x64 64. Zobacz [tworzenia w wierszu polecenia](building-on-the-command-line.md) Aby uzyskać więcej informacji.

1. Przejdź do folderu wyjściowego.

1. Wykonywania CMake kompilacji/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2015"

W programie Visual Studio 2015, Visual Studio użytkownicy mogą używać [generatora CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) do generowania plików projektu MSBuild, które IDE następnie zużywa dla technologii IntelliSense, przeglądanie i kompilacji.

::: moniker-end


## <a name="see-also"></a>Zobacz także

[Samouczek: Tworzenie międzyplatformowych projektów w języku C++ w programie Visual Studio](get-started-linux-cmake.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Dostosowywanie ustawień kompilacji narzędzia CMake](customize-cmake-settings.md)<br/>
[Dokumentacja pliku CMakeSettings.json](cmakesettings-reference.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](cmake-predefined-configuration-reference.md)<br/>
