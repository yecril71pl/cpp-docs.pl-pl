---
title: Klasy pasków sterowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13fe4cd9cc483bccde6a342ef224dfbafab36eca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378563"
---
# <a name="control-bar-classes"></a>Klasy pasków sterowania

Paski sterowania są dołączone do okna ramki. Zawierają one przyciski, stan okienka lub szablonu okna dialogowego. Paski sterowania swobodny, nazywane również palet narzędzia są implementowane przez dołączenie do [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) obiektu.

## <a name="framework-control-bars"></a>Paski sterowania Framework

Te paski kontrolki są integralną częścią struktura MFC. Są one łatwiejsze w użyciu i bardziej wydajne niż Windows pasków sterowania, ponieważ są one zintegrowane z architekturą. Większość aplikacji MFC, użyj pasków sterowania, a nie Windows pasków sterowania.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
Klasa bazowa paski sterowania MFC wymienione w tej sekcji. Pasek sterowania jest wyrównany do krawędzi okna ramki okna. Pasek sterowania zawierają dowolne `HWND`— na podstawie formantów podrzędnych lub kontrolki, które nie są oparte na `HWND`, takie jak przyciski paska narzędzi.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Pasek sterowania, który jest oparty na szablonu okna dialogowego.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Obsługuje pasek narzędzi, który może zawierać dodatkowe elementu podrzędnym MDI w formie kontrolki.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Na podstawie systemu windows formantu paska narzędzi, które nie zawierają przyciski z mapami polecenia `HWND`. Większość aplikacji MFC używa tej klasy zamiast `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
Klasa podstawowa dla systemu windows formantu paska stanu. Większość aplikacji MFC używa tej klasy zamiast `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Paski sterowania Windows

Te paski sterowania są alokowania elastycznego otoki dla odpowiednich kontrolek Windows. Ponieważ nie są zintegrowane z architekturą, są one trudniejsze do użycia niż paski sterowania wymienionych powyżej. Większość aplikacji MFC używa paski sterowania wymienionych powyżej.

[Z CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementuje wewnętrznej kontroli `CRebar` obiektu.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Poziomy okno zwykle są podzielone na okienka, w których aplikacja może wyświetlać informacje o stanie.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Oferuje funkcje formantu typowego paska narzędzi Windows.

## <a name="related-classes"></a>Klasy pokrewne

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Niewielkie okno podręczne, które wyświetla pojedynczy wiersz tekstu opisującego cel narzędzia w aplikacji.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Obsługuje trwałego magazynowania dokowania pasków sterowania dane o stanie.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

