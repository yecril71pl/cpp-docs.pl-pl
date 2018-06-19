---
title: Sekwencja likwidacji okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1c67d5a6391bbfc91bbce0d06a6bb58350e9a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382612"
---
# <a name="window-destruction-sequence"></a>Sekwencja likwidacji okna
W ramach MFC, gdy użytkownik zamyka okno ramowe domyślne okna [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołań obsługi [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatnim funkcji członkowskiej wywoływane, gdy okno systemu Windows zostanie zniszczony [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), która działa niektórych oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) elementu członkowskiego funkcja do wykonania oczyszczania systemu Windows, a na koniec wywołuje wirtualnej funkcji członkowskiej [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). [Cframewnd —](../mfc/reference/cframewnd-class.md) implementacja `PostNcDestroy` usuwa obiekt window C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

