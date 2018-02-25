---
title: Interfejsy obiektu transakcji | Dokumentacja firmy Microsoft
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
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d295bd73fbc8bb5fba7ae443b8a99705768753bf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="transaction-object-interfaces"></a>Interfejsy obiektu transakcji
Obiekt transaction definiuje Atomowej jednostki pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie. Ten obiekt nie jest bezpośrednio obsługiwana przez Szablony dostawców OLE DB (to znaczy, należy utworzyć własny obiektu).  
  
 W poniższej tabeli przedstawiono interfejsów obowiązkowe i opcjonalne zdefiniowanych przez OLE DB dla obiekt transakcji.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Obowiązkowy|Nie|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Obowiązkowy|Nie|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)