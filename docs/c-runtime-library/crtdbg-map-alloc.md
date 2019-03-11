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
ms.openlocfilehash: 8bcb0f5ea26218b74034eb0a41199a1104ba944d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739780"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Gdy **_CRTDBG_MAP_ALLOC** flaga jest zdefiniowany w wersji debugowania aplikacji, wersja podstawowa funkcji sterty bezpośrednio są mapowane do ich wersji debugowej. Flaga umożliwia w Crtdbg.h na potrzeby mapowania. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) Flaga został zdefiniowany w aplikacji.

Aby uzyskać więcej informacji o korzystaniu z wersji do debugowania w stosunku do podstawowej wersji funkcji sterty, zobacz [przy użyciu debugowania wersji i wersja podstawowa](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Zobacz także

[Flagi kontrolne](../c-runtime-library/control-flags.md)
