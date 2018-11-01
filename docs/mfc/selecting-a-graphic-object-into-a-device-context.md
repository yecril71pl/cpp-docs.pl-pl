---
title: Wybieranie obiektu graficznego do kontekstu urządzenia
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: c879369d445a9330139eff89be4ad8153252bfa1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438830"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Wybieranie obiektu graficznego do kontekstu urządzenia

Ten temat dotyczy przy użyciu obiektów graficznych w kontekście urządzenia okna. Po zakończeniu [utworzyć obiekt rysowania](../mfc/one-stage-and-two-stage-construction-of-objects.md), musisz wybrać go do kontekstu urządzenia zamiast domyślnego obiektu tam przechowywane:

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>Okres istnienia obiektów graficznych

Zwrócona przez obiekt graficzny [SelectObject](../mfc/reference/cdc-class.md#selectobject) jest "tymczasowe". Oznacza to, zostanie on usunięty przez [OnIdle](../mfc/reference/cwinapp-class.md#onidle) funkcji składowej klasy typu `CWinApp` czasu przy następnym program pobiera bezczynności. Tak długo, jak używać obiektu zwróconego przez `SelectObject` w jednej funkcji bez zwracanie formantu do główna pętla wiadomości, będziesz mieć żaden problem.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Obiekty graficzne](../mfc/graphic-objects.md)

- [Jedno- i dwuetapowa konstrukcja obiektów graficznych](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Konteksty urządzenia](../mfc/device-contexts.md)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Zobacz też

[Obiekty graficzne](../mfc/graphic-objects.md)

