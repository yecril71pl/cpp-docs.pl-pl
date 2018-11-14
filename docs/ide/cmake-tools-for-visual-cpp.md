---
title: Projekty CMake w programie Visual C++
ms.date: 10/18/2018
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: a4f7b3931dc8ed8bd7206c7f30ce4b65633f08b6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518987"
---
# <a name="cmake-projects-in-visual-c"></a>Projekty CMake w programie Visual C++

W tym artykule założono, że czytelnik zna za pomocą narzędzia CMake, narzędzie Międzyplatformowe, typu open-source Definiowanie procesów kompilacji, które są uruchamiane na wielu platformach.

W programie Visual Studio 2015, Visual Studio użytkownicy mogą używać [generatora CMake](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html) do generowania plików projektu MSBuild, które IDE następnie zużywa dla technologii IntelliSense, przeglądanie i kompilacji.

Począwszy od programu Visual Studio 2017, **Visual C++ Tools for CMake** składnik używa **Otwórz Folder** funkcję, aby umożliwić korzystają z plików projektu narzędzia CMake (na przykład pliku CMakeLists.txt) bezpośrednio na potrzeby środowiska IDE funkcja IntelliSense i przeglądania. Jeśli używasz generator programu Visual Studio, tymczasowy plik projektu zostanie wygenerowany i przekazane do msbuild.exe, ale nigdy nie jest załadowany do celów przeglądaniu lub IntelliSense.

**Visual Studio 2017 w wersji 15.3**: Pomoc techniczna jest dostępna dla generatorów Ninja i programu Visual Studio.

**Visual Studio 2017 w wersji 15.4**: Dodano obsługę narzędzia CMake w systemie Linux. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md).

**Visual Studio 2017 w wersji 15.5**: Dodano obsługę importowanie istniejących pamięć podręczną CMake. Program Visual Studio wyodrębnia niestandardowe zmienne i automatycznie tworzy plik CMakeSettings.json wstępnie wypełnione.

**Visual Studio 2017 w wersji 15.7**: Dodano obsługę wyłączenie pamięci podręcznej automatycznego generowania widok elementów docelowych w **Eksploratora rozwiązań**i kompilacja pojedynczego pliku.

## <a name="installation"></a>Instalacja

**Visual C++ Tools for CMake** jest instalowany domyślnie w jako część **programowanie aplikacji klasycznych w języku C++** obciążenia.

![Składnik narzędzia CMake w obciążeniu C++ na komputerach](media/cmake-install.png)

## <a name="ide-integration"></a>Integracja środowiska IDE

Po wybraniu **pliku | Otwórz | Folder** aby otworzyć folder zawierający plik CMakeLists.txt, się zdarzyć, następujące elementy:

- Program Visual Studio dodaje **CMake** element menu do menu głównego, za pomocą poleceń do wyświetlania i edytowania skryptów narzędzia CMake.

- **Eksplorator rozwiązań** wyświetla strukturę folderów i plików.

- Program Visual Studio uruchamia CMake.exe i generuje pamięci podręcznej narzędzia CMake dla domyślnej *konfiguracji*, czyli x86 debugowania. W wierszu polecenia CMake są wyświetlane w **okno danych wyjściowych**, wraz z dodatkowych danych wyjściowych z narzędzia CMake.  **Visual Studio 2017 w wersji 15.7 lub nowszej**: generowanie pamięci podręcznej automatycznego można wyłączyć w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

- W tle programu Visual Studio uruchamia do indeksowania plików źródłowych, aby włączyć technologię IntelliSense, informacji o przeglądaniu, Refaktoryzacja i tak dalej. Podczas pracy programu Visual Studio monitoruje zmiany w edytorze, a także na dysku w celu synchronizowania jej indeks ze źródłami.

Możesz otworzyć foldery zawierające dowolną liczbę projekty narzędzia CMake. Visual Studio wykrywa i skonfiguruje wszystkie pliki CMakeLists.txt "root" w obszarze roboczym. Operacje CMake (Konfigurowanie, tworzenie, debugowanie) również funkcji C++ IntelliSense i przeglądania są dostępne dla wszystkich projektów CMake w obszarze roboczym.

![Projekt narzędzia CMake z wielu katalogów głównych](media/cmake-multiple-roots.png)

