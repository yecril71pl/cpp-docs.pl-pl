---
title: CMake projekty w programie Visual Studio
description: Jak tworzyć i kompilować projekty języka C++ za pomocą CMake w programie Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: a4eea2b321bc07fc40c9a42b3ce515435e808ee4
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685035"
---
# <a name="cmake-projects-in-visual-studio"></a>CMake projekty w programie Visual Studio

CMake to międzyplatformowe narzędzie typu open source służące do definiowania procesów kompilacji, które są uruchamiane na wielu platformach. W tym artykule założono, że znasz już CMake. Więcej informacji na ten temat można znaleźć w witrynie [kompilacja, testowanie i pakowanie oprogramowania przy użyciu CMAKE](https://cmake.org/).

> [!NOTE]
> CMake stał się bardziej i bardziej zintegrowany z programem Visual Studio w ciągu ostatnich kilku wydań. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

Składnik **C++ CMAKE Tools for Windows** korzysta z funkcji [Otwórz folder](open-folder-projects-cpp.md) , aby używać plików projektu CMake (takich jak *CMakeLists.txt*) bezpośrednio na potrzeby funkcji IntelliSense i przeglądania. Obsługiwane są zarówno generatory ninja, jak i Visual Studio. Jeśli używasz generatora programu Visual Studio, generuje on tymczasowy plik projektu i przekazuje go do msbuild.exe. Jednak projekt nigdy nie jest ładowany do celów IntelliSense ani do przeglądania. Istnieje również możliwość zaimportowania istniejącej pamięci podręcznej CMake.

## <a name="installation"></a>Instalacja

**Narzędzia C++ CMAKE Tools for Windows** są instalowane w ramach **programowania aplikacji klasycznych w języku c++** i **Linux przy użyciu obciążeń języka c++** . Aby uzyskać więcej informacji, zobacz [Międzyplatformowe projekty CMAKE](../linux/cmake-linux-project.md).

![Zrzut ekranu przedstawiający Programowanie aplikacji klasycznych z wybranym listą rozwijaną C i Plus oraz poleceniem C + + C Utwórz narzędzia dla systemu Windows o nazwie wychodzącej.](media/cmake-install-2019.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie obciążeń C++ Linux w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja IDE

Po wybraniu opcji **plik > Otwórz folder >** , aby otworzyć folder zawierający plik *CMakeLists.txt* , następujące kwestie zachodzą poniżej:

- Program Visual Studio dodaje **CMAKE** elementy do menu **projekt** z poleceniami służącymi do wyświetlania i edytowania skryptów CMAKE.

- **Eksplorator rozwiązań** Wyświetla strukturę folderów i pliki.

- Program Visual Studio działa cmake.exe i generuje plik pamięci podręcznej CMake (*CMakeCache.txt*) dla konfiguracji domyślnej (debugowanie x64). Wiersz polecenia CMake jest wyświetlany w **okno dane wyjściowe**wraz z dodatkowymi danymi wyjściowymi z CMAKE.

- W tle program Visual Studio zaczyna indeksować pliki źródłowe w celu włączenia funkcji IntelliSense, przeglądania informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować synchronizację indeksu ze źródłami.

Można otwierać foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie pliki "root" *CMakeLists.txt* w obszarze roboczym. Operacje CMake (Konfigurowanie, kompilowanie, debugowanie), IntelliSense w języku C++ i przeglądanie są dostępne dla wszystkich projektów CMake w Twoim obszarze roboczym.

![CMake projekt z wieloma katalogami głównymi](media/cmake-multiple-roots.png)

Możesz również wyświetlać projekty zorganizowane logicznie według celów. Wybierz **widok obiektów docelowych** z listy rozwijanej na pasku narzędzi **Eksplorator rozwiązań** :

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png)

Kliknij przycisk **Pokaż wszystkie pliki** w górnej części **Eksplorator rozwiązań** , aby wyświetlić wszystkie dane wyjściowe generowane przez CMAKE w folderze *out/Build/ \<config> * .

Program Visual Studio używa pliku konfiguracji o nazwie **CMakeSettings.json**. Ten plik umożliwia definiowanie i przechowywanie wielu konfiguracji kompilacji oraz wygodne przełączanie się między nimi w środowisku IDE. *Konfiguracja* to konstrukcja programu Visual Studio, która hermetyzuje ustawienia specyficzne dla danego typu kompilacji. Ustawienia służą do konfigurowania domyślnych opcji wiersza polecenia, które program Visual Studio przekazuje do cmake.exe. W tym miejscu możesz również określić dodatkowe opcje CMake i zdefiniować wszelkie dodatkowe zmienne, które chcesz. Wszystkie opcje są zapisywane w pamięci podręcznej CMake jako zmienne wewnętrzne lub zewnętrzne. W programie Visual Studio 2019 **Edytor ustawień CMAKE** zapewnia wygodny sposób edytowania ustawień. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).

