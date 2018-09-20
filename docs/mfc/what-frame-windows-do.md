---
title: Co zrobić Windows ramki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b86b65d43fee16a0a2a8f03353c9700d6f0a5428
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423601"
---
# <a name="what-frame-windows-do"></a>Co robią okna ramowe

Oprócz po prostu ramek widoku, okien ramowych są odpowiedzialne za wiele zadań objętych koordynowanie ramkę z jej widok i aplikacji. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dziedziczyć [CFrameWnd](../mfc/reference/cframewnd-class.md), dzięki czemu mają one `CFrameWnd` możliwości, a także nowe funkcje, które dodają. Przykładami okien podrzędnych widoki, kontrolki, takie jak przyciski i pola listy i pasków sterowania w tym paski narzędzi, paski stanu i paski dialogowe.

Okno ramki jest odpowiedzialny za zarządzanie układu jego okien podrzędnych. W ramach MFC wewnątrz obszaru klienckiego okna ramki umieszcza pasków sterowania, widoki i inne okna podrzędnego.

Okno ramowe przesyła dalej polecenia, aby jego widoki i mogą odpowiadać na komunikaty powiadomień z poziomu kontroli systemu windows.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Paski sterowania (jak mieściły się w oknie ramki)](../mfc/control-bars.md)

- [Zarządzanie menu, paskami sterowania i akceleratorami (jak mieściły się w oknie ramki)](../mfc/managing-menus-control-bars-and-accelerators.md)

- [Routing poleceń (z okno ramowe jej widok i inne obiekty docelowe poleceń)](../mfc/command-routing.md)

- [Architektura/View dokumentów](../mfc/document-view-architecture.md)

- [Paski sterowania](../mfc/control-bars.md)

- [Kontrolki](../mfc/controls-mfc.md)

## <a name="see-also"></a>Zobacz też

[Okna ramowe](../mfc/frame-windows.md)

