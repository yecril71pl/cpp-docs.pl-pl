---
title: Typowe makra dla poleceń kompilacji oraz właściwości
ms.date: 05/29/2018
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
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 669114691bc89c1e8136e07a949be57cda3d71b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823301"
---
# <a name="common-macros-for-build-commands-and-properties"></a>Typowe makra dla poleceń kompilacji oraz właściwości

W zależności od opcje instalacji systemu Visual Studio można udostępnić setki makra dla Ciebie. Odpowiadają one właściwości programu MSBuild, które są ustawione domyślnie, lub w plikach .props i .targets lub w ustawieniach projektu. Te makra można użyć dowolnego miejsca w projekcie **stron właściwości** okno dialogowe, gdzie ciągi są akceptowane. Te makra nie są z uwzględnieniem wielkości liter.

## <a name="view-the-current-properties-and-macros"></a>Wyświetl bieżące właściwości i makra

Aby wyświetlić aktualnie dostępnych makr, na dowolnej stronie właściwości **stron właściwości** okno dialogowe, wybierz strzałkę listy rozwijanej na końcu wiersza właściwości. Jeśli **Edytuj** jest dostępna, wybierz go, a następnie w oknie dialogowym Edycja wybierz **makra** przycisku. Bieżący zestaw właściwości i makr widoczne w programie Visual Studio znajduje się wraz z bieżącą wartość dla każdego. Aby uzyskać więcej informacji, zobacz **wartości Specifying User-Defined** części [dokumentacja strony właściwości projektu C++](property-pages-visual-cpp.md).

## <a name="list-of-common-macros"></a>Lista typowych makr

