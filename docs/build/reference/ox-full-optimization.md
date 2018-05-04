---
title: -Ox (Włącz większości prędkości optymalizacji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 569563bff030904988e93db749438eaeb58ce9db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ox-enable-most-speed-optimizations"></a>OX (Włącz większości prędkości optymalizacji)

**Ox** kombinacja optymalizacji, które Preferuj prędkość włącza opcję kompilatora. W niektórych wersjach programu Visual Studio IDE i komunikat pomocy kompilatora, jest to *Pełna optymalizacja*, ale **ox** tylko podzbiór opcje optymalizacji szybkości włączane przez umożliwia — opcja kompilatora **/O2**.

## <a name="syntax"></a>Składnia

> OX

## <a name="remarks"></a>Uwagi

**Ox** włącza opcję kompilatora **/O** prędkości Preferuj opcji kompilatora. **Ox** — opcja kompilatora nie ma dodatkowych [/GF (eliminowanie ciągów zduplikowanych)](../../build/reference/gf-eliminate-duplicate-strings.md) i [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md) opcji włączane przez [/O1 lub/O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Dodatkowe opcje, które są stosowane przez **/O1** i **/O2** może spowodować wskaźników do ciągów lub funkcji udostępniania adresu docelowego, który może mieć wpływ na debugowanie i zgodność języka strict. **Ox** opcja jest prosty sposób Włącz optymalizacje większości bez uwzględniania **/GF** i **/Gy**. Aby uzyskać więcej informacji, zobacz opis [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) i [/Gy](../../build/reference/gy-enable-function-level-linking.md) opcje.

**Ox** — opcja kompilatora jest taka sama jak w połączeniu przy użyciu następujących opcji:

- [/OB (rozszerzenie funkcji wbudowanej)](../../build/reference/ob-inline-function-expansion.md), gdzie parametr opcji jest 2 (**/ob2**)

- [/Og (Optymalizacje globalne)](../../build/reference/og-global-optimizations.md)

- [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/OT (Preferuj szybki kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (pominięcie wskaźnika ramki)](../../build/reference/oy-frame-pointer-omission.md)

**Ox** się wzajemnie z:

- [/ O1 (Minimalizuj rozmiar)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md)

Możesz anulować odchylenia kierunku szybkości **ox** — opcja kompilatora Jeśli określisz **/Oxs**, który łączy **ox** — opcja kompilatora z  [ /OS (Preferuj mały Kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Opcje Scalonej Preferuj mniejszego rozmiaru kodu.

Aby zastosować wszystkie dostępne optymalizacje poziomu plików dla wersji kompilacji, firma Microsoft zaleca, należy określić [/O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast **ox**, i [/O1 (Minimalizuj rozmiar)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast niego z **/Oxs**. Aby jeszcze bardziej optymalizacji w wersji kompilacji, należy również rozważyć [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora i [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md) — opcja konsolidatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** strony właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)