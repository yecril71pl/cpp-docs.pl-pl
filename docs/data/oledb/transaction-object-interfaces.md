---
title: Interfejsy obiektu transakcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2d84d9a072d3eeaa84246a6692487be5c71679c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465522"
---
# <a name="transaction-object-interfaces"></a>Interfejsy obiektu transakcji
Obiekt transakcji definiuje pojedynczej Atomowej jednostki pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie nawzajem. Ten obiekt nie jest bezpośrednio obsługiwany przez Szablony dostawców OLE DB (oznacza to, należy utworzyć własny obiektu).  
  
 W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu transakcji.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Obowiązkowy|Nie|  
|[Metody ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Obowiązkowy|Nie|  
|[Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Optional|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)