---
title: Elementy wewnętrzne programu MSBuild dla projektów C++ w programie Visual Studio
ms.date: 02/26/2020
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: c52434fa4b652d52baea70df705920db4ee68a5f
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610854"
---
# <a name="msbuild-internals-for-c-projects"></a>Funkcje wewnętrzne aparatu MSBuild dla projektów w języku C++

Po ustawieniu właściwości projektu w IDE, a następnie zapisaniu projektu, program Visual Studio zapisuje ustawienia projektu w pliku projektu. Plik projektu zawiera ustawienia, które są unikatowe dla Twojego projektu. Nie zawiera on jednak wszystkich ustawień wymaganych do skompilowania projektu. Plik projektu zawiera `Import` elementy, które zawierają sieć dodatkowych *plików pomocniczych.* Pliki obsługi zawierają pozostałe właściwości, obiekty docelowe i ustawienia wymagane do skompilowania projektu.

Większość elementów docelowych i właściwości w plikach obsługi istnieje wyłącznie do wdrożenia systemu kompilacji. W tym artykule omówiono przydatne elementy docelowe i właściwości, które można określić w wierszu polecenia programu MSBuild. Aby odnaleźć więcej obiektów docelowych i właściwości, Przejrzyj pliki w katalogach plików pomocy technicznej.

## <a name="support-file-directories"></a>Obsługa katalogów plików

Domyślnie podstawowe pliki obsługi programu Visual Studio znajdują się w następujących katalogach. Te informacje są specyficzne dla wersji.

### <a name="visual-studio-2019"></a>Visual Studio 2019

- % VSINSTALLDIR% MSBuild \\ Microsoft \\ VC \\ *wersja*\\

  Zawiera pliki głównych plików docelowych (. targets) i pliki właściwości (. props), które są używane przez obiekty docelowe. Domyślnie makro $ (VCTargetsPath) odwołuje się do tego katalogu. Symbol zastępczy *wersji* odwołuje się do wersji programu Visual Studio: V160 for visual Studio 2019, V150 for visual Studio 2017.

- % VSINSTALLDIR% MSBuild \\ Microsoft \\ VC \\ *Version* \\ platform \\ *platform*\\

  Zawiera pliki docelowe i właściwości specyficzne dla platformy, które zastępują elementy docelowe i właściwości w katalogu nadrzędnym. Ten katalog zawiera również bibliotekę DLL, która definiuje zadania, które są używane przez obiekty docelowe w tym katalogu. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64.

- % VSINSTALLDIR% MSBuild \\ Microsoft \\ VC \\ *Version* \\ platform \\ *platform* \\ PlatformToolsets zestaw \\ *narzędzi*\\

  Zawiera katalogi, które umożliwiają kompilacji generowanie aplikacji C++ przy użyciu określonego zestawu *narzędzi*. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64. Symbol *zastępczy zestawu narzędzi reprezentuje* podkatalog zestawu narzędzi.

### <a name="visual-studio-2017"></a>Visual Studio 2017

- % VSINSTALLDIR% Common7 \\ IDE \\ VC \\ VCTargets\\

  Zawiera pliki głównych plików docelowych (. targets) i pliki właściwości (. props), które są używane przez obiekty docelowe. Domyślnie makro $ (VCTargetsPath) odwołuje się do tego katalogu.

- % VSINSTALLDIR% Common7 \\ IDE \\ VC \\ VCTargets \\ platform \\ *platformy*\\

  Zawiera pliki docelowe i właściwości specyficzne dla platformy, które zastępują elementy docelowe i właściwości w katalogu nadrzędnym. Ten katalog zawiera również bibliotekę DLL, która definiuje zadania, które są używane przez obiekty docelowe w tym katalogu. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64.

- % VSINSTALLDIR% Common7 \\ IDE \\ VC \\ VCTargets \\ platform \\ *platform* \\ PlatformToolsets zestawu \\ *narzędzi*\\

  Zawiera katalogi, które umożliwiają kompilacji generowanie aplikacji C++ przy użyciu określonego zestawu *narzędzi*. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64. Symbol *zastępczy zestawu narzędzi reprezentuje* podkatalog zestawu narzędzi.

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 i starsze

- *dysk*: \\ Program Files *(x86)* \\ MSBuild \\ Microsoft. cpp (x86) \\ \\ *wersja* 4.0\\

  Zawiera pliki głównych plików docelowych (. targets) i pliki właściwości (. props), które są używane przez obiekty docelowe. Domyślnie makro $ (VCTargetsPath) odwołuje się do tego katalogu.

