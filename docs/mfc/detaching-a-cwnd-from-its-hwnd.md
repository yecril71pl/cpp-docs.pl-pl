---
title: Odłączanie obiektu CWnd od jego właściwości HWND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a776b4ff4799750c89a322379a063030db748eec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odłączanie obiektu CWnd od jego właściwości HWND
Jeśli zachodzi konieczność obejścia obiektu -`HWND` relacji MFC zawiera inny `CWnd` funkcji członkowskiej [Detach](../mfc/reference/cwnd-class.md#detach), który rozłącza obiektem okna języka C++ z okna systemu Windows. Zapobiega to niszczenie okna systemu Windows, gdy obiekt zostanie zniszczony destruktor.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien](../mfc/creating-windows.md)  
  
-   [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)  
  
-   [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

