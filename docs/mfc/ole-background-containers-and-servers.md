---
title: 'Podstawy OLE: Kontenery i serwery | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f15ef532ba61a089f8adec9ed20f737c07eae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ole-background-containers-and-servers"></a>Podstawy OLE: kontenery i serwery
Aplikacji kontenera jest aplikacja, który można zastosować elementy osadzone lub połączone w swoich własnych dokumentów. Zarządza aplikacji kontenera dokumentów musi mieć możliwość przechowywania i wyświetlania elementów dokumentu OLE, a także dane utworzone przez samą aplikację. Aplikacji kontenera należy także zezwolić użytkownikom na wstawianie nowych elementów lub edytować istniejące elementy aktywowania aplikacji serwerowych, gdy jest to konieczne. Wymagania interfejsu użytkownika aplikacji kontenera są wymienione w artykule [kontenery: kwestie dotyczące interfejsu użytkownika](../mfc/containers-user-interface-issues.md).  
  
 Aplikacja serwera lub składnik aplikacji jest aplikacja, która można tworzyć składniki dokumentu OLE do użycia przez aplikacje kontenera. Aplikacje serwera zwykle obsługuje przeciągania i upuszczania lub kopiowania do Schowka swoje dane, tak aby aplikacji kontenera można wstawić danych jako element osadzony lub połączony. Aplikacja może być zarówno kontener, jak i serwera.  
  
 Większość serwerów są aplikacje autonomiczne lub pełne serwerów; one albo mogą być uruchamiane jako aplikacje autonomiczne lub można uruchomić aplikacji kontenera. Miniserver jest specjalnym rodzajem aplikacji serwera, który można uruchomić tylko przez kontener. Nie można uruchomić jako aplikacja autonomiczna. Przykłady miniservers są serwery Microsoft Draw i Microsoft Graph.  
  
 Kontenery i serwery nie komunikują się bezpośrednio. Zamiast tego komunikują się za pośrednictwem OLE systemu dołączanych dynamicznie bibliotekach (DLL). Te biblioteki DLL udostępniają funkcje, które wywołują kontenery i serwery i kontenery i serwery zapewniają funkcje wywołania zwrotnego, które wywołują bibliotek DLL.  
  
 Przy użyciu tej metody komunikacji, kontener nie musi wiedzieć, szczegóły implementacji aplikacji serwera. Umożliwia on kontenera zaakceptować elementy utworzone przez dowolny serwer bez konieczności Definiowanie typów serwerów, z którymi można pracować. W związku z tym użytkownik aplikacji kontenera mogą wykorzystać przyszłych aplikacji i formatów danych. Jeśli te nowe aplikacje są składnikami OLE, to złożonego dokumentu będą mogli dołączyć do nich elementy utworzone przez te aplikacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy OLE](../mfc/ole-background.md)   
 [Podstawy OLE: Implementacja MFC](../mfc/ole-background-mfc-implementation.md)   
 [Kontenery](../mfc/containers.md)   
 [Serwery](../mfc/servers.md)   
 [Kontenery: Elementy klienckie](../mfc/containers-client-items.md)   
 [Serwery: elementy serwera](../mfc/servers-server-items.md)