**Visual Studio 2017 w wersji 15.7 lub nowszej**: Możesz również wyświetlić swoje projekty logicznie uporządkowane według elementów docelowych. Wybierz **jest przeznaczony dla widoku** z listy rozwijanej w **Eksploratora rozwiązań** narzędzi:

![Przycisk Widok elementów docelowych narzędzia CMake](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>Importowanie istniejąca pamięć podręczna

Podczas importowania istniejącego pliku CMakeCache.txt programu Visual Studio wyodrębnia niestandardowe zmienne i automatycznie tworzy wstępnie wypełnionych [CMakeSettings.json](#cmake_settings) na ich podstawie plików. Oryginalny pamięci podręcznej nie jest modyfikowany w dowolny sposób i nadal można używać z poziomu wiersza polecenia lub przy użyciu dowolnego narzędzia lub IDE został użyty do jego wygenerowania. Nowy plik CMakeSettings.json znajduje się obok projektu głównego pliku CMakeLists.txt. Program Visual Studio generuje nową pamięć podręczną na podstawie pliku ustawień.

**Visual Studio 2017 w wersji 15.7 lub nowszej**: możesz zastąpić Generowanie automatyczne pamięci podręcznej w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

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

1. Wybierz element docelowy w **debugowania** listy rozwijanej i naciśnij klawisz **F5**, lub kliknij przycisk **Uruchom** przycisku (zielony trójkąt). Automatycznie kompilacje projektu po pierwsze, podobnie jak rozwiązanie programu Visual Studio.

1. Kliknij prawym przyciskiem myszy pliku CMakeLists.txt i wybierz pozycję **kompilacji** z menu kontekstowego. Jeśli masz wiele elementów docelowych w strukturze folderów, można tworzyć wszystkie lub tylko jeden określony element docelowy.

1. W menu głównym wybierz **kompilacji | Tworzenie rozwiązania** (**F7** lub **Ctrl + Shift + B**). Upewnij się, czy docelowych narzędzia CMake została już wybrana w **element startowy** liście rozwijanej **ogólne** paska narzędzi.

![Polecenia menu kompilacji CMake](media/cmake-build-menu.png "menu poleceń kompilacji CMake")

Po wybraniu generator programu Visual Studio dla aktywnej konfiguracji MSBuild.exe jest wywoływana z `-m -v:minimal` argumentów. Dostosowywanie kompilacji, w pliku CMakeSettings.json, można określić dodatkowe argumenty wiersza polecenia do przekazania do systemu kompilacji, za pośrednictwem `buildCommandArgs` właściwości:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Jak można oczekiwać wyników kompilacji są wyświetlane w **okno danych wyjściowych** i **lista błędów**.

![Błędy kompilacji CMake](media/cmake-build-errors.png "błędy kompilacji CMake")

W folderze o wiele obiektów docelowych kompilacji, można wybrać **kompilacji** elementu na **CMake** menu lub **CMakeLists.txt** menu kontekstowym, aby określić, które docelowej narzędzia CMake do kompilacji. Naciśnięcie klawisza **Ctrl + Shift + B** w CMake projekt jest kompilowany bieżący aktywny dokument.

## <a name="debug-the-project"></a>Debugowanie projektu

Aby debugować projekt CMake, wybierz żądaną konfiguracją i naciśnij klawisz **F5**, lub naciśnij **Uruchom** przycisku na pasku narzędzi. Jeśli **Uruchom** przycisk jest wyświetlany komunikat "Wybierz element startowy", wybierz strzałkę listy rozwijanej i wybierz cel, który chcesz uruchomić. (W projekcie programu CMake, "bieżący dokument" opcja jest prawidłowa tylko dla plików .cpp.)

![Przycisk Uruchom narzędzie CMake](media/cmake-run-button.png "przycisk Uruchom narzędzia CMake")

**Uruchom** lub **F5** polecenia najpierw skompilować projekt, jeśli zostały zmienione od poprzedniej kompilacji.

## <a name="configure-cmake-debugging-sessions"></a>Konfigurowanie narzędzia CMake sesjami debugowania

Wszystkie elementy docelowe z pliku wykonywalnego narzędzia CMake są wyświetlane w **element startowy** liście rozwijanej **ogólne** paska narzędzi. Aby rozpocząć sesję debugowania, po prostu zaznacz jedną i uruchomić debugera.

![Narzędzie CMake uruchamiania elementu z listy rozwijanej](media/cmake-startup-item-dropdown.png "CMake uruchamiania elementu z listy rozwijanej")

Można również uruchomić sesję debugowania z menu Narzędzia CMake.

Aby dostosować ustawienia debugera dla dowolnego pliku wykonywalnego docelowych narzędzia CMake w projekcie, kliknij prawym przyciskiem myszy w określonym pliku CMakeLists.txt, a następnie wybierz **ustawienia debugowania i uruchamiania**. Po wybraniu docelowych narzędzia CMake w podmenu, zostanie utworzony plik o nazwie pliku launch.vs.json. Ten plik jest wstępnie wypełniane przy użyciu informacji o docelowej narzędzia CMake, wybrana przez Ciebie i pozwala określić dodatkowe parametry, takie jak argumenty programu lub typ debugera. Aby odwołać się dowolnym kluczu w pliku CMakeSettings.json, należy poprzedzić go za pomocą "Narzędzia CMake." in launch.vs.json. Poniższy kod przedstawia pliku prostego pliku launch.vs.json, który pobiera wartość klucza "remoteCopySources" w pliku CMakeSettings.json dla aktualnie wybranej konfiguracji:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Bezpośrednio po zapisaniu pliku launch.vs.json zapis jest tworzony w **element startowy** lista rozwijana z nową nazwą. Podczas edycji pliku launch.vs.json, można tworzyć, jak wiele konfiguracji debugowania, jak dowolną liczbę elementów docelowych narzędzia CMake.

**Visual Studio 2017 w wersji 15.4**: pliku Launch.vs.json obsługuje zmienne, które są zadeklarowane w pliku CMakeSettings.json (patrz poniżej) i które mają zastosowanie do konfiguracji aktualnie wybrany. Ma również klucz o nazwie "currentDir", który ustawia bieżący katalog uruchamiania aplikacji:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Po uruchomieniu aplikacji, a wartość `currentDir` jest podobny do

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>Edytowanie pliku CMakeLists.txt plików

Aby edytować plik CMakeLists.txt, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**. Jeśli wprowadzisz zmiany w pliku paska stanu żółty pojawia się i informuje o spowoduje zaktualizowanie funkcji IntelliSense i daje możliwość anulowania operacji aktualizacji. Aby uzyskać informacji dotyczących pliku CMakeLists.txt, zobacz [dokumentacji narzędzia CMake](https://cmake.org/documentation/).

   ![Edytowanie pliku CMakeLists.txt](media/cmake-cmakelists.png "edycji pliku CMakeLists.txt")

Bezpośrednio po zapisaniu pliku kroku konfiguracji automatycznie ponownie uruchomiona i wyświetli informacje zawarte w **dane wyjściowe** okna. Błędy i ostrzeżenia są wyświetlane w **lista błędów** lub **dane wyjściowe** okna. Kliknij dwukrotnie błąd w **lista błędów** można przejść do problematycznych wierszy w pliku CMakeLists.txt.

   ![Błędy w pliku CMakeLists.txt](media/cmake-cmakelists-error.png "błędy w pliku CMakeLists.txt")

## <a name="cmake_settings"></a> Ustawienia narzędzia CMake i konfiguracje niestandardowe

Domyślnie program Visual Studio zawiera sześć domyślnej konfiguracji narzędzia CMake ("x86 debugowanie", "x86 wersja", "x64 debugowanie", "x64-wersja", "Linux-debugowanie" i "Linux-wersja"). Te konfiguracje definiują, jak CMake.exe jest wywoływana w celu utworzenia pamięci podręcznej narzędzia CMake dla danego projektu. Aby zmodyfikować te konfiguracje, lub Utwórz nową konfigurację niestandardowe, wybierz opcję **CMake | Zmień ustawienia narzędzia CMake**, a następnie wybierz plik CMakeLists.txt, które ustawienia dotyczą. **Zmień ustawienia narzędzia CMake** polecenia jest także dostępny w menu kontekstowym pliku w **Eksploratora rozwiązań**. To polecenie tworzy plik CMakeSettings.json w folderze projektu. Ten plik jest używany ponowne tworzenie pliku pamięci podręcznej narzędzia CMake, na przykład po **czysty** operacji.

   ![Polecenia menu głównego narzędzia CMake ustawienia zmian](media/cmake-change-settings.png)

JSON technologia IntelliSense pomaga edytować pliku CMakeSettings.json:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png "IntelliSense JSON narzędzia CMake")

Poniższy przykład pokazuje Przykładowa konfiguracja, który służy jako punkt wyjścia do tworzenia własnego w pliku CMakeSettings.json:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

1. **Nazwa**: Nazwa wyświetlana na liście rozwijanej konfiguracji C++. Wartość tej właściwości może również służyć jako makra, `${name}`, aby określić wartości innych właściwości. Aby uzyskać przykład, zobacz **wybrany element buildRoot** definicję w pliku CMakeSettings.json.

1. **Generator**: mapuje **- G** przełącznika i określa generator, który ma być używany. Ta właściwość może również służyć jako makra, `${generator}`, aby pomóc określić wartości innych właściwości. Program Visual Studio obsługuje obecnie następujące generatory CMake:

   - "Ninja"

   - "Visual Studio 14 2015"

   - "Visual Studio 14 2015 ARM"

   - "Win64 programu visual Studio 14 2015"

   - "Visual Studio 15 2017"

   - "Visual Studio 15 2017 ARM"

   - "Visual Studio 15 2017 Win64"

Ponieważ Ninja jest przeznaczona dla szybkości szybkie kompilacji zamiast elastyczności i funkcji, jest ustawiona jako domyślna. Jednak niektóre projekty narzędzia CMake, może być nie można poprawnie tworzyć zawartość przy użyciu Ninja. W takiej sytuacji można nakazać narzędzia CMake w celu wygenerowania projektu programu Visual Studio, zamiast tego.

Aby określić generator programu Visual Studio, otwórz pliku CMakeSettings.json z menu głównego, wybierając **CMake | Zmień ustawienia narzędzia CMake**. Usuń "Ninja", a następnie wpisz "V". Aktywuje funkcję IntelliSense, która pozwala na dokonanie wyboru generator, który ma.

1. **wybrany element buildRoot**: mapuje **-DCMAKE_BINARY_DIR** Przełącz i określa, w którym zostanie utworzona pamięci podręcznej narzędzia CMake. Jeśli folder nie istnieje, zostanie utworzony.

1. **zmienne**: zawiera pary nazwa wartość, zmienne narzędzia CMake, które będą przekazywane jako **-D** *_nazwa_=_wartość_* do narzędzia CMake. Instrukcje kompilacji projektu narzędzia CMake określić dodanie wszelkie zmienne bezpośrednio do pliku pamięci podręcznej narzędzia CMake, zaleca się dodanie ich w tym miejscu zamiast tego. Poniższy przykład pokazuje, jak określić pary nazwa wartość:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    }
  ]
