---
title: /LTCG (Generowanie łączonych kodów czasowych)
ms.date: 03/14/2018
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
ms.openlocfilehash: 40fb591952180735de3a2c226a3953a303c7d90f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810318"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Generowanie łączonych kodów czasowych)

Użyj **opcję/LTCG** przeprowadzić optymalizacji całego programu, lub do tworzenia Instrumentacji profilowana Optymalizacja (PGO), wykonaj szkolenia i utworzyć sterowane profilem zoptymalizowane pod kątem kompilacji.

## <a name="syntax"></a>Składnia

> **/LTCG**[**:**{**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]<br/>

Te opcje są przestarzałe, począwszy od programu Visual Studio 2015:

> **/ LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Argumenty

**PRZYROSTOWE**<br/>
(Opcjonalnie) Określa, że konsolidator dotyczy tylko całego programu optymalizacji lub linku w czasie generowania kodu (LTCG) zestaw plików wpływ, zamiast całego projektu. Domyślnie ta flaga nie ustawiono kiedy **opcję/LTCG** jest określony, i cały projekt jest połączona za pomocą optymalizacji całego programu.

**NOSTATUS** &AMP;#124; **STANU**<br/>
(Opcjonalnie) Określa, czy konsolidator wyświetla wskaźnik postępu, który pokazuje, jaki procent łącze zostało zakończone. Informacje o stanie nie jest wyświetlana domyślnie.

**OFF**<br/>
(Opcjonalnie) Wyłącza generowanie łączonych kodów czasowych. To zachowanie jest taka sama jak gdy **opcję/LTCG** nie jest określona w wierszu polecenia.

**PGINSTRUMENT**<br/>
(Opcjonalnie) Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i [przełączników/genprofile i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) do generowania instrumentowanej kompilacji dla optymalizacji sterowanej profilem. Dane, które są zbierane z instrumentowanych przebiegów jest używany do utworzenia zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md). Formularz Skrócony tej opcji jest **/LTCG:PGI**.

**PGOPTIMIZE**<br/>
(Opcjonalnie) Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i [/USEPROFILE](useprofile.md) tworzenie zoptymalizowanego obrazu. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md). Formularz Skrócony tej opcji jest **/LTCG:PGO**.

**PGUPDATE**<br/>
(Opcjonalnie) Ta opcja jest przestarzały, począwszy od programu Visual Studio 2015. Zamiast tego należy użyć **opcję/LTCG** i **/USEPROFILE** Aby ponownie skompilować zoptymalizowany obraz. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md). Formularz Skrócony tej opcji jest **/LTCG:PGU**.

## <a name="remarks"></a>Uwagi

**Opcję/LTCG** opcja informuje konsolidator, wywołań kompilatora i wykonywać optymalizacji całego programu. Można również wykonać Optymalizacja sterowana profilem. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md).

Z następującymi wyjątkami, nie można dodać opcje konsolidatora PGO kombinacji **opcję/LTCG** i **/USEPROFILE** nie zostały określone w poprzednim PGO inicjowania kombinacja  **/ LTCG** i **przełączników/genprofile** opcje:

- [/ BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/ OUT](out-output-file-name.md)

