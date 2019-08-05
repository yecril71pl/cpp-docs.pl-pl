---
title: Typowe makra dla poleceń i właściwości programu MSBuild
ms.date: 08/02/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 0de96306e645ec85562e414a96283923e93a00ad
ms.sourcegitcommit: af4ab63866ed09b5988ed53f1bb6996a54f02484
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787099"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Typowe makra dla poleceń i właściwości programu MSBuild

W zależności od opcji instalacji program Visual Studio może udostępnić Ci setki makr w projekcie programu Visual Studio (na podstawie MSBuild). Są one zgodne z właściwościami programu MSBuild, które są ustawiane domyślnie, lub w plikach. props lub. targets lub w ustawieniach projektu. Możesz użyć tych makr wszędzie w oknie dialogowym **strony właściwości** projektu, w którym są akceptowane ciągi. W tych makrach nie jest rozróżniana wielkość liter.

## <a name="view-the-current-properties-and-macros"></a>Wyświetlanie bieżących właściwości i makr

Aby wyświetlić wszystkie aktualnie dostępne makra, w oknie dialogowym **strony właściwości** w obszarze **Katalogi VC + +** wybierz strzałkę listy rozwijanej na końcu wiersza właściwości. Kliknij przycisk **Edytuj** , a następnie w oknie dialogowym Edycja wybierz przycisk **makra** . Bieżący zestaw właściwości i makr widoczny dla programu Visual Studio jest wyświetlany wraz z bieżącą wartością dla każdej z nich. Aby uzyskać więcej informacji, zobacz sekcję **Określanie wartości zdefiniowanych przez użytkownika** na [ C++ stronie właściwości projektu](property-pages-visual-cpp.md).

![Przycisk makr VC + +](../media/vcppdir_libdir_macros.png "Menu MACROS")

## <a name="list-of-common-macros"></a>Lista typowych makr

