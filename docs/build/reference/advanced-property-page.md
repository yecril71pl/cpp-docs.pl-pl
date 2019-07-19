---
title: Zaawansowana Strona właściwości (projekt)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315520"
---
# <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

Strona właściwości zaawansowane jest dostępna w programie Visual Studio 2019 i nowszych.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Właściwości zaawansowane

- **Rozszerzenie pliku docelowego**

   Określa rozszerzenie pliku do użycia dla danych wyjściowych kompilacji. Domyślna wartość **. exe** dla aplikacji, **lib** dla bibliotek statycznych i **dll** dla bibliotek DLL.

- **Rozszerzenia do usunięcia podczas czyszczenia**

   Opcja **Oczyść** (menu**kompilacja** ) usuwa pliki z katalogu pośredniego, w którym jest skompilowana Konfiguracja projektu. Pliki z rozszerzeniami określonymi za pomocą tej właściwości zostaną usunięte po uruchomieniu **czyszczenia** lub po wykonaniu odbudowy. Oprócz plików tych rozszerzeń w katalogu pośrednim, system kompilacji również usunie wszystkie znane dane wyjściowe kompilacji, bez względu na to, gdzie się znajdują (włącznie z wynikami pośrednimi, takimi jak pliki. obj). Należy pamiętać, że można określić symbole wieloznaczne.

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>, zobacz.

- **Plik dziennika kompilacji**

   Umożliwia określenie lokalizacji innej niż domyślna dla pliku dziennika, który jest tworzony za każdym razem, gdy kompilujesz projekt. Lokalizacja domyślna jest określana przez makra $ (IntDir) $ (MSBuildProjectName). log.

   Za pomocą makr projektu można zmienić lokalizację katalogu. Zobacz [typowe makra dotyczące poleceń i właściwości kompilacji](common-macros-for-build-commands-and-properties.md).

- **Preferowana architektura narzędzia kompilacji**

   Określa, czy mają być używane narzędzia kompilacji x86 i x64.

- **Użyj bibliotek debugowania**

   Określa, czy ma zostać utworzona kompilacja lub wersja kompilacji.

- **Włącz kompilację aparatu Unity (duża)**

   Włącza proces kompilacji, w którym C++ wiele plików źródłowych jest połączonych w jeden lub więcej plików "Unity" przed kompilacją w celu zwiększenia wydajności kompilacji. Niezwiązane z aparatem gier aparatu Unity.

- **Użycie MFC**

   Określa, czy projekt MFC będzie statycznie czy dynamicznie połączony z biblioteką MFC DLL. Projekty inne niż MFC mogą wybrać **Używanie standardowych bibliotek systemu Windows** do łączenia z różnymi bibliotekami Win32, które są uwzględnione w przypadku używania MFC.

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>, zobacz.

- **Zestaw znaków**

   Określa, czy należy ustawić _UNICODE lub _MBCS. Ma także wpływ na punkt wejścia konsolidatora, gdy jest to konieczne.

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>, zobacz.

- **Optymalizacja całego programu**

   Określa opcję kompilatora [/GL](gl-whole-program-optimization.md) i opcję konsolidatora [/LTCG](ltcg-link-time-code-generation.md) . Domyślnie to ustawienie jest wyłączone dla konfiguracji debugowania i włączone dla konfiguracji detalicznych.

- **Wersja zestawu narzędzi MSVC**

   Określa pełną wersję zestawu narzędzi MSVC, który zostanie użyty do skompilowania projektu. Jeśli masz zainstalowaną różne wersje aktualizacji i wersji zapoznawczej zestawu narzędzi, możesz określić, który z nich ma być używany w tym miejscu.

## <a name="ccli-properties"></a>C++Właściwości/CLI

- **Obsługa środowiska uruchomieniowego CLR**

   Powoduje, że opcja kompilatora [/CLR](clr-common-language-runtime-compilation.md) ma być używana.

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>, zobacz.

- **Wersja platformy docelowej platformy .NET**

   W obszarze projekty zarządzane określa wersję programu .NET Framework, która ma być docelowa.

- **Włącz zarządzaną kompilację przyrostową**

   W przypadku projektów zarządzanych pozwala to wykrywać widoczność zewnętrzną podczas generowania zestawów. Jeśli zmiana w projekcie zarządzanym nie jest widoczna dla innych projektów, projekty zależne nie są odbudowane. Może to znacznie poprawić czasy kompilacji w rozwiązaniach, które obejmują projekty zarządzane.

::: moniker-end
