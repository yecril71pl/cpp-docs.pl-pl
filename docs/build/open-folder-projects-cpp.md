---
title: Obsługa otwartych folderów dla C++ systemów kompilacji w programie Visual Studio
ms.date: 10/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 0eed40430050655f8fd9bdc83144adc7aa8c32e7
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778342"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Obsługa otwartych folderów dla C++ systemów kompilacji w programie Visual Studio

::: moniker range="vs-2015"

Funkcja Otwórz folder jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

W programie Visual Studio 2017 i nowszych funkcja "Otwórz folder" umożliwia otworzenie folderu plików źródłowych i natychmiastowe rozpoczęcie kodowania z obsługą funkcji IntelliSense, przeglądanie, Refaktoryzacja, debugowanie i tak dalej. Podczas edytowania, tworzenia, przenoszenia lub usuwania plików program Visual Studio automatycznie śledzi zmiany i ciągle aktualizuje swój indeks IntelliSense. Nie są załadowane pliki sln ani vcxproj; w razie konieczności można określić zadania niestandardowe, a także parametry kompilowania i uruchamiania za poorednictwem prostych plików JSON. Ta funkcja umożliwia integrację dowolnego systemu kompilacji innej firmy z Visual Studio. Aby uzyskać ogólne informacje na temat otwartego folderu, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake i QT

