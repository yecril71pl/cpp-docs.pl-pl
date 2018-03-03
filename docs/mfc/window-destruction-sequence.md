---
title: Sekwencja likwidacji okna | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b873d51f585336425537756064582eb709988f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="window-destruction-sequence"></a>Sekwencja likwidacji okna
W ramach MFC, gdy użytkownik zamyka okno ramowe domyślne okna [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołań obsługi [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatnim funkcji członkowskiej wywoływane, gdy okno systemu Windows zostanie zniszczony [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), która działa niektórych oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) elementu członkowskiego funkcja do wykonania oczyszczania systemu Windows, a na koniec wywołuje wirtualnej funkcji członkowskiej [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). [Cframewnd —](../mfc/reference/cframewnd-class.md) implementacja `PostNcDestroy` usuwa obiekt window C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

