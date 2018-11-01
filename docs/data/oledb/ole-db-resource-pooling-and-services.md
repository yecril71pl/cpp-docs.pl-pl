---
title: Buforowanie zasobów i usługi OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 7c57376404b37de95e01be6459b3d57ddcc53fe3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448103"
---
# <a name="ole-db-resource-pooling-and-services"></a>Buforowanie zasobów i usługi OLE DB

Do pracy oraz buforowanie OLE DB lub z dowolnej usługi OLE DB, Twój dostawca musi obsługiwać agregacji wszystkich obiektów. Jest to wymagane, OLE DB w wersji 1.5 lub nowszej dostawcy. Usługi za pomocą bardzo ważne jest. Puli dostawców, które nie obsługują agregacji i znajdują się żadnych dodatkowych usług.

Do puli, dostawców musi obsługiwać model wątku bezpłatne. Pula zasobów Określa model wątku dostawcy zgodnie z opisem w `DBPROP_THREADMODEL` właściwości.

Jeśli dostawca ma stan połączenia globalnego, które mogą ulec zmianie, gdy źródło danych jest w stanie zainicjowania, powinien obsługiwać nowe `DBPROP_RESETDATASOURCE` właściwości. Ta właściwość jest wywoływana przed połączenie jest ponownie i daje możliwość wyczyścić stanu przed jego użyciem dalej w dostawcy. Jeśli dostawca nie można wyczyścić pewnego stanu skojarzonych z tym połączeniem, może zwrócić `DBPROPSTATUS_NOTSETTABLE` dla właściwości i połączenie nie zostanie ponownie.

Dostawcy połączenia ze zdalną bazą danych, które może wykryć, czy możesz stracić połączenia powinien obsługiwać `DBPROP_CONNECTIONSTATUS` właściwości. Ta właściwość umożliwia usług OLE DB wykrywania nieaktywnych połączeń i upewnij się, że nie są zwracane do puli.

Na koniec rejestracji automatycznej transakcji ogólnie nie działa, o ile nie jest zaimplementowana na tym samym poziomie, występujący buforowanie. Dostawcy, obsługujące rejestracji automatycznej transakcji, samodzielnie powinien obsługiwać wyłączenie tej rejestracji uwidaczniając `DBPROP_INIT_OLEDBSERVICES` właściwości i wyłączanie rejestracji, jeśli `DBPROPVAL_OS_TXNENLISTMENT` zaznaczenie jest usunięte.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)