---
title: Elementy programu MSBuild wewnętrzne dla języka C++ projektów w programie Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 6c8e891f6bf6ed6b3bb3d1c84dbc13b64ab7b868
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021907"
---
# <a name="msbuild-internals-for-c-projects"></a>Wewnętrzne MSBuild dla projektów języka C++

Podczas ustawiania właściwości projektu w środowisku IDE, a następnie zapisujesz projekt, Visual Studio zapisuje ustawienia projektu do pliku projektu. Plik projektu zawiera ustawienia, które są unikatowe dla projektu, ale nie zawiera wszystkich ustawień, które są wymagane do kompilowania projektu. Plik projektu zawiera `Import` elementy, które zawierają sieć dodatkowych *plików obsługi.* Pliki obsługi zawierają pozostałe właściwości, cele i ustawienia, które są wymagane do skompilowania projektu.

Większość obiektów docelowych i właściwości w plikach pomocy technicznej istnieje wyłącznie w celu implementowania systemu kompilacji. W poniższej sekcji omówiono niektóre użyteczne cele i właściwości, które można określić w wierszu polecenia programu MSBuild. Aby dowiedzieć się więcej obiektów docelowych i właściwości, Eksploruj pliki w katalogach plików pomocy technicznej.

## <a name="support-file-directories"></a>Obsługa katalogów plików

Domyślnie podstawowe pliki obsługi programu Visual Studio znajdują się w następujących katalogach. Katalogi w ramach programu Microsoft Visual Studio są używane przez program Visual Studio 2017 i nowsze wersje, katalogi w ramach programu MSBuild są używane przez program Visual Studio 2015 i wcześniejszych wersji.

|Katalog|Opis|
|---------------|-----------------|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*version*\ |Zawiera podstawowe pliki docelowe (.targets) i pliki właściwości (.props), które są używane przez elementy docelowe. Domyślnie makro $(VCTargetsPath) odwołuje się do tego katalogu.|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platform\\*platformy*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\ |Zawiera pliki docelowych i właściwości specyficzne dla platformy, które zastępują cele i właściwości w katalogu nadrzędnym. Ten katalog zawiera również biblioteki DLL, który określa zadania, które są używane przez cele w tym katalogu.<br /><br /> *Platformy* symbol zastępczy reprezentuje ARM, Win32 lub x64 podkatalogu.|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platform\\*platformy*\PlatformToolsets\\*zestawu narzędzi*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platform*\PlatformToolsets\\*toolset*\ |Zawiera katalogi, które umożliwiają kompilacji wygenerowanie aplikacji w języku C++ przy użyciu określonego *narzędzi*.<br /><br /> *Roku* i *wersji* symbole zastępcze są używane przez program Visual Studio 2017 i nowsze wersje. *Wersji* symbol zastępczy jest V110 dla programu Visual Studio 2012, V120 dla programu Visual Studio 2013 lub Visual Studio 2015 w wersji 140. *Platformy* symbol zastępczy reprezentuje ARM, Win32 lub x64 podkatalogu. *Narzędzi* symbol zastępczy reprezentuje podkatalog zestawu narzędzi, na przykład w wersji 140 do tworzenia aplikacji Windows przy użyciu zestawu narzędzi programu Visual Studio 2015 v120_xp tworzenie dla Windows XP przy użyciu zestawu narzędzi Visual Studio 2013 lub v110_wp80 do Twórz aplikacje Windows Phone 8.0 przy użyciu zestawu narzędzi programu Visual Studio 2012.<br /><br />Nie zawiera ścieżkę, która zawiera katalogi, które umożliwiają kompilacji wygenerowanie aplikacji Visual Studio 2008 lub Visual Studio 2010 *wersji*i *platformy* symbolu zastępczego reprezentuje Itanium, Win32 lub x64 podkatalogu. *Narzędzi* symbol zastępczy reprezentuje podkatalog zestawu narzędzi v90 lub v100.|

## <a name="support-files"></a>Pliki pomocy technicznej

Katalogi plików obsługi zawierają pliki z tymi rozszerzeniami:

