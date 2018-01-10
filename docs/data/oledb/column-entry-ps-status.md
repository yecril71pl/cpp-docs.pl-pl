---
title: COLUMN_ENTRY_PS_STATUS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_ENTRY_PS_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_ENTRY_PS_STATUS macro
ms.assetid: c02140c6-246f-4df5-8b86-698d7d137022
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c0507ed572fcea6ba9f73cb0c16ae079f9ae857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="columnentrypsstatus"></a>COLUMN_ENTRY_PS_STATUS
Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COLUMN_ENTRY_PS_STATUS(  
nOrdinal  
,   
nPrecision  
,   
nScale  
,   
data  
,   
status  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) w *OLE DB Podręcznik programisty*.  
  
 `nOrdinal`  
 [in] Numer kolumny.  
  
 `nPrecision`  
 [in] Maksymalna dokładność kolumny, które chcesz powiązać.  
  
 `nScale`  
 [in] Skala kolumnę, którą chcesz utworzyć powiązania.  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
 *Stan*  
 [in] Zmienna może być powiązane z stan kolumny.  
  
## <a name="remarks"></a>Uwagi  
 Umożliwia określenie precyzję i skalę kolumny, które chcesz powiązać. To makro obsługuje *stan* zmiennej. Jest on używany w następujących miejscach:  
  
-   Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.  
  
-   Między [begin_accessor —](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.  
  
-   Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR —](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP —](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY —](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)