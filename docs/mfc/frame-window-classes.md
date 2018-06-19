---
title: Klasy okien ramowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b9003ba503e0a78e5f223e766346d63679d9959
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347889"
---
# <a name="frame-window-classes"></a>Klasy okien ramowych
Każda aplikacja ma jeden "główne okno ramowe," okien pulpitu, zazwyczaj mający nazwę aplikacji w jego podpis. Każdy dokument ma zazwyczaj jedną "okno ramowe dokumentu." Okna ramowe dokumentów zawiera co najmniej jeden widok, który przedstawia dane dokumentu.  
  
## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Okna ramowe w SDI i MDI — aplikacje  
 Dla aplikacji SDI jest jedno okno ramowe pochodzi od klasy [cframewnd —](../mfc/reference/cframewnd-class.md). To okno jest główną ramkę okna i okna ramowe dokumentu. Dla aplikacji MDI głównego okna ramowego pochodzi od klasy [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md), i okna ramowe dokumentów, które są okien podrzędnych MDI, są pochodnymi klasy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).  
  
## <a name="use-the-frame-window-class-or-derive-from-it"></a>Należy użyć klasy okien ramowych lub pochodzić od niego  
 Te klasy zawierają większość funkcjonalności okno ramowe potrzebnych dla aplikacji. W normalnych okolicznościach domyślnego zachowania i wyglądu, które zapewniają będzie własnych potrzeb. Jeśli potrzebujesz dodatkowych funkcji, pochodzi z tych klas.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Klasy okien ramowych tworzone przez Kreatora aplikacji](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Style okna ramowego](../mfc/frame-window-styles-cpp.md)  
  
-   [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna ramowe](../mfc/frame-windows.md)

