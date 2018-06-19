---
title: -O opcje (Optymalizuj kod) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83ddebec9db7a02db40ef31c89c7ff48a66cf665
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376803"
---
# <a name="o-options-optimize-code"></a>/O Opcje (optymalizuj kod)

**/O** opcje umożliwiają kontrolowanie różne funkcje optymalizacji, które ułatwiają tworzenie kodu dla szybkości maksymalnego lub minimalnego rozmiaru.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji, które generują minimalny rozmiar kodu.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji, który optymalizuje kod dla szybkości maksymalnej.

- [/OB](../../build/reference/ob-inline-function-expansion.md) steruje rozwijania funkcji śródwierszowych.

- [/Od](../../build/reference/od-disable-debug.md) wyłącza optymalizacji szybkości kompilacji i uprościć debugowania.

- [/Og](../../build/reference/og-global-optimizations.md) włącza optymalizacje globalne.

- [/OI](../../build/reference/oi-generate-intrinsic-functions.md) generuje funkcje wewnętrzne dla wywołań odpowiednią funkcję.

- [/ OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) informuje kompilator, aby preferował optymalizacji rozmiaru nad optymalizacji dla szybkości.

- [/OT](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (ustawienie domyślne) informuje kompilator, aby preferował optymalizacji dla szybkość nad optymalizacji rozmiaru.

- [Ox](../../build/reference/ox-full-optimization.md) to opcja kombinacja, która wybiera kilka optymalizacji, ze szczególnym uwzględnieniem szybkości. Jest ściśle podzbiór **/O2** optymalizacji.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) pomija tworzenie wskaźników ramek na stosie wywołań szybsze wywołania funkcji.

## <a name="remarks"></a>Uwagi

Można połączyć wiele **/O** opcje do instrukcji opcję. Na przykład **/Odi** jest taka sama jak **/Od /Oi**. Niektóre opcje wykluczają się wzajemnie i spowodować błąd kompilatora, jeżeli używane razem. Zobacz poszczególne **/O** opcje, aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)