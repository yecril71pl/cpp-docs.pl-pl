---
title: Gumka i trackery
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: 095f3c15546466c6a495f6aa348990ed69b04a9e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127369"
---
# <a name="rubber-banding-and-trackers"></a>Gumka i trackery

Inną funkcją dostarczoną z elementami śledzącymi jest wybór "gumy-Band", który umożliwia użytkownikowi wybranie wielu elementów OLE, przeciągając prostokąt zmiany rozmiarów wokół elementów do zaznaczenia. Po zwolnieniu lewego przycisku myszy elementy w regionie wybranym przez użytkownika są wybierane i mogą być przetwarzane przez użytkownika. Na przykład użytkownik może przeciągnąć zaznaczenie do innej aplikacji kontenera.

Implementacja tej funkcji wymaga dodatkowego kodu w funkcji obsługi WM_LBUTTONDOWN aplikacji.

Poniższy przykład kodu implementuje wybór gumowy i dodatkowe funkcje.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Jeśli chcesz zezwolić na odwracalną orientację w module śledzącym podczas gumy, należy wywołać [CRectTracker:: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) z trzecim parametrem o **wartości true**. Należy pamiętać, że umożliwienie odwracalnej orientacji czasami spowoduje odwrócenie [CRectTracker:: m_rect](../mfc/reference/crecttracker-class.md#m_rect) . Można to naprawić przez wywołanie [CRect:: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Aby uzyskać więcej informacji, zobacz [elementy klienckie kontenera](../mfc/containers-client-items.md) i [Przeciąganie i upuszczanie OLE: Dostosuj przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md#customize-drag-and-drop).

## <a name="see-also"></a>Zobacz też

[Trackery: implementowanie trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[Klasa CRectTracker](../mfc/reference/crecttracker-class.md)
