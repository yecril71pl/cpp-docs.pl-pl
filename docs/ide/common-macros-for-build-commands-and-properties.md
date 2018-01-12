---
title: "Typowe makra dla poleceń kompilacji oraz właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f96e403516d6f85804fa798d7a0c28575482ff43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="common-macros-for-build-commands-and-properties"></a>Typowe makra dla poleceń kompilacji oraz właściwości
W zależności od opcji instalacji program Visual Studio można udostępnić setki makra użytkownika. Odpowiadają one właściwości programu MSBuild, które są ustawione domyślnie lub .props lub .targets plików lub ustawienia projektu. Użyj tych makr dowolne miejsce w projekcie **strony właściwości** okno dialogowe, w którym są akceptowane ciągów. Tych makr nie jest uwzględniana.  
  
 Aby wyświetlić dostępne makra, w kolumnie z prawej strony nazwy właściwości, kliknij strzałkę listy rozwijanej. Jeśli **Edytuj** jest dostępny, kliknij go, a następnie kliknij w oknie dialogowym Edycja **makra**. Aby uzyskać więcej informacji, zobacz **wartości Specifying User-Defined** sekcji [strony właściwości](../ide/property-pages-visual-cpp.md).  
  
 Makra, które są oznaczone jako "Przestarzałe" nie są już używane lub zostały zastąpione przez równoważne [makro metadanych elementu](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(***nazwa***)**) . Makra, które są oznaczone jako "przestarzałe; Migracja"również są przestarzałe. I dodatkowo, jeśli projekt, który zawiera makro jest migracja z programu Visual Studio 2008, Visual Studio konwertuje makra na równoważne bieżącego makra.  
  
 W poniższej tabeli opisano typowe podzbioru dostępnych makr. Ta lista nie jest wyczerpująca. Szczegółowe informacje dotyczące sposobu tworzenia i używany jako makra w .props, .targets i .vcxproj plików definicji właściwości programu MSBuild, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
