---
title: Dostosowywanie ustawień kompilacji CMake w programie Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328676"
---
# <a name="customize-cmake-build-settings"></a>Dostosowywanie ustawień kompilacji narzędzia CMake

::: moniker range="vs-2019"

W programie Visual Studio 2019 i nowszych można dodać konfiguracje i dostosować ich ustawienia za pomocą **edytora ustawień CMAKE**. Edytor ma być prostszym rozwiązaniem alternatywnym do ręcznego edytowania pliku *pliku cmakesettings. JSON* , ale jeśli wolisz edytować plik bezpośrednio, możesz kliknąć link **Edytuj kod JSON** w prawym górnym rogu edytora.

Aby otworzyć Edytor, kliknij listę rozwijaną **Konfiguracja** na głównym pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami**.

![Lista rozwijana konfiguracji CMake](media/vs2019-cmake-manage-configurations.png)

Teraz zostanie wyświetlony **Edytor ustawień** z zainstalowanymi konfiguracjami po lewej stronie.

![Edytor ustawień CMake](media/cmake-settings-editor.png)

Program Visual Studio domyślnie `x64-Debug` udostępnia jedną konfigurację. Aby dodać dodatkowe konfiguracje, kliknij zielony znak plus. Ustawienia wyświetlane w edytorze mogą się różnić w zależności od tego, która konfiguracja została wybrana.

Opcje wybrane w edytorze są zapisywane w pliku o nazwie *pliku cmakesettings. JSON*. Ten plik zawiera argumenty wiersza polecenia i zmienne środowiskowe, które są przekazane do CMake podczas kompilowania projektów. Program Visual Studio nigdy nie modyfikuje *CMakeLists. txt* . za pomocą *pliku cmakesettings. JSON* można dostosować kompilację za pośrednictwem programu Visual Studio, pozostawiając nienaruszone pliki projektu cmake, tak aby inni członkowie zespołu mogli korzystać z nich za pomocą dowolnych narzędzi, które są używane.

## <a name="cmake-general-settings"></a>Ustawienia ogólne CMake

Następujące ustawienia są dostępne pod nagłówkiem **ogólnym** :

### <a name="configuration-name"></a>Nazwa konfiguracji

Odpowiada ustawieniu **nazwy** . Ta nazwa jest wyświetlana na liście rozwijanej konfiguracji języka C++. Możesz użyć `${name}` makra do redagowania innych wartości właściwości, takich jak ścieżki.

### <a name="configuration-type"></a>Typ konfiguracji

Odpowiada ustawieniu **ConfigurationType** . Definiuje typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane są wartości "debug", "MinSizeRel", "Release" i "RelWithDebInfo". Mapuje się do [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html).

### <a name="toolset"></a>Zestaw narzędzi

Odpowiada ustawieniu **inheritedEnvironments** . Definiuje środowisko kompilatora, które jest używane do tworzenia wybranej konfiguracji. Obsługiwane wartości zależą od typu konfiguracji. Aby utworzyć środowisko niestandardowe, wybierz łącze **Edytuj kod JSON** w prawym górnym rogu edytora ustawień i bezpośrednio Edytuj plik *pliku cmakesettings. JSON* .

### <a name="cmake-toolchain-file"></a>Plik łańcucha narzędzi CMake

