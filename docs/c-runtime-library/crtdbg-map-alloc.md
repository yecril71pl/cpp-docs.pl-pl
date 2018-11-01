---
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: a6b6ca5d3e6fdc1bac43d082b0d7df5a87830050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453449"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Gdy **_CRTDBG_MAP_ALLOC** flaga jest zdefiniowany w wersji debugowania aplikacji, wersja podstawowa funkcji sterty bezpośrednio są mapowane do ich wersji debugowej. Flaga umożliwia w Crtdbg.h na potrzeby mapowania. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) Flaga został zdefiniowany w aplikacji.

Aby uzyskać więcej informacji o korzystaniu z wersji do debugowania w stosunku do podstawowej wersji funkcji sterty, zobacz [przy użyciu debugowania wersji i wersja podstawowa](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Zobacz też

[Flagi kontrolne](../c-runtime-library/control-flags.md)