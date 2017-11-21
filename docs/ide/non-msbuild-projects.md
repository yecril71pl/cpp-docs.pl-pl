---
title: "Otwórz Folder projekty w programie Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da81f8731be97c69a73eddb96e9e56e49c59c91b
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="open-folder-projects-in-visual-c"></a>Otwórz Folder projekty w programie Visual C++
Visual Studio 2017 wprowadza funkcji "Otwórz Folder", która umożliwia otwieranie folderu plików źródłowych i natychmiast programować o obsługę funkcji IntelliSense, przeglądanie, refaktoryzacji, debugowanie i tak dalej. Żadne pliki SLN lub .vcxproj są ładowane; w razie potrzeby można określić niestandardowych zadań oraz tworzenie i uruchamianie parametrów za pomocą plików prostych JSON. Obsługiwane przez Otwórz Folder, Visual C++ może teraz obsługiwać nie tylko utracić kolekcje plików, ale również praktycznie dowolnego kompilacji systemu, w tym CMake, Nindżą, QMake (dla projektów Qt), gyp, SCons, Gradle, Buck, Utwórz i inne. 

Aby użyć Otwórz Folder, w menu głównym wybierz *pliku | Otwórz | Folder* lub naciśnij klawisz *Ctrl + Shift + Alt + O*. Eksplorator rozwiązań natychmiast wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć edycji. W tle Visual Studio rozpoczyna indeksowania pliki, aby włączyć IntelliSense, nawigacji i funkcje refaktoryzacji. Jak edytować, tworzenie, przenoszenie i usuwania plików programu Visual Studio automatycznie śledzenia zmian i stale aktualizuje jego indeks IntelliSense. 
  
