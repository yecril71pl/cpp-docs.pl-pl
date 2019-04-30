---
title: Klasy okien ramowych (architektura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: affa217f481cc6d9e125d526f1b97be9120e0990
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392846"
---
# <a name="frame-window-classes-architecture"></a>Klasy okien ramowych (architektura)

W ramach architektury dokument/widok okna ramowe są systemu windows, które zawierają okno Widok. Obsługują one również posiadanie kontrolować paski dołączonych do nich.

W wielu aplikacjach interfejsu (MDI) dokumentu, okno główne jest tworzony na podstawie `CMDIFrameWnd`. Zawiera pośrednio ramki dokumentów, które są `CMDIChildWnd` obiektów. `CMDIChildWnd` Obiektów, z kolei zawierają widoki dokumenty.

W aplikacjach interfejsu (SDI) pojedynczego dokumentu głównego okna pochodzące z `CFrameWnd`, zawiera widok bieżącego dokumentu.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Klasa bazowa dla aplikacji interfejsu SDI ramki głównego okna. Również klasę bazową dla wszystkich innych klas okna ramki.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Klasa bazowa dla okna głównej ramki aplikacji MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Klasa bazowa dla okien ramowych dokumentu w aplikacji MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramowe w celu wyświetlenia, gdy dokument serwera jest edytowany w miejscu.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
