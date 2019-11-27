---
title: 'Wyjątki: wyjątki OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246710"
---
# <a name="exceptions-ole-exceptions"></a>Wyjątki: wyjątki OLE

Techniki i obiekty obsługujące wyjątki w mechanizmie OLE są takie same jak w przypadku obsługi innych wyjątków. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [artykuł C++ nowoczesne najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md).

Wszystkie obiekty wyjątków są wyprowadzane z abstrakcyjnej klasy bazowej `CException`. MFC udostępnia dwie klasy do obsługi wyjątków OLE:

- [COleException](../mfc/reference/coleexception-class.md) Obsługa ogólnych wyjątków OLE.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) Do generowania i obsługi wyjątków wysyłania OLE (Automation).

Różnica między tymi dwiema klasami to ilość informacji, które zapewnia i gdzie są używane. `COleException` ma publiczny element członkowski danych zawierający kod stanu OLE dla wyjątku. `COleDispatchException` dostarcza więcej informacji, w tym:

- Kod błędu specyficzny dla aplikacji

- Opis błędu, taki jak "dysk zapełniony"

- Kontekst pomocy, który może być używany przez aplikację w celu podania dodatkowych informacji dla użytkownika

- Nazwa pliku pomocy aplikacji

- Nazwa aplikacji, która wygenerowała wyjątek.

`COleDispatchException` zawiera więcej informacji, dzięki którym można korzystać z produktów, takich jak Microsoft Visual Basic. Opisowy błąd można użyć w oknie komunikatu lub w innym powiadomieniu; informacje pomocy mogą pomóc użytkownikowi odpowiedzieć na warunki, które spowodowały wyjątek.

Dwie funkcje globalne odpowiadają dwóm klasom wyjątków OLE: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) i [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Są one używane do rzutowania ogólnych wyjątków OLE i wyjątków wysyłania OLE.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