W tej tabeli opisano często używany podzbiór dostępnych makr; w tym miejscu istnieje wiele innych informacji. Przejdź do okna dialogowego **makra** , aby wyświetlić wszystkie właściwości i ich bieżące wartości w projekcie. Aby uzyskać szczegółowe informacje na temat sposobu tworzenia i używania definicji właściwości programu MSBuild jako makr w plikach. props,. targets i. vcxproj, zobacz [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Opis|
|-----------|-----------------|
|**$ (Konfiguracja)**|Nazwa bieżącej konfiguracji projektu, na przykład "Debugowanie".|
|**$ (DevEnvDir)**|Katalog instalacyjny programu Visual Studio (zdefiniowany jako Drive + Path); zawiera końcowy ukośnik odwrotny "\\".|
|**$ (FrameworkDir)**|Katalog, w którym zainstalowano .NET Framework.|
|**$ (FrameworkSDKDir)**|Katalog, w którym zainstalowano .NET Framework. .NET Framework można zainstalować jako część programu Visual Studio lub oddzielnie.|
|**$ (FrameworkVersion)**|Wersja .NET Framework używana przez program Visual Studio. W połączeniu z **$ (FrameworkDir)** pełna ścieżka do wersji .NET Framework używana przez program Visual Studio.|
|**$ (FxCopDir)**|Ścieżka do pliku FxCop. cmd. Plik FxCop. cmd nie jest instalowany ze wszystkimi wersjami programu Visual Studio.|
|**$ (IntDir)**|Ścieżka do katalogu określonego dla plików pośrednich. Jeśli jest ścieżką względną, pliki pośrednie przechodzą do tej ścieżki dołączone do katalogu projektu. Ta ścieżka powinna mieć końcowy ukośnik. Jest on rozpoznawany jako wartość właściwości **katalogu** pośredniego. Nie używaj **$ (OutDir)** do definiowania tej właściwości.|
|**$(OutDir)**|Ścieżka do katalogu pliku wyjściowego. Jeśli jest ścieżką względną, pliki wyjściowe przejdą do tej ścieżki dołączenia do katalogu projektu. Ta ścieżka powinna mieć końcowy ukośnik. Jest on rozpoznawany jako wartość właściwości **katalogu wyjściowego** . Nie używaj **$ (IntDir)** do definiowania tej właściwości.|
|**$ (Platforma)**|Nazwa bieżącej platformy projektu, na przykład "Win32".|
|**$ (Nazwaskróconaplatformy)**|Krótka nazwa bieżącej architektury, na przykład "x86" lub "x64".|
|**$ (ProjectDir)**|Katalog projektu (zdefiniowany jako Drive + Path); zawiera końcowy ukośnik odwrotny "\\".|
|**$ (ProjectExt)**|Rozszerzenie pliku projektu. Zawiera "." przed rozszerzeniem pliku.|
|**$(ProjectFileName)**|Nazwa pliku projektu (zdefiniowana jako nazwa podstawowa + rozszerzenie pliku).|
|**$ (ProjectName)**|Podstawowa nazwa projektu.|
|**$ (ProjectPath)**|Nazwa ścieżki bezwzględnej projektu (zdefiniowana jako dysk + ścieżka + nazwa podstawowa + rozszerzenie pliku).|
|**$ (PublishDir)**|Lokalizacja wyjściowa dla elementu docelowego publikowania; zawiera końcowy ukośnik odwrotny "\\". Domyślnie jest to folder **$ (OutDir) App.\\ Publish** .|
|**$ (RemoteMachine)**|Ustaw wartość właściwości **maszyna zdalna** na stronie właściwości debugowania. Aby uzyskać więcej informacji [, zobacz Zmiana ustawieńC++ projektu dla konfiguracji C/Debug](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$ (RootNameSpace)**|Przestrzeń nazw (jeśli istnieje) zawierająca aplikację.|
|**$ (SolutionDir)**|Katalog rozwiązania (zdefiniowany jako Drive + Path); zawiera końcowy ukośnik odwrotny "\\". Zdefiniowane tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$ (SolutionExt)**|Rozszerzenie pliku rozwiązania. Zawiera "." przed rozszerzeniem pliku. Zdefiniowane tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(SolutionFileName)**|Nazwa pliku rozwiązania (zdefiniowana jako nazwa podstawowa + rozszerzenie pliku). Zdefiniowane tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$ (SolutionName)**|Podstawowa nazwa rozwiązania. Zdefiniowane tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$ (SolutionPath)**|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowana jako dysk + ścieżka + nazwa podstawowa + rozszerzenie pliku). Zdefiniowane tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$ (TargetDir)**|Katalog podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako Drive + Path); zawiera końcowy ukośnik odwrotny "\\".|
|**$ (TargetExt)**|Rozszerzenie pliku podstawowego pliku wyjściowego dla kompilacji. Zawiera "." przed rozszerzeniem pliku.|
|**$(TargetFileName)**|Nazwa pliku podstawowego pliku wyjściowego dla kompilacji (zdefiniowana jako nazwa podstawowa + rozszerzenie pliku).|
|**$ (TargetName)**|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|
|**$ (TargetPath)**|Nazwa ścieżki bezwzględnej podstawowego pliku wyjściowego dla kompilacji (zdefiniowana jako dysk + ścieżka + nazwa podstawowa + rozszerzenie pliku).|
|**$ (VCInstallDir)**|Katalog zawierający C++ zawartość instalacji programu Visual Studio. Ta właściwość zawiera wersję zestawu narzędzi firmy Microsoft C++ (MSVC), który może być inny niż host Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v140`, **$ (VCInstallDir)** zawiera ścieżkę do instalacji programu Visual Studio 2015.|
|**$ (VSInstallDir)**|Katalog, w którym zainstalowano program Visual Studio. Ta właściwość zawiera wersję zestawu narzędzi programu Visual Studio, który może być inny niż host programu Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v110`, **$ (VSInstallDir)** zawiera ścieżkę do instalacji programu Visual Studio 2012.|
|**$(WebDeployPath)**|Ścieżka względna od elementu głównego wdrożenia sieci Web do lokalizacji, do której należą dane wyjściowe projektu. Zwraca tę samą wartość, <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>co.|
|**$(WebDeployRoot)**|Ścieżka bezwzględna do lokalizacji  **\<hosta lokalnego >** . Na przykład c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Przestarzałe makra

