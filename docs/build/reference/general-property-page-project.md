---
title: Ogólna strona właściwości (projekt)
ms.date: 07/17/2019
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
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: bb301f63bfd1e6839d7893cdc03d61e021409666
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500068"
---
# <a name="general-property-page-project"></a>Ogólna strona właściwości (projekt)

::: moniker range=">=vs-2019"

Ten temat dotyczy projektów programu Visual Studio dla systemu Windows. W przypadku projektów systemu Linux zapoznaj się z informacjami na [stronie właściwości systemu Linux C++](../../linux/prop-pages-linux.md). W przypadku projektów CMake zobacz [CMAKE projects w programie Visual Studio](../cmake-projects-in-visual-studio.md). W przypadku projektów systemu Android zobacz [Ogólne właściwości projektu (Android C++)](../../cross-platform/general-android-prop-page.md). W przypadku projektów programu make dla systemu Android zobacz [Ogólne właściwości projektu (plik reguł programu make dla systemu Android C++)](../../cross-platform/general-makefile-android-prop-page.md)

Po kliknięciu prawym przyciskiem myszy węzła projektu w Eksplorator rozwiązań i wybraniu **Właściwości**, na stronie właściwości **Ogólne** w węźle **Właściwości konfiguracji** w lewym okienku zostaną wyświetlone następujące właściwości:

- **Katalog wyjściowy**

   Określa katalog, w którym narzędzia takie jak konsolidator umieści wszystkie Finalne pliki wyjściowe, które są tworzone podczas procesu kompilacji. Zazwyczaj obejmuje to wyjście narzędzi, takie jak konsolidator, bibliotekarza lub BSCMake. Domyślnie ta właściwość jest katalogiem określonym przez makra $ (SolutionDir) $ (Configuration) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A> .

- **Katalog pośredni**

   Określa katalog, w którym narzędzia takie jak kompilator umieści wszystkie pliki pośrednie utworzone podczas procesu kompilacji. Zazwyczaj obejmuje to wyjście narzędzi, takie jak kompilator C/C++, MIDL i kompilator zasobów. Domyślnie ta właściwość jest katalogiem określonym przez makro $ (Configuration) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A> .

- **Nazwa obiektu docelowego**

   Określa nazwę pliku, który generuje ten projekt. Domyślnie ta właściwość jest nazwą pliku określoną przez makro $ (ProjectName).

- **Typ konfiguracji**

  Istnieje kilka typów konfiguracji, spośród których można wybrać:

  - **Aplikacja (. exe)**

     Wyświetla zestaw narzędzi konsolidatora (kompilator C/C++, MIDL, kompilator zasobów, konsolidator, BSCMake, generator proxy usługi sieci Web XML, kompilacja niestandardowa, prebuild, prelink, zdarzenia postbuild).

  - **Biblioteka dynamiczna (. dll)**

     Wyświetla zestaw narzędzi konsolidatora, określa opcję konsolidatora/DLL i dodaje _WINDLL definiuje do CL.

  - **Make**

     Wyświetla zestaw narzędzi programu make (NMake).

  - **Biblioteka statyczna (. lib)**

     Wyświetla zestaw narzędzi bibliotekarza (taki sam jak zestaw narzędzi konsolidatora, z wyjątkiem zamiennika bibliotekarza dla konsolidatora i pomijania generatora proxy usługi sieci Web XML).

  - **Narzędzie**

     Wyświetla zestaw narzędzi Narzędzia (MIDL, kompilacja niestandardowa, prekompilacja, zdarzenia postbuild).

  Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A> .