Jedno ustawienie `intelliSenseMode` nie jest przesyłane do cmake, ale jest używane tylko przez program Visual Studio.

Użyj pliku **CMakeLists.txt** w każdym folderze projektu tak samo jak w każdym projekcie CMAKE. Można określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora, a także określić inne informacje związane z systemem kompilacji.

Aby przekazać argumenty do pliku wykonywalnego w czasie debugowania, można użyć innego pliku o nazwie **launch.vs.jsna**. W niektórych scenariuszach program Visual Studio automatycznie generuje te pliki. Można edytować je ręcznie, a nawet samodzielnie tworzyć pliki.

> [!NOTE]
> W przypadku innych rodzajów projektów typu "Open folder" są używane dwa dodatkowe pliki JSON: **CppProperties.json** i **tasks.vs.json**. Żadna z tych elementów nie jest istotna dla projektów CMake.

## <a name="open-an-existing-cache"></a>Otwieranie istniejącej pamięci podręcznej

Gdy otworzysz istniejący plik pamięci podręcznej CMake (*CMakeCache.txt*), program Visual Studio nie spróbuje zarządzać pamięcią podręczną i drzewem kompilacji. Niestandardowe lub preferowane narzędzia mają pełną kontrolę nad sposobem konfigurowania projektu przez program CMake. Aby otworzyć istniejącą pamięć podręczną w programie Visual Studio, wybierz pozycję **plik > otwórz > CMAKE**. Następnie przejdź do istniejącego pliku *CMakeCache.txt* .

