---
title: "OLE DB buforowanie zasobów i usługi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f1f97bde5c2922af3d6a5da5ca77fd270867ff21
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-resource-pooling-and-services"></a>Buforowanie zasobów i usługi OLE DB
Aby pracować z puli OLE DB lub z dowolnej usługi OLE DB, Twój dostawca musi obsługiwać agregacji wszystkich obiektów. Jest to wymagane, OLE DB w wersji 1.5 lub nowszego dostawcy. Jest to niezbędne do korzystania z usługi. Dostawców, które nie obsługują agregacji nie może być w puli i żadnych dodatkowych usług są dostępne.  
  
 Do puli, dostawców musi obsługiwać model wolnych wątków. Pula zasobów określa modelu wątku dostawcy zgodnie z **DBPROP_THREADMODEL** właściwości.  
  
 Jeśli dostawca ma stan połączenia globalnego, który może zmienić, gdy źródło danych jest w stanie zainicjowania, powinien obsługiwać nowe **DBPROP_RESETDATASOURCE** właściwości. Ta właściwość jest wywoływana przed połączeniem zostanie ponownie użyty i daje możliwość Wyczyść stan przed jego użyciem następnego dostawcy. Jeśli dostawca nie może wyczyścić niektórych stan skojarzony z tym połączeniem, może on zwrócić **DBPROPSTATUS_NOTSETTABLE** dla właściwości i połączenie nie zostanie ponownie.  
  
 Dostawców, którzy Połącz ze zdalną bazą danych i może wykryć, czy powinny obsługiwać połączenia zostaną utracone **DBPROP_CONNECTIONSTATUS** właściwości. Ta właściwość umożliwia usługi OLE DB do wykrywania nieaktywnych połączeń i upewnij się, że nie są zwracane do puli.  
  
 Na koniec rejestracji automatycznej transakcji zwykle nie działa, jeśli jest stosowana na tym samym poziomie, który występuje w puli. Dostawców, które same obsługują transakcji automatycznej rejestracji powinien obsługiwać wyłączenie tej rejestracji w przypadku wystawianego **DBPROP_INIT_OLEDBSERVICES** właściwości i wyłączanie rejestracji, jeśli **DBPROPVAL_OS_ TXNENLISTMENT** jest wyłączona.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)