- [/ PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

Wszelkie opcje konsolidatora, które są określone razem z **opcję/LTCG** i **przełączników/genprofile** nie trzeba można określić podczas kompilowania przy użyciu opcji, aby zainicjować PGO **opcję/LTCG** i **/USEPROFILE**; są też dorozumianych.

Omówiono w dalszej części tego artykułu **opcję/LTCG** pod względem Generowanie łączonych kodów czasowych.

**/ LTCG** jest implikowane przy użyciu [/GL](gl-whole-program-optimization.md).

Konsolidator wywołuje Generowanie łączonych kodów czasowych, jeśli zostanie przekazana, moduł, który został skompilowany przy użyciu **/GL** lub moduł MSIL (zobacz [pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md)). Jeśli nie zostanie jawnie określony **opcję/LTCG** podczas przekazywania **/GL** lub modułów MSIL, aby konsolidator ostatecznie konsolidator wykryje to i uruchamia ponownie link przy użyciu **opcję/LTCG**. Jawnie określić **opcję/LTCG** podczas przekazywania **/GL** i moduł MSIL do konsolidatora do ewentualnego najszybszy tworzenie wydajnością.

Nawet szybsze działanie, należy użyć **opcję/LTCG: PRZYROSTOWE**. Ta opcja nakazuje konsolidatorowi tylko ponownie zoptymalizować zbiór plików, które mają wpływ zmiany plików źródłowych, zamiast całego projektu. Może to znacznie zmniejszyć czas łącza. Nie jest ta sama opcja jako łączenie przyrostowe.

**/ LTCG** nie jest prawidłowa do stosowania z [/INCREMENTAL](incremental-link-incrementally.md).

Gdy **opcję/LTCG** służy do łączenia moduły skompilowane przy użyciu [/Og](og-global-optimizations.md), [/O1](o1-o2-minimize-size-maximize-speed.md), [/O2](o1-o2-minimize-size-maximize-speed.md), lub [ox](ox-full-optimization.md), następujące optymalizacje są wykonywane:

- Optimalizaci Mezi wbudowanie

- Alokacja rejestru interprocedural (tylko systemy operacyjne 64-bitowy)

- Konwencja wywoływania niestandardowych (tylko x86)

- Małe przemieszczenia protokołu TLS (tylko x86)

- Wyrównanie podwójny stos (tylko x86)

- Uściślanie ulepszone pamięci (lepsze informacje zakłócenia dla zmiennych globalnych i parametry wejściowe)

> [!NOTE]
> Konsolidator określa optymalizacje, które były używane do kompilowania poszczególnych funkcji i stosuje ten sam optymalizacje w czasie połączenia.

Za pomocą **opcję/LTCG** i **/Ogt** powoduje, że Optymalizacja wyrównanie podwójnej precyzji.

Jeśli **opcję/LTCG** i **/Ogs** są określone wyrównanie double nie jest wykonywane. Jeśli większości funkcji w aplikacji są kompilowane dla danej szybkości, z kilku funkcji skompilowany dla rozmiaru (na przykład za pomocą [zoptymalizować](../../preprocessor/optimize.md) pragma), kompilator double wyrównuje funkcje, które są zoptymalizowane pod kątem rozmiaru, jeśli wywołują Funkcje, które wymagają wyrównanie double.

Jeśli kompilator może zidentyfikować wszystkie witryny wywołania funkcji, kompilator ignoruje jawne modyfikatorów Konwencja wywoływania funkcji i próbuje zoptymalizować konwencja wywołania funkcji:

- Parametry są przekazywane w rejestrach

- Zmień kolejność parametrów wyrównanie

- Usuń nieużywane parametry

Jeśli funkcja jest wywoływana za pomocą wskaźnika funkcji lub jeśli funkcja jest wywoływana z poza modułem, który jest kompilowany przy użyciu **/GL**, kompilator nie jest podejmowana próba zoptymalizować konwencja wywołania funkcji.

> [!NOTE]
> Jeśli używasz **opcję/LTCG** i ponownie zdefiniować `mainCRTStartup`, aplikacja może mieć nieprzewidywalne zachowanie, które odnoszą się do kodu użytkownika, który jest wykonywany przed zainicjowaniem obiektów globalnych. Istnieją trzy sposoby, aby rozwiązać ten problem: nie przedefiniować `mainCRTStartup`, nie można skompilować pliku który zawiera `mainCRTStartup` przy użyciu **opcję/LTCG**, lub statycznie zainicjować zmienne globalne i obiektów.

### <a name="ltcg-and-msil-modules"></a>/ LTCG i modułów MSIL

Moduły, które są kompilowane przy użyciu [/GL](gl-whole-program-optimization.md) i [/CLR](clr-common-language-runtime-compilation.md) może służyć jako dane wejściowe do konsolidatora podczas **opcję/LTCG** jest określony.

- **/ LTCG** je zaakceptować, obiekt natywny, a mieszane natywnego/zarządzanego obiektu plików (skompilowany przy użyciu **/CLR**). **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

- **/LTCG:PGI** nie akceptuje skompilowane przy użyciu modułów macierzystych **/GL** i   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **ogólne** stronę właściwości.

1. Modyfikowanie **Optymalizacja Całoprogramowa** właściwości.

Można również zastosować **opcję/LTCG** określonej kompilacji, wybierając **kompilacji** > **profilowana Optymalizacja** na pasku menu lub wybierając jedną z profilu Profilowana Optymalizacja opcje menu skrótów dla projektu.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
