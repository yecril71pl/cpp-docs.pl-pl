---
title: Kiedy inicjować obiekty CWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee10a4632809a224028bfa482f80ed9e8a9334a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="when-to-initialize-cwnd-objects"></a>Kiedy inicjować obiekty CWnd
Nie można utworzyć własne podrzędne systemu windows lub wywołaniem dowolnej funkcji interfejsu API systemu Windows w Konstruktorze `CWnd`-pochodzi z obiektu. Jest to spowodowane `HWND` dla `CWnd` obiektu nie został jeszcze utworzony. Inicjowanie najbardziej właściwe dla systemu Windows, takie jak dodanie okno podrzędne, musi zostać wykonane w [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obsługi wiadomości.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

