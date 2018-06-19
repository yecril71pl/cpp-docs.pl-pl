---
title: Interfejsy obiektu źródła danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c8aaed0a9f50e20dba5938b9b37425f4caa2bb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101880"
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