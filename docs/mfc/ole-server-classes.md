---
title: Klasy serwerów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 06f5cf0985756506e42c7ad9fde24641b5a0ce93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619854"
---
# <a name="ole-server-classes"></a>Klasy serwerów OLE

Te klasy są używane przez aplikacje serwera. Dokumenty serwera pochodzą z, `COleServerDoc` a nie z `CDocument` . Należy pamiętać, że ponieważ pochodzi `COleServerDoc` z `COleLinkingDoc` , dokumenty serwera mogą również być kontenerami, które obsługują łączenie.

`COleServerItem`Klasa reprezentuje dokument lub część dokumentu, który może być osadzony w innym dokumencie lub połączony z.

`COleIPFrameWnd`i `COleResizeBar` obsługuje edytowanie w miejscu, gdy obiekt znajduje się w kontenerze i `COleTemplateServer` obsługuje tworzenie par dokumentów/widoków, aby można było edytować obiekty OLE z innych aplikacji.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Używane jako klasa bazowa dla klas dokumentu aplikacji serwera. `COleServerDoc`obiekty zapewniają zbiorczą obsługę serwera za pomocą interakcji z `COleServerItem` obiektami. Możliwość edycji wizualnej jest dostępna przy użyciu architektury dokumentu/widoku biblioteki klas.

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem` . Obiekty klas pochodzących od `CDocItem` reprezentowania części dokumentów.

[COleServerItem](reference/coleserveritem-class.md)<br/>
Używany do reprezentowania interfejsu OLE dla `COleServerDoc` elementów. Istnieje zwykle jeden `COleServerDoc` obiekt, który reprezentuje osadzoną część dokumentu. W przypadku serwerów, które obsługują linki do części dokumentów, może istnieć wiele `COleServerItem` obiektów, z których każdy reprezentuje link do części dokumentu.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramek dla widoku, gdy dokument serwera jest edytowany w miejscu.

[COleResizeBar](reference/coleresizebar-class.md)<br/>
Zapewnia standardowy interfejs użytkownika dla zmiany rozmiarów w miejscu. Obiekty tej klasy są zawsze używane w połączeniu z `COleIPFrameWnd` obiektami.

[Element COleTemplateServer](reference/coletemplateserver-class.md)<br/>
Służy do tworzenia dokumentów przy użyciu architektury dokumentu/widoku struktury. `COleTemplateServer`Obiekt deleguje większość swoich zadań do skojarzonego `CDocTemplate` obiektu.

[COleException](reference/coleexception-class.md)<br/>
Wyjątek wynikający z błędu przetwarzania OLE. Ta klasa jest używana przez kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
