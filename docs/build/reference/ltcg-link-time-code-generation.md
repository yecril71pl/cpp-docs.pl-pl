---
title: / LTCG (Generowanie łączonych kodów czasowych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc4266e8b01201226c53584bed9f90ed9dcabef7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703736"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Generowanie łączonych kodów czasowych)

Użyj **opcję/LTCG** do przeprowadzania optymalizacji całego programu lub do tworzenia Instrumentacji Optymalizacja sterowana profilem — (PGO), przeprowadzić szkolenie i utworzyć profilowana zoptymalizowanych pod kątem kompilacji.

## <a name="syntax"></a>Składnia

> **/ LTCG**[**:**{**PRZYROSTOWE**|**NOSTATUS**|**STAN** | **OFF**}]<br/>

Te opcje są przestarzałe, począwszy od programu Visual Studio 2015:

> **/ LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Argumenty

**PRZYROSTOWE** (opcjonalnie)<br/>
Określa, że konsolidator dotyczy tylko całego programu optymalizacji lub w czasie konsolidacji generowania kodu (LTCG) zestaw plików objętych edycji, zamiast całego projektu. Domyślnie ta flaga nie jest ustawiona podczas **opcję/LTCG** jest określony, a cały projekt jest połączony za pomocą optymalizacja całego programu.

**NOSTATUS** &#124; **stan** (opcjonalnie)<br/>
Określa, czy konsolidator wyświetlany jest wskaźnik postępu, pokazujący, jaki procent konsolidacji została ukończona. Domyślnie te informacje o stanie nie jest wyświetlana.

**Wyłącz** (opcjonalnie)<br/>
Powoduje wyłączenie generowania kodu w czasie konsolidacji. To zachowanie jest takie samo, jak kiedy **opcję/LTCG** nie jest określona w wierszu polecenia.

**PGINSTRUMENT** (opcjonalnie)<br/>
Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i [opcji/genprofile lub /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) do generowania instrumentowanej kompilacji dla optymalizacji sterowanych profilem. Dane, które mają być zbierane z Instrumentacją uruchamia służy do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](profile-guided-optimizations.md). Krótka forma ta opcja jest **/LTCG:PGI**.

**PGOPTIMIZE** (opcjonalnie)<br/>
Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i [/USEPROFILE](useprofile.md) do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md). Krótka forma ta opcja jest **/LTCG:PGO**.

**PGUPDATE** (opcjonalnie)<br/>
Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i **/USEPROFILE** odbudować zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md). Krótka forma ta opcja jest **/LTCG:PGU**.

## <a name="remarks"></a>Uwagi

**Opcję/LTCG** opcja informuje konsolidator, aby wywołać kompilatora i wykonywać optymalizacji całego programu. Możesz również wykonać do optymalizacji profilowej. Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md).

Opcje konsolidatora z następującymi wyjątkami nie można dodać do PGO kombinację **opcję/LTCG** i **/USEPROFILE** nie zostały określone w poprzedniej PGO inicjowania kombinacja  **/ LTCG** i **opcji/genprofile** opcje:

- [/ BASE](../../build/reference/base-base-address.md)

- [/FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/ OUT](../../build/reference/out-output-file-name.md)

- [/ PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

Wszystkie opcje konsolidatora, które zostały określone razem z **opcję/LTCG** i **opcji/genprofile** nie trzeba można określić podczas tworzenia przy użyciu opcji, aby zainicjować PGO **opcję/LTCG** i **/USEPROFILE**; są one niejawnego.

Omówiono w dalszej części tego artykułu **opcję/LTCG** pod względem Generowanie łączonych kodów czasowych.

**/ LTCG** technicznego z [/GL](../../build/reference/gl-whole-program-optimization.md).

Konsolidator wywołuje Generowanie łączonych kodów czasowych, jeśli został przekazany moduł, który został skompilowany przy użyciu **/GL** lub moduł MSIL (zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)). Jeśli nie zostanie jawnie określony **opcję/LTCG** podczas przekazywania **/GL** lub moduł MSIL do konsolidatora, konsolidator ostatecznie wykryje to i uruchamia ponownie łącza za pomocą **opcję/LTCG**. Określ jawnie **opcję/LTCG** podczas przekazywania **/GL** i moduł MSIL do konsolidatora do ewentualnego najszybszym kompilacji wydajności.

