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
ms.openlocfilehash: e9c9cb75d326642c86405992a4bf9d7da9e578df
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927696"
---
# <a name="midl-property-pages"></a>Strony właściwości MIDL

Strony właściwości MIDL są dostępne jako właściwość elementu w. Plik IDL w C++ projekcie, który używa modelu com. Użyj ich do skonfigurowania [kompilatora MIDL](/windows/win32/midl/using-the-midl-compiler-2). Aby uzyskać informacje na temat sposobu programistycznego dostępu do C++ opcji MIDL dla <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> projektów, zobacz Object. Zobacz również [Ogólne MIDL składni wiersza polecenia](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Ogólna strona właściwości

### <a name="preprocessor-definitions"></a>Definicje preprocesora

Określa co najmniej jedną definicję, w tym makra\]MIDL ([/d](/windows/win32/midl/-d))\[.

### <a name="additional-include-directories"></a>Dodatkowe katalogi dołączane

Określa co najmniej jeden katalog do dodania do ścieżki dołączania (ścieżka\][/i](/windows/win32/midl/-i)\[).

### <a name="additional-metadata-directories"></a>Dodatkowe katalogi metadanych

Określ katalog zawierający plik Windows. Foundation. winmd (ścieżka\][/metadata_dir](/windows/win32/midl/-metadata-dir) \[).

### <a name="enable-windows-runtime"></a>Włącz środowisko wykonawcze systemu Windows

Włącz semantykę środowisko wykonawcze systemu Windows, aby utworzyć plik metadanych systemu Windows ([/WinRT](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignoruj standardowe ścieżki dołączania

Ignoruj bieżące i katalogi dołączane ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Zgodne MkTypLib

Wymusza zgodność z MkTypLib. exe w wersji 2,03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Poziom ostrzeżeń

Wybiera rygorystyczność błędów kodu MIDL ([/w](/windows/win32/midl/-w)).

**Decyzji**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Umożliwia MIDL traktowanie wszystkich ostrzeżeń jako błędów ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Pomiń transparent startowy

Pomijaj wyświetlanie banera startowego i komunikatu informacyjnego ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>Typ char kompilatora języka C

Określa domyślny typ znaku kompilatora języka C, który będzie używany do kompilowania wygenerowanego kodu. ([/char](/windows/win32/midl/-char) podpisane | niepodpisane | ascii7).

**Decyzji**

- **Podpisane z** podpisem
- **Bez** znaku — bez znaku
- **ASCII** — ASCII

### <a name="target-environment"></a>Środowisko docelowe

Określa środowisko docelowe ([/ENV](/windows/win32/midl/-env) arm32 | Win32 | IA64 | x64).

**Decyzji**

- **Nie ustawiono** — Win32
- **Microsoft Windows 32-bit** -Win32
- **Microsoft Windows 64-bit na Itanium** — ia64
- **Microsoft Windows ARM** — ARM
- **Microsoft Windows arm64** — arm64
- **Microsoft Windows 64 — bit x64** — x64

### <a name="generate-stubless-proxies"></a>Generuj proxy bez klas zastępczych

Generuj w pełni interpretowane klasy zastępcze z rozszerzeniami oraz proxy bez klas zastępczych dla interfejsów obiektów ([/Oicf](/windows/win32/midl/-oi), [/OIF](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Pomijanie ostrzeżeń kompilatora

Pomijaj komunikaty ostrzegawcze kompilatora ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Tryb konfiguracji aplikacji

Zezwalaj na wybrane atrybuty ACF w pliku IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>Identyfikator ustawień regionalnych

Określa identyfikator LCID dla plików wejściowych, nazw plików i ścieżek katalogów ([/LCID](/windows/win32/midl/-lcid) Decimal).

### <a name="multi-processor-compilation"></a>Kompilacja wieloprocesorowa

Uruchom jednocześnie wiele wystąpień.

## <a name="output-property-page"></a>Strona właściwości danych wyjściowych

### <a name="output-directory"></a>Katalog wyjściowy

Określa katalog wyjściowy ([/out](/windows/win32/midl/-out) [katalog]).

### <a name="metadata-file"></a>Plik metadanych

Określa nazwę wygenerowanego pliku metadanych ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Plik nagłówka

Określa nazwę wygenerowanego pliku nagłówka ([/h](/windows/win32/midl/-h) filename).

### <a name="dlldata-file"></a>Plik DllData

Określa nazwę pliku DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>Plik IID

Określa nazwę pliku identyfikatora interfejsu ([/IID](/windows/win32/midl/-iid) filename).

### <a name="proxy-file"></a>Plik proxy

Określa nazwę pliku serwera proxy ([/proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Generuj bibliotekę typów

Określ, aby nie generować biblioteki typów ([/notlb] dla elementu No).

### <a name="type-library"></a>Biblioteka typów

Określa nazwę pliku biblioteki typów ([/TLB](/windows/win32/midl/-tlb) filename).

### <a name="generate-client-stub-files"></a>Generuj pliki szczątkowe klienta

Generuj tylko plik szczątkowy klienta ([/Client](/windows/win32/midl/-client) [stub | none]).

**Decyzji**

- **Stub** — stub
- **Brak** — brak

### <a name="generate-server-stub-files"></a>Generuj pliki szczątkowe serwera

Generuj tylko plik szczątkowy serwera ([/Server](/windows/win32/midl/-server) [stub | none]).

**Decyzji**

- **Stub** — stub
- **Brak** — brak

### <a name="client-stub-file"></a>Plik szczątkowy klienta

Określ plik szczątkowy klienta ([/cstub](/windows/win32/midl/-cstub) [plik]).

### <a name="server-stub-file"></a>Plik szczątkowy serwera

Określ plik szczątkowy serwera ([/sstub](/windows/win32/midl/-sstub) [plik]).

### <a name="type-library-format"></a>Format biblioteki typów

Określa format pliku biblioteki typów ([/oldtlb |/newtlb]).

**Decyzji**

- **NewFormat** — nowy format
- **OldFormat** — stary format

## <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

### <a name="c-preprocess-options"></a>Opcje przetwarzania wstępnego C

Określa przełączniki do przekazania do preprocesora kompilatora języka C (przełączniki[/cpp_opt](/windows/win32/midl/-cpp-opt) ).

### <a name="undefine-preprocessor-definitions"></a>Usuń Definicje preprocesora

Określa co najmniej jedną definicję, w tym makra MIDL ([/u](/windows/win32/midl/-U) [makra]).

### <a name="enable-error-checking"></a>Włącz sprawdzanie błędów

Wybierz opcję sprawdzania błędów ([/Error All | none]).

**Decyzji**

- **EnableCustom** — wszystko
- **Wszystko** — wszystkie
- **Brak** — brak

### <a name="check-allocations"></a>Sprawdź alokacje

Sprawdź, czy nie występują błędy pamięci (alokacja[/Error](/windows/win32/midl/-error) ).

### <a name="check-bounds"></a>Sprawdź granice

Sprawdzanie rozmiaru i określania długości transmisji ([/Error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Sprawdź zakres wyliczania

Sprawdź, czy wartości wyliczeniowe mają być w dozwolonym zakresie ([/Error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Sprawdź wskaźniki odwołań

Sprawdź, czy wskaźniki ref nie mają wartości null ([/Error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Sprawdź dane szczątkowe

Emituj dodatkowe sprawdzenie poprawności danych szczątkowych po stronie serwera ([/Error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Poprzedź z przestrzenią nazw "ABI"

Dołącz przestrzeń nazw "ABI" do wszystkich typów.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Weryfikuj parametry

Generuj dodatkowe informacje, aby sprawdzić poprawność parametrów ([/Robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Wyrównanie elementu członkowskiego struktury

Określa poziom pakowania struktur w systemie docelowym (/ZpN).

**Decyzji**

- **Nie ustawiono** — nie ustawiono
- **1 bajt** — ZP1
- **2 bajty** — Zp2
- **4 bajt** — Zp4
- **8-bajtowy** — ZP8

### <a name="redirect-output"></a>Przekieruj dane wyjściowe

Przekierowuje dane wyjściowe z ekranu do pliku ([/o](/windows/win32/midl/-o) plik).

### <a name="minimum-target-system"></a>Minimalny system docelowy

Ustaw minimalny system docelowy ([/Target](/windows/win32/midl/-target) ciąg).



