---
title: Klasy automatyzacji OLE
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 644a4930eb55636ba6e87b949ed610b725334661
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447682"
---
# <a name="ole-automation-classes"></a>Klasy automatyzacji OLE

Te klasy obsługują klientów automatyzacji (aplikacje kontrolujące inne aplikacje). Serwery automatyzacji (aplikacje, które mogą być kontrolowane przez inne aplikacje), są obsługiwane za pomocą [map wysyłania](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Służy do wywoływania serwerów automatyzacji z poziomu klienta automatyzacji. Podczas dodawania klasy Ta klasa jest używana do tworzenia klas bezpiecznych dla typów dla serwerów automatyzacji, które udostępniają bibliotekę typów.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Wyjątek wynikający z błędu podczas automatyzacji OLE. Wyjątki automatyzacji są generowane przez serwery automatyzacji i przechwytywane przez klientów usługi Automation.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
