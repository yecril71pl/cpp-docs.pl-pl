---
title: 'Serwery: Implementowanie dokumentów serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: 17ced1cdb0b40b13fbda68150030efde5735ba7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307916"
---
# <a name="servers-implementing-server-documents"></a>Serwery: Implementowanie dokumentów serwera

W tym artykule opisano kroki, które należy wykonać, aby pomyślnie wdrożyć dokumentu na serwerze, jeśli nie określono opcji serwera OLE w Kreatorze aplikacji.

#### <a name="to-define-a-server-document-class"></a>Aby zdefiniować klasę dokumentów serwera

1. Pochodzi z klasy dokumentu `COleServerDoc` zamiast `CDocument`.

1. Tworzenie elementu serwera klasy pochodzącej od `COleServerItem`.

1. Implementowanie `OnGetEmbeddedItem` funkcji składowej klasy dokumentu serwera.

   `OnGetEmbeddedItem` jest wywoływana, gdy użytkownik aplikacji kontenera tworzy lub edytuje element osadzony. Powinien zostać zwrócony element reprezentujący całego dokumentu. Powinno to być obiekt usługi `COleServerItem`-klasy pochodnej.

1. Zastąp `Serialize` funkcja elementu członkowskiego do serializacji zawartość dokumentu. Nie trzeba do serializacji lista elementów serwera, o ile nie są używane do reprezentowania danych natywnych w dokumencie. Aby uzyskać więcej informacji, zobacz *elementy serwera wdrażania* w artykule [serwerów: Elementy serwera](../mfc/servers-server-items.md).

Po utworzeniu dokumentu na serwerze platformę powoduje automatyczne zarejestrowanie dokumentu przy użyciu bibliotek DLL systemu OLE. Dzięki temu bibliotek DLL w celu identyfikowania dokumentów serwera.

Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md) i [COleServerDoc](../mfc/reference/coleserverdoc-class.md) w *odwołanie do biblioteki klas*.

## <a name="see-also"></a>Zobacz także

[Serwery](../mfc/servers.md)<br/>
[Serwery: Elementy serwera](../mfc/servers-server-items.md)<br/>
[Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)<br/>
[Serwery: Implementowanie Windows ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md)
