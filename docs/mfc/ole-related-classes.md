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
ms.openlocfilehash: 7d58072d133b9348558804b848ecfda4497931e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378300"
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

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
