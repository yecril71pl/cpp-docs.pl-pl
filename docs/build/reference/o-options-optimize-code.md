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
ms.openlocfilehash: ffd3023120f1d930a24ccef6fa297594062322df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320425"
---
# <a name="o-options-optimize-code"></a>/O Opcje (optymalizuj kod)

**/O** opcje umożliwiają kontrolowanie różne optymalizacje, które ułatwiają tworzenie kodu dla szybkości maksymalnego lub minimalnego rozmiaru.

- [/ O1](o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji, które generują kod minimalny rozmiar.

- [/ O2](o1-o2-minimize-size-maximize-speed.md) ustawia kombinacja optymalizacji optymalizuje kod dla prędkości maksymalnej.

- [/OB](ob-inline-function-expansion.md) kontroluje wbudowane rozwijanie funkcji.

- [/Od](od-disable-debug.md) wyłącza optymalizację kompilacji i upraszczaj debugowanie.

- [/Og](og-global-optimizations.md) włącza optymalizacje globalne.

- [/OI](oi-generate-intrinsic-functions.md) generuje funkcje wewnętrzne dla wywołań funkcji odpowiednie.

- [/OS](os-ot-favor-small-code-favor-fast-code.md) informuje kompilator, aby preferował optymalizacje dla rozmiaru nad optymalizacje dla danej szybkości.

- [/OT](os-ot-favor-small-code-favor-fast-code.md) (ustawienie domyślne) informuje kompilator, aby preferował optymalizacje dla danej szybkości nad optymalizacje dla rozmiaru.

- [Ox](ox-full-optimization.md) to opcja kombinacja, która wybiera kilka optymalizacji, ze szczególnym uwzględnieniem szybkości. Jest ścisłym podzbiorem **/O2** optymalizacji.

- [/Oy](oy-frame-pointer-omission.md) pomija tworzenie wskaźników ramek na stosie wywołań do szybszego wywołania funkcji.

## <a name="remarks"></a>Uwagi

Można połączyć wiele **/O** opcje w instrukcji pojedynczego opcję. Na przykład **/Odi** jest taka sama jak **/Od /Oi**. Niektóre opcje wykluczają się wzajemnie i spowodują błąd kompilatora, jeśli używane razem. Zobacz poszczególnych **/O** opcje, aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
