---
title: Ramka okna klasy (architektura) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.frame
dev_langs: C++
helpviewer_keywords: frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b4a8076cbec9292718c9bc2413d690bacbc4a67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="frame-window-classes-architecture"></a>Klasy okien ramowych (architektura)
Architektura dokument/Widok okien ramowych są systemu windows, które zawierają okno widoku. One również obsługiwać konieczności kontrolowania paski dołączyć do nich.  
  
 W wielu aplikacjach interfejsu (MDI) dokumentu głównego okna jest pochodną `CMDIFrameWnd`. Zawiera on pośrednio ramki dokumentów, które są `CMDIChildWnd` obiektów. `CMDIChildWnd` Obiektów, z kolei zawierają widoki tych dokumentów.  
  
 W aplikacjach pojedynczego dokumentu (SDI) interfejsu okno główne pochodną `CFrameWnd`, zawiera widok bieżącego dokumentu.  
  
 [Cframewnd —](../mfc/reference/cframewnd-class.md)  
 Klasa podstawowa aplikacja SDI głównego okna ramowego. Również klasę podstawową dla wszystkich innych klasy okien ramowych.  
  
 [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md)  
 Klasa podstawowa dla aplikacji MDI głównego okna ramowego.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 Klasa podstawowa dla okien ramowych dokumentu aplikacji MDI.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Udostępnia ramkę okna w widoku, gdy dokument serwera jest edytowany w miejscu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

