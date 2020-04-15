---
title: CZło projektów w programie Visual Studio
description: Jak tworzyć i tworzyć projekty języka C++ przy użyciu CMake w programie Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329161"
---
# <a name="cmake-projects-in-visual-studio"></a>CZło projektów w programie Visual Studio

CMake to wieloplatformowe narzędzie open source do definiowania procesów kompilacji, które działają na wielu platformach. W tym artykule założono, że jesteś zaznajomiony z CMake. Możesz dowiedzieć się więcej na ten temat w [Build, Test i Pakiet Oprogramowania z CMake](https://cmake.org/).

> [!NOTE]
> CMake stał się coraz bardziej zintegrowany z programem Visual Studio w ciągu ostatnich kilku wydań. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

**Narzędzia CMake języka C++ dla** składnika Windows używają funkcji Otwórz [folder](open-folder-projects-cpp.md) do korzystania z plików projektu CMake (takich jak *CMakeLists.txt)* bezpośrednio na potrzeby intellisense i przeglądania. Obsługiwane są generatory Ninja i Visual Studio. Jeśli używasz generatora programu Visual Studio, generuje tymczasowy plik projektu i przekazuje go do msbuild.exe. Jednak projekt nigdy nie jest ładowany do intellisense lub do celów przeglądania. Można również zaimportować istniejącą pamięć podręczną CMake.

## <a name="installation"></a>Instalacja

**Narzędzia C++ CMake dla systemu Windows** są instalowane w ramach **tworzenia pulpitu z programami C++** i Linux Development z obciążeniami **języka C++.** Aby uzyskać więcej informacji, zobacz [Międzyplatformowe projekty CMake](../linux/cmake-linux-project.md).

![Składnik CMake w obciążeniu pulpitu języka C++](media/cmake-install-2019.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie obciążenia systemu Linux w programie Visual Studio.](../linux/download-install-and-setup-the-linux-development-workload.md)

## <a name="ide-integration"></a>IDE Integration (Integracja środowiska IDE)

Po **wybraniu opcji File > Open > Folder** , aby otworzyć folder zawierający plik *CMakeLists.txt,* dzieją się następujące czynności:

- Visual Studio dodaje **CMake** elementów do menu **projektu,** z poleceń do przeglądania i edycji skryptów CMake.

- **Eksplorator rozwiązań** wyświetla strukturę folderów i pliki.

- Program Visual Studio uruchamia plik cmake.exe i generuje plik pamięci podręcznej*CMakeCache.txt*dla domyślnej konfiguracji (debugowanie x64). Wiersz polecenia CMake jest wyświetlany w **oknie wyjścia,** wraz z dodatkowym wyjściem z CMake.

- W tle visual studio rozpoczyna indeksowanie plików źródłowych, aby włączyć IntelliSense, przeglądanie informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować jego indeks w synchronizacji ze źródłami.

Można otworzyć foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie "główne" pliki *CMakeLists.txt* w obszarze roboczym. CMake operacji (konfigurowanie, tworzenie, debugowanie), C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![CZło projekt z wieloma korzeniami](media/cmake-multiple-roots.png)

Można również wyświetlić projekty uporządkowane logicznie według obiektów docelowych. Z listy rozwijanej na pasku **narzędzi Eksplorator rozwiązań** wybierz **widok obiekty docelowe:**

![CNakładuj widok cele](media/cmake-targets-view.png)

Kliknij przycisk **Pokaż wszystkie pliki** w górnej części **Eksploratora rozwiązań,** aby wyświetlić wszystkie wygenerowane przez CMake dane wyjściowe w folderach *out/build/\<config>.*

Program Visual Studio używa pliku konfiguracyjnego o nazwie **CMakeSettings.json**. Ten plik umożliwia definiowanie i przechowywanie wielu konfiguracji kompilacji i wygodne przełączanie się między nimi w IDE. *Konfiguracja* jest Visual Studio konstrukcji, która hermetyzuje ustawienia, które są specyficzne dla danego typu kompilacji. Ustawienia służą do konfigurowania domyślnych opcji wiersza polecenia, które program Visual Studio przekazuje do pliku cmake.exe. Można również określić dodatkowe opcje CMake w tym miejscu i zdefiniować wszelkie dodatkowe zmienne, które chcesz. Wszystkie opcje są zapisywane w pamięci podręcznej CMake jako zmienne wewnętrzne lub zewnętrzne. W programie Visual Studio 2019 **Edytor ustawień CMake** zapewnia wygodny sposób edytowania ustawień. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMake](customize-cmake-settings.md).

