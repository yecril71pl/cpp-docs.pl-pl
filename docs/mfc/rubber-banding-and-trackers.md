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
ms.openlocfilehash: a6a9c9848e21129d4e6a8ce300e8750b4a0c6126
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308852"
---
# <a name="rubber-banding-and-trackers"></a>Gumka i trackery

Kolejną funkcją dostarczony wraz z trackery jest wybór "gumki", który umożliwia użytkownikowi wybranie wielu elementów OLE, przeciągając prostokąt zmiany rozmiaru wokół elementów do wybrania. Gdy użytkownik zwolni przycisk myszy po lewej stronie, elementów w obrębie regionu wybrane przez użytkownika są zaznaczone i mogą być zmieniane przez użytkownika. Użytkownik może na przykład przeciągnij je do innej aplikacji kontenera.

Implementowanie ta funkcja wymaga dodatkowy kod w funkcji obsługi WM_LBUTTONDOWN Twojej aplikacji.

Poniższy przykładowy kod implementuje gumki — wybór i dodatkowe funkcje.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Jeśli chcesz zezwolić odwracalnego orientację śledzący podczas Gumka, należy wywołać [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) z trzecim określonym parametrem równa **TRUE**. Należy pamiętać, umożliwiając odwracalnego orientacji czasami spowoduje [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) aby stać się odwrócona. Ten problem można rozwiązać przez wywołanie [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Aby uzyskać więcej informacji, zobacz [elementy klienckie kontenerów](../mfc/containers-client-items.md) i [Dostosowywanie przeciągania i upuszczania](../mfc/drag-and-drop-customizing.md).

## <a name="see-also"></a>Zobacz także

[Trackery: Implementowanie Trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[Klasa CRectTracker](../mfc/reference/crecttracker-class.md)
