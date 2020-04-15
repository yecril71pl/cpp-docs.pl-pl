---
title: Strony właściwości kompilatora MIDL
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336252"
---
# <a name="midl-property-pages"></a>Strony właściwości MIDL

Strony właściwości MIDL są dostępne jako właściwość elementu w pliku . IDL w projekcie języka C++, który używa modelu COM. Użyj ich do skonfigurowania [kompilatora MIDL](/windows/win32/midl/using-the-midl-compiler-2). Aby uzyskać informacje na temat programowego dostępu do opcji <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> MIDL dla projektów W++, zobacz obiekt. Zobacz też [Ogólna składnia wiersza polecenia MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Strona właściwości ogólnych

### <a name="preprocessor-definitions"></a>Definicje preprocesora

Określa jedną lub więcej zdefiniowanych, w tym makra\]MIDL ([/D](/windows/win32/midl/-d)).\[).

### <a name="additional-include-directories"></a>Dodatkowe katalogi dołączania

Określa jeden lub więcej katalogów do dodania do\]ścieżki dołączania ([/I](/windows/win32/midl/-i)\[).

### <a name="additional-metadata-directories"></a>Dodatkowe katalogi metadanych

Określ katalog zawierający plik Windows.Foundation.WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[path\]).

### <a name="enable-windows-runtime"></a>Włączanie środowiska wykonawczego systemu Windows