Do otwartego projektu można dodać istniejącą pamięć podręczną CMake. W ten sam sposób można dodać nową konfigurację. Aby uzyskać więcej informacji, zobacz nasz wpis w blogu na temat [otwierania istniejącej pamięci podręcznej w programie Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Kompilowanie projektów CMake

Aby skompilować projekt CMake, możesz wybrać następujące opcje:

1. Na pasku narzędzi Ogólne znajdź listę rozwijaną **konfiguracje** . Prawdopodobnie domyślnie jest wyświetlana wartość "x64-debug". Wybierz preferowaną konfigurację i naciśnij klawisz **F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie kompiluje się jako pierwszy, podobnie jak rozwiązanie Visual Studio.

1. Kliknij prawym przyciskiem myszy *CMakeLists.txt* i wybierz opcję **Kompiluj** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystko lub tylko jeden określony element docelowy.

1. Z menu głównego wybierz kolejno opcje **kompiluj > Kompiluj wszystko** (**F7** lub **Ctrl + Shift + B**). Upewnij się, że element docelowy CMake został już wybrany na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** .

![CMake — polecenie menu kompilacji](media/cmake-build-menu.png "Menu poleceń kompilacji CMake")

Zgodnie z oczekiwaniami wyniki kompilacji są wyświetlane w **okno dane wyjściowe** i **Lista błędów**.

![Błędy kompilacji CMake](media/cmake-build-errors.png "Błędy kompilacji CMake")

W folderze z wieloma obiektami docelowymi kompilacji można określić, który element docelowy CMake do skompilowania: Wybierz element **Build** w menu **CMAKE** lub menu kontekstowego *CMakeLists.txt* , aby określić element docelowy. Jeśli wprowadzisz **kombinację klawiszy Ctrl + Shift + B** w projekcie cmake, kompiluje bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz preferowaną konfigurację i naciśnij klawisz **F5**lub naciśnij przycisk **Run (Uruchom** ) na pasku narzędzi. Jeśli przycisk **Uruchom** ma wartość "Wybierz element startowy", wybierz strzałkę listy rozwijanej. Wybierz obiekt docelowy, który chcesz uruchomić. (W projekcie CMake opcja "bieżący dokument" jest prawidłowa tylko dla plików. cpp).

![Przycisk uruchamiania CMake](media/cmake-run-button.png "Przycisk uruchamiania CMake")

Polecenia **Uruchom** lub **F5** najpierw kompilują projekt, jeśli wprowadzono zmiany od czasu poprzedniej kompilacji. Zmiany *CMakeSettings.jsna* wygenerowanie pamięci podręcznej CMAKE.

Można dostosować sesję debugowania CMake przez ustawienie właściwości w **launch.vs.js** pliku. Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMAKE](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Tylko mój kod projektów CMake

Podczas kompilowania dla systemu Windows za pomocą kompilatora MSVC, projekty CMake obsługują debugowanie Tylko mój kod. Aby zmienić ustawienie tylko mój kod, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **debugowanie**  >  **Ogólne**.

## <a name="vcpkg-integration"></a>Integracja Vcpkg

Jeśli zainstalowano [vcpkg](vcpkg.md), projekty CMAKE otwarte w programie Visual Studio automatycznie integrują plik vcpkg łańcucha narzędzi. Oznacza to, że żadna dodatkowa konfiguracja nie jest wymagana do używania vcpkg z projektami CMake. Ta obsługa działa zarówno w przypadku lokalnych instalacji vcpkg, jak i instalacji vcpkg w systemach zdalnych, które są przeznaczone do celów. To zachowanie jest wyłączone automatycznie po określeniu innych łańcucha narzędzi w konfiguracji ustawień CMake.

## <a name="customize-configuration-feedback"></a>Dostosowywanie informacji o konfiguracji

Domyślnie większość komunikatów konfiguracyjnych jest pomijana, o ile wystąpi błąd. Aby wyświetlić wszystkie komunikaty, Włącz tę funkcję w opcji **Narzędzia**  >  **Options**  >  **CMAKE**.

   ![Konfigurowanie opcji diagnostycznych CMake](media/vs2019-cmake-configure-options.png "Opcje diagnostyki CMake")

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists.txt

Aby edytować plik *CMakeLists.txt* , kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**. Po wprowadzeniu zmian w pliku zostanie wyświetlony żółty pasek stanu z informacją o tym, że IntelliSense zaktualizuje. Pozwala to na anulowanie operacji aktualizacji. Aby uzyskać informacje na temat *CMakeLists.txt*, zobacz [dokumentację CMAKE](https://cmake.org/documentation/).

   ![ Edycja plikuCMakeLists.txt](media/cmake-cmakelists.png "Edycja pliku CMakeLists.txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie uruchomiony ponownie i zostaną wyświetlone informacje w oknie **danych wyjściowych** . Błędy i ostrzeżenia są wyświetlane w oknie **Lista błędów** lub **dane wyjściowe** . Kliknij dwukrotnie błąd w **Lista błędów** , aby przejść do wiersza błędnego w *CMakeLists.txt*.

   ![ Błędy plikówCMakeLists.txt](media/cmake-cmakelists-error.png "Błędy plików CMakeLists.txt")

## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Po wprowadzeniu znaczących zmian w *CMakeSettings.js* lub *CMakeLists.txt* plików program Visual Studio automatycznie ponownie uruchamia krok konfigurowania CMAKE. Jeśli krok konfiguracji zakończy się bez błędów, zbierane informacje są dostępne w języku C++ IntelliSense i w usługach językowych. Jest on również używany w operacjach kompilowania i debugowania.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z pamięcią podręczną CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **projektu** lub menu kontekstowe *CMakeLists.txt* w **Eksplorator rozwiązań** , aby uruchomić jedno z następujących poleceń:

- **Wyświetl pamięć podręczną** otwiera plik *CMakeCache.txt* z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone w tym miejscu *CMakeCache.txt* są czyszczone w przypadku oczyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są utrwalane po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** powoduje otwarcie okna Eksploratora w folderze głównym kompilacji.

- **Czyszczenie pamięci podręcznej** powoduje usunięcie głównego folderu kompilacji, dzięki czemu następny krok CMAKE Konfiguruj rozpocznie się z czystej pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza, aby krok generowania był uruchamiany nawet wtedy, gdy program Visual Studio uzna, że to środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie **narzędzia > opcje > CMake > ogólne** .

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalator programu Visual Studio, można uruchomić je z poziomu wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiednie vsdevcmd.bat (x86/x64). Aby uzyskać więcej informacji, zobacz [Kompilowanie w wierszu polecenia](building-on-the-command-line.md).

1. Przejdź do folderu wyjściowego.

1. Uruchom CMake, aby skompilować/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2017"

Program Visual Studio 2017 ma rozbudowaną obsługę CMake, w tym [wieloplatformowych projektów CMAKE](../linux/cmake-linux-project.md). Składnik **Visual C++ Tools for CMAKE** korzysta z funkcji **Otwórz folder** , aby umożliwić IDE korzystanie z plików projektu CMake (takich jak *CMakeLists.txt*) bezpośrednio na potrzeby funkcji IntelliSense i przeglądania. Obsługiwane są zarówno generatory ninja, jak i Visual Studio. Jeśli używasz generatora programu Visual Studio, generuje on tymczasowy plik projektu i przekazuje go do msbuild.exe. Jednak projekt nigdy nie jest ładowany do celów IntelliSense ani do przeglądania. Istnieje również możliwość zaimportowania istniejącej pamięci podręcznej CMake.

## <a name="installation"></a>Instalacja

**Narzędzia Visual C++ Tools for CMAKE** są instalowane w ramach **programowania aplikacji klasycznych w języku c++** i **Linux przy użyciu obciążeń języka c++** .

![Zrzut ekranu przedstawiający kartę poszczególne składniki z narzędziami Visual C plus plus dla języka C.](media/cmake-install.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie obciążeń C++ Linux w programie Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integracja środowiska IDE

Po wybraniu opcji **plik > Otwórz folder >** , aby otworzyć folder zawierający plik *CMakeLists.txt* , następujące kwestie zachodzą poniżej:

- Program Visual Studio dodaje do menu głównego element menu **CMAKE** z poleceniami służącymi do wyświetlania i edytowania skryptów CMAKE.

- **Eksplorator rozwiązań** Wyświetla strukturę folderów i pliki.

- Program Visual Studio działa CMake.exe i opcjonalnie generuje pamięć podręczną CMake dla *konfiguracji*domyślnej, która jest debugowaniem x86. Wiersz polecenia CMake jest wyświetlany w **okno dane wyjściowe**wraz z dodatkowymi danymi wyjściowymi z CMAKE.

- W tle program Visual Studio zaczyna indeksować pliki źródłowe w celu włączenia funkcji IntelliSense, przeglądania informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować synchronizację indeksu ze źródłami.

Można otwierać foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie pliki "root" *CMakeLists.txt* w obszarze roboczym. Operacje CMake (Konfigurowanie, kompilowanie, debugowanie), IntelliSense w języku C++ i przeglądanie są dostępne dla wszystkich projektów CMake w Twoim obszarze roboczym.

![CMake projekt z wieloma katalogami głównymi](media/cmake-multiple-roots.png)

Możesz również wyświetlać projekty zorganizowane logicznie według celów. Wybierz **widok obiektów docelowych** z listy rozwijanej na pasku narzędzi **Eksplorator rozwiązań** :

![Przycisk Widok elementów docelowych CMake](media/cmake-targets-view.png)

Program Visual Studio używa pliku o nazwie *CMakeSettings.jsna* potrzeby przechowywania zmiennych środowiskowych lub opcji wiersza polecenia Cmake.exe. *CMakeSettings.json* umożliwia także Definiowanie i przechowywanie wielu konfiguracji kompilacji CMAKE. Można wygodnie przełączać się między nimi w środowisku IDE.

W przeciwnym razie użyj *CMakeLists.txt* tak samo jak w każdym projekcie cmake, aby określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora, a także określić inne informacje związane z systemem kompilacji.

Jeśli musisz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **launch.vs.jsna**. W niektórych scenariuszach program Visual Studio automatycznie generuje te pliki. Można edytować je ręcznie, a nawet samodzielnie tworzyć pliki.

> [!NOTE]
> W przypadku innych rodzajów projektów typu "Open folder" są używane dwa dodatkowe pliki JSON: **CppProperties.json** i **tasks.vs.json**. Żadna z tych elementów nie jest istotna dla projektów CMake.

## <a name="import-an-existing-cache"></a>Importowanie istniejącej pamięci podręcznej

Podczas importowania istniejącego pliku *CMakeCache.txt* program Visual Studio automatycznie wyodrębnia dostosowane zmienne i tworzy wstępnie wypełniony *CMakeSettings.jsna* pliku na podstawie tych elementów. Oryginalna pamięć podręczna nie jest w żaden sposób modyfikowana. Może być nadal używany z wiersza polecenia lub z dowolnym narzędziem lub środowiskiem IDE używanym do jego wygenerowania. Nowy  *CMakeSettings.jsw* pliku zostanie umieszczony obok *CMakeLists.txt*głównej projektu. Program Visual Studio generuje nową pamięć podręczną opartą na pliku ustawień. Automatyczne generowanie pamięci podręcznej można przesłonić w oknie **narzędzia > opcje > CMake > ogólne** .

Nie wszystkie elementy w pamięci podręcznej są importowane.  Właściwości, takie jak generator i lokalizacja kompilatorów, są zastępowane wartościami domyślnymi, które są znane do pracy z IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejącą pamięć podręczną

1. Z menu głównego wybierz kolejno pozycje **plik > otwórz > CMAKE**:

   ![Otwórz CMake](media/cmake-file-open.png "Plik, Otwórz, CMake")

   To polecenie powoduje wyświetlenie kreatora **importu CMAKE z pamięci podręcznej** .

2. Przejdź do pliku *CMakeCache.txt* , który chcesz zaimportować, a następnie kliknij przycisk **OK**. Zostanie wyświetlony Kreator **importowania projektu CMAKE z pamięci podręcznej** :

   ![Importowanie pamięci podręcznej CMake](media/cmake-import-wizard.png "Otwórz Kreatora importu pamięci podręcznej CMake")

   Po zakończeniu pracy Kreatora zobaczysz nowy plik *CMakeCache.txt* w **Eksplorator rozwiązań** obok głównego pliku *CMakeLists.txt* w projekcie.

## <a name="building-cmake-projects"></a>Kompilowanie projektów CMake

Aby skompilować projekt CMake, możesz wybrać następujące opcje:

1. Na pasku narzędzi Ogólne znajdź listę rozwijaną **konfiguracje** . Prawdopodobnie domyślnie jest wyświetlany ekran "Linux-debug" lub "x64-debug". Wybierz preferowaną konfigurację i naciśnij klawisz **F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie kompiluje się jako pierwszy, podobnie jak rozwiązanie Visual Studio.

1. Kliknij prawym przyciskiem myszy *CMakeLists.txt* i wybierz opcję **Kompiluj** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystko lub tylko jeden określony element docelowy.

1. Z menu głównego wybierz kolejno opcje **kompiluj > Kompiluj rozwiązanie** (**F7** lub **Ctrl + Shift + B**). Upewnij się, że element docelowy CMake został już wybrany na liście rozwijanej **elementu startowego** na pasku narzędzi **Ogólne** .

![CMake — polecenie menu kompilacji](media/cmake-build-menu.png "Menu poleceń kompilacji CMake")

Można dostosować konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia w *CMakeSettings.js* pliku. Umożliwia wprowadzanie zmian bez modyfikowania pliku *CMakeLists.txt* . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).

Zgodnie z oczekiwaniami wyniki kompilacji są wyświetlane w **okno dane wyjściowe** i **Lista błędów**.

![Błędy kompilacji CMake](media/cmake-build-errors.png "Błędy kompilacji CMake")

W folderze z wieloma obiektami docelowymi kompilacji można określić, który element docelowy CMake do skompilowania: Wybierz element **Build** w menu **CMAKE** lub menu kontekstowego *CMakeLists.txt* , aby określić element docelowy. Jeśli wprowadzisz **kombinację klawiszy Ctrl + Shift + B** w projekcie cmake, kompiluje bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz preferowaną konfigurację i naciśnij klawisz **F5**. Lub naciśnij przycisk **Run (Uruchom** ) na pasku narzędzi. Jeśli przycisk **Uruchom** ma wartość "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz obiekt docelowy, który chcesz uruchomić. (W projekcie CMake opcja "bieżący dokument" jest prawidłowa tylko dla plików. cpp).

![Przycisk uruchamiania CMake](media/cmake-run-button.png "Przycisk uruchamiania CMake")

Polecenia **Uruchom** lub **F5** najpierw kompilują projekt, jeśli wprowadzono zmiany od czasu poprzedniej kompilacji.

Można dostosować sesję debugowania CMake przez ustawienie właściwości w **launch.vs.js** pliku. Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMAKE](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists.txt

Aby edytować plik *CMakeLists.txt* , kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**. Po wprowadzeniu zmian w pliku zostanie wyświetlony żółty pasek stanu z informacją o tym, że IntelliSense zaktualizuje. Pozwala to na anulowanie operacji aktualizacji. Aby uzyskać informacje na temat *CMakeLists.txt*, zobacz [dokumentację CMAKE](https://cmake.org/documentation/).

   ![ Edycja plikuCMakeLists.txt](media/cmake-cmakelists.png "Edycja pliku CMakeLists.txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie uruchomiony ponownie i zostaną wyświetlone informacje w oknie **danych wyjściowych** . Błędy i ostrzeżenia są wyświetlane w oknie **Lista błędów** lub **dane wyjściowe** . Kliknij dwukrotnie błąd w **Lista błędów** , aby przejść do wiersza błędnego w *CMakeLists.txt*.

   ![ Błędy plikówCMakeLists.txt](media/cmake-cmakelists-error.png "Błędy plików CMakeLists.txt")

## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

Po wprowadzeniu znaczących zmian do  *CMakeSettings.js* lub do *CMakeLists.txt* plików program Visual Studio automatycznie ponownie uruchamia krok konfigurowania CMAKE. Jeśli krok konfiguracji zakończy się bez błędów, zbierane informacje są dostępne w języku C++ IntelliSense i w usługach językowych. Jest on również używany w operacjach kompilowania i debugowania.

Wiele projektów CMake może używać tej samej nazwy konfiguracji CMake (na przykład x86-Debug). Wszystkie z nich są konfigurowane i kompilowane (we własnym folderze głównym kompilacji), gdy ta konfiguracja jest wybrana. Można debugować cele ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji CMake.

   ![Element menu tylko dla kompilacji CMake](media/cmake-build-only.png "Element menu tylko dla kompilacji CMake")

Można ograniczyć kompilacje i debugować sesje do podzbioru projektów w obszarze roboczym. Utwórz nową konfigurację o unikatowej nazwie w  *CMakeSettings.js* pliku. Następnie Zastosuj konfigurację tylko do tych projektów. Po wybraniu tej konfiguracji, funkcja IntelliSense i polecenia Kompiluj i Debuguj stosują się tylko do tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z pamięcią podręczną CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **CMAKE** lub menu kontekstowe *CMakeLists.txt* w **Eksplorator rozwiązań** , aby uruchomić jedno z następujących poleceń:

- **Wyświetl pamięć podręczną** otwiera plik  *CMakeCache.txt* z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone w tym miejscu  *CMakeCache.txt* są czyszczone w przypadku oczyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są utrwalane po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMAKE](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** powoduje otwarcie okna Eksploratora w folderze głównym kompilacji.

- **Czyszczenie pamięci podręcznej** powoduje usunięcie głównego folderu kompilacji, dzięki czemu następny krok CMAKE Konfiguruj rozpocznie się z czystej pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza, aby krok generowania był uruchamiany nawet wtedy, gdy program Visual Studio uzna, że to środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie **narzędzia > opcje > CMake > ogólne** .

## <a name="single-file-compilation"></a>Kompilacja pojedynczego pliku

Aby skompilować pojedynczy plik w projekcie CMake, kliknij prawym przyciskiem myszy plik w **Eksplorator rozwiązań**. Wybierz opcję **Kompiluj** z menu podręcznego. Możesz również skompilować aktualnie otwarty plik w edytorze przy użyciu głównego menu **CMAKE** :

![Kompilacja pojedynczego pliku CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalator programu Visual Studio, można uruchomić je z poziomu wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiednie vsdevcmd.bat (x86/x64). Aby uzyskać więcej informacji, zobacz [Kompilowanie w wierszu polecenia](building-on-the-command-line.md) .

1. Przejdź do folderu wyjściowego.

1. Uruchom CMake, aby skompilować/skonfigurować aplikację.

::: moniker-end

::: moniker range="vs-2015"

W programie Visual Studio 2015 użytkownicy programu Visual Studio mogą używać [generatora CMAKE](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) do generowania plików projektu MSBuild, które następnie wykorzystuje środowisko IDE do IntelliSense, przeglądania i kompilowania.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Samouczek: Tworzenie projektów dla wielu platform C++ w programie Visual Studio](get-started-linux-cmake.md)\
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)\
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Dostosuj ustawienia kompilacji CMake](customize-cmake-settings.md)\
[CMakeSettings.jsodwołania do schematu](cmakesettings-reference.md)\
[Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)
