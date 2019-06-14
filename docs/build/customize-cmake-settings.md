---
title: Dostosowywanie ustawień kompilacji CMake w programie Visual Studio
ms.date: 05/16/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: a00b18f163758be0238a05c4d2af3195014d79b0
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042536"
---
# <a name="customize-cmake-build-settings"></a>Dostosowywanie ustawień kompilacji narzędzia CMake

::: moniker range="vs-2019"

W programie Visual Studio 2019 r i nowszych możesz dodać konfiguracje i ich ustawienia można dostosować za pomocą **edytora ustawienia narzędzia CMake**. Edytor ma być prostszej alternatywy ręczna Edycja pliku CMakeSettings.json, ale jeśli chcesz bezpośrednio edytować plik, możesz kliknąć **Edycja JSON** łącza w prawej górnej części edytora. 

Aby otworzyć Edytor, kliknij **konfiguracji** listy rozwijanej na głównym pasku narzędzi i wybierz polecenie **Zarządzanie konfiguracjami**.

![Konfiguracji narzędzia CMake listy rozwijanej](media/vs2019-cmake-manage-configurations.png)

Zostanie wyświetlona **ustawienia edytora** przy użyciu konfiguracji instalacji po lewej stronie. 

![Edytor ustawień narzędzia CMake](media/cmake-settings-editor.png)

Program Visual Studio oferuje dwie konfiguracje domyślne: `x64-Debug` i `x86-Debug`. Możesz dodać dodatkowe konfiguracje, klikając przycisk zielony znak plus. Ustawienia, które zostanie wyświetlony w edytorze może się różnić w zależności od konfiguracji jest zaznaczone.

Opcje, które wybrano w edytorze są zapisywane w pliku o nazwie pliku CMakeSettings.json. Ten plik zawiera argumenty wiersza polecenia i zmiennych środowiskowych, które są przekazywane do narzędzia CMake podczas tworzenia projektów. Visual Studio automatycznie; nigdy nie modyfikuje CMakeLists.txt przy użyciu pliku CMakeSettings.json można dostosować kompilacji za pomocą programu Visual Studio, przy równoczesnym zachowaniu pliki projektu narzędzia CMake w charakterze tak, aby inni członkowie zespołu mogą wykorzystywać je za pomocą narzędzi, niezależnie od ich za pomocą.

## <a name="cmake-general-settings"></a>Ogólne ustawienia narzędzia CMake

Następujące ustawienia są dostępne w obszarze **ogólne** nagłówka:

### <a name="configuration-name"></a>Nazwa konfiguracji

Odnosi się do **nazwa** ustawienie. Jest to nazwa, która jest wyświetlana w C++ listy rozwijanej konfiguracji. Możesz użyć `${name}` makra do tworzenia wartości innych właściwości, takich jak ścieżki.


### <a name="configuration-type"></a>Typ konfiguracji

Odnosi się do **typ konfiguracji** ustawienie. Definiuje typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane wartości to "Debug", "MinSizeRel", "Wersja" i "RelWithDebInfo".

### <a name="toolset"></a>Zestaw narzędzi

Odnosi się do **inheritedEnvironments** ustawienie. Definiuje środowiska kompilatora, która będzie służyć do tworzenia wybranej konfiguracji. Obsługiwane wartości zależą od typu konfiguracji. Aby utworzyć niestandardowe środowisko, kliknij przycisk **Edycja JSON** łącze w prawy górny róg edytora ustawień i bezpośredniego edytowania pliku CMakeSettings.json.

### <a name="cmake-toolchain-file"></a>Plik łańcuch narzędzi CMake

Ścieżka do pliku łańcuch narzędzi CMake. Zostaną przekazane do narzędzia CMake w postaci "-DCMAKE_TOOLCHAIN_FILE = \<ścieżka_pliku >".

### <a name="build-root"></a>Tworzenie katalogu głównego

Odnosi się do **wybrany element buildRoot**. Mapuje **-DCMAKE_BINARY_DIR** Przełącz i określa, w którym zostanie utworzona pamięci podręcznej narzędzia CMake. Jeśli folder nie istnieje, zostanie utworzony.

