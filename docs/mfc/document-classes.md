---
title: Klasy dokumentów
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615805"
---
# <a name="document-classes"></a>Klasy dokumentów

Obiekty klasy dokumentu, tworzone przez obiekty szablonu dokumentu, zarządzają danymi aplikacji. Klasa będzie dziedziczyć dla dokumentów z jednej z tych klas.

Obiekty klasy dokumentu współpracują z obiektami widoku. Obiekty widoku reprezentują obszar klienta okna, wyświetlają dane dokumentu i umożliwiają użytkownikom współdziałanie z nim. Dokumenty i widoki są tworzone przez obiekt szablonu dokumentu.

[CDocument](reference/cdocument-class.md)<br/>
Klasa bazowa dla dokumentów specyficznych dla aplikacji. Utwórz klasy dokumentu lub klasy z `CDocument` .

[COleDocument](reference/coledocument-class.md)<br/>
Używany do implementacji dokumentu złożonego, a także podstawowej obsługi kontenerów. Służy jako kontener dla klas pochodzących od [CDocItem](reference/cdocitem-class.md). Ta klasa może być używana jako klasa bazowa dla dokumentów kontenera i jest klasą bazową dla `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Klasa pochodna `COleDocument` , która zapewnia infrastrukturę do łączenia. Klasy dokumentów dla aplikacji kontenera należy dziedziczyć z tej klasy zamiast z, `COleDocument` Jeśli chcesz, aby obsługiwały linki do obiektów osadzonych.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Zachowuje listę elementów klienta OLE, które znajdują się w kontrolce edycji wzbogaconej. Używany z [CRichEditView](reference/cricheditview-class.md) i [CRichEditCntrItem](reference/cricheditcntritem-class.md).

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Używane jako klasa bazowa dla klas dokumentu aplikacji serwera. `COleServerDoc`obiekty zapewniają zbiorczą obsługę serwera za pomocą interakcji z obiektami [COleServerItem](reference/coleserveritem-class.md) . Możliwość edycji wizualnej jest dostępna przy użyciu architektury dokumentu/widoku biblioteki klas.

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
Oferuje programowi [CHtmlEditView](reference/chtmleditview-class.md)funkcjonalność platformy edycji HTML przeglądarki WebBrowser w kontekście architektury widoku dokumentu MFC.

## <a name="related-classes"></a>Powiązane klasy

Obiekty klasy dokumentu mogą być trwałe — innymi słowy mogą zapisywać ich stan na nośniku magazynu i odczytywać je z powrotem. MFC udostępnia `CArchive` klasy do ułatwienia przenoszenia danych dokumentu do nośnika magazynu.

[CArchive](reference/carchive-class.md)<br/>
Współdziała z obiektem [CFile](reference/cfile-class.md) , aby zaimplementować trwały magazyn dla obiektów przy użyciu serializacji (zobacz [CObject:: serializować](reference/cobject-class.md#serialize)).

Dokumenty mogą również zawierać obiekty OLE. `CDocItem`jest klasą podstawową elementów serwera i klienta.

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa klasy [COleClientItem](reference/coleclientitem-class.md) i [COleServerItem](reference/coleserveritem-class.md). Obiekty klas pochodzących od `CDocItem` reprezentowania części dokumentów.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
