---
title: Strona właściwości ogólnych (projekt) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6be3ef7609819c34209a9b8959bfd883a836db04
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716359"
---
# <a name="general-property-page-project"></a>Ogólna strona właściwości (projekt)

Gdy kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**, **ogólne** strony właściwości w obszarze **właściwości konfiguracji** węzeł w lewo w okienku wyświetlą się dwie sekcje właściwości:

- Ogólne

- Wartości domyślne projektu

Dla projektów innych niż Windows, zobacz [dokumentacja strony właściwości C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="general"></a>Ogólne

Właściwości w sekcji Ogólne mają wpływ na lokalizację plików, które są tworzone w procesie kompilacji i plików do usunięcia, kiedy **czysty** opcji (**kompilacji** menu) jest zaznaczona.

- **Platforma docelowa**

   Określa platformę, że projekt będzie działać w. Na przykład Windows, Android lub iOS. Wartość **systemu Windows 10** oznacza, że projekt jest ukierunkowany uniwersalnej platformy Windows. Jeśli są przeznaczone dla wcześniejszych wersji systemu Windows, wersja nie ma na liście, a wartość w tym polu jest wyświetlana jako po prostu **Windows**. To pole tylko do odczytu, która jest ustawiana podczas tworzenia projektu.

- **Wersja zestawu Windows SDK**

   Dla platformy docelowej Windows to określa wersję zestawu Windows SDK, którego Twój projekt wymaga. Po zainstalowaniu obciążenia C++ za pomocą Instalatora programu Visual Studio instalowane są również wymagane elementy z zestawu Windows SDK. W przypadku innych wersji zestawu Windows SDK na komputerze, na liście rozwijanej pojawi się każdej wersji narzędzi zestawu SDK, które zostały zainstalowane.

   Aby skierować je do Windows 7 lub Windows Vista, należy użyć wartości **8.1**, ponieważ Windows SDK 8.1 jest zgodne z poprzednimi wersjami dla tych platform. Ponadto należy zdefiniować odpowiednie wartości dla **_WIN32_WINNT** w targetver.h. Windows 7 to 0x0601. Zobacz [modyfikowanie symboli WINVER i _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

   Można zainstalować zestawu narzędzi platformy Windows XP, które zostały zawarte w Visual Studio ma używać bieżącej wersji bibliotek do tworzenia projektów Windows XP i Windows 2003 Server. Aby uzyskać informacje na temat sposobu uzyskania i używania tego zestawu narzędzi platformy, zobacz [Konfigurowanie programów systemu Windows XP](../build/configuring-programs-for-windows-xp.md). Aby uzyskać dodatkowe informacje na temat Zmiana zestawu narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- **Min platformy docelowej. Wersja**

   Określa najniższy numer wersji platformy, który będzie można uruchomić projekt w. Właściwość ta pojawia się tylko wtedy, gdy typ projektu ją obsługuje, takie jak w projektach Windows Universal. Jeśli aplikacja może korzystać z funkcji w nowszej wersji zestawu Windows SDK, ale mogą nadal działać w starszych wersjach bez tych funkcji, być może z pewną utratą funkcjonalności, następnie wartość te dwie właściwości mogą się różnić. Jeśli tak, kod ma wykonywać sprawdzania wersji platformy jest uruchamianiu w czasie wykonywania i próbuj używać funkcji, które nie są dostępne w starszej wersji platformy.

   Należy pamiętać, że Visual C++ nie wymusza tę opcję. Jest uwzględniony w celu zachowania spójności z innymi językami, takich jak C# i JavaScript, a także jako przewodnik dla każdego, kto korzysta z projektu. Visual C++ nie generuje błąd, jeśli używana jest funkcja, która nie jest dostępna w minimalnej wersji.

- **Katalog wyjściowy**

   Określa katalog, w którym narzędzia, takie jak program łączący umieszczą wszystkie końcowe pliki, które są tworzone podczas procesu kompilacji. Zazwyczaj zawiera dane wyjściowe narzędzi, takich jak program łączący, bibliotekarz lub BSCMake. Domyślnie ta właściwość jest katalogu określonego przez $ $(SolutionDir) makra (Konfiguracja) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Katalog pośredni**

   Określa katalog, w którym narzędzia, takie jak kompilator umieszczą wszystkie pośrednie pliki tworzone podczas procesu kompilacji. Zazwyczaj zawiera dane wyjściowe narzędzia, takie jak kompilator C/C++, regiony i kompilator zasobów. Domyślnie ta właściwość jest katalogu określonego przez makra $(Konfiguracja) \.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Nazwa obiektu docelowego**

   Określa nazwę pliku, który generuje ten projekt. Domyślnie ta właściwość jest nazwy pliku określonej przez makra $(nazwa_projektu).

- **Rozszerzenie docelowe**

   Określa rozszerzenie nazwy pliku, który generuje ten projekt; na przykład .exe lub .dll.

- **Rozszerzenia do usunięcia podczas oczyszczania**

   **Czysty** opcji (**kompilacji** menu) powoduje usunięcie plików z katalogu pośredniego, gdzie Konfiguracja projektu jest kompilowana. Pliki z rozszerzeniami określonymi tą właściwością będą usuwane, gdy **czysty** zostanie uruchomione lub podczas wykonywania ponownej kompilacji. Oprócz plików rozszerzeń w katalogu pośrednim system kompilacji usunie także wszelkie znane wyniki kompilacji, niezależnie od tego, gdzie się znajdują (w tym pośrednie dane wyjściowe, takie jak pliki .obj). Należy pamiętać, że można określić symbole wieloznaczne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Plik dziennika kompilacji**

   Umożliwia określenie lokalizacji innej niż domyślna dla pliku dziennika, który jest tworzony przy każdej kompilacji projektu. Domyślna lokalizacja jest określana przez .log$ (MSBuildProjectName) $(IntDir) makra.

   Projektu makra można użyć, aby zmienić lokalizację katalogu. Zobacz [typowe makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).

- **Zestaw narzędzi platformy**

   Zezwala projektowi, aby docelowa była inna wersja bibliotek języka Visual C++ i kompilatora. Projekty języka Visual C++ można kierować albo na domyślny zestaw narzędzi instalowanych przez program Visual Studio lub jeden z zestawów narzędzi instalowane przez kilka poprzednich wersji programu Visual Studio, w tym zestawy narzędzi, które tworzyć pliki wykonywalne, które można uruchamiać na być XP. Informacje dotyczące zmiany zestawu narzędzi platformy, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- **Włącz zarządzane kompilacje wzrostowe**

   Dla projektów zarządzanych umożliwia wykrywanie widoczność zewnętrznych podczas generowania zestawów. Jeśli zmiana zarządzanego projektu nie jest widoczny dla innych projektów, projektów zależnych nie są odbudowane. Może to znacznie poprawić czasy kompilacji w rozwiązaniach, które zawierają projektów zarządzanych.

## <a name="project-defaults"></a>Wartości domyślne projektu

Właściwości w sekcji Projekt domyślny reprezentują domyślne właściwości, które można modyfikować. Definicja tych właściwości można znaleźć w plikach .props w *katalog instalacyjny*\VC\VCProjectDefaults.

- **Typ konfiguracji**

   Istnieje kilka typów konfiguracji do wyboru:

   - **Aplikacja (.exe)**

      Wyświetla zestaw narzędzi konsolidatora (kompilator C/C++, MIDL, kompilator zasobów, konsolidator, BSCMake, Generator serwera Proxy usługi sieci Web XML, niestandardowej kompilacji, wydarzenia przedkompilacyjne, wydarzenie i postkompilacyjne).

   - **Biblioteka dynamiczna (dll)**
   
      Wyświetla zestaw narzędzi konsolidatora, określa opcję konsolidatora/dll i dodaje _windll, aby zdefiniować CL.

   - **Plik reguł programu make**

      Wyświetla zestaw narzędzi pliku reguł programu make (NMake).

   - **Biblioteka statyczna (lib)**

      Wyświetla zestaw narzędzi bibliotekarza (taki sam, jak zestaw narzędzi konsolidatora, z wyjątkiem podstawenia bibliotekarza na konsolidatora i pominięcia generatora serwera Proxy usługi sieci Web XML).

   - **Narzędzie**
   
      Wyświetla zestaw narzędzi (MIDL, niestandardowej kompilacji, wydarzenia przedkompilacyjne i postkompilacyjne).

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Użycie MFC**

   Określa, czy projekt MFC statycznie lub dynamicznie połączy się z MFC.dll. Projekty inne niż MFC mogą wybrać **Użyj standardowych bibliotek Windows** do łączenia różnych bibliotek Win32, które są uwzględniane przy użyciu klas MFC.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Użycie ATL**

   Określa, czy Projekt ATL statycznie lub dynamicznie połączy się ATL. BIBLIOTEKI DLL. Jeśli określisz nic innego niż **nie używa ATL**, określenie zostanie dodane w kompilatorze **wiersza polecenia** stronę właściwości.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.

- **Zestaw znaków**

   Określa, czy powinny być ustawione _UNICODE lub _MBCS. Wpływa również na punkt wejścia konsolidatora gdzie stosowne.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Obsługa środowiska uruchomieniowego języka wspólnego**

   Powoduje, że [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora ma być używany.

   Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **.NET Framework w wersji docelowej**

   W projektach zarządzanych określa wersji programu .NET framework do obiektu docelowego.

- **Optymalizacja całego programu**

   Określa [/GL](../build/reference/gl-whole-program-optimization.md) — opcja kompilatora i [opcję/LTCG](../build/reference/ltcg-link-time-code-generation.md) — opcja konsolidatora. Domyślnie to jest wyłączone dla konfiguracji debugowania i włączone w przypadku konfiguracji sieci sprzedaży.

- **Obsługa aplikacji Windows Store**

   Określa, czy ten projekt obsługuje aplikacje Windows Runtime (Universal Windows Platform). Aby uzyskać więcej informacji, zobacz [/ZW (kompilacja środowiska uruchomieniowego Windows)](../build/reference/zw-windows-runtime-compilation.md)and Windows Developer Center.

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../ide/property-pages-visual-cpp.md)  