```

1. **cmakeCommandArgs**: określa żadnych dodatkowych przełączników, które mają być przekazane do CMake.exe.

2. **Typ konfiguracji**: Określa typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane wartości to "Debug", "MinSizeRel", "Wersja" i "RelWithDebInfo".

3. **ctestCommandArgs**: Określa dodatkowe przełączniki do przekazania do narzędzia CTest podczas uruchamiania testów.

4. **buildCommandArgs**: Określa dodatkowe przełączniki do przekazania do bazowego systemu kompilacji. Na przykład przekazując - v, gdy przy użyciu generatora Ninja wymusza Ninja w danych wyjściowych wiersze polecenia.

### <a name="environment-variables"></a>Zmienne środowiskowe

CMakeSettings.json obsługuje również konsumencki zmiennych środowiskowych w dowolnej właściwości wymienionych powyżej. Składnia służąca do użycia jest `${env.FOO}` rozwinąć zmiennej środowiskowej % FOO %.
Masz także dostęp do wbudowanych makr, w tym pliku:

- `${workspaceRoot}` — zapewnia pełną ścieżkę folderu obszaru roboczego

- `${workspaceHash}` — Skrót lokalizacji obszaru roboczego. przydatne podczas tworzenia Unikatowy identyfikator dla bieżącego obszaru roboczego (na przykład do użycia w ścieżkach folderów)

- `${projectFile}` — Pełna ścieżka pliku CMakeLists.txt głównego

- `${projectDir}` — Pełna ścieżka do folderu głównego pliku CMakeLists.txt

- `${thisFile}` — Pełna ścieżka pliku CMakeSettings.json

- `${name}` — Nazwa konfiguracji

- `${generator}` — Nazwa generatora narzędzia CMake, używany w tej konfiguracji

### <a name="ninja-command-line-arguments"></a>Ninja argumenty wiersza polecenia

W przypadku nieokreślonego obiekty docelowe kompilacji docelowej "default" (zobacz ręczne).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opcja|Opis|
|--------------|------------|
| --wersji  | Drukuj ninja wersji ("1.7.1")|
|   -C DIR   | Zmień na katalog, przed wykonaniem jakichkolwiek innych czynności|
|   -f pliku  | Określ plik wejściowy kompilacji (default=build.ninja)|
|   -j N     | równoległe wykonywanie zadań N (domyślny = 14, pochodzące z procesorów dostępnych)|
|   -k N     | Kontynuuj, dopóki N zadanie zakończy się niepowodzeniem (domyślny = 1)|
|   -l N     | Nie uruchamiaj nowe zadania, jeśli średnia obciążenia jest większa niż N|
|   -n       | Wysuszyć Uruchom (nie uruchamiać polecenia, ale działają tak, jak one powiodło się)|
|   -v       | Pokaż wszystkie wiersze polecenia podczas tworzenia|
|   -d tryb  | Włącz debugowanie (tryby listy do użycia -d)|
|   t - narzędzie  | Uruchom subtool (Użyj -t listy do narzędzi niższego poziomu). kończy toplevel opcje; Dodatkowo flagi są przekazywane do narzędzia|
|   -w flagi  | Dostosuj ostrzeżenia (Użyj -w listy do ostrzeżenia)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Dziedziczonych środowisk (Visual Studio 2017 w wersji 15.5)

CMakeSettings.json obsługuje teraz dziedziczonych środowisk. Ta funkcja umożliwia (1) dziedziczą środowiska domyślnego i (2) Utwórz niestandardowe zmienne środowiskowe, które są przekazywane do CMake.exe po jego uruchomieniu.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

W powyższym przykładzie jest taka sama jak działa **wiersz polecenia programisty dla programu VS 2017** z **-arch = amd64-host_arch = amd64** argumentów.

W poniższej tabeli przedstawiono wartości domyślne:

|Nazwa kontekstu|Opis|
|-----------|-----------------|
|vsdev|Domyślne środowisko Visual Studio|
|msvc_x86|Kompiluj przy użyciu x86 x86 narzędzia|
|msvc_arm| Kompilowanie dla ARM przy użyciu x86 narzędzia|
|msvc_arm64|Kompilacji dla architektury ARM64 przy użyciu x86 narzędzia|
|msvc_x86_x64|Kompilacji dla AMD64 przy użyciu x86 narzędzia|
|msvc_x64_x64|Kompilacji dla AMD64 przy użyciu narzędzi 64-bitowych|
|msvc_arm_x64|Kompilowanie dla ARM przy użyciu narzędzi 64-bitowych|
|msvc_arm64_x64|Kompilacji dla architektury ARM64 przy użyciu narzędzi 64-bitowych|

### <a name="custom-environment-variables"></a>Niestandardowe zmienne środowiskowe

W pliku CMakeSettings.json, można zdefiniować niestandardowe zmienne środowiskowe globalnie lub na konfiguracji w **środowisk** właściwości. W poniższym przykładzie zdefiniowano jednej zmiennej globalnej, **BuildDir**, która jest dziedziczona przez konfiguracje debugowania x86 i x64 debugowania. Każda konfiguracja używa zmiennej, aby określić wartość dla **wybrany element buildRoot** właściwości dla tej konfiguracji. Należy zauważyć, jak korzysta z konfiguracjami **inheritEnvironments** właściwość, aby określić zmienną, która ma zastosowanie tylko do tej konfiguracji.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

W następnym przykładzie konfiguracja debugowania x86 definiuje wartość dla **BuildDir** właściwość i ta wartość zastępuje wartość ustawioną przy użyciu globalnego **BuildDir** właściwość tak, aby  **Wybrany element BuildRoot** daje w wyniku `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir",
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="cmake-configure-step"></a>Krok konfigurowania CMake

