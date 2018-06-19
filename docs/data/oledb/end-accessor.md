---
title: END_ACCESSOR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7bab52df0ed05886933a3df827fae5198651b39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099241"
---
# <a name="endaccessor"></a>END_ACCESSOR
Oznacza koniec wpis dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
END_ACCESSOR()  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Dla wielu metod dostępu w zestawie wierszy, należy określić `BEGIN_ACCESSOR_MAP` i użyj `BEGIN_ACCESSOR` makro dla każdego poszczególne metody dostępu. `BEGIN_ACCESSOR` Makro zostało zakończone z `END_ACCESSOR` makra. `BEGIN_ACCESSOR_MAP` Makro zostało zakończone z `END_ACCESSOR_MAP` makra.  
  
## <a name="example"></a>Przykład  
 Zobacz [begin_accessor_map —](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)