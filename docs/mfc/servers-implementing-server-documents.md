---
title: "Serwery: Implementowanie dokumentów serwera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5d2a3f42522ecceb09261de7437446f0d5be2d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="servers-implementing-server-documents"></a>Serwery: implementowanie dokumentów serwera
W tym artykule opisano kroki, które należy wykonać, aby pomyślnie wdrożyć dokument serwera, jeśli nie określono opcji serwera OLE w Kreatorze aplikacji.  
  
#### <a name="to-define-a-server-document-class"></a>Aby zdefiniować klasy dokumentów serwera  
  
1.  Pochodzi z klasy dokumentu `COleServerDoc` zamiast **CDocument**.  
  
2.  Tworzenie elementu serwera klasy pochodzącej od `COleServerItem`.  
  
3.  Implementowanie `OnGetEmbeddedItem` funkcji członkowskiej klasy dokumentu serwera.  
  
     `OnGetEmbeddedItem`jest wywoływane, gdy użytkownik aplikacji kontenera tworzy lub edytować element osadzony. Powinien zostać zwrócony element reprezentujący całego dokumentu. Powinna to być obiekt z `COleServerItem`-klasy.  
  
4.  Zastąpienie `Serialize` funkcji członkowskiej do serializacji zawartość dokumentu. Nie należy do serializacji na liście elementów serwera, o ile nie są używane do reprezentowania danych natywnych w dokumencie. Aby uzyskać więcej informacji, zobacz *elementy Implementowanie serwera* w artykule [serwery: elementy serwera](../mfc/servers-server-items.md).  
  
 Po utworzeniu dokumentu serwera platformę automatycznie rejestruje dokumentu OLE systemowej biblioteki dll. Dzięki temu bibliotek DLL zidentyfikować serwer dokumentów.  
  
 Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md) i [COleServerDoc](../mfc/reference/coleserverdoc-class.md) w *informacje dotyczące biblioteki klas*.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../mfc/servers.md)   
 [Serwery: Elementy serwera](../mfc/servers-server-items.md)   
 [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)   
 [Serwery: Implementowanie okien ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md)

