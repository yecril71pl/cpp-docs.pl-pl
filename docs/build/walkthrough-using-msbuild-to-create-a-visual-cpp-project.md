---
title: 'Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417188"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++

W tym instruktażu pokazano, jak utworzyć projekt Visual Studio C++ przy użyciu programu MSBuild w wierszu polecenia. Dowiesz się, jak utworzyć pliki źródłowe C++ i plik projektu oparty na języku XML dla Visual C++ aplikacji konsolowej. Po skompilowaniu projektu dowiesz się, jak dostosować proces kompilacji.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie plików źródłowych języka C++ dla projektu.

- Tworzenie pliku projektu MSBuild języka XML.

- Kompilowanie projektu przy użyciu programu MSBuild.

- Dostosowywanie projektu przy użyciu programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz wykonać następujące czynności:

- Kopia programu Visual Studio z zainstalowaną funkcją **tworzenia aplikacji klasycznych w języku C++** .

- Ogólna znajomość systemu MSBuild.

> [!NOTE]
> Nie należy używać tej metody, jeśli zamierzasz edytować plik projektu później za pomocą środowiska IDE programu Visual Studio. Jeśli utworzysz plik. vcxproj ręcznie, środowisko IDE programu Visual Studio może nie być w stanie go edytować ani ładować, zwłaszcza jeśli projekt używa symboli wieloznacznych w elementach projektu.

> [!NOTE]
> Większość instrukcji kompilacji niskiego poziomu znajduje się w plikach **targets** i **. props** , które są zdefiniowane w katalogu VCTargets, przechowywane we właściwości `$(VCTargetsPath)`. Domyślna ścieżka tych plików w programie Visual Studio 2019 Enterprise Edition to C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props.

## <a name="creating-the-c-source-files"></a>Tworzenie plików źródłowych języka C++

W tym instruktażu utworzysz projekt, który zawiera plik źródłowy i plik nagłówkowy. Plik źródłowy Main. cpp zawiera główną funkcję aplikacji konsolowej. Plik nagłówkowy Main. h zawiera kod umożliwiający dołączenie pliku nagłówkowego iostream. Te pliki C++ można utworzyć przy użyciu programu Visual Studio lub edytora tekstu, takiego jak Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Aby utworzyć pliki źródłowe języka C++ dla projektu

1. Utwórz katalog dla projektu.

1. Utwórz plik o nazwie Main. cpp i Dodaj następujący kod do tego pliku:

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

1. Utwórz plik o nazwie Main. h i Dodaj następujący kod do tego pliku:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Tworzenie pliku projektu MSBuild XML

Plik projektu MSBuild to plik XML, który zawiera element główny projektu (`<Project>`). W poniższym przykładowym projekcie `<Project>` element zawiera siedem elementów podrzędnych:

- Trzy Tagi grupy elementów (`<ItemGroup>`), które określają konfigurację projektu i platformę, nazwę pliku źródłowego i nazwę pliku nagłówkowego.

- Trzy znaczniki importu (`<Import>`) określające lokalizację Microsoft Visual C++ ustawień.

- Tag grupy właściwości (`<PropertyGroup>`), który określa ustawienia projektu.

### <a name="to-create-the-msbuild-project-file"></a>Aby utworzyć plik projektu MSBuild

1. Użyj edytora tekstów, aby utworzyć plik projektu o nazwie `myproject.vcxproj`, a następnie Dodaj następujący element główny. `<Project>` Wstaw elementy w poniższych krokach procedury między tagami głównymi `<Project>` . (Użyj ToolsVersion = "15.0", jeśli używasz programu Visual Studio 2017 lub ToolsVersion = "16.0", jeśli używasz programu Visual Studio 2019).

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Dodaj następujące dwa `<ProjectConfiguration>` elementy podrzędne w `<ItemGroup>` elemencie. Element podrzędny określa konfiguracje debugowania i wydania dla 32-bitowego systemu operacyjnego Windows:

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

