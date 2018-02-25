---
title: CDynamicAccessor::GetColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9f311e9fc5330a68edba4fd5029e97b75033406
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
Zwraca metadane kolumny wymagane przez większość konsumentów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRowset`  
 [in] Wskaźnik do [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) interfejsu.  
  
 *pColumns*  
 [out] Wskaźnik do pamięci, do której należy zwrócić liczbę kolumn w zestawie wierszy; Liczba ta obejmuje kolumny zakładki, jeśli istnieje.  
  
 *ppColumnInfo*  
 [out] Wskaźnik do pamięci, do której należy zwrócić tablicę **DBCOLUMNINFO** struktury. Zobacz sekcję "DBCOLUMNINFO struktury" w [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty*.  
  
 `ppStringsBuffer`  
 [out] Wskaźnik do pamięci zwraca wskaźnik do przechowywania wszystkich wartości ciągów (nazwy używane w *columnid* lub *pwszName*) w bloku pojedynczego alokacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty* informacje o typach danych **DBORDINAL**, **DBCOLUMNINFO**, i **OLECHAR**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)