- **Wersja Windows SDK**

   W przypadku platformy docelowej systemu Windows określa wersję Windows SDK wymaganą przez projekt. Podczas instalowania obciążenia języka C++ przy użyciu Instalatora programu Visual Studio wymagane są także zainstalowane części Windows SDK. Jeśli na komputerze znajduje się inna wersja Windows SDK, na liście rozwijanej są wyświetlane wszystkie zainstalowane narzędzia zestawu SDK.

   Aby przejść do systemu Windows 7 lub Windows Vista, użyj wartości **8,1**, ponieważ Windows SDK 8,1 jest zgodny z tymi platformami. Ponadto należy zdefiniować odpowiednią wartość dla **_WIN32_WINNT** w targetver. h. W przypadku systemu Windows 7 to 0x0601. Zobacz [Modyfikowanie winver i _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Możesz zainstalować zestaw narzędzi platformy systemu Windows XP dołączony do programu Visual Studio, aby użyć bieżącej wersji bibliotek do kompilowania projektów systemu Windows XP i Windows 2003 Server. Aby uzyskać informacje na temat uzyskiwania i używania tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](../configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmiany zestawu narzędzi platformy, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Zestaw narzędzi platformy**

   Zezwala, aby projekt był przeznaczony dla innej wersji bibliotek Visual C++ i kompilatora. Projekty Visual Studio C++ mogą wskazywać domyślny zestaw narzędzi instalowany przez program Visual Studio lub jeden z zestawów narzędzi zainstalowanych przez kilka wcześniejszych wersji programu Visual Studio, w tym zestawów narzędzi, które tworzą pliki wykonywalne, które można uruchomić w systemie Windows XP. Aby uzyskać informacje na temat zmiany zestawu narzędzi platformy, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Standard języka C++**

   Określa standard języka, który ma być używany. Wartość domyślna to/std: c++ 14. Określ/std: c++ 17, aby użyć funkcji C++ 17 lub/std: c++ + Najnowsza, aby użyć języka C++ 20 lub innych funkcji eksperymentalnych. Aby uzyskać więcej informacji, zobacz [/STD (Określ wersję standardu języka)](std-specify-language-standard-version.md)

::: moniker-end

::: moniker range="<=vs-2017"

W programie Visual Studio 2015 i Visual Studio 2017 po kliknięciu prawym przyciskiem myszy węzła projektu w **Eksplorator rozwiązań**, a następnie wybraniu **Właściwości**, na stronie właściwości **Ogólne** w węźle **Właściwości konfiguracji** w lewym okienku są wyświetlane dwie sekcje właściwości:

- Ogólne

- Wartości domyślne projektu

## <a name="general"></a>Ogólne

- **Platforma docelowa**

   Określa platformę, na której będzie wykonywany projekt. Na przykład Windows, Android lub iOS. Wartość **Windows 10** oznacza, że projekt jest przeznaczony dla platforma uniwersalna systemu Windows. Jeśli chcesz uzyskać dostęp do wcześniejszych wersji systemu Windows, wersja nie jest wyświetlana, a wartość w tym polu jest wyświetlana jako tylko **Windows**. Jest to pole tylko do odczytu, które jest ustawiane podczas tworzenia projektu.

- **Wersja platformy docelowej (Visual Studio 2015)**

   Określa najniższą wersję platformy, na której można uruchomić projekt. Ta właściwość jest wyświetlana tylko wtedy, gdy jest ona obsługiwana przez typ projektu. Jeśli Twoja aplikacja może korzystać z funkcji w nowszej wersji Windows SDK, ale nadal można uruchamiać ją we wcześniejszych wersjach bez tych funkcji, na przykład w przypadku utraty funkcjonalności, wartość tych dwóch właściwości może się różnić. Jeśli tak, kod powinien sprawdzić wersję platformy, w której działa, w czasie wykonywania, a nie próbować korzystać z funkcji, które nie są dostępne w starszej wersji platformy.

   System projektu C++ nie wymusza tej opcji. Jest on uwzględniany w celu zapewnienia spójności z innymi językami, takimi jak C# i JavaScript, oraz jako przewodnik dla każdej osoby, która używa Twojego projektu. Visual C++ nie wygeneruje błędu, jeśli używasz funkcji, która nie jest dostępna w minimalnej wersji.

- **Wersja Windows SDK (Visual Studio 2017)**

   W przypadku platformy docelowej systemu Windows określa wersję Windows SDK wymaganą przez projekt. Podczas instalowania obciążenia języka C++ przy użyciu Instalatora programu Visual Studio wymagane są także zainstalowane części Windows SDK. Jeśli na komputerze znajduje się inna wersja Windows SDK, na liście rozwijanej są wyświetlane wszystkie zainstalowane narzędzia zestawu SDK.

   Aby przejść do systemu Windows 7 lub Windows Vista, użyj wartości **8,1**, ponieważ Windows SDK 8,1 jest zgodny z tymi platformami. Ponadto należy zdefiniować odpowiednią wartość dla **_WIN32_WINNT** w targetver. h. W przypadku systemu Windows 7 to 0x0601. Zobacz [Modyfikowanie winver i _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

   Możesz zainstalować zestaw narzędzi platformy systemu Windows XP dołączony do programu Visual Studio, aby użyć bieżącej wersji bibliotek do kompilowania projektów systemu Windows XP i Windows 2003 Server. Aby uzyskać informacje na temat uzyskiwania i używania tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów dla systemu Windows XP](../configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat zmiany zestawu narzędzi platformy, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Katalog wyjściowy**

   Określa katalog, w którym narzędzia takie jak konsolidator umieści wszystkie Finalne pliki wyjściowe, które są tworzone podczas procesu kompilacji. Zazwyczaj obejmuje to wyjście narzędzi, takie jak konsolidator, bibliotekarza lub BSCMake. Domyślnie ta właściwość jest katalogiem określonym przez makra $ (SolutionDir) $ (Configuration) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A> .

- **Katalog pośredni**

   Określa katalog, w którym narzędzia takie jak kompilator umieści wszystkie pliki pośrednie utworzone podczas procesu kompilacji. Zazwyczaj obejmuje to wyjście narzędzi, takie jak kompilator C/C++, MIDL i kompilator zasobów. Domyślnie ta właściwość jest katalogiem określonym przez makro $ (Configuration) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A> .

- **Nazwa obiektu docelowego**

   Określa nazwę pliku, który generuje ten projekt. Domyślnie ta właściwość jest nazwą pliku określoną przez makro $ (ProjectName).

- **Rozszerzenie docelowe**

   Określa rozszerzenie nazwy pliku, które generuje ten projekt; na przykład. exe lub. dll.

- **Rozszerzenia do usunięcia podczas czyszczenia**

   Opcja **Oczyść** (menu**kompilacja** ) usuwa pliki z katalogu pośredniego, w którym jest skompilowana Konfiguracja projektu. Pliki z rozszerzeniami określonymi za pomocą tej właściwości zostaną usunięte po uruchomieniu **czyszczenia** lub po wykonaniu odbudowy. Oprócz plików tych rozszerzeń w katalogu pośrednim, system kompilacji również usunie wszystkie znane dane wyjściowe kompilacji, bez względu na to, gdzie się znajdują (włącznie z wynikami pośrednimi, takimi jak pliki. obj). Należy pamiętać, że można określić symbole wieloznaczne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A> .

- **Plik dziennika kompilacji**

   Umożliwia określenie lokalizacji innej niż domyślna dla pliku dziennika, który jest tworzony za każdym razem, gdy kompilujesz projekt. Lokalizacja domyślna jest określana przez makra $ (IntDir) $ (MSBuildProjectName). log.

   Za pomocą makr projektu można zmienić lokalizację katalogu. Zobacz [typowe makra dotyczące poleceń i właściwości kompilacji](common-macros-for-build-commands-and-properties.md).

- **Zestaw narzędzi platformy**

   Zezwala, aby projekt był przeznaczony dla innej wersji bibliotek Visual C++ i kompilatora. Projekty Visual Studio C++ mogą wskazywać domyślny zestaw narzędzi instalowany przez program Visual Studio lub jeden z zestawów narzędzi zainstalowanych przez kilka wcześniejszych wersji programu Visual Studio, w tym zestawów narzędzi, które tworzą pliki wykonywalne, które można uruchomić w systemie Windows XP. Aby uzyskać informacje na temat zmiany zestawu narzędzi platformy, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Włącz zarządzaną kompilację przyrostową**

   W przypadku projektów zarządzanych pozwala to wykrywać widoczność zewnętrzną podczas generowania zestawów. Jeśli zmiana w projekcie zarządzanym nie jest widoczna dla innych projektów, projekty zależne nie są odbudowane. Może to znacznie poprawić czasy kompilacji w rozwiązaniach, które obejmują projekty zarządzane.

## <a name="project-defaults"></a>Wartości domyślne projektu

Właściwości w sekcji domyślnej projektu reprezentują domyślne właściwości, które można modyfikować. Definicję tych właściwości można znaleźć w plikach. props w *katalogu instalacyjnym*\VC\VCProjectDefaults.

- **Typ konfiguracji**

  Istnieje kilka typów konfiguracji, spośród których można wybrać:

  - **Aplikacja (. exe)**

     Wyświetla zestaw narzędzi konsolidatora (kompilator C/C++, MIDL, kompilator zasobów, konsolidator, BSCMake, generator proxy usługi sieci Web XML, kompilacja niestandardowa, prebuild, prelink, zdarzenia postbuild).

  - **Biblioteka dynamiczna (. dll)**

     Wyświetla zestaw narzędzi konsolidatora, określa opcję konsolidatora/DLL i dodaje _WINDLL definiuje do CL.

  - **Make**

     Wyświetla zestaw narzędzi programu make (NMake).

  - **Biblioteka statyczna (. lib)**

     Wyświetla zestaw narzędzi bibliotekarza (taki sam jak zestaw narzędzi konsolidatora, z wyjątkiem zamiennika bibliotekarza dla konsolidatora i pomijania generatora proxy usługi sieci Web XML).

  - **Narzędzie**

     Wyświetla zestaw narzędzi Narzędzia (MIDL, kompilacja niestandardowa, prekompilacja, zdarzenia postbuild).

  Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A> .

- **Użycie MFC**

   Określa, czy projekt MFC będzie statycznie czy dynamicznie połączony z biblioteką MFC DLL. Projekty inne niż MFC mogą wybrać **Używanie standardowych bibliotek systemu Windows** do łączenia z różnymi bibliotekami Win32, które są uwzględnione w przypadku używania MFC.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A> .

- **Zestaw znaków**

   Określa, czy należy ustawić _UNICODE lub _MBCS. Ma także wpływ na punkt wejścia konsolidatora, gdy jest to konieczne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A> .

- **Obsługa środowiska uruchomieniowego CLR**

   Powoduje, że opcja kompilatora [/CLR](clr-common-language-runtime-compilation.md) ma być używana.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A> .

- **Wersja platformy docelowej platformy .NET**

   W obszarze projekty zarządzane określa wersję programu .NET Framework, która ma być docelowa.

- **Optymalizacja całego programu**

   Określa opcję kompilatora [/GL](gl-whole-program-optimization.md) i opcję konsolidatora [/LTCG](ltcg-link-time-code-generation.md) . Domyślnie to ustawienie jest wyłączone dla konfiguracji debugowania i włączone dla konfiguracji detalicznych.

- **Obsługa aplikacji ze sklepu Windows**

   Określa, czy ten projekt obsługuje aplikacje środowisko wykonawcze systemu Windows (platforma uniwersalna systemu Windows). Aby uzyskać więcej informacji, zobacz [/zw (kompilacja środowisko wykonawcze systemu Windows)](zw-windows-runtime-compilation.md)i centrum deweloperów systemu Windows.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Odwołanie do strony właściwości projektu C++](property-pages-visual-cpp.md)
