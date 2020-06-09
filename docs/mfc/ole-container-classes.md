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
ms.openlocfilehash: 596b94e7fdbb5d9dc1862867001f6c01c1aea7b2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617810"
---
# <a name="ole-container-classes"></a>Klasy kontenerów OLE

Te klasy są używane przez aplikacje kontenera. Zarówno `COleLinkingDoc` kolekcje obiektów, jak i `COleDocument` zarządzanie nimi `COleClientItem` . Zamiast wypełniania klasy dokumentu z programu `CDocument` , należy utworzyć ją od `COleLinkingDoc` lub, w zależności od tego `COleDocument` , czy chcesz obsługiwać linki do obiektów osadzonych w dokumencie.

Użyj `COleClientItem` obiektu do reprezentowania każdego elementu OLE w dokumencie, który jest osadzony z innego dokumentu lub link do innego dokumentu.

[Metody COleDocObjectItem](reference/coledocobjectitem-class.md)<br/>
Obsługuje zawieranie dokumentów aktywnych.

[COleDocument](reference/coledocument-class.md)<br/>
Używany do implementacji dokumentu złożonego, a także podstawowej obsługi kontenerów. Służy jako kontener dla klas pochodzących od `CDocItem` . Ta klasa może być używana jako klasa bazowa dla dokumentów kontenera i jest klasą bazową dla `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Klasa pochodna `COleDocument` , która zapewnia infrastrukturę do łączenia. Klasy dokumentów dla aplikacji kontenera należy dziedziczyć z tej klasy zamiast z, `COleDocument` Jeśli chcesz, aby obsługiwały linki do obiektów osadzonych.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Zachowuje listę elementów klienta OLE, które znajdują się w kontrolce edycji wzbogaconej. Używany z [CRichEditView](reference/cricheditview-class.md) i [CRichEditCntrItem](reference/cricheditcntritem-class.md).

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem` . Obiekty klas pochodzących od `CDocItem` reprezentowania części dokumentów.

[COleClientItem](reference/coleclientitem-class.md)<br/>
Klasa elementu klienta, która reprezentuje po stronie klienta połączenie z osadzonym lub połączonym elementem OLE. Utwórz elementy klienckie z tej klasy.

[CRichEditCntrItem](reference/cricheditcntritem-class.md)<br/>
Zapewnia dostęp po stronie klienta do elementu OLE przechowywanego w kontrolce edycji wzbogaconej, gdy jest używany z `CRichEditView` i `CRichEditDoc` .

[COleException](reference/coleexception-class.md)<br/>
Wyjątek wynikający z błędu przetwarzania OLE. Ta klasa jest używana przez kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