Jedno ustawienie, `intelliSenseMode` nie jest przekazywana do CMake, ale jest używana tylko przez program Visual Studio.

Użyj pliku **CMakeLists.txt** w każdym folderze projektu, tak jak w każdym projekcie CMake. Można określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora oraz określić inne informacje związane z kompilacją systemu.

Aby przekazać argumenty do pliku wykonywalnego w czasie debugowania, można użyć innego pliku o nazwie **launch.vs.json**. W niektórych scenariuszach visual studio automatycznie generuje te pliki. Można je edytować ręcznie, a nawet samodzielnie utworzyć plik.

> [!NOTE]
> W przypadku innych rodzajów projektów folderów otwartych używane są dwa dodatkowe pliki JSON: **CppProperties.json** i **tasks.vs.json**. Żadna z nich nie są istotne dla projektów CMake.

## <a name="open-an-existing-cache"></a>Otwieranie istniejącej pamięci podręcznej

Po otwarciu istniejącego pliku pamięci podręcznej CMake (*CMakeCache.txt),* program Visual Studio nie próbuje zarządzać pamięcią podręczną i drzewa kompilacji dla Ciebie. Niestandardowe lub preferowane narzędzia mają pełną kontrolę nad tym, jak CMake konfiguruje projekt. Aby otworzyć istniejącą pamięć podręczną w programie Visual Studio, wybierz pozycję **Plik > Otwórz > CMake**. Następnie przejdź do istniejącego pliku *CMakeCache.txt.*

Do otwartego projektu można dodać istniejącą pamięć podręczną CMake. Odbywa się to w ten sam sposób, w jaki można dodać nową konfigurację. Aby uzyskać więcej informacji, zobacz nasz wpis w blogu dotyczący [otwierania istniejącej pamięci podręcznej w programie Visual Studio.](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)

## <a name="building-cmake-projects"></a>Budowanie projektów CMake

Aby zbudować projekt CMake, masz następujące możliwości:

1. Na pasku narzędzi Ogólne znajdź **menu rozwijane Konfiguracje.** Prawdopodobnie domyślnie pokazuje "x64-Debug". Wybierz preferowaną konfigurację i naciśnij **klawisz F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie tworzy najpierw, podobnie jak rozwiązanie programu Visual Studio.

1. Kliknij prawym przyciskiem myszy na *CMakeLists.txt* i wybierz **Build** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystkie lub tylko jeden określony cel.

1. Z menu głównego wybierz **polecenie Buduj > Zbuduj wszystko** **(F7** lub **Ctrl+Shift+B**). Upewnij się, że cMake cel jest już zaznaczone w pozycji rozwijanej **elementu startowego** na pasku narzędzi **Ogólne.**

![Polecenie menu CMake build](media/cmake-build-menu.png "Menu polecenia CMake build")

Zgodnie z oczekiwaniami, wyniki kompilacji są wyświetlane w **oknie wyjściowym** i **liście błędów**.

![CMake błędy kompilacji](media/cmake-build-errors.png "CMake błędy kompilacji")

