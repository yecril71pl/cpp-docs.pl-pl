---
title: Klasy okien ramowych (architektura)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 483112d197b7c7211989ecda8b774deb9f30d49e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624605"
---
# <a name="frame-window-classes-architecture"></a>Klasy okien ramowych (architektura)

W obszarze architektura dokumentu/widoku okna z ramkami są okna zawierające okno wyświetlania. Obsługują one również paski kontroli dołączone do nich.

W aplikacjach interfejsu wielu dokumentów (MDI) główne okno pochodzi od `CMDIFrameWnd` . Zawiera on pośrednio ramki dokumentów, które są `CMDIChildWnd` obiektami. `CMDIChildWnd`Obiekty z kolei zawierają widoki dokumentów.

W aplikacjach interfejsu pojedynczego dokumentu (SDI) główne okno pochodne od `CFrameWnd` , zawiera widok bieżącego dokumentu.

[CFrameWnd](reference/cframewnd-class.md)<br/>
Klasa bazowa dla głównego okna ramki aplikacji SDI. Również Klasa bazowa dla wszystkich innych klas okien ramowych.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Klasa bazowa dla głównego okna ramki aplikacji MDI.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Klasa bazowa dla okien ramowych dokumentu aplikacji MDI.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramek dla widoku, gdy dokument serwera jest edytowany w miejscu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
