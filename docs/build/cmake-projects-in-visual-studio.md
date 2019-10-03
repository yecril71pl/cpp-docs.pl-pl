---
title: CMake projekty w programie Visual Studio
ms.date: 10/01/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 168f5b0aac34757a9c2d73bcebc908a0d58721fe
ms.sourcegitcommit: b85e1db6b7d4919852ac6843a086ba311ae97d40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71925576"
---
# <a name="cmake-projects-in-visual-studio"></a>CMake projekty w programie Visual Studio

CMake to międzyplatformowe narzędzie typu open source służące do definiowania procesów kompilacji, które są uruchamiane na wielu platformach. W tym artykule założono, że znasz już CMake. Więcej informacji na ten temat można znaleźć w witrynie [kompilacja, testowanie i pakowanie oprogramowania przy użyciu CMAKE](https://cmake.org/). 

> [!NOTE]
> CMake stał się bardziej i bardziej zintegrowany z programem Visual Studio w ciągu ostatnich kilku wydań. Aby wyświetlić prawidłowe informacje dotyczące używanej wersji, upewnij się, że selektor wersji w lewym górnym rogu tej strony jest poprawnie ustawiony. 

::: moniker range="vs-2019"

Składnik  **C++ narzędzia CMAKE Tools for Windows** korzysta z funkcji [Otwórz folder](https://docs.microsoft.com/en-us/cpp/build/open-folder-projects-cpp?view=vs-2019) , aby używać plików projektu CMAKE (takich jak CMakeLists. txt) bezpośrednio na potrzeby funkcji IntelliSense i przeglądania. Obsługiwane są zarówno generatory ninja, jak i Visual Studio. Jeśli używasz generatora programu Visual Studio, tymczasowy plik projektu jest generowany i przenoszona do programu MSBuild. exe, ale nigdy nie jest ładowany do funkcji IntelliSense ani do przeglądania. Istnieje również możliwość zaimportowania istniejącej pamięci podręcznej CMake.

## <a name="installation"></a>Instalacja

Narzędzia CMAKE Tools for Windows są instalowane domyślnie w ramach **tworzenia aplikacji C++ dla komputerów stacjonarnych** i w ramach tworzenia **C++** **C++** obciążeń w systemie Linux. Aby uzyskać więcej informacji, zobacz [Międzyplatformowe projekty CMAKE](../linux/cmake-linux-project.md) .

![Składnik CMake w C++ obciążeniu pulpitu](media/cmake-install-2019.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie C++ obciążenia systemu Linux w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja IDE

Po wybraniu opcji **plik > Otwórz folder >** , aby otworzyć folder zawierający plik CMakeLists. txt:

- Program Visual Studio dodaje **CMAKE** elementy do menu **projekt** z poleceniami służącymi do wyświetlania i edytowania skryptów CMAKE.

- **Eksplorator rozwiązań** Wyświetla strukturę folderów i pliki.

- Program Visual Studio uruchamia CMAKE. exe i generuje pamięć podręczną CMake dla *konfiguracji*domyślnej, którą jest debugowanie x64. Wiersz polecenia CMake jest wyświetlany w **okno dane wyjściowe**wraz z dodatkowymi danymi wyjściowymi z CMAKE.

- W tle program Visual Studio zaczyna indeksować pliki źródłowe w celu włączenia funkcji IntelliSense, przeglądania informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować synchronizację indeksu ze źródłami.

Można otwierać foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie pliki "root" CMakeLists. txt w obszarze roboczym. Operacje CMake (Konfigurowanie, kompilowanie, debugowanie) oraz funkcja C++ IntelliSense i przeglądanie są dostępne dla wszystkich projektów CMAKE w obszarze roboczym.

![CMake projekt z wieloma katalogami głównymi](media/cmake-multiple-roots.png)

Możesz również wyświetlać projekty zorganizowane logicznie według celów. Wybierz **widok obiektów docelowych** z listy rozwijanej na pasku narzędzi **Eksplorator rozwiązań** :

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png)

Program Visual Studio używa pliku o nazwie **pliku cmakesettings. JSON** do przechowywania zmiennych środowiskowych lub opcji wiersza polecenia programu CMAKE. exe. **Pliku cmakesettings. JSON** umożliwia także Definiowanie i przechowywanie wielu konfiguracji kompilacji CMAKE i wygodne przełączanie się między nimi w środowisku IDE. W programie Visual Studio 2019 **Edytor ustawień CMAKE** zapewnia wygodny sposób edytowania ustawień. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md) .

W przeciwnym razie użyj **CMakeLists. txt** tak jak w każdym projekcie cmake, aby określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora, a także określić inne informacje dotyczące systemu kompilacji.

Jeśli musisz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **Launch. vs. JSON**. W niektórych scenariuszach program Visual Studio będzie automatycznie generować te pliki. można edytować je ręcznie. Możesz również samodzielnie utworzyć plik.

> [!NOTE]
> W przypadku innych rodzajów projektów otwartych folderów są używane dwa dodatkowe pliki JSON: **pliku cppproperties. JSON** i **Tasks. vs. JSON**. Żadna z tych elementów nie jest istotna dla projektów CMake.

## <a name="open-an-existing-cache"></a>Otwieranie istniejącej pamięci podręcznej

Po otwarciu istniejącej pamięci podręcznej CMake program Visual Studio nie podejmie próby zarządzania pamięcią podręczną i drzewem kompilacji. Dzięki temu niestandardowe lub preferowane narzędzia mają pełną kontrolę nad sposobem konfigurowania projektu przez program CMake. Istnieje możliwość otwarcia istniejącej pamięci podręcznej w programie Visual Studio za pośrednictwem **pliku > otwórz > CMAKE** i przechodzenie do istniejącego pliku CMakeCache. txt. Alternatywnie, jeśli projekt został już otwarty w programie Visual Studio, można dodać do niego istniejącą pamięć podręczną w taki sam sposób, jak dodać nową konfigurację. Aby uzyskać więcej informacji, zobacz nasz wpis w blogu na temat [otwierania istniejącej pamięci podręcznej w programie Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Kompilowanie projektów CMake

Aby skompilować projekt CMake, możesz wybrać następujące opcje:

1. Na pasku narzędzi Ogólne znajdź listę rozwijaną **konfiguracje** . Prawdopodobnie domyślnie jest wyświetlana wartość "x64-debug". Wybierz żądaną konfigurację i naciśnij klawisz **F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie kompiluje się jako pierwszy, podobnie jak rozwiązanie Visual Studio.

1. Kliknij prawym przyciskiem myszy CMakeLists. txt i wybierz opcję **Kompiluj** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystko lub tylko jeden określony element docelowy.

1. Z menu głównego wybierz kolejno opcje **kompiluj > Kompiluj wszystko** (**F7** lub **Ctrl + Shift + B**). Upewnij się, że element docelowy CMake został już wybrany na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** .

![Polecenie menu kompilacji CMAKE](media/cmake-build-menu.png "CMAKE Kompilacja menu poleceń")

Można dostosować konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia bez modyfikowania pliku CMakeLists. txt przy użyciu **edytora ustawień CMAKE**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).

Zgodnie z oczekiwaniami wyniki kompilacji są wyświetlane w **okno dane wyjściowe** i **Lista błędów**.

![CMAKE błędy]kompilacji(media/cmake-build-errors.png "CMAKE błędy kompilacji")

W folderze z wieloma obiektami docelowymi kompilacji możesz wybrać element **kompilacja** w menu **CMAKE** lub menu kontekstowego **CMakeLists. txt** , aby określić, który element docelowy CMAKE ma zostać skompilowany. Naciśnięcie **klawiszy Ctrl + Shift + B** w projekcie CMAKE kompiluje bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz żądaną konfigurację i naciśnij klawisz **F5**lub naciśnij przycisk **Run (Uruchom** ) na pasku narzędzi. Jeśli przycisk **Uruchom** ma wartość "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz obiekt docelowy, który chcesz uruchomić. (W projekcie CMake opcja "bieżący dokument" jest prawidłowa tylko dla plików. cpp).

Przycisk ![uruchamiania CMAKE](media/cmake-run-button.png "CMAKE przycisk uruchamiania")

Polecenia **Uruchom** lub **F5** najpierw kompilują projekt, jeśli wprowadzono zmiany od czasu poprzedniej kompilacji.

Sesję debugowania CMake można dostosować przez ustawienie właściwości w pliku **Launch. vs. JSON** . Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMAKE](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Tylko mój kod projektów CMake

Podczas kompilowania dla systemu Windows za pomocą kompilatora MSVC, projekty CMake obsługują funkcję tylko mój kod debugowania w kompilatorze i konsolidatorze, jeśli opcja jest włączona w programie Visual Studio. Aby zmienić to ustawienie, przejdź do pozycji **narzędzia** > **Options** > **debugowanie** > **Ogólne**.

## <a name="vcpkg-integration"></a>Integracja Vcpkg

Jeśli zainstalowano [vcpkg](vcpkg.md), projekty CMAKE otwarte w programie Visual Studio automatycznie integrują plik vcpkg łańcucha narzędzi. Oznacza to, że żadna dodatkowa konfiguracja nie jest wymagana do używania vcpkg z projektami CMake. Ta obsługa działa zarówno w przypadku lokalnych instalacji vcpkg, jak i instalacji vcpkg w systemach zdalnych, które są przeznaczone do celów. To zachowanie jest wyłączone automatycznie po określeniu innych łańcucha narzędzi w konfiguracji ustawień CMake.

## <a name="customize-configuration-feedback"></a>Dostosowywanie informacji o konfiguracji

Domyślnie większość komunikatów konfiguracyjnych jest pomijana, o ile wystąpi błąd. Aby wyświetlić wszystkie komunikaty, Włącz tę funkcję w obszarze **narzędzia** > **Options** > **CMAKE**.

   ![Konfigurowanie opcji diagnostycznych CMAKE](media/vs2019-cmake-configure-options.png "CMAKE opcje diagnostyczne")

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists. txt

Aby edytować plik CMakeLists. txt, kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku, zostanie wyświetlony żółty pasek stanu z informacją o tym, że IntelliSense zaktualizuje, i umożliwi Ci anulowanie operacji aktualizacji. Informacje o CMakeLists. txt znajdują się w [dokumentacji CMAKE](https://cmake.org/documentation/).

   ![CMakeLists. txt]— Edycja(media/cmake-cmakelists.png "pliku CMakeLists. txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie uruchomiony ponownie i zostaną wyświetlone informacje w oknie **danych wyjściowych** . Błędy i ostrzeżenia są wyświetlane w oknie **Lista błędów** lub **dane wyjściowe** . Kliknij dwukrotnie błąd w **Lista błędów** , aby przejść do wiersza powodującego problemy w CMakeLists. txt.

   Błędy plików ![CMakeLists. txt](media/cmake-cmakelists-error.png "CMakeLists. txt")


## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Po wprowadzeniu znaczących zmian w plikach **pliku cmakesettings. JSON** lub CMakeLists. txt program Visual Studio automatycznie ponownie uruchamia krok konfiguracji CMAKE. Jeśli krok konfiguracji zakończy się bez błędów, zbierane informacje są dostępne w C++ ramach funkcji IntelliSense i usług językowych, a także w operacjach kompilowania i debugowania.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z pamięcią podręczną CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **projektu** lub menu kontekstowe **CMakeLists. txt** w **Eksplorator rozwiązań** , aby uruchomić jedno z następujących poleceń:

- **Wyświetl pamięć podręczną** otwiera plik CMakeCache. txt z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone w tym miejscu do CMakeCache. txt są czyszczone w przypadku oczyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są utrwalane po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** powoduje otwarcie okna Eksploratora w folderze głównym kompilacji.

- **Czyszczenie pamięci podręcznej** powoduje usunięcie głównego folderu kompilacji, dzięki czemu następny krok CMAKE Konfiguruj rozpocznie się z czystej pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza, aby krok generowania był uruchamiany nawet wtedy, gdy program Visual Studio uzna, że środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie **narzędzia > opcje > CMake > ogólne** .

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalator programu Visual Studio, można uruchomić je z poziomu wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiedni vsdevcmd. bat (x86/x64). Aby uzyskać więcej informacji [, zobacz Kompilowanie w wierszu polecenia](building-on-the-command-line.md) .

1. Przejdź do folderu wyjściowego.

1. Uruchom CMake, aby skompilować/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2017"

Program Visual Studio 2017 ma rozbudowaną obsługę CMake, w tym [wieloplatformowych projektów CMAKE](../linux/cmake-linux-project.md). Składnik **Visual C++ Tools for CMAKE** korzysta z funkcji **Otwórz folder** , aby umożliwić środowisku IDE korzystanie z plików projektu CMAKE (takich jak CMakeLists. txt) bezpośrednio na potrzeby funkcji IntelliSense i przeglądania. Obsługiwane są zarówno generatory ninja, jak i Visual Studio. Jeśli używasz generatora programu Visual Studio, tymczasowy plik projektu jest generowany i przenoszona do programu MSBuild. exe, ale nigdy nie jest ładowany do funkcji IntelliSense ani do przeglądania. Istnieje również możliwość zaimportowania istniejącej pamięci podręcznej CMake. 

## <a name="installation"></a>Instalacja

**Narzędzia C++ wizualne dla programu CMAKE** są instalowane domyślnie w ramach **tworzenia C++ aplikacji dla komputerów stacjonarnych** i w ramach tworzenia obciążeń w  **C++ systemie Linux** .

![Składnik CMake w C++ obciążeniu pulpitu](media/cmake-install.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie C++ obciążenia systemu Linux w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja IDE

Po wybraniu opcji **plik > Otwórz folder >** , aby otworzyć folder zawierający plik CMakeLists. txt:

- Program Visual Studio dodaje do menu głównego element menu **CMAKE** z poleceniami służącymi do wyświetlania i edytowania skryptów CMAKE.

- **Eksplorator rozwiązań** Wyświetla strukturę folderów i pliki.

- Program Visual Studio uruchamia CMake. exe i opcjonalnie generuje pamięć podręczną CMake dla *konfiguracji*domyślnej, która jest debugowaniem x86. Wiersz polecenia CMake jest wyświetlany w **okno dane wyjściowe**wraz z dodatkowymi danymi wyjściowymi z CMAKE.

- W tle program Visual Studio zaczyna indeksować pliki źródłowe w celu włączenia funkcji IntelliSense, przeglądania informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować synchronizację indeksu ze źródłami.

Można otwierać foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie pliki "root" CMakeLists. txt w obszarze roboczym. Operacje CMake (Konfigurowanie, kompilowanie, debugowanie) oraz funkcja C++ IntelliSense i przeglądanie są dostępne dla wszystkich projektów CMAKE w obszarze roboczym.

![CMake projekt z wieloma katalogami głównymi](media/cmake-multiple-roots.png)

Możesz również wyświetlać projekty zorganizowane logicznie według celów. Wybierz **widok obiektów docelowych** z listy rozwijanej na pasku narzędzi **Eksplorator rozwiązań** :

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png)

Program Visual Studio używa pliku o nazwie **pliku cmakesettings. JSON** do przechowywania zmiennych środowiskowych lub opcji wiersza polecenia programu CMAKE. exe. **Pliku cmakesettings. JSON** umożliwia także Definiowanie i przechowywanie wielu konfiguracji kompilacji CMAKE i wygodne przełączanie się między nimi w środowisku IDE. 

W przeciwnym razie użyj **CMakeLists. txt** tak samo jak w każdym projekcie cmake, aby określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora i określić inne informacje dotyczące systemu kompilacji.

Jeśli musisz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **Launch. vs. JSON**. W niektórych scenariuszach program Visual Studio będzie automatycznie generować te pliki. można edytować je ręcznie. Możesz również samodzielnie utworzyć plik.

> [!NOTE]
> W przypadku innych rodzajów projektów otwartych folderów są używane dwa dodatkowe pliki JSON: **pliku cppproperties. JSON** i **Tasks. vs. JSON**. Żadna z tych elementów nie jest istotna dla projektów CMake.

## <a name="import-an-existing-cache"></a>Importowanie istniejącej pamięci podręcznej

Podczas importowania istniejącego pliku CMakeCache. txt program Visual Studio automatycznie wyodrębnia dostosowane zmienne i tworzy wstępnie wypełniony plik **pliku cmakesettings. JSON** na podstawie tych elementów. Oryginalna pamięć podręczna nie jest modyfikowana w żaden sposób i nadal może być używana z wiersza polecenia lub z dowolnym narzędziem lub środowiskiem IDE użytym do jego wygenerowania. Nowy plik **pliku cmakesettings. JSON** zostanie umieszczony obok głównego pliku CMakeLists. txt projektu. Program Visual Studio generuje nową pamięć podręczną opartą na pliku ustawień. Automatyczne generowanie pamięci podręcznej można przesłonić w oknie **narzędzia > opcje > CMake > ogólne** .

Nie wszystkie elementy w pamięci podręcznej są importowane.  Właściwości, takie jak generator i lokalizacja kompilatorów, są zastępowane wartościami domyślnymi, które są znane do pracy z IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejącą pamięć podręczną

1. Z menu głównego wybierz kolejno pozycje **plik > otwórz > CMAKE**:

   ![Otwórz plik CMAKE](media/cmake-file-open.png ", Otwórz, CMAKE")

   Spowoduje to wyświetlenie kreatora **importu CMAKE z pamięci podręcznej** .

2. Przejdź do pliku CMakeCache. txt, który chcesz zaimportować, a następnie kliknij przycisk **OK**. Zostanie wyświetlony Kreator **importowania projektu CMAKE z pamięci podręcznej** :

   ![Importowanie pamięci podręcznej CMAKE](media/cmake-import-wizard.png "otwieranie Kreatora importu pamięci podręcznej CMAKE")

   Po zakończeniu pracy kreatora można zobaczyć nowy plik CMakeCache. txt w **Eksplorator rozwiązań** obok głównego pliku CMakeLists. txt w projekcie.

## <a name="building-cmake-projects"></a>Kompilowanie projektów CMake

Aby skompilować projekt CMake, możesz wybrać następujące opcje:

1. Na pasku narzędzi Ogólne znajdź listę rozwijaną **konfiguracje** ; prawdopodobnie domyślnie jest wyświetlany ekran "Linux-debug" lub "x64-debug". Wybierz żądaną konfigurację i naciśnij klawisz **F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie kompiluje się jako pierwszy, podobnie jak rozwiązanie Visual Studio.

1. Kliknij prawym przyciskiem myszy CMakeLists. txt i wybierz opcję **Kompiluj** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystko lub tylko jeden określony element docelowy.

1. Z menu głównego wybierz kolejno opcje **kompiluj > Kompiluj rozwiązanie** (**F7** lub **Ctrl + Shift + B**). Upewnij się, że element docelowy CMake został już wybrany na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** .

![Polecenie menu kompilacji CMAKE](media/cmake-build-menu.png "CMAKE Kompilacja menu poleceń")

Można dostosować konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia bez modyfikowania pliku CMakeLists. txt przy użyciu pliku **pliku cmakesettings. JSON** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).

Zgodnie z oczekiwaniami wyniki kompilacji są wyświetlane w **okno dane wyjściowe** i **Lista błędów**.

![CMAKE błędy]kompilacji(media/cmake-build-errors.png "CMAKE błędy kompilacji")

W folderze z wieloma obiektami docelowymi kompilacji możesz wybrać element **kompilacja** w menu **CMAKE** lub menu kontekstowego **CMakeLists. txt** , aby określić, który element docelowy CMAKE ma zostać skompilowany. Naciśnięcie **klawiszy Ctrl + Shift + B** w projekcie CMAKE kompiluje bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz żądaną konfigurację i naciśnij klawisz **F5**lub naciśnij przycisk **Run (Uruchom** ) na pasku narzędzi. Jeśli przycisk **Uruchom** ma wartość "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz obiekt docelowy, który chcesz uruchomić. (W projekcie CMake opcja "bieżący dokument" jest prawidłowa tylko dla plików. cpp).

Przycisk ![uruchamiania CMAKE](media/cmake-run-button.png "CMAKE przycisk uruchamiania")

Polecenia **Uruchom** lub **F5** najpierw kompilują projekt, jeśli wprowadzono zmiany od czasu poprzedniej kompilacji.

Sesję debugowania CMake można dostosować przez ustawienie właściwości w pliku **Launch. vs. JSON** . Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMAKE](configure-cmake-debugging-sessions.md).


## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists. txt

Aby edytować plik CMakeLists. txt, kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku, zostanie wyświetlony żółty pasek stanu z informacją o tym, że IntelliSense zaktualizuje, i umożliwi Ci anulowanie operacji aktualizacji. Informacje o CMakeLists. txt znajdują się w [dokumentacji CMAKE](https://cmake.org/documentation/).

   ![CMakeLists. txt]— Edycja(media/cmake-cmakelists.png "pliku CMakeLists. txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie uruchomiony ponownie i zostaną wyświetlone informacje w oknie **danych wyjściowych** . Błędy i ostrzeżenia są wyświetlane w oknie **Lista błędów** lub **dane wyjściowe** . Kliknij dwukrotnie błąd w **Lista błędów** , aby przejść do wiersza powodującego problemy w CMakeLists. txt.

   Błędy plików ![CMakeLists. txt](media/cmake-cmakelists-error.png "CMakeLists. txt")


## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Po wprowadzeniu znaczących zmian w plikach **pliku cmakesettings. JSON** lub CMakeLists. txt program Visual Studio automatycznie ponownie uruchamia krok konfiguracji CMAKE. Jeśli krok konfiguracji zakończy się bez błędów, zbierane informacje są dostępne w C++ ramach funkcji IntelliSense i usług językowych, a także w operacjach kompilowania i debugowania.

Gdy wiele projektów CMake korzysta z tej samej nazwy konfiguracji CMake (na przykład x86-Debug), wszystkie z nich są skonfigurowane i kompilowane (we własnym folderze głównym kompilacji), gdy ta konfiguracja jest zaznaczona. Można debugować cele ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji CMake.

   ![CMAKE Kompiluj tylko element menu](media/cmake-build-only.png "CMAKE tylko Kompiluj element menu")

Aby ograniczyć kompilacje i debugować sesje do podzbioru projektów w obszarze roboczym, Utwórz nową konfigurację o unikatowej nazwie w pliku **pliku cmakesettings. JSON** i Zastosuj ją tylko do tych projektów. Po wybraniu tej konfiguracji polecenia IntelliSense i kompilowanie oraz debugowanie są włączone tylko dla tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z pamięcią podręczną CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **CMAKE** lub menu kontekstowe **CMakeLists. txt** w **Eksplorator rozwiązań** , aby uruchomić jedno z następujących poleceń:

- **Wyświetl pamięć podręczną** otwiera plik CMakeCache. txt z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone w tym miejscu do CMakeCache. txt są czyszczone w przypadku oczyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są utrwalane po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** powoduje otwarcie okna Eksploratora w folderze głównym kompilacji.

- **Czyszczenie pamięci podręcznej** powoduje usunięcie głównego folderu kompilacji, dzięki czemu następny krok CMAKE Konfiguruj rozpocznie się z czystej pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza, aby krok generowania był uruchamiany nawet wtedy, gdy program Visual Studio uzna, że środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie **narzędzia > opcje > CMake > ogólne** .

## <a name="single-file-compilation"></a>Kompilacja pojedynczego pliku

Aby skompilować pojedynczy plik w projekcie CMake, kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Kompiluj**. Możesz również utworzyć plik, który jest aktualnie otwarty w edytorze przy użyciu głównego menu CMake:

![Kompilacja pojedynczego pliku CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalator programu Visual Studio, można uruchomić je z poziomu wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiedni vsdevcmd. bat (x86/x64). Aby uzyskać więcej informacji [, zobacz Kompilowanie w wierszu polecenia](building-on-the-command-line.md) .

1. Przejdź do folderu wyjściowego.

1. Uruchom CMake, aby skompilować/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2015"

W programie Visual Studio 2015 użytkownicy programu Visual Studio mogą używać [generatora CMAKE](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) do generowania plików projektu MSBuild, które następnie wykorzystuje środowisko IDE do IntelliSense, przeglądania i kompilowania.

::: moniker-end


## <a name="see-also"></a>Zobacz także

[Samouczek: Tworzenie C++ projektów dla wielu platform w programie Visual Studio](get-started-linux-cmake.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Dostosuj ustawienia kompilacji CMake](customize-cmake-settings.md)<br/>
[Odwołanie pliku cmakesettings. JSON](cmakesettings-reference.md)<br/>
[Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)<br/>