W przypadku istotnych zmian do pliku CMakeSettings.json lub do pliku CMakeLists.txt plików, programu Visual Studio automatycznie krok konfigurowania powtórkami narzędzia CMake. Jeśli krok konfiguracja zakończy się bez błędów, zbieranych informacji są dostępne w funkcji C++ IntelliSense i usług językowych również w kompilacji i debugowania operacji.

Korzystając z wielu projektów CMake taką samą nazwę konfiguracji narzędzia CMake (na przykład x86-Debug), wszystkie z nich są konfigurowane i wbudowane (folder główny własne kompilacji) po wybraniu tej konfiguracji. Można debugować cele ze wszystkich projektów CMake, które uczestniczą w tej konfiguracji narzędzia CMake.

   ![Kompilacji CMake tylko element menu](media/cmake-build-only.png "kompilacji CMake tylko element menu")

Aby ograniczyć kompilacji i debugowania sesji podzestaw projektów w obszarze roboczym, Utwórz nową konfigurację z unikatową nazwą w pliku CMakeSettings.json i dotyczą tylko tych projektów. Po wybraniu tej konfiguracji IntelliSense i kompilacja i debugowanie poleceń są włączone tylko dla tych określonych projektów.

## <a name="troubleshooting-cmake-cache-errors"></a>Rozwiązywanie problemów z błędami pamięci podręcznej narzędzia CMake

