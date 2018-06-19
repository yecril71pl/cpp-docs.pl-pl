---
title: Niszczenie obiektów okien | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aacb01d945429bc36543f78e3635c39ef58223d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343379"
---
# <a name="destroying-window-objects"></a>Niszczenie obiektów okien
Należy uważać z okien podrzędnych do zniszczenia obiektem okna języka C++, gdy zostanie zakończone w oknie. Jeśli te obiekty nie zostały zniszczone, aplikacja nie odzyska ich pamięci. Na szczęście w ramach zarządza zniszczenie okna, a także tworzenie okien ramowych, widoków i okien dialogowych. Jeśli utworzysz dodatkowe okna jest odpowiedzialny za zniszczenia.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)  
  
-   [Alokowanie i dealokowanie pamięci okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Ogólna sekwencja tworzenia okna](../mfc/general-window-creation-sequence.md)  
  
-   [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

