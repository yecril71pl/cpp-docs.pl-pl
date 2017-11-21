---
title: Historia modelu DCOM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation, DCOM
- DCOM, about DCOM
- DCOM
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9e5607fd240c7a97691189b8a3afa5e7c0171e26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="history-of-dcom"></a>Historia modelu DCOM
Automatyzacja została wprowadzona w wczesne 1993, został mogą być wykorzystywane tylko między aplikacjami działającymi na tym samym komputerze. Jednak ponieważ on udostępniony tego samego underpinnings jako reszty OLE, który jest (COM lub model Component Object Model), zawsze ma czy jego stanie się "lokalnie" COM sam czasie aktualizacji uwzględnienie możliwości komunikacji zdalnej. Również zaplanowano, że przejście od operacji wyłącznie lokalnych do rozproszonej operacji wymaga niewielkiego lub żadnego zmiany istniejącego kodu.  
  
 Dlatego co "remoting" oznacza lokalnego COM definiowane że znajdują się konsumenta interfejsu i wykonać na tym samym komputerze, ponieważ dostawca tego interfejsu. Na przykład program Microsoft Visual Basic można kontrolować kopii programu Microsoft Excel na tym komputerze pulpitu, ale nie umożliwia kierowanie wykonanie programu Excel na innym komputerze. Wraz z rozwojem rozproszonego modelu COM interfejsu nie jest już musi znajdować się na tym samym komputerze co wykonujący na którym dostawca interfejsu.  
  
 Po COM została dostosowana do pracy w sieci, następnie żadnego interfejsu, które nie zostało powiązane modelu wykonanie lokalne (niektóre interfejsy ma nieodłącznej zależność od urządzenia na komputerze lokalnym, takich jak rysunek interfejsy którego metody mają dojścia do konteksty urządzenia jako Parametry) była możliwość dystrybucji. Konsumenta interfejsu spowodowałoby żądania dla danego interfejsu; Ten interfejs mogą być udostępniane przez wystąpienie obiektu uruchomione (lub do uruchamiania) na innym komputerze. Mechanizm dystrybucji wewnątrz COM klient może zostać nawiązane połączenie dostawcy w taki sposób, że wywołania metody przez klienta pojawią się na końcu dostawcy, gdzie będą wykonywane. Wszelkie zwracać wartości może następnie zostać odesłana do klienta. Do wszystkich intents i purposes dystrybucji jest niewidoczny dla zarówno klient, jak i dostawcy.  
  
 Teraz istnieje różnych com. DCOM (dla "rozproszonego modelu COM") została wysłana z wersjami systemu Windows NT, począwszy od wersji 4.0 i tym systemu Windows 2000. Od późne 1996 również było dostępne dla systemu Windows 9 x. W obu przypadkach DCOM obejmuje zestaw zastępczy i dodatkowych bibliotek DLL, z niektórych narzędzi, które zapewniają możliwości COM lokalnych i zdalnych. W związku z tym jest teraz nieodłączną część platformach opartych na Win32 i będą dostępne na innych platformach przez inne organizacje wraz z upływem czasu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Gdzie automatyzacji zdalnej pasują do](where-does-remote-automation-fit-in-q.md)  
  
 [Co oferuje zdalna Automatyzacja](what-does-remote-automation-provide-q.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja zdalna](../mfc/remote-automation.md)
