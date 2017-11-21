---
title: COLUMN_NAME_PS_STATUS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_PS_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_PS_STATUS macro
ms.assetid: 134e1bfe-abfa-4b64-9159-e492f31de44b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0505197265a2507927aa5e7e7d09d0bd8d0029c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="columnnamepsstatus"></a>COLUMN_NAME_PS_STATUS
Reprezentuje powiązanie w zestawie wierszy w kolumnie określonej w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), ale to makro również ma stan precyzja, skala i kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COLUMN_NAME_PS_STATUS(  
pszName  
,   
nPrecision  
,   
nScale  
,   
data  
,   
status )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to zrobić przez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.  
  
 `nPrecision`  
 [in] Maksymalna dokładność kolumny, które chcesz powiązać.  
  
 `nScale`  
 [in] Skala kolumnę, którą chcesz utworzyć powiązania.  
  
 `data`  
 [in] Odpowiedni element członkowski danych w rekordzie użytkownika.  
  
 *Stan*  
 [in] Zmienna może być powiązane z stan kolumny.  
  
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
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)