Nawet zwiększyć wydajność, można użyć **opcję/LTCG: PRZYROSTOWE**. Ta opcja nakazuje konsolidatorowi tylko ponownie zoptymalizować zestawu plików, których dotyczy zmiana pliku źródłowego, zamiast całego projektu. To znacznie ograniczyć czas łącza. To nie jest ta sama opcja jako konsolidowania przyrostowego.

**/ LTCG** nie nadaje się do użytku z [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).

Gdy **opcję/LTCG** służy do łączenia moduły skompilowane przy użyciu [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), lub [ox](../../build/reference/ox-full-optimization.md), wykonywane są następujące funkcje optymalizacji:

- Między modułami

- Alokacja rejestru interprocedural (tylko systemy operacyjne 64-bitowe)

- Konwencja wywoływania niestandardowych (tylko x86)

- Mała przemieszczenie TLS (tylko x86)

- Wyrównanie podwójnego stosu (tylko x86)

- Ulepszone pamięci Uściślanie (lepsze zakłócenia informacje o zmiennych globalnych i parametry wejściowe)

> [!NOTE]
> Konsolidator określa optymalizacji, które były używane do kompilowania poszczególnych funkcji i stosuje tej samej optymalizacji w czasie łącza.

Przy użyciu **opcję/LTCG** i **/Ogt** powoduje wyrównanie o podwójnej precyzji optymalizacji.

Jeśli **opcję/LTCG** i **/Ogs** są określone wyrównanie double nie jest wykonywana. Jeśli większości funkcji w aplikacji są kompilowane dla danej szybkości, przy użyciu kilku funkcjach skompilowanych dla rozmiaru (na przykład za pomocą [zoptymalizować](../../preprocessor/optimize.md) pragma), kompilator o podwójnej precyzji wyrównuje funkcje, które są zoptymalizowane pod kątem rozmiaru, jeśli wywołanie Funkcje, które wymagają wyrównanie dwa razy.

Jeśli kompilator może zidentyfikować wszystkich miejsc wywołania funkcji, kompilator ignoruje jawne modyfikatorów Konwencja wywoływania funkcji i próbuje zoptymalizować konwencja wywołania funkcji:

- przekazywanie parametrów rejestrów

- zmiany kolejności parametrów dla wyrównania

- Usuń nieużywane parametry

Czy funkcja jest wywoływana przez wskaźnik funkcji, czy funkcja jest wywoływana z poza moduł, który ma być kompilowana przy użyciu **/GL**, kompilator nie będzie podejmował prób optymalizacji konwencja wywołania funkcji.

> [!NOTE]
> Jeśli używasz **opcję/LTCG** i ponownie zdefiniować `mainCRTStartup`, aplikacja może mieć nieprzewidywalne zachowanie, które odnoszą się do kodu użytkownika, który jest wykonywany przed zainicjowaniem obiektów globalnych. Istnieją trzy sposoby rozwiązania tego problemu: nie ponownego zdefiniowania `mainCRTStartup`, nie skompilować pliku, który zawiera `mainCRTStartup` za pomocą **opcję/LTCG**, lub statycznie zainicjować zmienne globalne i obiektów.

### <a name="ltcg-and-msil-modules"></a>/ LTCG i modułów MSIL

Moduły, które są kompilowane przy użyciu [/GL](../../build/reference/gl-whole-program-optimization.md) i [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) mogą być używane jako dane wejściowe konsolidatora podczas **opcję/LTCG** jest określona.

- **/ LTCG** je zaakceptować, obiekt natywny, a mieszane natywną/zarządzaną obiekt plików (skompilowana przy użyciu **/CLR**). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

- **/LTCG:PGI** nie akceptuje skompilowana przy użyciu modułów macierzystych **/GL** i   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **ogólne** strony właściwości.

1. Modyfikowanie **Optymalizacja Całoprogramowa** właściwości.

Można także zastosować **opcję/LTCG** do określonej kompilacji, wybierając **kompilacji** > **profilowana Optymalizacja** paska menu lub przez wybranie jednej profilu Wskazówki optymalizacji opcje menu skrótów dla projektu.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
