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
ms.openlocfilehash: b2c5c3f7001a98572129baaf3ee35bb02b6458fd
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041214"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++

W tym przewodniku pokazano, jak wykorzystać program MSBuild do tworzenia projektu Visual C++ w wierszu polecenia. Dowiesz się tworzenie pliki źródłowe C++ i pliku XML na podstawie projektu dla aplikacji konsoli języka Visual C++. Po utworzeniu projektu, dowiesz się, jak dostosować procesu kompilacji.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie C++ pliki źródłowe dla projektu.

- Tworzenie pliku projektu XML MSBuild.

- Przy użyciu programu MSBuild, aby skompilować projekt.

- Aby dostosować projekt za pomocą programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

Potrzebne w tym przewodniku:

- Kopię programu Visual Studio z **tworzenia klasycznych aplikacji w języku C++** obciążenia zainstalowane.

- Ogólny opis systemu MSBuild.

> [!NOTE]
> Nie należy używać tej metody, jeśli zamierzasz później edytować plik projektu za pomocą środowiska IDE programu Visual Studio. Jeśli ręcznie utworzyć plik .vcxproj, środowiska IDE programu Visual Studio może nie można edytować lub obciążenia, zwłaszcza, jeśli projekt używa symbole wieloznaczne w elementach projektu.

> [!NOTE]
> Większość instrukcji niskiego poziomu kompilacji są zawarte w **.targets** i **.props** pliki, które są zdefiniowane w katalogu VCTargets przechowywanych we właściwości `$(VCTargetsPath)`. Domyślna ścieżka dla tych plików w Visual Studio 2017 Enterprise Edition to C:\\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\Enterprise\\Common7\\IDE\\ VC\\VCTargets\\.

## <a name="creating-the-c-source-files"></a>Tworzenie plików źródłowych C++

W tym przewodniku utworzy projekt, który zawiera plik źródłowy i plik nagłówka. Main.cpp plik źródłowy zawiera główną funkcją aplikacji konsoli. Main.h pliku nagłówka zawiera kod, aby uwzględnić plik nagłówka iostream. Te pliki C++ można utworzyć za pomocą programu Visual Studio lub tekst edytora, takiego jak Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Aby utworzyć pliki źródłowe C++ dla projektu

1. Utwórz katalog projektu.

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

## <a name="creating-the-xml-msbuild-project-file"></a>Tworzenie pliku projektu MSBuild XML

Plik projektu programu MSBuild jest plik XML, który zawiera element główny projektu (\<projektu >). W poniższych przykładowy projekt \<projektu > element zawiera siedmiu elementów podrzędnych:

- Element trzy znaczniki grupy (\<ItemGroup >) określające konfiguracji projektu i platformy, nazwa pliku źródłowego i nazwa pliku nagłówka.

- Trzy importowanie znaczników (\<zaimportować >) które określają lokalizację ustawienia programu Microsoft Visual C++.

- Tag grupy właściwości (\<PropertyGroup >), który określa ustawienia projektu.

### <a name="to-create-the-msbuild-project-file"></a>Aby utworzyć plik projektu programu MSBuild

1. Użyj edytora tekstów, aby utworzyć plik projektu o nazwie `myproject.vcxproj`, a następnie dodaj poniższe głównego \<projektu > elementu. Wstaw elementy w poniższych krokach procedury między głównego \<projektu > tagów:

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Dodaj następujące dwa \<ProjectConfiguration > elementy podrzędne w \<ItemGroup > elementu. Element podrzędny określa debug i release konfiguracje dla 32-bitowym systemie operacyjnym Windows:

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

3. Dodaj następujące \<Import / > element, który określa ścieżkę C++ domyślne ustawienia dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. Dodaj następujący element grupy właściwości (\<PropertyGroup >), który określa dwie właściwości projektu:

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. Dodaj następujące \<Import / > element, który określa ścieżkę bieżące ustawienia C++ dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. Dodaj następujące \<ClCompile > elementu podrzędnego w \<ItemGroup > elementu. Element podrzędny określa nazwę pliku źródłowego C/C++ do kompilacji:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > jest *kompilacji docelowej* i jest zdefiniowany w **VCTargets** katalogu.

7. Dodaj następujące \<ClInclude > elementu podrzędnego w \<ItemGroup > elementu. Element podrzędny określa nazwę pliku nagłówka dla pliku źródłowego C/C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. Dodaj następujące \<Import > element, który określa ścieżkę pliku, który definiuje element docelowy dla tego projektu:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Zakończenie pliku projektu

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

## <a name="using-msbuild-to-build-your-project"></a>Korzystanie z MSBuild do tworzenia projektu

