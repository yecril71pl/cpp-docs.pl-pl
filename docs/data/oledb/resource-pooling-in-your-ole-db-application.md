---
title: Buforowanie zasobów w aplikacji OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: c4e548d00f5772e41e0a725020cd2f279e3ab89b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479550"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Buforowanie zasobów w aplikacji OLE DB

Aby skorzystać z puli w aplikacji, należy się upewnić usługi OLE DB są wywoływane, uzyskując źródła danych za pośrednictwem `IDataInitialize` lub `IDBPromptInitialize`. Jeśli używasz bezpośrednio `CoCreateInstance` aby wywołać dostawcę oparte na CLSID dostawcy, są wywoływane żadnych usług OLE DB.

Usługi OLE DB Obsługa pule połączonych źródeł danych tak długo, jak odwołanie do `IDataInitialize` lub `IDBPromptInitialize` jest publiczną, lub tak długo, jak istnieje połączenie w użyciu. Pule są także obsługiwane automatycznie w środowisku usług COM + 1.0 lub Internet Information Services (IIS). Jeśli aplikacja korzysta z puli poza środowiskiem modelu COM + 1.0 usług lub usług IIS, należy zachować odwołanie do `IDataInitialize` lub `IDBPromptInitialize` lub prowadzenia na co najmniej jedno połączenie. Aby upewnić się, że pula zniszczony po wydaniu ostatniego połączenia przez aplikację, należy zachować odwołania lub przytrzymaj połączenia przez okres istnienia aplikacji.

Usługi OLE DB zidentyfikować pulę, z którego połączenia jest rysowana w czasie, `Initialize` jest wywoływana. Po utworzeniu połączenia z puli nie można przenieść do innej puli. W związku z tym, unikanie robienia różnych rzeczy w aplikacji, które zmieniają inicjowania informacji, takich jak wywoływanie `UnInitialize` lub wywoływania `QueryInterface` interfejsu właściwe dla dostawcy, przed wywołaniem `Initialize`. Ponadto nie są w puli połączeń ustanowionych z monitu wartość inna niż DBPROMPT_NOPROMPT. Jednak ciągu inicjującego pobierane Połączenie nawiązywane za pośrednictwem monitowania może służyć do ustanawiania dodatkowe puli połączeń do tego samego źródła danych.

Niektórzy dostawcy należy osobnego połączenia dla każdej sesji. Te dodatkowe połączenia musi być oddzielnie zarejestrowany w transakcji rozproszonej, jeśli taka istnieje. Usługi OLE DB przechowuje i ponownie używa pojedynczej sesji na źródle danych, ale jeśli aplikacja żąda więcej niż jednej sesji w danym momencie z pojedynczego źródła danych, dostawca może się to zakończyć wykonywania dodatkowych połączeń i wykonując rejestracjach dodatkowe transakcji, które są nie w puli. Jest faktycznie bardziej wydajne, aby utworzyć oddzielnego źródła danych dla każdej sesji w środowisku pulpitów, niż można utworzyć wiele sesji z pojedynczego źródła danych.

Na koniec ponieważ ADO automatycznie korzysta z OLE DB usług, ADO mogą używać do nawiązywania połączeń i buforowanie i rejestracji następują automatycznie.

## <a name="see-also"></a>Zobacz też

[Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)