## <a name="command-arguments"></a>Argumenty wiersza polecenia

Następujące ustawienia są dostępne w obszarze **argumenty polecenia** nagłówka:

### <a name="cmake-command-arguments"></a>Argumenty wiersza polecenia narzędzia CMake

Odnosi się do **cmakeCommandArgs**. Określa dodatkowe przełączniki, które chcesz przekazać do CMake.exe.

### <a name="build-command-arguments"></a>Argumenty polecenia kompilacji

Odnosi się do **buildCommandArgs**: Określa dodatkowe przełączniki do przekazania do bazowego systemu kompilacji. Na przykład przekazując - v, gdy przy użyciu generatora Ninja wymusza Ninja w danych wyjściowych wiersze polecenia.


### <a name="ctest-command-arguments"></a>Argumenty wiersza polecenia narzędzia CTest

Odnosi się do**ctestCommandArgs**: Określa dodatkowe przełączniki do przekazania do narzędzia CTest podczas uruchamiania testów.

## <a name="general-settings-for-remote-builds"></a>Ustawienia ogólne dla kompilacji zdalnych

Konfiguracje takie jak Linux, używających kompilacji zdalnych dostępne są również następujące ustawienia:

### <a name="rsync-command-arguments"></a>argumenty wiersza polecenia rsync

Podaj wszelkie argumenty polecenia, które zostaną przekazane do polecenia rsync. 

## <a name="cmake-variables-and-cache"></a>Zmienne narzędzia CMake i pamięć podręczna

Te ustawienia umożliwiają ustawienie zmiennych narzędzia CMake i zapisywać je w pliku CMakeSettings.json. One zostaną przekazane do narzędzia CMake w czasie kompilacji i spowoduje zastąpienie wszelkich wartości może znajdować się w pliku CMakeLists.txt. W tej sekcji można użyć w taki sam sposób, który można użyć CMakeGUI, aby wyświetlić listę wszystkich zmiennych narzędzia CMake dostępne do edycji. Kliknij przycisk **Zapisz i Generuj pamięć podręczną** przycisk, aby wyświetlić listę wszystkich zmiennych narzędzia CMake dostępne do edycji, w tym zaawansowane zmienne (na CMakeGUI). Można filtrować listę według nazwy zmiennych. 

Odnosi się do **zmienne**: zawiera pary nazwa wartość, zmienne narzędzia CMake, które będą przekazywane jako **-D** *_nazwa_ =  _wartość_* do narzędzia CMake. Instrukcje kompilacji projektu narzędzia CMake określić dodanie wszelkie zmienne bezpośrednio do pliku pamięci podręcznej narzędzia CMake, zaleca się dodanie ich w tym miejscu zamiast tego.

## <a name="advanced-settings"></a>Ustawienia zaawansowane

### <a name="cmake-generator"></a>Generatora narzędzia CMake

Odnosi się do **generator**: mapuje do narzędzia CMake **- G** przełącznika i określa generator, który ma być używany. Ta właściwość może również służyć jako makra, `${generator}`, tworząc wartości innych właściwości. Program Visual Studio obsługuje obecnie następujące generatory CMake:

  - "Ninja"
  - "Unix pliki reguł programu make"
  - "Visual Studio 16 2019"
  - "Visual Studio 16 2019 Win64"
  - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  Ponieważ Ninja jest przeznaczona dla szybkości szybkie kompilacji zamiast elastyczności i funkcji, jest ustawiona jako domyślna. Jednak niektóre projekty narzędzia CMake, może być nie można poprawnie tworzyć zawartość przy użyciu Ninja. W takiej sytuacji można nakazać narzędzia CMake w celu wygenerowania projektu programu Visual Studio, zamiast tego.

### <a name="intellisense-mode"></a>Tryb IntelliSense

Dokładne funkcji IntelliSense Ustaw tę opcję na wartość odpowiednią dla Twojego projektu.

### <a name="install-directory"></a>Zainstaluj directory

Katalog, w którym narzędzie CMake instaluje obiektów docelowych, które tworzy on.

