---
title: Ogólna sekwencja tworzenia okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a9c6ecf6516adceda845dadd4f0313ae605f0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346519"
---
# <a name="general-window-creation-sequence"></a>Ogólna sekwencja tworzenia okna
Podczas tworzenia okna oknie użytkownika, takie jak element podrzędny platformę używa znacznie te same czynności, którą opisano w [tworzenia dokumentu/widoku](../mfc/document-view-creation.md).  
  
 Klasy okien podał zatrudnienia MFC [dwuetapowa konstrukcja](../mfc/one-stage-and-two-stage-construction-of-objects.md). Oznacza to, że podczas wywołania języka C++ **nowe** operatora, konstruktora przydziela i inicjuje obiekt C++, ale nie powoduje utworzenia odpowiedniego okna systemu Windows. Następnie wykonywane przez wywołanie metody [Utwórz](../mfc/reference/cwnd-class.md#create) funkcji członkowskiej klasy obiektu okna.  
  
 **Utwórz** funkcji członkowskiej sprawia, że okno systemu Windows i są przechowywane jego `HWND` w obiekcie C++ publicznego elementu członkowskiego danych [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). **Utwórz** przekazuje pełną elastyczność tworzenia parametrów. Przed wywołaniem **Utwórz**, można zarejestrować klasy okna za pomocą funkcji globalnej [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) było ustawić styl ikony, jak i klasy ramki.  
  
 Okna ramowe, można użyć [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkcji członkowskiej zamiast **Utwórz**. `LoadFrame` powoduje, że okno systemu Windows przy użyciu mniejszej liczby parametrów. Pobiera wiele wartości domyślnych z zasobów, w tym ramki podpis, ikona tabeli akceleratora i menu.  
  
> [!NOTE]
>  Ikona, w tabeli akceleratora i w zasoby menu musi mieć wspólny identyfikator zasobów, takich jak **IDR_MAINFRAME**, ich być załadowana przez LoadFrame.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Obiekty okna](../mfc/window-objects.md)  
  
-   [Rejestrowanie klas"okien"](../mfc/registering-window-classes.md)  
  
-   [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie okien](../mfc/creating-windows.md)

