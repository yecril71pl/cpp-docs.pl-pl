---
title: "-LTCG (Generowanie łączonych kodów czasowych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs: C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0932ba85a6570e83be655bb3f8f71bdf9726e88e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Generowanie łączonych kodów czasowych)
```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## <a name="remarks"></a>Uwagi  
 : PRZYROSTOWE (opcjonalnie)  
 Określa, że konsolidator dotyczy tylko całego programu optymalizacji lub w czasie konsolidacji generowania kodu (LTCG) zestaw plików objętych edycji, zamiast całego projektu. Domyślnie ta flaga nie jest ustawiona, gdy określono opcję/LTCG, a cały projekt jest połączony za pomocą optymalizacja całego programu.  
  
 : NOSTATUS &#124; : Stan (opcjonalnie)  
 Określa, czy konsolidator wyświetlany jest wskaźnik postępu, pokazujący, jaki procent konsolidacji została ukończona. Domyślnie te informacje o stanie nie jest wyświetlana.  
  
 : Wyłączone (opcjonalnie)  
 Powoduje wyłączenie generowania kodu w czasie konsolidacji. To zachowanie jest taka sama jak gdy nie określono opcję/LTCG z wiersza polecenia.  
  
 : PGINSTRUMENT (opcjonalnie)  
 Ta opcja jest przestarzała. Zamiast tego należy użyć **opcję/LTCG** i **opcji/genprofile** lub **/FASTGENPROFILE** do generowania instrumentowanej kompilacji dla optymalizacji sterowanych profilem.  
  
 Dane, które mają być zbierane z Instrumentacją uruchamia służy do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md). Krótka forma tej opcji jest /LTCG:PGI.  
  
 : PGOPTIMIZE (opcjonalnie)  
 Ta opcja jest przestarzała. Zamiast tego należy użyć **opcję/LTCG** i **/USEPROFILE** do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md). Krótka forma tej opcji jest /LTCG:PGO.  
  
 : PGUPDATE (opcjonalnie)  
 Ta opcja jest przestarzała. Zamiast tego należy użyć **opcję/LTCG** i **/USEPROFILE** do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md). Krótka forma tej opcji jest /LTCG:PGU.  
  
 Opcja opcję/LTCG informuje konsolidator, aby wywołać kompilatora i wykonywać optymalizacji całego programu. Możesz również wykonać do optymalizacji profilowej. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md).  
  
 Z następującymi wyjątkami nie można dodać opcji konsolidatora do PGO kombinację opcję/LTCG i /USEPROFILE, które nie zostały określone w poprzedniej PGO inicjowania kombinacja opcji opcję/LTCG i opcji/genprofile:  
  
-   [/ BASE](../../build/reference/base-base-address.md)  
  
-   [/ FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   / LTCG  
  
-   [/ MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [/ NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [/ OUT](../../build/reference/out-output-file-name.md)  
  
-   [/ PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [/ PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [/ STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 Wszelkie opcje konsolidatora, które zostały określone razem z opcję/LTCG i opcje opcji/genprofile zainicjować PGO nie trzeba określać podczas budowania przy użyciu opcję/LTCG i /USEPROFILE; są one niejawnego.  
  
 Pozostała część tego tematu opisano opcję/LTCG pod względem Generowanie łączonych kodów czasowych.  
  
 / Z technicznego LTCG [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
 Konsolidator wywołuje Generowanie łączonych kodów czasowych, jeśli został przekazany moduł, który został skompilowany przy użyciu **/GL** lub moduł MSIL (zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)). Jeśli nie zostanie jawnie określony **opcję/LTCG** podczas przekazywania **/GL** lub moduł MSIL do konsolidatora, konsolidator ostatecznie wykryje to i uruchamia ponownie łącza za pomocą **opcję/LTCG**. Określ jawnie **opcję/LTCG** podczas przekazywania **/GL** i moduł MSIL do konsolidatora do ewentualnego najszybszym kompilacji wydajności.  
  
 Nawet zwiększyć wydajność, można użyć **opcję/LTCG: PRZYROSTOWE**. Ta opcja nakazuje konsolidatorowi tylko ponownie zoptymalizować zestawu plików, których dotyczy zmiana pliku źródłowego, zamiast całego projektu. To znacznie ograniczyć czas łącza. To nie jest ta sama opcja jako konsolidowania przyrostowego.  
  
 **/ LTCG** nie nadaje się do użytku z [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).  
  
 Gdy **opcję/LTCG** służy do łączenia moduły skompilowane przy użyciu [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), lub [ox](../../build/reference/ox-full-optimization.md), wykonywane są następujące funkcje optymalizacji:  
  
-   Między modułami  
  
-   Alokacja rejestru interprocedural (tylko systemy operacyjne 64-bitowe)  
  
-   Konwencja wywoływania niestandardowych (tylko x86)  
  
-   Mała przemieszczenie TLS (tylko x86)  
  
-   Wyrównanie podwójnego stosu (tylko x86)  
  
-   Ulepszone pamięci Uściślanie (lepsze zakłócenia informacje o zmiennych globalnych i parametry wejściowe)  
  
> [!NOTE]
>  Konsolidator określa optymalizacji, które były używane do kompilowania poszczególnych funkcji i stosuje tej samej optymalizacji w czasie łącza.  
  
 Przy użyciu **opcję/LTCG** i **/Ogt** powoduje wyrównanie o podwójnej precyzji optymalizacji.  
  
 Jeśli **opcję/LTCG** i **/Ogs** są określone wyrównanie double nie jest wykonywana. Jeśli większości funkcji w aplikacji są kompilowane dla danej szybkości, przy użyciu kilku funkcjach skompilowanych dla rozmiaru (na przykład za pomocą [zoptymalizować](../../preprocessor/optimize.md) pragma), kompilator o podwójnej precyzji wyrównuje funkcje, które są zoptymalizowane pod kątem rozmiaru, jeśli wywołanie Funkcje, które wymagają wyrównanie dwa razy.  
  
 Jeśli kompilator może zidentyfikować wszystkich miejsc wywołania funkcji, kompilator ignoruje jawne modyfikatorów Konwencja wywoływania funkcji i próbuje zoptymalizować konwencja wywołania funkcji:  
  
-   przekazywanie parametrów rejestrów  
  
-   zmiany kolejności parametrów dla wyrównania  
  
-   Usuń nieużywane parametry  
  
 Czy funkcja jest wywoływana przez wskaźnik funkcji, czy funkcja jest wywoływana z poza moduł, który ma być kompilowana przy użyciu **/GL**, kompilator nie będzie podejmował prób optymalizacji konwencja wywołania funkcji.  
  
> [!NOTE]
>  Jeśli używasz **opcję/LTCG** i ponownie zdefiniować mainCRTStartup, aplikacja może mieć nieprzewidywalne zachowanie, które odnoszą się do kodu użytkownika, który jest wykonywany przed zainicjowaniem obiektów globalnych.  Istnieją trzy sposoby rozwiązania tego problemu: nie ponownego zdefiniowania mainCRTStartup, nie skompilować pliku, który zawiera mainCRTStartup przy użyciu **opcję/LTCG**, lub statycznie zainicjować zmienne globalne i obiektów.  
  
## <a name="ltcg-and-msil-modules"></a>/ LTCG i modułów MSIL  
 Moduły, które są kompilowane przy użyciu [/GL](../../build/reference/gl-whole-program-optimization.md) i [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) mogą być używane jako dane wejściowe konsolidatora podczas **opcję/LTCG** jest określona.  
  
-   **/ LTCG** je zaakceptować, obiekt natywny, mieszanym plików natywną/zarządzaną obiektów (skompilowana przy użyciu **/CLR**) i pliki czysty obiektów (skompilowana przy użyciu **/CLR: pure**), i bezpieczne obiektu plików ( skompilowane przy użyciu **/CLR: Safe**). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
-   **/ LTCG** może akceptować bezpiecznych modułów .netmodule, można utworzyć za pomocą **/CLR: Safe /LN** w programie Visual C++ i **/target: module** w dowolnym kompilatora .NET Visual Studio. . Netmodules utworzone za pomocą **/CLR** lub **/CLR: pure** nie są akceptowane przez **opcję/LTCG**.  
  
-   /LTCG:PGI nie akceptuje skompilowana przy użyciu modułów macierzystych **/GL** i **/CLR**, lub czystej modułów (utworzone za pomocą **/CLR: pure**)  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **właściwości konfiguracji** folderu.  
  
3.  Wybierz **ogólne** strony właściwości.  
  
4.  Modyfikowanie **Optymalizacja Całoprogramowa** właściwości.  
  
 Można także zastosować **opcję/LTCG** do określonej kompilacji, wybierając **kompilacji**, **profilowana Optymalizacja** paska menu lub przez wybranie jednej profilowana Optymalizacja Opcje menu skrótów dla projektu.  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)