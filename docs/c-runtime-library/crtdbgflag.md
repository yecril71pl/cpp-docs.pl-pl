---
title: _crtdbgflag — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb0c22e65c33ab8f689026e916f550280bf6a8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgflag"></a>_crtDbgFlag
**_Crtdbgflag —** flagi składa się z pól bitowych pięć, które kontrolują sposób przydzielania pamięci w wersji do debugowania sterty są śledzone, zweryfikować zgłoszone i utworzyć zrzutu. Pola bitowe flagi są ustawiane przy użyciu [_crtsetdbgflag —](../c-runtime-library/reference/crtsetdbgflag.md) funkcji. Ta flaga i jego pól bitowych są zadeklarowane w Crtdbg.h. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) flagi został zdefiniowany w aplikacji.  
  
 Aby uzyskać więcej informacji o używaniu tej flagi w połączeniu z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi kontrolne](../c-runtime-library/control-flags.md)