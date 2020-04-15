---
title: Obsługa otwierania folderów dla systemów kompilacji języka C++ w programie Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320960"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Obsługa otwierania folderów dla systemów kompilacji języka C++ w programie Visual Studio

::: moniker range="vs-2015"

Funkcja Otwórz folder jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

W programie Visual Studio 2017 i nowszych funkcja "Otwórz folder" umożliwia otwarcie folderu plików źródłowych i natychmiastowe rozpoczęcie kodowania z obsługą IntelliSense, przeglądania, refaktoryzacji, debugowania i tak dalej. Podczas edytowania, tworzenia, przenoszenia lub usuwania plików program Visual Studio śledzi zmiany automatycznie i stale aktualizuje swój indeks IntelliSense. Nie .sln lub .vcxproj plików są ładowane; w razie potrzeby można określić zadania niestandardowe, a także parametry kompilacji i uruchamiania za pomocą prostych plików .json. Ta funkcja umożliwia integrację dowolnego systemu kompilacji innych firm z programem Visual Studio. Aby uzyskać ogólne informacje na temat otwierania folderu, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake i Qt

CMake jest zintegrowany z ide programu Visual Studio jako składnik obciążenia pulpitu C++. Przepływ pracy dla CMake nie jest identyczny z przepływem pracy opisanym w tym artykule. Jeśli używasz CMake, zobacz [CMake projektów w programie Visual Studio](cmake-projects-in-visual-studio.md). Można również użyć CMake do tworzenia projektów Qt lub można użyć [rozszerzenia Qt Visual Studio](https://download.qt.io/development_releases/vsaddin/) dla programu Visual Studio 2015 lub Visual Studio 2017.

## <a name="other-build-systems"></a>Inne systemy kompilacji

Aby użyć środowiska IDE programu Visual Studio z zestawem narzędzi systemu kompilacji lub kompilatora, który nie jest bezpośrednio obsługiwany z menu głównego, wybierz **opcję Plik | Otwórz | Folder** lub naciśnij **klawisze Ctrl + Shift + Alt + O**. Przejdź do folderu zawierającego pliki kodu źródłowego. Aby utworzyć projekt, skonfiguruj intellisense i ustaw parametry debugowania, należy dodać trzy pliki JSON:

| | |
|-|-|
|Plik CppProperties.json|Określ niestandardowe informacje o konfiguracji do przeglądania. Utwórz ten plik, jeśli to konieczne, w głównym folderze projektu. (Nie używane w projektach CMake.)|
|zadania.vs.json|Określ niestandardowe polecenia kompilacji. Dostęp za pośrednictwem elementu menu kontekstowego **Eksploratora rozwiązań** **Konfigurowanie zadań**.|
|launch.vs.json|Określ argumenty wiersza polecenia dla debugera. Dostęp za pośrednictwem elementu menu kontekstowego **Eksploratora rozwiązań** **Debugowanie i ustawienia uruchamiania**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Konfigurowanie nawigacji po kodzie za pomocą pliku CppProperties.json

W przypadku intellisense i zachowania przeglądania, takie jak **Przejdź do definicji** do poprawnego działania, visual studio musi wiedzieć, który kompilator używasz, gdzie znajdują się nagłówki systemu i gdzie znajdują się dodatkowe pliki dołączania, jeśli nie znajdują się bezpośrednio w folderze, który został otwarty (folder obszaru roboczego). Aby określić konfigurację, można wybrać pozycję **Zarządzaj konfiguracjami** z listy rozwijanej na głównym pasku narzędzi:

![Zarządzanie rozwijaniem konfiguracji](media/manage-configurations-dropdown.png)

Program Visual Studio oferuje następujące konfiguracje domyślne:

![Konfiguracje domyślne](media/default-configurations.png)

Jeśli na przykład wybierzesz **x64-Debug,** program Visual Studio utworzy plik o nazwie *CppProperties.json* w głównym folderze projektu:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Ta konfiguracja dziedziczy zmienne środowiskowe [wiersza polecenia dewelopera](building-on-the-command-line.md)programu Visual Studio x64 . Jedną z tych `INCLUDE` zmiennych jest i można odwoływać się do niej tutaj za pomocą `${env.INCLUDE}` makra. Właściwość `includePath` informuje visual studio, gdzie szukać wszystkich źródeł, które potrzebuje intellisense. W takim przypadku jest na głos "spójrz we wszystkich katalogach określonych przez zmienną środowiskową INCLUDE, a także wszystkie katalogi w bieżącym drzewie folderów roboczych". Właściwość `name` jest nazwą, która pojawi się na rozwijanej i może być cokolwiek chcesz. Właściwość `defines` zawiera wskazówki do IntelliSense, gdy napotka bloki kompilacji warunkowej. Właściwość `intelliSenseMode` zawiera kilka dodatkowych wskazówek na podstawie typu kompilatora. Dostępnych jest kilka opcji dla serwerów MSVC, GCC i Clang.

> [!NOTE]
> Jeśli program Visual Studio wydaje się ignorować ustawienia w *pliku CppProperties.json,* spróbuj dodać `!/CppProperties.json`wyjątek do pliku *.gitignore* w ten sposób: .

## <a name="default-configuration-for-mingw-w64"></a>Domyślna konfiguracja MinGW-w64

Jeśli dodasz konfigurację MinGW-W64, JSON wygląda następująco:

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

Zanotuj `environments` blok. Definiuje właściwości, które zachowują się jak zmienne środowiskowe i są dostępne nie tylko w pliku *CppProperties.json,* ale także w innych plikach konfiguracyjnych *task.vs.json* i *launch.vs.json*. Konfiguracja `Mingw64` dziedziczy `mingw_w64` środowisko i używa `INCLUDE` jego właściwości, `includePath`aby określić wartość dla . W razie potrzeby można dodać inne ścieżki do tej właściwości tablicy.'

Właściwość `intelliSenseMode` jest ustawiona na wartość odpowiednią dla GCC. Aby uzyskać więcej informacji na temat wszystkich tych właściwości, zobacz [Odwołanie do schematu CppProperties](cppproperties-schema-reference.md).

Gdy wszystko działa poprawnie, po najechaniu kursorem na typ zobaczysz intellisense z nagłówków GCC:

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Włączanie diagnostyki intellisense

Jeśli nie widzisz intellisense, że można rozwiązać problem, przechodząc do **Narzędzia** > **Opcje** > **Edytor** > tekstu**C / C ++** > **Zaawansowane** i ustawienie **Włącz rejestrowanie** do **true**. Na początek spróbuj **zniwelować poziom rejestrowania** na 5, a **filtry rejestrowania** na 8.

![Rejestrowanie diagnostyczne](media/diagnostic-logging.png)

Dane wyjściowe są przesyłane w potoku do **okna wyjściowego** i są widoczne po wybraniu **Pokaż wyjście od: Visual C++ Log*. Dane wyjściowe zawiera między innymi listę rzeczywistych ścieżek dołączanych przez intellisense. Jeśli ścieżki nie są zgodne z ścieżkami w *pliku CppProperties.json,* spróbuj zamknąć folder i usunąć podfolder *.vs* zawierający buforowane dane przeglądania.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definiowanie zadań kompilacji za pomocą pliku tasks.vs.json

Skrypty kompilacji lub inne operacje zewnętrzne dotyczące plików w bieżącym obszarze roboczym można zautomatyzować, uruchamiając je jako zadania bezpośrednio w ide. Nowe zadanie można skonfigurować, klikając prawym przyciskiem myszy plik lub folder i wybierając pozycję **Konfiguruj zadania**.

![Otwieranie folderu Konfigurowanie zadań](media/configure-tasks.png)

Spowoduje to utworzenie (lub otwarcie) pliku *tasks.vs.json* w folderze .vs, który program Visual Studio tworzy w głównym folderze projektu. Można zdefiniować dowolne zadanie w tym pliku, a następnie wywołać je z menu kontekstowego **Eksploratora rozwiązań.** Aby kontynuować przykład GCC, poniższy fragment kodu pokazuje kompletny plik *tasks.vs.json* z jako pojedyncze zadanie, które wywołuje *g++.exe* do tworzenia projektu. Załóżmy, że projekt zawiera jeden plik o nazwie *hello.cpp*.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

Plik JSON jest umieszczany w podfolderze *.vs.* Aby wyświetlić ten folder, kliknij przycisk **Pokaż wszystkie pliki** u góry **Eksploratora rozwiązań**. To zadanie można uruchomić, klikając prawym przyciskiem myszy węzeł główny w **Eksploratorze rozwiązań** i wybierając **polecenie build hello**. Po zakończeniu zadania powinien zostać wyświetlony nowy plik *hello.exe* w **Eksploratorze rozwiązań**.

Można zdefiniować wiele rodzajów zadań. W poniższym przykładzie przedstawiono *plik tasks.vs.json* definiujący pojedyncze zadanie. `taskLabel`definiuje nazwę wyświetlaną w menu kontekstowym. `appliesTo`określa, na których plikach można wykonać polecenie. Właściwość `command` odwołuje się do zmiennej środowiskowej COMSPEC, która identyfikuje ścieżkę dla konsoli (*cmd.exe* w systemie Windows). Można również odwołać się do zmiennych środowiskowych, które są zadeklarowane w CppProperties.json lub CMakeSettings.json. Właściwość `args` określa wiersz polecenia, który ma być wywoływany. Makro `${file}` pobiera wybrany plik w **Eksploratorze rozwiązań**. W poniższym przykładzie zostanie wyświetlone nazwa pliku aktualnie wybranego pliku cpp.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Po *zapisaniu pliku tasks.vs.json*można kliknąć prawym przyciskiem myszy dowolny plik *cpp* w folderze, wybrać opcję **Nazwa_echa** z menu kontekstowego i wyświetlić nazwę pliku wyświetlaną w oknie Dane wyjściowe.

Aby uzyskać więcej informacji, zobacz [Odwołanie do schematu tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurowanie parametrów debugowania za pomocą pliku launch.vs.json

Aby dostosować argumenty wiersza polecenia programu i instrukcje debugowania, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratorze rozwiązań** i wybierz pozycję **Debugowanie i uruchamianie ustawień**. Spowoduje to otwarcie istniejącego pliku *launch.vs.json* lub jeśli taki plik nie istnieje, utworzy nowy plik z zestawem minimalnych ustawień uruchamiania. Najpierw masz wybór, jaki rodzaj sesji debugowania chcesz skonfigurować. Do debugowania projektu MinGw-w64 wybieramy **uruchamianie C/C++ dla MinGW/Cygwin (gdb).** Spowoduje to utworzenie konfiguracji uruchamiania dla korzystania z *gdb.exe* z niektórych wykształconych domysły na temat wartości domyślnych. Jedną z tych `MINGW_PREFIX`wartości domyślnych jest . Można zastąpić ścieżkę dosłowną (jak pokazano `MINGW_PREFIX` poniżej) lub zdefiniować właściwość w *CppProperties.json*:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

Aby rozpocząć debugowanie, wybierz plik wykonywalny z listy rozwijanej debugowania, a następnie kliknij zieloną strzałkę:

![Uruchamianie debugera](media/launch-debugger-gdb.png)

Powinno zostać wyświetlone okno dialogowe **Inicjowanie debugera,** a następnie okno konsoli zewnętrznej z uruchomionym programem.

Aby uzyskać więcej informacji, zobacz [launch.vs.json schema reference](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Uruchamianie innych plików wykonywalnych

Można zdefiniować ustawienia uruchamiania dla dowolnego pliku wykonywalnego na komputerze. Poniższy przykład uruchamia *7za* i określa dodatkowe argumenty, dodając je do tablicy `args` JSON:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Po zapisaniu tego pliku nowa konfiguracja pojawi się w rozwijaniu Debug target i można go wybrać, aby uruchomić debuger. Można utworzyć dowolną liczbę konfiguracji debugowania dla dowolnej liczby plików wykonywalnych. Jeśli naciśniesz **klawisz F5** teraz, debuger uruchomi się i trafi dowolny punkt przerwania, który może już ustawiono. Wszystkie znane okna debugera i ich funkcje są teraz dostępne.

::: moniker-end
