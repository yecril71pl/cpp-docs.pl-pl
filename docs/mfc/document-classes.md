---
title: "Klasy dokumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a2436b46b7486bd30398dffc530d2adea3d2e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="document-classes"></a>Klasy dokumentów
Obiekty klasy dokumentu, utworzone przez obiekty szablonu dokumentu, zarządzanie danych aplikacji. Klasy dokumentów uzyskuje z jednego z tych klas.  
  
 Obiektów klasy dokumentu interakcji z obiektami widoku. Obiekty widoku reprezentują obszaru klienckiego okna, dane dokumentu i Zezwól użytkownikom na interakcję z nią. Dokumenty i widoki są tworzone przez obiekt szablonu dokumentu.  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 Klasa podstawowa dla dokumentów aplikacji. Pochodzi z klasy dokumentu lub klas z **CDocument**.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Używane do implementacji złożonego dokumentu, a także zapewnia obsługę podstawowe kontenera. Służy jako kontener dla klas pochodnych [CDocItem](../mfc/reference/cdocitem-class.md). Ta klasa może służyć jako klasę podstawową dla dokumentów i jest klasą bazową dla kontenera `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Klasa pochodna od `COleDocument` który zapewnia infrastrukturę do konsolidacji. Klasy dokumentów powinien pochodzić z tej klasy, a nie z aplikacji kontenera `COleDocument` Jeśli chcesz, aby zapewnić obsługę łącza do osadzonych obiektów.  
  
 [Cricheditdoc —](../mfc/reference/cricheditdoc-class.md)  
 Przechowuje listę elementów OLE klienta, które są kontrolki zaawansowanej edycji. Używane z [cricheditview —](../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Używany jako klasa podstawowa dla klasy dokumentów aplikacji serwera. `COleServerDoc`obiekty dostarczają zbiorczego obsługi serwera za pomocą interakcji z [COleServerItem](../mfc/reference/coleserveritem-class.md) obiektów. Visual możliwości edycji jest realizowane przy użyciu architektury dokument/widok biblioteki klas.  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 Udostępnia, z [CHtmlEditView](../mfc/reference/chtmleditview-class.md), funkcje platformy edycji WebBrowser HTML w kontekście architektury dokument widok MFC.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 Obiektów klasy dokumentu może być trwałe — innymi słowy, można zapisać ich stan nośnika magazynowania i ponownie go odczytać. Udostępnia MFC `CArchive` klasy w celu ułatwienia transferu danych dokumentu do nośnika magazynowania.  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 Współpracuje z [cfile —](../mfc/reference/cfile-class.md) obiektu do zaimplementowania magazynu trwałego dla obiektów za pomocą serializacji (zobacz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 Dokumenty mogą również zawierać obiektów OLE. `CDocItem`jest klasą bazową dla elementów serwera i klienta.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstrakcyjna klasa podstawowa z [COleClientItem](../mfc/reference/coleclientitem-class.md) i [COleServerItem](../mfc/reference/coleserveritem-class.md). Obiekty klas pochodnych `CDocItem` reprezentują części dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

