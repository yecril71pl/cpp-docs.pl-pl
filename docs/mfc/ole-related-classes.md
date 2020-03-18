---
title: Klasy związane z mechanizmem OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447607"
---
# <a name="ole-related-classes"></a>Klasy związane z mechanizmem OLE

Klasy te udostępniają wiele różnych usług, w tym od wyjątków do plików wejściowych i wyjściowych.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Służy do tworzenia elementów na żądanie z innych kontenerów. Ta klasa służy jako klasa bazowa dla bardziej specyficznych typów fabryk, w tym `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Służy do zarządzania współbieżnością przy użyciu prostych wywołań procedur zdalnych OLE (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Używa interfejsu COM `IStream`, aby zapewnić `CFile` dostęp do plików złożonych. Ta klasa (pochodna z `CFile`) umożliwia serializacji MFC Używanie magazynu strukturalnego OLE.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Służy do zezwalania na przeniesienie, zmianę rozmiarów i zmiana położenia elementów w miejscu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
