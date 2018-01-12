---
title: Gumka i Trackery | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3bd9da00d2d6ea0110562f523a0adc53c1a476c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rubber-banding-and-trackers"></a>Gumka i trackery
Inna funkcja dostarczony wraz z trackerów jest wybór "gumki", który umożliwia użytkownikowi wybranie wielu elementów OLE przez przeciągnięcie prostokąta zmiany rozmiaru wokół elementów, które można wybrać. Gdy użytkownik zwalnia lewego przycisku myszy, elementy w obrębie regionu wybrane przez użytkownika są zaznaczone i może manipulować przez użytkownika. Użytkownik może na przykład, przeciągnij zaznaczenie do innej aplikacji kontenera.  
  
 Implementowanie ta funkcja wymaga dodatkowy kod w aplikacji `WM_LBUTTONDOWN` funkcji obsługi.  
  
 Poniższy przykładowy kod implementuje gumki — wybór i dodatkowe funkcje.  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]  
  
 Jeśli chcesz zezwolić odwracalnego orientację śledzący podczas Gumka, należy wywołać [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) z trzeci parametr ustawioną **TRUE**. Należy pamiętać, że stosowanie odwracalnego orientacji czasami spowoduje [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) aby stać się odwrócony. Ten problem można rozwiązać przez wywołanie do [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).  
  
 Aby uzyskać więcej informacji, zobacz [elementy klienckie kontenerów](../mfc/containers-client-items.md) i [Dostosowywanie przeciąganie i upuszczanie](../mfc/drag-and-drop-customizing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Trackery: Implementowanie Trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [Klasa CRectTracker](../mfc/reference/crecttracker-class.md)
