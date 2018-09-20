---
title: Klasy związane z OLE | Dokumentacja firmy Microsoft
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
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43dadaa4aaefa677106710d1adbcdf0e60be59d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411316"
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

