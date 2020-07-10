---
title: /O Opcje (Optymalizuj kod)
description: Opcje kompilatora MSVC/O określają optymalizacje kompilatora, które mają być używane.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: 36ef582787a3ec2d7aee1e589c70b48712d9d552
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180880"
---
# <a name="o-options-optimize-code"></a>`/O`Opcje (Optymalizuj kod)

**`/O`** Opcje kontrolują różne optymalizacje, które ułatwiają tworzenie kodu dla maksymalnej szybkości lub minimalnej wielkości.

- [`/O1`](o1-o2-minimize-size-maximize-speed.md)Ustawia kombinację optymalizacji generującej kod rozmiaru minimalnego.

- [`/O2`](o1-o2-minimize-size-maximize-speed.md)Ustawia kombinację optymalizacji, która optymalizuje kod w celu uzyskania maksymalnej prędkości.

- [`/Ob`](ob-inline-function-expansion.md)steruje rozwinięciem funkcji wbudowanych.

- [`/Od`](od-disable-debug.md)wyłącza optymalizację, aby przyspieszyć kompilację i uprościć debugowanie.

- [`/Og`](og-global-optimizations.md)(przestarzałe) umożliwia optymalizacje globalne.

- [`/Oi`](oi-generate-intrinsic-functions.md)generuje funkcje wewnętrzne dla odpowiednich wywołań funkcji.

- [`/Os`](os-ot-favor-small-code-favor-fast-code.md)instruuje kompilator, aby preferuje optymalizacje dla rozmiaru przez optymalizacje.

- [`/Ot`](os-ot-favor-small-code-favor-fast-code.md)(ustawienie domyślne) informuje kompilator, aby preferuje optymalizacje dla szybkości większej niż Optymalizacja rozmiaru.

- [`/Ox`](ox-full-optimization.md)jest opcją kombinacją, która wybiera kilka optymalizacji z naciskiem na szybkość. **`/Ox`** jest ścisłym podzbiorem **`/O2`** optymalizacji.

- [`/Oy`](oy-frame-pointer-omission.md)pomija tworzenie wskaźników ramek na stosie wywołań w celu szybkiego wywołania funkcji.

## <a name="remarks"></a>Uwagi

Można połączyć wiele **`/O`** opcji w jedną instrukcję Option. Na przykład **`/Odi`** jest taka sama jak **`/Od /Oi`** . Niektóre opcje wykluczają się wzajemnie i powodują błąd kompilatora, jeśli są używane razem. Aby uzyskać więcej informacji, zobacz poszczególne **`/O`** Opcje.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
