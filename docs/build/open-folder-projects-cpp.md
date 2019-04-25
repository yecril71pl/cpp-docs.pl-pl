---
title: Obsługa otwierania folderu dla systemów kompilacji języka C++ w programie Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 380a96bcb1a119b2b6d4104d60936217d1350fbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274200"
---
# <a name="open-folder-projects-for-c"></a>Otwórz Folder projektów w języku C++

W programie Visual Studio 2017 i nowszych funkcji "Otwórz Folder" umożliwia otwieranie folderu plików źródłowych i od razu Rozpocznij kodowanie dzięki obsłudze technologii IntelliSense, przeglądanie, refaktoryzację, debugowanie i tak dalej. Nie pliku SLN lub .vcxproj pliki są ładowane; Jeśli to konieczne, niestandardowe zadania można określić także twórz i uruchamiaj parametrów za pomocą plików prostych JSON. Aby uzyskać ogólne informacje dotyczące otwierania folderu, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

Narzędzie CMake jest zintegrowana w środowisku IDE programu Visual Studio jako narzędzia CMake dla programu Visual Studio, składnik obciążeniu C++ dla komputerów stacjonarnych. Aby uzyskać więcej informacji, zobacz [projektów CMake w programie Visual Studio](cmake-projects-in-visual-studio.md). Dla drugiego systemu kompilacji można użyć funkcji Otwórz Folder. Otwórz Folder efektywnie oddziela Edytor kodu, debuger i analizatorów — system kompilacji i zestawu narzędzi kompilatora. Za pomocą edytora kodu C++ z jego rozbudowane funkcje IntelliSense, analizatory kodu i debuger programu Visual Studio z praktycznie dowolnego systemu kompilacji, w tym CMake, Ninja, QMake (dla projektów Qt), gyp, SCons, Gradle, Buck, markę i nie tylko. Nawet w programach pojedynczy plik lub zbiór luźno plików bez systemu kompilacji.

Aby użyć Otwórz Folder, w menu głównym wybierz **pliku | Otwórz | Folder** lub naciśnij **Ctrl + Shift + Alt + O**. Eksplorator rozwiązań natychmiast wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć jego edycji. W tle programu Visual Studio uruchamia indeksowanie plików, aby włączyć funkcję IntelliSense, nawigowanie i funkcje refaktoryzacji. Jak edytowanie, tworzenie, przenieść lub usunąć pliki programu Visual Studio automatycznie śledzi zmiany i stale aktualizuje jego indeksu funkcji IntelliSense. 

## <a name="qmake-projects-that-target-the-qt-framework"></a>Projekty QMake, których platformą docelową platformę Qt

