---
title: "Co robią okna ramowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cda73727a7481c6c7d8b5002467ceeef378fdae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="what-frame-windows-do"></a>Co robią okna ramowe
Oprócz po prostu framing widoku, okien ramowych są odpowiedzialne za wiele zadań związanych z koordynowanie ramki z jego widoku i aplikacji. [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md) i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dziedziczyć [cframewnd —](../mfc/reference/cframewnd-class.md), więc mają `CFrameWnd` możliwości, a także nowe funkcje, które dodają. Okno podrzędne przykładem widoków, formanty, takie jak przycisków i pola listy i paski sterowania, w tym pasków narzędzi, pasków stanu i paski dialogowe.  
  
 Okno ramowe jest odpowiedzialny za zarządzanie układ jego okien podrzędnych. W ramach MFC okno ramowe umieszcza pasków sterowania, widoków i innych okien podrzędnych wewnątrz obszaru klienckiego.  
  
 Okno ramowe również przekazuje polecenia do jego widoków i mogą odpowiadać na komunikaty powiadomień z sterowania systemu windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Paski sterowania (jak mieściły się w oknie ramowym)](../mfc/control-bars.md)  
  
-   [Zarządzanie menu, paskami sterowania i akceleratorami (jak mieściły się w oknie ramowym)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [Routing poleceń (od ramkę okna do jego widoku i inne obiekty docelowe poleceń)](../mfc/command-routing.md)  
  
-   [Architektura/View dokumentu](../mfc/document-view-architecture.md)  
  
-   [Paski sterowania](../mfc/control-bars.md)  
  
-   [Formanty](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna ramowe](../mfc/frame-windows.md)

