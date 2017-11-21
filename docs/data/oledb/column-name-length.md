---
title: COLUMN_NAME_LENGTH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_LENGTH
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_LENGTH macro
ms.assetid: 3c4b6c94-d29d-4fba-a425-8186c9dc3f6a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96887e761b257bd6676adba27799992a73e910f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="columnnamelength"></a>COLUMN_NAME_LENGTH
Reprezentuje powiązanie w zestawie wierszy w kolumnie określonej w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), ale to makro również ma długość kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COLUMN_NAME_LENGTH(  
pszName  
,   
data  
,   
length  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to zrobić przez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
 *długość*  
 [in] Zmienna może być powiązane z długość kolumny.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) informacji o tym, gdzie **COLUMN_NAME_\***  makra są używane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR —](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP —](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)