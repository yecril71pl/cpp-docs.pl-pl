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
ms.openlocfilehash: 9994cdadb0ca2924a3ac773752ae40f3a750b74f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442893"
---
# <a name="ole-server-classes"></a>Klasy serwerów OLE

Te klasy są używane przez aplikacje serwera. Dokumenty serwera są uzyskiwane z `COleServerDoc` , a nie z `CDocument`. Należy pamiętać, że ponieważ `COleServerDoc` jest tworzony na podstawie `COleLinkingDoc`, dokumentów serwera może być również kontenery, które obsługują łączenie.

`COleServerItem` Klasa reprezentuje dokument lub jego części dokumentu, które mogą być osadzone w innym dokumencie lub połączone.

`COleIPFrameWnd` i `COleResizeBar` obsługuje edycję w miejscu, gdy obiekt jest w kontenerze i `COleTemplateServer` obsługuje tworzenie par dokument/widok, dzięki czemu można je edytować obiekty OLE z innych aplikacji.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Używane jako klasa bazowa dla klas dokumentów aplikacji serwera. `COleServerDoc` obiekty oferują zbiorczego serwera pomocy technicznej w ramach interakcji z `COleServerItem` obiektów. Wizualne możliwości edycji są dostarczane, przy użyciu architektury dokument/widok biblioteki klas.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakcyjna klasa bazowa `COleClientItem` i `COleServerItem`. Obiekty klasy pochodne `CDocItem` reprezentują części dokumentów.

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Używany do reprezentowania interfejsu OLE do `COleServerDoc` elementów. Ma to zwykle spowodowane jednym `COleServerDoc` obiektu, który reprezentuje części osadzonego dokumentu. Na serwerach, które obsługują linki do części dokumentów, może istnieć wiele `COleServerItem` obiektów, z których każdy reprezentuje łącze do części dokumentu.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramowe w celu wyświetlenia, gdy dokument serwera jest edytowany w miejscu.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Udostępnia standardowy interfejs użytkownika do zmiany rozmiaru w miejscu. Obiekty tej klasy są zawsze używane w połączeniu z `COleIPFrameWnd` obiektów.

[Element COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Używane do tworzenia dokumentów za pomocą architektury dokument/widok struktury. A `COleTemplateServer` obiektu deleguje większość swojej pracy, aby skojarzone `CDocTemplate` obiektu.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Wyjątek, wynikające z wystąpił błąd podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

