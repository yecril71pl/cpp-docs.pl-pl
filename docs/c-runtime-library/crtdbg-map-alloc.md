---
title: "_CRTDBG_MAP_ALLOC — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs: C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2b61b315baa337675147ded1232a943e82b24ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
Gdy **_crtdbg_map_alloc —** flaga jest zdefiniowany w wersji do debugowania aplikacji, wersja podstawowa funkcji sterty bezpośrednio są mapowane na ich wersje debugowania. Flaga jest wykorzystywana w Crtdbg.h do mapowania. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) flagi został zdefiniowany w aplikacji.  
  
 Aby uzyskać więcej informacji o korzystaniu z wersji do debugowania i wersja podstawowa funkcji sterty, zobacz [za pomocą debugowania wersji i wersja podstawowa](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi kontrolne](../c-runtime-library/control-flags.md)