|Makra|Opis|  
|-----------|-----------------|  
|**$(RemoteMachine)**|Ustaw wartość **maszyny zdalnej** właściwości na stronie właściwości debugowania. Zobacz [Zmienianie ustawienia projektu dla konfiguracji debugowania C/C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) Aby uzyskać więcej informacji.|  
|**$(Configuration)**|Nazwa w bieżącej konfiguracji projektu, na przykład "Debugowanie".|  
|**$(Platform)**|Nazwa bieżącego projektu platformy, na przykład "Win32".|  
|**$(ParentName)**|(Przestarzałe). Nazwa elementu zawierającego ten element projektu. Są to nazwa folderu nadrzędnego lub nazwę projektu.|  
|**$(Rootnamespace) —**|Przestrzeń nazw, jeśli istnieje aplikacja.|  
|**$(IntDir)**|Ścieżka do katalogu określonego dla plików pośrednich. Jeśli ścieżka względna plików pośrednich przejdź do tej ścieżki dołączone do katalogu projektu. Ta ścieżka powinna mieć ukośnika. To jest rozpoznawany jako wartość **katalog pośredni** właściwości. Nie używaj **$(OutDir)** do definiowania tej właściwości.|  
|**$(OutDir)**|Ścieżka do katalogu pliku danych wyjściowych. Jeśli jest to ścieżka względna, pliki wyjściowe przejdź do tej ścieżki dołączone do katalogu projektu. Ta ścieżka powinna mieć ukośnika. To jest rozpoznawany jako wartość **katalog wyjściowy** właściwości. Nie używaj **$(IntDir)** do definiowania tej właściwości.|  
|**$(Devenvdir) —**|Katalogu instalacyjnego programu Visual Studio (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|  
|**$(Inputdir) —**|(Przestarzałe; migracji). Katalog pliku wejściowego (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectdir) —**.|  
|**$(Inputpath) —**|(Przestarzałe; migracji). Nazwa ścieżki pliku wejściowego (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku). Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectpath) —**.|  
|**$(Inputname) —**|(Przestarzałe; migracji). Podstawowa nazwa pliku wejściowego. Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectname) —**.|  
|**$(Inputfilename) —**|(Przestarzałe; migracji). Nazwa pliku wejściowego (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku). Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectfilename) —**.|  
|**$(Inputext) —**|(Przestarzałe; migracji). Rozszerzenie pliku wejściowego. Obejmuje on "." przed rozszerzeniem pliku. Jeśli projekt danych wejściowych, wówczas to makro jest odpowiednikiem **$(projectext) —**.|  
|**$(Projectdir) —**|W katalogu projektu (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|  
|**$(Projectpath) —**|Nazwa ścieżki bezwzględnej projektu (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku).|  
|**$(Projectname) —**|Podstawowa nazwa projektu.|  
|**$(Projectfilename) —**|Nazwa pliku projektu (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku).|  
|**$(Projectext) —**|Rozszerzenie pliku projektu. Obejmuje on "." przed rozszerzeniem pliku.|  
|**$(SolutionDir)**|Katalog rozwiązania (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\". Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|  
|**$(Solutionpath) —**|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku). Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|  
|**$(Solutionname) —**|Nazwa podstawowego rozwiązania. Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|  
|**$(Solutionfilename) —**|Nazwa pliku rozwiązania (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku). Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|  
|**$(Solutionext) —**|Rozszerzenie pliku rozwiązania. Obejmuje on "." przed rozszerzeniem pliku. Zdefiniowany tylko w przypadku kompilowania rozwiązania w środowisku IDE.|  
|**$(Targetdir) —**|Katalogu podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|  
|**$(Targetpath) —**|Ścieżka bezwzględna Nazwa podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako dysk + ścieżki + podstawowej nazwy rozszerzenia pliku).|  
|**$(TargetName)**|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|  
|**$(Targetfilename) —**|Nazwa pliku podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako podstawowa nazwa + rozszerzenia pliku).|  
|**$(TargetExt)**|Rozszerzenie pliku podstawowego pliku wyjściowego dla kompilacji. Obejmuje on "." przed rozszerzeniem pliku.|  
|**$(Vsinstalldir) —**|Katalog, w którym jest zainstalowany program Visual Studio.<br /><br /> Ta właściwość zawiera wersja docelowa programu Visual Studio, która może się różnić który hosta programu Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v110`, **$(vsinstalldir) —** zawiera ścieżkę do instalacji programu Visual Studio 2012.|  
|**$(Vcinstalldir) —**|Katalog, w którym jest zainstalowany program Visual C++.<br /><br /> Ta właściwość zawiera wersję docelowej Visual C++, która może się różnić który hosta programu Visual Studio. Na przykład podczas kompilowania z `$(PlatformToolset) = v140`, **$(vcinstalldir) —** zawiera ścieżkę do instalacji programu Visual C++ 2015.|  
|**$(Frameworkdir) —**|Katalog, w którym został zainstalowany program .NET Framework.|  
|**$(Frameworkversion) —**|Wersja programu .NET Framework, używany przez Visual Studio. Połączone z **$(frameworkdir) —**, pełną ścieżkę do wersji programu .NET Framework korzystanie przez program Visual Studio.|  
|**$(Frameworksdkdir) —**|Katalog, w którym jest zainstalowany system .NET Framework. .NET Framework można zainstalować jako część programu Visual Studio lub oddzielnie.|  
|**$(Webdeploypath) —**|Ścieżka względna z katalogu głównego wdrożenia sieci web do których danych wyjściowych projektu należy. Zwraca taką samą wartość jak <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>.|  
|**$(Webdeployroot) —**|Ścieżka bezwzględna do lokalizacji  **\<localhost >**. Na przykład c:\inetpub\wwwroot.|  
|**$(SafeParentName)**|(Przestarzałe). Nazwa natychmiastowego elementu nadrzędnego w formacie prawidłową nazwę. Na przykład formularz jest elementem nadrzędnym pliku .resx.|  
|**$(SafeInputName)**|(Przestarzałe). Nazwa pliku jako prawidłową nazwą klasy, minus rozszerzenie pliku.|  
|**$(Saferootnamespace) —**|(Przestarzałe). Nazwa przestrzeni nazw, w którym kreatorów projekt doda kodu. Ta nazwa przestrzeni nazw będzie zawierać tylko znaki, które mogą być dozwolone w prawidłowego identyfikatora C++.|  
|**$(Fxcopdir) —**|Ścieżka do pliku fxcop.cmd. Plik fxcop.cmd nie jest zainstalowany we wszystkich wersjach Visual C++.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie projektów C++ w Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)