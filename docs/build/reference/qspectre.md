---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: 2b784e464f98ae6a1f9285f799d903ae689bf6d5
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68340993"
---
# <a name="qspectre"></a>/Qspectre

Określa generowanie kompilatora instrukcji w celu ograniczenia niektórych luk w zabezpieczeniach Spectre Variant 1.

## <a name="syntax"></a>Składnia

> **/Qspectre**

## <a name="remarks"></a>Uwagi

Opcja **/Qspectre** jest dostępna w programie visual Studio 2017 w wersji 15.5.5 i nowszych oraz w programie visual Studio 2015 Update 3 do [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Powoduje, że kompilator wstawia instrukcje w celu ograniczenia niektórych [luk w zabezpieczeniach Spectre](https://spectreattack.com/spectre.pdf). Te luki w zabezpieczeniach są nazywane *atakami z kanału po stronie wykonywania*. Wpływają one na wiele systemów operacyjnych i nowoczesnych procesorów, w tym procesory z procesorów Intel, AMD i ARM.

Opcja **/Qspectre** jest domyślnie wyłączona.

W początkowej wersji opcji **/Qspectre** działał tylko na zoptymalizowanym kodzie. W programie Visual Studio 2017 w wersji 15,7 lub nowszej opcja **/Qspectre** jest obsługiwana na wszystkich poziomach optymalizacji.

Biblioteki wizualne C++ firmy Microsoft są również dostępne w wersjach z ograniczeniami Spectre. Biblioteki Spectre-z ograniczeniami dla programu Visual Studio 2017 i nowszych można pobrać w Instalator programu Visual Studio. Znajdują się one na karcie **poszczególne składniki** w obszarze **kompilatory, narzędzia kompilacji i środowiska uruchomieniowe**i mają w nazwie "libs for Spectre". Dostępne są zarówno biblioteki DLL, jak i statyczne środowiska uruchomieniowe z włączonym ograniczaniem ryzyka C++ dla podzbioru wizualizacji środowiska uruchomieniowego: Kod uruchamiania programu VC + +, vcruntime140, msvcp140, concrt140 i vcamp140. Biblioteki DLL są obsługiwane tylko dla wdrożenia lokalnego aplikacji. Zawartość pakietu redystrybucyjnego C++ Visual 2017 i nowszych bibliotek środowiska uruchomieniowego nie została zmodyfikowana.

Można także zainstalować biblioteki z ograniczeniami Spectre dla MFC i ATL. Znajdują się one na karcie **poszczególne składniki** w zestawach **SDK, biblioteki i struktury**.

### <a name="applicability"></a>Stosowanie

Jeśli Twój kod operuje na danych, które przecinają granicę zaufania, zalecamy użycie opcji **/Qspectre** , aby skompilować i ponownie wdrożyć kod w celu ograniczenia tego problemu tak szybko, jak to możliwe. Przykładem takiego kodu jest kod, który ładuje niezaufane dane wejściowe, które mogą mieć wpływ na wykonanie. Na przykład kod, który wykonuje zdalne wywołania procedury, analizuje niezaufane dane wejściowe lub pliki lub korzysta z innych interfejsów komunikacji lokalnej między procesami (IPC). Standardowe techniki piaskownicy mogą być niewystarczające. Uważnie Zbadaj piaskownicy przed podjęciem decyzji, że kod nie przekracza granicy zaufania.

### <a name="availability"></a>Dostępność

Opcja **/Qspectre** jest dostępna w programie Visual Studio 2017 w wersji 15.5.5 i we wszystkich aktualizacjach kompilatorów Microsoft C++ (MSVC) wykonanych w dniu lub po 23 stycznia 2018. Użyj Instalator programu Visual Studio, aby zaktualizować kompilator i zainstalować biblioteki z ograniczeniami Spectre jako poszczególne składniki. Opcja **/Qspectre** jest również dostępna w programie Visual Studio 2015 Update 3 za pomocą poprawki. Aby uzyskać więcej informacji, zobacz [artykuł KB 4338871](https://support.microsoft.com/help/4338871).

Wszystkie wersje programu Visual Studio 2017 w wersji 15,5 oraz zapoznaj się ze wszystkimi wersjami zapoznawczymi programu Visual Studio 2017 w wersji 15,6. Uwzględnij nieudokumentowaną opcję, **/d2guardspecload**. Jest to równoważne z początkowym zachowaniem **/Qspectre**. Możesz użyć **/d2guardspecload** , aby zastosować te same środki zaradcze do kodu w tych wersjach kompilatora. Zalecamy zaktualizowanie kompilacji tak, aby korzystała z **/Qspectre** w kompilatorach, które obsługują tę opcję. Opcja **/Qspectre** może również obsługiwać nowe środki zaradcze w nowszych wersjach kompilatora.

### <a name="effect"></a>Efekt

Opcja **/Qspectre** wyprowadza kod w celu ograniczenia Specter wariant 1, Pominięcie sprawdzania granic, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Działa po wstawieniu instrukcji, które działają jako spekulacyjnej bariery wykonywania kodu. Szczegółowe instrukcje stosowane w celu ograniczenia spekulacji procesora zależą od procesora i jego mikroarchitektury oraz mogą ulec zmianie w przyszłych wersjach kompilatora.

Po włączeniu opcji **/Qspectre** kompilator próbuje zidentyfikować wystąpienia, w przypadku których wykonanie spekulacyjne może ominąć ograniczenia. Jest to miejsce, w którym wstawia instrukcje dotyczące bariery. Ważne jest, aby mieć świadomość limitów analizy, które kompilator może wykonać, aby zidentyfikować wystąpienia wariantu 1. W związku z tym nie ma gwarancji, że wszystkie możliwe wystąpienia wariantu 1 są Instrumentacją w ramach **/Qspectre**.

### <a name="performance-impact"></a>Wpływ na wydajność

Wpływ na wydajność **/Qspectre** okazał się nieznaczny w kilku bazach kodu o zmiennym rozmiarze. Nie ma jednak gwarancji, że wydajność kodu w obszarze **/Qspectre** pozostaje bez zmian. Należy przeprowadzić test porównawczy kodu, aby określić efekt opcji wydajności. Jeśli wiadomo, że środki zaradcze nie są wymagane w bloku lub pętli krytycznej dla wydajności, można wybiórczo wyłączyć środki zaradcze przy użyciu dyrektywy [__declspec (Spectre (nozaradcze))](../../cpp/spectre.md) . Ta dyrektywa nie jest dostępna w kompilatorach, które obsługują tylko opcję **/d2guardspecload** .

### <a name="required-libraries"></a>Wymagane biblioteki

Opcja kompilatora **/Qspectre** generuje kod, który niejawnie łączy wersje bibliotek środowiska uruchomieniowego utworzonych w celu zapewnienia Spectreych środków zaradczych. Te biblioteki są opcjonalnymi składnikami, które muszą zostać zainstalowane przy użyciu Instalator programu Visual Studio:

- MSVC wersja *version_numbers* libs dla Spectre \[(x86 i x64) | (ARM) | (ARM64)]
- Visual C++ ATL dla \[(x86/x64) | ARM | ARM64] z ograniczeniami Spectre
- Visual C++ MFC dla \[procesorów x86/x64 | ARM | ARM64] z ograniczeniami Spectre

Jeśli kompilujesz kod przy użyciu **/Qspectre** , a te biblioteki nie są zainstalowane, system kompilacji raportuje **MSB8038: Spectre ograniczenie jest włączone, ale nie znaleziono**bibliotek z ograniczeniami Spectre. Jeśli kompilacja kodu MFC lub ATL nie powiedzie się, a konsolidator zgłosi błąd, taki jak **błąd krytyczny LNK1104: nie można otworzyć pliku "OLDNAMES. lib"** , te brakujące biblioteki mogą być przyczyną.

### <a name="additional-information"></a>Dodatkowe informacje

Aby uzyskać więcej informacji, zapoznaj się z oficjalnym [poradnikiem dotyczącym zabezpieczeń firmy Microsoft ADV180002, aby wyeliminować luki w](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)zabezpieczeniach. Wskazówki są również dostępne na stronie rozwiązania do rozwiązywania [problemów](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)z technologią firmy Intel, spekulacyjnym i rozłożenia w [pamięci](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)podręcznej. Aby uzyskać omówienie rozwiązań Spectre i Meltdown związanych z systemem Windows, zobacz [Opis wpływu na wydajność Spectre i Meltdown w systemach Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Aby zapoznać się z omówieniem luk w zabezpieczeniach Spectre, które są rozwiązywane przez środki zaradcze MSVC, C++ zobacz [Spectre (ograniczenia w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) ) na blogu zespołu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **C/C++**  > **wiersz polecenia** .

1. Wprowadź opcję kompilatora **/Qspectre** w polu **dodatkowe opcje** . Wybierz **przycisk OK** , aby zastosować zmianę.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
