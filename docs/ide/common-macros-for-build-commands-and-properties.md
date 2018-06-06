---
title: Typowe makra dla poleceń kompilacji oraz właściwości
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 278cb34a49650d88b9e7de9efd8456ff430aca63
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569930"
---
# <a name="common-macros-for-build-commands-and-properties"></a>Typowe makra dla poleceń kompilacji oraz właściwości

W zależności od opcji instalacji program Visual Studio można udostępnić setki makra użytkownika. Odpowiadają one właściwości programu MSBuild, które są ustawione domyślnie lub .props lub .targets plików lub ustawienia projektu. Użyj tych makr dowolne miejsce w projekcie **strony właściwości** okno dialogowe, w którym są akceptowane ciągów. Tych makr nie jest uwzględniana.

## <a name="view-the-current-properties-and-macros"></a>Wyświetl bieżące właściwości i makra

Aby wyświetlić aktualnie dostępne makra, na stronach właściwości w **strony właściwości** okno dialogowe, wybierz strzałkę listy rozwijanej na końcu wiersza właściwości. Jeśli **Edytuj** jest dostępna, wybierz go, a następnie w oknie dialogowym Edycja wybierz **makra** przycisku. Bieżący zestaw właściwości oraz makra są widoczne dla programu Visual Studio jest wyświetlana wraz z bieżącą wartość dla każdego. Aby uzyskać więcej informacji, zobacz **wartości Specifying User-Defined** sekcji [strony właściwości](../ide/property-pages-visual-cpp.md).

## <a name="list-of-common-macros"></a>Listę typowych makr

Poniższa tabela zawiera opis najczęściej używanymi podzbioru dostępnych makr. Ta lista jest znacznie niższa niż wyczerpujący. Szczegółowe informacje dotyczące sposobu tworzenia i używany jako makra w .props, .targets i .vcxproj plików definicji właściwości programu MSBuild, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).

