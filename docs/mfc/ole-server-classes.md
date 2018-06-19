---
title: Klasy serwerów OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fc737a3d11307dff917132bfd113896b4ad801f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350432"
---
# <a name="ole-server-classes"></a>Klasy serwerów OLE
Te klasy są używane przez serwer aplikacji. Dokumenty serwera są uzyskiwane z `COleServerDoc` , a nie z **CDocument**. Należy pamiętać, że ponieważ `COleServerDoc` jest pochodną `COleLinkingDoc`, dokumenty serwera można także kontenerów, które obsługuje łączenia.  
  
 `COleServerItem` Klasa reprezentuje dokumentu lub części dokumentu, która może być osadzony w innym dokumencie lub połączony.  
  
 `COleIPFrameWnd` i `COleResizeBar` obsługuje edycji w miejscu, gdy obiekt jest w kontenerze i `COleTemplateServer` obsługuje tworzenie pary dokument/widok, tak, aby obiektów OLE z innych aplikacji można edytowane.  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Używany jako klasa podstawowa dla klasy dokumentów aplikacji serwera. `COleServerDoc` obiekty dostarczają zbiorczego obsługi serwera za pomocą interakcji z `COleServerItem` obiektów. Visual możliwości edycji jest realizowane przy użyciu architektury dokument/widok biblioteki klas.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstrakcyjna klasa podstawowa z `COleClientItem` i `COleServerItem`. Obiekty klas pochodnych `CDocItem` reprezentują części dokumentów.  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 Używany do reprezentowania interfejsu OLE `COleServerDoc` elementów. Jest zwykle `COleServerDoc` obiektu, który reprezentuje osadzonych części dokumentu. Na serwerach, które obsługują łącza do części dokumentów, może istnieć wiele `COleServerItem` obiektów, z których każdy reprezentuje łącze do części dokumentu.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Udostępnia ramkę okna w widoku, gdy dokument serwera jest edytowany w miejscu.  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 Udostępnia standardowy interfejs użytkownika do zmiany rozmiaru w miejscu. Obiekty z tej klasy są zawsze używane w połączeniu z `COleIPFrameWnd` obiektów.  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 Używany do tworzenia dokumentów za pomocą architektury dokument/widok struktury. A `COleTemplateServer` obiektu deleguje większość pracy do skojarzony `CDocTemplate` obiektu.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Wystąpił wyjątek awarii podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

