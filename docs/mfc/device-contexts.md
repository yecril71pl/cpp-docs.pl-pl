---
title: Konteksty urządzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45a2f99001d45de71ca3ea8a525152d53d67ee64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348573"
---
# <a name="device-contexts"></a>Konteksty urządzenia
Kontekst urządzenia jest strukturą danych systemu Windows zawierający informacje o atrybuty rysowania urządzeniami, takimi jak ekranu lub drukarki. Wszystkie wywołania rysowania są wykonywane za pośrednictwem obiektu kontekstu urządzenia, który hermetyzuje interfejsy API systemu Windows do rysowania linii, kształty i tekst. Konteksty urządzenia zezwala na rysowanie niezależne od urządzenia w systemie Windows. Konteksty urządzenia może służyć do rysowania ekranu, drukarki lub metaplik.  
  
 [Cpaintdc —](../mfc/reference/cpaintdc-class.md) obiektów hermetyzacji wspólnych idiom systemu Windows, wywołanie `BeginPaint` funkcji, w kontekście urządzenia, a następnie wywoływania `EndPaint` funkcji. `CPaintDC` Wywołania konstruktora `BeginPaint` dla użytkownika i wywołania destruktora `EndPaint`. Uproszczony proces jest utworzenie [CDC](../mfc/reference/cdc-class.md) obiektów, rysowania, a następnie zniszcz `CDC` obiektu. W ramach zautomatyzowana jest znacznie nawet tego procesu. W szczególności z `OnDraw` funkcji została przekazana `CPaintDC` już przygotowane (za pośrednictwem `OnPrepareDC`), i po prostu Rysuj do niego. Zostanie zniszczony przez platformę, i wydaniu podstawowy kontekst urządzenia do systemu Windows po powrocie z wywołania z `OnDraw` funkcji.  
  
 [Cclientdc —](../mfc/reference/cclientdc-class.md) obiektów Hermetyzowanie pracy z kontekstu urządzenia reprezentujący tylko obszaru klienckiego okna. `CClientDC` Wywołania konstruktora `GetDC` funkcji i wywołania destruktora `ReleaseDC` funkcji. [CWindowDC](../mfc/reference/cwindowdc-class.md) obiektów Hermetyzowanie kontekstu urządzenia reprezentujący całego okna, łącznie z jej ramki.  
  
 [Cmetafiledc —](../mfc/reference/cmetafiledc-class.md) obiektów Hermetyzowanie rysunku w metaplik systemu Windows. Contrast do `CPaintDC` przekazany do `OnDraw`, w tym przypadku należy wywołać [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) samodzielnie.  
  
## <a name="mouse-drawing"></a>Rysowanie myszy  
 Większość Rysowanie w ramach programu — i w związku z tym większość pracy kontekstu urządzenia — odbywa się w widoku `OnDraw` funkcję elementu członkowskiego. Można jednak nadal używać obiektów kontekstu urządzenia do innych celów. Na przykład, aby zapewnić opinii śledzenia ruchów myszy w widoku, należy rysowanie bezpośrednio w widoku bez oczekiwania na `OnDraw` do wywołania.  
  
 W takim przypadku można użyć [cclientdc —](../mfc/reference/cclientdc-class.md) obiektu kontekstu urządzenia do rysowania bezpośrednio w widoku.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Konteksty urządzenia (definicja)](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Rysowanie w widoku](../mfc/drawing-in-a-view.md)  
  
-   [Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Linii i krzywych](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [Wypełnione kształty](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [Czcionki i tekst](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [Kolory](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [Przestrzeni współrzędnych i przekształcenia](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

