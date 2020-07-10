---
title: /LTCG (Generowanie łączonych kodów czasowych)
description: MSVC opcja konsolidatora/LTCG umożliwia generowanie kodu w czasie konsolidacji dla optymalizacji całego programu.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: c954794d6d0fd087eee74ebb7e86d77b89a9a8fc
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180802"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG`(Generowanie kodu w czasie konsolidacji)

Służy **`/LTCG`** do przeprowadzania optymalizacji całego programu lub do tworzenia Instrumentacji optymalizacji opartej na profilach (PGO), wykonywania szkoleń i tworzenia zoptymalizowanych kompilacji opartych na profilach.

## <a name="syntax"></a>Składnia

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

Te opcje są przestarzałe, począwszy od programu Visual Studio 2015:

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>Argumenty

**`INCREMENTAL`**<br/>
Obowiązkowe Określa, że konsolidator stosuje tylko pełną optymalizację programu lub generowanie kodu w czasie konsolidacji (LTCG) do plików, których dotyczy Edycja, a nie cały projekt. Domyślnie ta flaga nie jest ustawiona, gdy **`/LTCG`** jest określona, a cały projekt jest połączony przy użyciu funkcji optymalizacji całego programu.

**`NOSTATUS`**&#124;**`STATUS`**<br/>
Obowiązkowe Określa, czy konsolidator wyświetla wskaźnik postępu, który pokazuje, jaki procent łącza został ukończony. Domyślnie te informacje o stanie nie są wyświetlane.

**`OFF`**<br/>
Obowiązkowe Wyłącza generowanie kodu w czasie konsolidacji. Takie zachowanie jest takie samo, jak w przypadku, gdy **`/LTCG`** nie jest określone w wierszu polecenia.

**`PGINSTRUMENT`**<br/>
Obowiązkowe Ta opcja jest przestarzała począwszy od programu Visual Studio 2015. Zamiast tego użyj **`/LTCG`** i `[/GENPROFILE` lub `/FASTGENPROFILE` ] (GENPROFILE-fastgenprofile-Generate-Profiling-instrumented-Build.MD), aby wygenerować instrumentację kompilacji dla optymalizacji opartej na profilach. Dane zbierane z przebiegów Instrumentacji są używane do tworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane. Krótka forma tej opcji to **`/LTCG:PGI`** .

**`PGOPTIMIZE`**<br/>
Obowiązkowe Ta opcja jest przestarzała począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **`/LTCG`** i [`/USEPROFILE`](useprofile.md) do skompilowania zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane. Krótka forma tej opcji to **`/LTCG:PGO`** .

**`PGUPDATE`**<br/>
Obowiązkowe Ta opcja jest przestarzała począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **`/LTCG`** i **`/USEPROFILE`** w celu odbudowania zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane. Krótka forma tej opcji to **`/LTCG:PGU`** .

## <a name="remarks"></a>Uwagi

**`/LTCG`** Opcja nakazuje konsolidatorowi wywołanie kompilatora i przeprowadzenie optymalizacji całego programu. Można także przeprowadzić optymalizację z przewodnikiem. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane.

Z następującymi wyjątkami nie można dodać opcji konsolidatora do kombinacji PGO **`/LTCG`** i **`/USEPROFILE`** , które nie zostały określone w poprzedniej kombinacji inicjowania PGO **`/LTCG`** i **`/GENPROFILE`** opcji:

- [`/BASE`](base-base-address.md)

- [`/FIXED`](fixed-fixed-base-address.md)

- **`/LTCG`**

- [`/MAP`](map-generate-mapfile.md)

- [`/MAPINFO`](mapinfo-include-information-in-mapfile.md)

- [`/NOLOGO`](nologo-suppress-startup-banner-linker.md)

- [`/OUT`](out-output-file-name.md)

- [`/PGD`](pgd-specify-database-for-profile-guided-optimizations.md)

- [`/PDB`](pdb-use-program-database.md)

- [`/PDBSTRIPPED`](pdbstripped-strip-private-symbols.md)

- [`/STUB`](stub-ms-dos-stub-file-name.md)

- [`/VERBOSE`](verbose-print-progress-messages.md)

Wszystkie Opcje konsolidatora, które są określone razem **`/LTCG`** z **`/GENPROFILE`** opcjami i w celu zainicjowania PGO nie muszą być określone podczas kompilowania przy użyciu **`/LTCG`** i **`/USEPROFILE`** ; są one implikowane.

W pozostałej części tego artykułu omówiono generowanie kodu w czasie konsolidacji wykonywane przez program **`/LTCG`** .

**`/LTCG`** jest implikowany przez [`/GL`](gl-whole-program-optimization.md) .

Konsolidator wywołuje generowanie kodu w czasie konsolidacji, jeśli przekazano moduł, który został skompilowany przy użyciu **`/GL`** lub moduł MSIL (zobacz [ `.netmodule` pliki jako dane wejściowe konsolidatora](netmodule-files-as-linker-input.md)). Jeśli nie określisz jawnie **`/LTCG`** podczas przekazywania lub przechodzenia **`/GL`** modułu MSIL do konsolidatora, konsolidator ostatecznie wykryje tę sytuację i ponownie uruchomi link przy użyciu **`/LTCG`** . Jawnie określ, **`/LTCG`** kiedy przekazują i przechodzenia **`/GL`** moduły MSIL do konsolidatora w celu uzyskania najszybszej możliwej wydajności kompilacji.

