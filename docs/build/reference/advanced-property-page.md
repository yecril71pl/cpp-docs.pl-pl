---
title: Strona właściwości zaawansowanej (projekt)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328424"
---
# <a name="advanced-property-page"></a>Strona właściwości zaawansowanej

Strona Właściwości Zaawansowane jest dostępna w programie Visual Studio 2019 i nowszych.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Właściwości zaawansowane

- **Rozszerzenie pliku docelowego**

   Określa rozszerzenie pliku, które ma być używane dla danych wyjściowych kompilacji. Domyślnie wartość **.exe** dla aplikacji, **.lib** dla bibliotek statycznych i biblioteka **DLL** dla bibliotek DLL.

- **Rozszerzenia do usunięcia przy czyszczeniu**

   Opcja **Wyczyść** (menu**Kompilacja)** usuwa pliki z katalogu pośredniego, w którym jest zbudowana konfiguracja projektu. Pliki z rozszerzeniami określonymi za pomocą tej właściwości zostaną usunięte po uruchomieniu **clean** lub podczas wykonywania przebudowy. Oprócz plików tych rozszerzeń w katalogu pośrednim, system kompilacji usunie również wszystkie znane dane wyjściowe kompilacji, niezależnie od tego, gdzie się znajduje (w tym pośrednie wyjścia, takie jak pliki obj). Należy zauważyć, że można określić symbole wieloznaczne.

   Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>do tej właściwości, zobacz .

- **Tworzenie pliku dziennika**

   Umożliwia określenie lokalizacji nie domyślnej dla pliku dziennika, który jest tworzony przy każdym tworzeniu projektu. Domyślna lokalizacja jest określona przez makra $(IntDir)$(MSBuildProjectName).log.

   Za pomocą makr projektu można zmienić lokalizację katalogu. Zobacz [Typowe makra dla poleceń kompilacji i właściwości](common-macros-for-build-commands-and-properties.md).

- **Preferowana architektura narzędzi kompilacji**

   Określa, czy mają być używane narzędzia kompilacji x86 czy x64.

- **Korzystanie z bibliotek debugowania**

   Określa, czy utworzyć kompilację DEBUG lub RELEASE.

- **Włącz kompilację Unity (JUMBO)**

   Umożliwia proces kompilacji, w którym wiele plików źródłowych języka C++ są łączone w jeden lub więcej plików "jedność" przed kompilacji w celu zwiększenia wydajności kompilacji. Niezwiązane z silnikiem gry Unity.

- **Korzystanie z MFC**

   Określa, czy projekt MFC będzie statycznie lub dynamicznie połączyć się z biblioteką DLL MFC. Projekty inne niż MFC można wybrać **użyj standardowych bibliotek systemu Windows,** aby połączyć się z różnymi bibliotekami Win32, które są uwzględniane podczas korzystania z MFC.

   Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>do tej właściwości, zobacz .

- **Zestaw znaków**

   Określa, czy należy ustawić _UNICODE czy _MBCS. W stosownych przypadkach wpływa również na punkt wejścia konsolidatora.

   Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>do tej właściwości, zobacz .

- **Optymalizacja całego programu**

   Określa opcję kompilatora [/GL](gl-whole-program-optimization.md) i opcję konsolidatora [/LTCG.](ltcg-link-time-code-generation.md) Domyślnie jest to wyłączone dla konfiguracji debugowania i włączone dla konfiguracji sieci sprzedaży.

- **Wersja zestawu narzędzi MSVC**

   Określa pełną wersję zestawu narzędzi MSVC, który będzie używany do tworzenia projektu. Jeśli masz zainstalowane różne wersje aktualizacji i wersji zapoznawczej zestawu narzędzi, możesz określić, który z nich ma być używany w tym miejscu.

## <a name="ccli-properties"></a>Właściwości języka C++/CLI

- **Obsługa środowiska wykonawczego języka wspólnego**

   Powoduje, że [opcja kompilatora /clr](clr-common-language-runtime-compilation.md) ma być używana.

   Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>do tej właściwości, zobacz .

- **Wersja docelowej struktury .NET**

   W projektach zarządzanych określa wersję programu .NET framework do docelowej.

- **Włącz zarządzana kompilacja przyrostowa**

   W przypadku projektów zarządzanych umożliwia to wykrywanie widoczności zewnętrznej podczas generowania zestawów. Jeśli zmiana w projekcie zarządzanym nie jest widoczna dla innych projektów, projekty zależne nie są przebudowywane. Może to znacznie skrócić czas kompilacji w rozwiązaniach, które obejmują projekty zarządzane.

::: moniker-end