Jeśli potrzebujesz więcej informacji na temat stanu pamięci podręcznej narzędzia CMake, aby zdiagnozować problem, otwórz **CMake** menu głównego lub **CMakeLists.txt** menu kontekstowego w **Eksploratora rozwiązań**do uruchamiania jednego z następujących poleceń:

- **Wyświetlanie pamięci podręcznej** otwiera plik CMakeCache.txt wobec folderu głównego kompilacji w edytorze. (Wszystkie zmiany wprowadzone w tym miejscu CMakeCache.txt są wyczyszczone, jeśli czyszczenia pamięci podręcznej. Aby wprowadzić zmiany, które są zachowywane po czyszczeniu pamięci podręcznej, zobacz [CMake ustawienia i konfiguracje niestandardowe](#cmake_settings) we wcześniejszej części tego artykułu.)

- **Otwórz Folder pamięci podręcznej** zostanie otwarte okno Eksploratora do folderu głównego kompilacji.

- **Czyszczenie pamięci podręcznej** usuwa folder główny kompilacji CMake dalej skonfigurowania uruchamia krok z czystą pamięci podręcznej.

- **Generuj pamięć podręczną** wymusza krok Wygeneruj, aby uruchomić, nawet jeśli program Visual Studio traktuje środowiska aktualne.

**Visual Studio 2017 w wersji 15.7 lub nowszej**: generowanie pamięci podręcznej automatycznego można wyłączyć w **narzędzia | Opcje | Narzędzie CMake | Ogólne** okna dialogowego.

## <a name="single-file-compilation"></a>Pojedynczy plik kompilacji

**Visual Studio 2017 w wersji 15.7 lub nowszej**: Aby utworzyć pojedynczy plik projektu narzędzia CMake, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** i wybierz polecenie **skompilować**. Można także utworzyć plik który jest obecnie otwarty w edytorze za pomocą menu głównego narzędzia CMake:

![Narzędzie CMake pojedynczy plik kompilacji](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Wykonywania CMake z wiersza polecenia

Po zainstalowaniu narzędzia CMake z Instalatora programu Visual Studio, można uruchomić go z wiersza polecenia, wykonując następujące czynności:

1. Uruchom odpowiedni vsdevcmd.bat — x86/x64 64. Zobacz [tworzenia w wierszu polecenia](../build/building-on-the-command-line.md) Aby uzyskać więcej informacji.

1. Przejdź do folderu wyjściowego.

1. Wykonywania CMake kompilacji/skonfigurować aplikację.
