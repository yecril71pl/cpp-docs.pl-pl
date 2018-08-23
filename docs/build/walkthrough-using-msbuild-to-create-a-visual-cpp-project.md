---
title: 'Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.walkthrough.createproject
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8bb957f0ab1dd2ea7d05151257aee0e15561e8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609702"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++

W tym przewodniku pokazano, jak używać programu MSBuild do tworzenia projektu Visual C++ w wierszu polecenia. Dowiesz się jak tworzyć pliki źródłowe C++ i pliku projektu opartego na języku XML dla aplikację konsolową w języku Visual C++. Po utworzeniu projektu dowiesz się, jak dostosować proces kompilacji.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie plików źródłowych C++ dla Twojego projektu.

- Tworzenie pliku projektu XML MSBuild.

- Korzystanie z programu MSBuild do kompilowania projektu.

- Korzystanie z programu MSBuild, aby dostosować projekt.

## <a name="prerequisites"></a>Wymagania wstępne

Potrzebne są następujące czynności w celu przeprowadzenia tego instruktażu:

- Kopię programu Visual Studio z **programowanie aplikacji klasycznych w języku C++** zainstalowanym obciążeniem.

- Ogólna wiedza o systemu MSBuild.

> [!NOTE]
> Nie należy używać tej metody, jeśli zamierzasz później edytować plik projektu za pomocą środowiska IDE programu Visual Studio. Jeśli ręcznie utworzyć plik .vcxproj, środowiska IDE programu Visual Studio nie można edytować lub obciążenia, zwłaszcza, jeśli projekt używa symboli wieloznacznych w elementach projektu.

> [!NOTE]
> Większość instrukcji niskiego poziomu kompilacji są zawarte w **.targets** i **.props** pliki, które są zdefiniowane w katalogu VCTargets przechowywana we właściwości `$(VCTargetsPath)`. Domyślna ścieżka do tych plików w Visual Studio 2017 Enterprise Edition to C:\\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\Enterprise\\Common7\\IDE\\ VC\\VCTargets\\.

## <a name="creating-the-c-source-files"></a>Tworzenie plików źródłowych języka C++

W tym instruktażu utworzysz projekt, który zawiera plik źródłowy i plik nagłówkowy. Plik źródłowy main.cpp zawiera główną funkcję dla aplikacji konsoli. Main.h pliku nagłówka zawiera kod, aby uwzględnić plik nagłówka iostream. Te pliki języka C++ można utworzyć za pomocą programu Visual Studio lub wysłanie wiadomości SMS edytora, takiego jak Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Aby utworzyć pliki źródłowe C++ dla Twojego projektu

1. Utwórz katalog dla projektu.

2. Utwórz plik o nazwie main.cpp i Dodaj następujący kod do tego pliku:

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

3. Utwórz plik o nazwie main.h i Dodaj następujący kod do tego pliku:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Tworzenie pliku XML projektu MSBuild

Plik projektu programu MSBuild jest plikiem XML, który zawiera element główny projektu (\<Projekt >). W następującym przykładowym projekcie \<Projekt > element zawiera siedem elementów podrzędnych:

- Element trzy znaczniki grupy (\<ItemGroup >) określające konfigurację projektu i platform, nazwa pliku źródłowego i nazwa pliku nagłówkowego.

- Trzy znaczniki importowania (\<Importuj >) określające położenie ustawień Microsoft Visual C++.

- Tag grupy właściwości (\<PropertyGroup >), który określa ustawienia projektu.

### <a name="to-create-the-msbuild-project-file"></a>Aby utworzyć plik projektu MSBuild

1. Użyj edytora tekstu, aby utworzyć plik projektu, który nosi nazwę `myproject.vcxproj`, a następnie dodaj następujący katalog główny \<Projekt > element. Wstaw elementy w poniższych krokach procedury między głównym \<Projekt > znaczniki:

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Dodaj dwie poniższe \<ProjectConfiguration > elementy podrzędne w \<ItemGroup > element. Element podrzędny określa debugowania i zwalniania konfiguracji dla 32-bitowym systemie operacyjnym Windows:

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

3. Dodaj następujący kod \<importowania / > element, który określa ścieżkę ustawień domyślnych C++ dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. Dodaj poniższy element grupy właściwości (\<PropertyGroup >), który określa dwie właściwości projektu:

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. Dodaj następujący kod \<importowania / > element, który określa ścieżkę aktualnych ustawień C++ dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. Dodaj następujący kod \<ClCompile > element podrzędny w \<ItemGroup > element. Element podrzędny określa nazwę pliku źródłowego języka C/C++ do skompilowania:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > jest *tworzenia pod kątem* i jest definiowany w **VCTargets** katalogu.

7. Dodaj następujący kod \<ClInclude > element podrzędny w \<ItemGroup > element. Element podrzędny określa nazwę pliku nagłówka dla pliku źródłowego języka C/C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. Dodaj następujący kod \<Import > element, który określa ścieżkę do pliku, który definiuje cel dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Ukończ plik projektu