System kompilacji dla programu C++ został znacząco zmieniony między programem visual Studio 2008 i visual Studio 2010. Wiele makr używanych we wcześniejszych typach projektów zostało zmienionych na nowe. Te makra nie są już używane lub zostały zastąpione przez jedną lub więcej wartości równoważnych lub [makr metadanych elementu](/visualstudio/msbuild/itemmetadata-element-msbuild) (_Nazwa_ **%(** **)** ). Makra oznaczone jako "zmigrowane" można aktualizować za pomocą narzędzia migracji projektu. Jeśli projekt zawierający makro jest migrowany z programu Visual Studio 2008 lub starszego do programu Visual Studio 2010, program Visual Studio konwertuje makro na równoważne bieżące makro. Nowsze wersje programu Visual Studio nie mogą konwertować projektów z programu Visual Studio 2008 i wcześniej do nowego typu projektu. Należy przekonwertować te projekty w dwóch krokach; najpierw przekonwertuj je na program Visual Studio 2010, a następnie Przekształć wynik na nowszą wersję programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Omówienie potencjalnych problemów](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)z uaktualnianiem.

|Macro|Opis|
|-----------|-----------------|
|**$ (InputDir)**|(Migrowane). Katalog pliku wejściowego (zdefiniowany jako Drive + Path); zawiera końcowy ukośnik odwrotny "\\". Jeśli projekt jest danymi wejściowymi, to makro jest równoważne z **$ (ProjectDir)** .|
|**$ (InputExt)**|(Migrowane). Rozszerzenie pliku wejściowego. Zawiera "." przed rozszerzeniem pliku. Jeśli projekt jest danymi wejściowymi, to makro jest równoważne z **$ (ProjectExt)** . W przypadku plików źródłowych jest to **% (rozszerzenie)** .|
|**$ (InputFileName)**|(Migrowane). Nazwa pliku wejściowego (zdefiniowana jako nazwa podstawowa + rozszerzenie pliku). Jeśli projekt jest danymi wejściowymi, to makro jest równoważne z **$ (ProjectFileName)** . W przypadku plików źródłowych jest to **% (tożsamość)** .|
|**$ (InputName)**|(Migrowane). Podstawowa nazwa pliku wejściowego. Jeśli projekt jest danymi wejściowymi, to makro jest równoważne z **$ (ProjectName)** . W przypadku plików źródłowych jest to **% (filename)** .|
|**$ (InputPath)**|(Migrowane). Nazwa ścieżki bezwzględnej pliku wejściowego (zdefiniowanego jako Drive + Path + nazwa podstawowa + rozszerzenie pliku). Jeśli projekt jest danymi wejściowymi, to makro jest równoważne z **$ (ProjectPath)** . W przypadku plików źródłowych jest to **% (FullPath)** .|
|**$ (Parentname)**|Nazwa elementu zawierającego ten element projektu. Będzie to nazwa folderu nadrzędnego lub nazwa projektu.|
|**$ (SafeInputName)**|Nazwa pliku jako prawidłowej nazwy klasy, pomniejszonej o rozszerzenie pliku. Ta właściwość nie ma dokładnego odpowiednika.|
|**$ (SafeParentName)**|Nazwa bezpośredniego elementu nadrzędnego w prawidłowym formacie nazwy. Na przykład formularz jest elementem nadrzędnym pliku resx. Ta właściwość nie ma dokładnego odpowiednika.|
|**$ (SafeRootNamespace)**|Nazwa przestrzeni nazw, w której Kreatorzy projektu dodają kod. Ta nazwa przestrzeni nazw będzie zawierać tylko znaki, które byłyby dozwolone w C++ prawidłowym identyfikatorze. Ta właściwość nie ma dokładnego odpowiednika.|

## <a name="see-also"></a>Zobacz także

[Projekty programu Visual Studio —C++](../creating-and-managing-visual-cpp-projects.md)\
[Wizualne C++ przenoszenie i uaktualnianie przewodnika](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[Omówienie potencjalnych problemów z uaktualnianiem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
