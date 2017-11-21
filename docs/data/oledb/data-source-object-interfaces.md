---
title: "Interfejsy obiektu źródła danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d71fa9303f1b837e9d7b7110f83718a1360b91e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-object-interfaces"></a>Interfejsy obiektu źródła danych
W poniższej tabeli przedstawiono interfejsów obowiązkowe i opcjonalne zdefiniowanych przez OLE DB dla obiekt źródła danych.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|Obowiązkowy|Tak|  
|`IDBInitialize`|Obowiązkowy|Tak|  
|`IDBProperties`|Obowiązkowy|Tak|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|Obowiązkowy|Tak|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|Nie|  
|`IDBDataSourceAdmin`|Optional|Nie|  
|`IDBInfo`|Optional|Nie|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Optional|Nie|  
|`ISupportErrorInfo`|Optional|Nie|  
  
 Źródło danych implementuje obiektu `IDBProperties`, `IDBInitialize`, i `IDBCreateSession` interfejsy przez dziedziczenie. Można wybrać do obsługi dodatkowych funkcji przy dziedziczeniu ani nie dziedziczy z jednej z tych klas implementacji. Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejsu, musi dziedziczyć z `IDBDataSourceAdminImpl` klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)