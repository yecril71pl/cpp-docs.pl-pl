---
title: Klasy okien ramowych (architektura)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441256"
---
# <a name="frame-window-classes-architecture"></a>Klasy okien ramowych (architektura)

W obszarze architektura dokumentu/widoku okna z ramkami są okna zawierające okno wyświetlania. Obsługują one również paski kontroli dołączone do nich.

W aplikacjach interfejsu wielu dokumentów (MDI) główne okno pochodzi od `CMDIFrameWnd`. Zawiera on pośrednio ramki dokumentów, które są `CMDIChildWnd` obiektów. Obiekty `CMDIChildWnd` z kolei zawierają widoki dokumentów.

W aplikacjach interfejsu pojedynczego dokumentu (SDI) główne okno pochodne od `CFrameWnd`, zawiera widok bieżącego dokumentu.

[Obiektu CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Klasa bazowa dla głównego okna ramki aplikacji SDI. Również Klasa bazowa dla wszystkich innych klas okien ramowych.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Klasa bazowa dla głównego okna ramki aplikacji MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Klasa bazowa dla okien ramowych dokumentu aplikacji MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramek dla widoku, gdy dokument serwera jest edytowany w miejscu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
