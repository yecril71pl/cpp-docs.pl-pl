---
title: Klasy serwerów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 92dec514611dcce7d6c666fdd271843e69561637
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447587"
---
# <a name="ole-server-classes"></a>Klasy serwerów OLE

Te klasy są używane przez aplikacje serwera. Dokumenty serwera pochodzą z `COleServerDoc`, a nie z `CDocument`. Należy pamiętać, że ponieważ `COleServerDoc` pochodzi od `COleLinkingDoc`, dokumenty serwera mogą być również kontenerami, które obsługują łączenie.

Klasa `COleServerItem` reprezentuje dokument lub część dokumentu, który może być osadzony w innym dokumencie lub połączony z.

`COleIPFrameWnd` i `COleResizeBar` obsługują edytowanie w miejscu, gdy obiekt znajduje się w kontenerze, a `COleTemplateServer` obsługuje tworzenie par dokumentów/widoków, aby można było edytować obiekty OLE z innych aplikacji.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Używane jako klasa bazowa dla klas dokumentu aplikacji serwera. obiekty `COleServerDoc` zapewniają zbiorczą obsługę serwera za pomocą interakcji z obiektami `COleServerItem`. Możliwość edycji wizualnej jest dostępna przy użyciu architektury dokumentu/widoku biblioteki klas.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem`. Obiekty klas pochodzących od `CDocItem` reprezentują części dokumentów.

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Używany do reprezentowania interfejsu OLE do `COleServerDoc` elementów. Istnieje zwykle jeden obiekt `COleServerDoc`, który reprezentuje osadzoną część dokumentu. W przypadku serwerów, które obsługują linki do części dokumentów, może istnieć wiele `COleServerItem` obiektów, z których każdy reprezentuje link do części dokumentu.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramek dla widoku, gdy dokument serwera jest edytowany w miejscu.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Zapewnia standardowy interfejs użytkownika dla zmiany rozmiarów w miejscu. Obiekty tej klasy są zawsze używane w połączeniu z obiektami `COleIPFrameWnd`.

[Element COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Służy do tworzenia dokumentów przy użyciu architektury dokumentu/widoku struktury. Obiekt `COleTemplateServer` deleguje większość swoich zadań do skojarzonego obiektu `CDocTemplate`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Wyjątek wynikający z błędu przetwarzania OLE. Ta klasa jest używana przez kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
