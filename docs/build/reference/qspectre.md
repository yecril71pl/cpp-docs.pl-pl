---
title: / Qspectre | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
f1_keywords: /Qspectre
helpviewer_keywords: /Qspectre
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b114239ad57b484c9290fbe1cc2f0ae18cb565ec
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="qspectre"></a>/ Qspectre

Określa Generowanie kompilatora instrukcji w celu ograniczenia pewnych luk w zabezpieczeniach wariantu 1 Spectre.

## <a name="syntax"></a>Składnia

> **/Qspectre**

## <a name="remarks"></a>Uwagi

**/Qspectre** opcja powoduje, że kompilator, aby wstawić instrukcje w celu ograniczenia pewnych [luk w zabezpieczeniach Spectre](https://spectreattack.com/spectre.pdf). Te luki w zabezpieczeniach, nazywany *ataków kanału po stronie rozważana wykonywania*, wpływ na wiele systemów operacyjnych i nowoczesne procesorów, w tym procesorów Intel, AMD i ARM.

**/Qspectre** opcja jest domyślnie wyłączona.

Wydanie początkowej **/Qspectre** opcja działa tylko na zoptymalizowanego kodu. Upewnij się skompilować kodu za pomocą opcji optymalizacji (na przykład [/O2 lub/O1](o1-o2-minimize-size-maximize-speed.md) , ale nie [/Od](od-disable-debug.md)) do upewnij się, że zastosowano środki zaradcze. Podobnie, sprawdź każdy kod, który używa [zoptymalizować #pragma ("stg", off)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Możliwość zastosowania

Jeśli kod działa na danych w granicy zaufania, firma Microsoft zaleca użycie **/Qspectre** opcję, aby ponowne skompilowanie i wdrożenie swój kod, aby zminimalizować ten problem tak szybko, jak to możliwe. Kod, który działa na danych w granicy zaufania przykładów kodu, który ładuje niezaufanych danych wejściowych, co może wpłynąć na wykonanie, na przykład kodu, który sprawia, że procedury zdalnej wywołuje, analizuje niezaufanych danych wejściowych lub plików lub korzysta z innego procesu, między lokalnym Komunikacja między interfejsów. Techniki sandboxing standardowa nie może być wystarczające. Twoje piaskownic należy zbadać dokładnie przed podjęciem decyzji, czy kod nie przecina granicę zaufania.

### <a name="availability"></a>Dostępność

**/Qspectre** opcja jest dostępna w wersji Visual Studio 2017 15.5.5 i wszystkie aktualizacje Kompilatory języka Microsoft Visual C++ (MSVC) na lub po 23 stycznia 2018.

Wszystkie wersje wersji programu Visual Studio 2017 15.5 i wszystkie funkcje w wersji zapoznawczej programu Visual Studio wersji 15,6 już jest dostępna opcja nieudokumentowanej, **/d2guardspecload**, który jest odpowiednikiem początkowe zachowanie **/Qspectre**. Można użyć **/d2guardspecload** do zastosowania tego samego środki zaradcze w kodzie w tych wersjach kompilatora. Zaktualizuj kompilację w celu użycia **/Qspectre** w kompilatorów wspierających opcji; **/Qspectre** opcji mogą obsługiwać nowe środki zaradcze w nowszych wersjach kompilatora.

### <a name="effect"></a>Efekt

**/Qspectre** opcja generuje kod, aby ograniczyć Specter wariantu 1, Pomiń sprawdzanie granice [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Jej działanie polega na wstawiania instrukcji pełniących rolę bariery wykonywania rozważana kodu. Szczegółowe instrukcje, które są używane w celu złagodzenia spekulacji procesora zależą od procesora i jego micro architektura i mogą ulec zmianie w przyszłych wersjach kompilatora.

Gdy **/Qspectre** jest włączona opcja, kompilator próbuje określić wystąpień, których wykonanie rozważana może pominąć sprawdzanie granic i wstawia instrukcje bariery. Należy pamiętać, że ma ograniczeń dotyczących analizy, które można wykonać kompilatora, aby zidentyfikować wystąpienia wariantu 1. W efekcie nie ma żadnej gwarancji, że wszystkie możliwe wystąpienia wariantu 1 są instrumentowane w obszarze **/Qspectre**.

### <a name="performance-impact"></a>Wpływ na wydajność

Jego wpływ na wydajność **/Qspectre** została napotkana bez znaczenia w kilku bardzo dużych baz kodu, ale nie ma żadnych gwarancji wydajności tego kodu w obszarze **/Qspectre** nie ma wpływu. Należy testu wydajności swój kod definiujący wpływu opcji na wydajność. Jeśli znasz łagodzenie nie jest wymagane w bloku krytyczne wydajności lub pętla, łagodzenie można selektywnie wyłączyć przy użyciu [__declspec(spectre(nomitigation))](../../cpp/spectre.md) dyrektywy. Ta dyrektywa jest niedostępne w kompilatorów, które obsługują tylko **/d2guardspecload** opcji.

### <a name="additional-information"></a>Dodatkowe informacje

Dla bardziej szczegółowe informacje można znaleźć pod adresem urzędnika [ADV180002 poradnik zabezpieczeń firmy Microsoft, wskazówki w celu ograniczenia wykonywania rozważana kanału po stronie luk w zabezpieczeniach](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Wskazówki dotyczące jest również dostępna z Intel, [kanału po stronie rozważana wykonywania środki zaradcze](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)i ARM, [spekulacji pamięci podręcznej po stronie Kanały](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Omówienie Spectre i Meltdown środki zaradcze aplikacji systemu Windows, zobacz [opis wpływu na wydajność Spectre i Meltdown środki zaradcze w systemach Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) na blogu Secure firmy Microsoft. Omówienie Spectre luki w zabezpieczeniach dotyczy środki zaradcze MSVC, zobacz [środki zaradcze Spectre w MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) na blogu zespołu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Wprowadź **/Qspectre** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** do zastosowania zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
