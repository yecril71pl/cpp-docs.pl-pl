---
title: "Ogólna strona właściwości (projekt) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
dev_langs: C++
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbe19414dbbe664f15ea2bbbc35a26827ac5b831
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="general-property-page-project"></a>Ogólna strona właściwości (projekt)

Kiedy kliknij prawym przyciskiem myszy w węźle projekt w Eksploratorze rozwiązań i wybierz **właściwości**, **ogólne** strony właściwości w obszarze **właściwości konfiguracji** w węźle w okienku po lewej stronie zawiera dwie sekcje właściwości:

- Ogólne

- Domyślne ustawienia projektu

Dla projektów z systemem innym niż Windows, temacie [odwołania do strony właściwości C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="general"></a>Ogólne

Właściwości w sekcji Ogólne wpływ na lokalizację plików, które są tworzone w procesie kompilacji i plików, których można usunąć, kiedy **wyczyść** opcji (**kompilacji** menu) jest zaznaczone.

**Platforma docelowa**  
Określa platformę uruchamianego projektu. Na przykład Windows, Android lub iOS. Wartość **systemu Windows 10** oznacza, że elementy docelowe projektu platformy uniwersalnej systemu Windows. Jeśli ma być przeznaczona dla wcześniejszych wersji systemu Windows, nie ma wersji i wartość w tym polu jest wyświetlana jako tylko **Windows**. To pole tylko do odczytu, który jest ustawiana podczas tworzenia projektu.

**Wersja zestawu SDK systemu Windows**  
Dla platformy docelowej systemu Windows określa wersję zestawu Windows SDK, który projekt wymaga. Po zainstalowaniu obciążenia C++ za pomocą Instalatora programu Visual Studio instalowane są również wymagane części zestawu Windows SDK. Jeśli masz inne wersje zestawu SDK systemu Windows na komputerze, na liście rozwijanej pojawi się każdej wersji narzędzia zestawu SDK, które zostały zainstalowane.

Pod kątem systemu Windows 7 lub Windows Vista, należy użyć wartości **8.1**, ponieważ system Windows 8.1 SDK jest zgodne z tymi platformami. Ponadto należy zdefiniować odpowiednią wartość dla **_WIN32_WINNT** w targetver.h. W systemie Windows 7, który jest 0x0601. Zobacz [modyfikowanie symboli WINVER i _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Można zainstalować zestawu narzędzi platformy systemu Windows XP, które zostały uwzględnione w Visual Studio, aby użyć bieżącej wersji biblioteki do kompilacji projektów systemu Windows XP i Windows 2003 Server. Aby uzyskać informacje na temat sposobu uzyskiwania i używania tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](../build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmieniania zestaw narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Min platformy docelowej. Wersja**  
Określa Najniższa wersja platformy, które projektu może być uruchamiane. Ta właściwość jest wyświetlana tylko wtedy, gdy typ projektu obsługuje, takimi jak w projektów uniwersalnych systemu Windows. Jeśli aplikację można korzystać z funkcji w nowszej wersji zestawu Windows SDK, ale mogą nadal działać w starszych wersjach bez tych funkcji, prawdopodobnie z utratę funkcjonalności, następnie wartość te dwie właściwości może być różne. Jeśli tak, kod należy sprawdzić wersję platformy działa względem w czasie wykonywania i nie spróbuj użyć funkcji, które nie są dostępne w starszej wersji platformy.

Należy pamiętać, że Visual C++ nie obsługuje wymuszania tej opcji. Jest on uwzględniony w spójności z innymi językami, takich jak C# i JavaScript, a jako przewodnik dla każdego, kto korzysta z projektu. Visual C++ nie generuje błąd w przypadku należy użyć funkcji, która nie jest dostępna w minimalnej wersji.

**Katalog wyjściowy**  
Określa katalog, w którym narzędzi, takich jak konsolidator umieści wszystkie pliki ostateczne dane wyjściowe, które są tworzone podczas procesu kompilacji. Zazwyczaj zawiera dane wyjściowe narzędzia, takie jak łączenie, bibliotekarza lub BSCMake. Domyślnie ta właściwość jest katalogu określonego przez makra $(solutiondir —) $(Konfiguracja) \.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

**Katalog pośredni**  
Określa katalog, w którym narzędzi, takich jak kompilator spowoduje umieszczenie wszystkich plików pośrednich utworzony podczas procesu kompilacji. Zazwyczaj zawiera dane wyjściowe narzędzia, takie jak kompilatora C/C++, MIDL i kompilator zasobów. Domyślnie ta właściwość jest katalogu określonego przez makra $(Konfiguracja) \.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

**Nazwa docelowa**  
Określa nazwę pliku, który generuje tego projektu. Domyślnie ta właściwość jest nazwa pliku określona przez makra $(ProjectName).

**Rozszerzenie docelowego**  
Określa rozszerzenie nazwy pliku, który generuje ten projekt; na przykład .exe lub .dll.

**Rozszerzenia do usunięcia podczas oczyszczania**  
**Wyczyść** opcji (**kompilacji** menu) usunie pliki z katalogu pośrednim, gdzie jest wbudowana konfigurację projektu. Pliki z rozszerzeniami określony za pomocą tej właściwości zostaną usunięte, gdy **wyczyść** zostanie uruchomione lub po wykonaniu odbudowie. Oprócz plików te rozszerzenia w katalogu pośrednim system kompilacji spowoduje również usunięcie żadnych znanych danych wyjściowych kompilacji niezależnie od tego, gdzie jest zlokalizowany (w tym pośredniego wyjścia, takich jak pliki .obj). Należy pamiętać, że można określić symboli wieloznacznych.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

**Tworzenie pliku dziennika**  
Służy do określenia innej niż domyślna lokalizację pliku dziennika, który jest tworzony, gdy w przypadku kompilowania projektu. Domyślna lokalizacja jest określana przez log (MSBuildProjectName) $ $(intdir —) makra.

Aby zmienić lokalizację katalogu, można użyć makra projektu. Zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).

**Zestaw narzędzi platformy**  
Umożliwia projekt pod kątem innej wersji kompilatora i bibliotek języka Visual C++. Projekty Visual C++ celem może być albo domyślny zestaw narzędzi instalowanych przez program Visual Studio lub jeden z procesami zainstalowane przez kilka poprzednie wersje programu Visual Studio, w tym procesami, które tworzenia plików wykonywalnych, które można uruchomić w systemie Windowx XP. Informacje na temat zmieniania zestaw narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

**Włącz zarządzane kompilacje wzrostowe**  
W przypadku projektów zarządzanych umożliwia wykrywania widoczności zewnętrznych podczas generowania zestawy. Jeśli zmiana zarządzanego projektu nie jest widoczny dla innych projektów, projektów zależnych nie zostały odbudowane. Może to znacznie zwiększyć czas kompilacji w rozwiązaniach, które obejmują projektów zarządzanych.

## <a name="project-defaults"></a>Domyślne ustawienia projektu

Właściwości w sekcji projektu domyślnego reprezentują właściwości domyślnych, które można modyfikować. Definicji tych właściwości można znaleźć w plikach .props w *katalog instalacyjny*\VC\VCProjectDefaults.

**Typ konfiguracji**  
Istnieją różne typy konfiguracji do wyboru:

- **Aplikacji (.exe)**, wyświetla narzędzi konsolidatora (kompilator C/C++, MIDL, kompilator zasobów, konsolidatora, BSCMake, Generator Proxy usługi sieci Web XML, niestandardowej kompilacji, prebuild, prelink, postbuild zdarzeń).

- **Dynamiczna Biblioteka (dll)**, wyświetla zestaw narzędzi konsolidatora określa — opcja konsolidatora/dll i dodaje _WINDLL zdefiniować CL.

- **Pliku reguł programu make**, wyświetla pliku reguł programu make zestaw narzędzi (NMake).

- **Biblioteka statyczna (lib)**, wyświetla narzędzia bibliotekarza, (tak samo, jak zestaw narzędzi konsolidatora, z wyjątkiem podstawić bibliotekarza konsolidatora i pominąć Generator Proxy usługi sieci Web XML).

- **Narzędzie**, wyświetla narzędzie toolset (MIDL, niestandardowej kompilacji, prebuild, postbuild zdarzeń).

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

**Korzystanie z MFC**  
Określa, czy projektu MFC będzie statycznie lub dynamicznie link do biblioteki MFC DLL. Projekty MFC nie można wybrać **Użyj standardowych bibliotek Windows** do odesłania do różnych biblioteki Win32, które są dołączone, korzystając z MFC.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

**Stosowanie ATL**  
Określa, czy Projekt ATL będzie statycznie lub dynamicznie łącze do ATL. BIBLIOTEKI DLL. Jeśli określisz cokolwiek innego niż **nie przy użyciu ATL**, zdefiniuj zostanie dodany do kompilatora **wiersza polecenia** strony właściwości.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.

**Zestaw znaków**  
Określa, czy _unicode — lub _MBCS powinien być ustawiony. Odpowiednim również wpływa na konsolidatora punktu wejścia.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

**Obsługa aparatu plików wykonywalnych języka wspólnego**  
Powoduje, że [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora do użycia.

Do uzyskania programowego dostępu do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

**.NET Framework w wersji docelowej**  
W projektach zarządzanych określa wersji programu .NET framework do obiektu docelowego.

**Optymalizacja całego programu**  
Określa [/GL](../build/reference/gl-whole-program-optimization.md) — opcja kompilatora i [opcję/LTCG](../build/reference/ltcg-link-time-code-generation.md) — opcja konsolidatora. Domyślnie to jest wyłączone dla konfiguracji debugowania i włączony w przypadku konfiguracji sieci sprzedaży.

**Obsługa aplikacji ze Sklepu Windows**  
Określa, czy ten projekt obsługuje aplikacje ze Sklepu Windows. Aby uzyskać więcej informacji, zobacz [/ZW (kompilacja środowiska uruchomieniowego systemu Windows)](../build/reference/zw-windows-runtime-compilation.md)i Centrum deweloperów systemu Windows.

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../ide/property-pages-visual-cpp.md)  