CMake jest zintegrowany w środowisku IDE programu Visual Studio jako składnik obciążenia C++ pulpitu. Przepływ pracy dla CMake nie jest identyczny z przepływem pracy opisanym w tym artykule. Jeśli używasz programu CMake, zobacz [CMAKE projects w programie Visual Studio](cmake-projects-in-visual-studio.md). Można również użyć CMake do kompilowania projektów QT lub użyć [rozszerzenia QT programu Visual Studio](https://download.qt.io/development_releases/vsaddin/) dla programu visual Studio 2015 lub visual Studio 2017.

## <a name="other-build-systems"></a>Inne systemy kompilacji

Aby użyć środowiska IDE programu Visual Studio z systemem kompilacji lub zestawem narzędzi kompilatora, który nie jest bezpośrednio obsługiwany z menu głównego wybierz **plik | Otwórz | Lub naciśnij** **klawisze Ctrl + Shift + Alt + O**. Przejdź do folderu, który zawiera pliki kodu źródłowego. Aby skompilować projekt, skonfigurować funkcję IntelliSense i ustawić parametry debugowania, należy dodać trzy pliki JSON:

| | |
|-|-|
|Pliku cppproperties. JSON|Określ informacje o konfiguracji niestandardowej do przeglądania. Utwórz ten plik, w razie konieczności, w folderze głównym projektu. (Nieużywane w projektach CMake).|
|Tasks. vs. JSON|Określ niestandardowe polecenia kompilacji. Dostępne za pośrednictwem **elementu menu**kontekstowego **Eksplorator rozwiązań** .|
|Uruchom plik. vs. JSON|Określ argumenty wiersza polecenia dla debugera. Dostępne za pośrednictwem elementu menu kontekstowego **Eksplorator rozwiązań** **Ustawienia debugowania i uruchamiania**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Skonfiguruj nawigację po kodzie za pomocą pliku pliku cppproperties. JSON

W przypadku funkcji IntelliSense i przeglądania, takich jak **Przejdź do definicji** , aby działała prawidłowo, program Visual Studio musi wiedzieć, którego kompilatora używasz, gdzie są nagłówki systemowe i gdzie znajdują się jakiekolwiek dodatkowe pliki dołączane, jeśli nie znajdują się one bezpośrednio w otwarty folder (folder obszaru roboczego). Aby określić konfigurację, możesz wybrać pozycję **Zarządzaj konfiguracjami** na liście rozwijanej na głównym pasku narzędzi:

![Lista rozwijana zarządzania konfiguracjami](media/manage-configurations-dropdown.png)

Obecnie program Visual Studio oferuje cztery konfiguracje domyślne, wszystkie dla kompilatora Microsoft C++ :

![Konfiguracje domyślne](media/default-configurations.png)

Jeśli na przykład wybierzesz opcję **x64-Debug**, program Visual Studio tworzy plik o nazwie *pliku cppproperties. JSON* w folderze głównym projektu i wypełnia go następująco:

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

Ta konfiguracja "dziedziczy" zmienne środowiskowe wiersz polecenia dla deweloperów programu Visual Studio [x64](building-on-the-command-line.md). Jedna z tych zmiennych jest `INCLUDE` i można do niej odwołać się w tym miejscu przy użyciu makra `${env.INCLUDE}`. Właściwość `includePath` nakazuje programowi Visual Studio wyszukanie wszystkich źródeł wymaganych przez funkcję IntelliSense. W tym przypadku jest to komunikat "Znajdź wszystkie katalogi określone przez zmienną środowiskową INCLUDE, a także wszystkie katalogi w bieżącym drzewie folderów roboczych". Właściwość `name` to nazwa, która będzie wyświetlana na liście rozwijanej i może być dowolna. Właściwość `defines` udostępnia podpowiedzi do funkcji IntelliSense, gdy napotykają one instrukcje kompilacji warunkowej. Właściwość `intelliSenseMode` zawiera dodatkowe wskazówki na podstawie typu kompilatora. Dostępne są różne opcje MSVC, w zatoce i Clang.

> [!NOTE]
> Jeśli program Visual Studio prawdopodobnie zignoruje ustawienia w *pliku cppproperties. JSON*, spróbuj dodać wyjątek do pliku *. gitignore* w następujący sposób: `!/CppProperties.json`.

## <a name="example-configuration-for-gcc"></a>Przykładowa konfiguracja dla programu w zatoce

Jeśli używasz kompilatora innego niż Microsoft C++, musisz utworzyć niestandardową konfigurację i środowisko w pliku *pliku cppproperties. JSON*. W poniższym przykładzie przedstawiono kompletny plik *pliku cppproperties. JSON* z jedną konfiguracją niestandardową używaną w ramach programu w ramach instalacji usługi MSYS2:

```json
{
  "configurations": [
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
          "TOOLSET_VERSION": "8.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
   }
}
```

Zwróć uwagę na blok `environments`. Definiuje właściwości, które zachowują się jak zmienne środowiskowe i są dostępne nie tylko w pliku *pliku cppproperties. JSON* , ale również w innych plikach konfiguracji *Task. vs. JSON* i *uruchamiania. vs. JSON*. @No__t_0 konfiguracja dziedziczy środowisko `mingw_w64` i używa jego właściwości `INCLUDE`, aby określić wartość dla `includePath`. W razie potrzeby możesz dodać inne ścieżki do tej właściwości tablicy.

> [!WARNING]
> Obecnie występuje znany problem, w którym wartość `INCLUDE` określona w `environments` nie jest prawidłowo przenoszona do właściwości `includePath`. Aby obejść ten problem, dodając pełny literał, Dołącz ścieżki do tablicy `includePath`.

Właściwość `intelliSenseMode` ma ustawioną wartość odpowiednią dla programu w zatoce. Aby uzyskać więcej informacji na temat wszystkich tych właściwości, zobacz [pliku cppproperties Schema Reference](cppproperties-schema-reference.md).

Gdy wszystko działa prawidłowo, po umieszczeniu wskaźnika myszy na typie zobaczysz funkcję IntelliSense z nagłówków w witrynie współpracy w zatoce:

![Technologia IntelliSense w zatoce](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Włączanie diagnostyki IntelliSense

Jeśli nie widzisz oczekiwanej technologii IntelliSense, możesz rozwiązać problemy, przechodząc do opcji **Narzędzia**  > **Opcje**  > **edytorze tekstów**  > **C/C++**   > **Zaawansowane** i ustawienie **Włącz rejestrowanie** na **wartość true**. Aby rozpocząć pracę z programem, spróbuj ustawić **poziom rejestrowania** na 5 i **filtry rejestrowania** na 8.

![Rejestrowanie informacji diagnostycznych](media/diagnostic-logging.png)

Dane wyjściowe są przekazywane do **okno dane wyjściowe** i są widoczne po wybraniu polecenia **Pokaż dane wyjściowe z: C++ dziennik wizualny*. Dane wyjściowe zawierają między innymi listę rzeczywistych ścieżek dołączania, które próbuje użyć IntelliSense. Jeśli ścieżki nie pasują do tych w pliku *pliku cppproperties. JSON*, spróbuj zamknąć ten folder i usunąć podfolder *. vs* zawierający buforowane dane przeglądania.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definiowanie zadań kompilacji przy użyciu zadań. vs. JSON

Możesz zautomatyzować skrypty kompilacji lub wszystkie inne operacje zewnętrzne na plikach znajdujących się w bieżącym obszarze roboczym, uruchamiając je jako zadania bezpośrednio w środowisku IDE. Nowe zadanie można skonfigurować, klikając prawym przyciskiem myszy plik lub folder, a następnie wybierając pozycję **Konfiguruj zadania**.

![Otwórz folder konfiguracja zadań](media/configure-tasks.png)

Spowoduje to utworzenie (lub otwarcie) pliku *Tasks. vs. JSON* w folderze. vs, który program Visual Studio tworzy w folderze głównym projektu. Można zdefiniować dowolne dowolne zadanie w tym pliku, a następnie wywołać je z menu kontekstowego **Eksplorator rozwiązań** . Aby kontynuować przykład w zatoce, w poniższym fragmencie kodu przedstawiono kompletny plik *Tasks. vs. JSON* zawierający pojedynczy zadanie, które wywołuje program *g + +. exe* w celu skompilowania projektu. Załóżmy, że projekt zawiera jeden plik o nazwie *Hello. cpp*.

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

Plik JSON jest umieszczany w podfolderze *. vs* , który można zobaczyć po kliknięciu przycisku **Pokaż wszystkie pliki** w górnej części **Eksplorator rozwiązań**. To zadanie można uruchomić, klikając prawym przyciskiem myszy węzeł główny w **Eksplorator rozwiązań** i wybierając polecenie **Kompiluj Hello**. Po zakończeniu zadania w **Eksplorator rozwiązań**powinien zostać wyświetlony nowy plik *Hello. exe* .

Można zdefiniować wiele rodzajów zadań. W poniższym przykładzie przedstawiono *plik Tasks. vs. JSON* , który definiuje pojedyncze zadanie. `taskLabel` definiuje nazwę, która pojawia się w menu kontekstowym. `appliesTo` definiuje pliki, na których można wykonać polecenie. Właściwość `command` odwołuje się do zmiennej środowiskowej wywołana, która identyfikuje ścieżkę konsoli programu (*cmd. exe* w systemie Windows). Można także odwoływać się do zmiennych środowiskowych, które są zadeklarowane w pliku cppproperties. JSON lub pliku cmakesettings. JSON. Właściwość `args` określa wiersz polecenia, który ma zostać wywołany. Makro `${file}` pobiera wybrany plik z **Eksplorator rozwiązań**. W poniższym przykładzie zostanie wyświetlona nazwa pliku aktualnie wybranego pliku CPP.

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

Po zapisaniu *zadań. vs. JSON*można kliknąć prawym przyciskiem myszy dowolny plik *. cpp* w folderze, wybrać polecenie **echo filename** z menu kontekstowego i zobaczyć nazwę pliku wyświetlanego w oknie danych wyjściowych.

Aby uzyskać więcej informacji, zobacz [Dokumentacja schematu Tasks. vs. JSON](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurowanie parametrów debugowania za pomocą pliku Launch. vs. JSON

Aby dostosować argumenty wiersza polecenia programu i instrukcje debugowania, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksplorator rozwiązań** a następnie wybierz pozycję **Ustawienia debugowania i uruchamiania**. Spowoduje to otwarcie istniejącego pliku *uruchamiania. vs. JSON* lub jeśli nie istnieje, spowoduje utworzenie nowego pliku z zestawem minimalnych ustawień uruchamiania. Po pierwsze użytkownik otrzymuje wybór rodzaju sesji debugowania, która ma zostać skonfigurowana. Do debugowania projektu MinGw-W64 wybieramy **CC++ /Launch dla MinGGW/Cygwin (GDB)** . Spowoduje to utworzenie konfiguracji uruchamiania dla programu *GDB. exe* z niektórymi przewidzianymi próbami dotyczącymi wartości domyślnych. Jedną z tych wartości domyślnych jest `MINGW_PREFIX`. Można zastąpić ścieżkę literału (jak pokazano poniżej) lub można zdefiniować Właściwość `MINGW_PREFIX` w *pliku cppproperties. JSON*:

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

Aby rozpocząć debugowanie, wybierz plik wykonywalny na liście rozwijanej debugowanie, a następnie kliknij zieloną strzałkę:

![Uruchom Debuger](media/launch-debugger-gdb.png)

Powinno zostać wyświetlone okno dialogowe **Inicjowanie debugera** , a następnie zewnętrzne okno konsoli z uruchomionym programem.

Aby uzyskać więcej informacji, zobacz informacje o [schemacie Launch. vs. JSON](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Uruchamianie innych plików wykonywalnych

Można zdefiniować ustawienia uruchamiania dla dowolnego pliku wykonywalnego na komputerze. Poniższy przykład uruchamia *7za* i określa dodatkowe argumenty, dodając je do tablicy JSON `args`:

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

Po zapisaniu tego pliku Nowa konfiguracja zostanie wyświetlona na liście rozwijanej cel debugowania i można ją wybrać, aby uruchomić debuger. Można utworzyć dowolną liczbę konfiguracji debugowania dla dowolnej liczby plików wykonywalnych. Po naciśnięciu klawisza **F5** teraz zostanie uruchomiony debuger i zostanie osiągnięty dowolny punkt przerwania, który został już ustawiony. Wszystkie znane okna debugera i ich funkcje są teraz dostępne.

::: moniker-end
