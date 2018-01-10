---
title: "Klasy kontenerów OLE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df809971ecf8bdd8700217cf6a1965e2973de754
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-container-classes"></a>Klasy kontenerów OLE
Te klasy są używane przez aplikacje kontenera. Zarówno `COleLinkingDoc` i `COleDocument` Zarządzanie kolekcjami `COleClientItem` obiektów. Zamiast wyprowadzanie klasy dokumentów z **CDocument**, będzie pochodzić z klasy `COleLinkingDoc` lub `COleDocument`, w zależności od tego, czy chcesz pomocy technicznej dla łącza do obiektów osadzonych w dokumencie.  
  
 Użyj `COleClientItem` obiektu do reprezentowania każdego elementu OLE w dokumencie, który jest osadzony z innego dokumentu lub link do innego dokumentu.  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 Obsługuje zawieranie dokumentów aktywnych.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Używane do implementacji złożonego dokumentu, a także zapewnia obsługę podstawowe kontenera. Służy jako kontener dla klas pochodnych `CDocItem`. Ta klasa może służyć jako klasę podstawową dla dokumentów i jest klasą bazową dla kontenera `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Klasa pochodna od `COleDocument` który zapewnia infrastrukturę do konsolidacji. Klasy dokumentów powinien pochodzić z tej klasy, a nie z aplikacji kontenera `COleDocument` Jeśli chcesz, aby zapewnić obsługę łącza do osadzonych obiektów.  
  
 [Cricheditdoc —](../mfc/reference/cricheditdoc-class.md)  
 Przechowuje listę elementów OLE klienta, które są kontrolki zaawansowanej edycji. Używane z [cricheditview —](../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstrakcyjna klasa podstawowa z `COleClientItem` i `COleServerItem`. Obiekty klas pochodnych `CDocItem` reprezentują części dokumentów.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 Klasa elementu klienta, która reprezentuje po stronie klienta połączenia osadzonego lub połączonego elementu OLE. Elementy klienckie dziedziczyć po tej klasie.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Umożliwia dostęp klienta do OLE elementu przechowywane w formancie edycji wzbogaconej, gdy jest używany z `CRichEditView` i `CRichEditDoc`.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Wystąpił wyjątek awarii podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

