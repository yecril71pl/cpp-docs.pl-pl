---
title: PROVIDER_COLUMN_ENTRY_WSTR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR macro
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd0f87bad4fbd758849e33ae18cdcfd6a8e72357
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="providercolumnentrywstr"></a>PROVIDER_COLUMN_ENTRY_WSTR
Przedstawia kolumnę określonych obsługiwane przez dostawcę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 `ordinal`  
 [in] Numer kolumny. Jeśli kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 `member`  
 [in] Zmiennej członkowskiej klasy danych, która przechowuje dane.  
  
## <a name="remarks"></a>Uwagi  
 Używanie tego makra, gdy kolumna danych jest zakończony znakiem null ciągu znaków Unicode, [DBTYPE_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)