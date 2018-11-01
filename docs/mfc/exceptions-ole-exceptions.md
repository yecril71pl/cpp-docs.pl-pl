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
ms.openlocfilehash: 2732f571d305fda2b739be02661ab9558f8bc653
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515425"
---
# <a name="exceptions-ole-exceptions"></a>Wyjątki: wyjątki OLE

Techniki i funkcje służące do obsługi wyjątków w OLE są takie same jak w przypadku obsługi innych wyjątków. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz artykuł [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md).

Wszystkie obiekty wyjątków są uzyskiwane z abstrakcyjna klasa bazowa `CException`. Biblioteka MFC zawiera dwie klasy do obsługi wyjątki OLE:

- [COleException](../mfc/reference/coleexception-class.md) obsługę ogólne wyjątki OLE.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) dla generowania i obsługa OLE wysyłania wyjątków (automation).

Różnica między tymi dwoma klasami jest ilość informacji zapewniają one oraz gdzie są używane. `COleException` ma składową danych publicznego, który zawiera kod stanu OLE, dla wyjątku. `COleDispatchException` dostarcza więcej informacji, w tym następujące:

- Kod błędu specyficzne dla aplikacji

- Opis błędu, takie jak "Dysk zapełniony:"

- Kontekst pomocy, który aplikacja może używać dostarczenie dodatkowych informacji dla użytkownika

- Nazwa pliku Pomocy usługi aplikacji

- Nazwa aplikacji, który wygenerował wyjątek

`COleDispatchException` zawiera więcej informacji, dzięki czemu może służyć za pomocą produktów takich jak Microsoft Visual Basic. Opis błędu ustnej mogą być używane w oknie komunikatu lub inne powiadomienia; informacje pomocy można pomóc użytkownikowi odpowiadanie na warunki, które powoduje wyjątek.

Dwie funkcje globalne odpowiadają dwie klasy wyjątku OLE: [afxthrowoleexception —](../mfc/reference/exception-processing.md#afxthrowoleexception) i [afxthrowoledispatchexception —](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Pozwala to zgłosić ogólne wyjątki OLE i wyjątki wysyłania OLE, odpowiednio.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

