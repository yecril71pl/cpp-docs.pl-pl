---
title: Klasy pasków sterowania
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440962"
---
# <a name="control-bar-classes"></a>Klasy pasków sterowania

Paski sterowania są dołączone do okna ramki. Zawierają przyciski, okienka stanu lub szablon okna dialogowego. Swobodne słupki kontrolne, nazywane również paletami narzędzi, są implementowane przez dołączenie ich do obiektu [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Paski formantów struktury

Te paski kontroli są integralną częścią struktury MFC. Są one łatwiejsze w użyciu i bardziej wydajne niż paski sterowania systemu Windows, ponieważ są zintegrowane z platformą. Większość aplikacji MFC używa tych pasków sterowania, a nie pasków sterowania systemu Windows.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
Klasa bazowa dla pasków sterowania MFC wymienionych w tej sekcji. Pasek sterowania jest oknem wyrównanym do krawędzi okna ramki. Pasek sterowania zawiera kontrolki podrzędne oparte na `HWND`lub formanty, które nie są oparte na `HWND`, takich jak przyciski paska narzędzi.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Pasek sterowania, który jest oparty na szablonie okna dialogowego.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Obsługuje pasek narzędzi, który może zawierać dodatkowe okna podrzędne w formie kontrolek.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Okna kontrolki paska narzędzi, które zawierają przyciski poleceń mapy bitowej, które nie są oparte na `HWND`. Większość aplikacji MFC używa tej klasy, a nie `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
Klasa bazowa dla okien kontrolki paska stanu. Większość aplikacji MFC używa tej klasy, a nie `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Paski sterowania systemu Windows

Te paski sterujące są cienkimi otokami dla odpowiednich kontrolek systemu Windows. Ponieważ nie są one zintegrowane z platformą, są trudniejsze do użycia niż paski kontroli wymienione wcześniej. Większość aplikacji MFC używa wymienionych wcześniej pasków sterowania.

[Korzystanie CReBarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementuje wewnętrzną kontrolę obiektu `CRebar`.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Okno poziome, zwykle podzielone na okienka, w którym aplikacja może wyświetlać informacje o stanie.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Oferuje funkcje formantu typowego paska narzędzi systemu Windows.

## <a name="related-classes"></a>Powiązane klasy

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Małe okno podręczne wyświetlające pojedynczy wiersz tekstu opisujący przeznaczenie narzędzia w aplikacji.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Obsługuje trwały magazyn danych stanu dokowania dla pasków sterowania.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
