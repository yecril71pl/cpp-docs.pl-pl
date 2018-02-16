---
title: "Caccessorbase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAccessorBase
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f57c771f0d129683bde0629f9c28cfbaa897ee4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="caccessorbase-class"></a>CAccessorBase — Klasa
Wszystkie metody dostępu w szablonach OLE DB dziedziczyć po tej klasie. `CAccessorBase` Umożliwia jednego zestawu wierszy do zarządzania wielu metod dostępu. Umożliwia także powiązanie dla parametrów i kolumn wyjściowych.  
  
## <a name="syntax"></a>Składnia

```cpp
// Replace with syntax  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zamknij](../../data/oledb/caccessorbase-close.md)|Zamyka metody dostępu.|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|Pobiera dojście metody dostępu.|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|Pobiera liczbę metod dostępu tworzone przez klasę.|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|Sprawdza, czy określona metoda dostępu jest autoaccessor.|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|Udostępnia metody dostępu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)