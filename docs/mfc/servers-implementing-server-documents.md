---
title: 'Serwery: Implementowanie dokumentów serwera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f15dbd16b48aade59470bfbf7e84faf4aeb03c61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380279"
---
# <a name="servers-implementing-server-documents"></a>Serwery: implementowanie dokumentów serwera
W tym artykule opisano kroki, które należy wykonać, aby pomyślnie wdrożyć dokument serwera, jeśli nie określono opcji serwera OLE w Kreatorze aplikacji.  
  
#### <a name="to-define-a-server-document-class"></a>Aby zdefiniować klasy dokumentów serwera  
  
1.  Pochodzi z klasy dokumentu `COleServerDoc` zamiast **CDocument**.  
  
2.  Tworzenie elementu serwera klasy pochodzącej od `COleServerItem`.  
  
3.  Implementowanie `OnGetEmbeddedItem` funkcji członkowskiej klasy dokumentu serwera.  
  
     `OnGetEmbeddedItem` jest wywoływane, gdy użytkownik aplikacji kontenera tworzy lub edytować element osadzony. Powinien zostać zwrócony element reprezentujący całego dokumentu. Powinna to być obiekt z `COleServerItem`-klasy.  
  
4.  Zastąpienie `Serialize` funkcji członkowskiej do serializacji zawartość dokumentu. Nie należy do serializacji na liście elementów serwera, o ile nie są używane do reprezentowania danych natywnych w dokumencie. Aby uzyskać więcej informacji, zobacz *elementy Implementowanie serwera* w artykule [serwery: elementy serwera](../mfc/servers-server-items.md).  
  
 Po utworzeniu dokumentu serwera platformę automatycznie rejestruje dokumentu OLE systemowej biblioteki dll. Dzięki temu bibliotek DLL zidentyfikować serwer dokumentów.  
  
 Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md) i [COleServerDoc](../mfc/reference/coleserverdoc-class.md) w *informacje dotyczące biblioteki klas*.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../mfc/servers.md)   
 [Serwery: Elementy serwera](../mfc/servers-server-items.md)   
 [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)   
 [Serwery: implementowanie okien ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md)

