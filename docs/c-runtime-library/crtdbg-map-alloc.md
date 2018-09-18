---
title: _CRTDBG_MAP_ALLOC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c48095acceefa4bb4852dab18d35284492e7ba0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069407"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Gdy **_CRTDBG_MAP_ALLOC** flaga jest zdefiniowany w wersji debugowania aplikacji, wersja podstawowa funkcji sterty bezpośrednio są mapowane do ich wersji debugowej. Flaga umożliwia w Crtdbg.h na potrzeby mapowania. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) Flaga został zdefiniowany w aplikacji.

Aby uzyskać więcej informacji o korzystaniu z wersji do debugowania w stosunku do podstawowej wersji funkcji sterty, zobacz [przy użyciu debugowania wersji i wersja podstawowa](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Zobacz też

[Flagi kontrolne](../c-runtime-library/control-flags.md)