---
title: "Buforowanie zasobów w aplikacji OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a11fe27fad42e7a27e55a8b4f494980aa9f708a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Buforowanie zasobów w aplikacji OLE DB
Aby skorzystać z puli aplikacji, należy upewnić się, OLE DB usług są wywoływane przez uzyskanie źródła danych za pośrednictwem **procedury IDataInitialize** lub **IDBPromptInitialize**. Jeśli używasz bezpośrednio `CoCreateInstance` do wywoływania dostawcy oparte na CLSID dostawcy, są wywoływane żadnych usług OLE DB.  
  
 Usługi OLE DB Obsługa pule połączonych źródeł danych tak długo, jak odwołanie do **procedury IDataInitialize** lub **IDBPromptInitialize** jest wstrzymany lub tak długo, jak istnieje połączenie w użyciu. Pule są także automatycznie obsługiwane w środowisku COM + 1.0 usług lub Internet Information Services (IIS). Jeśli aplikacja korzysta z puli poza środowiskiem usług COM + 1.0 lub usług IIS, należy mieć odwołanie do **procedury IDataInitialize** lub **IDBPromptInitialize** lub przechowywania na co najmniej jedną połączenie. Aby upewnić się, że puli nie pobrać zniszczone po wydaniu ostatniego połączenia przez aplikację, utrzymywać odwołania lub zaczekaj do połączenia przez czas ich istnienia aplikacji.  
  
 Usługi OLE DB identyfikację puli, w którym połączenie jest rysowana w czasie który `Initialize` jest wywoływana. Po utworzeniu połączenia z puli nie można przenieść do innej puli. W związku z tym uniknąć wykonywania czynności w aplikacji, które zmienić inicjowania informacje, takie jak wywołania `UnInitialize` lub wywoływania `QueryInterface` dla interfejsu specyficznych dla dostawcy, przed wywołaniem `Initialize`. Ponadto połączeń z monitu o wartości innej niż **DBPROMPT_NOPROMPT** nie są grupowane w pulach. Jednak ciągu inicjującego pobierane z Połączenie nawiązywane za pośrednictwem monitowania może służyć do ustanawiania dodatkowe puli połączeń z tym samym źródłem danych.  
  
 Niektórzy dostawcy należy oddzielnego połączenia dla każdej sesji. Te dodatkowe połączenia musi być oddzielnie zarejestrowany w transakcji rozproszonej, jeśli taka istnieje. Usługi OLE DB buforuje i ponownie używa pojedynczej sesji na źródle danych, ale jeśli aplikacja żąda więcej niż jedną sesję w czasie z pojedynczego źródła danych, dostawcę mogą wystąpić dodatkowe połączeń i wykonując rejestracji dodatkowych transakcji, które są nie w puli. Jest rzeczywiście bardziej wydajne, można utworzyć oddzielnego źródła danych dla każdej sesji w środowisku puli, niż można utworzyć wiele sesji z pojedynczego źródła danych.  
  
 Ponadto ponieważ ADO automatycznie korzysta z OLE DB usług, ADO można używać do nawiązywania połączeń i buforowanie i rejestracji następują automatycznie.  
  
## <a name="see-also"></a>Zobacz też  
 [OLE DB usług i korzystanie z puli zasobów](../../data/oledb/ole-db-resource-pooling-and-services.md)