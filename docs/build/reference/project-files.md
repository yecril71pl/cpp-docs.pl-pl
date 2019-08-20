---
title: Przykładowy plik projektu
ms.date: 08/19/2019
helpviewer_keywords:
- .vcxproj files
- C++ projects, project file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
ms.openlocfilehash: 0eb87c3f3ba8bd60f0944ad673d22f9b84e070a5
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630770"
---
# <a name="project-files"></a>Pliki projektu

Plik C++ projektu w programie Visual Studio jest plikiem opartym na języku XML, który ma rozszerzenie nazwy pliku. vcxproj i zawiera informacje wymagane do skompilowania C++ projektu. Należy zauważyć, że plik projektu importuje różne pliki projektu, które mają rozszerzenie ". props" lub ". targets". Te pliki zawierają dodatkowe informacje o kompilacji i mogą odwoływać się do innych plików ". props" lub ". targets". Makra w ścieżce pliku (na przykład `$(VCTargetsPath)`) są zależne od instalacji programu Visual Studio. Aby uzyskać więcej informacji na temat tych makr i plików ". props" i ". targets", zobacz [stronę właściwości katalogów VC + +](vcpp-directories-property-page.md), [Ustaw C++ kompilator i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md) i [typowe makra dla poleceń i właściwości kompilacji](common-macros-for-build-commands-and-properties.md).

## <a name="example"></a>Przykład

::: moniker range=">=vs-2019"

Następujący przykładowy plik. vcxproj został utworzony przez wybranie **Kreatora pulpitu systemu Windows** w oknie dialogowym **Nowy projekt** . Aby przetworzyć plik projektu, użyj narzędzia MSBuild. exe w wierszu polecenia lub polecenia **Build** w środowisku IDE. (Nie można przetworzyć tego przykładu, ponieważ nie podano wymaganych plików źródłowych i nagłówków). Aby uzyskać więcej informacji na temat elementów XML w pliku projektu, zobacz [Dokumentacja schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end

::: moniker range="<=vs-2017"

Następujący przykładowy plik. vcxproj został utworzony przez określenie **aplikacji konsolowej Win32** w oknie dialogowym **Nowy projekt** . Aby przetworzyć plik projektu, użyj narzędzia MSBuild. exe w wierszu polecenia lub polecenia **Build** w środowisku IDE. (Nie można przetworzyć tego przykładu, ponieważ nie podano wymaganych plików źródłowych i nagłówków). Aby uzyskać więcej informacji na temat elementów XML w pliku projektu, zobacz [Dokumentacja schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end


>[!NOTE]
> W przypadku projektów w programie Visual Studio 2017 i starszych `pch.h` wersjach `stdafx.h` Zmień `pch.cpp` na `stdafx.cpp`i na.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup Label="ProjectConfigurations">
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <PropertyGroup Label="Globals">
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>
    <Keyword>Win32Proj</Keyword>
    <RootNamespace>SomeProjName</RootNamespace>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <WholeProgramOptimization>true</WholeProgramOptimization>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings">
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <LinkIncremental>true</LinkIncremental>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <LinkIncremental>false</LinkIncremental>
  </PropertyGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <ClCompile>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <WarningLevel>Level3</WarningLevel>
      <MinimalRebuild>true</MinimalRebuild>
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>
      <Optimization>Disabled</Optimization>
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
    </Link>
  </ItemDefinitionGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <ClCompile>
      <WarningLevel>Level3</WarningLevel>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>
      <Optimization>MaxSpeed</Optimization>
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
      <FunctionLevelLinking>true</FunctionLevelLinking>
      <IntrinsicFunctions>true</IntrinsicFunctions>
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
      <EnableCOMDATFolding>true</EnableCOMDATFolding>
      <OptimizeReferences>true</OptimizeReferences>
    </Link>
  </ItemDefinitionGroup>
  <ItemGroup>
    <None Include="ReadMe.txt" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="pch.h" />
    <ClInclude Include="targetver.h" />
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="SomeProjName.cpp" />
    <ClCompile Include="pch.cpp">
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>
    </ClCompile>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets">
  </ImportGroup>
</Project>
```

## <a name="see-also"></a>Zobacz także

[Projekty programu Visual Studio — C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)
