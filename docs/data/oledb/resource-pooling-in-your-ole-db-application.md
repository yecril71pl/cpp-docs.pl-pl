---
title: Buforowanie zasobów w aplikacji OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209786"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Buforowanie zasobów w aplikacji OLE DB

Aby korzystać z puli w aplikacji, należy się upewnić, że OLE DB usługi są wywoływane przez pobranie źródła danych za pomocą `IDataInitialize` lub `IDBPromptInitialize`. Jeśli używasz bezpośrednio `CoCreateInstance` do wywołania dostawcy na podstawie identyfikatora CLSID dostawcy, nie zostaną wywołane żadne usługi OLE DB.

Usługi OLE DB obsługują pule połączonych źródeł danych tak długo, jak odniesienia do `IDataInitialize` lub `IDBPromptInitialize` są przechowywane lub tak długo, jak jest używane połączenie. Pule są również automatycznie obsługiwane w środowisku usług modelu COM+ 1,0 lub Internet Information Services (IIS). Jeśli aplikacja korzysta z puli zewnętrznej dla usług modelu COM+ 1,0 lub środowiska IIS, należy zachować odwołanie do `IDataInitialize` lub `IDBPromptInitialize` lub wstrzymać do co najmniej jednego połączenia. Aby mieć pewność, że pula nie zostanie zniszczona, gdy ostatnie połączenie zostanie wydane przez aplikację, Zachowaj odwołanie lub zaczekaj na połączenie przez okres istnienia aplikacji.

Usługi OLE DB identyfikują pulę, z której jest nawiązywane połączenie w momencie wywołania `Initialize`. Po nawiązaniu połączenia z puli nie można go przenieść do innej puli. Należy więc unikać wykonywania operacji w aplikacji, które zmieniają informacje o inicjacji, takie jak wywołanie `UnInitialize` lub wywoływanie `QueryInterface` dla interfejsu specyficznego dla dostawcy przed wywołaniem `Initialize`. Ponadto połączenia ustanowione z wartością monitu inną niż DBPROMPT_NOPROMPT nie są w puli. Jednak ciąg inicjujący pobrany z połączenia ustanowionego za pomocą monitowania może służyć do ustanowienia dodatkowych połączeń w puli z tym samym źródłem danych.

Niektórzy dostawcy muszą nawiązać oddzielne połączenie dla każdej sesji. Te dodatkowe połączenia muszą być osobno zarejestrowane w transakcji rozproszonej, jeśli taka istnieje. OLE DB usługi pamięci podręcznej i ponownie używa pojedynczej sesji dla każdego źródła danych, ale jeśli aplikacja zażąda więcej niż jednej sesji jednocześnie z pojedynczego źródła danych, dostawca może zakończyć tworzenie dodatkowych połączeń i wykonywanie dodatkowych rejestracji transakcji, które nie są obsługiwane w puli. W przypadku każdej sesji w środowisku w puli nie można utworzyć oddzielnego źródła danych niż w celu utworzenia wielu sesji z jednego źródła danych.

Na koniec ponieważ usługa ADO automatycznie korzysta z usług OLE DB, można używać obiektów ADO do nawiązywania połączeń, a buforowanie i rejestracja odbywają się automatycznie.

## <a name="see-also"></a>Zobacz też

[Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