Włącz semantykę środowiska wykonawczego systemu Windows, aby utworzyć plik metadanych systemu Windows ([/winrt](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignoruj standardową ścieżkę dołączania

Ignoruj bieżące i dołącz katalogi ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Kompatybilny z MkTypLib

Wymusza kompatybilność z mktyplib.exe w wersji 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Poziom ostrzeżenia

Wybiera surowość błędów kodu MIDL ([/W](/windows/win32/midl/-w)).

**Choices**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Potraktuj ostrzeżenia jako błędy

Umożliwia midl traktować wszystkie ostrzeżenia jako błędy ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Pomijanie banera startowego

Pomiń wyświetlanie banera startowego i komunikatu informacyjnego ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>Typ char kompilatora C

Określa domyślny typ znaku kompilatora C, który będzie używany do kompilowania wygenerowanego kodu. ([/char](/windows/win32/midl/-char) signed|unsigned|ascii7).

**Choices**

- **Podpisano** — podpisano
- **Niepodpisane** — niepodpisane
- **Ascii** - Ascii

### <a name="target-environment"></a>Środowisko docelowe

Określa, które środowisko ma być kierowane ([/env](/windows/win32/midl/-env) arm32|win32|ia64|x64).

**Choices**

- **Nie ustawiono** - Win32
- **Microsoft Windows 32-bitowy** - Win32
- **Microsoft Windows 64-bit na Itanium** - IA64
- **Microsoft Windows ARM** - ARM
- **Microsoft Windows ARM64** - ARM64
- **Microsoft Windows 64-bit na x64** - X64

### <a name="generate-stubless-proxies"></a>Generowanie serwerów proxy bez stubless

Generowanie w pełni interpretowanych wycinków z rozszerzeniami i bez stubless proxy dla interfejsów obiektów ([/Oicf](/windows/win32/midl/-oi), [/Oif](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Pomijanie ostrzeżeń kompilatora

Pomijanie komunikatów ostrzegawczych kompilatora ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Tryb konfiguracji aplikacji

Zezwalaj na wybrane atrybuty ACF w pliku IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>Identyfikator ustawień regionalnych

Określa identyfikator LCID dla plików wejściowych, nazw plików i ścieżek katalogów ([/lcid](/windows/win32/midl/-lcid) DECIMAL).

### <a name="multi-processor-compilation"></a>Kompilacja wieloprocesorowa

Uruchom wiele wystąpień w tym samym czasie.

## <a name="output-property-page"></a>Strona właściwości wyjściowej

### <a name="output-directory"></a>Katalog wyjściowy

Określa katalog wyjściowy ([/out](/windows/win32/midl/-out) [katalog]).

### <a name="metadata-file"></a>Plik metadanych

Określa nazwę wygenerowanego pliku metadanych ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Plik nagłówka

Określa nazwę wygenerowanego pliku nagłówka ([/h](/windows/win32/midl/-h) nazwa pliku).

### <a name="dlldata-file"></a>Plik DllData

Określa nazwę pliku DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>Plik IID

Określa nazwę pliku identyfikatora interfejsu ([/iid](/windows/win32/midl/-iid) filename).

### <a name="proxy-file"></a>Plik proxy

Określa nazwę pliku proxy ([/proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Generowanie biblioteki typów

Określ, aby nie generować biblioteki typów ([/notlb] dla nie).

### <a name="type-library"></a>Biblioteka typów

Określa nazwę pliku biblioteki typów ([/tlb](/windows/win32/midl/-tlb) nazwa pliku).

### <a name="generate-client-stub-files"></a>Generowanie plików skrótowych klienta

Wygeneruj tylko plik skrótowy klienta ([/client](/windows/win32/midl/-client) [stub|none]).

**Choices**

- **Odcinek** - Odcinek
- **Brak** - Brak

### <a name="generate-server-stub-files"></a>Generowanie plików skrótowych serwera

Generowanie tylko pliku skrótowego serwera ([/server](/windows/win32/midl/-server) [stub|none]).

**Choices**

- **Odcinek** - Odcinek
- **Brak** - Brak

### <a name="client-stub-file"></a>Plik skrótowy klienta

Określ plik skrótowy klienta ([/cstub](/windows/win32/midl/-cstub) [plik]).

### <a name="server-stub-file"></a>Plik skrótowy serwera

Określ plik skrótowy serwera ([/sstub](/windows/win32/midl/-sstub) [plik]).

### <a name="type-library-format"></a>Format biblioteki typów

Określa format pliku biblioteki typów ([/oldtlb|/newtlb]).

**Choices**

- **NewFormat** - nowy format
- **OldFormat** - Stary format

## <a name="advanced-property-page"></a>Strona właściwości zaawansowanej

### <a name="c-preprocess-options"></a>Opcje przetwarzania wstępnego C

Określa przełączniki, które mają być przerzucane do preprocesora kompilatora C ([/cpp_opt](/windows/win32/midl/-cpp-opt) przełączników).

### <a name="undefine-preprocessor-definitions"></a>Definicje przederocesora przeddefine

Określa jeden lub więcej niezdrobnień, w tym makra MIDL ([/U](/windows/win32/midl/-U) [makra]).

### <a name="enable-error-checking"></a>Włącz sprawdzanie błędów

Wybierz opcję sprawdzania błędów ([/error all|none]).

**Choices**

- **EnableCustom** — wszystkie
- **Wszystkie** - Wszystkie
- **Brak** - Brak

### <a name="check-allocations"></a>Sprawdź alokacje

Sprawdź, czy nie ma błędów pamięci ([/error](/windows/win32/midl/-error) allocation).

### <a name="check-bounds"></a>Sprawdź granice

Sprawdź rozmiar a specyfikację długości transmisji ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Sprawdź zakres wyliczenia

Sprawdź wartości wyliczenia, które mają znajdować się w dopuszczalnym zakresie ([/error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Sprawdź wskaźniki referencyjne

Sprawdź wskaźniki ref jako inne niż null ([/error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Sprawdź dane skrótowe

Emituj dodatkowe sprawdzanie ważności danych skrótowych po stronie serwera ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Poprzedzaj obszar nazw "ABI"

Przedaj obszar nazw "ABI" do wszystkich typów.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Sprawdzanie poprawności parametrów

Generowanie dodatkowych informacji w celu sprawdzenia poprawności parametrów ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Wyrównanie elementu członkowskiego struktury

Określa poziom pakowania struktur w systemie docelowym (/ZpN).

**Choices**

- **Nie ustawiono** — nie ustawiono
- **1 Bajt** - Zp1
- **2 Bajt** - Zp2
- **4 Bajt** - Zp4
- **8 Bajt** - Zp8

### <a name="redirect-output"></a>Przekieruj dane wyjściowe

Przekierowuje dane wyjściowe z ekranu do pliku ([/o).](/windows/win32/midl/-o)

### <a name="minimum-target-system"></a>Minimalny system docelowy

Ustaw minimalny system docelowy ([/target](/windows/win32/midl/-target) STRING).