Ścieżka do [pliku łańcucha narzędzi CMAKE](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Ta ścieżka jest przenoszona do CMake jako "-DCMAKE_TOOLCHAIN_FILE \<= FilePath>". Pliki łańcucha narzędzi określają lokalizacje kompilatorów i narzędzi łańcucha narzędzi oraz inne informacje związane z platformą docelową i kompilatorem. Domyślnie program Visual Studio używa [pliku vcpkg łańcucha narzędzi](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) , jeśli to ustawienie jest nieokreślone.

### <a name="build-root"></a>Kompiluj główny

Odnosi się do **element buildroot**. Mapuje do [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)i określa miejsce tworzenia pamięci podręcznej CMAKE. Określony folder zostanie utworzony, jeśli nie istnieje.

## <a name="command-arguments"></a>Argumenty polecenia

Następujące ustawienia są dostępne pod nagłówkiem **argumenty polecenia** :

### <a name="cmake-command-arguments"></a>Argumenty polecenia CMake

Odnosi się do **cmakeCommandArgs**. Określa wszelkie dodatkowe [Opcje wiersza polecenia](https://cmake.org/cmake/help/latest/manual/cmake.1.html) przekazaną do cmake. exe.

### <a name="build-command-arguments"></a>Argumenty polecenia kompilacji

Odnosi się do **buildCommandArgs**. Określa dodatkowe przełączniki do przekazania do bazowego systemu kompilacji. Na przykład przekazywanie `-v` przy użyciu generatora Ninja wymusza Ninja do danych wyjściowych wiersza polecenia.

### <a name="ctest-command-arguments"></a>Argumenty polecenia narzędzia ctest

Odnosi się do **ctestCommandArgs**. Określa dodatkowe [Opcje wiersza polecenia](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) , które zostaną przekazane do narzędzia ctest podczas uruchamiania testów.

## <a name="general-settings-for-remote-builds"></a>Ustawienia ogólne dla kompilacji zdalnych

W przypadku konfiguracji, takich jak Linux, które korzystają z kompilacji zdalnych, dostępne są również następujące ustawienia:

### <a name="rsync-command-arguments"></a>argumenty polecenia rsync

Dodatkowe opcje wiersza polecenia przechodzą do [rsync](https://download.samba.org/pub/rsync/rsync.html), szybkiego i uniwersalnego narzędzia do kopiowania plików.

## <a name="cmake-variables-and-cache"></a>CMake zmienne i pamięć podręczną

Te ustawienia umożliwiają ustawienie zmiennych CMake i zapisanie ich w pliku *pliku cmakesettings. JSON*. Są one przenoszone do CMake w czasie kompilacji i przesłonięcia wszelkich wartości w pliku *CMakeLists. txt* . Tej sekcji można użyć w taki sam sposób, w jaki można użyć CMakeGUI, aby wyświetlić listę wszystkich zmiennych CMake dostępnych do edycji. Kliknij przycisk **Zapisz i Generuj pamięć podręczną** , aby wyświetlić listę wszystkich zmiennych CMAKE dostępnych do edycji, w tym zmiennych zaawansowanych (na CMakeGUI). Można filtrować listę według nazwy zmiennej.

Odnosi się do **zmiennych**. Zawiera parę nazwa-wartość zmiennych CMAKE przekazaną jako **-D** *wartość _nazwy_=* D do cmake. Jeśli instrukcje dotyczące kompilacji projektu CMake określają dodanie jakichkolwiek zmiennych bezpośrednio do pliku pamięci podręcznej CMake, zalecamy ich dodanie zamiast tego.

## <a name="advanced-settings"></a>Ustawienia zaawansowane

### <a name="cmake-generator"></a>Generator CMake

Odnosi się do **generatora**. Mapuje na przełącznik CMake **-G** i określa [Generator CMAKE](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) , który ma być używany. Ta właściwość może być również używana jako makro, `${generator}`podczas tworzenia innych wartości właściwości. Program Visual Studio obecnie obsługuje następujące generatory CMake:

- Ninja
- "Pliki reguł programu make systemu UNIX"
- "Visual Studio 16 2019"
- "Program Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Program Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Program Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Ponieważ Ninja jest zaprojektowana dla szybkich szybkości kompilacji, a nie elastyczności i funkcji, jest ustawiana jako domyślna. Jednak niektóre projekty CMake mogą nie być w stanie poprawnie skompilować przy użyciu ninja. W takim przypadku można wydać CMake do wygenerowania projektu programu Visual Studio.

### <a name="intellisense-mode"></a>Tryb IntelliSense

Tryb IntelliSense używany przez aparat IntelliSense. Jeśli nie wybrano żadnego trybu, program Visual Studio będzie dziedziczyć z określonego zestawu narzędzi.  

### <a name="install-directory"></a>Katalog instalacji

Katalog, w którym CMake są instalowane elementy docelowe. Mapuje do [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>CMake plik wykonywalny

Pełna ścieżka do pliku wykonywalnego programu CMake, w tym nazwa i rozszerzenie pliku. Umożliwia użycie niestandardowej wersji programu CMake z programem Visual Studio. W przypadku kompilacji zdalnych Określ lokalizację CMake na maszynie zdalnej.

W przypadku konfiguracji, takich jak Linux, które korzystają z kompilacji zdalnych, dostępne są również następujące ustawienia:

### <a name="remote-cmakeliststxt-root"></a>Zdalny CMakeLists. txt — główny

Katalog na komputerze zdalnym, który zawiera plik root *CMakeLists. txt* .

### <a name="remote-install-root"></a>Katalog główny instalacji zdalnej

Katalog na komputerze zdalnym, w którym program CMake instaluje elementy docelowe. Mapuje do [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Źródła kopii zdalnych

Określa, czy pliki źródłowe mają być kopiowane do maszyny zdalnej, i umożliwia określenie, czy ma być używany rsync, czy SFTP.

## <a name="directly-edit-cmakesettingsjson"></a>Bezpośrednio Edytuj plik pliku cmakesettings. JSON

Można również bezpośrednio edytować plik *pliku cmakesettings. JSON* w celu utworzenia konfiguracji niestandardowych. **Edytor ustawień** ma przycisk **Edytuj JSON** w prawym górnym rogu, który otwiera plik do edycji.

W poniższym przykładzie przedstawiono przykładową konfigurację, której można użyć jako punktu wyjścia:

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

Funkcja IntelliSense JSON pomaga edytować plik *pliku cmakesettings. JSON* :

   ![Funkcja IntelliSense JSON CMake](media/cmake-json-intellisense.png "Funkcja IntelliSense JSON CMake")

Edytor JSON informuje także o wyborze niezgodnych ustawień.

Aby uzyskać więcej informacji na temat każdej z właściwości w pliku, zobacz [pliku cmakesettings. JSON — odwołanie do schematu](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Program Visual Studio 2017 zawiera kilka konfiguracji CMake, które definiują sposób wywoływania CMake. exe w celu utworzenia pamięci podręcznej CMake dla danego projektu. Aby dodać nową konfigurację, kliknij listę rozwijaną konfiguracja na pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami**:

   ![CMake Zarządzanie konfiguracjami](media/cmake-manage-configurations.png)

Można wybrać jedną z listy wstępnie zdefiniowanych konfiguracji:

   ![Wstępnie zdefiniowane konfiguracje CMake](media/cmake-configurations.png)

Przy pierwszym wybraniu konfiguracji program Visual Studio tworzy plik *pliku cmakesettings. JSON* w folderze głównym projektu. Ten plik jest używany do ponownego tworzenia pliku pamięci podręcznej CMake, na przykład po **czystej** operacji.

Aby dodać dodatkową konfigurację, kliknij prawym przyciskiem myszy plik *pliku cmakesettings. JSON* i wybierz polecenie **Dodaj konfigurację**.

   ![CMake Dodawanie konfiguracji](media/cmake-add-configuration.png "CMake Dodawanie konfiguracji")

Plik można również edytować za pomocą **edytora ustawień CMAKE**. Kliknij prawym przyciskiem myszy plik *pliku cmakesettings. JSON* w **Eksplorator rozwiązań** i wybierz polecenie **Edytuj ustawienia CMAKE**. Lub wybierz pozycję **Zarządzaj konfiguracjami** z listy rozwijanej konfiguracja w górnej części okna edytora.

Można również bezpośrednio edytować plik *pliku cmakesettings. JSON* w celu utworzenia konfiguracji niestandardowych. W poniższym przykładzie przedstawiono przykładową konfigurację, której można użyć jako punktu wyjścia:

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

Funkcja IntelliSense JSON pomaga edytować plik *pliku cmakesettings. JSON* :

   ![Funkcja IntelliSense JSON CMake](media/cmake-json-intellisense.png "Funkcja IntelliSense JSON CMake")

Aby uzyskać więcej informacji na temat każdej z właściwości w pliku, zobacz [pliku cmakesettings. JSON — odwołanie do schematu](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake wstępnie zdefiniowanej konfiguracji](cmake-predefined-configuration-reference.md)
