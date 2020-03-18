---
title: Klasy kontenerów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447657"
---
# <a name="ole-container-classes"></a>Klasy kontenerów OLE

Te klasy są używane przez aplikacje kontenera. Zarówno `COleLinkingDoc`, jak i `COleDocument` zarządzać kolekcjami obiektów `COleClientItem`. Zamiast wypełniania klasy dokumentu od `CDocument`, można utworzyć ją od `COleLinkingDoc` lub `COleDocument`, w zależności od tego, czy chcesz obsługiwać linki do obiektów osadzonych w dokumencie.

Użyj obiektu `COleClientItem`, aby reprezentować każdy element OLE w dokumencie osadzonym z innego dokumentu lub link do innego dokumentu.

[Metody COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Obsługuje zawieranie dokumentów aktywnych.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Używany do implementacji dokumentu złożonego, a także podstawowej obsługi kontenerów. Służy jako kontener dla klas pochodnych z `CDocItem`. Ta klasa może być używana jako klasa bazowa dla dokumentów kontenera i jest klasą bazową dla `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Klasa pochodna `COleDocument`, która udostępnia infrastrukturę do łączenia. Klasy dokumentów dla aplikacji kontenera należy utworzyć na podstawie tej klasy zamiast z `COleDocument`, jeśli chcesz, aby obsługiwały linki do obiektów osadzonych.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Zachowuje listę elementów klienta OLE, które znajdują się w kontrolce edycji wzbogaconej. Używany z [CRichEditView](../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem`. Obiekty klas pochodzących od `CDocItem` reprezentują części dokumentów.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Klasa elementu klienta, która reprezentuje po stronie klienta połączenie z osadzonym lub połączonym elementem OLE. Utwórz elementy klienckie z tej klasy.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Zapewnia dostęp po stronie klienta do elementu OLE przechowywanego w kontrolce edycji wzbogaconej, gdy jest używany z `CRichEditView` i `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Wyjątek wynikający z błędu przetwarzania OLE. Ta klasa jest używana przez kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
