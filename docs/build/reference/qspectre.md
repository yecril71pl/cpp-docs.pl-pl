---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e0d3af50015b77af297cbee22f439cd17d803de9
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344151"
---
# <a name="qspectre"></a>/Qspectre

Określa Generowanie kompilatora instrukcje eliminowanie luk w zabezpieczeniach określone luki Spectre w wariancie 1.

## <a name="syntax"></a>Składnia

> **/Qspectre**

## <a name="remarks"></a>Uwagi

**/Qspectre** opcja jest dostępna w programie Visual Studio 2017, wersja 15.5.5 później i w Visual Studio 2015 Update 3 za pomocą [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Sprawia, że kompilator, aby wstawić instrukcje, aby uniknąć pewnych [luk w zabezpieczeniach Spectre](https://spectreattack.com/spectre.pdf). Te luki w zabezpieczeniach są nazywane *ataków kanału po stronie wykonywania spekulacyjnego*. Wpływają na wiele systemów operacyjnych i nowoczesnych procesorów, takich jak procesory Intel, AMD i ARM.

**/Qspectre** opcja jest domyślnie wyłączona.

W wersji początkowej **/qspectre** opcji tylko prace zoptymalizowanego kodu. W programie Visual Studio 2017 wersji 15.7 lub nowszej **/qspectre** opcja jest obsługiwana na wszystkich poziomach optymalizacji.

Microsoft Visual C++ bibliotek są również dostępne w wersji z krokami zaradczymi dla luki środki zaradcze. W Instalatorze programu Visual Studio można pobrać biblioteki zminimalizować luki Spectre dla programu Visual Studio 2017 i nowszych. Znajdzie w **poszczególne składniki** karcie **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe**, i mieć "Libs dla luki Spectre" w nazwie. Biblioteki DLL i bibliotek statycznych środowiska uruchomieniowego za pomocą ograniczenia włączone są dostępne dla podzbioru środowiska uruchomieniowego Visual C++: Kod startowy VC ++, vcruntime140, msvcp140, concrt140 i vcamp140. Biblioteki DLL są obsługiwane tylko wdrożenia lokalnego aplikacji. Zawartość wizualizacji C++ 2017 i nowsze środowiska uruchomieniowego bibliotek do dystrybucji nie zostały zmodyfikowane.

Można także zainstalować biblioteki zminimalizować luki Spectre dla MFC i ATL. Znajdzie w **poszczególne składniki** karcie **zestawów SDK, bibliotek i struktur**.

### <a name="applicability"></a>Możliwości zastosowania

Jeśli Twój kod działa na danych w granicy zaufania, a następnie zalecane jest użycie **/qspectre** opcję, aby ponownie skompiluj i wdróż swój kod, aby jak najszybciej rozwiązać ten problem. Przykładem takiego kodu jest kod, który ładuje niezaufane dane wejściowe, które mogą mieć wpływ na wykonanie. Na przykład kod, który sprawia, że procedury zdalnej wywołuje, analizuje niezaufane dane wejściowe lub pliki lub korzysta z innych interfejsów lokalnej komunikacji międzyprocesowej (IPC). Piaskownicy standardowych technik może nie być wystarczające. Piaskownice usługi należy dokładnie zbadać, zanim zdecydujesz, że Twój kod nie cross granicy zaufania.

### <a name="availability"></a>Dostępność

**/Qspectre** opcja jest dostępna w Visual Studio 2017, wersja 15.5.5 i wszystkie aktualizacje do firmy Microsoft C++ kompilatory (MSVC), wprowadzone na lub po 23 stycznia 2018 r. Użyj Instalatora programu Visual Studio, aby zaktualizować kompilator i zainstalowanie biblioteki skorygowane z krokami zaradczymi dla luki jako poszczególnych składników. **/Qspectre** opcja jest również dostępna w programie Visual Studio 2015 Update 3 za pomocą poprawek. Aby uzyskać więcej informacji, zobacz [KB 4338871](https://support.microsoft.com/help/4338871).

Wszystkie wersje programu Visual Studio 2017 w wersji 15.5 i wszystkich wersji zapoznawczych programu Visual Studio 2017 w wersji 15.6. Nieudokumentowany opcją **/d2guardspecload**. Jest to równoważne zachowanie początkowej **/qspectre**. Możesz użyć **/d2guardspecload** do zastosowania tych samych środki zaradcze w kodzie w tych wersjach kompilatora. Firma Microsoft zaleca, zaktualizuj kompilacji, aby użyć **/qspectre** w kompilatory, które obsługują opcję. **/Qspectre** opcji mogą także obsługiwać nowe środki zaradcze w nowszych wersjach kompilatora.

### <a name="effect"></a>Efekt

**/Qspectre** opcja generuje kod, aby uniknąć Specter wariantu 1, Pomiń sprawdzanie granic [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Działa przez wstawienie instrukcji, które działają jako czynnik blokujący wykonywania spekulacyjnego kodu. Szczegółowe instrukcje zastosować, aby zminimalizować wstawiał procesora są zależne od procesora i jego mikro architektura i mogą ulec zmianie w przyszłych wersjach kompilatora.

Po włączeniu **/qspectre** opcja, kompilator próbuje identyfikować wystąpienia, gdzie związanego z wykonywaniem spekulatywnym może pominąć sprawdzanie granic. To, gdzie wstawia instrukcje dotyczące zapory. Należy mieć świadomość limity do analizy, które kompilator może zrobić, aby identyfikować wystąpienia w wariancie 1. W efekcie nie ma żadnej gwarancji, które działają w ramach wszystkich możliwych wystąpień w wariancie 1 **/qspectre**.

### <a name="performance-impact"></a>Wpływ na wydajność

Gdy wpływ wydajności **/qspectre** wydawało się być nieznaczny w wielu bazach kodu może być zmieniany. Istnieją jednak żadnej gwarancji taką wydajność Twój kod w ramach **/qspectre** pozostaje bez zmian. Należy testu porównawczego swój kod definiujący wpływu opcji na wydajność. Jeśli wiesz, że środki zaradcze nie jest wymagane w bloku newralgicznym dla wydajności lub pętli, środki zaradcze selektywnie można wyłączyć przy użyciu [__declspec(spectre(nomitigation))](../../cpp/spectre.md) dyrektywy. Ta dyrektywa nie jest dostępna w kompilatorach, które obsługują tylko **/d2guardspecload** opcji.

### <a name="required-libraries"></a>Wymaganych bibliotek

**/Qspectre** kompilator generuje kod, który niejawnie łączy wersje bibliotek środowiska uruchomieniowego, utworzona w celu zapewnienia krokami zaradczymi dla luki spectre. Biblioteki te są opcjonalne składniki, które muszą być zainstalowane za pomocą Instalatora programu Visual Studio:

- Wersji MSVC *version_numbers* Libs luki Spectre dla \[(x86 i x64) | (ARM) | (ARM64)]
- Wizualne C++ ATL dla \[— x86/x64 64 | ARM | ARM64] z krokami zaradczymi dla luki Spectre
- Wizualne C++ MFC dla \[x86/x64 | ARM | ARM64] z krokami zaradczymi dla luki Spectre

Jeśli tworzysz swój kod za pomocą **/qspectre** biblioteki te nie są zainstalowane, raporty systemu kompilacji **ostrzeżenie MSB8038: Spectre jest włączona, ale nie można odnaleźć bibliotek łagodzeń Spectre**. Jeśli kodu biblioteki ATL i MFC nie powiedzie się do tworzenia i konsolidator zgłasza błąd, taki jak **błąd krytyczny LNK1104: nie można otworzyć pliku "oldnames.lib"** , przyczyną może być Brak biblioteki.

### <a name="additional-information"></a>Dodatkowe informacje

Aby uzyskać więcej informacji można znaleźć w oficjalnej [ADV180002 poradnik zabezpieczeń firmy Microsoft, wskazówek, aby eliminowanie luk w zabezpieczeniach z wykonywaniem spekulatywnym kanału po stronie](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Wskazówki dotyczące jest również dostępna z Intel, [spekulacyjnego Spectre kanału po stronie wykonywania](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)i ARM, [wstawiał pamięci podręcznej po stronie Kanały](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Aby uzyskać przegląd specyficzne dla Windows z krokami zaradczymi dla luki i Meltdown środki zaradcze, zobacz [zrozumienie wpływu na wydajność z krokami zaradczymi dla luki i Meltdown środki zaradcze w systemach Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Omówienie luk w zabezpieczeniach Spectre odnoszącego środki zaradcze MSVC, zobacz [krokami zaradczymi dla luki spectre w MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) na C++ Blog zespołu ds.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++**  > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/qspectre** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
