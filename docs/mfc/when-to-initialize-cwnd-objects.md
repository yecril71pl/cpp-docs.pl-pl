---
title: "Kiedy inicjować obiekty CWnd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2e9d99fe2f01111308a9a7a002aeefbf472a0b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="when-to-initialize-cwnd-objects"></a>Kiedy inicjować obiekty CWnd
Nie można utworzyć własne podrzędne systemu windows lub wywołaniem dowolnej funkcji interfejsu API systemu Windows w Konstruktorze `CWnd`-pochodzi z obiektu. Jest to spowodowane `HWND` dla `CWnd` obiektu nie został jeszcze utworzony. Inicjowanie najbardziej właściwe dla systemu Windows, takie jak dodanie okno podrzędne, musi zostać wykonane w [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obsługi wiadomości.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