Aby uzyskać większą wydajność, użyj programu **`/LTCG:INCREMENTAL`** . Ta opcja nakazuje konsolidatorowi reoptymalizację tylko tych plików, których dotyczy zmiana pliku źródłowego, a nie całego projektu. Ta opcja może znacznie skrócić czas wymagany przez link. Ta opcja nie jest taka sama jak [Konsolidacja przyrostowa](incremental-link-incrementally.md).

**`/LTCG`** nie jest prawidłowy do użycia z [`/INCREMENTAL`](incremental-link-incrementally.md) .

Gdy **`/LTCG`** jest używany do łączenia modułów skompilowanych przy użyciu [`/Og`](og-global-optimizations.md) , [`/O1`](o1-o2-minimize-size-maximize-speed.md) , [`/O2`](o1-o2-minimize-size-maximize-speed.md) , lub [`/Ox`](ox-full-optimization.md) , wykonywane są następujące optymalizacje:

- Derysowanie między modułami

- Alokacja rejestrów międzyproceduralnych (tylko 64-bitowe systemy operacyjne)

- Niestandardowa Konwencja wywoływania (tylko x86)

- Małe przemieszczenie TLS (tylko x86)

- Podwójne wyrównanie stosu (tylko x86)

- Ulepszone Uściślanie pamięci (lepsze informacje o zakłóceniach dla zmiennych globalnych i parametrów wejściowych)

> [!NOTE]
> Konsolidator określa, które optymalizacje były używane do kompilowania każdej funkcji i stosuje te same optymalizacje w czasie łącza.

Używanie **`/LTCG`** i **`/O2`** powoduje optymalizację podwójnego wyrównania.

Jeśli **`/LTCG`** i **`/O1`** są określone, podwójne wyrównanie nie jest wykonywane. Jeśli większość funkcji w aplikacji jest skompilowanych pod kątem szybkości z kilkoma funkcjami skompilowanymi dla rozmiaru (na przykład przy użyciu [`optimize`](../../preprocessor/optimize.md) dyrektywy pragma), kompilator podwójnie wyrównuje funkcje, które są zoptymalizowane pod kątem rozmiaru, jeśli wywołują funkcje, które wymagają podwójnego wyrównania.

Jeśli kompilator może zidentyfikować wszystkie lokacje wywołań funkcji, kompilator ignoruje jawne Modyfikatory konwencji wywoływania dla funkcji i próbuje zoptymalizować konwencję wywoływania funkcji:

- Przekaż parametry w rejestrach

- Zmień kolejność parametrów dla wyrównania

- Usuń nieużywane parametry

Jeśli funkcja jest wywoływana za pośrednictwem wskaźnika funkcji lub jeśli funkcja jest wywoływana spoza modułu, który jest kompilowany przy użyciu **`/GL`** , kompilator nie próbuje zoptymalizować konwencji wywoływania funkcji.

> [!NOTE]
> Jeśli używasz **`/LTCG`** i przedefiniujesz `mainCRTStartup` , aplikacja może mieć nieprzewidywalne zachowanie, które odnosi się do kodu użytkownika, który jest wykonywany przed zainicjowaniem obiektów globalnych. Istnieją trzy sposoby rozwiązania tego problemu: nie należy przedefiniować `mainCRTStartup` , nie Kompiluj pliku, który zawiera `mainCRTStartup` za pomocą **`/LTCG`** lub zainicjuj zmienne globalne i obiekty statycznie.

### <a name="ltcg-and-msil-modules"></a>`/LTCG`Moduły MSIL i

Moduły, które są kompilowane przy użyciu [`/GL`](gl-whole-program-optimization.md) i [`/clr`](clr-common-language-runtime-compilation.md) mogą być używane jako dane wejściowe konsolidatora, gdy **`/LTCG`** jest określony.

- **`/LTCG`** może akceptować natywne pliki obiektów i mieszane pliki obiektów natywnych/zarządzanych (skompilowane przy użyciu **`/clr`** ). **`/clr:pure`** **`/clr:safe`** Opcje kompilatora i są przestarzałe w programie visual Studio 2015 i nie są obsługiwane w programie visual Studio 2017 lub nowszym.

- **`/LTCG:PGI`** nie akceptuje modułów natywnych skompilowanych za pomocą **`/GL`** i**`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Zobacz [Ustawianie właściwości kompilatora i kompilacji języka C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości**Ogólne** właściwości konfiguracji.

1. Zmodyfikuj właściwość **optymalizacji całego programu** .

Można również zastosować **`/LTCG`** do określonych kompilacji, wybierając opcję **Build**  >  **Optymalizacja profilu** kompilacji na pasku menu lub wybierając jeden z opcji optymalizacji profilowanej w menu skrótów dla projektu.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Zobacz też

[Odwołanie konsolidatora MSVC](linking.md)\
[Opcje konsolidatora MSVC](linker-options.md)
