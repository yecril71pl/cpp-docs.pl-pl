---
title: / POGOSAFEMODE (Uruchom PGO w trybie awaryjnym wątku) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- POGOSAFEMODE
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 886fbae5fbeb7606ec0321595f061d2262988170
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (Uruchom PGO w trybie awaryjnym wątków)

**Opcja /POGOSAFEMODE jest przestarzały, począwszy od programu Visual Studio 2015**. Użyj [opcji/genprofile: dokładne](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) i **/GENPROFILE:NOEXACT** zamiast tego opcje. **/POGOSAFEMODE** — opcja konsolidatora Określa, że instrumentowanej kompilacji do używania trybu wątkowo dla profilu przechwytywania danych podczas optymalizacji sterowanych profilem (PGO) szkolenia działa.

## <a name="syntax"></a>Składnia

> **/POGOSAFEMODE**

## <a name="remarks"></a>Uwagi

Optymalizacja sterowana profilem — (PGO) ma dwa tryby możliwe podczas fazy profilowania: *trybu szybkiego* i *tryb awaryjny*. Podczas profilowania jest w trybie szybkiego, używa instrukcji przyrostu zwiększające danych liczników. Instrukcja przyrostu jest szybsze, ale nie jest bezpieczne wątkowo. Podczas profilowania jest w trybie awaryjnym, używa instrukcji blokowanej przyrostu zwiększające danych liczników. Ta instrukcja ma te same funkcje instrukcji przyrostu ma i wątkowo, ale jest wolniejsze.

**/POGOSAFEMODE** opcji ustawia instrumentowanej kompilacji do pracy w trybie awaryjnym. Ta opcja może być tylko używana, gdy przestarzałe [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) określono w fazie konsolidatora PGO instrumentacji.

Domyślnie profilowania PGO działa w trybie Szybkie. **/ POGOSAFEMODE** jest wymagane tylko, jeśli chcesz użyć trybu awaryjnego.

Aby uruchomić PGO profilowania w trybie awaryjnym, należy użyć jednego **opcji/genprofile: dokładne** (preferowane), lub użyj zmiennej środowiskowej [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md) lub przełącznik konsolidatora **/POGOSAFEMODE**, w zależności od systemu. Jeśli przeprowadzasz profilowanie na x64 komputera, należy użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na x86 komputera, możesz użyć przełącznik konsolidatora lub zdefiniować wartości zmiennej środowiskowej, przed rozpoczęciem procesu Instrumentacji PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** strony właściwości.

1. W **generowanie kodu w czasie konsolidacji** właściwości, wybierz **profilowana Optymalizacja — dokumentu (/ LTCG:PGInstrument)**.

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wprowadź **/POGOSAFEMODE** opcji do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/ Opcję GENPROFILE i /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)<br/>
[Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
