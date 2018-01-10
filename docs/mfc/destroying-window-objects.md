---
title: "Niszczenie obiektów okien | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e7b8b2cf605e0f53418755b65151fd9eb2cff5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

