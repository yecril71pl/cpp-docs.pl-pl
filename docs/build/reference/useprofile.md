---
title: / Opcję USEPROFILE (PGO użycia danych za pomocą LTCG) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156a571eaa3db31b8c5345f1550346503651665d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377996"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ Opcję USEPROFILE (Uruchom PGO w trybie awaryjnym wątków)

Tej opcji konsolidatora wraz z [opcję/LTCG (Generowanie kodu w czasie konsolidacji](ltcg-link-time-code-generation.md) informuje konsolidator, aby utworzyć przy użyciu danych szkoleniowych Optymalizacja sterowana profilem — (PGO).

## <a name="syntax"></a>Składnia

> **/ Opcję USEPROFILE**[**:**{**AGRESYWNA**|**PGD =**_filename_}]

### <a name="arguments"></a>Argumenty

**AGRESYWNE**<br/>
Ten opcjonalny argument określa, że aktywnego prędkości optymalizacji powinny być używane podczas zoptymalizowane generowanie kodu.

**PGD**=*filename*<br/>
Określa nazwę pliku podstawowego plik .pgd. Domyślnie konsolidator użyta zostanie nazwa podstawowego pliku wykonywalnego z rozszerzeniem .pgd.

## <a name="remarks"></a>Uwagi

**/USEPROFILE** — opcja konsolidatora jest używany razem z **opcję/LTCG** do generowania lub zaktualizować optymalizowania kompilacji, na podstawie danych szkoleniowych PGO. Jest odpowiednikiem przestarzałe **/LTCG:PGUPDATE** i **/LTCG:PGOPTIMIZE** opcje.

Opcjonalny **AGRESYWNA** argument wyłącza odnoszące się do rozmiaru heurystyki prób Optymalizacja szybkości. Może to spowodować, że funkcje optymalizacji, które znacznie zwiększyć rozmiar pliku wykonywalnego, a nie może zwiększyć szybkość wynikowy. Należy profilu i porównywania wyników przy użyciu i nie **AGRESYWNA**. Ten argument musi zostać określone jawnie; nie jest włączona domyślnie.

**PGD** argument określa opcjonalną nazwę dla pliku .pgd danych szkoleniowych do użycia, takie same jak w [opcji/genprofile lub /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Jest odpowiednikiem przestarzałe **/PGD** przełącznika. Domyślnie lub jeśli nie *filename* jest określona, plik .pgd, który ma taką samą nazwę podstawową jak plik wykonywalny jest używany.

**/USEPROFILE** — opcja konsolidatora jest nowa w programie Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** strony właściwości.

1. W **generowanie kodu w czasie konsolidacji** właściwości, wybierz **Użyj generowanie kodu w czasie konsolidacji (/ LTCG)**.

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wprowadź **/USEPROFILE** opcji i opcjonalne argumenty do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/ Opcję GENPROFILE i /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
