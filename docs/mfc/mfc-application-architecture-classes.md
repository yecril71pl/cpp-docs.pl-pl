---
title: "Klasy związane z architekturą aplikacji MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b809daac194e1fed3abe98452c02f1521111fee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-application-architecture-classes"></a>Klasy związane z architekturą aplikacji MFC
Klasy w tej kategorii przyczyniają się do architektury aplikacji framework. Dostarczają funkcji wspólnych dla większości aplikacji. Wypełnij platformę, by dodać funkcje specyficzne dla aplikacji. Zazwyczaj można to zrobić przez wyprowadzanie z klas architektura nowe klasy i następnie dodanie nowych elementów członkowskich lub zastępowanie istniejących funkcji Członkowskich.  
  
 [Kreatorzy aplikacji](../mfc/reference/mfc-application-wizard.md) wygenerować kilka typów aplikacji, które używają struktury aplikacji na różne sposoby. SDI (interfejs pojedynczego dokumentu) i aplikacje MDI (interfejsu wielu dokumentów) wykorzystać część framework o nazwie architektury dokument/widok. Inne typy aplikacji, takich jak opartych na oknach dialogowych aplikacji, opartych na formularzach aplikacji i bibliotek DLL, użyj tylko niektóre funkcje architektury dokument/widok.  
  
 Aplikacje dokument/widok zawiera co najmniej jeden zbiór dokumentów, widoków i okien ramowych. Obiekt szablonu dokumentu kojarzy klasy dla każdego zestawu dokument/widok/ramki.  
  
 Chociaż nie trzeba używać architektury dokument/widok w aplikacji MFC, istnieje wiele zalet w ten sposób. MFC OLE kontenera i serwera obsługi jest oparta na architekturze dokument/widok jest obsługę drukowania i podglądu wydruku.  
  
 Wszystkie aplikacje MFC ma co najmniej dwa obiekty: obiekt aplikacji pochodzące z [CWinApp](../mfc/reference/cwinapp-class.md)i zainicjowania obiektu głównego okna pochodną (często pośrednio) [CWnd](../mfc/reference/cwnd-class.md). (W większości przypadków jest pochodną głównego okna [cframewnd —](../mfc/reference/cframewnd-class.md), [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md), lub [cdialog —](../mfc/reference/cdialog-class.md), z których pochodzą od `CWnd`.)  
  
 Aplikacje używające architektury dokument/widok zawiera dodatkowe obiekty. Obiekty główne są:  
  
-   Obiekt aplikacji pochodzi od klasy [CWinApp](../mfc/reference/cwinapp-class.md), jak wspomniano wcześniej.  
  
-   Co najmniej jeden obiekt klasy dokumentu pochodzi od klasy [CDocument](../mfc/reference/cdocument-class.md). Obiektów klasy dokumentu są zobowiązani do reprezentacji wewnętrznej manipulować w widoku danych. Mogą być skojarzone z plikiem danych.  
  
-   Co najmniej jeden obiekt widoku pochodzi od klasy [CView](../mfc/reference/cview-class.md). Każdy widok jest typu window, który jest dołączony do dokumentu i skojarzone z ramki okna. Widoki wyświetlanie i manipulowanie danymi zawarte w obiekcie klasy dokumentu.  
  
 Dokument/widok aplikacje zawierają również okien ramowych (pochodną [cframewnd —](../mfc/reference/cframewnd-class.md)) i szablony dokumentów (pochodną [cdoctemplate —](../mfc/reference/cdoctemplate-class.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