- *dysk*: \\ Program Files *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ *Version* \\ platform \\ *platform*\\

  Zawiera pliki docelowe i właściwości specyficzne dla platformy, które zastępują elementy docelowe i właściwości w katalogu nadrzędnym. Ten katalog zawiera również bibliotekę DLL, która definiuje zadania, które są używane przez obiekty docelowe w tym katalogu. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64.

- *dysk*: \\ Program Files *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ *Version*platforms \\ \\ *platform* \\ PlatformToolsets zestawu \\ *narzędzi*\\

  Zawiera katalogi, które umożliwiają kompilacji generowanie aplikacji C++ przy użyciu określonego zestawu *narzędzi*. Symbol zastępczy *wersji* to v110 dla programu visual Studio 2012, V120 dla Visual Studio 2013 i wersji 140 dla programu visual Studio 2015. Symbol zastępczy *platformy* reprezentuje podkatalog ARM, Win32 lub x64. Symbol *zastępczy zestawu narzędzi reprezentuje* podkatalog zestawu narzędzi. Na przykład jest wersji 140 do kompilowania aplikacji systemu Windows przy użyciu zestawu narzędzi programu Visual Studio 2015. Lub v120_xp do kompilowania dla systemu Windows XP przy użyciu zestawu narzędzi Visual Studio 2013.

- *dysk*: \\ Program Files *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ platform \\ *platform* \\ PlatformToolsets zestawu \\ *narzędzi*\\

  Ścieżki umożliwiające kompilację do generowania aplikacji programu Visual Studio 2008 lub Visual Studio 2010 nie obejmują *wersji*. W tych wersjach symbol zastępczy *platformy* reprezentuje podkatalog Itanium, Win32 lub x64. Symbol zastępczy zestawu *narzędzi* reprezentuje podkatalog zestawu narzędzi v90 lub V100.

## <a name="support-files"></a>Pliki obsługi

Katalogi plików pomocy technicznej zawierają pliki z następującymi rozszerzeniami:

| Wewnętrzny | Opis |
| --------- | ----------- |
| . targets | Zawiera `Target` elementy XML, które określają zadania, które są wykonywane przez element docelowy. Mogą również zawierać `PropertyGroup` `ItemGroup` elementy,, `ItemDefinitionGroup` i zdefiniowane przez użytkownika, `Item` które są używane do przypisywania plików i opcji wiersza polecenia do parametrów zadań.<br /><br /> Aby uzyskać więcej informacji, zobacz [Target element (MSBuild)](/visualstudio/msbuild/target-element-msbuild). |
| . props | Zawiera `Property Group` i zdefiniowane przez użytkownika `Property` elementy XML, które określają ustawienia plików i parametrów, które są używane podczas kompilacji.<br /><br /> Może również zawierać `ItemDefinitionGroup` i zdefiniowane przez użytkownika `Item` elementy XML, które określają dodatkowe ustawienia. Elementy zdefiniowane w grupie definicji elementu przypominają właściwości, ale nie są dostępne z wiersza polecenia. Pliki projektu programu Visual Studio często używają elementów zamiast właściwości do reprezentowania ustawień.<br /><br /> Aby uzyskać więcej informacji, zobacz [itemmanager element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)i [element Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild). |
| xml | Zawiera elementy XML, które deklarują i inicjują elementy interfejsu użytkownika IDE. Na przykład arkusze właściwości, strony właściwości, formanty TextBox i kontrolki ListBox.<br /><br /> Pliki. XML obsługują bezpośrednio środowisko IDE, a nie MSBuild. Jednak wartości właściwości IDE są przypisywane do właściwości i elementów kompilacji.<br /><br /> Większość plików XML znajduje się w podkatalogu specyficznym dla ustawień regionalnych. Na przykład pliki dla regionu angielski-US znajdują się w $ (VCTargetsPath) \\ 1033 \\ . |

## <a name="user-targets-and-properties"></a>Obiekty docelowe i właściwości użytkownika

Aby efektywnie korzystać z programu MSBuild, warto wiedzieć, które właściwości i cele są przydatne i istotne. Większość właściwości i obiektów docelowych pomaga zaimplementować system kompilacji programu Visual Studio i w związku z tym nie dotyczy użytkownika. W tej sekcji opisano właściwości zorientowane na użytkownika i cele, które warto znać.

### <a name="platformtoolset-property"></a>Właściwość PlatformToolset

