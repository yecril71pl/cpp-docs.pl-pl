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

W programie Visual Studio 2019 i nowszych można dodawać konfiguracje i dostosowywać ich ustawienia za pomocą **edytora ustawień CMake**. Edytor ma być prostszą alternatywą dla ręcznej edycji pliku *CMakeSettings.json,* ale jeśli wolisz edytować plik bezpośrednio, możesz kliknąć łącze **Edytuj JSON** w prawym górnym rogu edytora.

Aby otworzyć edytor, kliknij z listy rozwijanej **Konfiguracja** na głównym pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami**.

![CKsuj konfiguracje rozwijane](media/vs2019-cmake-manage-configurations.png)

Teraz zobaczysz **Edytor ustawień** z zainstalowanymi konfiguracjami po lewej stronie.

![Edytor ustawień CMake](media/cmake-settings-editor.png)

Visual Studio `x64-Debug` domyślnie zapewnia jedną konfigurację. Możesz dodać dodatkowe konfiguracje, klikając zielony znak plus. Ustawienia widoczne w edytorze mogą się różnić w zależności od wybranej konfiguracji.

Opcje, które można wybrać w edytorze są zapisywane w pliku o nazwie *CMakeSettings.json*. Ten plik zawiera argumenty wiersza polecenia i zmienne środowiskowe, które są przekazywane do CMake podczas tworzenia projektów. Visual Studio nigdy nie modyfikuje *CMakeLists.txt* automatycznie; za pomocą *CMakeSettings.json* można dostosować kompilacji za pośrednictwem programu Visual Studio, pozostawiając pliki projektu CMake nietknięte, tak aby inni w zespole mogą korzystać z nich za pomocą narzędzi, których używają.

## <a name="cmake-general-settings"></a>CMake Ustawienia ogólne

Następujące ustawienia są dostępne w nagłówku **Ogólne:**

### <a name="configuration-name"></a>Nazwa konfiguracji

Odpowiada ustawieniu **nazwy.** Ta nazwa pojawia się na rozwijaniu konfiguracji języka C++. Za pomocą `${name}` makra można redagować inne wartości właściwości, takie jak ścieżki.

### <a name="configuration-type"></a>Typ konfiguracji

Odpowiada ustawieniu **configurationType.** Definiuje typ konfiguracji kompilacji dla wybranego generatora. Obecnie obsługiwane wartości to "Debug", "MinSizeRel", "Release" i "RelWithDebInfo". Mapuje do [CMAKE_BUILD_TYPE.](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)

### <a name="toolset"></a>Zestaw narzędzi

Odpowiada **dziedziczonestawienie środowiska.** Definiuje środowisko kompilatora, który jest używany do tworzenia wybranej konfiguracji. Obsługiwane wartości zależą od typu konfiguracji. Aby utworzyć środowisko niestandardowe, wybierz łącze **Edytuj JSON** w prawym górnym rogu edytora Ustawienia i edytuj plik *CMakeSettings.json* bezpośrednio.

### <a name="cmake-toolchain-file"></a>Plik CMake toolchain

