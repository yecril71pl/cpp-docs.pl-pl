---
title: /O Opcje (optymalizuj kod)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: f4e2bf8b848654f7b87c59e7a54994448ee62d51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481331"
---
# <a name="o-options-optimize-code"></a>/O Opcje (optymalizuj kod)

**/O** opcje umożliwiają kontrolowanie różne optymalizacje, które ułatwiają tworzenie kodu dla szybkości maksymalnego lub minimalnego rozmiaru.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji, które generują kod minimalny rozmiar.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji optymalizuje kod dla prędkości maksymalnej.

- [/OB](../../build/reference/ob-inline-function-expansion.md) kontroluje wbudowane rozwijanie funkcji.

- [/Od](../../build/reference/od-disable-debug.md) wyłącza optymalizację kompilacji i upraszczaj debugowanie.

- [/Og](../../build/reference/og-global-optimizations.md) włącza optymalizacje globalne.

- [/OI](../../build/reference/oi-generate-intrinsic-functions.md) generuje funkcje wewnętrzne dla wywołań funkcji odpowiednie.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) informuje kompilator, aby preferował optymalizacje dla rozmiaru nad optymalizacje dla danej szybkości.

- [/OT](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (ustawienie domyślne) informuje kompilator, aby preferował optymalizacje dla danej szybkości nad optymalizacje dla rozmiaru.

- [Ox](../../build/reference/ox-full-optimization.md) to opcja kombinacja, która wybiera kilka optymalizacji, ze szczególnym uwzględnieniem szybkości. Jest ścisłym podzbiorem **/O2** optymalizacji.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) pomija tworzenie wskaźników ramek na stosie wywołań do szybszego wywołania funkcji.

## <a name="remarks"></a>Uwagi

Można połączyć wiele **/O** opcje w instrukcji pojedynczego opcję. Na przykład **/Odi** jest taka sama jak **/Od /Oi**. Niektóre opcje wykluczają się wzajemnie i spowodują błąd kompilatora, jeśli używane razem. Zobacz poszczególnych **/O** opcje, aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)