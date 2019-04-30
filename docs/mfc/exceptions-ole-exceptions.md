---
title: 'Wyjątki: Wyjątki OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: e404005a88398ec909e3043cfa55c7e8fbe2f594
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405967"
---
# <a name="exceptions-ole-exceptions"></a>Wyjątki: Wyjątki OLE

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

Dwie funkcje globalne odpowiadają dwie klasy OLE w wyjątek: [Afxthrowoleexception —](../mfc/reference/exception-processing.md#afxthrowoleexception) i [afxthrowoledispatchexception —](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Pozwala to zgłosić ogólne wyjątki OLE i wyjątki wysyłania OLE, odpowiednio.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
