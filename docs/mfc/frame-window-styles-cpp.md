---
title: Style okna ramowego (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102b3a4c8372a53aada23ad448ce5dc1cf323a97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343763"
---
# <a name="frame-window-styles-c"></a>Style okna ramowego (C++)
Okien ramowych uzyskać Framework są odpowiednie dla większości programów, ale mogą uzyskać większą elastyczność przy użyciu zaawansowanych funkcji [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) i funkcje globalne MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` Funkcja członkowska jest `CWnd`.  
  
 W przypadku zastosowania **ws_hscroll —** i **ws_vscroll —** style do głównego okna ramowego, są natomiast stosowane do **MDICLIENT** okna, użytkownicy mogą być przewijane **MDICLIENT** obszaru.  
  
 Jeśli okna **fws_addtotitle —** bit styl jest ustawiony (który jest domyślnie), widok informuje okno ramowe jaki tytuł do wyświetlania w pasku tytułu okna na podstawie nazwy dokumentu widoku.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Zarządzanie oknami podrzędnymi MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okna w ramce MDI, który zawiera okien podrzędnych MDI  
  
-   [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Style okna](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna ramowe](../mfc/frame-windows.md)