Ścieżka do [pliku CMake toolchain](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Ta ścieżka jest przekazywana do CMake \<jako "-DCMAKE_TOOLCHAIN_FILE =>". Pliki o pęku narzędzi określają lokalizacje kompilatorów i narzędzi o pęku narzędzi oraz inne informacje związane z platformą docelową i kompilatorem. Domyślnie program Visual Studio używa [pliku o pasku narzędzi vcpkg,](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) jeśli to ustawienie jest nieokreślone.

### <a name="build-root"></a>Tworzenie katalogu głównego

Odpowiada **buildRoot**. Mapy do [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)i określa, gdzie utworzyć pamięć podręczną CMake. Określony folder jest tworzony, jeśli nie istnieje.

## <a name="command-arguments"></a>Argumenty polecenia

Następujące ustawienia są dostępne w nagłówku **Argumenty polecenia:**

### <a name="cmake-command-arguments"></a>Argumenty polecenia CMake

Odpowiada **cmakeCommandArgs**. Określa wszelkie dodatkowe [opcje wiersza polecenia](https://cmake.org/cmake/help/latest/manual/cmake.1.html) przekazywane do programu CMake.exe.

### <a name="build-command-arguments"></a>Tworzenie argumentów polecenia

Odpowiada **buildCommandArgs**. Określa dodatkowe przełączniki, które mają być przerzucene do bazowego systemu kompilacji. Na przykład `-v` przekazywanie podczas korzystania z generatora Ninja zmusza Ninja do wyprowadzania linii poleceń.

### <a name="ctest-command-arguments"></a>CTest argumenty polecenia

Odpowiada **ctestCommandArgs**. Określa dodatkowe [opcje wiersza polecenia,](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) które mają być przedyszone do CTest podczas uruchamiania testów.

## <a name="general-settings-for-remote-builds"></a>Ustawienia ogólne dla kompilacji zdalnych

W przypadku konfiguracji, takich jak Linux korzystające z kompilacji zdalnych, dostępne są również następujące ustawienia:

### <a name="rsync-command-arguments"></a>argumenty polecenia rsync

Dodatkowe opcje wiersza polecenia przekazywane do [rsync](https://download.samba.org/pub/rsync/rsync.html), szybkie i wszechstronne narzędzie do kopiowania plików.

## <a name="cmake-variables-and-cache"></a>CZamić zmienne i pamięć podręczną

Te ustawienia umożliwiają ustawienie zmiennych CMake i zapisanie ich w *CMakeSettings.json*. Są one przekazywane do CMake w czasie kompilacji i zastąpić niezależnie od wartości są w pliku *CMakeLists.txt.* Tej sekcji można użyć w taki sam sposób, w jaki można użyć CMakeGUI, aby wyświetlić listę wszystkich zmiennych CMake dostępnych do edycji. Kliknij przycisk **Zapisz i wygeneruj pamięć podręczną,** aby wyświetlić listę wszystkich zmiennych CMake dostępnych do edycji, w tym zmiennych zaawansowanych (według CMakeGUI). Listę można filtrować według nazwy zmiennej.

Odpowiada **zmiennym**. Zawiera parę nazwa-wartość zmiennych CMake przekazanych jako wartość * _-D do_=* CMake. **-D** Jeśli instrukcje kompilacji projektu CMake określić dodanie wszelkich zmiennych bezpośrednio do pliku pamięci podręcznej CMake, zaleca się dodać je tutaj zamiast.

## <a name="advanced-settings"></a>Ustawienia zaawansowane

### <a name="cmake-generator"></a>Generator CMake

Odpowiada **generatorowi**. Mapuje do przełącznika CMake **-G** i określa [generator CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) do użycia. Ta właściwość może być również `${generator}`używana jako makro, podczas tworzenia innych wartości właściwości. Visual Studio obsługuje obecnie następujące generatory CMake:

- "Ninja"
- "Unix Makefiles"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Ponieważ Ninja jest przeznaczony do szybkiego budowania prędkości zamiast elastyczności i funkcji, jest ustawiony jako domyślny. Jednak niektóre projekty CMake mogą nie być w stanie poprawnie zbudować przy użyciu Ninja. W takim przypadku można poinstruować CMake do generowania projektu programu Visual Studio zamiast tego.

### <a name="intellisense-mode"></a>Tryb IntelliSense

Tryb IntelliSense używany przez silnik IntelliSense. Jeśli nie zostanie wybrany żaden tryb, program Visual Studio będzie dziedziczyć z określonego zestawu narzędzi.  

### <a name="install-directory"></a>Instalowanie katalogu

Katalog, w którym CMake instaluje obiekty docelowe. Mapy do [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>CMake plik wykonywalny

Pełna ścieżka do pliku wykonywalnego programu CMake, w tym nazwa pliku i rozszerzenie. Umożliwia użycie niestandardowej wersji CMake z programem Visual Studio. W przypadku kompilacji zdalnych określ lokalizację CMake na komputerze zdalnym.

W przypadku konfiguracji, takich jak Linux korzystające z kompilacji zdalnych, dostępne są również następujące ustawienia:

### <a name="remote-cmakeliststxt-root"></a>Zdalny katalog główny CMakeLists.txt

Katalog na komputerze zdalnym zawierający główny plik *CMakeLists.txt.*

### <a name="remote-install-root"></a>Katalog główny instalacji zdalnej

Katalog na komputerze zdalnym, w którym CMake instaluje obiekty docelowe. Mapy do [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Źródła kopii zdalnych

Określa, czy pliki źródłowe mają być kopiowane na komputerze zdalnym, i umożliwia określenie, czy mają być używane rsync czy sftp.

## <a name="directly-edit-cmakesettingsjson"></a>Bezpośrednio edytuj CMakeSettings.json

Można również bezpośrednio edytować *CMakeSettings.json,* aby utworzyć konfiguracje niestandardowe. **Edytor ustawień** ma w prawym górnym rogu przycisk **Edytuj JSON,** który otwiera plik do edycji.

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

JSON IntelliSense pomaga edytować plik *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Edytor JSON informuje również o wybraniu niezgodnych ustawień.

Aby uzyskać więcej informacji na temat każdej z właściwości w pliku, zobacz [CMakeSettings.json schema reference](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 zawiera kilka konfiguracji CMake, które definiują sposób CMake.exe jest wywoływany do tworzenia pamięci podręcznej CMake dla danego projektu. Aby dodać nową konfigurację, kliknij z listy rozwijanej konfiguracji na pasku narzędzi i wybierz pozycję **Zarządzaj konfiguracjami:**

   ![CMoke zarządzać konfiguracjami](media/cmake-manage-configurations.png)

Można wybrać z listy wstępnie zdefiniowanych konfiguracji:

   ![CZrobienie wstępnie zdefiniowanych konfiguracji](media/cmake-configurations.png)

Przy pierwszym wybraniu konfiguracji program Visual Studio tworzy plik *CMakeSettings.json* w folderze głównym projektu. Ten plik jest używany do ponownego tworzenia pliku pamięci podręcznej CMake, na przykład po **operacji Clean.**

Aby dodać dodatkową konfigurację, kliknij prawym przyciskiem myszy *pozycję CMakeSettings.json* i wybierz polecenie **Dodaj konfigurację**.

   ![Konfiguracja CMake Add](media/cmake-add-configuration.png "CMake Dodaj konfigurację")

Można również edytować plik za pomocą **Edytora ustawień CMake**. Kliknij prawym przyciskiem myszy *CMakeSettings.json* w **Eksploratorze rozwiązań** i wybierz polecenie **Edytuj ustawienia CMake**. Możesz też wybrać **opcję Zarządzaj konfiguracjami** z listy rozwijanej konfiguracji w górnej części okna edytora.

Można również bezpośrednio edytować *CMakeSettings.json,* aby utworzyć konfiguracje niestandardowe. W poniższym przykładzie przedstawiono przykładową konfigurację, której można użyć jako punktu wyjścia:

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

JSON IntelliSense pomaga edytować plik *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Aby uzyskać więcej informacji na temat każdej z właściwości w pliku, zobacz [CMakeSettings.json schema reference](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[CMake projekty w programie Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurowanie projektu CMake systemu Linux](../linux/cmake-linux-project.md)<br/>
[Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurowanie sesji debugowania narzędzia CMake](configure-cmake-debugging-sessions.md)<br/>
[Wdrażanie, uruchamianie i debugowanie projektu systemu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CZrobe wstępnie zdefiniowane odwołanie do konfiguracji](cmake-predefined-configuration-reference.md)
