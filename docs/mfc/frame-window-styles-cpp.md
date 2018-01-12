---
title: Style okna ramowego (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5bdc0204c538f476c791657d8b29a28b7baedd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-styles-c"></a>Style okna ramowego (C++)
Okien ramowych uzyskać Framework są odpowiednie dla większości programów, ale mogą uzyskać większą elastyczność przy użyciu zaawansowanych funkcji [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) i funkcje globalne MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`Funkcja członkowska jest `CWnd`.  
  
 W przypadku zastosowania **ws_hscroll —** i **ws_vscroll —** style do głównego okna ramowego, są natomiast stosowane do **MDICLIENT** okna, użytkownicy mogą być przewijane **MDICLIENT** obszaru.  
  
 Jeśli okna **fws_addtotitle —** bit styl jest ustawiony (który jest domyślnie), widok informuje okno ramowe jaki tytuł do wyświetlania w pasku tytułu okna na podstawie nazwy dokumentu widoku.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Zarządzanie oknami podrzędnymi MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okna w ramce MDI, który zawiera okien podrzędnych MDI  
  
-   [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Style okna](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna ramowe](../mfc/frame-windows.md)