Poniższy kod przedstawia plik kompletnego projektu, który został utworzony w poprzedniej procedurze.

```xml
<Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v141</PlatformToolset>
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

## <a name="using-msbuild-to-build-your-project"></a>Korzystanie z programu MSBuild do kompilowania projektu

Wpisz następujące polecenie w wierszu polecenia, aby skompilować aplikację konsoli:

`msbuild myproject.vcxproj /p:configuration=debug`

Program MSBuild tworzy katalog dla plików wyjściowych, a następnie kompiluje i łączy projekt, aby generować Myproject.exe program. Po zakończeniu procesu kompilacji Użyj następującego polecenia, aby uruchomić aplikację:

`myproject`

Aplikacja powinna wyświetlić "Hello, z programu MSBuild!" w oknie konsoli.

## <a name="customizing-your-project"></a>Dostosowywanie projektu

Program MSBuild umożliwia wykonywanie wstępnie zdefiniowanych celów kompilacji, stosowanie właściwości zdefiniowany przez użytkownika i używanie niestandardowych narzędzi, zdarzeń oraz kroków kompilacji. W tej sekcji przedstawiono następujące zagadnienia:

- Korzystanie z programu MSBuild z celami kompilacji.

- Korzystanie z programu MSBuild z właściwościami kompilacji.

- Korzystanie z programu MSBuild z 64-bitowym kompilatorem i narzędziami.

- Korzystanie z programu MSBuild z różnymi zestawami narzędzi.

- Dodawanie dostosowań programu MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Korzystanie z programu MSBuild z celami kompilacja

A *tworzenia pod kątem* jest zestawem nazwanym poleceń wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika, które mogą być wykonywane podczas kompilacji. Użyj opcji docelowego wiersza polecenia (**/t**) do określania docelowej kompilacji. W przypadku właściwości `myproject` przykładowym projekcie, wstępnie zdefiniowane **czyste** docelowy usuwa wszystkie pliki w folderze debugowania i tworzy nowy plik dziennika.

W wierszu polecenia wpisz następujące polecenie, aby wyczyścić `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Korzystanie z programu MSBuild z właściwościami kompilacja

Opcja wiersza polecenia właściwości (**/p**) umożliwia zastąpienie właściwości w pliku kompilacji projektu. W `myproject` przykładową konfigurację kompilacji projektu, wydania lub debugowania jest określona przez `Configuration` właściwości. I systemu operacyjnego, który jest przeznaczony do uruchamiania aplikacji jest określona przez `Platform` właściwości.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilację do debugowania `myproject` aplikacji, który jest przeznaczony do uruchamiania na 32-bitowa Windows.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Przyjęto założenie, że `myproject` przykładowy projekt również definiuje konfigurację dla 64-bitowych Windows a inną konfigurację dla niestandardowych systemu operacyjnego o nazwie `myplatform`.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć wersję kompilacji, która działa na Windows 64-bitowych.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilację wydania dla `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Korzystanie z programu MSBuild z 64-bitowym kompilatorem i narzędziami

Po zainstalowaniu programu Visual C++ na Windows 64-bitowych, domyślnie x64 64-bitowych natywna i krzyżowa narzędzia są zainstalowane. Można skonfigurować program MSBuild będzie używać 64-bitowym kompilatorem i narzędziami do tworzenia aplikacji przez ustawienie `PreferredToolArchitecture` właściwości. Właściwość ta nie wpływa na właściwości konfiguracji lub platformy projektu. Domyślnie używany jest 32-bitowej wersji narzędzia. Aby określić 64-bitową wersję kompilatora i narzędzi, Dodaj następujący element grupy właściwości do pliku projektu Myproject.vcxproj po `Microsoft.Cpp.default.props` \<importowania / > element:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

W wierszu polecenia wpisz następujące polecenie, aby użyć narzędzi 64-bitowych do budowania aplikacji.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Korzystanie z programu MSBuild z innym zestawem narzędzi

Jeśli masz zestawy narzędzi i biblioteki dla innych wersji programu Visual C++, zainstalowane, program MSBuild może kompilować aplikacje w bieżącej wersji Visual C++ lub innych zainstalowanych wersji. Na przykład po zainstalowaniu programu Visual Studio 2012, aby określić zestaw narzędzi Visual C++ 11.0 Windows XP, Dodaj następujący element grupy właściwości do pliku projektu myProject.vcxproj za elementem na po pliku Microsoft.Cpp.props `<Import />` elementu:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Aby odbudować projektu za pomocą narzędzi Visual C++ 11.0 Windows XP, wpisz jedno z następujących poleceń:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Dodawanie dostosowań programu MSBuild

Program MSBuild udostępnia różne sposoby dostosowywania procesu kompilacji. W następujących tematach opisano sposób dodawania niestandardowych kroków kompilacji, narzędzi i zdarzeń do projektu programu MSBuild:

- [Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)
