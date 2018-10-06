---
title: / Qspectre | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ed4b84ab761653dde4da6adcd14ec8e77334688
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821650"
---
# <a name="qspectre"></a>/ Qspectre

Określa Generowanie kompilatora instrukcje eliminowanie luk w zabezpieczeniach określone luki Spectre w wariancie 1.

## <a name="syntax"></a>Składnia

> **/Qspectre**

## <a name="remarks"></a>Uwagi

**/Qspectre** opcja jest dostępna w programie Visual Studio 2017, wersja 15.5.5 później i w Visual Studio 2015 Update 3 za pomocą [KB 4338871](https://support.microsoft.com/en-us/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Sprawia, że kompilator, aby wstawić instrukcje, aby uniknąć pewnych [luk w zabezpieczeniach Spectre](https://spectreattack.com/spectre.pdf). Te luki w zabezpieczeniach, o nazwie *ataków kanału po stronie wykonywania spekulacyjnego*, mają wpływ na wiele systemów operacyjnych i nowoczesnych procesorów, takich jak procesory Intel, AMD i ARM.

**/Qspectre** opcja jest domyślnie wyłączona.

W wersji początkowej **/qspectre** opcji tylko prace zoptymalizowanego kodu. W programie Visual Studio 2017 wersji 15.7 lub nowszej **/qspectre** opcja jest obsługiwana na wszystkich poziomach optymalizacji. 

Microsoft Visual C++ bibliotek są również dostępne w wersji z krokami zaradczymi dla luki środki zaradcze. W Instalatorze programu Visual Studio można pobrać biblioteki zminimalizować luki Spectre dla programu Visual Studio 2017. Znajdują się one w **poszczególne składniki** karcie **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe**, i mieć "Libs dla luki Spectre" w nazwie. Biblioteki DLL i bibliotek statycznych środowiska uruchomieniowego za pomocą ograniczenia włączone są dostępne dla podzbioru środowiska uruchomieniowego Visual C++: kod startowy VC ++, vcruntime140, msvcp140, concrt140 i vcamp140. Biblioteki DLL są obsługiwane w przypadku wdrożenia lokalnego aplikacji. zawartość 2017 środowiska uruchomieniowego bibliotek pakiet redystrybucyjny Visual C++ nie zostały zmodyfikowane. Można także zainstalować biblioteki zminimalizować luki Spectre dla MFC i ATL, znaleziono w **poszczególne składniki** karcie **zestawów SDK, bibliotek i struktur**.

### <a name="applicability"></a>Możliwości zastosowania

Jeśli Twój kod działa na danych w granicy zaufania, a następnie zaleca się, że używasz **/qspectre** opcję, aby ponownie skompiluj i wdróż swój kod, aby jak najszybciej rozwiązać ten problem. Kod, który operuje na danych w granicy zaufania przykłady kodu, który ładuje niezaufane dane wejściowe, które mogą mieć wpływ na wykonanie, na przykład, kod, który sprawia, że procedury zdalnej wywołuje, analizuje niezaufane dane wejściowe lub pliki lub korzysta z innego procesu, komunikacja między lokalnym interfejsy komunikacji (IPC). Piaskownicy standardowych technik może nie być wystarczające. Piaskownice usługi należy zbadać dokładnie, przed podjęciem decyzji, czy kod nie przekroczyć granicy zaufania.

### <a name="availability"></a>Dostępność

**/Qspectre** opcja jest dostępna w Visual Studio 2017, wersja 15.5.5 i wszystkie aktualizacje Kompilatory języka Microsoft Visual C++ (MSVC) wprowadzone na lub po 23 stycznia 2018 r. Użyj Instalatora programu Visual Studio, aby zaktualizować kompilator i zainstalowanie biblioteki skorygowane z krokami zaradczymi dla luki jako poszczególnych składników. **/Qspectre** opcja jest również dostępna w programie Visual Studio 2015 Update 3 za pomocą poprawek. Aby uzyskać więcej informacji, zobacz [KB 4338871](https://support.microsoft.com/help/4338871).

Wszystkie wersje programu Visual Studio 2017, wersja 15.5 i wszystkich wersji zapoznawczych programu Visual Studio 2017 w wersji 15.6 zawierać nieudokumentowane opcję **/d2guardspecload**, oznacza to odpowiednik początkowe zachowanie   **/qspectre**. Możesz użyć **/d2guardspecload** do zastosowania tych samych środki zaradcze w kodzie w tych wersjach kompilatora. Zaktualizuj kompilacji, aby użyć **/qspectre** w kompilatory, które obsługują opcję; **/qspectre** opcji mogą także obsługiwać nowe środki zaradcze w nowszych wersjach kompilatora.

### <a name="effect"></a>Efekt

**/Qspectre** opcja generuje kod, aby uniknąć Specter wariantu 1, Pomiń sprawdzanie granic [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Działa przez wstawienie instrukcji, które działają jako czynnik blokujący wykonywania spekulacyjnego kodu. Szczegółowe instrukcje zastosować, aby zminimalizować wstawiał procesora są zależne od procesora i jego mikro architektura i mogą ulec zmianie w przyszłych wersjach kompilatora.

Gdy **/qspectre** jest włączona opcja, kompilator próbuje identyfikować wystąpienia, gdzie związanego z wykonywaniem spekulatywnym może pominąć sprawdzanie granic i wstawia instrukcje dotyczące zapory. Należy zauważyć, że istnieją ograniczenia analizy, które kompilator może wykonywać do identyfikowania wystąpienia w wariancie 1. W efekcie nie ma żadnej gwarancji, które działają w ramach wszystkich możliwych wystąpień w wariancie 1 **/qspectre**.

### <a name="performance-impact"></a>Wpływ na wydajność

Gdy wpływ wydajności **/qspectre** został napotkany bez znaczenia w kilku bardzo dużych bazach kodu, ale istnieją nie gwarancje taką wydajność Twój kod w ramach **/qspectre** pozostaje bez zmian. Należy testu porównawczego swój kod definiujący wpływu opcji na wydajność. Jeśli znasz środki zaradcze nie jest wymagane w bloku newralgicznym dla wydajności lub pętli, środki zaradcze można selektywnie wyłączyć przy użyciu [__declspec(spectre(nomitigation))](../../cpp/spectre.md) dyrektywy. Ta dyrektywa nie jest dostępna w kompilatory, które obsługują tylko **/d2guardspecload** opcji.

### <a name="required-libraries"></a>Wymaganych bibliotek

**/Qspectre** kompilator generuje kod, który niejawnie łączy wersje bibliotek środowiska uruchomieniowego, które zostały skompilowane zapewnienie z krokami zaradczymi dla luki spectre. Biblioteki te są opcjonalne składniki, które muszą być zainstalowane za pomocą Instalatora programu Visual Studio:

- VC ++ 2017 w wersji *version_numbers* Libs luki Spectre dla \[(x86 i x64) | (ARM) | (ARM64)]
- Visual C++ ATL dla \[— x86/x64 64 | ARM | ARM64] z krokami zaradczymi dla luki Spectre
- Visual C++ MFC dla \[x86/x64 | ARM | ARM64] z krokami zaradczymi dla luki Spectre

Jeśli tworzysz swój kod za pomocą **/qspectre** i biblioteki te nie są zainstalowane, raporty systemu kompilacji **ostrzeżenie MSB8038: spectre jest włączona, ale nie można odnaleźć bibliotek łagodzeń Spectre**. W przypadku kodu biblioteki ATL i MFC awarii do tworzenia i konsolidator zgłasza błąd, taki jak **błąd krytyczny LNK1104: nie można otworzyć pliku "oldnames.lib"**, przyczyną może być Brak biblioteki.

### <a name="additional-information"></a>Dodatkowe informacje

Aby uzyskać więcej informacji można znaleźć official będzie przydatna [ADV180002 poradnik zabezpieczeń firmy Microsoft, wskazówek, aby eliminowanie luk w zabezpieczeniach z wykonywaniem spekulatywnym kanału po stronie](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Wskazówki dotyczące jest również dostępna z Intel, [spekulacyjnego Spectre kanału po stronie wykonywania](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)i ARM, [wstawiał pamięci podręcznej po stronie Kanały](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Aby uzyskać przegląd specyficzne dla Windows z krokami zaradczymi dla luki i Meltdown środki zaradcze, zobacz [zrozumienie wpływu na wydajność z krokami zaradczymi dla luki i Meltdown środki zaradcze w systemach Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) na blogu Microsoft Secure. Omówienie luk w zabezpieczeniach Spectre odnoszącego środki zaradcze MSVC, zobacz [krokami zaradczymi dla luki spectre w MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) na blogu zespołu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/qspectre** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
