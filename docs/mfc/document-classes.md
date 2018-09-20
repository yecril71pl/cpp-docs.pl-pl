---
title: Klasy dokumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b76ac2be6c864a0a6f52feb282b13ab831fa31ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413344"
---
# <a name="document-classes"></a>Klasy dokumentów

Obiekty klasy dokumentów, tworzone przez obiekty szablonu dokumentu, zarządzanie danymi aplikacji. Będzie wyprowadzić klasę dla dokumentów z jednego z tych klas.

Obiekty klasy dokumentu wchodzić w interakcje z obiektów widoku. Wyświetl obiekty reprezentują obszaru klienckiego okna wyświetlania danych dokumentu i Zezwól użytkownikom na interakcję z nią. Dokumenty i widoki są tworzone przez obiekt szablonu dokumentu.

[CDocument](../mfc/reference/cdocument-class.md)<br/>
Klasa podstawowa dla dokumentów specyficzne dla aplikacji. Pochodzi z klasy dokumentu lub klasy z `CDocument`.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Używany do wykonania złożonego dokumentu, a także obsługa kontenerów podstawowe. Służy jako kontener dla klasy pochodnej z [CDocItem](../mfc/reference/cdocitem-class.md). Ta klasa może służyć jako klasa bazowa dla kontenerów dokumentów i jest klasą bazową dla `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Klasa pochodząca z `COleDocument` , zapewnia infrastrukturę do konsolidacji. Klasy dokumentów powinien pochodzić dla aplikacji kontenera z tej klasy zamiast z `COleDocument` Jeśli chcesz, aby zapewnić obsługę łącza do osadzonych obiektów.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Przechowuje listę elementów klienta OLE, które znajdują się w formancie edycji wzbogaconej. Używane z [CRichEditView](../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Używane jako klasa bazowa dla klas dokumentów aplikacji serwera. `COleServerDoc` obiekty oferują zbiorczego serwera pomocy technicznej w ramach interakcji z [COleServerItem](../mfc/reference/coleserveritem-class.md) obiektów. Wizualne możliwości edycji są dostarczane, przy użyciu architektury dokument/widok biblioteki klas.

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
Udostępnia, za pomocą [CHtmlEditView](../mfc/reference/chtmleditview-class.md), funkcje platformy edycji WebBrowser w formacie HTML w kontekście architektury widoku dokumentu MFC.

## <a name="related-classes"></a>Klasy pokrewne

Obiekty klasy dokumentu może być stałe — innymi słowy, można zapisać ich stanu na nośniku i ponownie je odczytać. Biblioteka MFC zawiera `CArchive` klasy w celu ułatwienia przesyłania danych dokumentu na nośniku.

[CArchive](../mfc/reference/carchive-class.md)<br/>
Współpracuje z [CFile](../mfc/reference/cfile-class.md) obiektu do zaimplementowania trwałego magazynu obiektów za pomocą serializacji (zobacz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

Dokumenty mogą również zawierać obiekty OLE. `CDocItem` jest klasą bazową elementów serwera i klienta.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa [COleClientItem](../mfc/reference/coleclientitem-class.md) i [COleServerItem](../mfc/reference/coleserveritem-class.md). Obiekty klasy pochodne `CDocItem` reprezentują części dokumentów.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