W folderze z wieloma obiektami docelowymi kompilacji można określić, który obiekt docelowy CMake do zbudowania: Wybierz element **Kompilacja** w menu **CMake** lub *CMakeLists.txt,* aby określić cel docelowy. Jeśli wprowadzisz **ctrl+Shift+B** w projekcie CMake, tworzy bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz preferowaną konfigurację i naciśnij **klawisz F5**lub naciśnij przycisk **Uruchom** na pasku narzędzi. Jeśli przycisk **Uruchom** wytypuje "Wybierz element startowy", wybierz strzałkę rozwijaną. Wybierz obiekt docelowy, który chcesz uruchomić. (W projekcie CMake opcja "Bieżący dokument" jest prawidłowa tylko dla plików cpp).

![CNakładuj bieg](media/cmake-run-button.png "CNakładuj bieg")

Polecenia **Uruchom** lub **F5** najpierw skompilować projekt, jeśli zmiany zostały wprowadzone od poprzedniej kompilacji. Zmiany w *CMakeSettings.json* spowodować CMake pamięci podręcznej do ponownego wygenerowannia.

Sesję debugowania CMake można dostosować, ustawiając właściwości w pliku **launch.vs.json.** Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Tylko mój kod dla projektów CMake

Podczas tworzenia dla systemu Windows przy użyciu kompilatora MSVC, CMake projekty mają obsługę tylko mój kod debugowania. Aby zmienić ustawienie Tylko mój kod, przejdź do pozycji**Opcje** >  **narzędzi** > **Debugowania** > **ogólne**.

## <a name="vcpkg-integration"></a>Integracja vcpkg

Jeśli zainstalowano [vcpkg](vcpkg.md), CMake projektów otwartych w programie Visual Studio automatycznie zintegrować plik paska narzędzi vcpkg. Oznacza to, że do używania vcpkg z projektami CMake nie jest wymagana żadna dodatkowa konfiguracja. Ta obsługa działa zarówno w przypadku lokalnych instalacji vcpkg, jak i instalacji vcpkg w systemach zdalnych, do których dążysz. To zachowanie jest wyłączane automatycznie po określeniu innego pęku narzędzi w konfiguracji ustawień CMake.

## <a name="customize-configuration-feedback"></a>Dostosowywanie opinii o konfiguracji

Domyślnie większość komunikatów konfiguracyjnych jest pomijana, chyba że występuje błąd. Wszystkie wiadomości można wyświetlić, włączając tę funkcję w**opcjach** >  **narzędzi** > **CMake**.

   ![Konfigurowanie opcji diagnostycznych CMake](media/vs2019-cmake-configure-options.png "CMake opcje diagnostyczne")

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists.txt

