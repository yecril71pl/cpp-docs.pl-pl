---
title: 'Serwery: Elementy serwera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e83b75183fe226b4ff384a00b0b5260caba01efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="servers-server-items"></a>Serwery: elementy serwera
Gdy kontener uruchamia serwer sieci, dzięki czemu użytkownik może edytować element osadzony lub połączony OLE, aplikacja serwera tworzy "elementu serwera". Element serwera, który jest obiektem klasy pochodne `COleServerItem`, udostępnia interfejs między dokument serwera i aplikacji kontenera.  
  
 `COleServerItem` Klasa definiuje kilka funkcji możliwym do zastąpienia elementów członkowskich, które są wywoływane przez OLE, zwykle w odpowiedzi na żądania z kontenera. Elementy serwera może reprezentować części dokumentu serwera lub całego dokumentu. Gdy element OLE jest osadzony w dokumencie kontenera, element serwera reprezentuje dokument całego serwera. Po połączeniu elementu OLE elementu serwera może reprezentować części dokumentu serwera lub całego dokumentu w zależności od tego, czy łącze jest części lub całości.  
  
 W [HIERSVR](../visual-cpp-samples.md) przykładowe, na przykład klasa elementu serwera **CServerItem**, ma element członkowski, który jest wskaźnikiem do obiektu klasy **CServerNode**. **CServerNode** obiektu jest węzłem w dokumencie aplikacji HIERSVR, w którym jest drzewo. Gdy **CServerNode** obiekt jest węzeł główny **CServerItem** obiekt reprezentuje cały dokument. Gdy **CServerNode** obiektu jest elementem podrzędnym, **CServerItem** obiekt reprezentuje część dokumentu. Zobacz przykład MFC OLE [HIERSVR](../visual-cpp-samples.md) przykład interakcji.  
  
##  <a name="_core_implementing_server_items"></a> Implementowanie elementy serwera  
 Jeśli używasz Kreatora aplikacji do tworzenia "starter" kodu aplikacji, wystarczy wykonać, aby uwzględnić elementy serwera w kodzie starter jest wybierz jedną z opcji serwera na stronie opcje OLE. Jeśli dodajesz serwera elementy do istniejącej aplikacji, wykonaj następujące czynności:  
  
#### <a name="to-implement-a-server-item"></a>Aby zaimplementować elementu serwera  
  
1.  Klasa wyprowadzona z `COleServerItem`.  
  
2.  W klasie pochodnej zastąpienie `OnDraw` funkcję elementu członkowskiego.  
  
     Wywołania framework `OnDraw` aby renderować element OLE w metaplik. Aplikacja kontenera używa tego metaplik do renderowania elementu. Klasa widoku aplikacji ma również `OnDraw` funkcji członkowskiej, który jest używany do renderowania elementu, gdy aplikacja jest aktywna.  
  
3.  Implementowanie zastępująca `OnGetEmbeddedItem` dla klasy dokumentu na serwerze. Aby uzyskać więcej informacji, zobacz artykuł [serwery: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md) i przykładowa MFC OLE [HIERSVR](../visual-cpp-samples.md).  
  
4.  Implementuje klasy elementu serwera `OnGetExtent` funkcję elementu członkowskiego. Struktura wywołuje tę funkcję, aby pobrać rozmiar elementu. Domyślna implementacja nie działa.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Porada dla architektury serwera — element  
 Zgodnie z opisem w [elementy Implementowanie serwera](#_core_implementing_server_items), aplikacje serwera musi mieć możliwość wyświetlania elementów zarówno w widoku serwera, jak i w metaplik używany przez aplikację kontenera. Biblioteka Microsoft Foundation klasy architektury aplikacji w, klasy widoku dla `OnDraw` funkcji członkowskiej renderuje element, gdy jest edytowany (zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) w *informacje dotyczące biblioteki klas* ). Element serwera `OnDraw` renderuje element w metaplik we wszystkich innych przypadkach (zobacz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).  
  
 Można uniknąć duplikowania kodu pisanie funkcji pomocnika w klasie dokument serwera i wywoływanie je z `OnDraw` funkcji w widoku i elementu serwera klas. Przykładowe MFC OLE [HIERSVR](../visual-cpp-samples.md) używa tej strategii: funkcje **CServerView::OnDraw** i **CServerItem::OnDraw** zarówno wywołania **CServerDoc::DrawTree**  do renderowania elementu.  
  
 Widoku i elementu `OnDraw` funkcje Członkowskie, ponieważ ich Rysowanie w różnych warunkach. Widok należy wziąć pod uwagę takie czynniki jak powiększanie, wybór rozmiaru i zakres wycinka i elementów interfejsu użytkownika, takich jak paski przewijania. Element serwera z drugiej strony, zawsze rysuje cały obiekt OLE.  
  
 Aby uzyskać więcej informacji, zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), i [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)w *klasy odwołanie do biblioteki*.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../mfc/servers.md)

