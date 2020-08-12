---
title: Zaawansowana Strona właściwości (projekt)
ms.date: 08/10/2020
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 3d6694e44d3da4023998a0335cd06c85b353b2b1
ms.sourcegitcommit: 8140647370017b885432349ce89f187c3068b46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144168"
---
# <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

::: moniker range="<=vs-2017"

Strona właściwości zaawansowane jest dostępna w programie Visual Studio 2019 i nowszych. Aby zapoznać się z dokumentacją tej wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range="vs-2019"

Strona właściwości zaawansowane jest dostępna w programie Visual Studio 2019 i nowszych.

## <a name="advanced-properties"></a>Właściwości zaawansowane

- **Rozszerzenie pliku docelowego**

   Określa rozszerzenie pliku do użycia dla danych wyjściowych kompilacji. Domyślnie *`.exe`* dla aplikacji, *`.lib`* bibliotek statycznych i *`.dll`* bibliotek DLL.

- **Rozszerzenia do usunięcia podczas czyszczenia**

   Opcja **Oczyść** (menu**kompilacja** ) usuwa pliki z katalogu pośredniego, w którym jest skompilowana Konfiguracja projektu. Pliki z rozszerzeniami określonymi w tej właściwości zostaną usunięte po uruchomieniu **czyszczenia** lub po odbudowie. System kompilacji usuwa wszystkie pliki, które mają te rozszerzenia w katalogu pośrednim. Usuwa także wszystkie znane dane wyjściowe kompilacji, niezależnie od tego, gdzie się znajdują. (Obejmuje to pośrednie dane wyjściowe, takie jak *`.obj`* pliki). W tej właściwości można określić symbole wieloznaczne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A> .

- **Plik dziennika kompilacji**

   Umożliwia określenie lokalizacji innej niż domyślna dla pliku dziennika, który jest tworzony za każdym razem, gdy kompilujesz projekt. Domyślna lokalizacja jest określana przez makra `$(IntDir)$(MSBuildProjectName).log` .

   Za pomocą makr projektu można zmienić lokalizację katalogu. Zobacz [typowe makra dotyczące poleceń i właściwości kompilacji](common-macros-for-build-commands-and-properties.md).

- **Preferowana architektura narzędzia kompilacji**

   Określa, czy mają być używane narzędzia kompilacji x86 i x64.

- **Użyj bibliotek debugowania**

   Określa, czy ma zostać utworzona kompilacja lub wersja kompilacji.

- **Włącz kompilację aparatu Unity (duża)**

   Włącza szybszy proces kompilacji, który łączy wiele plików źródłowych C++ w jeden lub więcej plików przed kompilacją. Te połączone pliki są znane jako pliki *aparatu Unity* . Są one niepowiązane z aparatem gier aparatu Unity.

- **Kopiuj zawartość do OutDir**

   Skopiuj elementy oznaczone jako *zawartość* w projekcie do katalogu wyjściowego projektu ( `$(OutDir)` ). To ustawienie może uprościć wdrażanie. Ta właściwość jest dostępna od wersji 16,7 programu Visual Studio 2019.

- **Kopiuj odwołania projektu do OutDir**

   Skopiuj plik wykonywalny (DLL i EXE) do katalogu wyjściowego projektu ( `$(OutDir)` ). W projektach C++/CLI ( [`/clr`](clr-common-language-runtime-compilation.md) ) ta właściwość jest ignorowana. Zamiast tego, właściwość **copy Local** w każdym odwołaniu projektu kontroluje, czy jest ona kopiowana do katalogu wyjściowego. To ustawienie może uprościć wdrożenie lokalne. Jest dostępny od wersji 16,7 programu Visual Studio 2019.

- **Kopiuj symbole odwołań projektu do OutDir**

   Skopiuj pliki PDB dla elementów odwołania projektu wraz z elementami wykonywalnymi odwołania projektu do katalogu wyjściowego projektu ( `$(OutDir)` ). Ta właściwość jest zawsze włączona dla projektów C++/CLI. To ustawienie może uprościć wdrożenie debugowania. Jest dostępny od wersji 16,7 programu Visual Studio 2019.

- **Kopiuj środowisko uruchomieniowe języka C++ do OutDir**

   Skopiuj biblioteki DLL środowiska uruchomieniowego do katalogu wyjściowego projektu ( `$(OutDir)` ). To ustawienie może uprościć wdrożenie lokalne. Jest dostępny od wersji 16,7 programu Visual Studio 2019.

- **Użycie MFC**

   Określa, czy projekt MFC statycznie lub dynamicznie łączy się z biblioteką MFC DLL. W projektach bez klas MFC wybierz opcję **Użyj standardowych bibliotek systemu Windows** , aby połączyć biblioteki Win32 dołączone przez MFC.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A> .

- **Zestaw znaków**

   Określa `_UNICODE` , czy `_MBCS` należy ustawić. Ma także wpływ na punkt wejścia konsolidatora, gdy jest to konieczne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A> .

- **Optymalizacja całego programu**

   Określa [`/GL`](gl-whole-program-optimization.md) opcję kompilatora i [`/LTCG`](ltcg-link-time-code-generation.md) opcję konsolidatora. Domyślnie optymalizacja całego programu jest wyłączona dla konfiguracji debugowania i włączona w przypadku konfiguracji wydania.

- **Wersja zestawu narzędzi MSVC**

   Określa pełną wersję zestawu narzędzi MSVC, który jest używany do kompilowania projektu. Być może masz zainstalowaną różne wersje aktualizacji i wersji zapoznawczej zestawu narzędzi. Możesz określić, która z nich ma być używana w tym miejscu.

## <a name="ccli-properties"></a>Właściwości/CLI języka C++

- **Obsługa środowiska uruchomieniowego CLR**

   Powoduje, że [`/clr`](clr-common-language-runtime-compilation.md) Opcja kompilatora ma być używana.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A> .

- **Wersja platformy docelowej platformy .NET**

   W obszarze projekty zarządzane określa wersję programu .NET Framework, która ma być docelowa.

- **Włącz zarządzaną kompilację przyrostową**

   W przypadku projektów zarządzanych ta opcja umożliwia wykrywanie widoczności zewnętrznej podczas generowania zestawów. Jeśli zmiana w projekcie zarządzanym nie jest widoczna dla innych projektów, zależne projekty nie są ponownie kompilowane. Zarządzane Kompilacje przyrostowe mogą znacznie skrócić czasy kompilacji w rozwiązaniach, które obejmują projekty zarządzane.

::: moniker-end
