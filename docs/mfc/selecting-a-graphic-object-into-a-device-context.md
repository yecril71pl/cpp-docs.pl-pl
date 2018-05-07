---
title: Wybieranie obiektu graficznego do kontekstu urządzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc605be317d51c985e32fbad038d846b056e5fe6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Wybieranie obiektu graficznego do kontekstu urządzenia
Ten temat dotyczy przy użyciu obiektów graficznych kontekstu urządzenia okna. Po [utworzyć rysowania obiektu](../mfc/one-stage-and-two-stage-construction-of-objects.md), zaznacz go do kontekstu urządzenia zamiast domyślnego obiektu przechowywane:  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## <a name="lifetime-of-graphic-objects"></a>Okres istnienia obiektów graficznych  
 Zwrócona przez obiekt graficzny [SelectObject](../mfc/reference/cdc-class.md#selectobject) to "tymczasowe". Oznacza to, że zostanie ona usunięta przez [OnIdle](../mfc/reference/cwinapp-class.md#onidle) funkcji członkowskiej klasy `CWinApp` czasu przy następnym program pobiera bezczynności. Tak długo, jak używać obiektu zwróconego przez `SelectObject` w jednej funkcji bez zwracanie formantu do pętli komunikatów głównym, będą miały żadnych problemów.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md)  
  
-   [Jedno- i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md)  
  
-   [Rysowanie w widoku](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty graficzne](../mfc/graphic-objects.md)

