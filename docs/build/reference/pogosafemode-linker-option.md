---
title: / POGOSAFEMODE (uruchamianie PGO w trybie awaryjnym wątku)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: f210884d693ef0d778943580b9c5a7b2ec2ea336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544433"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (uruchamianie PGO w trybie awaryjnym wątku)

**Opcja /POGOSAFEMODE jest przestarzały, począwszy od programu Visual Studio 2015**. Użyj [przełączników/genprofile: dokładnie](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) i **/GENPROFILE:NOEXACT** zamiast opcji. **/POGOSAFEMODE** — opcja konsolidatora Określa, że kompilację instrumentowaną do używania trybu wątków dla profilu przechwytywania danych podczas profilowana Optymalizacja (PGO) wysyłanie przebiegów szkoleniowych.

## <a name="syntax"></a>Składnia

> **/POGOSAFEMODE**

## <a name="remarks"></a>Uwagi

Profilowana Optymalizacja (PGO) ma dwa możliwe tryby podczas fazy profilowania: *trybie szybkim* i *tryb awaryjny*. Gdy profilowanie odbywa się w trybie szybkim, wykorzystuje instrukcję przyrostu Aby zwiększyć liczniki danych. Instrukcja przyrost jest szybsze, ale nie jest metodą o bezpiecznych wątkach. Gdy profilowanie odbywa się w trybie awaryjnym, aby zwiększyć liczniki danych używa instrukcji blokowanej przyrostu. Ta instrukcja ma taką samą funkcjonalność instrukcji przyrostu ma i jest bezpieczna dla wątków, ale jest wolniejsze.

**/POGOSAFEMODE** opcja umożliwia ustawienie kompilację instrumentowaną do pracy w trybie awaryjnym. Ta opcja może być tylko używane podczas przestarzałego [pginstrument](ltcg-link-time-code-generation.md) określono w fazie konsolidatora Instrumentacja optymalizacji PGO.

Domyślnie profilowanie PGO działa w trybie szybkim. **/ POGOSAFEMODE** jest wymagany tylko, jeśli chcesz użyć trybu awaryjnego.

Aby uruchomić profilowanie PGO w trybie awaryjnym, należy użyć **przełączników/genprofile: dokładnie** (preferowany) lub użyć zmiennej środowiskowej [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md) lub przełącznika konsolidatora **/POGOSAFEMODE**, w zależności od systemu. Jeśli przeprowadzasz profilowanie na x64 komputera, musisz użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na x86 komputera, możesz użyć przełącznika konsolidatora lub zdefiniować zmienną środowiskową na dowolną wartość, przed rozpoczęciem procesu Instrumentacji PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** stronę właściwości.

1. W **łączonych kodów czasowych** właściwości, wybierz **profilowana Optymalizacja - Instrument (/ LTCG: pginstrument)**.

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/POGOSAFEMODE** opcji do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/ GENPROFILE i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