`PlatformToolset`Właściwość określa, który zestaw narzędzi MSVC jest używany w kompilacji. Domyślnie używany jest bieżący zestaw narzędzi. Gdy ta właściwość jest ustawiona, jej wartość jest pobierana z ciągami literału w celu utworzenia ścieżki. Jest to katalog, który zawiera pliki właściwości i obiekty docelowe wymagane do skompilowania projektu dla konkretnej platformy. Zestaw narzędzi platformy musi być zainstalowany do kompilowania przy użyciu tej wersji zestawu narzędzi platformy.

Na przykład ustaw właściwość na, aby `PlatformToolset` `v140` używać narzędzi i bibliotek programu Visual Studio 2015 do kompilowania aplikacji:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Właściwość PreferredToolArchitecture

`PreferredToolArchitecture`Właściwość określa, czy kompilator i narzędzia z 32-bitowym, 64-bitowym są używane w kompilacji. Ta właściwość nie ma wpływu na architekturę ani konfigurację platformy wyjściowej. Domyślnie program MSBuild używa wersji x86 kompilatora i narzędzi, jeśli ta właściwość nie jest ustawiona.

Na przykład ustaw właściwość na `PreferredToolArchitecture` `x64` Aby użyć kompilatora 64-bitowego oraz narzędzi do kompilowania aplikacji:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Właściwość UseEnv

Domyślnie ustawienia specyficzne dla platformy dla bieżącego projektu zastępują zmienne środowiskowe PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION i PLATFORM. Ustaw `UseEnv` Właściwość na, aby **`true`** zagwarantować, że zmienne środowiskowe nie zostaną zastąpione.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Targets (Obiekty docelowe)

Istnieją setki obiektów docelowych w plikach obsługi programu Visual Studio. Większość są jednak ukierunkowanymi na system, które użytkownik może zignorować. Większość obiektów docelowych systemu jest poprzedzona znakiem podkreślenia ( `_` ) lub ma nazwę rozpoczynającą się od "PrepareFor", "COMPUTE", "Before", "After", "pre" lub "post".

W poniższej tabeli przedstawiono kilka przydatnych elementów docelowych ukierunkowanych na użytkownika.

| Cel | Opis |
| ------ | ----------- |
| BscMake | Wykonuje narzędzie do konserwacji przeglądanych informacji firmy Microsoft, bscmake.exe. |
| Kompilacja | Kompiluje projekt.<br /><br /> Ten obiekt docelowy jest wartością domyślną dla projektu. |
| ClCompile | Wykonuje narzędzie kompilatora MSVC, cl.exe. |
| Clean | Usuwa tymczasowe i pośrednie pliki kompilacji. |
| Lib | Wykonuje narzędzie Microsoft 32-bit Library Manager, lib.exe. |
| Łącze | Wykonuje narzędzie konsolidatora MSVC, link.exe. |
| ManifestResourceCompile | Wyodrębnia listę zasobów z manifestu, a następnie wykonuje narzędzie kompilatora zasobów systemu Microsoft Windows, rc.exe. |
| MIDL | Wykonuje narzędzie kompilatora Microsoft Interface Definition Language (MIDL), midl.exe. |
| Ponowne kompilowanie | Czyści, a następnie kompiluje projekt. |
| ResourceCompile | Wykonuje narzędzie kompilatora zasobów systemu Microsoft Windows, rc.exe. |
| XdcMake | Wykonuje narzędzie dokumentacji XML xdcmake.exe. |
| XSD | Wykonuje narzędzie definicji schematu XML, xsd.exe. *Zobacz uwagę poniżej.* |

> [!NOTE]
> W programie Visual Studio 2017 lub nowszym obsługa projektu C++ dla plików **XSD** jest przestarzała. Nadal można użyć **programu Microsoft. VisualC. CppCodeProvider** , ręcznie dodając **CppCodeProvider.dll** do pamięci GAC.

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania programu MSBuild](/visualstudio/msbuild/msbuild-task-reference)\
[BscMake, zadanie](/visualstudio/msbuild/bscmake-task)\
[CL — zadanie](/visualstudio/msbuild/cl-task)\
[CPPClean —, zadanie](/visualstudio/msbuild/cppclean-task)\
[LIB — zadanie](/visualstudio/msbuild/lib-task)\
[Połącz zadanie](/visualstudio/msbuild/link-task)\
[MIDL, zadanie](/visualstudio/msbuild/midl-task)\
[MT — zadanie](/visualstudio/msbuild/mt-task)\
[RC — zadanie](/visualstudio/msbuild/rc-task)\
[SetEnv, zadanie](/visualstudio/msbuild/setenv-task)\
[VCMessage —, zadanie](/visualstudio/msbuild/vcmessage-task)\
[XDCMake, zadanie](/visualstudio/msbuild/xdcmake-task)
