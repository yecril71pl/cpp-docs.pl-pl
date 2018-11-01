---
title: Klasy związane z mechanizmem OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 2c3aa5ea4e720b14c5fdc4cb3285cd812eb550e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584655"
---
# <a name="ole-related-classes"></a>Klasy związane z mechanizmem OLE

Te klasy oferują szereg różnych usług, od wyjątki od plików wejściowych i wyjściowych.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Używane do tworzenia elementów, gdy wywołana z innych kontenerów. Ta klasa służy jako klasa bazowa dla bardziej specyficznych typów fabryki, w tym `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Umożliwia zarządzanie współbieżnością za pomocą OLE Lightweight zdalnego procedury wywołania (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
COM używa `IStream` interfejsu, aby zapewnić `CFile` dostęp do plików złożona (c). Ta klasa (pochodną `CFile`) umożliwia serializację MFC korzystać z magazynu strukturalnego OLE.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Umożliwia przenoszenie, zmienianie rozmiaru i reorientacji elementów w miejscu.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