## <a name="cmake-projects"></a>Projekty CMake
CMake jest zintegrowana w programie Visual Studio IDE jako narzędzia CMake w języku Visual C++, część obciążenia pulpitu C++. Aby uzyskać więcej informacji, zobacz [CMake Tools dla Visual C++](cmake-tools-for-visual-cpp.md).
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake projektów, które Qt platformy docelowej
Umożliwia CMake narzędzi dla programu Visual C++ docelowy Qt do kompilacji projektów Qt lub można użyć rozszerzenia Qt programu Visual Studio. Uwaga: Począwszy od sierpnia 2017 r. [Qt Visual Studio rozszerzenia obsługi programu Visual Studio 2017](https://download.qt.io/development_releases/vsaddin/) jest dostępna w wersji beta.

## <a name="gyp-cons-scons-buck-etc"></a>gyp wad, SCons, Buck, itp.
Można użyć dowolnego systemu kompilacji w programie Visual C++ i nadal korzystać z zalet środowiska IDE Visual C++ i debugera. Po otwarciu folderu głównego projektu Visual C++ korzysta z algorytmów heurystycznych do indeksowania plików źródłowych dla IntelliSense i przeglądania. Musisz podać wskazówki dotyczące struktury kodu przez edycję plików CppProperties.json. W podobny sposób można skonfigurować program kompilacji, edytując plik launch.vs.json. 

## <a name="configuring-open-folder-projects"></a>Konfigurowanie projektów Otwórz Folder
Otwórz Folder projektu można dostosować za pomocą trzech plików JSON:
|||
|-|-|
|CppProperties.json|Określ informacje o konfiguracji niestandardowej do przeglądania. Ten plik, należy utworzyć, jeśli to konieczne, w folderze głównym projektu.|
|Launch.VS.JSON|Określ argumenty wiersza polecenia. Używanych przez **Eksploratora rozwiązań** elementu menu kontekstowego **debugowania i ustawienia uruchamiania**.|
|Tasks.VS.JSON|Określenie niestandardowych poleceń kompilacji i przełączniki kompilatora. Używanych przez **Eksploratora rozwiązań** elementu menu kontekstowego **skonfigurować zadania**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Skonfiguruj CppProperties.json IntelliSense
IntelliSense i przeglądania częściowo zachowanie zależy od konfiguracji active kompilacji, który definiuje #include ścieżek, przełączniki kompilatora i innych parametrów. Domyślnie program Visual Studio udostępnia konfiguracje Debug i Release. Dla niektórych projektów może być konieczne utworzenie konfiguracji niestandardowej w kolejności dla IntelliSense i przeglądania funkcje w pełni zrozumienie kodu. Aby zdefiniować nową konfigurację, Utwórz plik o nazwie CppProperties.json w folderze głównym. Oto przykład:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Konfiguracja może być jedną z następujących właściwości:

|||  
|-|-| 
|`name`|Nazwa konfiguracji, który pojawia się na liście rozwijanej konfiguracji C++|
|`includePath`|listę folderów, które powinny być określone w ścieżce include (mapy do /I dla większości kompilatory)|
|`defines`|Lista makra, które powinny być zdefiniowane (mapy do /D dla większości kompilatory)|
|`compilerSwitches`|jeden lub więcej dodatkowych przełączników, które wpływają na zachowanie IntelliSense|
|`forcedInclude`|Nagłówek automatycznie uwzględnić w każdej jednostki kompilacji (mapuje /FI dla MSVC lub - zawierają clang)|
|`undefines`|Lista makra być Niezdefiniowany (map do /U dla MSVC)|
|`intelliSenseMode`|Aparat IntelliSense do użycia. Można określić architektury określonych wariantów MSVC, gcc lub Clang:
- msvc-x86 (ustawienie domyślne)
- msvc x64
- msvc arm
- Windows-clang-x86
- Windows-clang-x64
- Windows-clang — arm
- X64 systemu Linux
- X86 systemu Linux
- Linux — arm
- gccarm

Rozszerzanie zmiennych środowiskowych obsługuje CppProperties.json dla obejmują ścieżki i wartości innych właściwości. Składnia jest `${env.FOODIR}` aby rozwinąć zmiennej środowiskowej `%FOODIR%`.

Masz również dostęp do poniższych wbudowanych makr wewnątrz tego pliku:
|||
|-|-|
|`${workspaceRoot}`| Pełna ścieżka do folderu roboczego|
|`${projectRoot}`| Pełna ścieżka do folderu, w której jest umieszczona CppProperties.json|
|`${vsInstallDir}`| Pełna ścieżka do folderu, w którym zainstalowany jest uruchomione wystąpienie VS 2017|

Na przykład projektu folderem include, obejmuje także windows.h i inne typowe nagłówki z zestawu SDK systemu Windows można zaktualizować Twojego CppProperties.json zawiera plik konfiguracji z tych:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**Uwaga:** `%WindowsSdkDir%` i `%VCToolsInstallDir%` nie są ustawione jako globalnych zmiennych środowiskowych dlatego należy upewnić się, uruchom devenv.exe z "wiersz polecenia dla deweloperów VS 2017" definiujący zmienne.

Rozwiązywać IntelliSense błędy spowodowane przez brak ścieżki dołączanych plików, otwórz **listy błędów** Filtruj dane wyjściowe do "Tylko IntelliSense" i kod błędu E1696 "nie można otworzyć pliku źródłowego...". 

Można utworzyć dowolną liczbę konfiguracje w CppProperties.json. Każdy będą wyświetlane na liście rozwijanej konfiguracji:

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```
### <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań z tasks.vs.json
Można zautomatyzować kompilacji skryptów lub inne operacje zewnętrznych od plików, które ma w bieżącym obszarze roboczym przez uruchomienie zadania bezpośrednio w środowisku IDE. Można skonfigurować nowe zadanie prawym przyciskiem myszy plik lub folder, a następnie wybierając **skonfigurować zadania**. 

![Otwórz Folder skonfigurować zadania](media/open-folder-config-tasks.png)

Tworzy (lub otwiera) `tasks.vs.json` pliku w folderze VS, które Visual Studio utworzy w folderze głównym projektu. Można zdefiniować dowolnego dowolnego zadania w tym pliku, a następnie wywołaj z **Eksploratora rozwiązań** menu kontekstowego. Poniższy przykład przedstawia plik tasks.vs.json, który definiuje jedno zadanie. `taskName`Określa nazwę, która jest wyświetlana w menu kontekstowym. `appliesTo`Określa pliki, które można wykonać polecenia na. `command` Właściwość odwołuje się do zmiennej środowiskowej COMSPEC, który określa ścieżkę do konsoli (cmd.exe w systemie Windows). `args` Właściwość określa wiersz poleceń do wywołania. `${file}` Makro pobiera wybrany plik w **Eksploratora rozwiązań**. Poniższy przykład będzie wyświetlana nazwa pliku .cpp obecnie wybrany.

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
Po zapisaniu tasks.vs.json, kliknij prawym przyciskiem myszy dowolny plik .cpp w folderze, wybierz polecenie **Echo filename** z menu kontekstowego i zobacz, wyświetlana nazwa pliku w oknie danych wyjściowych.

#### <a name="appliesto"></a>Element appliesTo
Można tworzyć zadania dla dowolnego pliku lub folderu, określając jej nazwę w `appliesTo` pól, na przykład `"appliesTo" : "hello.cpp"`. Następujące maski plików może być używane jako wartości:
|||
|-|-|
|`"*"`| zadanie jest dostępna dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.cpp"`| zadanie jest dostępny dla wszystkich plików z .cpp rozszerzenia w obszarze roboczym|
|`"/*.cpp"`| zadanie jest dostępny dla wszystkich plików z .cpp rozszerzenia w katalogu głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów folderu "src"|
|`"makefile"`| zadanie jest dostępny dla wszystkich plików w pliku reguł programu make w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępne tylko w pliku reguł programu make w folderze głównym obszaru roboczego|

#### <a name="output"></a>dane wyjściowe
Użyj `output` właściwości w celu określenia pliku wykonywalnego, który zostanie uruchomiony po naciśnięciu **F5**. Na przykład:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Makra dla tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Określa wszelkie zmienna środowiskowa (na przykład ${env. ŚCIEŻKA} ${env.COMSPEC} itd.) dla wiersza polecenia dewelopera ustawiono. Aby uzyskać więcej informacji, zobacz [wiersz polecenia dla programu Visual Studio deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu roboczego (na przykład "C:\sources\hello")|
|`${file}`| Pełna ścieżka pliku lub folder wybrany do uruchomienia tego zadania przed (na przykład "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| Ścieżka względna do pliku lub folderu (na przykład "src\hello.cpp")|
|`${fileBasename}`| Nazwa pliku bez ścieżki i rozszerzenia (na przykład "hello")|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyjątkiem nazwy pliku (na przykład "C:\sources\hello\src")|
|`${fileExtname}`| rozszerzenie wybranego pliku (na przykład, "CPP")|

#### <a name="custom-macros"></a>Niestandardowe makra
Aby zdefiniować niestandardowe makra w tasks.vs.json, Dodaj parę nazwa: wartość przed bloków zadań. W poniższym przykładzie zdefiniowano makra o nazwie `outDir` które jest używane w `args` właściwości:

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfiguruj parametry debugowania z launch.vs.json
Aby dostosować argumenty wiersza polecenia programu, kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań** i wybierz **debugowania i ustawienia uruchamiania**. Spowoduje to otwarcie istniejącego `launch.vs.json` pliku, lub jeśli żaden nie istnieje, zostanie utworzony nowy plik wstępnie wypełnione informacjami o programie wybrano. 

Aby określić dodatkowe argumenty, po prostu dodaj je w `args` tablicy JSON, jak pokazano w poniższym przykładzie:

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

Po zapisaniu tego pliku nowej konfiguracji zostanie wyświetlona na liście rozwijanej debugowania docelowych i możesz wybrać je można uruchomić debugera. Można utworzyć wiele konfiguracje debugowania, jak lubisz, dla dowolnej liczby plików wykonywalnych. Jeśli naciśniesz **F5** teraz, uruchom i trafień dowolnego punktu przerwania może już zostały ustawione przez debuger. Wszystkie znane debugera systemu windows i ich funkcje są teraz dostępne.

## <a name="see-also"></a>Zobacz też
[IDE i narzędzia do programowania w języku Visual C++](ide-and-tools-for-visual-cpp-development.md)