Aby edytować plik *CMakeLists.txt,* kliknij prawym przyciskiem myszy plik w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wniesiesz zmiany do pliku, pojawi się żółty pasek stanu i informuje, że intellisense zostanie zaktualizowany. To daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacje o *CMakeLists.txt,* zobacz [dokumentację CMake](https://cmake.org/documentation/).

   ![Edycja pliku CMakeLists.txt](media/cmake-cmakelists.png "Edycja pliku CMakeLists.txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie ponownie uruchamiany i wyświetla informacje w oknie **Dane wyjściowe.** Błędy i ostrzeżenia są wyświetlane na **liście błędów** lub **danych wyjściowych** okna. Kliknij dwukrotnie błąd na **liście błędów,** aby przejść do linii naruszającej w *CMakeLists.txt*.

   ![Błędy pliku CMakeLists.txt](media/cmake-cmakelists-error.png "Błędy pliku CMakeLists.txt")

## <a name="cmake-configure-step"></a>CMoke konfiguracji kroku

Po wprowadzeniu istotnych zmian w *CMakeSettings.json* lub do plików *CMakeLists.txt,* Visual Studio automatycznie ponownie ustawia CMake skonfigurować krok. Jeśli krok konfiguracji zakończy się bez błędów, informacje, które są zbierane są dostępne w języku C++ IntelliSense i usług językowych. Jest również używany w operacjach kompilacji i debugowania.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej CMake

Jeśli potrzebujesz więcej informacji o stanie pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **projektu** lub menu kontekstowe *CMakeLists.txt* w **Eksploratorze rozwiązań,** aby uruchomić jedno z następujących poleceń:

- **Widok Pamięci podręcznej** otwiera plik *CMakeCache.txt* z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone tutaj do *CMakeCache.txt* są wymazane, jeśli wyczyścić pamięć podręczną. Aby wprowadzić zmiany, które utrzymują się po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMake](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** otwiera okno Eksploratora do folderu głównego kompilacji.

- **Czysta pamięć podręczna** usuwa folder główny kompilacji, dzięki czemu następny krok konfiguracji CMake rozpoczyna się od czystej pamięci podręcznej.

- **Generowanie pamięci podręcznej** wymusza generowanie kroku do uruchomienia, nawet jeśli program Visual Studio uważa, że środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie dialogowym **Narzędzia > > CMake > Ogólne.**

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalatora programu Visual Studio, można go uruchomić z wiersza polecenia, wykonując następujące kroki:

1. Uruchom odpowiedni vsdevcmd.bat (x86/x64). Aby uzyskać więcej informacji, zobacz [Tworzenie w wierszu polecenia](building-on-the-command-line.md).

1. Przełącz się do folderu wyjściowego.

1. Uruchom CMake do tworzenia/konfigurowania aplikacji.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 ma bogatą obsługę CMake, w tym [wieloplatformowych projektów CMake](../linux/cmake-linux-project.md). **Visual C++ Tools for CMake** składnik używa funkcji **Otwórz folder,** aby umożliwić IDE do korzystania z plików projektu CMake (takich jak *CMakeLists.txt*) bezpośrednio na potrzeby IntelliSense i przeglądania. Obsługiwane są generatory Ninja i Visual Studio. Jeśli używasz generatora programu Visual Studio, generuje tymczasowy plik projektu i przekazuje go do msbuild.exe. Jednak projekt nigdy nie jest ładowany do intellisense lub do celów przeglądania. Można również zaimportować istniejącą pamięć podręczną CMake.

## <a name="installation"></a>Instalacja

**Visual C++ Tools for CMake** jest instalowany jako część **tworzenia pulpitu z C++** i Linux Development z obciążeniami **C++.**

![Składnik CMake w obciążeniu pulpitu języka C++](media/cmake-install.png)

Aby uzyskać więcej informacji, zobacz [Instalowanie obciążenia systemu Linux w programie Visual Studio.](../linux/download-install-and-setup-the-linux-development-workload.md)

## <a name="ide-integration"></a>Integracja IDE

Po **wybraniu opcji File > Open > Folder** , aby otworzyć folder zawierający plik *CMakeLists.txt,* dzieją się następujące czynności:

- Visual Studio dodaje **CMake** element menu do menu głównego, z polecenia do przeglądania i edycji skryptów CMake.

- **Eksplorator rozwiązań** wyświetla strukturę folderów i pliki.

- Visual Studio uruchamia CMake.exe i opcjonalnie generuje pamięć podręczną CMake dla *domyślnej konfiguracji*, która jest x86 Debug. Wiersz polecenia CMake jest wyświetlany w **oknie wyjścia,** wraz z dodatkowym wyjściem z CMake.

- W tle visual studio rozpoczyna indeksowanie plików źródłowych, aby włączyć IntelliSense, przeglądanie informacji, refaktoryzacji i tak dalej. Podczas pracy program Visual Studio monitoruje zmiany w edytorze, a także na dysku, aby zachować jego indeks w synchronizacji ze źródłami.

Można otworzyć foldery zawierające dowolną liczbę projektów CMake. Program Visual Studio wykrywa i konfiguruje wszystkie "główne" pliki *CMakeLists.txt* w obszarze roboczym. CMake operacji (konfigurowanie, tworzenie, debugowanie), C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![CZło projekt z wieloma korzeniami](media/cmake-multiple-roots.png)

Można również wyświetlić projekty uporządkowane logicznie według obiektów docelowych. Z listy rozwijanej na pasku **narzędzi Eksplorator rozwiązań** wybierz **widok obiekty docelowe:**

![CNakładuj widok cele](media/cmake-targets-view.png)

Visual Studio używa pliku o nazwie *CMakeSettings.json* do przechowywania zmiennych środowiskowych lub opcji wiersza polecenia dla cmake.exe. *CMakeSettings.json* umożliwia również definiowanie i przechowywanie wielu konfiguracji kompilacji CMake. Można wygodnie przełączać się między nimi w IDE.

W przeciwnym razie użyj *CMakeLists.txt* tak samo, jak w każdym projekcie CMake, aby określić pliki źródłowe, znaleźć biblioteki, ustawić opcje kompilatora i konsolidatora oraz określić inne informacje związane z systemem kompilacji.

Jeśli musisz przekazać argumenty do pliku wykonywalnego w czasie debugowania, możesz użyć innego pliku o nazwie **launch.vs.json**. W niektórych scenariuszach visual studio automatycznie generuje te pliki. Można je edytować ręcznie, a nawet samodzielnie utworzyć plik.

> [!NOTE]
> W przypadku innych rodzajów projektów folderów otwartych używane są dwa dodatkowe pliki JSON: **CppProperties.json** i **tasks.vs.json**. Żadna z nich nie są istotne dla projektów CMake.

## <a name="import-an-existing-cache"></a>Importowanie istniejącej pamięci podręcznej

Podczas importowania istniejącego pliku *CMakeCache.txt* program Visual Studio automatycznie wyodrębnia dostosowane zmienne i tworzy na ich podstawie wstępnie wypełniony plik *CMakeSettings.json.* Oryginalna pamięć podręczna nie jest w żaden sposób modyfikowana. Nadal może być używany z wiersza polecenia lub z dowolnym narzędziem lub IDE używanym do jego wygenerowania. Nowy plik *CMakeSettings.json* jest umieszczany obok głównego projektu *CMakeLists.txt*. Visual Studio generuje nową pamięć podręczną na podstawie pliku ustawień. Automatyczne generowanie pamięci podręcznej można zastąpić w oknie dialogowym **Narzędzia > opcje > CMake > Ogólne.**

Nie wszystko w pamięci podręcznej jest importowane.  Właściwości, takie jak generator i lokalizacja kompilatorów są zastępowane wartościami domyślnymi, które są znane dobrze współpracować z IDE.

### <a name="to-import-an-existing-cache"></a>Aby zaimportować istniejącą pamięć podręczną

1. Z menu głównego wybierz **polecenie Plik > Otwórz > CMake**:

   ![Otwórz CMake](media/cmake-file-open.png "Plik, Otwórz, CMake")

   To polecenie powoduje **wyświetlenie kreatora Import CMake z pamięci podręcznej.**

2. Przejdź do pliku *CMakeCache.txt,* który chcesz zaimportować, a następnie kliknij przycisk **OK**. Zostanie wyświetlony Kreator **Projektu CMake z pamięci podręcznej:**

   ![Importowanie pamięci podręcznej CMake](media/cmake-import-wizard.png "Otwórz kreatora cMake importu pamięci podręcznej")

   Po zakończeniu pracy kreatora nowy plik *CMakeCache.txt* w **Eksploratorze rozwiązań** jest widoczny obok głównego pliku *CMakeLists.txt* w projekcie.

## <a name="building-cmake-projects"></a>Budowanie projektów CMake

Aby zbudować projekt CMake, masz następujące możliwości:

1. Na pasku narzędzi Ogólne znajdź **menu rozwijane Konfiguracje.** Prawdopodobnie domyślnie pokazuje "Linux-Debug" lub "x64-Debug". Wybierz preferowaną konfigurację i naciśnij **klawisz F5**lub kliknij przycisk **Uruchom** (zielony trójkąt) na pasku narzędzi. Projekt automatycznie tworzy najpierw, podobnie jak rozwiązanie programu Visual Studio.

1. Kliknij prawym przyciskiem myszy *na CMakeLists.txt* i wybierz **build** z menu kontekstowego. Jeśli masz wiele obiektów docelowych w strukturze folderów, możesz utworzyć wszystkie lub tylko jeden określony cel.

1. Z menu głównego wybierz **opcję Buduj > Rozwiązanie kompilacji** **(F7** lub **Ctrl+Shift+B**). Upewnij się, że cMake cel jest już zaznaczone w pozycji rozwijanej **elementu startowego** na pasku narzędzi **Ogólne.**

![Polecenie menu CMake build](media/cmake-build-menu.png "Menu polecenia CMake build")

Konfiguracje kompilacji, zmienne środowiskowe, argumenty wiersza polecenia i inne ustawienia można dostosować w pliku *CMakeSettings.json.* Umożliwia wprowadzanie zmian bez modyfikowania pliku *CMakeLists.txt.* Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień CMake](customize-cmake-settings.md).

Zgodnie z oczekiwaniami, wyniki kompilacji są wyświetlane w **oknie wyjściowym** i **liście błędów**.

![CMake błędy kompilacji](media/cmake-build-errors.png "CMake błędy kompilacji")

W folderze z wieloma obiektami docelowymi kompilacji można określić, który obiekt docelowy CMake do zbudowania: Wybierz element **Kompilacja** w menu **CMake** lub *CMakeLists.txt,* aby określić cel docelowy. Jeśli wprowadzisz **ctrl+Shift+B** w projekcie CMake, tworzy bieżący aktywny dokument.

## <a name="debugging-cmake-projects"></a>Debugowanie projektów CMake

Aby debugować projekt CMake, wybierz preferowaną konfigurację i naciśnij **klawisz F5**. Możesz też **nacisnąć** przycisk Uruchom na pasku narzędzi. Jeśli przycisk **Uruchom** wywiesza "Wybierz element startowy", wybierz strzałkę rozwijaną i wybierz cel, który chcesz uruchomić. (W projekcie CMake opcja "Bieżący dokument" jest prawidłowa tylko dla plików cpp).

![CNakładuj bieg](media/cmake-run-button.png "CNakładuj bieg")

Polecenia **Uruchom** lub **F5** najpierw skompilować projekt, jeśli zmiany zostały wprowadzone od poprzedniej kompilacji.

Sesję debugowania CMake można dostosować, ustawiając właściwości w pliku **launch.vs.json.** Aby uzyskać więcej informacji, zobacz [Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Edytowanie plików CMakeLists.txt

Aby edytować plik *CMakeLists.txt,* kliknij prawym przyciskiem myszy plik w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wniesiesz zmiany do pliku, pojawi się żółty pasek stanu i informuje, że intellisense zostanie zaktualizowany. To daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacje o *CMakeLists.txt,* zobacz [dokumentację CMake](https://cmake.org/documentation/).

   ![Edycja pliku CMakeLists.txt](media/cmake-cmakelists.png "Edycja pliku CMakeLists.txt")

Po zapisaniu pliku krok konfiguracji zostanie automatycznie ponownie uruchamiany i wyświetla informacje w oknie **Dane wyjściowe.** Błędy i ostrzeżenia są wyświetlane na **liście błędów** lub **danych wyjściowych** okna. Kliknij dwukrotnie błąd na **liście błędów,** aby przejść do linii naruszającej w *CMakeLists.txt*.

   ![Błędy pliku CMakeLists.txt](media/cmake-cmakelists-error.png "Błędy pliku CMakeLists.txt")

## <a name="cmake-configure-step"></a>CMoke konfiguracji kroku

Po wprowadzeniu istotnych zmian do *CMakeSettings.json* lub do plików *CMakeLists.txt,* Visual Studio automatycznie ponownie wywrze cMake skonfigurować krok. Jeśli krok konfiguracji zakończy się bez błędów, informacje, które są zbierane są dostępne w języku C++ IntelliSense i usług językowych. Jest również używany w operacjach kompilacji i debugowania.

Wiele projektów CMake może używać tej samej nazwy konfiguracji CMake (na przykład x86-Debug). Wszystkie z nich są konfigurowane i budowane (we własnym folderze głównym kompilacji), gdy ta konfiguracja jest zaznaczona. Można debugować obiekty docelowe ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji CMake.

   ![CZamić tylko element menu](media/cmake-build-only.png "CZamić tylko element menu")

Można ograniczyć kompilacje i sesje debugowania do podzbioru projektów w obszarze roboczym. Utwórz nową konfigurację o unikatowej nazwie w pliku *CMakeSettings.json.* Następnie zastosuj konfigurację tylko do tych projektów. Po wybraniu tej konfiguracji intellisense i polecenia kompilacji i debugowania mają zastosowanie tylko do tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej CMake w celu zdiagnozowania problemu, otwórz menu główne **CMake** lub menu kontekstowe *CMakeLists.txt* w **Eksploratorze rozwiązań,** aby uruchomić jedno z następujących poleceń:

- **Widok Pamięci podręcznej** otwiera plik *CMakeCache.txt* z folderu głównego kompilacji w edytorze. (Wszelkie zmiany wprowadzone tutaj do *CMakeCache.txt* są wymazane, jeśli wyczyścić pamięć podręczną. Aby wprowadzić zmiany, które utrzymują się po wyczyszczeniu pamięci podręcznej, zobacz [Dostosowywanie ustawień CMake](customize-cmake-settings.md).)

- **Otwórz folder pamięci podręcznej** otwiera okno Eksploratora do folderu głównego kompilacji.

- **Czysta pamięć podręczna** usuwa folder główny kompilacji, dzięki czemu następny krok konfiguracji CMake rozpoczyna się od czystej pamięci podręcznej.

- **Generowanie pamięci podręcznej** wymusza generowanie kroku do uruchomienia, nawet jeśli program Visual Studio uważa, że środowisko jest aktualne.

Automatyczne generowanie pamięci podręcznej można wyłączyć w oknie dialogowym **Narzędzia > > CMake > Ogólne.**

## <a name="single-file-compilation"></a>Kompilacja pojedynczego pliku

Aby utworzyć pojedynczy plik w projekcie CMake, kliknij prawym przyciskiem myszy plik w **Eksploratorze rozwiązań**. Z wyskakującego menu wybierz **polecenie Skompiluj.** Aktualnie otwarty plik można również utworzyć w edytorze za pomocą głównego menu **CMake:**

![CZgodna kompilacja pojedynczego pliku](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Uruchom CMake z wiersza polecenia

Jeśli zainstalowano CMake z Instalatora programu Visual Studio, można go uruchomić z wiersza polecenia, wykonując następujące kroki:

1. Uruchom odpowiedni vsdevcmd.bat (x86/x64). Aby uzyskać więcej informacji, zobacz [Tworzenie wiersza polecenia](building-on-the-command-line.md) .

1. Przełącz się do folderu wyjściowego.

1. Uruchom CMake do tworzenia/konfigurowania aplikacji.

::: moniker-end

::: moniker range="vs-2015"

W programie Visual Studio 2015 użytkownicy programu Visual Studio mogą używać [generatora CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) do generowania plików projektu MSBuild, które IDE następnie zużywa dla IntelliSense, przeglądania i kompilacji.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Samouczek: Tworzenie projektów międzyplatformowych w programie Visual Studio w języku C++](get-started-linux-cmake.md)\
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)\
[Połącz się ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Dostosowywanie ustawień kompilacji CMake](customize-cmake-settings.md)\
[Odwołanie do schematu CMakeSettings.json](cmakesettings-reference.md)\
[Konfigurowanie sesji debugowania CMake](configure-cmake-debugging-sessions.md)\
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[CZrobe wstępnie zdefiniowane odwołanie do konfiguracji](cmake-predefined-configuration-reference.md)
