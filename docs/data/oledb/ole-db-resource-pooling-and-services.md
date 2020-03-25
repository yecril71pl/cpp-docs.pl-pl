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
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210031"
---
# <a name="ole-db-resource-pooling-and-services"></a>Buforowanie zasobów i usługi OLE DB

Aby dobrze współpracować z pulami OLE DB lub z dowolną usługą OLE DB, dostawca musi obsługiwać agregację wszystkich obiektów. Jest to wymagane przez dowolnego dostawcę OLE DB 1,5 lub nowszego. Jest to istotne dla korzystania z usług. Nie można dodać do puli dostawców, którzy nie obsługują agregacji, i nie podano dodatkowych usług.

Aby można było korzystać z puli, dostawcy muszą obsługiwać bezpłatny model wątków. Pula zasobów określa model wątku dostawcy zgodnie z właściwością DBPROP_THREADMODEL.

Jeśli dostawca ma stan połączenia globalnego, który może ulec zmianie, gdy źródło danych jest w stanie zainicjowania, powinien obsługiwać nową właściwość DBPROP_RESETDATASOURCE. Ta właściwość jest wywoływana przed ponownym użyciem połączenia i nadaje dostawcy możliwość oczyszczenia stanu przed rozpoczęciem następnego użycia. Jeśli dostawca nie może oczyścić jakiegoś stanu skojarzonego z połączeniem, może zwrócić DBPROPSTATUS_NOTSETTABLE dla właściwości, a połączenie nie będzie ponownie używane.

Dostawcy, którzy łączą się ze zdalną bazą danych i mogą wykryć, czy połączenie mogło zostać utracone, powinno obsługiwać Właściwość DBPROP_CONNECTIONSTATUS. Ta właściwość daje usługom OLE DB możliwość wykrywania utraconych połączeń i upewnienia się, że nie są one zwracane do puli.

Na koniec automatyczna rejestracja transakcji zwykle nie działa, chyba że zostanie zaimplementowana na tym samym poziomie, w którym występuje buforowanie. Dostawcy obsługujący funkcję automatycznego rejestracji transakcji powinni obsługiwać wyłączenie tej rejestracji przez ujawnienie właściwości DBPROP_INIT_OLEDBSERVICES i wyłączenie rejestracji, jeśli DBPROPVAL_OS_TXNENLISTMENT została odzaznaczona.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
