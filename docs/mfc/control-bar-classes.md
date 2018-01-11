---
title: "Klasy pasków sterowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
helpviewer_keywords: control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44fcecbf1d7ddb6c46469f25349d972c8b317809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="control-bar-classes"></a>Klasy pasków sterowania
Paski sterowania są dołączone do ramki okna. Zawierają one przycisków, stan okienka lub szablonu okna dialogowego. Paski sterowania swobodnego, nazywane również palety narzędzia są implementowane przez dołączenie do [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) obiektu.  
  
## <a name="framework-control-bars"></a>Paski sterowania Framework  
 Te paski kontrolki są integralną częścią programu MFC framework. Są one łatwiejsza w użyciu i wydajniejsze niż systemu Windows pasków sterowania, ponieważ są one zintegrowane z architekturą. Większość aplikacji MFC używa pasków sterowania zamiast paski sterowania systemu Windows.  
  
 [Ccontrolbar —](../mfc/reference/ccontrolbar-class.md)  
 Klasa podstawowa dla paski sterowania MFC wymienione w tej sekcji. Pasek sterowania jest wyrównany do krawędzi okna ramki okna. Pasek sterowania zawiera albo `HWND`— na podstawie formantów podrzędnych lub kontrolki, nie jest oparty na `HWND`, takie jak przyciski paska narzędzi.  
  
 [Cdialogbar —](../mfc/reference/cdialogbar-class.md)  
 Pasek sterowania, który jest oparty na szablonie — okno dialogowe.  
  
 [Crebar —](../mfc/reference/crebar-class.md)  
 Obsługuje narzędzi, który może zawierać więcej podrzędnych windows w postaci formantów.  
  
 [Ctoolbar —](../mfc/reference/ctoolbar-class.md)  
 Z systemem windows formantu paska narzędzi, które nie zawierają przyciski poleceń mapy bitowej na `HWND`. Klasa używana w większości aplikacji MFC zamiast `CToolBarCtrl`.  
  
 [Cstatusbar —](../mfc/reference/cstatusbar-class.md)  
 Klasa podstawowa dla systemu windows formantu paska stanu. Klasa używana w większości aplikacji MFC zamiast `CStatusBarCtrl`.  
  
## <a name="windows-control-bars"></a>Paski sterowania systemu Windows  
 Pasków sterowania są alokowania otoki dla odpowiedniego formantów systemu Windows. Ponieważ nie są zintegrowane z architekturą, są one trudniej Użyj niż paski sterowania wymienionego powyżej. Większość aplikacji MFC używa paski sterowania wymienionego powyżej.  
  
 [Crebarctrl —](../mfc/reference/crebarctrl-class.md)  
 Implementuje wewnętrznej kontroli `CRebar` obiektu.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Poziomy okno zwykle podzielone okienka, w których aplikacja może wyświetlać informacje o stanie.  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Udostępnia funkcje formantu typowych narzędzi systemu Windows.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Małe okno podręczne wyświetlające pojedynczy wiersz tekst opisujący cel narzędzia w aplikacji.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Obsługuje trwałego magazynu o dokowania pasków sterowania dane o stanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

