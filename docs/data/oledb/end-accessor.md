---
title: END_ACCESSOR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: END_ACCESSOR
dev_langs: C++
helpviewer_keywords: END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04cdfc3d40bcf45db45998700a9a0a5d1c1177d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="endaccessor"></a>END_ACCESSOR
Oznacza koniec wpis dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
END_ACCESSOR( )  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Dla wielu metod dostępu w zestawie wierszy, należy określić `BEGIN_ACCESSOR_MAP` i użyj `BEGIN_ACCESSOR` makro dla każdego poszczególne metody dostępu. `BEGIN_ACCESSOR` Makro zostało zakończone z `END_ACCESSOR` makra. `BEGIN_ACCESSOR_MAP` Makro zostało zakończone z `END_ACCESSOR_MAP` makra.  
  
## <a name="example"></a>Przykład  
 Zobacz [begin_accessor_map —](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP —](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR —](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)