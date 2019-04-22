---
title: Buforowanie zasobów i usługi OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: f46c6f493ae41570c75c384fcc836707faeab99f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023753"
---
# <a name="ole-db-resource-pooling-and-services"></a>Buforowanie zasobów i usługi OLE DB

Do pracy oraz buforowanie OLE DB lub z dowolnej usługi OLE DB, Twój dostawca musi obsługiwać agregacji wszystkich obiektów. Jest to wymagane, OLE DB w wersji 1.5 lub nowszej dostawcy. Usługi za pomocą bardzo ważne jest. Puli dostawców, które nie obsługują agregacji i znajdują się żadnych dodatkowych usług.

Do puli, dostawców musi obsługiwać model wątku bezpłatne. Pula zasobów Określa model wątku dostawcy zgodnie z właściwością DBPROP_THREADMODEL.

Jeśli dostawca ma stan połączenia globalnego, które mogą ulec zmianie, gdy źródło danych jest w stanie zainicjowania, jego powinien obsługiwać nową właściwość DBPROP_RESETDATASOURCE. Ta właściwość jest wywoływana przed połączenie jest ponownie i daje możliwość wyczyścić stanu przed jego użyciem dalej w dostawcy. Jeśli dostawca nie można wyczyścić pewnego stanu skojarzonych z tym połączeniem, może zwracać DBPROPSTATUS_NOTSETTABLE właściwości i nie będzie można ponownie użyć połączenia.

Dostawcy połączenia ze zdalną bazą danych, które może wykryć, czy połączenie mogło zostać utracone powinien obsługiwać właściwość DBPROP_CONNECTIONSTATUS. Ta właściwość umożliwia usług OLE DB wykrywania nieaktywnych połączeń i upewnij się, że nie są one zwrócone do puli.

Na koniec rejestracji automatycznej transakcji ogólnie nie działa, chyba że jest stosowana na tym samym poziomie, występujący buforowanie. Dostawcy, obsługujące rejestracji automatycznej transakcji powinien obsługiwać wyłączenie tej rejestracji przez udostępnianie właściwości DBPROP_INIT_OLEDBSERVICES i wyłączenie rejestracji, jeśli nie jest zaznaczona DBPROPVAL_OS_TXNENLISTMENT.

## <a name="see-also"></a>Zobacz także

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)