W tej tabeli opisano typowe podzbioru dostępnych makr. Ta lista nie jest wyczerpująca. Aby uzyskać szczegółowe informacje dotyczące sposobu tworzenia definicji właściwości programu MSBuild i używany jako makra w pliki.vcxproj, .props i .targets, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Opis|
|-----------|-----------------|
|**$(Configuration)**|Nazwa bieżącej konfiguracji projektu, na przykład "Debug".|
|**$(DevEnvDir)**|Katalogu instalacyjnego programu Visual Studio (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(FrameworkDir)**|Katalog, w którym został zainstalowany program .NET Framework.|
|**$(FrameworkSDKDir)**|Katalog, w którym zainstalowany jest .NET Framework. .NET Framework można zainstalować jako część programu Visual Studio lub oddzielnie.|
|**$(FrameworkVersion)**|Wersja .NET Framework co używany przez program Visual Studio. W połączeniu z **$(FrameworkDir)**, pełną ścieżkę do wersji programu .NET Framework korzystanie przez program Visual Studio.|
|**$(FxCopDir)**|Ścieżka do pliku fxcop.cmd. Plik fxcop.cmd nie jest zainstalowany we wszystkich wersjach Visual C++.|
|**$(IntDir)**|Ścieżka do katalogu określonym dla plików pośrednich. Jeśli jest to ścieżka względna, pliki pośrednie przejdź do tej ścieżki do katalogu projektu. Ścieżka ta powinna mieć znaku ukośnika na końcu. To jest rozpoznawana jako wartość **katalog pośredni** właściwości. Nie używaj **$(OutDir)** do definiowania tej właściwości.|
|**$(OutDir)**|Ścieżka do katalogu pliku wyjściowego. Jeśli jest to ścieżka względna, pliki wyjściowe przejdź do tej ścieżki do katalogu projektu. Ścieżka ta powinna mieć znaku ukośnika na końcu. To jest rozpoznawana jako wartość **katalog wyjściowy** właściwości. Nie używaj **$(IntDir)** do definiowania tej właściwości.|
|**$(Platform)**|Nazwa bieżącego projektu platformy, na przykład "Win32".|
|**$(ProjectDir)**|Katalogu projektu (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(ProjectExt)**|Rozszerzenie pliku projektu. Zawiera on "." przed rozszerzeniem pliku.|
|**$(ProjectFileName)**|Nazwa pliku projektu (zdefiniowany jako podstawowej nazwy + rozszerzenia pliku).|
|**$(ProjectName)**|Podstawowa nazwa projektu.|
|**$(ProjectPath)**|Nazwa ścieżki bezwzględnej projektu (zdefiniowany jako dysku i ścieżki + nazwa podstawowa rozszerzenie pliku).|
|**$(RemoteMachine)**|Ustaw wartość **maszyny zdalnej** właściwości na stronie właściwości debugowania. Zobacz [Zmienianie ustawienia projektu dla konfiguracji debugowania języka C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Aby uzyskać więcej informacji.|
|**$(RootNameSpace)**|Przestrzeń nazw, jeśli aplikacja.|
|**$(SolutionDir)**|Katalog rozwiązania (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Zdefiniowane tylko wtedy, gdy tworzenie rozwiązania w środowisku IDE.|
|**$(SolutionExt)**|Rozszerzenie pliku rozwiązania. Zawiera on "." przed rozszerzeniem pliku. Zdefiniowane tylko wtedy, gdy tworzenie rozwiązania w środowisku IDE.|
|**$(SolutionFileName)**|Nazwa pliku rozwiązania (zdefiniowany jako podstawowej nazwy + rozszerzenia pliku). Zdefiniowane tylko wtedy, gdy tworzenie rozwiązania w środowisku IDE.|
|**$(SolutionName)**|Podstawowa nazwa rozwiązania. Zdefiniowane tylko wtedy, gdy tworzenie rozwiązania w środowisku IDE.|
|**$(SolutionPath)**|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowany jako dysku i ścieżki + nazwa podstawowa rozszerzenie pliku). Zdefiniowane tylko wtedy, gdy tworzenie rozwiązania w środowisku IDE.|
|**$(TargetDir)**|Katalog pliku główny wynik kompilacji (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(TargetExt)**|Rozszerzenie pliku plik główny wynik kompilacji. Zawiera on "." przed rozszerzeniem pliku.|
|**$(TargetFileName)**|Nazwa pliku plik główny wynik kompilacji (zdefiniowany jako podstawowej nazwy + rozszerzenia pliku).|
|**$(TargetName)**|Podstawowa nazwa pliku wyjściowego podstawowej dla kompilacji.|
|**$(TargetPath)**|Nazwa ścieżki bezwzględnej plik główny wynik kompilacji (zdefiniowany jako dysku i ścieżki + nazwa podstawowa rozszerzenie pliku).|
|**$(VCInstallDir)**|Katalog, który zawiera zawartości C++ w instalacji programu Visual Studio. Ta właściwość zawiera wersję narzędzi Visual C++ docelowej mogą się różnić, host programu Visual Studio. Na przykład podczas kompilowania przy użyciu `$(PlatformToolset) = v140`, **$(VCInstallDir)** zawiera ścieżkę do instalacji programu Visual C++ 2015.|
|**$(VSInstallDir)**|Katalog, w którym jest zainstalowany program Visual Studio. Ta właściwość zawiera wersję docelowego zestawu narzędzi Visual Studio, które mogą się różnić, host programu Visual Studio. Na przykład podczas kompilowania przy użyciu `$(PlatformToolset) = v110`, **$(VSInstallDir)** zawiera ścieżkę do instalacji programu Visual Studio 2012.|
|**$(WebDeployPath)**|Ścieżka względna z katalogu głównego wdrażania sieci web do której dane wyjściowe projektu należą. Zwraca taką samą wartość jak <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(WebDeployRoot)**|Ścieżka bezwzględna do lokalizacji  **\<localhost >**. Na przykład c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Przestarzałe makra

System kompilacji dla języka C++ został znacznie zmodyfikowany między Visual Studio 2008 i programu Visual Studio 2010. Wiele makra używane w starszych typach projektów zostały zmienione na nowe. Te makra nie są już używane lub został zastąpiony przez jedną lub więcej właściwości równoważne lub [makro metadanych elementu](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_nazwa_**)**) wartości. Makra, które są oznaczone jako "migrowane" można aktualizować za pomocą narzędzia migracji projektu. Jeśli projekt, który zawiera makra jest migracja z programu Visual Studio 2008 lub jego starszej wersji programu Visual Studio 2010, Visual Studio konwertuje makro równoważne bieżącego makra. Nowsze wersje programu Visual Studio nie można przekonwertować projekty z Visual Studio 2008 i wcześniej na nowy typ projektu. Musisz konwertować te projekty w dwóch krokach; najpierw przekonwertuj je do programu Visual Studio 2010, a następnie przekonwertować wynik do nowszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [omówienie potencjalnych problemów z uaktualnieniem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Opis|
|-----------|-----------------|
|**$(InputDir)**|(Migracji). Katalog pliku wejściowego (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Jeśli projekt jest w danych wejściowych, wówczas to makro jest odpowiednikiem **$(ProjectDir)**.|
|**$(InputExt)**|(Migracji). Rozszerzenie pliku wejściowego. Zawiera on "." przed rozszerzeniem pliku. Jeśli projekt jest w danych wejściowych, wówczas to makro jest odpowiednikiem **$(ProjectExt)**. W przypadku plików źródłowych jest **%(Extension)**.|
|**$(InputFileName)**|(Migracji). Nazwa pliku wejściowego (zdefiniowany jako podstawowej nazwy + rozszerzenia pliku). Jeśli projekt jest w danych wejściowych, wówczas to makro jest odpowiednikiem **$(ProjectFileName)**. W przypadku plików źródłowych jest **%(Identity)**.|
|**$(InputName)**|(Migracji). Podstawowa nazwa pliku wejściowego. Jeśli projekt jest w danych wejściowych, wówczas to makro jest odpowiednikiem **$(ProjectName)**. W przypadku plików źródłowych jest **%(Filename)**.|
|**$(InputPath)**|(Migracji). Nazwa ścieżki bezwzględnej pliku wejściowego (zdefiniowany jako dysku i ścieżki + nazwa podstawowa rozszerzenie pliku). Jeśli projekt jest w danych wejściowych, wówczas to makro jest odpowiednikiem **$(ProjectPath)**. W przypadku plików źródłowych jest **%(FullPath)**.|
|**$(ParentName)**|Nazwa elementu zawierającego tego elementu projektu. Są to nazwa folderu nadrzędnego lub nazwa projektu.|
|**$(SafeInputName)**|Nazwa pliku jako prawidłową nazwą klasy, bez rozszerzenia pliku. Ta właściwość nie ma dokładnie odpowiadać.|
|**$(SafeParentName)**|Nazwa bezpośredni obiekt nadrzędny w formacie prawidłową nazwę. Na przykład formularz jest elementem nadrzędnym pliku resx. Ta właściwość nie ma dokładnie odpowiadać.|
|**$(SafeRootNamespace)**|Nazwa przestrzeni nazw, w którym kreatorów projektu spowoduje dodanie kodu. Ta nazwa przestrzeni nazw będzie zawierać tylko znaki, które będą dozwolone w prawidłowego identyfikatora C++. Ta właściwość nie ma dokładnie odpowiadać.|

## <a name="see-also"></a>Zobacz także

- [Projekty programu Visual Studio — C++](../creating-and-managing-visual-cpp-projects.md)
- [Visual C++, przenoszenie i uaktualnianie przewodnik](../../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Omówienie potencjalnych problemów z uaktualnieniem](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
