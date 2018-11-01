---
title: / USEPROFILE (dane PGO korzystanie z funkcji LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 4b780bed3b92b874f2bf18fb0235e8e2baf95ae9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550634"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (uruchamianie PGO w trybie awaryjnym wątku)

Tę opcję konsolidatora wraz z [opcję/LTCG (Generowanie kodu w czasie konsolidacji](ltcg-link-time-code-generation.md) informuje konsolidator, aby tworzyć przy użyciu danych szkoleniowych profilowana Optymalizacja (PGO).

## <a name="syntax"></a>Składnia

> **/ USEPROFILE**[**:**{**AGRESYWNE**|**PGD =**_filename_}]

### <a name="arguments"></a>Argumenty

**AGRESYWNE**<br/>
Ten opcjonalny argument określa, że optymalizacji szybkości agresywne powinny być używane podczas generowania zoptymalizowanego kodu.

**Plik PGD**=*nazwy pliku*<br/>
Określa nazwę pliku podstawowego pliku .pgd. Domyślnie konsolidator używa nazwa podstawowa pliku wykonywalnego z rozszerzeniem .pgd.

## <a name="remarks"></a>Uwagi

**/USEPROFILE** — opcja konsolidatora jest używany razem z **opcję/LTCG** można wygenerować lub zaktualizować optymalizowania kompilacji, na podstawie danych szkoleniowych PGO. Jest to równoważne z przestarzałego **/LTCG:PGUPDATE** i **/LTCG:PGOPTIMIZE** opcje.

Opcjonalny **AGRESYWNE** argument wyłącza dotyczących rozmiaru Algorytm heurystyczny, aby podjąć próbę Optymalizuj pod kątem szybkości. Może to spowodować optymalizacje, które znacznie zwiększyć rozmiar plik wykonywalny i nie może zwiększyć szybkość wynikowe. Należy profilowania i porównać wyniki przy użyciu i nie używa **AGRESYWNE**. Ten argument muszą być jawnie; określone. nie włączono domyślnie.

**PGD** argument określa nazwę opcjonalną dla pliku .pgd danych szkolenia użyto tych samych, jak w [przełączników/genprofile i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Jest to równoważne z przestarzałego **/PGD** przełącznika. Domyślnie lub jeśli nie *filename* jest określony, plik .pgd, który ma taką samą nazwę pliku wykonywalnego, który jest używany.

**/USEPROFILE** — opcja konsolidatora jest nowa w programie Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** stronę właściwości.

1. W **łączonych kodów czasowych** właściwości, wybierz **Użyj łączonych kodów czasowych (/ LTCG)**.

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/USEPROFILE** opcja i opcjonalne argumenty do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/ GENPROFILE i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