Wpisz następujące polecenie w wierszu polecenia, aby skompilować aplikację konsoli:

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild tworzy katalog dla plików wyjściowych, a następnie kompiluje i łączy z projektem, aby wygenerować Myproject.exe program. Po zakończeniu kompilacji, użyj następującego polecenia, aby uruchomić aplikację:

`myproject`

Aplikacja powinien być wyświetlany "tekst Hello, z MSBuild!" w oknie konsoli.

## <a name="customizing-your-project"></a>Dostosowywanie projektu

MSBuild umożliwia wykonanie kompilacji wstępnie zdefiniowanych celów, Zastosuj właściwości zdefiniowane przez użytkownika i użyj narzędzi niestandardowych zdarzeń i kroki procesu kompilacji. W tej części przedstawiono następujące zadania:

- Przy użyciu programu MSBuild z obiektami docelowymi kompilacji.

- Używanie programu MSBuild z właściwościami kompilacji.

- Kompilator 64-bitowy i narzędzia przy użyciu programu MSBuild.

- Przy użyciu programu MSBuild z różnych procesami.

- Dodawanie dostosowań MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Przy użyciu programu MSBuild z obiektami docelowymi kompilacji

A *kompilacji docelowej* to nazwany zestaw wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika poleceń, które mogą być wykonywane podczas kompilacji. Użyj opcji wiersza polecenia docelowego (**/t**) do określania docelowych kompilacji. W przypadku liczby `myproject` przykładowy projekt, wstępnie zdefiniowane **czystą** docelowy usuwa wszystkie pliki w folderze debugowania i tworzy nowy plik dziennika.

W wierszu polecenia wpisz następujące polecenie, aby wyczyścić `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Przy użyciu programu MSBuild z właściwości kompilacji

Opcja wiersza polecenia właściwości (**/p**) umożliwia zastąpienie właściwości w pliku projektu kompilacji. W `myproject` Przykładowa konfiguracja kompilacji projektu, wersji lub debug jest określona przez `Configuration` właściwości. I systemu operacyjnego, który jest przeznaczony do uruchamiania zbudowanych aplikacji jest określona przez `Platform` właściwości.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilacji debugowania `myproject` aplikacji, która jest przeznaczony do uruchamiania na 32-bitowego systemu Windows.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Przyjęto założenie, że `myproject` przykładowy projekt również definiuje konfigurację dla 64-bitowego systemu Windows i innego konfiguracji dla niestandardowego systemu operacyjnego o nazwie `myplatform`.

W wierszu polecenia wpisz następujące polecenie, aby utworzyć wersję kompilacji, która działa w 64-bitowym systemie Windows.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

W wierszu polecenia wpisz następujące polecenie, aby tworzenie kompilacji wydania dla `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Przy użyciu programu MSBuild z narzędzi i kompilatora 64-bitowych

Po zainstalowaniu programu Visual C++ na 64-bitowym systemie Windows, domyślnie x64 64-bitowych natywne i Międzyplatformowe narzędzia są zainstalowane. Można skonfigurować program MSBuild na potrzeby tworzenia aplikacji przez ustawienie narzędzi i kompilatora 64-bitowych `PreferredToolArchitecture` właściwości. Ta właściwość nie ma wpływu na właściwości konfiguracji lub platformy projektu. Domyślnie używany jest 32-bitowa wersja narzędzi. Aby określić 64-bitowej wersji narzędzi i kompilatora, Dodaj następujący element grupy właściwości do pliku projektu Myproject.vcxproj po `Microsoft.Cpp.default.props` \<Import / > elementu:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

W wierszu polecenia wpisz następujące polecenie, aby skompilować aplikację za pomocą narzędzi 64-bitowych.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Przy użyciu programu MSBuild z innego zestawu narzędzi

Jeśli masz procesami i bibliotek dla innych wersji programu Visual C++ zainstalowany program MSBuild mogą tworzyć aplikacje z bieżącą wersją programu Visual C++ lub innych zainstalowanych wersji. Na przykład, jeśli zainstalowano [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], aby określić zestaw narzędzi Visual C++ 11.0 dla systemu Windows XP, Dodaj następujący element grupy właściwości do pliku projektu Myproject.vcxproj po Microsoft.Cpp.props `<Import />` elementu:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Aby ponownie skompiluj projekt z zestawu narzędzi programu Visual C++ 11.0 systemu Windows XP, wpisz jedno z następujących poleceń:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Dodawanie dostosowań MSBuild

MSBuild udostępnia różne sposoby dostosowania procesu kompilacji. W następujących tematach opisano sposób dodawania do projektu MSBuild niestandardowe kroki procesu kompilacji, narzędzia i zdarzenia:

- [Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)
