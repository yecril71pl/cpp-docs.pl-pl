---
title: "_crtdbgflag — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs: C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b5169a9f5110e40e0d7ff7e9b036c2e28c98660
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtdbgflag"></a>_crtDbgFlag
**_Crtdbgflag —** flagi składa się z pól bitowych pięć, które kontrolują sposób przydzielania pamięci w wersji do debugowania sterty są śledzone, zweryfikować zgłoszone i utworzyć zrzutu. Pola bitowe flagi są ustawiane przy użyciu [_crtsetdbgflag —](../c-runtime-library/reference/crtsetdbgflag.md) funkcji. Ta flaga i jego pól bitowych są zadeklarowane w Crtdbg.h. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) flagi został zdefiniowany w aplikacji.  
  
 Aby uzyskać więcej informacji o używaniu tej flagi w połączeniu z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi kontrolne](../c-runtime-library/control-flags.md)