|Macro|Opis|
|-----------|-----------------|
|**$(Configuration)**|Nazwa w bieżącej konfiguracji projektu, na przykład "Debugowanie".|
|**$(Devenvdir) —**|Katalogu instalacyjnego programu Visual Studio (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(Frameworkdir) —**|Katalog, w którym został zainstalowany program .NET Framework.|
|**$(Frameworksdkdir) —**|Katalog, w którym jest zainstalowany system .NET Framework. .NET Framework można zainstalować jako część programu Visual Studio lub oddzielnie.|
|**$(Frameworkversion) —**|Wersja programu .NET Framework, używany przez Visual Studio. Połączone z **$(frameworkdir) —**, pełną ścieżkę do wersji programu .NET Framework korzystanie przez program Visual Studio.|
|**$(Fxcopdir) —**|Ścieżka do pliku fxcop.cmd. Plik fxcop.cmd nie jest zainstalowany we wszystkich wersjach Visual C++.|
|**$(IntDir)**|Ścieżka do katalogu określonego dla plików pośrednich. Jeśli ścieżka względna plików pośrednich przejdź do tej ścieżki dołączone do katalogu projektu. Ta ścieżka powinna mieć ukośnika. To jest rozpoznawany jako wartość **katalog pośredni** właściwości. Nie używaj **$(OutDir)** do definiowania tej właściwości.|
|**$(OutDir)**|Ścieżka do katalogu pliku danych wyjściowych. Jeśli jest to ścieżka względna, pliki wyjściowe przejdź do tej ścieżki dołączone do katalogu projektu. Ta ścieżka powinna mieć ukośnika. To jest rozpoznawany jako wartość **katalog wyjściowy** właściwości. Nie używaj **$(IntDir)** do definiowania tej właściwości.|
|**$(Platform)**|Nazwa bieżącego projektu platformy, na przykład "Win32".|
|**$(Projectdir) —**|W katalogu projektu (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(Projectext) —**|Rozszerzenie pliku projektu. Obejmuje on "." przed rozszerzeniem pliku.|
|**$(Projectfilename) —**|Nazwa pliku projektu (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku).|
|**$(Projectname) —**|Podstawowa nazwa projektu.|
|**$(Projectpath) —**|Nazwa ścieżki bezwzględnej projektu (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku).|
|**$(RemoteMachine)**|Ustaw wartość **maszyny zdalnej** właściwości na stronie właściwości debugowania. Zobacz [Zmienianie ustawienia projektu dla konfiguracji debugowania C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Aby uzyskać więcej informacji.|
|**$(Rootnamespace) —**|Przestrzeń nazw, jeśli istnieje aplikacja.|
|**$(SolutionDir)**|Katalog rozwiązania (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(Solutionext) —**|Rozszerzenie pliku rozwiązania. Obejmuje on "." przed rozszerzeniem pliku. Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(Solutionfilename) —**|Nazwa pliku rozwiązania (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku). Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(Solutionname) —**|Nazwa podstawowego rozwiązania. Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(Solutionpath) —**|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku). Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|
|**$(Targetdir) —**|Katalogu podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|**$(TargetExt)**|Rozszerzenie pliku podstawowego pliku wyjściowego dla kompilacji. Obejmuje on "." przed rozszerzeniem pliku.|
|**$(Targetfilename) —**|Nazwa pliku podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku).|
|**$(TargetName)**|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|
|**$(Targetpath) —**|Ścieżka bezwzględna Nazwa podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku).|
|**$(Vcinstalldir) —**|Katalog, który zawiera zawartość C++ instalację programu Visual Studio. Ta właściwość zawiera wersję docelowej narzędzi Visual C++, która może się różnić który hosta programu Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v140`, **$(vcinstalldir) —** zawiera ścieżkę do instalacji programu Visual C++ 2015.|
|**$(Vsinstalldir) —**|Katalog, w którym jest zainstalowany program Visual Studio. Ta właściwość zawiera wersję docelowej narzędzi Visual Studio, która może się różnić który hosta programu Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v110`, **$(vsinstalldir) —** zawiera ścieżkę do instalacji programu Visual Studio 2012.|
|**$(Webdeploypath) —**|Ścieżka względna z katalogu głównego wdrożenia sieci web do których danych wyjściowych projektu należy. Zwraca taką samą wartość jak <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|
|**$(Webdeployroot) —**|Ścieżka bezwzględna do lokalizacji  **\<localhost >**. Na przykład c:\inetpub\wwwroot.|

## <a name="obsolete-macros"></a>Przestarzałe makra

System kompilacji dla języka C++ znacznie została zmieniona między programu Visual Studio 2008 i programu Visual Studio 2010. Makra wiele starszych typów projektu została zmieniona na nowe. Tych makr nie są już używane lub zostały zastąpione przez jedną lub więcej właściwości równoważne lub [makro metadanych elementu](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_nazwa_**)**) wartości. Makra, które są oznaczone jako "migrowane" może być aktualizowany przez narzędzie do migracji projektu. Jeśli projekt, który zawiera makro jest migracja z programu Visual Studio 2008 lub jego starszej wersji programu Visual Studio 2010, Visual Studio konwertuje makra równoważne bieżącego makra. Nowsze wersje programu Visual Studio nie można przekonwertować projektów programu Visual Studio 2008 i starszych nowy typ projektu. Przekonwertuj te projekty w dwóch krokach; najpierw przekonwertuj je do programu Visual Studio 2010, a następnie wykonać konwersję wynik do nowszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [omówienie potencjalne problemy z uaktualnieniem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Macro|Opis|
|-----------|-----------------|
|**$(Inputdir) —**|(Migracja). Katalog pliku wejściowego (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectdir) —**.|
|**$(Inputext) —**|(Migracja). Rozszerzenie pliku wejściowego. Obejmuje on "." przed rozszerzeniem pliku. Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectext) —**. W przypadku plików źródłowych jest **%(Extension)**.|
|**$(Inputfilename) —**|(Migracja). Nazwa pliku wejściowego (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku). Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectfilename) —**. W przypadku plików źródłowych jest **%(Identity)**.|
|**$(Inputname) —**|(Migracja). Podstawowa nazwa pliku wejściowego. Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectname) —**. W przypadku plików źródłowych jest **%(Filename)**.|
|**$(Inputpath) —**|(Migracja). Nazwa ścieżki pliku wejściowego (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku). Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectpath) —**. W przypadku plików źródłowych jest **%(FullPath)**.|
|**$(ParentName)**|Nazwa elementu zawierającego ten element projektu. Są to nazwa folderu nadrzędnego lub nazwę projektu.|
|**$(SafeInputName)**|Nazwa pliku jako prawidłową nazwą klasy, minus rozszerzenie pliku. Ta właściwość nie ma równoważnej.|
|**$(SafeParentName)**|Nazwa natychmiastowego elementu nadrzędnego w formacie prawidłową nazwę. Na przykład formularz jest elementem nadrzędnym pliku .resx. Ta właściwość nie ma równoważnej.|
|**$(Saferootnamespace) —**|Nazwa przestrzeni nazw, w którym kreatorów projekt doda kodu. Ta nazwa przestrzeni nazw będzie zawierać tylko znaki, które mogą być dozwolone w prawidłowego identyfikatora C++. Ta właściwość nie ma równoważnej.|

## <a name="see-also"></a>Zobacz także

- [Kompilowanie projektów C++ w Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)
- [Visual C++, przenoszenie i uaktualnianie przewodnik](../porting/visual-cpp-porting-and-upgrading-guide.md)
- [Omówienie potencjalne problemy z uaktualnieniem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
