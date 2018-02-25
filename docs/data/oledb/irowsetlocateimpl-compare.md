---
title: IRowsetLocateImpl::Compare | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57cef167c76d3cfe2396684ddb4ba5959ef38e5c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
Porównuje dwa zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Jedną z zakładki może być standard zdefiniowane OLE DB [standardowe zakładki](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST**, **DBBMK_LAST**, lub **DBBMK_INVALID**). Wartość zwracana w `pComparison` wskazuje relację między dwiema zakładek:  
  
-   **DBCOMPARE_LT** (`cbBookmark1` przed `cbBookmark2`.)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1` jest równa `cbBookmark2`.)  
  
-   **DBCOMPARE_GT** (`cbBookmark1` po `cbBookmark2`.)  
  
-   **DBCOMPARE_NE** (zakładki są takie same i nie uporządkowanych).  
  
-   **DBCOMPARE_NOTCOMPARABLE** (nie można porównać zakładki.)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetLocateImpl, klasa](../../data/oledb/irowsetlocateimpl-class.md)