1. Dodaj następujący `<Import>` element określający ścieżkę domyślnych ustawień języka C++ dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Dodaj następujący element grupy właściwości (`<PropertyGroup>`), który określa dwie właściwości projektu. (Użyj najnowsze 141, jeśli używasz programu Visual Studio 2017 lub v142, jeśli używasz programu Visual Studio 2019).

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Dodaj następujący `<Import>` element określający ścieżkę bieżących ustawień języka C++ dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Dodaj następujący `<ClCompile>` element podrzędny w `<ItemGroup>` elemencie. Element podrzędny określa nazwę pliku źródłowego C/C++ do skompilowania:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>`jest *elementem docelowym kompilacji* i jest zdefiniowany w katalogu **VCTargets** .

1. Dodaj następujący `<ClInclude>` element podrzędny w `<ItemGroup>` elemencie. Element podrzędny określa nazwę pliku nagłówkowego dla pliku źródłowego C/C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Dodaj następujący `<Import>` element określający ścieżkę pliku, który definiuje element docelowy dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Ukończ plik projektu

Poniższy kod przedstawia kompletny plik projektu, który został utworzony w poprzedniej procedurze. (Użyj ToolsVersion = "15.0" dla programu Visual Studio 2017).

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v142</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>Kompilowanie projektu przy użyciu programu MSBuild

Wpisz następujące polecenie w wierszu polecenia, aby skompilować aplikację konsolową:

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild tworzy katalog dla plików wyjściowych, a następnie kompiluje i łączy projekt w celu wygenerowania programu Project. exe. Po zakończeniu procesu kompilacji Użyj następującego polecenia, aby uruchomić aplikację z folderu debugowania:

`myproject`

Aplikacja powinna wyświetlać "Hello, z MSBuild!" w oknie konsoli.

## <a name="customizing-your-project"></a>Dostosowywanie projektu

Program MSBuild umożliwia wykonywanie wstępnie zdefiniowanych celów kompilacji, stosowanie właściwości zdefiniowanych przez użytkownika i używanie niestandardowych narzędzi, zdarzeń i kroków kompilacji. W tej sekcji przedstawiono następujące zadania:

- Korzystanie z programu MSBuild z obiektami docelowymi kompilacji.

- Korzystanie z programu MSBuild z właściwościami kompilacji.

- Korzystanie z programu MSBuild z 64-bitowym kompilatorem i narzędziami.

- Korzystanie z programu MSBuild z różnymi zestawami narzędzi.

- Dodawanie dostosowań MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Korzystanie z programu MSBuild z obiektami docelowymi kompilacji

*Element docelowy kompilacji* to nazwany zestaw wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika poleceń, które mogą być wykonywane podczas kompilacji. Aby określić cel kompilacji, użyj docelowej opcji`/t`wiersza polecenia (). W przypadku `myproject` przykładowego projektu wstępnie zdefiniowany **czysty** element docelowy usuwa wszystkie pliki w folderze debugowania i tworzy nowy plik dziennika.

W wierszu polecenia wpisz następujące polecenie, aby oczyścić `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Korzystanie z programu MSBuild z właściwościami kompilacji

Opcja wiersza polecenia właściwości (`/p`) umożliwia przesłonięcie właściwości w pliku kompilacji projektu. W `myproject` przykładzie projekt konfiguracja kompilacji wersji lub debugowania jest określona przez `Configuration` właściwość. A system operacyjny przeznaczony do uruchamiania skompilowanej aplikacji jest określony przez `Platform` właściwość.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilację debugowania `myproject` aplikacji, która jest przeznaczona do uruchamiania w 32-bitowej wersji systemu Windows.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Załóżmy, że `myproject` przykładowy projekt definiuje również konfigurację dla 64-bitowego systemu Windows i inną konfigurację dla niestandardowego systemu operacyjnego o nazwie `myplatform`.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilację wydania działającą w 64-bitowym systemie Windows.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilację wydania dla programu `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Korzystanie z programu MSBuild z 64-bitowym kompilatorem i narzędziami

Jeśli zainstalowano program Visual Studio w systemie 64-bitowym, domyślnie zainstalowane są narzędzia 64-bit x64 Native i Cross. Program MSBuild można skonfigurować tak, aby korzystał z kompilatora 64-bitowego oraz narzędzi do kompilowania aplikacji przez `PreferredToolArchitecture` ustawienie właściwości. Ta właściwość nie ma wpływu na właściwości konfiguracji projektu ani platformy. Domyślnie używana jest 32-bitowa wersja narzędzi. Aby określić 64-bitową wersję kompilatora i narzędzi, Dodaj następujący element grupy właściwości do pliku projektu Project. vcxproj po `Microsoft.Cpp.default.props` \<elemencie import/>:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

W wierszu polecenia wpisz następujące polecenie, aby użyć narzędzi 64-bitowych do kompilowania aplikacji.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Korzystanie z programu MSBuild z innym zestawem narzędzi

Jeśli masz zestawy narzędzi i biblioteki dla innych wersji Visual C++ zainstalowanych, MSBuild może kompilować aplikacje dla bieżącej wersji Visual C++ lub dla innych zainstalowanych wersji. Na przykład jeśli zainstalowano program Visual Studio 2012, aby określić zestaw narzędzi Visual C++ 11,0 dla systemu Windows XP, Dodaj następujący element grupy właściwości do pliku projektu Project. vcxproj po `Microsoft.Cpp.props` \<elemencie import/>:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Aby ponownie skompilować projekt przy użyciu zestawu narzędzi Visual C++ 11,0 systemu Windows XP, wpisz następujące polecenia:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Dodawanie dostosowań MSBuild

Program MSBuild oferuje różne sposoby dostosowywania procesu kompilacji. W poniższych tematach pokazano, jak dodać niestandardowe kroki kompilacji, narzędzia i zdarzenia do projektu MSBuild:

- [Porady: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Porady: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild](how-to-use-build-events-in-msbuild-projects.md)
