---
title: Klasy pasków sterowania
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: f89770683edb1f4268b4f19adb74e5c08aa5f109
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620523"
---
# <a name="control-bar-classes"></a>Klasy pasków sterowania

Paski sterowania są dołączone do okna ramki. Zawierają przyciski, okienka stanu lub szablon okna dialogowego. Swobodne słupki kontrolne, nazywane również paletami narzędzi, są implementowane przez dołączenie ich do obiektu [CMiniFrameWnd](reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Paski formantów struktury

Te paski kontroli są integralną częścią struktury MFC. Są one łatwiejsze w użyciu i bardziej wydajne niż paski sterowania systemu Windows, ponieważ są zintegrowane z platformą. Większość aplikacji MFC używa tych pasków sterowania, a nie pasków sterowania systemu Windows.

[CControlBar](reference/ccontrolbar-class.md)<br/>
Klasa bazowa dla pasków sterowania MFC wymienionych w tej sekcji. Pasek sterowania jest oknem wyrównanym do krawędzi okna ramki. Pasek sterowania zawiera `HWND` kontrolki podrzędne lub formanty, które nie są oparte na `HWND` , takie jak przyciski paska narzędzi.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Pasek sterowania, który jest oparty na szablonie okna dialogowego.

[CReBar](reference/crebar-class.md)<br/>
Obsługuje pasek narzędzi, który może zawierać dodatkowe okna podrzędne w formie kontrolek.

[CToolBar](reference/ctoolbar-class.md)<br/>
Okna kontrolki paska narzędzi, które zawierają przyciski poleceń mapy bitowej, które nie są oparte na `HWND` . Większość aplikacji MFC używa tej klasy, a nie `CToolBarCtrl` .

[CStatusBar](reference/cstatusbar-class.md)<br/>
Klasa bazowa dla okien kontrolki paska stanu. Większość aplikacji MFC używa tej klasy, a nie `CStatusBarCtrl` .

## <a name="windows-control-bars"></a>Paski sterowania systemu Windows

Te paski sterujące są cienkimi otokami dla odpowiednich kontrolek systemu Windows. Ponieważ nie są one zintegrowane z platformą, są trudniejsze do użycia niż paski kontroli wymienione wcześniej. Większość aplikacji MFC używa wymienionych wcześniej pasków sterowania.

[Korzystanie CReBarCtrl](reference/crebarctrl-class.md)<br/>
Implementuje wewnętrzną kontrolę `CRebar` obiektu.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Okno poziome, zwykle podzielone na okienka, w którym aplikacja może wyświetlać informacje o stanie.

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Oferuje funkcje formantu typowego paska narzędzi systemu Windows.

## <a name="related-classes"></a>Powiązane klasy

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Małe okno podręczne wyświetlające pojedynczy wiersz tekstu opisujący przeznaczenie narzędzia w aplikacji.

[CDockState](reference/cdockstate-class.md)<br/>
Obsługuje trwały magazyn danych stanu dokowania dla pasków sterowania.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