Można użyć narzędzia CMake dla programu Visual Studio pod kątem Qt do tworzenia projektów Qt lub można użyć [rozszerzenie programu Visual Studio Qt](https://download.qt.io/development_releases/vsaddin/) dla programu Visual Studio 2015 lub Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc

Możesz użyć dowolnego systemu kompilacji w programie Visual Studio i nadal korzystaj z zalet środowisko IDE języka C++ i debugera. Po otwarciu folderu głównego projektu, Edytor kodu C++ używa heurystyki do indeksowania plików źródłowych dla technologii IntelliSense i przeglądania. Za dostarczanie wskazówek na temat strukturę kodu przez edycję pliku CppProperties.json. W podobny sposób można skonfigurować i wywołać program kompilacji, edytowania pliku launch.vs.json.

## <a name="configuring-open-folder-projects"></a>Konfigurowanie projektów Otwórz Folder

Otwórz Folder projektu można dostosować za pomocą trzech plików JSON:

| | |
|-|-|
|CppProperties.json|Określ informacje o konfiguracji niestandardowej do przeglądania. Ten plik, należy utworzyć, jeśli to konieczne, w folderze głównym projektu. (Nie używane w projektach CMake).|
|tasks.vs.json|Określenie niestandardowych poleceń kompilacji i przełączniki kompilatora. Udostępnianych za pośrednictwem **Eksploratora rozwiązań** element menu kontekstowego **skonfigurować zadania**.|
|launch.vs.json|Określ argumenty wiersza polecenia dla debugera. Udostępnianych za pośrednictwem **Eksploratora rozwiązań** element menu kontekstowego **ustawienia debugowania i uruchamiania**.|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>Konfigurowanie funkcji IntelliSense i przeglądania wskazówek z CppProperties.json

Funkcja IntelliSense i przeglądanie częściowo zachowanie zależy od aktywną konfigurację kompilacji, który definiuje #include ścieżki, przełączniki kompilatora i inne parametry. Domyślnie program Visual Studio zawiera konfiguracje Debug i Release. Projekty CMake w tym celu użyć pliku CMakeSettings.json i pliki CMakeLists.txt. Dla innych rodzajów projektów Otwórz Folder może być konieczne utworzenie konfiguracji niestandardowej w kolejności dla technologii IntelliSense i przeglądania funkcji w pełni zrozumienie kodu. Aby zdefiniować nową konfigurację, Utwórz plik o nazwie CppProperties.json w folderze głównym. Oto przykład:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "windows-msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Aby uzyskać więcej informacji, zobacz [odwołanie do schematu CppProperties](cppproperties-schema-reference.md).

### <a name="define-build-tasks-with-tasksvsjson"></a>Definiowanie zadań kompilacji za pomocą pliku tasks.vs.json

Można zautomatyzować skrypty kompilacji lub innych zewnętrznych operacji na plikach, znajdującym się w bieżącym obszarze roboczym, uruchamiając je jako zadania bezpośrednio w środowisku IDE. Można skonfigurować nowe zadanie, kliknij prawym przyciskiem myszy pliku lub folderu i wybierając **skonfigurować zadania**.

![Otwórz Folder skonfigurować zadania](media/open-folder-config-tasks.png)

Tworzy (lub zostanie otwarty) **tasks.vs.json** pliku w folderze .vs, który program Visual Studio tworzy w folderze głównym projektu. Można zdefiniować wszystkie dowolnego zadania w tym pliku, a następnie wywołaj ją z **Eksploratora rozwiązań** menu kontekstowego. Poniższy przykład pokazuje plik pliku tasks.vs.json, który definiuje jedno zadanie. `taskName` Określa nazwę, która jest wyświetlana w menu kontekstowym. `appliesTo` Określa pliki, które można wykonać polecenia na. `command` Właściwość odwołuje się do zmiennej środowiskowej COMSPEC, który określa ścieżkę do konsoli (cmd.exe na Windows). Możesz też przywołać zmienne środowiskowe, które są zadeklarowane w CppProperties.json lub w pliku CMakeSettings.json. `args` Właściwość określa wiersz polecenia do wywołania. `${file}` — Makro pobiera wybranego pliku w **Eksploratora rozwiązań**. Poniższy przykład spowoduje wyświetlenie nazwy pliku .cpp zaznaczony.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Po zapisaniu pliku tasks.vs.json, kliknij prawym przyciskiem myszy dowolny plik .cpp, w tym folderze, wybierz polecenie **Echo, nazwa_pliku** z menu kontekstowego i zobacz, nazwa pliku jest wyświetlany w oknie danych wyjściowych.

Aby uzyskać więcej informacji, zobacz [odwołanie do schematu pliku Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfiguruj parametry debugowania za pomocą pliku launch.vs.json

Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**. Spowoduje to otwarcie istniejącego **launch.vs.json** pliku, lub jeśli żaden nie istnieje, zostanie utworzony nowy plik wstępnie wypełnione informacjami o programie wybrano.

Aby określić dodatkowe argumenty, wystarczy dodać ich w `args` tablicę JSON, jak pokazano w poniższym przykładzie:

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

Po zapisaniu tego pliku, nowa konfiguracja zostanie wyświetlona w menu rozwijanym Debuguj element docelowy i możesz wybrać go, aby uruchomić debuger. Można utworzyć wiele konfiguracji debugowania, jak chcesz, dla dowolnej liczby plików wykonywalnych. Jeśli użytkownik naciśnie klawisz **F5** teraz uruchomić i trafiony punkt przerwania, wszelkie może już zostały ustawione przez debuger. Obecnie są dostępne wszystkie znajomego debugera systemu windows i ich funkcje.