### <a name="cmake-executable"></a>Plik wykonywalny narzędzia CMake

Pełna ścieżka do pliku wykonywalnego narzędzia CMake, w tym nazwę i rozszerzenie pliku. Dla kompilacji zdalnych Określ lokalizację narzędzia CMake na komputerze zdalnym.

Konfiguracje takie jak Linux, używających kompilacji zdalnych dostępne są również następujące ustawienia:

### <a name="remote-cmakeliststxt-root"></a>Zdalny katalog główny pliku CMakeLists.txt

Katalog na maszynie zdalnej zawierający główny plik CMakeLists.txt.

### <a name="remote-install-root"></a>Katalog główny instalacji zdalnej

Katalog na komputerze zdalnym, w którym narzędzie CMake instaluje elementów docelowych.

### <a name="remote-copy-sources"></a>Zdalna kopia źródeł

Określa, czy mają być kopiowane pliki źródłowe do maszyny zdalnej i umożliwia określenie, czy użyć polecenia rsync, sftp. 

## <a name="directly-edit-cmakesettingsjson"></a>Directly edit CMakeSettings.json

Można także bezpośrednio edytować `CMakeSettings.json` do utworzenia konfiguracji niestandardowych. **Ustawienia edytora** ma **Edycja JSON** przycisk w prawym górnym rogu, który zostanie otwarty plik do edycji. 

Poniższy przykład pokazuje Przykładowa konfiguracja, który służy jako punkt początkowy:

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

JSON technologia IntelliSense pomaga edytować `CMakeSettings.json` pliku:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png "IntelliSense JSON narzędzia CMake")

Edytor JSON także dowiesz się, gdy wybierzesz niezgodne ustawienia.

Aby uzyskać więcej informacji na temat każdej właściwości w pliku, zobacz [odwołanie do schematu pliku CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Program Visual Studio 2017 udostępnia kilka konfiguracji narzędzia CMake, które definiują, jak CMake.exe jest wywoływana w celu utworzenia pamięci podręcznej narzędzia CMake dla danego projektu. Aby dodać nową konfigurację, kliknij pozycję Konfiguracja, z listy rozwijanej na pasku narzędzi, a następnie wybierz **Zarządzanie konfiguracjami**:

   ![Narzędzie CMake Zarządzanie konfiguracjami](media/cmake-manage-configurations.png)

Można wybrać z listy wstępnie zdefiniowanych konfiguracji:

   ![Narzędzie CMake wstępnie zdefiniowane konfiguracje](media/cmake-configurations.png)

Po raz pierwszy, wybierz konfigurację, program Visual Studio tworzy `CMakeSettings.json` pliku w folderze głównym projektu. Ten plik jest używany ponowne tworzenie pliku pamięci podręcznej narzędzia CMake, na przykład po **czysty** operacji. 

Aby dodać dodatkową konfigurację, kliknij prawym przyciskiem myszy `CMakeSettings.json` i wybierz polecenie **Dodawanie konfiguracji**. 

   ![Dodawanie CMake konfiguracji](media/cmake-add-configuration.png "Dodawanie konfiguracji narzędzia CMake")

Można również edytować plik przy użyciu **edytora ustawienia narzędzia CMake**. Kliknij prawym przyciskiem myszy `CMakeSettings.json` w **Eksploratora rozwiązań** i wybierz polecenie **Edytuj ustawienia narzędzia CMake**. Lub wybierz **Zarządzanie konfiguracjami** z konfiguracji listy rozwijanej w górnej części okna edytora. 

Można także bezpośrednio edytować `CMakeSettings.json` można tworzyć niestandardowe konfiguracje poniższy przykład pokazuje Przykładowa konfiguracja, który służy jako punkt początkowy:

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

JSON technologia IntelliSense pomaga edytować `CMakeSettings.json` pliku:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png "IntelliSense JSON narzędzia CMake")

Aby uzyskać więcej informacji na temat każdej właściwości w pliku, zobacz [odwołanie do schematu pliku CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Projekty CMake w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informacje o konfiguracji narzędzia CMake wstępnie zdefiniowane](cmake-predefined-configuration-reference.md)<br/>