|Wewnętrzny|Opis|
|---------------|-----------------|
|.TARGETS|Zawiera `Target` elementów XML, które określają zadania, które są wykonywane przez element docelowy. Może również zawierać `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`i zdefiniowane przez użytkownika `Item` elementy, które są używane do przypisywania plików i opcji wiersza polecenia do parametrów zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Target — Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Zawiera `Property Group` i zdefiniowane przez użytkownika `Property` elementów XML, które określają ustawienia plików i parametrów, które są używane podczas kompilacji.<br /><br /> Może również zawierać `ItemDefinitionGroup` i zdefiniowane przez użytkownika `Item` elementów XML, które określają dodatkowe ustawienia. Elementy zdefiniowane w grupie definicji elementów przypominają właściwości, ale nie są dostępne z poziomu wiersza polecenia. Pliki projektu w usłudze Visual Studio najczęściej używać elementów zamiast właściwości do reprezentowania ustawień.<br /><br /> Aby uzyskać więcej informacji, zobacz [itemgroup — Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[ItemDefinitionGroup — Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), i [elementu — Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Zawiera elementy XML, które deklaruje i inicjuje elementy interfejsu użytkownika IDE, takie jak arkusze właściwości i strony właściwości i tekstu pola i formanty pola listy.<br /><br /> Pliki .xml bezpośrednio obsługują IDE, nie MSBuild. Jednak wartości właściwości środowiska IDE są przypisywane do właściwości i elementów kompilacji.<br /><br /> Większość plików .XML znajduje się w podkatalogu specyficzne dla ustawień regionalnych. Na przykład pliki dla regionu Angielski-Stany Zjednoczone znajdują się w $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Cele i właściwości użytkownika

Za pomocą najbardziej efektywne programu MSBuild w wierszu polecenia, warto wiedzieć, które właściwości i elementy docelowe są przydatne i istotne. Większość właściwości i obiektów docelowych ułatwia implementację systemu kompilacji programu Visual Studio, a w związku z tym nie mają znaczenia dla użytkownika. W tej sekcji opisano niektóre zorientowane ukierunkowanych na użytkownika właściwości i obiektów docelowych.

### <a name="platformtoolset-property"></a>Właściwość PlatformToolset

`PlatformToolset` Właściwość określa, który zestaw narzędzi MSVC jest używany w kompilacji. Domyślnie używany jest bieżący zestaw narzędzi. Gdy ta właściwość jest ustawiona, wartość właściwości jest połączona z ciągami tekstowymi ścieżkę katalogu, zawierającego pliki właściwości i docelowych, które są wymagane do utworzenia projektu dla konkretnej platformy. Tworzenie za pomocą tej wersji zestawu narzędzi platformy można zainstalować zestawu narzędzi platformy.

Na przykład ustawić `PlatformToolset` właściwość `v140` używać bibliotek i narzędzi Visual Studio 2015 do budowania aplikacji:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Właściwość PreferredToolArchitecture

`PreferredToolArchitecture` Właściwość określa, czy 32-bitową lub 64-bitowy kompilator i narzędzia są używane w kompilacji. Właściwość ta nie wpływa na konfigurację ani architekturę platformy wyjściowej. Domyślnie MSBuild używa x86 wersję kompilatora i narzędzi, jeśli ta właściwość nie jest ustawiona.

Na przykład ustawić `PreferredToolArchitecture` właściwość `x64` używać 64-bitowego kompilatora i narzędzi do budowania aplikacji:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Właściwość UseEnv

Domyślnie ustawienia specyficzne dla platformy dla bieżącego projektu zastępują zmienne środowiskowe PATH, INCLUDE, LIB, LIBPATH, Konfiguracja i PLATFORMA. Ustaw `UseEnv` właściwości **true** celu zagwarantowania, że zmienne środowiskowe nie są zastępowane.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Obiekty docelowe

Istnieją setki obiektów docelowych w plikach pomocy technicznej programu Visual Studio. Jednak większość to cele systemowe, które użytkownik może ignorować. Większość obiektów docelowych systemów jest poprzedzonych znakiem podkreślenia (_) lub mają nazwę, która zaczyna się od "PrepareFor", "Compute", "Before", "After", "Pre" lub "Post".

W poniższej tabeli wymieniono kilka przydatne celów ukierunkowanych na użytkownika.

|Cel|Opis|
|------------|-----------------|
|BscMake|Uruchamia narzędzie przeglądać informacje o konserwacji narzędzie Microsoft bscmake.exe.|
|Kompilacja|Kompiluje projekt.<br /><br /> Jest to domyślny cel dla projektu.|
|ClCompile|Uruchamia narzędzie kompilatora MSVC cl.exe.|
|czyszczenie|Usuwa tymczasowe i pośrednie pliki kompilacji.|
|lib|Uruchamia narzędzie Microsoft 32-bitowy Library Manager, lib.exe.|
|Łącze|Uruchamia narzędzie konsolidatora MSVC link.exe.|
|ManifestResourceCompile|Wyodrębnia listę zasobów z manifestu, a następnie uruchamia narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe.|
|Midl|Uruchamia narzędzie kompilatora języka definicji interfejsu Microsoft (MIDL) midl.exe.|
|Ponowna kompilacja|Czyści, a następnie kompiluje projekt.|
|ResourceCompile|Uruchamia narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe.|
|XdcMake|Uruchamia narzędzie dokumentacji XML xdcmake.exe.|
|Xsd|Uruchamia narzędzie definicji schematu XML xsd.exe. *Zobacz uwagi poniżej.*|

> [!NOTE]
> Projekt w programie Visual Studio 2017, obsługa C++ **xsd** plików jest przestarzała. Można nadal używać **Microsoft.VisualC.CppCodeProvider** , dodając **CppCodeProvider.dll** ręcznie do pamięci podręcznej GAC.

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania MSBuild](/visualstudio/msbuild/msbuild-task-reference)<br/>
[BscMake — Zadanie](/visualstudio/msbuild/bscmake-task)<br/>
[CL — Zadanie](/visualstudio/msbuild/cl-task)<br/>
[CPPClean — Zadanie](/visualstudio/msbuild/cppclean-task)<br/>
[LIB — Zadanie](/visualstudio/msbuild/lib-task)<br/>
[Połącz — Zadanie](/visualstudio/msbuild/link-task)<br/>
[MIDL — Zadanie](/visualstudio/msbuild/midl-task)<br/>
[MT — Zadanie](/visualstudio/msbuild/mt-task)<br/>
[RC — Zadanie](/visualstudio/msbuild/rc-task)<br/>
[SetEnv — Zadanie](/visualstudio/msbuild/setenv-task)<br/>
[VCMessage — Zadanie](/visualstudio/msbuild/vcmessage-task)<br/>
[XDCMake — Zadanie](/visualstudio/msbuild/xdcmake-task)<br/>
