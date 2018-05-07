---
title: CDynamicAccessor::GetColumnFlags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
dev_langs:
- C++
helpviewer_keywords:
- GetColumnFlags method
ms.assetid: b2ba2f3a-2c61-4a49-abfb-75823908ccf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9cb4e439ab650793dcbafa79092d03b53271e45a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetcolumnflags"></a>CDynamicAccessor::GetColumnFlags
Pobiera właściwości kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```
bool GetColumnFlags(DBORDINAL nColumn,   
  DBCOLUMNFLAGS* pFlags) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
 `pFlags`  
 [out] Wskaźnik do maską bitów opisano charakterystyki kolumny. Zobacz sekcję "Typ wyliczany DBCOLUMNFLAGS" w [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli właściwości kolumny są pomyślnie pobrane. W przeciwnym razie zwraca **false**.  
  
## <a name="remarks"></a>Uwagi  
 Numer kolumny jest przesunięta w jeden. Kolumna zero jest szczególnych przypadkach; Jeśli dostępny jest zakładki.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)