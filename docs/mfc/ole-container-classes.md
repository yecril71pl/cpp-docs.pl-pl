---
title: Klasy kontenerów OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 518ae4889a2c5d9dae10e5b5cba6845010ba883c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517146"
---
# <a name="ole-container-classes"></a>Klasy kontenerów OLE

Te klasy są używane przez aplikacje kontenera. Zarówno `COleLinkingDoc` i `COleDocument` Zarządzanie kolekcjami `COleClientItem` obiektów. Zamiast wyprowadzanie klasy dokumentów z `CDocument`, będzie pochodzi on z `COleLinkingDoc` lub `COleDocument`, w zależności od tego, czy potrzebujesz pomocy technicznej dla łączy do obiektów osadzonych w dokumencie.

Użyj `COleClientItem` obiektu do reprezentowania każdego elementu OLE w dokumencie, która jest osadzony z innego dokumentu lub link do innego dokumentu.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Obsługuje zawierania dokumentów aktywnych.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Używany do wykonania złożonego dokumentu, a także obsługa kontenerów podstawowe. Służy jako kontener dla klasy pochodnej z `CDocItem`. Ta klasa może służyć jako klasa bazowa dla kontenerów dokumentów i jest klasą bazową dla `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Klasa pochodząca z `COleDocument` , zapewnia infrastrukturę do konsolidacji. Klasy dokumentów powinien pochodzić dla aplikacji kontenera z tej klasy zamiast z `COleDocument` Jeśli chcesz, aby zapewnić obsługę łącza do osadzonych obiektów.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Przechowuje listę elementów klienta OLE, które znajdują się w formancie edycji wzbogaconej. Używane z [CRichEditView](../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem`. Obiekty klasy pochodne `CDocItem` reprezentują części dokumentów.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Klasa elementu klienta, który reprezentuje połączenie do elementu OLE osadzony lub połączony po stronie klienta. Pochodzi elementów klienta od tej klasy.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Umożliwia dostęp klienta do elementu są przechowywane w formancie edycji wzbogaconej, gdy jest używane z OLE `CRichEditView` i `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Wyjątek, wynikające z wystąpił błąd podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

