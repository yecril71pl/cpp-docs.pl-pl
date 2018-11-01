---
title: Co robią okna ramowe
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: ea35b98e5234c10a10143bad1d35fdd1b4510ced
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508774"
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

